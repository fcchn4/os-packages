# xubuntu 20.04 - Desktop Configuration 

Configuration for Operating System Ubuntu 20.04 with Open Source Desktop XFCE4.

## Sources List 

```bash
## Repos Ubuntu 20.04
deb http://bo.archive.ubuntu.com/ubuntu/ focal main restricted universe multiverse
deb http://bo.archive.ubuntu.com/ubuntu/ focal-updates main restricted universe multiverse
deb http://bo.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu focal-security main restricted universe multiverse

deb-src http://bo.archive.ubuntu.com/ubuntu/ focal main restricted universe multiverse
deb-src http://bo.archive.ubuntu.com/ubuntu/ focal-updates main restricted universe multiverse
deb-src http://bo.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu focal-security main restricted universe multiverse

deb http://archive.canonical.com/ubuntu focal partner
deb-src http://archive.canonical.com/ubuntu focal partner
```

## Update and Install Packages 

```bash
## Update Operating System 
apt update
apt upgrade -y

## Installing required packages
apt install -y linux-headers-$(uname -r) build-essential checkinstall make \
automake cmake autoconf lsb-release dkms

## Intel Firmware and sensors controller
apt install -y intel-microcode intel-gpu-tools lm-sensors

## For lm-sensors
sensors-detect --auto

## Packages for compress and uncompress
apt install -y bzip2 zip unzip unace rar unace-nonfree p7zip p7zip-full \
p7zip-rar unrar unrar-free lzip lhasa arj sharutils mpack lzma lzop \
cabextract xz-utils

## Desktop Tools
apt install -y apt-transport-https ca-certificates curl \
gnupg-agent software-properties-common tuned tuned-gtk tuned-utils \
hardinfo arc-theme acpi acpid acpitool software-properties-common dirmngr

## Ubuntu extra tools
apt install -y ubuntu-restricted-extras xubuntu-icon-theme 

## Vim 
apt install -y vim vim-scripts vim-syntax-docker vim-syntax-gtk
```

## Uninstall snap

```bash
## List and remove snap packages
snap list
snap remove <NAME_PACKAGE>

## Unmount snap point
umount /snap/core/<ID_INSIDE>
## or 
umount /var/snap

## Purge snap
apt purge snapd

## Remove snap files
rm -rf ~/snap
sudo rm -rf /snap
sudo rm -rf /var/snap
sudo rm -rf /var/lib/snapd
```

## Audio Codecs

```bash
## Codecs, Sound and Video
apt install -y vlc gstreamer1.0-libav gstreamer1.0-plugins-ugly gstreamer1.0-plugins-bad \
gstreamer1.0-pulseaudio vorbis-tools faac faad ffmpeg ffmpeg2theora
```

## Tipografías

```bash
## Fonts for OS
apt install -y ttf-mscorefonts-installer fonts-freefont-ttf fonts-freefont-otf
```

## Design

```bash
## Editor images
apt install -y gimp gimp-data-extras inkscape inkscape-open-symbols dia \
dia-rib-network dia-shapes dia-common blender blender-ogrexml-1.9
```

## Tools for DB

```bash
## SQLite3
apt install -y sqlitebrowser sqlmap sqlite3

## MariaDB
apt install software-properties-common dirmngr apt-transport-https
apt-key adv --fetch-keys 'https://mariadb.org/mariadb_release_signing_key.asc'
add-apt-repository 'deb [arch=amd64] https://mirror.insacom.cl/mariadb/repo/10.5/ubuntu focal main'
## Update repos
apt update
apt upgrade -y
## Install MariaDB
apt install -y mariadb-server mariadb-client mycli
```

## Google Chrome

```bash
## Add repo
echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" | sudo tee /etc/apt/sources.list.d/google-chrome.list
apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 78BD65473CB3BD13
## Update repo
apt update
## Install Web Browser
apt install -y google-chrome-stable
```

## Electronic Tools

```bash
apt install -y arduino arduino-core fritzing fritzing-parts
```

## VSCode

```bash
## Add repo
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
install -o root -g root -m 644 packages.microsoft.gpg /etc/apt/trusted.gpg.d/
rm packages.microsoft.gpg
sh -c 'echo "deb [arch=amd64,arm64,armhf signed-by=/etc/apt/trusted.gpg.d/packages.microsoft.gpg] https://packages.microsoft.com/repos/code stable main" > /etc/apt/sources.list.d/vscode.list'
## Update repo
apt update
## Install packages
apt install apt-transport-https
apt install code
```

## Typora

```bash
## Add repo
wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -
add-apt-repository 'deb https://typora.io/linux ./'
## Update repo
apt-get update
## Install Package
apt-get install typora
```

## Extra tools

```bash
## Hardware detect
apt install hwinfo 

## Tools for video
apt install -y mesa-utils 

## Network scan
apt install -y iftop 

## Hacking tools
apt install -y crunch speedtest-cli etherape ettercap-text-only aircrack-ng wireshark \
nmap

## Varied tools
apt install -y peek putty putty-tools telegram-desktop transmission cheese figlet mlocate

## Mail tools
apt install -y geary hunspell-es
```

## Dash Dock for Gnome

```bash
gsettings set org.gnome.shell.extensions.dash-to-dock extend-height false
```

## Comandos 

```bash
ubuntu-drivers devices
ubuntu-drivers autoinstall
nvidia-smi
```