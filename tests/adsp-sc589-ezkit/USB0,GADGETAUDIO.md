# USB0: Gadget Audio
-----------------------------------

Probe g_audio driver
```
root@adsp-sc589-ezkit:~# modprobe g_audio
g_audio gadget: Linux USB Audio Gadget, version: Feb 2, 2012
g_audio gadget: g_audio ready
g_audio gadget: high-speed config #1: Linux USB Audio Gadget
```

Make sure gadget driver is found on host machine
```
nathan@Debian-BuildMachine:$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Gadget [Linux USB Audio Gadget], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Run speaker-test
```
nathan@Debian-BuildMachine:/mnt/HDD/Projects/AnalogDevices$ speaker-test -D hw:2,0 -c 2

speaker-test 1.1.3

Playback device is hw:2,0
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 96 to 262144
Period size range from 48 to 131072
Using max buffer size 262144
Periods = 4
was set period_size = 65536
was set buffer_size = 262144
 0 - Front Left
 1 - Front Right
```