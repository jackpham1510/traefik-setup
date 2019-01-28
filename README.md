# Traefik Setup

My traefik boilerplate

## Change mod acme.json

```bash
chmod 600 acme.json
```

## Generate encrypted password for Traefik dashboard

```bash
htpasswd -nb <username> <password>
```

Put its output in `traefik.toml` and `traefik.prod.toml`

```toml
...

[entryPoints.dashboard.auth.basic]
users = ["<username>:<encryped_password>"]

...
```

## Run

```bash
# Dev environment
docker-compose up -d -- build

# Production
docker-compose up -f docker-compose.prod.yml -d --build
```

## Shutdown

```bash
docker-compose down
```

## Traefik dashboard

* Dev: **traefik.localhost**
* Production: **traefik.phamdung.me**