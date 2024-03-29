<link href="style.css" rel="stylesheet"></link>

**[ [Home](00-Home.html) | Systemd | [Network](02-Network.html) | [FFmpeg](03-FFmpeg.html) | [Bugs](04-Bugs.html) | [Other](99-Other.html) ]**

## Systemd

---

#### References

https://www.freedesktop.org/software/systemd/man/systemctl.html  
[https://access.redhat.com/attachments/12052018_systemd_6.pdf](https://access.redhat.com/sites/default/files/attachments/12052018_systemd_6.pdf)  
[https://access.redhat.com/documentation/](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system_administrators_guide/chap-managing_services_with_systemd)  

* Manage services and units
    
    [https://www.digitalocean.com/community/tutorials/](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units-fr)  
    
    ```
    sudo systemctl status application.service
    ```
    ```
    sudo systemctl start application.service
    sudo systemctl stop application.service
    ```
    ```
    sudo systemctl enable application.service
    sudo systemctl disable application.service
    ```
    ```
    sudo systemctl restart application.service
    sudo systemctl reload application.service
    ```

* List services
    
    https://askubuntu.com/questions/795226/  
    
    ```
    systemctl list-unit-files --type=service
    systemctl list-unit-files | grep "enabled "
    systemctl list-units --no-pager
    systemctl | grep running
    ```
    
* List timers
    
    ```
    systemctl list-timers --all
    ```


#### Log files

[https://www.golinuxcloud.com/view-logs-using-journalctl-filt](https://www.golinuxcloud.com/view-logs-using-journalctl-filter-journald/)

* journalctl

    ```
    journalctl -b -f --lines=100
    journalctl --no-pager -b -p err
    ```

* Rotation des logs avec logrotate
    
    [https://journaldunadminlinux.fr/rotation-des-logs-avec-logro](https://journaldunadminlinux.fr/rotation-des-logs-avec-logrotate/)

* Delete old files
    
    https://unix.stackexchange.com/questions/459996/  
    https://unix.stackexchange.com/questions/184488/  

    ```
    sudo find /var/log -type f -mtime +5 -delete
    sudo find /var/log -maxdepth 1 -type f -mtime +5 -delete
    sudo find /var/log ! -wholename "/var/log/journal/*" -type f -mtime +5 -delete
    ```


#### Turn off excessive logging

* sudo
    
    https://unix.stackexchange.com/questions/224370/  
    https://unix.stackexchange.com/questions/637227/  
    
    In `/etc/pam.d/sudo` replace user_name with real name
    
    ```
    session [success=1 default=ignore] pam_succeed_if.so quiet uid = 0 ruser = user_name
    ```

* rtkit-daemon
    
    https://unix.stackexchange.com/questions/684379/  
    
    ```
    sudo mkdir /etc/systemd/system/rtkit-daemon.service.d/
    sudo geany rtkit-daemon.service.d/log.conf
    sudo systemctl daemon-reload
    sudo systemctl restart rtkit-daemon.service
    ```


#### Other

* Analyze startup

    ```
    systemd-analyze time
    systemd-analyze blame --no-pager
    systemd-analyze critical-chain
    ```

* Disable systemd-oomd
    
    https://askubuntu.com/questions/1404888/  
    
* Modify unit file
    
    https://serverfault.com/questions/840996/  
    
    ```
    systemctl edit <service-name>
    ```

* Read shutdown log

    ```
    journalctl -b -1 -e
    ```
    

