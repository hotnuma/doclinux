<link href="style.css" rel="stylesheet"></link>

**[ Home | [Xfce](05-Xfce.html) | [Network](10-Network.html) | [FFmpeg](15-FFmpeg.html) | [Systemd](20-Systemd.html) | [Bugs](25-Bugs.html) | [Other](99-Other.html) ]**

## Docs Linux

---

#### References

https://wiki.debian.org/FrontPage  
https://forums.debian.net/viewtopic.php?p=781767#p781767  


#### System

* System Infos

    `inxi -b`

    `glxinfo | egrep "OpenGL vendor|OpenGL renderer"`

* Alias
    
    List aliases : `alias`
    
    Define aliases in `~/.bash_aliases` or `~/.bashrc`

    Example : `alias cgrep='grep -rni --include=*.{h,c,cpp,cxx}'`

* Alternatives
    
    https://wiki.debian.org/DebianAlternatives  
    
    list alternatives : `update-alternatives --get-selections`  
    list choices : `update-alternatives --list x-cursor-theme`  
    
    default session : `sudo update-alternatives --config x-session-manager`  
    defaylt terminal : `sudo update-alternatives --config x-terminal-emulator`  
    
* Boot target

    ```
    sudo systemctl get-default
    sudo systemctl set-default graphical.target
    ```

* Environment variables
    
    https://wiki.archlinux.org/title/environment_variables  
    https://askubuntu.com/questions/866161/  
    https://askubuntu.com/questions/60218/  
    
    ```
    /etc/environment
    $HOME/.profile
    /etc/profile
    ```

* grub.conf
    
    https://askubuntu.com/questions/575651/  
    
    Modify : `/etc/default/grub`
    
    Execute : `sudo update-grub`

* Locale
    
    https://wiki.archlinux.org/title/locale
    
    `/etc/default/locale`
    
* pkexec
    
    https://unix.stackexchange.com/questions/203136/  
    https://askubuntu.com/questions/608419/  
    
* Reboot / Halt System
    
    ```
    systemctl reboot
    systemctl poweroff
    ```

* User's groups
    
    `groups username`


#### Install

* Source list
    
    `/etc/apt/sources.list`

* Check if reboot is needed
    
    https://askubuntu.com/questions/164/  

* Check which packages can be uodated
    
    `sudo apt update && apt list --upgradable`

