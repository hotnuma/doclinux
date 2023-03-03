**[ Home | [Systemd](01-Systemd.html) | [FFmpeg](02-FFmpeg.html) | [Network](03-Network.html) | [Bugs](04-Bugs.html) | [Other](99-Other.html) ]**

## Docs Linux

---

#### References

* FreeDesktop
    
    https://specifications.freedesktop.org/  

* Disable Overlay Scrollbars
    
    https://forums.linuxmint.com/viewtopic.php?t=298083  

* Ubuntu periodic tasks
    
    https://0e39bf7b.blog/posts/ubuntu-periodic-tasks/

* pkexec
    
    https://unix.stackexchange.com/questions/203136/  
    https://forum.ubuntu-fr.org/viewtopic.php?pid=22395969#p22395969  
    https://stackoverflow.com/questions/6764030/  
    https://askubuntu.com/questions/608419/  
    https://sites.google.com/site/installationubuntu/home/ubuntu-17-10/alternatives-for-gksu-and-gksudo  
    https://lists.ubuntu.com/archives/foundations-bugs/2012-July/100103.html  
    https://www.freedesktop.org/software/polkit/docs/0.105/polkit-apps.html  

* disable gnome-keyring-daemon
    
    https://unix.stackexchange.com/questions/271661/  
    https://ubuntuforums.org/showthread.php?t=1655397  
    
    ```
    /etc/pam.d/lightdm
    /usr/share/dbus-1/services/
    ```



#### Processes / Services

https://debian-facile.org/viewtopic.php?pid=254022#p254022  
    
* polkitd polkit-gnome-authentication-agent-1
    
    https://wiki.archlinux.org/title/Polkit  
    https://doc.ubuntu-fr.org/policykit  
    
    mem : 11543

* udisksd
    
    https://wiki.archlinux.org/title/udisks  
    
    mem : 6010

* systemd-resolved
    
    https://wiki.archlinux.org/title/systemd-resolved  
    
    mem : 5850

* systemd-udevd
    
    https://linuxembedded.fr/2018/03/kernel-udev-et-systemd-la-gestion-du-hotplug  
    
    mem : 2722

* gnome-keyring-daemon
    
    https://wiki.archlinux.org/title/GNOME/Keyring  
    
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
    
    getty@tty1 service : `systemctl status getty@tty1`
    
    ```
    mem : 372
    ```

* acpid
    
    https://wiki.archlinux.org/title/acpid  
    
    A flexible and extensible daemon for delivering ACPI events. When an event occurs, it executes programs to handle the event.
    
    ```
    mem : 261
    ```



#### System

* /bin /sbin /local/bin
    
    https://askubuntu.com/questions/308045/  

* Environment variables
    
    https://askubuntu.com/questions/866161/  
    
    ```
    ~/.profile
    /etc/environment
    ```
    
* File associations
    
    `~/.config/mimeapps.list`
    
* Xsession xdg paths
    
    https://askubuntu.com/questions/1179729/  

* Locale
    
    https://wiki.archlinux.org/title/locale
    
    ```
    /etc/default/locale
    ```
    
* Alias
    
    Define aliases in `~/.bash_aliases` or `~/.bashrc`

    ```
    alias cgrep='grep -rni --include=*.{h,c,cpp,cxx}'
    ```

* Disable autostart program
    
    https://wiki.archlinux.org/title/XDG_Autostart

    ```
    echo "Hidden=true" > $HOME/.config/autostart/xcompmgr.desktop
    ```
    
* XBindKeys
    
    https://www.nongnu.org/xbindkeys/xbindkeys.html  

* Reboot / Halt System
    
    ```
    systemctl reboot
    systemctl poweroff
    ```



#### Drives

* Format `/dev/sdc1` partition in Ext4

    ```
    lsblk -p
    sudo umount /dev/sdc1
    sudo mkfs.ext4 -L "Backup" /dev/sdc1
    sudo chown $USER:$USER /media/$USER/Backup
    ```
    
* Format `/dev/sdc1` partition in NTFS

    ```
    lsblk -p
    sudo umount /dev/sdc1
    sudo mkfs.ntfs -f -L "Backup" /dev/sdc1
    ```
    
* Unmount all partitions

    ```
    umount /dev/sdc?
    ```
    
* Read UUID of partitions

    ```
    sudo blkid
    ```
    
* Read smart infos

    ```
    sudo smartctl -s on -a /dev/sdc
    ```
    
* Write img file to drive /dev/sdc using systools

    https://github.com/hotnuma/systools  
    
    ```
    lsblk -p
    sudo umount /dev/sdc?
    lsblk -p
    rpimg "file.img" /dev/sdc
    ```



#### Directories

