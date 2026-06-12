---
title: "Ubuntu 9.10 64-bit freezes"
date: 2009-11-03
forum: x86 64-bit Users
---

### Post by LxndrPhnx on 2009-11-03
I'm running Ubuntu 9.10 64-bit and it keeps freezing.  I thought it might be a video driver issue (I forgot to activate the proprietary driver), but when activated it, it still keeps freezing mid use.  I did a clean install from 9.04 32-bit and never had this issue.  (Actually, I can't remember Ubuntu ever freezing since I've been using it over the past year.)  Has anyone else had this issue?

---

### Post by MG37221 on 2009-11-03
I'm having it.  About once a day.  Firefox is always in use when this happens.  I've no clue but only my reset button can unfreeze it (cold boot).  Been on Ubuntu since 7.04 and used SuSE prior.  Am actively looking for patches to make 9.10 as stable as all previous versions.  This one has not been trouble free as I've gotten used to although I am aware of the vast complexities involved with an update to an entire operating system!  Mine has been a clean install.

---

### Post by michaelzap on 2009-11-03
> **MG37221 said:**
> I'm having it.  About once a day.  Firefox is always in use when this happens.  I've no clue but only my reset button can unfreeze it (cold boot).  Been on Ubuntu since 7.04 and used SuSE prior.  Am actively looking for patches to make 9.10 as stable as all previous versions.  This one has not been trouble free as I've gotten used to although I am aware of the vast complexities involved with an update to an entire operating system!  Mine has been a clean install.

+1

Although my system crashes (reboots) as well as freezes, and it does so far more often than once a day and not always when Firefox is running.

It's the worst issue I've ever had to deal with in Linux.

---

### Post by MG37221 on 2009-11-03
> **michaelzap said:**
> +1

Although my system crashes (reboots) as well as freezes, and it does so far more often than once a day and not always when Firefox is running.

It's the worst issue I've ever had to deal with in Linux.
Doesn't get much worse than system instability.  It is frustrating (and surprising for Ubuntu) but I suspect it will be corrected with patches.  If I find it unworkable (haven't yet), I can always just install 9.04 as it was extremely stable for me.  I suspect that this will be corrected.  My hardware is relatively new.  I'm thinking that may be a contributing factor.

---

### Post by michaelzap on 2009-11-04
> **MG37221 said:**
> Doesn't get much worse than system instability.  It is frustrating (and surprising for Ubuntu) but I suspect it will be corrected with patches.  If I find it unworkable (haven't yet), I can always just install 9.04 as it was extremely stable for me.  I suspect that this will be corrected.  My hardware is relatively new.  I'm thinking that may be a contributing factor.

Apparently it's a kernel issue and thus affecting all of the major distros that have rolled out new releases with 2.6.31-14 (at least that's what I've read elsewhere in these forums).

---

### Post by MG37221 on 2009-11-04
> **michaelzap said:**
> Apparently it's a kernel issue and thus affecting all of the major distros that have rolled out new releases with 2.6.31-14 (at least that's what I've read elsewhere in these forums).

In that case, I'd guess that a proper fix is well in the works already.  I check for updates daily.  There have been a few but nothing on the level of an updated kernel.  Probably won't be long though.  Uncorrected problems don't go very long with linux.  That's a big reason it is so highly trusted by those who use it.

---

### Post by michaelzap on 2009-11-04
> **MG37221 said:**
> In that case, I'd guess that a proper fix is well in the works already.  I check for updates daily.  There have been a few but nothing on the level of an updated kernel.  Probably won't be long though.  Uncorrected problems don't go very long with linux.  That's a big reason it is so highly trusted by those who use it.

I'm checking hourly!

---

