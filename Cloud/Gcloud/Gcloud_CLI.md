# Gcloud

## Install

[Install page](https://cloud.google.com/sdk/docs/install)

## 🌐General Commands🌐

### Check version

```bash
gcloud version
```

### Connect to gcloud project

```bash
gcloud init
```

Then follow the instructions

### Get info on current environment

```bash
gcloud info
```

### List active accounts

```bash
gcloud auth list
```

### Switch account

```bash
gcloud config set account <account>
```

### Create topic

```bash
gcloud pubsub topics create <topic-name>
```

## 📨Pub/Sub Commands📮

### Publish to topic

```bash
gcloud pubsub topics publish <topic-name> --message=<message>
```

### Upload to bucket

```bash
gsutil cp <file> gs://<bucket-name>/<file-name>
```

### Add viewing permissions on bucket for all users

```bash
gcloud storage buckets add-iam-policy-binding gs://<bucket-name> --member=allUsers --role=roles/storage.objectViewer
```

### Create subscription

```bash
gcloud pubsub subscriptions create <subscription-name> --topic=<topic-name>
```

### Send notification from bucket to topic

```bash
gcloud storage buckets notifications create gs://<bucket-name> --topic=<topic-name>
```

### Pull answer from subscription

```bash
gcloud pubsub subscriptions pull <subscription-name>
```

Options:

- Change the default limit of messages received: `--limit=<number-of-messages>`
- Enable auto-acknowledgment (You probably want this) : `--auto-ack`

### Create scheduler job to send messages to Pub/Sub

```bash
gcloud scheduler jobs create pubsub <job-name> --location=<location> --schedule="<cron>" --topic=<topic-name> --message-body="<message>"
```

## 🗝Secret Commands🔑
### Create secret

```bash
gcloud secrets create <secrect-name> --replication-policy=automatic --data-file=<file>
```

Notes:

You can echo a string directly into the secret by doing this:

```bash
echo "<secret-string>" | gcloud secrets create <secraft-name> --data-file=-
```

### Access secret

```bash
gcloud secrets versions access 1 --secret=<secret-name>
```

### Give access to serviceAccounts

```bash
gcloud secrets add-iam-policy-binding <secret-name> --member="serviceAccount:<service-account>" --role="roles/secretmanager.secretAccessor"
```

## 📄Instance Template📄

### Create template from cli:

[Official documentation]([https://cloud.google.com/sdk/gcloud/reference/compute/instance-templates/create#--description](https://cloud.google.com/sdk/gcloud/reference/compute/instance-templates/create#--description "https://cloud.google.com/sdk/gcloud/reference/compute/instance-templates/create#--description"))