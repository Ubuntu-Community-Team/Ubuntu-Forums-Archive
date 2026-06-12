---
title: "[HowTo] Latest Compiz Fusion on (K)Ubuntu64"
date: 2007-06-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kobalt on 2007-06-26
Allright, since I have been asked a few times how Compiz Fusion could be installed on 64bit, here it is...

Yes, it is possible to have the latest and greatest Compiz Fusion, using either Ubuntu or Kubuntu, on a 32bit or 64bit version alike. In order to do so, we will use the great Franz Rogar's script (which I only had to adjust by adding a missing 's'). 

Before installing Compiz Fusion, please note that [B]this is still unstable. It should not be used on production machines and should not be attempted by any user not feeling capable of undoing these steps, possibly through command line. 

In order to avoid conflicts/problems, you should remove anything you installed related to Compiz/Beryl. 
[/B]
**1. Download the makefusion script** that's attached to this thread (at the end). Save it wherever you like, but place it in a CompizGit (or whatever) folder, since sources will be downloaded within. Rename it to remove the .txt extension, leave it just to *makefusion*
[B]
2. Make the script executable[/B]
```
chmod +x makefusion
```
[B]
3. Configure the script[/B]
The script is made of the following sections:

>     PACKAGES="fusion fusion-gconf compiz-script"
    FUSIONPLUGINS="main extra unsupported zoom gears mswitch wallpaper workarounds"
    COMPIZREMOVE="kde etc..."
    PREFIX="/usr/local"
    DISTRO="ubuntu-feisty"

Here are a few explanations: 
[LIST]
[*]PACKAGES : Compiz Fusion packages to install
[*]FUSIONPLUGINS : Compiz Fusion plugins that doesn't have autogen
[*]COMPIZREMOVE : Compiz compiling options
[*]PREFIX : Compiz Fusion installation folder (don't change it unless you know what you are doing)
[*]DISTRO : Applies patches and configure the dependencies to compile.
[/LIST]
**NOTE:** tested only on Feisty, but should also work in Gutsy. Possibly not Edgy.

Edit these sections to your liking (using the command below), mainly adjusting whether you use Gnome or KDE. You can also select your plugins to install, etc.
```
sudo nano makefusion
```
[B]
4. Dependencies[/B]
In order to install Compiz Fusion we need compiling tools and Git:
```
sudo apt-get install build-essential linux-headers-`uname -r` git-core xsltproc
```
We can now move on with the script and use it to download and install the direct build dependencies of Compiz Fusion:
```
./makefusion packages
```
[B]
5. Downloading Compiz Fusion sources:[/B]
```
./makefusion clone
```
[B]
6. Installing Compiz Fusion:[/B]
```
./makefusion install
```

**7. Configure Compiz Fusion:**
You can either press Alt+F2 and enter *ccsm* or go into System > Pref. > Compiz Config Settings Manager to configure your Compiz.
[B]
8. Run Compiz Fusion:[/B]
Press Alt+F2 and run *compiz-manager*. To launch Compiz Fusion with your sessions add */usr/bin/compiz-manager* to System > Pref. > Sessions.
[B]
9. Uninstall Compiz Fusion:[/B]
./makefusion uninstall
[B]
10. Update Compiz Fusion[/B]
Make sure Compiz isn't running and uninstall it. Run steps 4, 5 and 6 again, and your Compiz is up to date.

Enjoy! :)

---

### Post by Pdavid on 2007-06-26
Is this script meant to install compiz-manager? Because I've followed the instructions with no apparent errors (a few warnings on compile) and I don't seem to have any compiz-manager in /usr/bin (or anywhere else). I looked at it and couldn't tell (but I think it isn't).

The other thing is, running compiz --replace seems to get the compiz desktop, but I can't move windows or anything; I thought this might be because it's not loading the emerald decorator, but that doesn't make much sense.

Maybe the best option is to leave it for now :)

yeah, I'm running feisty 64 on amd.

---

### Post by Kobalt on 2007-06-27
oOops! You made me realise I had forgotten to attach the script...
Yes, when you run it this script installs compiz-manager.

---

