# Windows Setup with Winget and PowerShell

This repository automates the setup of a fresh Windows machine using Winget, PowerShell, and optional configuration files. It is designed to quickly install applications, restore terminal and editor settings, and configure developer tools.

---

## Repository Structure

```
.
├── setup.ps1                     # Main setup script
├── winget-packages.json          # Exported list of Winget packages
├── manual-apps.md                # Manual install list for apps not on Winget
├── powershell/
│   └── profile.ps1               # PowerShell configuration
├── themes/                       # (Optional) Terminal or editor themes
└── fonts/                        # (Optional) Custom fonts (e.g., Fira Code)
```

---

## Purpose

- Reinstall preferred software using Winget
- Restore PowerShell profile and CLI environment
- Document and guide manual app installs
- Optionally restore terminal themes and fonts

---

## Setup Workflow

### 1. Ensure Winget is Available

[WinGet](https://learn.microsoft.com/en-us/windows/package-manager/winget/) is included in the Windows App Installer.

To verify it's installed, run:

```powershell
winget --version
```

If the command is not recognized, install [App Installer from the Microsoft Store](https://apps.microsoft.com/store/detail/app-installer/9NBLGGH4NNS1).

(Source: [Microsoft Learn](https://learn.microsoft.com/en-us/windows/package-manager/winget/))

---

### 2. Clone this Repository

```powershell
git clone https://github.com/tinysilverfish/windows-setup.git
cd windows-setup
```

---

### 3. Run Setup Script

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force
./setup.ps1
```

This will:
- Update Winget sources
- Install apps from `winget-packages.json`
- Provide instructions for manual installs
- Optionally copy your PowerShell profile

---

### 4. Install Manual Apps

See `manual-apps.md` for download links and notes for tools not available via Winget.

---

### 5. Update Installed Apps

To regenerate your Winget export file:

```powershell
winget export -o winget-packages.json --accept-source-agreements
```

Commit and push changes to keep the repo updated.

---

## Future Improvements

- Automate font installation (e.g., Fira Code)
- Sync Windows Terminal or VS Code settings
- Add Scoop support for niche software
