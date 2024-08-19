<link href="style.css" rel="stylesheet"></link>

**[ Home | [Xfce](05-Xfce.html) | [Systemd](10-Systemd.html) | [Network](15-Network.html) | [FFmpeg](20-FFmpeg.html) | [Bugs](25-Bugs.html) | [Other](99-Other.html) ]**

## Docs Linux

---

#### References

* FreeDesktop
    
    https://specifications.freedesktop.org/  

* Memory Usage
    
    https://itvision.altervista.org/linux-desktop-environments-system-usage.html  

* Ubuntu periodic tasks
    
    https://0e39bf7b.blog/posts/ubuntu-periodic-tasks/


#### <a name="disable"></a> Enable / Disable Programs

* Disable AppArmor
    
    https://linuxconfig.org/how-to-disable-apparmor-on-ubuntu-20-04-focal-fossa-linux  
    https://help.ubuntu.com/community/AppArmor  

* Disable at-spi
    
    https://wiki.archlinux.de/title/GNOME#Tipps_und_Tricks  
    
    In `/etc/environment` add :
    
    `NO_AT_BRIDGE=1`

* Disable ssh agent and pgp agent
    
    https://docs.xfce.org/xfce/xfce4-session/advanced#ssh_and_gpg_agents  
    
    ```
    xfconf-query -c xfce4-session -p /startup/ssh-agent/enabled -n -t bool -s false
    xfconf-query -c xfce4-session -p /startup/gpg-agent/enabled -n -t bool -s false
    ```

* Disable Overlay Scrollbars
    
    https://forums.linuxmint.com/viewtopic.php?t=298083  

* Disable autostart programs
    
    https://wiki.archlinux.org/title/XDG_Autostart  

    `echo "Hidden=true" > $HOME/.config/autostart/xcompmgr.desktop`

* Disable systemd-oomd
    
    https://askubuntu.com/questions/1404888/  
    

#### System Configuration

* Edit grub.conf
    
    https://askubuntu.com/questions/575651/  
    
    Modify : `/etc/default/grub`
    
    Execute : `sudo update-grub`

* Alias
    
    List aliases : `alias`
    
    Define aliases in `~/.bash_aliases` or `~/.bashrc`

    Example : `alias cgrep='grep -rni --include=*.{h,c,cpp,cxx}'`

* Alternatives
    
    https://wiki.debian.org/DebianAlternatives  

* /sbin /bin /local/bin
    
    https://askubuntu.com/questions/308045/  

* Environment variables
    
    https://wiki.archlinux.org/title/environment_variables  
    https://askubuntu.com/questions/866161/  
    
    ```
    /etc/environment
    ~/.profile
    ```
    
* File associations
    
    `~/.config/mimeapps.list`
    
* Locale
    
    https://wiki.archlinux.org/title/locale
    
    `/etc/default/locale`
    
* User's groups
    
    `groups username`

* Default boot target

    ```
    sudo systemctl get-default
    sudo systemctl set-default graphical.target
    ```

* Reboot / Halt System
    
    ```
    systemctl reboot
    systemctl poweroff
    ```

* pkexec
    
    https://unix.stackexchange.com/questions/203136/  
    https://askubuntu.com/questions/608419/  
    
* Xsession xdg paths
    
    https://askubuntu.com/questions/1179729/  


#### Drives

* Check drive spin down

    https://superuser.com/questions/173622/  

* Eject USB drives
    
    https://unix.stackexchange.com/questions/35508/

* Power Off Drive
    
    https://askubuntu.com/questions/671683/  
    https://forum.manjaro.org/t/eject-external-hard-drive-option-gone/61895/6  
    
    ```
    sync
    udisksctl power-off -b /dev/sdX
    ```

* Read smart infos

    `sudo smartctl -s on -a /dev/sdc`
    
* Read UUID of partitions

    `sudo blkid`
    
* Unmount all partitions

    `umount /dev/sdc?`
    
* Delete all partitions

    https://serverfault.com/questions/250839/  
    
    `sudo dd if=/dev/zero of=/dev/sdc bs=512 count=1 conv=notrunc`

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

* Rename partition
    
    `sudo ntfslabel -f /dev/sdc1 Backup1`

* Fix NTFS
    
    `sudo ntfsfix /dev/sdc1`

