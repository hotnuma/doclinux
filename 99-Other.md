<link href="style.css" rel="stylesheet"></link>

**[ [Home](00-Home.html) | [Systemd](01-Systemd.html) | [Network](02-Network.html) | [FFmpeg](03-FFmpeg.html) | [Bugs](04-Bugs.html) | Other ]**

## Other

---

#### Forums

84 https://forums.linuxmint.com/search.php?search_id=active_topics  
59 https://forums.raspberrypi.com/search.php?search_id=active_topics  
41 https://ubuntuforums.org/search.php?do=getnew&contenttype=vBForum_Post  
39 https://forum.manjaro.org/latest  
23 https://forum.mxlinux.org/search.php?search_id=active_topics  
16 https://forum.ubuntu-fr.org/search.php?action=show_recent  
14 https://forums.debian.net/search.php?search_id=active_topics  

08 https://forum-francophone-linuxmint.fr/search.php?search_id=active_topics  
06 https://www.debian-fr.org/latest  
05 https://debian-facile.org/search.php?action=show_recent  
03 https://forum-debian.fr/  
04 https://forum.palemoon.org/search.php?search_id=active_topics  


#### Articles

* Set  default audio output
    
    https://askubuntu.com/questions/1038490/  


#### Processes / Services

https://debian-facile.org/viewtopic.php?pid=254022#p254022  
    
* polkitd polkit-gnome-authentication-agent-1
    
    https://www.freedesktop.org/software/polkit/docs/latest/polkit.8.html  
    https://wiki.archlinux.org/title/Polkit  
    
    Polkit is used for controlling system-wide privileges. It provides an organized way for non-privileged processes to communicate with privileged ones. In contrast to systems such as sudo, it does not grant root permission to an entire process, but rather allows a finer level of control of centralized system policy.
    
    mem : 11543

* udisksd
    
    https://wiki.archlinux.org/title/udisks  
    
    udisks provides a daemon udisksd, that implements D-Bus interfaces used to query and manipulate storage devices, and a command-line tool udisksctl, used to query and use the daemon.
    
    mem : 6010

* systemd-resolved
    
    https://wiki.archlinux.org/title/systemd-resolved  
    
    `systemd-resolved` is a systemd service that provides network name resolution to local applications via a D-Bus interface, the resolve NSS service (nss-resolve), and a local DNS stub listener on 127.0.0.53.
    
    mem : 5850

* systemd-udevd
    
    https://linuxembedded.fr/2018/03/kernel-udev-et-systemd-la-gestion-du-hotplug  
    
    `systemd-udevd` listens to kernel uevents. For every event, systemd-udevd executes matching instructions specified in udev rules.
    
    mem : 2722

* gnome-keyring-daemon
    
    https://wiki.archlinux.org/title/GNOME/Keyring  
    
    GNOME Keyring is a collection of components that store secrets, passwords, keys, certificates and make them available to applications.
    
    Directory : `~/.local/share/keyrings`
    
    mem : 2637

* (sd-pam)
    
    https://www.reddit.com/r/linuxquestions/comments/n6akxv/  
    
    The sole purpose of this process is to wait for the service to terminate and to perform the "close PAM session" operations when that occurs.
    
    mem : 2622
    
* upowerd
    
    https://upower.freedesktop.org/  
    https://www.cyberciti.biz/faq/linux-upower-command-examples-and-syntax/  
    
    UPower is an abstraction for enumerating power devices, listening to device events and querying history and statistics. Any application or service on the system can access the org.freedesktop.UPower service via the system message bus.
    
    ```
    mem : 2308
    ```

* systemd-logind
    
    https://www.freedesktop.org/software/systemd/man/systemd-logind.service.html  
    
    A system service that manages user logins.
    
    ```
    mem : 1911
    ```

* accounts-daemon
    
    https://www.freedesktop.org/wiki/Software/AccountsService/  
    
    AccountsService is a D-Bus service for accessing the list of user accounts and information attached to those accounts.
    
    ```
    mem : 1604
    ```

* irqbalance
    
    https://linux.die.net/man/1/irqbalance  
    
    Distribute hardware interrupts across processors on a multiprocessor system.
    
    ```
    mem : 563
    ```

* rtkit-daemon
    
    Realtime Kit enables realtime scheduling for the PulseAudio daemon.
    
    ```
    mem : 477
    ```

* agetty
    
    https://man.archlinux.org/man/agetty.8.en  
    
    Ctrl+Alt+F1 terminal started by getty@tty1 service :
    
    ```
    systemctl status getty@tty1
    ```
    
    ```
    mem : 372
    ```

* acpid
    
    https://wiki.archlinux.org/title/acpid  
    
    A flexible and extensible daemon for delivering ACPI events. When an event occurs, it executes programs to handle the event.
    
    ```
    mem : 261
    ```


#### Anti-Linux :-D

* Horrible Gnome
    
    https://felipec.wordpress.com/2023/02/24/gnomes-horrid-coding-practices/  
    [https://www.theregister.com/2021/11/10/system76_gnome_deskto](https://www.theregister.com/2021/11/10/system76_gnome_desktop_fight/)  
    [https://www.osnews.com/story/133955/gnome-to-prevent-theming](https://www.osnews.com/story/133955/gnome-to-prevent-theming-wider-community-not-happy/)  
    https://forum.zorin.com/t/the-direction-of-gnome/22697/4  
    [https://ubuntu-mate.community/t/horrible-gtk3-gnome-ui-desig](https://ubuntu-mate.community/t/horrible-gtk3-gnome-ui-design-is-leaking-into-ubuntu-mate-applications-in-20-04/22028)  
    [https://igurublog.wordpress.com/2012/11/05/gnome-et-al-rotti](https://igurublog.wordpress.com/2012/11/05/gnome-et-al-rotting-in-threes/)  
    https://news.ycombinator.com/item?id=27075980  
    https://news.ycombinator.com/item?id=26002504  

* Horrible Gtk
    
    https://github.com/lah7/gtk3-classic  
    https://www.reddit.com/r/xfce/comments/spn0d0/avoid_gtk3/  
    https://joshuastrobl.com/2021/09/14/building-an-alternative-ecosystem/  
    https://www.reddit.com/r/GTK/comments/xdfgjr/api_changes_in_gtk4_removal_of_gtkmenu/  
    https://blogs.gnome.org/antoniof/2022/06/15/the-tree-view-is-undead-long-live-the-column-view%e2%80%bd/  
    https://bugzilla.mozilla.org/show_bug.cgi?id=1701123  
    https://medium.com/@fulalas/gnome-42-the-nonsense-continues-7d96c3287f7  
    https://ludditus.com/2021/05/30/is-there-any-future-for-the-gtk-based-desktop-environments/  
    https://medium.com/@sarvex/gnome-shell-for-stupids-by-morons-a9020318198b  
    https://fosspost.org/are-gtk-developers-destroying-linux-desktop-with-their-plans/  
    https://www.reddit.com/r/linux/comments/xwtns5/does_it_seem_like_gnome_wants_system_76s_cosmic/  
    https://www.theregister.com/2022/07/05/gtk_5_might_drop_x11/  

* Ulrich Drepper
    
    https://news.ycombinator.com/item?id=2378013  

* Manjarno
    
    https://manjarno.snorlax.sh/  

* Wayland

    [https://gist.github.com/probonopd/...](https://gist.github.com/probonopd/9feb7c20257af5dd915e3a9f2d1f2277)  
    [https://dudemanguy.github.io/blog/...](https://dudemanguy.github.io/blog/posts/2022-06-10-wayland-xorg/wayland-xorg.html)  


