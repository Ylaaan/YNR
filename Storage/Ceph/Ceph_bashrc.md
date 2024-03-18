# Ceph bashrc

## Table of contents

- [Ceph bashrc](#ceph-bashrc)
  - [Table of contents](#table-of-contents)
  - [files contents](#files-contents)

While using Ceph on a [Kubernetes](../../Virtualisation/Containers/Kubernetes/K8s_commands.md) cluster, you must set an alias to use the [Ceph commands](./Ceph_Commands.md) directly.

## files contents

Add this to the bashrc

```bash
alias ceph='kubctl -n <nom-namespace> exec -it deploy/rook-ceph-tools -- ceph'
```

[Apply bashrc](../../Bash/Bash_commands.md#)
