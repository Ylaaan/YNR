# Connect to remote via SSH

- [Private key generation](#Private%20key%20generation)
- [Private key storage](#Private%20key%20storage)
- [Before-script](#Before-script)
- [Usage in script](#Usage%20in%20script)

[Official source](https://docs.gitlab.com/ee/ci/ssh_keys/)
## Private key generation

You must first and foremost [generate a private key and configure it on the remote](../../../Services/SSH/SSH.md#setup-a-private-key-connection)

## Private key storage

1. Create a [CICD variable](./Gitlab_Pipeline#CI-Variables), it **must** be of type `file`.
2. Copy your **private** key in the value field.
3. Make sure the value field ends with a newline character. **It will not work otherwise**

## Before-script

Add the following `before-script:` block to your job :
```bash
before_script:
  ##
  ## Install ssh-agent if not already installed, it is required by Docker.
  ## (change apt-get to yum if you use an RPM-based image)
  ##
  - 'command -v ssh-agent >/dev/null || ( apt-get update -y && apt-get install openssh-client -y )'

  ##
  ## Run ssh-agent (inside the build environment)
  ##
  - eval $(ssh-agent -s)

  ##
  ## Give the right permissions, otherwise ssh-add will refuse to add files
  ## Add the SSH key stored in SSH_PRIVATE_KEY file type CI/CD variable to the agent store
  ##
  - chmod 400 "$SSH_PRIVATE_KEY"
  - ssh-add "$SSH_PRIVATE_KEY"

  ##
  ## Create the SSH directory and give it the right permissions
  ##
  - mkdir -p ~/.ssh
  - chmod 700 ~/.ssh

  ##
  ## Optionally, if you will be using any Git commands, set the user name and
  ## and email.
  ##
  # - git config --global user.email "user@example.com"
  # - git config --global user.name "User name"

```
## Usage in script

You can now execute `ssh` commands in your script block with the following scheme:
```bash
ssh <user>@<remote> "<command>"
```

You can also copy files with `scp`:
```bash
scp <source-file> <user>@<remote>:<destination>
```