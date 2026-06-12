---
title: "newbie MOL works with Tiger?"
date: 2005-12-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by macki on 2005-12-28
Ive been doing the steps of the mol wiki installation, but cant run mol :( somewhere I read that Mac OS X Tiger doesnt work with the ubuntu-ppc mol version

is this true? how could I make it work?

thanks :)

---

### Post by felix_stegerman on 2005-12-28
I haven't used MOL on Ubuntu, and never tried MOL with Tiger on Debian, but you should be able to find what you need on:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=328826](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=328826)

Felix

---

### Post by MonolithTMA on 2005-12-28
I never even tried with Tiger, as I had read that it didn't work. I installed Panther on a partition and MoL works fine.

---

### Post by Rob_Frohne on 2006-01-02
Hi,

I just added some notes to the wiki on installing the latest version of MOL to run Tiger.  It is working for me except that I'm still working on some networking problems.

Rob

---

### Post by tmeier on 2006-01-04
I have been trying to get the workaround that Rob had posted from the Wiki on MOL and have run into a snag at the Make command.  here is what I get

<code>
+ Entering lxdialog
    Compiling    checklist.o
cc1: note: obsolete option -I- used, please use -iquote instead
In file included from checklist.c:24:
./dialog.h:29:20: error: curses.h: No such file or directory
In file included from checklist.c:24:
./dialog.h:127: error: syntax error before &#8216;use_colors&#8217;
Any ideas on this would be greatly appreciated.  I don't mind having to revert back to 10.3 to make it work, but if I don't have to that is good also.  Thanks

---

### Post by tmeier on 2006-01-05
Did a search for curses.h on the forums and found that I needed to install from synaptic libncurses5-dev.  I was then able to move on.  Still working on it.  I sure hope it works.

---

### Post by tmeier on 2006-01-05
I got it working.  It is nice to be able run both and not have one affect the other.  Thanks to Rob for putting the information together, this is great.

---

### Post by dombleu on 2006-01-06
It works fine on my side too.... only a little thing:

Since i'm using a powerbook with NVidia video, is there anything to do to get full screen, in X or in console? 

Dom

---

### Post by bawalker on 2006-11-23
Well I wanted to drop a note in here that after several days of work, research, and hard work, I was able to get MacOnLinux 0.9.70-2 installed on a copy of Ubuntu 6.06 by using the default MOL version on the repository servers.  However I was still unable to compile it from source.

Today I reinstalled Ubuntu 6.10 and proceeded to do the critical updates first.  From there I got the appropriate packages I was missing, namely M4, autoconf, xlibs and many others.  This time around, when I do a 'make' command in the MOL 0.9.72_pre1 (AND) 0.9.71.1 versions, everything compiles except I get an error at the very end of the compile regarding the USBDEV.o file.  For the life of me I can't figure out if I'm missing another package or if this regards something in the kernel that needs to be recompiled...??

<much more above this>
cc1: note: obsolete option -I- used, please use -iquote instead
    Compiling    console.o           
cc1: note: obsolete option -I- used, please use -iquote instead
    Compiling    usbdev.o            
cc1: note: obsolete option -I- used, please use -iquote instead
usbdev.c:26:75: error: linux/compiler.h: No such file or directory
make[2]: *** [../../obj-ppc/build/src/drivers/usbdev.o] Error 1
make[1]: *** [sub-drivers-all] Error 2
make: *** [sub-src-all] Error 2
root@UbuntuPPC:/home/bawalker/Desktop/mol-0.9.72_pre1# 


Does anyone have any ideas as to what is causing the USBDEV.o file to throw out that error?  When doing the initial make command, I got a menuconfig screen that I could disable Generic USB support, but when I do that, I get the following:


<more above this>
cc1: note: obsolete option -I- used, please use -iquote instead
    Linking      libxkeyremap.a        
    Compiling    init.o              
cc1: note: obsolete option -I- used, please use -iquote instead
cc1: note: obsolete option -I- used, please use -iquote instead
../../obj-ppc/build/src/molelf/libxselftest.a(selftest.o): In function `entry':
/home/bawalker/Desktop/mol-0.9.72_pre1/src/molelf/selftest.c:115: undefined reference to `__stack_chk_fail'
../../obj-ppc/build/src/molelf/libxselftest.a(vsprintf.o): In function `number':
/home/bawalker/Desktop/mol-0.9.72_pre1/src/molelf/vsprintf.c:120: undefined reference to `__stack_chk_fail'
../../obj-ppc/build/src/molelf/libxselftest.a(vsprintf.o): In function `printm':
/home/bawalker/Desktop/mol-0.9.72_pre1/src/molelf/vsprintf.c:334: undefined reference to `__stack_chk_fail'
make[2]: *** [../../obj-ppc/build/src/molelf/selftest] Error 1
make[1]: *** [sub-molelf-all] Error 2
make: *** [sub-src-all] Error 2
root@UbuntuPPC:/home/bawalker/Desktop/mol-0.9.72_pre1# 


Does anyone have any remote idea what is causing this??

Brad

---

