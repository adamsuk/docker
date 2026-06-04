# Obsidian

## Purpose
Web-based Obsidian vault viewer. Access markdown notes from any browser.

## Key Files
- `config/` - Obsidian application config
- `vaults/` - Obsidian vault files (markdown)

## Access
- Port: 3020 (web UI), 3021 (HTTPS)
- URL: http://server:3020

## Dependencies
- None (standalone)

## Important Notes
- Watchtower enabled for auto-updates
- `shm_size: 1gb` for browser performance
- SWAG proxy network is commented out (direct access only)
- Vaults stored in `./vaults` directory
