---
title: "New User"
date: 2007-07-07
forum: Wisconsin Team
---

### Post by wowie on 2007-07-07
Hello everyone,
I'm new here, and to Ubuntu. Actually, I haven't even loaded it on my computer yet. I'm still reading and learning. I found you all here by total accident, but am glad I did!
I'm in Appleton, Wi (of course) and was thrilled to find a WI site, much less a forum! Thank You for being here! I'm sure I will need lots of help, since I know just enough about computers to be considered dangerous, hehehe
I'm a home user, and all self taught, so there are probably a lot of wholes in my computer education, so please be patient with me, k? (actually my sister is the real geek, I just do what she tells me to do, and have learned a little along the way)

K, my problem-i just tried to burn the Ubuntu 6.06.1 to a disk, and I tried to check the disk integrity, like it said on the site, I downloaded the PC(Intelx86)desktop cd, from this link: [http://releases.ubuntu.com/dapper/](http://releases.ubuntu.com/dapper/)
and when i tried to boot to the cd, to check the integrity, I got nothing. My computer starts to load, gets to the self test/memory test window, stops for about 3 minutes, then goes on to load windows. So, I'm stopped in my tracks. Now, my guess is that I screwed up the iso burn to the cd, so now what do I do? Is there another way to verify the disk integrity? I still have the programs on the desktop, and I did verify the checksum before I tried to burn it, and that verified as fine/good to go.

I did go into my Bios, to make sure the boot to cd was listed before the hard drive, and it was, so I've done everything I know to do. And that leads me to you all!

This is my system: E-machine, (k, the only thing left on here that's e-machine is the case, I've completely replaced the hardware in here, except the processor, I kept that when I relpaced the mobo, but the power supply is new, the video card is newer pretty much everything, oh, the HD is still the same. I haven't decided if I should replace that, or just get another computer. This is an older computer, but she's tweaked to the max, and works great! It's an AMD, 1.7, running Win XP Pro, with a Gig of Ram (no overclocking on this) I'm trying to think if I need to tell you anything else, I know the more info you have, the better. Well, I guess that's it for hardware.
These are the links that I got all the software from, I guess we should make sure I'm getting the right programs downloaded. 
[http://sourceforge.net/project/downloading.php?groupname=infrarecorder&filename=ir0431_unicode.zip&use_mirror=superb-east](http://sourceforge.net/project/downloading.php?groupname=infrarecorder&filename=ir0431_unicode.zip&use_mirror=superb-east)
this is the recorder I got for burning the iso, like it said in the instructions
this is the link to where I started
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
this is the link to the checksum verification that I did
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
and here's the link to what I can't do
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck)

So, this is where I am, I'm hoping you all can help me. Thanks sooooo much, I'm soooo glad you are here!
wowie

---

### Post by wowie on 2007-07-07
Hi again everyone,
Well, I'm quite proud of myself! lol  I went to square one, and checked the cd under good lighting, and sure enough, she had a very large scratch in it. It was obvious where the writing to the cd began and quit.  So, I burned another disk, and this time it worked just fine. I have checked the disk integrity, and am now golden to do the install.
I'm off to the other Ubuntu forums to learn what I may need to know, and what, if anything, I may need to do to make the install as easy as possible. Any advise any of you may have would be greatly appreciated!

Oh, and I have to tell you, I have the Microsoft Laser 6000 desktop set, and it would not work when I first put in the cd, I had no mouse, or keyboard to work with at all. I had to go back into my supplies and find a wired keyboard and mouse-both usb, before I was able to do anything in the boot window. These worked just fine, so I'm thinking that I will have to configure my mouse and keyboard to work in Ubuntu. (I'm not looking forward to that at all! It's one of the reasons I haven't gone to a Linux distro yet, don't like to have to configure all the drivers for the hardware) I just thought I'd let you know that, and everything else that goes on with this install. 

Take care all, and thanks again for any help you may give me:D       wowie

---

### Post by uberushaximus on 2007-07-09
Good for you :D

I've always had problems with CDs I burn of ubuntu. I never have the issues with the shipit discs, so that's  where I usually start ;)

---

### Post by wowie on 2007-07-09
Hi uberushaximus  :)  
Well, thanks for answering me!  Glad to have a response from someone. I just looked at you're profile, and you are waaaayyyyy ahead of me in Linux, I don't even know what you're distro is!  hehehe  Just curious, where is Richfleld? You know, just a general direction, you certainly don't have to give specific info. 
Well, I loaded the cd, on an older box I have laying around here, it's an old Pll, HP, that isn't altogether stable, she likes to freeze once in a while, not often, but it still does. And I've enjoyed what I've seen so far, but I'm kind of stymied right now. This old Pll only had a 4 gig hd, so I can't even do the updates on it, much less get into Synaptix. So, off I go to ebay to find a bigger hd for the box, then I will have to reload, but at least then I can run it, so I can get to know it. 
I also have another issue, my "working" box, it has a Nvidia graphics card-fx5200, and I've been reading about the issues with that, so I may have to use the VM in order to get it on this box, with Windows XP Pro on it. It's either that, or wait for another distro, that will have all these issues with the Nvidia cards solved.
So, thanks again for answering my post, and have a great night!      wowie

