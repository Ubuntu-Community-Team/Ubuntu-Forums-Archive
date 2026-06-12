---
title: "Howto:  Get Continuum (a.k.a. Subspace) to work with Ubuntu."
date: 2007-01-15
forum: Wine
---

### Post by Gen2ly on 2007-01-15
**[SIZE="6"][COLOR="DarkRed"]Howto Install Continuum[/COLOR][/SIZE]**

IMHO Subspace, a.k.a Continuum, is one of the best MMOPG's in... well, ever.  Yes, I'm biased, but this isn't a wiki ;).  Continuum/Subspace is a Windows game, so you will need Wine installed to play it.  For anyone who hasn't played Continuum, it is a online ship battle (hundreds of ships are possible) with a number of different game types.

[COLOR="Sienna"]**Warning:**[/COLOR] *Because Subspace is a highly mod-able game be sure you trust the administrators on the server.  Admins have been known to change settings on a ship by ship basis, on the fly.*

[[IMG]http://www.archive.org/download/ForgotThumb/Screenshot2.png[/IMG]]("http://www.archive.org/download/TitleContinuum/Screenshot.png")

**[SIZE="5"][COLOR="DarkRed"]Notes:[/COLOR][/SIZE]**

[LIST]
[*]There are two ways to do this: Either download a patched wine kernel and place it by hand (the easy way), or patching the wine source and compiling yourself (the other way :) ).
[*]If you perused my previous [HowTo]("http://www.ubuntuforums.org/showthread.php?p=1978740#post1978740") on this before, you may want to do this again.  It eventually ended up breaking my wine installation.
[/LIST]

**[SIZE="5"][COLOR="DarkRed"]Download Patched Wine[/COLOR][/SIZE]**

**1)** Install Wine as normal.
**2)** Rename the wine kernel:
```
sudo mv /usr/lib/wine/kernel32.dll.so{,.bak}
```
**3)** Get the patched wine kernel:
```
sudo wget http://subspace2.net/kernel32.dll.so -O /usr/lib/wine/kernel32.dll.so
```
**4)** Install Continuum (see step 15 in the next section).
**5)** Play...  Woohooo! :)

**[SIZE="5"][COLOR="DarkRed"]Compiling Wine[/COLOR][/SIZE]**

[LIST][*][COLOR="Sienna"]If you have wine already installed, make sure you remove it!  Synaptic Package Manager is probably the best way to do this.  I marked Wine for Complete Removal.[/COLOR]
[/LIST]

Installation is pretty simple.  We'll need patch Wine for Continuum to work and then compile it.  If you haven't tried compiling anything before this, don't worry, its not that big a deal.

Ok, lets do it.

**1)** This will need to be done as root.

```
sudo bash
```

**2)** These are the tools we'll needed compile Wine.

```
apt-get install build-essential flex bison xlibs-dev x11proto-gl-dev libgl1-mesa-dev fontconfig libfreetype6-dev fontforge checkinstall
```

**3)** I like to compile in the source directory.  So much cleaner.

```
cd /usr/src
```

**4)** Download wine source ( this command will get the source and uncompress it. )

```
apt-get source wine
```

**5)** Change to the uncompressed Wine directory

```
cd wine*
```

**6)** Open the text editor with new filename [FONT="Fixedsys"]cont.diff[/FONT] so that we can create the patch.

```
sudo gedit cont.diff
```

**7)** The text below is the patch.  Choose the right version for the build of Wine you are using.  

With versions Wine-0.9.3.38 and above.  Copy the text below and paste it in the new text file.

```
diff --git a/dlls/kernel32/process.c b/dlls/kernel32/process.c
index 33f9ee1..d50cb7d 100644
--- a/dlls/kernel32/process.c
+++ b/dlls/kernel32/process.c
@@ -2460,6 +2464,7 @@ HANDLE WINAPI OpenProcess( DWORD access,
     OBJECT_ATTRIBUTES   attr;
     CLIENT_ID           cid;
 
+if (access & PROCESS_VM_WRITE) return NULL;
     cid.UniqueProcess = ULongToHandle(id);
     cid.UniqueThread = 0; /* FIXME ? */
```

With versions prior to Wine-0.9.3.38. Copy the text below and paste it in the new text file.

```
diff --git a/dlls/kernel32/process.c b/dlls/kernel32/process.c
index 33f9ee1..d50cb7d 100644
--- a/dlls/kernel32/process.c
+++ b/dlls/kernel32/process.c
@@ -2460,6 +2464,7 @@ HANDLE WINAPI OpenProcess( DWORD access,
     OBJECT_ATTRIBUTES   attr;
     CLIENT_ID           cid;
 
+if (access & PROCESS_VM_WRITE) return NULL;
     cid.UniqueProcess = (HANDLE)id;
     cid.UniqueThread = 0; /* FIXME ? */
```

