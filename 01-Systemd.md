**[ [Home](00-Home.html) | Systemd | [FFmpeg](02-FFmpeg.html) | [Network](03-Network.html) | [Bugs](04-Bugs.html) | [Other](99-Other.html) ]**

## Systemd

---

#### References

* Journalctl cheat sheet with 10+ commands to filter systemd logs | GoLinuxCloud
    
    [https://www.golinuxcloud.com/view-logs-using-journalctl-filt](https://www.golinuxcloud.com/view-logs-using-journalctl-filter-journald/)

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
    
* References
    
    https://www.freedesktop.org/software/systemd/man/systemctl.html  
    [https://access.redhat.com/attachments/12052018_systemd_6.pdf](https://access.redhat.com/sites/default/files/attachments/12052018_systemd_6.pdf)  
    [https://access.redhat.com/documentation/](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system_administrators_guide/chap-managing_services_with_systemd)  


