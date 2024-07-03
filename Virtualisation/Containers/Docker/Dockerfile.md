# Dockerfile

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

### Add an exception to the rule too

```dockerignore
!<file-name>
```

## Multi-staging

Multi-staging is when you use multiple `FROM` statements in a Dockerfile. This can be very useful make your final docker image much smaller.

You can set a `as <name>` parameter at the end of the `FROM` statement to set a name for your stage.

To copy file from one stage to the other simply use the following statement:

```dockerfile
COPY --from=<stage-name> <path-in-specified-stage> <path-in-new-stage>
```

Example:

```Dockerfile
FROM node:latest AS build
RUN mkdir -p /srv/app
WORKDIR /srv/app/
COPY package.json package-lock.json server.js /srv/app/
RUN npm install

FROM build AS clean
WORKDIR /srv/app
RUN npm ci

FROM alpine:3.19 AS final
RUN apk --no-cache add nodejs
WORKDIR /srv/app
COPY --from=clean /srv/app ./
ENTRYPOINT ["node","server.js"]
```

This images is approximatively 88.5mb while the original image without multi-staging is 1.3Gb.

Dockerfile before multi-staging:

```dockerfile
FROM node:latest 
WORKDIR /srv/app/ 
COPY . /srv/app 
RUN npm install 
EXPOSE 4000 
ENTRYPOINT ["npm","start"]
```