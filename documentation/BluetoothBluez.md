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
cd bluez
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
