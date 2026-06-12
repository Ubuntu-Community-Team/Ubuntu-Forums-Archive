---
title: "Black Screen after HDD Boot - FGLRX"
date: 2006-06-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by charlie. on 2006-06-09
I have recently wiped my PC and installed Kubuntu 6.06 LTS from the standard install CD. The install ran beautifully. I have tried to install the FGLRX drivers for my ATI RADEON X1900XTX using the instructions that worked for me with the Dapper BETA. Now when I restart, the screen remains black immediately after the change to graphical mode. (I hear the screen click as it changes resolutions, after that, nothing happens.) Interestingly, I can bring up the screen's on-screen-display by pressing buttons on the monitor, and it does show the screen to be in the correct resolution. Trying to change to text mode has no effect (Ctrl + Alt + F1). I have to restart into recovery mode to get a console. Please Help!

Here are the specs of my PC:

AMD X2 4400+ Dual Core
1024MB RAM
ATI Radeon X1900XTX
Asus A8N-E Motherboard

I have done hardly anything to modify my install, here is exactly what I did to get here:

Tested the CD - it's perfect.
Installed from the CD (normal, not alternate)
Upgraded to a suitable kernal for my X2 = linux-amd64-k8-smp
Installed the FGLRX module = xorg-driver-fglrx
(Note 1: I never enabled the universe/multiverse, the module was there without touching sources.list)
(Note 2: Up until this point, the desktop has run perfectly with the VESA driver)
Ran aticonfig --initial
Ran aticonfig --overlay-type=Xv
Restarted - this was the first time the black screen problem presented itself.

I fiddled a bit, here is what I have tried so far:

In recovery mode, I tried reverting back to the xorg.conf backup that used the VESA driver, just to check that the kernel upgrade never broke it. X started up with VESA.

In recovery mode, with the original xorg.conf, I tried...
dpkg-reconfigure xserver-xorg -p high
aticonfig --initial
aticonfig --overlay-type=Xv
... to simulate what WOULD have happened under the Dapper BETA. No joy, same problem. (I tried the dpkg-reconfigure trick because I missed that screen using the graphical installer. (Honestly, I think the text installer rocked!))

Literally, this document describes EXACTLY what I have done after installing, minus a few "apt-cache search" commands to check package names.

Any help would be greatly appreciated! Thank you.

---

### Post by fadeh on 2006-06-10
Hi,

i'm a brand new ubuntu member so i'm not so experienced with ubuntu to say: "let's do what i say, i know it's correct!" :) but i've passed the last few days fighting against fglrx, dri, xgl and so on. I've got an amd64 3500+, X1900XT and the solution i found for black screen freeze is to commend Load "extmod" in your /etc/X11/xorg.conf i dunno why but there'are incompatibilities with fglrx driver while using dri.


Bye,

fadeh

---

### Post by campnic on 2006-06-11
[QUOTE=fadeh]Hi,

i'm a brand new ubuntu member so i'm not so experienced with ubuntu to say: "let's do what i say, i know it's correct!" :) but i've passed the last few days fighting against fglrx, dri, xgl and so on. I've got an amd64 3500+, X1900XT and the solution i found for black screen freeze is to commend Load "extmod" in your /etc/X11/xorg.conf i dunno why but there'are incompatibilities with fglrx driver while using dri.


Bye,

fadeh[/QUOTE]

Wow, thanks for taking the time to post.  This has been bothering me for almost 4 days now.  I almost went to windows.  Thanks soo much. :KS   I'm going to post this in the Video & Sound forum so others can see it too, since i was lucky to search in here (on page 2 even)

---

### Post by fadeh on 2006-06-11
I'm happy it worked for u and for the ones having the same problem :)


Bye,

fadeh

---

### Post by misterlizard on 2006-06-13
Just wanted to add that this worked for me too. I'm using the 64-bit Ubuntu Dapper. PC spec as follows:

AMD X2 4400+
2048MB
Sapphire Radeon X1600PRO 512MB
Abit KN8 Ultra

Before commenting out the Load "extmod" line, it would just go to a blank screen on starting GDM, but the monitor (CRT) made noises like it was changing resolution 3 times. It then locked up and I couldn't do Ctrl-Alt-F1 even to get a terminal window. Had to reboot into recovery mode and go back to the vesa driver to get X working again.

Thanks for the tip. Much appreciated :D

---

### Post by Pankrat on 2006-08-31
Sorry to revive that old topic, but the provided solution has a serious problem (at least on my machine):

AMD64 3700+
HIS Radeon X1600XT
ASUS A8N Premium

I had the same problem and commenting out Load "extmod" fixed the black screen after bootup - however, since then, programs were crashing randomly for no apparent reason, especially after long runtime sessions. When running these apps from the console I got *"X Window System error [...] BadRequest"* when they crashed. Somewhere, I found a hint that it has something to do with the absence of extmod, which seems to be the case.

I installed the latest FGLRX driver from ATI website, but DRI was broken. However, the black screen problem vanished when loading extmod, supporting  fadeh's assumption that extmod and dri do not work together.

Since extmod is loaded again the X Window System errors disappeared. 

Has anyone experienced similar issues? Or has managed to get DRI to work without disabling extmod?

---

### Post by hytek on 2006-10-18
This has occured to me also with a X1900GT.

1.
# Load "dri"
Load "extmod"

this resulted in glx being disabled. (can't run glxgears)

2.
Load "dri"
# Load "extmod"

this resulted in glx working (glxgears runs fine)

As noticed by everyone else, these two together do not work, but make sure to disable extmod and not dri or you may lose certain functionality. (I have had no issues with X with extmod disabled)

---

### Post by DavidJE13 on 2006-10-23
I'm getting this same problem after installing ATI drivers, but I don't understand any of the solutions posted here :S (I'm very new to ubuntu) If anyone can explain what fadeh means by "commend Load "extmod" in your /etc/X11/xorg.conf" and/or how to do it I would be greatful.

---

### Post by DavidJE13 on 2006-10-23
Ok, never mind - I found a solution here: [http://www.ubuntuforums.org/showthread.php?t=190133](http://www.ubuntuforums.org/showthread.php?t=190133)

And now I'm not only back running, but also running with both monitors (at last) :D

---

