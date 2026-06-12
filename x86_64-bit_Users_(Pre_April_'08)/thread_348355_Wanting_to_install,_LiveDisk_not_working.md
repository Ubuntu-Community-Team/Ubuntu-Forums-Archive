---
title: "Wanting to install, LiveDisk not working"
date: 2007-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by bender324 on 2007-01-28
Hi, 
I'm a current user of Debian Linux (self-admitted newbie) and wanting to give Ubuntu a whirl.  I downloaded the ISO image for 6.10 Desktop and am trying to run it - I understand that the install can be initiated from the live disk once Ubuntu's up & running in it.  When I select option 1 from the boot, I get the loading screen, but when it attempts to load the desktop, things get a little weird.  I see the background color ( a light brown color) and the splash screen comes up, but the splash screen is very garbled (pixels are off and scrambled).  Sometimes the splash screen goes away, sometimes it doesn't.  In either case, I'm left with a blank desktop and am only able to move my mouse.  I believe the keyboard is not responding, as even the numlock key fails to light the LED, and I'm unable to switch to another shell/desktop (ctl+alt+f#).  Is there anything else I can try?  I tried loading from safe graphics mode, but it worked the exact same way.  Here are my system specs:
CPU - AMD X2 3800+ (dual core, 64-bit)
1 GB of Ram
Asus A8N5X motherboard & using onboard sound
GeForce 7800.
Using dual boot with a separate hard drive running Win XP

As I said, I currently run Debian Sarge on the machine.  I'm using a 2.6.11 kernel to support the sound drivers, and using Nvidia's Linux graphics drivers.  However, it worked on the vanilla sarge install without anything really weird, other than no sound.  I'm using the 32-bit Ubuntu ISO - I assume that shouldn't matter as the 64-bit processor should be backwards-compatible and the Debian is also 32-bit - let me know if that could be a problem please.  

Please advise if there is something I need to be doing differently here, such as if I'm using the wron gLiveDisk, etc.  I'm hoping Ubuntu will be able to work with my system.  Thanks in advance!

---

### Post by sizzlor on 2007-01-28
> **bender324 said:**
> (...) I'm using the 32-bit Ubuntu ISO (...)
Please advise if there is something I need to be doing differently here, such as if I'm using the wron gLiveDisk, etc.  I'm hoping Ubuntu will be able to work with my system.  Thanks in advance!

hi there, 

from what i know you've gotta use a 64-bit-specific disc image if you want to be sure that it'll run on an AMD 64-bit system, i.e. an ISO file like [**ubuntu-6.10-desktop-amd64.iso**]("http://releases.ubuntu.com/6.10/ubuntu-6.10-desktop-amd64.iso.torrent") (this is also a bootable 'live' CD of course).  

it's what worked for me -- hope it helps.

---

### Post by kuja on 2007-01-28
You don't have to. You can use the i386 disk, but why on earth would someone buy 64-bit hardware just to use a 32-bit os?

---

### Post by neekap on 2007-01-29
> **kuja said:**
> You don't have to. You can use the i386 disk, but why on earth would someone buy 64-bit hardware just to use a 32-bit os?

certain software may not work correctly under the 64-bit version, the 32-bit version is perfectly acceptable and many people prefer it until the 64-bit OS matures

---

### Post by Kilz on 2007-01-29
> **neekap said:**
> certain software may not work correctly under the 64-bit version, the 32-bit version is perfectly acceptable and many people prefer it until the 64-bit OS matures

Pure FUD. The total package difference between 64 and 32 bit is 1%. Taking into account merged packages, old software no longer needed. and software not needed on a platform it is less than 1%. Now take into account that the 64bit OS can run 32bit applications. 
Like I said pure FUD.
Exactly are you waiting on to "mature"? What version are you running?

---

### Post by bender324 on 2007-01-29
I have/wanted a 64-bit CPU because I was under the impression that 64-bit OS's and programs were drastically faster, etc.  I was later told (correct me if I'm wrong), that the only real difference in speed is if you have over some insane amount of RAM (8 gb's or something) and most applications that support 64 do so only for bare functionality and don't take advantage of much of the 64-bit instruction sets, etc., so there is really little benefit there.  Additionally, I found out the hard way that (at least at the time), not much supported 64-bit OS's.  Forgive me for mentioning the W word on this forum, but Windows XP 64 was garbage.  Even with its "WOW" 32-bit application emulator, all drivers and most more "kernel-level" applications (such as anti-virus) did not work, and no vendors would touch patches or new drivers for it.  
I didn't have much luck with the 64-bit version of Debian, either.  Ralink didn't make the drivers for my wireless NIC at the time for Linux and the Windows drivers were also just 32-bit, so no NDISWrapper.  Nvidia also didn't make the Linux drivers for their cards.  There were also some other complications which I fail to recall at the moment.  Long story short, I failed to see the benefit for all of the hassle for going 64, and 32 worked just fine.

Now disclaimer - my last attempts to get Debian working on 64 were probably 9 months ago, so if the availability of supporting apps & drivers has increased dramatically, please correct me.  Additionally, I'm very much a casual hobbyist with all this (definition - permanent newbie), so if anything else I've said above is completely incoherent and/or wrong, please (kindly) correct me - I'll appreciate it.

Now back onto my subject - I didn't have any further luck with the 64-bit Edgy disk.  Same exact results (scrambled pixels, froze before loading).  I'll give DD a try next.  Thanks to everyone for their help/suggestions/thoughts!

---

### Post by AllenGG on 2007-01-29
:cool::cool:Hmm, wonder if we've lost Bender forever, guess so .
For the last 2 years I've been running Ubuntu on my AMD64 machine, successfully. YES, there are some problems (buzzword= issues) Flash on Firefox etc. But faster yes, much. Install requires AMD64 alternate CD , updates: yes there were some problems, quickly overcome.
Was it worth it? YES, is instant fast enough ? And Bender , if you read this and want help use the message feature and I'll walk you through it, SKYPE anyone ?
Allen  aka olsneezy on SKYPE:D

---

### Post by bender324 on 2007-01-29
No luck with Dapper Drake either (only tried 32-bit, but I think we've agreed it shouldn't matter).  PC completely hangs when I attempt to run the Live CD, right after I all of the messages complete and X tries to load (I see the X screen and the Ubuntu splash, but it's scrambled and is completely unresponsive).  A quick search on 7800 (for my graphics card) suggests other people have problems with Ubuntu and this card.  
Any final suggestions before I completely give up hope (or if you'd prefer I move this to another forum since it doesn't seem to pertain to 64 OS anymore, I'll gladly do so).  Thanks!

---

### Post by kuja on 2007-01-30
bender324, you might have better luck with the proprietary nvidia drivers, if you haven't tried them already. 

First enable the multiverse repository in  your /etc/apt/sources.list
Then run "sudo aptitude install nvidia-glx && sudo nvidia-glx-config".

---

### Post by bender324 on 2007-01-30
Sorry if this is a dumb question, but how do I get there?  I currently can't get the live disk to load up, even in safe graphics mode, so I never get a chance to get a shell prompt or anything.  Are there other ways I can install so I can get to a shell prompt?  Thank you.

---

### Post by kuja on 2007-01-30
bender324, you'll need to use the alternate install disk.

---

### Post by bender324 on 2007-01-30
Thank you!

I downloaded the alt install 32-bit Edgey.  After trying to install, found out (the hard way) that the download/disk was corrupted.  Saw this as a sign to take everyone's advice and go with 64-bit.  Installed without any problems.  As expected, kept seeing the same video problem.  Rebooted into command-prompt only/recovery mode, and as you said ran sudo aptitude install nvidia-glx && sudo nvidia-glx-config enable.  Hit an error on the nvidia-glx-config at first, had to run modprobe -i nvidia, ran config again, rebooted, all is now well and I'm typing this into my shiney new AMD-64 Edgey system!  
Thanks, everyone, and I apologize as this probably should have been in the new users section.

---

### Post by kuja on 2007-01-30
bender, I disagree, this was probably the right place to post. Had you posted in the beginner section you would have been given a load of FUD telling you to not use the 64-bit version and you'd be running 32-bit right now.

---

### Post by 1doeish1 on 2007-02-10
> **bender324 said:**
> Thank you!

I downloaded the alt install 32-bit Edgey.  After trying to install, found out (the hard way) that the download/disk was corrupted.  Saw this as a sign to take everyone's advice and go with 64-bit.  Installed without any problems.  As expected, kept seeing the same video problem.  Rebooted into command-prompt only/recovery mode, and as you said ran sudo aptitude install nvidia-glx && sudo nvidia-glx-config enable.  Hit an error on the nvidia-glx-config at first, had to run modprobe -i nvidia, ran config again, rebooted, all is now well and I'm typing this into my shiney new AMD-64 Edgey system!  
Thanks, everyone, and I apologize as this probably should have been in the new users section.


Congrats on your new system and your help! I too have a ASUS A8N5X Mainboard, but running with an AMD Opteron 146 processor. I have installed the 64-bit alternate Kubuntu because of the vary same problems you had encountered. Now I am unsure of the commands and the process that got you through this. I also have the Kubuntu desktop 64-bit disk burned, both are 6.10 edgy. I'm hoping you could post a bit more precisely the commands and the order in which you performed them. I am very new to Linux and Ubuntu so bare with me. Thanx so much for posting, I'm sure I am not the only person you have helped by doing so.
Much appreciation

---

### Post by bender324 on 2007-02-10
Hi,
Are you seeing the same problems as I was (system crashing upon the x-system loading)?  I assumed my problem was with my video card, not the motherboard, but I can't say for sure (I'm also inexperienced with Linux).

Anyway, I'll walk through what I did assuming you got the alternate disk install, you just can't boot into normal mode.  When you boot up, you should be prompted for what systems you want to boot into, and one of your choices should be in recovery mode.  You'll want to boot into that as it will not attempt to load up the x-server/KDE.  Log in at the command prompt & your first step is to enable the multiverse repository by editing the /etc/apt/sources.list ... I used vim as the text editor.
*sudo vim /etc/apt/sources.list*

In the file, uncomment the lines by deleting the # - these were lines 32 & 33 for me but you'll want to double-check:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

Save the file and return to the command prompt.   Next you'll want to install the nvidia-glx package (you'll need a network connection for this)

*sudo aptitude install nvidia-glx*

I had to insert the Edgy cd-rom to load a dependency - you may or may not have to. Anyway, let the package install, and run the config by
[I]
sudo nvidia-glx-config enable[/I]

If you hit an error on this (I did), first load the nvidia module into the kernel:
[I]
sudo modprobe -i nvidia[/I]

and then run the nvidia-glx-config enable again.  Finally, reboot (*sudo shutdown -r now*) into normal mode.  This is what I did to fix my problem - what video card are you using?  Anyway, like I said I'm very inexperienced with Linux so I hope this helps, please let us know!

---

### Post by 1doeish1 on 2007-02-10
Thank you so much for getting to this so soon.:)   I have an ATI Radeon x850xt.
(I bought this for a good price for my boyfriend, the computer included the vid card.) 
While I went through the HCL I did not find this main board, but similar ones as well as the video card both had problems loading the X-Server. Apparently it is the ATI driver. So that is one problem. The other is the main board may require the "noaapic" & "nolapic" boot parameters at the beginning of the install.
I believe that between your situation and this added knowledge I will be able to boot the system with Kubuntu 64-bit by the end of the night! I will let you know.
Any more insight is greatfully appreciated, and thanx.

---

### Post by curts on 2007-02-10
I too have had problems with the 6.10 Ubuntu distro for 64-bit AMD.  I downloaded the ubuntu-6.10-desktop-amd64.iso distro using bittorrent when it first became available, but I didn't get a chance to try it out until January.  The live disc would not load properly on my system as described here previously.  I tried dumbing down the startup with more compatible kernel and lower resolution video choices, but to no avail.  I even re-burned the CDROM and verified there were no errors in the burn.

My system consists of an AMD 64 4000+, VIA K8T890 north bridge, 1 GB dual-port RAM, and NVIDIA 6800 GS video.

The failure of the 6.10 live CD was disappointing, because I have been running with the ubuntu-6.06-desktop-amd64.iso distro without a problem (as a matter of fact, I am using it to post this).  At this point, though, I think I'll just wait for the 7.04 distro.

Curt

---

