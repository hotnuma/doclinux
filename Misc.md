

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

* Ubuntu-fr alias thread

    https://forum.ubuntu-fr.org/viewtopic.php?id=20437

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

* ntfs fix
    
    ```
    chkdsk /r d:
    ```
    ```
    sudo ntfsfix /dev/sda1
    ```


<!--

* Hide menu items
    
    https://bbs.archlinux.org/viewtopic.php?id=138015  
    
    ```
    echo "NoDisplay=true" > $HOME/.local/share/applications/hplj1020.desktop
    ```

* List processes
    
    ps_mem : https://github.com/pixelb/ps_mem

    by mem usage
    
    ```
    top -b -o +%MEM | head -n 30
    ```

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

* Win 2K color
    
    ```
    #3B6EA5
    #53708E
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

* misc
    
    ```
    x11-xserver-utils
    libxss-dev
    socat
    ```

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



#### youtube-dl

* RMC Story url

    youtube-dl http://players.brightcove.net/data-account/default_default/index.html?videoId=data-video-id

-->

