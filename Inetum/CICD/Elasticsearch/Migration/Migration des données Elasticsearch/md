## Installation du cluster NFS et démarrage de l'ancien cluster

Pour pouvoir migrer les données d'Elasticsearch il faut que l'ancien et le nouveau cluster soient allumés et prêt à fonctionner. Dans notre environment CICD, Elasticsearch est installé avec l'[Opérateur](https://www.elastic.co/fr/blog/introducing-elastic-cloud-on-kubernetes-the-elasticsearch-operator-and-beyond) fournis par Elasticsearch. 

Cet opérateur est déjà installé. Pour s'assurer de son fonctionnement, il suffit de scale son statefulset à 1.

``` bash
kubectl scale statefulset -n=elastic-system elastic-operator --replicas=1
```

Les deployments de l'ancien cluster sont présents sur Gitlab de la CICD. Le deployment et l'ingress sont déjà appliqués. L'ancien cluster devrai donc se construire automatiquement après le lancement de l'opérateur.

Voici le deployment pour le nouveau cluster :
``` yaml
apiVersion: elasticsearch.k8s.elastic.co/v1
kind: Elasticsearch
metadata:
  name: es-cluster
  namespace: elg
spec:
  version: 7.15.1
  http:
    tls:
      selfSignedCertificate:
        disabled: true
  nodeSets:
  - name: default
    count: 3
    config:
      node.store.allow_mmap: false
      reindex.remote.whitelist: es-cluster-ceph-es-default:9200
      xpack.security.authc:
          anonymous:
            username: anonymous
            roles: superuser
            authz_exception: false
    podTemplate:
      spec:
        initContainers:
        - name: install-plugins # For backups
          command: ['sh', '-c', '/usr/share/elasticsearch/bin/elasticsearch-plugin install --batch repository-s3']
    volumeClaimTemplates:
    - metadata:
        name: elasticsearch-data # Do not change this name unless you set up a volume mount for the data path.
      spec:
        accessModes:
        - ReadWriteOnce
        resources:
          requests:
            storage: 10Gi
        storageClassName: managed-nfs-storage
```

## Suppression des clusters

Il existe deux façons de supprimer le cluster, ***la première supprime également les PVC il ne faut donc pas l'utiliser sur le cluster CEPH tant que les données ne sont pas migrées!***

On supprime  l'objet Elasticsearch : 

``` bash
kubectl delete -n=elg elasticsearch <nom-objet-elastic>
```

La deuxième méthode consiste à éteindre l'opérateur et a supprimer le statefulset et pods du cluster Elasticsearch à supprimer ***cette méthode conserve les PVD et les services*** : 
On scale d'abord l'opérateur à 0 :

``` bash
kubectl scale statefulset -n=elastic-system elastic-operator --replicas=0
```

On supprime le statefulset

``` bash
kubectl delete statefulset -n=elg <nom-statefulset>
```

On supprime le on supprime les pods s'il sont encore présents.

``` bash
kubectl delete pods -n=elg <nom-pod nom-pod nom-pod>
```

## Migration des données

Pour migrer les donnés nous allons utiliser les requête d'API POST fournies par la [documentation d'Elastic](https://www.elastic.co/guide/en/cloud/current/ec-migrating-data.html#ec-reindex-remote).

Voici un example de requête de migration :

``` bash
curl -k --location --request POST 'http://es-cluster-es-default:9200/_reindex' -H 'Content-Type: application/json' -d'
{
  "source": {
    "remote": {
      "host": "http://es-cluster-ceph-es-default:9200"
    },
    "index": "gde-jenkins-jobs-details-2022-21",
    "query": {
      "match_all": {}
    }
  },
  "dest": {
    "index": "gde-jenkins-jobs-details-2022-21"
  }
}'
```

Pour que cela fonctionne il faut que le cluster source soit whitelisté, mais cela est déjà fait dans le [[#Installation du cluster NFS et démarrage de l'ancien cluster|déploiement]]

Il faut réaliser ces commandes de l'intérieur d'un pod pour pouvoir requêter les services :

``` bash
kubectl exec -it [pod] -- bash
```

Il existe cependant une limitation qui empêche la migration de trop d'index à la fois, il faut donc utiliser un script pour requêter la migration des index un par un : 

``` bash
#!/bin/bash
for i in $(seq 20 52);
do
echo $i
echo ""
curl -k --location --request POST 'http://es-cluster-es-default:9200/_reindex' -H 'Content-Type: application/json' -d'
{
  "source": {
    "remote": {
      "host": "http://es-cluster-ceph-es-default:9200"
    },
    "index": "gde-jenkins-jobs-details-2022-'$i'",
    "query": {
      "match_all": {}
    }
  },
  "dest": {
    "index": "gde-jenkins-jobs-details-2022-'$i'"
  }
}'
echo ""
done
```

Il  suffit de remplacer le range du for par les numéros en fin de dom d'index et de changer le nom de l'index si besoin.

Pour passer ce script dans le pod :

``` bash
kubectl cp [file-to-copy] [pod]:[where-to-copy]
```

On donne ensuite les permission d'executions et on lance le script :

``` bash
kubectl exec -it [pod] -- bash
chmod +x [script]
./[script]
```

## Vérifications
On peut utiliser l'outils Elastic-HQ déjà installé sur la CICD pour vérifier l'état des cluster et de leurs données.
