# Immich

Immich is a high-performance, self-hosted photo and video management solution with automatic backup capabilities. It provides a modern mobile and web interface similar to Google Photos but with complete control over your data.

## Features

- **Mobile Auto Backup**: Automatic photo/video backup from iOS and Android
- **Timeline View**: Browse photos by date with smooth scrolling
- **AI-Powered Search**: Face recognition, object detection, and smart search
- **Sharing**: Share albums with family and friends
- **Maps**: View photos on a map based on GPS data
- **Live Photos**: Support for iOS Live Photos and Android Motion Photos
- **Raw Format**: Support for RAW image formats
- **Multi-User**: Multiple user accounts with individual libraries
- **Hardware Acceleration**: GPU transcoding for video and machine learning

## Installation

### Option 1: Quick Install
```bash
curl -q -LSsf "https://raw.githubusercontent.com/composemgr/immich/main/docker-compose.yaml" | docker compose -f - up -d
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

## Configuration

### Environment Variables

**Database:**
- `DB_USER_NAME`: Database username (default: immich)
- `DB_USER_PASS`: Database password (default: changeme_db_password)
- `DB_CREATE_DATABASE_NAME`: Database name (default: immich)

### Hardware Acceleration

**NVIDIA GPU (Video Transcoding):**
```yaml
immich-server:
  runtime: nvidia
  environment:
    - NVIDIA_VISIBLE_DEVICES=all
```

**Intel QuickSync:**
```yaml
immich-server:
  devices:
    - /dev/dri:/dev/dri
```

### Ports

- `2283`: Web interface and API

## Initial Setup

1. Access Immich at `http://localhost:2283`
2. Create administrator account
3. Download mobile app (iOS/Android)
4. Sign in to mobile app with server URL
5. Enable automatic backup in mobile app settings
6. Configure storage settings and quotas
7. Set up machine learning features (face recognition, object detection)

## Mobile Apps

- **iOS**: Available on App Store
- **Android**: Available on Google Play and F-Droid

Configure the server URL in the app: `http://your-server-ip:2283`

## Security Recommendations

- **Strong Passwords**: Use strong passwords for all accounts
- **Reverse Proxy**: Use HTTPS with reverse proxy (nginx, Traefik)
- **Backups**: Regular backups of database and photo storage
- **Network Security**: Restrict access with firewall rules
- **Updates**: Keep Immich updated for security patches
- **API Keys**: Protect API keys if using external integrations

## Backup

Critical directories to backup:
- `./rootfs/db/postgres/immich`: Database with metadata and user data
- `./rootfs/data/immich`: All uploaded photos and videos
- `./rootfs/data/ml-cache`: Machine learning models (optional, can be re-downloaded)

## Storage Management

### Monitoring Storage
Use the admin dashboard to monitor storage usage per user.

### External Storage
Mount external drives for photo storage:
```yaml
volumes:
  - /path/to/external/drive:/usr/src/app/upload
```

## Troubleshooting

### Mobile App Connection Issues
- Verify server URL is correct
- Check firewall allows port 2283
- Ensure server is accessible from mobile network

### Face Recognition Not Working
- Allow time for ML models to download
- Check immich-machine-learning container logs
- Verify sufficient CPU/RAM for ML processing

### Upload Failures
- Check disk space availability
- Review immich-server logs
- Verify file permissions on upload directory

### Database Connection Errors
- Verify immich-db container is running
- Check database credentials
- Review PostgreSQL logs

## Performance Optimization

- **Storage**: Use SSD for database and thumbnails
- **RAM**: Allocate sufficient RAM for ML container (4GB+ recommended)
- **GPU**: Enable hardware acceleration for faster processing
- **Network**: Use wired connection for initial bulk uploads

## Documentation

- Official Documentation: https://immich.app/docs/overview/introduction
- GitHub: https://github.com/immich-app/immich
- Discord Community: https://discord.immich.app/

## License

Immich is licensed under the GNU AGPL v3.
