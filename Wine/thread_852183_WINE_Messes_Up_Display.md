---
title: "WINE Messes Up Display"
date: 2008-07-07
forum: Wine
---

### Post by Vince4Amy on 2008-07-07
Wine seems to mess up my display. I've just installed it on my system (Version 1.0) and when I type winecfg in the command line the display garbles up though I can clearly see that winecfg is open.

I can restart X and it will run fine again.

The latest release also does this and I am using the closed source ATI Drivers which are working fine.

How can I correct this so that this doesn't happen?

---

### Post by cogadh on 2008-07-07
I've never heard of something like this happening with winecfg. Would it be possible to get a screenshot?

---

### Post by Vince4Amy on 2008-07-08
When I screenshot it everything looks as normal in the screnshot. There are no error messages and after I restart X and run winecfg again it's absolutely fine.

I can then use WINE but some applications, especially ones which want to change the display resolution just cause the same thing to happen again until I restart X.

---

### Post by chrysemys on 2008-09-12
Hi, I have got a similar problem. 
I am trying to get Thomb raider running under wine on a 24" monitor for a friend of mine
screenresolution 1920x1200
ATI Technologies Inc Radeon HD 3870 (1GB video RAM)
using Hardy Heron 8.04.1
fglrx 8.522
Though I celebrated my 10th anniversary of switching to (debian/GNU)-linux, two months ago ( ;-) ) this problem is somewhat new to me.

---

### Post by v4npro on 2008-09-12
> **chrysemys said:**
> Hi, I have got a similar problem. 
I am trying to get Thomb raider running under wine on a 24" monitor for a friend of mine
screenresolution 1920x1200
ATI Technologies Inc Radeon HD 3870 (1GB video RAM)
using Hardy Heron 8.04.1
fglrx 8.522
Though I celebrated my 10th anniversary of switching to (debian/GNU)-linux, two months ago ( ;-) ) this problem is somewhat new to me.

I got same graphics card as you, and same drivers, i also get the same problem.  It's not just Wine, it also happens in Cedega --> [Picture]("http://customwow.net/pics/linx.jpg")

Try "Troubleshooting
[edit] Rectangle/Checkerbox corruption with OpenGL programs

OpenGL programs like e.g. blender in windowed mode, show a rectangle/checkerbox corruption. This can be solved by using a Virtual display setting with a multiple of 64 bigger than you actual resolution like 1664 instead 1600 for width: "   i dunno if it will help, since I'm reading that ati linux drivers from 8.5-8.8 cause these problems in Wine. 8.4 works though, apprently.

---

### Post by jaqie on 2008-09-12
If it won't capture on a screencap then it's definitely driver/card problems, I would say.

---

### Post by Vince4Amy on 2008-09-13
It seems to be well known now, apparently ATI are working on a fix though it's  been like 2/3 versions of the driver so far with the same problem.

---

### Post by chrysemys on 2008-09-13
Yup, we  also guessed it was a driver problem.

I succeeded to get a non-messed up screen bij adding the virtual layout in the /etc/X11/xorg.conf, but in contrast to Debian, Ubuntu does not detect that this configuration file was edited manually and overwrites it with old values (using something called dexconfig) if something else goes wrong with the X-server. (This was self-assertiveness is  the reasons why I returned to Debian on my own systems again,but this is not an option for my friend)

There is some speak of that these values come from a debconf database, where are its files located?
(where I could add my own calculated screen Modelines for example)

Thanks for the OpenGL tip, Any more tips how we add some more weight to the severity factor of this bug at ATI? (get them to speed up to solve this problem)

---

### Post by chrysemys on 2008-09-15
Well, the workaround seems to be working.
The only problem is that after I edit the /etc/X11/xorg.conf to the appropriate virtual desktop, it appears to `automagically' replaces the custom, working 1920x1200 modeline to drive the screen, which I found on the internet, with one coming from its own database but is not working with my screen.(Iiyama ProLite E2403WS) (another fglrx-bug?)

After a reboot some kind of `bulletproof-X'mechanism then takes the liberty to replace all carefully selected settings, by some crude VESA-Caveman settings and I can start the whole process again. Already I tried screenconfig-gtk which gets the right video timings from the `.INF'file, but the system seems to forget these after a reboot, and I was unable to locate the corresponding database-file myself in order to hack the custom timings into it myself. Also the /etc/gdm/gdm.conf file is not present since it is a Kubuntu system without GDM, so I cannot tell it at the predefined spot that the bulletproof-X feature should be disabled.

