---
title: "Gentoo vs Kubumtu"
date: 2005-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by jabster on 2005-10-15
Hi.
I am currently runnng Gentoo, but am considering switching over to kubuntu. I was running Mandrake, but consistently having to reinstall for every release was getting to be a pain, and RPM-dependency hell hit me a few too many times.

Anyway, I have nothing against gentoo, but it is sort of hard to upgrade at times, for example, kde to the current version. I basically end up running an ~x86 (untested/unstable) system in order to get kde3.4.4. And certain aspects of emerge are quite a pain.

So I was thinking of going back to a more "normal" distro, and I've heard much good things about this one.

Couple of questions:
1.What is upgrading like? with gentoo, you install once, then just continually emerge. You never have to install from scratch again. Similar with kubuntoo? From what I've heard you just apt-get, and end up with an up to date system.

2. How's the amd64 version? I'll be getting my athlon64 3000+ in a few days, and, if there are no shortcomings with it, I may end up installing kubuntu rather than gentoo.

3. How up to date are the programs? For example, I was really looking forward to trying the latest amarok (1.3), and it is easy with some accept_keywords trickery in gentoo. How up to date or recent are packages in kubuntu. How does the package list compare to those available for gentoo?

Thanks,
john

---

### Post by zekolas on 2005-10-15
[QUOTE=jabster]Hi.

Couple of questions:
1.What is upgrading like? with gentoo, you install once, then just continually emerge. You never have to install from scratch again. Similar with kubuntoo? From what I've heard you just apt-get, and end up with an up to date system.

2. How's the amd64 version? I'll be getting my athlon64 3000+ in a few days, and, if there are no shortcomings with it, I may end up installing kubuntu rather than gentoo.

3. How up to date are the programs? For example, I was really looking forward to trying the latest amarok (1.3), and it is easy with some accept_keywords trickery in gentoo. How up to date or recent are packages in kubuntu. How does the package list compare to those available for gentoo?
[/QUOTE]

1. Ubuntu uses apt-get like debian. So upgrading programs is as simple as running the command 
apt-get upgrade 
will upgrade all your installed packeges. To upgrade to a new realease of ubuntu all you do is change your apt repositorys to point to the new release then run two commands
apt-get update
apt-get dist-upgrade
So it is fairly simple.

2. AMD64 is supported as well as any other linux distro out there. However there are small things like no 64 bit flash, or many plug ins or codecs do not work in the 64 bit version, however this is true about all 64 bit linux distros and is not specific to ubuntu.

3. Ubuntu is very up to date, they come out with a new ubuntu realease every 6 months, and in between realeases they have updates for current realeases. Also you can add other apt repositories besides the "offical" ones that may offer the latest software.

Ok I realised I used ubuntu as and example here, but ubuntu is no differnt from kubuntu aside from ubuntu has gnome as a default desktop and Kubuntu and KDE.

---

### Post by jabster on 2005-10-15
[QUOTE=zekolas]
2. AMD64 is supported as well as any other linux distro out there. However there are small things like no 64 bit flash, or many plug ins or codecs do not work in the 64 bit version, however this is true about all 64 bit linux distros and is not specific to ubuntu.
[/QUOTE]

Hi. Thx for the reply.

I know there's some workarounds for the 32-64 bit stuff (I think konq accepts 32bit plugins now) such as a 32bit chroot and OO.o-bin for gentoo. Also, some of the 32-bit media codecs don't work.

The "bin" packages in gentoo allow the use of 32-bit codecs and flash, etc. Des all the multimedia stuff work in 64bit k/ubuntu as well? I'm assuming the 32-bit chroot is non-gentoo specific?

Just trying to make sure I can still play all my movies once I go 64bit. If it's a major pain I might just stick with gentoo for now.

thanks,
john

---

### Post by brentoboy on 2005-10-15
if you could use kde and amarok in gentoo, ubuntu will be a cake walk.

Im running athlon64 3000+ with no worries.

I did have issues with the nv driver for my 6200 geforce - pcie card, but they were fixed from downloading the official nvidia drivers and using them.

if you have installed gentoo, you have seen enough of the command line and understand the lingo enough to breeze right through ubuntu.