---

### Post by ridgeland on 2007-07-09
Nvidia is easy with Envy.
Envy does all the setup work.
I've used it on two PCs with Nvidia cards.
When you install Ubuntu you'll probably get NV in /etc/X11/xorg.conf for a driver, then just get Envy from Synaptics.  Run Envy and it will determine which Nvidia driver you need and install it for you.
Just a caution:
If you update the kernel you should first uninstall the Nvidia driver then reinstall it after the kernel update.

You'll get better specific support and info in the other categories of UbuntuForums.  Search for Nvidia for example and you'll find lots of suggestions.  Alberto Milone wrote Envy and would probably help you with issues if he recognized the thread title as an Nvidia issue.

Think outside the cheese :)

A question though Wowie,
Why would you install 6.06 rather than 7.04?

---

### Post by uberushaximus on 2007-07-10
> **wowie said:**
> where is Richfleld? You know, just a general direction, you certainly don't have to give specific info. 
[http://en.wikipedia.org/wiki/Richfield%2C_Washington_County%2C_Wisconsin](http://en.wikipedia.org/wiki/Richfield%2C_Washington_County%2C_Wisconsin)
 
> **wowie said:**
> Well, I loaded the cd, on an older box I have laying around here, it's an old Pll, HP, that isn't altogether stable, she likes to freeze once in a while, not often, but it still does. And I've enjoyed what I've seen so far, but I'm kind of stymied right now. This old Pll only had a 4 gig hd, so I can't even do the updates on it, much less get into Synaptix. So, off I go to ebay to find a bigger hd for the box, then I will have to reload, but at least then I can run it, so I can get to know it.

First off, I'd use [xubuntu]("http://www.xubuntu.org/") on that box, or [fluxbox]("http://en.wikipedia.org/wiki/Fluxbox") as a window manager

> **wowie said:**
> I also have another issue, my "working" box, it has a Nvidia graphics card-fx5200, and I've been reading about the issues with that, so I may have to use the VM in order to get it on this box, with Windows XP Pro on it. It's either that, or wait for another distro, that will have all these issues with the Nvidia cards solved.
So, thanks again for answering my post, and have a great night!      wowie

According to [this]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html") your card should work just fine on feisty fawn.

> **ridgeland said:**
> Nvidia is easy with Envy.
Envy does all the setup work.
I've used it on two PCs with Nvidia cards.
When you install Ubuntu you'll probably get NV in /etc/X11/xorg.conf for a driver, then just get Envy from Synaptics.  Run Envy and it will determine which Nvidia driver you need and install it for you.
Just a caution:
If you update the kernel you should first uninstall the Nvidia driver then reinstall it after the kernel update.

You'll get better specific support and info in the other categories of UbuntuForums.  Search for Nvidia for example and you'll find lots of suggestions.  Alberto Milone wrote Envy and would probably help you with issues if he recognized the thread title as an Nvidia issue.

Think outside the cheese :)

A question though Wowie,
Why would you install 6.06 rather than 7.04?

I personally dislike [envy]("http://albertomilone.com/nvidia_scripts1.html"), however, whatever floats your boat though. I find [this]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") cleaner.

---

### Post by herteljt on 2007-07-17
Hi Wowie 

Welcome to the group.  I live in Neenah and if I can be of help please let me know.

---

### Post by wowie on 2007-07-29
Hi uberushaximus,
Thanks for the tips, things have changed quite a lot around here, since I last posted. First I decided to put the LiveCD into another older box that I had laying around here, but I ran into hard drive issues, it was too small, so I had to wait to get another hd, and still couldn't install, so now I'm running this in a vm, on my daily use box. No, I didn't figure that one out myself, my son has been a Linux fan for a long time, and he walked me thru the install of the vmplayer, and then the install of Ubuntu. Works great! I must say! So now I am playing in here, and so far, liking this distro very much. Also, I'm on this distro because my sister is, the one I mentioned earlier, so we are learning together. Actually, she's just waiting for me to catch up, hehehehe  I'm working on it!

