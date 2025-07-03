# Positron Remote Access Guide

Complete setup guide for accessing the Positron system remotely via VPN, SSH, and desktop environments.

## Overview

This guide will help you connect to the Positron system using the credentials provided in your welcome email. The system supports three connection methods:

- **Terminal Only** - Command line access via SSH
- **Single Application** - Launch specific apps directly via SSH X11 forwarding
- **Full Desktop** - Complete KDE desktop environment via X2Go

## Quick Start

1. **Save your credentials** from the email (VPN config, SSH key, Windows batch file)
2. **Choose your operating system** below and follow the setup instructions
3. **Pick your connection method** (see below)
4. **Connect and enjoy** access to the Positron system!

## Connection Methods

Choose the method that best fits your needs:

### 🖥️ **Full Desktop** (Recommended for extended work)
- Complete KDE desktop environment via X2Go
- Multiple applications, taskbar, file manager
- Best for: Extended work sessions, productivity tasks
- **Setup:** Install X2Go client, configure session

### 🎯 **Single Application** (Fastest for specific tasks)
- Launch individual apps directly via SSH with X11 forwarding
- No desktop environment needed
- Best for: Quick access to specific tools (Msty, LibreOffice, etc.)
- **Setup:** Install X server (Windows/Mac), use SSH -X

### 💻 **Terminal Only** (System administration)
- Command line access only
- File transfers, system management
- Best for: Advanced users, scripting, file operations
- **Setup:** SSH client only

---

## <details><summary>🪟 Windows Setup</summary>

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

## <details><summary>🍎 macOS Setup</summary>

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

## <details><summary>🐧 Linux Setup</summary>

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

## Applications Available

Once connected, you have access to:

- **Msty** - AI chat interface (`msty`)
- **Msty Studio** - Advanced AI development environment (`mstystudio`)
- **LibreOffice** - Complete office suite:
  - Writer: `libreoffice --writer`
  - Calc: `libreoffice --calc`
  - Impress: `libreoffice --impress`
  - Draw: `libreoffice --draw`
- **Firefox** - Web browser (`firefox`)
- **Dolphin** - File manager (`dolphin`)
- **Kate** - Text editor (`kate`)
- **Konsole** - Terminal emulator (`konsole`)
- **Okular** - PDF viewer (`okular`)
- **GIMP** - Image editor (`gimp`)
- **VLC** - Media player (`vlc`)
- **And many more standard Linux applications**

### Direct App Launch Examples
```bash
# AI Tools
ssh -X -i username_ssh_key username@10.0.0.1 msty
ssh -X -i username_ssh_key username@10.0.0.1 mstystudio

# Office Applications
ssh -X -i username_ssh_key username@10.0.0.1 libreoffice --writer
ssh -X -i username_ssh_key username@10.0.0.1 libreoffice --calc

# System Tools
ssh -X -i username_ssh_key username@10.0.0.1 dolphin
ssh -X -i username_ssh_key username@10.0.0.1 kate
ssh -X -i username_ssh_key username@10.0.0.1 firefox
```

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

### FAMILY Role
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

### FRIENDS Role  
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

## Troubleshooting

### VPN Won't Connect?
- Check internet connection
- Verify port 51820 is not blocked by firewall
- Ensure WireGuard shows "Active"

### SSH Permission Errors?
- **Windows:** Run the `set-ssh-permissions.bat` file from your email
- **Mac/Linux:** `chmod 600 username_ssh_key`

### X2Go Black Screen?
- Wait 15 seconds for the desktop to load
- Session → Terminate → Reconnect
- Try changing: Colors → 256, Compression → 4-balanced

### Slow Performance?
- **X2Go:** Reduce colors to 256, increase compression to 4-balanced
- **SSH X11:** Use `-C` flag for compression: `ssh -XC -i key user@host`

### X11 Forwarding Not Working?
- **Windows:** Ensure VcXsrv/Xming is running first
- **Mac:** XQuartz must be running (starts automatically after login)
- **Linux:** If using Wayland (check with `echo $XDG_SESSION_TYPE`), X11 apps still work through XWayland. Alternative: use full desktop via X2Go
- **Error "Can't open display":** Try `export DISPLAY=:0`
- **Try trusted X11:** Use `ssh -Y` instead of `ssh -X`

### System Appears Asleep?
- **FAMILY users:** Use the Wake-on-LAN shortcut provided in your credentials email
- **FRIENDS users:** Contact admin at art.josh@gmail.com

### Can't Connect to 10.0.0.1?
- Verify VPN is active and shows "Connected" in WireGuard
- Test with `ping 10.0.0.1` - should show replies
- Check firewall isn't blocking port 51820
- Try disconnecting and reconnecting VPN

### Applications Won't Launch?
- **"Can't open display" error:** Set `export DISPLAY=:0` or use `ssh -Y` instead of `ssh -X`
- **Windows:** Ensure X server (VcXsrv/Xming) is running before SSH
- **Mac:** XQuartz must be running (starts automatically after login)
- **Linux:** On Wayland systems, X11 apps work through XWayland

### SSH Key Permission Errors?
- **Windows:** Run the `set-ssh-permissions.bat` file from your credentials email
- **Mac/Linux:** Run `chmod 600 username_ssh_key` in Terminal

### Slow Performance?
- **X2Go:** Change Colors to 256, Compression to 4-balanced
- **SSH X11:** Add `-C` flag: `ssh -XC -i key user@host`
- **Network:** Use compression on slow connections

## Support

For help, contact: **art.josh@gmail.com**

Include your username in support requests for faster assistance.

---

*Generated for the Positron Remote Access System*