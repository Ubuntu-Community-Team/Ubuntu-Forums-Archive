---
title: "Perfect World International working"
date: 2011-08-31
forum: Wine
---

### Post by vanquishedangel on 2011-08-31
Hi, this is a great game with very stunning graphics and is great to play if you like mmo's.  This game also is wonderful at story line as far as I have played it for a few months now. It can be very difficult to get this game running in wine or playonlinux, not mention it has problems in windows as well according to many threads on their forums.

First off I use playonlinux just for ease and the one off their website, not the one in the repo's. The new one I like better for many reasons. Download from torrent ([http://thepiratebay.org/torrent/4969523/perfect_world](http://thepiratebay.org/torrent/4969523/perfect_world)) because I have never gotten the new client to work off the website, it stops at PMB.exe same as the playonlinux install script. Also the language packs ([http://www.microsoft.com/download/en/details.aspx?id=4194](http://www.microsoft.com/download/en/details.aspx?id=4194)) help according to may forums.

Step1. Download and install playonlinux

Step2. Playonlinux has a Perfect World International installer that doesn't work but it will help so open playonlinux, click install,click testing in the left pane, highlight perfect world international and click install. This will start the script that will install vcrun6 and wine 1.2.2. when it asks for the perfect world client find the one you downloaded in your download folder usually and select that. and wait for it to finish installing.

step3. you may need many of these files for many reasons, this game can be very graphics demanding, but you may not need all of them. I have installed:

vcrun2005
vcrun2008
vcrun2010
vcrun6(installed by script)
d3dx9
d3dx10(if graphics card supports)
d3dx11(if graphics card supports)
dinput
dinput8
directmusic
directplay
directx9
dxfullsetup
fakeie6( may not be needed)
ie6
msxml3
msxml4
msxml6
wininet

this can easily be done by opening playonlinux, highlighting perfect world international and selecting configure, select the install packages tab, and selecting each one from the list and clicking install. Also under the general tab make sure that the wine version is 1.2.2. Also some of these may need to be re-installed after game is setup, not sure why

Step4 installing the language pack, open playonlinux click install, click install non-listed program (looks like a link in bottom left corner), click next, highlight "edit or update and existing application", select perfect world and click next, next again, browse to the chinese lang pack you downloaded (download folder) and click next, finish the install.

step5 configure wine, with playonlinux open, right click perfect world and select configure wine. Windows version should be windows xp under applications tab, under audio tab select alsa and oss, under graphics tab set vertex shader to hardware and check allow pixel shader also check emulate virtual desktop and set to 1024x768 or 1280x1024 depending, mine is 1024x768

step6 More configurations. with playonlinux open highlight perfect world and select configure (gear shape icon)and select the display tab, follow these settings

GLSL                        disabled
Direct Draw Renderer        opengl
Video Memory Size           "you video card memory here"
Off Screen Rendering Mode   fbo
Render Target Lock Mode     default
Multisampling               Diasabled
Strict draw Ordering        default

Step7 update the game, if all went well the game should update fine if you select run from playonlinux, there may be some settings it asks for.

Stpe8  while it is updating you may set the graphics, mine are set to all boxes checked except v-sync and soften, and all sliders maxed out except sample at lowest possible. resolution set to 1024x768(if put 1280x1024 in wine) or 800x600 (if put 1024x768 in wine) mine is 800x600. the game crashes if not run in windowed mode on the game

my specs are hp dc7100 sff, 3.8 ghz ht, sapphire radeon hd 6450 1 gig overclocked to gpu 550mhz, memory 700mhz,  ram 4 gig 64 bit lubuntu. I use proprietary drivers from jockey. also the flick/tearing stopped when I set the refresh rate to 60mhz


My friends comp also runs this game he has a hp dc7100 3.0ghz ht, asus radeon hd 4350 512 mb vram, 1.5 gigs ram, Lubuntu 11.04 natty 32bit, and he run this at 1268x1024 resolution set up the same way as mine just different resolution. however he still has tearing/flickering load screens at 60mhz. Also he doesn't have d3dx11 because the 4350 doesn't support it.

