<link href="style.css" rel="stylesheet"></link>

**[ [Home](00-Home.html) | [Systemd](01-Systemd.html) | Network | [FFmpeg](03-FFmpeg.html) | [Bugs](04-Bugs.html) | [Other](99-Other.html) ]**

## Network

---

#### Reference

* Configuration
    
    https://wiki.debian.org/NetworkConfiguration  
    https://wiki.debian.org/NetworkManager  

* Read network configuration
    
    `networkctl`
    
    `ip route show default`
    
    `ip route show default | cut -d " " -f 5`

* Read DNS servers
    
    `cat /etc/resolv.conf`
    
    `ls /etc/resolv.conf`
    
    `resolvectl status`

* Predictable Network Interface Names
    
    [https://www.freedesktop.org/.../PredictableNetworkInterfaceNames](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)  
    
    Switch back to eth0 :
    
    Add `GRUB_CMDLINE_LINUX="net.ifnames=0"` in `/etc/default/grub`
    
    Execute `sudo update-grub`
    
* Set BBox name in hosts file

    `echo "192.168.1.254  mabbox.bytel.fr" >> /etc/hosts`


#### Switch to /etc/network/interfaces

* Install systemd-resolved
    
    ```
    sudo apt install ifupdown systemd-resolved
    sudo cp /etc/resolv.conf /etc/resolv.conf.bak
    sudo rm /etc/resolv.conf
    sudo ln -sf /run/systemd/resolve/stub-resolv.conf /etc/resolv.conf

* Disable NetworkManager

    ```
    sudo systemctl stop NetworkManager
    sudo systemctl disable NetworkManager
    ```

* Disable systemd-networkd
    
    ```
    sudo systemctl stop systemd-networkd
    sudo systemctl disable systemd-networkd
    sudo rm /etc/systemd/network/00-eth0.network
    ```

* Interface
    
    Create `/etc/network/interfaces` :

    ```
    # The loopback network interface
    auto lo
    iface lo inet loopback

    allow-hotplug eth0
    auto eth0
    iface eth0 inet static
      address 192.168.1.100
      netmask 255.255.255.0
      broadcast 192.168.1.255
      gateway 192.168.1.254
      # Only relevant if you make use of RESOLVCONF(8)
      # or similar...
      #dns-nameservers 8.8.8.8 8.8.4.4
    ```

    Configure eth0 using ifup :

    `sudo ifup eth0`

* Enable eth0

    `ln -s /dev/null /etc/systemd/network/99-default.link`

* Uninstall network manager

    `sudo apt purge network-manager`


#### Use systemd-networkd

* Use systemd-networkd
    
    [https://linux.fernandocejas.com/docs/...systemd-networkd](https://linux.fernandocejas.com/docs/how-to/switch-from-network-manager-to-systemd-networkd)  
    
    Create a configuration file :
    
    `/etc/systemd/network/00-eth0.network`

    ```
    [Match]
    Name=eth0

    [Network]
    Address=192.168.1.101
    Gateway=192.168.1.254
    DNS=8.8.8.8
    DNS=8.8.4.4
    ```
    
    Start services :
    
    ```
    sudo apt install systemd-resolved

    sudo systemctl stop NetworkManager
    sudo systemctl disable NetworkManager

    sudo systemctl enable systemd-networkd

    sudo systemctl enable systemd-resolved
    sudo systemctl start systemd-resolved

    sudo rm /etc/resolv.conf
    sudo ln -s /run/systemd/resolve/resolv.conf /etc/resolv.conf

    networkctl
    ```

<!--

https://unix.stackexchange.com/questions/113828/how-to-find-and-reload-specific-driver-from-kernel  
https://www.layerstack.com/resources/tutorials/How-to-restart-Network-Interface-or-Network-Adapter-on-Linux-and-Windows-Cloud-Servers  
https://www.cyberciti.biz/faq/linux-restart-network-interface/  

-->


