---
title: "Compile Wine 0.9.24 on 64-bit Edgy"
date: 2006-11-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by RoyArne on 2006-11-02
EDIT: napsilan has compiled Wine 0.9.25 and made it available as [a .deb file]("http://www.ubuntuforums.org/showthread.php?t=297280"). Just download and install it!

This is how I installed [Wine 0.9.24]("http://www.winehq.org/?announce=0.9.24") on the 64-bit version of Ubuntu 6.10/Edgy Eft. Note that I have the Nvidia drivers, and build Wine with OpenGL.

**1. Get the source**

Download Wine from [sourceforge]("http://prdownloads.sourceforge.net/wine/wine-0.9.24.tar.bz2") or [ibiblio]("http://ibiblio.org/pub/linux/system/emulators/wine/wine-0.9.24.tar.bz2"). Open a terminal, and:

```
tar xjf /path/to/wine-0.9.24.tar.bz2
cd wine-0.9.24
```

**2. Install packages and make symbolic links in /usr/lib32**

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

Wine will not compile if you install libicu34-dev listed at [Recommended Packages on 32bit]("http://wiki.winehq.org/Recommended_Packages"). No bi-directional text support.

```
sudo ln -s /usr/lib32/libX11.so.6 /usr/lib32/libX11.so
sudo ln -s /usr/lib32/libXext.so.6 /usr/lib32/libXext.so
sudo ln -s /usr/lib32/libfreetype.so.6 /usr/lib32/libfreetype.so
sudo ln -s /usr/lib32/libz.so.1 /usr/lib32/libz.so
sudo ln -s /usr/lib32/libGL.so.1 /usr/lib32/libGL.so
sudo ln -s /usr/lib32/libGLU.so.1 /usr/lib32/libGLU.so
sudo ln -s /usr/lib32/libXrender.so.1 /usr/lib32/libXrender.so
```

**3. Configure, make and install.**

```
CFLAGS="-fno-stack-protector -O2" ./configure --verbose
make depend && make
sudo make install
```

**References**

[LIST]
[*][Recommended Packages on 32bit]("http://wiki.winehq.org/Recommended_Packages")
[*][Wine on 64-bit]("http://wiki.winehq.org/WineOn64bit")
[*][Building Wine from Source]("https://help.ubuntu.com/community/BuildingWineFromSource")
[*][WoW Nvidia flicker patch]("http://appdb.winehq.org/appview.php?iVersionId=5606")
[/LIST]

---

### Post by fabertawe on 2006-11-03
Hi RoyArne,

That's interesting... what advantage does this give you over forcing in the i386 deb as per Kilz's HowTo?

Paul

---

### Post by RoyArne on 2006-11-03
> **fabertawe said:**
> what advantage does this give you over forcing in the i386 deb as per Kilz's HowTo?

Probably none; I don't think I have read that howto, I was just trying to compile it myself.

When I searched the forums here I found one or two threads where people where having problems compiling it, so when I had found a working procedure I decided to post it here.

---

### Post by xstaticxgpx on 2006-11-03
one of those threads was mine, I'm intrigued on how you got your CFLAG variable, I don't have much expirience in coding, can you explain what the variable does? ty

---

### Post by xstaticxgpx on 2006-11-03
nvm, read your references. I'm a little disappointed in myself for missing the Recommended Packages page... ](*,)

edit** I'm still getting my error

> ld: Relocatable linking with relocations from format elf64-x86-64 (/usr/lib/libsicuuc.a(ubidi.ao)) to format elf32-i386 (gdi32.ia53P9.o) is not supported
winebuild: ld -m elf_i386 -r failed with status 256
winegcc: ../../tools/winebuild/winebuild failed.
make[2]: *** [gdi32.dll.so] Error 2


---

### Post by ekerazha on 2006-11-04
Somebody could make a package for Edgy AMD64 :)

---

### Post by RoyArne on 2006-11-04
> **xstaticxgpx said:**
> I'm intrigued on how you got your CFLAG variable, I don't have much expirience in coding, can you explain what the variable does? ty

I found that variable [in this thread]("http://www.ubuntuforums.org/showthread.php?t=286089") (third last post). I don't know what it does, I couldn't find it in the gcc documentation.

> **xstaticxgpx said:**
> I'm still getting my error

Did you install libicu34-dev? I got the same error until I removed libicu34-dev (libicu-dev).

---

### Post by Kilz on 2006-11-04
> **ekerazha said:**
> Somebody could make a package for Edgy AMD64 :)

I have tried, it isnt as easy as just making a package. The fact that the application is 32bit emulator (I know what wine stands for) makes that hard to do. 
But there is an easy way. My wine howto should work for Edgy. Link in my signature.

---

### Post by AVonGauss on 2006-11-07
> **RoyArne said:**
> I found that variable [in this thread]("http://www.ubuntuforums.org/showthread.php?t=286089") (third last post). I don't know what it does, I couldn't find it in the gcc documentation.


The CFLAGS variable on the configure command line just tells configure the default options to pass to the C compiler.  The "-fno-stack-protector" option is necessary to prevent Wine from seg faulting upon startup.

