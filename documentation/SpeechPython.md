# Python SpeechRecognition


```sh
root@edison:~# pip install SpeechRecognition
Downloading/unpacking SpeechRecognition
...
root@edison:~# python
```

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
root@edison:~# opkg install libjack                                           root@edison:~# opkg install --nodeps jack-dev                                 root@edison:~# opkg install libportaudio-dev
root@edison:~# opkg install flac-dev
```

## Google

```python
import speech_recognition as sr
from os import path

AUDIO_FILE = path.join(path.dirname(path.realpath(__file__)), "hello.wav")

r = sr.Recognizer()
with sr.AudioFile(AUDIO_FILE) as source:
    audio = r.record(source) # read the entire audio file

print("Google Speech Recognition thinks you said " + r.recognize_google(audio, key=""))

WIT_AI_KEY = ""
print("Wit.ai thinks you said " + r.recognize_wit(audio, key=WIT_AI_KEY))
```

## Wit

```python
import speech_recognition as sr
import pyaudio
import wit


r = sr.Recognizer()
with sr.Microphone() as source:
    r.adjust_for_ambient_noise(source) # listen for 1 second to calibrate the energy threshold for ambient noise levels
    print("Say something!")
    audio = r.listen(source)

    

    WIT_AI_KEY = "32-character uppercase alphanumeric strings"
try:
    print("Wit.ai thinks you said " + r.recognize_wit(audio, key=WIT_AI_KEY))
except sr.UnknownValueError:
    print("Wit.ai could not understand audio")
except sr.RequestError:
    print("Could not request results from Wit.ai service")
```

## Wave

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