# Webtop

## Purpose
Full Linux desktop environment accessible via web browser. Like a remote desktop.

## Key Files
- `config/` - Desktop configuration and user data

## Access
- Port: 3010 (web UI), 3011 (HTTPS)
- URL: http://server:3010

## Mounts
- `./config` → `/config` (desktop config)
- `/media` → `/media` (all media drives)
- Docker socket mounted for container management

## Dependencies
- None (standalone)

## Important Notes
- `shm_size: 1gb` for browser performance
- Docker socket mounted (can manage containers from desktop)
- Full Linux desktop (KDE, XFCE, etc.)
- Can access all media drives