### Post by Pdavid on 2007-06-27
hehe... I found the script elsewhere and didn't mention that I couldn't find yours because I thought I was being stupid..maybe I had an old version, I'm trying with yours.

---

### Post by Kobalt on 2007-06-27
You must have had the old version (which I tested as well) : it actually doesn't install Compiz Manager. The script I give here does install it.

---

### Post by jamesford on 2007-06-27
should i uninstall beryl etc first?

---

### Post by Kobalt on 2007-06-27
I stronlgy recommend to uninstall anything related to Compiz/Beryl before installing it, yes.

---

### Post by acadiansteph on 2007-06-27
Does anyone know if my ATI Radeon 200M will work with compiz-fusion. I am using 3d acceleration (direct rendering). I'm assuming I'm using Xorg drivers and not XGL's. I have a 32-bit architecture.

---

### Post by Kobalt on 2007-06-27
The R200 cards should support full 3D, depending on which drivers you use. When you say 'Xorg drivers' : do you mean fglrx ? If so, I believe you should change your xorg.conf file in order to use ati drivers. 
But I'm no ATI expert at all, so if anyone has a good tip...

---

### Post by acadiansteph on 2007-06-27
Yes I am using fglrx. When I changed the xorg.conf file I replaced the ATI string with fglrx in order to get direct rendering. Thanks for your help! Steph

---

### Post by Kobalt on 2007-06-27
I meant you should change the drivers string from *fglrx* to *ati*.

---

### Post by acadiansteph on 2007-06-27
Oops, now I cannot remember what I did initially, if it was fglrx to ATI or ATI to fglrx?What I do know is that my driver is in the Restricted Drivers manager and is in use. I will surely check the xorg.conf file again. Thanks

---

### Post by Mauriciobc on 2007-06-27
The instalation went fine except for one little detail. The compiz-icon script in /usr/share/compiz-icon/compiz-icon.py is missing this line in the beginning:

>  import gconf 

Without this my compiz wouldn´t start with windows borders.
Hope it helps!
:D

---

### Post by Kobalt on 2007-06-27
Thanks for noticing, It's edited.

---

### Post by eks on 2007-06-28
Thanks a lot!!!

This worked for me out of the box. :)

Using AMD64 with ATI GeForce 8500GT (drivers are still the previous beta though) on Feisty.



eks

---

### Post by Kobalt on 2007-06-28
You're welcome :)

---

### Post by dxdemetriou on 2007-06-28
I'll give a try. now I have packages from Trevino's apt on my one pc.
the compiz-fusion is from 0.4 or 0.5 that starts?
another I have to ask is about the compiz that depends on desktop-effects that depends on ubuntu-desktop, the script makes deb packages or it used with make install?
thanks

---

### Post by Azakus on 2007-06-28
I'm having this problem
```
gcc -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -o compiz main.o privates.o texture.o display.o screen.o window.o event.o paint.o option.o plugin.o session.o fragment.o matrix.o cursor.o match.o metadata.o -Wl,--export-dynamic  -lpng12 -lXcomposite -lXdamage -lXfixes -lXrandr -lXinerama -lSM -lICE /usr/lib/libxslt.so /usr/lib/libxml2.so -lstartup-notification-1 -lGL -lm
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make[2]: *** [compiz] Error 1
make[2]: Leaving directory `/home/XXXXX/COMPIZ/compiz/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/XXXXX/COMPIZ/compiz'
make: *** [all] Error 2

```
I'm not quite sure how to fix this. I'm using the beta nVidia drivers 100.14.11 for my 8600 GT card.
{UPDATE}
Solved it. Envy doesn't create a link between my libGL.so.100.14.11 and libGL.so, it makes libGL.so.1
If anyone else has this problem, try this
```
cd /usr/lib && sudo ln -s libGL.so.100.14.11 libGL.so
```

---

### Post by mr.snuff on 2007-06-29
Hi,

I followed the steps and it seemed to install without problems. But there is no compiz-manager I could start!

```
$ compiz-manager
bash: compiz-manager: command not found

