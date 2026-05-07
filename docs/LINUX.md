# Linux Notes

## Supported Distros

| Distro | Package Manager |
|--------|----------------|
| Ubuntu/Debian | apt |
| Fedora | dnf |
| Arch | pacman |

## Chezmoi Install

```bash
sh -c "$(curl -fsLS get.chezmoi.io)"
```

## Default Shell

```bash
chsh -s $(which zsh)
```

## Fonts

```bash
mkdir -p ~/.local/share/fonts
cd ~/.local/share/fonts
wget https://github.com/ryanoasis/nerd-fonts/releases/download/v3.1.1/Monaspace.zip
unzip Monaspace.zip && rm Monaspace.zip
fc-cache -fv
```

## Powerlevel10k

Installed via git (not brew):
```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git \
  ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

## Known Issues

- `bat` may be `batcat` on Debian/Ubuntu
- `fd` may be `fdfind` on Debian/Ubuntu
- The `dot install` command shows Brewfiles on Linux; install manually
