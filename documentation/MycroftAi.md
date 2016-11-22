# MycroftAi

> A.I. for everyone. Connecting the Internet of things has never been easier. Mycroft has a lot of native skills and abilities baked in and, since it is open source, it allows outside developers to add more features over time. [Mycroft](https://mycroft.ai/)

- Always Learning
- Always Changing
- Always Listening
- For the Office: Increase Productivity!
- For the Maker: Encourage Creativity!
- For the Home: Integrated Artificial Intelligence!

- [Kickstarter Mycroft: An Open Source Artificial Intelligence For Everyone](https://www.kickstarter.com/projects/aiforeveryone/mycroft-an-open-source-artificial-intelligence-for)
- [Indiegogo Mycroft: Open Source Artificial Intelligence](https://www.indiegogo.com/projects/mycroft-open-source-artificial-intelligence#/)
- [Update #28 from Mycroft: An Open Source Artificial Intelligence For Everyone](https://www.kickstarter.com/projects/aiforeveryone/mycroft-an-open-source-artificial-intelligence-for/posts/1597302?ref=dash)
- [Mycroft Community](https://community.mycroft.ai/)
- [Gnome Shell GUI Extension for Mycroft Ai](https://github.com/AIIX)

## Components

### Adapt Intent Parser

> The Adapt Intent Parser is an open source software library for converting natural language into machine readable data structures. Adapt is lightweight and streamlined and is designed to run on devices with limited computing resources. Adapt takes in natural language and outputs a data structure that includes the intent, a match probability, a tagged list of entities.

#### Mycroft Core

> Mycroft is the technology that ties natural language processing, text-to-speech, speech-to-text, and powerful APIs together to create a powerful experience allowing users to manipulate their smart devices and the Internet of Things through voice control.

```sh
xe1gyq@jessie:~$ git clone https://github.com/MycroftAI/mycroft-core.git
Cloning into 'mycroft-core'...
remote: Counting objects: 1623, done.
remote: Compressing objects: 100% (155/155), done.
remote: Total 1623 (delta 64), reused 0 (delta 0), pack-reused 1452
Receiving objects: 100% (1623/1623), 9.45 MiB | 687.00 KiB/s, done.
Resolving deltas: 100% (751/751), done.
Checking connectivity... done.
xe1gyq@jessie:~$ cd mycroft-core/
xe1gyq@jessie:~/mycroft-core$ 
```

```sh
xe1gyq@jessie:~/mycroft-core$ ./build_host_setup.sh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
autoconf is already the newest version.
bison is already the newest version.
curl is already the newest version.
git is already the newest version.
libglib2.0-dev is already the newest version.
libffi-dev is already the newest version.
libtool is already the newest version.
mpg123 is already the newest version.
libssl-dev is already the newest version.
portaudio19-dev is already the newest version.
python-gobject-dev is already the newest version.
python is already the newest version.
python-dev is already the newest version.
python-setuptools is already the newest version.
python-virtualenv is already the newest version.
s3cmd is already the newest version.
swig is already the newest version.
virtualenvwrapper is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 168 not upgraded.
Searching for virtualenv
Reading https://pypi.python.org/simple/virtualenv/
Best match: virtualenv 15.0.2
Processing virtualenv-15.0.2-py2.7.egg
virtualenv 15.0.2 is already the active version in easy-install.pth
Installing virtualenv script to /usr/local/bin

Using /usr/local/lib/python2.7/dist-packages/virtualenv-15.0.2-py2.7.egg
Processing dependencies for virtualenv
Finished processing dependencies for virtualenv
xe1gyq@jessie:~/mycroft-core$ 
```

```sh
xe1gyq@jessie:~/mycroft-core$ ./dev_setup.sh
```

### Mimic Text to Speech

> Mimic is a fast, lightweight Text-to-speech engine developed by Mycroft A.I. and VocaliD, based on Carnegie Mellon University’s FLITE software. Mimic takes in text and reads it out loud to create a high quality voice. Mimic’s low-latency, small resource footprint, and good quality voices set it apart from other open source text-to-speech projects.

### Open Speech to Text

> OpenSTT is being led by members of the Mycroft A.I. team as they strive to create a powerful voice interface and artificial intelligence platform. Our goal is to make this technology available to as many people as possible. We do this by leading development of open source projects, OpenSTT is one of these initiatives.

###  Mycroft Core 0.6 Alpha

> We are pleased to announce that Mycroft Core 0.6 Alpha is available for download today. Mycroft Core is a lightweight, portable piece of software written in Python. You can run it on anything from a Raspberry Pi to a gaming rig. Mycroft Core includes Adapt, Mimic, OpenSTT, and multiple open APIs to create an experience that allows users to interact with their technology using the most natural form of human communication – speech. 

- [Mycroft Core, the Mycroft Artificial Intelligence Platform Github](https://github.com/MycroftAI/mycroft-core)
- [Mycroft Alpha v0.6 Software Demo](https://www.youtube.com/watch?v=-c8kfupIbO4&feature=youtu.be)

