---
title: "Help!!..many problems!!"
date: 2005-11-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by treyazagthoth on 2005-11-26
this is my second thread... no one seems to be able to help me ...
The problem is this..got an amd64 sysytem...
a)my systems keeps crashing repeatedly..sometimes upto 3 times per session.. even afeter upgrading the same problem is there? what can i do?
b)XMMS and Xine-ui act real strange sometimes..some cd's which initially work.. fail to do so only moments later!! 
c)i cant write any file to my cd's..even with root access..ditto for my floppy drive? why?
d)two days back my sysytem crashed... after upgrading .. and grub got corrupted..
i had to reinstall..not to mention loosing some academic data of importance
..is this a problem with ubuntus lack of support for AMD64? 
any help will be appreciated..
dont misunderstand me..but i swithced to linux from windows because i thought it was more stable... don't (frustatingly) think so now..
anyways.. try to help if you can..

---

### Post by steve.horsley on 2005-11-26
Not much help, I know, but have you tried the 32-bit Ubuntu? If 32-bit is unstable too, it would point the finger at a hardware problem. If it is stable, then you have a useable option.

---

### Post by atoponce on 2005-11-26
It sounds like you have a faulty hardware, rather than software problems. The repeaded crashing may be due to thermal paste getting thin between your processor and the fan. It could be a number of other things also. You may have bad sectors on your hard disk. Your board could have some bad connections. Could be a whole number of things. I really think it is hardware related, however, as Ubuntu 5.10 is running just fine on my brothers AMD64 laptop without any hiccups.

Edit: spelling.

---

### Post by treyazagthoth on 2005-11-29
hey!.. atoponce..my system is brand new..just i month old for that matter..!!
ever heard a saying.." a bad work man always blames his tools"..any way thanks for the reply.. and just for your information these crashes are getting preety frequent now..
will using a ubuntu32 bit cause any problems? fedora4 for 32bit did not seem to recognise my sata drive.

---

### Post by RAOF on 2005-11-29
[QUOTE=treyazagthoth]...a bad work man always blames his tools"...[/QUOTE]
And a **good** workman doesn't use bad tools ;)  Just because it's a new computer doesn't mean that there can't be a hardware fault.

32bit Ubuntu should work with all your hardware, if the 64bit version does.

When asking questions like these, it's really important to clearly give any information you think is relevant.  We're going to have to ask, anyway - we can't fix something without actually knowing what's wrong.  Finally, make the post as easy to read as possible.  Using upper case where appropriate just makes it that little bit easier to read, so we're more likely to answer :).

a) What exactly do you mean by "crashes"?  Are you consistently doing anything at the time of the crash?  Does the screen do anything funny?  Are there symptoms leading up to the crash, or do they seem to happen from nowhere?

b) In what way do XMMS & xine-ui "fail to work"?

c) How are you trying to write files to the CD?  Using the nautlilus cd-creator thing, or a dedicated CD writing program like K3B or gnome-baker?  I no longer have a floppy drive, and haven't used one for ages, but do you still have to mount the floppy before reading from/writing to it?  Is the floppy formatted?  Is the floppy write protected?

d) Not that it'll be much use now, but with a livecd you can access your Ubuntu installation and fix grub without reinstalling.

---

### Post by jvictor on 2005-11-29
Can u plz post ur machine config ?

When exactly does it crash ? Is it when u fiddle with the CD/DVD  ? Yes Ububtu is v stable.. for me & I'm an AMD 64 user..

---

### Post by atoponce on 2005-11-29
[quote=treyazagthoth]hey!.. atoponce..my system is brand new..just i month old for that matter..!!
ever heard a saying.." a bad work man always blames his tools"..any way thanks for the reply.. and just for your information these crashes are getting preety frequent now..
will using a ubuntu32 bit cause any problems? fedora4 for 32bit did not seem to recognise my sata drive.[/quote]

Did you build the system?  This may be a bad question, but when installing the motherboard, did you forget about installing the brass posts between the case and the board?  That will cause your board to short, causing a "crash".  The frequency of the crashes leads me to believe it has to be hardware.  Are you having the same number of crashes, despite what OS you use?

---

### Post by treyazagthoth on 2005-11-30
Hi there..

