**[ [Home](00-Home.html) | [Bugs](01-Bugs.html) | [FFmpeg](01-FFmpeg.html) | [Network](02-Network.html) | Systemd | [Wayland](04-Wayland.html) ]**

### Systemd

---

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
    sudo systemctl restart application.service
    sudo systemctl reload application.service
    ```
    ```
    sudo systemctl enable application.service
    sudo systemctl disable application.service
    ```

* Modify unit file
    
    https://serverfault.com/questions/840996/
    
    ```
    systemctl edit <service-name>
    ```

* List services
    
    https://askubuntu.com/questions/795226/
    ```
    systemctl list-units --no-pager
    systemctl list-unit-files | grep "enabled "
    systemctl | grep running
    ```

* Analyze startup
    ```
    systemd-analyze time
    systemd-analyze blame --no-pager
    systemd-analyze critical-chain
    ```
* Read shutdown log
    ```
    journalctl -b -1 -e
    ```
* References
    
    https://www.freedesktop.org/software/systemd/man/systemctl.html \
    [https://access.redhat.com/attachments/12052018_systemd_6.pdf](https://access.redhat.com/sites/default/files/attachments/12052018_systemd_6.pdf) \
    [https://access.redhat.com/documentation/](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system_administrators_guide/chap-managing_services_with_systemd)

