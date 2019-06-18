
Video Transcoding
=================
::

    ffmpeg.exe -i o_statecnem_kovari.avi -acodec aac -strict experimental -vcodec mpeg4 -b:v 1200k o_statecnem_kovari.mp4

Audio Encoding
==============
Convert all files in current directory from flac to mp3::

    FOR /F "tokens=*" %G IN ('dir /b *.flac') DO ffmpeg -i "%G" -acodec mp3 "%~nG.mp3" 

DVD Ripping
===========

Begin by opening a terminal window and typing the following command::

    sudo apt-get install handbrake

This will install the video decoding software for converting DVDs to MP4.

Next, type the following command at the terminal prompt to install the restricted extras package. This will install a collection of codecs::

    sudo apt-get install ubuntu-restricted-extras

During the installation, a blue screen will appear with a license agreement. Press Tab to highlight the option to accept the agreement and press Enter.

Finally, install the libdvd-pkg to install a library that will let you play DVDs within Ubuntu by entering the following command::

    sudo apt-get install libdvd-pkg
    
During the installation, you will be asked to accept an agreement. Press Tab to select the OK option and press Enter.

At the end of the process, you may get a message saying you need to run another apt-get command to continue installing the package. If you get this message type the following command::

    sudo dpkg-reconfigure libdvd-pkg
    
Allow the installation to finish, and then run Handbrake either by pressing the super key to bring up the dash and searching for Handbrake or by running the following command in the terminal::

    handbrake &

After installing and launching Handbrake in Ubuntu, insert a DVD into your disc drive. In Handbrake, click on the Source button in the top left corner of the screen. In the bottom left corner of the screen, you will see a dropdown called Detected DVD Devices. Select your DVD player from the list and click OK. A scan will take place to import information about the DVD. 

Click the Summary tab. Details for the DVD that you intend to rip along with settings are displayed. You can change the output format by clicking the Format dropdown and selecting your choice from the available options. The most common format is MP4, but MKV is also common.

In the Save As field, Enter a name for the converted file, and set the location where you want to save the file.

In the top right corner, you can choose between normal and high profile. You can also choose a preset for encoding the DVD in the best format for certain devices such as iPods and Android tablets. You can choose to encode the entire DVD or a range of chapters. You can also optimize the output for putting the final video on the web.

The Dimensions tab isn't particularly useful unless you want to crop the video's dimensions.

The Video tab lets you choose the video encoder and determine the quality of the final output. The encoders available include:

- H.264
- H.265
- MPEG-4
- MPEG-2

You can also choose between a constant and a variable framerate. In most situations, you will want to choose a constant framerate rather than variable framerate.

Other settings include the ability to choose the quality, choose a profile, and choose a level. The defaults suffice in most cases. However, if you are converting cartoons and you use the H.264 encoder, you will notice that there is a Tune option called Animation and this is probably better than the default option.

The best way to get the most out of Handbrake is with trial and error. These settings will work well for most DVDs, but you can try different settings to see what works for you.

A DVD may be encoded in different languages. You can choose the languages you wish to use on the Audio Defaults tab. Select individual languages by clicking the add or remove buttons.

By default, the AAC encoder is selected for ripping the audio from the DVD. It is worth adding a second encoder for MP3 in case the machine playing the ripped file isn't capable of playing AAC encoded files. 

The Subtitles tab lets you select the languages to use for subtitles. It works in the same way as the ​Audio tab. If you don't want subtitles, choose None as the selection behavior.

The Chapters tab has a list of all the DVD's chapters. You can name each chapter to make it more memorable during playback.

The Tags tab lets you add information about the video, such as the title, the actors, the director, release date, a comment, genre, description, and details about the plot.

When you have finished adjusting the settings for your video, you can start the ripping process. Click the Start button at the top of the screen. The process can take a while depending on the length of the DVD you are encoding.
