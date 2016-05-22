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
root@edison:~/vision# 
```