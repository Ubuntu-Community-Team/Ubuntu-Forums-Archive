---
title: "Ubuntu 11.10 Linux: how to install WoW Cataclysm 4.2"
date: 2011-11-04
forum: Wine
---

### Post by Zettaichi on 2011-11-04
Hello guys,

I am extremely new to linux, so I was in need of some help with playing windows games in ubuntu. 
I understand, I need an emulator and I found several posts recommending WINE and others. I've tried several including wine and for the most part I get pass the installation, yet when it comes to launching the game (WOW) it does not pop up. 

Anyone have any ideas on how can I get it working?  

> Some hardware info:

- XFX Radeon HD 6950 (downloaded and installed the latest ver.)
- Intel i7 950 3.06ghz
- 6gm ram

---

### Post by thatguruguy on 2011-11-04
You may want to read the threads about WoW in the [Wine forum]("http://ubuntuforums.org/forumdisplay.php?f=313").

---

### Post by Dlambert on 2011-11-05
Taken from [http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine]("http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine")


Introduction Edit
This article primarily talks about setting up Wine for running the MS Windows version of  World of Warcraft. Wine also runs on Macintosh computers with x86 CPUs under Mac OS X, but since Blizzard makes a Mac OS X native World of Warcraft client, running it under Wine is unnecessary and even silly.
World of Warcraft had a client for Linux while it was in the beta phase of development, but it was later dropped and never officially released.[1] Currently, WoW is run on Linux by use of Windows compatibility layers. Given that the World of Warcraft client is no longer officially developed to work in Linux, the installation of it on Linux is a somewhat more involved process than on Windows, which it is streamlined to install more easily on. However, with some careful research, and a bit of patience, it's very possible to do so.

Alternatively a streamlined process of installation and Windows installation conversion is available via Play On Linux.

While this guide will only cover the Wine compatibility layer, WoW is fully compatible with Crossover.

Preparation Edit
Before you begin the installation, you should run the following simple command, which will check whether your video card driver has DRI enabled, which allows WoW to run much faster (you may need to install package mesa-utils or equivalent for your distribution):
glxinfo | grep rendering
Which should return a line similar to this:
direct rendering: Yes
If this line says "No", it means that the graphics data will be handled in software rather than directly by the graphics hardware, thus significantly reducing speed at which WoW will run. Thankfully if you are using relatively recent hardware, enabling DRI is usually just a configuration issue.
For more information about enabling DRI, refer to the information from your distribution's support guides on graphic card driver installation. For extended personal help, forums and chatrooms are usually a good bet. Just tell them what the Make and Model of your graphic card is and they will be able to point you in the right direction. As always, remember that search engines are your friend.

