---
title: "To 64 bit or not to 64 bit"
date: 2008-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by wordwarrior on 2008-01-25
I'm picking up a new Intel Core 2 Duo system tomorrow and I plan to install Ubuntu on it.

Since I already have an iMac for my "leisure" computing activities, I plan to use my new Ubuntu system for Java development.    This includes server-side stuff as well as Swing, Applets and anything else I feel like trying out.

I also need basic functionality like web browsing and the ability to listen to legally obtained MP3s while I'm coding.

From what I understand, the only real problems with 64 bit Ubuntu are with Flash and Java applets.  However, I heard that it's possible to run a 32 bit version of Firefox through some sort of emulation layer.

What do you think?  Any advice will be appreciated.

---

### Post by NightwishFan on 2008-01-25
I recommend 64-bit mainly because it seems like you are only using a bit of your processor's potential on 32. Getting Flash and Java from what I know is a bit more complicated but not ridiculous.

---

### Post by damvcoool on 2008-01-25
you can use 64bit firefox and get IcedTea Java7 and for Flash you can use either Gnash works pretty fine with me, or ndswarper (whatever the name is) and flash.

---

### Post by amorangi on 2008-01-25
I've just upgraded to the 64bit and it is noticeably faster - probably a good 20% or so. The only problem I've encountered is flash, but running the script here [http://home.comcast.net/~ubuntume/oldflash-0.1.2.tar.gz](http://home.comcast.net/~ubuntume/oldflash-0.1.2.tar.gz) fixes that nicely.

---

### Post by NightwishFan on 2008-01-25
This is the method i used to install flash and it has worked flawlessly.

[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

---

### Post by MetalOverlord on 2008-01-25
My advice is try it. 64bit java is horrible. I could never get Netbeans or Eclipse to run with anything close to acceptable performance and ended up having to create a 32bit chroot to do java programming and run the java plugin. There's a script floating around created by one of the mods (at least I think he's a mod) for installing 32bit versions of a browser and plugins that many people around here have used with success. I believe it also installs version 6 of java for the plugin so that would be an alternative to creating a chroot.

Otherwise 64bit Ubuntu runs just fine and there's a lot of 64bit software available.

If you find it doesn't suit your needs, you can always switch to a 32bit version, but I'd give 64bit a try first.

---

### Post by stmiller on 2008-01-25
64bit!

---

### Post by Kilz on 2008-01-25
> **wordwarrior said:**
> I'm picking up a new Intel Core 2 Duo system tomorrow and I plan to install Ubuntu on it.

Since I already have an iMac for my "leisure" computing activities, I plan to use my new Ubuntu system for Java development.    This includes server-side stuff as well as Swing, Applets and anything else I feel like trying out.

I also need basic functionality like web browsing and the ability to listen to legally obtained MP3s while I'm coding.

From what I understand, the only real problems with 64 bit Ubuntu are with Flash and Java applets.  However, I heard that it's possible to run a 32 bit version of Firefox through some sort of emulation layer.

What do you think?  Any advice will be appreciated.

Flash is installable to your 64bit browser, but not a Sun Java plugin. Icedtea is not sun java, its a open source version that may or may not work for you. [You can run a 32bit firefox, flash , and Sun java plugin if you want.]("http://ubuntuforums.org/showthread.php?t=202537") The install script should take a few minutes to run and have everything setup.

---

### Post by JCMS on 2008-01-26
> **NightwishFan said:**
> I recommend 64-bit mainly because it seems like you are only using a bit of your processor's potential on 32. Getting Flash and Java from what I know is a bit more complicated but not ridiculous.


Yeah that's how I feel about 64bits, even though I'm using 32bits Ubuntu. I'll probably switch next month.

The main advantage of 64bits is if you wanna use 4-128GB (well, this is the maximum now but I think 64bits' theoretical limit is 16TB) of RAM

---

### Post by bufsabre666 on 2008-01-26
theres very few things that you cant do in 64bit linux anymore that you could do in 32

its not like microsoft where the 64bit is slightly faster but you cant install alot of things

---

### Post by macaholic on 2008-01-26
I use 64-bit swiftwesel 3.0b2 with icedtea from these sources and its never gave me any problems.
```
deb http://people.ubuntu.com/~doko/ubuntu/ gutsy/
deb-src http://people.ubuntu.com/~doko/ubuntu/ gutsy/
```
Keep in mind this is development code, but for me it's alot more stable then the iced tea from the repositories.

---

### Post by Kilz on 2008-01-26
> **macaholic said:**
> I use 64-bit swiftwesel 3.0b2 with icedtea from these sources and its never gave me any problems.
```
deb http://people.ubuntu.com/~doko/ubuntu/ gutsy/
deb-src http://people.ubuntu.com/~doko/ubuntu/ gutsy/
```
Keep in mind this is development code, but for me it's alot more stable then the iced tea from the repositories.

It may not give you problems simply because of the sites you visit. But other users have said that they have had problems seeing some applets while using icedtea.

---

### Post by DJiNN on 2008-01-26
I've got several distros on my Core 2 Duo laptop, and just recently (again) installed Xubuntu Hardy Alpha 3. Just setting it up now, with Firefox 3 as browser, and it's perfectly stable.  As a previous poster said, 64 bit OS isn't what it used to be just a scant 18 months ago. It's fast, and really solid...... even this Alpha! :)

Give it a go...... i'm sure you'll not be disappointed. :)  Oh, and while i think of it, AFAIK the 64 bit snapshot of Opera (Which is really stable) comes with Flash ready to go (not sure about Java).

---

### Post by cotcot on 2008-01-26
I switched from 64 to 32 because of apps in 32 bit only (printer driver ...). The loss of speed was limited. I could only observe a difference for heavy apps such as video rendering. I have done some tests as well. Nevertheless I kept my 64 for video rendering. I also tried with more ram but that gave no speed gain neither. I had up to 3 GB but never saw more than 1 GB used.

---

### Post by Perfect Storm on 2008-01-26
and if you're into gaming: [http://ubuntuforums.org/showthread.php?t=662770](http://ubuntuforums.org/showthread.php?t=662770)

---

