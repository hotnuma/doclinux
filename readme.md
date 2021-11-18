# Linux Notes

Reminder of common Linux commands.

[ffmpeg](ffmpeg.md)\
[network](network.md)\
[startup](startup.md)\
[wayland](wayland.md)\
[xfce](xfce.md)

[bugs](misc_bugs.md)\
[links](misc_links.md)

### Markdown Reference

[github markdown](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
[cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Here-Cheatsheet)

### Drives

* Format USB key on /dev/sdc
    ```
    lsblk -p
    sudo umount /dev/sdc1
    ```
    ext4
    ```
    sudo mkfs.ext4 -L "Backup" /dev/sdc1
    ```
    ntfs
    ```
    sudo mkfs.ntfs -f -L "Backup" /dev/sdc1
    sudo chown $USER:$USER /media/hotnuma/Backup
    ```
* Read smart infos
    ```
    sudo smartctl -s on -a /dev/sda
    ```
* Write img file to drive /dev/sdc
    ```
    lsblk -p
    sudo umount /dev/sdc?
    lsblk -p
    rpimg "file.img" /dev/sdc
    ```
### Files

* Files not own by user in home
    ```
    find ~ \( ! -user $USER -o ! -group $USER \)
    ```
* Last modified files in directory
    ```
    find /var/log -cmin -5
    ```
* Remove execute flag
    ```
    find . ! -type l ! -type d -exec chmod ls -l {} +
    find . ! -type l ! -type d -exec chmod 0664 {} +
    find . ! -type l ! -type d -exec chmod a-x {} +
    ```
    ```
    find . ! -wholename "./.git/*" ! -type l ! -type d -exec ls -l {} +
    find . ! -wholename "./.git/*" ! -type l ! -type d -exec chmod 0664 {} +
    find . ! -wholename "./.git/*" ! -type l ! -type d -exec chmod a-x {} +
    ```
* Biggest folders
    ```
    sudo du -ham / 2>/dev/null | sort -nr | head -n 20
    ```
### Misc

* Firefox config
    about:config
    ```
    browser.sessionstore.resume_from_crash user_set boolean false
    layers accelerated
    gpu process
    gpu enabled
    ```
* Output without localization
    ```
    LANG=C free -h
    ```
### Packages

[pacman](https://wiki.archlinux.org/title/pacman)

* check if installed
	Manjaro :
    ```
    pacman -Ss mesa | grep installé
    ```
    Ubuntu :
    ```
    apt list thunar
    ```
* Remove unneeded packages
    ```
    sudo apt autoremove --purge
    ```
### System

* systemd
    ```
    systemd-analyze time
    systemd-analyze blame
    systemd-analyze blame --no-pager
    systemd-analyze critical-chain
    
    systemctl list-units --no-pager
    systemctl list-unit-files | grep "enabled "
    systemctl | grep running
    ```

### Linux

alias et function
[Alias Ubuntu](https://forum.ubuntu-fr.org/viewtopic.php?id=20437)\

determine audio playing
[Audio playing detect](https://stackoverflow.com/questions/22144203/how-to-determine-the-last-time-the-audio-device-was-playing-a-file)\

getusage.c
[CPU getusage_c](https://github.com/fho/code_snippets/blob/master/c/getusage.c)\

linux - Show top five CPU consuming processes with `ps` - Unix & Linux Stack Exchange
[CPU top processes](https://unix.stackexchange.com/questions/13968/show-top-five-cpu-consuming-processes-with-ps)\

CPU usage by PID
[CPU usage by PID](https://stackoverflow.com/questions/1420426/how-to-calculate-the-cpu-usage-of-a-process-by-pid-in-linux-from-c)\

CPU usage
[CPU usage](https://stackoverflow.com/questions/1221555/retrieve-cpu-usage-and-memory-usage-of-a-single-process-on-linux)\

cpu-frequtils
[cpu-frequtils](https://doc.ubuntu-fr.org/cpu-frequtils)\

disable at-spi-bus-launcher / Applications & Desktop Environments / Arch Linux Forums
[disable at-spi-bus-launcher _ Applications & Desktop Environments _ Arch Linux Forums](https://bbs.archlinux.org/viewtopic.php?id=237697)\

Display Signaling
[Display Signaling](https://wiki.archlinux.org/title/Display_Power_Management_Signaling)\

Drive spin down
[Drive spin down](https://superuser.com/questions/173622/hdparm-checking-if-a-drive-is-spun-down/176079)\

executable - How to recursively remove execute permissions from files without touching folders? - Unix & Linux Stack Exchange
[Execute flag remove](https://unix.stackexchange.com/questions/296967/how-to-recursively-remove-execute-permissions-from-files-without-touching-folder)\

Linux find process by name - nixCraft
[Find process by name](https://www.cyberciti.biz/faq/linux-find-process-name/)\

disable auto suspend
[Idle Reset](https://askubuntu.com/questions/1323618/how-to-disable-auto-suspend-temporary-reset-idle-time)\

best Image Viewer
[Image Viewers](https://itsfoss.com/image-viewers-linux/)\

lightdm [Wiki ubuntu-fr]
[LightDm](https://doc.ubuntu-fr.org/lightdm)\

Locale - ArchWiki
[Locale Collation](https://wiki.archlinux.org/title/locale#LC_COLLATE:_collation)\

Viewing log files
[Log files](https://ubuntu.com/tutorials/viewing-and-monitoring-log-files#2-log-files-locations)\

View System Log
[Log view](https://vitux.com/view-system-log-files-ubuntu/)\

Mount ntfs
[Mount ntfs](https://superuser.com/questions/1049044/how-to-mount-properly-ntfs-partition-shared-between-linux-and-windows)\

Format Partitions
[Partitions Format](https://phoenixnap.com/kb/linux-format-disk)\

Setting PATH variable in /etc/environment vs .profile - Ask Ubuntu
[PATH variable](https://askubuntu.com/questions/866161/setting-path-variable-in-etc-environment-vs-profile)\

remove snap
[Remove snap](https://askubuntu.com/questions/1369159/how-to-remove-snap-completely-without-losing-firefox)\

restart is needed
[Restart if needed](https://askubuntu.com/questions/921541/how-to-determine-if-a-restart-is-needed-on-my-ubuntu-server/921546#921546)\

turn off screen
[Screen On Off](https://superuser.com/questions/374637/how-to-turn-off-screen-with-shortcut-in-linux)\

désactiver l'écran
[Screen sleep](https://qastack.fr/superuser/31726/how-to-disable-the-screen-linux-without-x)\

Set CPU governor
[Set CPU governor](https://askubuntu.com/questions/1021748/set-cpu-governor-to-performance-in-18-04)\

linux - Checking sudo in Bash (script with if statements) - Stack Overflow
[sudo test](https://stackoverflow.com/questions/42875809/checking-sudo-in-bash-script-with-if-statements/42876846)\

Comment utiliser Systemctl pour gérer les services et les unités de Systemd | DigitalOcean
[Systemctl howto](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units-fr)\

list services
[Systemctl list services](https://askubuntu.com/questions/795226/how-to-list-all-enabled-services-from-systemctl)\

Systemctl
[Systemctl](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units-fr)\

theme based on Adwaita
[Theme Adwaita based](https://askubuntu.com/questions/1170151/help-creating-a-new-theme-based-on-adwaita)\

Gtk-Theming-Guide
[Theme Guide](https://github.com/surajmandalcell/Gtk-Theming-Guide/blob/master/creating_gtk_themes.md)\

How to Find Top Directories and Files (Disk Space) in Linux
[Top directory 1](https://www.tecmint.com/find-top-large-directories-and-files-sizes-in-linux/)\

linux - How to find the largest directories or largest files? - Super User
[Top directory 2](https://superuser.com/questions/276487/how-to-find-the-largest-directories-or-largest-files)\

Linux find largest file in directory recursively using find/du - nixCraft
[Top directory 3](https://www.cyberciti.biz/faq/linux-find-largest-file-in-directory-recursively-using-find-du/)\

desktop environments - Where is XDG_CONFIG_DIRS set? - Ask Ubuntu
[XDG_CONFIG_DIRS](https://askubuntu.com/questions/1179729/where-is-xdg-config-dirs-set)\

    
