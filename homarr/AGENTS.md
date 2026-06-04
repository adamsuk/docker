# Homarr

## Purpose
Modern dashboard for organizing and accessing all self-hosted services.

## Key Files
- `homarr/appdata/` - Dashboard configuration and layouts

## Access
- Port: 7575
- URL: http://server:7575

## Dependencies
- Docker socket (optional, for container widgets)

## Important Notes
- Docker socket mounted for container status widgets
- SECRET_ENCRYPTION_KEY set in compose (for credentials)
- Restart policy is commented out (not auto-restarting)
- Visual dashboard with drag-and-drop widgets
