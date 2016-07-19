# Script

```sh
    user@host:~$ tar xvf edison-src-ww25.5-15.tgz
    user@host:~$ cd edison-src
    user@host:~$ pwd
    /home/xe1gyq/Projects/edison-src
    user@host:~$ ls
    Makefile  meta-intel-edison
    user@host:~$ mkdir bitbake_download_dir
    user@host:~$ mkdir bitbake_sstate_dir
    user@host:~$ ./meta-intel-edison/setup.sh --dl_dir=bitbake_download_dir --sstate_dir=bitbake_sstate_dir
```

```
    user@host:~$ source poky/oe-init-build-env
```

# Fix Paho-Mqtt

```sh
    user@host:~$ wget http://git.yoctoproject.org/cgit/cgit.cgi/meta-intel-iot-middleware/plain/recipes-connectivity/paho-mqtt/paho-mqtt_3.1.bb
    user@host:~$ mv paho-mqtt_3.1.bb file/to/paho-mqtt_3.1.bb
```

```
    user@host:~$ bitbake edison-image
    user@host:~$ ../meta-intel-edison/utils/flash/postBuild.sh .
    user@host:~$ build/toFlash/flashall.sh
    user@host:~$ build/toFlash/flashall.sh --keep-data
    user@host:~$ build/toFlash/flashall.sh --recovery
```
