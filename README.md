# Dotfiles

Cross-platform dotfiles managed with [Chezmoi](https://www.chezmoi.io/).

## Quick Start

```bash
sh -c "$(curl -fsLS get.chezmoi.io)"
chezmoi init --apply https://github.com/heyimteee/dotfiles.git
dot install core
```

## Commands

```bash
dot install core    # Essential tools
dot install dev     # Dev stack
dot install db      # Databases
dot install media   # Media tools
dot install monitor # Monitoring
dot install gui     # GUI apps (macOS)
dot install all     # Everything
dot backup          # Snapshot packages
dot sync            # Push to GitHub
dot doctor          # Check setup
```

## Structure

- `install/` — Package manifests (Brewfiles, npm, pip)
- `bin/dot` — Custom CLI
- `private_dot_config/nvim/` — Neovim config
- `docs/` — Documentation
