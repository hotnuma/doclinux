<link href="style.css" rel="stylesheet"></link>

**[ [Home](00-Home.html) | [Xfce](05-Xfce.html) | [Systemd](10-Systemd.html) | [Network](15-Network.html) | [FFmpeg](20-FFmpeg.html) | Bugs | [Other](99-Other.html) ]**

## Bugs

---

#### Thunar

* memory leak
    
    https://gitlab.xfce.org/xfce/thunar/-/issues/573  
    [https://gitlab.xfce.org/xfce/thunar/-/commit/...](https://gitlab.xfce.org/xfce/thunar/-/commit/bdb2f762cf335e621d9bd2556f5f92306ecf4201)  

* Sorting
    
    https://gitlab.xfce.org/xfce/thunar/-/issues/68  
    https://unix.stackexchange.com/questions/510530/  
    https://github.com/linuxmint/nemo/issues/2247  


#### XFCE

* xfsettingsd shortcuts
    
    [https://archived.forum.manjaro.org/t/xfce4-keyboard-shortcut](https://web.archive.org/web/20210123051319/https://archived.forum.manjaro.org/t/xfce4-keyboard-shortcut-not-working-sometimes-when-logging-in/73498)  
    [https://itectec.com/unixlinux/](https://itectec.com/unixlinux/linux-cannot-change-global-keyboard-shortcuts-in-linux-mint-xfce/)  
    [https://gitlab.xfce.org/xfce/xfce4-settings/](https://gitlab.xfce.org/xfce/xfce4-settings/-/issues/116)  
    [https://gitlab.xfce.org/xfce/xfce4-settings/](https://gitlab.xfce.org/xfce/xfce4-settings/-/issues/232)  
    [https://gitlab.xfce.org/xfce/xfce4-settings/](https://gitlab.xfce.org/xfce/xfce4-settings/-/issues/257)  
    
* /usr/share appears twice in XDG_DATA_DIRS
    
    https://gitlab.xfce.org/xfce/xfce4-session/-/issues/50  
    https://gitlab.xfce.org/xfce/xfce4-session/-/issues/111  

* CSD
    
    https://gitlab.xfce.org/xfce/xfce4-settings/-/issues/235  
    https://forum.xfce.org/viewtopic.php?id=15116  
    https://github.com/Xfce-Classic/libxfce4ui-nocsd  
    https://gitlab.xfce.org/xfce/libxfce4ui/-/issues/14  
    https://winaero.com/disable-client-side-decorations-in-xfce-for-open-save-dialog/  

* Window Border
    
    http://sevkeifert.blogspot.com/2014/12/increase-window-border-size-in-xubuntu.html  


#### Gtk

* Go Back shortcut Alt+P

    https://gitlab.gnome.org/GNOME/evince/-/issues/1095  
    

#### Errors

* gnome-keyring-daemon
    
    https://bbs.archlinux.org/viewtopic.php?id=224652  
    https://askubuntu.com/questions/243210/  
    
    ```
    gnome-keyring-daemon: couldn't access control socket: /run/user/1000/keyring/control
    ```

* udisk2
    
    https://github.com/storaged-project/udisks/issues/638  
    https://github.com/storaged-project/udisks/commit/818b7b29b0d8fee43994646a944d046b1cf47633  

    ```
    udisksd: failed to load module mdraid: libbd_mdraid.so.2: cannot open shared object file: No such file or directory
    udisksd: Failed to load the 'mdraid' libblockdev plugin

    /etc/udisks2/udisks2.conf
    ```

* systemd
    
    https://bbs.archlinux.org/viewtopic.php?id=261330  

    ```
    systemd: -.slice: Failed to migrate controller cgroups from
    /user.slice/user-1000.slice/user@1000.service, ignoring: Permission denied
    ```
    
    In `/etc/default/grub` edit `GRUB_CMDLINE_LINUX_DEFAULT` :
    
    `GRUB_CMDLINE_LINUX_DEFAULT="systemd.unified_cgroup_hierarchy=true quiet splash"`

    Update grub.conf : `sudo update-grub`

* Startup/Restart freeze
    
    ```
    nov. 15 16:28:59 athlon kernel: [drm:drm_atomic_helper_wait_for_flip_done [drm_kms_helper]] *ERROR* [CRTC:62:crtc-0] flip_done timed out
    ```

    ```
    dev/sdaX: clean, X files, X blocks
    ```
    
* Firefox
    
    https://support.google.com/youtube/thread/120697903?hl=en&msgid=120734104  

    ```
    Your browser can't play this video.
    Impossible de lire cette vidéo avec votre navigateur
    Votre navigateur est à jour
    ```


#### Other

* Geany Underscore Bug
    
    https://github.com/geany/geany/issues/1387  
    
    Tools > Configuration Files > filetypes.common
    
    ```ini
    [styling]
    line_height=0;2;
    ```

* Geany double clic on tab buttons
    
    https://github.com/geany/geany/issues/1890  
    
* Mpv
    
    ```
    ls -l /var/crash
    -rw-r-----  1 hotnuma hotnuma 23227218 févr. 24 05:59 _usr_bin_mpv.1000.crash
    ```

* QtCreator printf

    https://chowdera.com/2020/12/20201208210320326z.html  

* ifupdown
    
    https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1907878  
    https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1910273  
    [https://git.launchpad.net/ubuntu/+source/ifupdown/](https://git.launchpad.net/ubuntu/+source/ifupdown/commit/?id=54fec5eedfd59adaffe9021c271914578dd05d1b)  

* Plymouth KillMode=none
    
    [https://gitlab.freedesktop.org/plymouth/](https://gitlab.freedesktop.org/plymouth/plymouth/-/commit/c74b3aef9c34c1c51b2c9c14f10f2906925ed380)  
    https://ubuntuforums.org/showthread.php?t=2457946  


<!--

* Gtk4 Listview scrolling is broken
    
    https://gitlab.gnome.org/GNOME/gtk/-/issues/2971  

* Double click bug

    https://discourse.gnome.org/t/double-click-on-already-selected-item-will-often-not-open-item-in-nautilus/4590/5  
    https://gitlab.gnome.org/GNOME/nautilus/-/issues/1599  

* GtkTreeView Memory leak
    
    https://bugzilla.redhat.com/show_bug.cgi?id=1965195  
    [https://gitlab.gnome.org/GNOME/gtk/-/commit/21f8098261486417](https://gitlab.gnome.org/GNOME/gtk/-/commit/21f8098261486417db371b202bc0494c12017468)  
    https://gitlab.gnome.org/GNOME/gtk/-/pipelines/289296  
    https://gitlab.gnome.org/GNOME/gtk/-/merge_requests/3660  

* Gtk 3.24.26 preedit bug
    
    https://gitlab.gnome.org/GNOME/gtk/-/issues/5744  

* Tooltip position
    
    https://gitlab.gnome.org/GNOME/gtk/-/issues/2784  

-->