I picked ubuntu for 3 reasons: 

1) amd64 is one of only 3 platforms - it gets focus from the main team - it isnt just a side project where they compile it and hope it works - its an officially supported version.

2) its based on debian - so I get to use apt (I love synaptic) apt is the best package manager I have ever used. 

3) Its free.

---

### Post by t2kburl on 2005-10-15
My opinion:   I'd definately go with Kubuntu on your new system ... maybe split partitions so you can experiment with 64-bit to see if you can live with its shortcomings (which also exist in gentoo) while living comfortably in 32 bit.
If for no other reason ... Installing kubuntu took me 5 presses of the enter key, setup partitions (easy to navigate text interface), set time zone, enter username and password and done.
Nothing like the Gentoo install which reminds me of having teeth pulled

---

### Post by jabster on 2005-10-15
I'm d/l-ing the 32-bit live cd  (64-bit components are still on the UPS truck) to check it out. I will at least try kubuntu first. Way easier than trying gentoo first. :-) Problem with live-cds is that you really only get a feel for the GUI. Don't really give you the whole sysadmin/upgrading/all the pitfalls experiences.

thx for the replies.

=john

---

### Post by gorod on 2005-10-17
Just wanted to post my experiences. I tried  breezy@amd64 after 2 years of gentoo and allthough i liked it i ran into few problems which are probably specific to a gentoo user. 

 - very little 32bit compatibility so to run simple things like 32bit mplayer you have to spend much time (even if you know what you are doing). Also that whole 64/32bit schouldn't be in my opinion. I mean you can boot with 64bit kernel and 32bit everything else , so 32bit apps are as native to amd64 as 64bit apps why lots of them getting masked while using synaptic.

 - lots of packages are not in the packaging system so you have to hunt for all reporistories that have that packages what you want (and a version what you want). While in gentoo that was only a line in the config-file.

- also i used bittornado and wxgtk2.4 was a dependancy, but you can use it with wxgtk 2.6 which is more stable and doesn't have memory leaks with gtk2. So to use for example amule and bittornado together you have to use both of wxgtk which is actually not needed so you end up wasting diskspace on that. (well in gentoo you have 400mb portage tree which is also an insane waste of space)

- When i first started breezy it just froze. There should have been an option somewhere in the installation program to chooose your xorg  driver.

Well i liked ubuntu and will try it also in the future , but i am kind of too used to portage and it is for me quite less of an effor to maintain gentoo system than ubuntu. But if you re not as used to portage as me i think ubuntu will be a great choice.

---

### Post by reub2000 on 2005-10-17
I tried the amd64 version of gentoo. A problem with emul-linux-x86-sdl caused many 32-bit sdl apps like pearpc to be unable to compile. Also, 32-bit kernel modules will not run on a 64 bit kernel. I couldn't tell the difference between a 64-bit and 32-bit installation. 64-bit is mainly for making better usage of a ****load of ram. I went back to 32-bit gentoo.

Gentoo's portage contains a lot more packages than ubuntu's apt sources. It contains pretty much everything, including commercial software. The ebuilds are basiclly scripts that can do pretty much anything, from copying game data of the ut2004 cds, to using cvs to download cedega source code. There also adaptable, being able to be compiled with different versions of their dependencies, and with features enabled or disabled. However it does a poor job of trying to keep the system intact and working. Upgrading a package that is depended on by others can, and will break the packages that depend on it. While it's a simple task to recompile the program, portage does not notify you that any programs depend on the package your upgrading. Also, portage will not check if anything depends on a package when unmerging it. However "emerge -uDav world" will reinstall the package. "emerge -e world" will fix these issues, however, it will probably take a couple of days. Apt checks what packages depends on a package when upgrading it or uninstalling it, and generally does a better job at keeping your system from just falling apart.

The installation are worlds apart. While many people complain that gentoo's installer is hard, I find that it allows me to set up my system the way I want. For example I usually like to set hard drive partitions I rarely use to "noauto". Not many installers will let me do that. Plus I like my way of organizing /etc/fstab much better than most distros. Also, I have to manually set up my xorg.conf since I have a dual-head setup. I also like to compile only drivers I use. With only 1 ethernet driver, theres no guessing weather eth0 is the oboard ethernet, or my 3com 3c905c, or weather hw:0 is my onboard sound or my sound card.