```

When I type in
```
ccsm
```
then the settings manager starts. But "compiz-manager" is not working.

I also tried 
```
compiz --replace
```
but the only effect I can see is that my windows don't have any borders then. Also the task bars are gone sometimes and the cube doesn't work.

Any ideas how to fix that?

Thanks!

---

### Post by Kobalt on 2007-06-29
> **dxdemetriou said:**
> I'll give a try. now I have packages from Trevino's apt on my one pc.
the compiz-fusion is from 0.4 or 0.5 that starts?
another I have to ask is about the compiz that depends on desktop-effects that depends on ubuntu-desktop, the script makes deb packages or it used with make install?
thanks

Compiz Fusion is Compiz in its 0.5 version. 
This script does not use Debian packages, it download and compile the latest sources.

---

### Post by Kobalt on 2007-06-29
> **mr.snuff said:**
> Hi,

I followed the steps and it seemed to install without problems. But there is no compiz-manager I could start!

Did you modify the script? If so, please attach here your version.

---

### Post by dxdemetriou on 2007-06-29
I used the script without any modifications, and all related libraries are broken.
I can't use emerald --replace, gtk-window-decorator --replace etc

---

### Post by Kobalt on 2007-06-29
Did you remove your installed packages of Compiz before ?
When you say 'all related libraries are broken' : do you mean apt doesn't find them or do you mean you have broken packages ?
Note that you don't need the Trevino's repos in order to use this script, the dependencies are all in the Ubuntu repos...

---

### Post by mr.snuff on 2007-06-29
Hi, 

I uninstalled it and installed it again, and now I have compiz-manager as well. Unfortunately, as soon as I start compiz-manager my system freezes completely and I'm not able to do anything but shut it off by pressing the button a few seconds.

I'm using Ubuntu Feisty with Gnome and Intel graphics (GMA X3100). 

Any ideas what I could do to make it work?

Thanks for your help!

---

### Post by Kobalt on 2007-06-29
Did you install the proper drivers for your graphic card ?

---

### Post by mr.snuff on 2007-06-29
Yes, I installed the last xserver-xorg-video-intel driver for feisty (version 1.94 or so). Resolution is working fine so I guess the driver is ok.

---

### Post by jamesford on 2007-06-29
script worked fine here and i didnt even uninstall beryl, only disabled it.
just one question, is there a tray icon thing like the beryl manager somewhere, i knida miss that

oh and also, im confused what is compiz-fusion really? is there compiz and then there is compiz-fusion which really just is the old beryl effects available as a plugin for compiz?
or is the whole project known as compiz-fusion now?

---

### Post by wilberfan on 2007-06-29
Wow.

This actually seems to have worked!  :D  Thanks so much for providing this nifty addition to my 64-bit 'buntu!

---

### Post by wilberfan on 2007-06-29
With no trayicon, how do I switch back to metacity or kwin??

[edit]  Nevermind... This seems to be the solution (in KDE):

> To start compiz+emerald from kde:
Code:

compiz --replace -c emerald &
killall kwin #just for the case it has some kwin processes

To swich back to 'normal' mode in kde:
Code:

kwin --replace &
killall compiz compiz.real # mandatory!

[http://ubuntuforums.org/showpost.php?p=2922619&postcount=6](http://ubuntuforums.org/showpost.php?p=2922619&postcount=6)

---

### Post by themoebius on 2007-06-29
this worked well for me, although I had to add a few things to my xorg.conf in order to get window borders.

```
sudo nvidia-xconfig --add-argb-glx-visuals
``` and restart X


But compiz-icon or compiz-fusion-icon aren't included with this script. How can we get those?

---

### Post by Kobalt on 2007-06-30
> **themoebius said:**
> But compiz-icon or compiz-fusion-icon aren't included with this script. How can we get those?
You could possibly add them to the PLUGINS section of the script and see if it's working.. If you test it, can you please repport here how it is working? Just so you know, the last time I tested the compiz-icon (a week ago) it wasn't working, this is why I didn't add it to the script...

---

### Post by accessd on 2007-06-30
This isn't working for me. I followed the instructions and after the install I get:

$ ccsm
bash: ccsm: command not found

$ compiz-manager 
Looking for configuration file(s): 
         Not found: /etc/xdg//compiz-managerrc
         Not found: "/home/jesse/.config/compiz-managerrc"
Checking for nVidia: present. 
Checking for Xgl: not present. 
Checking for FBConfig: present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for XDamage extension: present. 
Checking for XSync extension: present. 
Detected 1 screen(s)
Writing configuration to: /home/jesse/.config/compiz-managerrc
Starting delayed decorator in the background: sleep 1 && emerald --replace &
Checks indicate compiz should work on your system
Exporting: __GL_YIELD=NOTHING  
Executing: compiz --loose-binding --sm-disable --replace ccp 
/usr/bin/compiz-manager: line 548: compiz: command not found

Please let me know if you need any further information.

EDIT:

I was getting the following error while compiling compiz: "/usr/bin/ld: cannot find -lGL". I fixed it by doing the following:

cd /usr/lib/
sudo ln -s libGL.so.1.0.9755 libGL.so

---

### Post by (^o^) on 2007-06-30
While your script installed everything perfectly on my machine, the effects refuse to work,
The managers are present, ati drivers installed, xorg.conf as instructed.
I'm at a loss here.

---

### Post by colo505 on 2007-07-01
Same here, and I've lost my windows borders too..:(

---

### Post by ErBiC on 2007-07-01
This isn't working for me. Kubuntu 7.04 64-bit. I've got fglrx installed properly, with Composite disabled in xorg.conf as instructed. I've tried to run the ./makefusion install a few times now, and each time it seems to only partially work.

Throughout the process, these four lines show up a lot. I'm assuming they're somehow the root of the problem.

```
Executing make
make: *** No targets specified and no makefile found.  Stop.

