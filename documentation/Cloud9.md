Cloud9
==
> Your development environment, in the cloud. Cloud9 combines a powerful online code editor with a full Ubuntu workspace in the cloud. [c9.io](https://c9.io/blog/2015-a-year-of-living-learningly/)

> This is your Workspace. We maintain it, you control it

> Fast. Scalable. Easily handle hundreds of thousands of files in your workspace and hundreds of thousands of lines of code in the editor

> Wind River saw the potential of Cloud9 and built Cloud9 into their Helix Device Cloud to create a next generation development platform for their embedded developer community. 

[Cloud9 Homepage](https://c9.io/)

```sh
    root@edison:~# npm version -g
    { http_parser: '1.0',
      node: '0.10.38',
      v8: '3.14.5.9',
      ares: '1.9.0-DEV',
      uv: '0.10.36',
      zlib: '1.2.8',
      modules: '11',
      openssl: '1.0.1m',          
      npm: '1.4.28' }
    root@edison:~# git clone https://github.com/c9/core.git c9sdk
    Cloning into 'c9sdk'...
    remote: Counting objects: 26633, done.
    remote: Compressing objects: 100% (636/636), done.
    remote: Total 26633 (delta 406), reused 0 (delta 0), pack-reused 25996
    Receiving objects: 100% (26633/26633), 16.41 MiB | 1.03 MiB/s, done.
    Resolving deltas: 100% (17324/17324), done.     
    Checking connectivity... done.
    Checking out files: 100% (3010/3010), done.                    
    root@edison:~# cd c9sdk
    root@edison:~/c9sdk# ls
    LICENSE       build         local         plugins       settings
    README.md     configs       node_modules  scripts       test
    bin           docs          package.json  server.js
    root@edison:~/c9sdk# ./scripts/install-sdk.sh
    ...
    checking for LIBEVENT... yes
    checking for library containing setupterm... no
    configure: error: "curses not found"
    ...
```

```sh
    root@edison:~# git clone https://github.com/navin-bhaskar/Cloud9-on-Intel-Edison.git c9
    root@edison:~# cd c9
    root@edison:~# sh Setup_Cloud9_On_Edison.sh install
    <Install a Ps specific version>
    root@edison:~# sh Setup_Cloud9_On_Edison.sh
```