And, I wanted to say a big HELLO to herteljt, I was born and raised in Neenah! Thanks for the offer of help, Thanks to all of you!

K, now here's my new issue, and I am looking on the main forum site for this answer, but you know forums, if you don't word you're search just so, you won't easily find the  info you may need. I need to configure my Microsoft Laser 6000 mouse. I actually have the desktop set, but keyboard is working fine, mouse doesn't. It's a 5 button mouse, and I need to configure the thumb button to work, as a back button, (geeze I miss my back button!) and my scroll wheel is acting sluggish-sometimes it will scroll just fine, other times I have to use my pointer to move pages up and down. Does anyone have any links to send, to help me with this? I will be looking on the forums today for this too, but shooting me in the right direction would be most helpful.  Thanks sooo much    :)

Now, just to give you an idea of how far I'm not in here, this vmplayer just went in on Friday night, and all I got done yesturday was getting firefox in here, and doing a little bit on the desktop, just so it's set to my liking. Oh, and I did do updates yesturday-145 of them! I was impressed, on Windows that would have taken a couple of hours, on here it took less than 6 minutes!!!!  I have to say, so far I'm liking this very much!  Oh, and does anyone know about SwiftFox, and Swiftweasel? I've been reading a lot about them in the forums, some say they are much faster, some say not, and have lots of trouble with them. I just have Firefox 1.5.0.12 in here, and I'm not complaining at all. Works great, nice and fast for me.

Anyway, I will check back more often now, sorry I didn't check back and say Hi, at least while I was working out all the other things I had to do.
Thanks again all!    wowie

---

### Post by wowie on 2007-07-29
Hi ridgeland,
hehehehehe, lmfao,  "Think outside the cheese"

---

