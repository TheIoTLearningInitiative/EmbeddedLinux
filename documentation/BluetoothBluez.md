# Bluez

```sh
root@edison:~# git clone https://github.com/Arkq/bluez-alsa.git
Cloning into 'bluez-alsa'...
remote: Counting objects: 713, done.
remote: Compressing objects: 100% (129/129), done.
remote: Total 713 (delta 90), reused 0 (delta 0), pack-reused 584
Receiving objects: 100% (713/713), 244.45 KiB | 177.00 KiB/s, done.
Resolving deltas: 100% (524/524), done.
Checking connectivity... done.
root@edison:~/bluez-alsa# 
```

```sh
root@edison:~# cd bluez-alsa/
root@edison:~/bluez-alsa# autoreconf --install
aclocal: warning: couldn't open directory 'm4': No such file or directory
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: copying file `m4/libtool.m4'
libtoolize: copying file `m4/ltoptions.m4'
libtoolize: copying file `m4/ltsugar.m4'
libtoolize: copying file `m4/ltversion.m4'
libtoolize: copying file `m4/lt~obsolete.m4'
configure.ac:12: installing './ar-lib'
configure.ac:10: installing './compile'
configure.ac:14: installing './config.guess'
configure.ac:14: installing './config.sub'
configure.ac:5: installing './install-sh'
configure.ac:5: installing './missing'
src/Makefile.am: installing './depcomp'
parallel-tests: installing './test-driver'
root@edison:~/bluez-alsa# 
```

```sh
root@edison:~/bluez-alsa# mkdir build && cd build
root@edison:~/bluez-alsa# mkdir build && cd build
```

```sh
linphone/ortp/sources/ortp-0.9.1.tar.gztps://download.savannah.gnu.org/releases/ 
--2016-10-30 05:16:21--  https://download.savannah.gnu.org/releases/linphone/ortp/sources/ortp-0.9.1.tar.gz
Resolving download.savannah.gnu.org... 208.118.235.73
Connecting to download.savannah.gnu.org|208.118.235.73|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://download.savannah.gnu.org/releases-redirect/linphone/ortp/sources/ortp-0.9.1.tar.gz [following]
--2016-10-30 05:16:23--  https://download.savannah.gnu.org/releases-redirect/linphone/ortp/sources/ortp-0.9.1.tar.gz
Reusing existing connection to download.savannah.gnu.org:443.
HTTP request sent, awaiting response... 302 Found
Location: http://nongnu.askapache.com//linphone/ortp/sources/ortp-0.9.1.tar.gz [following]
--2016-10-30 05:16:24--  http://nongnu.askapache.com//linphone/ortp/sources/ortp-0.9.1.tar.gz
Resolving nongnu.askapache.com... 192.185.42.228
Connecting to nongnu.askapache.com|192.185.42.228|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 445857 (435K) [application/x-gzip]
Saving to: 'ortp-0.9.1.tar.gz'

100%[======================================>] 445,857     41.9KB/s   in 9.6s   

2016-10-30 05:16:35 (45.5 KB/s) - 'ortp-0.9.1.tar.gz' saved [445857/445857]

root@edison:~/bluez-alsa/build# 
```