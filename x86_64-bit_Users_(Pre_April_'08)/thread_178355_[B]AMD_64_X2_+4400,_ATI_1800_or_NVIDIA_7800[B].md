---
title: "[B]AMD 64 X2 +4400, ATI 1800 or NVIDIA 7800??[/B]"
date: 2006-05-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by steelspyder on 2006-05-17
I am building a new machine for use with multimedia (tv recording and digital imaging) as well as gaming machine.  I have wanted to dump Windows forever at home.  I have tested Ubuntu at work for some time now and I finally feel that it is ready for home use.  I finally feel that Ubuntu has matured enough that it should be an easy transformation for my wife (she doesn't deal with computers that much) that the interface is easy enough for her to pick up all she needs.

My question is.... I want to build an AMD 64 X2 4400 box but, I want to be sure that the components are compatable with Ubuntu.  So first, is there any issues with the 64 X2 procesors?  Second, would you reccomend the ATI 1800 or the NVIDIA 7800?  Also does Ubuntu support NVIDIA SLI and ATI CrossFire so that I can install 2 of either graphics card?

Thank you for your time.

---

### Post by Jason_25 on 2006-05-17
I know the processor will work but I don't know if there are specific issues with them.  Get the Nvidia.  Their drivers support SLI in linux.

---

### Post by tseliot on 2006-05-17
[QUOTE=steelspyder]My question is.... I want to build an AMD 64 X2 4400 box but, I want to be sure that the components are compatable with Ubuntu.  So first, is there any issues with the 64 X2 procesors?[/QUOTE]
No, there's no compatibility problem with the processor. 

In ubuntu Breezy you need to install the "smp" kernel to use all its power. 

In Ubuntu Dapper (which is bound to be released on June 1) the processor will work at its full power out of the box (the kernel has the support for "smp" enabled by default.

Make sure that the **motherboard** you buy is compatible with Linux. I think **THAT's** the choice you should more concerned about. Try asking here on the forums.

[QUOTE=steelspyder]Second, would you reccomend the ATI 1800 or the NVIDIA 7800?  Also does Ubuntu support NVIDIA SLI and ATI CrossFire so that I can install 2 of either graphics card?

Thank you for your time.[/QUOTE]
I can recommend you Nvidia cards in general. I can't assure you that a SLI configuration will give you a performance boost (some users told me that).

---

### Post by turbojugend_gr on 2006-05-19
Hi, I am very happy to help with that...
I have an AMD 4400 X2 for nearly 9 months now and it is working great on Linux (In SuSE there's absolutely no trouble, but for the past 2 months I am using ubuntu and the only thing needed is to download the SMP kernel from Synaptic, really easy one).
When I bought the PC I had an X800GT ATI gpu but it sucked under Linux (and Windows by the way). I sold it and bought an nVidia 7800GTX it rocks and especially on Linux it is Years ahead!!!! Let alone the Fact SLI is supperted (though I only use 1 gpu I found out that).
As for tha Mainboard I use Asus A8N-SLI and have absolutely no issue on anything.... ethernet,sound.graphics,RAM all work gracefully, try that one.

Any question is welcomed, I used this system for about 9 months now and thus I gained enough experience on it...

---

### Post by steelspyder on 2006-05-23
Thanks turbojugend_gr... I plan on putting a system together sometime this next month.  If I have any issues I will be sure to ask at the Forums.

Thanks all for your recommendations.

---

### Post by radinator on 2006-05-23
I've got the AMD64 4400 X2 with the 7800 graphics card, and while things are up and running now there were a few days of frustration getting it set up (which this board helped a lot).

When I tried the Breezy live CD, it would start up and then go to a corrupted login screen.  I've still not figured that one out, and could never break it out of that, even to get to a console login without X.

When I decided to plunge in and installed Breezy, I had a similar problem in that X would fail starting up. However, with the installation I was able to get to a console login and start working to properly install the nvidia drivers.  I still don't know if I have it all working (GL especially), but it looks good and for now I an tweaking other issues (like getting the latest thunderbird to work).  I'll probably get it all sorted out by the time Dapper is released. ;)

In any case it's been quite a learning experience getting the networking and other things to work.  For example, I had no problem networking disks from my XP machine, but it took the longest time before I could access disks on my other linux machine.  Go figure.

---

### Post by Jason_25 on 2006-05-23
That's actually standard procedure for modern nvidia graphics cards with ubuntu.  Apparently the NV driver doesn't work, and has never worked for as long as I have used ubuntu.  No Nvidia graphics card I own or my friends own will work with the NV driver unless it's an ancient card.  I wonder if it would be best to just ship with the vesa driver, similar to how windows does it.

---

