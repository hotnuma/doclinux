# Linux Notes

Reminder of common Linux commands.

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
* Files not own by user in home
    ```
    find ~ \( ! -user $USER -o ! -group $USER \)
    ```

* Output without localization
    ```
    LANG=C free -h
    ```

* Firefox config
    about:config
    ```
    browser.sessionstore.resume_from_crash user_set boolean false
    layers accelerated
    gpu process
    gpu enabled
    ```
    
* smartmontools
    ```
    sudo smartctl -s on -a /dev/sda
    ```
    
* write rpi image
    ```
    rpimg "file.img" /dev/sdc
    ```
    
* systemd
    ```
    systemd-analyze time
    systemd-analyze blame
    systemd-analyze blame --no-pager
    systemd-analyze critical-chain
    
    systemctl list-unit-files | grep "enabled "
    systemctl | grep running
    ```
    
* build dependencies
    ```
    sudo apt-get build-dep --dry-run thunar
    ```
    
* check if installed
    ```
    apt list thunar
    ```
    


