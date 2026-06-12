---
title: "how to find for i386 packages on 64 bit system"
date: 2008-01-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by tenmoi on 2008-01-29
Hello everyone!

I am back again to the Ubuntu world after two weeks. At last I can install Ubuntu 64 bit. 
And for the past two weeks I have lived in Fedora world. And  I don't know if Ubuntu has a way to find out if there are any i386 packages on a 64 bit system as in fedora "rpm -qa | grep i386". I just want a pure 64 bit system.

Thanx for your help.:guitar:

---

### Post by Kilz on 2008-01-29
> **tenmoi said:**
> Hello everyone!

I am back again to the Ubuntu world after two weeks. At last I can install Ubuntu 64 bit. 
And for the past two weeks I have lived in Fedora world. And  I don't know if Ubuntu has a way to find out if there are any i386 packages on a 64 bit system as in fedora "rpm -qa | grep i386". I just want a pure 64 bit system.

Thanx for your help.:guitar:

Ubuntu is a pure 64bit install, but you can install 32bit applications if you cant find them in 64bit. This is uncommon but possible. [You will want to look at this thread if you have to.]("http://ubuntuforums.org/showthread.php?t=474790")

---

### Post by tenmoi on 2008-01-29
Thank you!

So Ubuntu does not include 32 bit packages in its clean 64 bit install? THat's great news. YOu know things are different with Fedora, where you will find lots of 32 bit packages (over 100 or so) on a clean install. That was why I was suspicious at first. Again thanks!

Anyway, if there Should exist a way to find out, please tell me.:)

---

### Post by utUtu on 2008-01-29
> **tenmoi said:**
> Hello everyone!

I am back again to the Ubuntu world after two weeks. At last I can install Ubuntu 64 bit. 
And for the past two weeks I have lived in Fedora world. And  I don't know if Ubuntu has a way to find out if there are any i386 packages on a 64 bit system as in fedora "rpm -qa | grep i386". I just want a pure 64 bit system.

Thanx for your help.:guitar:

If you want a pure 64bit, you have to compile everything yourself.  And before you compile, make sure all variable definitions are 64bit.  I could define some as int8 or int16 or int32 and still compile in 64bit.

---

### Post by Perfect Storm on 2008-01-29
If you come across on an application/game/whatever that only run 32-bit, say a game in your home folder. you simple;

cd <into where the binary is>
ldd <binary>

It tells you which libs it needs to run it.
Then with help of getlibs you can grab the libs you need. *IF* The application/game needs a specific libs name you have to make a symblink.

---

### Post by Cappy on 2008-01-29
> **Artificial Intelligence said:**
> If you come across on an application/game/whatever that only run 32-bit, say a game in your home folder. you simple;

cd <into where the binary is>
ldd <binary>

It tells you which libs it needs to run it.
Then with help of getlibs you can grab the libs you need. *IF* The application/game needs a specific libs name you have to make a symblink.

You can use getlibs with a syntax such as
```
getlibs Desktop/unzipped/program
```
and it will find the needed libraries. Getlibs uses ldd inside the script.

---

### Post by tenmoi on 2008-01-29
Thanx all! but what i really meant was how to REMOVE 32 bit packages on a 64 bit Ubuntu. The title is misleading, sorry.

---

### Post by Kilz on 2008-01-29
> **tenmoi said:**
> Thanx all! but what i really meant was how to REMOVE 32 bit packages on a 64 bit Ubuntu. The title is misleading, sorry.

That isnt necessary as none exist in the standard 64bit Ubuntu install. You would have to install them (32bit packages and applications) yourself. There are none in the standard install.

To my knowledge, 32bit things in the repositories you could install are.
Any package with ia32 in its title (these are mostly libraries to make installing 32bit applications and games easier if the user wants to install them)
flashplugin-nonfree (this is the 32bit macromedia plugin that is wrapped so your 64bit browser can use it)

---

### Post by tenmoi on 2008-01-30
Thanx Kilz!

And one more question. Are the codecs  installed sort of automatically by Totem 64 bit?  I am just curious b/c Vlc can handle almost all media files and it is 64 bit.:guitar:

---

