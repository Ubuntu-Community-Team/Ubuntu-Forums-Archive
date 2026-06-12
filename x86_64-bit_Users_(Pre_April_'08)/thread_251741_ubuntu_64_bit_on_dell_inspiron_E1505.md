---
title: "ubuntu 64 bit on dell inspiron E1505"
date: 2006-09-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by jsvidyad on 2006-09-05
Hi!!!

     Does anyone have experience installing 64 bit ubuntu  on a dell inspiron E1505 with a core 2 duo processor (T7400). If you have experienced any problems, please let me know.

---

### Post by John.Michael.Kane on 2006-09-06
These cards are supported and are offered options on that laptop.
Intel® Graphics Media Accelerator 950 
ATI MOBILITY RADEON 
NVIDIA® GeForce™Go 7300 TurboCache 

This wifi should be supported,and is also an offered option on that laptop.
Intel PRO/Wireless 

For the most part i don't think you will have any issues getting the machine up,and golden.

---

### Post by jsvidyad on 2006-09-06
Thank You

---

### Post by pdicresc on 2006-10-12
I've tried to install Ubuntu's 64-bit flavor of the 6.06.1 LTS platform on an E1505, also with the Core 2 Duo processor.  After some wrangling with the video driver (using ATI's proprietary) and the wireless card (NetworkManager works out of the box, and can be installed using Automatix2), I've come |--| that close to considering this a done deal.  

The remaining issues I've got are around:

i.  the built-in modem, which isn't recognized at all 
ii. the built-in card reader, which I haven't tried yet
iii. and the CPU performance / fan enabling.  

The last one is what scares me the most right now; although I can see both cores recognized in the System Monitor, the CPU monitor applet I've added to a menubar tells me that they're both consistently running at 1Ghz/50%, even when idle.  I haven't heard the fans go on at all.

The clock appears to be running at double-speed, counting up seconds and minutes much more rapidly.  

I've been finding posts on how Ubuntu users managed to fry the hell out of their motherboards because 6.06 didn't know how to handle the fans or the CPU stepping.  

I've tried to add apic, ACPI, and APM kernel options through GRUB to handle this, but I end up turning off my wireless or having no effect at all.  The one option I tried (I believe it was ACPI=OFF) managed to pin the clock to a proper second interval, but pegged the CPU at 2.0Ghz and killed my wireless again.

I've seen reports of an i8kutils package that's supposed to help in conjunction with gkrellm, but I don't see exactly why.

Can someone detail the extra steps I need to take in order to make this notebook ready to be a notebook?  How do I properly set up dynamic CPU scaling and fan management?

- Peter

---

### Post by John.Michael.Kane on 2006-10-12
Heres a thread on this machine. it may be of help.

[ubuntu-E1505]("http://ubuntuforums.org/showthread.php?t=190167&highlight=E1505")

[E1505-install_linux]("http://home.concepts.nl/~bergmans/linux/install_linux.html")

---

### Post by siersmak on 2006-10-12
I used this HOWTO as a guide and have had good success with everything I need: [http://www.ubuntuforums.org/showthread.php?t=257684&highlight=dell+inspiron+6400](http://www.ubuntuforums.org/showthread.php?t=257684&highlight=dell+inspiron+6400)

That includes SMP (make sure you install the smp kernel), the IPW3945 wireless card (worked out of the box, definitely worth the extra $30 or so), 1680x1050 resolution with 3D and hibernation.  I don't care about the modem or the MMC reader.

I was able to get my system clock to settle down by passing "no_timer_check notsc" to the kernel at boot, which doesn't prevent ACPI from running.  

I too was concerned about the CPU temps on this machine after reading all the threads about heat and the necessity to install i8kutils.  Turns out that i8kutils  is not available on x86_64.  i8kutils depends on the i8k kernel module, which doesn't appear as an option in a 64-bit kernel.  It is true that many have reported heat problems, but my CPU temps idle around 40 deg C, then with minor activity the temps increase to 60 deg C before the fan(s?) kick on.  I am running two CPU intensive applications right now, and the fans are running at apparently full speed and keeping the temps between 61 and 63 deg C.  On occasion, I'll see the temps go over 70, but they come back down very quickly.  I'm not an expert, but I don't think these temperatures are too high.  I just bought my laptop at the end of September, so we'll see.

It's a nice machine, I'm quite happy with it.  Give 64-bit a shot and come back here with any problems you encounter.
-Ken

---

### Post by mattyj on 2006-10-13
Siersmak,

Those temps don't look so different than alot of laptops.  Maybe the BIOS that comes with the Core2duos plays a little better with ubuntu.  

Have you heard anymore about i8k on 64 bit?   Any other issues with the machine?   It looks likes everything installs well.

MJ

---

### Post by siersmak on 2006-10-13
I agree Ubuntu and the BIOS seem to have worked out their issues.

Everything that I need is working pretty well.  I love the networkmanager applet and how well it works with the IPW3945 wireless card.  Every now and then ( once every other day maybe? ) Gnome will lock itself up, where I can move the mouse around but the desktop doesn't change and I can't type anything.  Switching to console mode and then back to X windows (Ctrl-Alt-F2 then Ctrl-Alt-F7) seems to clear it up usually. That's better than when I first installed, I would have to kill X windows all together with a Ctrl-Alt-Backspace when this would happen.  It's not a huge issue so I haven't pursued fixing it.

Edit: Oh, and no I haven't heard anything more about i8k on 64-bit.  I tried to contact the developer but haven't received a response.  I wonder if the kernel module is in the process of being ported but I'm not sure who to contact for that information.

-Ken

---

### Post by mattyj on 2006-10-13
Thank You.

I contacted one of the original debian developers on i8k based on this site:

[http://people.debian.org/~dz/i8k/00-README](http://people.debian.org/~dz/i8k/00-README)

This was his reply...

Unfortunately I don't have a 64bit Dell laptop for testing, so I can't help
about this. It is possible that the 32bit bios interface works also in 64bit
mode but I can't verify it. If anybody with a 64bit laptop could do some
tests with my (dangerous) smm program I could have some hints for modifying
the driver.

--
Massimo Dal Zotto

To which I replied the kernel does't support it.  I think as the Core2duo laptops increase in prevalence it will be easier.  

Has anyone tried it with Windows?  Do the fans kick in at the same thresholds?

---

### Post by mattyj on 2006-10-14
So just to make sure I understand the SMP kernel takes care of the speedstep issue described above.  Mine is coming soon and I am hoping to get it dialed in the first time.

Do your processors go to ~ zero at idle with the SMP kernel?

MJ

---

### Post by mattyj on 2006-10-14
This review lists the temps in Windows as alot cooler(max in the 40s) than those listed before, maybe it still does need i8k...

[http://www.notebookreview.com/default.asp?newsID=3137&review=Inspiron+e1505+Core+2+Duo](http://www.notebookreview.com/default.asp?newsID=3137&review=Inspiron+e1505+Core+2+Duo)

---

### Post by mattyj on 2006-10-14
A couple more questions: 

1.  What are you using to report temps if you are not using modules related to i8k?
2.  Can you be more specific on how you got ubuntu to load (passing command to kernel), I am not sure how to do that...
3.  These are the intel spec sheets for the Core2 duo laptops, seems like they do OK up to 100C, although I guess the heat could hurt other components...

[http://processorfinder.intel.com/details.aspx?sSpec=SL9SF](http://processorfinder.intel.com/details.aspx?sSpec=SL9SF)
[http://processorfinder.intel.com/List.aspx?ProcFam=2643&sSpec=&OrdCode=](http://processorfinder.intel.com/List.aspx?ProcFam=2643&sSpec=&OrdCode=)

Thank you for all the help...

---

### Post by siersmak on 2006-10-16
1. Install sensors-applet with Synaptic, then add Hardware Sensors Monitor to your panel.
2. One example of how to do this is here:  [http://www.ubuntuforums.org/showthread.php?t=260637&highlight=boot+options](http://www.ubuntuforums.org/showthread.php?t=260637&highlight=boot+options)
3. Not sure.

-Ken

---

### Post by agentstewie on 2006-10-22
hmm i seem to still have issues with the ati graphics loading on the 64-bit ubuntu...

Dell Insprion E1505
Intel Core 2 Duo T5500
ATI Mobility Radeon X1300
Ubuntu Drapper Drake 6.06 64-bit

---

### Post by siersmak on 2006-10-22
Details?  Worked fine for me, when following the howto at [http://www.ubuntuforums.org/showthread.php?t=257684&highlight=inspiron+6400](http://www.ubuntuforums.org/showthread.php?t=257684&highlight=inspiron+6400)

---

### Post by agentstewie on 2006-10-22
> **siersmak said:**
> Details?  Worked fine for me, when following the howto at [http://www.ubuntuforums.org/showthread.php?t=257684&highlight=inspiron+6400](http://www.ubuntuforums.org/showthread.php?t=257684&highlight=inspiron+6400)
nvm, i just got it to work, following Method 2! @ this link
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by jsvidyad on 2006-10-25
Hi!!!



  Did the ethernet card work out of the box for you guys??  It doen't for me. When i got the laptop, it already had 4 primary aprtitions. so, i erased the windows parttion, created a new extended partition to install ubuntu. I am not sure if the problem with the ethernet connections is because of that. But, the etehrnet card does work under windows. With ubuntu, it does not work. i am using network manager to connect to the network. If anyone has any suggestions, please do let me know

---

