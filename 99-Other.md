**[ [Home](00-Home.html) | [Bugs](01-Bugs.html) | [FFmpeg](01-FFmpeg.html) | [Network](02-Network.html) | [Systemd](03-Systemd.html) | [Wayland](04-Wayland.html) | Other ]**

### Other

---

<!--
#### Reference

* Simplified LFS
    
    https://github.com/luisgbm/lfs-scripts  











#### Git

* Basics

    [Git status doesn’t know if your local repository is out of date · Mike F. Robbins](https://mikefrobbins.com/2016/02/18/git-status-doesnt-know-if-your-local-repository-is-out-of-date/)

    [les commandes Git que vous devez absolument connaitre!](https://www.hostinger.fr/tutoriels/commandes-git)

    [Access token](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token)

    [An Intro to Git](https://product.hubspot.com/blog/git-and-github-tutorial-for-beginners)

    [Authenticate Token](https://stackoverflow.com/questions/18935539/authenticate-with-github-using-a-token)

    [Git Guide](https://github.com/git-guides/)

    [Line endings](https://docs.github.com/en/github/getting-started-with-github/configuring-git-to-handle-line-endings)

    [Main vs Master](https://stackoverflow.com/questions/64249491/difference-between-main-branch-and-master-branch-in-github)

    [Remote Origin](https://stackoverflow.com/questions/6565357/git-push-requires-username-and-password)

#### Raspi

* Custom OS
    
    https://forums.raspberrypi.com/viewtopic.php?t=327060

* XML libraries
    
    https://forums.raspberrypi.com/viewtopic.php?p=1958438#p1958438
    
* Double click bug

    https://discourse.gnome.org/t/double-click-on-already-selected-item-will-often-not-open-item-in-nautilus/4590/5
    https://gitlab.gnome.org/GNOME/nautilus/-/issues/1599
    
    GTK version :
    
    ```
    libgtk-3-0:amd64 3.24.25-1ubuntu4.1 amd64 
    ```

* Test RPi version

    https://forums.raspberrypi.com/viewtopic.php?t=34678  
    https://forums.raspberrypi.com/viewtopic.php?t=200059

    ```
    ARCH=$(uname -m)
    VERSION=$(cat /etc/debian_version)
    if [[ $ARCH != "aarch64" ]] || [[ $VERSION != 11* ]]; then
        echo " *** This script was tested only on a Raspberry Pi 4B 64 bit"
        echo " *** abort..."
        exit 1
    fi

    cat /proc/cpuinfo
    grep -q BCM2708 /proc/cpuinfo
    cat /etc/*-release
    cat /proc/device-tree/model
    cat /sys/firmware/devicetree/base/model
    ```
* Command line piclone
    
    https://forums.raspberrypi.com/viewtopic.php?t=180383

* Default audio playback
    
    https://forums.raspberrypi.com/viewtopic.php?t=327267#p1958987
    
* C++ SSD1306 I2C LCD
    
    https://forums.raspberrypi.com/viewtopic.php?t=224984  
    https://forums.raspberrypi.com/viewtopic.php?t=171817
    
* Chromium/Youtube audio choppy with Bullseye and KMS driver

    https://forums.raspberrypi.com/viewtopic.php?p=1945157#p1935815

* RPi4 with PiOS ignore display setting in config.txt

    https://forums.raspberrypi.com/viewtopic.php?p=1945199#p1945199

* Display issue with Bullseye image and Pi 4B

    https://forums.raspberrypi.com/viewtopic.php?p=1945198#p1945198

* RPi4 HW Acceleration
    
    https://forums.raspberrypi.com/viewtopic.php?t=325586
    
* Chromium 88 HW
    
    https://forums.raspberrypi.com/viewtopic.php?t=319304

#### Manjaro

* LXDE profiles and settings

    https://forum.manjaro.org/t/lxde-lxqt-openbox-community-iso/77471  
    [https://gitlab.manjaro.org/profiles-and-settings/](https://gitlab.manjaro.org/profiles-and-settings/iso-profiles/-/blob/master/community/lxde/Packages-Desktop)

* Brcm patchram plus
    
    https://forum.manjaro.org/t/arm-testing-update-2020-11-16-bitwarden-mesa-git-pacman-and-kernels/37996/19  
    https://forum.manjaro.org/t/brcm-patchram-plus-conflict-with-pi-bluetooth/37935

* Mpv
    
    https://forum.manjaro.org/t/possible-rpi-mpv-hwdec-v4l2m2m-copy-solution/96636
    
#### Ubuntu
    
    * Uninstall block snaps
    
    https://forum.ubuntu-fr.org/viewtopic.php?pid=22458861#p22458861
    
#### Wayland

* Wayward
    
    https://github.com/varmd/wayward
    
---

- Usefull commands
- Wayland
- Raspi
- Misc
- Log files
- CPU governor
- Packages
- youtube-dl

#### Firefox

* Webrender

	https://www.google.com/search?q=raspberry+pi+webrender  
	https://bugzilla.mozilla.org/show_bug.cgi?id=1663285  
	https://forum.manjaro.org/t/firefox-webrender-pi4-400/63702
		
	https://forums.raspberrypi.com/search.php?keywords=webrender

	https://www.google.com/search?q=raspberry+pi+firefox+webrender

	https://bugzilla.mozilla.org/show_bug.cgi?id=1663285

	```
	gfx.webrender.all to true
	Run 'MOZ_X11_EGL=1 firefox' in terminal
	```
	
	https://bugzilla.mozilla.org/show_bug.cgi?id=1725624

	https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1930982

#### Raspberry Pi

* USB Chipset
    
    https://forums.raspberrypi.com/viewtopic.php?t=326157
    
    ```
    That's true for most of the JMS578 family of USB 3.0 bridge chips,
    but not necessarily with the 580 series USB 3.1 chips.
    I have a USB 3.1 Gen 2 enclosure with a JMS583 chip that works
    fine with Pi computers. It supports UASP in RPiOS, and TRIM works
    with a udev rule.
    ```
    
* Custom RPi images
	
	https://forums.raspberrypi.com/viewtopic.php?f=131&t=314419
	
#### Manjaro

https://forum.manjaro.org/tag/raspberry-pi-4
https://forum.manjaro.org/t/arm-stable-update-2021-12-13-firefox-kde-gear-thunderbird-libreoffice-icu-and-kernels/94518

https://forum.manjaro.org/t/additional-arm-packages/10132  
https://gitlab.manjaro.org/manjaro-arm

* bcrm_patchram_plus

    https://forum.manjaro.org/t/bcrm-patchram-plus-at-100-cpu-utilization/51035/4

    ```
    sudo systemctl disable attach-bluetooth.service
    sudo chmod 000 /usr/bin/brcm_patchram_plus
    ```

* Vivaldi

    https://help.vivaldi.com/fr/desktop-fr/install-update-fr/raspberry-pi-astuces-pour-utiliser-vivaldi/

    ```
    wget https://downloads.vivaldi.com/snapshot/install-vivaldi.sh
    sh install-vivaldi.sh
    ```

#### Mini PC

£140.00 ChromeBox  
£25 for a 4GB memory module

Gemnes - Chromebox – Mini PC Windows 10,  
processeur Intel 3865U 8e génération,  
double 4k, USB type-c PD, 4G-DDR4, 32G-mSATA

https://fr.aliexpress.com/item/32966393971.html

https://ark.intel.com/content/www/us/en/ark/products/96507/

Intel® Celeron® Processor 3865U  
2M Cache, 1.80 GHz

#### Sysconfig

* Manjaro update error 

    ```
    error: failed to commit transaction (conflicting files)
    rpi4-post-install: /etc/udev/rules.d/99-vcio-rewrite.rules exists in filesystem
    ```
    fix
    ```
    sudo pacman -Syu --overwrite /etc/udev/rules.d/99-vcio-rewrite.rules
    ```

#### Links 

references :

https://specifications.freedesktop.org/  
https://askubuntu.com/questions/1179729/where-is-xdg-config-dirs-set  
https://www.nongnu.org/xbindkeys/xbindkeys.html

display settings :

video=HDMI-1:800x480@60

https://forums.raspberrypi.com/viewtopic.php?t=325011#p1945199

chromium crash :

https://forums.raspberrypi.com/viewtopic.php?t=323640&start=75#p1940502

firefox :

https://forum.manjaro.org/t/new-mesa-drivers/39735  
https://forum.manjaro.org/t/firefox-webrender-pi4-400/63702

#### Compton

https://www.youtube.com/watch?v=3esPpe-fclI  
https://gist.github.com/kelleyk/6beba22586ac0c40aa30  
compton --backend glx --unredir-if-possible --vsync opengl-swc
compton --backend glx --vsync opengl-swc

#### Bugs

* Syslog

    kernel: v3d fec00000.v3d: MMU error from client L2T  
    https://forums.raspberrypi.com/viewtopic.php?t=277917  
    http://tabuas.tech/2021/05/19/pi-400-log/

* Mutter

    ```
    (mutter:2044): Clutter-WARNING **: 07:06:58.281: Bogus presentation time 0 travelled back in time, using current time.

    (mutter:2044): Clutter-WARNING **: 07:07:28.733: Can't update stage views actor MetaStage is on because it needs an allocation.

    (mutter:2044): Clutter-WARNING **: 07:07:28.734: Can't update stage views actor MetaWindowGroup is on because it needs an allocation.

    (mutter:2044): Clutter-WARNING **: 07:07:28.734: Can't update stage views actor MetaWindowActorX11 is on because it needs an allocation.
    ```
    
* Pixel wrap bug fix

    ```
    Jun 24 2021 17:24:58 
    Copyright (c) 2012 Broadcom
    version 65aff9e0bea5b64c530db52aa4497e809fdf22c8 (clean) (release) (start)
    Linux raspberrypi 5.10.44-v8+ #1429 SMP PREEMPT Fri Jun 25 10:03:37 BST 2021 aarch64 GNU/Linux
    ```

#### Usefull commands

* Diagnostic commands
    
    https://forum.ubuntu-fr.org/viewtopic.php?id=2069019

* Eject USB drives
    
    https://unix.stackexchange.com/questions/35508/
    
* CPU top processes
    
    https://unix.stackexchange.com/questions/13968/  
    https://stackoverflow.com/questions/1420426/  
    https://stackoverflow.com/questions/1221555/

    ```
    ps aux k-pcpu | head -6
    ```

* find process by name

    https://www.cyberciti.biz/faq/linux-find-process-name/
    
    pidof firefox
    ps aux | grep firefox
    ps aux | grep -i firefox
    pgrep firefox 

* mount NTFS partition
    
    https://superuser.com/questions/1049044/

* Check drive spin down

    https://superuser.com/questions/173622/

* Reset IDLE time
    
    https://askubuntu.com/questions/1323618/

* Stop dkms from blanking the screen
    
    ```
    xset dpms force off
    ```

* turn off screen

    https://superuser.com/questions/374637/how-to-turn-off-screen-with-shortcut-in-linux  
    https://qastack.fr/superuser/31726/how-to-disable-the-screen-linux-without-x

#### Misc

* What's the purpose of ramfs image?

    Linux needs drivers for every type of hardware it might access, and every filesystem type, etc. You can build drivers into the kernel image, but kernel memory is not swappable, so they would be occupying RAM all the time, even if never used. And there are literally a few thousand possible drivers.
    The other option is to build drivers as loadable modules: *.ko files under /lib/modules/. At run time, the system can then load only the modules that are actually needed. But now there is a problem with any drivers that are needed before mounting the root filesystem. You cannot load those from /lib/modules/, which is inside the root filesystem.
    So almost all modern distributions use an initramfs image, which is a tiny filesystem containing just the essential modules, some scripts, and commands such as mount and fsck. The bootloader loads the kernel and initramfs into RAM together, and the kernel uses it is as a temporary root until it can access the real one.
    I have not used Manjaro, but I guess it uses initramfs on all platforms.
    The real question is how does Raspberry Pi OS boot without any initramfs? It can assume it is running on a Pi, so the hardware is much less variable than on a PC. You could never change the GPU, for instance. Also, because it is distributed as a pre-formatted image, it can assume that the rootfs will always be ext4. And the root device can only really be an SD card or USB storage.
    If you wanted to change any of those assumptions, using a different root filesystem type, RAID, LVM, full-disk encryption, network storage, or attaching custom PCI-Express hardware on a Pi4 Compute Module, then it is likely you would need to build an initramfs (or custom kernel) for Pi OS too.

* Firefox config
    
    about:config
    
    ```
    browser.sessionstore.resume_from_crash false
    layers.acceleration.force-enabled true
    layers.gpu-process.enabled true
    media.gpu-process-decoder true
    ```

* Remove Snap completely

    https://askubuntu.com/questions/1369159/

* Ubuntu upgrade

    ```
    sudo do-release-upgrade
    ```
    Troubles can come from third party repositories or orphan packages
    
    ```
    cat /etc/apt/sources.list
    ls /etc/apt/sources.list.d
    cat /etc/apt/sources.list.d/*.list
    apt list | grep "installé, local"
    ```

* Install desktop using tasksel

    ```
    sudo apt install tasksel
    sudo tasksel
    ```
    Press space to select a desktop, then select Ok.
    
    ```
    sudo update-alternatives --config x-session-manager
    ```
    Select a session.

* glamor
    
    /usr/share/X11/xorg.conf.d/20-noglamor.conf

* Downmix stereo to mono
    
    https://askubuntu.com/questions/17791/

* Xfce Classic Fork
    
    [https://www.linuxadictos.com/en/xfce-classic](https://www.linuxadictos.com/en/xfce-classic-a-fork-of-xfce-but-without-the-client-side-window-decoration.html)

* Delete thumbnails older than 30 days

    find ~/.cache/thumbnails/ -type f -iname \*.png -mtime +30 -delete

* Power manager

    https://wiki.archlinux.org/title/Display_Power_Management_Signaling

* Modifiy Themes

    https://askubuntu.com/questions/1170151/  
    https://github.com/surajmandalcell/Gtk-Theming-Guide/blob/master/creating_gtk_themes.md
    
    ```
    sassc
    ```
* Ubuntu-fr alias thread

    https://forum.ubuntu-fr.org/viewtopic.php?id=20437

* Win 2K color
    
    ```
    #3B6EA5
    #53708E
    ```

* max pid value
    
    ```
    cat /proc/sys/kernel/pid_max

    4194304
    ```
    
* Disable at-spi
    
    According to https://wiki.archlinux.de/title/GNOME#Tipps_und_Tricks
    
    ```
    export NO_AT_BRIDGE=1

    in /etc/environment.
    ```
    or
    ```
    ~/.profile
    ```
* diagnostics
    
    ```
    sudo dmesg | tail -30
    ls -l /var/crash
    ```
* dmesg

    Pour le dmesg c'est un paramètre du noyau (et c'est bien qu'il soit activé) :

    ```
    sudo sysctl -a | grep dmesg
    kernel.dmesg_restrict = 1
    ```

    Si cela te gêne il suffit de modifier le fichier /etc/sysctl.d/10-kernel-hardening.conf en changeant la valeur :

    ```
    kernel.dmesg_restrict = 0
    ```

    Si tu as accès avec journalctl aux log du système (ou des autres utilisateurs) c'est que l'utilisateur est dans le groupe wheel ou adm :

    ```
    journalctl | head -2
    ```
    
    Hint: You are currently not seeing messages from other users and the system.
    Users in groups 'adm', 'systemd-journal' can see all messages.
    Pass -q to turn off this notice.

* ntfs fix
    
    ```
    chkdsk /r d:
    ```
    ```
    sudo ntfsfix /dev/sda1
    ```

* misc
    
    x11-xserver-utils
    libxss-dev
    socat

* Mate desktop utils
    
    https://github.com/mate-desktop/mate-utils  
    
* disable gnome-keyring-daemon
    
    https://unix.stackexchange.com/questions/271661/    
    https://ubuntuforums.org/showthread.php?t=1655397
    
    ```
    /etc/pam.d/lightdm
    /usr/share/dbus-1/services/
    ```

#### Log files

* Viewing log files

    https://ubuntu.com/tutorials/viewing-and-monitoring-log-files

* View System Log

    https://vitux.com/view-system-log-files-ubuntu/

#### CPU governor

https://askubuntu.com/questions/1021748/  
https://raspberrypi.stackexchange.com/questions/9034/

#### Packages

* pour purger les caches du gestionnaire de paquets APT/.deb
    ```
    sudo apt clean ; sudo apt autoclean
    ```
* paquets cassés

    https://forum.ubuntu-fr.org/viewtopic.php?pid=22273320#p22273320
    ```
    dpkg -l | grep -v ^ii

    dpkg -l | awk '/^rc/{print $2}' | xargs -r sudo dpkg -P
    ```
    
#### youtube-dl

* ytdl

    https://ytdl-org.github.io/youtube-dl/download.html
    
    ```
    sudo apt -y purge youtube-dl
    sudo apt install python3-pip
    sudo pip install --upgrade youtube_dl
    ```

* RMC Story url

    youtube-dl http://players.brightcove.net/data-account/default_default/index.html?videoId=data-video-id


---

* A trip into dbus-send
    
    https://sheitsandgiggles.com/2019/07/16/a-trip-into-dbus-send/

* An example Linux daemon using DBus
    
    https://gist.github.com/dradtke/4949546

* DFeet
    
    https://wiki.gnome.org/action/show/Apps/DFeet?action=show&redirect=DFeet

* DBus tutorial using the low-level API
    
    [https://leonardoce.wordpress.com/2015/03/11/](https://leonardoce.wordpress.com/2015/03/11/dbus-tutorial-using-the-low-level-api/)

* Dbus using C API
    
    https://stackoverflow.com/questions/43118430/

* dbus
    
    https://www.freedesktop.org/wiki/Software/dbus/

* How to Send Dbus Messages Manually
    
    https://developer.ridgerun.com/wiki/index.php/How_to_send_Dbus_messages_manually

* Introspecting D-Bus from the command-line
    
    http://www.kaizou.org/2014/06/dbus-command-line.html

* How to emit dbus signal from command line
    
    https://stackoverflow.com/questions/3684999/how-to-emit-dbus-signal-from-command-line

* stuff_dbus-example_c
    
    https://github.com/wware/stuff/blob/master/dbus-example/dbus-example.c

---

# FFmpeg

    https://trac.ffmpeg.org/wiki
    http://ffmpeg.org/documentation.html
    https://ffmpeg.org/ffmpeg-filters.html
    https://trac.ffmpeg.org/wiki/FFprobeTips

* Obtenir des informations sur le fichier

    ffprobe -v quiet -show_format -show_streams "input.avi"

* Créer un extrait de 1 min à partir de 2 min du début

    ffmpeg -ss 00:02:00 -i "input.avi" -t 00:01:00 -c copy "output.avi"

* Copier un extrait de 1 min avec uniquement la vidéo

    ffmpeg -ss 00:02:00 -i "input.avi" -t 00:01:00 -map 0:0 -c copy "output.avi"

* Copier un extrait de 1 min avec uniquement l'audio

    ffmpeg -ss 00:02:00  -i "input.avi" -t 00:01:00 -map 0:1 -c copy "output.avi"

#### Audio

* Filtrer l'audio :

    ffmpeg -i "input.mp4" -c:v copy -af "highpass=f=100" "output.mp4"

#### Images

    On peut modifier les options de VLC pour qu'il utilise une numérotation séquencielle.
    Dans Options/Préférences, Video, cocher la case "Numérotation séquentielle".

* 2x2 images, chacune de 333px de large :

    ffmpeg -i "vlcsnap-%05d.png" -vf "scale=333:-1,tile=2x2" "output.png"

* 3x3 images, chacune de 111px de large :

    ffmpeg -i "vlcsnap-%05d.png" -vf "scale=111:-1,tile=3x3" "output.png"

    "%05d" signifie, un nombre de 5 chiffres, par exemple vlcsnap-00001.png.

    A noter que les images doivent être consécutives,
    exemple pic-001.png, pic-002.png, pic-003.png etc...

* Créer automatiquement à partir d'une série de captures d'écran :

    ffmpeg -i "input.avi" -frames 1 -vf "select=not(mod(n\,7600)),scale=111:-1,tile=4x4" "output.png"

#### Other

* Créer une capture d'écran toutes les 5 minutes :

    ffmpeg -i "input.avi" -vf fps=1/300 "pic-%03d.png"

    (300 = 5 x 60 secondes)

* Appliquer le même traitement sur une série d'images :

    ffmpeg -y -i "input-%03d.png" -vf "scale=666:-1" "output-%03d.png"

* Concatenating files

    concat VOB files      
    copy /b *.vob output.vob
    cat file*.vob > Allfiles.vob

* Enregistrer un flux en direct

    ffmpeg -i http://live.francetv.fr/simulcast/France_3/hls_v1/index.m3u8 \
    -bsf:a aac_adtstoasc -c:a copy -c:v copy output.mp4

* Utiliser un preset

    ffmpeg -i "input.mp4" -preset ultrafast -crf 18 "output.mp4"
    ffmpeg -i "input.mp4" -preset slow -crf 18 "output.mp4"

    Le preset détermine la compression et par conséquent la qualité et la taille du fichier.
    La valeur par défaut est "médium". Les valeurs plus rapides sont fast, faster, veryfast,
    superfast, ultrafast. Les valeurs plus lents sont, slow, slower, veryslow, placebo.

* Upscale and unsharp with default values :

    ffmpeg -i input.mp4 -vf "scale=640:480:flags=lanczos,unsharp" output.mp4
    ffmpeg -i input.mp4 -vf "scale=640:480,unsharp" -sws_flags lanczos output.mp4

    For downscaling use Lanczosresize only
    For upscaling use Bicubicresize with 0.45 to 0.6 sharpening.    

* Diaporama

    ffmpeg -framerate 1/12 -i pic-%03d.png -c:v libx264 -r 25 -pix_fmt yuv420p out.mp4
    ffmpeg -i "vlcsnap-%05d.png" -vf "scale=-1:480,pad=640:480:154:0" "input-%05d.png"

    Add metadata :

    ffmpeg -i "input.avi" -c copy -metadata title="Le schpountz" "output.avi"
    ffmpeg -i "input.avi" -c copy -map_metadata -1 -metadata title="1938 - Le schpountz" -metadata comment="tt0030722" "output.avi"

    ffmpeg -i [INPUT] -aspect 4:3 -c copy [OUPTPUT]

    ffmpeg -ss 00:00:14 -i "D:/Films/Convert/1945 - Carmen-orig.mp4" \
    -deinterlace -b:v 1200k -vf hue=s=0,crop=704:566:0:2 "1945 - Carmen-orig.mp4"

    ffmpeg -i "D:/Films/Films 4-7/1935 - La Kermesse héroïque.avi" \
    -b:v 1000k -vf scale=720:576 "1935 - La Kermesse héroïque.avi"

    ffmpeg -t 01:51:20 -i "D:/Films Supprimer/1945 - La vie de boheme.ts" \
    -b:v 1000k -deinterlace -vf crop=530:566:91:2 -aspect 4:3

    ffmpeg -i "D:/Films/Convert/1929 - Adieu Mascotte.mp4" -preset ultrafast \
    -crf 22 -deinterlace -r 25 -vf crop=626:470:8:6 "1929 - Adieu Mascotte.mp4"

    ffmpeg -y -i "1934 - Caravane-orig.mp4" -preset slow -vsync 0 -crf 22 \
    -vf hue=s=0,crop=938:704:15:3,unsharp=3:3:0.4 -af highpass=f=100 "1934 - Caravane.mp4"

    ffmpeg -y -t 01:34:46 -i "D:/Films Selection/_1935 - L'École des cocottes.avi" -crf 18 \
    -preset slow -vsync 0 -vf hue=s=0,crop=680:544:14:14,unsharp=3:3:0.3 -b:a 256k \
    "1935 - L'École des cocottes-unsharp303.mp4"

    ffmpeg -y -t 01:29:54 -i "D:/Films Convert/1941 - Valet Maitre.mkv" -b:v 2000k \
    -preset slow -vsync 0 -vf hue=s=0,crop=710:568:0:0,unsharp=3:3:0.3 "1941 - Valet Maitre.mp4"

    "Too many packets buffered for output stream"

    -max_muxing_queue_size 1024

    ffmpeg -framerate 1/2 -loop 1 -t 1 -i NWL1.png -framerate 60 -loop 1 -t 1 -i NWL2.png -framerate 60 -loop 1 -t 1 -i NWL3.png -framerate 60 -loop 1 -t 1 -i NWL4.png -framerate 60 -loop 1 -t 1 -i NWL5.png -filter_complex "[1:v][0:v]blend=all_expr='A*(if(gte(T,0.5),1,T/0.5))+B*(1-(if(gte(T,0.5),1,T/0.5)))'[b1v]; [2:v][1:v]blend=all_expr='A*(if(gte(T,0.5),1,T/0.5))+B*(1-(if(gte(T,0.5),1,T/0.5)))'[b2v]; [3:v][2:v]blend=all_expr='A*(if(gte(T,0.5),1,T/0.5))+B*(1-(if(gte(T,0.5),1,T/0.5)))'[b3v]; [4:v][3:v]blend=all_expr='A*(if(gte(T,0.5),1,T/0.5))+B*(1-(if(gte(T,0.5),1,T/0.5)))'[b4v]; [0:v][b1v][1:v][b2v][2:v][b3v][3:v][b4v][4:v]concat=n=9:v=1:a=0,format=yuv420p,scale=480:270[vx]" -map "[vx]" -c:v libx264 -r 30 -pix_fmt yuv420p "EXfondu2.mp4"

    ffmpeg -i "video.mp4"  -i "audio.mp3" -c copy -shortest "output.mp4"

    youtube-dl --extract-audio --audio-format mp3 -l "https://www.youtube.com/watch?v=xN8Q75ov6A4"

* remux avi to mp4

    avi2raw.exe -v "D:\Films\Films 3-8\1936 - Topaze.avi" "1936 - Topaze.264"
    avi2raw.exe -a "D:\Films\Films 3-8\1936 - Topaze.avi" "1936 - Topaze.aac"
    ffmpeg -i "D:\Films\Films 3-8\1936 - Topaze.avi" -vn -c:a copy "1936 - Topaze.aac"
    mp4box.exe -add "1936 - Topaze.264" -fps 25 -add "1936 - Topaze.aac" "1936 - Topaze.mp4"
    ffmpeg -i input.mkv -itsoffset 1.0 -i input.mkv -map 0:0 -map 1:1 -c copy output.mkv   
    ffmpeg -ss 00:00:33.5 -i "D:\Downloads\Invitation.to.the.Waltz.1935.mkv" \
    -c copy -avoid_negative_ts 1 "D:\Downloads\1935 - Invitation to the Waltz.mkv"

* screenshot

    ffmpeg -ss 00:00:30 -i "D:\Films\Convert\1937 - Forfaiture-0.mkv" -vframes 1 -q:v 2 output.jpg


---

# Network

* DND BBox 

    echo "192.168.1.254  mabbox.bytel.fr" >> /etc/hosts

* interfaces

    The following procedure works for Ubuntu 18.04 (Bionic Beaver)

    I. Reinstall the ifupdown package:

    sudo apt update
    sudo apt install ifupdown

    II. Configure your /etc/network/interfaces file with configuration stanzas such as:

    # The loopback network interface
    auto lo
    iface lo inet loopback

    auto enp27s0
    iface enp27s0 inet dhcp

    # The loopback network interface
    auto lo
    iface lo inet loopback

    allow-hotplug enp27s0
    auto enp27s0
    iface enp27s0 inet static
    address 192.168.1.100
    netmask 255.255.255.0
    broadcast 192.168.1.255
    gateway 192.168.1.254
    # Only relevant if you make use of RESOLVCONF(8)
    # or similar...
    dns-nameservers 8.8.8.8 8.8.4.4

    III. Make the configuration effective (no reboot needed):

    sudo ifdown --force enp27s0 lo && ifup -a
    sudo systemctl unmask networking
    sudo systemctl enable networking
    sudo systemctl restart networking

    IV. Disable and remove the unwanted services:

    sudo systemctl stop systemd-networkd.socket systemd-networkd networkd-dispatcher systemd-networkd-wait-online
    sudo systemctl disable systemd-networkd.socket systemd-networkd networkd-dispatcher systemd-networkd-wait-online
    sudo systemctl mask systemd-networkd.socket systemd-networkd networkd-dispatcher systemd-networkd-wait-online

    sudo apt -y purge nplan netplan.io
    #sudo apt --assume-yes purge nplan netplan.io

    Then, you're done.

    Note: You MUST, of course, adapt the values according to your system
    (network, interface name...).

    V. DNS Resolver

    Because Ubuntu Bionic Beaver (18.04) make use of the DNS stub
    resolver as provided by SYSTEMD-RESOLVED.SERVICE(8), you SHOULD
    also add the DNS to contact into the /etc/systemd/resolved.conf
    file. For instance:

    ....
    DNS=1.1.1.1 1.0.0.1
    ....

    and then restart the systemd-resolved service once done:

    systemctl restart systemd-resolved

    The DNS entries in the ifupdown INTERFACES(5) file, as shown above,
    are only relevant if you make use of RESOLVCONF(8) or similar.

* disable network manager

    Using Systemd

    Systemd became the default initialization system in Ubuntu 15.04.
    Here's how to stop and disable Network Manager without uninstalling
    it (taken from AskUbuntu):

    Stop network manager

    sudo systemctl stop NetworkManager.service
    sudo systemctl stop NetworkManager-wait-online.service
    sudo systemctl stop NetworkManager-dispatcher.service
    sudo systemctl stop network-manager.service

    Disable network manager (permanently) to avoid it restarting after a reboot

    sudo systemctl disable NetworkManager.service
    sudo systemctl disable NetworkManager-wait-online.service
    sudo systemctl disable NetworkManager-dispatcher.service
    sudo systemctl disable network-manager.service

* uninstall network manager

    First edit /etc/network/interfaces so that the ifup utility can be
    used to configure eth0 once NetworkManager is gone.

    Remove NetworkManager from the system

    sudo apt purge network-manager

    Configure eth0 using ifup.

    sudo ifup eth0

* DNS

    CODE:
    (check to see if resolvconf is installed)
    sudo systemctl status resolvconf.service

    (install resolveconf package)
    sudo apt update
    sudo apt install resolvconf

    (confirm resolveconf is running)
    sudo systemctl status resolvconf.service

    (if resolveconf isn't running, enable then start it)
    sudo systemctl enable resolvconf.service
    sudo systemctl start resolvconf.service

    (check resolveconf status)
    sudo systemctl status resolvconf.service

    (edit the head file)
    sudo nano /etc/resolvconf/resolv.conf.d/head

    (enter your nameservers below the comments)
    nameserver 8.8.8.8
    nameserver 8.8.4.4

    (update resolve.conf file)
    sudo resolvconf --enable-updates
    sudo resolvconf -u

    (check if changes we successful)
    sudo nano /etc/resolv.conf

-->


