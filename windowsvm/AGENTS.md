# Windows VM

## Purpose
Windows virtual machine running in Docker via KVM.

## Key Files
- `vagrant/` - Vagrant configuration
- `Dockerfile` - Custom KVM container

## Access
- Port: 3389 (RDP)
- Connect via RDP client

## Dependencies
- KVM support on host (`/dev/kvm`)
- TUN device (`/dev/net/tun`)

## Important Notes
- Uses custom `ubuntukvm` image (built from Dockerfile)
- `privileged: true` for KVM access
- Exposes `/dev/kvm` and `/dev/net/tun`
- CAP_ADD: NET_ADMIN, SYS_ADMIN
- Experimental setup for running Windows in Docker