Executing sudo make install
make: *** No rule to make target `install'.  Stop.
```

There don't seem to be any specific errors otherwise... a few times aclocal exits with code 2 but besides that I can't see anything. I could attach the whole log if someone wants to see it.

Oh, and if I run ./makefusion uninstall it keeps failing, with "no rule to make target 'clean'" and "no rule to make target 'uninstall'". Any ideas?

---

### Post by avik on 2007-07-01
This is so awesome!  I couldn't find certain plugins Beryl had (like the 3d windows when the cube is rotated), but the Fire Paint and Expo plugins are worth it!  Thank you so much!

---

### Post by Kobalt on 2007-07-01
(^o^)  &  colo505: your problelms are linked to your graphic card drivers and your xorg.conf file. You should read the [docs on compiz website]("http://compiz.org/Documentation/Documentation") on how to configure xorg.conf properly in order to get it running. 

ErBiC: your problem seems a bit more complicated. first of all, if composite is disabled in xorg.conf it can be a problem for compiz... You may want to try with the ATI proprietary drivers, possibly through Envy. 
And you shouldn't get all these error messages. Do you get error messages when running ./makefusion clone ?
By the way, are you sure you have the build-essential package installed?

avik: you're very welcome ! :)

---

### Post by strumluff on 2007-07-01
On some ATI cards the composite extension isn't supported with the fglrx drivers and you therefore will need to install XGL and run an XGL session in order for it to work.

I know this is the case for my ATI card the Xpress 200M (aka X1100)

Anyway I am having this issue after installing and configuring I run:

```
compiz-manager
```

And then get this error:

```

Executing: compiz --sm-disable --replace ccp 
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :1.0

```

Not quite sure why! I had Beryl and Compiz both working in XGL before (yes I did remove them before installing Fusion)

Anyone know why?

---

### Post by colo505 on 2007-07-01
Kobalt..

Attempted the install once again after following your Compiz/NVidia link, and everything works perfectly so far!

Thanks a mill.

---

### Post by ErBiC on 2007-07-01
> **Kobalt said:**
> ErBiC: your problem seems a bit more complicated. first of all, if composite is disabled in xorg.conf it can be a problem for compiz... You may want to try with the ATI proprietary drivers, possibly through Envy. 
And you shouldn't get all these error messages. Do you get error messages when running ./makefusion clone ?
By the way, are you sure you have the build-essential package installed?)

If composite is NOT disabled, I get a bunch of Mesa stuff when I run fglrxinfo. [This guide](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) is what I followed. Everything seems to work, I get really good frame rates with fgl_glxgears... it's just that this is screwy.