**8 )** Save the text file.  And apply the patch.

```
cat cont.diff | patch -p1
```

**9)** Configure so that your computer is ready to build wine - the CFLAGS varible is needed due to an Ubuntu Bug.

```
./configure CFLAGS=-fno-stack-protector
```

**10)** Build wine

```
make depend && make
```

This will take awhile depending on the computer, anywhere from 15 minutes to an hour.

**11)** Now the source code has been made into binaries and all the binary support files.  Make it a Debian Package if you wish so it's all nice and easy to install / uninstall.  Note, this also installs it.

```
checkinstall
```

**12)** Ok, done with the root stuff.

```
exit
```

**14)** Now we need to configure wine.

```
winecfg
```

It is important to run winecfg, select the Drives tab, click C:, Show Advanced, and set the Serial: value to a random number higher than 2000. If you do not, you cannot connect to catid billers, i.e the name you like may not be registered, or may cause other issues on the SSC biller.

**15)** Download Continuum

You can get Continuum [here]("http://getcontinuum.com/"). 

Now install it like any other program, click installer icon after you uncompress it.  

*Tip: Wine uses drive Z: for often than not for your root-partition.  Navigate from there to where you want to Install Continuum.*

**16)** Start Continuum

Change into the directory the Continuum is installed with the command-line.

```
cd ~/Games/Continuum
```

And start it: :)

```
wine Continuum.exe
```

That's it! 

**[SIZE="5"][COLOR="DarkRed"]Troubleshooting[/COLOR][/SIZE]**

**Graphics**

Continuum's graphic setting are best if they match your current desktop settings.  i.e. 16 bit color, etc.  But many find this isn't necessary.

**Sound**

If you experience snapping or crackly sound, or not sound at all!, try setting audio to emulation in the drop-down menu using [FONT="Fixedsys"]winecfg[/FONT].  If this doesn't work, try using OSS instead of Alsa.

**Add Continuum to the Gnome-menu**

To add Continuum to the Gnome-menu you can use a similar entry as the one below, substituting the location where you have Continuum installed.

```
[Desktop Entry]
Encoding=UTF-8
Name=Continuum
Type=Application
Comment=A Top Down Shooter Online
Exec=wine /home/USER/Applications/Continuum/Continuum.exe
Icon=continuum.png
Categories=Application;Game;ActionGame;
```

I nice icon can be found [here]("http://ssdownloads.com/index.php?act=file&fid=1320").  Place it in "/usr/share/pixmaps/continuum.png" to easily find it.

**[SIZE="5"][COLOR="DarkRed"]Resources:[/COLOR][/SIZE]**

[LIST]
[*]Linux / Continuum specific details [here]("http://wiki.minegoboom.com/index.php/Running_Continuum_under_Wine") 
[*]Learned what I needed to compile Wine for Ubuntu [here]("http://ubuntuforums.org/showthread.php?t=293533&highlight=howto+compile+wine+eve").
[/LIST]

---

### Post by Gen2ly on 2007-01-17
Oh, Powerball Rulez

---

### Post by Geekboy on 2007-01-23
Thanks, can't wait to get into this.  This game rocked back in the day!!  :KS:D

---

### Post by Geekboy on 2007-01-24
> 
6) copy the text below and paste it in the new text file.

 	Quote:
 	 	 		 			 				diff --git a/dlls/kernel32/process.c b/dlls/kernel32/process.c
index 33f9ee1..d50cb7d 100644
--- a/dlls/kernel32/process.c
+++ b/dlls/kernel32/process.c
@@ -2460,6 +2464,7 @@ HANDLE WINAPI OpenProcess( DWORD access,
     OBJECT_ATTRIBUTES   attr;
     CLIENT_ID           cid;
 
+if (access & PROCESS_VM_WRITE) return NULL;
     cid.UniqueProcess = (HANDLE)id;
     cid.UniqueThread = 0; /* FIXME ? */ 			 		 	 	 
7) save the text file.

8- apply the patch

 	Quote:
 	 	 		 			 				cat cont.diff | patch -p1
I get an error message applying the patch.  

> root@ubuntupc:~/wine-0.9.29# cat cont.diff | patch -p1
patching file dlls/kernel32/process.c
patch: **** malformed patch at line 6: OBJECT_ATTRIBUTES attr;
Any ideas?

---

### Post by Gen2ly on 2007-01-25
Try doing it again, Geekboy.  I typed it in incorrectly. :)

