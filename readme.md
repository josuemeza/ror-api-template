# Rails API template with docker-compose

A base structure to create a Rails API with PostgreSQL.

## Requirements

- [Docker](https://www.docker.com/)
- [Docker-compose](https://docs.docker.com/compose/)

## Get started

### Create a Rails environment

Create the project 
```sh
$ docker-compose run --rm api rails new . --api --force --database=postgresql --skip-bundle
```

Build services
```sh
$ docker-compose build
```

### Set database environment

Set values on database.yml file.
```yml
username: [user on docker-compose]
password: [pass on docker-compose]
host: db
```

### Up services
Execute
```sh
$ docker-compose up -d
```

### Create, migrete and seed database

- Alternative 1
```sh
$ docker-compose run --rm api rails db:create
$ docker-compose run --rm api rails db:migrate
$ docker-compose run --rm api rails db:seed
```

- Alternative 2
```sh
$ docker-compose exec api bash
$ rails db:create
$ rails db:migrate
$ rails db:seed
```

## Logs
- To get log use:
```sh
$ tail -f log/development.log
```

## Simplify with makefile
To simplify the use, you can use a make commands like `make {command}`. All commands is described on next table.

| Command | Description |
|---------|-------------|
| new-project | Init a project creating and build. |
| new-database | Create, migrate and seed database. |
| database-migration | Make a database migration. |
| database-seed | Run seeds on database. |
| project-up | Up the project. |
| project-down | Down the project. |
| log-monitor | Show development logs. |
| clean-all | Remove all containers and images. |

## Author

Josue Meza Peña, contacto@josuemeza.com

## License

**Rails API template with docker-compose** is available under the MIT license. See the [LICENSE](LICENSE) file for more info.