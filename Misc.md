
#### Articles

* Diagnostic commands
    
    https://forum.ubuntu-fr.org/viewtopic.php?id=2069019  

* Ubuntu-fr alias thread

    https://forum.ubuntu-fr.org/viewtopic.php?id=20437

* Install XFCE Desktop on Debian
    
    [http://linux.how2shout.com/2-ways-to-install-xfce-desktop-on](http://linux.how2shout.com/2-ways-to-install-xfce-desktop-on-debian-11-bullseye/)  

* Display network traffic
    
    [https://askubuntu.com/questions/257263/how-to-display-networ](https://askubuntu.com/questions/257263/how-to-display-network-traffic-in-the-terminal)  
    [https://askubuntu.com/questions/2411/how-do-i-find-out-which](https://askubuntu.com/questions/2411/how-do-i-find-out-which-process-is-eating-up-my-bandwidth)  
    [https://askubuntu.com/questions/532424/how-to-monitor-bandwi](https://askubuntu.com/questions/532424/how-to-monitor-bandwidth-usage-per-process)  
    https://forum.ubuntu-fr.org/viewtopic.php?id=2018157  
    https://forum.ubuntu-fr.org/viewtopic.php?id=443009  
    https://forum.ubuntu-fr.org/viewtopic.php?id=1600291  
    https://doc.ubuntu-fr.org/trafic  
    https://geekflare.com/fr/netstat/  

* Disable gnome-keyring-daemon
    
    https://ubuntuforums.org/showthread.php?t=1655397  
    https://unix.stackexchange.com/questions/271661/  
    https://unix.stackexchange.com/questions/612525/  
    
    ```
    /etc/pam.d/lightdm

    grep -r "gnome-keyring-daemon" /usr/share/dbus-1/services/
    
    /usr/share/dbus-1/services/org.freedesktop.secrets.service
    /usr/share/dbus-1/services/org.gnome.keyring.service
    /usr/share/dbus-1/services/org.freedesktop.impl.portal.Secret.service
    ```

* Gtk File Chooser
    
    https://gitlab.xfce.org/xfce/thunar/-/issues/547  
    [https://www.reddit.com/r/xfce/comments/kk8xo5/file_chooser_b](https://www.reddit.com/r/xfce/comments/kk8xo5/file_chooser_buttons_in_csd_titlebar_not_of/)  
    [https://superuser.com/questions/944119/replace-gtk-file-dial](https://superuser.com/questions/944119/replace-gtk-file-dialog-with-alternative)  

* avahi-daemon:
    
    https://wiki.archlinux.org/title/avahi  
    
    The Avahi mDNS/DNS-SD daemon implements Apple's Zeroconf architectur.
    
    ```
    mem : 1100
    required : no
    ```

* Desktop entries
    
    https://wiki.archlinux.org/title/desktop_entries

* Regex tutorials
    
    [https://www3.ntu.edu.sg/home/ehchua/...](https://www3.ntu.edu.sg/home/ehchua/programming/howto/Regexe.html)  

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

* CPU top processes
    
    https://unix.stackexchange.com/questions/13968/  
    https://stackoverflow.com/questions/1420426/  
    https://stackoverflow.com/questions/1221555/  

    ```
    ps aux k-pcpu | head -6
    ```

* find process by name

    https://www.cyberciti.biz/faq/linux-find-process-name/  
    
    ```
    pidof firefox
    ps aux | grep firefox
    ps aux | grep -i firefox
    pgrep firefox 
    ```

* Block Unwanted Content Using uBlock Origin
    
    [https://www.freecodecamp.org/news/how-to-block-content-from-](https://www.freecodecamp.org/news/how-to-block-content-from-web-pages-using-ublock-origin/)  
    [https://www.reddit.com/r/uBlockOrigin/comments/gja36d/help_n](https://www.reddit.com/r/uBlockOrigin/comments/gja36d/help_needed_modifying_css_with_ublock_origin/)  

* /usr/share/applications/hplj1020.desktop
    
    [https://www.apt-browse.org/browse/debian/jessie/main/all/pri](https://www.apt-browse.org/browse/debian/jessie/main/all/printer-driver-foo2zjs-common/20140925dfsg0-3/file/usr/share/applications/hplj1020.desktop)  

* XOrg TearFree Page-Flipping Merged
    
    https://www.phoronix.com/news/Modesetting-TearFree-Merged

* Command fd not found
    
    https://github.com/sharkdp/fd/issues/791

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

* max pid value
    
    ```
    cat /proc/sys/kernel/pid_max

    4194304
    ```
    
* Downmix stereo to mono
    
    https://askubuntu.com/questions/17791/

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


#### Drives and Power Manager

* Reset IDLE time
    
    https://askubuntu.com/questions/1323618/  

* Stop dkms from blanking the screen
    
    ```
    xset dpms force off
    ```

* turn off screen

    https://superuser.com/questions/374637/how-to-turn-off-screen-with-shortcut-in-linux  
    https://qastack.fr/superuser/31726/how-to-disable-the-screen-linux-without-x  

* ntfs fix
    
    ```
    chkdsk /r d:
    ```

* Power manager

    https://wiki.archlinux.org/title/Display_Power_Management_Signaling



#### Text utils

* Text encoding detector
    
    https://gitlab.freedesktop.org/uchardet/uchardet  
    https://github.com/Joungkyun/libchardet  
    https://utrac.sourceforge.net/  

* Format output to a specific line length
    
    https://unix.stackexchange.com/questions/146089/  



#### Themes

* Libadwaita theme for xfwm4
    
    https://github.com/lassekongo83/adw-gtk3  
    https://github.com/FabianOvrWrt/adw-xfwm4  

* Windows 95 theme
    
    https://github.com/grassmunk/Chicago95

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



#### Image Viewers

* City-busz/gpicview
    
    https://github.com/City-busz/gpicview/tree/gtk3

* hellosiyan/Viewnior
    
    https://github.com/hellosiyan/Viewnior

* phillipberndt/pqiv
    
    https://github.com/phillipberndt/pqiv

* 4 lightweight image viewers for the Linux desktop
    
    [https://opensource.com/article/17/7/4-lightweight-image-view](https://opensource.com/article/17/7/4-lightweight-image-viewers-linux-desktop)



#### youtube-dl

* RMC Story url

    youtube-dl http://players.brightcove.net/data-account/default_default/index.html?videoId=data-video-id



#### Wayland

* References
    
    https://wiki.archlinux.org/title/wayland  

* awesome-wayland : a curated list of Wayland code and resources
    
    https://github.com/natpen/awesome-wayland  

* wlroots : a modular Wayland compositor library
    
    https://gitlab.freedesktop.org/wlroots/wlroots  

* Labwc : a Wayland stacking compositor
    
    https://github.com/labwc/labwc  

* Xfce Xfwm4
    
    https://github.com/adlocode/xfwm4/tree/wlroots  

* Waybar : a highly customizable Wayland bar
    
    https://github.com/Alexays/Waybar  

* Yes another task bar for Wayland
    
    https://github.com/selairi/yatbfw  

* Wayward
    
    https://github.com/varmd/wayward


