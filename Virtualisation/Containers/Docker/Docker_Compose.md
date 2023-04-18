[[Docker_Commands]]

The docker compose file is a YAML file, it allows the user to use a file definition of a container instead of using commands.

##### List compose projects

```bash
docker compose ls
```

Options : 
- Also list stopped composes : ``-a``

##### Using docker compose

```bash
docker compose up
```

Options : 
- Run in backgroud : ``-d``
- Specify file : ``-f [file-name]``

##### Example : 

*docker-compose.yaml*

```YAML
services:
  webapp:
    image: examples/web
    command: sh -c "echo 'Hello world.'"
    ports:
      - "8000:8000"
    working_dir: /bin
    volumes:
      - "/data"
    environment:
      TEST: value1
      TEST2: value2
      TEST3: value3
```

##### Remove docker compose

```bash
docker compose down
```

Options :
- Also remove volumes : ``--volumes``

