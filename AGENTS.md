# Docker Home Server

## Overview
Self-hosted home server running 35 Docker services on a single machine (hostname: `server`). Primary purposes: home automation, media server, file storage, and development tools.

## Architecture
- **Host OS**: Linux (Debian/Ubuntu-based)
- **User**: `server` (UID 1000, GID 1000)
- **Timezone**: Europe/London
- **Storage**: Multiple drives mounted at `/media/small_boi`, `/media/big_boi`, `/media/full_boi`
- **Backup**: Hourly rsync to `/backup` via `/home/server/scripts/sync-media-backup.sh` with flock locking

## Common Patterns
- Most images use LinuxServer.io (`lscr.io/linuxserver/`) for consistency
- PUID/PGID: 1000/1000 (server user)
- TZ: Europe/London
- Restart policy: `unless-stopped`
- Watchtower labels for auto-updates (opt-in per container)

## Networking
- **SWAG** (port 443/80): Reverse proxy with Let's Encrypt, Cloudflare DNS validation for `sradams.co.uk`
- **Cloudflared**: Tunnel for external access
- **Host network mode**: Used by HA, ESPHome, Matter, MQTT, Music Assistant (required for mDNS/discovery)
- **Proxy network**: `swag_proxy` bridge network for reverse-proxied services

## Key Services by Category

### Home Automation
| Service | Port | Network | Notes |
|---------|------|---------|-------|
| homeassistant | 8123 | host | Core automation hub |
| esphome | 6052 | host | ESP device management |
| matter | 5580 | host | Matter protocol server |
| mosquitto | 1883 | host | MQTT broker |
| node-red | 1880 | host | Visual automation flows |
| music-assistant | 8095 | host | Music library for HA |
| eufy-security | 3000 | host | Eufy camera bridge |

### Media
| Service | Port | Notes |
|---------|------|-------|
| plexms | 32400 | Media streaming |
| sonarr | 8989 | TV show management |
| tautulli | 8181 | Plex monitoring |
| calibre | 8080 | Ebook management |
| kavita | 5000 | Ebook/comic reader |
| booklore | 6060 | Ebook reader with MariaDB |
| mylar | 8090 | Comic book management |
| ubooquity | 2202 | Ebook/comic server |

### Productivity
| Service | Port | Notes |
|---------|------|-------|
| nextcloud | 8200 | File sync, contacts, calendar |
| obsidian | 3020 | Note-taking (web-based) |
| vscode | 8443 | code-server web IDE |
| webtop | 3010 | Full Linux desktop in browser |

### AI/LLM
| Service | Port | Notes |
|---------|------|-------|
| ollama | 7869 | LLM inference |
| open-webui | 8089 | Chat UI for Ollama |

### Infrastructure
| Service | Port | Notes |
|---------|------|-------|
| swag | 443/80 | Reverse proxy + SSL |
| cloudflared | - | Cloudflare tunnel |
| portainer | 9000 | Docker management UI |
| watchtower | - | Auto-updates (label-based) |
| homarr | 7575 | Dashboard |
| glance | 8088 | Dashboard |

## Directory Structure
```
/media/small_boi/docker/
  ├── homeassistant/config/     # HA configuration (automations, scenes, etc.)
  ├── nextcloud/{config,data}/  # Nextcloud data
  ├── swag/config/              # Reverse proxy configs
  ├── plexms/                   # Plex metadata + media mounts
  ├── [service]/docker-compose.yml
  └── [service]/config/         # Per-service config (where applicable)
```

## Git Structure
- Only `docker-compose.yml` and `Dockerfile` files are tracked by default
- Config directories are NOT tracked (large, service-specific)
- Exception: `grott/grott/config/grott.ini` is tracked
- Home Assistant has a submodule: `homeassistant/homeassistant-`

## Backup Strategy
- Script: `/home/server/scripts/sync-media-backup.sh`
- Cron: `0 * * * *` (hourly) with flock at `/var/lock/backup-sync.lock`
- Syncs: `big_boi`, `small_boi`, `full_boi`, `server` → `/backup/media/`
- Uses `rsync -a --delete` with exclusions for trash, cache, etc.
- Sends HA notifications on failure

## Important Notes
- Entity area assignment in HA: entities may show in area UI via device assignment, but `area_entities()` template function requires entity-level `area_id` in registry
- Some services use `network_mode: host` which bypasses Docker networking (required for mDNS)
- Watchtower is label-based: only containers with `com.centurylinklabs.watchtower.enable=true` are auto-updated
- SWAG proxy configs are in `swag/config/nginx/proxy-confs/`
