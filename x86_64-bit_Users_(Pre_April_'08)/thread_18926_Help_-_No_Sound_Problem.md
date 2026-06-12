---
title: "Help - No Sound Problem ??"
date: 2005-03-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by mips on 2005-03-09
Hi,

I have a fresh install of Hoary AMD64-K8 Array6

I cannot get any sound out of my Plantronics **USB** headset. I do not have normal speakers so I cannot test the onboard sound.

I did a update & upgrade to ensure I'm current with the OS.

At startup I get an **ERROR:** failed to initialize HAL!  I can however open the Device Manager & the Plantronics headset is a listed device.

Anybody got any ideas ??? 

Read somewhere that I might have to change the device to 0 instead of 1 but have no clue how to do that.


Some sample output attached...

> 
reon@box:~$ **more /proc/asound/version**
Advanced Linux Sound Architecture Driver Version 1.0.6 (Sun Aug 15 07:17:53 2004 UTC).
Compiled on Mar  2 2005 for kernel 2.6.10-4-amd64-k8.


reon@box:~$ **grep VERSION_STR /usr/include/alsa/version.h**
grep: /usr/include/alsa/version.h: No such file or directory


reon@box:~$ **more /etc/modutils/alsa-base**
# snd module options
options snd device_mode=0660
# autoloader aliases
alias char-major-116 snd
alias char-major-14 soundcore
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1
alias sound-slot-2 snd-card-2
alias sound-slot-3 snd-card-3
alias sound-slot-4 snd-card-4
alias sound-slot-5 snd-card-5
alias sound-slot-6 snd-card-6
alias sound-slot-7 snd-card-7
# Load optional modules above their base modules
above snd-pcm snd-pcm-oss
above snd-mixer snd-mixer-oss
above snd-seq snd-seq-oss snd-seq-midi
# Cause a script to be run after snd-emu8000-synth module initialization
post-install snd-emu8000-synth /lib/alsa/modprobe-post-install snd-emu8000-synth
# Cause a script to be run after card driver module initialization
post-install snd-ad1816a /lib/alsa/modprobe-post-install snd-ad1816a
post-install snd-ad1848 /lib/alsa/modprobe-post-install snd-ad1848
post-install snd-ali5451 /lib/alsa/modprobe-post-install snd-ali5451
post-install snd-als100 /lib/alsa/modprobe-post-install snd-als100
post-install snd-als4000 /lib/alsa/modprobe-post-install snd-als4000
post-install snd-asihpi /lib/alsa/modprobe-post-install snd-asihpi
post-install snd-atiixp /lib/alsa/modprobe-post-install snd-atiixp
post-install snd-au8810 /lib/alsa/modprobe-post-install snd-au8810
post-install snd-au8820 /lib/alsa/modprobe-post-install snd-au8820
post-install snd-au8830 /lib/alsa/modprobe-post-install snd-au8830
post-install snd-azt2320 /lib/alsa/modprobe-post-install snd-azt2320
post-install snd-azt3328 /lib/alsa/modprobe-post-install snd-azt3328
post-install snd-azx /lib/alsa/modprobe-post-install snd-azx
post-install snd-ca0106 /lib/alsa/modprobe-post-install snd-ca0106
post-install snd-cmi8330 /lib/alsa/modprobe-post-install snd-cmi8330
post-install snd-cmipci /lib/alsa/modprobe-post-install snd-cmipci
post-install snd-cs4231 /lib/alsa/modprobe-post-install snd-cs4231
post-install snd-cs4232 /lib/alsa/modprobe-post-install snd-cs4232
post-install snd-cs4236 /lib/alsa/modprobe-post-install snd-cs4236
post-install snd-cs4281 /lib/alsa/modprobe-post-install snd-cs4281
post-install snd-cs46xx /lib/alsa/modprobe-post-install snd-cs46xx
post-install snd-darla20 /lib/alsa/modprobe-post-install snd-darla20
post-install snd-darla24 /lib/alsa/modprobe-post-install snd-darla24
post-install snd-dt019x /lib/alsa/modprobe-post-install snd-dt019x
post-install snd-emu10k1 /lib/alsa/modprobe-post-install snd-emu10k1
post-install snd-emu10k1x /lib/alsa/modprobe-post-install snd-emu10k1x
post-install snd-ens1370 /lib/alsa/modprobe-post-install snd-ens1370
post-install snd-ens1371 /lib/alsa/modprobe-post-install snd-ens1371
post-install snd-es1688 /lib/alsa/modprobe-post-install snd-es1688
post-install snd-es18xx /lib/alsa/modprobe-post-install snd-es18xx
post-install snd-es1938 /lib/alsa/modprobe-post-install snd-es1938
post-install snd-es1968 /lib/alsa/modprobe-post-install snd-es1968
post-install snd-es968 /lib/alsa/modprobe-post-install snd-es968
post-install snd-fm801 /lib/alsa/modprobe-post-install snd-fm801
post-install snd-gina20 /lib/alsa/modprobe-post-install snd-gina20
post-install snd-gina24 /lib/alsa/modprobe-post-install snd-gina24
post-install snd-gina3g /lib/alsa/modprobe-post-install snd-gina3g
post-install snd-gusclassic /lib/alsa/modprobe-post-install snd-gusclassic
post-install snd-gusextreme /lib/alsa/modprobe-post-install snd-gusextreme
post-install snd-gusmax /lib/alsa/modprobe-post-install snd-gusmax
post-install snd-harmony /lib/alsa/modprobe-post-install snd-harmony
post-install snd-hdsp /lib/alsa/modprobe-post-install snd-hdsp
post-install snd-hdspm /lib/alsa/modprobe-post-install snd-hdspm
post-install snd-ice1712 /lib/alsa/modprobe-post-install snd-ice1712
post-install snd-ice1724 /lib/alsa/modprobe-post-install snd-ice1724
post-install snd-indigo /lib/alsa/modprobe-post-install snd-indigo
post-install snd-indigodj /lib/alsa/modprobe-post-install snd-indigodj
post-install snd-indigoio /lib/alsa/modprobe-post-install snd-indigoio
post-install snd-intel8x0 /lib/alsa/modprobe-post-install snd-intel8x0
post-install snd-interwave /lib/alsa/modprobe-post-install snd-interwave
post-install snd-interwave-stb /lib/alsa/modprobe-post-install snd-interwave-stb
post-install snd-korg1212 /lib/alsa/modprobe-post-install snd-korg1212
post-install snd-layla20 /lib/alsa/modprobe-post-install snd-layla20
post-install snd-layla24 /lib/alsa/modprobe-post-install snd-layla24
post-install snd-layla3g /lib/alsa/modprobe-post-install snd-layla3g
post-install snd-maestro3 /lib/alsa/modprobe-post-install snd-maestro3
post-install snd-mia /lib/alsa/modprobe-post-install snd-mia
post-install snd-mixart /lib/alsa/modprobe-post-install snd-mixart
post-install snd-mona /lib/alsa/modprobe-post-install snd-mona
post-install snd-mpu401 /lib/alsa/modprobe-post-install snd-mpu401
post-install snd-msnd-pinnacle /lib/alsa/modprobe-post-install snd-msnd-pinnacle
post-install snd-mtpav /lib/alsa/modprobe-post-install snd-mtpav
post-install snd-nm256 /lib/alsa/modprobe-post-install snd-nm256
post-install snd-opl3sa2 /lib/alsa/modprobe-post-install snd-opl3sa2
post-install snd-opti92x-ad1848 /lib/alsa/modprobe-post-install snd-opti92x-ad1848
post-install snd-opti92x-cs4231 /lib/alsa/modprobe-post-install snd-opti92x-cs4231
post-install snd-opti93x /lib/alsa/modprobe-post-install snd-opti93x
post-install snd-pc98-cs4232 /lib/alsa/modprobe-post-install snd-pc98-cs4232
post-install snd-pcxhr /lib/alsa/modprobe-post-install snd-pcxhr
post-install snd-pdaudiocf /lib/alsa/modprobe-post-install snd-pdaudiocf
post-install snd-pdplus /lib/alsa/modprobe-post-install snd-pdplus
post-install snd-portman2x4 /lib/alsa/modprobe-post-install snd-portman2x4
post-install snd-powermac /lib/alsa/modprobe-post-install snd-powermac
post-install snd-rme32 /lib/alsa/modprobe-post-install snd-rme32
post-install snd-rme96 /lib/alsa/modprobe-post-install snd-rme96
post-install snd-rme9652 /lib/alsa/modprobe-post-install snd-rme9652
post-install snd-sa11xx-uda1341 /lib/alsa/modprobe-post-install snd-sa11xx-uda1341
post-install snd-sb16 /lib/alsa/modprobe-post-install snd-sb16
post-install snd-sb8 /lib/alsa/modprobe-post-install snd-sb8
post-install snd-sbawe /lib/alsa/modprobe-post-install snd-sbawe
post-install snd-serialmidi /lib/alsa/modprobe-post-install snd-serialmidi
post-install snd-serial-u16550 /lib/alsa/modprobe-post-install snd-serial-u16550
post-install snd-sgalaxy /lib/alsa/modprobe-post-install snd-sgalaxy
post-install snd-sonicvibes /lib/alsa/modprobe-post-install snd-sonicvibes
post-install snd-sscape /lib/alsa/modprobe-post-install snd-sscape
post-install snd-sun-amd7930 /lib/alsa/modprobe-post-install snd-sun-amd7930
post-install snd-sun-cs4231 /lib/alsa/modprobe-post-install snd-sun-cs4231
post-install snd-sun-dbri /lib/alsa/modprobe-post-install snd-sun-dbri
post-install snd-trident /lib/alsa/modprobe-post-install snd-trident
post-install snd-usb-audio /lib/alsa/modprobe-post-install snd-usb-audio
post-install snd-usb-usx2y /lib/alsa/modprobe-post-install snd-usb-usx2y
post-install snd-via82xx /lib/alsa/modprobe-post-install snd-via82xx
post-install snd-vx222 /lib/alsa/modprobe-post-install snd-vx222
post-install snd-vxp440 /lib/alsa/modprobe-post-install snd-vxp440
post-install snd-vxpocket /lib/alsa/modprobe-post-install snd-vxpocket
post-install snd-wavefront /lib/alsa/modprobe-post-install snd-wavefront
post-install snd-ymfpci /lib/alsa/modprobe-post-install snd-ymfpci
# Prevent abnormal drivers from grabbing index 0
options snd-atiixp-modem index=-2
options snd-bt87x index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2


reon@box:~$ **more /proc/asound/cards**
0 [CK804          ]: NFORCE - NVidia CK804
                     NVidia CK804 with ALC850 at 0xf4006000, irq 23
1 [Headset        ]: USB-Audio - Plantronics Headset
                     Plantronics Plantronics Headset at usb-0000:00:02.0-1, full speed


reon@box:~$ **lspci | egrep audio**
0000:00:04.0 Multimedia audio controller: nVidia Corporation: Unknown device 0059 (rev a2)


reon@box:~$ **more /dev/sndstat**
Sound Driver:3.8.1a-980706 (ALSA v1.0.6 emulation code)
Kernel: Linux box 2.6.10-4-amd64-k8 #1 Wed Mar 2 06:21:59 UTC 2005 x86_64
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
NVidia CK804 with ALC850 at 0xf4006000, irq 23
Plantronics Plantronics Headset at usb-0000:00:02.0-1, full speed

Audio devices:
0: NVidia CK804 (DUPLEX)
1: USB Audio (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Realtek ALC850 rev 0
1: USB Mixer


reon@box:~$ **sudo alsamixer**
Password:
##NO ERRORS REPORTED##


reon@box:~$ **ls -l /dev/snd/**
total 0
crw-rw----  1 root audio 116,  0 2005-03-09 23:00 controlC0
crw-rw----  1 root audio 116, 32 2005-03-09 23:00 controlC1
crw-rw----  1 root audio 116, 24 2005-03-09 23:00 pcmC0D0c
crw-rw----  1 root audio 116, 16 2005-03-09 23:00 pcmC0D0p
crw-rw----  1 root audio 116, 25 2005-03-09 23:00 pcmC0D1c
crw-rw----  1 root audio 116, 18 2005-03-09 23:00 pcmC0D2p
crw-rw----  1 root audio 116, 56 2005-03-09 23:00 pcmC1D0c
crw-rw----  1 root audio 116, 48 2005-03-09 23:00 pcmC1D0p
crw-rw----  1 root audio 116, 33 2005-03-09 23:00 timer


reon@box:~$ **ls -l /etc/modprobe.d**
total 36
-rw-r--r--  1 root root  4745 2005-01-14 15:37 aliases
-rw-r--r--  1 root root 11691 2005-02-03 09:12 alsa-base
drwxr-xr-x  2 root root  4096 2005-03-08 18:47 arch
lrwxrwxrwx  1 root root     9 2005-03-08 18:48 arch-aliases -> arch/i386
-rw-r--r--  1 root root    38 2005-03-03 01:41 ibm_acpi.modprobe
drwxr-xr-x  2 root root  4096 2005-03-08 21:38 isapnp
-rw-r--r--  1 root root    41 2005-03-03 01:41 toshiba_acpi.modprobe



---

### Post by kubla on 2005-03-09
You have checked if your mixer has the output for the device turned up?

---

### Post by mips on 2005-03-09
Hi kubla,

Sorry forgot to mention that the device listed in alsamixer is NOT my USB headset but the onboard audio device. I need to get alsa to use my USB device.

Cheers
mips

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.8 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;&#9474; Card: NVidia CK804                                                           &#9474;&#9474; Chip: Realtek ALC850 rev 0                                                   &#9474;&#9474; View: Playback                                                               &#9474;&#9474; Item: LFE [Off]                                                              &#9474;&#9474;                                                                              &#9474;&#9474;    &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;              &#9474;&#9474;    &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;              &#9474;&#9474;    &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;              &#9474;&#9474;    &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;              >&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;              >&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;              >&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;              >&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;              >&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;              >&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;              &#9474;&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;              &#9474;&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;              &#9474;&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9484;&#9472;&#9472;&#9488;     &#9474;&#9474;    &#9474;OO&#9474;     &#9474;MM&#9474;      &#9474;OO&#9474;     &#9474;MM&#9474;     &#9474;MM&#9474;      &#9474;MM&#9474;     &#9474;MM&#9474;     &#9474;MM&#9474;     &#9474;&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9474;&#9474;   71<>71     100     71<>71  100<>100    100       100    94<>94             &#9474;&#9474;   Master  Master M    PCM    Surround  Center  <  LFE   >  Line   Line-In    &#9474;&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by mips on 2005-03-10
C'mon, surely there must be someone out there that knows how to fix this problem ?!

Maybe I should just bin this whole Ubuntu/Linux idea and try again in a year or two, I know I'm running a beta version but there must be a fix for this.

Any help would be appreciated.

Thanks
mips

---

### Post by mips on 2005-03-11
Ok, my USB headset is now my default device and working thanks to crimsun on IRC #ubuntu

Solution:

Had to determine loaded sound modules:

reon@box:~$ cat /proc/asound/modules
0 snd_intel8x0
1 snd_usb_audio
reon@box:~$


Then change /etc/modprobe.d/alsa-base so snd_intel8x0 does not grab index 0:

echo "options snd_intel8x0 index=-2" | sudo tee -a /etc/modprobe.d/alsa-base

just ensure snd_usb_audio is not set to index=2


cheers
mips

---

### Post by 1337sithlord on 2005-05-30
is that reon@box code, stuff that u type in the root terminal? cause it keeps saying command not found.  Also that file that u said i had to change so it doesnt grab index 0, uhh what line is that?  its filled with crazy code.  Sry but i am VERY new to ubuntu lol

---

### Post by matesrates on 2005-05-31
in the command given as:

[INDENT]reon@box:~$ cat /proc/asound/modules[/INDENT]

the 'reon@box:~$' bit is the prompt

so you just need to type the 'cat /proc/asound/modules' part as a command


have fun with Ubuntu!

---

### Post by 1337sithlord on 2005-05-31
Yea i did that code now, and it did set my usb headset (socom) as my defualt sound device.  It includes a microhpone tho and that stil wont work.  It probably has to be put into the kernel somehow which is very hard.  The file where u have to set the indexes doesnt mention the names of the sound devices listed when i typed that code.  So i dunno what the second part is all about.  Anyway, im mad at this stuff so il just get a normal mic lol.

---

### Post by OpposingForce on 2005-09-02
on hoary im geting this problem but my plantronics headset isnt being detected by the device manager

---

### Post by icheyne on 2007-11-29
You can switch between soundcards by installing and using asoundconf-gtk

---

### Post by pickles46 on 2008-03-17
> **mips said:**
> Ok, my USB headset is now my default device and working thanks to crimsun on IRC #ubuntu

Solution:

Had to determine loaded sound modules:

reon@box:~$ cat /proc/asound/modules
0 snd_intel8x0
1 snd_usb_audio
reon@box:~$


Then change /etc/modprobe.d/alsa-base so snd_intel8x0 does not grab index 0:

echo "options snd_intel8x0 index=-2" | sudo tee -a /etc/modprobe.d/alsa-base

just ensure snd_usb_audio is not set to index=2


cheers
mips

What should it index to?

I don't want to change from to 2 to something that may be worse. :confused:

Thank you for posting the solution though. :)

i changed usb options to 1 however some programs still do not have sound (vlc, firefox/swiftweasel, wine applications) but it does work for totem

what it looks like now:
"# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-1
options snd-usb-usx2y index=-1
options snd-usb-caiaq index=-1
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388"

Any help would be greatly appreciated.

---

