# Python Package Index

> The Python Package Index or PyPI is the official third-party software repository for the Python programming language. Python developers intend it to be a comprehensive catalog of all open source Python packages. Wikipedia

> The Python Package Index is a repository of software for the Python programming language. Official Homepage

- [Python Package Index Homepage](https://pypi.python.org/pypi)
- [Python Package Index Wikipedia](https://en.wikipedia.org/wiki/Python_Package_Index)
- [Python Packaging User Guide](https://packaging.python.org/en/latest/current/)

```sh
    root@edison:~# opkg install python-pip python-dev
    root@edison:~# pip install setuptools
```

# Python Library

```sh
    root@edison:~# python
    Python 2.7.3 (default, Dec 19 2015, 23:06:02)
    [GCC 4.9.1] on linux2
    Type "help", "copyright", "credits" or "license" for more information.
    >>> import psutil
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    ImportError: No module named psutil
    >>> <CTRL-D>
```

# Python Library Search

```sh
    root@edison:~# pip search psutil
    ...
    psutil                    - psutil is a cross-platform library for retrieving
                                information onrunning processes and system
                                utilization (CPU, memory, disks, network)in
                                Python.
    ...
```

# Python Library Optional Installation Path

```sh
    root@edison:~# pip install psutil --target /root
    Downloading/unpacking psutil
      Running setup.py egg_info for package psutil
    
        warning: no previously-included files matching '*' found under directory 'docs/_build'
        warning: manifest_maker: MANIFEST.in, line 18: 'recursive-include' expects <dir> <pattern1> <pattern2> ...
        0
    Installing collected packages: psutil
      Running setup.py install for psutil
        
        warning: no previously-included files matching '*' found under directory 'docs/_build'
        warning: manifest_maker: MANIFEST.in, line 18: 'recursive-include' expects <dir> <pattern1> <pattern2> ...
    
    Successfully installed psutil
    Cleaning up...
    root@edison:~# ls /root/
    psutil                       psutil-3.3.0-py2.7.egg-info
    root@edison:~# ls /root/psutil
    __init__.py       _compat.pyc       _psosx.py         _pssunos.pyc
    __init__.pyc      _psbsd.py         _psosx.pyc        _psutil_linux.so
    _common.py        _psbsd.pyc        _psposix.py       _psutil_posix.so
    _common.pyc       _pslinux.py       _psposix.pyc      _pswindows.py
    _compat.py        _pslinux.pyc      _pssunos.py       _pswindows.pyc
    
    root@edison:~# export PYTHONPATH=$PYTHONPATH:/root
    root@edison:~# echo "export PYTHONPATH=$PYTHONPATH:/root" >> /etc/profile
    root@edison:~# python
    Python 2.7.3 (default, Dec 19 2015, 23:06:02) 
    [GCC 4.9.1] on linux2
    Type "help", "copyright", "credits" or "license" for more information.
    >>> import psutil
    >>> <CTRL-D>
    root@edison:~# pip uninstall psutil
```

# Python Library Default Installation Path

```sh
    root@edison:~# pip install psutil
    Downloading/unpacking psutil
      Running setup.py egg_info for package psutil
    
        warning: no previously-included files matching '*' found under directory 'docs/_build'
        warning: manifest_maker: MANIFEST.in, line 18: 'recursive-include' expects <dir> <pattern1> <pattern2> ...
        
    Installing collected packages: psutil
      Running setup.py install for psutil
        
        warning: no previously-included files matching '*' found under directory 'docs/_build'
        warning: manifest_maker: MANIFEST.in, line 18: 'recursive-include' expects <dir> <pattern1> <pattern2> ...
    
    Successfully installed psutil
    Cleaning up...
```

# Python Library Github Installation

```sh
    root@edison:~# pip install https://github.com/mitsuhiko/flask/tarball/master
```

# Python Easy_Install

```sh
root@edison:~# easy_install requests
Searching for requests
Reading https://pypi.python.org/simple/requests/
Best match: requests 2.10.0
Downloading https://pypi.python.org/packages/49/6f/183063f01aae1e025cf0130772b55848750a2f3a89bfa11b385b
35d7329d/requests-2.10.0.tar.gz#md5=a36f7a64600f1bfec4d55ae021d232ae
Processing requests-2.10.0.tar.gz
Writing /tmp/easy_install-E4KeMV/requests-2.10.0/setup.cfg
Running requests-2.10.0/setup.py -q bdist_egg --dist-dir /tmp/easy_install-E4KeMV/requests-2.10.0/egg-d
ist-tmp-qSTGq5
warning: no files found matching 'test_requests.py'
creating /usr/lib/python2.7/site-packages/requests-2.10.0-py2.7.egg
Extracting requests-2.10.0-py2.7.egg to /usr/lib/python2.7/site-packages
Adding requests 2.10.0 to easy-install.pth file

Installed /usr/lib/python2.7/site-packages/requests-2.10.0-py2.7.egg
Processing dependencies for requests
Finished processing dependencies for requests
root@edison:~# 
```