# Gcloud

- [CLI](#CLI)
	- [Install](#Install)
	- [Commands](#Commands)
		- [Check version](#Check%20version)
		- [Connect to gcloud project](#Connect%20to%20gcloud%20project)
		- [Get info on current environment](#Get%20info%20on%20current%20environment)
		- [List active accounts](#List%20active%20accounts)
		- [Switch account](#Switch%20account)

## 🖥CLI🖥

### Install

[Install page](https://cloud.google.com/sdk/docs/install)

### Commands

#### Check version

```bash
gcloud version
```

#### Connect to gcloud project

```bash
gcloud init
```

Then follow the instructions

#### Get info on current environment

```bash
gcloud info
```

#### List active accounts

```bash
gcloud auth list
```

#### Switch account

```bash
gcloud config set account <account>
```

