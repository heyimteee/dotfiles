# Windows WSL Notes

## Setup

```powershell
# In PowerShell as Admin
wsl --install -d Ubuntu
```

Then follow the Linux setup guide.

## Windows Terminal

Recommended terminal. Install from Microsoft Store.

## File Access

```bash
# Windows C: drive
ls /mnt/c/Users/YourName/Documents
```

## VS Code Integration

```bash
code .
```

Opens VS Code on Windows connected to WSL.

## Docker

Docker Desktop integrates with WSL automatically.

## Git Credentials

```bash
git config --global credential.helper "/mnt/c/Program\ Files/Git/mingw64/bin/git-credential-manager.exe"
```
