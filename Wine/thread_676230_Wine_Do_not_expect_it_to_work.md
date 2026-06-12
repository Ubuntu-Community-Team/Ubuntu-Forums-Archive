---
title: "Wine: Do not expect it to work"
date: 2008-01-23
forum: Wine
---

### Post by Game_boy on 2008-01-23
Wine is a great program; I believe it is essential for getting Windows users to consider migrating to Linux.

However, when asking questions about it, I would really, really like if people stopped *complaining* that it doesn't work. It's a miracle *anything at all* in Wine works, and as such your bug is neither special nor deserving of the developers' attention.

When your program doesn't work and the community has helped you conclude that simple option tweaking won't work, do not start complaining to the Wine team or trying to contact them about your bug. Unlike normal software, Wine will *never* have a stable or feature-complete release. They know that millions of bugs exist, and pursuing them to tell them about problem X in Y app won't help. 

Each Wine contributor already has *thousands* of applications that are known not to work and is trying to fix general bugs rather than specific issues. In later versions, this general bug fixing will turn into improvement in your application.

If there is anything you can do to help, it is by specifically pointing out where Wine differs from the Windows API and precisely what needs to be written to solve this.

My conclusion is that it is fine getting small help for your applications, but don't be surprised when applications completely fail due to major gaps in the implementation - this is on purpose and no amount of ranting will solve it.

Whiners - thank you and good day.

---

### Post by bruhja on 2008-01-24
WOW!!!! people actualy bash developers who give them **free** software????? *shakes head with dismay.:confused:

---

### Post by constchar* on 2008-01-28
> **Game_boy said:**
> When your program doesn't work and the community has helped you conclude that simple option tweaking won't work, do not start complaining to the Wine team or trying to contact them about your bug.

"Bugs" are often actually configuration problems so insted of complaining you
can go to [http://appdb.winehq.org/](http://appdb.winehq.org/) since AppDB will often already have fixes
to your "bug" already! (Yes its true!)

A good example would be
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7500](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7500)
which has installation instructions and some tweaking instructions.

