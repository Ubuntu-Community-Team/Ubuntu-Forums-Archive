---
title: "[SOLVED] CODE::BLOCKS... wont start..."
date: 2008-06-22
forum: x86 64-bit Users
---

### Post by saidinesh5 on 2008-06-22
guys , Ive recently installed Hardy on my AMD64 desktop..n i am still a n00b when it comes to linux....i ve installed CODE::BLOCKS (via synaptic) on my PC and when i select it from the APPLICATIONS menu , it says starting code::blocks for some time and after that it disappears....
when i type codeblocks on terminal , this is what i get...

dinesh@dinesh-desktop:~$ codeblocks
codeblocks: error while loading shared libraries: libwx_gtk2u_richtext-2.8.so.0: cannot open shared object file: No such file or directory


so here i am waiting for your help....

---

### Post by Cappy on 2008-06-22
Install libwxgtk2.8-0

If that doesn't work install getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
and try
```
sudo getlibs -p libwxgtk2.8-0
```

---

### Post by saidinesh5 on 2008-06-22
dude 1st i ve downloaded getlibs-all.deb from the link you gave,
and then this is wht i ve done in terminal...

dinesh@dinesh-desktop:~$ sudo getlibs -p libwxgtk2.8-0
The following i386 packages will be installed: libwxgtk2.8-0
Continue [Y/n]? y
Downloading ...
Installing libraries ...

dinesh@dinesh-desktop:~$ codeblocks
codeblocks: error while loading shared libraries: libwx_gtk2u_richtext-2.8.so.0: cannot open shared object file: No such file or directory

so same error again...can you help me out again?n yes, i thought synaptic already checks for and installs all the libraries needed for the installation of any program , wont it?

---

### Post by tenmoi on 2008-06-22
Open synaptics - search "libwxgtk2.8-0" and install it. 

You are running 64 bit why bother installing a 32 bit library package for a 64 bit programme?

Remember to COMPLETELY remove the 32 bit library first (Mark for complete removal).

---

### Post by saidinesh5 on 2008-06-22
thnk you guys, problem solved...i was actually searching for libex_gtk...lolz........

---

### Post by zirtik on 2009-02-12
Hey Tenmoi, thanks a lot. That solved my problem on a 64-bit Hardy.

---

### Post by asuastrophysics on 2009-11-11
> **Cappy said:**
> Install libwxgtk2.8-0

If that doesn't work install getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
and try
```
sudo getlibs -p libwxgtk2.8-0
```

Neither of these 2 steps worked. I tried both getlib and this:

```
jake@jake-laptop:~$ sudo apt-get install libwxgtk2.8-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libwxgtk2.8-0 is already the newest version.

```

fantastic. 

I even compiled it. didn't work. failed on "make"
As far as I'm concerned code::blocks is broken, unusable. If they can't make a decent DEB package for a 64 bit OS or have it compile without error (w/ all dependencies met), then it's not worth installing.

---

