---
title: "OMG!Help!I can't stand it anymore!"
date: 2007-12-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by quasimodo69 on 2007-12-15
I am sorry..but I really can't stand it anymore!I have better things to do..a real job and people who need my help with their systems.
I started with Ubuntu back in October.It has been nothing but a nightmare.I have not been able to help my friends due to working constantly to get this Ubuntu to work.I get it running for a little while to answer my e-mails.It crashes before I can download what I want to run and work with..I mean a hard crash that requires me to turn off the power supply and re-start the system.And of course I lost what ever was downloading.I can not tell you how many hours..day crawling the help files for and answer and trying tons of things.
  I will continue my tail of woe..the long version if you care to read it with a system spec at the end....
I downloaded and installed 7.04..It worked ok.I upgraded to 7.10 and it started with the crashes.I rolled it back to 6.4...and the crashes continued.I wiped the hard drive cean and re-installed 7.10...and it crashed...over and over again.All of these crashes were black screen with warning buzzers...I had to shut off the power supply and re-engage it to start over.
  I re-downloaded the ISO for AMD64.I re-installed this..same thing.I changed my video card.I changed my settings.I did not installe the compiz...I did not engage the extra desktop effects.I did a minimal install.I did a minimal install with security updates.I re-downloaded he ISO and did a minimal install.I did this over and over with different combinations.All with e same result..until I finally gave up after2 and 1/2 months.
  I wiped my hard drive and installed 7.10 i386 version on my AMD 64 system..It was slower and I had some hangups.It went pretty good and I installed all the things I wanted to work with..I was looking for some programming stuff to get into that.I did the downloads.I started the desktop enhancements.The 1st re-start went OK..I thought I had the answer.I did an update..installed all it recommended.I did a restart..And then the doo doo hit the fan on restart!The screen had a mind of it's own.I had nothing but 640x?? for screen resolution..no way to get it better.I will have to admit I could get my sound working all the time (with the 64 bit ver my sound only worked 60% of the time..and I could not figure out why).I am contiplating building an AMD64x2 system and am wondering if Ishould wait for the next version?
 I am a newbie to this and need some guidance of ANY kind to get me through to a succesful running install that I do not have to spend 90% of my time maintaining...I just want to use it...not keep patching it or upgrading it...
thnx:mad:

System:AMD 64 Abit- AV8 MoBo w Via 800kt pro north and south bridge
realtek audio onboard and SB Live! PCI card-nVidia 5200 GFX video card-1 IDE 40GB hard drive with Ubuntu installed-4.8GB IDE hard drive blank-40GB SATA hard drive

---

### Post by DrMega on 2007-12-15
A couple of questions:

1. Do you have dual boot with another OS? If so how is that? Is it stable and fine?

2. If you boot from the LiveCD one of the options is to run a memory test. Have you tried this?

3. When you refer to a "hard crash", do you mean a full lockup, a spontaneous reboot or something else? I ask this because I had spontaneous full lockups on a previous setup and it turned out to be a compatibility issue with my aged video card.

---

### Post by Nebutron on 2007-12-15
Sorry you have had such trouble.  I am running 7.10 on an AMD 64 system with no trouble.  Also, my first experience with it. I have a couple of thoughts:

   1.  I wonder if you may be having a hardware issue that is really just coincidental to the timing of your install.  Memory instability can cause such problems.  What type of memory are you using?

   2.  I wonder also if you are using the restricted drivers from Nvidea?  If not, I would recommend installing them.  

I have been using Ubuntul for about 2.5 months now with no significant issues.  My mother in law has in on a machine I built for her and loves it too.  We are both using ASUS motherboards and Athlon 64 CPU's, one single and one dual core.  I am sure that once you figure this out, you will be amazed at what you can do with the system.

---

### Post by quasimodo69 on 2007-12-16
> **DrMega said:**
> A couple of questions:

1. Do you have dual boot with another OS? If so how is that? Is it stable and fine?

2. If you boot from the LiveCD one of the options is to run a memory test. Have you tried this?

3. When you refer to a "hard crash", do you mean a full lockup, a spontaneous reboot or something else? I ask this because I had spontaneous full lockups on a previous setup and it turned out to be a compatibility issue with my aged video card.
  
