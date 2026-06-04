# ABCDesktop.io

## Purpose
Virtual desktop infrastructure (VDI). Provides browser-based desktop environments.

## Key Files
- None (stateless containers)

## Access
- Port: 80 (HTTP), 444 (HTTPS)
- URL: http://server

## Services
- `pyos` - Python orchestration server
- `nginx` - Web frontend
- `memcached` - Session cache
- `mongodb` - Database
- `speedtest` - Network speed test app

## Dependencies
- Docker socket (for container orchestration)

## Important Notes
- Uses two networks: `netuser` (external) and `netback` (internal)
- Docker socket mounted for dynamic container creation
- Experimental/educational setup
- Each user gets their own containerized desktop
