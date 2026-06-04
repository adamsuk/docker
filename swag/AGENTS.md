# SWAG (Secure Web Application Gateway)

## Purpose
Reverse proxy with automatic Let's Encrypt SSL certificates via Cloudflare DNS validation.

## Key Files
- `config/nginx/proxy-confs/` - Proxy configurations for each service
- `config/nginx/site-confs/` - Site configurations
- `config/letsencrypt/` - SSL certificates

## Access
- Port 443 (HTTPS), 80 (HTTP redirect)
- Domain: sradams.co.uk
- Subdomains: homeassistant.sradams.co.uk

## Dependencies
- Cloudflare account for DNS validation
- Services on `swag_proxy` network

## Important Notes
- Uses Cloudflare DNS plugin for certificate validation
- `ONLY_SUBDOMAINS=true` - only proxies configured subdomains
- Services must be on the `proxy` network (or `swag_proxy` external network)
- Proxy configs auto-generated for common apps, custom ones in `proxy-confs/`