I have been runninh this computer for a year with Micr$oft and no problems.I ran Ubuntu 6.4 for 2 weeks and no problems.It started with 7.04 install and upgrade.I wiped everything and did a re-install.
What I mean by a crash-the screen would go black,the warning buzzers in the computer case would go off and I would have to power down the power supply in the case by turning of the switch in the back and then turning it back on.These crashes would occur after 1 hour...or 5 minutes.
 I was running a full install.I did not have this problem before.Now that I have 7.10 1386 running it works pretty good.I even have sound ALL the time..where as before I only had sound 60% of the time.
as for another poster..I run only Crucial memory.I ran the memory test and the CD test-all were fine.

---

### Post by BIGtrouble77 on 2007-12-17
If hardware warning buzzers are going off then it's most likely a hardware issue.  An OS should never trigger those internal warnings unless you're experimenting with overclocking or memory timings.  

You might want to install winxp and setup the most basic drivers.  I'd then snag something like 3dmark and  let it run over night.  If the app drops to desktop or freezes then you have to start targeting the hardware.  I would try each stick of ram individually (if you have more than 1), strip out all of the non essential cards and simply get the system to a barebone state to try and figure out the root of the instability.  Make sure you try another power supply too, if possible.

You should also reset the bios to the defaults (just to make sure memory timings and fsb are not out of whack).  I really don't think this is Ubuntu, other than suspend issues on my macbook, gutsy is very stable  on all of my machines and some are very similar to your desktop.

-bt

