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

#### Create topic

```bash
gcloud pubsub topics create <topic-name>
```

#### Publish to topic

```bash
gcloud pubsub topics publish topic-groupe2 --message=<message>
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

#### Create scheduler job to send messages to pubsub

```bash
gcloud scheduler jobs create pubsub <job-name> --location=<location> --schedule="<cron>" --topic=<topic-name> --message-body="<message>"
```

#### Create secret

```bash
gcloud secrets create journal-intime-de-ylan-leterrier --replication-policy=automatic --data-file=<file>
```

#### Access secret

```bash
gcloud secrets versions access 1 --secret=<secret-name>
```

#### Give access to services account

```bash
gcloud secrets add-iam-policy-binding <secret-name> --member="serviceAccount:<service-account>" --role="roles/secretmanager.secretAccessor"
```
