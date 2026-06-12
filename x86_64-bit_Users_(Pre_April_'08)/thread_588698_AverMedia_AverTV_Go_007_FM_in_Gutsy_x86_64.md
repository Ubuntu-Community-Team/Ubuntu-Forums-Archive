---
title: "AverMedia AverTV Go 007 FM in Gutsy x86_64"
date: 2007-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by databoy2k on 2007-10-23
Hey All:
This card worked great in Feisty, but it's not working at all anymore in Gutsy. I truly cannot figure out why it's not working, and unfortunately I'm too green to even know where to begin requesting help!
I've searched all of the other threads, there's no answers for this particular card and I suspect I've messed up the configuration file with incorrect modprobes and rmmod's. 
Can anyone point me in the right direction? Thanks a ton!
--Databoy2k

---

### Post by gywst on 2007-10-24
I am a Linux novice, but I manged to hear sound with my AverMedia AverTV Go 007 FM PCI card.

I installed [tvtime]("http://packages.ubuntu.com/gutsy/x11/tvtime") and [sox]("http://packages.ubuntu.com/gutsy/sound/sox") 

```
sudo apt-get install tvtime
```
```
sudo apt-get install sox
```

I used this [script]("http://ubuntuforums.org/showthread.php?t=172085") :
```

#!/bin/sh
sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -w -r 32000 /dev/dsp &
tvtime --mixer=/dev/mixer:pcm
wait tvtime
t=`pidof sox`;
kill $t;
amixer -c 0 sset PCM 80%,80%  unmute

```

Good Luck :)

---

### Post by chimerazz on 2007-11-12
Hey Gywst can you please tell me how to setup my AverTV Go 007 Fm with audio in gutsy
with all the steps to configure it 
please 
I am new to Linux

---

### Post by darthchaosofrspw on 2007-12-23
> **chimerazz said:**
> Hey Gywst can you please tell me how to setup my AverTV Go 007 Fm with audio in gutsy
with all the steps to configure it 
please 
I am new to Linux

To load up the TV tuner card, you will have to execute the following commands :

```

sudo modprobe saa7134

```

and

```

sudo modprobe saa7134-alsa

```

And then you can proceed with the other steps.

---

### Post by gywst on 2008-03-18
```
$ sudo apt-get install sox tvtime xmltv-util 
```

I used this script :

```
#!/bin/sh
sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -w -r 32000 /dev/dsp &
tvtime --mixer=/dev/mixer:pcm
wait tvtime
t=`pidof sox`;
kill $t;
amixer -c 0 sset PCM 80%,80%  unmute
```

---

### Post by extremetr on 2008-04-15
can anyone help me.I can't watch tv.I'm new at linux

lspci

[PHP]00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0a.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)[/PHP]

---

### Post by gywst on 2008-05-29
in **Hardy Ubuntu 8.04** try *libsox-fmt-all*


```
$ sudo apt-get install sox libsox-fmt-all tvtime xmltv-util 
```
use this script :

```
#!/bin/sh
sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -w -r 32000 /dev/dsp &
tvtime --mixer=/dev/mixer:pcm
wait tvtime
t=`pidof sox`;
kill $t;
amixer -c 0 sset PCM 80%,80%  unmute
```

---