* Top Directories
    
    [https://www.cyberciti.biz/faq/how-do-i-find-the-largest-file](https://www.cyberciti.biz/faq/how-do-i-find-the-largest-filesdirectories-on-a-linuxunixbsd-filesystem/)  

    ```
    sudo du -ham / 2>/dev/null | sort -nr | head -n 20
    ```
    
* Compress a directory with 7zip

    ```
    7z a example.7z example/
    ```
    without compression

    ```
    7z a -mx=0 example.7z example/
    ```
    
* Recursive grep

    https://stackoverflow.com/questions/12516937/
    
    ```
    grep -r "texthere" .
    ```
    
    ```
    grep -rni --include=*.{h,c,cpp,cxx} "texthere"
    ```
    


#### Files

* Create a symbolic link

    ```
    ln -s target_path link_name
    ```

* Ignore errors
    
    ```
    find / -name *.html 2>/dev/null
    ```
    
* List biggest files in directory
    
    ```
    find . -type f -printf "%s\t%p\n" | sort -nr | head -10
    ```
    
* find multiple pattern
    
    ```
    find . -type f \( -name "*.h" -o -name "*.c" \)
    ```
    
* Find files not own by user

    ```
    find ~ \( ! -user $USER -o ! -group $USER \)
    ```
    
* Find last modified files

    ```
    find ~ -cmin -5
    ```
    
* Remove execute flag

    ```
    find . ! -type l ! -type d -exec ls -la {} +
    find . ! -type l ! -type d -exec chmod 0664 {} +
    find . ! -type l ! -type d -exec chmod a-x {} +
    ```
    
    ```
    find . ! -wholename "./.git/*" ! -type l ! -type d -exec ls -la {} +
    find . ! -wholename "./.git/*" ! -type l ! -type d -exec chmod 0664 {} +
    find . ! -wholename "./.git/*" ! -type l ! -type d -exec chmod a-x {} +
    ```



#### Install

* Source list
    
    ```
    /etc/apt/sources.list
    ```

* Uninstall block snaps
    
    https://askubuntu.com/questions/1369159/  
    https://forum.ubuntu-fr.org/viewtopic.php?pid=22458861#p22458861  

* Remove useless packages

    ```
    sudo apt autoremove --purge
    ```

     https://forum.ubuntu-fr.org/viewtopic.php?pid=22563731#p22563731  
    
    ```
    apt list ~c
    sudo apt purge ~c
    ```

   https://forum.ubuntu-fr.org/viewtopic.php?pid=22273320#p22273320  
    
    ```
    dpkg -l | grep -v ^ii
    dpkg -l | awk '/^rc/{print $2}' | xargs -r sudo dpkg -P
    ```
    
* End of life releases
    
    https://doc.ubuntu-fr.org/old-releases  
    
* List installed packages
    
    ```
    apt list --installed | grep glib
    ```

    ```
    apt list thunar
    ```
    
* List of installed files from a package
    
    https://askubuntu.com/questions/32507/  

* Find the package that provides a file
    
    https://askubuntu.com/questions/481/  

* Get package version

    ```
    dpkg -l libgtk-3-0 | grep ^ii
    ```

* Ubuntu upgrade system

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

* Check if reboot is needed
    
    https://askubuntu.com/questions/164/  

* yt-dlp
    
    https://github.com/yt-dlp/yt-dlp
    
    Install or Update :
    
    ```
    python3 -m pip install -U yt-dlp
    ```
    
* Codecs and fonts

    ```
    sudo apt install ubuntu-restricted-extras
    ```

* NVidia Drivers

    https://phoenixnap.com/kb/install-nvidia-drivers-ubuntu

    ```
    apt search nvidia-driver
    ```

    or

    ```
    ubuntu-drivers devices
    ```

    ```
    sudo apt install nvidia-driver-470
    ```


#### Firefox

* Extensions
    
    uBlock Origin, Single File, Export Cookies
    
* Config
    
    about:config
    
    ```
    browser.sessionstore.resume_from_crash false
    layers.acceleration.force-enabled true
    layers.gpu-process.enabled true
    media.gpu-process-decoder true
    ```

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



#### Misc

* Change desktop background

    Solid color : `hsetroot -solid '#5e5c64'`
    
    Walpaper : `feh --bg-scale /usr/share/rpd-wallpaper/clouds.jpg`
    
    Random walpaper : `feh --bg-scale --randomize /usr/share/rpd-wallpaper/`

* Installation date
    
    ```
    stat -c %w /
    ```

* Play a sound
    
    `paplay /usr/share/sounds/freedesktop/stereo/dialog-information.oga`
    
* Delete thumbnails older than 30 days

    find ~/.cache/thumbnails/ -type f -iname \*.png -mtime +30 -delete

* Output command without localization

    ```
    LANGUAGE=C free -h
    ```
    
    or
    
    ```
    LANG=C free -h
    ```
    
* Change default terminal
    
    https://stackoverflow.com/questions/16808231/  
    
    ```
    sudo update-alternatives --config x-terminal-emulator
    ```
    
* Change default session
    
    ```
    sudo update-alternatives --config x-session-manager
    ```


