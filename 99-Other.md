<link href="style.css" rel="stylesheet"></link>

**[ [Home](00-Home.html) | [Xfce](05-Xfce.html) | [Systemd](10-Systemd.html) | [Network](15-Network.html) | [FFmpeg](20-FFmpeg.html) | [Bugs](25-Bugs.html) | Other ]**

## Other

---

#### Forums

020 https://forum.ubuntu-fr.org/search.php?action=show_recent  
018 https://forums.debian.net/search.php?search_id=active_topics  
071 https://forums.raspberrypi.com/search.php?search_id=active_topics  


#### Articles

* Format output to a specific line length
    
    https://unix.stackexchange.com/questions/146089/  
    
    `fmt --width=120 input.txt > output.txt`

* Repack epub files
    
    https://ebooks.stackexchange.com/questions/257/
    
    Extract : `unzip ../file.epub`
    
    Compress : `zip -rX ../file.epub mimetype META-INF/ OPS/`
    
* Named anchor in markdown
    
    https://stackoverflow.com/questions/5319754/  

    `#### <a name="tith"></a>This is the Heading`

* Set  default audio output
    
    https://askubuntu.com/questions/1038490/  

* OCR
    
    https://stackoverflow.com/questions/52998331/  
    https://stackoverflow.com/questions/31407010/  
    https://github.com/tesseract-ocr/tessdata/blob/main/fra.traineddata  
    https://dfir.science/2017/04/tesseract-ocr-extract-text-from-images.html  
    https://tech.kibatic.com/linux/ocr-tesseract-pdf/  
    
    ```
    convert -density 300 input.pdf -depth 8 -strip -background white -alpha off out1.tiff
    tesseract out1.tiff out2 -l fra
    ```


#### System Processes on Debian 12

https://debian-facile.org/viewtopic.php?pid=254022#p254022  

* agetty
    
    https://man.archlinux.org/man/agetty.8.en  
    
    Ctrl+Alt+F1 terminal started by getty@tty1 service :
    
    `systemctl status getty@tty1`
    
    mem : 358

* dbus-daemon
    
    System bus, two processes.
    
    mem : 2378

* gvfsd gvfsd-metadata gvfsd-trash
    
    Virtual file system.
    
    mem : 3623 + 3011 + 4035

* gvfs-udisks2-volume-monitor
    
    mem : 5571

* init
    
    mem : 3831

* polkitd polkit-gnome-authentication-agent-1
    
    https://www.freedesktop.org/software/polkit/docs/latest/polkit.8.html  
    https://wiki.archlinux.org/title/Polkit  
    
    Polkit is used for controlling system-wide privileges. It provides an organized way for non-privileged processes to communicate with privileged ones. In contrast to systems such as sudo, it does not grant root permission to an entire process, but rather allows a finer level of control of centralized system policy.
    
    mem : 2884 + 5509

* rtkit-daemon
    
    Realtime Kit enables realtime scheduling for the PulseAudio daemon.
    
    mem : 511

* (sd-pam)
    
    https://www.reddit.com/r/linuxquestions/comments/n6akxv/  
    
    The sole purpose of this process is to wait for the service to terminate and to perform the "close PAM session" operations when that occurs.
    
    mem : 2239

* ssh-agent
    
    https://docs.xfce.org/xfce/xfce4-session/advanced#ssh_and_gpg_agents  
    
    mem : 1074

* systemd
    
    mem : 3760

* systemd-journald
    
    mem : 13752

* systemd-logind
    
    https://www.freedesktop.org/software/systemd/man/systemd-logind.service.html  
    
    A system service that manages user logins.
    
    mem : 2584

* systemd-timesyncd
    
    mem : 1826

* systemd-udevd
    
    https://linuxembedded.fr/2018/03/kernel-udev-et-systemd-la-gestion-du-hotplug  
    
    `systemd-udevd` listens to kernel uevents. For every event, systemd-udevd executes matching instructions specified in udev rules.
    
    mem : 4150

* udisksd
    
    https://wiki.archlinux.org/title/udisks  
    
    udisks provides a daemon udisksd, that implements D-Bus interfaces used to query and manipulate storage devices, and a command-line tool udisksctl, used to query and use the daemon.
    
    mem : 10203

* upowerd
    
    https://upower.freedesktop.org/  
    https://www.cyberciti.biz/faq/linux-upower-command-examples-and-syntax/  
    
    UPower is an abstraction for enumerating power devices, listening to device events and querying history and statistics. Any application or service on the system can access the org.freedesktop.UPower service via the system message bus.
    
    mem : 3546


#### More System Processes on Ubuntu

* accounts-daemon
    
    https://www.freedesktop.org/wiki/Software/AccountsService/  
    
    AccountsService is a D-Bus service for accessing the list of user accounts and information attached to those accounts.
    
    mem : 1604

* acpid
    
    https://wiki.archlinux.org/title/acpid  
    
    A flexible and extensible daemon for delivering ACPI events. When an event occurs, it executes programs to handle the event.
    
    mem : 261

* gnome-keyring-daemon
    
    https://wiki.archlinux.org/title/GNOME/Keyring  
    https://docs.xfce.org/xfce/xfce4-session/advanced#ssh_and_gpg_agents  
    
    GNOME Keyring is a collection of components that store secrets, passwords, keys, certificates and make them available to applications.
    
    directory : `~/.local/share/keyrings`
    
    mem : 2637

* irqbalance
    
    https://linux.die.net/man/1/irqbalance  
    
    Distribute hardware interrupts across processors on a multiprocessor system.
    
    mem : 563


#### Other

* Install Firefox deb
    
    https://forum.ubuntu-fr.org/viewtopic.php?id=2074608  
    [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-d](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)  
    https://www.youtube.com/watch?v=H7VcIIrdoXg  

* How to disable DRM banner
    
    [https://www.reddit.com/r/firefox/comments/sgyu1s/how_to_disa](https://www.reddit.com/r/firefox/comments/sgyu1s/how_to_disable_enable_drm_banner_to_prompt/)  
    https://support.cdn.mozilla.net/ml/questions/1388341  


<!--

* CPU Load
    
    https://superuser.com/questions/443406/  
    
    `openssl speed -multi $(nproc --all)`

* XBindKeys
    
    https://www.nongnu.org/xbindkeys/xbindkeys.html  

-->