Installing Wine Edit
Usually, installing the latest development version of Wine is the best option. However, sometimes Wine suffers from regression and some older version might perform better. If you are having trouble with one version, try another.
Distribution-specific methods Edit
Different GNU/Linux distributions use different methods of installing software, which oftentimes makes it hard to make easy installation options available for all distributions, especially for large and complex projects like Wine. Luckily a lot of energy has been put into making the distribution native installation methods available for a large variety of popular distributions. Please see [http://www.winehq.org/site/download](http://www.winehq.org/site/download) and follow the installation directions for your particular distribution.
Compiling Wine Edit
If you were unable to install Wine with a method found on that site, or if you are an experienced user wanting more control over the installation, then you may want to look into compiling Wine from source code. See the WineHQ wiki for information: [http://wiki.winehq.org/Recommended_Packages](http://wiki.winehq.org/Recommended_Packages)
Installing WoW Edit
It is only required to use one of these methods. If you have a preference, or one approach doesn't work for you, then try another.
Method 1: Download the client Edit
The simplest way to install the latest version of the full client is to get it from the Battle.net Dashboard. Simply run the installer, follow the prompts, and you'll end up with a fully patched, ready-to-play game.
Method 2: Use a pre-existing Windows installation Edit
If you're migrating to Linux from Windows and don't want to reinstall and repatch your client, it is possible to copy your existing installation to Linux.
It is also possible to run your Windows installation directly, which is useful in a multi-boot environment. However, for this to work correctly, you need read AND write access to your Windows (NTFS) partition. Most recent distributions support NTFS write out of the box, but explaining how to achieve NTFS write access is beyond the scope of this guide.

To copy your installation from Windows, simply copy your "World of Warcraft" directory from Windows to somewhere on your Linux partition.

To run WoW from your Windows partition, use:

 wine "/path/to/windows-partition/World of Warcraft/Wow.exe" -opengl
Note: If you run WoW in Windows after running it in Linux, you will have to change a few video settings back, like the shadow quality.
Method 3: Using installation CDs Edit
This method requires you to monitor the installation in order to switch CDs, but is usually faster than downloading the game and can be done without an internet connection.
Insert disc 1 in the CD/DVD drive, and do the following (replace /media/cdrom with wherever you mount your CDs):

wine /media/cdrom/Installer.exe
Some dialogs during installation may appear blank or garbled, and the installer may even hang for up to 5 minutes at 100% CPU, while appearing to be doing nothing. Simply wait and click next when possible.
Note: If the text is too small, and it annoys you: Please install msttcorefonts per instruction of your distribution.

As the installer runs, you will be prompted to change discs. If the installer repeatedly asks for the same disc, try unmounting the disc before ejecting, then insert the next disc.

If you have problems ejecting CDs in wine try: Start winecfg, then select Drives, and click auto detect drives Your CD drive should be assigned a letter, like "X: /media/cdrom" Now you can use that letter to eject the CD from Wine with:

 wine eject X:
You should now be able to eject the CD normally. You may need to repeat this process for each disc.
No Installer.exe? Edit
This may primarily be a Fuse problem, but may appear on other systems not using Fuse as well. Run the following command from a terminal:
 sudo mount -o remount,unhide /dev/cdrom
Note that your CD drive may not be /dev/cdrom! Check by running the command mount without arguments and look for a reasonable device (cd#, sr#, etc...)
Problems mounting the DVD (collectors edition for [Vanilla] and [TBC] and standard for [WotLK]) Edit
The issues might be related to either a defective (auto-)mount for the Hybrid Disks used (ISO 9660 and HFS+) or defective (auto-)mount without UDF support. For the Hybrid disks please refer to the specific documentation available on the internet. However the most likely cause is the missing UDF support when mounting the disc. In case it is mounted please unmount it
 umount /dev/drivename #(e.g. cdrom)
then use the following line to mount it again with UDF support:
 mount -t udf -o ro,unhide,uid=1000 /dev/drivename /mountpoint #(e.g. /mnt)
Playing Edit
Start from the Desktop Icon Edit
Double click the icon you find on your Desktop titled World of Warcraft, this will start the launcher. If you have never used something requiring HTML rendering with Wine you will be prompted to download and install the Gecko rendering engine, you should do this as it will enable the WoW Launcher to display news.
Start from the Terminal Edit
Starting from the terminal is simple, just enter:
wine "C:\\Program Files\\World of Warcraft\\Launcher.exe"
(install when prompted about the Gecko rendering engine)
Or, dive right into the game with:

wine "C:\\Program Files\\World of Warcraft\\WoW.exe" -opengl
Gnome menu icon Edit
You can make a Gnome menu entry by doing the following commands in a terminal (you will need superuser/root rights):
wget [http://images.wikia.com/wowwiki/images/d/d3/Wow-icon-scalable.svg](http://images.wikia.com/wowwiki/images/d/d3/Wow-icon-scalable.svg)
mv Wow-icon-scalable.svg /usr/share/icons/
gedit /usr/share/applications/wow.desktop
Add this to the text editor window, which should have appeared after the third command, change LAUNCHER in the Exec= line to command used to run Wow, and save:
[Desktop Entry]
Encoding=UTF-8
Name=World of Warcraft
Name[hr]=World of Warcraft
Exec=wine LAUNCHER
Icon=Wow-icon-scalable.svg
Terminal=false
Type=Application
Categories=Application;Game;
StartupNotify=false
Remember that you should also edit the Exec= line to reflect your WoW installation path, if you've installed to a special location.
Post-3.3.0 runtime errorEdit
Update to the most recent version of Wine or run:
 winetricks vcrun2005sp1
4.2 Launcher.exe hangs on "Downloading updated toolset..."Edit
On Fedora 14, run winetricks in the console by itself. When the winetricks window pops up with its options, choose "install game", and pick the wow trial client.
Miscellaneous Edit
For other relevant various information and tips please see Wine miscellaneous info.
For troubleshooting tips (including common problems and their workarounds), see Wine troubleshooting.
For Linux Native Ventrilo check out [http://www.mangler.org](http://www.mangler.org).

---

### Post by Tweak42 on 2011-11-06
> **Zettaichi said:**
> Hello guys,

I am extremely new to linux, so I was in need of some help with playing windows games in ubuntu. 
I understand, I need an emulator and I found several posts recommending WINE and others. I've tried several including wine and for the most part I get pass the installation, yet when it comes to launching the game (WOW) it does not pop up. 

Anyone have any ideas on how can I get it working?

I think the launcher is broken such that it will not launch the game when you hit play.  It should still patch the game ok, but to run the game you need to invoke the wow.exe directly.  If you did the typical install, open a terminal and enter:

```
wine "c:\program files\world of warcraft\wow.exe" -opengl
```

---

### Post by cwwilson721 on 2011-11-06
The answer is here in the forum (If anybody EVER cares to
SEARCH FIRST:

[http://ubuntuforums.org/showthread.php?t=1773985&highlight=cata]("http://ubuntuforums.org/showthread.php?t=1773985&highlight=cata")

---

### Post by tersogar on 2011-11-07
*I have several 85 levels characters all made under wine. **Just follow the link below. Since I have a fast internet connection I download the entire game after  making sure the*_direct rendering: Yes_ was done first. Remember that the last step is to Enable OpenGL with _Set gxApi ¨opengl¨._ Direct rendering / download the game / enable openGL and play. For me this process works like a charm. 
*[FONT=Tahoma][https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)[/FONT]*
[I]




[]("https://help.ubuntu.com/community/WorldofWarcraft")[/I]

---

### Post by Zettaichi on 2011-11-08
> **tersogar said:**
> *I have several 85 levels characters all made under wine. **Just follow the link below. Since I have a fast internet connection I download the entire game after  making sure the*_direct rendering: Yes_ was done first. Remember that the last step is to Enable OpenGL with _Set gxApi ¨opengl¨._ Direct rendering / download the game / enable openGL and play. For me this process works like a charm. 
*[FONT=Tahoma][https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)[/FONT]*
[I]

[]("https://help.ubuntu.com/community/WorldofWarcraft")[/I]

Thanks Tersogar.

for one of the guys above.

As I mention before, I am really new to linux in general. I did research how to install it and use several wine base software out there. But non really explained what I had to do or how to get it done.

Must post were, you need to configure this and that but did not help much since it didn't say how to do so. Due to time, I had to go back to win7 until my raid week finish so I can try the suggestions of some of you guys and take it from there. 

Thanks for the time and I appreciate the patient on explaining and offering guidance.

Zettai

---

### Post by Tweak42 on 2011-11-08
> **Zettaichi said:**
> Thanks Tersogar.

for one of the guys above.

As I mention before, I am really new to linux in general. I did research how to install it and use several wine base software out there. But non really explained what I had to do or how to get it done.

Must post were, you need to configure this and that but did not help much since it didn't say how to do so. Due to time, I had to go back to win7 until my raid week finish so I can try the suggestions of some of you guys and take it from there. 

Thanks for the time and I appreciate the patient on explaining and offering guidance.

Zettai

It's tricky to gauge how much actual linux knowledge you have when you say you are new to linux in general.  Some people are power windows users and have little difficulty making transition, others can be just as lost in windows as linux.  Additionally it can be tricky to ask the right questions to get the answers you need.  Patience is a must when starting out.

If you have a functioning wow install in windows, you can save a chunk of install/patch time copying the game directory into your linux partition.  Although you could run wow from the windows partition, it's not advised to avoid odd problems.

If you get stuck, PLEASE read the sticky guide thread [** Before asking for help with Wine << PLEASE READ BEFORE POSTING **]("http://ubuntuforums.org/showthread.php?t=885111")

---

### Post by Kaboom3009 on 2011-11-16
I thought about quoting the message with the 4 mile long explanation of how to get cata 4.2 to work in linux but I dont think many people would appreciate that. My basic question is will this work for a fresh install from scratch of WOW as well or is this specific to cata only.

I forsee many hours of WOW patches and updates ahead for me :(

---

### Post by Tweak42 on 2011-11-16
> **Kaboom3009 said:**
> I thought about quoting the message with the 4 mile long explanation of how to get cata 4.2 to work in linux but I dont think many people would appreciate that. My basic question is will this work for a fresh install from scratch of WOW as well or is this specific to cata only.

I forsee many hours of WOW patches and updates ahead for me :(

Unlike all previous expansions, Cata went back and revamped all the wow lvl 1-60 classic content (and added some new high lvl stuff) so it is now integrated with any fresh install of Wow.  What content you can access (races, zones & dungeons) and lvl cap is determined by which expansions are enabled on your account. 

A base trial install only pulls down the basics, but it will pull the rest of high lvl and expansions if you login with a expansion enabled account.  Pulling down all the content can take quite some time.

The fastest way to get the client is copy it from a existing (preferably updated) install.  The game is standalone so it's all you need to copy then entire wow directory.  Failing that, use a Cata DVD because older discs will practically require just as much download & patching as a full download install.

Lastly: MAKE A BACKUP of the game directory in case you need to wipe your wow install.  You can easily restore it and only need to download and patch recent updates.

---

### Post by burntout on 2012-02-03
I'm fairly new to Ubuntu so I'm trying to wrap my head around all this as i go along. 

Ive had a problem with this for the last few days, issue in itself being that wine keeps crashing while I'm attempting to download WoW through the launcher.

Any tips at all would be very welcome.

---

### Post by Tweak42 on 2012-02-03
> **burntout said:**
> I'm fairly new to Ubuntu so I'm trying to wrap my head around all this as i go along. 

Ive had a problem with this for the last few days, issue in itself being that wine keeps crashing while I'm attempting to download WoW through the launcher.

Any tips at all would be very welcome.

Biggest tip:  When asking for help be as detailed as possible of the problem, your setup, and what solutions you have tried.  There's a sticky thread at the top of the wine forum [** Before asking for help with Wine << PLEASE READ BEFORE POSTING **]("http://ubuntuforums.org/showthread.php?t=885111") if you need pointers.

That said, I think the P2P part of the wow launcher is still bugged.  You can disable it by running the BackgroundDownloader.exe in the game directory. Select View->Preferences->uncheck "Enable Peer-to-peer transfer", then try running the wow launcher.

---

### Post by Gadien on 2012-03-30
Wine Does NOT work for me. I followed all the basic commands that were posted here and on other sites, Even tried running WoW from the Windows XP partition.

The results are: Missing background on Starting screen;
Choppy graphics; I got into the Game, but as soon as i move it froze and I couldn't do anything except force my PC to shut down.

I'm using an EeePC 1000H with about 1G Ram and onboard Graphics. WoW works fine in XP, I just turn all the blazing Graphics down to bare minimum.

This game is the only thing keeping me from switching over to Linux. So if there's ANY possibility I can get WoW on this Ubuntu 11.10 I'll stay and work through the minor bugs.

Even if it means I have to PAY for crossover software. 

I've been struggling to move to Linux for 10 years. because it's so Alien to windows. 
I'm 30 now.

---

### Post by cwwilson721 on 2012-03-30
> **Gadien said:**
> Wine Does NOT work for me. I followed all the basic commands that were posted here and on other sites, Even tried running WoW from the Windows XP partition.

The results are: Missing background on Starting screen;
Choppy graphics; I got into the Game, but as soon as i move it froze and I couldn't do anything except force my PC to shut down.

[COLOR="Red"]I'm using an EeePC 1000H with about 1G Ram and onboard Graphics. [/COLOR]WoW works fine in XP, I just turn all the blazing Graphics down to bare minimum.

This game is the only thing keeping me from switching over to Linux. So if there's ANY possibility I can get WoW on this Ubuntu 11.10 I'll stay and work through the minor bugs.

Even if it means I have to PAY for crossover software. 

I've been struggling to move to Linux for 10 years. because it's so Alien to windows. 
I'm 30 now.

Odds are VERY high it'll never work good in Linux.

A Netbook just doesn't have the horsepower and graphics for running WoW in wine on Linux.

1GB ram and a Integrated Intel graphics chip just won't cut it.

Even in Windows (which doesn't use opengl, it uses D3D, so the Intel chip works better), you'll have a VERY hard time playing in more than a 5man setting. 10man MIGHT be playable, but 25man, BGs, large raids, large PvP battlegrounds, and even Home Cities will force your 'computer' to it's knees.

Using Crossover will change nothing (Crossover WILL NOT HELP). It's the Intel/opengl/weak hardware/terrible driver situation that is killing you.

P.S. Age means nothing. I'm 48 and use Ubuntu as my "main" distro. My kids (since age 3) have been using various Distros of Linux, too.

---

