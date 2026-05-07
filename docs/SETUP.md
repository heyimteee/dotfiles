# Setup Guide

> Step-by-step guide for setting up a new machine with these dotfiles.

## Prerequisites

- macOS, Linux, or WSL on Windows
- Internet connection
- GitHub account

## Step 1: Install Chezmoi

```bash
sh -c "$(curl -fsLS get.chezmoi.io)"
```

## Step 2: Initialize Dotfiles

```bash
chezmoi init --apply https://github.com/heyimteee/dotfiles.git
```

You'll be prompted for:
- Your name
- Your email

## Step 3: Restart Terminal

```bash
exec zsh
```

## Step 4: Configure Powerlevel10k (First Time)

```bash
p10k configure
```

## Step 5: Install Tools

```bash
# Essential only
dot install core

# Or everything
dot install all
```

## What's Installed

**Core:** zsh, tmux, git, fzf, eza, bat, fd, ripgrep, zoxide, lazygit

**Dev:** Node (nvm), Python (uv), PHP (Composer), Go, Ruby

**DB:** MySQL, PostgreSQL, MongoDB

**Media:** ffmpeg, imagemagick

**Monitor:** Prometheus, Grafana

**GUI (macOS):** Ghostty, Nerd Fonts

## Next Steps

- Run `dot doctor` to verify
- Read [BACKUP.md](BACKUP.md) for backup workflow
- Read [BITWARDEN.md](BITWARDEN.md) for secrets
