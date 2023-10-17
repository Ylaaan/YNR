# Kubernetes certificates renewal

On the master node :

## 🔄Renew the certificates🔄

```bash
sudo kubeadm certs renew all
```

## 🔴Restart the control plane🟢

```bash
cd /etc/kubernetes/
mv manifests/ /tmp
systemctl restart kubelet
```

Wait for the control plane to be deleted.

```bash
mv /tmp/manifests .
```

## 📜Configure kubectl with the new certificates📜

[Follow these instructions.](./Kubernetes_Commands.md#configure-kubectl)
