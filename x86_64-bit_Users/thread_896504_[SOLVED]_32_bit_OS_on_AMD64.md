---
title: "[SOLVED] 32 bit OS on AMD64"
date: 2008-08-21
forum: x86 64-bit Users
---

### Post by StageCraft on 2008-08-21
Hello Forum, Hows life?

Here's my problem: I've had quite a bit of experiance now working with the 32 bit version of Xubuntu and I dont want to change. I like it and see no reason to "Take full advantage of my hardware". You see, the problem is that I now have a new computer with an AMD Athlon 64 and I cant install the 32 bit OS. I get to the first screen an I'm left haning in a termional, I'm not sure if GRUB even loads. I know that most of the hardware is recognized because I can still  do stuff in this screen, but I cant get any kind of graphic OS.

I may try the 64 bit as a dual boot later, but for now I want something that I know so I can fix any problems as they arrise. Can anyone help me install the 32 bit version of Xubuntu?

---

### Post by forger on 2008-08-21
1) Is it a laptop?
2) Did you try to boot with the latest Xubuntu 8.04**[COLOR="Red"].1[/COLOR]** live cd? (not 8.04)
3) Did you install it using Wubi installer or did you boot off the Xubuntu Live CD?

Xubuntu 64-bit shouldn't be that different from 32-bit, I use flash on Ubuntu 64-bit with java (never tried the java in browser), nowadays it installs the same way the 32-bit package does :)

---

### Post by insane_alien on 2008-08-21
well, first of i would urge you to try the 64-bit version. it is perfectly stable and has all the apps you are used to on 32-bit. 

the 32-bit should work on your computer. have you checked the install CD? if that is defective it won't work.

---

### Post by StageCraft on 2008-08-21
Its a Desktop

I'm downloading the 64 bit right now to give it a go

The Install worked on my laptop and it is the 8.04.1

I'm not using Wubi, I'd rather just Dual boot.

Mainly I'm just a bit concerned because I've heard that there are differences in a few things and I dont want to end up with too many problems I wont know how to fix. I'll try the 64 bit later today and see how it goes. This may all be a waste of time If all goes well but either way the Tread may be a resource to someone else later.

---

### Post by Kilz on 2008-08-21
> **StageCraft said:**
> Its a Desktop

I'm downloading the 64 bit right now to give it a go

The Install worked on my laptop and it is the 8.04.1

I'm not using Wubi, I'd rather just Dual boot.

Mainly I'm just a bit concerned because I've heard that there are differences in a few things and I dont want to end up with too many problems I wont know how to fix. I'll try the 64 bit later today and see how it goes. This may all be a waste of time If all goes well but either way the Tread may be a resource to someone else later.

Please provide a link to the place you got the information that says there are differences that cause problems so we can see exactly what you are worried about.

Those of us that have run both versions know that there is no significant difference. 

All versions of Linux require some setup. One of the advantages of Ubuntu is the very very active community that can help you if something is to hard for you. But I honestly dont think there will be problems if you are comfortable with other versions of Ubuntu.

Also please realize that while the 32bit os in most cases will run on 64bit hardware. There is no guarantee that it will or that the problems you have to solve to make it do so are simple. Its always best to run the operating system designed for your hardware.

---

### Post by Jouke74 on 2008-08-21
Can you please write in a bit more detail what hardware is in your computer? Especially the graphics card or similar chip on the motherboard would be of help.

Try to install using the safe graphics mode. 

Another option is to burn the alternate install CD. 
(Preferably the AMD64 version).

---

### Post by Sef on 2008-08-21
> Mainly I'm just a bit concerned because I've heard that there are differences in a few things

Almost all programs have 64-bit equivalents now.  It is the rare program that does not have a 64-bit equivalent.

---

### Post by tuxxy on 2008-08-21
Welcome to 64bit im sure you wont go back now :)

---

### Post by Yellow Pasque on 2008-08-21
> Also please realize that while the 32bit os in most cases will run on 64bit hardware. There is no guarantee that it will or that the problems you have to solve to make it do so are simple. Its always best to run the operating system designed for your hardware

Uhh, the last time I checked, x86_64 processors run x86 code natively. I'm all for 64-bitness too, but let's not get carried away and spew over-generalized FUD.

---

### Post by Kilz on 2008-08-21
> **Temüjin said:**
> Uhh, the last time I checked, x86_64 processors run x86 code natively. I'm all for 64-bitness too, but let's not get carried away and spew over-generalized FUD.

