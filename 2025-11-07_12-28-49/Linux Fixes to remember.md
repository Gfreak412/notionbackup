# General
## Create a .desktop file
Template - 
```bash
[Desktop Entry]
Encoding=UTF-8 Version=1.0
Type=Application Terminal=false
Exec=/path/to/executable Name=Name of Application
Icon=/path/to/icon
```
## Sudo delete a directory
`sudo rm -rf "Directory Name"`
<br/>
## ffmpeg Video Conversion Commands
Individual Files Coversion - `ffmpeg -i intro.mkv -codec copy intro.mp4`
Batch File Convert - `for i in *.mkv; do ffmpeg -i "$i" -codec copy "${i%.*}.mp4"`
## smb.conf
```bash
[global]
server role = standalone server
map to guest = Bad User
usershare allow guests = yes
[share]
comment = movies
path = /home/kanishk
read only = no
guest ok = yes
force user = kanishk
force group = kanishk
```
## Slow Surfing Speed
- Install `reflector`
- Edit `/etc/xdg/reflector/reflector.conf` this file.
- Change Country to India
## If Slow Surfing Speed
([https://forum.manjaro.org/t/internet-speed-is-slow/103443](https://forum.manjaro.org/t/internet-speed-is-slow/103443))
- You could write a config file…
- Create a file & Edit it:
- `sudo vim /etc/modprobe.d/wifi.conf`
- Add to it:
```bash
options iwlwifi swcrypto=1
options iwlwifi power_save=0
options iwlwifi 11n_disable=1
options iwlwifi disable_11ac=1
options iwlwifi disable_11ax=1
```
- Save it and exit.
- Reboot your system.
## Set Default Magnet Link Opener
`gio mime x-scheme-handler/magnet org.qbittorrent.qBittorrent.desktop`
`gio mime x-scheme-handler/magnet org.deluge_torrent.deluge`
<br/>
## Pamac-gtk not following gtk theme
`sudo pacman -S pamac-gtk3`
<br/>
## BIOS Splash Screen not Showing
It could be due to Secure boot being enabled.
- Make a Windows Installation USB and Plug it in, this may enable you to again see the splash screen, and the motherboard will start POSTing via dedicated GPU again.
- Disable Secure Boot
- Enable CSM 
<br/>
# **Printing**
[CUPS](https://openprinting.github.io/cups/) is the standards-based, open source printing system developed by OpenPrinting for Linux® and other Unix®-like operating systems. (This Is necessary for printing, config can be available in archcraft config files folder on 2nd storage)
<br/>
# **Manjaro**
- make legacy application theme permanent by disabling extension "Legacy (GTK3) Theme Scheme Auto Switcher"
- if a pacman mirror of india starts showing error and update cannot be applied/transaction cannot be made reset pacman-mirrors by
`sudo pacman-mirrors --country all --api --protocols all --set-branch stable && sudo pacman -Syu`
<br/>
# Fedora
## Running Apps on Wayland instead of XWayland
### Ulauncher
-  install `wmctrl` 
- set any keybind which will never be used
- set `Super+Shift+Return` in Custom Shortcut with command `ulauncher-toggle`
### VS Code
- install `code`
- run `cp /usr/share/applications/code.desktop ~/.local/share/applications/`
- run `nvim ~/.local/share/applications/code.desktop`
- Comment out `# Exec=/usr/share/code/code --unity-launch %F`
- Add `Exec=/usr/share/code/code --enable-features=UseOzonePlatform,WaylandWindowDecorations --ozone-platform-hint=auto --unity-launch %F` in its place
### Chrome and Brave
- Go to `chrome://flags` or `brave://flags`
- Set `PreferredOzonePlatform` to `Auto`
# Running Apps on Wayland instead of XWayland (Glitches Fixed)
- If `NVIDIA GPU Drivers (Proprietary) `from Fedy > Drivers section, then the Browsers, if has Graphic acceleration on, would cause visual glitches in wayland mode, after boot or waking up from suspend
- After Installing NVIDIA Drivers, the suspend-wake mechanism may break, so follow - ([Fixing Suspend and Wake Mechanism](https://www.notion.so/1730a91202c38127881df8c47aee6852#1730a91202c38171b0bdf6a8a106f7c2]) 
## Fixing Suspend and Wake Mechanism
- `sudo nvim /usr/local/bin/suspend-gnome-shell.sh`
- Put this in the file
```bash
#!/bin/bash
case "$1" in
suspend)
killall -STOP gnome-shell
;;
resume)
killall -CONT gnome-shell
;;
esac
```
- `sudo chmod +x /usr/local/bin/suspend-gnome-shell.sh`
- `sudo nvim /etc/systemd/system/gnome-shell-suspend.service`
- Put this in file 
```bash
[Unit]
Description=Suspend gnome-shell
Before=systemd-suspend.service
Before=systemd-hibernate.service
Before=nvidia-suspend.service
Before=nvidia-hibernate.service
[Service]
Type=oneshot
ExecStart=/usr/local/bin/suspend-gnome-shell.sh suspend
[Install]
WantedBy=systemd-suspend.service
WantedBy=systemd-hibernate.service
```
- `sudo nvim /etc/systemd/system/gnome-shell-resume.service`
- Put this in file
```bash
[Unit]
Description=Resume gnome-shell
After=systemd-suspend.service
After=systemd-hibernate.service
After=nvidia-resume.service
[Service]
Type=oneshot
ExecStart=/usr/local/bin/suspend-gnome-shell.sh resume
[Install]
WantedBy=systemd-suspend.service
WantedBy=systemd-hibernate.service
```
- `systemctl daemon-reload` 
- `systemctl enable gnome-shell-suspend`
- `systemctl enable gnome-shell-resume`
- Restart
# SMB 
## ✅ Samba Sharing Setup on Fedora KDE (Like Manjaro KDE)
### 🧱 1. Install Required Packages
```plain text
sudo dnf install samba samba-client samba-common \
kdenetwork-filesharing system-config-samba \
plasma-discover --setopt=install_weak_deps=False
```
### 🔧 2. Enable and Start Samba Services
```plain text
sudo systemctl enable --now smb nmb
```
### 🔥 3. Allow Samba in Firewall
```javascript
sudo firewall-cmd --permanent --add-service=samba
sudo firewall-cmd --reload
```
### 🔐 4. Set Up Samba User (optional, if not using guest)
```javascript
sudo smbpasswd -a kanishk
```
> Enter your password when prompted.
### 🛡 5. Fix SELinux Permissions (Fedora-specific)
```javascript
sudo setsebool -P samba_enable_home_dirs on
sudo chcon -Rt samba_share_t /home/kanishk/Documents/Multimedia
```
### 🖥 6. Share Folder from Dolphin
1. Open **Dolphin**
1. Right-click on the folder (e.g., `Multimedia`)
1. Go to **Properties → Share tab**
1. Tick **“Share this folder”**
1. Allow guest access or require login
1. Apply
### 🌐 7. Optional: Enable `.local` Hostname Resolution
```javascript
sudo systemctl enable --now avahi-daemon
```
> Lets you access your PC as `fedorakde.local` from other devices (if mDNS is supported).
### ✅ Now You Can:
- Access via `smb://fedorakde.local/Multimedia` or `smb://<your-ip>/Multimedia`
- See Fedora machine under **Network** in Dolphin/Android/Windows
### 🧪 Useful Debug Commands
- Test config:
```javascript
testparm
```
- Check IP:
```javascript
ip a
```
# **Window Manager**
## If in a WM, qt5ct or qt6ct don't work and showing "not configured correctly" do this -
- `sudo vim /etc/environment`
- add line `QT_QPA_PLATFORMTHEME=qt5ct`
## If Flatpak is not uniform
> `**sudo flatpak override --filesystem=xdg-config/gtk-3.0 && sudo flatpak override --filesystem=xdg-config/gtk-4.0**`
- Install `flatseal`
-  Allow user file permission and to `~/.themes` `~/.icons`
- ENV Variables for Flatseal - 
`ICON_THEME=Qogir-dark` 
`GTK_THEME=Arc-Dark`
- **ALT - **`nvim ~/.local/share/flatpak/overrides/global`
```bash
[Context]
filesystems=/usr/share/themes;/usr/share/icons;/usr/share/fonts;home;~/.themes;~/.icons;~/.fonts;host
[Environment]
GTK_THEME=Matcha-dark-sea
ICON_THEME=Papirus-maia
```
## Bind Multimedia Keys
- Install `pulseaudio` , `pulseaudio-alsa` & `pulsemixer`
```bash
XF86AudioRaiseVolume amixer -q set Master 5%+ unmute
XF86AudioLowerVolume amixer -q set Master 5%- unmute
XF86AudioMute amixer -D pulse set Master toggle-mute
```
## Properly Align & SIze The Icons In Polybar or any other bar]
- Install SymbolsOnly Nerd font (`Symbols Nerd Font`)
- Use the Main text font non-nerd font version
- And second font will be `Symbols Nerd Font Mono`
## Set User Icons
- User icon (avatar) SDDM reads the user icon (a.k.a. "avatar") as a PNG image from either `~/.face.icon `for each user, or the common location for all users specified by FacesDir in an SDDM configuration file. The configuration setting can be placed in either `/etc/sddm.conf `directly, or, better, a file under `/etc/sddm.conf.d/` such as` /etc/sddm.conf.d/avatar.conf`
- To use the FacesDir location option, place a PNG image for each user named `username.face.icon` at the location specified by the FacesDir key in the configuration file. The default location for FacesDir is `/usr/share/sddm/faces/`
- I Just kept the pic I wanted in `/usr/share/sddm/faces/` with the name `kanishk.face.icon`
- As per the wiki it seems only .png files are supported.
## OBS & Screen Capture
![2023-04-21_072859-](afd4512b_2023-04-21_072859-.png)
- If Screen Capture(PipeWire) doesn't show screen, it's just black, `pipewire-media-session` maybe missing. (IT IS MISSING IN MANJARO)
<br/>
## Pacman requires Manual Intervention
`sudo pacman -S base-devel` or some dependecy is missing, search for the required prequisite packages
<br/>
## GTK+ apps take 25s to launch
`yay -R xdg-dekstop-portal-gnome`
<br/>
## network-manager-applet asking for wifi password on reboot and relogin on KDE base
- kde-system-settings > connections > wifi > wifi-security > store password for all users (unencrypted)
- change and then save it again as unencrypted
- Restart
# Linux on Laptop
## Battery Life
- Look into TLP [TLPUI (GUI)]
- Look into powertop and Laptop-mode-tools
- Look into laptop-mode-tools [[https://wiki.archlinux.org/title/Laptop_Mode_Tools](https://wiki.archlinux.org/title/Laptop_Mode_Tools)]
- Look into auto-cpufreq
Articles & Wikis
-  [https://wiki.archlinux.org/title/Power_management/Suspend_and_hibernate#:~:text=In order to use hibernation,specified swap in early userspace](https://wiki.archlinux.org/title/Power_management/Suspend_and_hibernate#:~:text=In%20order%20to%20use%20hibernation,specified%20swap%20in%20early%20userspace).
- [https://itsfoss.com/limit-battery-charging-linux/](https://itsfoss.com/limit-battery-charging-linux/)
<br/>
<br/>