Isn't xorg-driver-fglrx the ATI proprietary drivers? I know it's probably not the latest version, but I (seemingly) permanently crashed my X server last time I tried to install the latest from ATI.com. I suppose I could try it again... maybe through Envy this time.

There weren't any errors when I ran the clone command. Everything seemed to download without issue. Despite this, though, it seems like a lot of makefiles are either missing or not created properly.

And build-essential is installed... I needed it to compile MadWifi for my wireless.

> **strumluff said:**
> On some ATI cards the composite extension isn't supported with the fglrx drivers and you therefore will need to install XGL and run an XGL session in order for it to work.

Thanks, I'll try that too. I don't think it'll solve my build problems, though.....

---

### Post by cmoz on 2007-07-01
> **ErBiC said:**
> 
There weren't any errors when I ran the clone command. Everything seemed to download without issue. Despite this, though, it seems like a lot of makefiles are either missing or not created properly.

And build-essential is installed... I needed it to compile MadWifi for my wireless.



Thanks, I'll try that too. I don't think it'll solve my build problems, though.....

I'm getting the same errors is there some dependency that's not specified?

---

### Post by gaaslight on 2007-07-01
Thanks for the howto Kobalt. I can finally use emerald themes on my  amd64 fiesty installation. I was even able to activate the svn repositories and fetch more themes after installing subversion. 
There is 1 problem however, when I switch workspaces, the desktop panel disappears. I have to ctrl alt F2 to reboot when this happens and then it takes a long time for ccsm to run (its in my sessions startup)........do you have any tips for me to help use multiple desktop workspaces? I'm using window selector instead of workspace switcher when I have more than 1 window open.

---

### Post by Kobalt on 2007-07-01
> **cmoz said:**
> I'm getting the same errors is there some dependency that's not specified?
Make sure you have the *git-core* and *xsltproc* packages installed maybe.

gaaslight: I'm affraid I had the same problem a few times, I think it's a Compiz bug but I've never digged any deeper on this issue since I now use the new Expose plugin (that works flawlessly).

---

### Post by gaaslight on 2007-07-01
new Expose plugin?
is this the same as or newer version of Expo plugin?
I have both git-core and xsltproc packages installed.
Should I reinstall them?

---

### Post by gaaslight on 2007-07-01
I tried reinstalling those packages and it worked. Thanks again Kobalt!

---

### Post by strumluff on 2007-07-01
Debugged a little more and I find that in XGL when I run

```
 glxinfo | grep direct 
```

I get this output:

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No

```

Can anyone tell me how to fix this ? 

Cheers

---

### Post by Azakus on 2007-07-01
> **strumluff said:**
> Debugged a little more and I find that in XGL when I run

```
 glxinfo | grep direct 
```

I get this output:

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No

```

Can anyone tell me how to fix this ? 

Cheers

