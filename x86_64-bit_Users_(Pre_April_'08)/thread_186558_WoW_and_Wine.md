---
title: "WoW and Wine"
date: 2006-06-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by leris on 2006-06-02
Greetings,

I have one thing holding me back (like many) from making the COMPLETE change to a linux based system. This is stupid games (yes, I know.).

My drama - I play World of Warcraft and enjoy the game. I wish to solely use Ubuntu 6.04 as my OS of choice and would rather not have to keep switching back and forth between windows.

To my understandind, Wine does not compile on 64 bit systems because it was made for i386, so I found a work around on the forums and did so. (This didn't work properly however, as I didn't have ANY text).

Now in order to play, I have also read that you need to patch Wine's source code so it works correctly.  This is a MAJOR draw back.  I could get _some_ of the patch to work but came up with an error also discribed on that thread where LINE 4 from the second patch was not found.

Even when I compile it WITHOUT this other patch, I'm still at a loss because I then am unable to run/install wine. ](*,) 

Does anyone know of someone running WoW (and PhotoShop) on Ubuntu 64bit?  If so, can you please direct me to the appropriate place in order to get both the patches for wine set up AND wine running under 64bit.

Thanking you SO much in advance for taking the time.

Darren.

---

### Post by bmichel on 2006-06-02
Think about the free vmware player. You still need to install a windows guest OS inside but this is really a nice and reliable solution to run few mandatory Windows applications while keeping Linux as main OS.
I'm using vmware player since 3 months on my AMD64 3200+, 2GB memory with W2k as guest with 512MB. Everything works fine but for sure slower than native. If Wow needs DirectX you can experience some issue since it's a beta feature with vmware.

---

### Post by Kilz on 2006-06-02
WoW on vmware would be slow, I tried it once with Diablo 2 and it was like a snail. You can install Wine on a 64 bit Dapper without a chroot. [Here is a link to the howto.]("http://www.ubuntuforums.org/showthread.php?t=185557") . [Then go to This Page for the setup info]("http://appdb.winehq.org/appview.php?versionId=4031").

---

### Post by JoWilly on 2006-06-02
Yes guys.... just use the search function. All these 32/64 bit things very discussed many times but keep comming again.

Could someone make a sticky howto ?

---

### Post by miggl on 2006-06-02
[QUOTE=leris]
Does anyone know of someone running WoW (and PhotoShop) on Ubuntu 64bit?  If so, can you please direct me to the appropriate place in order to get both the patches for wine set up AND wine running under 64bit.
QUOTE]

Hi Leris!
I had WoW running without a hitch in Ubuntu back when I was playing it. Here;s the problem though: I had it running using Cedega, not Wine (Cedega is $5/month). Now, Cedega is compiled for 32-bit systems, but you can curcumvent that by doing:```
sudo dpkg -i --force-all [cedega-package].dpg
```
Cedega doesn't support the latest games all the time, they are usually a few months behind (they don't support Oblivion yet). But the games they do support are usually running very good.

