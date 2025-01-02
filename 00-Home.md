<link href="style.css" rel="stylesheet"></link>

**[ Home | [Xfce](05-Xfce.html) | [Systemd](10-Systemd.html) | [Network](15-Network.html) | [FFmpeg](20-FFmpeg.html) | [Bugs](25-Bugs.html) | [Other](99-Other.html) ]**

## Docs Linux

---

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
    ~/.profile
    ```
    
* File associations
    
    `~/.config/mimeapps.list`
    
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

* Session

    https://askubuntu.com/questions/77191/  

    _The Name entry is what lightdm would display for this session. The Exec entry is the important thing, and it should be the name of the program that starts the actual session. When you log in, lightdm calls the /etc/X11/Xsession script, passing it the value of Exec as an argument, and Xsession will, eventually, execute this program (for example, it could be startxfce4 for starting a xfce4 session). If the Exec entry is the special string default, then Xsession will execute the user's ~/.xsession file. (Xsession would also execute ~/.xsession if it's called without arguments.)_

    `cat ~/.dmrc`

    ```
    [Desktop]
    Session=xubuntu
    ```

    `/usr/share/xsessions/xubuntu.desktop`

    ```
    [Desktop Entry]
    Version=1.0
    Name=Default Xsession
    Exec=startxfce4
    Icon=
    Type=Application
    ```
    
    Startup script : `/usr/bin/startxfce4`

    session variable : `DESKTOP_SESSION=xubuntu`

* Xsession xdg paths
    
    https://askubuntu.com/questions/1179729/  


#### Install

* Source list
    
    `/etc/apt/sources.list`

* Check if reboot is needed
    
    https://askubuntu.com/questions/164/  

* Enable non-free-firmware
    
    [https://www.linuxtricks.fr/wiki](https://www.linuxtricks.fr/wiki/debian-configurer-les-sources-activer-non-free-et-contrib)  

* End of life releases
    
    https://doc.ubuntu-fr.org/old-releases  
    
* Find the package that provides a file
    
    https://askubuntu.com/questions/481/  

* Get package version

    `dpkg -l libgtk-3-0 | grep ^ii`

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

* Hardware acceleration
    
    https://wiki.debian.org/HardwareVideoAcceleration  

* yt-dlp
    
    https://github.com/yt-dlp/yt-dlp  
    
    Install or Update :
    
    `python3 -m pip install -U yt-dlp`


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


#### Firefox

* Install from mozilla
    
    https://support.mozilla.org/en-US/kb/install-firefox-linux  
    https://ftp.mozilla.org/pub/firefox/releases/  
    
    Might require dbus-glib : `sudo apt install libdbus-glib-1-2`
    
    ```
    sudo tar xjf firefox-*.tar.bz2 && sudo mv firefox /opt/firefox121_01/
    sudo mv /usr/bin/firefox /usr/bin/firefox.bak
    sudo ln -s /opt/firefox/firefox /usr/bin/firefox
    ```

* Test Videos
    
    https://www.youtube.com/watch?v=cuXsupMuik4  
    https://www.youtube.com/watch?v=TVtoxUohG5E  

* Change user agent
    
    Create the following key in `about:config` :
    
    `general.useragent.override	Mozilla/5.0 (X11; Linux x86_64; rv:131.0) Gecko/20100101 Firefox/131.0`

* Profiles location
    
    Type `about:profiles` in the address bar.

* User data

    https://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data  

* Safe Mode
    
    In a terminal : `firefox --safe-mode`

* Turn off ambient mode
    
    https://www.popsci.com/diy/youtube-ambient-mode-off-on/  
    
* Turn off picture-in-picture mode
    
    https://support.mozilla.org/en-US/kb/turn-picture-picture-mode  

* Turn off updates
    
    Create a `policies.json` file in `firefox/distribution/` :
    
    ```
    {
        "policies":
        {
            "DisableAppUpdate": true,
            "ManualAppUpdateOnly": true
        }
    }
    ```
    
    ```
    sudo mkdir -p /opt/firefox115esr/distribution/
    sudo cp ./policies.json /opt/firefox115esr/distribution/
    ```


#### Misc

* Center window
    
    https://superuser.com/questions/141032/  
    
    `Alt+F7`

* Change default session
    
    `sudo update-alternatives --config x-session-manager`

* Change default terminal
    
    https://stackoverflow.com/questions/16808231/  
    
    `sudo update-alternatives --config x-terminal-emulator`
    
* Change desktop background

    Solid color :       `hsetroot -solid '#5e5c64'`
    
    Walpaper :          `feh --bg-scale /usr/share/rpd-wallpaper/clouds.jpg`
    
    Random walpaper :   `feh --bg-scale --randomize /usr/share/rpd-wallpaper/`

* Check VA-API

    `vainfo`

* Convert .csv file to .ods
    
    https://askubuntu.com/questions/1105378/  
    
    `soffice --convert-to ods example.csv --headless`

* Enable copy-to-clipboard in Zathura
    
    https://unix.stackexchange.com/questions/339487/  
    
* Get installation date
    
    `stat -c %w /`

* Get source of package
    
    https://www.cyberciti.biz/faq/how-to-get-source-code-of-package-using-the-apt-command-on-debian-or-ubuntu/  

* Output command without localization

    `LANGUAGE=C free -h`
    
    or
    
    `LANG=C free -h`
    
* Replace multiple spaces
    
    https://superuser.com/questions/241018/  

* Switch to non-graphical
    
    https://superuser.com/questions/100693/  

    console :   `Ctrl+Alt+F1`
    graphical : `Ctrl+Alt+F7`


