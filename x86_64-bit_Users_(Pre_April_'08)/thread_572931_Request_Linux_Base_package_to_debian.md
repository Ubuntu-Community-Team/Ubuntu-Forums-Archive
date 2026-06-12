---
title: "Request: Linux Base package to debian"
date: 2007-10-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by lonrot on 2007-10-11
I need to install a network driver (I don't have internet), however it has been a nightmare, and I haven't been able to install it, too much codes I don't understand, I'm pretty new to Linux or Ubuntu.

The package is this one:
Intel 82566 Gigabit Network Driver
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2775&DwnldID=9180&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2775&DwnldID=9180&strOSs=39&OSFullName=Linux*&lang=eng)

This is what I have tried to install the package so far:
```
lonrot@lonrot-desktop:~$ cd e1000-7.6.5
lonrot@lonrot-desktop:~/e1000-7.6.5$ ./configure
bash: ./configure: No such file or directory
lonrot@lonrot-desktop:~/e1000-7.6.5$ make
make: *** No targets specified and no makefile found.  Stop.
lonrot@lonrot-desktop:~/e1000-7.6.5$ make dos.rpm
make: *** No rule to make target `dos.rpm'.  Stop.
lonrot@lonrot-desktop:~/e1000-7.6.5$ makefile
bash: makefile: command not found
lonrot@lonrot-desktop:~/e1000-7.6.5$ sudo alien -i 
Password:
sudo: alien: command not found
lonrot@lonrot-desktop:~/e1000-7.6.5$ make install
make: *** No rule to make target `install'.  Stop.
lonrot@lonrot-desktop:~/e1000-7.6.5$ make install e1000.7
make: *** No rule to make target `install'.  Stop.
lonrot@lonrot-desktop:~/e1000-7.6.5$ 

```


Please, convert it for me, for some people I suppose this is a breeze.
It's so difficult to learn using Ubuntu if I don't have internet!

---

### Post by theonlyrealperson on 2007-10-11
Ah, you are in a difficult catch-22...

You can't "make" or "make install" any packages until you install the build-essential packages... But you need the internet to do that.

Maybe someone can help you install build-essential by burning it on to a CD... 

I'm sorry, I can't - but I'm pretty sure that is what is going on.

Sorry!

---

### Post by lonrot on 2007-10-11
I already have the build-essential packages...

---

### Post by lonrot on 2007-10-11
Help please! Is it really so hard?

---

### Post by steveneddy on 2007-10-11
Is this a 64 bit package? 

Did you un tar the package?

What does the read me file say?

Sorry - no linux at work or I would look at it closer to try to help more.

---

### Post by John.Michael.Kane on 2007-10-11
> **lonrot said:**
> I need to install a network driver (I don't have internet), however it has been a nightmare, and I haven't been able to install it, too much codes I don't understand, I'm pretty new to Linux or Ubuntu.

The package is this one:
Intel 82566 Gigabit Network Driver
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2775&DwnldID=9180&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2775&DwnldID=9180&strOSs=39&OSFullName=Linux*&lang=eng)

This is what I have tried to install the package so far:
```
lonrot@lonrot-desktop:~$ cd e1000-7.6.5
lonrot@lonrot-desktop:~/e1000-7.6.5$ ./configure
bash: ./configure: No such file or directory
lonrot@lonrot-desktop:~/e1000-7.6.5$ make
make: *** No targets specified and no makefile found.  Stop.
lonrot@lonrot-desktop:~/e1000-7.6.5$ make dos.rpm
make: *** No rule to make target `dos.rpm'.  Stop.
lonrot@lonrot-desktop:~/e1000-7.6.5$ makefile
bash: makefile: command not found
lonrot@lonrot-desktop:~/e1000-7.6.5$ sudo alien -i 
Password:
sudo: alien: command not found
lonrot@lonrot-desktop:~/e1000-7.6.5$ make install
make: *** No rule to make target `install'.  Stop.
lonrot@lonrot-desktop:~/e1000-7.6.5$ make install e1000.7
make: *** No rule to make target `install'.  Stop.
lonrot@lonrot-desktop:~/e1000-7.6.5$ 

```


Please, convert it for me, for some people I suppose this is a breeze.
It's so difficult to learn using Ubuntu if I don't have internet!

You can't compile cause you are not in the right directory
The readme file clearly states.
1. Move the base driver tar file to the directory of your choice.
example, use /home/username/e1000 or /usr/local/src/e1000. 

2. Untar/unzip archive:
tar zxf e1000-x.x.x.tar.gz

3. Change to the driver src directory: in your case the file is on your desktop
cd Desktop/e1000-x.x.x/src/ This is where your mistake is. 
look at where your trying to compile the file, As you can see you are not in the proper directory. **lonrot@lonrot-desktop:~/e1000-7.6.5$**

Also what version of Ubuntu are you using that requires you to compile a driver?

Have you tried Feisty or Gutsy?

---

### Post by lonrot on 2007-10-11
My version Ubuntu x64 7.04
I don't know if that package is set for x64 architecture but that's the only package I found.
Could the alternative cd contain the drivers ready to be installed for me?

---

### Post by jocko on 2007-10-11
> **lonrot said:**
> My version Ubuntu x64 7.04
I don't know if that package is set for x64 architecture but that's the only package I found.
Could the alternative cd contain the drivers ready to be installed for me?

How did you come to the conclusion that you need to install the driver?
As far as I know, "e1000" should be included in the kernel already.

---

### Post by lonrot on 2007-10-12
e1000-7.6.5, then why I'm offline?

I have tried Ubuntu before, in amd and I never needed to setup anything.
But for this one s its quite different, even in Windows I had to install network drivers in order to get online.
The intel network chipset is:
Intel 82566 Gigabit

Any other suggestion, or should move to another easier Linux Distro?

---

### Post by jocko on 2007-10-12
Ok, you could of course be right that the current e1000 module in feisty does not support your card (some posts on this forum seem to indicate that, but I'm not sure).
Have you really read the readme file that comes with the drivers (in your first post you just seem to throw random commands)?
In it, it say what you need to do (I'll explain):

1. Unpack the downloaded .tar.gz in your home directory (right click--> extract here. You have already done this)
2. In a terminal, change to the e1000-7.6.9/src directory:
```
cd ~/e1000-7.6.9/src
```3. Run this command to install:
```
sudo make install
```4. Load the module:
```
sudo modprobe e1000
```That's it. If the "make install" command doesn't work you'll need to install build-essential and the linux-headers-package for your kernel.

And chances are if support for your nic is missing in feisty, it has hopefully been added in gutsy, which should be officially released on Oct. 18:th.

---

### Post by Jouke74 on 2007-10-12
A small addition: You can get both the Linux headers as well as the Build essential package from the CD that you installed Ubuntu with. Just put the CD in the drive and then run Synaptic. No need for internet as implied earlier. The headers are installed already by the way.

---

### Post by lonrot on 2007-10-12
jocko thank you so much!
It worked perfectly fine, I'm typing through Ubuntu right now. :lolflag:

---

