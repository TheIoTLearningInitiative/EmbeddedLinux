# Virtual Network Computing

> In computing, Virtual Network Computing (VNC) is a graphical desktop sharing system that uses the Remote Frame Buffer protocol (RFB) to remotely control another computer. It transmits the keyboard and mouse events from one computer to another, relaying the graphical screen updates back in the other direction, over a network. Wikipedia

## VNC Server @ Edison X Desktop @ Ubilinux

    root@edison:~# apt-get install xfce4
    root@edison:~# apt-get install vnc4server
    root@edison:~# vnc4passwd 
    Password:
    Verify:
    root@edison:~# vnc4server -geometry 800x600 -depth 24
    xauth:  file /home/chip/.Xauthority does not exist
    xauth: (stdin):1:  bad display name "chip:1" in "add" command
    
    New 'edison:1 (edison)' desktop is edison:1
    
    Creating default startup script /home/root/.vnc/xstartup
    Starting applications specified in /home/root/.vnc/xstartup
    Log file is /home/root/.vnc/edison:1.log

## VNC Server @ Edison Default Desktop

```sh
    root@edison:~# vnc4server -kill :1
    Killing Xvnc4 process ID 18807
    root@edison:~# nano ~/.vnc/xstartup                         
    #!/bin/sh
    # Uncomment the following two lines for normal desktop:
    unset SESSION_MANAGER 
    #exec /etc/X11/xinit/xinitrc 
    startxfce4 &
    ...
    root@edison:~# vnc4server -geometry 800x600 -depth 24
    xauth: (stdin):1:  bad display name "edison:1" in "add" command
    
    New 'edison:1 (edison)' desktop is edison:1
    
    Starting applications specified in /home/root/.vnc/xstartup
    Log file is /home/root/.vnc/edison:1.log
```

## VNC Viewer @ Host
    
    root@jessie:/home/xe1gyq# apt-get install xvnc4viewer
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    xvnc4viewer is already the newest version.
    0 upgraded, 0 newly installed, 0 to remove and 109 not upgraded.
    root@jessie:/home/xe1gyq# exit
    exit
    xe1gyq@jessie:~$ xvnc4viewer 192.168.1.77:1