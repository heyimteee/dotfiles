# AGENTS.md

## Architecture

- **chezmoi-managed dotfiles.** All config files are chezmoi sources. The `dot_` prefix maps to `~/.` and `private_dot_config/` maps to `~/.config/`. Templates use Go template syntax (`{{ .chezmoi.os }}`), not shell.
- **The `dot` CLI** (`bin/dot`) is the primary local tool. Use it instead of raw chezmoi commands after initial setup.
- **Cross-platform conditionals** in templates: `{{ if eq .chezmoi.os "darwin" }}` for macOS, `linux` for Linux. Template data (name, email, bitwarden bool) comes from `.chezmoi.toml.tmpl`.
- **Brewfiles are macOS-only.** `dot install <group>` on Linux prints a warning; the Brewfiles are reference-only there.

## Commands

```bash
# All workflow goes through `dot`:
dot install core|dev|db|media|monitor|gui|all    # Install packages (macOS: brew bundle)
dot install util <pkg>                            # Install a single package
dot backup                                        # Snapshot current packages to backup/
dot sync                                          # chezmoi re-add + apply + git commit + push
dot apply                                         # chezmoi apply
dot update                                        # chezmoi update
dot doctor                                        # Check core CLI tools exist
```

## Key gotchas

- **Never edit deployed files directly** (e.g. `~/.zshrc`). Edit the source in the repo and run `dot apply` or `chezmoi apply`.
- **`.chezmoiignore` excludes `bin/`, `install/`, `docs/`, `README.md`** from deployment — these are repo-only infrastructure, not copied to `$HOME`.
- **`dot sync` does a blind `chezmoi re-add`** (adds all managed files) then `git add -A` (adds everything). Be careful about what's unstaged in the repo when running it.
- **No CI, no tests, no build system.** This repo is purely dotfile configuration.
- **Bitwarden secrets** are gated behind the `bitwarden` template bool (set during `chezmoi init`). If bitwarden is false, secrets are skipped silently.

## File roles

| Path | Purpose |
|---|---|
| `bin/dot` | Local CLI entrypoint |
| `install/Brewfile.*` | macOS package groups (brew bundle expects these) |
| `.chezmoiscripts/run_once_before_*` | Pre-apply OS detection + dependency install |
| `.chezmoiscripts/run_once_after_*` | Post-apply: zsh, oh-my-zsh, powerlevel10k, nvm |
| `dot_zshrc.tmpl` | Main zsh config with conditionals |
| `dot_gitconfig.tmpl` | Git user identity (templated from `.chezmoi.toml.tmpl`) |
| `dot_tmux.conf` | Tmux config with tpm plugin manager |
| `private_dot_config/nvim/` | Full Neovim config (LazyVim-based) |
| `backup/` | Machine snapshots (gitignored except README) |

## Neovim config

The Neovim config under `private_dot_config/nvim/` is LazyVim-based. Plugin specs live in `lua/plugins/` organized by category (ui, coding, editor, lang, tools). Key directories:
- `lua/config/` — core options, keymaps, autocmds
- `lua/utils/` — shared utilities
- Plugin READMEs exist per category.
