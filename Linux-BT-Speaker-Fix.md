Linux Bluetooth Speaker Configuration
=====================================

Use these steps to fix the following problems.
- Speaker unable to play sound.
- Computer unable to connect to speaker.
- Speaker appears as a mono device resulting in poor audio quality.

Tested on Linux Mint with an Anker SoundCore, Model: A3102.

1. In the file `/etc/pulse/default.pa` comment out the following line so it now reads:

`#load-module module-bluetooth-discover`

2. At the bottom of the file `/usr/bin/start-pulseaudio-x11` add the following line in between the last two `fi`:

`/usr/bin/pactl load-module module-bluetooth-discover`

3. Add the following line to the bottom of `/etc/pulse/system.pa`:

```
### Automatically redirect to newly available sinks
load-module module-switch-on-connect
```

You may need to open the sound preferences go to the hardware tab and change the profile to (A2DP Sink). You'll also need to go on the output tab and change your output device to the speaker.

If the speaker pairs but won't connect try the following commands:

```
sudo apt-get install pulseaudio-module-bluetooth
pactl load-module module-bluetooth-discover
```
