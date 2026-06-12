---
title: "64 bit Wine packages for Feisty now available for testing"
date: 2007-05-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by YokoZar on 2007-05-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/wine/+bug/43324](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/43324) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				After a lot of annoying work, community involvement, and hacking, I am pleased to say I have a working Wine package for the amd64 architecture available for testing.

This will *not* run 64 bit Windows apps - instead, it's a version of the 32 bit Wine package that will build, install, and run cleanly under 64 bit Ubuntu.  This is fine, since almost all Windows apps that you will want to run are 32 bit applications anyway.


Installation instructions are the same as for the 32 bit package; simply go to [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb) and follow the instructions there.  Ignore the warning on that page to amd64 users for now, since that no longer applies to Feisty users with these new packages.

Please test the package to make sure it installs right.  I'm particularly interested if anything is different between this package and the results you get if you try to install the 32 bit package directly with the old hack found on this page: [http://wiki.winehq.org/UbuntuAMD64](http://wiki.winehq.org/UbuntuAMD64)


Also, feel free to talk about Wine in general here.

---

### Post by Ledah on 2007-05-03
First thanks for your work :)

Well, installation and 2D-Applications works fine with your package, but I get an error running an OpenGL game (Jedi Academy): "GLW_StartOpenGL() - could not load OpenGL subsystem". I get the same error with a self compiled package. If I use the i386 package the game runs without problems. I don't know, if the problem is a missing library or whatever on my computer or if it's a problem with the package.
Another point is, that your package doesn't support ALSA output, only OSS.

---

### Post by wildlifer on 2007-05-04
Just tried it out. Installs without fuss and seems to work fine. I use it only for some small scientific programs, and I see no difference between the 32bit and the 64bit version.

---

### Post by Kilz on 2007-05-04
> **wildlifer said:**
> Just tried it out. Installs without fuss and seems to work fine. I use it only for some small scientific programs, and I see no difference between the 32bit and the 64bit version.

For the most part you wont see any difference. The reason is that wine is a 32bit application layer. The only thing a 64bit package gives you is a little easier time installing it. The package for 64bit still only installs a 32bit application layer. Thats because Windows programs are all 32bit.

---

### Post by wildlifer on 2007-05-04
> **Kilz said:**
> For the most part you wont see any difference. The reason is that wine is a 32bit application layer. The only thing a 64bit package gives you is a little easier time installing it. The package for 64bit still only installs a 32bit application layer. Thats because Windows programs are all 32bit.

It's one more step towards a complete 64bit Ubuntu.

---

### Post by YokoZar on 2007-05-07
I've uploaded a new version of the package (0.9.36-3).  Is anyone still getting issues that aren't present when using the 32 bit version?

---

### Post by Rhubarb on 2007-05-07
YokoZar, I've just download wine 0.9.36-3 now, and am using 7-zip ([www.7-zip](www.7-zip)) 4.45 beta with it.
It's working perfectly here in Ubuntu 64bit.

Thanks :)

---

### Post by gbesso on 2007-05-08
> **YokoZar said:**
> I've uploaded a new version of the package (0.9.36-3).  Is anyone still getting issues that aren't present when using the 32 bit version?

Hey, thanks for compiling this!
I just installed it and it seems that it fails to link the linux fonts to wine, so only fonts that come with wine(about 5) are usable.
Doesn't happen with the i386 version.
Thanks!

---

### Post by Ledah on 2007-05-08
> **YokoZar said:**
> I've uploaded a new version of the package (0.9.36-3).  Is anyone still getting issues that aren't present when using the 32 bit version?
Hey, OpenGL works for me now and ALSA is available, too. Great work :)

---

### Post by dptxp on 2007-05-08
Great. 
I use 64 bit, now on Feisty, never used wine.

Since I want to run just a couple of Windows applications (hope that they run), I just want to know how much resources Wine shall use.

a) When No Windows application is running
b) When some Windows application is running.

If resources are large, shall it be possible to easily enable / disable Wine ?

