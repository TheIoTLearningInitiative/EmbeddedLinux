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
Installing collected packages: google-api-python-client Pillow, httplib2, oauth2client, uritemplate, pyasn1, pyasn1-modules, rsa
...
```

```
root@edison:~/vision/cloud-vision/python/face_detection# scp xe1gyq@192.168.1.72:/home/xe1gyq/cred.json .
xe1gyq@192.168.1.72's password:
cred.json                                     100% 2355     2.3KB/s   00:00                       
root@edison:~/vision/cloud-vision/python/face_detection# export GOOGLE_APPLICATION_CREDENTIALS=<path_to_service_account_file>
```

```sh
root@edison:~/vision/cloud-vision/python/face_detection# python faces.py face-input.jpeg
```

```sh
root@edison:~/vision/cloud-vision/python/face_detection# wget https://upload.wikimedia.org/wikipedia/commons/5/5d/Barack_Obama_family_portrait_2011.jpg
    --2016-03-20 00:24:03--  https://upload.wikimedia.org/wikipedia/commons/5/5d/Barack_Obama_family_portrait_2011.jpg
    Resolving upload.wikimedia.org... 208.80.153.240, 2620:0:860:ed1a::2:b
    Connecting to upload.wikimedia.org|208.80.153.240|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 1972894 (1.9M) [image/jpeg]
    Saving to: 'Barack_Obama_family_portrait_2011.jpg'
    
    100%[======================================>] 1,972,894    264KB/s   in 16s
    
    2016-03-20 00:24:20 (122 KB/s) - 'Barack_Obama_family_portrait_2011.jpg' saved [1972894/1972894]
    
root@edison:~/vision/cloud-vision/python/face_detection# mv Barack_Obama_family_portrait_2011.jpg face-input.jpeg
root@edison:~/vision/cloud-vision/python/face_detection# time python faces.py face-input.jpeg
Found 4 faces
Writing to file out.jpg

real    0m56.898s
user    0m11.820s
sys     0m0.490s
root@edison:~/vision/cloud-vision/python/face_detection# 
```

### Errors

```sh
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
