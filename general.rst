
WWW
===
[-inurl:(htm|html|php) intitle:"index of" +"last modified" + "parent directory" +description +size +(jpg|jpeg|png|gif) "some string"]

Screen
======

256 Colors
----------
Put following lines in ~/.bashrc::

    export TERM=xterm-256color

PC Marian
=========
In emergency mode::

    fsck /dev/dev-mapper-fedora/fedora-root
    
Usupported resolution of monitor
================================

In shell::

    cvt 2560 1440 40 (instead 60)
    xrandr --newmode "2560x1440_40.00" 201.00  2560 2720 2984 3408  1440 1443 1448 1476 -hsync +vsync
    xrandr --addmode HDMI-3 2560x1440_40.00
    xrandr --output HDMI-3 --mode 2560x1440_40.00
