---
title: "Problems installing on Presario CQ50"
date: 2008-09-04
forum: x86 64-bit Users
---

### Post by jdguzman on 2008-09-04
Ok so this is my last resort.  I've tried many options to try and get Ubuntu 64 bit installed on this laptop to no avail.  Following are the laptop specs:

AMD Athlon 64 X2 QL-60
3 GB RAM
NVIDIA GeForce 8200M
FUJITSU MHZ2250BH G2 ATA (250 GB)
Optiarc DVD-RW AD-7561S ATA
Synaptics Touchpad
HDAudio Soft Data Fax Modem
Atheros AR5007 802.11b/g WiFi Adapter
NVidia nForce 10/100/1000 NIC
Conexant High Defenition SmartAudio 221
Realtek USB 2.0 Card Reader

I tried installing it with several different boot options but nothing worked (ie. acpi=off, noapci, brokenmodules=ath5k).

I also tried to install a wubi install in windows but also wasn't able to get it to boot.

I get a CPU 0: Machine Fault Error.

After messing with it a little i tried installing the 32 bit version and got it to work however i did get this message:

wifi%d: unable to load device

This might have something to do with the 64 bit version not working but I'm not sure.

All of this was with the latest Ubuntu Hardy download (8.4)

Any suggestions would be appreciated.

Regards!

---

### Post by jdguzman on 2008-09-04
I don't like to bump threads but i'm really at a loss here.  Any ideas would be helpful.

Thanks again.

---

### Post by jdguzman on 2008-09-05
Just thought I'd throw in an update (the more info the better right?) ... 

I just tried to run the alternate install cd and got all the way the the formating of the hard drive and about 40% through the format I got a kernel panic.

So now I've tried the 7.10, and all the variants of 8.4.1 and no luck.  And by the looks of it there isn't anyone that has any ideas :confused:

---

### Post by gragib on 2008-09-15
I was having the same problem when I burnt the image to a CD. But it works fine when I burnt it to a DVD. I don't even want to guess why it works that way.

---

### Post by cus4fun on 2008-09-15
I gave up and installed 32 bit. But it works fine.

Here's a copy of the solution I posted elsewhere:

I have a CQ50-105NR that I just bought at Best Buy. About 8 hours of my noob fumbling and here's what I found.

I d/l'd and burned 8.04.1 and booted the live CD. Let the whole thing settle until it tossed the restricted driver notice at me, then I clicked Install.

By the way, this is a dual (duel) boot with Vista.

Installation went without a hitch.

I had minimal graphics and no wireless.

Graphics: [http://ubuntuforums.org/showthread.php?t=880787](http://ubuntuforums.org/showthread.php?t=880787) Scroll down to the "Tricky Tricky Way After Mainly attempt" section. That's the one that worked for me.

Wireless: [http://ubuntuforums.org/showthread.php?t=865971](http://ubuntuforums.org/showthread.php?t=865971) Scroll down to the #4 post by chilli555. Very simple, and that latest driver seems to do the trick. I still use Network Manager and it gives me no grief, seems to do a great job.

Sometime during all this, I think it was during the Nvidia driver install, my xorg.conf got goofed up and my touchpad was nearly featureless, no scrolling, no double-click-and-drag... so I had to re-edit xorg.conf, both the touchpad section and the server layout section. Just make sure there IS a section for "Synaptics Touchpad" with "synaptics" as the driver and make certain that "Synaptics Touchpad" is the default in the server layout section.

System .wav sounds are still crackly sounding, but music and movies play fine.

Hope this helps someone. Happy day.

---

### Post by el_escorpion on 2008-09-16
I have the same laptop and unfortunatly the same set of problems. The nVidia guide link was of great help so thank you, however for some reason the wireless still doesn't work... what exactly did you do to get it to work for you?

---

### Post by el_escorpion on 2008-09-16
Hmmm, on problem fixed. Used the brand new driver ath9k. Someone on the forums here posted a bash script that generates a custom .deb for you it's called compat-wireless-ath9k-.......sh

---

### Post by jdguzman on 2008-09-16
Well i've been away for a while but I might give the 64 bit ubuntu another shot.  i got 32 bit to work with no problems wireless and video included but i haven't gone back to try the 64 bit version.  I'll see if I give it another shot tomorrow.

---

### Post by cus4fun on 2008-09-20
Anyone been able to get the sound to work without the crackling?

---

### Post by iv2101 on 2008-09-27
Hi, I also have the cq50. I first tried to boot 7.10 32bit, but i would go (busybox error). THen I burned 8.04.1 x64 on an expensive cdr and it installed fine. No wireless, 800x640 res, fuzzy sound. It would freeze with the driver ubuntu suggested and envy couldn't locate a good driver. I followed instructions to install the nvidia driver and that problem went away. I still can't get the wireless to work (see my recent thread) and am about to explore how to fix the sound.

---

### Post by jithinkr on 2008-10-02
Cracking and Popping Sound.

Never found any proper help for this problem, the problem regarding the crackling and popping sound when playing multimedia. I don't have the perfect solution, but I think what I have found can be a starting point. While playing with the Sound Preferences (System>Preferences>Sound), I selected HDA NVidia Alsa Mixer Device and selected Digital in the listbox. What I noticed is that, with this, I am unable to control the volume using the function key and the volume up and volume down keys (In my laptop it is function key + pg up / pg dn). This is because I have selected to control the Digital Volume using the keys. But this is what caught my fascination, When I keep pressing (fn + pg dn) the crackling and popping sound subsides. But if I let go of the keys, the annoying sound comes back. 
I changed the Default Mixer Tracks Device selection and tried. Now the keys function properly and help you control the sound. 
I don't know if that helps, but I hope this observation will be of help to someone, and he/she could get a proper solution to this annoying sound problem in Ubuntu. :)

---

### Post by seijuuroo23 on 2008-10-08
I have the same computer but another version (Presario CQ 105ef). I managed to fix the sound by unticking the ESD option in the second tab of system>preference>sound. btw, I had tons of problem with Hardy but since I upgraded to Intrepid, everything works flawlessly. For a beta release, I'm very impressed. Might solve some of your problems guys.

---

### Post by iv2101 on 2008-10-09
Doesn't do the job for me, but ill give the beta a try.

---

### Post by iv2101 on 2008-10-14
Ok, so I upgraded to the Ibex beta version (I couldn't boot from the cd). Now wireless works out of the box, sound is fine (no choppiness like before), the recommended video driver works. I totally support what seijuuroo23 said. 

Suspend didn't work the only time I tried it and I haven't tried the hybernate option yet.

---

### Post by cmat on 2008-10-30
So wireless just worked? I haven't been able to get it going. I needed to use my USB adaptor. I used a clean install.

---

