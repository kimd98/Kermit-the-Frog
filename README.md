# Kermit-the-Frog

## Microphone & Speaker Setup
Speaker: `aplay -l`

Microphone: `arecord -l`

Create a file /home/pi/.asoundrc and add the following lines:
```
pcm.!default {
  type asym
  capture.pcm "mic"
  playback.pcm "speaker"
}
pcm.mic {
  type plug
  slave {
    pcm "hw:<card number>,<device number>"
    rate 48000
  }
}
pcm.speaker {
  type plug
  slave {
    pcm "hw:<card number>,<device number>"
  }
}
```

To test recording: `arecord --device=hw:1,0 --format S16_LE --rate 44100 -c1 test.wav`

To test speakers: `aplay --device=plughw:3,0 test.wav`


## Google Assistant Setup

Check out the website (https://pimylifeup.com/raspberry-pi-google-assistant/) for detailed instructions.