As for setting the ATI catalyst settings pretty much everything is set to application decide except anisotropic filtering set to 2x and antiailiasing set to 2x as well with the boxes for overide application settings checked for those two. A.I is off, vertical refresh is off and so is tear free off.

---

### Post by kazuya on 2011-09-02
You totally rock man. I run archbang (easier implementation of archlinux), and although I have successfully installed the game, it actually launches, but would not connect to game server.
 
I tried the patch1 and patch 2 options, but wine complains about deficiency.
I shall follow your instructions closely again.
 
What version of playonlinux did you use?
I shall experiment again to try get this game to launch on my laptop. Thanks for very detailed guide.

---

### Post by vanquishedangel on 2011-09-03
Hi, I got that error about deficiency in wine a few times, try different settings, also if you are using a 64 bit os then you need 32bit libs installed, ia32 has some 32bit libs, the winehq says the the vertex shader doesn't work, although it works on mine and my friends systems.

I dont know about archbang at all but in ubuntu some say this command helps "sudo apt-get build-dep wine" and on my system it installs these packages:


bison comerr-dev diffstat docbook docbook-dsssl docbook-to-man
  docbook-utils docbook-xsl esound-common flex fontforge jadetex
  krb5-multidev lacheck latex-beamer latex-xcolor lib32asound2-dev
  lib32ncurses5-dev lib32v4l-dev libasound2-dev libaudio-dev libaudiofile-dev
  libaudiofile0 libavahi-client-dev libavahi-common-dev libcapi20-3
  libcapi20-dev libconfig++8 libcups2-dev libdbus-1-dev libesd0 libesd0-dev
  libexif-dev libffado-dev libffado2 libfontconfig1-dev libfontforge1
  libfreetype6-dev libgdraw4 libgif-dev libgl1-mesa-dev libglibmm-2.4-1c2a
  libglu1-mesa-dev libgphoto2-2-dev libgsm1-dev libgssrpc4 libhal-dev
  libhal-storage-dev libhal-storage1 libhal1 libice-dev libieee1284-3-dev
  libjack-dev libjack0 libjpeg62-dev libkadm5clnt-mit7 libkadm5srv-mit7
  libkdb5-4 libkrb5-dev liblcms1-dev libldap2-dev libltdl-dev libmpg123-0
  libmpg123-dev libncurses5-dev libodbcinstq1c2 libosp5 libostyle1c2
  libpng12-dev libqt3-mt libsamplerate0-dev libsane-dev libsgmls-perl
  libsm-dev libsp1c2 libspiro0 libssl-dev libtiff4-dev libtiffxx0c2 libtool
  libuninameslist0 libv4l-dev libxcomposite-dev libxcursor-dev libxi-dev
  libxinerama-dev libxml++2.6-2 libxml2-dev libxrandr-dev libxrender-dev
  libxslt1-dev libxt-dev lmodern luatex lynx lynx-cur mesa-common-devodbcinst odbcinst1debian2 openjade pgf prelink prosper ps2eps quilt sgmlspl
  sharutils sp tex-common texlive-base texlive-binaries texlive-common
  texlive-doc-base texlive-extra-utils texlive-font-utils
  texlive-fonts-recommended texlive-fonts-recommended-doc
  texlive-generic-recommended texlive-latex-base texlive-latex-base-doc
  texlive-latex-recommended texlive-latex-recommended-doc texlive-luatex
  texlive-pstricks texlive-pstricks-doc tipa unixodbc unixodbc-dev
  x11proto-composite-dev xorg-sgml-doctools

and their dependancies, I am trying this now because even tho the game is very playable on my system, it works better on my friends 32 bit system.

I will post if they help me or not, my connection is very slow so it may take some time.


Update: having these installed does help with a few things in game but didn't fix the few issues still there (32bit libs). some pictures are clearer and less artifacts, slightly better fps (very slight)

---

