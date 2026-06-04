# Cloudflared

## Purpose
Cloudflare Tunnel for external access to internal services without opening ports.

## Key Files
- `tunnel/` - Tunnel configuration and credentials
- `.env` - Contains `TUNNEL_TOKEN` (not tracked in git)

## Access
- No direct port (uses Cloudflare network)
- Configured routes in Cloudflare dashboard

## Dependencies
- Cloudflare account with tunnel configured
- Tunnel token in `.env` file

## Important Notes
- Uses `network_mode: host`
- Runs `tunnel run` command with token from environment
- More secure than port forwarding (no inbound ports needed)
