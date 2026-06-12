---
title: "Help! No sound!"
date: 2007-11-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by HeavyP on 2007-11-15
I can't get my system to produce any sound and I'm totally new to Ubuntu! I went to sound and test a several times and no sound is made.

Please help me diagnose the problem!

Any wee help is appreciated!

Thank you in advance.

---

### Post by Sef on 2007-11-15
1) What version of Ubuntu are you using?

2) What are your system specs?

3a) open the terminal and type in this command: ```
cat /proc/asound/cards
```.  

3b) Applications > Accessories > Terminal

3c) Copy and paste the results here.

---

### Post by Yellow Pasque on 2007-11-15
Also run:
```
sudo update-pciids
lspci | grep "audio"
```

---

### Post by alip on 2007-11-15
alip@aLiP-Laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd4340000 irq 23

---

### Post by HeavyP on 2007-11-15
> **Sef said:**
> 1) What version of Ubuntu are you using?

I'm using the latest version of 64-bit Ubuntu. [Gutsy?]

> 
2) What are your system specs?

Core 2 Duo T7100
Ram 2gb
On board sound and VGA

Detailed specs please google for Lenovo 3000 Y410
> 


3a) open the terminal and type in this command: ```
cat /proc/asound/cards
```.  

3c) Copy and paste the results here.

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf8300000 irq 22


```
sudo update-pciids
```
Works fine look like it's updating something but still no sound

```
lspci | grep "audio"
```
Nothing seems to happen

Thank you everyone for your help!
Really appreciate that, god bless ya :)

---

### Post by Six Ways on 2007-11-15
I'm having similar problems except ```
lspci | grep "audio"
``` works and gives me all the right info, whereas ```
cat /proc/asound/cards
``` says there's no such file/directory. My specs are

Core2Duo Q6600
Asus P5N32 SLi Premium mobo
nVidia GeForce8800 GTX 768mb
Soundblaster X-Fi XtremeMusic
500Gb SATA HDD
2Gb RAM

Any help appreciated.

---

### Post by rpmpv1 on 2007-11-15
This might sound stupid, but have you tried right-clicking on the Volume Control icon up near the clock and going to preferences? My sound wouldn't work right away when I installed Gutsy and it was because the volume control was set for the analog audio signal. I'm using an optical cable connected to a surround receiver for my audio so I couldn't hear anything until I selected the Digital-1 option and un-muted it. Hopefully that helps!

---

### Post by Luis Macias on 2007-11-15
hi, i had the same problem, i solved following method g from this link : [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller), so see there which method is for you. Only problem that i still have is low sounds.

Hope that helps

---

### Post by HeavyP on 2007-11-15
I followed the link and mess up in one of the steps. Now in volume control it shows 

No volume control GStreamer plugis and/or devices found 

- -"

I'll try this again when I got home this evening

Edit: I guess I should go back to Windows - -"

---

### Post by Six Ways on 2007-11-16
That's the problem I've had from the start. The hardware properties list the soundcard as being connected etc, but nothing on the system seems to realise it's a soundcard!

---

### Post by nullpex on 2007-11-24
> **Six Ways said:**
> I'm having similar problems except ```
lspci | grep "audio"
``` works and gives me all the right info, whereas ```
cat /proc/asound/cards
``` says there's no such file/directory. My specs are

Core2Duo Q6600
Asus P5N32 SLi Premium mobo
nVidia GeForce8800 GTX 768mb
Soundblaster X-Fi XtremeMusic
500Gb SATA HDD
2Gb RAM

Any help appreciated.

Hi I have a P5N32-E SLI. Sound works great and

```

$ cat /proc/asound/cards 
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xefff0000 irq 20

```

Make sure that you have your on-board sound card enabled in the BIOS. Search for HD Audio and set it to [Auto].

---

