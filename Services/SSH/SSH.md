# SSH

## 📡SSH command📡

```bash
ssh <username>@<hostname>
```

Options :

- Specify a private key : `-i <path-to-private-key>`

## 🔑Setup a private key connection🔑

### Generate a private key on your host

```bash
ssh-keygen
```

Options :

- Specify a encrypting protocol : `-t <protocol>`
- Specify key length in bytes : `-b <number-of-bytes>`

If you don't want a passphrase, leave the prompt blank.

### Copy the public key the the remote destination

#### ssh-copy-id

If available use the following method :

```bash
ssh-copy-id <username>@<hostname>
```

If asked for passphrase type it and press `ENTER`.

#### copy with SSH

If only ssh is available

```bash
cat ~/.ssh/id_rsa.pub | ssh <username>@<hostname> "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"
```

#### Copy manually

**On the host**, Copy the public key's content :

```bash
cat ~/.ssh/id_rsa.pub
```

**On the remote**, execute the following commands :

```bash
mkdir -p ~/.ssh
```

```bash
sudo chmod 700 ~/.ssh
sudo chmod 644 ~/.ssh/id_rsa.pub
sudo chmod 600 ~/.ssh/authorized_keys
sudo chmod 600 ~/.ssh/id_rsa
```

```bash
echo <public-key> >> ~/.ssh/authorized_keys
```

Make sure your home directory doesn't have more than 755 permissions (drwxr-xr-x).

## ⛔Disable password login (Optionnal but recommended)⛔

### Modifiy sshd config

Open the file :

```bash
sudo vim /etc/ssh/sshd_config
```

Change the field `PasswordAuthentication` from `yes` to `no`.

### Restart the SSH service

Depends on the OS.
