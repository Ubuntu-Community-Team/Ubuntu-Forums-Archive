---
title: "My Motherboard is dead after... Ubuntu installation??"
date: 2007-01-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Pelefon on 2007-01-10
Helo there. 
I used myself Slackware and OpenBSD about 6 Years ago and now wanted to return and see how Linux progressed. I tried to install the Ubuntu version 6.06 LTS for 64-bit. After partitioning, the installation began, and it was stuck on the 53%. The PC didnt respond anymore to anything so after waiting about ten minutes I pushed reset. I restarted my PC and because it was 2:30am I decided to continue another time (knowing that Linux problems sometimes can take it to the next day and beyond..) . I shut the PC as usual ( from winXP) and the next morning it didnt respond anymore. I couldnt turn it on. It did nothing at all when I pressed the button. So I opened the PC and noticed that when you take out the 4-PIN plug (next to the processor) the computer turns on but nothing happens (motherboard is dead). So i took it to service and after 4 weeeks they sent me brand new MB. They didnt tell me what was the problem...

I have Pentium D805 2.66 Ghz with ASUS Mainboard P5L 1394.

So is it possible that Ubuntu was the cause? The first time I tried to turn on the PC after the installation tryout (it was really stuck) it didnt funktion anymore.. But winXP worked fine after restart... I dont know exactly but maybe it is coincidence... Maybe it has something to do with compatibility with the new 64bit processors? The processor works fine until now but the MB is new and I dont feel like to try and install the 64bit Version of Ubuntu again.. Anyone read already about something like this?

---

### Post by meng on 2007-01-10
What motherboard is this? I know there are some Ubuntu compatibility problems with some motherboards, although I don't think this could explain why your motherboard **died**. If it halted during the install, that sounds even less likely that it would cause your problem. It may not even be related, installs often halt like that because the CD wasn't burned properly. But if it was related, it seems more likely to me that the motherboard dysfunction caused the Ubuntu installation to halt.

---

### Post by PilotJLR on 2007-01-10
I don't think Ubuntu (or any OS) could cause this damage. It's FAR more likely something in the motherboard failed, which is a possible explanation why the install froze as well.

---

### Post by ostvarivanje on 2007-01-12
I have an asus m2n-sli deluxe and I had some problems with usb devices when plugin off my computer freezed. My processor is amd athlon X2 64bit 3800+ and recently I had ubuntu edgy i386, but before I had installed amd64.
One day I wanted to connect my mobile phone (Nokia 6270) via usb. The computer freezed and I have no other chance than to reboot it. When pc is rebooting I saw a light in hard disk but nothing on the monitor. Again reboot and then after 5-7 seconds, itself shut down. Now I'm using brother's laptop with XP :( My motherboard don't work and must change it. 
Do you hear any of you something like that? Do you think that is possible Ubuntu caused this?
Is it better to use amd64 or i386 edgy? (I think better for my hardware)

I know, my english is too bad :)

---

### Post by Hub-1 on 2007-01-12
> **ostvarivanje said:**
> I have an asus m2n-sli deluxe and I had some problems with usb devices when plugin off my computer freezed. My processor is amd athlon X2 64bit 3800+ and recently I had ubuntu edgy i386, but before I had installed amd64.
One day I wanted to connect my mobile phone (Nokia 6270) via usb. The computer freezed and I have no other chance than to reboot it. When pc is rebooting I saw a light in hard disk but nothing on the monitor. Again reboot and then after 5-7 seconds, itself shut down. Now I'm using brother's laptop with XP :( My motherboard don't work and must change it. 
Do you hear any of you something like that? Do you think that is possible Ubuntu caused this?
Is it better to use amd64 or i386 edgy? (I think better for my hardware)

I know, my english is too bad :)

The Asus M2N-SLI deluxe is a new first generation AM2 socket Motherboard. The BIOS provided with it is very basic, most likely the version 201. It caused a lot of problems with incompatible RAM and buggy BIOS. With the 201 BIOS, the board is VERY picky on Ram and most likely causes problems with Ram not on the (QVL-Qualified Vendors List). It is highly recommended to upgrade to a up to date version which by now is probably 702, it supports a wide range of new ram and cpu's. If you don't have windows, use the freedos livecd to upgrade to a new BIOS. It is not likely ubuntu related.

