# Application Library

Comprehensive guide to applications available on the Positron system, organized by use case.

## 🚀 **Key Feature: Application Ecosystem Access**

When you launch any application via SSH X11 forwarding, that application can launch other applications automatically. This means:

**Start with one app → Access the entire ecosystem**

### How It Works:
1. Launch any application: `ssh -X -i key user@host dolphin`
2. That application inherits the X11 forwarding session
3. Click files, use menus, or open dialogs to launch other apps
4. Each new application appears as a separate window on your local desktop
5. All applications share the same SSH session

### Real-World Examples:
- **Dolphin → Kate:** Click a `.txt` file → Kate text editor opens automatically
- **Dolphin → LibreOffice:** Click a `.docx` file → LibreOffice Writer opens automatically  
- **Dolphin → Firefox:** Click an `.html` file → Firefox opens to display the page
- **Kate → Dolphin:** Use "Open containing folder" → Dolphin opens to that location
- **LibreOffice → Any app:** Use "Insert → Object → From File" → File browser launches

### What You'll See:
- Multiple application windows on your local desktop (Windows/Mac/Linux)
- Each application runs independently but shares the connection
- Alt-Tab between remote apps just like local applications
- Seamless integration with your local desktop environment

### Why This Is Powerful:
- **Faster than full desktop:** No desktop environment overhead
- **More integrated:** Apps appear directly on your local desktop
- **Workflow-friendly:** Start with what you need, expand naturally
- **Resource efficient:** Only running the applications you actually use

**Recommended approach:** Start with Dolphin file manager for maximum flexibility!

## AI & Machine Learning

### Msty
- **Command:** `msty`
- **Description:** AI chat interface for conversations with various language models
- **Best for:** Quick AI assistance, code help, general questions
- **Documentation:** [docs](https://docs.msty.app/)

### Ollama CLI
- **Command:** `ollama`
- **Description:** Command-line interface for local language models
- **Best for:** AI model management, scripting, API access
- **Usage:** `ollama list`, `ollama run model-name`

### ComfyUI
- **Command:** `comfyui` or access via web browser at `http://10.0.0.1:8188`
- **Description:** Node-based interface for AI image generation and processing
- **Best for:** Stable Diffusion workflows, image generation, AI art creation
- **Features:** Visual workflow editor, custom nodes, batch processing
- **Documentation:** [docs](https://docs.comfy.org/)

## Development Environment

### Kate
- **Command:** `kate`
- **Description:** Advanced text editor with syntax highlighting
- **Best for:** Code editing, configuration files, markdown
- **Documentation:** [docs](https://docs.kde.org/stable/en/applications/kate/)

### Vim
- **Command:** `vim`
- **Description:** Powerful text editor for advanced users
- **Best for:** System administration, configuration files, programming
- **Documentation:** [docs](https://vimhelp.org/)

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

### Konsole
- **Command:** `konsole`
- **Description:** Terminal emulator with tabs and profiles
- **Features:** Multiple tabs, customizable profiles, split view
- **Documentation:** [docs](https://docs.kde.org/stable/en/applications/konsole/)

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

## File Management & System Tools

### Dolphin
- **Command:** `dolphin`
- **Description:** Advanced file manager with dual-pane support
- **Features:** Network browsing, archive support, preview pane
- **Documentation:** [docs](https://docs.kde.org/stable/en/applications/dolphin/)

### Okular
- **Command:** `okular`
- **Description:** Universal document viewer
- **Supports:** PDF, EPUB, images, DjVu, PostScript
- **Documentation:** [docs](https://docs.kde.org/stable/en/applications/okular/)

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
- **Documentation:** [docs](https://support.brave.app/hc/en-us)

## Content Creation

### Shotwell
- **Command:** `shotwell`
- **Description:** Photo organizer and basic editor
- **Best for:** Photo management, basic editing, organizing image collections
- **Documentation:** [docs](https://wiki.gnome.org/Apps/Shotwell)


## Quick Launch Examples

### Recommended: Start with File Manager
```bash
# Launch Dolphin file manager - gives access to entire application ecosystem
ssh -X -i username_ssh_key username@10.0.0.1 dolphin
# Then: Double-click any file to launch the appropriate application automatically!
```

### AI & Machine Learning
```bash
# Launch Msty for AI chat
ssh -X -i username_ssh_key username@10.0.0.1 msty

# Use Ollama CLI for model management
ssh -i username_ssh_key username@10.0.0.1 ollama list

# Access ComfyUI via web browser (after connecting to VPN)
# Navigate to: http://10.0.0.1:8188
```

### Development Environment
```bash
# Launch code editor
ssh -X -i username_ssh_key username@10.0.0.1 kate

# Launch terminal
ssh -X -i username_ssh_key username@10.0.0.1 konsole

# Use development tools (command line)
ssh -i username_ssh_key username@10.0.0.1 # Then use git, node, python3, etc.
```

### Office & Productivity
```bash
# Launch LibreOffice Writer
ssh -X -i username_ssh_key username@10.0.0.1 libreoffice --writer

# Launch LibreOffice Calc
ssh -X -i username_ssh_key username@10.0.0.1 libreoffice --calc

# Launch LibreOffice Impress
ssh -X -i username_ssh_key username@10.0.0.1 libreoffice --impress
```

### File Management & System Tools
```bash
# Launch file manager
ssh -X -i username_ssh_key username@10.0.0.1 dolphin

# Launch document viewer
ssh -X -i username_ssh_key username@10.0.0.1 okular
```

### Web Browsers
```bash
# Launch Firefox
ssh -X -i username_ssh_key username@10.0.0.1 firefox

# Launch Brave browser
ssh -X -i username_ssh_key username@10.0.0.1 brave-browser
```

### Content Creation
```bash
# Launch photo organizer
ssh -X -i username_ssh_key username@10.0.0.1 shotwell
```

## Performance Tips

### Connection Optimization
**For slow connections, add compression:**
```bash
ssh -XC -i username_ssh_key username@10.0.0.1 application_name
```

**For graphics-heavy applications, use trusted X11 forwarding:**
```bash
ssh -Y -i username_ssh_key username@10.0.0.1 shotwell
```

### Workflow Optimization
**Start with Dolphin file manager for the best experience:**
```bash
ssh -XC -i username_ssh_key username@10.0.0.1 dolphin
```
- Navigate to files visually
- Double-click to launch appropriate applications automatically
- No need to remember specific commands for each file type
- Applications launch faster than full desktop environment

## System Resources

### AI Models
- **Location:** `/opt/shared-models`
- **Description:** Pre-installed language models for AI applications
- **Usage:** Automatically available to Msty and other AI tools
- **Access:** All users can access shared models for inference

### User Permissions

**FAMILY Users:**
- Full system administrator access with `sudo`
- Can install additional software: `sudo apt install package_name`
- Access to snap packages: `sudo snap install package_name`
- Can add PPAs and third-party repositories

**FRIENDS Users:**
- Access to all pre-installed applications
- Cannot install new software
- Can request software installation by contacting admin
- Resource limits: 8GB RAM, 200 processes, 4 hours CPU time/day

---

*For the complete setup guide, return to the [main README](README.md)*