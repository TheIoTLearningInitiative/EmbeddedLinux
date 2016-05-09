# Manual

## Pywapi

> Pywapi is a Python wrapper around different weather APIs

[Pywapi Pip Homepage](https://pypi.python.org/pypi/pywapi)

```sh
    root@edison:~# wget https://launchpad.net/python-weather-api/trunk/0.3.8/+download/pywapi-0.3.8.tar.gz
    --2016-03-19 18:51:24--  https://launchpad.net/python-weather-api/trunk/0.3.8/+download/pywapi-0.3.8.tar.gz
    Resolving launchpad.net... 91.189.89.223, 91.189.89.222
    Connecting to launchpad.net|91.189.89.223|:443... connected.
    HTTP request sent, awaiting response... 302 Moved Temporarily
    Location: https://launchpadlibrarian.net/166317636/pywapi-0.3.8.tar.gz [following]
    --2016-03-19 18:51:26--  https://launchpadlibrarian.net/166317636/pywapi-0.3.8.tar.gz
    Resolving launchpadlibrarian.net... 91.189.89.228, 91.189.89.229
    Connecting to launchpadlibrarian.net|91.189.89.228|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 25166 (25K) [application/x-tar]
    Saving to: 'pywapi-0.3.8.tar.gz.1'
    
    100%[======================================>] 25,166       139KB/s   in 0.2s   
    
    2016-03-19 18:51:27 (139 KB/s) - 'pywapi-0.3.8.tar.gz.1' saved [25166/25166]
    root@edison:~# tar zxvf pywapi-0.3.8.tar.gz
    pywapi-0.3.8/examples/pywapi-countries-example.py
    pywapi-0.3.8/setup.py
    pywapi-0.3.8/MANIFEST
    pywapi-0.3.8/examples/
    pywapi-0.3.8/examples/pywapi-noaa-example.py
    pywapi-0.3.8/examples/pywapi-example.py
    pywapi-0.3.8/pywapi.pyc
    pywapi-0.3.8/LICENSE
    pywapi-0.3.8/examples/pywapi-weather-com-example.py
    pywapi-0.3.8/pywapi.py
    pywapi-0.3.8/examples/pywapi-cities-example.py
    pywapi-0.3.8/CHANGELOG
    pywapi-0.3.8/README
    pywapi-0.3.8/
    pywapi-0.3.8/examples/pywapi-yahoo-example.py
    pywapi-0.3.8/examples/get-weather.py
    root@edison:~# cd pywapi-0.3.8
    root@edison:~/pywapi-0.3.8# ls
    CHANGELOG   MANIFEST    examples    pywapi.pyc
    LICENSE     README      pywapi.py   setup.py
    root@edison:~/pywapi-0.3.8# python setup.py build
    running build
    running build_py
    creating build
    creating build/lib
    copying pywapi.py -> build/lib
    root@edison:~/pywapi-0.3.8# python setup.py install
    running install
    running build
    running build_py
    running install_lib
    copying build/lib/pywapi.py -> /usr/lib/python2.7/site-packages
    byte-compiling /usr/lib/python2.7/site-packages/pywapi.py to pywapi.pyc
    running install_egg_info
    Writing /usr/lib/python2.7/site-packages/pywapi-0.3.8-py2.7.egg-info
    root@edison:~/pywapi-0.3.8# cd
    root@edison:~# 
```
