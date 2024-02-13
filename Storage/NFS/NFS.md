# NFS

## Table of contents

- [NFS](#nfs)
  - [Table of contents](#table-of-contents)
  - [⏬Install NFS Package⏬](#install-nfs-package)
  - [💽Mount an NFS shared directory💽](#mount-an-nfs-shared-directory)
  - [🔂Mount on startup🆙](#mount-on-startup)

## ⏬Install NFS Package⏬

```bash
apt install nfs-common
```

## 💽Mount an NFS shared directory💽

```bash
mount -t nfs <nfs-server-address>:<path-to-shared-folder> <mount-point-path>
```

## 🔂Mount on startup🆙

Add mount in /etc/fstab :

```plaintext
<nfs-server-address>:<shared-folder-path>        <mount-point-path>        nfs     defaults        0       0
```
