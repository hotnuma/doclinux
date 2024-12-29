<link href="style.css" rel="stylesheet"></link>

**[ [Home](00-Home.html) | Xfce | [Systemd](10-Systemd.html) | [Network](15-Network.html) | [FFmpeg](20-FFmpeg.html) | [Bugs](25-Bugs.html) | [Other](99-Other.html) ]**

## Xfce

---

#### Reference

* Links
    
    https://wiki.archlinux.org/title/xfce  
    https://wiki.xfce.org/fr/howto/customize-menu  
    
    [xfce-forum](https://forum.xfce.org/search.php?action=show_recent)  
    [xfce-gitlab](https://gitlab.xfce.org/xfce)  
    [xfce-gitlab-apps](https://gitlab.xfce.org/apps)  
    [xfce-developer](https://developer.xfce.org/)  

* Xfce Dialogs
    
    | Command                   | Description               |
    | :------------------------ | :------------------------ |
    | xfce4-settings-manager    | Configuration Panel       |
    | xfce4-mime-settings       | Default Apps              |
    | xfce4-keyboard-settings   | Keyboard Settings         |
    | xfce4-mouse-settings      | Mouse Settings            |
    | xfce4-notifyd-config      | Notifications Settings    |
    | xfce4-panel --preferences | Panel Preferences         |
    | xfce4-session-settings    | Session Settings          |
    | xfce4-settings-editor     | Xfconf Editor             |
    | xfce4-appearance-settings | Appearance                |
    | xfce4-display-settings    | Display Settings          |
    | xfwm4-settings            | Window Manager Settings   |
    | xfwm4-tweaks-settings     | Window Manager Tweaks     |
    

#### Sessions

* Desktop sessions
    
    https://askubuntu.com/questions/77191/  
    https://askubuntu.com/questions/62833/  
    
    ```
    /usr/share/xsessions/lightdm-xsession.desktop
    /usr/share/xsessions/xfce.desktop
    ```
    
* lightdm
    
    https://wiki.archlinux.org/title/LightDM  
    
    ```
    /etc/lightdm/lightdm.conf
    /usr/share/lightdm/lightdm.conf.d/
    ```
    
    Show configuration : `lightdm --show-config`

* startup

    ```
    /sbin/ini
        graphical.target
        lightdm
            startxfce4
                Xorg
                lightdm --session-child
                    xfce4-session
        agetty
        systemd/systemd --user
    ```

* Bash Startup Files
    
    [https://www.linuxfromscratch.org/blfs/view/11.0/postlfs/prof](https://www.linuxfromscratch.org/blfs/view/11.0/postlfs/profile.html)  


#### Configuration

* xfconf-query
    
    https://docs.xfce.org/xfce/xfconf/xfconf-query  
    [http://manpages.ubuntu.com/manpages/...](http://manpages.ubuntu.com/manpages/bionic/man1/xfconf-query.1.html)  

* Profile

    ```
    /etc/environment
    $HOME/.profile
    /etc/profile
    ```

* Default config
    
    `/etc/skel/.config`

* XDG_CONFIG_DIRS
    
    https://askubuntu.com/questions/1179729/  

    https://xubuntu-users.narkive.com/yXIe6V85/difference-between-etc-xdg-and-etc-xdg-xdg-xubuntu  
    https://gitlab.xfce.org/xfce/xfce4-session/-/issues/50  

    `$XDG_CONFIG_DIRS : /etc/xdg`

* XFCE Config
    
    ```
    $HOME/.config/xfce4/
    /etc/xdg/xfce4/
    ```

* xfce4-session

    `/etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml`

* xsettings
    
    http://www.freedesktop.org/wiki/Specifications/XSettingsRegistry  

    `/etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml`

* Xdg menu
    
    `/etc/xdg/menus/xfce-applications.menu`

* Keyboard shortcuts
    
    ```
    $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml
    /etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml
    ```

* The offending /etc/xdg/xfce4/xinitrc script
    
    https://gist.github.com/ncraike/6204799  

* XF86 Multimedia Keys
    
    https://unix.stackexchange.com/questions/426977/  


#### Applications

* Launchers

    ```
    $HOME/.local/share/applications/
    /usr/share/applications/
    /usr/local/share/applications/
    ```

* Prefered applications

    `/etc/xdg/xfce4/helpers.rc`
    
* Default Applications
    
    ```
    $HOME/.config/mimeapps.list
    /usr/share/xfce4/applications/defaults.list
    /etc/xfce4/defaults.list
    /usr/share/applications/defaults.list
    /etc/gnome/defaults.list
    ```

* XDG MIME Applications
    
    https://wiki.archlinux.org/title/XDG_MIME_Applications


#### Themes

* Location
    
    `$HOME/.themes/`

* Desktop background
    
    `hsetroot -solid '#5e5c64'`

    `feh --bg-scale /usr/share/rpd-wallpaper/clouds.jpg`

* Wallpapers

    ```
    $HOME/.local/share/xfce4/backdrops/
    /usr/share/xfce4/backdrops/
    /usr/share/xfce4/backdrops/xfce/
    /usr/share/backgrounds/
    ```


#### Other

* Thunar Custom Actions
    
    https://docs.xfce.org/xfce/thunar/4.12/custom-actions  
    https://forum.xfce.org/viewtopic.php?id=12633  
    
    `xfce4-terminal -e 'bash -c "extract.sh %f; bash"'`


