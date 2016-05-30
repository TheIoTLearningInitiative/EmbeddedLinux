# Speech

- [Alexa AWS Raspberry Pi](https://github.com/amzn/alexa-avs-raspberry-pi)
- [How to get Edison to speak](https://software.intel.com/en-us/blogs/2016/02/18/how-to-get-edison-to-espeak-with-a-scottish-accent)
- [Gewtting Started with Intel Edison](https://books.google.com.mx/books?id=MMXeCgAAQBAJ&pg=PT154&lpg=PT154&dq=sr.Microphone+speech+recognition&source=bl&ots=MSWuFftGhI&sig=rvJleYKb7yYYDNlTiKgDXGUORT4&hl=en&sa=X&ved=0ahUKEwiVoKKyxIDNAhUn4YMKHTnEBO0Q6AEIUjAI#v=onepage&q=sr.Microphone%20speech%20recognition&f=false)
- [PyAudio](http://www.programcreek.com/python/example/52624/pyaudio.PyAudio)
- [SR Lists](http://raspberrypi.stackexchange.com/questions/10384/speech-processing-on-the-raspberry-pi/10392)

## eSpeak

> eSpeak is a compact open source software speech synthesizer for English and other languages, for Linux and Windows [Homepage](http://espeak.sourceforge.net)

## VoiceRss

> The Voice RSS Text-to-Speech (TTS) API allows conversion of textual content to speech easier than ever. Just connect to our Text-to-Speech (TTS) API with a few lines of code and get verbal representation of a textual content. For converting text to speech you don’t need special hardware to care about intensive use of CPU and memory during conversion operations. [Homepage](http://www.voicerss.org/)

## OpenSST

> An Open Source Speech To Text Project

> The OpenSTT project is aimed at creating an open source speech-to-text model that can be used by individuals and company to allow for high accuracy, low-latency conversion of speech into text. OpenSST

- [Mycroft Adapt](https://adapt.mycroft.ai/)
- [Mycroft Mimic](https://mimic.mycroft.ai/)

## Google Cloud Speech API Alpha
 
> Speech to text conversion powered by machine learning [Homepage](https://cloud.google.com/speech/)
 
- Android Speech API
- Web Speech aPI
- Cloud Speech API
  - REST API
  - gRPC API


### gRPC

> A high performance, open source, general RPC framework that puts mobile and HTTP/2 first. [Homepage](http://www.grpc.io/)

### Pyttsx

> Text-to-Speech X-Platform [Homepage](http://pyttsx.readthedocs.io/en/latest/index.html)

### Jasper

> Control anything with your voice [Homepage](http://jasperproject.github.io/)

- [Jasper Hackaday](http://hackaday.com/2014/04/09/create-your-own-j-a-r-v-i-s-using-jasper/)
- [Jasper Github](https://github.com/jasperproject)

## Lab

```python
>>> import speech_recognition as sr
>>> list = sr.Microphone.list_microphone_names()
>>> for element in list:
...     print element
... 
Loopback: Loopback PCM (hw:0,0)
Loopback: Loopback PCM (hw:0,1)
dummy-audio:  (hw:1,0)
USB PnP Sound Device: USB Audio (hw:3,0)
sysdefault
front
surround21
surround40
surround41
surround50
surround51
surround71
dmix
default
>>> 
```

```sh
opkg install libjack
opkg install --nodeps jack-dev
opkg install libportaudio-dev
opkg install flac-dev
```

```sh
import speech_recognition as sr
from os import path
AUDIO_FILE = path.join(path.dirname(path.realpath(__file__)), "hello.wav")
r = sr.Recognizer()
with sr.AudioFile(AUDIO_FILE) as source:
    audio = r.record(source) # read the entire audio file
print("Google Speech Recognition thinks you said " + r.recognize_google(audio, key="")
WIT_AI_KEY = ""
print("Wit.ai thinks you said " + r.recognize_wit(audio, key=WIT_AI_KEY))
```

```python
import audioop
import pyaudio
import wave
 
FORMAT = pyaudio.paInt16
CHANNELS = 2
RATE = 44100
CHUNK = 1024
RECORD_SECONDS = 5
WAVE_OUTPUT_FILENAME = "file.wav"
 
audio = pyaudio.PyAudio()
 
# start Recording
stream = audio.open(format=FORMAT, channels=CHANNELS,
                rate=RATE, input=True,
                frames_per_buffer=CHUNK)
print "recording..."
frames = []

threshold = 1000
for i in range(0, int(RATE / CHUNK * RECORD_SECONDS)):
    data = stream.read(CHUNK)
    rms = audioop.rms(data,2)
    if rms > threshold:
        print "I am hearing you now"
    frames.append(data)
print "finished recording"
 
 
# stop Recording
stream.stop_stream()
stream.close()
audio.terminate()
 
waveFile = wave.open(WAVE_OUTPUT_FILENAME, 'wb')
waveFile.setnchannels(CHANNELS)
waveFile.setsampwidth(audio.get_sample_size(FORMAT))
waveFile.setframerate(RATE)
waveFile.writeframes(b''.join(frames))
waveFile.close()
```