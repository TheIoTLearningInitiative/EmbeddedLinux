# Gstreamer

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