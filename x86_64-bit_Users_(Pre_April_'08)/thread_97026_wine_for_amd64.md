---
title: "wine for amd64"
date: 2005-11-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Josef K. on 2005-11-30
is there somewhere a recent wine version amd64 packaged?!
I can't find one in repositories and compiling the source seems not to work ](*,) 

```

make[2]: *** [casemap.o] Error 1
make[2]: Leaving directory `~/wine-0.9.2/libs/unicode'
make[1]: *** [unicode] Error 2
make[1]: Leaving directory `~/wine-0.9.2/libs'
make: *** [libs] Error 2

```

---

### Post by TSJason on 2005-11-30
Hi,

 You'll need to setup a 32bit chroot for wine to run (at least for now). Checkout: [http://ubuntuforums.org/showthread.php?t=24575&highlight=32+bit+chroot](http://ubuntuforums.org/showthread.php?t=24575&highlight=32+bit+chroot)

 It doesn't cover wine but it should be enough to get you going.

---

### Post by Jeffj on 2005-11-30
[QUOTE=TSJason]Hi,

 You'll need to setup a 32bit chroot for wine to run (at least for now). Checkout: [http://ubuntuforums.org/showthread.php?t=24575&highlight=32+bit+chroot](http://ubuntuforums.org/showthread.php?t=24575&highlight=32+bit+chroot)

 It doesn't cover wine but it should be enough to get you going.[/QUOTE]

Why can't I compile the 64 bit version of wine? will that not work?
-Jeff

---

### Post by TSJason on 2005-11-30
Hi,

 They're using the 32-bit windows api implementation so I don't see why it would work natively if you tried to compiled it with 64-bit flags. I had attempted this a while back but it didn't work; the chroot, however, works fine.

---

### Post by RAOF on 2005-12-02
Or, if you think a chroot just for wine is a bit much, you can install all the ia32-libs, and manually download the deb from wine.sourceforge.net/apt.

From the console, after you've downloaded the .deb:
```
sudo apt-get install ia32-libs*
sudo dpkg -i --force-architecture whatever_the_name_of_the_wine_deb_is.deb
```
and there you have it.

---

### Post by RAOF on 2005-12-02
[QUOTE=Jeffj]Why can't I compile the 64 bit version of wine? will that not work?
-Jeff[/QUOTE]
You wouldn't want to compile it as a 64bit binary - it then couldn't interface with 32bit code, like each and every windows program you'd want to run.  You can't compile it with gcc-4, because the wine code is sufficiently broken that gcc-4 won't compile it.  It **will** compile with gcc-3.4, but I can never get gcc-3.4 to produce 32bit binaries under Ubuntu!  Of course, I **can** get gcc-4 to produce 32bit code. ](*,)

---

### Post by Josef K. on 2005-12-03
[QUOTE=RAOF]Or, if you think a chroot just for wine is a bit much, you can install all the ia32-libs, and manually download the deb from wine.sourceforge.net/apt.[/QUOTE]

don't work :(

```

err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:module:load_builtin_dll failed to load .so lib for builtin L"ddraw.dll": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:module:load_builtin_dll failed to load .so lib for builtin L"msxml3.dll": libxslt.so.1: cannot open shared object file: No such file or directory
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
wine: '~/.wine' created successfully.
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

```

---

### Post by RAOF on 2005-12-03
Really?  Damn, must have changed between 0.9 & whatever wine version is out now.

However, you should still be able to get it to work (although it's starting to get complicated):  Download the 32bit libXxf86dga deb from an Ubuntu repository, in the same way that you got the wine deb.  **Do not install it**.  Instead, extract it as an archive, and copy the .so file into your /lib32 directory.  Run ldconfig.

Now you should be able to wine.

---

### Post by pmandes on 2006-01-16
hello

still don't work :(

root@ubuntu:/lib32# ls -l libXxf86dga*
lrwxrwxrwx  1 root root    20 2006-01-16 15:30 libXxf86dga.so.1 -> libXxf86dga.so.1.0.0
-rw-r--r--  1 root root 17380 2006-01-16 15:15 libXxf86dga.so.1.0.0

trying to run something (as normal user):

$ winemine
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86vm.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86vm.so.1: cannot open shared object file: No such file or directory
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

any idea?

---

### Post by RAOF on 2006-01-16
Ah, ok.  Looks like you need the 32bit libXxf86vm library as well.  Just do the same thing as for the libXxf86dga lib.

---

### Post by evilpig on 2006-04-02
Sorry for bumping, but I want to thank RAOF for helping me fix it. I appreciate it. :D

---

### Post by DA_uf on 2006-04-16
Would someone be so kind as to post step by step instructions to get wine running on AMD64?  From what I gather, I will only be able to run 32-bit binaries, but something is better than nothing.

I tried [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) Building the Wine Package from Source using APT: but "apt-get --build source wine" complains:
**configure: error: C compiler cannot create executables**

I have build-essential so I don't know what else to do.

Also, are ubuntu repositories different than **k**ubuntu repositories?
I installed wine (albeit for an i686) on breezy kubuntu (server) at work wednesday.  Then thursday I installed breezy ubuntu (standard) at home on amd64.  I added universe and multiverse and even "deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/" and could not see wine in Synaptic.

EDIT:
I'm back at work on the i686 kubuntu with wine installed.  I reloaded repositories from within Synaptic and got:
Could not download all repository indexes
[http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz:) Sub-process bzip2 returned an error code (2)

This is not where I would expect wine to be.  But if it is supposed to be in this repository, then maybe that is a clue as to why I could not find wine over the weekend.

---

### Post by DA_uf on 2006-04-23
After more research, I believe I have never installed wine for AMD 64.  I think I was using Crossover Office (cxoffice) from the command line.  The standard version comes with an i386.deb, an i386.rpm, and a generic install.sh file.  I have to use the sh file on my AMD 64, but it does install.

But an app like xwine, that is available in the ubuntu repository still complains that wine is not installed.

Can I tell xwine (or other apps that need wine) to use cxoffice instead?  Maybe a symlink?

---

### Post by DragonOrta on 2006-04-24
OK, I've been having the same problem as pmandes, downoaded both files, and moved them to the /lib32 folder and am still getting this error.

> dragonorta64@dragonorta64:~/Desktop/Downloads$ wine utorrent.exe
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
dragonorta64@dragonorta64:~/Desktop/Downloads$


---

### Post by RAOF on 2006-04-24
[QUOTE=DragonOrta]OK, I've been having the same problem as pmandes, downoaded both files, and moved them to the /lib32 folder and am still getting this error.[/QUOTE]
Have you run **ldconfig**?  You'll need to ```
sudo ldconfig
```

---

### Post by skrållarn on 2006-04-28
> leaf@amd64:/lib32$ sudo ldconfig
ldconfig: /lib32/libXxf86dga.so.1.0.0 is not an ELF file - it has the wrong magic bytes at the start.

ldconfig: /lib32/libXxf86dga.so is not an ELF file - it has the wrong magic bytes at the start.

ldconfig: /lib32/libXxf86vm.so.1.0.0 is not an ELF file - it has the wrong magic bytes at the start.

ldconfig: /lib32/libXxf86vm.so is not an ELF file - it has the wrong magic bytes at the start.

leaf@amd64:/lib32$

still wont work...

---

### Post by RAOF on 2006-04-30
[QUOTE=skrållarn]still wont work...[/QUOTE]
Those errors mean that the libraries you've copied are corrupt.  Try downloading the debs again.

---

### Post by brcha on 2006-05-02
Hi,

I just made .debs for breezy and made them available on my apt repository. I made winetools package (i386 and amd64). I also mirrored wine for i386, so that both i386 and amd64 users can use my repo. The address is

   deb [http://brcha.no-ip.org/apt/](http://brcha.no-ip.org/apt/) unstable/
   deb-src [http://brcha.no-ip.org/apt/](http://brcha.no-ip.org/apt/) unstable/

If someone wants to mirror my repo, please go ahead. I have 256kbps connection, so mirroring is not unwanted :)

Best regards
Brcha

PS: I don't see why the repo wouldn't work for anyone using any debian/ubuntu on amd64.

---

### Post by jontxo on 2006-05-04
Brcha, when i try to play  gta san andreas with your wine package i can install the game but when i try to play with it i get the following error with a message box sayin' that this game needs directx 9.0
jontxo@demian:/media/sda4/GTA San Andreas/GTA San Andreas$ sudo wine gta_sa.exe fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
epoll_ctl: Operation not permitted
err:module:load_builtin_dll failed to load .so lib for builtin L"D3D8.DLL": libGL.so.1: cannot open shared object file: No such file or directory
jontxo@demian:/media/sda4/GTA San Andreas/GTA San Andreas$

---

### Post by jontxo on 2006-05-06
with the last version of the package that you've made when i execute wine or any other of the binaries of the package it doesn't show anything, i mean that no message is shown, only the cursor goes to the next line.

---

### Post by i23098 on 2006-05-15
[QUOTE=brcha]I just made .debs for breezy and made them available on my apt repository. I made winetools package (i386 and amd64).[/QUOTE]

Thanks =D> I've just seen this post, can't test it right now... Hope it works when I get home ;) 

Why don't you send a mail to Scott Ritchie (scott@open-vote.org), Wine's debian/ubuntu package maintaner? Maybe it's possible to put your package in wine official repository. :)

BTW, wine 0.9.13 has been released ;) :D

---

### Post by ruudiculus on 2006-05-21
This really works great (Dapper Drake-k8 system)!

Thanks for this relatively simple workaround!

---

### Post by flapane on 2006-05-22
[QUOTE=brcha]Hi,

I just made .debs for breezy and made them available on my apt repository. I made winetools package (i386 and amd64). I also mirrored wine for i386, so that both i386 and amd64 users can use my repo. The address is

   deb [http://brcha.no-ip.org/apt/](http://brcha.no-ip.org/apt/) unstable/
   deb-src [http://brcha.no-ip.org/apt/](http://brcha.no-ip.org/apt/) unstable/

If someone wants to mirror my repo, please go ahead. I have 256kbps connection, so mirroring is not unwanted :)

Best regards
Brcha

PS: I don't see why the repo wouldn't work for anyone using any debian/ubuntu on amd64.[/QUOTE]

wow i will try it with utorrent as soon as i get home!!!!

---

### Post by flapane on 2006-05-22
it doesn't happend anything

flapane@a64:~$ wine
wine              winedump          winepath
wineboot          winefile          wineprefixcreate
winebrowser       wineg++           wine-preloader
winebuild         winegcc           wine-pthread
winecfg           wine-kthread      wineserver
wineconsole       winelauncher      wineshelllink
winecpp           winemaker         winetools/
winedbg           winemine
flapane@a64:~$ winepath
flapane@a64:~$ linux32 wine
flapane@a64:~$ winefile
flapane@a64:~$ wine
flapane@a64:~$
                                  
all the commands have no effect

flapane@a64:~$ wine-kthread /media/sdb1/Altro/Download\ ZIP\ da\ Internet/utorrent-1.4.1-beta-build-406.exe
Segmentation fault
flapane@a64:~$ wine-kthread /media/sdb1/cpu\ z/cpuz.exe
Segmentation fault
flapane@a64:~$

---

### Post by darida on 2006-05-25
The same for me... when I type 'wine' just goes to a new line...:( 

Anybody can fix this ?
Thanks

---

### Post by flapane on 2006-05-25
unfortunately the developer of 64bit pkgs seems to be disappeared

---

### Post by RAOF on 2006-05-25
[QUOTE=darida]The same for me... when I type 'wine' just goes to a new line...:( 

Anybody can fix this ?
Thanks[/QUOTE]
What do you expect to happen when you type "wine"?  Wine just runs other programs.  A better way to check would be to run "winecfg" - that actually does the wine setup stuff (like where your "c:" drive is, the sound driver, etc).

Then, you run "wine */path/to/the/program*" to run something.  Like
**wine ./ProgressQuest.exe**

---

### Post by flapane on 2006-05-26
it's obvious, but I already tried winecfg, and it does a blank line

---

### Post by nuttycom on 2007-02-22
Well, I've followed the instructions here but wine (and winecfg) seem to be having problems setting up the virtual Windows root directory. Here's what I'm getting:

mirror@anaconda:~/download$ wine my.exe
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/mirror/download', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\my.exe": Module not found

Anyone have any ideas?

---

### Post by nuttycom on 2007-02-22
Sorry for the double...

Here's my output from winecfg:

mirror@anaconda:~/download$ winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/mirror/download', starting in the Windows directory.
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15

---

