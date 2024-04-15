# K8s certificates renewal

## Table of contents

- [K8s certificates renewal](#k8s-certificates-renewal)
  - [Table of contents](#table-of-contents)
  - [🔄Renew the certificates🔄](#renew-the-certificates)
  - [🔴Restart the control plane🟢](#restart-the-control-plane)
  - [📜Configure kubectl with the new certificates📜](#configure-kubectl-with-the-new-certificates)

On the master node:

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

[Follow these instructions.](./K8s_commands.md#configure-kubectl)
