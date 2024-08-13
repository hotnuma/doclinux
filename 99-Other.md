<link href="style.css" rel="stylesheet"></link>

**[ [Home](00-Home.html) | [Systemd](01-Systemd.html) | [Network](02-Network.html) | [FFmpeg](03-FFmpeg.html) | [Bugs](04-Bugs.html) | Other ]**

## Other

---

#### Forums

018 https://forums.debian.net/search.php?search_id=active_topics  
020 https://forum.ubuntu-fr.org/search.php?action=show_recent  
071 https://forums.raspberrypi.com/search.php?search_id=active_topics  


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

<!--

* Uninstall block snaps
    
    https://askubuntu.com/questions/1369159/  
    https://forum.ubuntu-fr.org/viewtopic.php?pid=22458861#p22458861  

* Firefox ESR
    
    https://ubuntuhandbook.org/index.php/2022/03/install-firefox-esr-ubuntu/  

    ```
    sudo add-apt-repository ppa:mozillateam/ppa
    sudo apt update
    sudo apt install firefox-esr
    ```

* Install Firefox deb
    
    https://forum.ubuntu-fr.org/viewtopic.php?id=2074608  
    [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-d](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)  

* How to disable DRM banner
    
    [https://www.reddit.com/r/firefox/comments/sgyu1s/how_to_disa](https://www.reddit.com/r/firefox/comments/sgyu1s/how_to_disable_enable_drm_banner_to_prompt/)  
    https://support.cdn.mozilla.net/ml/questions/1388341  

-->


