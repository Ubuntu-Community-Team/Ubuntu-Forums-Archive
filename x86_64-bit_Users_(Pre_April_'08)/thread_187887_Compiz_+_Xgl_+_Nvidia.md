---
title: "Compiz + Xgl + Nvidia"
date: 2006-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by IbeeX on 2006-06-03
Hi

did anybody manage to istall this on Latest dapper,
first I couldn't install nvidia binary package then I managed to get laest nvidia driver via script "envy_8762_64"
and then i tried using this gude
[http://www.ubuntuforums.org/showthread.php?t=148860&highlight=compiz.real%3A+composite+extension](http://www.ubuntuforums.org/showthread.php?t=148860&highlight=compiz.real%3A+composite+extension)

but nothing compiz fails to start.

If anybody made it can he describe hov he did it ?

Thx

---

### Post by JoWilly on 2006-06-03
[QUOTE=IbeeX]Hi

did anybody manage to istall this on Latest dapper,
first I couldn't install nvidia binary package then I managed to get laest nvidia driver via script "envy_8762_64"
and then i tried using this gude
[http://www.ubuntuforums.org/showthread.php?t=148860&highlight=compiz.real%3A+composite+extension](http://www.ubuntuforums.org/showthread.php?t=148860&highlight=compiz.real%3A+composite+extension)

but nothing compiz fails to start.

If anybody made it can he describe hov he did it ?

Thx[/QUOTE]


Yes it works fine on dapper.

Well... its always the same stories... there are dozens of threads about this.

Make sure that :

1. 3D works before trying to install xgl/compiz -> setup nvidia/ati drivers first and test them.
2. follow the howto -> if you FOLLOW the howtos properly it WORKS.

Good luck.

PS: nvidia drivers in the repo work, you have nothing to install (just replace nv with nvidia in xorg.conf). If you could not install the deb you have a problem right here.

---

### Post by IbeeX on 2006-06-03
I have 3D drivers and they are working,

but I cant get compiz working and I was following sinstructions.

do you have dapper x64 with Nvidia? And what were you doing to get it working?

---

### Post by FluffyElmo on 2006-06-03
I got this working following the How-To, but now that I've done a full reboot it doesn't work anymore. No obvious errors in the logs...strange.

---

### Post by JoWilly on 2006-06-03
Yep, amd64 + nvidia.

1. get 3d working and test it.
2. install xgl,compiz,mesa,...
3. edit /etc/gdm/gdm.conf-custom to add xgl
4. add "gnome-window-decorator" & "compiz --replace gconf" to the gnome startup sessions (menu/system/prefs/sessions/startup)

Easy...

EDIT: to get the latest version of xgl/compiz add raof's wonderfull repo to your /etc/apt/sources.list:

"deb [http://raof.dyndns.org/falcon/](http://raof.dyndns.org/falcon/) dapper eyecandy flash multimedia mythtv all"

---

### Post by IbeeX on 2006-06-04
[QUOTE=JoWilly]Yep, amd64 + nvidia.

1. get 3d working and test it.
2. install xgl,compiz,mesa,...
3. edit /etc/gdm/gdm.conf-custom to add xgl
4. add "gnome-window-decorator" & "compiz --replace gconf" to the gnome startup sessions (menu/system/prefs/sessions/startup)

Easy...

EDIT: to get the latest version of xgl/compiz add raof's wonderfull repo to your /etc/apt/sources.list:

"deb [http://raof.dyndns.org/falcon/](http://raof.dyndns.org/falcon/) dapper eyecandy flash multimedia mythtv all"[/QUOTE]

I did the same but no luck :(
I am certain tht it has to do with librarys I actualy managet to get it working by manualy changing libs 
this are my libs
```

ibrkanac@ibrkanac-desktop:~$ ls -al /usr/lib/libGL*
lrwxrwxrwx 1 root root      21 2006-06-04 19:30 /usr/lib/libGLcore.so.1 -> libGLcore.so.1.0.8762
-rw-r--r-- 1 root root 7835344 2006-05-29 14:54 /usr/lib/libGLcore.so.1.0.8762
lrwxrwxrwx 1 root root      12 2006-06-04 20:02 /usr/lib/libGL.so.1 -> libGL.so.1.2
-rw-r--r-- 1 root root  734512 2006-05-29 14:54 /usr/lib/libGL.so.1.0.8762
-rw-r--r-- 1 root root  604792 2006-06-04 19:36 /usr/lib/libGL.so.1.2
lrwxrwxrwx 1 root root      20 2006-06-04 19:35 /usr/lib/libGLU.so.1 -> libGLU.so.1.3.060500
-rw-r--r-- 1 root root  517168 2006-06-01 11:03 /usr/lib/libGLU.so.1.3.060500


ls -al /usr/lib/nvidia/
total 648
drwxr-xr-x   2 root root   4096 2006-06-04 20:02 .
drwxr-xr-x 137 root root  32768 2006-06-04 20:02 ..
-rw-r--r--   1 root root 604792 2006-06-01 11:03 libGL.so.1.2.xlibmesa
lrwxrwxrwx   1 root root     12 2006-06-04 20:02 libGL.so.1.xlibmesa -> libGL.so.1.2
-rwxr-xr-x   1 root root   4680 2006-05-29 14:54 tls_test
-rw-r--r--   1 root root   4584 2006-05-29 14:54 tls_test_dso.so


```
when I manualz extracted libGL.so.1.2 It started to work but it crashes after some time :(

---

### Post by RAOF on 2006-06-05
[QUOTE=JoWilly]...

EDIT: to get the latest version of xgl/compiz add raof's wonderfull repo to your /etc/apt/sources.list:

"deb [http://raof.dyndns.org/falcon/](http://raof.dyndns.org/falcon/) dapper eyecandy flash multimedia mythtv all"[/QUOTE]
Or even better, the mirror, kindly provided by Doc.Horn, which is more frequently up & has a better than 256K uplink :)
```
deb http://ubuntu.moshen.de/ dapper all
```
You might want to replace "all" with "eyecandy" to get only the XGL/compiz stuff.  The other sections of the repository contain other things (Mythtv 0.19.1, a newer Rhythmbox, newer (& more codecs) ffmpeg, etc).

---

### Post by bluevoodoo1 on 2006-06-06
[QUOTE=RAOF]
```
deb http://ubuntu.moshen.de/ dapper all
```[/QUOTE]

Does that have xgl/compiz packages newer than...

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

?

---

### Post by spork27 on 2006-06-06
Took a while to figure this out.  When using the driver instal script from nvidia.com, specify the module path as follows:
```
sudo sh NVIDIA-Linux-x86_64-1.0-8762-pkg2.run --x-module-path=/usr/lib/xorg/modules
```

---

### Post by RAOF on 2006-06-06
[QUOTE=bluevoodoo1]Does that have xgl/compiz packages newer than...

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

?[/QUOTE]
I'm actually building the AMD64 packages for those repos, so it has versions at least as new as there ;).  And there's less delay between me building the package and it showing up in the ubuntu.moshen.de repo than the main compiz repos.

---

### Post by funkenstein on 2006-06-06
@RAOF

Thanks for the repo, along with the HowTo at the begining of this thread I finally got everything running smoothly in 64bit flavour (32bit has never been a hassle, but 64 bit....  ](*,) sheesh!)

Questions though:
1. do you think you might be able to provide us with up to date gset-compiz?

2. I have <Super_L> and _R, but no <Super> key.... ??? strange... On the same note, I can't find the xmodmap that works with my laptop keyboard - the uk and uk_x86 are both wrong. Strange thing is, without xmodmap at all, everything is fine... :confused: my keyb prefs through system>prefs>keyb>layouts say generic 101pc with the US layout, but none of the US xmodmaps work either.... and the 3 key has a £ above it, so it *is* seen as british.... but hey ho, don't fix it if it ain't broke...

3. is the dock plugin b0rkt? it certainly seems so from here...

and finally,
4. can you please sign your repo/provide us with the key? 

ta very muchly again from sunny ediburgh (scotland, not austraila... :p)

---

### Post by RAOF on 2006-06-06
The repo is signed - as it says on the webpage,
```

gpg --keyserver subkeys.pgp.net --recv-keys 2F306651
gpg --export --armor 2F306651 | sudo apt-key add -

```
will add my key to your apt keychain.

The latest (packaged) gset-compiz is in my repo.  If it's in beerorkid or xgl.compiz.info, it (should) be in my repo.  If there's a newer one, I might look at packaging it myself.

For the rest of the questions: [The Compiz/XGL forums](compiz.net).  In short - I don't know about the keymap, and dock is pretty borked, yes.

---

### Post by funkenstein on 2006-06-06
[quote=RAOF]The repo is signed - as it says on the webpage,[/quote] LOL, I didn't even look at the website.... sorry, I'm up all night tonight (it's 4.30 now) as my thesis is due in 7.30 hours.... (so wtf am i doing on the ubuntu forums playing with compiz???)
[quote=RAOF]
The latest (packaged) gset-compiz is in my repo.  If it's in beerorkid or xgl.compiz.info, it (should) be in my repo.  If there's a newer one, I might look at packaging it myself.[/quote] again, fool that I am for not trying. It's the sleeplessness, I tells ya! also, the beerorkid repos didn't have gset for 64bit last time I checked.... again, I may well be wrong.

[quote=RAOF]For the rest of the questions[/quote]thanks for your help, I'll check it out tomorrow re: the keyboard etc...

---

### Post by gaatmx on 2006-06-08
:confused: I finally make this work!:D 
Well almost..... the super-key (windows) does not woprk at all, so I am missing the zoom effect among other goodies:confused: 
Anyone knows if there is a way to make it work???
G.

---

### Post by spyke01 on 2006-06-08
ok guys few questions, when reading through the pages of the how to(no i did not read all 157 pages only about 10), i found that the card i use(geforce 4 mx 440 agp 8x) has  aklot of problems with compiz. Heres my questions though:

1. If i install XGL and use it instead of X, then am i going to experience the huge bugs that compiz gives?

2. I have seen people saying that XGL is faster than X is this true?

3. Do i still need to do [this](http://www.ubuntuforums.org/showthread.php?t=180647&highlight=xgl) after i install XGL?

4. Does anyone know if the huge bus people were expiriencing mwith my card were ever fixed? The discussion kinda flipped flopped back and forth on this one at the begining, works, doesnt, works with this patch, doesnt, and so on.

5. Will programs that are dependant upon the gtk+-2.0 packages be affected by this?

6. I saw that someone was saying that compiz is running as a full screen app ontop of XGL and that is why you are able to run kill compiz.real to get back to XGL, any thoughts on this?

---

### Post by RAOF on 2006-06-09
[QUOTE=spyke01]...
1. If i install XGL and use it instead of X, then am i going to experience the huge bugs that compiz gives?

2. I have seen people saying that XGL is faster than X is this true?

3. Do i still need to do [this](http://www.ubuntuforums.org/showthread.php?t=180647&highlight=xgl) after i install XGL?

4. Does anyone know if the huge bus people were expiriencing mwith my card were ever fixed? The discussion kinda flipped flopped back and forth on this one at the begining, works, doesnt, works with this patch, doesnt, and so on.

5. Will programs that are dependant upon the gtk+-2.0 packages be affected by this?

6. I saw that someone was saying that compiz is running as a full screen app ontop of XGL and that is why you are able to run kill compiz.real to get back to XGL, any thoughts on this?[/QUOTE]

1. XGL has a different set of bugs to Compiz.  But the compiz bugs are pretty minimal, at least for me.  The biggest XGL bug I've encountered is with XV & Mythtv - mythfrontend will kill the XGL server as soon as it tries to fiddle with XV.

2.  XGL has the capacity to be faster than a traditional Xorg server.  Whether it is or not depends on many things - how good your current drivers are, how good the OpenGL drivers are, how good **XGL** is at the moment... I don't know in total.

3. You can, if you want to.

4. I think the MX440 bugs are mostly fixed, but check out [compiz.net](compiz.net) if you like.  The card just plain lacks some useful features, so not everything possible with Compiz will work, but you should be able to use it.

5. Nothing cares whether you run XGL or Xorg.  Not even Compiz - it's just that XGL provides a necessary extension.  You can run Compiz on the new Xorg servers with AIGLX support enabled.

6. That someone was slightly wrong.  Compiz is (among other things) a window-manager, just like metacity or kwin, or whatever.  You can run a completely standard Gnome on top of XGL if you want.  It might even be worthwhile, if Composite support doesn't work in your graphics drivers & they have reasonable GL support.  That someone was right in that **XGL** runs as a (most often) fullscreen nested X server in a separate X server.  So, when you run XGL you're running a normal X server, then an XGL server on top of that, then all your programs through the XGL server...

---

### Post by spyke01 on 2006-06-09
thanks for all the great replies, im going to have to check it out

---

### Post by FluffyElmo on 2006-06-09
Somewhat unrelated, but since Myth was mentioned I'm wondering if anyone has it working? After installing the latest version from Raof's repo and running mythbackend I get the following error: 

```
2006-06-09 15:58:08.834 This app was compiled against libmyth version: 0.19.20060331-1
                        but the library is version: 0.19.20060121-2
                        You probably want to recompile everything, and do a
                        'make distclean' first.
2006-06-09 15:58:08.835 Failed to init MythContext, exiting.
```

I tried installing it because of the X crash when it tried to play video and I thought the svn version may not have that problem.

---

### Post by guix on 2006-06-12
Falcon, thanks a lot for the repo, it worked for me (AMD64 + nVidia 6600 GT with latest drivers installed with universe's deb).

Some things don't work however :
- cube just works when dragging a window, ctrl+alt+arrows don't work and moving the pointer (without any window dragged) doesn't flip desktops.
- water plugin doesn't work
- zoom doesn't work
- expose-like effect doesn't work.

I suspect it is a problem with the gconf settings.

I my session startup I have /usr/bin/thefuture :
```
#!/bin/bash
gnome-window-decorator & compiz --replace gconf miniwin decoration wobbly fade minimize cube rotate zoom scale move resize place switcher trailfocus water
```

I also have :
```
xmodmap /usr/share/xmodmap/xmodmap.fr
```

When I looked in gconf-editor I had something else. I edited the key to put :
```
gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher trailfocus water
```. I don't want miniwindow. After that trailfocus DID work but no zoom, switcher, cube buggy, ...

Any help ?

---

### Post by guix on 2006-06-12
Hum. I'll reply to myself :-)
I've changed for xmodmap.fr-2 and cube, switcher, "expose" and water work... I just have to find the keys for zoom.

---

### Post by RAOF on 2006-06-13
[QUOTE=FluffyElmo]Somewhat unrelated, but since Myth was mentioned I'm wondering if anyone has it working? After installing the latest version from Raof's repo and running mythbackend I get the following error: 

```
2006-06-09 15:58:08.834 This app was compiled against libmyth version: 0.19.20060331-1
                        but the library is version: 0.19.20060121-2
                        You probably want to recompile everything, and do a
                        'make distclean' first.
2006-06-09 15:58:08.835 Failed to init MythContext, exiting.
```

I tried installing it because of the X crash when it tried to play video and I thought the svn version may not have that problem.[/QUOTE]
Whoops.  I should clean out my repository.  I don't think the mythtv-svn packages work at all, sorry.

---

### Post by FluffyElmo on 2006-06-13
I actually got it working by just installing the 'myth' packages instead of the svn versions. I didn't realize the other packages had been updated at first:)

Thanks.

---

### Post by IbeeX on 2006-06-18
I tried to install compiz again and still same thing

ibrkanac@ibee:~$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

[1]+  Done                    compiz --replace gconf

I hawe working XGl

here are my setup files

```


FOR sources

deb http://ubuntu.moshen.de/ dapper all
deb http://xgl.compiz.info/ dapper main

FOR gdm

[servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true



```

any idea?

Actualy I managed to start compiz, funy thing is that I realy don't now how, I deleted all files  from /usr/lib/nvidia/
then reinstalled all libs for copiz and it runs :)

---

### Post by guix on 2006-06-20
XGL/Compiz runs great now thanks to Falcon's repository, but I'm often loosing windows borders, is there a workaround ?

---

### Post by guix on 2006-06-23
Nobody ?

---

### Post by JoWilly on 2006-06-25
FYI : I yesterday had the same problem on a fresh dapper install people have reported here with xgl not working.

This was due to a new version of mesa or xgl in the raof repos.

The **updated packages that have appeared today in the repo have fixed the problem**.

Regarding window borders disappearing, people have reported that this as well as xgl crashes is due to the dock plugin. Disabling the dock plugin should fix this (I never used the dock plugin, so I never had the problem).

---

### Post by guix on 2006-06-26
OK thanks for the info, I'll try without dock.

---

### Post by mattlach on 2006-08-12
*deleted for being a stupid question :p*

---

### Post by mattlach on 2006-08-16
Hey...

So I have searched the forums and google without coming up with anything.  I was hoping one of you might have an answer for me.

I am suffering from the white screen (bad refresh) bug.  Everyone in past posts keep suggesting that it is due to outdated packages, but to my knowledge everything I have is new.

I am on an AMD64 system with a GeForce 6800GT.

My sources.list
```
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://www.beerorkid.com/compiz dapper main
deb http://ubuntu.systemadministrator.org dapper eyecandy
deb http://ubuntu.moshen.de/ dapper all
deb http://xgl.compiz.info/ dapper main

```

Versions installed:
compiz-gnome 0.0.13-0quinn31
compiz  0.0.13-0quinn31
cgwd  0.53
xserver-xgl  7.0.0cvs20060625
libglitz-glx1  0.5.6-0ubuntu1
nvidia-kernel 20051028+1
nvidia-glx  1.0.8762+2.6.15.11-3

I have tried everything, including removing compiz-gnome and trying compiz-vanilla without any success.  The white refresh error still remains.

Does anyone have any idea why I am having this problem?

Thanks,
Matt

---

### Post by ekerazha on 2006-08-25
I've used the packages from [http://ubuntu.moshen.de](http://ubuntu.moshen.de) to install XGL+Compiz, but now when I reboot/shutdown, my system freezes on "deconfiguring network interfaces".

I tried several times on fresh installs but same problem ](*,)

---

### Post by sarmadzhiev on 2006-08-26
I just move from gentoo to ubuntu, and under gentoo there are very nice program gset-compiz. Any ideas how to isntall it here. I forgot from where it is in order to compile it. 

Thx

---

### Post by John.Michael.Kane on 2006-08-26
sarmadzhiev gset-compiz has been depreciate thus removed from most of the known compiz repositories.most users are asked to use gconf to adjust compiz settings.

You will have to find the gset source,and compile your own deb for 64bit use.

---

### Post by sarmadzhiev on 2006-08-28
Yes, 
I got that, but do you have any idea where is the source or project page?

I heard it is not maintain and this is the reason. Intresting it is such nice add-on. 

Thx

---

### Post by John.Michael.Kane on 2006-08-28
sarmadzhiev the only gset-compiz source file i found was for suse 10.1 .

Your best bet is to ask over at [compiz.net]("http://www.compiz.net/")

---