If I am able to run the programs in Wine, I shall be able to run Pure Ubuntu.

---

### Post by sawjew on 2007-05-08
All the menu entries for wine apart from the uninstaller have disappeared.  I no longer have entries for winecfg etc. which I thought were great features.

---

### Post by crhylove on 2007-05-08
I posted this elsewhere, but San Andreas is VERY close to playable in Feisty, sans joystick support (which is essential for reasonable game play IMHO).  Here's the bug blocking it:

[http://bugs.winehq.org/show_bug.cgi?id=7800](http://bugs.winehq.org/show_bug.cgi?id=7800)

Hey, you SAID wine in general!

rhY

---

### Post by gbesso on 2007-05-08
> **dptxp said:**
> Great. 
I use 64 bit, now on Feisty, never used wine.

Since I want to run just a couple of Windows applications (hope that they run), I just want to know how much resources Wine shall use.

a) When No Windows application is running
b) When some Windows application is running.

If resources are large, shall it be possible to easily enable / disable Wine ?

If I am able to run the programs in Wine, I shall be able to run Pure Ubuntu.

When no windows applications are running, wine takes no resources other than disk space for your settings.
When windows applications are running, it takes about as much as it would take normally under windows, plus 10 or so MB for the api layer(wineserver and explorer.exe)

Running uTorrent here uses 3mb from wineserver, 14mb for explorer.exe and about 30mb for utorrent.exe

---

### Post by dptxp on 2007-05-09
> **gbesso said:**
> When no windows applications are running, wine takes no resources other than disk space for your settings.
When windows applications are running, it takes about as much as it would take normally under windows, plus 10 or so MB for the api layer(wineserver and explorer.exe)

Running uTorrent here uses 3mb from wineserver, 14mb for explorer.exe and about 30mb for utorrent.exe

Thanks gbesso.
I am going to install Wine.

---

### Post by YokoZar on 2007-05-10
> **dptxp said:**
> Great. 
I use 64 bit, now on Feisty, never used wine.

Since I want to run just a couple of Windows applications (hope that they run), I just want to know how much resources Wine shall use.

a) When No Windows application is running
b) When some Windows application is running.

If resources are large, shall it be possible to easily enable / disable Wine ?

If I am able to run the programs in Wine, I shall be able to run Pure Ubuntu.When no Windows applications are running, Wine isn't running either.  The only resources consumed are whatever disk space the applications take up.

When a Windows application is running, the application itself consumes the resources.  It should consume about whatever it does in Windows, although occasionally bugs in Wine will result in extra usage.

---

### Post by YokoZar on 2007-05-10
> **sawjew said:**
> All the menu entries for wine apart from the uninstaller have disappeared.  I no longer have entries for winecfg etc. which I thought were great features.What version of Ubuntu are you using (Kubuntu?), and where did you install Wine from previously?  Those menu entries aren't there to begin with in typical Wine installs (although they should be).

---

### Post by gbesso on 2007-05-13
> **gbesso said:**
> Hey, thanks for compiling this!
I just installed it and it seems that it fails to link the linux fonts to wine, so only fonts that come with wine(about 5) are usable.
Doesn't happen with the i386 version.
Thanks!

Is anyone else experiencing this issue?

---

### Post by luvallcomputers on 2007-05-15
The program installed fine and now under system settings I click on wine and add the windows program that I want to install but do not know how to install it now.

Great program for wine as soon as I get it to work.

---

### Post by DaRush on 2007-05-15
Can anyone clarify this for me??

In FC6 (64bit), wine was recently made available from their own repositories - I installed it using add/remove programs...  
It installed with a nifty folder and options under the applications menu (in gnome) and allowed me to launch any .exe by simply clicking on it.  

I switched back to 'buntu, and I installed the .deb, seems to work for some appz but I have no idea about how to configure it from the command line.  Is there a way to install it so it comes integrated into gnome???

---

