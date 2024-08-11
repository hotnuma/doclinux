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


#### Interfaces

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

#### Network

* networkd: interfaces stuck in "configuring" state · Issue #17831 · systemd/systemd · GitHub
    
    https://github.com/systemd/systemd/issues/17831  

* Disabling IPv6 causes network interface to stay in configuring status · Issue #1419 · coreos/bugs · GitHub
    
    https://github.com/coreos/bugs/issues/1419  

* Systemd-networkd: ipv6 et ipv4 - Support Debian - debian-fr.org
    
    [https://www.debian-fr.org/t/systemd-networkd-ipv6-et-ipv4/80](https://www.debian-fr.org/t/systemd-networkd-ipv6-et-ipv4/80773/7)  

* [Résolu]Changer le DNS (de façon stable) / Accès internet et réseaux / Forum Ubuntu-fr.org
    
    https://forum.ubuntu-fr.org/viewtopic.php?id=2074877  

-->


