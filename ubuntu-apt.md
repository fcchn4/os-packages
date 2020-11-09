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

## Extra Repositories

```bash
## Beekeeper
deb https://dl.bintray.com/beekeeper-studio/releases disco main

## Gradle Compiler Java 
deb http://ppa.launchpad.net/cwchien/gradle/ubuntu focal main
# deb-src http://ppa.launchpad.net/cwchien/gradle/ubuntu focal main

## Docker CE
deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable
# deb-src [arch=amd64] https://download.docker.com/linux/ubuntu focal stable

## Github Official Tool
deb https://cli.github.com/packages focal main
# deb-src https://cli.github.com/packages focal main

## Google Chrome 
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

## Libreoffice PPA
deb http://ppa.launchpad.net/libreoffice/libreoffice-7-0/ubuntu focal main
# deb-src http://ppa.launchpad.net/libreoffice/libreoffice-7-0/ubuntu focal main

## MariaDB 10.5 Stable
deb [arch=amd64] https://mirror.ufro.cl/mariadb/repo/10.5/ubuntu focal main
deb-src https://mirror.ufro.cl/mariadb/repo/10.5/ubuntu focal main

## NodeJS
deb https://deb.nodesource.com/node_14.x focal main
deb-src https://deb.nodesource.com/node_14.x focal main

## Spotify
deb http://repository.spotify.com stable non-free

## Typora - Markdown client
deb https://typora.io/linux ./
# deb-src https://typora.io/linux ./

## VirtualBox
deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian focal contrib

## VSCode
deb [arch=amd64 signed-by=/etc/apt/trusted.gpg.d/packages.microsoft.gpg] https://packages.microsoft.com/repos/vscode stable main

## Yarn 
deb https://dl.yarnpkg.com/debian/ stable main
```

## Base Packages

```bash
## Packages Essentials
apt install -y linux-headers-$(uname -r) build-essential checkinstall make \
automake cmake autoconf lsb-release dkms

## Packages requiered for hardware Intel
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

## Cursor Mouse
apt install -y oxygen-cursor-theme
```

## Ubuntu Restricted Extras

```bash
## Extras
apt install -y ubuntu-restricted-extras

## Codecs, Sound and Video
apt install -y vlc gstreamer1.0-libav gstreamer1.0-plugins-ugly gstreamer1.0-plugins-bad \
gstreamer1.0-pulseaudio vorbis-tools faac faad ffmpeg ffmpeg2theora libdvdcss2
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
dia-rib-network dia-shapes dia-common
```

## Dash Dock for Gnome

```bash
gsettings set org.gnome.shell.extensions.dash-to-dock extend-height false
```

## Tools

```bash
apt install hwinfo mesa-utils iftop crunch
```

## Comandos 

```bash
ubuntu-drivers devices
ubuntu-drivers autoinstall
nvidia-smi
```