First off.. . windows works flawlessly on my system.. regardless of the amount of hours i use it.

Ok then..
a) the main problems that i face are that the system hangs abruptly within the first five min. of using ubuntu. i then have to reboot the system.. after which the system works smoothly.. these ocuurances have become pretty frequent now.

b) ditto when i connect to the net..the system hangs abruptly , the cursor gets stuck ,the keyboard is unresponsive and the screen just gets frozen.. a particularly dangerous problem when i browse through secure sites as i do not have the chance to log off. however this only occurs the first time i access the web.. i mean after i reboot the system it's ok..for some time

c) as for xmms or xine -ui ,  it is able to play certain vcd's but when i try to play the same vcd after say.. a few days .. as usual the system hangs

d)whenever i try to multitask , like try to simultaneosly open a couple of windows and try to listen to some music and download something.. BOOM>!!! the system hangs

e) Yesterday i get a msg . telling me of updates that are avialble for my BitTornado client.. i download it... only for the programme to tell me that  it cannot be run on account of some Critical error.

f)Ubuntu had graciously deleted my GRUB last week.. and i had to reinstall it..of course after loosing everything i was working on.the particular problem occuring after i had updated the latest linux kernel.

g) and last but not the least..atoponce i hope i have graciously adhered to your ettiquetes which the other members of this forum always adhere to..

My config is as follows:
AMD 64 3000+
ATI rs 480 il-2 (939socket)
Nvidia 6200 pcie card
512 mb ram

THat's it.. Bye! until next time

---

### Post by Jason_25 on 2005-11-30
Sounds like hardware to me too.  With the A64 it's usually to do with your memory settings.  You need to run some stabilty testing software like prime, etc.  Sorry I don't know of any of those programs for linux.

---

### Post by atoponce on 2005-11-30
[quote=treyazagthoth]Hi there..

First off.. . windows works flawlessly on my system.. regardless of the amount of hours i use it.

Ok then..
a) the main problems that i face are that the system hangs abruptly within the first five min. of using ubuntu. i then have to reboot the system.. after which the system works smoothly.. these ocuurances have become pretty frequent now.

b) ditto when i connect to the net..the system hangs abruptly , the cursor gets stuck ,the keyboard is unresponsive and the screen just gets frozen.. a particularly dangerous problem when i browse through secure sites as i do not have the chance to log off. however this only occurs the first time i access the web.. i mean after i reboot the system it's ok..for some time

c) as for xmms or xine -ui ,  it is able to play certain vcd's but when i try to play the same vcd after say.. a few days .. as usual the system hangs

d)whenever i try to multitask , like try to simultaneosly open a couple of windows and try to listen to some music and download something.. BOOM>!!! the system hangs

e) Yesterday i get a msg . telling me of updates that are avialble for my BitTornado client.. i download it... only for the programme to tell me that  it cannot be run on account of some Critical error.

f)Ubuntu had graciously deleted my GRUB last week.. and i had to reinstall it..of course after loosing everything i was working on.the particular problem occuring after i had updated the latest linux kernel.[/quote] 
You definitely have the hardware specs to support running the OS, and seeing as though XP runs flawlessly on your system, it definitely points to the software.  What versions of Ubuntu have you tried?  Have you tried both the AMD 64-bit version and the i386 32-bit version?  I would imagine that the 64-bit Ubuntu would work better, but I guess you never know.

Also, you haven't mentioned what release you have tried. Whether you installed Dapper 6.04, Breezy 5.10, Hoary 5.04 or Warty 4.10.  I can imagine that with Dapper in the heaviy development stages now, that could cause some problems.  You should install Breezy 5.10.

Lastly, if Ubuntu just doesn't work on your system, which may be the case, then use a distro that does.  There certainly is nothing wrong with using a distro that best fits your needs.  If it isn't Ubuntu, it isn't Ubuntu.  I settled on Ubuntu, because Slackware, RedHat, Mandrake, SuSE and FedoraCore just didn't work quite right with my laptop.  Ubuntu does.  It just works for me.
 

[quote=treyazagthoth]g) and last but not the least..atoponce i hope i have graciously adhered to your ettiquetes which the other members of this forum always adhere to..[/quote] 
Not exactly sure what you mean here...

---

