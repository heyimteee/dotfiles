# Tristan's Dotfiles

> Cross-platform dotfiles managed with [Chezmoi](https://www.chezmoi.io/).
> Works on macOS, Linux, and WSL.

## Quick Start

```bash
# 1. Install chezmoi
sh -c "$(curl -fsLS get.chezmoi.io)"

# 2. Clone and apply dotfiles
chezmoi init --apply https://github.com/heyimteee/dotfiles.git

# 3. Install additional tools
dot install all
```

## What's Included

| Component | Tools |
|-----------|-------|
| **Shell** | Zsh, Oh My Zsh, Powerlevel10k |
| **Editor** | Neovim (fully configured) |
| **Terminal** | Tmux, Ghostty (macOS) |
| **CLI Tools** | eza, bat, fd, fzf, zoxide, ripgrep, lazygit |
| **Dev Stack** | Node (nvm), Python (uv), PHP (Composer), Go, Ruby |
| **Databases** | MySQL, PostgreSQL, MongoDB |
| **Monitoring** | Prometheus, Grafana |

## The `dot` CLI

```bash
dot install core       # Essential CLI tools (~20 packages)
dot install dev        # Development stack (~25 packages)
dot install db         # Databases (~6 packages)
dot install media      # Media tools (~6 packages)
dot install monitor    # Monitoring stack (~4 packages)
dot install gui        # GUI apps (macOS only, ~7 casks)
dot install all        # Everything except osdev
dot install util <pkg> # One-off package

dot backup             # Snapshot current packages
dot sync               # Push changes to GitHub
dot apply              # Apply dotfiles
dot update             # Pull latest and apply
dot doctor             # Check dependencies
```

## Secrets Management

API keys are managed via Bitwarden. Set `bitwarden = true` during `chezmoi init`.

```bash
bw login your@email.com
export BW_SESSION=$(bw unlock --raw)
chezmoi apply
```

See [docs/BITWARDEN.md](docs/BITWARDEN.md) for details.

## Directory Structure

```
.
├── .chezmoi.toml.tmpl          # Chezmoi config (prompts for name/email)
├── .chezmoiscripts/            # Setup scripts (auto-run on new machines)
│   ├── run_once_before_00-check-os.sh.tmpl
│   ├── run_once_before_01-install-deps.sh.tmpl
│   └── run_once_after_99-finalize.sh.tmpl
├── bin/
│   └── dot                     # Custom CLI
├── install/
│   ├── Brewfile.core           # Core tools
│   ├── Brewfile.dev            # Dev stack
│   ├── Brewfile.db             # Databases
│   ├── Brewfile.media          # Media tools
│   ├── Brewfile.monitor        # Monitoring
│   ├── Brewfile.gui            # GUI apps (macOS)
│   ├── npm-global.txt          # Global npm packages
│   └── requirements.txt        # Python packages
├── backup/                     # Machine snapshots (gitignored)
├── docs/
│   ├── SETUP.md                # New machine guide
│   ├── BACKUP.md               # Backup workflow
│   ├── BITWARDEN.md            # Secret management
│   ├── MACOS.md                # macOS notes
│   ├── LINUX.md                # Linux notes
│   └── WINDOWS-WSL.md          # WSL notes
├── private_dot_config/
│   └── nvim/                   # Neovim config
├── private_dot_ssh/
│   └── config                  # SSH config
├── dot_zshrc.tmpl              # Zsh config (cross-platform)
├── dot_p10k.zsh                # Powerlevel10k theme
├── dot_tmux.conf               # Tmux config
└── dot_gitconfig.tmpl          # Git config
```

## Documentation

- [docs/SETUP.md](docs/SETUP.md) — New machine step-by-step guide
- [docs/BACKUP.md](docs/BACKUP.md) — Backup & restore workflow
- [docs/BITWARDEN.md](docs/BITWARDEN.md) — Secret management
- [docs/MACOS.md](docs/MACOS.md) — macOS-specific notes
- [docs/LINUX.md](docs/LINUX.md) — Linux-specific notes
- [docs/WINDOWS-WSL.md](docs/WINDOWS-WSL.md) — WSL notes

## License

MIT
