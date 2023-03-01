**[ Home | [Systemd](01-Systemd.html) | [FFmpeg](02-FFmpeg.html) | [Network](03-Network.html) | [Bugs](04-Bugs.html) | [Other](99-Other.html) ]**

## Docs Linux

---

#### References

* FreeDesktop
    
    https://specifications.freedesktop.org/  



#### Processes
    
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
    
    mem : 2308

* systemd-logind
    
    mem : 1911

* accounts-daemon
    
    mem : 1604

* avahi-daemon:
    
    The Avahi mDNS/DNS-SD daemon implements Apple's Zeroconf architectur
    
    mem : 1100
    
* irqbalance
    
    mem : 563

* rtkit-daemon
    
    Realtime Kit enables realtime scheduling for the PulseAudio daemon
    
    mem : 477

* agetty
    
    mem : 372

* acpid
    
    mem : 261



#### Log files

* journalctl

    ```
    journalctl -b -f --lines=100
    ```

* Rotation des logs avec logrotate
    
    [https://journaldunadminlinux.fr/rotation-des-logs-avec-logro](https://journaldunadminlinux.fr/rotation-des-logs-avec-logrotate/)

* Delete old files
    
    https://unix.stackexchange.com/questions/459996/  
    https://unix.stackexchange.com/questions/184488/  

    ```
    sudo find /var/log -type f -mtime +7 -delete
    sudo find /var/log -mindepth 1 -mtime +7 -delete
    ```

* Stop excessive logging of sudo
    
    https://unix.stackexchange.com/questions/224370/  
    https://unix.stackexchange.com/questions/637227/  
    
    In `/etc/pam.d/sudo` replace user_name with real name
    
    ```
    session [success=1 default=ignore] pam_succeed_if.so quiet uid = 0 ruser = user_name
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

* Paquets Cassés

    https://forum.ubuntu-fr.org/viewtopic.php?pid=22273320#p22273320  
    
    ```
    dpkg -l | grep -v ^ii
    ```
    
    Cleanup
    
    ```
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


