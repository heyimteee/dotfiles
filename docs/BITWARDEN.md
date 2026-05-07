# Bitwarden Secret Management

## Overview

Secrets are managed via Bitwarden and injected at apply-time. **Never commit secrets to git.**

## Setup

```bash
# Install Bitwarden CLI
brew install bitwarden-cli  # macOS

# Login
bw login your@email.com

# Unlock vault
export BW_SESSION=$(bw unlock --raw)

# Apply dotfiles
chezmoi apply
```

## How It Works

Templates in git:
```zsh
export GITHUB_TOKEN="{{ bitwarden "github-token" "password" }}"
```

Generated on machine:
```zsh
export GITHUB_TOKEN="ghp_xxxxxxxxxxxx"
```

## Required Items

| Item | Field | Used In |
|------|-------|---------|
| `github-token` | `password` | Git config |
| `git-config` | `email`, `name` | Git config |

## Without Bitwarden

Set `bitwarden = false` during `chezmoi init` or manually add secrets to `~/.zshenv.local` (gitignored).
