# Ubuntu VNC

## Purpose
Web-based Ubuntu desktop via VNC. Access Ubuntu desktop from browser.

## Key Files
- `/media/SmallSlave/docker/ubuntu_vnc/config` → `/dev/shm` (shared memory)

## Access
- Port: 6080
- URL: http://server:6080

## Dependencies
- None (standalone)

## Important Notes
- Uses `dorowu/ubuntu-desktop-lxde-vnc:focal` image
- LXDE desktop environment
- Based on Ubuntu Focal (20.04)
- Lightweight alternative to webtop
