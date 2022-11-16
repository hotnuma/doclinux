**[ Home | [Bugs](01-Bugs.html) | [FFmpeg](01-FFmpeg.html) | [Network](02-Network.html) | [Systemd](03-Systemd.html) | [Wayland](04-Wayland.html) | [Other](99-Other.html) ]**

## Docs Linux

---

#### References

* FreeDesktop
    
    https://specifications.freedesktop.org/  

* XBindKeys
    
    https://www.nongnu.org/xbindkeys/xbindkeys.html  



#### System

* Background color
    
    ```
    #5e5c64
    ```
    
* Installation date
    
    ```
    stat -c %w /
    ```

* List processes
    
    by mem usage
    
    ```
    top -b -o +%MEM | head -n 30
    ```
    ps_mem : https://github.com/pixelb/ps_mem
    
* Environment variables
    
    https://askubuntu.com/questions/866161/
    
    ```
    /etc/environment
    ~/.profile
    ```
    
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

    ```
    grep -r "texthere" .
    ```
    
    https://stackoverflow.com/questions/12516937/
    
    ```
    grep -rni --include=*.{h,c,cpp,cxx} "texthere"
    ```
    


#### Files

* Create a symbolic link

    ```
    ln -s target_path link_name
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



#### Packages apt

* Source list
    
    ```
    /etc/apt/sources.list
    ```

* End of life releases
    
    https://doc.ubuntu-fr.org/old-releases  
    
* Uninstall block snaps
    
    https://forum.ubuntu-fr.org/viewtopic.php?pid=22458861#p22458861  

* Check if a package is installed using apt

    ```
    apt list thunar
    ```

* List installed packages
    
    ```
    apt list --installed | grep glib
    ```
    
* Get package version

    
    ```
    dpkg -l libgtk-3-0 | grep ^ii
    ```

* Remove useless packages

    ```
    sudo apt autoremove --purge
    ```

* Ubuntu upgrade system

    ```
    sudo do-release-upgrade
    ```

* Check if reboot is needed
    
    https://askubuntu.com/questions/164/



#### Log files

* Viewing log files

    https://ubuntu.com/tutorials/viewing-and-monitoring-log-files

* View System Log

    https://vitux.com/view-system-log-files-ubuntu/



#### Install

* Firefox ESR

    ```
    sudo add-apt-repository ppa:mozillateam/ppa
    sudo apt update
    sudo apt install firefox-esr
    ```

* yt-dlp
    
    https://github.com/yt-dlp/yt-dlp
    
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

* Output command without localization

    ```
    LANGUAGE=C free -h
    ```
    
    or
    
    ```
    LANG=C free -h
    ```
    
* Change desktop background

    Solid color : `hsetroot -solid '#5e5c64'`
    
    Walpaper : `feh --bg-scale /usr/share/rpd-wallpaper/clouds.jpg`
    
    Random walpaper : `feh --bg-scale --randomize /usr/share/rpd-wallpaper/`

* Change default terminal
    
    https://stackoverflow.com/questions/16808231/
    
    ```
    sudo update-alternatives --config x-terminal-emulator
    ```
    
* Change default session
    
    ```
    sudo update-alternatives --config x-session-manager
    ```


