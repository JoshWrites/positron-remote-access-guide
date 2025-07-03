# Positron Remote Access System

## What is Positron?

Positron is a **high-performance remote workstation** that transforms how you approach computationally intensive tasks. Rather than being limited by your laptop's resources, Positron provides on-demand access to server-grade hardware through secure remote connections.

## The Core Value Proposition

**Why use a remote system?** While cloud services offer raw power, Positron provides something more valuable: **complete control and privacy**. Positron bridges the gap between laptop limitations and cloud dependencies by offering:

- **Data sovereignty**: Your files and AI conversations never leave your infrastructure
- **Customizable environment**: Install anything, configure everything, no platform restrictions
- **Persistent workspaces**: Your work continues even when you disconnect
- **Multi-device access**: Same environment from laptop, tablet, or any internet-connected device

<details>
<summary><strong>Key Capabilities</strong></summary>

### Privacy & Security
- **Data sovereignty**: Your files and AI conversations never leave your infrastructure
- **No cloud surveillance**: Unlike Google Docs or ChatGPT, your data isn't scanned or mined
- **Private AI models**: Local inference means sensitive conversations stay completely private
- **Secure remote access**: WireGuard VPN with key-based authentication

### Full Customization
- **Root access**: Install any software, modify any configuration
- **Your choice of tools**: No platform restrictions or app store limitations
- **Custom AI models**: Load and run any models you want, not just what vendors provide
- **Personal infrastructure**: Configure networking, security, and services your way

### AI Workstation
- **Local language models**: Host 70B+ models with Ollama CLI and Msty GUI
- **Image generation**: ComfyUI for Stable Diffusion and AI art workflows
- **Always-on AI**: Models loaded and ready, no cold start delays or usage limits

### Dedicated Computing
- **Exclusive hardware**: AMD Ryzen 5950X (16c/32t), 64GB RAM, RX 7900 XTX just for you
- **Sustained performance**: No thermal throttling or resource sharing with other users
- **Persistent environments**: Long-running processes, development servers, background tasks

### Hybrid Workflows
- **Edit locally, render remotely**: Responsive editing with server-grade processing
- **Git-based collaboration**: Code locally, build/test/deploy remotely
- **AI-assisted development**: Local coding with remote AI review and optimization

</details>

<details>
<summary><strong>Connection Methods</strong></summary>

### SSH X11 Ecosystem (Recommended)
Launch individual applications that can spawn others naturally. Start with Dolphin file manager, double-click files, and associated applications launch automatically - creating a full application ecosystem without desktop overhead.

### Full Desktop (X2Go)
Complete KDE Plasma environment for extended desktop work requiring window management and multiple simultaneous applications.

### Terminal Access
Direct command-line access for server administration, CLI tools, and text-based AI interactions.

</details>

<details>
<summary><strong>Access Architecture</strong></summary>

**Secure by design**: WireGuard VPN with role-based access controls ensure your remote workspace remains private and protected.

**When to use Positron:**
- Heavy computational tasks that would drain laptop battery
- AI model inference and training
- Video rendering and transcoding
- Large software builds and deployments
- Persistent development environments
- Collaborative projects requiring shared resources

**When to stay local:**
- Real-time gaming or interactive media
- Simple document editing and web browsing
- Tasks requiring immediate responsiveness
- Quick file organization and basic productivity

</details>

---

Positron isn't a replacement for your laptop - it's a **computational multiplier** that unlocks capabilities impossible on portable hardware.

## Setup Guide

This guide will help you connect to the Positron system using the credentials provided in your welcome email.

## Quick Start

1. **Save your credentials** from the email (VPN config, SSH key, Windows batch file)
2. **Choose your operating system** below and follow the setup instructions
3. **Pick your connection method** (see below)
4. **Connect and enjoy** access to the Positron system!

## Connection Methods

Choose the method that best fits your workflow:

### 🎯 **SSH X11 Ecosystem** (Recommended)
- Launch individual applications that spawn others naturally
- Start with Dolphin file manager, double-click files to launch associated apps
- No desktop environment overhead, full application ecosystem access
- **Best for:** Most workflows, faster than full desktop, integrated experience
- **Available apps:** [View complete application library →](APPLICATIONS.md)

