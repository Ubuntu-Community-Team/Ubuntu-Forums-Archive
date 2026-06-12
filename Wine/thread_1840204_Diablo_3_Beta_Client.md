---
title: "Diablo 3 Beta Client"
date: 2011-09-07
forum: Wine
---

### Post by 8Kuula on 2011-09-07
Do not look promissing.

Tried that D3 Beta client installer.

First it did not go forward on "Updating setup files..." until I did kill Agent.exe process.

Blizzard Launcher did start, and stops on "Installing..." without going forward.
Agent.exe is up again so I think that Agent.exe has something to do with communicating to server. If Agent.exe is killed then launcher crys about communication error.

I used VirtualBox to get installer download files.

Now even when starting Diablo III.exe directly it still starts that Agent.exe. So can't get pass that.

Launcher stops on "Updating tools 100%" and console spams
```
fixme:process:GetLogicalProcessorInformation (0x1afe3dc,0x1afe3d8): stub
```

Wine v1.3.26
OS: Ubuntu 10.04.3
Beta Client Installer: [http://www.diablofans.com/topic/28060-diablo-iii-beta-client-leaks/](http://www.diablofans.com/topic/28060-diablo-iii-beta-client-leaks/)

---

### Post by tkmn on 2011-09-07
I had no problems with the installation part. Already configured for Starcraft 2.

I think this fix is for the Installer: 
```
To get the updater working you need to install ie6 via winetricks:

winetricks ie6

OR set the override for "mshtml" to "native" in winecfg 
```

When I try to run the game it complains about unsupported graphics card. I have a Radeon HD 5750. However it did start **once** for unknown reasons. Menu working fine just like SC2 but when I tried to log in it crashed.

---

### Post by 8Kuula on 2011-09-07
winetrics ie6: error 404: not found.

so tried
winetricks ie7, ended up with box "internet explorer 7 is not supported on this operating system."

still ends up on "fixme:process:GetLogicalProcessorInformation (0x1afe3dc,0x1afe3d8): stub" spam

override method was no go either.

SC2 works on default prefix (atleast for me), and used same prefix these tests.

---

### Post by 8Kuula on 2011-09-08
Yee, beta client started up!

Used virtualbox again to get client patched to v0.3.0.7318 Beta.
After that it did startup with wine v1.3.26.

Looks alot more promissing now :)

Launcher did not detect my graphics card right thou says I have nVidia GTX 280, I have GTX 285, and sound do not work, asuming login screen has atleast some music.

No idea do actual game work, just up to login screen.

---

### Post by alphasoup on 2012-04-21
Today: the weekend of Diablo 3 free beta trial, greate but
there is just one patch missing to get this working with latest wine:
[http://source.winehq.org/patches/data/85573](http://source.winehq.org/patches/data/85573)
Here are the steps I followed on Ubuntu 11.10, you must build the
latest git source today with the one patch missing else the
installer will not be able to load and install the gaime :(

This verifies that only this one patch is needed for Diablo 3 free beta
to work on Ubuntu 11.10 latest release (today).

 # 1) Setup a directories to build git wine software

 $ sudo mkdir -p /opt/local/src

 $ cd /opt/local/src

 # 2) Give yourself access to this dir
 $ sudo chown yourlogin:yourlogin /opt/local/src

 # 3) Get the latest source from winehq (currently 1.5) and go to that dir
 $ git clone git://source.winehq.org/git/wine.git /opt/local/src/wine-git

 $ cd wine-git
 /opt/local/src/wine-git

 # 4) Figure out all the packages you will need to build wine form source
 # See how to install wine "The Ubuntu Way" 
 # [http://wiki.winehq.org/WineOn64bit#head-245e8f90708da8070a4f3cbe336254c712af07e2](http://wiki.winehq.org/WineOn64bit#head-245e8f90708da8070a4f3cbe336254c712af07e2)

 # If you don't have it already: 
 $ sudo add-apt-repository ppa:ubuntu-wine/ppa

 # Then get the require packages (not wine1.5!)
 $ sudo apt-get build-dep wine1.5
...
Selecting previously deselected package gcc-4.5-base.
...
(for me this installed 40 new packages)

 # 5) Get and apply [somehow] the one patch still required to wine1.5 git:
[http://source.winehq.org/patches/data/85573](http://source.winehq.org/patches/data/85573)
 # the patch changes a couple of lines in these 2 files: 
 # dlls/ws2_32/socket.c
 # server/async.c
 # I apply the code change manually as I did not find the actual patch file source anywhere :(
 # perhaps just cutting last portion of the email give syou a bug.patch file that can be patched...

 # 6) Configure the patched wine (note the prefix option!):
 $ ./configure --prefix=/opt/local

 # 7) Make the patched wine1.5 git (this can take over 1 hour), then install it if successful:
 $ make

 $ sudo make install

 # Note: thanks to prefix this patch build will not overwrite
 # your existing installation of wine in /usr/bin
 # this will put the latest patched version of wine in /opt/local/bin

 # 8) Download the client from blizzard.net for Diablo II beta (now) it goes into: $HOME/Downloads/Diablo-III-Beta-enUS-Setup.exe 

 # 9) Start the install via YOUR NEW PATCHED WINE 1.5 (this is on 1 line):

 $ env WINEPREFIX="$HOME/.wine" /opt/local/bin/wine $HOME/Downloads/Diablo-III-Beta-enUS-Setup.exe 

 # This will prompt you to wine intall Gecko, go ahead
 # then the setup program will start installing the game
 # worked first time after that, no config issue, no restart required
 # (note could not adjust the graphics setting from the game, that quit,
 # everything else worked so far for several hours...)

You still have time to do the above (about 2-3 hours depending on your connection speed)
 Enjoy the game :)

---

### Post by plo_dev on 2012-04-21
> **alphasoup said:**
> Today: the weekend of Diablo 3 free beta trial, greate but
.....

You still have time to do the above (about 2-3 hours depending on your connection speed)
 Enjoy the game :)

It works for me! Big thanks to you!

---

### Post by gameame on 2012-04-21
After:

> **alphasoup said:**
> 
 # If you don't have it already: 
 $ sudo add-apt-repository ppa:ubuntu-wine/ppa


You should add:

 $ sudo apt-get update

---

### Post by Eriad on 2012-04-21
> **alphasoup said:**
> 
 # 5) Get and apply [somehow] the one patch still required to wine1.5 git:
[http://source.winehq.org/patches/data/85573](http://source.winehq.org/patches/data/85573)
 # the patch changes a couple of lines in these 2 files: 
 # dlls/ws2_32/socket.c
 # server/async.c
 # I apply the code change manually as I did not find the actual patch file source anywhere :(
 # perhaps just cutting last portion of the email give syou a bug.patch file that can be patched...


Could you give a mini tutorial about what needs to be done with the patch. Or is it as simple as finding where a lump of the code is and just pasting it over where it was?

After reading it a bit can someone confirm that all I need to do is delete the lines marked with a '-' and add the lines with a '+'

---

### Post by subdee on 2012-04-22
If you are on 12.04, there's no chance to build wine from source unless you have tons of patience.

[https://bugs.launchpad.net/ubuntu/+source/wine1.4/+bug/944321/comments/8](https://bugs.launchpad.net/ubuntu/+source/wine1.4/+bug/944321/comments/8)

---

