
Video Transcoding
=================
::

    ffmpeg.exe -i o_statecnem_kovari.avi -acodec aac -strict experimental -vcodec mpeg4 -b:v 1200k o_statecnem_kovari.mp4

Audio Encoding
==============
Convert all files in current directory from flac to mp3::

    FOR /F "tokens=*" %G IN ('dir /b *.flac') DO ffmpeg -i "%G" -acodec mp3 "%~nG.mp3" 