### 🖥️ **Full Desktop** (Extended work sessions)
- Complete KDE Plasma environment via X2Go
- Multiple applications, taskbar, window management
- **Best for:** Extended work sessions requiring desktop environment
- **Setup:** Install X2Go client, configure session

### 💻 **Terminal Access** (Development & administration)
- Direct command-line access for development and system management
- **Best for:** CLI tools, scripting, AI model management with Ollama
- **Setup:** SSH client only

---

<details>
<summary>🪟 <strong>Windows Setup</strong></summary>


### Step 1: Install Required Software

**VPN Client:**
- Download and install [WireGuard](https://www.wireguard.com/install/)

**For Single App Access (optional):**
- Install an X server: [VcXsrv](https://sourceforge.net/projects/vcxsrv/) (recommended) or [Xming](https://sourceforge.net/projects/xming/)
- Alternative: [MobaXterm](https://mobaxterm.mobatek.net/) (includes SSH client and X server)

**For Full Desktop Access:**
- Download and install [X2Go Client](https://wiki.x2go.org/doku.php/download:start)

### Step 2: Configure VPN

1. Open WireGuard application
2. Click "Import tunnel(s) from file" 
3. Select your `username.conf` file from the email
4. Click "Activate" to connect
5. **Test connection:** Open Command Prompt and run `ping 10.0.0.1` - you should see replies

### Step 3: Set SSH Key Permissions

1. Save your SSH private key as `username_ssh_key` (no file extension) in your Documents folder
2. Save the `set-ssh-permissions.bat` file from your email
3. Double-click the batch file to fix permissions

### Step 4: Choose Your Access Method

#### Terminal Only
```cmd
ssh -i "%USERPROFILE%\Documents\username_ssh_key" username@10.0.0.1
```

#### Single Application (requires X server running)
```cmd
ssh -X -i "%USERPROFILE%\Documents\username_ssh_key" username@10.0.0.1 msty
```

#### Full Desktop (X2Go)
1. Open X2Go Client
2. Configure session:
   - **Session name:** Positron Desktop
   - **Host:** 10.0.0.1
   - **Login:** username
   - **SSH port:** 22
   - **Use RSA/DSA key:** Browse to your `username_ssh_key` file
   - **Session type:** KDE
   - **Media:** ✓ Sound support

### One-Click Desktop Shortcuts

Save these files on your Desktop for easy access:

**Remote Desktop - username.bat:**
```batch
@echo off
echo Starting VPN connection...
"C:\Program Files\WireGuard\wireguard.exe" /installtunnelservice "C:\Users\%USERNAME%\Documents\username.conf"
timeout /t 3 /nobreak > nul
echo Launching remote desktop...
start "" "C:\Program Files (x86)\x2goclient\x2goclient.exe" --session="Positron Desktop"
```

**Remote Terminal - username.bat:**
```batch
@echo off
"C:\Program Files\WireGuard\wireguard.exe" /installtunnelservice "C:\Users\%USERNAME%\Documents\username.conf"
timeout /t 3 /nobreak > nul
ssh -i "%USERPROFILE%\Documents\username_ssh_key" username@10.0.0.1
pause
```

**Launch Msty - username.bat:** (requires VcXsrv/Xming)
```batch
@echo off
echo Starting X server and VPN...
start "" "C:\Program Files\VcXsrv\vcxsrv.exe" :0 -multiwindow -clipboard -wgl
"C:\Program Files\WireGuard\wireguard.exe" /installtunnelservice "C:\Users\%USERNAME%\Documents\username.conf"
timeout /t 3 /nobreak > nul
set DISPLAY=localhost:0
ssh -X -i "%USERPROFILE%\Documents\username_ssh_key" username@10.0.0.1 msty
```

**Wake Computer - username.bat:** (FAMILY users only)
```batch
@echo off
echo Sending Wake-on-LAN packet...
powershell -Command "$mac='AA:BB:CC:DD:EE:FF'; $mac_bytes=$mac -split '[:-]'|ForEach-Object{[byte]('0x'+$_)}; $packet=[byte[]](,0xFF*6)+($mac_bytes*16); $udp=New-Object System.Net.Sockets.UdpClient; $udp.Connect(([System.Net.IPAddress]::Broadcast),7); $udp.Send($packet,$packet.Length)|Out-Null; $udp.Close()"
echo Wake packet sent! Wait 30-60 seconds for system to boot...
timeout /t 5
```
*Note: Replace AA:BB:CC:DD:EE:FF with the MAC address provided in your credentials email*

</details>

---

<details>
<summary>🍎 <strong>macOS Setup</strong></summary>


### Step 1: Install Required Software

**VPN Client:**
- Install WireGuard from the [App Store](https://apps.apple.com/us/app/wireguard/id1451685025) or [download directly](https://www.wireguard.com/install/)

**For Single App Access:**
- Install [XQuartz](https://www.xquartz.org/) - **IMPORTANT: Log out and back in (or restart) after installing**

**For Full Desktop Access:**
- Download and install [X2Go Client](https://wiki.x2go.org/doku.php/download:start)

### Step 2: Configure VPN

1. Open WireGuard application
2. Click "Import tunnel(s) from file"
3. Select your `username.conf` file from the email
4. Toggle the connection ON
5. **Test connection:** Open Terminal and run `ping 10.0.0.1` - you should see replies

### Step 3: Set SSH Key Permissions

1. Save your SSH private key as `username_ssh_key` in your home directory
2. Open Terminal and run:
```bash
chmod 600 ~/username_ssh_key
```

### Step 4: Choose Your Access Method

#### Terminal Only
```bash
ssh -i ~/username_ssh_key username@10.0.0.1
```

#### Single Application (requires XQuartz)
```bash
ssh -X -i ~/username_ssh_key username@10.0.0.1 msty
```

#### Full Desktop (X2Go)
1. Open X2Go Client
2. Configure session:
   - **Session name:** Positron Desktop
   - **Host:** 10.0.0.1
   - **Login:** username
   - **SSH port:** 22
   - **Use RSA/DSA key:** Browse to your `username_ssh_key` file
   - **Session type:** KDE
   - **Media:** ✓ Sound support

### Automator Shortcuts

**For Full Desktop:**
1. Open Automator → New → Application
2. Add "Run Shell Script" action with:
```bash
/usr/local/bin/wg-quick up username 2>/dev/null || true
sleep 2
open -a X2Go
```
3. Save as "Positron Desktop.app"

**For Direct App Launch (e.g., Msty):**
1. Open Automator → New → Application
2. Add "Run Shell Script" action with:
```bash
/usr/local/bin/wg-quick up username 2>/dev/null || true
sleep 2
osascript -e 'tell app "Terminal" to do script "ssh -X -i ~/.ssh/username_ssh_key username@10.0.0.1 msty"'
```
3. Save as "Launch Msty.app"

</details>

---

<details>
<summary>🐧 <strong>Linux Setup</strong></summary>


### Step 1: Install Required Software

**VPN Client:**
```bash
# Ubuntu/Debian
sudo apt install wireguard

# Fedora
sudo dnf install wireguard-tools

# Arch
sudo pacman -S wireguard-tools
```

**For Full Desktop Access:**
```bash
# Ubuntu/Debian
sudo apt install x2goclient

# Fedora
sudo dnf install x2goclient

# Arch
sudo pacman -S x2goclient
```

**Note:** X11 is already available on most Linux distributions for single app access.

### Step 2: Configure VPN

1. Save your VPN config as `/etc/wireguard/username.conf`:
```bash
sudo cp username.conf /etc/wireguard/
sudo chmod 600 /etc/wireguard/username.conf
```

2. Connect to VPN:
```bash
sudo wg-quick up username
```

3. **Test connection:** `ping 10.0.0.1` - you should see replies

4. **Auto-start VPN on boot (optional):**
```bash
sudo systemctl enable wg-quick@username
```

### Step 3: Set SSH Key Permissions

```bash
chmod 600 username_ssh_key
```

### Step 4: Choose Your Access Method

#### Terminal Only
```bash
ssh -i username_ssh_key username@10.0.0.1
```

#### Single Application (X11 built-in)
```bash
ssh -X -i username_ssh_key username@10.0.0.1 msty
```

#### Full Desktop (X2Go)
1. Open X2Go Client
2. Configure session:
   - **Session name:** Positron Desktop
   - **Host:** 10.0.0.1
   - **Login:** username
   - **SSH port:** 22
   - **Use RSA/DSA key:** Browse to your `username_ssh_key` file
   - **Session type:** KDE
   - **Media:** ✓ Sound support

### Desktop Shortcut

Create a `.desktop` file for quick access:
```bash
cat > ~/.local/share/applications/positron-desktop.desktop << EOF
[Desktop Entry]
Name=Positron Desktop
Exec=bash -c 'sudo wg-quick up username; x2goclient'
Icon=computer
Type=Application
EOF

chmod +x ~/.local/share/applications/positron-desktop.desktop
```

</details>

---

## Quick Reference

### Connection Commands
```bash
# Terminal only
ssh -i username_ssh_key username@10.0.0.1

# Single application (requires X server running)
ssh -X -i username_ssh_key username@10.0.0.1 msty
ssh -X -i username_ssh_key username@10.0.0.1 libreoffice --writer
ssh -X -i username_ssh_key username@10.0.0.1 dolphin

# With compression for slow connections
ssh -XC -i username_ssh_key username@10.0.0.1 msty

# Trusted X11 forwarding (if regular X11 fails)
ssh -Y -i username_ssh_key username@10.0.0.1 msty
```

### VPN Connection Test
```bash
# After connecting VPN, test with:
ping 10.0.0.1
# Should show replies if VPN is working
```

### File Transfer Examples
```bash
# Upload file to remote system
scp -i username_ssh_key localfile.txt username@10.0.0.1:~/

# Download file from remote system  
scp -i username_ssh_key username@10.0.0.1:~/remotefile.txt ./

# Upload entire directory
scp -r -i username_ssh_key local_folder/ username@10.0.0.1:~/
```

## Access Levels

<details>
<summary>👨‍👩‍👧‍👦 <strong>FAMILY Role</strong></summary>

- ✅ Full system administrator (sudo) access
- ✅ Unlimited resources
- ✅ ALL files and settings access  
- ✅ Can download new AI models
- ✅ Direct LAN access option (no VPN needed at home)
- ✅ Wake-on-LAN capability for remote system wake-up
- **Connection options:**
  - On home network: Direct IP (no VPN needed)
  - From internet: VPN → 10.0.0.1
  - System sleeping: Use Wake-on-LAN shortcut

</details>

<details>
<summary>👥 <strong>FRIENDS Role</strong></summary>

- ✅ Full desktop with private workspace
- ✅ All applications (Msty, Ollama, LibreOffice)
- ✅ Private conversations and documents
- ✅ Shared AI models at `/opt/shared-models` (read-only)
- ❌ No access to other users' files
- ❌ Cannot install software
- ❌ Must use VPN always
- **Resource limits:**
  - RAM: 8GB maximum
  - Processes: 200 maximum
  - CPU time: 4 hours/day
  - Disk quota: User home directory only

</details>

## Troubleshooting

### Connection Issues

**VPN Won't Connect?**
- Check internet connection and ensure port 51820 isn't blocked
- Verify WireGuard shows "Active" status
- Test with `ping 10.0.0.1` after connecting

**SSH Permission Errors?**
- **Windows:** Run the `set-ssh-permissions.bat` file from your email
- **Mac/Linux:** `chmod 600 username_ssh_key`

**System Appears Asleep?**
- **FAMILY users:** Use Wake-on-LAN shortcut from credentials email
- **FRIENDS users:** Contact admin at art.josh@gmail.com

### Application Issues

**X11 Forwarding Not Working?**
- **Windows:** Ensure VcXsrv/Xming is running before SSH
- **Mac:** XQuartz must be running (starts automatically after login)
- **Linux:** X11 apps work through XWayland on Wayland systems
- **Error "Can't open display":** Try `export DISPLAY=:0` or use `ssh -Y`

**X2Go Black Screen?**
- Wait 15 seconds for desktop to load
- Session → Terminate → Reconnect
- Reduce colors to 256, increase compression to 4-balanced

### Performance Optimization

**Slow Performance?**
- **X2Go:** Colors → 256, Compression → 4-balanced
- **SSH X11:** Add `-C` flag: `ssh -XC -i key user@host`
- Use compression on slower connections

## Support

For help, contact: **art.josh@gmail.com**

Include your username in support requests for faster assistance.

---

*Generated for the Positron Remote Access System*
