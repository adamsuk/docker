# OpenCode

## Purpose
SSH workspace for remote development. Provides SSH access to a containerized environment.

## Key Files
- `workspace/` - Project files
- `/home/server/.ssh/authorized_keys` - SSH keys (read-only)

## Access
- Port: 2222 (SSH)
- Connect: `ssh -p 2222 server@localhost`

## Dependencies
- SSH keys for authentication

## Important Notes
- Injects AI provider keys (OpenAI, Anthropic) via environment
- Workspace mounted at `/workspace`
- SSH keys mounted read-only
- API keys are placeholders (need to be set)
