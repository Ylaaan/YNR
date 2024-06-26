# Docker Compose

[Docker Commands](Docker_Commands.md#docker-commands)

The docker compose file is a YAML file, it allows the user to use a file definition of a container instead of using commands.

## Commands

### List compose projects

```bash
docker compose ls
```

Options:

- Also list stopped composes: ``-a``

### Build image from docker compose

```bash
docker compose build
```

Options:

- Run without cache:`--no-cache`

### Bring compose up

```bash
docker compose up
```

Options:

- Run in background: ``-d``
- Specify file: ``-f <file-name>``
- Specify `.env` file: `--env-file=<file-name>`

### Bring compose down

```bash
docker compose down
```

Options:

- Specify `.env` file: `--env-file=<file-name>`
- Also remove volumes: ``--volumes``

### List containers running from compose

```bash
docker compose ps
```

### Get logs from compose containers

```bash
docker compose logs <log-options>
```

Options:

- Follow logs: `-f` or `--follow`
- Get last n lines: `--tail <number-of-lines>`
- Add timestamps: `--timestamps`
## 📚Syntax 📚

### Networks

If nothing is specified, docker compose will create it's own network.

You can specifiy you own network in the docker compose, it can either be an already existing one, or be created inside the docker compose.
If that is the case, the network will be removed when you bring the compose down.

```yaml
networks:
  network:
    driver: bridge
    name: networkName
    external: true
```
