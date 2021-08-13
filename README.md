# docker-juicero

A wildly over-engineered set of tooling for doing development inside docker containers.

## What's Included?

`docker-juicero` includes the following tools:

* [Portainer CE](https://www.portainer.io/)
* [cAdvisor](https://github.com/google/cadvisor)
* [Grafana Loki](https://grafana.com/oss/loki/)
* [alertmanager](https://prometheus.io/docs/alerting/latest/alertmanager/)
* [prometheus](https://prometheus.io/)
* [Grafana](https://grafana.com/)

## Usage

### Install Loki Docker Driver

In order to support logging docker container output to Grafana Loki you'll need to install the loki docker driver. You can find more information on the Grafana Loki docker driver in the [loki documentation](https://grafana.com/docs/loki/latest/clients/docker-driver/).

```
$> docker plugin install grafana/loki-docker-driver:latest --alias loki --grant-all-permissions
```

### Run Docker

```
$> git clone https://github.com/easyas314159/docker-juicero.git
$> cd docker-juicero
$> docker compose up
```

## Configuration

`docker-juicero` uses [docker compose file environment variables](https://docs.docker.com/compose/environment-variables/). Documentation on the available configuration parameters can be found in the [`.env`](https://github.com/easyas314159/docker-juicero/blob/main/.env) file in this repository.

To customize your configuration (e.g. when you have port mapping conflicts, or you want to pin a service to a specific tag) make a copy of the `.env` file, make and save your desire changes, and run docker compose with the `--env-file` flag.

```
$> docker compose --env-file .env.custom up
```

Note: docker compose does not currently support the use of multiple `--env-file` flags. See issue [docker/compose#7847](https://github.com/docker/compose/issues/7847).