---

### Post by Geekboy on 2007-01-25
Thanks.  That fixed it.  It's great to be able to play this game again.

---

### Post by Jasper84 on 2007-01-28
EASIER WAY
Note that the website of continuum [http://subspace.net](http://subspace.net) itself has a special wine-with-continuum download now. For me, it worked in windowed mode. But black screen in full-screen mode, but its good enough for me.

---

### Post by Gen2ly on 2007-01-29
Full screen, no disctractions. ;)

Also, this isn't very difficult.  Took me about 15 to 20 minutes.

---

### Post by Gen2ly on 2007-03-23
Just added patch to wine 0.9.32 and it still works.

---

### Post by Endium on 2007-04-22
wow thanks for this. Im new to ubuntu and this was the only thing that I needed Windows for. 

i can't seem to get it to go fullscreen though. The menubars cut the top and bottom off.

---

### Post by Gen2ly on 2007-04-26
This is possibly a related to Beryl.  Since Beryl has an effect on all display properties it is possible that it has something to do with it.  Disable Beryl fist and try once more.

---

### Post by forgreatsource on 2007-06-22
nevermind

---

### Post by Gen2ly on 2007-06-22
> **forgreatsource said:**
> i get an error when ever i try to join a server the error is:

invalid password for the specified user. the name you entered may already be in use by another player ....

i get this no matter which user name i pic.
thanks

Yeah, alot of people use this game and use many different users - you'll probably have create a pretty unique username.  Also some servers may not let you create a new username.  Trench usually will.

---

### Post by Krusnix on 2007-07-04
Hey, I'm happy to see such a comprehensive newbie friendly tutorial compiled out of the somewhat vague minegoboom page. Thanks, but I've encountered an error. The following is what I get when I do the patching command "winecfg"
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/jathavan', starting in the Windows directory.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.

When I try to make the drive via winecfg I get this error popping up in the terminal "err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '../drive_c'".
I would also like to point out that I run Ubuntu Feisty Fawn. I've tried to make this as clear as possible, any assistance in the matter would be nice.

---

### Post by Gen2ly on 2007-07-04
> **Krusnix said:**
> Hey, I'm happy to see such a comprehensive newbie friendly tutorial compiled out of the somewhat vague minegoboom page. Thanks, but I've encountered an error. The following is what I get when I do the patching command "winecfg"
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/jathavan', starting in the Windows directory.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.

When I try to make the drive via winecfg I get this error popping up in the terminal "err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '../drive_c'".
I would also like to point out that I run Ubuntu Feisty Fawn. I've tried to make this as clear as possible, any assistance in the matter would be nice.

Hey!  Looks like you got the bulk of it done - the patching and compiling.  'winecfg' is a program to setup wine.  Are you using 'winecfg' as regular user?  If the error is the same, erase the directory ~/.wine, and try to start it once more.

---

### Post by Krusnix on 2007-07-07
Yeah, so I re-installed wine (after wiping ubuntu because I broke it extensively). I'm just confused now.. Do I install continuum with wine?

---

### Post by Gen2ly on 2007-07-07
> **Krusnix said:**
> Yeah, so I re-installed wine (after wiping ubuntu because I broke it extensively). I'm just confused now.. Do I install continuum with wine?

wine... its your best bet to goto the line and type:

```
wine continuum.0.39.exe
```

Or whatever the name of the installer it.  If you want to be able to click on a file and not use the command-line you can instruct sysctl to do so.

```
nano /etc/sysctl.conf 
```

```
fs.binfmt_misc.register = :WINEXE:M::MZ::/usr/bin/wine:
```

and add to fstab

```
none  /proc/sys/fs/binfmt_misc  binfmt_misc  defaults 0 0
```

---

### Post by Krusnix on 2007-07-14
Alright thanks!, now I just have to get windowed mode up and running, haha. But altogether great tutorial!

---

### Post by Gen2ly on 2007-07-18
Links to Continuum updated,

Powerball Rulez

---

### Post by Gen2ly on 2007-08-08
Updated and cleaned up.  Added new patch information for versions of Wine-0.9.3.38 and above.

---

### Post by kingvik on 2007-08-17
i'm new to linux so don't be to complex. Your tutorial was great i did everything and it got continuum to work, but then when i closed it and tried to open it i get "Fatal Error 000004bc"
So then I installed it in another location but I keep getting the same error message.

---

### Post by Gen2ly on 2007-08-18
Wine doesn't always cleanly disconnect from the system audio (alsa) after quiting.  You can logoff and logon again, or just restart sound:

```
sudo /etc/init.d/alsasound restart
```