---

### Post by Lord Illidan on 2007-01-12
I fail to see any connection between using Linux and damaging a motherboard. Please stop regarding Linux as an amateur operating system which can damage your computer if you use it incorrectly. It is very powerful, true, but it is not a system wrecker. Quite the contrary.

---

### Post by Jongi on 2007-01-12
So the last OS to interact with the system was XP yet you blame Ubuntu?

But to answer the question, no OS (as far as I know) is capable of causing hardware damage. In fact, your problem could be something as simple as a PSU failure.

---

### Post by kullan&#305;c&#305; on 2007-01-12
In the present i'm telling you about my beryl project at school. Given the reactions of people who have seen the beryl movie, i'm betting that showing them the real thing will even draw them in more. So before summer break i started installing ubuntu and beryl on a spare computer at school, i failed numerously. After the break i continued and after the first hour i worked on it, i had got beryl working. I felt so happy inside 8} I had used the nvidia-glx-legacy drivers because the video card was to old. And because i did that i needed to install XGL, eventualy i got beryl working. The next day (yesterday) i fixed the theming and it looks pretty! Here are some of the compy's specs
look:
[www.unreadedpost.com](www.unreadedpost.com)

---

### Post by ostvarivanje on 2007-01-12
> **Hub-1 said:**
> The Asus M2N-SLI deluxe is a new first generation AM2 socket Motherboard. The BIOS provided with it is very basic, most likely the version 201. It caused a lot of problems with incompatible RAM and buggy BIOS. With the 201 BIOS, the board is VERY picky on Ram and most likely causes problems with Ram not on the (QVL-Qualified Vendors List). It is highly recommended to upgrade to a up to date version which by now is probably 702, it supports a wide range of new ram and cpu's. If you don't have windows, use the freedos livecd to upgrade to a new BIOS. It is not likely ubuntu related.
Thank you very much for your answer and very important information for me. 
But, because I don't know very much things about hardware, what do you recommend me to do with this. Do you think that it's better to change motherboard because I'll put the same. If yes, what motherboard do you think. Or to change memory? 
For now, I don't have here my computer. When it arrives to me with new motherboard I'll upgrade, but if you want and have time, tell me about freedos livecd and give me a link. Can I download this livecd? I don't have Windows and don't have a plan to install :) 
Please help me, because I think is very important this bios upgrade.
And, one more time, thank you for useful informations.
My system: 
hard disk: western digital 250gb wd2500yd 7200rpm sataII
Dvdrw: lg gsa-h20 multi-lightscribe dvd+/-r/rw
Dvd player: liteon shd-16p1s dvd-rom 16X bulk
Graphic: msi vga nx7600gt-t2d256e pci-e retail
Motherboard: asus m2n-sli deluxe
Ram: corsair xms2 ddr2 pc6400 (800mhz) dual channel
Processor: amd athlon 64 X2 3800+ 2.00gz am2 box
Power (I don't know in enlish how to write): tagan tg480-u01 480w dual fan black
Case: thermaltake mambo black

Because on Monday they will put a new one (same) motherbord, tell me if it's better to put other than this one.
I had problems freezing computer with usb and now I think I know who is guilty.
Tell me the best way  to do, please


Lord Illidan: If you write all these for me (or and for me) I want to tell you that when you have a problem, you are trying to explain what caused it. Because of this I wrote about Ubuntu.
I like very much Linux (especially Ubuntu) and imagine that after two months I have Linux, I don't want to come back to Windows. I am very impressed with this operating system.
And of course I didn't believe that there is a operating system to keep me to don't use Windows (I don't think that Windows is too very good, but if you have a car and you don't see any other, then you think that you have the better car in the world).

And especially thanks ubuntuforum for brilliant support.

---

### Post by Hub-1 on 2007-01-13
> **ostvarivanje said:**
> Thank you very much for your answer and very important information for me. 
But, because I don't know very much things about hardware, what do you recommend me to do with this. Do you think that it's better to change motherboard because I'll put the same. If yes, what motherboard do you think. Or to change memory? 
For now, I don't have here my computer. When it arrives to me with new motherboard I'll upgrade, but if you want and have time, tell me about freedos livecd and give me a link. Can I download this livecd? I don't have Windows and don't have a plan to install :) 
Please help me, because I think is very important this bios upgrade.
And, one more time, thank you for useful informations.
My system: 
hard disk: western digital 250gb wd2500yd 7200rpm sataII
Dvdrw: lg gsa-h20 multi-lightscribe dvd+/-r/rw
Dvd player: liteon shd-16p1s dvd-rom 16X bulk
Graphic: msi vga nx7600gt-t2d256e pci-e retail
Motherboard: asus m2n-sli deluxe
Ram: corsair xms2 ddr2 pc6400 (800mhz) dual channel
Processor: amd athlon 64 X2 3800+ 2.00gz am2 box
Power (I don't know in enlish how to write): tagan tg480-u01 480w dual fan black
Case: thermaltake mambo black

Because on Monday they will put a new one (same) motherbord, tell me if it's better to put other than this one.
I had problems freezing computer with usb and now I think I know who is guilty.
Tell me the best way  to do, please
.
The best solution to update your BIOS is to ask the people at your PC-repairshop to do it for you. They are experienced and should be able to do this without any problems, free of charge. If for some reason you didn't get them to update your BIOS, I can certainly help you. However, updating the BIOS is dangerous, as it can render your motherboard useless all over again if the process is interrupted. To check if your BIOS is up to date, press the '*Tab*' key after boot to get rid of the splash screen (you should now see the POST messages), then press the '*Pause/Break*' key to stop the boot process. Look for a line which includes "BIOS Revision". If the number is lower than 501, you should update to have a stable system.

---

### Post by ostvarivanje on 2007-01-13
> **Hub-1 said:**
> The best solution to update your BIOS is to ask the people at your PC-repairshop to do it for you. They are experienced and should be able to do this without any problems, free of charge. **If for some reason you didn't get them to update your BIOS, I can certainly help you.** However, updating the BIOS is dangerous, as it can render your motherboard useless all over again if the process is interrupted. To check if your BIOS is up to date, press the '*Tab*' key after boot to get rid of the splash screen (you should now see the POST messages), then press the '*Pause/Break*' key to stop the boot process. Look for a line which includes "BIOS Revision". If the number is lower than 501, you should update to have a stable system.
Thank you for your answer and especially thanks because you are willing to help me.
Right now I'm searching in Asus site and found that there is beta bios version 701 (or 702, I don't remember). 501 is like stable bios version;
First of all, on Monday I'll call to repairshop to update my bios to 501 version. If they don't accept this, then I must upgrade myself. In this case I'll needed your help about upgrading.
Do you have the same motherboard or just you know about this motherboard?

