---
title: "Wine 0.9.56 Released!"
date: 2008-02-23
forum: Wine
---

### Post by Kosimo on 2008-02-23
[http://www.winehq.org/](http://www.winehq.org/)

We've been waiting long for 0.9.55 repository update! And now, wine folks give us more stability and some new features! 

Here the changelog:

This is release 0.9.56 of Wine, a free implementation of Windows on Unix.

What's new in this release:
  - Proper handling of OpenGL/Direct3D windows with menu bars.
  - Stubs for all the d3dx9_xx dlls.
  - Several graphics optimizations.
  - Many installer fixes.
  - Improved MIME message support.
  - Lots of bug fixes.

---

### Post by Sammi on 2008-02-23
Seems like a larger release than usual.

---

### Post by Sockerdrickan on 2008-02-23
For gamer, maybe.

---

### Post by xtek0 on 2008-02-23
Yea how would you install this package? Its not in automatic updates??

---

### Post by -random on 2008-02-23
that was a close follow up to the previous version.. :)

---

### Post by xtek0 on 2008-02-23
yea but how do you install the .56?

---

### Post by Captain_Redbeard on 2008-02-23
I suppose you will have to wait for the rpos to be updated with the new version... or build it yourself

---

### Post by Captain_Redbeard on 2008-02-23
...or if you really can't wait and are running hardy... I'm currently building a deb for it... I'll post it once it's done

---

### Post by xtek0 on 2008-02-23
How long will that take?

---

### Post by Captain_Redbeard on 2008-02-23
uhm... 40 mins or something like that

---

### Post by xtek0 on 2008-02-23
Your a new user to the community...

---

### Post by Captain_Redbeard on 2008-02-23
Yea I haven't spent much time in Linux forums at all to be honest... why? You're not sure if you can trust my deb-packages? :)
Well it's up to you, I'll post it anyway when it's done and if people want to download/use it, that's great and if you don't want to trust it because I'm "new to the community" that's your choice, I'm just trying to help ppl who don't want to compile for themselfs out... Anyway, I'll stop this spamming now and I'll come back when I'm done and have uploaded it somewhere...

---

### Post by Kosimo on 2008-02-23
> **Captain_Redbeard said:**
> Yea I haven't spent much time in Linux forums at all to be honest... why? You're not sure if you can trust my deb-packages? :)
Well it's up to you, I'll post it anyway when it's done and if people want to download/use it, that's great and if you don't want to trust it because I'm "new to the community" that's your choice, I'm just trying to help ppl who don't want to compile for themselfs out... Anyway, I'll stop this spamming now and I'll come back when I'm done and have uploaded it somewhere...

Go ahead, I'll try your deb. Help is always appreciated

---

