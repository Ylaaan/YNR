# DockerFile

## Table of contents

- [DockerFile](#dockerfile)
  - [Table of contents](#table-of-contents)
  - [🏗️Structure🏗️](#️structure️)
    - [Name](#name)
    - [Comments](#comments)
    - [Multiline](#multiline)
  - [🛂Instructions🛂](#instructions)
    - [Use a Docker image as a base](#use-a-docker-image-as-a-base)
    - [Copy files from host to image](#copy-files-from-host-to-image)
    - [Set environement variables](#set-environement-variables)
  - [🚫.dockerignore🚫](#dockerignore)
    - [.dockerignore Comments](#dockerignore-comments)
    - [Add a files to ignore](#add-a-files-to-ignore)
    - [Add an exeption to the rule too](#add-an-exeption-to-the-rule-too)

[Docker_Commands](Docker_Commands.md#docker-commands)

## 🏗️Structure🏗️

### Name

The file must be named "**Dockerfile**".

### Comments

```dockerfile
#This is a comment
```

This is not included in the execution of the file.

### Multi line

You can use the backslash to make multi line commands.

```dockerfile
RUN echo this is \
a multiline command
```

## 🛂Instructions🛂

### Use a Docker image as a base

**Be careful :** This must be used at the beginning of the file!

```dockerfile
FROM <image>:<tag>
```

Options :

- Specify a platform : ``--platform=``

### Copy files from host to image

```dockerfile
COPY <source> <destination>
```

### Set environement variables

```dockerfile
ENV <variable>=<value>
```

Environment variables are supported by the following list of instructions in the `Dockerfile`:

- `ADD`
- `COPY`
- `ENV`
- `EXPOSE`
- `FROM`
- `LABEL`
- `STOPSIGNAL`
- `USER`
- `VOLUME`
- `WORKDIR`

## 🚫.dockerignore🚫

Similarly to  .gitignore files, a "**.dockerignore**" file can be created. This comments allows file to be ignored by docker even if they are in the Dockerfiles, context.

### .dockerignore Comments

```dockerignore
# This is still a comment
```

### Add a files to ignore

```dockertignore
*/temp*
*/*/temp*
```

### Add an exeption to the rule too

```dockerignore
!<file-name>
```
