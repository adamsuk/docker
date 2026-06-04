# Eufy Security

## Purpose
WebSocket bridge for Eufy security cameras and doorbells. Provides local access to Eufy devices for Home Assistant.

## Key Files
- `data/` - Bridge state and cache
- `.env` - Eufy credentials (not tracked)

## Access
- Port: 3000 (host network mode)
- Protocol: WebSocket

## Dependencies
- Home Assistant (Eufy integration)
- Eufy account credentials

## Important Notes
- Uses `network_mode: host` for local device discovery
- Credentials in `.env` file (EUFY_USERNAME, EUFY_PASSWORD)
- Provides local API to Eufy cameras without cloud dependency
- Used by HA's Eufy Security integration