Cedega is available at [http://www.transgamaing.com](http://www.transgamaing.com)

---

### Post by JoWilly on 2006-06-02
[QUOTE=leris]
Does anyone know of someone running WoW (and PhotoShop) on Ubuntu 64bit?  If so, can you please direct me to the appropriate place in order to get both the patches for wine set up AND wine running under 64bit.
[/QUOTE]

Regarding photoshop, version 7 works fine with crossover... also install with dpkg -i --force-architecture.

---

### Post by espike on 2006-06-29
[QUOTE=JoWilly]Yes guys.... just use the search function. All these 32/64 bit things very discussed many times but keep comming again.

Could someone make a sticky howto ?[/QUOTE]

I am working on this for a few days now, and i can answer your question a bit here: 
This keeps coming, cause there is no solution available.
All guides, and howtos are written for 32bit ubuntu, not 64bit. 
getting the cvs, and applying the patch isn't the real problem, ppl  should be able to get that, ok, u do get a warning regarding missing freetype, but as far as my googling tells me, that's not something you should really worry about.

What seems to be the problem, are the different locations for 32, and 64 bit libraries, i tried circumventing that by using ./configure --x-libraries=/usr/X11R6/lib
but it ends up giving  me " /usr/bin/ld: cannot find -lXext"  during make 
i did check btw, and even reinstalled xlibs-dev, but the same error keeps popping up.
Now i am far from an expert on anything, just been using linux for a week or so now, but u figure a lot out when u need/want it to be fixed.

```
make[2]: Entering directory `/home/sushi/wine-0.9.16/dlls/dciman32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/sushi/wine-0.9.16/dlls/dciman32'
make[2]: Entering directory `/home/sushi/wine-0.9.16/dlls/ddraw'
../../tools/winegcc/winegcc -B../../tools/winebuild -shared ./ddraw.spec    clipper.o ddraw.o ddraw_thunks.o device.o direct3d.o executebuffer.o gamma.o light.o main.o material.o palette.o parent.o regsvr.o surface.o surface_thunks.o texture.o utils.o vertexbuffer.o viewport.o  version.res   -Wl,--rpath,\$ORIGIN/`../../tools/relpath /usr/local/lib/wine /usr/local/lib` -o ddraw.dll.so -L../../dlls -lwined3d -lole32 -luser32 -lgdi32 -ladvapi32 -lkernel32 -lntdll  -L../../libs -lwine -ldxguid -luuid  -L/usr/X11R6/lib  -lXext -lX11   -L../../libs/port -lwine_port
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed.
make[2]: *** [ddraw.dll.so] Error 2
make[2]: Leaving directory `/home/sushi/wine-0.9.16/dlls/ddraw'
make[1]: *** [ddraw] Error 2
make[1]: Leaving directory `/home/sushi/wine-0.9.16/dlls'
make: *** [dlls] Error 2

```

i've put up only the part i hope is relevant, the lines before this just stated leaving, nothing to do etc.
If someone has a suggestion on how to fix this, i got my dualboot windows system working fine for everything else, and to those that got stuck before this somewhere, i used the files and everything from [http://appdb.winehq.org/appview.php?versionId=5109](http://appdb.winehq.org/appview.php?versionId=5109)
if i do get this working asomehow, i will post the rest here as well

---

### Post by Kilz on 2006-06-29
[QUOTE=espike]I am working on this for a few days now, and i can answer your question a bit here: 
This keeps coming, cause there is no solution available.
All guides, and howtos are written for 32bit ubuntu, not 64bit. 
getting the cvs, and applying the patch isn't the real problem, ppl  should be able to get that, ok, u do get a warning regarding missing freetype, but as far as my googling tells me, that's not something you should really worry about.

What seems to be the problem, are the different locations for 32, and 64 bit libraries, i tried circumventing that by using ./configure --x-libraries=/usr/X11R6/lib
but it ends up giving  me " /usr/bin/ld: cannot find -lXext"  during make 
i did check btw, and even reinstalled xlibs-dev, but the same error keeps popping up.
Now i am far from an expert on anything, just been using linux for a week or so now, but u figure a lot out when u need/want it to be fixed.

```
make[2]: Entering directory `/home/sushi/wine-0.9.16/dlls/dciman32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/sushi/wine-0.9.16/dlls/dciman32'
make[2]: Entering directory `/home/sushi/wine-0.9.16/dlls/ddraw'
../../tools/winegcc/winegcc -B../../tools/winebuild -shared ./ddraw.spec    clipper.o ddraw.o ddraw_thunks.o device.o direct3d.o executebuffer.o gamma.o light.o main.o material.o palette.o parent.o regsvr.o surface.o surface_thunks.o texture.o utils.o vertexbuffer.o viewport.o  version.res   -Wl,--rpath,\$ORIGIN/`../../tools/relpath /usr/local/lib/wine /usr/local/lib` -o ddraw.dll.so -L../../dlls -lwined3d -lole32 -luser32 -lgdi32 -ladvapi32 -lkernel32 -lntdll  -L../../libs -lwine -ldxguid -luuid  -L/usr/X11R6/lib  -lXext -lX11   -L../../libs/port -lwine_port
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed.
make[2]: *** [ddraw.dll.so] Error 2
make[2]: Leaving directory `/home/sushi/wine-0.9.16/dlls/ddraw'
make[1]: *** [ddraw] Error 2
make[1]: Leaving directory `/home/sushi/wine-0.9.16/dlls'
make: *** [dlls] Error 2

```

i've put up only the part i hope is relevant, the lines before this just stated leaving, nothing to do etc.
If someone has a suggestion on how to fix this, i got my dualboot windows system working fine for everything else, and to those that got stuck before this somewhere, i used the files and everything from [http://appdb.winehq.org/appview.php?versionId=5109](http://appdb.winehq.org/appview.php?versionId=5109)
if i do get this working asomehow, i will post the rest here as well[/QUOTE]

I looked at that page, and it looks like there was a patch released on June 27th. [There is a hidden post that mentions it.]("http://appdb.winehq.org/commentview.php?appId=1922&versionId=5109&threadId=13109")
I wish you luck. I gave up on wine after battling it on a few games and just paid the $15 bucks for Cedega. Wow took all of 15 minutes to install and start to play.

---

### Post by espike on 2006-06-30
found a so called solution for installing wine on 64bit dapper, however, somehow it just ain't working, it keeps giving me the message as stated above 
What is worse, is that someone closely related to ubuntu claims he got it working with a few symlinks, which, basically stopped ppl from trying it seems.
Other sites like wiki's quickly copy the solution without verifying.
The other option ofcourse would be, that i get in to trouble cause i use an upgraded ubuntu 5, instead of a clean installed 6 
I'm going to try making a fresh install dapper, and see if that works.
for those wondering which solution: 
>  Building Wine on Ubuntu / Kubuntu 6.06 (Dapper Drake)

First one must install the necessary libraries: Finding the correct set may take a few minutes and several tries.

configure will find several omissions, but a few will only be noticed by the 'make' steps.

The following add links, that the library install does not make:

# Do this as *root* by hand, it won't work as a script as written.
cd /usr/lib32
ln -s libX11.so.6 libX11.so
ln -s libXext.so.6 libXext.so
ln -s libfreetype.so.6 libfreetype.so

Run configure, build and install with:

LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32"  ./configure
make depend
make all
sudo make install

If all needed libraries are present there will be no missing-library warnings or errors anywhere.

wine seems to work (installed in /usr/local)  
source:  [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

just noticed that i now eneded up at a different error then posted above.
```
 ld: Relocatable linking with relocations from format elf64-x86-64 (/usr/lib/libsicuuc.a(ubidi.ao)) to format elf32-i386 (gdi32.I7jKw1.o) is not supported
winebuild: ld -m elf_i386 -r failed with status 256
winegcc: ../../tools/winebuild/winebuild failed.

```

been seeing this one for a day now, everything goes right, i get passed configure, make depend, and at make, or make all, it stops everytime with this one, which imo could have to do with 64 bit compiler vs 32bit code. 
ah well, will look in to this

btw tnx killz, for the link, however, atm it's not to relevant, cause i still need to get wine installed first, functional will be part 2 however.

---

### Post by Kilz on 2006-06-30
[QUOTE=espike]found a so called solution for installing wine on 64bit dapper, however, somehow it just ain't working, it keeps giving me the message as stated above 
What is worse, is that someone closely related to ubuntu claims he got it working with a few symlinks, which, basically stopped ppl from trying it seems.
Other sites like wiki's quickly copy the solution without verifying.
The other option ofcourse would be, that i get in to trouble cause i use an upgraded ubuntu 5, instead of a clean installed 6 
I'm going to try making a fresh install dapper, and see if that works.
for those wondering which solution: 

source:  [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

just noticed that i now eneded up at a different error then posted above.
```
 ld: Relocatable linking with relocations from format elf64-x86-64 (/usr/lib/libsicuuc.a(ubidi.ao)) to format elf32-i386 (gdi32.I7jKw1.o) is not supported
winebuild: ld -m elf_i386 -r failed with status 256
winegcc: ../../tools/winebuild/winebuild failed.

```

been seeing this one for a day now, everything goes right, i get passed configure, make depend, and at make, or make all, it stops everytime with this one, which imo could have to do with 64 bit compiler vs 32bit code. 
ah well, will look in to this

btw tnx killz, for the link, however, atm it's not to relevant, cause i still need to get wine installed first, functional will be part 2 however.[/QUOTE]

Sorry I thought you had wine installed, otherwise I would have told you to go to my howto.  [But here it is  :grin:]("http://www.ubuntuforums.org/showthread.php?t=185557") It will allow you to install 32bit wine. Don't try and compile wine for 64bit. Its near impossible, i couldn't do it. I think because you are trying to compile a 64bit version of a 32bit emulator.

---

### Post by espike on 2006-07-01
Saw your howto, looks rather solid, however, i need to patch wine for usage with world of warcraft (call it an addiction, i know, ) for which i need the cvs i think. 
am gonna try a few things though. 
Still consider it quite odd that wine doesn't give any real support to amd64, or to be more exact, that this just ain't doable using ubuntu, cause ppl using gentoo seem to have far less trouble with this.
frustrating

---

### Post by Kilz on 2006-07-01
[QUOTE=espike]Saw your howto, looks rather solid, however, i need to patch wine for usage with world of warcraft (call it an addiction, i know, ) for which i need the cvs i think. 
am gonna try a few things though. 
Still consider it quite odd that wine doesn't give any real support to amd64, or to be more exact, that this just ain't doable using ubuntu, cause ppl using gentoo seem to have far less trouble with this.
frustrating[/QUOTE]
Wine is still working on getting wine to do everything, I'm sure a 64 bit version will come later. But 32bit wine should work. The reason it doesn't on Ubuntu has to do with Ubuntu being derived from Debian. While the developers get a lot of good stable code from Debian there are also drawbacks. One of them is that Debian is one of the distro's that isn't even slightly multiarch. That we can run some 32 bit applications by forcing them in is the work of the Ubuntu developers. From what I understand Debian is just now talking about multiarch so they can write up a spec. That means it will not be until after edgy before Ubuntu is multi arch, because Ubuntu doesn't want to duplicate efforts.
I also understand the addiction, Blizzard makes addicting games. I gave up on wine, Cedega is worth the $15 bucks I spent to make it all click and install. After 5 hours of trying to make it work my time is worth $3 an hour, that isnt even minimum wage. I value my free/playing time a lot more than that.

---