* I/O test
    
    [how_to_io_test](https://www.cyberciti.biz/faq/howto-linux-unix-test-disk-performance-with-dd-command/)  
    
    `dd if=/dev/zero of=/tmp/test1.img bs=1G count=1 oflag=dsync`
    
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

    `sudo du -ham / 2>/dev/null | sort -nr | head -n 20`
    
* Compress a directory with 7zip

    `7z a example.7z example/`
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

* Check open files
    
    https://linuxhint.com/check-open-files-in-linux/  

* Get file's MIME type
    
    [https://stackoverflow.com/questions/2227182/how-can-i-find-o](https://stackoverflow.com/questions/2227182/how-can-i-find-out-a-files-mime-type-content-type)  

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


#### Install

* Source list
    
    `/etc/apt/sources.list`

* Enable non-free-firmware
    
    [https://www.linuxtricks.fr/wiki](https://www.linuxtricks.fr/wiki/debian-configurer-les-sources-activer-non-free-et-contrib)  

* System upgrade

    ```
    sudo apt update
    sudo apt upgrade
    ```
    or

    ```
    sudo apt update
    sudo apt full-upgrade
    ```

* Remove useless packages

    ```
    sudo apt autoremove
    ```
    
    or
    
    ```
    sudo apt autoremove --purge
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
    
* Find the package that provides a file
    
    https://askubuntu.com/questions/481/  

* List of installed files from a package
    
    https://askubuntu.com/questions/32507/  

* Get package version

    ```
    dpkg -l libgtk-3-0 | grep ^ii
    ```

* Purge Apt Cache

    ```
    sudo apt clean ; sudo apt autoclean
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

* Hardware acceleration
    
    https://wiki.debian.org/HardwareVideoAcceleration  


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


#### Misc

* Delete empty directories
    
    https://unix.stackexchange.com/questions/46322/  

* Replace multiple spaces
    
    https://superuser.com/questions/241018/  

* Get source of package
    
    https://www.cyberciti.biz/faq/how-to-get-source-code-of-package-using-the-apt-command-on-debian-or-ubuntu/  

* Fix Screen Tearing in Linux
    
    https://www.youtube.com/watch?v=rVBq6d3c1gM  
    [https://unix.stackexchange.com/questions/667911/](https://unix.stackexchange.com/questions/667911/intel-modesetting-driver-screen-tearing)  
    https://forum.ubuntu-fr.org/viewtopic.php?id=2066260  
    [https://linuxfr.org/les-drivers-xorg](https://linuxfr.org/users/gnumdk/journaux/les-drivers-xorg-inutiles-avec-un-noyau-recent)  

* Center window
    
    https://superuser.com/questions/141032/  
    
    `Alt+F7`

* Convert .csv file to .ods
    
    https://askubuntu.com/questions/1105378/  
    
    `soffice --convert-to ods example.csv --headless`

* Statistics
    
    `LC_ALL=C datamash --header-out min 1 max 1 mean 1 < data.txt`
    
    `LC_ALL=C datamash --header-out min 1 max 1 median 1 mode 1 mean 1 < data.txt`
    
    `gnuplot -p -e "plot './data.txt'"`

    `gnuplot -p -e "plot './data.txt' lc rgb 'blue' pt 6"`

* Check VA-API

    `vainfo`

* Change desktop background

    Solid color : `hsetroot -solid '#5e5c64'`
    
    Walpaper : `feh --bg-scale /usr/share/rpd-wallpaper/clouds.jpg`
    
    Random walpaper : `feh --bg-scale --randomize /usr/share/rpd-wallpaper/`

* Installation date
    
    `stat -c %w /`

* Play a sound
    
    `paplay /usr/share/sounds/freedesktop/stereo/dialog-information.oga`
    
* Delete thumbnails older than 30 days

    `find ~/.cache/thumbnails/ -type f -iname \*.png -mtime +30 -delete`

* Output command without localization

    `LANGUAGE=C free -h`
    
    or
    
    `LANG=C free -h`
    
* Change default terminal
    
    https://stackoverflow.com/questions/16808231/  
    
    `sudo update-alternatives --config x-terminal-emulator`
    
* Change default session
    
    `sudo update-alternatives --config x-session-manager`


