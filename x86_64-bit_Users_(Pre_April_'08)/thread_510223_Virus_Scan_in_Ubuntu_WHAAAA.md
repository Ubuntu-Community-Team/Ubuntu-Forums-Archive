---
title: "Virus Scan in Ubuntu??? WHAAAA???"
date: 2007-07-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by AegisTalons on 2007-07-26
So I was looking through other parts of this forum, and there is a little talk about virus scanners in Ubuntu. I found [this nice tutorial]("http://ubuntuforums.org/showthread.php?t=88357") on how to install F-Prot and a gui front end. 

-The question is if you are running a home computer, do you really need a virus scanner for Ubuntu, even if you dual-boot? 
-What if in XP64, you do have a virus scanner? 
-Also in the tutorial, it said do not try this for 64 bit? 
-Do any of you guys run a virus scanner?

---

### Post by zach12 on 2007-07-26
no you do not need a  Virus Scaner for ubuntu it's  Virus free
have fun

---

### Post by aysiu on 2007-07-26
**If** a viable virus threat appeared for Ubuntu, it would take longer for the anti-virus maintainers to update the definitions than it would take you to install the anti-virus program. So, no, there's no point in having anti-virus installed now.

---

### Post by zsouthboy on 2007-07-26
Linux is inheritly more secure - you have to enter a password to giev a program root rights.

Also note that closed source operating systems haven't had millions of eyes looking over the code, over and over, for security vunerabilities.

So (and as Ubuntu grows in popularity, you never know when we'll be targetted..) the most a virus could do is delete your home folder.

---

### Post by Jussi01 on 2007-07-26
Hi, 

As others have said, virus scanners are not needed in Linux. However, It is useful to have a virus scanner for scanning files that are incoming from the web, such as word docs etc, as to not pass any viruses on to friends/family who have windows pc's. One such virus scanner is clamav - available in the repositories.

---

### Post by praxis22 on 2007-07-26
I built a (heavily tweaked) Ubuntu box for the kid upstairs, I installed ClamAV on it, more because I felt he was likely to download stuff that was infected, than because I thought that the OS needed to be protected. 

Provided you don't do anything stupid online, (download music/movies with p2p apps, surf porn, open unknown attachments, etc.) then you have no need of AV, if you do, then you need all the help you can get.

YMMV

---

### Post by Kilz on 2007-07-26
> **praxis22 said:**
> I built a (heavily tweaked) Ubuntu box for the kid upstairs, I installed ClamAV on it, more because I felt he was likely to download stuff that was infected, than because I thought that the OS needed to be protected. 

Provided you don't do anything stupid online, (download music/movies with p2p apps, surf porn, open unknown attachments, etc.) then you have no need of AV, if you do, then you need all the help you can get.

YMMV

Even if you download things online, you dont really need a virus scanner with Ubuntu. That is unless you plan on then sending them to people with windows. 
The only linux viruses are "proof of concept" viruses that exist. They require you to do something stupid. Like run as root. Something that is hard to do with Ubuntu, but Im sure there is someone that does it.

---

### Post by marsmissionaries on 2007-07-26
**Virus scanners are VERY important even when you are on a virus free OS, i reccomend you get one, linux users can pass on WINDOWS virusses through email and such, so it is important to be careful or get a virus scanner that detects windows AND linux viruses.**

---

### Post by Kilz on 2007-07-26
> **marsmissionaries said:**
> **Virus scanners are VERY important even when you are on a virus free OS, i reccomend you get one, linux users can pass on WINDOWS virusses through email and such, so it is important to be careful or get a virus scanner that detects windows [COLOR="Red"]AND linux viruses[/COLOR].**

There is no such thing as a "Linux " Virus. There may be "proof of concept" examples , ones that require you to run as root. But they dont exist in the wild. It doesnt exist. If you are stupid enough to send, or forward friends attachments from other people, without opening them to see what they are. Then maybe you fall into the select group of people who think tin foil hats are useful, there was no reason to fight ww2, and the moon landing was shot in a movie lot..... opps I forgot add in the people who think linux needs a virus scanner.
If you feel the absolute need to install this useless set of applications to use up ram and processing power. For sanity's sake dont pay for one. Virus scanners are **_only_** important to WINDOWS users, not people running any flavor of Linux.

---

### Post by AegisTalons on 2007-07-27
Wow, I did not want this to get into a flame war. I just pose the question because I saw other forum threads talking about it, and wanted to see what the 64 bit community thought. Because in the windows world, there have been maybe 4 64 bit viruses, while the rest have been of course 32 bit.

Since it is very rare to the have a Linux virus and even more rare to have one that is 64 bit, I was wondering if people still installed virus scanners and for what purpose. Thanks for all the replies though.

---

### Post by Myzrael on 2007-07-27
The fact that virusses for windows are not writen in 64bit is irrelevant. A 32bit virus runs fine on 64bit as far as I know. It's only specials drivers and low-level-calls that give problems. Must virusses are not that special so should run just fine.

---

### Post by Bolshevik on 2008-01-31
I want a virus scanning program on my 64bit Linux boot, so I can scan my flashdrive. I was helping a friend clean out her computer today, and had all my utilities on my flashdrive. She had so many viruses, 10 mins after installing spybot even it's .exe was infected, in fact practically all .exes on her computer were infected.

So I worry about my flashdrive, Since I dual boot and use it on others computers, I don't want to infect anyone. what can I use? I'm running 64bit Ubuntu.

People seem to like Avast, ClamAV, and AVG. Thanks!





On a completely unrelated note, the other day, my buddy was trying to crack xp home edition, haha! so I went to this super shady site, found a "keygen" and downloaded it (and labeled it as 'probably a virus') then told it to run in wine... nothing really happened, then I checked my .wine/drive_c/windows and it was loaded with randomly named .dlls and then a minute later I had an 'XPDefender' icon in my taskbar, said it was scanning my HDD for viruses (more likely credit card numbers) but it was funny cause it couldn't do jack, I just removed all dlls created that day and uninstalled the app. woohoo Linux!


Oh and all my windows license are legit, that was just for kicks, showing off Ubuntu to my buddy.

---

### Post by rousseau09 on 2008-01-31
I know I'll get flames for this, but I ran a MS box without any virus scanners for 6 months and it never got affected. Only reason being I never opened unknown things, never copied stupid things for went to websites that might be suspicious. 

If a MS box could do that (with almost 99.99% virus being developed for those) I guess its kind of pointless to install virus scanner in NIX except for if you are sending files to someone and want to be sure that this file is not affected and hence receiving end doesn't get affected in the process.

But again, don't we all run virus scanner in MS box? I guess obvious answer should be YES. If so and it gets affected with virus which is by any means protected much better antivirus and possibly commercial versions (such a waste of $$, people get smart and move to NIX) and gets updated every now and then.. I don't see any point installing an antivirus in NIX box wasting processing power. 

Though I think its nice to see people developing antivirus s/w in NIX,

Cheers all.

---

### Post by Jouke74 on 2008-01-31
I dual boot and have installed a virus scanner and anti ad-aware in Windows namely NOD32, Spybot S&D and Ad-aware. This keeps the windows part quite safe. I only surf to about 5 sites (this one included), but even on trusted websites and their forums you can be infected by virus writers. For example : al you have to do is place a link here and connect it too something bad... with some comment like the newest better working ATI drivers are here :)

As for disk structure, the linux EXT3 and Swap partitions cannot be accessed by windows (it does not know how without any extra driver). And therefore those cannot infected, but they also cannot be scanned. Linux can only read my windows NTFS partitons, I disabled the write. I have one small FAT32 partition which I use for temporary files that I work on and need to be present at both OSes. 

I therefore always have the possibility to boot into linux and clean up some windows in case I get infected. Of course then I need to mount the partition read/write. And in case a Linux update / distro update goes bad I can survive a few days in Windows.

In my opinion you need to take a good program for the job, so I do use MS-office SPSS and a few other programs under Windows. While I do lots of simulations, calculations  and batch-work under linux. I work about 50/50 in both OSes.

Finally I am slowly getting the habbit of going to linux when I need to surf a bit further from home and do my banking. It's also frustrating to see that some websites are still Explorer only....

My 2 cents..

---

### Post by stooshbunutu on 2008-01-31
There is a very reliable and free virus scan that now has a .deb all inclusive file for download. AVG anti-virus. it can be useful for scanning files even though the threats are low

[click here]("http://free.grisoft.com/filedir/inst/avg75fld-r51-a1243.i386.deb") to download

Hope this helps:)