A Quick and dirty fix I realized was clearing  the writable bit of xorg.conf file for all users and the system seems to understand this hint, but now it shows some other unwanted behaviour, like not properly powering down when using the KDE-windowmanager buttons (the halt command as root works though, but is not acceptable for the eventual, less commandline-oriented main user of the system.)

If this question exceeds the scope of this community, please tell me where I should ask it instead.

Regards

---

### Post by nwlinkvxd on 2008-09-15
The problem you're encountering is referred to as the "Checkerboard of Doom". The best solution is to revert fglrx to version 8.5, which is the last known stable version of the drivers. To do so, follow [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8.29") replacing all instances of "8-8" with "8-5". You'll probably want to fully uninstall your drivers first.

---

### Post by chrysemys on 2008-09-18
Hi, thanks for your input; 

Google-ing the term `Checkerboard of doom'did indeed clarify the problem and deliverd some additional workaround candidates I would have tried, were it not that ATI released version 8.9 of its drivers yesterday (17-09-2008) which seems to be working.

Also the tip of version 8.5 was welcome because somehow I thought I saw it mentioned somewhere that 8.1 was the lates version without the problem. Since this would not create Hardy Heron Packages in my case I was about to get pretty annoyed -were it not for your remark- :-)

Thanks for the help.

---

### Post by Alfx on 2008-09-18
> **chrysemys said:**
> Hi, thanks for your input; 

Google-ing the term `Checkerboard of doom'did indeed clarify the problem and deliverd some additional workaround candidates I would have tried, were it not that ATI released version 8.9 of its drivers yesterday (17-09-2008) which seems to be working.

Also the tip of version 8.5 was welcome because somehow I thought I saw it mentioned somewhere that 8.1 was the lates version without the problem. Since this would not create Hardy Heron Packages in my case I was about to get pretty annoyed -were it not for your remark- :-)

Thanks for the help.

Im running unbuntu hardy (lastest version)

Can you give me step by step instruction on how to install the new ATI drivers, so I can get rid of the checkboard of doom?

Thanks

---

### Post by zami on 2008-09-19
> **Alfx said:**
> Im running unbuntu hardy (lastest version)

Can you give me step by step instruction on how to install the new ATI drivers, so I can get rid of the checkboard of doom?

Thanks

One of these might be what you are looking for -

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8.29](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8.29)

I'm still suffering the checkerboard myself (though I was calling it "scrambled mosaic") with an HD3850 so I'll be eagerly following this thread if it goes on.

-zami

---

### Post by Canis familiaris on 2008-09-19
Are you using ATI?
Upgrading to Catalyst 8.9 solves the problem.

---

### Post by chrysemys on 2008-09-19
Well, I guess the upgrade procedure depends on how the user Alfx has installed the drivers initially. (  (s)he asks to install the NEW drivers, which suggests (s)he did at least one instell already).
Possibly:
1) (s)he downloaded the ATI binary, executed it and used the option `install Driver xxxx on X.org xxxxxxx" 

instead of 

2)*first executing `./ati-driver-installer-8-9-x86.x86_64.run --buildpkg Ubuntu/hardy' from commandline in order to creat a set of deb-package files
*issueing `sudo dpkg -i *.deb' from the same commandline, to install the packages using the dpkg package mechanism (afterwards: run `sudo apt-get -f install' to get things right.)

It might it be a little bit more difficult to remove all traces from the old driver-files and links if (s)he used the first method.

If (s)he did it the second way, (s)he just needs to `dpkg --purge ' the old driver packages (in my case these were: fglrx-amdcccle xorg-driver-fglrx
fglrx-kernel-source  xorg-driver-fglrx-dev fglrx-modaliases) regenerate the packages, using the new installer version-file and install them like denoted above, using dpkg and apt-get...

---

### Post by zami on 2008-09-19
> **zami said:**
> One of these might be what you are looking for -

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8.29](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8.29)

I'm still suffering the checkerboard myself (though I was calling it "scrambled mosaic") with an HD3850 so I'll be eagerly following this thread if it goes on.

-zami


I forgot to mention, if you are using these instructions, 
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8.29](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8.29)
**[COLOR="SeaGreen"]replace the two instances of "8-8" with "8-9"[/COLOR]**
Very important!  Otherwise you'll just end up with Catalyst 8.8, which is still checkerboardy.

Also, on a second run through everthing actually took for me (why? tis a mystery) and I've rid myself of the checkerboard.  (And replaced it with a grey screen - uhg.)

-zami

---

### Post by Vince4Amy on 2008-09-20
I've found that running the file provided from ATI and using the automatic option installs the drivers fine now.

---

