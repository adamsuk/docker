# Puppet

## Purpose
Configuration management system. Manages infrastructure as code.

## Key Files
- `puppetserver-code/` - Puppet modules and manifests
- `puppetserver-config/` - Puppet configuration
- `puppetserver-data/` - Puppet server data
- `puppetdb/` - PuppetDB data
- `puppetdb-postgres/` - PostgreSQL data for PuppetDB

## Services
- `puppet` - Puppet server (port 8140)
- `puppetdb` - PuppetDB (ports 8080, 8081)
- `postgres` - PostgreSQL for PuppetDB

## Access
- Port: 8140 (Puppet server)
- Hostname: server

## Dependencies
- PostgreSQL 9.6 (included)
- PuppetDB (included)

## Important Notes
- Multi-container setup (server + DB + PuppetDB)
- DNS_ALT_NAMES must be set before first start
- CA_ALLOW_SUBJECT_ALT_NAMES=true for multiple hostnames
- Experimental/learning setup
