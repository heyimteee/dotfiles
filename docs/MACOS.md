# macOS Notes

## Homebrew Path

Apple Silicon uses `/opt/homebrew`. Intel uses `/usr/local`. Handled automatically in zshrc.

## GUI Apps

```bash
dot install gui
```

Installs: Ghostty, MiddleClick, Nerd Fonts

## Services

```bash
apache-start    # Start Apache
php-restart     # Restart PHP
sql-start       # Start MySQL
web-start       # Start all web services
```

## Xcode Tools

```bash
xcode-select --install
```

## Rosetta (Apple Silicon)

```bash
softwareupdate --install-rosetta --agree-to-license
```
