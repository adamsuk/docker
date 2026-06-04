# Plex Media Server

## Purpose
Media streaming server. Organizes and streams movies, TV shows, music, and photos to clients.

## Key Files
- `docker.env` - Environment variables (PLEX_CLAIM, etc., not tracked)
- `/media/small_boi/docker/plexms/` - Plex metadata and config

## Access
- Port: 32400 (host network mode)
- URL: http://server:32400 or https://app.plex.tv

## Media Mounts
- `/media/big_boi/Movies` → `/movies`
- `/media/big_boi/Music` → `/music`
- `/media/big_boi/Photos` → `/photos`
- `/media/big_boi/TV` → `/TV1`
- `/media/full_boi/TV` → `/TV2`
- `/media/small_boi/Users` → `/user_data`

## Dependencies
- Media files on big_boi and full_boi drives

## Important Notes
- Uses `network_mode: host` for DLNA/discovery
- Watchtower enabled for auto-updates
- PLEX_CLAIM token needed for initial setup
- Library paths map to multiple drives
