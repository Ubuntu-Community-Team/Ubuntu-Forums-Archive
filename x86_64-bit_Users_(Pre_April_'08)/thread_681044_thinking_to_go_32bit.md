---
title: "thinking to go 32bit?"
date: 2008-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by windows-killer on 2008-01-28
Am using a 64bit version Ubuntu 7.10 and I was wondering whats the difference in terms of Performance, will the 32bit run slower than 64bit?
Also what about graphics? will compiz fusion run well on 32Bit?
there are many programs designed for 32bit ubuntu but not for 64bit so thats my main reason to switch.
Is there a backward compatibility to use 32 bit programs on 64 bit OS?
I have an AMD64 processor, will that work on 32 bit ubuntu

---

### Post by KhaaL on 2008-01-28
that's a lot of questions in one post :)

Yes, a 32-bit applications and the OS *will* run slower, which will notice when you will encode media or render advanced scenes (or use other number-crunching applications).
Compiz runs well on 32-bit here
AMD64 CPU works well with a 32-bit ubuntu.
And you can use 32-bit applications on a 64-bit OS without performance loss, so you don't have a reason to switch really...

---

### Post by Kilz on 2008-01-28
> **windows-killer said:**
> Am using a 64bit version Ubuntu 7.10 and I was wondering whats the difference in terms of Performance, will the 32bit run slower than 64bit?
**Also what about graphics? will compiz fusion run well on 32Bit?**
there are many programs designed for 32bit ubuntu but not for 64bit so thats my main reason to switch.
Is there a backward compatibility to use 32 bit programs on 64 bit OS?
I have an AMD64 processor, will that work on 32 bit ubuntu

If you are thinking that all you have to do is switch to 32bit and all your problems will vanish, dont even think it. There is no such animal as a linux install that doesnt require some setup.
Compiz can be a major problem no matter what version you run, do a search for compiz, tons of the results will be in areas other that the 64bit version.
There is no difference in the number of packages in the 32bit and 64bit repositories. You can run 32bit applications on 64bit.
There is a learning curve when switching operating systems. Changing the bit of the os will not make problems go away.

---

### Post by windows-killer on 2008-01-29
Thanks for the reply guys.
How can I make 32bit applications run on a 64bit OS?

---

### Post by Kilz on 2008-01-29
> **windows-killer said:**
> Thanks for the reply guys.
How can I make 32bit applications run on a 64bit OS?

The procedure is simple, force install them then run getlibs. [Go here for Getlibs]("http://ubuntuforums.org/showthread.php?t=474790") and exact instructions. Getlibs installs libraries, you can not force install libraries.

---

### Post by Perfect Storm on 2008-01-29
For games check my signature (you can also make a request if needed).
Most newer games are 64-bit supported, those there are not, are easely solved with ia32-libs + getlibs

---

### Post by windows-killer on 2008-01-30
once again thanks.
Now I got another problem. Am trying to convert 32bit packages to 64bit by typing"--build:" on the command line along with the file I want to convert. For example am trying to install a program called "checkinstall" to convert packages to .deb format, but am unable to convert it.

on command I type: --build:checkinstall.deb 

but then I get an error message saying package not found Or invalid package.

please help me am very glad with my ubuntu and I never look back at windows.

---

### Post by Cappy on 2008-01-30
If you wanted checkinstall you only need to
```
sudo apt-get install checkinstall
```
or use Synaptic (System-->Administration-->Synaptic Package Manger).

There isn't any need to use a 32-bit package.

As for getlibs --build .. it's very beta and I don't recommend you test it.

What you want to do is ```
sudo dpkg -i --force-all whatever.deb
```
if it is a PROGRAM. Use getlibs for LIBRARIES.

If after you install the program use the getlibs instructions
```
getlibs /path/to/program
```
or
```
getlibs -l missinglibrary.so.2
```
for instance.

---