XGL doesn't support direct rendering using the standard backend, Xglx. The alternative, Xegl, supports direct rendering, but only works on Radeon r200 cards (Radeon 9000's).
[http://en.wikipedia.org/wiki/XGL#Backends](http://en.wikipedia.org/wiki/XGL#Backends)

---

### Post by ErBiC on 2007-07-02
Never mind what was here before... still screwing up with make errors. I installed the xsltproc package and it made no difference. :(

---

### Post by tlaloczint on 2007-07-03
hi I follow you intuccion but I get this error 

tlaloc@aztlan:~$ ccsm
bash: ccsm: command not found
tlaloc@aztlan:~$ compiz-manager 
Looking for configuration file(s): 
         Not found: /etc/xdg//compiz-managerrc
         Not found: "/home/tlaloc/.config/compiz-managerrc"
Checking for nVidia: present. 
Checking for Xgl: not present. 
Checking for FBConfig: present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for XDamage extension: present. 
Checking for XSync extension: present. 
Detected 1 screen(s)
Writing configuration to: /home/tlaloc/.config/compiz-managerrc
Starting delayed decorator in the background: sleep 1 && emerald --replace &
Checks indicate compiz should work on your system
Exporting: __GL_YIELD=NOTHING  
Executing: compiz --loose-binding --sm-disable --replace ccp 
/usr/bin/compiz.real: Couldn't load plugin 'ccp'

any help?
I intalled the nvidia drivers using th envy scrip if that helps

---

### Post by enryf89 on 2007-07-03
I've got the same problem of **sturmluff**.
i have a ati radeon X1300 and ven i run compiz everything crashes.

thx for your help!

Ciao a tutti

---

### Post by Kobalt on 2007-07-04
sturmluff & enryf89 : your problem lies in installing and configuring your ATI card drivers properly. Unfortunately I'm not an ATI expert, I advice you to search these forums a thread (there are many) explaining how to do that and then come back to test Compiz Fusion.

tlacozint : did you get any errors during the compilling?

---

### Post by unimatrix on 2007-07-04
The script failed for me. There were at least two things missing: **xsltproc** and **moc**
You should install those packages as deps.

Anyway, the script does NOT work.
Here's what happens when I run it with "install":
```

andrej@Andrej:/media/X/Apps/CompizFusion$ ./makefusion install
Welcome to Compiz Fusion

Configuring compiz...

Executing autogen.sh --prefix=/usr/local  --enable-kde --disable-gtk --enable-librsvg in compiz...
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
kde/window-decorator/Makefile.am:32: `%'-style pattern rules are a GNU make extension
kde/window-decorator/Makefile.am:35: `%'-style pattern rules are a GNU make extension
kde/window-decorator/Makefile.am:38: `%'-style pattern rules are a GNU make extension
metadata/Makefile.am:39: patsubst %.xml.in,compiz-%.schemas,$(xml_in_files: non-POSIX variable name
metadata/Makefile.am:39: (probably a GNU make extension)
metadata/Makefile.am:42: `%'-style pattern rules are a GNU make extension
metadata/Makefile.am:43: subst compiz-,,$*: non-POSIX variable name
metadata/Makefile.am:43: (probably a GNU make extension)
autoreconf: Leaving directory `.'
cat: /etc/ld.so.conf.d/*.conf: No such file or directory
cat: /etc/ld.so.conf.d/*.conf: No such file or directory

Installing compiz...

Executing make
decorator.o: In function `KWinInterface':
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
decorator.o: In function `Decorator':
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/decorator.cpp:195: undefined reference to `vtable for KWD::Decorator'
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/decorator.cpp:195: undefined reference to `vtable for KWD::Decorator'
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/decorator.cpp:195: undefined reference to `vtable for KWD::Decorator'
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/decorator.cpp:195: undefined reference to `vtable for KWD::Decorator'
decorator.o: In function `~KWinInterface':
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
decorator.o: In function `Decorator':
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/decorator.cpp:195: undefined reference to `vtable for KWD::Decorator'
decorator.o: In function `~Decorator':
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/decorator.cpp:245: undefined reference to `vtable for KWD::Decorator'
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/decorator.cpp:245: undefined reference to `vtable for KWD::Decorator'
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/decorator.cpp:245: undefined reference to `vtable for KWD::Decorator'
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/decorator.cpp:245: undefined reference to `vtable for KWD::Decorator'
decorator.o:/media/X/Apps/CompizFusion/compiz/kde/window-decorator/decorator.cpp:245: more undefined references to `vtable for KWD::Decorator' follow
decorator.o: In function `~KWinInterface':
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
decorator.o: In function `~Decorator':
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/decorator.cpp:245: undefined reference to `vtable for KWD::Decorator'
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/decorator.cpp:245: undefined reference to `vtable for KWD::Decorator'
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/decorator.cpp:245: undefined reference to `vtable for KWD::Decorator'
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/decorator.cpp:245: undefined reference to `vtable for KWD::Decorator'
decorator.o: In function `~KWinInterface':
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
window.o: In function `Window':
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/window.cpp:86: undefined reference to `vtable for KWD::Window'
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/window.cpp:86: undefined reference to `vtable for KWD::Window'
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/window.cpp:86: undefined reference to `vtable for KWD::Window'
window.o: In function `~Window':
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/window.cpp:132: undefined reference to `vtable for KWD::Window'
/media/X/Apps/CompizFusion/compiz/kde/window-decorator/window.cpp:132: undefined reference to `vtable for KWD::Window'
window.o:/media/X/Apps/CompizFusion/compiz/kde/window-decorator/window.cpp:132: more undefined references to `vtable for KWD::Window' follow
collect2: ld returned 1 exit status
make[3]: *** [kde-window-decorator] Error 1
make[2]: *** [all-recursive] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2

```

It continues, but the rest is pointless as all packages depend on the first one that's not being compiled.

---

### Post by mpneerkaje on 2007-07-04
desktop effects in 64 bit ubuntu is a nightmare for me.  I have tried hundreds of times - beryl, compiz, compiz-fusion everything but in vain. It really sucks!
All i get is a borderless window. I tried all the tricks as per different threads here but in vain. ***off ubuntu 64!

---

### Post by barefootsanders on 2007-07-04
Hey everyone.  I'm new around here so cut me some slack:)... I ran the script and it seemed to work fine.  I can get into the configuration manager but it dosent to start up the effects that i select.  So is there a way to enable the effects or do i have to perform an additional step.

Thanks in advance!

---

### Post by Kobalt on 2007-07-04
> **mpneerkaje said:**
> desktop effects in 64 bit ubuntu is a nightmare for me.  I have tried hundreds of times - beryl, compiz, compiz-fusion everything but in vain. It really sucks!
All i get is a borderless window. I tried all the tricks as per different threads here but in vain. ***off ubuntu 64!
This kind of reply is purely usless, spare us this kind of posts.

---

### Post by Kobalt on 2007-07-04
> **unimatrix said:**
> The script failed for me. There were at least two things missing: **xsltproc** and **moc**
You should install those packages as deps.

These packages are not required for on every install, and I'm still wondering why...
As I wrote in the first post this Compiz Fusion install isn't meant for rookie users, Compiz is still in alpha : its install can break and needs tweakings and Compiz Fusion **will** crash on your system.

---

### Post by unimatrix on 2007-07-04
Who are you calling a rookie?! :D

Anyway, it worked now. I deleted everything and cloned compiz again. The only thing different was that this time i had xsltproc and moc.

---

### Post by Kobalt on 2007-07-04
Great then :) I'm glad it finally worked. I'll add xsltproc to the dependencies list, but I'm really puzzled by moc : how can 'Music On Console' have an effet on Compiz Fusion... ?

---

### Post by unimatrix on 2007-07-08
It's not "Music On Console", it's **Meta Object Compiler** for the Qt GUI app framework. It's probably needed when you're compiling for KDE.

---

### Post by matalon on 2007-07-08
It worked nice here, only a few questions, I don't have the cube reflection and can change the picture in the skydome.   Any ideas? By the way, I AM A ROOKIE :)!

---

### Post by Bondrake on 2007-07-09
I just installed compiz using your script. Thanks!

However, I was receiving an error when I initially tried running Compiz:
```
compiz (core) - Fatal: No RandR extension
```

I found that since I had two monitors and had enabled the nVidia driver feature Xinerama, it had disabled RandR.  So for those nVidia people with dual-screens, you need to disable Xinerama in order to use Compiz! (for some more info, check out this post on freedesktop.org: [http://lists.freedesktop.org/archives/xorg/2007-June/025145.html]("http://lists.freedesktop.org/archives/xorg/2007-June/025145.html"))

---

### Post by Kobalt on 2007-07-09
Thanks for the tip Bondrake ;)

Matalone: you can adjust any settings of Compiz in System > Pref. > Compiz Config. and Settings Manager

---

### Post by Azakus on 2007-07-10
This script worked really well! That being said, Compiz Fusion is giving me a couple of show-stopper errors (such as freezing the screen and rendering my keyboard unusuable), which is why I am still using Beryl until Fusion matures a bit more.

---

### Post by DaveTRG on 2007-07-14
First off, many thanks to Kobalt for providing this script & guide.

I had compiz working great on Feisty, but was having some hardware issues (no wired ethernet) so I went to Gutsy.  

Has anyone had problems with Compiz on Gutsy?  

My video drivers are installed (glxgears, glxinfo work) but when I go to install compiz --replace (or compiz-manager after following the instructions on this thread) it crashes X.

I've tried using the packages that came with Gutsy and uninstalling those packages and installing via the makefusion script.  Either way, compiz crashes X when I try to enable it.  It doesn't take down the whole machine (which it did before I ran "./makefusion package"), but it crash X and X continues to misbehave if restarted, until reboot.

My platform is a Dell Inspiron 1420 laptop, Core 2 Duo T7300, 2GB ram, NVidia Geforce Go 8400 GS video card.

Thanks in advance for any assistance that you can provide.

---

### Post by DaveTRG on 2007-07-14
Okay, I fixed the above issue after much persistence.  I believe the problem was due to answering yes to the question "Install 32bit Opengl compatibility" when installing the NVidia driver.  I re-ran the NVidia drver install, answered no to that question, used the makefusion script following instructions and viola, all is once again well with the world.

Thanks again Kobalt for the script, as the Gutsy packages still don't work.

---

### Post by f1uxam on 2007-07-14
Thanks a lot for this script -- it got back my compiz after a repository update from uPure twhich drew in Trevino's latest borked 64-bit the setup.
Whenever I have had Trevino's builds working, I had transparency in dropdowns of Firefox as well as all other apps.  But, with this script and the tortuously long instructions at
[http://forums.opencompositing.org/viewtopic.php?f=51&t=758&p=5416&hilit=feisty+fawn#p5416](http://forums.opencompositing.org/viewtopic.php?f=51&t=758&p=5416&hilit=feisty+fawn#p5416)
I can get the translucency by adding the type-DropDownMenu -15 in CCSM General>Opacity Settings, but translucency appears in basic system apps but not Firefox. 
Most basically, I'd like to know how the setup one gets by running this script differs from what come by clicking all the debs on Trevino's Feisty AMD64 eyecandy page.

---

### Post by Oppoman on 2007-08-23
> **ErBiC said:**
> Never mind what was here before... still screwing up with make errors. I installed the xsltproc package and it made no difference. :(

Did you ever figure out what was giving you those make problems?  I'm having the same thing punching me while i'm trying to get this working.  The 'packages' and 'clone' operations work fine, but when i try the 'install' i get this output:

Configuring compiz...

Executing autogen.sh --prefix=/usr/local  --enable-gtk --disable-kde --enable-librsvg in compiz...
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
configure.ac:21: installing `./missing'
configure.ac:21: installing `./install-sh'
gtk/gnome/Makefile.am: installing `./depcomp'
kde/window-decorator/Makefile.am:32: `%'-style pattern rules are a GNU make extension
kde/window-decorator/Makefile.am:35: `%'-style pattern rules are a GNU make extension
kde/window-decorator/Makefile.am:38: `%'-style pattern rules are a GNU make extension
metadata/Makefile.am:40: patsubst %.xml.in,compiz-%.schemas,$(xml_in_files: non-POSIX variable name
metadata/Makefile.am:40: (probably a GNU make extension)
metadata/Makefile.am:43: `%'-style pattern rules are a GNU make extension
metadata/Makefile.am:53: patsubst %.xml.in,compiz-%.kcfg,$(xml_in_files: non-POSIX variable name
metadata/Makefile.am:53: (probably a GNU make extension)
metadata/Makefile.am:57: `%'-style pattern rules are a GNU make extension
metadata/Makefile.am:58: subst compiz-,,$*: non-POSIX variable name
metadata/Makefile.am:58: (probably a GNU make extension)
autoreconf: Leaving directory `.'
cat: /etc/ld.so.conf.d/*.conf: No such file or directory
cat: /etc/ld.so.conf.d/*.conf: No such file or directory
configure: error: Package requirements (x11-xcb                  xcomposite              xfixes                  xdamage                xrandr                  xinerama                ice                     sm                      libxml-2.0             libxslt                 libstartup-notification-1.0 >= 0.7) were not met:

No package 'x11-xcb' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_CFLAGS
and COMPIZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


Installing compiz...

Executing make
make: *** No targets specified and no makefile found.  Stop.

Executing sudo make install
make: *** No rule to make target `install'.  Stop.


EDIT*  I fixed my problem by running 'export PKG_CONFIG_PATH=/usr/bin/pkg-config:$PKG_CONFIG_PATH'
I also needed to add libxslt by running 'export PKG_CONFIG_PATH=/usr/lib/libxlt.so.1:$PKG_CONFIG_PATH'

---