---

### Post by rousseau09 on 2008-01-31
> **stooshbunutu said:**
> There is a very reliable and free virus scan that now has a .deb all inclusive file for download. AVG anti-virus. it can be useful for scanning files even though the threats are low

[click here]("http://free.grisoft.com/filedir/inst/avg75fld-r51-a1243.i386.deb") to download

Hope this helps:)

nice one mate. Thanks. 
I just hope its remains free.

---

### Post by Kilz on 2008-01-31
> **stooshbunutu said:**
> There is a very reliable and free virus scan that now has a .deb all inclusive file for download. AVG anti-virus. it can be useful for scanning files even though the threats are low

[click here]("http://free.grisoft.com/filedir/inst/avg75fld-r51-a1243.i386.deb") to download

Hope this helps:)

Threats are low? How about the threats to Linux are non existent? There are no Linux viruses, none. The only so called Linux viruses are proof of concept ones made by anti-virus companies to try and show anti-virus is good for Linux. They require the user to run as root , and do other stupid things.

If someone share files between windows boxes and wants to make sure a file is safe after, why not install the anti-virus to one of the windows boxes?

---

### Post by shane2peru on 2008-02-03
However viruses can be a threat if you use wine.  I ran a virus infected file in wine once, and within a matter of 5 minutes it made over 1000 viruses on my computer in tons of directories.  You can read this post:  [http://ubuntuforums.org/showthread.php?t=72598&highlight=wine+virus](http://ubuntuforums.org/showthread.php?t=72598&highlight=wine+virus)  if you are interested.  Overall, no it didn't harm my Linux installation one bit, however I do connect to my wife's windows computer via network, so that aspect it was important to me to, 1.  clean the viruses, and 2.  keep a virus scan running on my comptuer to alert me when I do have one, and where it is located.  Overall, my system stays clean.  Once again, this is for the sake of windows computers and not Linux computers as it didn't harmfully affect my computer.

Shane

---

### Post by Kilz on 2008-02-03
> **shane2peru said:**
> However viruses can be a threat if you use wine.  I ran a virus infected file in wine once, and within a matter of 5 minutes it made over 1000 viruses on my computer in tons of directories.  You can read this post:  [http://ubuntuforums.org/showthread.php?t=72598&highlight=wine+virus](http://ubuntuforums.org/showthread.php?t=72598&highlight=wine+virus)  if you are interested.  Overall, no it didn't harm my Linux installation one bit, however I do connect to my wife's windows computer via network, so that aspect it was important to me to, 1.  clean the viruses, and 2.  keep a virus scan running on my comptuer to alert me when I do have one, and where it is located.  Overall, my system stays clean.  Once again, this is for the sake of windows computers and not Linux computers as it didn't harmfully affect my computer.

Shane

Wine can be backed up, removed, and replaced. The viruses cant infect your Linux, and are dead. Linux antivirus does not have a scan running in the background as Windows antivirus, you have to tell it what to scan. So it cant stop Windows viruses coming into your Linux system or alert you that one is there. Its probably a better idea to make sure the Windows computers have an up to date scanner that have antivirus on Linux.

---

### Post by shane2peru on 2008-02-03
> **Kilz said:**
> Wine can be backed up, removed, and replaced. The viruses cant infect your Linux, and are dead. Linux antivirus does not have a scan running in the background as Windows antivirus, you have to tell it what to scan. So it cant stop Windows viruses coming into your Linux system or alert you that one is there. Its probably a better idea to make sure the Windows computers have an up to date scanner that have antivirus on Linux.

Well, actually my wife started dual booting, and now uses Ubuntu about 99% of the time, so it is far less of an issue.  I had (in my 32 bit setup) a cronjob to run clamscan on my entire home directory to tell me when I had a virus, I'm sure I will move it to my 64bit side the way things are going.  I know it doesn't run in the background, I just want it to log and tell me when it does have a virus so I can delete it.  Also, when I ran that virus via wine, it produced all those viruses in my home directory, which has many files that I share with Windows people.  That was my concern.  It didn't touch my Linux setup, other than leaving viruses in every folder. :lolflag:  Oh, and I do keep up-to-date antivirus and firewall on windows, I'm paranoid about that kind of stuff.  Ran windows for years without having a problem.  I do the same on Linux, just out of habit now.  Plus I take my usb drive to places and swap files or give documents, and about 75% of the computers here in Peru have viruses, that is how I accidentally ran one via wine.

Shane

---

### Post by Xamusk on 2008-02-04
I have had no problem with viruses in Linux, since I started in 2003.
I once convinced my wife to use Linux once, but she came back to Windows, just because of MSN Conference (audio/video) support.
Anyway, even though she uses that damning OS, I still don't have problems with viruses, because of some simple actions:
[LIST]
[*]I don't forward any e-mails with PPT or DOC attachments (usually I don't even open them, because they tend to be stupid internet chains or hoaxes
[*]I keep her AV software up-to-date
[*]I don't run wine. When I need to run some random win-only software, I run it in my VMWare virtual box. That usually does it, but if it don't I can go to my small dual-boot machine (which I try not to turn on, since THAT machine isn't run, nor updated, for more than a year.
[*]If I do have to run a program that needs more juice, I just "borrow" my wife's PC. Then again, I don't do that often, as Windows is very unconfortable to use after one experiences the power of Linux
[*]I run my network behind a home internet router, which also acts as a firewall, so those viruses that can infect a (windows) pc through the network even before one installs the AV software don't have a chance
[/LIST]
That's just some of the reasons I won't go back to windows anytime soon (I hope, because this year I'll probably have to use a lot of win-only apps)
---
One OS to rule them all.

---