### Post by Trismegister on 2007-05-18
Can you clarify the comment on the download page:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
that there is no WINE yet available for AMD64 processors.
I hope I read that right :)
I am running Ubuntu Feisty (AMD64 build) just great with Samba and supplied applications - super!
But still have Dreamweaver and GoLive sites to maintain .... would be nice to pop into AMD64 box!

---

### Post by ernstblaauw on 2007-05-18
> **Trismegister said:**
> Can you clarify the comment on the download page:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
that there is no WINE yet available for AMD64 processors.
I hope I read that right :)
I am running Ubuntu Feisty (AMD64 build) just great with Samba and supplied applications - super!
But still have Dreamweaver and GoLive sites to maintain .... would be nice to pop into AMD64 box!

Look here:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by YokoZar on 2007-05-19
> **Trismegister said:**
> Can you clarify the comment on the download page:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
that there is no WINE yet available for AMD64 processors.
I hope I read that right :)
I am running Ubuntu Feisty (AMD64 build) just great with Samba and supplied applications - super!
But still have Dreamweaver and GoLive sites to maintain .... would be nice to pop into AMD64 box!No you read it completely wrong.  Which means I wrote it confusingly.  There are amd64 bit feisty packages available now, but only feisty packages - no 64 bit for edgy or dapper.

---

### Post by DUNC4N on 2007-05-22
Help, so close.

I followed the instructions, and copied the steam exe from disk to a folder, then cd <foldername>

steam installed fine, but I forgot to install the tahoma.ttf font.

However I can't find the .wine in my home folder.

