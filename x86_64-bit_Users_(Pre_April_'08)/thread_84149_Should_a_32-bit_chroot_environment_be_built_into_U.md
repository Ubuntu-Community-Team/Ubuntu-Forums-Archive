---
title: "Should a 32-bit chroot environment be built into Ubuntu-64 ?"
date: 2005-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by aneeshm on 2005-10-30
I've been using Ubuntu since 5.04 came out , and I'm extremely impressed by the absolutely seamless end-to-end integration the system has shown . I have a request - can a 32-bit chroot jail be built into the system itself , in which system are run packages like firefox , so that java and flash can work out-of-the-box ?

Any 32-bit binary would automatically be run in the 32-bit chroot jail . So would be any 32-bit package be installed there . Is this practicable ?

---

### Post by Big Venus on 2005-10-30
Yes a 32bit chroot environment should be built into Ubuntu 64. I am one of a few that had problems trying to get the dchroot to start up and I followed all of the directions. I am pleased to say that I like the fact that you can use dchroot if you can get it to run, versus the fedora not having anything equal to it.

---

### Post by BoyOfDestiny on 2005-10-31
Hmm. No. 
Not everyone needs 32-bit.

However many (and me too) would like 32-bit support. Either debian/ubuntu can implement "multilib" or in the mean time make it trivial to do this chroot business...

Would it be doable as a meta-package or an automated script?

---

### Post by RAOF on 2005-10-31
You can already get the ia32-libs package (and the ia32-libs-gtk, -qt, etc packages).  That works fine - I can build 32bit executables, and the 32bit wine .deb installs and runs cleanly (with --force-architecture, of course).

---

### Post by Navyblue on 2005-11-01
[QUOTE=RAOF]You can already get the ia32-libs package (and the ia32-libs-gtk, -qt, etc packages).  That works fine - I can build 32bit executables, and the 32bit wine .deb installs and runs cleanly (with --force-architecture, of course).[/QUOTE]

Would it also enable the installation of binary packages like Opera or Flash plugin?

---

### Post by RAOF on 2005-11-01
If you've got a i386 binary .deb, you can install it with
```
sudo dpkg -i --force-architecture <whatever.deb>
```
and if you've got all the ia32-libs-* there's a good chance that it will run.  Some things still won't, and to install flash in firefox you'll need a 32bit firefox.  So it won't do the same as a 32bit chroot, where AFAIK you install **both** a 64- & 32-bit system, but it will work for many things.

---

### Post by Navyblue on 2005-11-01
[QUOTE=RAOF]If you've got a i386 binary .deb, you can install it with
```
sudo dpkg -i --force-architecture <whatever.deb>
```
and if you've got all the ia32-libs-* there's a good chance that it will run.  Some things still won't, and to install flash in firefox you'll need a 32bit firefox.  So it won't do the same as a 32bit chroot, where AFAIK you install **both** a 64- & 32-bit system, but it will work for many things.[/QUOTE]

Hmmm... Would it mean that chroot is unnesessary if all I want is 32 Firefox + 32 bit Flash plugin and may be Wine?

---

### Post by rplantz on 2005-11-01
[QUOTE=Navyblue]Hmmm... Would it mean that chroot is unnesessary if all I want is 32 Firefox + 32 bit Flash plugin and may be Wine?[/QUOTE]

I asked this question (about firefox) and have not yet seen an answer.

After installing the ia-32 libraries, it was very easy for me to write my own assembly language programs and run them.

It would seem that 32-bit firefox should run (after installing the required libraries). In fact, I would submit that this should be the default version in our 64-bit world.

As far as I know, this is what's done with openoffice.

Bob

---

### Post by Navyblue on 2005-11-01
[QUOTE=rplantz]I asked this question (about firefox) and have not yet seen an answer.

After installing the ia-32 libraries, it was very easy for me to write my own assembly language programs and run them.

It would seem that 32-bit firefox should run (after installing the required libraries). In fact, I would submit that this should be the default version in our 64-bit world.

As far as I know, this is what's done with openoffice.

Bob[/QUOTE]
Has anyone actually run 32 bit firefox without chrooting in 64 bit ubuntu? Where can I download the .deb file?

Thanks.

Editted: Btw, would there be conflict if 2 versions of firefox are installed without chrooting?

---

### Post by Optimal Aurora on 2005-11-02
the force architecture command doesn't work everytime and I haven't gotten it to work yet. But know I am worried about other things.

---

### Post by RAOF on 2005-11-02
Aha!  It's possible to run the 32bit firefox 1.5rc1 binary from mozilla.org!  Details in[ this thread]("http://www.ubuntuforums.org/showthread.php?t=84732").  Maybe I'll write a howto, sometime ;)

---

### Post by Optimal Aurora on 2005-11-03
Yes please do...

---

### Post by Bloot on 2005-11-03
[QUOTE=RAOF]Aha!  It's possible to run the 32bit firefox 1.5rc1 binary from mozilla.org!  Details in[ this thread]("http://www.ubuntuforums.org/showthread.php?t=84732").  Maybe I'll write a howto, sometime ;)[/QUOTE]


It'll be much appreciated, I can asure you. I tried a few hours ago and firefox was about to launch but it finally couldn't, with no error reported, just the try to launch and that's all.

I installed the 1.0.7 32bit by the way, not the 1.5 beta.

Greetings!.

---

### Post by Yagisan on 2005-11-04
Personally, I'm not at all in favour of 32bit chroot jail being built in by default. If you need one you can easily build it yourself.

I looked carefully at this list, and with the exception of wine and openoffice, every single application listed is a proprietery application, with a vendor that has no intention of supporting amd64 as a platform.

Wine, because if it's nature (it is a 32bit Windows Compatablity Layer) can not be built as a 64bit binary - if it was, your Windows applications would not work. OpenOffice.org, well - obviously the primary author (Sun Microsystems) hadn't bothered to see if it was 64bit clean (which any well written, non system specific should be), that is why Ubuntu has the ia32-libs packages, they can examine the source and deterime what they need to do to get it working.

I think that you should be complaining to the vendor of your proprietery application that it should be making amd64 versions of their software, instead of saying Ubuntu amd64 should support those applications.

If you can't live without those (non-essential) applications, then I suggest you install Ubuntu i386 and be happy.

For those of you using --force-architecture with dpkg, remember that option may as well read as "break my Ubuntu" because when you go to upgrade, you may find yourself having to reinstall your ubuntu system. You will most likely have to force many dependencies like this, and each time you do it, it will overwrite your amd64 version libaries, and eventually we'll see you on the forums, or on irc with a "waah, my Ubuntu is broken, I did --force-architecture to install package foo, and now I can't do bar"

---

