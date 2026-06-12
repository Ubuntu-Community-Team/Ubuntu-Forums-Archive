---
title: "no sound after instalation"
date: 2006-07-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by BerlinOliver on 2006-07-03
Hi all,

I just installed kubuntu on my AMD 64 Bit 3200+. But when I log into kubunto my left sound box starts beeping loud and plays the normal sound quiet. After a minute or so my sound (both boxes) is completly gone. 

I am running a Nvidia GeForce 6150 chipset. my soundcard is integrated. (Soundbridge Nvidia nForce 430 MCP) Kmix tells me, that I use a "HDA Nvidia" mixer. lspci tells me:
0000:00:10.1 0403: nVidia Corporation MCP51 High Definition Audio (rev a2)

Does anybody have an idea how to fix this?

---

### Post by FenrisAbraxas on 2006-07-03
run:

```
sudo alsamixer 
```

Adjust the values of the controls accordingly test it and when it's good enough use:


```
alsactl save
```

I think :P im not in my linux box at the moment :( but if alsactl fails it will tell you the proper usage :) hope it helps

---

### Post by TripleE on 2006-07-03
[QUOTE=BerlinOliver]Hi all,

I just installed kubuntu on my AMD 64 Bit 3200+. But when I log into kubunto my left sound box starts beeping loud and plays the normal sound quiet. After a minute or so my sound (both boxes) is completly gone. 

I am running a Nvidia GeForce 6150 chipset. my soundcard is integrated. (Soundbridge Nvidia nForce 430 MCP) Kmix tells me, that I use a "HDA Nvidia" mixer. lspci tells me:
0000:00:10.1 0403: nVidia Corporation MCP51 High Definition Audio (rev a2)

Does anybody have an idea how to fix this?[/QUOTE]


I had to use Master Surround to adjust my volume (it was muted) in gnome.  Master did not work at all for me.  Look for any muted connections and try to unmute them and adjust the volume.  I always unmute all of the options for my sound and turn them up half way and play music.  Once I can here it I start muting the options that I do need.

_____________
AMD Athlon64 3000+, 1 GB RAM, Asus A8S-X
BFG Geforce 7300 GS pci-e x16

---

### Post by BerlinOliver on 2006-07-04
I unmuted everything in alsamixer.. still no sound. any other idea?

by the way. aadebug gives out the following information:

olli@Venusfalle:~$ ./aadebug
ALSA Audio Debug v0.1.0 - Wed Jul  5 18:49:38 CEST 2006
[http://alsa.opensrc.org/index.php?page=aadebug](http://alsa.opensrc.org/index.php?page=aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux Venusfalle 2.6.15-25-amd64-k8 #1 SMP PREEMPT Wed Jun 14 11:39:18 UTC 2006 x86_64 GNU/Linux

Loaded Modules --------------------------------------------
snd_mpu401              8968  0
snd_mpu401_uart         9792  1 snd_mpu401
snd_rawmidi            31072  1 snd_mpu401_uart
snd_seq_device         10704  1 snd_rawmidi
snd_bt87x              17576  1
snd_hda_intel          21088  3
snd_hda_codec         174408  1 snd_hda_intel
snd_pcm_oss            58784  0
snd_mixer_oss          19968  1 snd_pcm_oss
snd_pcm               104008  4 snd_bt87x,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              28424  1 snd_pcm
snd                    68000  19 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_bt87x,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         13328  3 snd_bt87x,snd_hda_intel,snd_pcm

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).
0 [NVidia         ]: HDA-Intel - HDA NVidia
                     HDA NVidia at 0xfe024000 irq 217
1 [UART           ]: MPU-401 UART - MPU-401 UART
                     MPU-401 UART at 0x330, irq 10
2 [Bt878          ]: Bt87x - Brooktree Bt878
                     Brooktree Bt878 at 0xfdafe000, irq 66
 17: [0- 1]: digital audio playback
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
 33:       : timer
 40: [1- 0]: raw midi
 32: [1- 0]: ctl
 89: [2- 1]: digital audio capture
 88: [2- 0]: digital audio capture
 64: [2- 0]: ctl
cat: /proc/asound/hwdep: No such file or directory
00-00: AD198x Analog : AD198x Analog : playback 1 : capture 1
00-01: AD198x Digital : AD198x Digital : playback 1
02-00: Bt87x Digital : Bt87x Digital : capture 1
02-01: Bt87x Analog : Bt87x Analog : capture 1
cat: /proc/asound/seq/clients: No such file or directory

Dev Snd ---------------------------------------------------
controlC0  controlC1  controlC2  midiC1D0  pcmC0D0c  pcmC0D0p  pcmC0D1p  pcmC2D0c  pcmC2D1c  timer

CPU -------------------------------------------------------
model name      : AMD Athlon(tm) 64 Processor 3200+
cpu MHz         : 2004.217

RAM -------------------------------------------------------
MemTotal:       478900 kB
SwapTotal:      979956 kB

Hardware --------------------------------------------------
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:04:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:04:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

---

### Post by BerlinOliver on 2006-07-09
Is it posible, that I use a wrong sound module?

---

### Post by zazeri on 2006-07-09
I've installed the Dapper 64 and I've had problems with sound too.
It never worked, and during the installation the system fell in a black screen, although it the cdrom and HD worked until the end of process... it was very strange!!! at least the Dapper works, but the sound... :confused: 
What can I do to fix the sound system???

Proc. Intel PIV 521 (2.8 GHz) HT, EM64T
MB Intel 82945G Express Chipset Family
1 GB DDR2 SDRAM a 533 MHz
Intel Graphics Media Accelerator 950 (GMA950, video onboard)
Sigmatel High Definition Audio (sound card onboard)

---

### Post by srkitch on 2006-07-11
i have the same controller and i use the nvidia driver module "nvsound".  it works, but i can't make it work with ALSA, but it's perfect with the aRTs engine.

---

### Post by BerlinOliver on 2006-07-11
I instaled the nvsound module and sound is from now on not crashed. BUt the beep tone is still there. I hear the normal sound very quiet, but the beep is very loud. Any ideas?

---

