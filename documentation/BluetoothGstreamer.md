# Gstreamer

- [Gstreamer Overview of available plug-ins](https://gstreamer.freedesktop.org/documentation/plugins.html)
- [](https://www.mankier.com/1/gst-launch-1.0)

# MP3

```sh
root@edison:~# wget https://dl.last.fm/static/1477806840/131211148/80e73bda617b3f102999b714b5515dc57d8c33986ea28b4a3a8395b62f15700c/Death+Grips+-+Get+Got.mp3
root@edison:~# mv Death+Grips+-+Get+Got.mp3 music.mp3
root@edison:~# gst-launch-1.0 filesrc location=music.mp3  ! mad ! pulsesink
WARNING: erroneous pipeline: no element "mad"
root@edison:~# gst-launch-1.0 filesrc location=music.mp3 ! mad ! audioconvert ! audioresample ! pulsesink
```

```sh
root@edison:~# opkg list | grep gstreamer | grep bad > bad
gstreamer1.0-plugins-bad
root@edison:~# opkg install gstreamer1.0-plugins-bad
root@edison:~# gst-inspect-1.0
```

# OGG

```sh
root@edison:~# wget http://opengameart.org/sites/default/files/GAME%20SOUND%20FX%20PACK%20WAV%20OGG%20M4A_0.zip
--2016-10-30 06:12:31--  http://opengameart.org/sites/default/files/GAME%20SOUND%20FX%20PACK%20WAV%20OGG%20M4A_0.zip
Resolving opengameart.org... 199.180.155.30
Connecting to opengameart.org|199.180.155.30|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5241100 (5.0M) [application/zip]
Saving to: 'GAME SOUND FX PACK WAV OGG M4A_0.zip'

100%[======================================>] 5,241,100   1.07MB/s   in 4.7s   

2016-10-30 06:12:36 (1.06 MB/s) - 'GAME SOUND FX PACK WAV OGG M4A_0.zip' saved [5241100/5241100]

root@edison:~# 
```

```sh
root@edison:~# unzip GAME\ SOUND\ FX\ PACK\ WAV\ OGG\ M4A_0.zip
  ...
  inflating: GAME SOUND FX PACK WAV OGG M4A/Randomize9.m4a
  inflating: GAME SOUND FX PACK WAV OGG M4A/Randomize9.ogg
  inflating: GAME SOUND FX PACK WAV OGG M4A/Randomize9.wav
root@edison:~# mv GAME\ SOUND\ FX\ PACK\ WAV\ OGG\ M4A sounds
root@edison:~# cd sounds/ 
root@edison:~/sounds# ls
...
Explosion3.m4a     Laser_Shoot17.ogg  Powerup12.wav      Randomize9.m4a
Explosion3.ogg     Laser_Shoot17.wav  Powerup13.m4a      Randomize9.ogg
Explosion3.wav     Laser_Shoot18.m4a  Powerup13.ogg      Randomize9.wav
Explosion4.m4a     Laser_Shoot18.ogg  Powerup13.wav
root@edison:~/sounds# gst-typefind-1.0 Randomize9.m4a
Randomize9.m4a - audio/x-m4a
root@edison:~/sounds# gst-typefind-1.0 Randomize9.ogg
Randomize9.ogg - audio/ogg
root@edison:~/sounds# gst-typefind-1.0 Randomize9.wav 
Randomize9.wav - audio/x-wav
root@edison:~/sounds# 
```

```sh
root@edison:~/sounds# opkg install gstreamer1.0-plugins-base-ogg
root@edison:~/sounds# opkg install gstreamer1.0-plugins-base-ogg-dev
```

```sh
root@edison:~/sounds# gst-inspect-1.0 | grep ogg 
typefindfunctions: application/x-id3v2: mp3, mp2, mp1, mpga, ogg, flac, tta
typefindfunctions: application/x-id3v1: mp3, mp2, mp1, mpga, ogg, flac, tta
typefindfunctions: application/ogg: ogg, oga, ogv, ogm, ogx, spx, anx, axa, axv
typefindfunctions: application/x-ogg-skeleton: no extensions
ogg:  oggdemux: Ogg demuxer
ogg:  oggmux: Ogg muxer
ogg:  ogmaudioparse: OGM audio stream parser
ogg:  ogmvideoparse: OGM video stream parser
ogg:  ogmtextparse: OGM text stream parser
ogg:  oggparse: Ogg parser
ogg:  oggaviparse: Ogg AVI parser
root@edison:~/sounds# 
```

```sh
root@edison:~/sounds# gst-launch-1.0 filesrc location=Randomize9.ogg ! oggdemux ! vorbisdec ! audioconvert ! audioresample ! pulsesink
```

[Arachnosoft](http://www.arachnosoft.com/main/music.php)

```sh
root@edison:~/sounds# wget http://maxime.abbey.free.fr/mirror/arachnosoft/files/music/current/green/green-20-ogg.zip
--2016-10-30 06:37:12--  http://maxime.abbey.free.fr/mirror/arachnosoft/files/music/current/green/green-20-ogg.zip
Resolving maxime.abbey.free.fr... 212.27.63.116
Connecting to maxime.abbey.free.fr|212.27.63.116|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 12960542 (12M) [application/zip]
Saving to: 'green-20-ogg.zip'

100%[======================================>] 12,960,542  1.08MB/s   in 16s    

2016-10-30 06:37:29 (803 KB/s) - 'green-20-ogg.zip' saved [12960542/12960542]

root@edison:~/sounds# 
```

```sh
root@edison:~/sounds# unzip green-20-ogg.zip 
Archive:  green-20-ogg.zip
  inflating: Maxime Abbey - Green Hills.ogg
  inflating: ReadMe.txt
  inflating: ReadMe - OGG Version.txt
root@edison:~/sounds# 
```

```sh
root@edison:~/sounds# mv Maxime\ Abbey\ -\ Green\ Hills.ogg music.ogg
root@edison:~/sounds# gst-launch-1.0 filesrc location=music.ogg ! oggdemux ! vorbisdec ! audioconvert ! audioresample ! pulsesink
```

# RTSP

```sh
```
