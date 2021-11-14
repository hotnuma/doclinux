# Linux Notes

Reminder of common Linux commands.

## System commands

* Format USB key on /dev/sdc
    
    lsblk -p
    sudo umount /dev/sdc1

    sudo mkfs.ext4 -L "Backup" /dev/sdc1

or

    sudo mkfs.ntfs -f -L "Backup" /dev/sdc1
    sudo chown $USER:$USER /media/hotnuma/Backup

