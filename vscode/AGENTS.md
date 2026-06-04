# VS Code (code-server)

## Purpose
Web-based VS Code IDE. Full development environment accessible from browser.

## Key Files
- `/media/SmallSlave/docker/vscode/config` → `/config`
- `/media/SmallSlave/Users` → `/home` (user files)
- `/home/server/.ssh` → `/config/.ssh` (SSH keys)

## Access
- Port: 8443 (HTTPS)
- URL: https://server:8443
- Password: `password` (set in compose)

## Dependencies
- None (standalone)

## Important Notes
- SUDO_PASSWORD also set to `password`
- SSH keys mounted for git operations
- Full Linux development environment
- Can access host filesystem via mounts