---

### Post by kingvik on 2007-08-18
it wasn't working for me so i did it all again but now when i give the command, in the terminal, to start the game nothing happens, and when i click on the icon for it it starts to load and then just stops. then about 5 minutes later i get error 0000012b

---

### Post by Gen2ly on 2007-08-21
All I can think about is sound.  Well, you also try turning off desktop effects too.  Try messing with the settings a little bit too.

---

### Post by merkel04 on 2008-05-22
I went ahead and applied the patch to Wine RC1 and compiled it into a deb package. Its running continuum .40 great on ubuntu 8.04.

Heres the link: [http://www.pricent.com/subspace/winerc1_cont40_patched.deb](http://www.pricent.com/subspace/winerc1_cont40_patched.deb)

For those who prefer to do it manually through source, the same patch and instructions on the first post work perfectly with Wine RC1.

Thanks for the info,
Brian

---

### Post by rvergara on 2008-07-01
Melkel,

Your patched wine worked spotlessly.

Regards

Ramiro

---

### Post by Xog on 2009-11-04
> **merkel04 said:**
> I went ahead and applied the patch to Wine RC1 and compiled it into a deb package. Its running continuum .40 great on ubuntu 8.04.

Heres the link: [http://www.pricent.com/subspace/winerc1_cont40_patched.deb](http://www.pricent.com/subspace/winerc1_cont40_patched.deb)

For those who prefer to do it manually through source, the same patch and instructions on the first post work perfectly with Wine RC1.

Thanks for the info,
Brian

I have the same problem with the same error and I got it exactly the same way. However the patched Wine RC1 is no longer on that link. Anyone happen to know where I can find it?

---

### Post by Gen2ly on 2009-11-04
Xog, nowdays I just download and extract a patched wine kernel to the correct directory:

**1)** Install Wine and Continuum as normal.
**2)** Rename the wine kernel:
```
sudo mv /usr/lib/wine/kernel32.dll.so{,.bak}
```
**3)** Get the patched wine kernel:
```
sudo wget http://subspace2.net/kernel32.dll.so -O /usr/lib/wine/kernel32.dll.so
```
**4)** Play...  Woohooo! :)

I'll put these directions on the front page, hasn't been updated in a bit.

---

### Post by Xog on 2009-11-04
holy crap that was fast

i didn't think anybody would answer for such an unknown game.. and to think, you posted in this like 3 posts ago.. which was like 2 years ago! man.. im lucky thismorning.

PS: it worked. Thanks !!!

---

### Post by hushman on 2009-11-06
hi, great to see the thread active

what versions of ubuntu does the modified wine kernel work with
9.10?  64bit matter?

and also what version of wine to begin with, matter?

---

### Post by Xog on 2009-11-22
Gen2ly, is there a fix for the new 1.1.33 (1.2) wine version? It won't load. It was working fine before, however I need the new wine version.

---

### Post by Gen2ly on 2009-11-23
> **Xog said:**
> Gen2ly, is there a fix for the new 1.1.33 (1.2) wine version? It won't load. It was working fine before, however I need the new wine version.

I'd like to be able to help you Xog but am using wine-stable-1.0.1-8 here because I discovered it runs better for some of my games.  I'm guessing the the process.c file has been altered again and a new patch will need to be created.  You can look at the patch and see if you can fix it.  Otherwise, I'd ask in the [minegoboom](http://forums.minegoboom.com/) forums.  They would be the most likely to know how to fix this (they created the earlier patch) and see if they can help you.

---

### Post by Xog on 2009-12-04
Thanks,

> 
```

mkdir ~/contwine-build
cd ~/contwine-build
sudo apt-get build-dep wine
sudo apt-get source wine
cd wine1.2-1.1.31
sed -i '2568 i\\if (access \& PROCESS_VM_WRITE) return NULL;' dlls/kernel32/process.c
./configure
make
sudo checkinstall

```
At this point the modified wine is installed, so I ran the normal cont installation:
```

wget http://getcontinuum.com/downloads/continuum/Continuum040Setup.exe
wine Continuum040Setup.exe

```
and it all runs fine.

(note: if "checkinstall" isn't already installed, you may have to first issue "sudo apt-get install checkinstall" to get it)

---

### Post by mathfreak123 on 2009-12-12
I'm probably a little impatient in asking this, but the subspace2.net server doesn't seem to be working, so I can't download the new kernel32.dll.so.

I'm going to wait for a bit and see if it starts working again later, but if it doesn't, can someone provide a link for their kernel32's?:P

**Edit: Ok, I was a little impatient. subspace2.net is back online now.**

---

