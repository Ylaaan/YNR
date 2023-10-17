# Ceph bashrc

While using ceph on a [kubernetes](../Virtualisation/Containers/Kubernetes/Kubernetes_Commands.md) cluster, you must set an alias to use the [ceph commands](./Ceph_Commands.md) directly.

## files contents

Add this to the bashrc

```bash
alias ceph='kubctl -n <nom-namespace> exec -it deploy/rook-ceph-tools -- ceph'
```

[Apply bashrc](../Bash/Bash_commands.md#apply-modifications-of-bashrc-file)