---

### Post by RoyArne on 2006-11-07
> **AVonGauss said:**
> The CFLAGS variable on the configure command line just tells configure the default options to pass to the C compiler.  The "-fno-stack-protector" option is necessary to prevent Wine from seg faulting upon startup.

True enough... See [GCC extension for protecting applications from stack-smashing attacks]("http://www.trl.ibm.com/projects/security/ssp/").

---

### Post by hvidgaard on 2006-11-07
Hmm... I cannot get wine the compile with OpenGL support, witch I need :(

I have followed this tutorial and get the following warning:

----------
...
config.status: executing include/wine commands

configure: WARNING: Wine will be build without OpenGL or Direct3D support
configure: WARNING: because something is wrong with the OpenGL setup:
configure: WARNING: No OpenGL library found on this system.

Configure finished.  Do 'make depend && make' to compile Wine.
----------

---

### Post by RoyArne on 2006-11-08
> **hvidgaard said:**
> I have followed this tutorial and get the following warning:

----------
...
config.status: executing include/wine commands

configure: WARNING: Wine will be build without OpenGL or Direct3D support
configure: WARNING: because something is wrong with the OpenGL setup:
configure: WARNING: No OpenGL library found on this system.

Configure finished.  Do 'make depend && make' to compile Wine.
----------

Sorry, my bad. I think libGL has been updated since I wrote the tutorial, and this broke the link to libGL.so.1.xxx. The following should fix this issue:

First remove the symbolic links you have created in /usr/lib32

```
sudo rm /usr/lib32/libX11.so /usr/lib32/libXext.so /usr/lib32/libfreetype.so  /usr/lib32/libz.so /usr/lib32/libGL.so /usr/lib32/libGLU.so /usr/lib32/libXrender.so
```

and then recreate them

```
sudo ln -s /usr/lib32/libX11.so.6 /usr/lib32/libX11.so
sudo ln -s /usr/lib32/libXext.so.6 /usr/lib32/libXext.so
sudo ln -s /usr/lib32/libfreetype.so.6 /usr/lib32/libfreetype.so
sudo ln -s /usr/lib32/libz.so.1 /usr/lib32/libz.so
sudo ln -s /usr/lib32/libGL.so.1 /usr/lib32/libGL.so
sudo ln -s /usr/lib32/libGLU.so.1 /usr/lib32/libGLU.so
sudo ln -s /usr/lib32/libXrender.so.1 /usr/lib32/libXrender.so
```

Please let me know if this does not solve your problem.

---

### Post by hvidgaard on 2006-11-08
Thanks a lot :D Now it at least ./configure without warnings (other than the missing libicu34-dev) :)

Compiling this very moment...

EDIT

Works like a charm :) the gf is now playing WoW, so now I don't have reboot the the pc into Windows when she wanna play. I'm happy, she's happy, win/win :P

---

### Post by napsilan on 2006-11-08
I'm getting the same error as xstaticglx

> 
../../tools/winegcc/winegcc -B../../tools/winebuild -shared ./gdi32.spec dispdib.spec.o gdi.exe.spec.o wing.spec.o bidi16.o dispdib.o env.o gdi16.o metafile16.o wing.o  bidi.o bitblt.o bitmap.o brush.o clipping.o dc.o dib.o driver.o enhmetafile.o enhmfdrv/bitblt.o enhmfdrv/dc.o enhmfdrv/graphics.o enhmfdrv/init.o enhmfdrv/mapping.o enhmfdrv/objects.o font.o freetype.o gdi_main.o gdiobj.o icm.o mapping.o metafile.o mfdrv/bitblt.o mfdrv/dc.o mfdrv/graphics.o mfdrv/init.o mfdrv/mapping.o mfdrv/objects.o mfdrv/text.o opengl.o painting.o palette.o path.o pen.o printdrv.o region.o     version.res   -o gdi32.dll.so  -ladvapi32 -lkernel32 -lntdll  /usr/lib/libsicuuc.a /usr/lib/libsicudata.a -lstdc++ -lgcc_s ../../libs/port/libwine_port.a  
ld: Relocatable linking with relocations from format elf64-x86-64 (/usr/lib/libsicuuc.a(ubidi.ao)) to format elf32-i386 (gdi32.Gea9aw.o) is not supported
winebuild: ld -m elf_i386 -r failed with status 256
winegcc: ../../tools/winebuild/winebuild failed.
make[2]: *** [gdi32.dll.so] Error 2
make[2]: Leaving directory `/home/napsilan/Tools/wine-0.9.24/wine-0.9.24/dlls/gdi32'
make[1]: *** [gdi32] Error 2
make[1]: Leaving directory `/home/napsilan/Tools/wine-0.9.24/wine-0.9.24/dlls'
make: *** [dlls] Error 2



Edgy 64 bit kde and gnome installed, using beryl aiglx, and most every library I could find mentioned in any thread on wine, although I do not have that specific one mentioned by the OP not to have.

---

### Post by RAOF on 2006-11-08
Why are you trying to compile wine?  Why not just install the binary i386 .deb packages avaliable from the wine site?

