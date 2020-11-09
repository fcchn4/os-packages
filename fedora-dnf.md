# Fedora 32 Workstation Post Install 

## Repositories for Personal Desktop

- Files location: **/etc/yum.repos.d/**

**Fedora Official Repository:**

```sh 
## Adding Official Repository
dnf install -y fedora-workstation-repositories

## List files
--> fedora-cisco-openh264.repo
--> fedora-modular.repo
--> fedora.repo
--> fedora-updates-modular.repo
--> fedora-updates.repo
--> fedora-updates-testing-modular.repo
--> fedora-updates-testing.repo
``` 

**RPM Fusion Repository:**

```sh
## RPM Fusion Free
dnf install -y https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm 
## RPM Fusion Non Free
dnf install -y https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm

## List files   
--> rpmfusion-free.repo
--> rpmfusion-free-updates.repo
--> rpmfusion-free-updates-testing.repo
--> rpmfusion-nonfree.repo
--> rpmfusion-nonfree-updates.repo
--> rpmfusion-nonfree-updates-testing.repo
```

**Updating**

```sh
## Update Packages OS
dnf update -y
```

## Install Drivers  - Hardware Tools

```sh
## Intel Drivers
dnf install -y iucode-tool

## Intel Video
dnf install -y libva-intel-driver xorg-x11-drv-intel mesa-dri-drivers mesa-libGLU

## Hardware Sensors
dnf install -y lm_sensors tuned tuned-utils tuned-gtk acpi acpid acpitool

## Commands
sensors-detect --auto
systemctl enable tuned.service
systemctl start tuned.service
systemctl enable acpid.service
systemctl start acpid.service
```

## Operating System Tools

```sh
## Kernel Add-ons
dnf install -y kernel-headers
dnf install -y kernel-devel
dnf groupinstall -y "Development Tools" 
dnf groupinstall -y "Development Libraries"
```

### Install NVIDIA Driver 390xxx

```bash
## Enable NVIDIA RPM Fusion
dnf config-manager --set-enabled rpmfusion-nonfree-nvidia-driver

## Check Info Driver List
dnf repository-packages rpmfusion-nonfree-nvidia-driver info

## Install Driver
dnf install xorg-x11-drv-nvidia-390xx akmod-nvidia-390xx
dnf install xorg-x11-drv-nvidia-390xx-cuda

## Test Driver
dnf install -y gwe lshw libdazzle
```

### Prompt Git

```bash
## Prompt Git custom on local user directory ~/bashrc
source /usr/share/git-core/contrib/completion/git-prompt.sh
export GIT_PS1_SHOWCOLORHINTS=true
export GIT_PS1_SHOWDIRTYSTATE=true
export GIT_PS1_SHOWUNTRACKEDFILES=true
export PROMPT_COMMAND='__git_ps1 "\[\033[01;33m\]\t\[\033[00m\] \[\033[01;31m\][\W]\[\033[00m\]" " \\\$ "'
```

## Maintainer Packages

```sh
## Packages for create RPM
dnf groupinstall -y "RPM Development Tools"
dnf install -y fedora-packager
```

## Security Group Packages

```sh
## Security Lab
dnf groupinstall -y "Security Lab"

## Command
dnf remove -y xfce4-terminal httpd security-menus
```

## Tools Essentials

```sh
## Gnome Shell Tools
dnf install -y gnome-shell-extension-refresh-wifi gnome-shell-extension-pomodoro \
gnome-tweaks gnome-disk-utility gnome-shell-extension-user-theme gnome-documents \
gnome-games gnome-firmware gnome-extensions-app

## Essentials packages for OS
dnf install -y redhat-lsb-core vim-enhanced curl wget whois telnet nmap 

## Packages for manage versions
dnf install -y git gitg subversion subversion-tools

## Packages NFS Tools - Disks Formats
dnf install -y nfs-utils ntfs-3g ntfsprogs parted gdisk gparted gpart exfat-utils fuse-exfat

## Codecs Multimedia 
dnf install -y gstreamer1-plugins-base gstreamer1-plugins-good gstreamer1-libav \
gstreamer1-plugins-bad-free gstreamer1-plugins-bad-freeworld gstreamer1-plugins-bad-free-extras \
gstreamer1-plugins-good-extras gstreamer1-plugins-ugly gstreamer1-plugins-ugly-free gstreamer1-libav \
gstreamer1-plugins-good-gtk gstreamer1-plugins-good-qt ffmpeg caca-utils gstreamer1 faac faad2

dnf install -y gstreamer1-plugins-{bad-\*,good-\*,base} gstreamer1-plugin-openh264 gstreamer1-libav \
--exclude=gstreamer1-plugins-bad-free-devel

dnf install -y lame\* --exclude=lame-devel

dnf group upgrade -y --with-optional Multimedia

## Alsa Tools
dnf install -y alsa-lib alsa-plugins-pulseaudio alsa-utils 

## Arduino and Raspberry Pi
dnf install -y arduino fritzing arm-image-installer

## Packages for compress and uncompress
dnf install -y unrar p7zip p7zip-plugins unrar unzip

## Java JDK
dnf install -y java

## Tor
dnf install -y torbrowser-launcher torsocks tor

## Extra tools
dnf install -y pv youtube-dl dkms axel android-tools Zim zsh smartmontools speedtest-cli gd glances \
golang putty pwgen rdesktop sl transmission hexchat intltool iotop itop keepassxc lua telegram-desktop \
testssl tmux terminator sqlitebrowser fdupes figlet mediainfo mediainfo-gui pdfmod httpd-tools \
httrack linkchecker ghex gqrx perl-Image-ExifTool glade python3-virtualenv

## Remote Desktop and VNC
dnf install -y vinagre vino
```

### Packages for multimedia

```sh
## Sound and Video
dnf install -y vlc soundconverter vokoscreen peek 
```

### Graphics Design 

```sh 
## Editor images
dnf install -y gimp inkscape inkscape-psd inkscape-view blender dia dia-CMOS dia-Digital \
dia-electric2 dia-electronic dia-gnomeDIAicons dia-optics
```

### Web Browsers 

```sh 
## Default Firefox and Chromium, Email Client
dnf install -y firefox chromium-freeworld elinks geary 

## Add and install Google Chrome
dnf install -y https://dl.google.com/linux/direct/google-chrome-stable_current_x86_64.rpm
```

### Cups Server
    
```sh
## CUPS Server and drivers HP 
dnf install -y cups cups-client cups-libs cups-pdf hplip hplip-libs
```

### SSH Server

```sh
## Remote connection SSH and mosh
dnf install -y openssh-askpass openssh-clients openssh-server openssh sshpass mosh
```

### Vitualization KVM

```sh
## KVM Virtualization
dnf install -y @virtualization 
dnf install -y virt-install virt-manager virt-viewer virt-what bridge-utils
```

### Virtualization VirtualBox

```sh
## Add repository
dnf config-manager --add-repo https://download.virtualbox.org/virtualbox/rpm/fedora/virtualbox.repo

## Update List Packages
dnf update -y 

## Install Virtualbox
dnf install -y VirtualBox-6.0

## Add user on group
usermod -a -G vboxusers $(whoami)
```

### Install VSCode

```sh 
## Import Keys for repo 
rpm --import https://packages.microsoft.com/keys/microsoft.asc
    
## Add Repository
sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'

## Update list packages
dnf update -y 

## Install VSCode
dnf install code
```

### MariaDB

```sh
## Install MariaDB
dnf install mariadb-server mycli

## Command
systemctl enable mariadb.service
systemctl start mariadb.service
mysql_secure_installation
```

### Web Server

```sh
## Apache Web
dnf install -y httpd httpd-tools
```

or

```sh
## Nginx Web
dnf install -y nginx
```

### PHP

```sh
## PHP Fedora
dnf install -y php-cli php-common php-fedora-autoloader php-fpm php-gd php-mbstring php-mysqlnd php-opcache \
php-pdo php-pear php-pecl-apcu php-pecl-mcrypt php-pgsql php-process php-xml
```

### Docker CE

```sh
## Add repository
dnf config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo
    
## Install Docker 
dnf install -y docker-ce docker-ce-cli containerd.io

## Command
systemctl enable docker.service
systemctl start docker.service
usermod -a -G docker $(whoami)

## Install Docker Compose
dnf install docker-compose
```