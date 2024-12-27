<link href="style.css" rel="stylesheet"></link>

**[ [Home](00-Home.html) | [Xfce](05-Xfce.html) | [Systemd](10-Systemd.html) | Network | [FFmpeg](20-FFmpeg.html) | [Bugs](25-Bugs.html) | [Other](99-Other.html) ]**

## Network

---

#### Reference

* Configuration
    
    https://wiki.debian.org/NetworkConfiguration  
    https://wiki.debian.org/NetworkManager  

* Read DNS servers
    
    ```
    cat /etc/resolv.conf
    ls /etc/resolv.conf
    ```

* Change DNS

    https://serverfault.com/questions/810636/  
    
    Get network connection name : `nmcli con`
    
    ```
    nmcli con mod "Wired connection 1" ipv4.dns "8.8.8.8 8.8.4.4"
    nmcli con mod "Wired connection 1" ipv4.ignore-auto-dns yes
    service NetworkManager restart
    cat /etc/resolv.conf
    ```

* Read hostname and domain name
    
    ```
    hostname
    hostname -d
    ```

* Read network configuration
    
    ```
    ip a
    ip route show default
    networkctl
    networkctl status
    ```
    
    List interfaces : `ls /sys/class/net`
    
* Change interface state
    
    ```
    sudo ifdown eth0
    sudo ifup eth0
    ```

    ```
    sudo ip link set dev eth0 down
    sudo ip link set dev eth0 up
    ```
    
    `sudo systemctl restart networking`

* Predictable Network Interface Names
    
    [https://www.freedesktop.org/.../PredictableNetworkInterfaceNames](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)  
    
    Switch back to eth0 :
    
    Add `GRUB_CMDLINE_LINUX="net.ifnames=0"` in `/etc/default/grub`
    
    Execute `sudo update-grub`
    

#### Switch to /etc/network/interfaces

* Install ifupdown
    
    ```
    sudo apt install ifupdown resolvconf
    ```

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
    auto lo
    iface lo inet loopback

    auto eth0
    iface eth0 inet static
        address 192.168.1.100/24
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.254
        dns-nameservers 8.8.8.8 8.8.4.4
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
    Address=192.168.1.100/24
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

    networkctl
    ```

<!--

    sudo cp /etc/resolv.conf /etc/resolv.conf.bak
    sudo rm /etc/resolv.conf
    sudo ln -s /run/systemd/resolve/resolv.conf /etc/resolv.conf
    
    sudo cp /etc/resolv.conf /etc/resolv.conf.bak
    sudo rm /etc/resolv.conf
    sudo ln -sf /run/systemd/resolve/stub-resolv.conf /etc/resolv.conf
    
    ip route show default | cut -d " " -f 5

-->


