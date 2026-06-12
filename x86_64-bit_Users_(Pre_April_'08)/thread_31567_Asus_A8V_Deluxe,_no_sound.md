---
title: "Asus A8V Deluxe, no sound"
date: 2005-05-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by DutchLau on 2005-05-03
Hello Ubuntu community,

The last few weeks I've been trying to help out all of you here in the forums, but now I need some help and it would be greatly greatly appreciated.

I have just performed a clean i386 (I don't want to go 64 yet) Ubuntu install on my PC (The specs are in my signature) Everything is working AMAZING, fast load up, quick unpackaging and an amazingly fast install, now the question is: How do I get sound working?

At the login screen I have no sound, and in Ubuntu I have no sound, even though I've installed all the codecs.

Could someone please please please help me out with this? It's very frustrating to have a new PC and not to be able to play sound on it. Could someone please reply?

Friendly greets,

DutchLau

---

### Post by Ride Jib on 2005-05-04
[QUOTE=DutchLau]Hello Ubuntu community,

The last few weeks I've been trying to help out all of you here in the forums, but now I need some help and it would be greatly greatly appreciated.

I have just performed a clean i386 (I don't want to go 64 yet) Ubuntu install on my PC (The specs are in my signature) Everything is working AMAZING, fast load up, quick unpackaging and an amazingly fast install, now the question is: How do I get sound working?

At the login screen I have no sound, and in Ubuntu I have no sound, even though I've installed all the codecs.

Could someone please please please help me out with this? It's very frustrating to have a new PC and not to be able to play sound on it. Could someone please reply?

Friendly greets,

DutchLau[/QUOTE]
 So you can't get *any* sound to work? I don't have an answer for you, but I am subscribing to this because I plan to install Ubuntu on my x64 desktop once the install cd's arrive (if they ever do!)

---

### Post by rsw on 2005-05-04
[QUOTE=DutchLau]The last few weeks I've been trying to help out all of you here in the forums, but now I need some help and it would be greatly greatly appreciated.

I have just performed a clean i386 (I don't want to go 64 yet) Ubuntu install on my PC (The specs are in my signature) Everything is working AMAZING, fast load up, quick unpackaging and an amazingly fast install, now the question is: How do I get sound working?

At the login screen I have no sound, and in Ubuntu I have no sound, even though I've installed all the codecs.

Could someone please please please help me out with this? It's very frustrating to have a new PC and not to be able to play sound on it. Could someone please reply?[/QUOTE]
 if you could post the output from the following commands, that'd help out a lot:

$ lspci

and 

$ lsmod | grep snd

---

### Post by DutchLau on 2005-05-04
@rsw

Just to clarify things, I don't have sound *at all* the following are the outputs you asked for:

lspci:

> 0000:00:00.0 Host bridge: VIA Technologies, Inc.: Unknown device 0282
0000:00:00.1 Host bridge: VIA Technologies, Inc.: Unknown device 1282
0000:00:00.2 Host bridge: VIA Technologies, Inc.: Unknown device 2282
0000:00:00.3 Host bridge: VIA Technologies, Inc.: Unknown device 3282
0000:00:00.4 Host bridge: VIA Technologies, Inc.: Unknown device 4282
0000:00:00.7 Host bridge: VIA Technologies, Inc.: Unknown device 7282
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800 South]0000:00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:00:08.0 RAID bus controller: Promise Technology, Inc. PDC20378 (FastTrak 378/SATA 378) (rev 02)
0000:00:0a.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Ethernet 10/100/1000Base-T Adapter (rev 13)
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [K8T800 South]0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1) 

lsmod | grep snd :

> snd_via82xx            25248  1
snd_ac97_codec         64608  1 snd_via82xx
snd_pcm_oss            47652  0
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_via82xx,snd_pcm
gameport                4608  1 snd_via82xx
snd_mpu401_uart         7168  1 snd_via82xx
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  1 snd_rawmidi
snd                    50276  9 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  2 snd 

I hope this helps. I really don't understand what's going on though. The device manager shows I have the VIA AC 97 Codec installed, but Still nothing.  ](*,) 

Thanks already,

DutchLau

EDIT: I'm using Hoary i386, this shouldn't be a problem right?

---

### Post by DutchLau on 2005-05-04
Okay!

I got my sound working! I had to configure Alsa and now it works perfectly! On the reboot I heard the beautiful sounds of the Ubuntu startup, I've never been so happy in my entire life :D

Thanks Ubuntu community,

DutchLau

---

### Post by mrscintilla on 2005-05-15
[QUOTE=DutchLau]Okay!

I got my sound working! I had to configure Alsa and now it works perfectly! On the reboot I heard the beautiful sounds of the Ubuntu startup, I've never been so happy in my entire life :D

Thanks Ubuntu community,

DutchLau[/QUOTE]


What's Alsa? How did you configure it?   I have an Asus A8N-SLI w/ Real AC97 audio chip.  Can you tell me whether your solution will work for my board?

---

### Post by makis on 2005-05-15
[QUOTE=mrscintilla]What's Alsa? How did you configure it? I have an Asus A8N-SLI w/ Real AC97 audio chip. Can you tell me whether your solution will work for my board?[/QUOTE]

well,[color=black] ALSA is Advanced Linux Sound Architecturefor more information and complete HowTo about sound look here:[http://ubuntuforums.org/showthread.php?t=26567]("http://ubuntuforums.org/showthread.php?t=26567")

I am sure u will find what u want!

Cheers!


[/color]

---

### Post by DutchLau on 2005-05-15
@ mrscintilla

Maybe [this](http://www.ubuntuguide.org/#configuresoundproperly) might help you? Also make sure to have the volume on full for the mixer (look in the top right corner of the Ubuntu dekstop  :razz: 

GL,

DutchLau

---

### Post by mrscintilla on 2005-05-15
Followed the guide but I have amd64 version.  no libesd-also0 in synaptic..
any other ideas?  


[QUOTE=DutchLau]@ mrscintilla

Maybe [this](http://www.ubuntuguide.org/#configuresoundproperly) might help you? Also make sure to have the volume on full for the mixer (look in the top right corner of the Ubuntu dekstop  :razz: 

GL,

DutchLau[/QUOTE]

---

### Post by hack_benjamin on 2005-06-04
i got this board (although im running gentoo on it now)
are you aware that the sound you need is intel8x0 not the via module? i had to load it  in the kernel for it to work.. (it still doesnt properly but its getting there!)

---

### Post by FluffyElmo on 2005-06-05
I have sound running on this board and it is reported as a *VIA VT8233/A/8235/8237 AC97 Audio*, and working using ESD as the sound daemon. 

As far as I know there is no Intel chip on the board for sound.

---

### Post by Octane on 2005-06-19
[QUOTE=FluffyElmo]I have sound running on this board and it is reported as a *VIA VT8233/A/8235/8237 AC97 Audio*, and working using ESD as the sound daemon. 

As far as I know there is no Intel chip on the board for sound.[/QUOTE]
Just wanted to verify this. I have an A8V-E Deluxe and it uses the via82xx module

---

