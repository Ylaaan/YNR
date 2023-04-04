https://learn.microsoft.com/en-us/azure/virtual-desktop/getting-started-feature?tabs=existing-adds

## Avancée Globale
Tache|Avancée 
-|-
Creation du Workspace|Fait
Création Host pool|Fait
Ajout des utilisateur au portail|Fait
Création de l'AD Local|Fait
Connexion des VM Host à l'AD|Fait
Connexion avec les utilisateurs de l'AD|Pas fait
Récupération des utilisateurs Externe dans l'AD|Pas Fait

## Identifiants :
Machine|ID|Password
-|-|-
AD Local|AdminPOC@ctf-ad.local|Password1234POC
AD Local|User1|Password1234!!
AD Local|User2|Password1234!!
AVD Host|AdminLOCAL|Password1234LOCAL

## Creation du Workspace
https://learn.microsoft.com/en-us/azure/virtual-desktop/create-application-group-workspace
Pour qu'AVD fonctionne il faut qu'un workspace soit créé :

![Creation workspace.png](Creation_workspace.png)

On le configure : 

![Configuration host pool](Configuration_workspace1.png)

Le groupe d'application sera sélectionné plus tard. On peut ensuite créer la ressource.

## Création Host pool
https://learn.microsoft.com/en-us/azure/virtual-desktop/create-application-group-workspace
Pour créer un host pool il suffit de se rendre sur le portail Azure et de créer une ressource "Host pool" : 

![Creation du host pool](Creation_host_pool.png)

Une fois sélectionné, on le configure : 

![Configuration host pool](Configuration_host_pool1.png)

On ne créer pas de machines virtuelles directement à la création du pool. Ces VM seront crées plus tard pour faciliter les tests. On sélectionne un espace de travail : 

![Configuration host pool](Configuration_host_pool2.png)

On peut ensuite valider et créer le pool AVD :

![Configuration host pool](Configuration_host_pool3.png)

## Ajout des utilisateur au portail
https://learn.microsoft.com/en-us/azure/virtual-desktop/create-application-group-workspace
L'ajout des utilisateurs au portail AVD est simple, il faut se rendre sur le chemin suivant et de cliquer sur ajouter. Pour que cela fonctionne il faut être propriétaire du groupe d'application. 

![[Ajout_Utilisateurs.png]]

## Creation des machines AVD Hosts
https://learn.microsoft.com/en-us/azure/virtual-desktop/add-session-hosts-host-pool?tabs=portal%2Cgui

## Connexion des VM Host à l'AD
https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/join-a-computer-to-a-domain

Pour connecter un machine AVD host au domaine de l'AD local, il faut se rendre en RDP sur l'AD Local, et depuis cette machine se reconnecter sur l'AVD host en RDP.

Une fois connecter on se rend dans :
panneau de configuration → système et sécurité  → système → renommer ce PC → member of → changer le domaine

on se connecte avec le compte AdminPOC.

## Connexion avec les utilisateurs de l'AD

#### Tests déjà réalisés
- Mettre les utilisateurs VDI dans le groupe "Remote Desktop Users"
- Ajouter le role "Utilisateur de virtualisation de bureau" sur Azure dans l'application Group
- Joindre l'AAD d'Inetum et se connecter avec son compte Inetum (Sans succès)
- Créer des GPO dans L'AD.
