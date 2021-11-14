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
    
    find ~ \( ! -user $USER -o ! -group $USER \)
    
* Output without localization

    LANG=C free -h



