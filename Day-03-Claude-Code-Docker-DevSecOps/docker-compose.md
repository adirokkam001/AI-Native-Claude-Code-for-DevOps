# Docker Compose – Production-Oriented Configuration

## What was demonstrated
Claude generated a Compose file with a service definition, image/build settings, health check, dedicated network, CPU/memory limits, labels, restart policy, and port mapping.

## Common commands

```bash
docker compose config
docker compose up -d --build
docker compose ps
docker compose logs -f
docker compose down
```

Review volume behavior and data retention before cleanup commands.

## Illustrative template
Adjust image, context, port, health endpoint, and limits to your application.

```yaml
services:
  app:
    build:
      context: .
      dockerfile: Dockerfile
    image: ops-plus:local
    container_name: ops-plus
    ports:
      - "8000:8000"
    restart: unless-stopped
    read_only: true
    security_opt:
      - no-new-privileges:true
    cap_drop:
      - ALL
    networks:
      - app-network
    deploy:
      resources:
        limits:
          cpus: "1.0"
          memory: 512M
    healthcheck:
      test: ["CMD", "python", "-c", "import urllib.request; urllib.request.urlopen('http://127.0.0.1:8000/health')"]
      interval: 30s
      timeout: 5s
      retries: 3
      start_period: 10s
    labels:
      app: ops-plus
      environment: local

networks:
  app-network:
    driver: bridge
```

**Important:** This is an illustrative template, not a guaranteed copy-and-run configuration. Distroless images may not contain Python, a shell, or utilities used by a health check. Use an application-supported health-check mechanism or validate the design separately. Resource-limit behavior can depend on the Compose implementation/runtime.
