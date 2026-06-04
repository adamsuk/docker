# 🏠 Docker Home Server

A comprehensive self-hosted home server running **35+ Docker services** for home automation, media streaming, file storage, and development tools.

## 📊 Overview

| Category | Services | Highlights |
|----------|----------|------------|
| 🏠 Home Automation | 7 | Home Assistant, ESPHome, Matter, MQTT |
| 🎬 Media | 8 | Plex, Sonarr, Kavita, Calibre |
| 💼 Productivity | 4 | Nextcloud, Obsidian, VS Code, Webtop |
| 🤖 AI/LLM | 2 | Ollama, Open WebUI |
| 🔧 Infrastructure | 14 | SWAG, Cloudflared, Portainer, Watchtower |

**Total: 35 services** running on a single Linux host with multiple storage drives.

## 🏗️ Architecture

- **Host**: Linux (Debian/Ubuntu-based), hostname `server`
- **User**: `server` (UID 1000, GID 1000)
- **Timezone**: Europe/London
- **Storage**: 3 drives mounted at `/media/small_boi`, `/media/big_boi`, `/media/full_boi`
- **Images**: Primarily LinuxServer.io for consistency

### Networking

- **SWAG** (port 443/80): Reverse proxy with Let's Encrypt SSL via Cloudflare DNS validation
- **Cloudflared**: Tunnel for secure external access without port forwarding
- **Host network mode**: Used by HA, ESPHome, Matter, MQTT, Music Assistant (required for mDNS/discovery)
- **Proxy network**: `swag_proxy` bridge network for reverse-proxied services

### Backup Strategy

- **Script**: `/home/server/scripts/sync-media-backup.sh`
- **Schedule**: Hourly via cron with `flock` locking to prevent overlaps
- **Target**: `/backup/media/` on external drive
- **Features**: 
  - `rsync -a --delete` with smart exclusions (trash, cache, etc.)
  - Disk space monitoring (minimum 10GB free)
  - Home Assistant notifications on failure
  - Persistent logging to `/home/server/logs/backup-sync.log`

## 📁 Directory Structure

```
/media/small_boi/docker/
├── homeassistant/config/     # HA configuration (automations, scenes, etc.)
├── nextcloud/{config,data}/  # Nextcloud data and config
├── swag/config/              # Reverse proxy configs
├── plexms/                   # Plex metadata + media mounts
├── [service]/docker-compose.yml
└── [service]/config/         # Per-service config (where applicable)
```

## 🚀 Getting Started

### Prerequisites

- Linux host with Docker and Docker Compose
- Multiple storage drives (optional, adjust paths in compose files)
- Domain name with Cloudflare (for SSL certificates)
- Basic understanding of Docker networking

### Quick Start

1. **Clone this repo**:
   ```bash
   git clone https://github.com/yourusername/docker.git
   cd docker
   ```

2. **Review each service**: Check the `AGENTS.md` in each service directory for purpose, access details, and dependencies.

3. **Configure environment variables**: Many services use `.env` files or inline environment variables. Review and update as needed.

4. **Start services**:
   ```bash
   cd [service]
   docker-compose up -d
   ```

5. **Set up backup**: Copy the backup script and configure cron:
   ```bash
   cp scripts/sync-media-backup.sh /home/server/scripts/
   chmod +x /home/server/scripts/sync-media-backup.sh
   # Add to crontab: 0 * * * * /home/server/scripts/sync-media-backup.sh
   ```

## 🔑 Key Services

### Home Automation
- **Home Assistant** (port 8123): Core automation hub with YAML-managed automations
- **ESPHome** (port 6052): ESP device firmware management
- **Matter** (port 5580): Matter/Thread protocol support
- **Mosquitto** (port 1883): MQTT broker for IoT communication
- **Node-RED** (port 1880): Visual automation flows
- **Music Assistant** (port 8095): Music library for HA
- **Eufy Security** (port 3000): Eufy camera bridge

### Media
- **Plex** (port 32400): Media streaming server
- **Sonarr** (port 8989): TV show management
- **Kavita** (port 5000): Ebook/comic reader
- **Calibre** (port 8080): Ebook management
- **Booklore** (port 6060): Modern ebook reader with MariaDB
- **Mylar** (port 8090): Comic book management

### Productivity
- **Nextcloud** (port 8200): File sync, contacts, calendar
- **Obsidian** (port 3020): Web-based note-taking
- **VS Code** (port 8443): code-server web IDE
- **Webtop** (port 3010): Full Linux desktop in browser

### AI/LLM
- **Ollama** (port 7869): Local LLM inference
- **Open WebUI** (port 8089): Chat interface for Ollama

### Infrastructure
- **SWAG** (port 443/80): Reverse proxy with Let's Encrypt
- **Cloudflared**: Cloudflare tunnel for external access
- **Portainer** (port 9000): Docker management UI
- **Watchtower**: Auto-updates (label-based, opt-in)
- **Homarr** (port 7575): Service dashboard
- **Glance** (port 8088): Monitoring dashboard

## 🔒 Security Notes

- All services use LinuxServer.io images with consistent PUID/PGID (1000/1000)
- SWAG provides automatic SSL certificates via Cloudflare DNS validation
- Cloudflared tunnel eliminates need for port forwarding
- Watchtower is label-based: only containers with `com.centurylinklabs.watchtower.enable=true` are auto-updated
- Backup script includes disk space monitoring and failure notifications

## 📝 Documentation

Each service directory contains an `AGENTS.md` file with:
- Purpose and functionality
- Key configuration files
- Access details (ports, URLs)
- Dependencies
- Important notes and gotchas

## 🤝 Contributing

This is a personal project, but feel free to:
- Open issues for questions or suggestions
- Fork and adapt for your own setup
- Submit PRs for improvements

## 📄 License

This project is for educational and personal use. Review individual service licenses as needed.

## 🙏 Acknowledgments

- [LinuxServer.io](https://www.linuxserver.io/) for excellent Docker images
- [Home Assistant](https://www.home-assistant.io/) for the amazing automation platform
- The self-hosted community for inspiration and support

---

**Note**: This is a living repository. Services are added, removed, and updated regularly. Check individual `docker-compose.yml` files for the most current configuration.
