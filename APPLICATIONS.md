# Available Applications

Complete list of applications available on the Positron system.

## AI & Development Tools

### Msty
- **Command:** `msty`
- **Description:** AI chat interface for conversations with various language models
- **Best for:** Quick AI assistance, code help, general questions
- **Documentation:** [docs](https://msty.app/docs)


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

## Web Browsers

### Firefox
- **Command:** `firefox`
- **Description:** Full-featured web browser
- **Features:** Extensions support, bookmarks sync, privacy controls
- **Documentation:** [docs](https://support.mozilla.org/en-US/products/firefox)

### Brave Browser
- **Command:** `brave-browser`
- **Description:** Privacy-focused web browser with built-in ad blocking
- **Features:** Enhanced privacy, crypto wallet, tor browsing
- **Documentation:** [docs](https://support.brave.com/)


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

### Evince
- **Command:** `evince`
- **Description:** GNOME document viewer
- **Supports:** PDF, DjVu, TIFF, PostScript
- **Documentation:** [docs](https://wiki.gnome.org/Apps/Evince)

## Graphics & Media

### Shotwell
- **Command:** `shotwell`
- **Description:** Photo organizer and basic editor
- **Best for:** Photo management, basic editing, organizing image collections
- **Documentation:** [docs](https://wiki.gnome.org/Apps/Shotwell)

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

### EOG (Eye of GNOME)
- **Command:** `eog`
- **Description:** Simple and fast image viewer
- **Features:** Basic image viewing, slideshow, simple editing
- **Documentation:** [docs](https://wiki.gnome.org/Apps/EyeOfGnome)

### Rhythmbox
- **Command:** `rhythmbox`
- **Description:** Music player and library manager
- **Features:** Music library, playlists, radio, podcasts
- **Documentation:** [docs](https://wiki.gnome.org/Apps/Rhythmbox)

### Totem
- **Command:** `totem`
- **Description:** GNOME video player
- **Features:** Video playback, subtitle support, playlist
- **Documentation:** [docs](https://wiki.gnome.org/Apps/Videos)

## Development Tools

### Vim
- **Command:** `vim`
- **Description:** Powerful text editor for advanced users
- **Best for:** System administration, configuration files, programming
- **Documentation:** [docs](https://vimhelp.org/)

### GNOME Text Editor
- **Command:** `gnome-text-editor`
- **Description:** Modern, simple text editor
- **Best for:** Quick text editing, notes, simple coding
- **Documentation:** [docs](https://apps.gnome.org/TextEditor/)

### Git
- **Command:** `git`
- **Description:** Version control system
- **Includes:** Full Git suite with GUI tools
- **Documentation:** [docs](https://git-scm.com/doc)

### GitHub CLI
- **Command:** `gh`
- **Description:** GitHub's official command line tool
- **Features:** Repository management, issues, pull requests
- **Documentation:** [docs](https://cli.github.com/manual/)

### Node.js
- **Command:** `node`
- **Description:** JavaScript runtime environment
- **Features:** Server-side JavaScript, package ecosystem
- **Documentation:** [docs](https://nodejs.org/en/docs/)

### Python 3
- **Command:** `python3`
- **Description:** High-level programming language
- **Features:** Extensive library ecosystem, data science tools
- **Documentation:** [docs](https://docs.python.org/3/)


## System Utilities


### Calculator (KDE)
- **Command:** `kcalc`
- **Description:** Scientific calculator with multiple modes
- **Documentation:** [docs](https://docs.kde.org/trunk5/en/kcalc/kcalc/)

### Calculator (GNOME)
- **Command:** `gnome-calculator`
- **Description:** Simple calculator with advanced functions
- **Documentation:** [docs](https://wiki.gnome.org/Apps/Calculator)

### Archive Manager (KDE)
- **Command:** `ark`
- **Description:** Archive creation and extraction tool
- **Supports:** ZIP, TAR, RAR, 7Z, and many more formats
- **Documentation:** [docs](https://docs.kde.org/trunk5/en/ark/ark/)

### Archive Manager (GNOME)
- **Command:** `file-roller`
- **Description:** Archive manager for GNOME
- **Supports:** ZIP, TAR, RAR, 7Z, and many more formats
- **Documentation:** [docs](https://wiki.gnome.org/Apps/FileRoller)


## Quick Launch Examples

### AI Tools
```bash
# Launch Msty for AI chat
ssh -X -i username_ssh_key username@10.0.0.1 msty
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

# Launch photo organizer
ssh -X -i username_ssh_key username@10.0.0.1 shotwell

# Launch document viewer
ssh -X -i username_ssh_key username@10.0.0.1 okular
```

### Media Applications
```bash
# Launch VLC media player
ssh -X -i username_ssh_key username@10.0.0.1 vlc

# Launch image viewer (KDE)
ssh -X -i username_ssh_key username@10.0.0.1 gwenview

# Launch image viewer (GNOME)
ssh -X -i username_ssh_key username@10.0.0.1 eog

# Launch music player
ssh -X -i username_ssh_key username@10.0.0.1 rhythmbox

# Launch video player
ssh -X -i username_ssh_key username@10.0.0.1 totem
```

### Web Browsers
```bash
# Launch alternative browser
ssh -X -i username_ssh_key username@10.0.0.1 brave-browser
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
ssh -Y -i username_ssh_key username@10.0.0.1 shotwell
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

## Available Resources

### AI Models
- **Location:** `/opt/shared-models`
- **Description:** Pre-installed language models for AI applications
- **Usage:** Automatically available to Msty and other AI tools

---

*For the complete setup guide, return to the [main README](README.md)*