### Post by LxndrPhnx on 2009-11-04
That's somewhat of a relief.  Mine freezes whenever Firefox is open as well, but Firefox is open 90% of the time I'm on my laptop though.  I've been using 9.04 (Have them both installed at the moment) for anything serious (such as school work).  I've never, ever, ever had Ubuntu freeze before now.  Ever.  Hopefully the kernel issue (if that's what it is) will be fixed soon.

---

### Post by MG37221 on 2009-11-04
I've just [read]("http://www.phoronix.com/scan.php?page=news_item&px=NzY2OQ") where a new kernel 2.6.32-RC6 has been made available for testing.  Hopefully these issues will be addressed.

---

### Post by michaelzap on 2009-11-04
> **MG37221 said:**
> I've just [read]("http://www.phoronix.com/scan.php?page=news_item&px=NzY2OQ") where a new kernel 2.6.32-RC6 has been made available for testing.  Hopefully these issues will be addressed.

I certainly hope so. I'm writing this from Vista! VISTA!!!:evil:

---

### Post by MG37221 on 2009-11-04
> **michaelzap said:**
> I certainly hope so. I'm writing this from Vista! VISTA!!!:evil:

Hopefully, I'll never become that desperate:p  As I said, I can always revert to 9.04.  It was most excellent proving once again that newer isn't always better.

---

### Post by michaelzap on 2009-11-04
> **MG37221 said:**
> Hopefully, I'll never become that desperate:p  As I said, I can always revert to 9.04.  It was most excellent proving once again that newer isn't always better.

I never thought it could happen to me, either. The only time I ever booted up into this pre-installed Vista before was to shrink the partition to install Ubuntu. I suffered through six whole months of annoying video flickering in Jaunty, but constant freezing and crashing is not a bearable condition.

---

### Post by MG37221 on 2009-11-04
Video flickering?  Jaunty was perfect for me, as were all preceding flavors of Ubuntu (once SuSE got into bed with Microsoft and I left them both for good) Can you list your hardware please?

---

### Post by michaelzap on 2009-11-04
> **MG37221 said:**
> Video flickering?  Jaunty was perfect for me, as were all preceding flavors of Ubuntu (once SuSE got into bed with Microsoft and I left them both for good) Can you list your hardware please?

I have a Lenovo Y530 with integrated Intel video and sound. Intel video was problematic in Jaunty, and I had to use Alsa to get 5.1 sound. I was really happy to ditch Jaunty at first because I thought that Karmic was going to be so much better for me.

---

### Post by MG37221 on 2009-11-04
> **michaelzap said:**
> I have a Lenovo Y530 with integrated Intel video and sound. Intel video was problematic in Jaunty, and I had to use Alsa to get 5.1 sound. I was really happy to ditch Jaunty at first because I thought that Karmic was going to be so much better for me.

Gotcha.  I hope they get it fixed soon too, for you.  Mine's working except fpr the occasional lockups.  Fortunately I use nVidia for graphics.  I left ATI when I left Windows many years ago.

---

### Post by ganeshmallyap on 2009-11-05
Hai all,

My story is very similar to [LxndrPhnx]("http://ubuntu-ky.ubuntuforums.org/member.php?u=731815")'s first message. I was using Ubuntu Jaunty 32 bits.  And this time I switched to Ubuntu Karmic AMD64 with clean install.  I do see my applications freezing every now and then during interactive usage.  For example, while selecting new applications for installation from Software Center the window gets greyed out and comes back to life after 15-20 seconds of time.  Another example - while doing a huge data transfer the machine's responsiveness gets worse.  Had it been the case of a application crash, it was easier to report the bugs.  In such cases, I am not sure how to report them to Ubuntu team.  

I use Core 2 duo, nvidia card & 2 GB RAM and have installed proprietary drivers for my graphics card (ver. 185).  I was using the same version of the driver in jaunty also.  But never faced any issues in Jaunty.    

For few unavoidable reasons I was running few windows applications via WINE in Jaunty.  But in Karmic AMD64 I am not able to run them via WINE. I presume this is due to the 32 bit v/s 64 bit architecture difference.   Any clues how to make AMD64 WINE run 32 bit WIN32 apps?  

Installing applications applications like Handbrake, Skype and Mobile Media Converter is another challenge for me.  I saw couple of posts indicating solutions for these three applications, but none of solved my issue and I am still struggling to fix them.

Overall I am very happy with the visual improvements, usability and new versions of the applications that came with Karmic AMD64, and now only wish these bugs will be fixed at the soonest.   I have no plans to revert back to Jaunty, rather I would prefer to wait for the bug fixes.

Ganesh

---

### Post by LxndrPhnx on 2009-11-05
Yeah, I've been using Karmic until if freezes, then restart and use Jaunty.  Though, if I didn't have them both installed on one machine I would probably bear through it.  I have ATI Graphics so Jaunty worked perfect for me (other than the installation, it was my first update and I managed to majorly mess up the update, so went with clean install, which didn't go too smoothly either).  Other than this issue with the freezing I adore Karmic.  It boots and runs a lot faster than Jaunty did.  I hope the kernel issue is resolved soon.

---

### Post by michaelzap on 2009-11-06
Given that Linus says it's almost ready and it fixes [this serious bug]("http://linux.slashdot.org/story/09/11/04/0320254/Bug-In-Most-Linuxes-Can-Give-Untrusted-Users-Root?from=rss") that can give undeserved root access (not in Ubuntu), I don't think we'll have long to wait.

---

### Post by MystaMax on 2009-11-06
> **ganeshmallyap said:**
> Hai all,
My story is very similar to [LxndrPhnx]("http://ubuntu-ky.ubuntuforums.org/member.php?u=731815")'s first message. I was using Ubuntu Jaunty 32 bits.  And this time I switched to Ubuntu Karmic AMD64 with clean install.  I do see my applications freezing every now and then during interactive usage.  For example, while selecting new applications for installation from Software Center the window gets greyed out and comes back to life after 15-20 seconds of time.  Another example - while doing a huge data transfer the machine's responsiveness gets worse.

I'm having very similar (if not the the exact same) issue. I'm also running 9.10 64-bit on a Dell Latitude D630 with 2GB of RAM.

> **ganeshmallyap said:**
> Overall I am very happy with the visual improvements, usability and new versions of the applications that came with Karmic AMD64, and now only wish these bugs will be fixed at the soonest.   I have no plans to revert back to Jaunty, rather I would prefer to wait for the bug fixes.

Me too! I have no intentions of downgrading. Bluetooth A2DP finally works out the box, and I love it enough not to downgrade!

> **MG37221 said:**
> Video Flickering?

I'm experiencing some flicking as well w/ Youtube videos. I've got an Intel graphics card.


Here are some descriptions of the problem:

1. Opening an MP3 file takes over 30 seconds. WHOA! If the player is already open, its much faster.

2. Viewing the help file for "System Monitor Preferences" took over 15 minutes to appear on screen (I timed it). During this time System Monitor reported that IOWait usage was around 50%. Subsequent attempts to open the same help file are a lot faster ~60 seconds, which is still TOO SLOW. I'm not really sure what this means, but everytime the PC locks up, IOWait usage is high.

3. Trying to edit the applications menu takes ~2-3 minutes to start; again subsequent attempts are much faster, but still TOO slow.

4. Installing applications take a very long time. For example, I just used aptitude to update grub & chromium-browser. Downloading the packages was very quick... Less than 1 min. Preconfiguring, Unpacking, and processing the packages is taking over 10 minutes. Similar updates on my 9.04 laptop do not take this long. Again, during this time System Monitor reported IOWait usage was around 60% the whole time. Since this is a fresh install, I'm having to reinstall a lot of 3rd party apps, and this situation is prolonging the update process.

5. File copying takes a very long time. I tested it with 96MB of MP3's, and it took over 2 minutes to copy it from my Music folder, to a test folder on my desktop. Both folders are on the same hard drive, and local to the PC.

Does anyone know if there is a bug report for this issue filed in launchpad? If so, whats its link? I would like to watch it. Otherwise, I'll be filing one myself.

Overall, I'm happy, but this does make it bit difficult to be productive. I hope there is a fix soon.

System Specs:

Intel Core 2 Duo 2.0Ghz
2GB RAM
Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller

---

### Post by ganeshmallyap on 2009-11-15
Hi all,

Earlier I had posted a message about system freeze in my Karmic AMD64 desktop.  But for the past one week I have seen noticeable improvement in the stability and I have not faced a single freeze/crash in spite of me running my desktop for more than 2 days at a stretch.  I am very happy about this and I wanted to share this with all of you.

I have applied system updates of all sorts on a regular basis and removed Sun Java library and retained only open JDK 6.   Not sure whether these were the reasons for the improvement.

BTW I have noticed one minor glitch.  That is Linux Multi Media Studio (LMMS) still keeps running in the background and while shutting down, I will get a prompt some thing like do you want to close this application etc..  Hope this will also be taken care of in near future.

---

### Post by MG37221 on 2009-11-15
I too have been aggressively seeking out and applying all available updates.  No problems for several days until today.  I am noticing that every time I have a hard freeze, it is only during a Firefox session.  This has been the pattern all along but today I'm confident that I can say that this **is** the case.  I may look into an alternate browser to use for a while.

---

### Post by utrading on 2009-11-16
My experience has been that Firefox+Flash is the biggest culprit that causes system freeze on my box (Jaunty 9.04), especially if you have lots of add-on installed.

Now I removed flash, and keep NoScript add-on and my system seems to be much more stable. Previously my system would freeze VirtualBox for a while.

It also helps to install the latest proprietary driver (190.42), if you have Nvidia card, which I find much more stable than previous version (185.18.36).

> **MG37221 said:**
> I too have been aggressively seeking out and applying all available updates.  No problems for several days until today.  I am noticing that every time I have a hard freeze, it is only during a Firefox session.  This has been the pattern all along but today I'm confident that I can say that this **is** the case.  I may look into an alternate browser to use for a while.

---

### Post by gpstar on 2009-11-16
i've been having these system freezes everyday now since doing a fresh install of karmic 64 bit recently. My other laptop running 32bit karmic has no issues. Just unbearable now. May have to convert this one to 32bit. I"ve tried latest 2.6.32-rc7 kernel and latest 190.45 nvidia driver, doesn't help at all. Also of course pulseaudio eats up all my memory and kills the system, so I kill pulseaudio on startup now.  syslog shows no reason why the system freezes up.

---

### Post by utrading on 2009-11-17
I forgot to mention that I also followed this post:
[http://www.nvnews.net/vbulletin/showthread.php?t=58498](http://www.nvnews.net/vbulletin/showthread.php?t=58498)

In particular I applied the following upon kernel boot:[INDENT]*pci=nommconf*
*clocksource=hpet*
[/INDENT]I don't know if they helped since I also upgraded the driver, but since the system is much more stable now I don't bother to remove them.

Again, I no longer use flash in firefox, which is less than ideal.  I do use flash in virtualbox which is no problem.

> **gpstar said:**
> i've been having these system freezes everyday now since doing a fresh install of karmic 64 bit recently. My other laptop running 32bit karmic has no issues. Just unbearable now. May have to convert this one to 32bit. I"ve tried latest 2.6.32-rc7 kernel and latest 190.45 nvidia driver, doesn't help at all. Also of course pulseaudio eats up all my memory and kills the system, so I kill pulseaudio on startup now.  syslog shows no reason why the system freezes up.

---

### Post by gpstar on 2009-11-18
I think I found the problem and tracked it down to the Terminal Screenlets I was using. I've since turned them off and my system has been rock solid so far with no more freezing since.

---

### Post by gpstar on 2009-11-18
well i spoke a bit too soon. system just froze up on me again.

tried the ALT + SysRq + R E I S U B and that did not do anything.

last thing in my syslog to show before the freeze was

```
Nov 18 10:45:01 michael-laptop CRON[11890]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
```

---

### Post by MG37221 on 2009-11-18
I think I've just about had enough.  I'm going back to 9.04.

---

