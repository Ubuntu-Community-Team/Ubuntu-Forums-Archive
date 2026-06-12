---
title: "Flash in AMD?"
date: 2005-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by luckyaba on 2005-10-13
Is flash suppported yet in 64bit? or are we still waiting?
if so anyone know how long?

---

### Post by DJ_Max on 2005-10-13
No, and seeing as Macromedia Flash is closed sourced, it's up to Macromedia, and they have made no mention of native 64bit linux binaries. Which isn't a surprise.

---

### Post by luckyaba on 2005-10-13
well aren't they the stingy ones. 

thanks

---

### Post by Xiata on 2005-10-13
[QUOTE=luckyaba]well aren't they the stingy ones. 

thanks[/QUOTE]
Install 32bit firefox then install flash inside that.
Generally works like a charm.

---

### Post by DancingSun on 2005-10-13
Well, according [this blog]("http://www.kaourantin.net/2005/08/porting-flash-player-to-alternative.html"), macromedia is looking for Linux guru to help them with the port.  At least you know they are working on it, and it *will* come eventually.

---

### Post by RAOF on 2005-10-14
[QUOTE=Xiata]Install 32bit firefox then install flash inside that.
Generally works like a charm.[/QUOTE]
Can you link a howto to install 32bit firefox?  I'd like to install it, but I don't know a good way to.  I suppose I could change repositories to 32bit breezy & download it from there, but that doesn't seem like a good idea :)

---

