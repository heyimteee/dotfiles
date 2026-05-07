# Backup & Restore

## Creating a Backup

```bash
dot backup
```

Creates a timestamped snapshot in `backup/YYYYmmDD_HHMMSS/`:

- `brew-formulae.txt` — All brew packages
- `brew-leaves.txt` — Top-level packages
- `brew-casks.txt` — GUI apps
- `npm-global.txt` — Global npm packages
- `pip-all.txt` — Pip packages
- `vscode-extensions.txt` — VS Code extensions

## Syncing to GitHub

```bash
dot sync
```

Commits and pushes all local changes.

## Restoring on New Machine

```bash
# Install from tracked manifests
chezmoi init --apply https://github.com/heyimteee/dotfiles.git
dot install all
```

## Schedule

| Frequency | Command |
|-----------|---------|
| Daily | `dot sync` |
| Weekly | `dot backup` |
| Monthly | Review `backup/latest/` |