And if all else fails check [http://bugs.winehq.org/](http://bugs.winehq.org/) to see if anyone has filed
a similar report to your "Bug" and has a temporary fix.

My last and final suggestion is to make a custom compile of Wine since custom
compiles are compiled specifically to your machine and your configuration by going
to [http://www.winehq.org/?announce=latest](http://www.winehq.org/?announce=latest) and downloading the source package,
example:

```

noob@localhost: cd ~
noob@localhost: tar -xvf wine-0.9.54.tar.bz2
...
noob@localhost:  cd wine-0.9.54
noob@localhost: ./tools/wineinstall

```

the WineInstall script makes making custom compiles relatively easy and of
course you can always do it the old fashioned way:

```

noob@localhost: ./configure
noob@localhost: make
noob@localhost: sudo make install

```

---

### Post by ELD on 2008-01-29
constchar* 
If i do the custom compile option how easy is it to remove it or to upgrade?
Thanks for the great posts people.

---

### Post by Northsider on 2008-02-01
I used to get angry at Wine...but to what purpose?  That's why I still have my dual boot for those fesky XP apps that will only work in XP.

---

### Post by Sockerdrickan on 2008-02-03
> **Northsider said:**
> I used to get angry at Wine...but to what purpose?  That's why I still have my dual boot for those fesky XP apps that will only work in XP.

[www.virtualbox.org](www.virtualbox.org) :KS

---

### Post by criskat777 on 2008-02-03
Dang, Wine has bin a big head ache. never got anything to work on it no mater how much time i put  in to it. looked all over for good wiki and how to's with no luck. At the end i just gave up and for me that is very heavy to admit. BUT IN NO WAY DO I BLAME THE DEV. TEAM. Remember there just trying to make Yugo parts work on a Mercedes  :)

---

### Post by Sillywombat on 2008-02-05
Look at it this way, there are so many bugs in MW to start with, plus the generally high resources it uses. I consider it a mirracle that the WINE team have managed to make even a couple of programs work stably.

And dont forget, before using it, go on their wiki site and check the compatibility page. They have a huge liste of programs that will, and wont work. With help on how to install and tips about the common bugs.

---

### Post by cogadh on 2008-02-06
While I do agree that no one should ever blame the Wine devs when their Windows app does not work correctly, discouraging bug reports is not the way to address it. Wine will never improve if users don't report problems with specific applications. A problem in one app may indicate a larger bug that will eventually effect other apps and if those bugs are not reported, the devs can never research and address them. AppDB is intentionally set up for users to report problems with specific applications, so that the devs can use those reports to identify areas that need to be worked on. Additionally, the bug reports on AppDB can assist other users with identifying a proper course of action to take when troubleshooting a problem application in Wine.

So by all means, no one should ever rant or blame the Wine devs if their Windows app doesn't work, but they most definitely should file a bug report on that app (or add to an existing bug report) in AppDB.

---

### Post by Northsider on 2008-02-06
> **Tux0r said:**
> [www.virtualbox.org](www.virtualbox.org) :KS

What is this virtual box you speak of?  :popcorn:

---

### Post by cogadh on 2008-02-07
It a virtual machine client. It allows you to install Windows on a virtual machine that runs within Linux. With the exception of most modern games, it will allow you to run almost all Windows software in its native environment while still using Linux.

---

### Post by Northsider on 2008-02-07
I've used VMware in windows...same thing?

---

### Post by Sammi on 2008-02-07
VMware = Coca Cola
Virtualbox = Pepsi

But keep in mind that neither will do 3D, or at least not very well.

---

### Post by Northsider on 2008-02-07
I LOVE PEPSI!  hehe, gonna give virtualbox a try then

---

### Post by Alucard-sama on 2008-02-21
I have this friend who points out WINE not running all windows progam's flawlessly as one of the faults in Linux as an Operating System. This greatly angers me because it's a miracle that ANY Windows programs work in Linux Let alone work functionally, When I see Windows running a Linux GUI application at all -let alone at a functional or native speed- I'll be amazed. So people can stop bitching IMHO

---

### Post by Sammi on 2008-02-21
> **Alucard-sama said:**
> I have this friend who points out WINE not running all windows progam's flawlessly as one of the faults in Linux as an Operating System. This greatly angers me because it's a miracle that ANY Windows programs work in Linux Let alone work functionally, When I see Windows running a Linux GUI application at all -let alone at a functional or native speed- I'll be amazed. So people can stop bitching IMHOWhen Windows program work in Linux, it's often because of Linux hackers.

When Linux programs work in Windows, it's again often to the credit of Linux hackers.

I don't get why anyone would credit anything  on the OS interoperability front to MS. Don't get me wrong, I'm not a mindless zombie MS basher, I just think everyone will have to concede that they're as anti OS interoperability as you can get, and that it really is a miracle that Wine is as good as it is.

---

### Post by jimcooncat on 2008-02-24
'Tis true but funny: Most of the time I have problems with Windows programs on Windows!

When things go wrong with an app on Linux, many times I have a shot at fixing them, or very simple purge/reinstall works. Not so with proprietary software.

I'm afraid I've given up hope on Wine, and conceded to using virtualized Windows sessions for the apps I need. 

But I think thing would work better if Wine could import some native dll's from an existing Windows install when they're available. Do you know if this can be done? Kind of like Captive NTFS did?

---

### Post by Game_boy on 2008-02-25
> **jimcooncat said:**
> 'Tis true but funny: Most of the time I have problems with Windows programs on Windows!

When things go wrong with an app on Linux, many times I have a shot at fixing them, or very simple purge/reinstall works. Not so with proprietary software.

I'm afraid I've given up hope on Wine, and conceded to using virtualized Windows sessions for the apps I need. 

But I think thing would work better if Wine could import some native dll's from an existing Windows install when they're available. Do you know if this can be done? Kind of like Captive NTFS did?

Copy them over the existing Wine DLLs, and using winecfg to set them as overridded?

---

### Post by gnome.youbuntoo on 2008-03-02
> **Northsider said:**
> What is this virtual box you speak of?  :popcorn:
innotek VirtualBox is a family of powerful x86 virtualization products for enterprise as well as home use. Not only is VirtualBox an extremely feature rich, high performance product for enterprise customers, it is also the only professional solution that is freely available as Open Source Software under the terms of the GNU General Public License (GPL). See "About VirtualBox" for an introduction; see "innotek" for more about our company. 

Presently, VirtualBox runs on Windows, Linux, Macintosh and OpenSolaris hosts and supports a large number of guest operating systems including but not limited to Windows (NT 4.0, 2000, XP, Server 2003, Vista), DOS/Windows 3.x, Linux (2.4 and 2.6), and OpenBSD. 

VirtualBox is being actively developed with frequent releases and has an ever growing list of features, supported guest operating systems and platforms it runs on. VirtualBox is a community effort backed by a dedicated company: everyone is encouraged to contribute while innotek ensures the product always meets professional quality criteria. 

On this site, you can find sources, binaries, documentation and other resources for VirtualBox. If you are interested in VirtualBox (both as a user, or possibly as a contributor), this website is for you.

---

### Post by daInvincibleGama on 2008-03-05
> **jimcooncat said:**
> 'Tis true but funny: Most of the time I have problems with Windows programs on Windows!

Yes. The Windows API has so many little bugs and quirks that its a surprise even some Windows apps like uTorrent and ImgBurn and such work that well(Most of them don't) . It's ridiculously hard to reimplement not only the features but also the bugs. Yes, bugs:popcorn:.

> **jimcooncat said:**
> But I think thing would work better if Wine could import some native dll's from an existing Windows install when they're available. Do you know if this can be done? Kind of like Captive NTFS did?

Wine attempts to be a cleanroom reimplementation of the Windows API. Its possible to use DLL overrides in Wine although admittedly its a little complex. However, they cannot legally redistribute Windows DLLs to make things work right. Windows is proprietary and the license forbids it. Only if you own a copy of Windows does fair use come into play for WinDLLs on Wine.

---

### Post by Keltenbleich on 2008-03-05
I understand that I'd be better off migrating to LINUX and using open source software in order to dispense with WINE, than trying to use it on a LINUX platform to run WINDOWS software. This does make sense to me.

---

### Post by jimcooncat on 2008-03-06
> **Keltenbleich said:**
> I understand that I'd be better off migrating to LINUX and using open source software in order to dispense with WINE, than trying to use it on a LINUX platform to run WINDOWS software. This does make sense to me.

The only thing I'm running Windows for now (both home and office) is Quickbooks and MS Access. They have me quite locked-in, and it's a shame. I've taken to using Virtualbox for those programs, but I'll be looking forward to using KVM instead once I get my head wrapped around it.

For everything else, I use Ubuntu. Once you migrate over, you'll appreciate how easy it is to keep security updates caught up, especially if you take care of multiple computers. It's also pretty much a one-stop shop if you need advice on running programs, too. I was very frustrated with having to deal with multiple software vendors.

---

### Post by DrMega on 2008-03-12
I think WINE is great. If there is a Windows app that I really need/want to use then quite often WINE will run it. If it won't, I can always boot into Windows. I think the WINE development team have done really good work.

---

### Post by Eddie Wilson on 2008-03-18
I find this thread title really misleading. What is the purpose of this? I'm sorry you feel like you do but WINE runs a lot more then you give it credit for. Are you saying that the WINE devs are wasting their time developing WINE? I don't really understand what you are trying to say about trying to get someone to migrate to linux and using WINE to get them to try. With your way of thinking isn't that like lying to them? WINE is a great app and I've been using it for years. If you want to try to convert someone from Windows to Linux and they say they HAVE to run a Windows program then tell them about Crossover Linux and then after that you can tell them to try WINE first. Also I have found from experience that most of the time if you try to get a person to use a VM in order to migrate they will say what is the use. You still  have to own Windows don't you? You must answer yes. As far as reporting bugs to the WINE devs, I feel that is none of your business. If you feel that it doesn't help then don't do it, but you shouldn't try to get other people not to report bugs with WINE. The WINE devs may not be interested in a certain program not working but they might be interested in why it doesn't work. As far as complaining that WINE doesn't work, it does work, just not for all apps. And if an app doesn't work, I don't whine, I don't complain, I use a linux app.

Eddie

---

### Post by hvac3901 on 2008-03-21
You know i never bothered to read this until now, and i have to say its pretty depressing. I perceive maybe it wasn't a pleasant day for you when you posted, maybe.

If no one should expect it to work why do you bother developing it? its really depressing, lots of bad energy in between those lines, seriously, i almost got fed up with Ubuntu because of it, it isn't an easy thing to give up all your windows stuff, and switch cold turkey, wine is a hope that maybe we don't loose so much, and there you are STICKY at the top with all the negativity

but yeah thanks for saying don't expect it to work nice heads up. ;).

---

### Post by Crash 0verride on 2008-03-23
BLAME TO PROGRAMS LOL
You blame the programs for not being open source and not making a version for linux

---

### Post by Sammi on 2008-03-23
@ Eddie Wilson & hvac3901

The point of the tread is not to belittle the effort that has been put in to making Wine, nor to say that Wine is bad in any way.

Wine is a wonderful piece of code. And we love it because it enables us to enjoy some of the best applications that are otherwise windows-only.

The point is that Wine is not done yet. It hasn't reached 100% compatibility with Windows and it will be some time before it does. Wine has some warts still and does not always work. It would be disastrous if we kept saying that it was perfect, when it's not. For the time being it is better to say things as they are, rather than to promise something that Wine can't possibly deliver to - YET.

---

### Post by Black Hawk on 2008-03-24
I find WINE to work pretty well. It even ran an old win 3.11 app that wouldn't work on any of the nt based os's. Every app i've tried in wine works, some with more hacking than others. The only exception is Office 07

---

### Post by zhanglini on 2008-03-28
Yeah, I installed Wine and nothing works with it.
Excel, some FX software, Sopcast, you name it, nothing works under wine.

---

### Post by roberto.eiberle on 2008-03-29
I see I am not alone, it's really terrible, my windows apps don't work with wine and my hardware won't work with vista, so I am stuck and must use excellent opensorce for free, to bad.

---

### Post by wawadave on 2008-04-02
You will finally see windoz start to drop off the map when any or most windoz apps can be run easily on linux.

---

### Post by GeekGirl1 on 2008-04-12
I just tried Wine to see what it can do for me. My interest is for Quicken 2007 Premier and MS Excel. I checked the database, [http://appdb.winehq.org/](http://appdb.winehq.org/), and found that Quicken 2007 crashes. I tried it anyway, Quicken crashed in a bad way.

MS Excel ran, but MS wanted me to install the application for a different user. That is not acceptable for me. It's already installed in MS Windows. Steam would not start (Half-Life 2, etc.).

From either running wine directly, or as an indirect problem of the Quicken 2007 Premier crash, MS Windows was broken. The Generic Host Processor service (svchost.exe) failed, causing major problems at startup. Also, the registry was corrupted. I restored the registry from a backup, but the problems persisted. The only solution was a complete format / restore from my most recent MS Windows backup.

I'm dual-booting with Hardy 8.04 LTS Beta, AMD 64-bit.  Hardy survived just fine. The only tweaks I needed to do were to resync my profiles of Thunderbird and Firefox (using MS Windows profiles) and reinstall the grub bootloader on my Windows partition.

I see most of the points about emulation have already been made in this forum, so I won't repeat them. I am not discouraged by these problems - I just need to find the right emulator. VirtualBox is next, but not until after 8.04 is released.

---

### Post by cogadh on 2008-04-12
Using Wine will not affect any existing Windows installation, unless you made the mistake of trying to run an application from your Windows drive using Wine. That is not the correct way to use Wine at all. Applications that you intend to run with Wine should actually be installed in Linux with Wine.

---

### Post by GeekGirl1 on 2008-04-12
You are correct. I checked the FAQ again to look for what you described and the section about needing to install applications in Linux wasn't mentioned until later in the page. I missed it. My bad :oops:. However, Quicken 2007 Premier is listed as a problem in the Wine database. 

There should be some kind of warning about running Windows apps in Wine that are not installed correctly.

---

### Post by cogadh on 2008-04-12
Yeah, Quicken has a long history of being a problem app in Wine. Someday Wine will be complete enough to make it work, but not today.

I don't want to sound like I'm saying "RTFM", but I would suggest you read through the entire Wine user documentation before jumping right into it. Generally speaking, there isn't much you can do with Wine that will actually hurt your system, but it is always better to learn what you should do before you try doing it, just in case. Unfortunately, this time you just happened to be unlucky enough to try one of the two things you really never should do with Wine (the second is running Wine as root or with sudo).

---

### Post by vexorian on 2008-04-12
Most of the times, you should try complaining to the company that made the software that doesn't work. I had developed plenty of apps in WINE and noticed that most of the times (iif directx is not involved) it is an error with my own code what prevented it from working well. Winapi's documentation only states what to do when the code is correct, otherwise, WINE devs have no idea how to implement it.

---

### Post by jimoz on 2008-04-18
I've only been using Ubuntu for a few months, and Wine for less. In all honesty, there are only two or three windows apps that I cant find a Linux equivalent for, unfortunately though, none of them work under Wine. In the course of trying to get a couple of them to work, Ive had some nasty crashes - the last one gnome was still working but couldnt shutdown, couldnt override it from terminal, couldnt manually kill off the wine processes... had to power it down. This also caused a few other minor problems.
Are there any tips or tricks you all have to avoid this? Basically I mean ways to safely test apps under Wine, and how to abort/kill a wine session without it screwing up everything else?

---

### Post by developerX on 2008-04-21
Well, I have feeling if something mostly don't work then it should not use. If Wine ever is usable then I will use it - not before.

---

### Post by YokoZar on 2008-04-22
> **developerX said:**
> Well, I have feeling if something mostly don't work then it should not use. If Wine ever is usable then I will use it - not before.Wine works very well with many things.  It gets better every release.

Really, I disagree with this entire thread topic.

---

### Post by vexorian on 2008-04-22
> **vexorian said:**
> Most of the times, you should try complaining to the company that made the software that doesn't work. I had developed plenty of apps in WINE and noticed that most of the times (iif directx is not involved) it is an error with my own code what prevented it from working well. Winapi's documentation only states what to do when the code is correct, otherwise, WINE devs have no idea how to implement it.
WINE has just removed covered the most important drawback I had for switching to Linux, I am finally able to run warcraft III world editor in a way that's practical in WINE, which is great. I really missed it since I switched to Linux.

virtualization seems unlikely to ever allow 3d acceleration, it also requires a windows license, WINE is the way to go and the WINE devs are doing an outstanding job lately.

> You will finally see windoz start to drop off the map when any or most windoz apps can be run easily on linux.
yay then? since WINE already covers "most"

---

### Post by mimp on 2008-04-27
> **cogadh said:**
> Using Wine will not affect any existing Windows installation, unless you made the mistake of trying to run an application from your Windows drive using Wine. 

Which is what I did, and it appears to have completely killed my windows install.

I understand completely that this is not wine's fault, it's mine for not reading documentaion and diving right in, plus it's not that big a deal to rescue my windows data + reinstall.

However, as nuking windows is the sort of thing that might put a potential linux user off for life, some big red text in winecfg telling you not to point wine at an existing windows install might be prudent.

---

### Post by cogadh on 2008-04-27
Again, I really don't want to sound like I'm saying "RTFM", but if you took the time to read something as simple as the [Wine FAQ](http://wiki.winehq.org/FAQ), it does warn you off of doing [that exact thing](http://wiki.winehq.org/FAQ#head-3647fcb12328bf8f43d7cfce4d0dcbcee12c0541). Its not in big, bold red letters, but it is there, very plainly stated, right under the "Using Wine" section. Its really not up to the Wine developers to do more than make the necessary info available to new users. As a new Wine user, you should be responsible for making sure you know what you are doing before you do it.

---

### Post by vexorian on 2008-04-28
> **mimp said:**
> Which is what I did, and it appears to have completely killed my windows install.

I understand completely that this is not wine's fault, it's mine for not reading documentaion and diving right in, plus it's not that big a deal to rescue my windows data + reinstall.

However, as nuking windows is the sort of thing that might put a potential linux user off for life, some big red text in winecfg telling you not to point wine at an existing windows install might be prudent.

The problem is not with WINE, as in at all, I would blame the ntfs drivers. running a WINE app from hard drive will not ruin windows' it 'might' break the app but that's unlikely, if the app is made correctly it will use the registry and documents and settings (so it will edit WINE stuff, not the ones in his folder)

---

### Post by tech9 on 2008-04-28
> **bruhja said:**
> WOW!!!! people actualy bash developers who give them **free** software????? *shakes head with dismay.:confused:

wow... agreed!

---

### Post by hodenkat on 2008-04-29
No complaints here, but I do feel the pain when I need to run my tax software each year, or I want to play that cool 3D game that's only able to work on WinXP. I'm dual booting with XP so it's always there for those MS-only apps.

I think what I'm hearing out there is the frustration people are feeling when they realize how hard MS has made it to leave their OS behind.
People really want to kick the MS habit, but they are finding out it's not so easy at times. Anything that looks like it may be the
"magic bullet" gets their hopes up high. Like somebody said though, be thankful it works at all... it's FREE!

I have come to the point where I like all operating systems.
What I DON'T like is the politics they bring with them.

That said, I'm sticking with Linux:popcorn:

---

### Post by vexorian on 2008-04-30
> **hodenkat said:**
> No complaints here, but I do feel the pain when I need to run my tax software each year, or I want to play that cool 3D game that's only able to work on WinXP. I'm dual booting with XP so it's always there for those MS-only apps.

I think what I'm hearing out there is the frustration people are feeling when they realize how hard MS has made it to leave their OS behind.
People really want to kick the MS habit, but they are finding out it's not so easy at times. Anything that looks like it may be the
"magic bullet" gets their hopes up high. Like somebody said though, be thankful it works at all... it's FREE!

I have come to the point where I like all operating systems.
What I DON'T like is the politics they bring with them.

That said, I'm sticking with Linux:popcorn:
In all seriousness, if all you use windows for is to run non-3d accelerating software, then you should just use a virtual machine, it works very well and removes the hassle of dual booting, I use virtualbox almost daily to do stuff that can only be done in windows, and windows makes a great Linux app, since you can just remove its access to the network...

---

### Post by hodenkat on 2008-05-03
> **vexorian said:**
> In all seriousness, if all you use windows for is to run non-3d accelerating software, then you should just use a virtual machine, it works very well and removes the hassle of dual booting, I use virtualbox almost daily to do stuff that can only be done in windows, and windows makes a great Linux app, since you can just remove its access to the network...

I've tried to get virtualbox running without success on 8.04.
After downloading and installing it I was unable to find it.
When I attempted to launch it from terminal it told me to try installing virtualbox-ose (sudo apt-get install virtualbox-ose).
After doing this, I was able to launch the program but after creating a virtual drive I wasn't able to "start" it. Kept getting a message that some package was unable to start or a directory wasn't created. This lead to searching for related packages in synaptic and installing them. Still got the same message and now my grub menu showed a bunch of new boot choices. Lost my sound and wireless connections. Removed all the additional packages, removed virtualbox-ose, edited my grub menu.lst to get rid of the numerous menu choices that had been created and ended up back where I started. I think at this point it's just better for me to boot into windows!

---

### Post by cogadh on 2008-05-03
Don't install VirtualBox from the regular Ubuntu repositories, get it from Innotek's repository, that one works perfectly without all the hassle of extraneous packages.

---

### Post by hodenkat on 2008-05-03
[U]Nope, guess again.

Installed virtualbox_1.6.0-30421_Ubuntu_hardy_i386.deb and have more issues. After setting up and creating a virtual machine I get:[/U]

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason.
Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.

VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED)."

_So I ran the "Re-setup" and got:_

* Stopping VirtualBox kernel module vboxdrv [ OK ]
* Recompiling VirtualBox kernel module vboxdrv
* Look at /var/log/vbox-install.log to find out what went wrong.


_Looked at vbox-install.log:_

Makefile:75: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again. Stop.


Back where I started...:mad:

---

### Post by cogadh on 2008-05-03
That's because you installed just the VirtualBox package from a download. I said use the VirtualBox repository. Add this to your /etc/apt/sources.list:
```
deb http://www.virtualbox.org/debian/ gutsy non-free
```
Then just run "sudo apt-get update" followed by "sudo apt-get install virtualbox" and everything should work fine.

---

### Post by hodenkat on 2008-05-06
Cool!

I'll give it a try, but I think I'm going to install Hardy on a spare harddrive and play with it first before I dive into my main machine.

Thanks!

I'll post again when I get it going.

---

### Post by DaVince21 on 2008-05-07
> **daInvincibleGama said:**
> Yes. The Windows API has so many little bugs and quirks that its a surprise even some Windows apps like uTorrent and ImgBurn and such work that well(Most of them don't) . It's ridiculously hard to reimplement not only the features but also the bugs. Yes, bugs:popcorn:.



Wine attempts to be a cleanroom reimplementation of the Windows API. Its possible to use DLL overrides in Wine although admittedly its a little complex. However, they cannot legally redistribute Windows DLLs to make things work right. Windows is proprietary and the license forbids it. Only if you own a copy of Windows does fair use come into play for WinDLLs on Wine.
About this... I think Wine could definitely use a script/application to auto-override some DLLs from your native Windows partition where necessary or recommended. Of course, such an application would have to be constantly updated with each version of Wine (add/remove recommended DLL overrides) and in the end it'd become obsolete (when the Windows API is fully implemented, which won't be for the time being anyway).

---

### Post by stupidforum on 2008-05-08
What I get irritated is when the developers don't test commonly implemented features when putting out a release.  Wine works great for some things and not for others.  However, right now I'm upset about a problem I'm having with ubuntu not wine.  I have a Gutsy box.  I've had previous versions of wine and ubuntu.  wine always worked out of the box for applications that were listed in the appdb as gold or platinum.  Still does.

Built a similar box using newer versions of essentially the same hardware but the difference here being that I'm using hardy not gutsy and now I'm having a problem.  We're not talking about flaky programs here either:
Ones I've tried:
Quake II  Rated Platinum on appdb
Guild Wars   Rated Platinum on appdb
Tomb Raider: Legend  Rated Gold on appdb
I got garbage results though.  All of these applications work on my other machine with the EXACT same build of wine.
---end of rant---

---

### Post by cogadh on 2008-05-08
I had lots of problems with Hardy myself, not just with Wine. I would feel comfortable blaming Hardy for your Wine problems before I would say Wine was at fault. I've gone back to Gutsy myself, everything worked perfectly with it and I see no reason to "upgrade" to Ubuntu's version of Vista (yes, Hardy was that bad of an experience for me).

---

### Post by YokoZar on 2008-05-09
> **cogadh said:**
> Again, I really don't want to sound like I'm saying "RTFM", but if you took the time to read something as simple as the [Wine FAQ](http://wiki.winehq.org/FAQ), it does warn you off of doing [that exact thing](http://wiki.winehq.org/FAQ#head-3647fcb12328bf8f43d7cfce4d0dcbcee12c0541). Its not in big, bold red letters, but it is there, very plainly stated, right under the "Using Wine" section. Its really not up to the Wine developers to do more than make the necessary info available to new users. As a new Wine user, you should be responsible for making sure you know what you are doing before you do it.Winecfg is being changed to prevent users from even attempting this.

---

### Post by cogadh on 2008-05-09
Excellent news! Glad they decided to make this a "non issue" now.

---

