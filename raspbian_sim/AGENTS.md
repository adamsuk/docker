# Raspbian Simulator

## Purpose
Raspberry Pi OS emulation in Docker. Runs Raspbian in a container.

## Key Files
- None (uses container defaults)

## Access
- Ports: 2222 (SSH), 81 (HTTP), 443 (HTTPS)

## Dependencies
- Privileged mode for full system access

## Important Notes
- Uses `desktopcontainers/raspberrypi` image
- `privileged: true` for full system emulation
- Similar to minecraftpi but without Minecraft
- Experimental/educational setup