### Post by skylark on 2005-12-01
treyazagthoth, I also think it is a hardware issue. Have your tried testing your system's memory with [www.memtest.org](www.memtest.org) ? 

PS: when your system hangs - what if any error messages do you receive? Do you get a kernel panic?

---

### Post by RickCB on 2005-12-01
:KS  I have been running Ubuntu 5.10 on my AMD64 x2 4200+ ASUS A8N-SLI Deluxe system without any noticable instabilities. As an experiment, I have just reverted back to the 32bit version, just to see if there was any noticable difference, and the response does seem to be a bit more sliggish under 32bit, so I'll be reverting to the 64bit install tonight.

---

### Post by nalmeth on 2005-12-01
Regarding all your crashes etc. I have nothing to offer you. But if you still want a stable linux alternative there are tons of options. 
I have heard Kanotix has really good 64-bit support. You can download a live CD, and I think an install CD. I think that like ubuntu it is debian based, which is a good thing for many reasons.
If ubuntu, or debian in general is not suiting you and if you are newer at linux I have also heard really good things about Mandriva in terms of ease of use and installation. 
Mandriva is made by a company and has enterprise editions available, but has a free-edition. This is usually not something I get into, who knows if you will have to pay for support. 
Or go to distrowatch.com, and you might find something that fits just right for you. 

Quote:
Originally Posted by treyazagthoth
g) and last but not the least..atoponce i hope i have graciously adhered to your ettiquetes which the other members of this forum always adhere to..

I'm sure you're frustrated with having major problems and not having major solutions, but sarcasm usually won't help you out when asking other people for help.

---

### Post by rjpiercy2 on 2005-12-03
I am having similar problems.  Let me grab some details and I will post the exact symptoms.  It seem to start after I adjusted the  settings on my package management system.

more later

---

### Post by Hobbes on 2005-12-03
I would make a comment about you not reading the thread carefully, but that could fit into the "holier than thou" category you listed so I will just say this, from what I read, which I will grant could have been edited in some way I suppose, I can't find anything atoponce says which is in any way sarcastic, bad mannered, or anything but helpful.  He may have gotten kind of stuck on it being a hardware problem, but nowhere does he say anything spiteful.....in summary... I guess just be careful when you accuse people of being bad-mannered, or else it may just come back around to reflect poorly on you. (which is not what I'm trying to do, I"m just saying...)

---

### Post by MentalDisruptor on 2005-12-03
> Hi there..

First off.. . windows works flawlessly on my system.. regardless of the amount of hours i use it.

I used to have similar problems with my brandnew AMD Athlon 64 3200+ System at first. Perhaps I can offer you some help...

> 
Ok then..
a) the main problems that i face are that the system hangs abruptly within the first five min. of using ubuntu. i then have to reboot the system.. after which the system works smoothly.. these ocuurances have become pretty frequent now.

b) ditto when i connect to the net..the system hangs abruptly , the cursor gets stuck ,the keyboard is unresponsive and the screen just gets frozen.. a particularly dangerous problem when i browse through secure sites as i do not have the chance to log off. however this only occurs the first time i access the web.. i mean after i reboot the system it's ok..for some time

c) as for xmms or xine -ui ,  it is able to play certain vcd's but when i try to play the same vcd after say.. a few days .. as usual the system hangs

d)whenever i try to multitask , like try to simultaneosly open a couple of windows and try to listen to some music and download something.. BOOM>!!! the system hangs


Well, the crashes seem to occur, when you're getting your system busy. Have you ever tried to reproduce a crash when it occured? To do exactly the same things again to provoke a system crash? Might be useful to know if you can somehow reproduce these errors.

You might also want to check /var/log/syslog and /var/log/messages if corresponding messages (regarding the crashes) have been logged.

As skylarg suggested, it won't be a mistake to test your memory for errors. Simply select Memtest86 in the grub boot menu.

If you aren't able to reproduce the crashes as described, you can try to install the package stress (it's in the universe repositories iirc). Run it on the console (NOT under X!), perhaps it is able to set your system on fire - IF you are experiencing kernel panics, you will gain very useful information from the console output.

In my case, accessing my primary slave harddisk made my system crash with a Machine Check Exception kernel panic - I think my PSU (450W) is to weak. Disconnecting the harddisk from the system solved all my problems.

---

