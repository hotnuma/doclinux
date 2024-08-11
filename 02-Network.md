<link href="style.css" rel="stylesheet"></link>

**[ [Home](00-Home.html) | [Systemd](01-Systemd.html) | Network | [FFmpeg](03-FFmpeg.html) | [Bugs](04-Bugs.html) | [Other](99-Other.html) ]**

## Network

---

#### Reference

* Configuration
    
    https://wiki.debian.org/NetworkConfiguration  
    [https://www.fr.linuxfromscratch.org/.../network.html](https://www.fr.linuxfromscratch.org/view/lfs-7.9-systemd-fr/chapter07/network.html)  

* Read network configuration
    
    `networkctl`
    
    `ip route show default`
    
    `ip route show default | cut -d " " -f 5`

* Read DNS servers
    
    `cat /etc/resolv.conf`

* Predictable Network Interface Names
    
    [https://www.freedesktop.org/.../PredictableNetworkInterfaceNames](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)  
    
    Switch back to eth0 :
    
    Add `GRUB_CMDLINE_LINUX="net.ifnames=0"` in `/etc/default/grub`
    
    Execute `sudo update-grub`
    
* Set BBox name in hosts file

    `echo "192.168.1.254  mabbox.bytel.fr" >> /etc/hosts`

* Disable IPv6 in Kernel

    Edit `/etc/default/grub` and add `ipv6.disable=1` :
    
    `GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet"`

    Update grub :

    `sudo update-grub`


#### Interfaces

* Use systemd-networkd
    
    [https://linux.fernandocejas.com/docs/...systemd-networkd](https://linux.fernandocejas.com/docs/how-to/switch-from-network-manager-to-systemd-networkd)  
    
    Create a configuration file :
    
    `/etc/systemd/network/00-eth0.network`

    ```
    [Match]
    Name=eth0

    [Network]
    LinkLocalAddressing=no
    IPv6AcceptRA=no
    DHCP=no
    Address=192.168.1.101/24
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

    sudo mv /etc/resolv.conf /etc/resolv.conf.bak
    sudo ln -s /run/systemd/resolve/resolv.conf /etc/resolv.conf

    networkctl
    ```

<!--

* Disable IPv6

    In `/etc/sysctl.conf` add the following :
    
    ```
    net.ipv6.conf.all.disable_ipv6 = 1
    net.ipv6.conf.default.disable_ipv6 = 1
    net.ipv6.conf.lo.disable_ipv6 = 1
    net.ipv6.conf.tun0.disable_ipv6 = 1
    ```
    
    Reboot the system.

-->


