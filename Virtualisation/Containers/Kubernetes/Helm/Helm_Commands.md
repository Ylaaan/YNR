# Helm Commands

Helm help you managing and installing apps on [Kubernetes](../K8s_Commands.md).

## 👀 Info Commands 👀

### List existing Helm releases

```bash
helm list
```

Options :

- Show in all namespaces : `--all-namespaces` or `-A`
- Show by deployment date : `--date`
- Only show deployed : `--deployed`
- Only show pending : `--pending`
- Only show failed : `--failed`
- Only show uninstalled `--uninstalled`
- Print in YAML : `-o yaml`
- Print in JSON : `-o json`
- Print in a table `-o table`

### Show release status

```bash
helm status [release]
```

Options :

- Display a specific revision : `--revision [number]`

### Show release history

```bash
helm history [release]
```

## ⏸ Managing commands 🔄

### Install a chart

```bash
helm install [name] [chart]
```

Options :

- Install in specific namespace : `--namespace [namespace]`
- Specify a YAML value file : `--values [file]`
- Dry run : `--dry-run --debug`

### Uninstall a release

```bash
helm unistall [name]
```

### Upgrade a release

```bash
helm upgrade [release] [chart]
```

Options :

- Rollback if failed upgrade : `--atomic`
- Update dependencies before upgrade : `--dependency-update`
- Specify a YAML values file : `--values`

### Rollback to specific revision

```bash
helm rollback [release] [revision]
```

Options :

- Remove newly create ressources on fail : `--cleanup-on-fail`

## Repository commands

### List repositories

```bash
helm repo list
```

### Add Helm repository

```bash
helm repo add [repository-name] [repository-url]
```

### Helm repositories update

```bash
helm repo update
```

### Remove Helm repository

```bash
helm repo remove
```

### Search for charts

#### In Repositories

```bash
helm search repo [keyword]
```

#### In Hub

```bash
helm search hub [keyword]
```

## Other commands

### Show Helm ENV variables

```bash
helm env
```