(btw, once your done testing in winxp don't forget to reinstall ubuntu :))

---

### Post by LoneWolfJack on 2007-12-17
I will have to agree that it is most likely a hardware issue.

I've been running Gutsy for several months with quite exotic (for the desktop) hardware, without any major problems.

If your beepers go off with a black screen the first thing that comes to mind is an overheating CPU. Also, despite of the memcheck you did there could still be something wrong with your RAM. As Linux will always try to max out your RAM, you may have a stick that's faulty. It may only show under Linux for the aforementioned reason due to overheating of the RAM stick.

My advice would be to keep an eye on the CPU temperature, if that's OK watch your RAM sticks. Also, it maybbe that your graphics card isn't properly secured in its slot or something. In fact, if your PC starts beeping, it's either for temperature, CPU, failed memory check, faulty graphics card or no mouse/keyboard present.

---

### Post by BIGtrouble77 on 2007-12-17
I forgot to mention that you should look up what the beep code is, it should be indicated in your mobo manual.

-bt

---

### Post by DrMega on 2007-12-17
> **LoneWolfJack said:**
> I will have to agree that it is most likely a hardware issue

Agreed.

> **LoneWolfJack said:**
> As Linux will always try to max out your RAM, you may have a stick that's faulty. It may only show under Linux for the aforementioned reason due to overheating of the RAM stick.

Is this right? Whenever I check the memory usage on my box it is rarely more than about 200MB and swap file use is usually zero, even when I'm running fairly busy stuff. Windows used to max out my memory.

A faulty power supply can cause the kind of problems described. It may be that the PSU is delivering enough power when the computer isn't doing a great deal, but as soon as it is busy, voltages drop causing all manner of problems.

---

### Post by quasimodo69 on 2007-12-19
ThanksGang,
To respond to all here..I was dual booting with xp pro and 6.4...no problems.Did an upgrade over the net...problems started with 7.04 ver...did a download of 7.10 64ver and problems started again....did a check of memory and disk (I do not know how to do the checksum..a newbie at this).Wiped both hardives clean with Partition Magic (one is IDE..and 2 others are SATA)Installed ONLY 7.10 ver for 64bitAMD.It worked for about 3 days and then the crashes I described started..black screen with waring buzzers.The codes for the MoBo indicator showed invalid codes.I started it again and checked CPU and case temps and they were under 113 degrees.
  By my way of thinking...if I have run the same setup with no changes for over a year with win 2k pro and worked the heck out of it...why would I have problems with Ubuntu?And while I was running Ubuntu 7.10 64 bit ver I had starnge problems like sound that did not work 40% of the time..it did or it did not..and I do not know enough about how to trouble shoot it when it did not work.
  After almost 2 months of frustration and trying tons of things that I did understand in the forums..I looked at my other computer which was an intel chip with an i386 7.10 install (clean) and it worked fine..I loved it.So I finally tried the i386 install of 7.10 on this AMD64 bit and it worked great!
 I still have some quirks with 7.10 i386 running on an AMD 64 system...and it may be my misunderstanding of the O/S  though.The sound is very low on start up...but works normally once booted.I have a problem with flash on websites (it looks like a kindergardener cut and pasted cut out pieces in the space for the flash...even though I downloaded flash 9 and thought it was installed).I installed the glx-new for my nVidia card and lost all the choices for resolution choices-only 1024x768-but got to enjoy all those cool desktop graphics!By the way I did not use the desktop graphics until I new it was pooched and I was going to re-install,yet again.

  My video card is an nVidia 5200..MoBo is and Abit AV8.1gb Crucial memory.
I tried the nVidia drivers with the 7.10 install at first (I didn't know how to change them at first)and had the crashes at first..I tried the restricted drivers after I had crashes to see if it was the video driver because most in the forum seemed to think it was the nVidia drivers causing the crashes.I am running them now (hence the few resolution choices) on 7.10 i386 with no crashes.
  I also noticed one of you mentioned making sure the BIOS is set to defaults..I have gone through it and set it for the memory I have.I did not think about setting for defaults with 7.10 64...do you really think this would makea difference after all the other things i have done?I do not believe in overclocking (if you want it faster..buy it! :-) )
  As for the power supply-the recommended was 450w and I have a600w-an Ultra which is a  brand I have not had problems with and not with this case..
  That is all I have to respond for now.I am not a person who has a lot of money and that is the main reason I went itno building my ownIi love 'em.I enjoy helping other people with them when i can and I am fascinated bu them.I also build my own because I can wait and buy the best I can afford..though I do not need to be exotic..and try to keep up with the mainstream in the learning curve.
I want to thank all who contribute here..DrMega,Bigtrouble77,LoneWolfJack and NebuTron for trying to help me.I am new to trying to crawl the forums for help and apreciate all the help..and the fact somebody read my WHOLE long winded post.
Give me your faxe numbers and I will fax you a beer!
Thynx

---

### Post by LoneWolfJack on 2007-12-19
> I started it again and checked CPU and case temps and they were under 113 degrees.

If this is celsius (should be), then your CPU is overheating. In fact, its WAY too hot. At about 120 degrees, the internal structure of the cpu die will break down and your CPU will be garbage. You CPU should be at like 60 degrees maximum.

---

### Post by jocko on 2007-12-19
> **LoneWolfJack said:**
> If this is celsius (should be), then your CPU is overheating. In fact, its WAY too hot. At about 120 degrees, the internal structure of the cpu die will break down and your CPU will be garbage. You CPU should be at like 60 degrees maximum.

I'm sure he means 113 deg. Fahrenheit (=45 deg. Celcius). That's a pretty good temperature.

---

### Post by bluedragon436 on 2007-12-19
I am running this on two 64bit setups, on regular AMD Athlon, and two laptops, so 5 setups all together and have had a few issues, but nothing like this...I would definately say that it sounds more like a hardware failure more than an issue with the OS....  I had some issues when I first setup one of my 64bit systems, but after changing out the memory with my other 64bit setup it ran just fine, and then I found out that there was an issue with the sticks of memory that I had in my computer...and other than that have only had a few small tweaks between the other systems....but that is just me...if you really want to run Linux and have decided you for whatever reason want to hate Ubuntu then try out [www.opensuse.org](www.opensuse.org) and try that out and see if you have these same issues.....or you can actually give it a chance and not just blow up..... there are many people on here that have had issues and have worked them out by not just giving up...I realize that it can some tiems be a pain to have "down time" working on figure out the issues, but I have enjoyed the end results....but that is just my two cents worth...

---

### Post by quasimodo69 on 2008-05-07
> **LoneWolfJack said:**
> If this is celsius (should be), then your CPU is overheating. In fact, its WAY too hot. At about 120 degrees, the internal structure of the cpu die will break down and your CPU will be garbage. You CPU should be at like 60 degrees maximum.
Hey Guys,I was off for  awhile and built a new box and it works great..if I ever get the resolution fixed.
The temp was 113 F and I can only guess it was a hardware issue..but I don't know why Ubuntu set it off-that same machice is now re-installed with Micr$oft and setting in the corner for my guests to use...never a problem with it on Micro$oft.
thnx

---

