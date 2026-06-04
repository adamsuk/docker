# Glance

## Purpose
Lightweight dashboard for monitoring services and system status.

## Key Files
- `config/` - Dashboard configuration (YAML)
- `assets/` - Custom assets (icons, images)
- `.env` - Environment variables (not tracked)

## Access
- Port: 8088
- URL: http://server:8088

## Dependencies
- Docker socket (for container widgets)

## Important Notes
- Docker socket mounted for container status
- Configuration via YAML files in `config/`
- Lightweight alternative to Homarr
- Supports various widgets (weather, RSS, etc.)
