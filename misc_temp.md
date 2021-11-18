### Misc

git remote show origin

* Most consumming programs.

ps aux k-pcpu | head -6

* pour purger les caches du gestionnaire de paquets APT/.deb

sudo apt clean ; sudo apt autoclean

* Vider les vignettes d'images plus vieilles que 30 jours

find ~/.cache/thumbnails/ -type f -iname \*.png -mtime +30 -delete

* paquets cassés

https://forum.ubuntu-fr.org/viewtopic.php?pid=22273320#p22273320

dpkg -l | grep -v ^ii

dpkg -l | awk '/^rc/{print $2}' | xargs -r sudo dpkg -P

* diagnostique

sudo dmesg | tail -30
ls -l /var/crash

* envoyer rapports

for r in /var/crash/*.crash ; do if test ! -f "${r/.crash/.uploaded}" -a -f "$r" ; then if test "${r:$((-10)):$((4))}" == "$(id -u)" ; then /usr/share/apport/apport-gtk -c "$r" ; else pkexec /usr/share/apport/apport-gtk -c "$r" ; fi ; fi ; done



## Dev

* fix library error

sudo /sbin/ldconfig -v

* pkg-config

pkg-config --libs --cflags gtk+-3.0
pkg-config --modversion glib-2.0

* Push an existing repository

git remote add origin https://github.com/hotnuma/testcmd.git
git branch -M master
git push -u origin master

* Check Remote

git remote -v

* Remove subdirs

git rm -r --cached autre

* clone

git clone https://github.com/hotnuma/libtinycpp.git
git clone -b master --single-branch https://github.com/hotnuma/libtinycpp.git

[Tutorial - Gnome](https://developer.gnome.org/documentation/tutorials.html)\



## Install

* Define an alias

in ~/.bash_rc

alias syslog='tail -150 /var/log/syslog | grep -v 'rtkit-daemon''

* Ubuntu Firefox ESR

sudo add-apt-repository ppa:mozillateam/ppa
sudo apt update
sudo apt install firefox-esr

* Geany Underscore Bug

https://github.com/geany/geany/issues/1387

"Tools" > "Configuration Files" > "filetypes.common"

[styling]
line_height=0;2;

* Win 2K color

#3B6EA5
#53708E

* Ubuntu install codecs and fonts

sudo apt install ubuntu-restricted-extras

* Install NVidia Drivers

https://phoenixnap.com/kb/install-nvidia-drivers-ubuntu

apt search nvidia-driver

or

ubuntu-drivers devices

sudo apt install nvidia-driver-470



## Notes

* analyse shutdown

journalctl -b -1 -e

* disable gnome-keyring-daemon

/etc/pam.d/lightdm
/usr/share/dbus-1/services/

* dmesg

Pour le dmesg c'est un paramètre du noyau (et c'est bien qu'il soit activé) :

$ sudo sysctl -a | grep dmesg
kernel.dmesg_restrict = 1

Si cela te gêne il suffit de modifier le fichier /etc/sysctl.d/10-kernel-hardening.conf en changeant la valeur :

kernel.dmesg_restrict = 0

Si tu as accès avec journalctl aux log du système (ou des autres utilisateurs) c'est que l'utilisateur est dans le groupe wheel ou adm :

$ journalctl |head -2
Hint: You are currently not seeing messages from other users and the system.
Users in groups 'adm', 'systemd-journal' can see all messages.
Pass -q to turn off this notice.

sudo systemctl stop unattended-upgrades
sudo systemctl disable unattended-upgrades

* CSS pre-processor

sassc

* misc

x11-xserver-utils
libxss-dev
socat
p7zip*

* ytdl

https://ytdl-org.github.io/youtube-dl/download.html
sudo apt -y purge youtube-dl
sudo apt install python3-pip
sudo pip install --upgrade youtube_dl

* max pid value

cat /proc/sys/kernel/pid_max

4194304

* upgrade

sudo do-release-upgrade

Sachant que les problèmes éventuels viennent généralement de
dépôts tiers ou de paquets orphelins. On peut déjà jeter
un coup d'œil à tout ça :

cat /etc/apt/sources.list
ls /etc/apt/sources.list.d
cat /etc/apt/sources.list.d/*.list
apt list | grep "installé, local"

* Disable at-spi

~/.profile
append export NO_AT_BRIDGE=1
According to https://wiki.archlinux.de/title/GNOME#Tipps_und_Tricks
this warning can be put off by setting

export NO_AT_BRIDGE=1

in /etc/environment.
or
~/.profile

* ntfs fix

chkdsk /r d:

sudo ntfsfix /dev/sda1



### youtube-dl

* RMC Story url

youtube-dl http://players.brightcove.net/data-account/default_default/index.html?videoId=data-video-id


* use cookies
    youtube-dl --cookies=cookies/youtube.txt "URL"



### FFmpeg

https://trac.ffmpeg.org/wiki
http://ffmpeg.org/documentation.html
https://ffmpeg.org/ffmpeg-filters.html
https://trac.ffmpeg.org/wiki/FFprobeTips

- TESTER UNE COMMANDE SUR UN EXTRAIT

* Obtenir des informations sur le fichier

ffprobe -v quiet -show_format -show_streams "input.avi"

* Créer un extrait de 1 min à partir de 2 min du début

ffmpeg -ss 00:02:00 -i "input.avi" -t 00:01:00 -c copy "output.avi"

* Copier un extrait de 1 min avec uniquement la vidéo

ffmpeg -ss 00:02:00 -i "input.avi" -t 00:01:00 -map 0:0 -c copy "output.avi"

* Copier un extrait de 1 min avec uniquement l'audio

ffmpeg -ss 00:02:00  -i "input.avi" -t 00:01:00 -map 0:1 -c copy "output.avi"


- TRAITEMENTS AUDIO

* Filtrer l'audio :

ffmpeg -i "input.mp4" -c:v copy -af "highpass=f=100" "output.mp4"


- CREER UNE MOSAIQUE D'IMAGES

On peut modifier les options de VLC pour qu'il utilise une numérotation séquencielle.
Dans Options/Préférences, Video, cocher la case "Numérotation séquentielle".

* 2x2 images, chacune de 333px de large :

ffmpeg -i "vlcsnap-%05d.png" -vf "scale=333:-1,tile=2x2" "output.png"

* 3x3 images, chacune de 111px de large :

ffmpeg -i "vlcsnap-%05d.png" -vf "scale=111:-1,tile=3x3" "output.png"

"%05d" signifie, un nombre de 5 chiffres, par exemple vlcsnap-00001.png.

A noter que les images doivent être consécutives,
exemple pic-001.png, pic-002.png, pic-003.png etc...

* Créer automatiquement à partir d'une série de captures d'écran :

ffmpeg -i "input.avi" -frames 1 -vf "select=not(mod(n\,7600)),scale=111:-1,tile=4x4" "output.png"


- AUTRES

* Créer une capture d'écran toutes les 5 minutes :

ffmpeg -i "input.avi" -vf fps=1/300 "pic-%03d.png"

(300 = 5 x 60 secondes)

* Appliquer le même traitement sur une série d'images :

ffmpeg -y -i "input-%03d.png" -vf "scale=666:-1" "output-%03d.png"

* Regrouper plusieurs vidéos en une seule :

Créer d'abord un fichier texte contenant la liste des fichiers a réunir.

Exemple :

file 'part1.avi'
file 'part2.avi'
file 'part3.avi'

Ensuite utiliser ce fichier texte comme fichier d'entrée :

ffmpeg -f concat -safe 0 -i "input.txt" -c copy "output.avi"

concat VOB files      
copy /b *.vob output.vob
cat file*.vob > Allfiles.vob

* Enregistrer un flux en direct

ffmpeg -i http://live.francetv.fr/simulcast/France_3/hls_v1/index.m3u8 \
-bsf:a aac_adtstoasc -c:a copy -c:v copy output.mp4


* Utiliser un preset

ffmpeg -i "input.mp4" -preset ultrafast -crf 18 "output.mp4"
ffmpeg -i "input.mp4" -preset slow -crf 18 "output.mp4"

Le preset détermine la compression et par conséquent la qualité et la taille du fichier.
La valeur par défaut est "médium". Les valeurs plus rapides sont fast, faster, veryfast,
superfast, ultrafast. Les valeurs plus lents sont, slow, slower, veryslow, placebo.


* Upscale and unsharp with default values :

ffmpeg -i input.mp4 -vf "scale=640:480:flags=lanczos,unsharp" output.mp4
ffmpeg -i input.mp4 -vf "scale=640:480,unsharp" -sws_flags lanczos output.mp4

For downscaling use Lanczosresize only
For upscaling use Bicubicresize with 0.45 to 0.6 sharpening.    


* Diaporama
ffmpeg -framerate 1/12 -i pic-%03d.png -c:v libx264 -r 25 -pix_fmt yuv420p out.mp4
ffmpeg -i "vlcsnap-%05d.png" -vf "scale=-1:480,pad=640:480:154:0" "input-%05d.png"

Add metadata :

ffmpeg -i "input.avi" -c copy -metadata title="Le schpountz" "output.avi"
ffmpeg -i "input.avi" -c copy -map_metadata -1 -metadata title="1938 - Le schpountz" -metadata comment="tt0030722" "output.avi"

ffmpeg -i [INPUT] -aspect 4:3 -c copy [OUPTPUT]

ffmpeg -ss 00:00:14 -i "D:/Films/Convert/1945 - Carmen-orig.mp4" \
-deinterlace -b:v 1200k -vf hue=s=0,crop=704:566:0:2 "1945 - Carmen-orig.mp4"

ffmpeg -i "D:/Films/Films 4-7/1935 - La Kermesse héroïque.avi" \
-b:v 1000k -vf scale=720:576 "1935 - La Kermesse héroïque.avi"

ffmpeg -t 01:51:20 -i "D:/Films Supprimer/1945 - La vie de boheme.ts" \
-b:v 1000k -deinterlace -vf crop=530:566:91:2 -aspect 4:3

ffmpeg -i "D:/Films/Convert/1929 - Adieu Mascotte.mp4" -preset ultrafast \
-crf 22 -deinterlace -r 25 -vf crop=626:470:8:6 "1929 - Adieu Mascotte.mp4"

ffmpeg -y -i "1934 - Caravane-orig.mp4" -preset slow -vsync 0 -crf 22 \
-vf hue=s=0,crop=938:704:15:3,unsharp=3:3:0.4 -af highpass=f=100 "1934 - Caravane.mp4"

ffmpeg -y -t 01:34:46 -i "D:/Films Selection/_1935 - L'École des cocottes.avi" -crf 18 \
-preset slow -vsync 0 -vf hue=s=0,crop=680:544:14:14,unsharp=3:3:0.3 -b:a 256k \
"1935 - L'École des cocottes-unsharp303.mp4"

ffmpeg -y -t 01:29:54 -i "D:/Films Convert/1941 - Valet Maitre.mkv" -b:v 2000k \
-preset slow -vsync 0 -vf hue=s=0,crop=710:568:0:0,unsharp=3:3:0.3 "1941 - Valet Maitre.mp4"

"Too many packets buffered for output stream"

-max_muxing_queue_size 1024


ffmpeg -framerate 1/2 -loop 1 -t 1 -i NWL1.png -framerate 60 -loop 1 -t 1 -i NWL2.png -framerate 60 -loop 1 -t 1 -i NWL3.png -framerate 60 -loop 1 -t 1 -i NWL4.png -framerate 60 -loop 1 -t 1 -i NWL5.png -filter_complex "[1:v][0:v]blend=all_expr='A*(if(gte(T,0.5),1,T/0.5))+B*(1-(if(gte(T,0.5),1,T/0.5)))'[b1v]; [2:v][1:v]blend=all_expr='A*(if(gte(T,0.5),1,T/0.5))+B*(1-(if(gte(T,0.5),1,T/0.5)))'[b2v]; [3:v][2:v]blend=all_expr='A*(if(gte(T,0.5),1,T/0.5))+B*(1-(if(gte(T,0.5),1,T/0.5)))'[b3v]; [4:v][3:v]blend=all_expr='A*(if(gte(T,0.5),1,T/0.5))+B*(1-(if(gte(T,0.5),1,T/0.5)))'[b4v]; [0:v][b1v][1:v][b2v][2:v][b3v][3:v][b4v][4:v]concat=n=9:v=1:a=0,format=yuv420p,scale=480:270[vx]" -map "[vx]" -c:v libx264 -r 30 -pix_fmt yuv420p "EXfondu2.mp4"

ffmpeg -i "video.mp4"  -i "audio.mp3" -c copy -shortest "output.mp4"

$ youtube-dl --extract-audio --audio-format mp3 -l "https://www.youtube.com/watch?v=xN8Q75ov6A4"


remux avi to mp4
avi2raw.exe -v "D:\Films\Films 3-8\1936 - Topaze.avi" "1936 - Topaze.264"
avi2raw.exe -a "D:\Films\Films 3-8\1936 - Topaze.avi" "1936 - Topaze.aac"
ffmpeg -i "D:\Films\Films 3-8\1936 - Topaze.avi" -vn -c:a copy "1936 - Topaze.aac"
mp4box.exe -add "1936 - Topaze.264" -fps 25 -add "1936 - Topaze.aac" "1936 - Topaze.mp4"
ffmpeg -i input.mkv -itsoffset 1.0 -i input.mkv -map 0:0 -map 1:1 -c copy output.mkv   
ffmpeg -ss 00:00:33.5 -i "D:\Downloads\Invitation.to.the.Waltz.1935.mkv" \
-c copy -avoid_negative_ts 1 "D:\Downloads\1935 - Invitation to the Waltz.mkv"

screenshot :
ffmpeg -ss 00:00:30 -i "D:\Films\Convert\1937 - Forfaiture-0.mkv" -vframes 1 -q:v 2 output.jpg



### Network

* DND BBox 

echo "192.168.1.254  mabbox.bytel.fr" >> /etc/hosts

* interfaces

The following procedure works for Ubuntu 18.04 (Bionic Beaver)

I. Reinstall the ifupdown package:

sudo apt update
sudo apt install ifupdown

II. Configure your /etc/network/interfaces file with configuration stanzas such as:

---

# The loopback network interface
auto lo
iface lo inet loopback

auto enp27s0
iface enp27s0 inet dhcp

---

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

---

III. Make the configuration effective (no reboot needed):

sudo ifdown --force enp27s0 lo && ifup -a
sudo systemctl unmask networking
sudo systemctl enable networking
sudo systemctl restart networking

IV. Disable and remove the unwanted services:

sudo systemctl stop systemd-networkd.socket systemd-networkd networkd-dispatcher systemd-networkd-wait-online
sudo systemctl disable systemd-networkd.socket systemd-networkd networkd-dispatcher systemd-networkd-wait-online
sudo systemctl mask systemd-networkd.socket systemd-networkd networkd-dispatcher systemd-networkd-wait-online

sudo apt -y purge nplan netplan.io
#sudo apt --assume-yes purge nplan netplan.io

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

systemctl restart systemd-resolved

The DNS entries in the ifupdown INTERFACES(5) file, as shown above,
are only relevant if you make use of RESOLVCONF(8) or similar.

* disable network manager

Using Systemd

Systemd became the default initialization system in Ubuntu 15.04.
Here's how to stop and disable Network Manager without uninstalling
it (taken from AskUbuntu):

Stop network manager

sudo systemctl stop NetworkManager.service
sudo systemctl stop NetworkManager-wait-online.service
sudo systemctl stop NetworkManager-dispatcher.service
sudo systemctl stop network-manager.service

Disable network manager (permanently) to avoid it restarting after a reboot

sudo systemctl disable NetworkManager.service
sudo systemctl disable NetworkManager-wait-online.service
sudo systemctl disable NetworkManager-dispatcher.service
sudo systemctl disable network-manager.service

* uninstall network manager

First edit /etc/network/interfaces so that the ifup utility can be
used to configure eth0 once NetworkManager is gone.

Remove NetworkManager from the system

sudo apt purge network-manager

Configure eth0 using ifup.

sudo ifup eth0

* DNS

CODE:
(check to see if resolvconf is installed)
sudo systemctl status resolvconf.service

(install resolveconf package)
sudo apt update
sudo apt install resolvconf

(confirm resolveconf is running)
sudo systemctl status resolvconf.service

(if resolveconf isn't running, enable then start it)
sudo systemctl enable resolvconf.service
sudo systemctl start resolvconf.service

(check resolveconf status)
sudo systemctl status resolvconf.service

(edit the head file)
sudo nano /etc/resolvconf/resolv.conf.d/head

(enter your nameservers below the comments)
nameserver 8.8.8.8
nameserver 8.8.4.4

(update resolve.conf file)
sudo resolvconf --enable-updates
sudo resolvconf -u

(check if changes we successful)
sudo nano /etc/resolv.conf

* ModemManager

sudo systemctl stop ModemManager.service
sudo systemctl disable ModemManager.service


