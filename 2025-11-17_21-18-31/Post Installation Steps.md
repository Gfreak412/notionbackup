# **Arch-Linux/Manjaro**
## Install yay
([https://www.linuxcapable.com/how-to-install-yay-aur-helper-on-manjaro-21-linux/](https://www.linuxcapable.com/how-to-install-yay-aur-helper-on-manjaro-21-linux/))
## Install Multimedia Codecs-If not Available
`sudo pacman -S a52dec faac faad2 flac jasper lame libdca libdv libmad libmpeg2 libtheora libvorbis libxv wavpack x264 xvidcore gstreamer0.10-plugins`
## Enable Firewall
## Uncomment the `Parallel Downloads` line in `/etc/pacman.conf`
# **Fedora Workstation**
## Set Fastest Mirror
`sudo nano /etc/dnf/dnf.conf`
`fastestmirror=true`
`max_parallel_downloads=10`
`deltarpm=true`
## Update & Upgrade
`sudo dnf update && sudo dnf upgrade && exit`
## Add Flathub Repo
`flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo`
## Install Apps
`flatpak install vlc`
`flatpak install qbittorrent`
`sudo dnf install steam`
## Install RPM Fusion
`https://rpmfusion.org/Configuration`
<br/>
# Install Multimedia Codecs
`https://rpmfusion.org/Howto/Multimedia`
# Install NVIDIA Drive
`https://rpmfusion.org/Howto/NVIDIA`
## Gnome Extensions
`sudo dnf install gnome-shell-extension-appindicator`
`flatpak install ExtensionManager` 
`sudo dnf install gnome-tweak-tool`
## Change Hostname
`sudo hostnamectl set-hostname "MyPreciousFedora"`
## Install Fedy
`sudo dnf copr enable kwizart/fedy && sudo dnf install fedy -y`
## Customization
`flatpak install ExtensionManager`
`sudo dnf install gnome-shell-extension-appindicator`
`sudo dnf install gnome-shell-extension-gsconnect`
<br/>
## **Enable in ExtensionManager - **
- **User Themes**
- **dash to dock**
- **Impatience**
- **weather o’ clock**
- **Media Label and Controls**
- **Blur my shell**
- **Just perfection**
- **Clipboard history by SUPERCILEX**
## Github
- Go appimaged
- Sunroof Discord
## Theming
- Bibata mordern cursor
- WhiteSur-gtk-theme
- `./install.sh -l`
- `sudo dnf install numix-icon-theme-circle-…`
- Numix folders
- `sudo ./numix-folders`
# **Open SUSE**
## Packman Essential Repo
`zypper ar -cfp 90 <http://ftp.gwdg.de/pub/linux/misc/packman/suse/openSUSE_Leap_15.0/Essentials> packman-essentials`
## [KDE Rice On OpenSuse](https://www.reddit.com/r/unixporn/comments/pilgqs/kde_my_current_kde_setup/)
- Icons McMuse-circle-red
- Workspace theme: Midnight Dark
- Icons: Zafiro
- Window decorations: Sierra breeze
- Wallpaper and article here
- Latte dock for both panels. ([https://www.pling.com/p/1916655/](https://www.pling.com/p/1916655/))
# **Zorin OS**
[https://forum.zorin.com/t/things-you-should-do-after-installing-zorin-os-16/11015](https://forum.zorin.com/t/things-you-should-do-after-installing-zorin-os-16/11015)[https://forum.zorin.com/t/top-x-1-things-to-do-after-installing-zorin-os-16/5938](https://forum.zorin.com/t/top-x-1-things-to-do-after-installing-zorin-os-16/5938)
