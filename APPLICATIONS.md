# Available Applications

Complete list of applications available on the Positron system.

## AI & Development Tools

### Msty
- **Command:** `msty`
- **Description:** AI chat interface for conversations with various language models
- **Best for:** Quick AI assistance, code help, general questions
- **Documentation:** [docs](https://msty.app/docs)

### Msty Studio
- **Command:** `mstystudio`
- **Description:** Advanced AI development environment with enhanced features
- **Best for:** Complex AI workflows, development projects, extended sessions
- **Documentation:** [docs](https://msty.app/studio)

## Office & Productivity Suite

### LibreOffice
Complete office suite with full document editing capabilities:

- **Writer:** `libreoffice --writer` - Word processor
- **Calc:** `libreoffice --calc` - Spreadsheet application
- **Impress:** `libreoffice --impress` - Presentation software
- **Draw:** `libreoffice --draw` - Vector graphics and flowcharts
- **Base:** `libreoffice --base` - Database management
- **Math:** `libreoffice --math` - Formula editor
- **Documentation:** [docs](https://documentation.libreoffice.org/)

## Web & Communication

### Firefox
- **Command:** `firefox`
- **Description:** Full-featured web browser
- **Features:** Extensions support, bookmarks sync, privacy controls
- **Documentation:** [docs](https://support.mozilla.org/en-US/products/firefox)

## File Management & System Tools

### Dolphin
- **Command:** `dolphin`
- **Description:** Advanced file manager with dual-pane support
- **Features:** Network browsing, archive support, preview pane
- **Documentation:** [docs](https://docs.kde.org/trunk5/en/dolphin/dolphin/)

### Kate
- **Command:** `kate`
- **Description:** Advanced text editor with syntax highlighting
- **Best for:** Code editing, configuration files, markdown
- **Documentation:** [docs](https://docs.kde.org/trunk5/en/kate/kate/)

### Konsole
- **Command:** `konsole`
- **Description:** Terminal emulator with tabs and profiles
- **Features:** Multiple tabs, customizable profiles, split view
- **Documentation:** [docs](https://docs.kde.org/trunk5/en/konsole/konsole/)

### Okular
- **Command:** `okular`
- **Description:** Universal document viewer
- **Supports:** PDF, EPUB, images, DjVu, PostScript
- **Documentation:** [docs](https://docs.kde.org/trunk5/en/okular/okular/)

## Graphics & Media

### GIMP
- **Command:** `gimp`
- **Description:** GNU Image Manipulation Program
- **Best for:** Photo editing, digital art, image creation
- **Documentation:** [docs](https://docs.gimp.org/)

### VLC Media Player
- **Command:** `vlc`
- **Description:** Universal media player
- **Supports:** Most video/audio formats, streaming, DVD/Blu-ray
- **Documentation:** [docs](https://www.videolan.org/doc/)

### Gwenview
- **Command:** `gwenview`
- **Description:** Fast image viewer and basic editor
- **Features:** Slideshow, basic editing, RAW support
- **Documentation:** [docs](https://docs.kde.org/trunk5/en/gwenview/gwenview/)

## Development Tools

### Visual Studio Code
- **Command:** `code`
- **Description:** Modern code editor with extensions
- **Features:** IntelliSense, debugging, Git integration
- **Documentation:** [docs](https://code.visualstudio.com/docs)

### Git
- **Command:** `git`
- **Description:** Version control system
- **Includes:** Full Git suite with GUI tools
- **Documentation:** [docs](https://git-scm.com/doc)

## System Utilities

### KDE System Settings
- **Command:** `systemsettings5`
- **Description:** System configuration interface
- **Note:** FAMILY users have full access, FRIENDS users have limited access
- **Documentation:** [docs](https://docs.kde.org/trunk5/en/systemsettings/systemsettings/)

### Calculator
- **Command:** `kcalc`
- **Description:** Scientific calculator with multiple modes
- **Documentation:** [docs](https://docs.kde.org/trunk5/en/kcalc/kcalc/)

### Archive Manager
- **Command:** `ark`
- **Description:** Archive creation and extraction tool
- **Supports:** ZIP, TAR, RAR, 7Z, and many more formats
- **Documentation:** [docs](https://docs.kde.org/trunk5/en/ark/ark/)

## Quick Launch Examples

### AI Tools
```bash
# Launch Msty for AI chat
ssh -X -i username_ssh_key username@10.0.0.1 msty

# Launch Msty Studio for development
ssh -X -i username_ssh_key username@10.0.0.1 mstystudio
```

### Office Applications
```bash
# Launch LibreOffice Writer
ssh -X -i username_ssh_key username@10.0.0.1 libreoffice --writer

# Launch LibreOffice Calc
ssh -X -i username_ssh_key username@10.0.0.1 libreoffice --calc

# Launch LibreOffice Impress
ssh -X -i username_ssh_key username@10.0.0.1 libreoffice --impress
```

### System Tools
```bash
# Launch file manager
ssh -X -i username_ssh_key username@10.0.0.1 dolphin

# Launch text editor
ssh -X -i username_ssh_key username@10.0.0.1 kate

# Launch web browser
ssh -X -i username_ssh_key username@10.0.0.1 firefox

# Launch image editor
ssh -X -i username_ssh_key username@10.0.0.1 gimp
```

### Media Applications
```bash
# Launch VLC media player
ssh -X -i username_ssh_key username@10.0.0.1 vlc

# Launch image viewer
ssh -X -i username_ssh_key username@10.0.0.1 gwenview
```

## Performance Tips

### For Slow Connections
Add compression to any command:
```bash
ssh -XC -i username_ssh_key username@10.0.0.1 application_name
```

### For Graphics-Heavy Applications
Use trusted X11 forwarding if regular forwarding has issues:
```bash
ssh -Y -i username_ssh_key username@10.0.0.1 gimp
```

## Installation Notes

### FAMILY Users
- Can install additional software using `sudo apt install package_name`
- Have access to snap packages: `sudo snap install package_name`
- Can add PPAs and third-party repositories

### FRIENDS Users
- Cannot install new software
- Have access to all pre-installed applications
- Can request software installation by contacting admin

## Shared Resources

### AI Models (All Users)
- **Location:** `/opt/shared-models`
- **Access:** Read-only for FRIENDS, full access for FAMILY
- **Models:** Various LLMs optimized for different tasks

### Shared Documents (FAMILY Only)
- **Location:** `/shared`
- **Access:** FAMILY users can share files here
- **Purpose:** Collaboration between family members

---

*For the complete setup guide, return to the [main README](README.md)*