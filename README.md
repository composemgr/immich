## 👋 Welcome to immich 🚀

High-performance self-hosted photo and video backup solution

## 📋 Description

High-performance self-hosted photo and video backup solution

## 🚀 Services

- **immich-server**: ghcr.io/immich-app/immich-server:release
- **immich-machine-learning**: ghcr.io/immich-app/immich-machine-learning:release
- **immich-db**: tensorchord/pgvecto-rs:pg14-v0.2.0

### Infrastructure Components

- **immich-redis**: Redis database


## 📦 Installation

### Option 1: Quick Install
```bash
curl -q -LSsf "https://raw.githubusercontent.com/composemgr/immich/main/docker-compose.yaml" -o compose.yml
```

### Option 2: Git Clone
```bash
git clone "https://github.com/composemgr/immich" ~/.local/srv/docker/immich
cd ~/.local/srv/docker/immich
docker compose up -d
```

### Option 3: Using composemgr
```bash
composemgr install immich
```

## 🔧 Configuration

### Environment Variables

```shell
TZ=America/New_York
DB_USER_NAME=immich
DB_USER_PASS=changeme_db_password
DB_CREATE_DATABASE_NAME=immich
```

See `docker-compose.yaml` for complete list of configurable options.

## 🌐 Access

- **Web Interface**: http://172.17.0.1:2283

## 📂 Volumes

- `./rootfs/data/immich` - Data storage
- `./rootfs/data/ml-cache` - Data storage
- `./rootfs/data/db/postgres/immich` - Data storage

## 🔐 Security

- Change all default passwords before deploying to production
- Use strong secrets for all authentication tokens
- Configure HTTPS using a reverse proxy (nginx, traefik, caddy)
- Regularly update Docker images for security patches
- Backup your data regularly

## 🔍 Logging

```shell
docker compose logs -f immich-server
```

## 🛠️ Management

```bash
# Start services
docker compose up -d

# Stop services
docker compose down

# Update to latest images
docker compose pull && docker compose up -d

# View logs
docker compose logs -f

# Restart services
docker compose restart
```

## 📋 Requirements

- Docker Engine 20.10+
- Docker Compose V2+

## 🤝 Author

🤖 casjay: [Github](https://github.com/casjay) 🤖  
🦄 composemgr: [Github](https://github.com/composemgr) 🦄