---

### Post by napsilan on 2006-11-08
> **RAOF said:**
> Why are you trying to compile wine?  Why not just install the binary i386 .deb packages avaliable from the wine site?

They do not have the wow patch applied, and (I think) don't have ALSA.  I do have a working deb that someone posted around here that fixes both of those problems.  

At this point it's more "because I can" and I'd like to see how to fix things like this in the future.

---

### Post by Kilz on 2006-11-09
> **napsilan said:**
> They do not have the wow patch applied, and (I think) don't have ALSA.  I do have a working deb that someone posted around here that fixes both of those problems.  

At this point it's more "because I can" and I'd like to see how to fix things like this in the future.

There is a i386 .deb with the wow patches already installed. Check out the wine link in my signature.

---

### Post by napsilan on 2006-11-09
Compiled regular old wine on Edgy AMD64, no ALSA or WoW yet.  Here is the .deb if anyone wants it.  Works on WC3:TFT so far. 

[https://netfiles.uiuc.edu/agoodri2/wine_0.9.24-1_amd64.deb](https://netfiles.uiuc.edu/agoodri2/wine_0.9.24-1_amd64.deb)

The problem was that libicu34 thing.  It's listed in apt as libicu-dev, rather than libicu34.

---

### Post by Brakbabord on 2006-11-09
I'm trying to compile wine on dapper 64 bits, using this howto. I just used "LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure" for the configure script.

EDIT: It works great, thanks a lot !

---

### Post by VirusSE on 2006-11-21
> make[2]: Betrete Verzeichnis '/home/virusse/wine/wine-0.9.25/dlls/gdi32'
../../tools/winegcc/winegcc -B../../tools/winebuild -shared ./gdi32.spec dispdib.spec.o gdi.exe.spec.o wing.spec.o bidi16.o dispdib.o env.o gdi16.o metafile16.o wing.o  bidi.o bitblt.o bitmap.o brush.o clipping.o dc.o dib.o driver.o enhmetafile.o enhmfdrv/bitblt.o enhmfdrv/dc.o enhmfdrv/graphics.o enhmfdrv/init.o enhmfdrv/mapping.o enhmfdrv/objects.o font.o freetype.o gdi_main.o gdiobj.o icm.o mapping.o metafile.o mfdrv/bitblt.o mfdrv/dc.o mfdrv/graphics.o mfdrv/init.o mfdrv/mapping.o mfdrv/objects.o mfdrv/text.o opengl.o painting.o palette.o path.o pen.o printdrv.o region.o     version.res   -o gdi32.dll.so  -ladvapi32 -lkernel32 -lntdll  /usr/lib/libsicuuc.a /usr/lib/libsicudata.a -lstdc++ -lgcc_s ../../libs/port/libwine_port.a  
ld: Relocatable linking with relocations from format elf64-x86-64 (/usr/lib/libsicuuc.a(ubidi.ao)) to format elf32-i386 (gdi32.4GW6wr.o) is not supported
winebuild: ld -m elf_i386 -r failed with status 256
winegcc: ../../tools/winebuild/winebuild failed.
make[2]: *** [gdi32.dll.so] Fehler 2
make[2]: Verlasse Verzeichnis '/home/virusse/wine/wine-0.9.25/dlls/gdi32'
make[1]: *** [gdi32] Fehler 2
make[1]: Verlasse Verzeichnis '/home/virusse/wine/wine-0.9.25/dlls'
make: *** [dlls] Fehler 2

I had the same problems too. My machine runs Edgy 6.10 AMD64 with only Gnome installed. I'll compile wine for myself, because i don't play WoW but Eve and there is no package available. :-(

---

### Post by scorpio810 on 2006-11-21
[http://www.ubuntuforums.org/showpost.php?p=1779667&postcount=25](http://www.ubuntuforums.org/showpost.php?p=1779667&postcount=25)
 install libicu34-dev for resolve problems with the make

---

### Post by omrsafetyo on 2007-04-10
VirusSE; napsilan; and xstaticxgpx - 
here is how I solved that particular problem:

Make sure you have the icu dev libraries installed:

[COLOR="Red"]sudo apt-get install libicu-dev[/COLOR]

next, run your configure as such:

[COLOR="Red"]LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" CC="gcc -m32" CXX="g++ -m32" ./configure[/COLOR]

edit the Makefile in  [COLOR="Blue"]wine-X.X.XX/dlls/gdi32/Makefile[/COLOR]  I used pico - you can use vi or text editor or whatever.

and modify the line with "EXTRALIBS" to read:

[COLOR="DarkRed"]EXTRALIBS = /usr/lib32/libsicuuc.a /usr/lib/libsicudata.a -lstdc++ -lgcc_s[/COLOR]

It may be blank to start, or the libsicuuc.a may be pointing to [COLOR="Blue"]/usr/lib[/COLOR]

compile:

[COLOR="Red"]make depend && make[/COLOR]

Make the install:

[COLOR="Red"]make install[/COLOR]

Done!

Edit:  My bad, didn't see how old that last post was.  Hope this helps someone though!

---

