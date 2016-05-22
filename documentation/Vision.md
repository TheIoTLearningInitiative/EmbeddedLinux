# Vision

## Neural Networks

## Google Cloud Vision API

> Derive insight from images with our powerful Cloud Vision API. Image analysis with pretrained models. [Homepage](https://cloud.google.com/vision/)

> Integrates Google Vision features, including image labeling, face, logo, and landmark detection, optical character recognition (OCR), and detection of explicit content, into applications.

> How it works? You’ll get $300 credit to use for up to 60 days. You won’t be charged until you upgrade your account, and you can cancel at any time.

- [Tutorial](https://cloud.google.com/vision/docs/tutorials)
- [Github Sample code for Google Cloud Vision](https://github.com/GoogleCloudPlatform/cloud-vision/)


### Google Cloud Platform Dashboard

- Go to [Cloud Vision API](https://cloud.google.com/vision/)
  - Try it for Free

> Google Cloud Platform
> > Thanks for signing up for the 60-day free trial. We have given your $300 in free trial credit to spend. If you run out of credit, do not worry, you will not be billed until you give permission.

- New Project
  - Project Name: The IoT Learning Initiative

> You've set up a Cloud Vision API project in the Google Cloud Platform Console.

- Search
  - Vision -> Enable

> You've set up your environment for using Application Default Credentials.

- [Authenticating to a Cloud API Service](https://cloud.google.com/vision/docs/auth-template/cloud-api-auth#set_up_an_api_key)

- Go to [Google APIs](https://console.developers.google.com/projectselector/apis/credentials)
  - Select or create a project: The IoT Learning Initiative
  - Continue


```sh
root@edison:~# mkdir vision
root@edison:~# cd vision
ion.gitison:~/vision# git clone https://github.com/GoogleCloudPlatform/cloud-vision.git
Cloning into 'cloud-vision'...
remote: Counting objects: 1237, done.
remote: Total 1237 (delta 0), reused 0 (delta 0), pack-reused 1237
Receiving objects: 100% (1237/1237), 3.92 MiB | 322.00 KiB/s, done.
Resolving deltas: 100% (451/451), done.
Checking connectivity... done.
root@edison:~/vision# ls cloud-vision
root@edison:~/vision# ls cloud-vision/
CONTRIBUTING.md  android                 data  java    php
LICENSE          chrome-extension        go    js      python 
README.md        client-secret.json.enc  ios   nodejs  travis.sh
root@edison:~/vision# cd cloud-vision/python/face_detection/
root@edison:~/vision/cloud-vision/python/face_detection# 
```

```sh
root@edison:~/vision/cloud-vision/python/face_detection# opkg install libjpeg-dev
```

```sh
root@edison:~/vision/cloud-vision/python/face_detection# pip install -r requirements.txt --target /home/root
Downloading/unpacking google-api-python-client==1.5.0 (from -r requirements.txt (line 1))
Downloading/unpacking Pillow==3.1.1 (from -r requirements.txt (line 2))
...
Installing collected packages: google-api-python-client Pillow, httplib2, oauth2client, uritemplate, pyasn1, pyasn1-modules, rsn
...
root@edison:~/vision/cloud-vision/python/face_detection# pip install six
```

```sh
root@edison:~# git clone https://github.com/google/google-api-python-client.git
Cloning into 'google-api-python-client'...
remote: Counting objects: 13396, done.
remote: Compressing objects: 100% (405/405), done.
remote: Total 13396 (delta 196), reused 0 (delta 0), pack-reused 12991
Receiving objects: 100% (13396/13396), 23.18 MiB | 2.05 MiB/s, done.
Resolving deltas: 100% (10115/10115), done.
Checking connectivity... done.
Checking out files: 100% (1495/1495), done.
root@edison:~# cd google-api-python-client/
root@edison:~/google-api-python-client# python setup.py install --user
```
