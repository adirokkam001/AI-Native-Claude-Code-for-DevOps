# Useful Commands – Day 3

## Build and inspect

```bash
docker build -t ops-plus:local .
docker image ls
docker image inspect ops-plus:local
```

## Container diagnostics

```bash
docker run -d --name ops-plus -p 8000:8000 ops-plus:local
docker ps
docker ps -a
docker logs ops-plus
docker inspect ops-plus
docker port ops-plus
docker stop ops-plus
docker rm ops-plus
```

## Compose

```bash
docker compose config
docker compose up -d --build
docker compose ps
docker compose logs -f
docker compose down
```

## Trivy

```bash
trivy --version
trivy config .
trivy image ops-plus:local
```

## Podman

```bash
podman build -t ops-plus:local .
podman images
podman run -d --name ops-plus -p 8000:8000 ops-plus:local
```

## Destructive cleanup warning
The instructor demonstrated commands that forcibly remove all containers and images. These can delete unrelated workloads and cached images. Never run broad cleanup commands such as `docker rm -f $(docker ps -aq)` or `docker rmi -f $(docker images -q)` on shared/production systems. Remove only identified resources you are authorized to delete.