### Post by wowie on 2007-07-29
Hi all,
Well, I've been all over the forums, found a whole bunch of info on how to set up my mouse in here. Mostly I've learned that I don't need to get imwheel, that I can configure my mouse thru Xorg.config. Only, how do I get to this file???? I've tried to search for it, (do I have to configure my search some special way? Every time I use it, I get no files found???) and I don't know how to find it. Everyone says the same thing, just to do some script changes in this file, only I'm so green, that I don't have a clue how to find anything in here yet! hehehe   I keep reading the forums, but really, I have to tell you, it might as well be written in greek! I'm a baby here, and I need someone to help me with my crawling! So, If anyone could tell me, how to get to my Xorg.config file, to do the changes that I need to do in it, geeze, would I ever appreciate it.  I'm going to go into Ubuntu, thru my vm, and try to get the links that I have been on, just so you know exactly what I'm talking about.   Thanks,  wowie

   [http://ubuntuforums.com/community/Peripherals](http://ubuntuforums.com/community/Peripherals)

[http://ubuntuforums.com/community/ManyButtonsMouseHowto](http://ubuntuforums.com/community/ManyButtonsMouseHowto)

[http://blog.blackdown.de/2005/03/01/tilt-wheel-mouse/](http://blog.blackdown.de/2005/03/01/tilt-wheel-mouse/)

(I used to have a logitech mouse, that had a tilt-wheel, that I used for my back button, just push to the left, and boom, you go back a page, or however many you want. This mouse has a tilt-wheel, and a back/thumb button, but if I could get the tilt-wheel configured to work as my actual back button, hey, happiness would be my name! lol  Any ideas on that one?)

---

### Post by ridgeland on 2007-07-29
Try /etc/X11/xorg.conf
You'll need admin rights so something like:
$ sudo gedit /etc/X11/xorg.conf
I haven't done anything with the mouse myself though.

Always make a backup copy first and/or use # comments to just comment out what you replace when editing system files.

---

### Post by wowie on 2007-08-06
Hi Ridgeland,
Sorry I haven't been around lately, work has been nuts!
Well, here's what's going on now, sheesh, what a pain! I cannot get Ubuntu to install on the older box, the HP PII, I bought another hd, a 30 gig, and found out the hard way that I had to go into the Bios, enable the LDM?? something like that, it tells the computer to recognize a hd larger than 8.4 gig, only way to do that. Well, then I loaded the disk, loads fine from the disk, but when I go to install, I get to the Partitioning part, and that's it, total stall. It's not recognizing the new hd. Well, I bought the hd from ebay, and the seller just sent it in a bubble wrapped mailer, I think it's dead, but I can't be sure, I don't have another box to test it on. So, he sent me a replacement, another 30 gig, but I haven't installed it yet. I'm asscarred, lol  I'm afraid this one won't work either, since I can't test it on any other box than this one. So, here I sit, hd in hand, waiting to get up the nerve to try again! Or, just decide to buy another box, cheap, a PIII, and see if I can get this thing working properly. It seems to me I need to upgrade my testing box anyway. Well, wish me luck! I'll keep you informed
wowie

---

### Post by wowie on 2007-08-06
Hi everyone, and Ridgeland,
Well, here I am again. I installed the new hd, everything went fine, so I loaded Ubuntu, and guess what? It also installed. Wahoooo, I was very happy. Everything went fine with the install, until I rebooted, I get black screen that says "Operating System not found"  I can't get into the bios either. So now what?  Any suggestions anyone? 
Well, I'll be online looking for info, any help would be appreciated.  
Thanks, wowie

---

### Post by ridgeland on 2007-08-06
Hi Wowie,
What is this PC you're installing on?
How much RAM?  Processor?  How old? Windows 98?
With less than 256MB of RAM you should use Xubuntu not Ubuntu.
Or even DSL (Damn Small Linux)
I've had install fail on an old PC due to low RAM.

---

### Post by jamesstansell on 2007-08-07
"Operating system not found" sounds like a message from the BIOS (or maybe a boot ROM?)  Are you able to boot from a CD?

---

### Post by wowie on 2007-08-08
Hi ridgeland, and james (I hope you don't mind me calling you by james, it was just for the sake of typing)
K, the box is an old PII,450 /500mgz, HP Pavilion 6470z. I have 256 of ram in there, I think that's plenty for any PII, I did put in a new battery when I got this, since it's a 1999 computer, and I loaded Win Me on here with no trouble at all, even on the old 4 gig hd. It had a bad sound card with modem in when I got it, so I put a different sound card in, good thing I had one lying around here  :-)   Everything worked fine under Windows-(boy, I hate to say that!)  But, I did do some homework on this, and this box was built to run Win 98SE. 
I can boot from the cd just fine, it will run the live cd no problem, even installed it just fine, just won't ?acknowledge? the installation after the reboot. 
I cannot get back into the Bios, at least I haven't been able to since the installation of Ubuntu, it very well could be me just not hitting the key fast enough, but I've tried every which way you can, and it still won't let me into the bios, and the  "no operating system found" screen looks like it might be DOS, but I can't get a command prompt, the cursur-line  is the flat one that you can't type to.
But, I'm not giving up yet, I really think it may have to do with a bios setting, at least that's what I'm looking into now-well, when I get time, not much of that during the week when I'm working.  I'll check back for any other suggestions you may have, and thanks for hanging in here with me!       wowie

---

### Post by ridgeland on 2007-08-08
Hi Wowie,
You have to be able to get to the BIOS, keep trying to hit keys faster or something.  Maybe search on HP's web site for a manual that explains the key stoke, Usually F1, F2 or F10 or F12, as soon as you turn it on start pecking at the right key until it agrees.  Quite possibly the BIOS is set to only allow boot from CD or network, not the hard-drive.  Or a master boot record problem, but the install should correct that.

When you boot from the LiveCD (install CD) you should be able to find sda1, sda2 etc and see if they are OK.

I have an old Pentium 5? at 200 MHz with 196 MB of RAM.  It runs Xubuntu but not Ubuntu, takes it about 10 minutes to boot.  Once running it's fine for Firefox and Abiword (like OpenOffice->Writer).

I had an issue with an older PC and two hard drives.  It refused to boot from the second hard drive only the first.  Do you have two hard drives?  Two drives may require jumpers to define master and slave.

---

### Post by wowie on 2007-08-09
Hi Ridgeland,
Well, you may very well be correct about it being the older computer, or the mobo is going bad on me. I think it may be the latter, I have been working on this, and now I'm having problems with the mouse and keyboard connecting, or being recognized on boot-up. They did just fine before, I've been using a wired optical ps2 mouse, and a wired ps2 keyboard, just because of the age of the computer. Now they take turns, seems like, on which one will work on boot. I think I just have to give up the ghost, and put this old p2 to rest. I think it's time is up.
I have a question for you though. I have an older ibook, it's a 500mgz, dual usb with firewire, cd rom only, 10 gig hard drive, and 576 ram in it. (the first thing I did with this little ibook, was max out the ram)  I think it's called a Pismo.      Anyway, would I be able to put Ubuntu on the ibook? I think it should work just fine, since they both run on a GUI. I don't have any disks for the ibook, that's one of the draw backs of it, and I bouight it to start learning Mac's, but I don't seem to be doing to well with that, and mostly it sits here, doing nothing, not being used. (I know, I know, seems I'm more windows whipped than I thought!)   Anyway, I don't want to waste the little ibook, but I'm not sure if it's a good idea to put ubuntu on it either.  Let me know what you think, Ridgeland. Oh, I could have a Ubuntu disk for the ibook, I have an old external cdrw, that's Mac compatible, so I would be able to burn the ISO disk for it.  That's a plus for me.   Anyway, I hope to hear from you soon, and Thanks very, very much for all of you're help!      wowie

---

### Post by Ek0nomik on 2007-08-09
> **wowie said:**
> Hi Ridgeland,
Well, you may very well be correct about it being the older computer, or the mobo is going bad on me. I think it may be the latter, I have been working on this, and now I'm having problems with the mouse and keyboard connecting, or being recognized on boot-up. They did just fine before, I've been using a wired optical ps2 mouse, and a wired ps2 keyboard, just because of the age of the computer. Now they take turns, seems like, on which one will work on boot. I think I just have to give up the ghost, and put this old p2 to rest. I think it's time is up.
I have a question for you though. I have an older ibook, it's a 500mgz, dual usb with firewire, cd rom only, 10 gig hard drive, and 576 ram in it. (the first thing I did with this little ibook, was max out the ram)  I think it's called a Pismo.      Anyway, would I be able to put Ubuntu on the ibook? I think it should work just fine, since they both run on a GUI. I don't have any disks for the ibook, that's one of the draw backs of it, and I bouight it to start learning Mac's, but I don't seem to be doing to well with that, and mostly it sits here, doing nothing, not being used. (I know, I know, seems I'm more windows whipped than I thought!)   Anyway, I don't want to waste the little ibook, but I'm not sure if it's a good idea to put ubuntu on it either.  Let me know what you think, Ridgeland. Oh, I could have a Ubuntu disk for the ibook, I have an old external cdrw, that's Mac compatible, so I would be able to burn the ISO disk for it.  That's a plus for me.   Anyway, I hope to hear from you soon, and Thanks very, very much for all of you're help!      wowie

You should be able to install Ubuntu on your other box just fine.  You will notice in my signature my fourth box which runs Ubuntu 7.10 Gutsy Gibbon only has 512MB of RAM and it installed smooth as a whistle.  Gnome only requires 256MB of RAM I believe.  The only downside is the 10GB hard disk which is a bit low.  A fresh install of Ubuntu is around 2.5GB I believe.  Although, as long as you don't use the box to download or store a lot of music and movies, you will actually probably be fine on space if you are only installing software to make use of the operating system.

---

### Post by ridgeland on 2007-08-10
My last PC ran fine with 512 MB of RAM.  I had Ubuntu, Fedora, SuSE and tried many others.   I use OS partitions of about 8GB.  But I keep Data, Images, Music on a partition of 120GB.  10GB will be fine for learning an OS and downloading lots of packages to try.
I haven't tried the Mac world though.  The processor matters but from 
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)
searching for "ibook" I see others have done it with earlier versions.
Try it :)
When you install don't forget to create a swap partition.  I would try 1GB (or just 576MB).
Once installed from the terminal use 
$ df 
to see how much of the remaining 9 GB in / is used and how much is free.  You'll see you have lots of room to grow.

---

### Post by Ek0nomik on 2007-08-10
> **ridgeland said:**
> My last PC ran fine with 512 MB of RAM.  I had Ubuntu, Fedora, SuSE and tried many others.   I use OS partitions of about 8GB.  But I keep Data, Images, Music on a partition of 120GB.  10GB will be fine for learning an OS and downloading lots of packages to try.
I haven't tried the Mac world though.  The processor matters but from 
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)
searching for "ibook" I see others have done it with earlier versions.
Try it :)
When you install don't forget to create a swap partition.  I would try 1GB (or just 576MB).
Once installed from the terminal use 
$ df 
to see how much of the remaining 9 GB in / is used and how much is free.  You'll see you have lots of room to grow.

I installed Fedora last week, and while it looks amazing, the RPM base scared me away.  I installed Gutsy Gibbon on it instead.

---

### Post by ridgeland on 2007-08-10
I started with FedoraCore 4, FC5, FC6, SuSE 10.1, SuSE10.2, ..... I use Ubuntu now as my main OS.  
Like package management there were other differences such as the use of sudo rather than root that made switching difficult.  I didn't switch to Ubuntu until I got help from the forum about user ID 500.  All my legacy data, music etc was owned by user 500.  Ubuntu starts at 1000 and blocks lower IDs from user maintenance by default!  The forums helped me set up user 500.  All my Linux OSs (several on each PC) share Data and my wife and I share partitions by NFS.  So having the same user ID for both of us on all PCs and OSs is very important.  
I've gotten tired of distro-hopping.  I'll still try Fedora 8 and SuSE 10.3 this fall.

---

### Post by wowie on 2007-08-11
Hi Ridge,
Well, I've been reading-alot!-and it sounds like some peeps have had a lot of trouble with the older ibooks, and others have not. All problems they had with the Ubuntu install, all seemed to be different for each box, so I'll probably be on the other forum for a while, because I'm going to need all the help I can get!  hehehe
I like you're testing box ridge, I've been all over ebay looking for something just like that! I was all ready to buy, when my son told me to try to put it on the ibook. I thought that was a great idea, since I don't like to waste a computer, and this is wasting away here, so off I go to the main forum site.  Wish me luck!!  I will check back often, just to let you know how things are going, and to ask more questions, I'm sure  lol  Thanks again for all you're help, all of you.     wowie

---

### Post by wowie on 2007-08-13
Hi Ridgeland, and everyone,
Well, a lot has changed since the last time I posted. I did a lot more research on putting Ubuntu on the Mac, and dedided not to do it. Mainly because, well, wowowow, I sure would learn a lot! It's not so easy, not that that scares me, but timewise, I have a problem. If I were like my sister, and didn't have to work, I wouln't hesitate to take this on, but, unfortunately, I work absolutely crazy hours, so I'm not going to do it. Another reason is that my Son is now going to buy himself a new laptop, he needs one for school, and he's ready to upgrade (you all aught to know, when a geek is ready to upgrade, don't get in the way!  :lolflag: 
So, I get to inherit the old laptop, hey, it's not so bad, an HP, 1.8 with a gig of ram, cdrw, i think it has like 4 usb's, and he has this thing tweaked to the nines! And he has linux on it already, although he has Gentu on it. But he will put Ubuntu on it for me, just load it on there mind you, then he'll make me do the rest. I wouldn't have it any other way! I don't learn if he set's up all the software and hardware for me.  But, this is going to take about a month, children never move fast enough for parents, do they???  hehehehe   So, I thank everyone that has sent their help, but unil I get the laptop, I can't do anything.   :(    I'll check in now and then, just to say HI!    Thanks again, you guys rock!   :guitar:         wowie

---

### Post by Ek0nomik on 2007-08-14
> **wowie said:**
> Hi Ridgeland, and everyone,
Well, a lot has changed since the last time I posted. I did a lot more research on putting Ubuntu on the Mac, and dedided not to do it. Mainly because, well, wowowow, I sure would learn a lot! It's not so easy, not that that scares me, but timewise, I have a problem. If I were like my sister, and didn't have to work, I wouln't hesitate to take this on, but, unfortunately, I work absolutely crazy hours, so I'm not going to do it. Another reason is that my Son is now going to buy himself a new laptop, he needs one for school, and he's ready to upgrade (you all aught to know, when a geek is ready to upgrade, don't get in the way!  :lolflag: 
So, I get to inherit the old laptop, hey, it's not so bad, an HP, 1.8 with a gig of ram, cdrw, i think it has like 4 usb's, and he has this thing tweaked to the nines! And he has linux on it already, although he has Gentu on it. But he will put Ubuntu on it for me, just load it on there mind you, then he'll make me do the rest. I wouldn't have it any other way! I don't learn if he set's up all the software and hardware for me.  But, this is going to take about a month, children never move fast enough for parents, do they???  hehehehe   So, I thank everyone that has sent their help, but unil I get the laptop, I can't do anything.   :(    I'll check in now and then, just to say HI!    Thanks again, you guys rock!   :guitar:         wowie



He's a Gentoo user, eh?  He must know a bit about Linux then because Gentoo is a customizable king.  I don't have the guts or patience to go through compiling everything myself, at least not yet.  :)

Keep checking back to the Wisconsin LoCo *wowie*, always good to have more members active in our state.  :)

---