I think that you should install both and see which one you like. Both cater to 2 diffrent types of users.

---

### Post by TheJoker on 2005-10-17
my 2p...

I have been running Debian for a very long time, and when time came for a new workstation I oped for an AMD64 powered by Gentoo. And despite the scare-stories I've heard about Gentoo, it wasn't such a bad thing to install. However, I never really got everything configured and working perfectly (for example I had forgotten some character encodings in my USB stuff and thus didn't work untill I should have recompiled my kernel - which I didn't).
The upside to Gentoo is, as mentioned, that "everything" is in Portage, Skype, VMWare etc etc... Lovely. 
The downside is that once in a while you end up having your machine recompile *everything* for three days. *Not a very good uptime!* As my girlfriends machine and my laptop had been running Kubuntu very nicely I decided to switch (especially as I managed to remove some needed packages with emerge LOL!).
Now I find that Kubuntu works better - once I got it running - I had problems with Powernowd etc. I can't get Skype, Opera or VMWare running without that "Typical Linux Fiddling"(tm) ;) On the other hand I can stick in my USB gadgets and the mostly "just pop-up" and everything works fine. YAY!

Oh, and I'm a Linux *user*, not a Linux *tinkerer* nor Linux *hacker* - I like stuff that "just works". 

For me I think I'll be happier with Kubuntu in the Long run - it already feels really nice even if I've just been running Kubuntu for a few weeks.

---

### Post by Biased turkey on 2005-10-17
Here is my frantic  Linux distros installs  on my 2 hardisks over the latest couple of months:

July:
1) Fedora core3
2) nothing

August:
1) Debian Sarge
2) Gentoo 2005 32 bits x86 ( just to see if I could install Gentoo )
I was satisfied with both, but I have an AMD64 CPU so wanted to make the big jump to Linux 64 bits

1st half of September:
1) Debian sarge
2) Gentoo AMD64  and of course discovered that somme 32 bits applications are a real pain in the neck to run. I was thinking going back to Gentoo x86
But compiling SDL programs rocks on the AMD64

2nd half of september: I discovered Ubuntu
1) Ubuntu 5.04 + KDE
2) Gentoo AMD64.

Yesterday:
1) Ubuntu 5.10 , didn't even bother trying to upgrade from 5.04
Like with Ubuntu 5.05 I'll use it on a daytoday base like email, surfing the web, video ,graphics : Gimp and blender, gaming and C++ programming
2) Gentoo AMD64, I think I'll keep it on my 2nd drive, but just for experimenting
I think I found the perfect match now : Ubuntu 32 bits + Gentoo AMD64

I'll swith to Ubuntu64 for the next release, by that time I hope Ubuntu64 to be 100% functional and as easy to run as the Ubuntu32 bits version.

My $ .017  ( $.02 Canadian )

---

### Post by jabster on 2005-10-21
[QUOTE=Biased turkey]
Yesterday:
1) Ubuntu 5.10 , didn't even bother trying to upgrade from 5.04
Like with Ubuntu 5.05 I'll use it on a daytoday base like email, surfing the web, video ,graphics : Gimp and blender, gaming and C++ programming
2) Gentoo AMD64, I think I'll keep it on my 2nd drive, but just for experimenting
I think I found the perfect match now : Ubuntu 32 bits + Gentoo AMD64
[/QUOTE]
WEll, I have Kubuntu installed finally. Had some problems, and ended up needing a new bios chip from Asus to recognize my Venice-core AMD64-3000+. So. Finally running now. Easier than a mandrake install. Cool.

Keeps freezing up tho. Apparently I need to install the nvidia drivers. Will do so next. 

So, once I get the nvidia drivers installed, hopefully I'll be able to use this thing for awhile and see how it works. May end up doing the 32bit OS on a 64bit processor tho until more stuff "just works" on 64bit.

-john

---

### Post by BlueNoteMKVI on 2005-10-21
I run Gentoo on my laptop and a server.  I tried Gentoo64 on my desktop box and it was a nightmare - every time I emerged something, something would break.  I spent days dinking with it.