### Post by vanquishedangel on 2011-09-05
as I work out issues I post them here

As for ati cards in amdcccle under 3d - antiailiasing click over ride application settings and set to whatever possible change filter to whatever, it seems the screen tearing is cause by the apllication decide setting. I can set mine to the highest settings and no tearing but if I check that box then there is tearing. also sampling is working as well this way, I also installed wmp9 and the codecs to. AmdOverdrivectrl is the overclocking program i am using. I have my sapphire radeon hd 6450 set at gpu 725 mhz, and memory at 800 mhz, and volts at 1

---

### Post by vanquishedangel on 2011-09-07
I have also installed a few native windows dll files into system 32 folder in playonlinux (version 4.0.11) the native files I downloaded from here:
[http://www.dll-files.com/](http://www.dll-files.com/)

and these are them so far:
IMM32.dll
shdocvw.dll
dinput.dll
crypt32.dll
msoss.dll
cygpixbufloader-ras.dll
dimm.dll
winsock.dll
d3d8.dll

and this is the list so far, DO NOT INALL wininet.dll FROM HERE!!! use the one in playonlinux, it wont work from another place. it will cause a error about a deficiency in wine. I also have a windows disk but I dont have it installed on any drive atm.

If you are using the open source drivers for graphics they work but not as well. vertex shader needs to be disabled and sampling as well the drivers from xorg never worked for this game for me. x-swat worked however.

---

### Post by _d_ on 2011-09-07
What kinds of FPS were you getting on PWI through Wine? I'm curious as I want to try out PW again and will most likely be following this guide (only without using POL though).

---

### Post by vanquishedangel on 2011-09-08
> **_d_ said:**
> What kinds of FPS were you getting on PWI through Wine? I'm curious as I want to try out PW again and will most likely be following this guide (only without using POL though).

I am getting only 4-8 fps in busy areas about 15 normally and 30 in light areas, it is very playable for me tho it seems like it wouldn't be.  I also have most graphics maxed out and the sapphire radeon hd 6450 is very poor performance wise but it does what i need, it is a HTPC card not for gaming.

I am not sure this will work for all versions of wine but i dont see why it wouldnt, I had it working in wine 1.3 from the repos but wine 1.2.2 seemed to work best.

---

### Post by _d_ on 2011-09-08
> **vanquishedangel said:**
> I am getting only 4-8 fps in busy areas about 15 normally and 30 in light areas, it is very playable for me tho it seems like it wouldn't be.  I also have most graphics maxed out and the sapphire radeon hd 6450 is very poor performance wise but it does what i need, it is a HTPC card not for gaming.

I am not sure this will work for all versions of wine but i dont see why it wouldnt, I had it working in wine 1.3 from the repos but wine 1.2.2 seemed to work best.


Hmm, ok thanks. Will have to test it all out with 1.3 and 1.2 and see which is better.

---

### Post by vanquishedangel on 2011-09-16
Here is a link to my youtube video of it

[http://www.youtube.com/watch?v=hX8LBpkcI04](http://www.youtube.com/watch?v=hX8LBpkcI04)

---

### Post by _d_ on 2011-09-16
> **vanquishedangel said:**
> Here is a link to my youtube video of it

[http://www.youtube.com/watch?v=hX8LBpkcI04](http://www.youtube.com/watch?v=hX8LBpkcI04)

Looks pretty good. What kind of system specs are you on?

---

### Post by vanquishedangel on 2011-09-16
> **_d_ said:**
> Looks pretty good. What kind of system specs are you on?

I have an hp dc7100 3.8 ghz ht intel processor (670, single core), 4 gig high density ram, sapphire radeon hd 6450 (ati overclocked to 725 mhz GPU, 800mhz memory, 1 volt), Lubuntu 64 bit OS. BTW i use a mobile broadband connection anywhere from 270 bytes- 40 kps.

My friends comp is an hp dc7100 3.0 ghz ht intel (single core), 1.5 gig low density ram, asus radeon hd 4350 (ati over clocked to 800mhz GPU, 500mhz memory, 1.1 volts), Lubuntu 32bit OS. uses mobile broad band as well.

---

### Post by _d_ on 2011-09-16
> **vanquishedangel said:**
> I have an hp dc7100 3.8 ghz ht intel processor (670, single core), 4 gig high density ram, sapphire radeon hd 6450 (ati overclocked to 725 mhz GPU, 800mhz memory, 1 volt), Lubuntu 64 bit OS. BTW i use a mobile broadband connection anywhere from 270 bytes- 40 kps.

My friends comp is an hp dc7100 3.0 ghz ht intel (single core), 1.5 gig low density ram, asus radeon hd 4350 (ati over clocked to 800mhz GPU, 500mhz memory, 1.1 volts), Lubuntu 32bit OS. uses mobile broad band as well.

Heh.

I'm just now wondering how well this is going to work out for me in the end. xD

AMD Athlon II X4 635 2.9GHz
4GB DDR3 RAM
ATI Radeon HD4200
Ubuntu 11.04 x86_64 (Ubuntu Classic no effects)

:S

---

### Post by vanquishedangel on 2011-09-17
> **_d_ said:**
> Heh.

I'm just now wondering how well this is going to work out for me in the end. xD

AMD Athlon II X4 635 2.9GHz
4GB DDR3 RAM
ATI Radeon HD4200
Ubuntu 11.04 x86_64 (Ubuntu Classic no effects)

:S

Well the processor and ram should be fine lol, Though perfect world isn't multi threaded yet as far as I know. I do know that using Lubuntu leaves more system resources for applications to use. Also if you can overclock your card I found that some go to 600mhz GPU and 533mhz memory, I would use the program mentioned earlier in this thread and set core clock to max and memory to like 500mhz or 533mhz and voltage to max for the high load. And the opensouce drivers work but on low settings only, and they will be slower.

---

### Post by _d_ on 2011-09-17
> **vanquishedangel said:**
> Well the processor and ram should be fine lol, Though perfect world isn't multi threaded yet as far as I know. I do know that using Lubuntu leaves more system resources for applications to use. Also if you can overclock your card I found that some go to 600mhz GPU and 533mhz memory, I would use the program mentioned earlier in this thread and set core clock to max and memory to like 500mhz or 533mhz and voltage to max for the high load.

Well, I guess I'll have to find out.

Just finished installing in Wine...brb.

---

### Post by vanquishedangel on 2011-09-17
I also made a registry key:

Nonpower2Mode repack

Almost forgot about that lol. I enabled debug mode in pol and all of the things that I installed got rid of errors though the game worked and they made play better. I am still searching for a few errors yet like there is a ras error and when I look it up online it has to with libgnutls, I have it installed both 32 bit and 64 bit, but the error is still there. This error isn't present on my friends system.

---

### Post by _d_ on 2011-09-17
Bleh, I just gave up on PWI.

Tried POL Wine 1.2.2, either resulted in immediate crash or fatal error.

Tried wine solo 1.3.28, same thing.

Tried wine solo 1.2.3, same thing.

Compiled wine 1.2.2 solo, same thing.

:(

---

### Post by vanquishedangel on 2011-09-18
> **_d_ said:**
> Bleh, I just gave up on PWI.

Tried POL Wine 1.2.2, either resulted in immediate crash or fatal error.

Tried wine solo 1.3.28, same thing.

Tried wine solo 1.2.3, same thing.

Compiled wine 1.2.2 solo, same thing.

:(

I hope you don't give up, there might be something i missed because it took me awhile to get it it working so I may have missed something, try different wine settings. Playonlinux has a debugger that may reveal what the issue is as well.

---

### Post by Talieson on 2011-09-29
Hi i just wanted to post my success in intalling PWI on my bohdilinux sytem.  i did have a one setback which was a faulty shlwapi.dll file.  the game crashed while it was installed however after removing it (error found through POL debugger) the game worked fine :) seems it wasn't needed.  thank you for you help and your time.

---