No, not fud. While a little old, [this thread gives examples]("http://ubuntuforums.org/showthread.php?t=395164") of people who could not install the i386 version or had issues with it.

---

### Post by Yellow Pasque on 2008-08-21
> **Kilz said:**
> No, not fud. While a little old, [this thread gives examples]("http://ubuntuforums.org/showthread.php?t=395164") of people who could not install the i386 version or had issues with it.
Yes, but they would have the same problems if their CPU's didn't have the extra registers and instructions available.

---

### Post by StageCraft on 2008-08-22
I feel this topic is getting out of control, the main reason I came here was to get the OS installed and it seems that nither the 64 bit nor the 32 are working. I cant even get the alternate to work. I'll try again tomorrow and post how far the startup of the install goes. I didnt have time to copy it down.

Also, heres the desktop I'm using (Sorry about the format, I copied and pasted): 

Processor Type   		AMD Athlon 64 X2 Dual-Core 5600+
Processor Speed		 	2.8GHz
RAM 				3GB PC2-5300 DDR2
Hard Drive Speed/Capacity 	500GB 7200RPM
Optical Drives 			Dual-Layer DVD Burner w/ LightScribe
Graphics 			NVIDIA GeForce 6150 SE Graphics
Pre-loaded Operating System 	Windows Vista Home Premium

Graphics 	
Dedicated Video Memory 		Yes
Shared Video Memory 		1343MB
TV Tuner 			No
Video Memory 			128MB Dedicated
Sound Card 			High Definition Audio

Networking 	
Ethernet Port 			10/100Base-T
Integrated WiFi 		No
Inputs/Outputs 	
Card Reader 			15-In-1 Media Card Reader
Component Output 		No
Composite Output 		No
DVI Output 			No
E-SATA 				No
FireWire (IEEE 1394) 		1 Front, 1 Back
HDMI 				No
Modem 				56K Modem
USB 2.0 			2 Front 4 Back
VGA Output 			Yes

Computing Features 	
Available AGP Slots	 	Not Applicable
Available Hard Drive Bays 	1x 3.5"
Available Memory Slots 		None
Available Optical Bays 		1x 5.25"
Available PCI Slots 		1 PCI Express x1
Available PCI-E Slots 		1 PCI Express x16
Power Supply 			300W
Processor Cache 		1MB + 1MB L2
Removable Storage 		Pocket Media Drive bays
System Bus		 	2000MT/s

---

### Post by Kilz on 2008-08-22
> **Temüjin said:**
> Yes, but they would have the same problems if their CPU's didn't have the extra registers and instructions available.

Not the case for everyone in that thread.

---

### Post by LateNiteTV on 2008-08-22
32bit can be run on 64 bit without a problem. as far as the problem you, OP, are having, im not sure. but to take full advantage of the multiple cores in the 64bit processor, you need to compile SMP support into your kernel.

---

### Post by Kilz on 2008-08-22
> **LateNiteTV said:**
> **32bit can be run on 64 bit without a problem**. as far as the problem you, OP, are having, im not sure. but to take full advantage of the multiple cores in the 64bit processor, you need to compile SMP support into your kernel.

That is incorrect, most of the time it can be ran without a problem. But problems do happen.

---

### Post by LateNiteTV on 2008-08-22
> **Kilz said:**
> That is incorrect, most of the time it can be ran without a problem. But problems do happen.

lol did you just say that to increase your post count?

---

### Post by Kilz on 2008-08-22
> **LateNiteTV said:**
> lol did you just say that to increase your post count?

I stopped looking at that number a looooong time ago. But you know what they say. Those that see problems are usually guilty of them.

---

### Post by Sef on 2008-08-22
> I may try the 64 bit as a dual boot later, but for now I want something that I know so I can fix any problems as they arrise. Can anyone help me install the 32 bit version of Xubuntu?

Things I think of when one cannot install an os:

1) Incompatible Hardware?

2) Md5sum checked?

3) Burned at 4x or less? (Faster can cause a bad burn.)

4)Bad disks?  (Best to get a totally different disk and not one from the ones you just used.  Sometimes a batch of them are bad.)

---

### Post by StageCraft on 2008-08-23
Well I managed to get the 64 bit Alternate installed, (the others were fine, that was just a bad disk) but now I have screen resolution problems, but I think that this is a post for antoher thread as It seems to be a driver issue. Thanks for all the help

---

