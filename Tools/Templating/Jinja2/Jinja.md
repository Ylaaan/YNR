# Jinja templates

- [🎛Variables🎛](#%F0%9F%8E%9BVariables%F0%9F%8E%9B)
- [🔁For loops🔁](#%F0%9F%94%81For%20loops%F0%9F%94%81)
- [⛩Use Jinja in docker🐳](#%E2%9B%A9Use%20Jinja%20in%20docker%F0%9F%90%B3)
	- [Templates](#Templates)
	- [Variables](#Variables)
	- [Usage](#Usage)


[Official documentation](https://jinja.palletsprojects.com/en/3.0.x/)

Jinja allows you to generate text based files from templates.

It includes functionalities such as:
- Variables
- For loops...

It can be used very easily in Python with the `jinja2` library as well as the [jinja2-cli](https://github.com/mattrobenolt/jinja2-cli) package

## 🎛Variables🎛

In templates, variables follow the following scheme:
```jinja2
{{VARIABLE_NAME}}
```


## 🔁For loops🔁

```jinja2
{%- for <VAR> in <LIST> %}
	TEXT
{% endfor %}
```

## ⛩Use Jinja in docker🐳

[Original idea and source code](https://github.com/dinuta/jinja2docker) 

Build a docker image with this [Dockerfile](Dockerfile.md):

```dockerfile
FROM alpine:3.19.0

# Set env vars
ENV TEMPLATES_DIR /templates
ENV VARIABLES_DIR /variables


# Create folders
RUN mkdir $TEMPLATES_DIR
RUN mkdir $VARIABLES_DIR

RUN apk add --no-cache py3-pip

RUN pip3 install jinja2-cli[yaml,toml,xml,hjson,json5]==0.8.2 --break-system-packages

ENTRYPOINT ["jinja2"]
```

### Templates

You can simply place your Jinja templates in the template directory.

### Variables

You can create a `YAML` file in the variables directory such as this one:

```yaml
databases:
  mysql56:
    container_name: mysql
    restart: always
    image: mysql:latest
    environment:
      MYSQL_ROOT_PASSWORD: 'root'
      MYSQL_DATABASE: 'store'
    command: --default-authentication-plugin=mysql_native_password
    expose:
      - '3306'
    volumes:
      - ./data:/var/lib/mysql
      - ./mysqlcnf:/etc/mysql/conf.d/

apps:
  mysql56:
    environment:
      DatabaseType: 0
      DBPassword: password0
      DBName: store
      DBServerName: mysql
      DBUserName: root
      DBPort: 3306
```

You can see how theses variables could be used in the template below:

```jinja2
{%- set database=databases[environ('DATABASE')] -%}
{%- set app=apps[environ('DATABASE')] -%}

version: '3'
services:
  {{environ('DATABASE')}}:
    container_name: {{database.container_name}}
    restart: {{database.restart}}
    image: {{database.image}}
    environment:
        {% for item in database.environment %} {{ item | safe }}: '{{database.environment[item] }}'
        {% endfor %}

    command: {{database.command}}
    expose:
        - '{{database.expose[0]  | safe | trim}}'
    volumes:
        {%for item in database.volumes%} - {{item | trim}}
        {% endfor %}

  server1:
    container_name: server1
    image: docker.swf-artifactory.lab.com/home_company/server:{{environ('IMAGE')}}
    hostname: server1
    command: -w {{environ('DATABASE')}}:{{database.expose[0] | int | safe | trim}} --debug --before /init/before.sh --after /init/after.sh  --after "sudo /usr/sbin/sshd -D &"
    environment:
      LicenseFile: /license/license.xml
      appSharedDirectory: /shared
      DatabaseType: {{app.environment.DatabaseType}}
      DBName: {{app.environment.DBName}}
      DBServerName: {{app.environment.DBServerName}}
      DBUserName: {{app.environment.DBUserName}}
      DBPort: {{app.environment.DBPort}}
      DBPassword: {{app.environment.DBPassword}}
      DBVerify: 'true'
#    ports:
#      - '6443:6443'
#      - '8089:8089'
#      - "8800-8883:8800-8883"
#      - '22:22'
    expose:
      - '6443'
      - "5005-5025"
      - "22"
      - "8089"
      - "8850-8883"
```

### Usage

Once your template and variables set you can launch the generation with these commands:

```bash
docker run --rm \
-v $PWD/inputs/templates:/templates \
-v $PWD/inputs/variables:/variables \
-e DATABASE=mysql56 -e IMAGE=latest \
dinutac/jinja2docker:latest /templates/standalone.j2 /variables/variables.yml --format=yaml > docker-compose.yml
```

You can also use the `Json` format.