<link href="style.css" rel="stylesheet"></link>

**[ [Home](00-Home.html) | [Xfce](05-Xfce.html) | [Network](10-Network.html) | FFmpeg | [Systemd](20-Systemd.html) | [Bugs](25-Bugs.html) | [Other](99-Other.html) ]**

## FFmpeg

---

https://ffmpeg.org/documentation.html  
https://ffmpeg.org/ffmpeg-filters.html  

[https://www.codeproject.com/Tips/5356341/](https://www.codeproject.com/Tips/5356341/How-to-Compile-FFmpeg-6-0-in-Linux-and-What-New-Th)  


#### Audio

* Mp3 encoding

    `ffmpeg -i input.m4a -c:a libmp3lame -b:a 192k output.mp3`
    
* Keep left channel

    `ffmpeg -i "input.avi" -c:v copy -c:a libmp3lame -b:a 192k -af "pan=stereo|c0=c0|c1=c0" "output.avi"`
    
* Keep right channel

    `ffmpeg -i "input.avi" -c:v copy -c:a libmp3lame -b:a 192k -af "pan=stereo|c0=c1|c1=c1" "output.avi"`
    
* Audio normalize

    http://superuser.com/questions/323119/

    Analyze audio level with volumedetect
    
    `ffmpeg -i "input.avi" -af "volumedetect" -f null /dev/null`
    
    Read "max_volume", for example -22.5 dB, then amplify audio channel by +22.5dB.
    
    `ffmpeg -i "input.mp4" -c:v copy -c:a libmp3lame -b:a 192k -af "volume=22.5dB" "output.mp4"`
    
* Delay audio by one second

    `ffmpeg -i input.mkv -itsoffset -1.0 -i input.mkv -map 0:0 -map 1:1 -c copy output.mkv`
    
* Choose default audio channel

    ```
    ffmpeg -i "input.mkv" -map 0:0 -map 0:2 -map 0:1 \
    -disposition:a:0 default -disposition:a:1 none -c copy "output.mkv"
    ```
    
* Change audio speed

    `ffmpeg -i "audio.mp3" -af "atempo=1.001" -b:a 192k "audio-faster.mp3"`


#### Video

* Curves
    
    https://hhsprings.bitbucket.io/docs/programming/examples/ffmpeg/manipulating_video_colors/curves.html
    
    ```
    curves=preset=darker
    curves=preset=lighter
    ```


#### Subtitles

* Download subtitles from YouTube

    ```
    yt-dlp --list-subs "URL"
    yt-dlp --write-sub --sub-lang en --skip-download "URL"
    yt-dlp --write-sub --convert-subs=srt --skip-download "URL"
    yt-dlp --write-auto-sub --sub-lang fr --skip-download "URL"
    ```
    
* Remove subtitles and chapters

    `ffmpeg -i in.mp4 -c copy -sn out.mp4`

    `ffmpeg -i in.mp4 -c copy -map_chapters -1 out.mp4`
    
    `ffmpeg -i in.mp4 -c copy -dn -map_metadata:c -1 out.mp4`
    
* Extract subs with MKVToolNix

    `mkvextract tracks "input.mkv" 2:out.idx`
    
* Convert sub to srt online

    https://subtitletools.com/convert-sub-idx-to-srt-online  


#### Cookies

* Youtube

    `yt-dlp --cookies=cookies/youtube.txt "URL"`


#### Other

* Concatenating files
    
    https://stackoverflow.com/questions/7333232/  
    https://trac.ffmpeg.org/wiki/Concatenate  

    Create a file containing the list of files to concatenate :
    
    ```
    file 'part1.avi'
    file 'part2.avi'
    file 'part3.avi'
    ``` 

    Then execute the concat command :

    `ffmpeg -f concat -safe 0 -i "input.txt" -c copy "output.avi"`

* Download thumbnail
    
    `yt-dlp --write-thumbnail --skip-download "URL"`

* Write title metadata
    
    `ffmpeg -i "input.mp4" -c copy -metadata title="Test title" "output.mp4"`

