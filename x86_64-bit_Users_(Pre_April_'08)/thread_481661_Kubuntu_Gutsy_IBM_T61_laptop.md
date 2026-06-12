---
title: "Kubuntu Gutsy IBM T61 laptop"
date: 2007-06-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by caryb on 2007-06-22
Hi, I take delivery of a new T61 laptop in a couple of days:) This will be my 1st leap into 64 land! Has anyone installed Ubuntu/Kubuntu on this hardware before? The processor is a Intel T7300 2Ghz with a Nvidea Graphics chipset. If someone could let me know of there experiences I would like to be armed before I start! The one pleasure will be to insert the live CD & blow away Vista:D


Cary

---

### Post by John.Michael.Kane on 2007-06-22
Looking over the specs i would say it's fully supported.

Can we have the specs of the one your getting?

---

### Post by caryb on 2007-06-22
Specs of my new toy lol 766415M
O/S:- Windows Vista (life expectancy 30ms) I will be putting Kubuntu Gutsy on (some of you might say just as      bad as Vista but unfortunately there is no finger emicon) 
Network:- Ethernet intel pro/1000, wireless Intel pro/3945AGB, bluetooth 
Processor:- Intel core 2 Duo T7300 2Ghz
Ram:- 4Gb (might be enough) lol
Chipset:- PM965 mobile
Video:- nvidia Quadro NVS 140M
HDD: 120Gb SATA
& IBM HDD shockproof stuff & fingerprint reader (these I guess will be the challenge) 
Can't find the audio chipset!

Cary

---

### Post by John.Michael.Kane on 2007-06-22
You should be perfectly fine. read here [http://www.thinkwiki.org/wiki/Installation_instructions_for_the_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installation_instructions_for_the_ThinkPad_T61)

Hope that helps.

---

### Post by caryb on 2007-06-26
Well I got the laptop, Vista is a pig! how slow is that? as for Kubuntu 64 It will not load past the main menu, as soon as I say install or safe graphics mode it dies & nothing but black screen:( The cd rom runs for about 15 secs then absolutely nothing! I can get fiesty 32 bit to run in safe graphics mode off the live cd!


Cary

---

### Post by caryb on 2007-06-26
Is sort of working in VGA mode will have to find out how to install the Nvidea driver! on 1 post it says that you have to install the prop version & reinstall after every kernel upgrade:-(






Cary

---

### Post by robrmd9 on 2007-06-26
What's wrong with the generic kernel?  Don't you want to use both cores of your CPU?

---

### Post by caryb on 2007-06-26
I removed the post after looking a bit closer it is generic 64bit I thought it was 32bit & was a bit pinged off!


Cary

---

### Post by John.Michael.Kane on 2007-06-26
This should help get you going. [http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_%28Feisty_Fawn%29_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_%28Feisty_Fawn%29_on_a_ThinkPad_T61)

---

### Post by caryb on 2007-06-26
I thought ATI was bad! I now have no video unless I boot into safe mode! I cant even Ctrl + alt F2 etc to get to a terminal from the 2.6.22.6 kernel boot! I tried the old dpkg xorg rebuild but gives me the same! at this point I can either rebuild & keep the vesa (very ugly) or Vista (even more ugly & slow) or resign myself to cli & lynx! Is there another 64 bit distro without the anal "open source" rules for drivers out there? It would be ashame to leave Kubuntu but I would rather another distro than Windows.



Cary

---

### Post by enderandrew on 2007-06-27
It really is a matter of the GPL.  When you distribute non-GPL code bundled with GPL code, people get a little upset.

Some distros have made it easy to install the non-free stuff right away.

Personally, Gentoo makes it pretty easy if you ask me.  Just put nvidia, mp3, wincodecs in your USE flags and install as per usual.

---

### Post by gladiac on 2007-06-27
There is a problem with the t61 when it comes to audio support. it has the ad1984 chip which is currently unsupported in alsa 1.0.14. There are already patches in the dev-tree though. Can I assume that that chip will be supported by gutsy when it gets stable? 2.6.22 is the chosen kernel as far as I know which will have alsa 1.0.14 so ubuntu will have to patch for itselfs... What do you think, will it be available or will I have to do it myself?

---

### Post by caryb on 2007-06-27
Does anyone know how to install the "gpl'd" open source version of Nvidia video driver for this beast! I don't need the run around using the proprietary version & breaking it for the 3rd time:(



Cary

---

### Post by gladiac on 2007-06-27
> **caryb said:**
> Does anyone know how to install the "gpl'd" open source version of Nvidia video driver for this beast! I don't need the run around using the proprietary version & breaking it for the 3rd time:(



Cary

The opensource-version is incompatible as far as I know. You will have to use the driver from nvidia.com because they added support for the quadro nvs140m in 100.14.09. 100.14.11 is the current version. You will have to install the linux-headers to make it compile (of course).
cheers

---

### Post by John.Michael.Kane on 2007-06-27
Have look over these.
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

[http://www.nvidia.com/object/linux_display_ia32_100.14.09.html](http://www.nvidia.com/object/linux_display_ia32_100.14.09.html)

[http://ubuntuforums.org/showthread.php?p=2911227](http://ubuntuforums.org/showthread.php?p=2911227)

---

### Post by gladiac on 2007-06-27
> **SD-Plissken said:**
> Have look over these.
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

[http://www.nvidia.com/object/linux_display_ia32_100.14.09.html](http://www.nvidia.com/object/linux_display_ia32_100.14.09.html)

[http://ubuntuforums.org/showthread.php?p=2911227](http://ubuntuforums.org/showthread.php?p=2911227)

A newer version of the nvidia-module is available here:
[http://www.nvidia.com/object/linux_display_ia32_100.14.11.html]("http://www.nvidia.com/object/linux_display_ia32_100.14.11.html")

---

### Post by caryb on 2007-06-29
I have perfect 2D video now Beryl & Compiz have major issues:( I have Frostwire & all my favorite apps installed & working perfectly, my next hurdle is sound & flash! Oh well back to faithful Google!


Cary

---

### Post by caryb on 2007-06-29
Well life is full of trials & tribulations:) I compiled & installed alsa (latest version can't tell you the release) & killed Xorg! I guess I have 2 options 1) no sound & video 2) no sound but video! I like my gui too much so I guess I'll wait for sound in *buntu updates!


Cary

Addendum! I just did a apt-get update & upgrade with the new alsa app & it killed my video again! It seems anything that probes the kernel stuffs up my running kernel. Is there a way to make the Nvidia patch stick?


Cary

---

### Post by caryb on 2007-07-10
I just installed Feisty on a friends identical laptop (we both bought together in bulk) it has the Kubuntu splash screen etc! This must be a idiosyncrasy of Gutsy! I checked & my Gutsy machine has ksplash enabled & also on the Feisty machine I can break out to ctl + F2 etc to a terminal while on Gutsy there is no display! I have checked the bios & both have the same revision & settings! Is gutsy broken at present for Nvivia cards?


Cary

---

### Post by frustschieber on 2008-06-25
I use Hardy 32 bit and found almust everything running immediately. no problems with video wlan suspend.
64 bit is not recommended

---

