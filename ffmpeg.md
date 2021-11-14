==============================================================
 FFmpeg Diabolicum Handbook by Fantônumas >:-D
 
 https://ffmpeg.org/documentation.html
 https://ffmpeg.org/ffmpeg-filters.html

==============================================================

- TRAITEMENTS AUDIO

    * Encoder en mp3 :

      ffmpeg -i input.m4a -c:a libmp3lame -b:a 192k output.mp3

    * Ne garder qu'un seul canal audio :

      Certains fichiers tirés d'une VHS n'ont qu'un seul canal audio, on peut donc sélectionner cet
      unique canal et le diriger dans les deux voies gauche et droite.

      Garder la voie gauche
      ffmpeg -i "input.avi" -c:v copy -c:a libmp3lame -b:a 192k -af "pan=stereo|c0=c0|c1=c0" "output.avi"

      Garder la voie droite
      ffmpeg -i "input.avi" -c:v copy -c:a libmp3lame -b:a 192k -af "pan=stereo|c0=c1|c1=c1" "output.avi"

    * Normaliser le volume audio :
      
      source : http://superuser.com/questions/323119/how-can-i-normalize-audio-using-ffmpeg

      Analyser le volume audio avec le filtre "volumedetect".

      ffmpeg -i "input.avi" -af "volumedetect" -f null NUL

      Lire la valeur "max_volume", par exemple -22.5 dB.
      On peut augmenter de la même valeur :

      ffmpeg -i "input.mp4" -c:v copy -c:a libmp3lame -b:a 192k -af "volume=22.5dB" "output.mp4"

    * Retarder la piste audio de 1 seconde.

      ffmpeg -i input.mkv -itsoffset 1.0 -i input.mkv -map 0:0 -map 1:1 -c copy output.mkv
      
    * Choisir la piste par défaut
    
      ffmpeg -i "input.mkv" -map 0:0 -map 0:2 -map 0:1 \
      -disposition:a:0 default -disposition:a:1 none -c copy "output.mkv"

    * Changer la vitesse audio
	
      ffmpeg -i "audio.mp3" -af "atempo=1.001" -b:a 192k "audio-2.mp3"

- Subtitles

    * Download subtitles

      youtube-dl --write-sub --sub-lang en --skip-download URL
      youtube-dl --cookies=cookies/youtube.txt --write-auto-sub --convert-subs=srt --skip-download URL
      youtube-dl --cookies=cookies/youtube.txt URL

    * Remove all subs and chapters :

      ffmpeg -i in.mp4 -c:v copy -c:a copy -map_chapters -1 out.mp4
      or
      ffmpeg -i in.mp4 -c copy -dn -map_metadata:c -1 out.mp4

- Autre

    * Title metadata
    
    ffmpeg -i "input.mp4" -c copy -metadata title="Test title" "output.mp4"
    
    * pts has no value

    First, a background on why this error exists.
    AVI does not support variable frame rate video.
    So somewhere at the start of the file the frame rate is recorded.
    mp4 does support variable frame rate, so it is required that
    the duration of each frame is known. In ffmpeg the pts generation
    for fixed frame rate video is usually handled by the decoder.
    but by using -codec copy, you are bypassing the decoder.
    The solution is specifying -fflags +genpts (must be before
    the input file is specified with -i).

    * generate pts

        ffmpeg -fflags +genpts -i film.avi -codec copy film.mp4
        
        or
        
        ffmpeg -i source.mp4 -map 0:v -vcodec copy -bsf:v h264_mp4toannexb source-video.h264
        
        ffmpeg -fflags +genpts -r 60 -i source-video.h264 -vcodec copy output.mp4

    * extract subs
        
        mkvextract tracks "input.mkv" 2:out.idx
        
    * convert sub to str
        
        https://subtitletools.com/convert-sub-idx-to-srt-online

- youtube-dl

    * RMC Story url
    
    youtube-dl http://players.brightcove.net/data-account/default_default/index.html?videoId=data-video-id
        