Although I can double click on the steam icon on my desktop, and it will run...
[[IMG]http://img256.imageshack.us/img256/8415/screenshotnv3.th.png[/IMG]](http://img256.imageshack.us/my.php?image=screenshotnv3.png)

Thanks in advance...

---

### Post by strumluff on 2007-05-22
To find the .wine folder in your home folder just do Ctrl+H in nautilus and you will be able to see the hidden files and folders. You should find .wine now.

If you still don't see a .wine folder run this in a terminal to create one:

```
winecfg
```

Hope it helps.

---

### Post by DUNC4N on 2007-05-22
Thanks I ended up cp-ing it and it worked, but then crashed right in the middle of steam updating...Grrrr.

I guess I'll try again, at least the font is installed :)

I appreciate the help, none the less. I'll remember that.:)

---

### Post by IngetSikte on 2007-05-23
I'm trying to use the file from winehq as described in the link. I got no problem installing it but when I try to start anything from the wine installtion, winevfg, wine, winecreateprefix, winefile and so on I get 100% cpu load and nothing at all happens. I'm using 64-bits version of feisty and have installed the newest version on wine and tried to reinstall it. I don't get any error messages so I don't know what to fix :(

---

### Post by Master Orion on 2007-05-23
Not bad at all.  I got the 64-bit wine package off [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) and it seems to work just fine on my Athon 64, Feisty system.  It's obviously a work in progress as the sound test function has a nice error fixme window basically reading: Coming Soon, lol.  So far, no problems with apps tho.

---

### Post by Lucho on 2007-05-24
I'm using 64-bit Feisty, and I gave the wine .debs a try. First the 0.9.36, and I couldn't
get it to work- not even winecfg*. A bit later I was able to DL the 0.9.37 .deb and got the same
result. I'm familiar with wine on 32-bit Etch, but here I can't even create a .wine folder. 

Outside of this bug, would simply copying my .wine folder from the 32-bit Etch work? In
any case, this is what happens when I try to use wine (the first and only result I got from
wine):
> 
lucho@ubuntu64:~$ winecfg
/usr/bin/wine: 1: Syntax error: "(" unexpected
lucho@ubuntu64:~$ 


       So, what exactly am I doing wrong?
* it might be useful to point out that both the 0.9.36 and 0.9.37 .debs installed cleanly with no 
fuss; they just won't run

---

### Post by DUNC4N on 2007-05-24
[[IMG]http://img472.imageshack.us/img472/4660/csspicek0gr6.th.png[/IMG]](http://img472.imageshack.us/my.php?image=csspicek0gr6.png)
Finally got it working pretty good, thanks :)

---

### Post by Lucho on 2007-05-27
> I'm using 64-bit Feisty, and I gave the wine .debs a try. First the 0.9.36, and I couldn't
 get it to work- not even winecfg*. A bit later I was able to DL the 0.9.37 .deb and got the same
 result. I'm familiar with wine on 32-bit Etch, but here I can't even create a .wine folder. 
 
 Outside of this bug, would simply copying my .wine folder from the 32-bit Etch work? In
 any case, this is what happens when I try to use wine (the first and only result I got from
 wine):
 
Quote:
 lucho@ubuntu64:~$ winecfg
 /usr/bin/wine: 1: Syntax error: "(" unexpected
 lucho@ubuntu64:~$ 
 So, what exactly am I doing wrong?
 * it might be useful to point out that both the 0.9.36 and 0.9.37 .debs installed cleanly with no 
 fuss; they just won't run

*BUMP*

       so far, still nothing except that infernal error message. Any ideas?

---

### Post by ConsummateK on 2007-05-27
Big Linux nub here (Installed AMD64 Feisty yesterday, first experience with Linux ever!)

My project today was going to be getting utorrent running through WINE. I followed all instructions from the above link (I hope)

Opened up the terminal and first ran:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

Then 

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
```

Finally

```
sudo apt-get update
```

And

```
sudo apt-get install wine
```

Everything seemed to be ship-shape what with all the text scrolling by on the terminal but then after all of this, I can't seem to find WINE anywhere on my machine. I installed Beagle and ran a search for "WINE" and it came back with 0 results....:-k

Now I might just be fundamentally misunderstanding how WINE works but I assumed it was an application that you would run normal Windows installs through?

I think I'll try to snag it again through the synaptic manager for now but any insight would be much appreciated :)

---

### Post by YokoZar on 2007-05-31
> **ConsummateK said:**
> Now I might just be fundamentally misunderstanding how WINE works but I assumed it was an application that you would run normal Windows installs through?Wine is not something you run in and of itself - you run applications with it.  Open a terminal, go to your utorrent.exe program, and type wine utorrent.exe - you'll see it run just fine.

It should be as simple as double clicking on the utorrent executable, but there's a bug in Gnome at the moment that gives you a really cryptic error message if you do this.  So, you have to use the terminal for now.

---

### Post by JAPrufrock on 2007-05-31
the executable file, "wine", is in /usr/bin.  Howerver, as previously mentioned, it has to run in conjunction with another executable Windows file.

---

### Post by sataniceaden saklura on 2007-06-13
he peps i have a little problem my wine wont run anything and when i go to treminal and type winecfg i get 

```

sakura@sakura-desktop:~$ winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
wine: Unhandled page fault on read access to 0x00000004 at address 0xf7f295ee (thread 0009), starting debugger...
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Usage:
        winedbg [ [ --gdb ] [ prog-name [ prog-args ] | <num> | file.mdmp | --help ]
sakura@sakura-desktop:~$ 
sakura@sakura-desktop:~$ 

```

any help???

---

### Post by SledgeHammer_999 on 2007-06-16
hey guys I have wine 0.9.37 installed. now there is 0.9.39 out. but no matter how many apt-get update the new version doesn't show up in synaptic. What do I do to install it?

---

### Post by darknightuk on 2007-06-16
> **SledgeHammer_999 said:**
> hey guys I have wine 0.9.37 installed. now there is 0.9.39 out. but no matter how many apt-get update the new version doesn't show up in synaptic. What do I do to install it?you dont they havnt been built yet, u can force install the i386 if u really need 0.9.39.
havn't got a clue why we are 2 versions behind with build now though

---

### Post by YokoZar on 2007-06-19
> **darknightuk said:**
> you dont they havnt been built yet, u can force install the i386 if u really need 0.9.39.
havn't got a clue why we are 2 versions behind with build now thoughIt's up to date now.

Sorry, was my fault.  A failure in my build machine combined with real life in a rather unfortunate way.

---

