#Startup Sequence

Xubuntu / Xorg

/sbin/ini

    graphical.target

    lightdm
        Xorg
        lightdm --session-child
            xfce4-session
    agetty
    systemd/systemd --user

