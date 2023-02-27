**[ [Home](00-Home.html) | [Systemd](01-Systemd.html) | [FFmpeg](02-FFmpeg.html) | Network | [Bugs](04-Bugs.html) | [Other](99-Other.html) ]**

## Network

---

* DNS
    
    https://askubuntu.com/questions/1080230/  

* Netplan
    
    https://askubuntu.com/questions/1034711/  

* Uninstall NetworkManager
    
    https://askubuntu.com/questions/249944/  
    https://help.ubuntu.com/community/NetworkManager  
    [https://techpiezo.com/linux/switch-back-to-ifupdown](https://techpiezo.com/linux/switch-back-to-ifupdown-etc-network-interfaces-in-ubuntu/)  
    https://askubuntu.com/questions/1031709/  

* DNS BBox 

    ```
    echo "192.168.1.254  mabbox.bytel.fr" >> /etc/hosts
    ```

#### Network

* interfaces

    The following procedure works for Ubuntu 18.04 (Bionic Beaver)

    I. Reinstall the ifupdown package:

    ```
    sudo apt update
    sudo apt install ifupdown
    ```

    II. Configure your /etc/network/interfaces file with configuration stanzas such as:

    ```
    # The loopback network interface
    auto lo
    iface lo inet loopback

    auto enp27s0
    iface enp27s0 inet dhcp

    # The loopback network interface
    auto lo
    iface lo inet loopback

    allow-hotplug enp27s0
    auto enp27s0
    iface enp27s0 inet static
    address 192.168.1.100
    netmask 255.255.255.0
    broadcast 192.168.1.255
    gateway 192.168.1.254
    # Only relevant if you make use of RESOLVCONF(8)
    # or similar...
    dns-nameservers 8.8.8.8 8.8.4.4
    ```

    III. Make the configuration effective (no reboot needed):

    ```
    sudo ifdown --force enp27s0 lo && ifup -a
    sudo systemctl unmask networking
    sudo systemctl enable networking
    sudo systemctl restart networking
    ```

    IV. Disable and remove the unwanted services:

    ```
    sudo systemctl stop systemd-networkd.socket systemd-networkd networkd-dispatcher systemd-networkd-wait-online
    sudo systemctl disable systemd-networkd.socket systemd-networkd networkd-dispatcher systemd-networkd-wait-online
    sudo systemctl mask systemd-networkd.socket systemd-networkd networkd-dispatcher systemd-networkd-wait-online

    sudo apt -y purge nplan netplan.io
    #sudo apt --assume-yes purge nplan netplan.io
    ```

    Then, you're done.

    Note: You MUST, of course, adapt the values according to your system
    (network, interface name...).

    V. DNS Resolver

    Because Ubuntu Bionic Beaver (18.04) make use of the DNS stub
    resolver as provided by SYSTEMD-RESOLVED.SERVICE(8), you SHOULD
    also add the DNS to contact into the /etc/systemd/resolved.conf
    file. For instance:

    ....
    DNS=1.1.1.1 1.0.0.1
    ....

    and then restart the systemd-resolved service once done:

    ```
    systemctl restart systemd-resolved
    ```

    The DNS entries in the ifupdown INTERFACES(5) file, as shown above,
    are only relevant if you make use of RESOLVCONF(8) or similar.

* disable network manager

    Using Systemd

    Systemd became the default initialization system in Ubuntu 15.04.
    Here's how to stop and disable Network Manager without uninstalling
    it (taken from AskUbuntu):

    Stop network manager

    ```
    sudo systemctl stop NetworkManager.service
    sudo systemctl stop NetworkManager-wait-online.service
    sudo systemctl stop NetworkManager-dispatcher.service
    sudo systemctl stop network-manager.service
    ```

    Disable network manager (permanently) to avoid it restarting after a reboot

    ```
    sudo systemctl disable NetworkManager.service
    sudo systemctl disable NetworkManager-wait-online.service
    sudo systemctl disable NetworkManager-dispatcher.service
    sudo systemctl disable network-manager.service
    ```

* uninstall network manager

    First edit /etc/network/interfaces so that the ifup utility can be
    used to configure eth0 once NetworkManager is gone.

    Remove NetworkManager from the system

    ```
    sudo apt purge network-manager
    ```

    Configure eth0 using ifup.

    ```
    sudo ifup eth0
    ```

* DNS

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

