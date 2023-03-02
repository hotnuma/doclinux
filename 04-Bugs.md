**[ [Home](00-Home.html) | [Systemd](01-Systemd.html) | [FFmpeg](02-FFmpeg.html) | [Network](03-Network.html) | Bugs | [Other](99-Other.html) ]**

## Bugs

---

#### Firefox
    
Impossible de lire cette vidéo avec votre navigateur  
Votre navigateur est à jour  



#### XFCE

* xfsettingsd shortcuts
    
    [https://archived.forum.manjaro.org/t/xfce4-keyboard-shortcut](https://archived.forum.manjaro.org/t/xfce4-keyboard-shortcut-not-working-sometimes-when-logging-in/73498)  
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

* File Manager Sorting
    
    https://gitlab.xfce.org/xfce/thunar/-/issues/68  
    https://unix.stackexchange.com/questions/510530/  
    https://github.com/linuxmint/nemo/issues/2247  

* Window Border
    
    http://sevkeifert.blogspot.com/2014/12/increase-window-border-size-in-xubuntu.html  



#### Gtk

* Double click bug

    https://discourse.gnome.org/t/double-click-on-already-selected-item-will-often-not-open-item-in-nautilus/4590/5  
    https://gitlab.gnome.org/GNOME/nautilus/-/issues/1599

* GtkTreeView Memory leak
    
    https://bugzilla.redhat.com/show_bug.cgi?id=1965195  
    [https://gitlab.gnome.org/GNOME/gtk/-/commit/21f8098261486417](https://gitlab.gnome.org/GNOME/gtk/-/commit/21f8098261486417db371b202bc0494c12017468)  
    https://gitlab.gnome.org/GNOME/gtk/-/pipelines/289296  
    https://gitlab.gnome.org/GNOME/gtk/-/merge_requests/3660  



#### Other

* QtCreator printf

    https://chowdera.com/2020/12/20201208210320326z.html  

* Geany Underscore Bug
    
    https://github.com/geany/geany/issues/1387  
    
    Tools > Configuration Files > filetypes.common
    
    ```ini
    [styling]
    line_height=0;2;
    ```

* Geany double clic on tab buttons
    
    https://github.com/geany/geany/issues/1890  
    
* ifupdown
    
    https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1907878  
    https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1910273  
    [https://git.launchpad.net/ubuntu/+source/ifupdown/](https://git.launchpad.net/ubuntu/+source/ifupdown/commit/?id=54fec5eedfd59adaffe9021c271914578dd05d1b)  

* Startup freeze
    
    ```
    nov. 15 16:28:59 athlon kernel: [drm:drm_atomic_helper_wait_for_flip_done [drm_kms_helper]] *ERROR* [CRTC:62:crtc-0] flip_done timed out
    ```

* Plymouth KillMode=none
    
    [https://gitlab.freedesktop.org/plymouth/](https://gitlab.freedesktop.org/plymouth/plymouth/-/commit/c74b3aef9c34c1c51b2c9c14f10f2906925ed380)  
    https://ubuntuforums.org/showthread.php?t=2457946  


