**[ [Home](00-Home.html) | [Bugs](01-Bugs.html) | [FFmpeg](01-FFmpeg.html) | [Network](02-Network.html) | [Systemd](03-Systemd.html) | [Wayland](04-Wayland.html) | Other ]**

## Other

---

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



#### Anti-Linux :-D

* System76 accused of not collaborating with GNOME
    
    [https://www.theregister.com/2021/11/10/system76_gnome_deskto](https://www.theregister.com/2021/11/10/system76_gnome_desktop_fight/)

* GNOME to prevent theming, wider community not happy
    
    [https://www.osnews.com/story/133955/gnome-to-prevent-theming](https://www.osnews.com/story/133955/gnome-to-prevent-theming-wider-community-not-happy/)

* The Direction of Gnome
    
    https://forum.zorin.com/t/the-direction-of-gnome/22697/4

* Gtk 5 might drop X11 support
    
    https://www.theregister.com/2022/07/05/gtk_5_might_drop_x11/

* Gnome developers actively hate their users and non-gnome developers
    
    https://news.ycombinator.com/item?id=27075980

* Gnome is the worst major FOSS project
    
    https://news.ycombinator.com/item?id=26002504

* Ulrich Drepper
    
    https://news.ycombinator.com/item?id=2378013

* GNOME Rotting In Threes
    
    [https://igurublog.wordpress.com/2012/11/05/gnome-et-al-rotti](https://igurublog.wordpress.com/2012/11/05/gnome-et-al-rotting-in-threes/)

* Manjarno
    
    https://manjarno.snorlax.sh/


* Gtk
    
    https://github.com/lah7/gtk3-classic  
    https://joshuastrobl.com/2021/09/14/building-an-alternative-ecosystem/  
    https://www.reddit.com/r/GTK/comments/xdfgjr/api_changes_in_gtk4_removal_of_gtkmenu/  
    https://blogs.gnome.org/antoniof/2022/06/15/the-tree-view-is-undead-long-live-the-column-view%e2%80%bd/  
    https://bugzilla.mozilla.org/show_bug.cgi?id=1701123  
    https://medium.com/@fulalas/gnome-42-the-nonsense-continues-7d96c3287f7  
    https://ludditus.com/2021/05/30/is-there-any-future-for-the-gtk-based-desktop-environments/  

    <!--
    https://medium.com/@sarvex/gnome-shell-for-stupids-by-morons-a9020318198b  
    https://fosspost.org/are-gtk-developers-destroying-linux-desktop-with-their-plans/  

    system 76
    https://www.reddit.com/r/linux/comments/xwtns5/does_it_seem_like_gnome_wants_system_76s_cosmic/  
    https://nitter.net/jeremy_soller  
    -->

* Wayland

    [https://gist.github.com/probonopd/...](https://gist.github.com/probonopd/9feb7c20257af5dd915e3a9f2d1f2277)  
    [https://dudemanguy.github.io/blog/...](https://dudemanguy.github.io/blog/posts/2022-06-10-wayland-xorg/wayland-xorg.html)  



<!--

#### Misc

* What's the purpose of ramfs image?

    Linux needs drivers for every type of hardware it might access, and every filesystem type, etc. You can build drivers into the kernel image, but kernel memory is not swappable, so they would be occupying RAM all the time, even if never used. And there are literally a few thousand possible drivers.
    The other option is to build drivers as loadable modules: *.ko files under /lib/modules/. At run time, the system can then load only the modules that are actually needed. But now there is a problem with any drivers that are needed before mounting the root filesystem. You cannot load those from /lib/modules/, which is inside the root filesystem.
    So almost all modern distributions use an initramfs image, which is a tiny filesystem containing just the essential modules, some scripts, and commands such as mount and fsck. The bootloader loads the kernel and initramfs into RAM together, and the kernel uses it is as a temporary root until it can access the real one.
    I have not used Manjaro, but I guess it uses initramfs on all platforms.
    The real question is how does Raspberry Pi OS boot without any initramfs? It can assume it is running on a Pi, so the hardware is much less variable than on a PC. You could never change the GPU, for instance. Also, because it is distributed as a pre-formatted image, it can assume that the rootfs will always be ext4. And the root device can only really be an SD card or USB storage.
    If you wanted to change any of those assumptions, using a different root filesystem type, RAID, LVM, full-disk encryption, network storage, or attaching custom PCI-Express hardware on a Pi4 Compute Module, then it is likely you would need to build an initramfs (or custom kernel) for Pi OS too.

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

* Downmix stereo to mono
    
    https://askubuntu.com/questions/17791/

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



#### Network

* DND BBox 

    ```
    echo "192.168.1.254  mabbox.bytel.fr" >> /etc/hosts
    ```

* interfaces

    The following procedure works for Ubuntu 18.04 (Bionic Beaver)

    I. Reinstall the ifupdown package:

    ```
    sudo apt update
    sudo apt install ifupdown
    ```

    II. Configure your /etc/network/interfaces file with configuration stanzas such as:

    ```
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
    ```

    III. Make the configuration effective (no reboot needed):

    ```
    sudo ifdown --force enp27s0 lo && ifup -a
    sudo systemctl unmask networking
    sudo systemctl enable networking
    sudo systemctl restart networking
    ```

    IV. Disable and remove the unwanted services:

    ```
    sudo systemctl stop systemd-networkd.socket systemd-networkd networkd-dispatcher systemd-networkd-wait-online
    sudo systemctl disable systemd-networkd.socket systemd-networkd networkd-dispatcher systemd-networkd-wait-online
    sudo systemctl mask systemd-networkd.socket systemd-networkd networkd-dispatcher systemd-networkd-wait-online

    sudo apt -y purge nplan netplan.io
    #sudo apt --assume-yes purge nplan netplan.io
    ```

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

    ```
    systemctl restart systemd-resolved
    ```

    The DNS entries in the ifupdown INTERFACES(5) file, as shown above,
    are only relevant if you make use of RESOLVCONF(8) or similar.

* disable network manager

    Using Systemd

    Systemd became the default initialization system in Ubuntu 15.04.
    Here's how to stop and disable Network Manager without uninstalling
    it (taken from AskUbuntu):

    Stop network manager

    ```
    sudo systemctl stop NetworkManager.service
    sudo systemctl stop NetworkManager-wait-online.service
    sudo systemctl stop NetworkManager-dispatcher.service
    sudo systemctl stop network-manager.service
    ```

    Disable network manager (permanently) to avoid it restarting after a reboot

    ```
    sudo systemctl disable NetworkManager.service
    sudo systemctl disable NetworkManager-wait-online.service
    sudo systemctl disable NetworkManager-dispatcher.service
    sudo systemctl disable network-manager.service
    ```

* uninstall network manager

    First edit /etc/network/interfaces so that the ifup utility can be
    used to configure eth0 once NetworkManager is gone.

    Remove NetworkManager from the system

    ```
    sudo apt purge network-manager
    ```

    Configure eth0 using ifup.

    ```
    sudo ifup eth0
    ```

* DNS

    ```
    # check to see if resolvconf is installed
    sudo systemctl status resolvconf.service

    # install resolveconf package
    sudo apt update
    sudo apt install resolvconf

    # confirm resolveconf is running
    sudo systemctl status resolvconf.service

    # if resolveconf isn't running, enable then start it
    sudo systemctl enable resolvconf.service
    sudo systemctl start resolvconf.service

    # check resolveconf status
    sudo systemctl status resolvconf.service

    # edit the head file
    sudo nano /etc/resolvconf/resolv.conf.d/head

    # enter your nameservers below the comments
    nameserver 8.8.8.8
    nameserver 8.8.4.4

    # update resolve.conf file
    sudo resolvconf --enable-updates
    sudo resolvconf -u

    # check if changes we successful
    sudo nano /etc/resolv.conf
    ```

-->

