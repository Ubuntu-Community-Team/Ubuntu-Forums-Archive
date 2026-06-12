---
title: "audio device connection refused"
date: 2009-04-18
forum: x86 64-bit Users
---

### Post by Richard-g8jvm on 2009-04-18
I have pulseaudio disabled as I have multiple sound cards.
I'm using an application which is dependent on portaudio, mainly running python scripts.Easiest to show the example of whats happening:-

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)

Audio     Input    Output     Device Name
Device  Channels  Channels
------------------------------------------------------------------
   0       12        10       M Audio Delta 66: ICE1712 multi (hw:0,0)
   1        2         8       PnP Audio Device        : USB Audio (hw:1,0)
   2        0        10       front
   3        0        10       surround40
   4        0        10       surround51
   5        0        128       iec958
   6       128        128       spdif
   7       128        128       default
   8        0        10       dmix
   9       16        16       /dev/dsp
  10       16         2       /dev/dsp1

User requested devices:   Input = 0   Output = 0
Default devices:          Input = 7   Output = 7
Will open devices:        Input = 7   Output = 7
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)



Other audio apps run OK, I've run the app as root and the same happens.
Anyone any idea as to why  the ALSA backend would refusing connection

TIA

Richard

---

### Post by Yellow Pasque on 2009-04-19
It appears that the ALSA backend only works in portaudio19. Try installing portaudio19-dev, libportaudiocpp0, and libportaudio2.

---

### Post by Richard-g8jvm on 2009-04-19
Thanks for the hint, I did compile the application with the portaudio-v19
libs and headers.
What is strange is that after saying its refused in connects.
What really is a pain is when the app is closed it seg faults and core dumps.
I haven't found where its dumping the core each time.
I'm suspecting this behavior is caused by file permissions.
The app is run as root and I've made sure that the app is in the same group
as root and me.
I've run the app with strace and make python verbose, but I'm not catching
where its going wrong.

Richard

---

