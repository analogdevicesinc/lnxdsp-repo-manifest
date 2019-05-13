# MPlayer Testing
-----------------------------------

May need to add the following to build/conf/local.conf

```
#Add this to allow mpv (mplayer port) to build
LICENSE_FLAGS_WHITELIST="commercial"
```

We have incorporated MPV in the build instead of Mplayer, as Yocto has default recipes for MPV.  If this ends up being an issue, a separate mplayer recipe can be written.

As we do not have an LCD to test with, this is currently testing that MPV has been installed:
```
root@adsp-sc589-ezkit:~# mpv --version
mpv 0.26.0 (C) 2000-2017 mpv/MPlayer/mplayer2 projects
 built on Mon May 13 17:17:25 UTC 2019
ffmpeg library versions:
   libavutil       56.14.100
   libavcodec      58.18.100
   libavformat     58.12.100
   libswscale      5.1.100
   libavfilter     7.16.100
   libswresample   3.1.100
ffmpeg version: 4.0.2
```

