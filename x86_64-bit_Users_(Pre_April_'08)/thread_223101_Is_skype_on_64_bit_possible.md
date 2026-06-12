---
title: "Is skype on 64 bit possible?"
date: 2006-07-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by cneil on 2006-07-25
Hey,
I've got a question.  I know that there hasn't ever been a 64 bit version of skype released, but has anyone ever gotten skype to work on 64 bit ubuntu?  I'm sure if it has been done then someone has posted a HOWTO in the past, but I can't find it.  If it has been done will someone post the instructions or a link to the instructions.
Thanks

---

### Post by braj on 2006-07-26
This is exactly what I wanted to ask as well. There are some things said about skype on amd64 here and there but it's all scattered and not much focused. Could anyone try to give a comprehensive guide to this problem?

---

### Post by RAOF on 2006-07-26
The simple answer:  Yes, it is possible.  Download the statically linked i386 client from the Skype website, and run that.

Of course, Skype uses the (obsolete) OSS sound drivers, which means that only one program can use the soundcard at a time.  And you can't use the "aoss" ALSA OSS wrapper, because that tries to use 64bit libraries with 32bit code :(.

But, for simple cases, you should be able to just download the **statically linked** 32bit version, and use that.

---

### Post by DiabboVerdde on 2006-07-26
I have put it to work perfectly with x86 binaries in a chroot environment. Search this forum for "chroot script". Is a very nice and well created script that creates a "32-bit area" inside your 64-bit system, and you can install any 32-bit program inside it and call it from the 64-bit environment transparently, because they'll think they are on a 32-bit system. The CHROOT thing has solved all my compatibility problems (i use dapper on a HP Pavilion zv5000 notebook).

[]'s!

Geoff

---

### Post by Kilz on 2006-07-26
Chroot's are not nessasary in Dapper. But they can make some things(media players with loads of libs needed)easier to install. For 32bit skype you can use
```
sudo dpkg --force-architecture -i PackageName.deb
```
and replace the PackageName with the .deb files name.

---

### Post by BIGtrouble77 on 2006-07-26
You  can just use the automatix script. ([http://www.getautomatix.com](http://www.getautomatix.com))

Only thing I noticed is that skype takes a while to launch.

---

### Post by Kilz on 2006-07-26
> **BIGtrouble77 said:**
> You  can just use the automatix script. ([http://www.getautomatix.com](http://www.getautomatix.com))

Only thing I noticed is that skype takes a while to launch.

Installing Automatrix to install one application may be double the work. A silple dpkg command isnt that hard.

---

### Post by cneil on 2006-07-26
Hey,
Thanks!  I installed with automatix and everything seems to be working great.  On BoingBoing I just saw a thing about the Democracy player.  It seems to be  a good program, available for 32 bit.  Has anyone successfully gotten this installed on amd64?  Could I use the -force architecture argument with dpkg?

---

### Post by tymek666 on 2006-07-26
new version of skype i alsa compatible:
[http://www.skype.com/download/skype/linux/changelog.html]("http://www.skype.com/download/skype/linux/changelog.html")

---

### Post by braj on 2006-07-26
I followed RAOF's advice (getting statically linked 32bit version) and it works, the only trouble is that it takes some time to start. In any case, thanks a lot!

---

### Post by happyisland on 2006-07-26
I am a total newbie, having just switched over from a lifelong relationship with Windows, and the Automatix install worked perfectly for me. I had tried and failed several times to follow simple how-tos - thanks Automatix!

---

### Post by rayohauno on 2006-08-11
kilz says to use:

sudo dpkg --force-architecture -i PackageName.deb

how i can force the architecture but using aptitude. is this possible ?

---

### Post by zuser on 2006-08-11
I just tried the force-architecture on new beta 1.3 and it did not work due to dependency problems.
Has anyone installed the beta version yet, if so , how?

---

### Post by RAOF on 2006-08-12
> **zuser said:**
> I just tried the force-architecture on new beta 1.3 and it did not work due to dependency problems.
Has anyone installed the beta version yet, if so , how?

Yup:  
Download the statically linked .deb (if there is one - I used the statically linked .tar.gz).  
Download the i386 libasound2 .deb from packages.ubuntu.com.  
Extract the libraries from the .deb, and copy them to /usr/lib32.  
Run **sudo ldconfig**

Skype should now work, although it will still look terrible.

---

### Post by rayohauno on 2006-08-17
ok, gracias, voy a probar.
saludos.

---

### Post by pravsr on 2008-02-16
Hi,

I tried Skype on PC Linux OS and it works perfectly fine. I just went to the synaptic package manager and checked skype and it installed properly.

I even managed to make international calls with my Skype Credit and the voice quality was proper. 

I have an AMD 64 Bit Athlon processor and ASUS A8NVM motherboard.

However, I had problems installing Skype on SuSe, Fedora, Ubuntu/Kubuntu.

Regards,
Prav

---

### Post by Cappy on 2008-02-16
This thread is outdated
Look here: [http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

---

### Post by Timokl on 2008-02-17
> **Kilz said:**
> Chroot's are not nessasary in Dapper. But they can make some things(media players with loads of libs needed)easier to install. For 32bit skype you can use
```
sudo dpkg --force-architecture -i PackageName.deb
```
and replace the PackageName with the .deb files name.

I tried that but when I start Skype, I get error messages:

```
skype: error while loading shared libraries: libQtDBus.so.4: cannot open shared object file: No such file or directory
```

I use Gutsy 64 Bit, and Skype  Version 1.4.0.118 from [http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)

Timo

---

