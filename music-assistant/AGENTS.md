# Music Assistant

## Purpose
Music library and streaming server for Home Assistant. Manages music collection and provides playback to media players.

## Key Files
- `data/` - Music Assistant database and cache

## Access
- Port: 8095 (host network mode)
- URL: http://server:8095

## Dependencies
- Home Assistant (integrates as a media provider)
- Music files on network storage

## Important Notes
- Uses `network_mode: host` for device discovery
- `SYS_ADMIN` and `DAC_READ_SEARCH` caps for SMB mounting
- `apparmor:unconfined` for container filesystem access
- Can mount SMB shares for music libraries
- LOG_LEVEL configurable (default: info)
