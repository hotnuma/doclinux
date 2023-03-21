**[ [Home](00-Home.html) | [Systemd](01-Systemd.html) | Network | [FFmpeg](03-FFmpeg.html) | [Bugs](04-Bugs.html) | [Other](99-Other.html) ]**

## Network

---

#### Reference

* Configuration
    
    https://wiki.debian.org/NetworkConfiguration  

* Netplan
    
    https://askubuntu.com/questions/1034711/  

* DNS
    
    https://askubuntu.com/questions/1080230/  

* Default network interface
    
    ```
    ip route show default | cut -d " " -f 5
    ```
    
    https://unix.stackexchange.com/questions/14961/  
    https://serverfault.com/questions/842964/  
    https://stackoverflow.com/questions/15668653/  
    [https://www.linuxquestions.org/questions/linux-networking-3/](https://www.linuxquestions.org/questions/linux-networking-3/howto-find-gateway-address-through-code-397078/)  
    https://unix.stackexchange.com/questions/270008/  



#### Interfaces

* Predictable Network Interface Names
    
    https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/  
    
* Switch back to /etc/network/interfaces
    
    https://askubuntu.com/questions/1031709/  
    [https://linuxconfig.org/how-to-switch-back-networking-to-etc](https://linuxconfig.org/how-to-switch-back-networking-to-etc-network-interfaces-on-ubuntu-20-04-focal-fossa-linux)  
    [https://support.solusvm.com/hc/en-us/articles/360018794671-H](https://support.solusvm.com/hc/en-us/articles/360018794671-How-to-configure-Ubuntu-18-to-use-eth0-and-switch-back-to-etc-network-interfaces-file-)  

* resolvconf
    
    https://fr.linux-console.net/?p=1413#gsc.tab=0  
    
    ```
    # check to see if resolvconf is installed
    sudo systemctl status resolvconf.service

    # install resolveconf package
    sudo apt update
    sudo apt install resolvconf

    # confirm resolveconf is running
    sudo systemctl status resolvconf.service

    # if resolveconf isn't running, enable then start it
    sudo systemctl enable resolvconf.service
    sudo systemctl start resolvconf.service

    # check resolveconf status
    sudo systemctl status resolvconf.service

    # edit the head file
    sudo nano /etc/resolvconf/resolv.conf.d/head

    # enter your nameservers below the comments
    nameserver 8.8.8.8
    nameserver 8.8.4.4

    # update resolve.conf file
    sudo resolvconf --enable-updates
    sudo resolvconf -u

    # check if changes we successful
    sudo nano /etc/resolv.conf
    ```

* DNS BBox 

    ```
    echo "192.168.1.254  mabbox.bytel.fr" >> /etc/hosts
    ```



#### Network Manager

https://askubuntu.com/questions/249944/  
https://help.ubuntu.com/community/NetworkManager  
[https://techpiezo.com/linux/switch-back-to-ifupdown](https://techpiezo.com/linux/switch-back-to-ifupdown-etc-network-interfaces-in-ubuntu/)  

* Disable network manager

    ```
    sudo systemctl stop NetworkManager.service
    sudo systemctl disable NetworkManager.service
    sudo systemctl stop NetworkManager-wait-online.service
    sudo systemctl disable NetworkManager-wait-online.service
    sudo systemctl stop NetworkManager-dispatcher.service
    sudo systemctl disable NetworkManager-dispatcher.service
    sudo systemctl stop network-manager.service
    sudo systemctl disable network-manager.service
    ```

* Uninstall network manager

    Remove NetworkManager from the system

    ```
    sudo apt purge network-manager
    ```

    Configure eth0 using ifup.

    ```
    sudo ifup eth0
    ```


