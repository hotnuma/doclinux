# Linux Notes

Reminder of common Linux commands.

### Dev

* build dependencies
    ```
    sudo apt-get build-dep --dry-run thunar
    ```
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

* check if installed
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
    