---

### Post by Hub-1 on 2007-01-13
> **ostvarivanje said:**
> Thank you for your answer and especially thanks because you are willing to help me.
Right now I'm searching in Asus site and found that there is beta bios version 701 (or 702, I don't remember). 501 is like stable bios version;
First of all, on Monday I'll call to repairshop to update my bios to 501 version. If they don't accept this, then I must upgrade myself. In this case I'll needed your help about upgrading.
Do you have the same motherboard or just you know about this motherboard?

The newest version is 702, look here: [Click ]("http://support.asus.com/download/download.aspx?SLanguage=en-us&model=M2N-SLI%20Deluxe&type=map&mapindex=1")

---

### Post by ostvarivanje on 2007-01-13
> **Hub-1 said:**
> The newest version is 702, look here: [Click ]("http://support.asus.com/download/download.aspx?SLanguage=en-us&model=M2N-SLI%20Deluxe&type=map&mapindex=1")
Because I decided to call PC-repairshop (on Monday) to update bios for me, do you think to tell them to upgrade to 702 version and not to 501? Is this a stable update version?

---

### Post by Hub-1 on 2007-01-13
> **ostvarivanje said:**
> Because I decided to call PC-repairshop (on Monday) to update bios for me, do you think to tell them to upgrade to 702 version and not to 501? Is this a stable update version?

Just tell them to upgrade to the newest version, they'll know which one. As for the 702, yes, this is the new stable version, not beta, check it out on the link I provided in my last post.

---

### Post by ostvarivanje on 2007-01-13
> **Hub-1 said:**
> Just tell them to upgrade to the newest version, they'll know which one. As for the 702, yes, this is the new stable version, not beta, check it out on the link I provided in my last post.

Ok, thank you one more time. When I have something new, I'll post you here.

---

