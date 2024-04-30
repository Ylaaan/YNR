# Gcloud

- [🖥CLI🖥](#%F0%9F%96%A5CLI%F0%9F%96%A5)
	- [Install](#Install)
	- [General Commands](#General%20Commands)
		- [Check version](#Check%20version)
		- [Connect to gcloud project](#Connect%20to%20gcloud%20project)
		- [Get info on current environment](#Get%20info%20on%20current%20environment)
		- [List active accounts](#List%20active%20accounts)
		- [Switch account](#Switch%20account)
		- [Create topic](#Create%20topic)
	- [Pub/Sub Commands](#Pub/Sub%20Commands)
		- [Publish to topic](#Publish%20to%20topic)
		- [Upload to bucket](#Upload%20to%20bucket)
		- [Add viewing permissions on bucket for all users](#Add%20viewing%20permissions%20on%20bucket%20for%20all%20users)
		- [Create subscription](#Create%20subscription)
		- [Send notification from bucket to topic](#Send%20notification%20from%20bucket%20to%20topic)
		- [Pull answer from subscription](#Pull%20answer%20from%20subscription)
		- [Create scheduler job to send messages to pubsub](#Create%20scheduler%20job%20to%20send%20messages%20to%20pubsub)
	- [Secret Commands](#Secret%20Commands)
		- [Create secret](#Create%20secret)
		- [Access secret](#Access%20secret)
		- [Give access to services account](#Give%20access%20to%20services%20account)

## 🖥CLI🖥

### Install

[Install page](https://cloud.google.com/sdk/docs/install)

### General Commands

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

#### Create topic

```bash
gcloud pubsub topics create <topic-name>
```

### Pub/Sub Commands

#### Publish to topic

```bash
gcloud pubsub topics publish <topic-name> --message=<message>
```

#### Upload to bucket

```bash
gsutil cp <file> gs://<bucket-name>/<file-name>
```

#### Add viewing permissions on bucket for all users

```bash
gcloud storage buckets add-iam-policy-binding gs://<bucket-name> --member=allUsers --role=roles/storage.objectViewer
```

#### Create subscription

```bash
gcloud pubsub subscriptions create <subscription-name> --topic=<topic-name>
```

#### Send notification from bucket to topic

```bash
gcloud storage buckets notifications create gs://<bucket-name> --topic=<topic-name>
```

#### Pull answer from subscription

```bash
gcloud pubsub subscriptions pull <subscription-name> --limit 5 --auto-ack
```

#### Create scheduler job to send messages to Pub/Sub

```bash
gcloud scheduler jobs create pubsub <job-name> --location=<location> --schedule="<cron>" --topic=<topic-name> --message-body="<message>"
```

### Secret Commands
#### Create secret

```bash
gcloud secrets create <secrect-name> --replication-policy=automatic --data-file=<file>
```

#### Access secret

```bash
gcloud secrets versions access 1 --secret=<secret-name>
```

#### Give access to services account

```bash
gcloud secrets add-iam-policy-binding <secret-name> --member="serviceAccount:<service-account>" --role="roles/secretmanager.secretAccessor"
```
