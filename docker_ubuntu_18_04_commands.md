# Ubuntu 18.04 and Docker Command Reference

## System information

```bash
lsb_release -a
```

```text
Description: Ubuntu 18.04 LTS
Release: 18.04
Codename: bionic
```

## Install Docker prerequisites and packages

```bash
apt-get update
apt-get install openssh*
apt-get install apt-transport-https ca-certificates curl software-properties-common
apt install docker.io
service docker start
apt install docker-compose
```

## Check Docker and Compose versions

```bash
docker --version
docker-compose --version
docker compose version
```

## Remove Docker

```bash
apt purge docker.io
```

## Firewall

```bash
ufw disable
```

## List containers

```bash
docker ps -as
docker container ls -a
docker ps --format "table {{.ID}}\t{{.Names}}\t{{.Command}}"
```

## List container IDs and names

```bash
docker ps --format "table {{.ID}}\t{{.Names}}"
```

## Stop and remove containers

```bash
docker container stop $(docker container ls -aq)
docker container rm 25e2e4f797e5 90057d5e0dde
```

## Run and clean up containers

```bash
docker run -d --name webapp nginx:1.14-alpine
docker container prune

# Remove all images
docker image prune -a
```

## List and remove images

```bash
docker container ls -a
docker images
docker rmi yjjy0921/redhat7.2
docker image rm 75835a67d134 2a4cca5ac898
```

## Stop running containers

```bash
docker kill $(docker ps -q)
```

## Open a shell inside a container

```bash
docker exec -it 9b37998225b4 /bin/bash
```

## Docker Compose

```bash
docker-compose up -d
docker-compose down
```

## Operational notes

- Use `sudo` or a root shell where required.
- `ufw disable` turns off the host firewall.
- `docker container prune` and `docker image prune -a` can permanently delete unused Docker data.
