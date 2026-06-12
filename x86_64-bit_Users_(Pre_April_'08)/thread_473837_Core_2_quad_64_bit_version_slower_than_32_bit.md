---
title: "Core 2 quad 64 bit version slower than 32 bit"
date: 2007-06-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by pixel34 on 2007-06-14
When I install the 64 bit version of Feisty ubuntu on my new

core2 quad 2.4 ghz
MSI P6N motherboard
4 gigs ram
500 gigs HD, Western DIgital SE16
Biostar Geforce 6200

It is painfully slow. I am talking about an install process that literally takes 30+ hours!

Then when I try to install 32 bit version of Feisty on my machines (I have 6 of them I need to set up for my research group) It takes the 30-45 minutes you would expect.

Is this a problem with the linux kernel and quad core2 computers?

Does someone else have a similar experience and/or solution?

I only have 4 gigs of RAM so I guess I don't really need the 64-bit edition. It would be nice to install it now though so that in the future I can expand to 8 gigs without having to reinstall the OS.

Thanks in advance for any help!

---

### Post by ansicplusplus on 2007-06-14
Dear pixel34,

I don't think it's a general problem with core 2 quad. My system (Feisyt x64, core 2 quad 2.4, 2G Ram, MSI P965 Platinum) is fast as hell. 

You should check your bios settings, although i can't put a finger on a special option. Maybe a bios update does the trick. Not all boards supported core 2 quad without difficulties when i looked 2 month ago.

Yours,
ansicplusplus

---

### Post by pentax on 2007-06-14
You have something else going on here, on my AMD 3800X2 w/ 2gigs of ram the installation of Ubuntu 64 only took around 30 minutes- faster than installing XP.

---

### Post by downhillgames on 2007-06-14
on many motherboard bios/cmos options (especially MSI, in my experience anyway) there are a few options that are specific to what OS you are booting to and what bit (32 or 64). Like the other person said, dunno what to tell you to change but go through and read a bit... prolly some bios setting...

30+hrs isn't a problem with the support of your cpu. sorry to hear that tho, heh... you were prolly ripping your hair out.

---

### Post by pixel34 on 2007-06-14
I don't know if it makes sense for the problem to be a mobo issue if it runs fine in 32 bit mode. This really seems like a software issue.

---

### Post by pixel34 on 2007-06-14
I just installed Fedora Core 7. It runs like a charm on it.

---

### Post by Kilz on 2007-06-14
> **pixel34 said:**
> I don't know if it makes sense for the problem to be a mobo issue if it runs fine in 32 bit mode. This really seems like a software issue.

Lets look at it this way 

machines taking 30 hours to install = your hardware that you built

Machines taking 30 minutes to install = everyone else

Both sets are using the same software. 
Where do you think the problem might lie?

---

### Post by tgm4883 on 2007-06-14
> **Kilz said:**
> Lets look at it this way 

machines taking 30 hours to install = your hardware that you built

Machines taking 30 minutes to install = everyone else

Both sets are using the same software. 
Where do you think the problem might lie?

That is one of the best explanations that I have ever seen

---

### Post by muximus on 2007-06-14
may sound stupid.. but it could also be a media issue.. try burning a fresh cd for ur feisty 64 bit ... cant see any other reason really

---

### Post by dannyboy79 on 2007-06-14
> **Kilz said:**
> Lets look at it this way 

machines taking 30 hours to install = your hardware that you built

Machines taking 30 minutes to install = everyone else

Both sets are using the same software. 
Where do you think the problem might lie?

well said. I am going to say that he should review the installer log to see what it was hanging on. I am guessing it was the reading of the media.

---

### Post by pixel34 on 2007-06-14
I apologize for my hasty assessment of Fedora core7. It is also just as slow as ubuntu Feisty. Both using the 64 bit versions.

I really don't undersand what part of the hardware installation it could be.
I tried a new videocard that works in another 64-bit ubuntu environment.
I have tried disabling ACPI, USB, onboard audio and lan.
I am not using any of the overclocking features.
There is no newer version of the bios.

I honestly don't understand how this can be a hardware issue. I have really tried to isolate every piece of the system and check if it is to blame.

I would appreciate specific advise instead of the blanket "It is your hardware that you built". That type of advise is kind of useless. Has anyone built with the core 2 quad? or the MSI P6N SLI Platinum mobo?

By the way, I have tried both cd install and installing from another harddrive. I prepare the hard drive by installing 2 partitions, One with grub and the other with the cd .ISO
I boot into the cd .iso and the install is still very slow. I doubt it is the media.

These machines respond like they are 486s not core 2 quads.

---

### Post by nss0000 on 2007-06-14
BigP:

Are you using a "from-the-factory" disk ( shipped by UBUNTU ) or a burn-it-yourself ( and pray ) disc ?

nss
****

---

### Post by John.Michael.Kane on 2007-06-14
Is the memory configured to run at it's proper speed be it dd2 667 or higher?

is the cpu being read properly by the bios?

Have you enable the proper MPS table version under your bios?

Also have you tried disabling HPET? 

You may want to also look at your PCI Latency Timer.

What kind of cd/dvd drive is in this machine? if your using a sata HD, and sata dvd/cd drive have you tried disabling the ide chip, and ide bus master under the bios.

Theres a lot of variables for the issues your having. 

Personally I would install only the peripherals needed to get the machine to boot, and i would also disable as many items as possible under the bios, and try doing a clean install.

---

### Post by incubus on 2007-06-14
Perhaps somebody could figure it out if you would post more information, such as dmesg, /proc/cpuinfo, lspci, etc.

Just out of curiosity, did you say you tried a 32bit OS on this computer as well?

incubus

---

### Post by pixel34 on 2007-06-15
> **SD-Plissken said:**
> Is the memory configured to run at it's proper speed be it dd2 667 or higher?

is the cpu being read properly by the bios?

Yes, as it comes up it identifies 4 cpu's and has the appropriate name for each.
> 
Have you enable the proper MPS table version under your bios?

I am using MPS 1.4, 1.1 is also available in the bios and I will try it.
> 
Also have you tried disabling HPET? 

I have, no effect.
> 
You may want to also look at your PCI Latency Timer.

It was initially set to 32. I have tried 64 and 192.
> 
What kind of cd/dvd drive is in this machine? if your using a sata HD, and sata dvd/cd drive have you tried disabling the ide chip, and ide bus master under the bios.

I am using an ide drive. It uses the Jmicron controller that used to have problems. I think those have been resolved. I have disabled the ide busmaster option.

Thanks for these new ideas. I will go and try them right now. 

I also think I will try the machines without the full 4 gigs of ram in them. maybe 2 gigs and see if that could be the problem.

thanks.

---

### Post by pixel34 on 2007-06-15
> **incubus said:**
> Perhaps somebody could figure it out if you would post more information, such as dmesg, /proc/cpuinfo, lspci, etc.

Just out of curiosity, did you say you tried a 32bit OS on this computer as well?

incubus

Yes actually the 32 bit version of ubuntu flies! 

I am going to try a few more things (poke at it) if these don't work I will post anything you recommend I post (dmesg, /proc/cpuinfo, lspci, etc). I dont want to waste your time if one of these other things solves the problem.

Thank you.

---

### Post by pixel34 on 2007-06-15
When I remove two sticks of ram the machine runs faster.  This must be a bios problem?

I will try to flash the bios. To do this I need to install windows first. MSI only supports a windows based procedure for updating the bios.

I appreciate the help and advise I have received here.

---

### Post by dannyboy79 on 2007-06-15
> **pixel34 said:**
> When I remove two sticks of ram the machine runs faster.  This must be a bios problem?

I will try to flash the bios. To do this I need to install windows first. MSI only supports a windows based procedure for updating the bios.

I appreciate the help and advise I have received here.

you don't need to install Windows to flash your bios. I just read their site, they are just telling you that you can't flash it when the bios is saved on the floppy! 

Just download and extract the new bios files within a place on your linux machine that you can access from the boot floppy is all. Then you would boot your Ubuntu machine to the floppy that they want you to, flash it using the correct location and bios file, and that's it! reboot, BOOM, touch actin tinactin. ha ha ha

Why has the world become so dependent on Winbloz???????????????????????

---

### Post by kyrhash on 2007-06-15
I disagree with the assessment that the j micron issues have been hammered out.  I have a brand new intel core 2 duo system and am experiencing some issues that i think may be related to yours.  I managed to get 7.04 installed but now it is unbearably slow at the boot process at points.  I have never waited the whole 30 hours but mine inches along at a pace that might take 30 hours.  My fix was to keep booting until i got lucky and hit a sweet spot.  it then boots in like 20 seconds.  I tricked my computer into working :p

---

### Post by pixel34 on 2007-06-18
After a updated the bios the machines work very well. One easy key to tell if this is the same problem for you is just taking out all but 2gigs of ram and booting. If it runs faster you need to update your bios to 1.2 (using the P6N SLI platinum board from MSI).

Thanks again all!

---