### Post by Orborde on 2005-10-14
[This is one way to do it](https://wiki.ubuntu.com/DebootstrapChroot), but it's kind of messy and, when I did it, sound didn't work. However, I got Flash and Sun Java in, so it was mostly happy.

My opinion is that grabbing a 32bit Ubuntu for the time being might be a better bet. But do as you will.

---

### Post by rplantz on 2005-10-14
[QUOTE=DancingSun]Well, according [this blog]("http://www.kaourantin.net/2005/08/porting-flash-player-to-alternative.html"), macromedia is looking for Linux guru to help them with the port.  At least you know they are working on it, and it *will* come eventually.[/QUOTE]

Thanks for the link.

After reading it, I retract any statements I've made about this being an easy problem.

I didn't realize that they were using mmx and altivec to optimize things. I've written a little altivec code (the PowerPC chip) and know that it's not easy. Furthermore, nothing is standard. Altivec on the G5 chip differs from the one on the G4.

I've also done a lot of assembly language coding. Moving from Intel syntax to AT&T is not trivial. Yes, there's an option in the gnu assembler (gas) to use Intel syntax. With over 30 years experience in the field, I've never seen such things work 100%. There's always a gotcha.

I don't have great hopes about seeing a 64-bit version any time soon. I think their best hope is to release the software into the open source community. For example, I'd love to work on it, but I don't feel like taking on the pressure of the whole project at this point in my life.

Bottom line: I now have a better understanding of the problem. It's a difficult one to solve.

Bob

---

### Post by zekolas on 2005-10-15
You may also want to check out gplflash
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
scroll down untill you see the "Flash for x86_64" section.

---

### Post by luckyaba on 2005-10-15
excellent. i will try that out later on.

---

### Post by gsaathoff on 2005-10-15
just tried gplflash.  works great -- but dependencies were a bit of an issue... either way, a few hundred megs later everything works.  thanks!

note that the wget command didn't work for me.  i had to search for the package on google and download manually.

-g

---

### Post by chaok on 2005-10-16
are there apt repositories that have this?

---

### Post by RAOF on 2005-10-17
The repositories certainly have **a** version of gplflash.  I personally found that version to not work in any real way and to kill firefox on pages with flash, etc.

---

### Post by zekolas on 2005-10-17
I successfully compliled gpl flash, I did need to stop and install a lot of differnt packages to get it to successfully compile. When you try to compile it it should send an error message saying cannot find "xxxdev" or something so I just tried to compile, got error, installed missing package and repeated untill I finally got all the packeges installed. you can use the command

sudo apt-cache search packagename

to find what packeges you need to install.

---

### Post by RAOF on 2005-10-17
[QUOTE=zekolas]...you can use the command

sudo apt-cache search packagename

to find what packeges you need to install.[/QUOTE]
Actually, you don't need the "sudo"

apt-cache search package

works fine :D

---

### Post by mandos on 2005-10-17
solved

---

### Post by rplantz on 2005-10-18
I had the same experience as RAOF (post #13) when I installed gplflash from a repository under hoary.

I followed the suggestions of zekolas in posts #9 and #14 to compile and install gplflash under breezy. I found that I needed to install the following libraries:
libjpeg62-dev
libmad0-dev
xlibs-dev
zlig1g-dev

Some of them had dependencies that installed additional libraries.

I simply used Synaptic.

It works when I test it at [http://www.macromedia.com/shockwave/welcome/](http://www.macromedia.com/shockwave/welcome/)

One mistake I made was that I forgot the options to the ./configure command as specified in the wiki instructions. If you make a mistake, I recommend reading the INSTALL file that comes with the gplflash package. It tells you how to uninstall and clean everything up so you can start over. Just to be safe, I uninstalled, deleted the gplflash directory, unstuffed the .tar.bz2 archive and started all over again.

Bob

---

### Post by RAOF on 2005-10-18
[QUOTE=rplantz]...
One mistake I made was that I forgot the options to the ./configure command as specified in the wiki instructions. If you make a mistake, I recommend reading the INSTALL file that comes with the gplflash package. It tells you how to uninstall and clean everything up so you can start over. Just to be safe, I uninstalled, deleted the gplflash directory, unstuffed the .tar.bz2 archive and started all over again.

Bob[/QUOTE]
Or, I recommend installing home-built stuff using the excellent checkinstall program/script.  Simply replace "sudo make install" with "sudo checkinstall", and it will build a .deb and install it, for easy removal/upgrade using apt :)

---

### Post by whiskybar on 2005-10-18
There is a yet simpler way of resolving the dependencies to build the package:

apt-get build-dep libflash0c2

You can then download the current version of gplflash and build it - the dependencies won't likely change from the packaged version to the current version.

HTH,  jbar

---

### Post by JuanC on 2005-10-18
I try these flash alternatives , but no one works fine for me.

I think the problem would be worst when websites using VP6 codec for videos in Flash , because VP6 codec is not supported in Linux , it only works if you put dll codec from Windows to Linux and this doesn't work on amd64 because these dlls are 32-bits ...

---

### Post by Navyblue on 2005-10-18
Hi all,

I am trying to install the Flash plug-in for my Mozilla.

I was following the instruction here:
[https://wiki.ubuntu.com/RestrictedFormats#head-4b63d2b9b0665a64bd1125bfedebe1fb6335df7c](https://wiki.ubuntu.com/RestrictedFormats#head-4b63d2b9b0665a64bd1125bfedebe1fb6335df7c)

When I typed:

```

./configure --prefix=/usr --with-plugin-dir=/usr/lib/mozilla-firefox/plugins/

```

I get this:

```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.

```

Is this the dependancy problem that you guys are talking about? How do I solve this?

Thanks. :)

---

### Post by nwillis on 2005-10-18
I just tried this (with checkinstall) and it works great.  I really am surprised that it is this functional.  Can we add this package to Tamir's repo?

n

---

### Post by Navyblue on 2005-10-18
[QUOTE=Navyblue]Hi all,

I am trying to install the Flash plug-in for my Mozilla.

I was following the instruction here:
[https://wiki.ubuntu.com/RestrictedFormats#head-4b63d2b9b0665a64bd1125bfedebe1fb6335df7c](https://wiki.ubuntu.com/RestrictedFormats#head-4b63d2b9b0665a64bd1125bfedebe1fb6335df7c)

When I typed:

```

./configure --prefix=/usr --with-plugin-dir=/usr/lib/mozilla-firefox/plugins/

```

I get this:

```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.

```

Is this the dependancy problem that you guys are talking about? How do I solve this?

Thanks. :)[/QUOTE]

Btw I have solved this dependency problem.

The flash plug-in did showed up on the Mozilla's "About Plug-ins" page. However, flash would not get displayed on the web page.

Anyone got this working for Mozilla? If it works for Firefox I guess it should work for Mozilla.

Thanks in advance.

---

### Post by zekolas on 2005-10-18
[QUOTE=Navyblue]Btw I have solved this dependency problem.

The flash plug-in did showed up on the Mozilla's "About Plug-ins" page. However, flash would not get displayed on the web page.

Anyone got this working for Mozilla? If it works for Firefox I guess it should work for Mozilla.

Thanks in advance.[/QUOTE]

Does any webpages display flash? I have not tried flash in mozilla, but in firefox the plugin will work for most simple flash pages, however in my experance the plug in is far from perfect and I have encountered many pages were the plugin did not play the flash.

---

### Post by Navyblue on 2005-10-18
[QUOTE=zekolas]Does any webpages display flash? I have not tried flash in mozilla, but in firefox the plugin will work for most simple flash pages, however in my experance the plug in is far from perfect and I have encountered many pages were the plugin did not play the flash.[/QUOTE]

I tried a couple of sites (not all of course) and it didn't show up anything, whereas those same pages have no problem on the Firefox.

---

### Post by bonzodog on 2005-10-19
I have finally downloaded and installed GPL flash and it kinda works. Some sites say they will only accept Macromedia Flash though...so it's not a complete fix, but it stops firefox displaying the annying plugins are missing thing, and firefox doesn't crash when trying to load them. they just don't load, is all. I have yet to trawl through some other sites to see what works...could be fun

---

### Post by zupermanz on 2005-10-19
i have tried this it works but i noticed that mozilla closes automatically (often not always) when entering a site with flash.
Do you have the same prob?

---

### Post by Uber_n00b on 2005-10-23
I tried to install gplflash with the method proposed by zekolas, and when i got to the very end, it said the isntall failed.  I want to remove it so that I can try again, because every time i get to a page with flash content, my browser crashes.  I followed the instructions in the install file, but it's still hangin around.  Can somebody tell me how I can remove this?  thanks.

---

### Post by rplantz on 2005-10-23
[QUOTE=Uber_n00b]Can somebody tell me how I can remove this?  thanks.[/QUOTE]

Have you tried ```
make uninstall
```

---

### Post by Uber_n00b on 2005-10-23
make: *** No rule to make target `uninstall'.  Stop.

this is what I get when I try make uninstall

---

### Post by zekolas on 2005-10-23
To uninstall you simply have to remove the flash files from the 
/usr/lib/mozilla-firefox/plugins/ 
directory, the files are flashplayer.xpt and libflashplayer.so

just use the command 
```
sudo rm /usr/lib/moxilla-firefox/plugins/flashplayer.xpt

```
then use the same command to remove the libflashplayer.so file.

---

