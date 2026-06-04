# Minecraft Pi

## Purpose
Raspberry Pi Minecraft server emulation. Runs Minecraft Pi edition in a container.

## Key Files
- None (uses container defaults)

## Access
- Ports: 2222 (SSH), 80 (HTTP), 4443 (HTTPS)

## Dependencies
- Privileged mode for full system access

## Important Notes
- Uses `desktopcontainers/raspberrypi` image
- `privileged: true` for full system emulation
- Port 4711 (Minecraft Pi API) is commented out
- Experimental/educational setup
