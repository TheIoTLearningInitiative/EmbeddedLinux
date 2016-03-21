Conda
==
> Conda is a package manager application that quickly installs, runs, and updates packages and their dependencies. [Intro to Conda](http://conda.pydata.org/docs/intro.html)

> Anaconda is a free, easy-to-install package manager, environment manager, Python distribution, and collection of over 720 open source packages with free community support. Hundreds more open source packages and their dependencies can be installed with a simple “conda install [packagename]”. It’s platform-agnostic, can be used on Windows, OS X and Linux. [New to Anaconda Start Here](https://docs.continuum.io/new-anaconda-start-here)

- [Conda Download](https://www.continuum.io/downloads)
- [Conda Test Drive](http://conda.pydata.org/docs/test-drive.html)

```sh
    root@edison:~# opkg install python-pip
    root@edison:~# wget http://09c8d0b2229f813c1b93-c95ac804525aac4b6dba79b00b39d1d3.r79.cf1.rackcdn.com/Anaconda-2.1.0-Linux-x86.sh
    root@edison:~# opkg install http://repo.opkg.net/edison/repo/core2-32/bash_4.3-r0_core2-32.ipk
    root@edison:~# opkg install http://repo.opkg.net/edison/repo/core2-32/tar_1.27.1-r0_core2-32.ipk
    root@edison:~# bash ./Anaconda-2.1.0-Linux-x86.sh
    tar: lib/python2.7/site-packages/sklearn/utils/weight_vector.so: Cannot write: No space left on device
    tar: Exiting with failure status due to previous errors
```

## Miniconda

> These Miniconda installers contain the conda package manager and Python. Once Miniconda is installed, you can use the conda command to install any other packages and create environments, etc. 

- [Miniconda Python on Intel Edison](https://scivision.co/miniconda-python-on-intel-edison/)
- [The most important stuff to know about Intel Edison](http://tiredhacker.blogspot.mx/2015/01/the-most-important-stuff-to-know-about.html)

```sh
    root@edison:~# wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86.sh
    --2016-03-21 06:23:29--  https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86.sh
    Resolving repo.continuum.io... 23.21.234.195, 54.197.250.243, 23.23.254.16, ...
    Connecting to repo.continuum.io|23.21.234.195|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 29686993 (28M) [application/octet-stream]
    Saving to: 'Miniconda3-latest-Linux-x86.sh'
    
    100%[============================================================================================>] 29,686,993  1.20MB/s   in 25s
    
    2016-03-21 06:23:55 (1.13 MB/s) - 'Miniconda3-latest-Linux-x86.sh' saved [29686993/29686993]
    root@edison:~# bash Miniconda3-latest-Linux-x86.sh
    ...
    [/home/root/miniconda3] >>>
    PREFIX=/home/root/miniconda3
    installing: _cache-0.0-py35_x0 ...
    ...
    You may wish to edit your .bashrc or prepend the Miniconda3 install location:
    
    $ export PATH=/home/root/miniconda3/bin:$PATH
    
    Thank you for installing Miniconda3!
    
    Share your notebooks and packages on Anaconda Cloud!
    Sign up for free: https://anaconda.org
    

```