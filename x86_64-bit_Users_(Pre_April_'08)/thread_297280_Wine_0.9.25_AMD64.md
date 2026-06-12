---
title: "Wine 0.9.25 AMD64"
date: 2006-11-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by napsilan on 2006-11-10
Feisty AMD64 Wine .9.36
[http://rapidshare.com/files/28642102/wine_0.9.36-1_amd64.deb.html](http://rapidshare.com/files/28642102/wine_0.9.36-1_amd64.deb.html)


To install
```

sudo dpkg -i wine_0.9.36-1_amd64.deb
winecfg

```

To remove
```

sudo dpkg -r wine

```
These do NOT include dependency information.  If things do not work, try the following (from [http://www.ubuntuforums.org/showthread.php?t=291620](http://www.ubuntuforums.org/showthread.php?t=291620)).  Once finals are over I'm going to see if I can include the needed dependencies in the deb without all the developement ones.  These are the packages needed to compile, and they are overkill to run, but covers most/all of the dependency stuff for now.  
```

sudo aptitude install build-essential flex bison libc6-i386 libc6-dev-i386
sudo aptitude install libasound2-dev libaudiofile-dev libesd0-dev libjack0.100.0-dev
sudo aptitude install libaudio-dev libcapi20-dev liblcms1-dev libcupsys2-dev
sudo aptitude install libsane-dev libfreetype6-dev fontforge freeglut3-dev
sudo aptitude install libexpat1-dev libfontconfig1-dev libgcrypt11-dev libglib1.2-dev
sudo aptitude install libglib2.0-dev libgnutls-dev libgpg-error-dev libice-dev
sudo aptitude install libieee1284-3-dev libjpeg62-dev libldap2-dev libltdl3-dev
sudo aptitude install libmad0-dev libmng-dev libncurses5-dev libogg-dev
sudo aptitude install libopencdk8-dev libpng12-dev libqt3-mt-dev libsm-dev
sudo aptitude install libtasn1-3-dev libusb-dev libvorbis-dev libx11-dev
sudo aptitude install libxcursor-dev libxext-dev libxft-dev libxi-dev
sudo aptitude install libxml2-dev libxmu-dev libxrandr-dev libxrender-dev
sudo aptitude install libxslt1-dev libxt-dev libxv-dev render-dev
sudo aptitude install unixodbc-dev x-dev zlib1g-dev xlibs-dev
sudo aptitude install libxxf86dga-dev libxxf86vm-dev libungif4-dev libssl-dev
sudo aptitude install libgphoto2-dev ia32-libs

```

Old Version
Wine 9.30 Edgy AMD64
[http://rapidshare.com/files/15729269/wine_0.9.30-1_amd64.deb.html](http://rapidshare.com/files/15729269/wine_0.9.30-1_amd64.deb.html)

Wine 9.28 Edgy AMD64 
[http://rapidshare.com/files/8610145/wine_0.9.28-1_amd64.deb.html](http://rapidshare.com/files/8610145/wine_0.9.28-1_amd64.deb.html)
[https://netfiles.uiuc.edu/agoodri2/wine_0.9.28-1_amd64.deb](https://netfiles.uiuc.edu/agoodri2/wine_0.9.28-1_amd64.deb)

Wine 9.27 AMD64 Edgy Package compiled by perdurablehubris
[https://netfiles.uiuc.edu/southwor/shared/wine_0.9.27-1_amd64.deb](https://netfiles.uiuc.edu/southwor/shared/wine_0.9.27-1_amd64.deb)

and mine (.5mb bigger for some reason)
[http://rapidshare.com/files/8524277/wine_0.9.27-1_amd64.deb.html](http://rapidshare.com/files/8524277/wine_0.9.27-1_amd64.deb.html)
[https://netfiles.uiuc.edu/agoodri2/wine_0.9.27-1_amd64.deb](https://netfiles.uiuc.edu/agoodri2/wine_0.9.27-1_amd64.deb)


Wine 9.26 AMD64 Edgy
[https://netfiles.uiuc.edu/agoodri2/wine_0.9.26-1_amd64.deb](https://netfiles.uiuc.edu/agoodri2/wine_0.9.26-1_amd64.deb)

Friend's compile.
[https://netfiles.uiuc.edu/agoodri2/wine_0.9.26-1_amd64_hubris.deb](https://netfiles.uiuc.edu/agoodri2/wine_0.9.26-1_amd64_hubris.deb)

Wine 9.25 AMD64 Edgy
[https://netfiles.uiuc.edu/agoodri2/wine_0.9.25-1_amd64_alsa.deb](https://netfiles.uiuc.edu/agoodri2/wine_0.9.25-1_amd64_alsa.deb)

Wine 9.25 without alsa
[https://netfiles.uiuc.edu/agoodri2/wine_0.9.25-1_amd64.deb](https://netfiles.uiuc.edu/agoodri2/wine_0.9.25-1_amd64.deb)

Credit to RoyArne ([http://www.ubuntuforums.org/showthread.php?t=291620](http://www.ubuntuforums.org/showthread.php?t=291620)) for original instructions

RAOF's repository will probably update faster than my posts here.  Credit to RAOF for this
[http://raof.dyndns.org/falcon](http://raof.dyndns.org/falcon)

---

### Post by darkshadow on 2006-11-11
Thank you. This helped alot.

---

### Post by scorpio810 on 2006-11-16
hello
this deb is for edgy no for dapper ?

laurent@ubuntu:~/temp$ sudo dpkg -i wine_0.9.25-1_amd64.deb
Password:
Sélection du paquet wine précédemment désélectionné.
(Lecture de la base de données... 202245 fichiers et répertoires déjà installés.)
Préparation du remplacement de wine 0.9.21~winehq0~ubuntu~6.06-1 (en utilisant wine_0.9.25-1_amd64.deb) ...
Dépaquetage de la mise à jour de wine ...
Paramétrage de wine (0.9.25-1) ...
laurent@ubuntu:~/temp$ cd
laurent@ubuntu:~$ winecfg
/usr/local/bin/wine: /lib32/libc.so.6: version `GLIBC_2.4' not found (required by /usr/local/bin/../lib/libwine.so.1)
laurent@ubuntu:~$ sudo ln -s /usr/lib32/libX11.so.6 /usr/lib32/libX11.so
ln: création d'un lien symbolique `/usr/lib32/libX11.so' vers `/usr/lib32/libX11.so.6': Le fichier existe.
laurent@ubuntu:~$ sudo ln -s /usr/lib32/libXext.so.6 /usr/lib32/libXext.so
ln: création d'un lien symbolique `/usr/lib32/libXext.so' vers `/usr/lib32/libXext.so.6': Le fichier existe.
laurent@ubuntu:~$ sudo ln -s /usr/lib32/libfreetype.so.6 /usr/lib32/libfreetype.so
ln: création d'un lien symbolique `/usr/lib32/libfreetype.so' vers `/usr/lib32/libfreetype.so.6': Le fichier existe.
laurent@ubuntu:~$ sudo ln -s /usr/lib32/libz.so.1 /usr/lib32/libz.so
ln: création d'un lien symbolique `/usr/lib32/libz.so' vers `/usr/lib32/libz.so.1': Le fichier existe.
laurent@ubuntu:~$ sudo ln -s /usr/lib32/libGL.so.1 /usr/lib32/libGL.so
ln: création d'un lien symbolique `/usr/lib32/libGL.so' vers `/usr/lib32/libGL.so.1': Le fichier existe.
laurent@ubuntu:~$ sudo ln -s /usr/lib32/libGLU.so.1 /usr/lib32/libGLU.so
ln: création d'un lien symbolique `/usr/lib32/libGLU.so' vers `/usr/lib32/libGLU.so.1': Le fichier existe.
laurent@ubuntu:~$ sudo ln -s /usr/lib32/libXrender.so.1 /usr/lib32/libXrender.so
laurent@ubuntu:~$ winecfg
/usr/local/bin/wine: /lib32/libc.so.6: version `GLIBC_2.4' not found (required by /usr/local/bin/../lib/libwine.so.1)

---

### Post by napsilan on 2006-11-16
compiled on edgy

also 
```
/usr/local/bin/wine: /lib32/libc.so.6: version `GLIBC_2.4' not found (required by /usr/local/bin/../lib/libwine.so.1)
```

check synaptic to make sure you have libc stuff installed.  "libc6" seemed like a likely candidate when I took a quick look just now.

---

### Post by xstaticxgpx on 2006-11-16
well it looked like the wine developers fixed the 64bit build error, but i just successfully built wine 64bit myself, using the info on [this page]("http://wiki.winehq.org/WineOn64bit#head-56206e8bc74083807ffe06ccb471d3f964cb670a")

---

### Post by scorpio810 on 2006-11-16
> **xstaticxgpx said:**
> well it looked like the wine developers fixed the 64bit build error, but i just successfully built wine 64bit myself, using the info on [this page]("http://wiki.winehq.org/WineOn64bit#head-56206e8bc74083807ffe06ccb471d3f964cb670a")

thank you

---

### Post by xstaticxgpx on 2006-11-16
also if anyone wants to build wine themselve, follow [this]("http://wiki.winehq.org/WineOn64bit#head-56206e8bc74083807ffe06ccb471d3f964cb670a")  guide, and download this* copy of libsicuuc.a, copy it to /usr/lib32, and then edit the wine dir/dll/gdi32/Makefile so that it says "EXTRALIBS = /usr/**lib32**/libsicuuc.a /usr/lib/libsicudata.a -lstdc++ -lgcc_s" _instead_ of "EXTRALIBS = /usr/**lib**/libsicuuc.a /usr/lib/libsicudata.a -lstdc++ -lgcc_s"

and then use "LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" CC="gcc-3.4 -m32" ./configure" to configure it, and then do make depend && make all - then use sudo checkinstall to make the .deb


* [http://www.box.net/public/dnvzg6maep](http://www.box.net/public/dnvzg6maep)

---

### Post by xstaticxgpx on 2006-11-16
napsilan, did you build these packages? if so, do you know how to integrate the alsa support?

---

### Post by napsilan on 2006-11-16
I built the two packages in my first post.  In order to get ALSA working, I searched synaptic for "ALSA" and randomly installed anything that looked like an ALSA development package.  I recompiled wine and alsa worked. I wish it were more scientific.  I think the packages were "libasound2-dev" and "lib32asound2-dev".

---

### Post by xstaticxgpx on 2006-11-16
alright, thanks

---

### Post by jkwarras on 2006-11-17
Thanks for this package :)

---

### Post by scorpio810 on 2006-11-17
hello 
wine compil dont print for me
why ? 
but crosover print well

thanks

---

### Post by Sqwishy on 2006-11-17
i used the guide and built wine. it was built sucessfully but it won't run. here's the errors

I get lots of these
```
err:imagelist:ImageList_ReplaceIcon no color!
```
and a couple of these
```

Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!

```

---

### Post by scandar on 2006-11-17
I installed the libxxf86dga1 package. That solved it for me.

---

### Post by Kilz on 2006-11-17
> **scandar said:**
> I installed the libxxf86dga1 package. That solved it for me.

That is something I learned long ago. Its on my wine howto. The people who run into problems might want to look there. The link is in my signature. 
If anyone is having problems compiling wine they could alternatly install the i386 package. There is no loss of performance, because wine is a 32bit application layer. That means its 32bit, even if compiled to install to 64bit Ubuntu

---

### Post by xstaticxgpx on 2006-11-17
> **Kilz said:**
> That is something I learned long ago. Its on my wine howto. The people who run into problems might want to look there. The link is in my signature. 
If anyone is having problems compiling wine they could alternatly install the i386 package. There is no loss of performance, because wine is a 32bit application layer. That means its 32bit, even if compiled to install to 64bit Ubuntu

I don't agree with that. Even if wine is emulating windows 32bit, if the base app is utilizing your 64bit processor, then there has to be at least a slight boost in performance.

---

### Post by RAOF on 2006-11-18
> **xstaticxgpx said:**
> I don't agree with that. Even if wine is emulating windows 32bit, if the base app is utilizing your 64bit processor, then there has to be at least a slight boost in performance.

No.  **W**ine **I**s **N**ot an **E**mulator.  Actually, there'll probably be a slight drop in performance, because of the added overhead of switching between the x86-64 and IA32 modes.  Almost all of the processing done by the program is going to be done in the actual Windows program, which is IA32.

---

### Post by Kilz on 2006-11-18
> **RAOF said:**
> No.  **W**ine **I**s **N**ot an **E**mulator.  Actually, there'll probably be a slight drop in performance, because of the added overhead of switching between the x86-64 and IA32 modes.  Almost all of the processing done by the program is going to be done in the actual Windows program, which is IA32.

So it may have better performance with a 32bit package or at least none would be lost? Because there would be no overhead of switching between the x86-64 and IA32 modes?

---

### Post by RAOF on 2006-11-18
> **Kilz said:**
> So it may have better performance with a 32bit package or at least none would be lost? Because there would be no overhead of switching between the x86-64 and IA32 modes?

Well, there's always going to be the mode-switching overhead (the kernel runs in x86-64, after all), it just changes precisely where it is :).

But the speed differences between the x86-64 and IA32 packages should be negligible.

---

### Post by Sqwishy on 2006-11-18
> **Sqwishy said:**
> i used the guide and built wine. it was built sucessfully but it won't run. here's the errors

I get lots of these
```
err:imagelist:ImageList_ReplaceIcon no color!
```
and a couple of these
```

Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!

```
yah is any1 goona help me? libxxf86dga1 was already installed (although i'm not sure scandar was talking to me...)

---

### Post by xstaticxgpx on 2006-11-18
> **Sqwishy said:**
> yah is any1 goona help me? libxxf86dga1 was already installed (although i'm not sure scandar was talking to me...)
 see if these packages help:

libx11-dev
xlibs-dev
libxxf86dga-dev
libxxf86misc-dev

---

### Post by RAOF on 2006-11-18
> **Sqwishy said:**
> yah is any1 goona help me? libxxf86dga1 was already installed (although i'm not sure scandar was talking to me...)

Is that the 32bit version of libxxf86dga?  Download the i386 deb from packages.ubuntu.com, extract it with **dpkg -x *pkgname* tmp/** and then copy the .so file(s) into /usr/lib32

---

### Post by Sqwishy on 2006-11-19
> **xstaticxgpx said:**
> see if these packages help:
libx11-dev
xlibs-dev
libxxf86dga-dev
libxxf86misc-dev gotem

> **RAOF said:**
> Is that the 32bit version of libxxf86dga?  Download the i386 deb from packages.ubuntu.com, extract it with **dpkg -x *pkgname* tmp/** and then copy the .so file(s) into /usr/lib32 got it

still doesn't work without recomplile. so i'm recompling it tonight
i get this error when running 'make depend && make' :(

```
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed.
make[2]: *** [ddraw.dll.so] Error 2
make[2]: Leaving directory `/home/sqwishy/Desktop/wine-0.9.25/dlls/ddraw'
make[1]: *** [ddraw] Error 2
make[1]: Leaving directory `/home/sqwishy/Desktop/wine-0.9.25/dlls'
make: *** [dlls] Error 2

```

---

### Post by Teroedni on 2006-11-19
Thanks napsilan
Ive been able to run 3dmark 2001 with your package:mrgreen:

---

### Post by scorpio810 on 2006-11-19
> **xstaticxgpx said:**
> also if anyone wants to build wine themselve, follow [this]("http://wiki.winehq.org/WineOn64bit#head-56206e8bc74083807ffe06ccb471d3f964cb670a")  guide, and download this* copy of libsicuuc.a, copy it to /usr/lib32, and then edit the wine dir/dll/gdi32/Makefile so that it says "EXTRALIBS = /usr/**lib32**/libsicuuc.a /usr/lib/libsicudata.a -lstdc++ -lgcc_s" _instead_ of "EXTRALIBS = /usr/**lib**/libsicuuc.a /usr/lib/libsicudata.a -lstdc++ -lgcc_s"

and then use "LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" CC="gcc-3.4 -m32" ./configure" to configure it, and then do make depend && make all - then use sudo checkinstall to make the .deb


* [http://www.box.net/public/dnvzg6maep](http://www.box.net/public/dnvzg6maep)

thanks xstaticxgpx
it 's works for me on dapper 6.06 amd64,and i install libicu34-dev for resolve problems with the make

It works great, thanks

---

### Post by flapane on 2006-11-21
it seems it works, but if I try to run a game, ONLY if I set "emulate virtual desktop", otherwise programs say: can't set video mode.
Unfortunately (donnow if it depends on new .25 or 64bit version) simcity3000 doesn't work
[[IMG]http://img156.imageshack.us/img156/8568/simcityko3.th.jpg[/IMG]](http://img156.imageshack.us/img156/8568/simcityko3.jpg)

this is comman&conquer
[[IMG]http://img156.imageshack.us/img156/92/tiberianne9.th.jpg[/IMG]](http://img156.imageshack.us/img156/92/tiberianne9.jpg)

diablo2, unhandeld violation, like the olders versions, even 32 and 64bit
[[IMG]http://img224.imageshack.us/img224/4480/diabloaz5.th.jpg[/IMG]](http://img224.imageshack.us/img224/4480/diabloaz5.jpg)

can't hear audio in van basco
[[IMG]http://img224.imageshack.us/img224/6515/screenshot3zj9.th.png[/IMG]](http://img224.imageshack.us/img224/6515/screenshot3zj9.png)

---

### Post by sargosis on 2006-11-21
I just followed the instructions and this is what the terminal output:

Selecting previously deselected package wine.
(Reading database ... 102363 files and directories currently installed.)
Unpacking wine (from wine_0.9.25-1_amd64_alsa.deb) ...
Setting up wine (0.9.25-1) ...


that's it. i'm still really new to Ubuntu, but the fact that it didn't spit out a bunch of errors seems like good news. i'm not sure if this was successful or not, could anyone let me know? also if this was indeed a success, how to i open wine now?

---

### Post by jonah1980 on 2006-11-21
hi just type

winecfg

into a terminal and this will set wine up for you

then you just have to install any .exe's as you would on windows, right click em and open them with wine

---

### Post by trinaryouroboros on 2006-11-28
You are definitely awesome, thanks for the simple how-to! 

Saved me a lot of self-skull-bashing while figuring out compilation issues with x86_64

:KS

---

### Post by napsilan on 2006-11-29
Added debs for wine 9.26 in first post

---

### Post by janfsd on 2006-12-01
> **napsilan said:**
> Added debs for wine 9.26 in first post

Thanks,but what is the difference between the two versions of 9.26 you posted?

---

### Post by napsilan on 2006-12-01
> Thanks,but what is the difference between the two versions of 9.26 you posted?

Mine is .4mb bigger for some reason.  We probably had different dev packages for different random things installed.  I posted them both simply to provide an alternative incase one doesn't work.  I'd recommend mine first because it probably has more stuff in it.

---

### Post by blitze on 2006-12-01
Did an install of your Wine package.

Very nice, thanks.  I have had no drama with Utorrent or with Reaper which was pleasently suprising.  Only need to learn how to get my VSTi's working with Linux and I could drop Windows on the Audio front.

I should also look into getting Steam up and running under Wine as I love RedOrchestra which is really the only Windows game I play.

My only other problem is getting sound working but that is a firmware loader issue I have to deal with.

Anyway, again, thanks.

---

### Post by 9tail on 2006-12-02
Should add dependencies
... like ia32-libs :-)

The amd64 confused my and I forgot about them.

If anyone see something like "/usr/share/local/bin/wine not found" then hes missing them

---

### Post by encho on 2006-12-03
> **9tail said:**
> Should add dependencies
... like ia32-libs :-)

The amd64 confused my and I forgot about them.

If anyone see something like "/usr/share/local/bin/wine not found" then hes missing them

Thanks, you've saved my day. I am new to 64 arch and was wondering why this was not working.

---

### Post by napsilan on 2006-12-03
The debs were made as a part of checkinstall, so I don't think it adds dependencies.  How do you add depencies to a deb file manually?  I'll be happy to do it.

---

### Post by Dungeon Keeper on 2006-12-05
Hi fellows,

The packages posted by napsilan helped me alot and wanna say thanks. Its a month since i start with ubuntu and i use wine to play some of my favorite games ;).

Here is a couple of scripts writed to compile wine with all dependences (even libicu34). They run without erros in my amd64 with a nvidia video card and perhaps this who wish to compile wine could use them too or add some improvements. Im just starting in bash script :D .

The 'libicu34.sh' is to download, compile an place libsicuuc.a in your /usr/lib32 directory. The 'wine.sh' is to download, compile and install wine. All process is divided in steps so you can follow and stop it if needed. This files was ziped and attached with this post. 

Check if opengl is working and WineHQ repository (deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main) is in your repository list before run 'wine.sh'.  Its download the wine source from it.

References:
[http://ubuntuforums.org/showthread.php?p=1711240]("http://ubuntuforums.org/showthread.php?p=1711240")
[http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/014dc737d64d660a/c6a0418f8bb469a5]("http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/014dc737d64d660a/c6a0418f8bb469a5")

My regards

---

### Post by janfsd on 2006-12-09
Any debs for 0.9.27 version?

---

### Post by perdurablehubris on 2006-12-09
Here's the deb for 0.9.27 that I compiled last night. 

[https://netfiles.uiuc.edu/southwor/shared/wine_0.9.27-1_amd64.deb](https://netfiles.uiuc.edu/southwor/shared/wine_0.9.27-1_amd64.deb)

It was made with checkinstall so it doesn't include any dependencies.

---

### Post by RAOF on 2006-12-10
Ok.  Everyone seems quite able to compile the new wine releases.  Now, I'd like to properly package Wine to get a working build for AMD64 in to the Universe repository.

So, for all those building wine - how are you doing it?  Are all the necessary packages in Ubuntu?  If there are packages missing, what are they and where do *you* get them?

---

### Post by napsilan on 2006-12-10
[http://www.ubuntuforums.org/showthread.php?t=291620](http://www.ubuntuforums.org/showthread.php?t=291620)  

This guide is how I did most of it.  "Wine will not compile if you install libicu34-dev listed at Recommended Packages on 32bit. No bi-directional text support." was one of the bigger hangups for compiling, although wine should run with it installed.  It's listed in synaptic as "libicu-dev".  Some of the steps in that are no longer necessary because it's specific to an older version, such as the configure flag.  

I have finals this week, when I have some time I'll look into how to properly make debs with dependencies and such.

---

### Post by jonah1980 on 2006-12-11
Wine 0.9.27 Released according to winehq website. just wondered if anyone could update the 64bit builds to this...

thanks

---

### Post by macross3003 on 2006-12-11
Gooooooooooooooooooooood Work!
Congratulations :d :d

---

### Post by jvc26 on 2006-12-14
Hi there downloaded [https://netfiles.uiuc.edu/agoodri2/w...27-1_amd64.deb](https://netfiles.uiuc.edu/agoodri2/w...27-1_amd64.deb) and ran:
sudo dpkg -i wine_0.9.27-1_amd64.deb

so far so good. 

However when I then run winecfg in terminal I get the error message:
exec: 29: /usr/local/bin/wine: not found 

any ideas?

Thanks,
Il

---

### Post by napsilan on 2006-12-14
try removing it (sudo dpkg -r wine) and trying the other deb from hubris.  Also, check [http://www.ubuntuforums.org/showthread.php?t=291620](http://www.ubuntuforums.org/showthread.php?t=291620) and see if installing the recommended packages solves anything.

---

### Post by jvc26 on 2006-12-14
Hmm... now very confused... after telling me it had successfully installed the [https://netfiles.uiuc.edu/agoodri2/w...27-1_amd64.deb](https://netfiles.uiuc.edu/agoodri2/w...27-1_amd64.deb) package on executing sudo dpkg -r wine it sends back the error:
(Reading database ... 120504 files and directories currently installed.)
Removing wine ...
dpkg - warning: while removing wine, directory `/usr/local/share' not empty so not removed.
dpkg - warning: while removing wine, directory `/usr/local/lib' not empty so not removed.
dpkg - warning: while removing wine, directory `/usr/local/bin' not empty so not removed.
dpkg - warning: while removing wine, directory `/usr/local' not empty so not removed.
Slightly confused: does this mean it didn't install at all? Or does it mean it did uninstall it but didnt remove those directories because there are other packages installed in them?
Thanks:
James

---

### Post by perdurablehubris on 2006-12-14
That's a normal message when removing wine.  It just means that non wine files were in those folders so it did not delete them.  

The package you need to get wine running is most likely ia32-libs, so either do a search in synaptic for it or just 
```
sudo apt-get install ia32-libs
```

That should get it running for you. If you still run into problems you can try installing all the dependencies in napsilan's first post.

---

### Post by jvc26 on 2006-12-15
Right that worked, thanks very much! I then got this error:

```

Failed to open the service control manager.
wine: '/home/james/.wine' created successfully.
err:module:load_builtin_dll failed to load .so lib for builtin L"winealsa.drv": libasound.so.2: cannot open shared object file: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet

```

Which I partially fixed by running:
```

sudo apt-get install lib32asound2-dev
sudo apt-get install libasound2-dev

```

So on the next install I got the error:
```
ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

```

I had a look around for ALSA packages which via synaptic threw up these possibles:

- lib32asound2 and lib32asound2-dev both of which I already have installed
- alsa-tools and alsa-tools-gui which are console and gui based alsa utilities for specific hardware
- alsa-source which is alsa source drivers
- about 10 or so various packages for 'alsa players'

Which of these does it want - I read the earlier post about lib32asound2 and lib32asound2-dev solving the problem, but sudo-apt-getting them has partially removed one of the errors, but not all of them, and what does it want for ALSA - or should I just have an adventurous installing session til I can find the one that I need? and what about the libjack.so - again a synaptic search for 'libjack' yields a whole load of things any ideas?

Apologies for the huge numbers of questions!
Thanks
Il

---

### Post by xaryC on 2006-12-15
Hi,

I succesfully installed wine with your package, but I cant seem to run DVD Decrypter. DVD Shrink runs fine.
I get the following error trying to open DVD Decrypter:

[PHP]olivier@linuxpc:~/.wine/drive_c/Program Files/DVD Decrypter$ wine DVDDecrypter.exe
libgcc_s.so.1 must be installed for pthread_cancel to work
wine client error:c: write: Bad file descriptor[/PHP]

any ideas?

Thanks in advance :)

---

### Post by SizzlerWA on 2006-12-18
Hi,

Nice instructions, thanks!

However, I've tried installing wine using your compile as well as other binaries and I always get the  following error when trying to run winecfg:

X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  144 (NV-GLX)
  Minor opcode of failed request:  4 ()
  Resource id in failed request:  0x24a
  Serial number of failed request:  19
  Current serial number in output stream:  19

I have an NVidia card.  It is OpenGL-enabled since glxgears runs fine.  I am running Xinerama with two monitors and have had no other problems except with winecfg.

Somebody please help!

Thanks.

---

### Post by blitze on 2006-12-22
With a dead link, I take it there is no Wine 0.9.27 for AMD64 then?

---

### Post by napsilan on 2006-12-22
Don't think any links should be dead there, but I added a RS link just incase.

---

### Post by exp0zed on 2006-12-22
```

winecfg 

/usr/local/bin/wine: /lib32/libc.so.6: version `GLIBC_2.4' not found (required by /usr/local/bin/../lib/libwine.so.1)

```

Not sure why I get this message when i have everything installed. Someone earlier in this post got the same message. Any clue on how to fix?

---

### Post by napsilan on 2006-12-22
did you try installing that massive list of programs in my first post?  It's the compile dependency list but it should cover some of the problems.  Otherwise, try

```

sudo ln -s /usr/lib32/libX11.so.6 /usr/lib32/libX11.so
sudo ln -s /usr/lib32/libXext.so.6 /usr/lib32/libXext.so
sudo ln -s /usr/lib32/libfreetype.so.6 /usr/lib32/libfreetype.so
sudo ln -s /usr/lib32/libz.so.1 /usr/lib32/libz.so
sudo ln -s /usr/lib32/libGL.so.1 /usr/lib32/libGL.so
sudo ln -s /usr/lib32/libGLU.so.1 /usr/lib32/libGLU.so
sudo ln -s /usr/lib32/libXrender.so.1 /usr/lib32/libXrender.so

```

again from [http://www.ubuntuforums.org/showthread.php?t=291620](http://www.ubuntuforums.org/showthread.php?t=291620)

---

### Post by b0le on 2006-12-23
When trying to upgrade America's Army 2.7 - 2.8 - using Wine 0.9.28 I get this error:
```

$ wine AA27to28Installer_Generic.exe
fixme:advapi:LookupAccountNameW (null) L"joel" (nil) 0x33bdd0 (nil) 0x33bdcc 0x33bdd8 - stub
fixme:advapi:LookupAccountNameW (null) L"joel" 0x170b00 0x33bdd0 0x170b18 0x33bdcc 0x33bdd8 - stub
err:msi:ITERATE_DuplicateFiles Failed to copy file L"c:\\Program Files\\Common Files\\InstallShield\\Driver\\9\\Intel 32\\IDriver.exe" -> L"c:\\Program Files\\Common Files\\InstallShield\\Driver\\9\\Intel 32\\", last error 80
fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveRegistryValues"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveFolders"
fixme:advapi:LookupAccountNameW (null) L"joel" (nil) 0x34f770 (nil) 0x34f76c 0x34f778 - stub
fixme:advapi:LookupAccountNameW (null) L"joel" 0x165ae8 0x34f770 0x165b00 0x34f76c 0x34f778 - stub
err:rpc:RPCRT4_OpenBinding receive failed
err:ole:ifproxy_get_public_ref IRemUnknown_RemAddRef returned with 0x800706c0, hrref = 0x00000000
err:ole:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800706c0
err:ole:CoGetClassObject no class object {b3ede298-ae75-4a1c-ab7e-1b9229b77bbe} could be created for context 0x4
err:msi:ITERATE_Actions Execution halted, action L"ISStartup" returned 1603
fixme:msi:msi_dialog_set_control_condition Unhandled action L"Default"
fixme:msi:msi_dialog_set_control_condition Unhandled action L"Default"

```

Joel

(I don't know if this is the right place to put this)

---

### Post by CybrSpy on 2007-01-10
Is someone working on the 64bit Ubuntu package for 0.9.29?  I know it just came out, but was curious.

Cheers

---

### Post by rogeriovinhal on 2007-01-10
I am trying to run Warcraft III, but it simply crashes after like 2 minutes without any reason. Whe sound simply goes choppy and and it locks hard the computer, forcing a hard-reset.

I installed the 0.9.28 wine, all the dependencies in the first page, and run it with wine Frozen\ Throne.exe -opengl

What should I do? I have ATI fglrx installed correctly.

---

### Post by janfsd on 2007-01-10
Maybe you can try another version of wine? I use an Nvidia card and Warcraft runs ok.

---

### Post by pay on 2007-01-12
It's not too hard to compile wine on amd64. I used this guide [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit) and sudo apt-get install ia32-libs*

---

### Post by flapane on 2007-01-12
any news about newer amd64 packages?

---

### Post by xstaticxgpx on 2007-01-12
looks like 0.9.29 fixed the libicu34-dev problem. The gdi32 api uses freetype now to compile.

---

### Post by janfsd on 2007-01-12
Well, I just made a deb file of the last wine, I didn't know it was so easy to compile...
Here is the link:
[http://rapidshare.com/files/11405931/wine_0.9.29-1_amd64.deb](http://rapidshare.com/files/11405931/wine_0.9.29-1_amd64.deb)

---

### Post by rogeriovinhal on 2007-01-15
I have recompiled the kernel, installed the newer fglrx drivers, but warcraft III still freezes everything up.

I noticed that the sound was a lot delayed from where it should be, so it may be the sound that is freezing everything. Also, it told me to change Hardware Acceleration to "Emulation" in winecfg, but if I do that, just after I start Warcraft, a loud and scratchy noise comes up and no recgnozable sound is heard.

I have a Nforce3 motherboard, so I have another Realtek ALC chipset for sound, (AC 97). I tried both ALSA and OSS drivers, the OSS seemed a little better, but still got a delay and asked for Emulation.

Anyone with similar problems got this through?

---

### Post by Doug11 on 2007-01-16
Success!!!!   First I did this..


sudo apt-get install ia32-libs

And then installed this..

> **perdurablehubris said:**
> Here's the deb for 0.9.27 that I compiled last night. 

[https://netfiles.uiuc.edu/southwor/shared/wine_0.9.27-1_amd64.deb](https://netfiles.uiuc.edu/southwor/shared/wine_0.9.27-1_amd64.deb)

It was made with checkinstall so it doesn't include any dependencies.

And had no problems at all. Thanks.

---

### Post by janfsd on 2007-01-28
There is a new version (9.30)
Here is the deb I made:
[http://rapidshare.com/files/13834386/wine_0.9.30-1_amd64.deb](http://rapidshare.com/files/13834386/wine_0.9.30-1_amd64.deb)

---

### Post by darkshadow on 2007-01-28
Can someone copy and paste the commands you use to compile these wine packages on 64 bit. I have a program that used to work under 0.9.17 on dapper64 but has broke on newer wine. I just want to use the old version but can't find and edgy compiles of such a old version.

---

### Post by mkoyle on 2007-01-28
> **napsilan said:**
> I built the two packages in my first post.  In order to get ALSA working, I searched synaptic for "ALSA" and randomly installed anything that looked like an ALSA development package.  I recompiled wine and alsa worked. I wish it were more scientific.  I think the packages were "libasound2-dev" and "lib32asound2-dev".

lib32asound2-dev did it for me; thanks.

---

### Post by janfsd on 2007-01-28
> **darkshadow said:**
> Can someone copy and paste the commands you use to compile these wine packages on 64 bit. I have a program that used to work under 0.9.17 on dapper64 but has broke on newer wine. I just want to use the old version but can't find and edgy compiles of such a old version.

I think that old versions are difficult to compile on amd64, however you can try here:
[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)
It describes how to compile on several distros. Hope it helps.

---

### Post by darkshadow on 2007-01-29
I have tried that before and can't get any version new or old to compile right. I must be missing some dependancies.

I know this version can be compiled on amd64 because I used it on my old 64bit dapper install.

---

### Post by janfsd on 2007-01-29
Maybe you can show the output of the error when compiling?

---

### Post by Azakus on 2007-01-29
Wine 0.9.30 has a bug where it dies on making the gdi32.dll file. It happens because the file needed to make gdi32, libsicuuc.a, is a 64-bit only ELF library, and ./configure doesn't port it right. I made a package with a modified libsicuuc.a and Makefile for gdi32. The file included, installwine+gw64Ver2.tar.gz is a script I modified to download all the necessary components for Wine, a 32-bit mouse patch for Guild Wars compatibility, and the necessary 32-bit libsicuuc.a file and Makefile for gdi32. All of it is automated through the script installwine+gw.sh.
Alternately, you could use this script if you don't want Guild Wars installed with Wine.
```
#/bin/bash
#This is a 64-bit only compile of WINE
#Includes modified Makefile for gdi32 and a 32-bit libsicuuc.a
sudo aptitude install patch libc6-i386 libc6-dev-i386 checkinstall

mkdir ~/winestuff
mv ./libsicuuc.a ~/winestuff/libsicuuc.a
mv ./Makefile_gdi32 ~/winestuff/Makefile_gdi32
cd ~/winestuff
wget http://kegel.com/wine/edgy.sh -O ~/winestuff/pkgs.sh
sudo sh ./pkgs.sh
wget http://prdownloads.sourceforge.net/wine/wine-0.9.30.tar.bz2 -O ~/winestuff/winesource.tar.bz2
wget http://jarn103.bravehost.com/32mouse.patch.html -O ~/winestuff/32mouse.patch
tar -xjvf winesource.tar.bz2
pushd wine-*/dlls/winex11.drv
patch <~/winestuff/32mouse.patch
popd
#Marks out necessary 32-bit paths
pushd /usr/lib32
sudo ln -s libX11.so.6 libX11.so
sudo ln -s libXext.so.6 libXext.so
sudo ln -s libfreetype.so.6 libfreetype.so
sudo ln -s libz.so.1 libz.so
sudo ln -s libGL.so.1 libGL.so
sudo ln -s libGLU.so.1 libGLU.so
popd
LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure
echo "Adding necessary 64-bit files"
sudo cp ~/winestuff/libsicuuc.a /usr/lib32/libsicuuc.a
cp ~/winestuff/Makefile_gdi32 ~/winestuff/wine-0.9.30/dlls/gdi32/Makefile
make depend
make
sudo checkinstall
wineprefixcreate
echo "Build Complete. Wine is ready to go"
```

---

### Post by janfsd on 2007-01-30
Are you sure about that? For me it compiles without problem.

---

### Post by Mongoose on 2007-01-30
The only problems I've had buliding where that one of the generated Makefiles doesn't link in GLU, and that's easy to fix with a -lGLU in the LIBS var or whatver the name is for it.  You'll know it if you see it.  ;)

---

### Post by rogeriovinhal on 2007-02-05
I did exatly like the tutorial told, but my compiled version of wine is missing some things.

If I get the i386 package and install it with dpkg --force-architecture, I try to run Diablo 2 Video Test, and it shows me Directdraw and Direct3d options to choose, and I can play the game nicely.

If I install my compiled version, Diablo 2 Video Test doesn't show any options, and says my computer can't run Diablo 2.

What is missing?

---

### Post by RAOF on 2007-02-05
A link to my repository, which has working AMD64 packages of wine 0.9.30.  No need to compile yourself :).

---

### Post by mikerduffy on 2007-02-06
> **RAOF said:**
> A link to my repository, which has working AMD64 packages of wine 0.9.30.  No need to compile yourself :).

Thank you!

---

### Post by rogeriovinhal on 2007-02-06
> **RAOF said:**
> A link to my repository, which has working AMD64 packages of wine 0.9.30.  No need to compile yourself :).

Your package does the same error as the one I compiled, D2Vidtest show no possible way to run.

In terminal, this is what is shown:

```

fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x194b30) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x194428)->(0x2002a,00000011)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x194428)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x194570)->(0x3002a,00000011)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x194570)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock


```

---

### Post by RAOF on 2007-02-06
> **rogeriovinhal said:**
> Your package does the same error as the one I compiled, D2Vidtest show no possible way to run.

In terminal, this is what is shown:

```

fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x194b30) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x194428)->(0x2002a,00000011)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x194428)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x194570)->(0x3002a,00000011)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x194570)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock


```

Interesting.  I don't know what's wrong, though, and I don't have Diablo 2 to test.  World of Warcraft works just fine for me though, although that is in OpenGL.

You could just --force-architecture the i386 deb in the meanwhile.

---

### Post by feld on 2007-02-07
dont waste your time building a 64bit wine. You're not going to get a performance increase. It's _just_ WINE!


apt-get install -u ia32-libs lib32asound2 lib32z1 lib32stdc++6 linux32 

go here:

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Download your .deb

dpkg -iE wine_version.deb


Done.

---

### Post by rogeriovinhal on 2007-02-07
> **feld said:**
> dont waste your time building a 64bit wine. You're not going to get a performance increase. It's _just_ WINE!


apt-get install -u ia32-libs lib32asound2 lib32z1 lib32stdc++6 linux32 

go here:

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Download your .deb

dpkg -iE wine_version.deb


Done.

Actually, that is what I am doing right now, but this doesn't work with many 3D games with me, including Warcraft III. If I compile it myself, I can run these games, but I lose Direct Draw for Diablo II. I would like a way to make direct draw work with my compiled wine so I could have both games working...

---

### Post by DRagonRage on 2007-02-11
can someone post another link somehow rapidshare is down :(

---

### Post by RAOF on 2007-02-11
Use my repository.  Links in my sig.

---

### Post by GreenMedallion on 2007-02-11
> **exp0zed said:**
> ```

winecfg 

/usr/local/bin/wine: /lib32/libc.so.6: version `GLIBC_2.4' not found (required by /usr/local/bin/../lib/libwine.so.1)

```

Not sure why I get this message when i have everything installed. Someone earlier in this post got the same message. Any clue on how to fix?


I'm getting this same message when trying to configure wine. Anyone know where/how to find the missing piece? All other dependencies seem to be installed.

---

### Post by firekat on 2007-02-28
Thanks for the deb.  I did an install and did a winecfg.  Interestingly enough during the processing to get winecfg up I actually here a ticking on my speakers,  I don't know if that is normal.

When I clicked on the audio tab on winecfg the following message came up in the terminal:

```
firekat@ubuntu:~$ winecfg
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
firekat@ubuntu:~$ 

```

In all my previous attempts at loading wine I got a lot more of a message regarding this.

It seems like I am really close.  What do I need to do now?

Thanx!

---

### Post by zoro on 2007-03-03
i'm getting that error too

---

### Post by RAOF on 2007-03-04
It's a warning, really.  It means you can't use the jack audio output.  But you don't want to, anyway.  Just use ALSA or OSS.

---

### Post by elyse on 2007-04-01
I followed the instructions and they worked quite well for me, except that wine does not seem to have picked up my CUPS printers the way it is supposed to. It doesn't recognize that there are any printers there at all (KDE recognizes several of them, and prints correctly, and the CUPS admin tool is happy.

Is this a known problem? Is there something I can do to configure CUPS so it is easier for WinE to recognize things?

---

### Post by prince_niceguy on 2007-04-17
can you put the latest version of wine .deb.. please...

thanks in advance...

---

### Post by xopher on 2007-04-18
How does installing this amd64-version of wine differ from --force-architecture installing the i386-version?

> xopher RAOF, hi, how does your wine_amd64 debs differ from installing wine-i386 with --force-architecture?
(RAOF) Pretty much not at all.
(RAOF) It's just nicer to be able to apt-get it.
(RAOF) Also, it's closer to being able to be included in the main Universe wine package :)
xopher RAOF, true, that'd be really nice..
xopher Are you going to update the wine in your repository btw? ;)
(RAOF) xopher: Yeah, sometime :)


---

### Post by kruppe on 2007-04-20
Thanks

---

### Post by dominicd on 2007-04-21
Wine 0.9.35 AMD64 (Edgy)
[http://rapidshare.com/files/27221274/wine_0.9.35-1_amd64.deb.html](http://rapidshare.com/files/27221274/wine_0.9.35-1_amd64.deb.html)

---

### Post by Azakus on 2007-04-22
> **xopher said:**
> How does installing this amd64-version of wine differ from --force-architecture installing the i386-version?

I've found that --force-architecture installing didn't include reliable sound. It was because 64-bit Ubuntu doesn't have a necessary 32-bit library, libsicuuc.a. It has to be generated for the 64-bit version, at least in my experience.

---

### Post by Tanker Bob on 2007-04-22
Will the Edgy version run on Feisty?  If not, can someone do a Feisty version?  Thanks.

---

### Post by Kilz on 2007-04-22
> **Azakus said:**
> I've found that --force-architecture installing didn't include reliable sound. It was because 64-bit Ubuntu doesn't have a necessary 32-bit library, libsicuuc.a. It has to be generated for the 64-bit version, at least in my experience.

If that lib for the i386 wine deb is needed it would be a simple thing to [download the i386 package]("http://packages.ubuntu.com/feisty/libdevel/libicu36-dev") that includes it, extract the files from the deb, then copy it/them into /usr/lib32 .

---

### Post by Azakus on 2007-04-22
> **Kilz said:**
> If that lib for the i386 wine deb is needed it would be a simple thing to [download the i386 package]("http://packages.ubuntu.com/feisty/libdevel/libicu36-dev") that includes it, extract the files from the deb, then copy it/them into /usr/lib32 .

Yeah, but I always compile my own and just add in the library in the compile script.

---

### Post by KamiCrazy on 2007-04-22
I'm trying to compile wine on my system again under feisty and I'm getting this error :(

```
gcc -m32 -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -g -O2  -o utils.o utils.c
utils.c: In function &#8216;set_tex_op&#8217;:
utils.c:2184: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.1/README.Bugs>.
Preprocessed source stored into /tmp/cc18nZgv.out file, please attach this to your bugreport.
make[2]: *** [utils.o] Error 1
make[2]: Leaving directory `/home/deon/winestuff/wine-0.9.35/dlls/wined3d'
make[1]: *** [wined3d] Error 2
make[1]: Leaving directory `/home/deon/winestuff/wine-0.9.35/dlls'
make: *** [dlls] Error 2

```

If someone has a guide on the steps required to compile wine from a clean install of feisty I would really appreciate that!

---

### Post by KamiCrazy on 2007-04-23
Okay I got it compiled and installed finally,

things which I did to make it all go

Get Azakus' script and do all the dependency stuff laid out in there including kedgels script for edgy, EXCEPT compile my own libsicuuc.a

followed kilz advice and downloaded the i386 package, unpacked it and copied libsic*.a to /usr/lib32

did a few more dependency stuff like apt-get install build-dep wine really I installed so many dependencies that I cannot remember what everything that I installed.

compiled wine using this config command

LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure CFLAGS=-fno-stack-protector --prefix=/usr/local

the no stack protector thing seemed to work me for and it compiled fine, installed up and runnning! Now I have to actually go and test whether any games work... not entirely in the clear yet.

I don't understand why I need the no stack protector and others don't...

---

### Post by Azakus on 2007-04-24
Here's a better version of my script.

---

### Post by Satman on 2007-04-26
Thanks Domonicd, 
your 9.35 64 bits version works fine on Feisty too.
Had to install it with dpkg in recovery mode though,  because it hanged in graphic mode.
Thanks again for your efforts

---

### Post by laxon on 2007-04-26
Thanks for the install script, works very well!!
Alex

---

### Post by jtnoob on 2007-04-29
I'm a total newb. Would this work in Feisty?

Thanks

---

### Post by tegger on 2007-04-29
the script generate a "wine_0.9.36-1_i386.deb"

```
tegger@asus:~/winestuff/wine-0.9.36$ sudo dpkg -i wine_0.9.36-1_i386.deb
Password:
dpkg: Fehler beim Bearbeiten von wine_0.9.36-1_i386.deb (--install):
 Paket-Architektur (i386) passt nicht zum System (amd64)
Fehler traten auf beim Bearbeiten von:
 wine_0.9.36-1_i386.deb
```

the same with VERSION 0.9.35... and now ?

EDIT: too simple....

in last part checkinstall, it asks you if you want to change something..... simple button 7 and typing amd64, ENTER....5min, finish, working fine on feisty

---

### Post by Azakus on 2007-04-29
Should be
```
sudo dpkg -i --force architecture wine_0.9.36-1_i386.deb
```

---

### Post by Tanker Bob on 2007-04-29
The 64-bit version posted earlier works great with the couple of apps I have installed under WINE.  So does forcing the archihtecture on the 32-bit verison.  Can't see any real difference between them.

---

### Post by napsilan on 2007-04-29
added Feisty .9.36 AMD64 to the first post.  Apologies for the really slow updates

---

### Post by Azakus on 2007-05-31
Wine is now compiling 64-bit versions for Feisty that you can add to sources.list.
```

## WineHQ - Ubuntu 7.04 "Feisty Fawn"
deb http://wine.budgetdedicated.com/apt feisty main
deb-src http://wine.budgetdedicated.com/apt feisty main
```
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

---

### Post by vandetta on 2007-09-28
This is what i get when follow the instruction at first page:

vandetta@vandetta-linux:~$ cd '/home/vandetta/Desktop' 
vandetta@vandetta-linux:~/Desktop$ sudo dpkg -i wine_0.9.36-1_amd64.deb
(Reading database ... 110750 files and directories currently installed.)
Unpacking wine (from wine_0.9.36-1_amd64.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing wine_0.9.36-1_amd64.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/local/lib/wine/user32.dll.so')
Errors were encountered while processing:
 wine_0.9.36-1_amd64.deb
vandetta@vandetta-linux:~/Desktop$ 

What should I do?

---

### Post by Kilz on 2007-09-28
> **vandetta said:**
> This is what i get when follow the instruction at first page:

vandetta@vandetta-linux:~$ cd '/home/vandetta/Desktop' 
vandetta@vandetta-linux:~/Desktop$ sudo dpkg -i wine_0.9.36-1_amd64.deb
(Reading database ... 110750 files and directories currently installed.)
Unpacking wine (from wine_0.9.36-1_amd64.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing wine_0.9.36-1_amd64.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/local/lib/wine/user32.dll.so')
Errors were encountered while processing:
 wine_0.9.36-1_amd64.deb
vandetta@vandetta-linux:~/Desktop$ 

What should I do?

```
sudo apt-get install -f
```
Let it remove the package as its pretty old.
[Go here,]("http://www.winehq.org/site/download-deb") add the repository with the command and then 
```
sudo apt-get install wine
```

---

### Post by vandetta on 2007-10-01
vandetta@vandetta-linux:~$ sudo apt-get install wine
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
ia32-libs lib32asound2 lib32gcc1 lib32stdc++6 lib32z1 libc6-i386
Suggested packages:
libasound2-plugins
The following NEW packages will be installed:
ia32-libs lib32asound2 lib32gcc1 lib32stdc++6 lib32z1 libc6-i386 wine
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.2MB/32.6MB of archives.
After unpacking 108MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) feisty/main ia32-libs 1.5ubuntu9 [17.9MB]
Get:2 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) feisty/main lib32asound2 1.0.13-1ubuntu5 [319kB]
Fetched 18.2MB in 37m9s (8154B/s)                                              
Selecting previously deselected package libc6-i386.
(Reading database ... 104611 files and directories currently installed.)
Unpacking libc6-i386 (from .../libc6-i386_2.5-0ubuntu14_amd64.deb) ...
Selecting previously deselected package lib32gcc1.
Unpacking lib32gcc1 (from .../lib32gcc1_1%3a4.1.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package lib32stdc++6.
Unpacking lib32stdc++6 (from .../lib32stdc++6_4.1.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package lib32z1.
Unpacking lib32z1 (from .../lib32z1_1%3a1.2.3-13ubuntu4_amd64.deb) ...
Selecting previously deselected package ia32-libs.
Unpacking ia32-libs (from .../ia32-libs_1.5ubuntu9_amd64.deb) ...
Selecting previously deselected package lib32asound2.
Unpacking lib32asound2 (from .../lib32asound2_1.0.13-1ubuntu5_amd64.deb) ...
Selecting previously deselected package wine.
Unpacking wine (from .../wine_0.9.46~winehq0~ubuntu~7.04-1_amd64.deb) ...
Setting up libc6-i386 (2.5-0ubuntu14) ...
Setting up lib32gcc1 (4.1.2-0ubuntu4) ...
Setting up lib32stdc++6 (4.1.2-0ubuntu4) ...
Setting up lib32z1 (1.2.3-13ubuntu4) ...
Setting up ia32-libs (1.5ubuntu9) ...
Setting up lib32asound2 (1.0.13-1ubuntu5) ...
Setting up wine (0.9.46~winehq0~ubuntu~7.04-1) ...
vandetta@vandetta-linux:~$ 

**I think there's no problem in the installation, but I still could not see wine in my menu, is there anything I missed?**

---

### Post by Kilz on 2007-10-01
> **vandetta said:**
> 
**I think there's no problem in the installation, but I still could not see wine in my menu, is there anything I missed?**


[This page]("http://tghc.org/winefaq.html") may help you understand wine better.

---

### Post by vandetta on 2007-10-01
Now I understood, thanks a lot :)

---