* Enable non-free-firmware
    
    [https://www.linuxtricks.fr/wiki](https://www.linuxtricks.fr/wiki/debian-configurer-les-sources-activer-non-free-et-contrib)  

* End of life releases
    
    https://doc.ubuntu-fr.org/old-releases  
    
* Find the package that provides a file
    
    https://askubuntu.com/questions/481/  

* Get package version

    `dpkg -l libgtk-3-0 | grep ^ii`

* Get source of package
    
    https://www.cyberciti.biz/faq/how-to-get-source-code-of-package-using-the-apt-command-on-debian-or-ubuntu/  
    
    Check if `deb-src` is enabled : `cat /etc/apt/sources.list`
    
    ```
    sudo apt update
    apt source <package>
    ```

* List installed packages
    
    `dpkg -l`
    
    `dpkg -l | grep thunar`
    
    `apt list thunar`
    
    `apt list --installed | grep glib`
    
* List files from a package
    
    https://askubuntu.com/questions/32507/  

* Purge Apt Cache

    `sudo apt clean ; sudo apt autoclean`

* Remove useless packages

    `sudo apt autoremove`
    
    or
    
    `sudo apt autoremove --purge`
    
    or
    
    `sudo apt autopurge`

* Search package name

    `apt search thunar`

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

* Install python programs
    
    https://stackoverflow.com/questions/58831133/  
    https://luminousmen.com/post/why-use-pip-install-user  
    
    `python3 -m pip install --user <appname>`
    
* yt-dlp
    
    https://github.com/yt-dlp/yt-dlp  
    
    Install or Update :
    
    `python3 -m pip install --user -U yt-dlp`


#### Drives

* Check drive spin down

    https://superuser.com/questions/173622/  

* Eject USB drives
    
    https://unix.stackexchange.com/questions/35508/

* Power Off Drive
    
    https://askubuntu.com/questions/671683/  
    https://forum.manjaro.org/t/eject-external-hard-drive-option-gone/61895/6  
    
    `sync; udisksctl power-off -b /dev/sdX`

* Read smart infos

    `sudo smartctl -s on -a /dev/sdc`
    
* I/O test
    
    [how_to_io_test](https://www.cyberciti.biz/faq/howto-linux-unix-test-disk-performance-with-dd-command/)  
    
    `dd if=/dev/zero of=/tmp/test1.img bs=1G count=1 oflag=dsync`
    
* Write img file to drive /dev/sdc using systools

    https://github.com/hotnuma/systools  
    
    ```
    lsblk -p
    sudo umount /dev/sdX?
    rpimg "file.img" /dev/sdX
    ```

* Write Debian Iso
    
    ```
    lsblk -p
    sudo umount /dev/sdX?
    sudo cp "debian.iso" /dev/sdX
    sudo sync
    ```

#### Drives Partitions

* Read UUID

    `sudo blkid`

* Unmount all

    `umount /dev/sdc?`
    
* Delete all partitions

    https://serverfault.com/questions/250839/  
    
    `sudo dd if=/dev/zero of=/dev/sdX bs=512 count=1 conv=notrunc`

* Format `/dev/sdc1` in Ext4

    ```
    lsblk -p
    sudo umount /dev/sdc1
    sudo mkfs.ext4 -L "Backup" /dev/sdc1
    sudo chown $USER:$USER /media/$USER/Backup
    ```
    
* Format `/dev/sdc1` in NTFS

    ```
    lsblk -p
    sudo umount /dev/sdc1
    sudo mkfs.ntfs -f -L "Backup" /dev/sdc1
    ```

* Rename NTFS partition
    
    `sudo ntfslabel -f /dev/sdc1 Backup1`

* Fix NTFS partition
    
    `sudo ntfsfix /dev/sdc1`


#### Directories

* Top Directories
    
    [https://www.cyberciti.biz/faq/how-do-i-find-the-largest-file](https://www.cyberciti.biz/faq/how-do-i-find-the-largest-filesdirectories-on-a-linuxunixbsd-filesystem/)  

    `sudo du -ham / 2>/dev/null | sort -nr | head -n 20`
    
* Compress a directory with 7zip

    `7z a example.7z example/`
    
    without compression :

    `7z a -mx=0 example.7z example/`
    
* Delete empty directories
    
    https://unix.stackexchange.com/questions/46322/  
    
    To check : `find . -type d -empty -print`

    To delete : `find . -type d -empty -delete`
`

* Recursive grep

    https://stackoverflow.com/questions/12516937/
    
    `grep -r "texthere" .`
    
    `grep -rni --include=*.{h,c,cpp,cxx} "texthere"`
    

#### Files

* Check opened files
    
    https://linuxhint.com/check-open-files-in-linux/  

* Create a symbolic link

    `ln -s target_path link_name`

* Find biggest files in directory
    
    `find . -type f -printf "%s\t%p\n" | sort -nr | head -10`

* Find files not own by user

    `find ~ \( ! -user $USER -o ! -group $USER \)`
    
* Find ignore errors
    
    `find / -name *.html 2>/dev/null`
    
* Find last modified files

    `find ~ -cmin -5`

* Find multiple pattern
    
    `find . -type f \( -name "*.h" -o -name "*.c" \)`
    
* Get file's MIME type
    
    https://stackoverflow.com/questions/2227182/  

* Remove presentation mode in PDFs
    
    https://unix.stackexchange.com/questions/754414/  


#### Misc

* Switch to non-graphical
    
    https://superuser.com/questions/100693/  

    console : `Ctrl+Alt+F1`  
    graphical : `Ctrl+Alt+F7`  

* Check VA-API

    `vainfo`

* Hardware acceleration
    
    https://wiki.debian.org/HardwareVideoAcceleration  

* Edit config files
    
    https://unix.stackexchange.com/questions/642578/  
    
    `sudo sed -e 's/^GRUB_TIMEOUT=.*/GRUB_TIMEOUT=0/' -i "$dest"`
    
* Convert .csv file to .ods
    
    https://askubuntu.com/questions/1105378/  
    
    `soffice --convert-to ods example.csv --headless`

* Replace multiple spaces
    
    https://superuser.com/questions/241018/  

* Enable copy-to-clipboard in Zathura
    
    https://unix.stackexchange.com/questions/339487/  
    
* Get installation date
    
    `stat -c %w /`

* Output command without localization

    `LANGUAGE=C free -h`
    
    or
    
    `LANG=C free -h`
    

