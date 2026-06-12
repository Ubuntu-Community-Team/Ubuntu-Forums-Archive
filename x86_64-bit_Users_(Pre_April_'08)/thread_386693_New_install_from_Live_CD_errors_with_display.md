---
title: "New install from Live CD errors with display"
date: 2007-03-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by vincedia on 2007-03-17
I just finished downloading and trying to run the live CD on my self built system.
When booting the progress bar has a glitch and when I see the desktop it is an orange page with nothing but small lines over the top portion of the screen. The mouse pointer looks and works fine.

Version: ubuntu-6.10-desktop-amd64

I tried safe graphical mode, it did not help. I do not know how to use command line, nor how ot enter command line from the cd.

I have a PC I built myself and have XP running fine.

PC specs are as follows...

ASUS A8n-SLI
2GB Crucial RAM
AMD 64 3700+
Single Nividia BFG 7800GT OC
Multi Hard drives (NOT RAID)
Dell 2005 FP running at 1680X1050

Could any of my hardware be causing this problem?

I have read about issues with a display of 1680X1050, could this be causing my display troubles?

Please know that I have very limited experence with Linux. I have installed it a few times on different machines, but I never got to far into the actual workings. It seems that my biggest problems are always related to video issues.

Thanks in advance!

Vince

---

### Post by vincedia on 2007-03-17
Just a little update on what I have been working on.

I checked my bios to make sure that X64 operation was on. I could not find it in my bios.

So I sownloaded and ran the X32 version with almost the same problem. The loading bar looked fine this time, but after the orange page loaded I was left with a bunch of fuzz in the middle of the screen. (kinda looks like it might be a dialog box, only rendered wrong)

I am now working on running the live CD in another PC to make sure they are not bad copies.


I also forgot to mention that I had 2 monitors connected at the start, but I only have one connected now.

That is all I can think of right now....

Vince

---

### Post by therage on 2007-03-23
I am having the same problem.  Using the the 64 bit cd and the x86 cd.  Same results you describe.  
My system:
A8N-32 SLI deluxe
AMD 64 4200+ X2 (manchester, socket 939)
Single nvidia 7800GT
19" Viewsonic LCD

Anyone?  Anyone?

---

### Post by NeilBlanchard on 2007-03-25
Greetings,

I'm a noob myself, and I had slightly different issues that you are describing with a dual 7600GS display -- installing the nVidia Linux driver solved it for me.  (The display anomolies that is, the dual screens is another issue...)

[http://www.nvidia.com/content/drivers/drivers.asp]("http://www.nvidia.com/content/drivers/drivers.asp")
[http://www.nvidia.com/object/linux_display_amd64_1.0-9755.html]("http://www.nvidia.com/object/linux_display_amd64_1.0-9755.html")

---

### Post by nidoh on 2007-03-29
I too have the same problem! (BTW installing the system is impossible so telling us how to install a driver after its installed is not helpfull)

It would appear from the various posts all over the net that this is quite a big issue!

Things I have tried and failed are:

a) 6.06 Live CD --- Screen All messed up
b) 6.07 Alt CD --- Screen after install messed up
c) 7.04 Live CD --- Screen All messed up
d) 7.04 Alt CD --- Install just hung (not sure its related to this problem though)

I tried both 32bit and 64bit versions of each (I have few blanks left) 

What the hell is going on? I am using a nforce MoBo and AMD dual core 64bit CPU.

 As much as I hate to say this XP works great on this system. I used ubuntu on my old hardware with np. I am no *nix newbie, but this is just odd.

Please help, I really really dont want my XP freak friends to laugh at me


Thanks

Nids
PS I just spent hour going through the forums, so posting last resort

---

