**[ Home | [Bugs](01-Bugs.html) | [FFmpeg](01-FFmpeg.html) | [Network](02-Network.html) | [Systemd](03-Systemd.html) | [Wayland](04-Wayland.html) | [Other](99-Other.html) ]**

### Docs Linux

---

#### Alias

* Defines aliases in `~/.bashrc` or `~/.bash_aliases`

    ```
    alias cgrep='grep -rni --include=*.{h,c,cpp,cxx}'
    ```



#### System

* List processes
    
    by mem usage
    
    ```
    top -b -o +%MEM | head -n 30
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



#### Files

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
    
* Top Directories

    ```
    sudo du -ham / 2>/dev/null | sort -nr | head -n 20
    ```
    
* Create a symbolic link

    ```
    ln -s target_path link_name
    ```



#### Packages apt

* Check if a package is installed using apt

    ```
    apt list thunar
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



#### Paths

* Environment variables
    
    https://askubuntu.com/questions/866161/
    
    ```
    /etc/environment
    ~/.profile
    ```
    
* Locale
    
    https://wiki.archlinux.org/title/locale
    
    ```
    /etc/default/locale
    ```



#### Misc

* Installation date
    
    ```
    stat -c %w /
    ```

* Disable autostart program
    
    https://wiki.archlinux.org/title/XDG_Autostart

    ```
    echo "Hidden=true" > $HOME/.config/autostart/xcompmgr.desktop
    or
    echo "Hidden=true" > $XDG_CONFIG_HOME/autostart/xcompmgr.desktop
    ```
    
* Install yt-dlp
    
    https://github.com/yt-dlp/yt-dlp
    
    ```
    python3 -m pip install -U yt-dlp
    ```
    
* Output command without localization

    ```
    LANGUAGE=C free -h
    ```
    
    or
    
    ```
    LANG=C free -h
    ```
    
* Change wallpaper with feh
    
    https://wiki.archlinux.org/title/feh

    ```
    feh --bg-scale /usr/share/rpd-wallpaper/clouds.jpg
    ```
    
    ```
    feh --bg-scale --randomize /usr/share/rpd-wallpaper/
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



#### Install

* Install Firefox ESR

    ```
    sudo add-apt-repository ppa:mozillateam/ppa
    sudo apt update
    sudo apt install firefox-esr
    ```

* Ubuntu install codecs and fonts

    ```
    sudo apt install ubuntu-restricted-extras
    ```

* Install NVidia Drivers

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