### Post by Captain_Redbeard on 2008-02-23
Ok guys, here goes
[http://rapidshare.com/files/94295459/wine_0.9.56-1_i386.deb.html](http://rapidshare.com/files/94295459/wine_0.9.56-1_i386.deb.html)

Sorry for the crappy hosting service, if you like it you can maybe find a better one for it, anyways... it's for i386 compiled on Hardy. it works perfectly for me. If you have problems with it, please let me know :)

Have fun guys!

---

### Post by xtek0 on 2008-02-23
Will it work on gutsy?

---

### Post by happyhamster on 2008-02-23
At the bottom of the announcement page is I think the most interesting change:

Vitaliy Margolen (3):
      dinput: Skip old mouse movement events.
      Revert "dinput: Skip old mouse movement events.".
      dinput: Don't use event times, report current tick count instead.
([http://www.winehq.org/?announce=0.9.56](http://www.winehq.org/?announce=0.9.56))

This means that for several games with mouse problems (not all) the mouse will actually be usable again. Two games I quickly tested: No One Lives Forever (needed native dinput.dll before) and Prince of Persia, The Two Thrones have correct cursor behaviour now. :guitar:

---

### Post by justin whitaker on 2008-02-23
> **Captain_Redbeard said:**
> Ok guys, here goes
[http://rapidshare.com/files/94295459/wine_0.9.56-1_i386.deb.html](http://rapidshare.com/files/94295459/wine_0.9.56-1_i386.deb.html)

Sorry for the crappy hosting service, if you like it you can maybe find a better one for it, anyways... it's for i386 compiled on Hardy. it works perfectly for me. If you have problems with it, please let me know :)

Have fun guys!

Ok, the new one in the repos 9.55 seg faulted. This one works fine. 

Well done, and many thanks!

---

### Post by Captain_Redbeard on 2008-02-23
> **justin whitaker said:**
> Ok, the new one in the repos 9.55 seg faulted. This one works fine. 

Well done, and many thanks!
No sweat mate :) I was building it for myself anyway, and since the official ubuntu packages are usual delayed by up to a week I thought it would be nice to provide a home brewed package instead ;)

---

### Post by soxs on 2008-02-23
I made a x86_64 AMD package(compiled on 8.04 alpha): [http://rapidshare.com/files/94362952/wine_0.9.56-1_amd64.deb.html](http://rapidshare.com/files/94362952/wine_0.9.56-1_amd64.deb.html)

---

### Post by inportb on 2008-02-23
> **Captain_Redbeard said:**
> Ok guys, here goes
[http://rapidshare.com/files/94295459/wine_0.9.56-1_i386.deb.html](http://rapidshare.com/files/94295459/wine_0.9.56-1_i386.deb.html)

Sorry for the crappy hosting service, if you like it you can maybe find a better one for it, anyways... it's for i386 compiled on Hardy. it works perfectly for me. If you have problems with it, please let me know :)

Have fun guys!

Thanks man!

I have uploaded it to FileFront, which appears to be better.
[http://files.filefront.com/wine+0956+1+i386deb/;9690336;/fileinfo.html](http://files.filefront.com/wine+0956+1+i386deb/;9690336;/fileinfo.html)

---

### Post by Kabezon on 2008-02-23
thanks, worked great =]

---

### Post by djbon2112 on 2008-02-24
Nevermind, just installed it from source.

---

### Post by Twitch6000 on 2008-02-24
Hey I know most things about ubuntu except Bulfinch from the source and installing files other then .deb can someone explain step by step how the heck to install one.(that one being building from the source or installing a tar,tar.gz and all that)

---

### Post by Fir3chi3f on 2008-02-24
> **soxs said:**
> I made a x86_64 AMD package(compiled on 8.04 alpha): [http://rapidshare.com/files/94362952/wine_0.9.56-1_amd64.deb.html](http://rapidshare.com/files/94362952/wine_0.9.56-1_amd64.deb.html)

Thanks for package worked like a charm!

---

### Post by kindofabuzz on 2008-02-25
woohoo!!  World of Warcraft works great with this new realease!!  in direct3d too!  for those of you who don't know how to install it:  [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by nchase on 2008-02-25
> **inportb said:**
> Thanks man!

I have uploaded it to FileFront, which appears to be better.
[http://files.filefront.com/wine+0956+1+i386deb/;9690336;/fileinfo.html](http://files.filefront.com/wine+0956+1+i386deb/;9690336;/fileinfo.html)

Thank you both.

---

### Post by KhaaL on 2008-02-25
> **Captain_Redbeard said:**
> uhm... 40 mins or something like that

I think 40 minutes has passed ;-)

---

### Post by aikishugyo on 2008-02-25
Heh....40 minutes. I laugh at your gullibility LOL On my PIII 750 MHz w/ 2 GiB RAM this took around 2.5 hours. But it works like a dream!

---

### Post by Meow27 on 2008-02-25
so how do u install .56 using 7.10 (fiesty) on 32 bits

---

### Post by Dark Aspect on 2008-02-25
> **Meow27 said:**
> so how do u install .56 using 7.10 (fiesty) on 32 bits

The Source right now,that version is not in the repositories.However compiling seems very easy to me and I have no C/C++ knowledge so.

For 64-bit I followed:

[http://wiki.winehq.org/WineOn64bit]("http://wiki.winehq.org/WineOn64bit")

Should be the same on 32-bit just skip the 32-bit symlinks and I think it'll work but I am not sure.

---

### Post by Captain_Redbeard on 2008-02-26
> **KhaaL said:**
> I think 40 minutes has passed ;-)

Yea but I had it done after 40 minutes :O
And it's uploaded both on filefront and fileshack... go ahead and try it if you want

---

### Post by SBFC on 2008-02-26
> **aikishugyo said:**
> Heh....40 minutes. I laugh at your gullibility LOL On my PIII 750 MHz w/ 2 GiB RAM this took around 2.5 hours. But it works like a dream!

Believe it or not there are currently processors that are a tad faster than a 750 MHz. Why, some even have more than one core!

He wasn't being gullible, it can compile in under 40 min.

---

### Post by KhaaL on 2008-02-26
I just tried the packet from [this link]("http://rs308.rapidshare.com/files/94362952/wine_0.9.56-1_amd64.deb") and it works real nice. The minimap works both in NWN2 and DoW. Thanks to whoever posted it (I'm too lazy to find out who did it).

---

### Post by Captain_Redbeard on 2008-02-26
> **SBFC said:**
> Believe it or not there are currently processors that are a tad faster than a 750 MHz. Why, some even have more than one core!

He wasn't being gullible, it can compile in under 40 min.

Indeed.. intel core duo 2Ghz with 4GB RAM... my laptop :)

---

### Post by aikishugyo on 2008-02-27
> **SBFC said:**
> Believe it or not there are currently processors that are a tad faster than a 750 MHz. Why, some even have more than one core!

He wasn't being gullible, it can compile in under 40 min.

I think you need a course in reading comprehension :-) ... do you know what LOL means?

FWIW, I use a dual-core AMD64 2 GHz with 8 GiB of ECC  and registered SDRAM so yes, I do realize the foolishness of working on my older machine at home. But hey, I did write it jokingly!

---

### Post by SBFC on 2008-02-27
If I came across as a jack hole I do apologize.

---

### Post by jecos on 2008-02-28
I love how every distribution BUT ubuntu & debian have up to date wine packages.

I appreciate the repository, just wish we could get someone that can actually get it packaged quicker.  Ubuntu is a big deal, is it not??

---

### Post by Rizado on 2008-02-28
> **jecos said:**
> I love how every distribution BUT ubuntu & debian have up to date wine packages.

I appreciate the repository, just wish we could get someone that can actually get it packaged quicker.  Ubuntu is a big deal, is it not??Usually there's packages ready in a few hours but this time it's different, probably the package maintainer isn't available or something.

---

### Post by anjilslaire on 2008-03-01
Just wanted to clarify about the repository:
We're talking about the wineHQ repo, correct?

I just rebuilt my box last week and re-added  wineHQ to sources.list and reimported the key, and its not available :(

I knew the official ubuntu repos were understandably slow to get it, but the wine folks haven't updated their own site yet, then?
I can wait, I just wanted to be sure it wasn't something I've done wrong...

---

### Post by fatbuttlarry on 2008-03-02
Here's a mirror:

-- removed -- see [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) for 0.9.56.

-Tres:popcorn:

---

### Post by agtownz on 2008-03-02
The .debs mess it up for me completely

---

### Post by fatbuttlarry on 2008-03-02
> **agtownz said:**
> The .debs mess it up for me completely

please elaborate.

---

### Post by Lvcoyote on 2008-03-02
Didnt work for me either, it appears to install, but the program will not open when I try to start it.

---

### Post by Lvcoyote on 2008-03-02
When I try to uninstall I get the following, is this a problem, is it not uninstalling??
[PHP]lvcoyote@lvcoyote-desktop:~$ sudo apt-get purge wine
[sudo] password for lvcoyote:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  menu libwxgtk2.8-0 libwxbase2.8-0 python-wxversion python-wxgtk2.8
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  wine*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 68.9MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 116359 files and directories currently installed.)
Removing wine ...
Purging configuration files for wine ...
dpkg - warning: while removing wine, directory `/usr/local/lib' not empty so not removed.
dpkg - warning: while removing wine, directory `/usr/local/share' not empty so not removed.
dpkg - warning: while removing wine, directory `/usr/local' not empty so not removed.
lvcoyote@lvcoyote-desktop:~$ 
[/PHP]

---

### Post by Lvcoyote on 2008-03-02
Wine is the one program I can never get to work or even install correctly.  I've tried and retried so many times.  Every time a new version comes out I try again, but it never works......  Considering all the other things I've managed to get working on Ubuntu, this one really has me stumped...........

---

### Post by fatbuttlarry on 2008-03-02
> **Lvcoyote said:**
> Didnt work for me either, it appears to install, but the program will not open when I try to start it.

Did you install the one I hosted or the rapidshare one? What do you get in console when you type "wine notepad"

-Tres

---

### Post by Lvcoyote on 2008-03-02
The one you hosted.......  Wine-notepad in terminal results in nothing, wine does not open.

---

### Post by Lvcoyote on 2008-03-02
At this point I think I may have remnants laying around from all the previous install attempts, can you tell by looking above if I have it uninstalled completely??

---

### Post by agtownz on 2008-03-02
> please elaborate.
Basically, nothing works.  Some things can start, but only last until 3d runs or for example, in BlitzMax, as soon as I open up another tab in the editor.  Window goes blue and it dies.
> 
Wine is the one program I can never get to work or even install correctly. I've tried and retried so many times. Every time a new version comes out I try again, but it never works...... Considering all the other things I've managed to get working on Ubuntu, this one really has me stumped...........
Have you tried with Synaptic or with Add/Remove?  I'm not sure what would cause the problem.

---

### Post by Lvcoyote on 2008-03-03
Yes I have.  I've kind of given up on wine, its really not a very good program at all at this stage of development.  I installed VMware and a copy of XP inside of it.  There is only a couple windows programs I need and I was hoping to not have to use VMware and install the whole OS, but at this point I really have no choice.

---

### Post by fatbuttlarry on 2008-03-03
> **Lvcoyote said:**
> The one you hosted.......  Wine-notepad in terminal results in nothing, wine does not open.

I installed the 64bit one, and it is ok.  Sorry if either one is bad, I would not have hosted them if not for the positive feedback on forums.

Perhaps try the rapidshare hosted one and post if its any better or worse?

-Tres

---

### Post by Lvcoyote on 2008-03-03
I do not think anything is wrong with your download, I think its just the craptacular program itself.

---

### Post by CarpKing on 2008-03-04
> **Lvcoyote said:**
> I do not think anything is wrong with your download, I think its just the craptacular program itself.

Not unless they've really messed it up with this release.  It's normal for programs not to work with Wine, but I've never heard of Wine itself not working at all.

---

### Post by mc4man on 2008-03-04
@Lvcoyote 
do you run winecfg after 'installing' wine ?

I tried the 32 bit - seemed fine though I didn't  keep. I think it installed to /usr/local vs. /usr that the normal debs do.

---

### Post by yoyu007 on 2008-03-04
&#35874;&#35874;
&#24456;&#24555;

---

### Post by fwilliams on 2008-03-04
[http://www.winehq.org/site/download](http://www.winehq.org/site/download)

---

### Post by CarpKing on 2008-03-04
Yep, it finally hit the official repository.

---

### Post by Lvcoyote on 2008-03-04
Thats the problem I'm having, wine loads fine but wont run.  All I'm trying to get working is Internet explorer 6.0 and Media player.  Both of those come as available in Wine-Doors.  When I install them they will not open or work.

winecfg ??  No I have not, do I just type that in terminal??

---

### Post by agtownz on 2008-03-04
Wine 0.9.56 is seriously messed up.

---

### Post by chips24 on 2008-03-04
how do you update to the newest version in the terminal?

---

### Post by agtownz on 2008-03-04
Go to winehq and read the instructions there.

---

### Post by CarpKing on 2008-03-05
> **Lvcoyote said:**
> winecfg ??  No I have not, do I just type that in terminal??

Yes.  You're supposed to do that before you try to run anything.

---

### Post by Eddie Wilson on 2008-03-05
> **agtownz said:**
> Wine 0.9.56 is seriously messed up.

Explain in detail please. I haven't upgraded yet. 

Eddie

---

### Post by GSZX1337 on 2008-03-05
So much for Team Fortress 2 in Linux. I got the latest version and now it runs even worse! I can't even go into the water in 2Fort because the game turns into a flippin' slideshow!

---

### Post by CarpKing on 2008-03-05
Yeah, it looks like they broke 3d acceleration in some games.  If you can't find anyone who has tried the game before, you might just have to upgrade and see.

---

### Post by agtownz on 2008-03-05
> Explain in detail please. I haven't upgraded yet.

Eddie
BF2 doesn't even start, all BlitzMax tests used to run perfectly, now all crash, BlitzMax IDE is so unstable it's unusable (I realize BMax has Linux IDE, but I test extensively for compatibility).  Major stability problems, most things I can't even get 3d to run on.  I have no idea what they did, but I used Synaptic to bring back 0.9.55.

---

### Post by kenton_r on 2008-03-06
I just upgraded to .56 and I have a problem with the contents of the window being shifted down leaving a 1/4 inch black bar at the top. The target area to click on a button has not changed.

Have any of you experienced this after installing the latest wine?

---

### Post by desertboy on 2008-03-07
> **chips24 said:**
> how do you update to the newest version in the terminal?

From [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
open terminal

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

sudo apt-get update (If you've already installed wine or just grab it from add/remove programs.)

You only have to do this once and then Ubuntu will keep it up to date automatically (Not always a good thing with wine) this assumes you're using gutsy see link for info for fiesty/dapper users.

---

### Post by samitharansara on 2008-03-07
its really great........

---

### Post by Lvcoyote on 2008-03-07
> **CarpKing said:**
> Yes.  You're supposed to do that before you try to run anything.

Well that presents me with a small window with "wine configuration" as the window title.  Blank window, nothing inside and nothing to work with........ I give up on wine.....  I've now tried Wine-Doors, PlayonLinux, and just plain WIne, nothing will work at all, cant get any of them to show in the start menu, or even in Preferences/Main Menu........ oh well.  Its a shame too because this install is running everything else I ever wanted it to do with it.

---

### Post by CarpKing on 2008-03-08
> **Lvcoyote said:**
> Well that presents me with a small window with "wine configuration" as the window title.  Blank window, nothing inside and nothing to work with........ I give up on wine.....  I've now tried Wine-Doors, PlayonLinux, and just plain WIne, nothing will work at all, cant get any of them to show in the start menu, or even in Preferences/Main Menu........ oh well.  Its a shame too because this install is running everything else I ever wanted it to do with it.

You should try running a program now to see if it works.  Even if you weren't able to do anything in the window, running it should have properly set up your .wine directory.  

In the current release I sometimes have a blank portion of the winecfg window.  Using a virtual Wine desktop fixes that problem, but I don't know how to set that without being able to use at least part of winecfg.  Are you running Compiz?  It has a reputation for giving Wine issues, though I haven't run into any myself (the aforementioned problem doesn't happen often enough for me to have bothered testing it without Compiz).  

At the very least, don't give up on Wine forever.  Ideally, you should file bugs if you can't get it working, but even if you don't you should try again every couple releases to see if the problem goes away.

---

### Post by Lvcoyote on 2008-03-08
I did try a program or two, but it will not open.  I have tried the last few releases, all with the same result.  I would file a bug report, but what do I say??  "The program wont open anything"??  that wouldn't be much help.....LOL.  I can't get anything to open so I can't really explain any behaviours.

---

### Post by SBFC on 2008-03-08
> **Lvcoyote said:**
> I can't get anything to open so I can't really explain any behaviours.

Perhaps you could provide some output from the terminal? Any error messages? Any messages at all?

Also, what is it you're trying to run?

---

### Post by Lvcoyote on 2008-03-08
Trust me, I've tried it all.  I'm trying to run wine itself first but becauseI cant even get that to load I have not even been able to get to the next step of actually installing a program to it.  I'm not blaming wine persey, there is obviously something in my configuration that wine does not like, its no big deal as I tripple boot with XP and Vista so on the rare occasion I need windows for something I have it at my disposal.  Maybe when the next version of Ubuntu comes out I'll do a clean install and try wine again, but for now its just not happening.

---

### Post by CarpKing on 2008-03-08
The fact that it's not doing anything is a reportable behavior in and of itself.  The people who read the bug reports will also be more knowledgeable about the workings of Wine than people here.  

As you mentioned earlier, since you've installed it a variety of ways it might be that you have leftover files that are screwing things up.  The only way I can think of to tell is to do a complete removal of the most recent way you installed it, delete your .wine directory, and run "locate wine" in the terminal.  It should have no results (unless there are unrelated files that happen to have that letter sequence in their name, which should be easy to figure out).  Tell us what the output is.  Unfortunately I can't tell you any way to get rid of such remnants short of manually deleting them, which may or may not be a bad idea, but maybe someone here can.  Then when you reinstall I recommend using the official repository, then running winecfg, then running notepad (you mentioned wine-notepad earlier, the valid command for this is just "notepad").  

You also said that you were trying to run wine before trying any programs.  did you mean winecfg?  The command "wine" must be followed by the name of an exe that is in the directory your terminal is in.

---

### Post by Lvcoyote on 2008-03-08
Ok CK you might be on to something, here is what I get when I run "Find Wine"[PHP]/home/lvcoyote/.wine/drive_c/windows/temp/msi268b.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/mny515e.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi3043.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/1656.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi8fad.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi9168.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi2173.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi520e.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/1770_autohotkey.0.xpm
/home/lvcoyote/.wine/drive_c/windows/temp/mny5ca7.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/cpuz_x32.sys
/home/lvcoyote/.wine/drive_c/windows/temp/IXP002.TMP
/home/lvcoyote/.wine/drive_c/windows/temp/IXP002.TMP/ole32.dll
/home/lvcoyote/.wine/drive_c/windows/temp/IXP002.TMP/olethk32.dll
/home/lvcoyote/.wine/drive_c/windows/temp/IXP002.TMP/W95INF16.DLL
/home/lvcoyote/.wine/drive_c/windows/temp/mny3a03.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/IXP003.TMP
/home/lvcoyote/.wine/drive_c/windows/temp/IXP003.TMP/W95INF16.DLL
/home/lvcoyote/.wine/drive_c/windows/temp/msi9d73.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi5a20.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi5100.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi6a8.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/1770_au3_spy.0.xpm
/home/lvcoyote/.wine/drive_c/windows/temp/msi6646.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi3fcf.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi59c7.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi21c0.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/IXP000.TMP
/home/lvcoyote/.wine/drive_c/windows/temp/IXP000.TMP/W95INF16.DLL
/home/lvcoyote/.wine/drive_c/windows/temp/msi9d9c.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/Streets and Trips 2005 Setup(0001).txt
/home/lvcoyote/.wine/drive_c/windows/temp/msi3167.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi39d6.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi37ba.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/a20c_autoscriptwriter.0.xpm
/home/lvcoyote/.wine/drive_c/windows/temp/msi512b.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi3062.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi9dda.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/mny65c4.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/mnysetup.log
/home/lvcoyote/.wine/drive_c/windows/temp/msi788d.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi7732.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi6593.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/IXP001.TMP
/home/lvcoyote/.wine/drive_c/windows/temp/IXP001.TMP/ole32.dll
/home/lvcoyote/.wine/drive_c/windows/temp/IXP001.TMP/olethk32.dll
/home/lvcoyote/.wine/drive_c/windows/temp/IXP001.TMP/W95INF16.DLL
/home/lvcoyote/.wine/drive_c/windows/temp/msi5c4e.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi4176.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi29f1.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi4605.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/mny454a.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi4503.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi37df.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi9d48.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi4f3.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi2193.tmp
/home/lvcoyote/.wine/drive_c/windows/temp/msi5c77.tmp
/home/lvcoyote/.wine/drive_c/windows/regedit.exe
/home/lvcoyote/.wine/drive_c/windows/winhelp.exe
/home/lvcoyote/.wine/drive_c/windows/Sysbckup
/home/lvcoyote/.wine/drive_c/windows/Sysbckup/compobj.dll
/home/lvcoyote/.wine/drive_c/windows/explorer.exe
/home/lvcoyote/.wine/drive_c/windows/twain_32.dll
/home/lvcoyote/.wine/drive_c/windows/Active Setup Log.txt
/home/lvcoyote/.wine/drive_c/windows/winsxs
/home/lvcoyote/.wine/drive_c/windows/winsxs/x86_policy.8.0.microsoft.vc80.crt_1fc8b3b9a1e18e3b_8.0.50727.42_none_5c4003bc63e949f6
/home/lvcoyote/.wine/drive_c/windows/winsxs/x86_policy.8.0.microsoft.vc80.crt_1fc8b3b9a1e18e3b_8.0.50727.42_none_5c4003bc63e949f6/8.0.50727.42.policy
/home/lvcoyote/.wine/drive_c/windows/winsxs/x86_policy.8.0.microsoft.vc80.crt_1fc8b3b9a1e18e3b_8.0.50727.42_none_5c4003bc63e949f6/8.0.50727.42.cat
/home/lvcoyote/.wine/drive_c/windows/winsxs/x86_microsoft.vc80.crt_1fc8b3b9a1e18e3b_8.0.50727.42_none_db5f52fb98cb24ad
/home/lvcoyote/.wine/drive_c/windows/winsxs/x86_microsoft.vc80.crt_1fc8b3b9a1e18e3b_8.0.50727.42_none_db5f52fb98cb24ad/x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.42_x-ww_0de06acd.manifest
/home/lvcoyote/.wine/drive_c/windows/winsxs/x86_microsoft.vc80.crt_1fc8b3b9a1e18e3b_8.0.50727.42_none_db5f52fb98cb24ad/x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.42_x-ww_0de06acd.cat
/home/lvcoyote/.wine/drive_c/windows/winsxs/x86_microsoft.vc80.crt_1fc8b3b9a1e18e3b_8.0.50727.42_none_db5f52fb98cb24ad/msvcm80.dll
/home/lvcoyote/.wine/drive_c/windows/winsxs/x86_microsoft.vc80.crt_1fc8b3b9a1e18e3b_8.0.50727.42_none_db5f52fb98cb24ad/msvcp80.dll
/home/lvcoyote/.wine/drive_c/windows/winsxs/x86_microsoft.vc80.crt_1fc8b3b9a1e18e3b_8.0.50727.42_none_db5f52fb98cb24ad/msvcr80.dll
/home/lvcoyote/.wine/drive_c/windows/winsxs/x86_microsoft.vc80.atl_1fc8b3b9a1e18e3b_8.0.50727.42_none_dc990e4797f81af1
/home/lvcoyote/.wine/drive_c/windows/winsxs/x86_microsoft.vc80.atl_1fc8b3b9a1e18e3b_8.0.50727.42_none_dc990e4797f81af1/ATL80.dll
/home/lvcoyote/.wine/drive_c/windows/winsxs/x86_microsoft.vc80.atl_1fc8b3b9a1e18e3b_8.0.50727.42_none_dc990e4797f81af1/x86_Microsoft.VC80.ATL_1fc8b3b9a1e18e3b_8.0.50727.42_x-ww_6e805841.cat
/home/lvcoyote/.wine/drive_c/windows/winsxs/x86_microsoft.vc80.atl_1fc8b3b9a1e18e3b_8.0.50727.42_none_dc990e4797f81af1/x86_Microsoft.VC80.ATL_1fc8b3b9a1e18e3b_8.0.50727.42_x-ww_6e805841.manifest
/home/lvcoyote/.wine/drive_c/windows/winsxs/Policies
/home/lvcoyote/.wine/drive_c/windows/winsxs/Policies/x86_policy.8.0.Microsoft.VC80.ATL_1fc8b3b9a1e18e3b_x-ww_5f0bbcff
/home/lvcoyote/.wine/drive_c/windows/winsxs/Policies/x86_policy.8.0.Microsoft.VC80.ATL_1fc8b3b9a1e18e3b_x-ww_5f0bbcff/8.0.50727.42.policy
/home/lvcoyote/.wine/drive_c/windows/winsxs/Policies/x86_policy.8.0.Microsoft.VC80.ATL_1fc8b3b9a1e18e3b_x-ww_5f0bbcff/8.0.50727.42.cat
/home/lvcoyote/.wine/drive_c/windows/winsxs/Policies/x86_policy.8.0.Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_x-ww_77c24773
/home/lvcoyote/.wine/drive_c/windows/winsxs/Policies/x86_policy.8.0.Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_x-ww_77c24773/8.0.50727.42.policy
/home/lvcoyote/.wine/drive_c/windows/winsxs/Policies/x86_policy.8.0.Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_x-ww_77c24773/8.0.50727.42.cat
/home/lvcoyote/.wine/drive_c/windows/winsxs/manifests
/home/lvcoyote/.wine/drive_c/windows/winsxs/manifests/x86_microsoft.windows.common-controls_6595b64144ccf1df_6.0.2600.2982_none_deadbeef.manifest
/home/lvcoyote/.wine/drive_c/windows/winsxs/manifests/x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.42_x-ww_0de06acd.manifest
/home/lvcoyote/.wine/drive_c/windows/winsxs/manifests/x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.42_x-ww_0de06acd.cat
/home/lvcoyote/.wine/drive_c/windows/winsxs/manifests/x86_microsoft.windows.common-controls_6595b64144ccf1df_6.0.0.0_none_deadbeef.manifest
/home/lvcoyote/.wine/drive_c/windows/winsxs/manifests/x86_Microsoft.VC80.ATL_1fc8b3b9a1e18e3b_8.0.50727.42_x-ww_6e805841.cat
/home/lvcoyote/.wine/drive_c/windows/winsxs/manifests/x86_Microsoft.VC80.ATL_1fc8b3b9a1e18e3b_8.0.50727.42_x-ww_6e805841.manifest
/home/lvcoyote/.wine/drive_c/windows/winsxs/x86_policy.8.0.microsoft.vc80.atl_1fc8b3b9a1e18e3b_8.0.50727.42_none_58b19c2866332652
/home/lvcoyote/.wine/drive_c/windows/winsxs/x86_policy.8.0.microsoft.vc80.atl_1fc8b3b9a1e18e3b_8.0.50727.42_none_58b19c2866332652/8.0.50727.42.policy
/home/lvcoyote/.wine/drive_c/windows/winsxs/x86_policy.8.0.microsoft.vc80.atl_1fc8b3b9a1e18e3b_8.0.50727.42_none_58b19c2866332652/8.0.50727.42.cat
/home/lvcoyote/.wine/drive_c/windows/winsxs/x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.42_x-ww_0de06acd
/home/lvcoyote/.wine/drive_c/windows/winsxs/x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.42_x-ww_0de06acd/msvcm80.dll
/home/lvcoyote/.wine/drive_c/windows/winsxs/x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.42_x-ww_0de06acd/msvcp80.dll
/home/lvcoyote/.wine/drive_c/windows/winsxs/x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.42_x-ww_0de06acd/msvcr80.dll
/home/lvcoyote/.wine/drive_c/windows/winsxs/x86_Microsoft.VC80.ATL_1fc8b3b9a1e18e3b_8.0.50727.42_x-ww_6e805841
/home/lvcoyote/.wine/drive_c/windows/winsxs/x86_Microsoft.VC80.ATL_1fc8b3b9a1e18e3b_8.0.50727.42_x-ww_6e805841/ATL80.dll
/home/lvcoyote/.wine/drive_c/windows/wmsetup.log
/home/lvcoyote/.wine/drive_c/windows/RegisteredPackages
/home/lvcoyote/.wine/drive_c/windows/RegisteredPackages/{89820200-ECBD-11cf-8B85-00AA005B4383}
/home/lvcoyote/.wine/drive_c/windows/winebrowser.exe
/home/lvcoyote/.wine/drive_c/windows/IE Uninstall
/home/lvcoyote/.wine/drive_c/windows/IE Uninstall/ieexcep.inf
/home/lvcoyote/.wine/drive_c/windows/IE Uninstall/w2kexcp.exe
/home/lvcoyote/.wine/drive_c/windows/IE Uninstall/ieexcep.cat
/home/lvcoyote/.wine/drive_c/windows/system.ini
/home/lvcoyote/.wine/drive_c/windows/help
/home/lvcoyote/.wine/drive_c/windows/help/msoe.hlp
/home/lvcoyote/.wine/drive_c/windows/help/accessib.chm
/home/lvcoyote/.wine/drive_c/windows/help/iexplore.hlp
/home/lvcoyote/.wine/drive_c/windows/help/iewebhlp.chm
/home/lvcoyote/.wine/drive_c/windows/help/wab.hlp
/home/lvcoyote/.wine/drive_c/windows/help/wscript.hlp
/home/lvcoyote/.wine/drive_c/windows/help/iesupp.chm
/home/lvcoyote/.wine/drive_c/windows/help/msoe.chm
/home/lvcoyote/.wine/drive_c/windows/help/msoeacct.hlp
/home/lvcoyote/.wine/drive_c/windows/help/ieshared.chm
/home/lvcoyote/.wine/drive_c/windows/help/wab.chm
/home/lvcoyote/.wine/drive_c/windows/help/oe_msgr.chm
/home/lvcoyote/.wine/drive_c/windows/help/iexplore.chm
/home/lvcoyote/.wine/drive_c/windows/help/update.cnt
/home/lvcoyote/.wine/drive_c/windows/help/ratings.hlp
/home/lvcoyote/.wine/drive_c/windows/help/ratings.chm
/home/lvcoyote/.wine/drive_c/windows/help/ratings.cnt
/home/lvcoyote/.wine/drive_c/windows/win.ini
/home/lvcoyote/.wine/drive_c/windows/Cursors
/home/lvcoyote/.wine/drive_c/windows/Cursors/globe.ani
/home/lvcoyote/.wine/drive_c/windows/Installer
/home/lvcoyote/.wine/drive_c/windows/Installer/5203.msi
/home/lvcoyote/.wine/drive_c/windows/Installer/28bf.msi
/home/lvcoyote/.wine/drive_c/windows/Installer/5d29.msi
/home/lvcoyote/.wine/drive_c/windows/Installer/45fe.msi
/home/lvcoyote/.wine/drive_c/windows/Installer/3ab8.msi
/home/lvcoyote/.wine/drive_c/windows/Installer/663f.msi
/home/lvcoyote/.wine/drive_c/windows/Installer/315e.msi
/home/lvcoyote/.wine/drive_c/windows/Installer/38de.msi
/home/lvcoyote/.wine/drive_c/windows/Installer/8fa4.msi
/home/lvcoyote/.wine/drive_c/windows/fonts
/home/lvcoyote/.wine/drive_c/windows/fonts/Comic.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/ArialNbi.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/Arial.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/Verdanaz.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/Ariali.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/AriBlk.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/Georgiai.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/Verdanai.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/Timesbd.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/Impact.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/trebucit.ttf
/home/lvcoyote/.wine/drive_c/windows/fonts/ArialNi.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/Timesi.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/Georgiab.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/Georgiaz.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/Times.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/Arialbd.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/Ninabi.ttf
/home/lvcoyote/.wine/drive_c/windows/fonts/Ninai.ttf
/home/lvcoyote/.wine/drive_c/windows/fonts/trebuc.ttf
/home/lvcoyote/.wine/drive_c/windows/fonts/ArialNb.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/arialn.ttf
/home/lvcoyote/.wine/drive_c/windows/fonts/cour.ttf
/home/lvcoyote/.wine/drive_c/windows/fonts/couri.ttf
/home/lvcoyote/.wine/drive_c/windows/fonts/Nina.ttf
/home/lvcoyote/.wine/drive_c/windows/fonts/Trebucbd.ttf
/home/lvcoyote/.wine/drive_c/windows/fonts/courbd.ttf
/home/lvcoyote/.wine/drive_c/windows/fonts/Georgia.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/Timesbi.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/Comicbd.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/Ninab.ttf
/home/lvcoyote/.wine/drive_c/windows/fonts/Verdanab.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/Verdana.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/Arialbi.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/courbi.ttf
/home/lvcoyote/.wine/drive_c/windows/fonts/AndaleMo.TTF
/home/lvcoyote/.wine/drive_c/windows/fonts/trebucbi.ttf
/home/lvcoyote/.wine/drive_c/windows/fonts/Webdings.TTF
/home/lvcoyote/.wine/drive_c/windows/inf
/home/lvcoyote/.wine/drive_c/windows/inf/iereadme.inf
/home/lvcoyote/.wine/drive_c/windows/inf/dcom98.inf
/home/lvcoyote/.wine/drive_c/windows/inf/msoe50.inf
/home/lvcoyote/.wine/drive_c/windows/inf/wab50.inf
/home/lvcoyote/.wine/drive_c/windows/inf/scripten.inf
/home/lvcoyote/.wine/drive_c/windows/inf/wine.inf
/home/lvcoyote/.wine/drive_c/windows/inf/removbak.inf
/home/lvcoyote/.wine/drive_c/windows/inf/oeexcep.inf
/home/lvcoyote/.wine/drive_c/windows/inf/Iesetup.inf
/home/lvcoyote/.wine/drive_c/windows/inf/iereset.inf
/home/lvcoyote/.wine/drive_c/Program Files
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Office
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Office/Office10
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Office/Office10/AW.DLL
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Office/Office10/HLP95EN.DLL
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Office/Office10/1033
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Office/Office10/1033/MSOHLP10.CHM
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Office/Office10/1033/MSOHELP.EXE
/home/lvcoyote/.wine/drive_c/Program Files/Common Files
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/System
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/System/wab32res.dll
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/System/wab32.dll
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/System/directdb.dll
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Services
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Services/bigfoot.bmp
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Services/infospbz.bmp
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Services/whowhere.bmp
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Services/infospce.bmp
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Services/verisign.bmp
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Maize Bkgrd.jpg
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/amaizrul.gif
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Leaves.htm
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Clear Day Bkgrd.jpg
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/sunbannA.gif
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/anabnr2.gif
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Pie Charts.htm
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Glacier.htm
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Glacier Bkgrd.jpg
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Pie Charts Bkgrd.jpg
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/aswrule.gif
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Sweets Bkgrd.gif
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Leaves Bkgrd.jpg
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Technical.htm
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Ivy.htm
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Ivy.gif
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Btzhsepa.gif
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Nature Bkgrd.jpg
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Blank Bkgrd.gif
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/aleabanr.gif
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Network Blitz.htm
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Nature.htm
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Network Blitz Bkgrd.gif
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Citrus Punch.htm
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/citbannA.gif
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Fiesta Bkgrd.jpg
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Fiesta.htm
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Citrus Punch Bkgrd.gif
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Sweets.htm
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/tech.gif
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Sunflower.htm
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Maize.htm
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Sunflower Bkgrd.jpg
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Blank.htm
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/Clear Day.htm
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Stationery/fieruled.gif
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/VGX
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/VGX/vgx.dll
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/TriEdit
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/TriEdit/triedit.dll
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/TriEdit/dhtmled.ocx
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Works Shared
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Works Shared/Mny16Eula.txt
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Works Shared/st12eula.txt
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Works Shared/wkernlng.dll
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Works Shared/eularegn.dll
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Works Shared/st12warr.htm
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/TextConv
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/TextConv/HTML32.CNV
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/TextConv/MSCONV97.DLL
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Information Retrieval
/home/lvcoyote/.wine/drive_c/Program Files/Common Files/Microsoft Shared/Information Retrieval/msitss.dll
/home/lvcoyote/.wine/drive_c/Program Files/Internet Explorer
/home/lvcoyote/.wine/drive_c/Program Files/Internet Explorer/W2K
/home/lvcoyote/.wine/drive_c/Program Files/Internet Explorer/W2K/ieex.cab
/home/lvcoyote/.wine/drive_c/Program Files/Internet Explorer/W2K/expinst.exe
/home/lvcoyote/.wine/drive_c/Program Files/Internet Explorer/W2K/ieexinst.inf
/home/lvcoyote/.wine/drive_c/Program Files/Internet Explorer/readme.txt
/home/lvcoyote/.wine/drive_c/Program Files/Internet Explorer/SIGNUP
/home/lvcoyote/.wine/drive_c/Program Files/Internet Explorer/SIGNUP/INSTALL.INS
/home/lvcoyote/.wine/drive_c/Program Files/Internet Explorer/iedetect.dll
/home/lvcoyote/.wine/drive_c/Program Files/Internet Explorer/support.txt
/home/lvcoyote/.wine/drive_c/Program Files/Internet Explorer/iesetup.cif
/home/lvcoyote/.wine/drive_c/Program Files/Internet Explorer/Connection Wizard
/home/lvcoyote/.wine/drive_c/Program Files/Internet Explorer/Connection Wizard/phone.icw
/home/lvcoyote/.wine/drive_c/Program Files/Internet Explorer/fixie.inf
/home/lvcoyote/.wine/drive_c/Program Files/Internet Explorer/iexplore.exe
/home/lvcoyote/.wine/drive_c/Program Files/Outlook Express
/home/lvcoyote/.wine/drive_c/Program Files/Outlook Express/oemiglib.dll
/home/lvcoyote/.wine/drive_c/Program Files/Outlook Express/oemig50.exe
/home/lvcoyote/.wine/drive_c/Program Files/Outlook Express/setup50.exe
/home/lvcoyote/.wine/drive_c/Program Files/Outlook Express/msimn.exe
/home/lvcoyote/.wine/drive_c/Program Files/Outlook Express/msoe.txt
/home/lvcoyote/.wine/drive_c/Program Files/Outlook Express/wabfind.dll
/home/lvcoyote/.wine/drive_c/Program Files/Outlook Express/oeimport.dll
/home/lvcoyote/.wine/drive_c/Program Files/Outlook Express/msoe.dll
/home/lvcoyote/.wine/drive_c/Program Files/Outlook Express/msoeres.dll
/home/lvcoyote/.wine/drive_c/Program Files/Outlook Express/wabmig.exe
/home/lvcoyote/.wine/drive_c/Program Files/Outlook Express/wab.exe
/home/lvcoyote/.wine/drive_c/Program Files/Outlook Express/wabimp.dll
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/2DMgr100.dll
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/Streets.chm
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/streets.aw
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/Data
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/Data/USAP2M.DAT
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/Data/USA_HD.mad
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/Data/MSMBase.htm
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/Data/USARoute.DAT
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/Data/USAARTS.ITS
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/Data/USARoute.VLF
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/Data/USA_ATT.psi
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/Data/MSD8.htm
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/Data/USAGeom.DAT
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/Data/ConstructionA4052609.dat
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/Data/USARoute.DCT
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/MapExt10.dll
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/Streets.hlp
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/dw.exe
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/Samples
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/Samples/color sample.bmp
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/Samples/color table.pal
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/msvcp60.dll
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/BUGREP10.dll
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/Streets.exe
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/1033
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/1033/dwintl.dll
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/Templates
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/Templates/New North American Map.stt
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/readme.htm
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/GPrn100.dll
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/BR90.dll
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/WSTasks
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/WSTasks/StrtTrip.xtr
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/WSTasks/FindAddr.png
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/WSTasks/TaskST.aw
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/WSTasks/StrtTrip.png
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/WSTasks/STSmall.png
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/WSTasks/Direct.png
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/WSTasks/FindPlac.png
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/WSTasks/FindNear.png
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/MOBB110.dll
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/MSM10USA.dll
/home/lvcoyote/.wine/drive_c/Program Files/Microsoft Streets and Trips/mfc42.dll
/home/lvcoyote/.wine/backup
/home/lvcoyote/.wine/backup/ole32.dll
/home/lvcoyote/.wine/backup/oleaut32.dll
/home/lvcoyote/.wine/backup/olepro32.dll
/home/lvcoyote/.wine/backup/rpcrt4.dll
/home/lvcoyote/.wine/dll-backup
/home/lvcoyote/.wine/dosdevices
/home/lvcoyote/.wine/dosdevices/y:
/home/lvcoyote/.wine/dosdevices/a:
/home/lvcoyote/.wine/dosdevices/c:
/home/lvcoyote/.wine/dosdevices/d::
/home/lvcoyote/.wine/dosdevices/d:
/home/lvcoyote/.wine/dosdevices/z:
/home/lvcoyote/.wine/userdef.reg
/home/lvcoyote/.wine/system.reg
/home/lvcoyote/.wine/user.reg
/home/lvcoyote/.wine.stderr.log
/home/lvcoyote/.nautilus/metafiles/file:%2F%2F%2Fhome%2Flvcoyote%2F.wine%2Fdrive_c%2FProgram%2520Files.xml
/home/lvcoyote/.nautilus/metafiles/file:%2F%2F%2Fhome%2Flvcoyote%2F.wine%2Fdrive_c%2Fwindows%2Fprofiles%2Flvcoyote%2FFavorites.xml
/var/cache/apt/archives/wine_0.9.55~winehq0~ubuntu~7.10-1_i386.deb
/var/cache/apt/archives/wine_0.9.56~winehq0~ubuntu~7.10-1_i386.deb
/var/lib/dpkg/info/wine-doors.postrm
/var/lib/dpkg/info/wine-doors.list
/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_gutsy_Release
/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_gutsy_main_binary-i386_Packages
/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_gutsy_Release.gpg
/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_gutsy_main_source_Sources
/var/lib/python-support/python2.5/winewrite.pyc
/var/lib/python-support/python2.5/wineread.py
/var/lib/python-support/python2.5/winewrite.py
/var/lib/python-support/python2.5/wineread.pyc
lvcoyote@lvcoyote-desktop:~$ 

[/PHP]

What now???....LOL

---

### Post by Lvcoyote on 2008-03-08
Ok, I did the following
gksudo nautilus
show hidden files
found the folders for playonlinux, wine and wine-dorrs and removed them.  I'll try installing wine again and see what happens now.

---

### Post by Lvcoyote on 2008-03-09
Ok, that got wine to load and after running winecfg everything appears ok.  I opened terminal and ran "notepad" and it opened also.  I still have the problem of wine not showing anywhere in the start menu, including system/preferences/main menu, its not even in there so I can add it.

---

### Post by Lvcoyote on 2008-03-09
Ok, I found another thread here on how to get wine to show in the menu, thats working now too.  Now that I have it working and before I screw it all up again, can someone tell me the best way to get Internet Explorer and Windows Media player installed???

---

### Post by mc4man on 2008-03-09
If you want to stay solely with wine go here and do some searching and reading. [http://appdb.winehq.org/](http://appdb.winehq.org/)
Otherwise your back to trying wine doors - seems flaky at best

---

### Post by CarpKing on 2008-03-09
For Internet Explorer, there's a "fake" IE that is actually using Gecko (I think it's called iexplore).  There's also a script to install three versions of IE (5, 5.5, and 6) called ies4linux.  For newer versions, probably download the installer from Microsoft and check AppDB to see if they have any hints.  Same goes for Media Player, unless you find some other way on the forums here.

---

### Post by Lvcoyote on 2008-03-09
I tried ies4linux, playonlinux, wine-doors and installing from the directions at winehq.  I did a complete uninstall of everything before trying each option.  Never could get it to work.  While I have managed to get wine and all the others installed and showing in the menu, I just cant get it to do what I need it to do which is to run the programs.  Playonlinux came the closest as it actually installed IE6 with an included script, but alas IE6 would not run.

At this point I gave up on wine and all its little brothers and installed VMware 1.4 and loaded a copy of Windows 2000 SP4 to it, not what I wanted to do but I do have IE and WMP at my disposal from within Ubuntu, keeps me from having to restart the computer and boot to the other OS's I have.

I appreciate all the help, I'll try again at the next release!!!

---