I just installed Kubuntu on that same box.  So far I haven't been terribly impressed.  The install was easy (especially compared to Gentoo) but I've had problems setting up a static IP address, trying to use administrator mode in KDE's control panel, and currently I'm trying to get a particular version of a package to install using apt.  It's looking like a long night for me.

---

### Post by jabster on 2005-10-22
WEll, installing the nvidia driver appears to have ended all my instablity problems. Hasn't locked up once since I apt-get installed nvidia-glx. STill seems odd that nv driver could do 1600x1200, and nvidia only does 1280x1024. Monitor says 1280x1024 max resolution too. Wierd. Oh well.

In some ways, apt-get is nicer than portage. Quicker, that's for sure. :-) 30 minutes or so to be fully up and running.

No flash yet. Will look at more of that stuff tomorrow. But overall kubuntu seems pretty good. Quick.

Can't view my avi's either. Gotta lookinto that as well. Worst cast, I'll just grab the x86 install CD and wait a bit until the 64bit version is feature complete.

-john

---

### Post by fistfullofroses on 2005-10-26
In Ubuntu and Kubuntu one never needs to reinstall this is very true, 'apt-get update' followed by an 'apt-get upgrade' will bring your full system up to date. 'apt-get dist-upgrade' will upgrade your system to the latest and greatest version of Ubuntu or Kubuntu. The AMD64 version is the most complete distro I have seen so far for AMD64s. The only real drawback I have seen is the lack of Flash for web browsing, but as far as I know this is because Macromedia has not made a 64bit Flash. As far as the programs themselves, I would say that they are as up to date as one can get. I was hesitant with Ubuntu at first, for I heard that it was debian based, and debian waits quite a long time to update their program list. With Ubuntu this was not a problem. Every program is the latest and greatest, and if not will be within a few days/weeks.

---

### Post by BlueNoteMKVI on 2005-12-22
I've been running Ubuntu for two months now on several machines here at home.  I've converted my backup server, my main desktop and my main laptop from Gentoo to Ubuntu.  My wife's laptop was running Xandros, I've converted that as well.  My webservers are still running CentOS only because my control panel software isn't supported on anything other than a RedHat variant.

My experience:

-64 bit is a waste of time unless you like to tinker.  I never got mp3 playback to work correctly, FireFox crashed on a regular basis, the administrator mode in the system control panel did not work, files downloaded through giFT were constantly marked as corrupted, etc, etc.  I still have it installed on a separate partition and I log in now and then to do an apt-get upgrade.  Until I hear about some pretty major improvements I'm working in 32-bit.

-Gentoo is more up-to-date and more flexible.  If you must have a certain version of some package, it's easier to make that happen with Portage than with Apt.  If it's important to you that your computer is always bleeding-edge up-to-date, Ubuntu is not necessarily for you.

-Ubuntu (excluding the 64-bit version) is far more stable.  Gentoo broke on me on a regular basis.  Ubuntu has not broken.  This is probably directly related to the above statement.  It's not as far behind as Debian, but not as up as Gentoo.  I find it to be a very happy medium.

-Gentoo claims to be the fastest distro on the planet because everything is tweaked for your particular machine.  When I first loaded Ubuntu it did seem a bit slower but not enough to make a difference in everyday work.  Once I tweaked things a bit to remove modules that I did not need (ie, wireless drivers on this box with no wifi card) it boots up quickly and runs well.  Any slight difference in speed that might be there I more than make up for in regained productivity from not dinking with the most recent broken package from Portage.

-Apt is great.  From my personal experience it works as well as Portage in nearly everything, except installing a particular software version.  It is of course much faster as you're not compiling everything but simply installing binaries.  I have not had occasion to try a dist-upgrade, but from seeing what happened to those who tried going from 5.04 to 5.10 I think I may wait a while when the next big upgrade comes out.

My advice then, make the switch.  If you have the spare room to install on a separate partition, that's a great way to start - especially if you have /home in its own partition.  That's the way my main desktop box is set up, so my 64-bit install and my 32-bit install have all the same files and most of the same configuration, at least as far as my desktop goes.

---

