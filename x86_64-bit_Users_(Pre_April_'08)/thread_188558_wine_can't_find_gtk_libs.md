---
title: "wine can't find gtk libs"
date: 2006-06-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by thelost on 2006-06-04
I recently installed ubuntu for the first time, and wine as well. I'm a  newb looking to switch and I've had fun so far, but I've reached a brick wall.

I installed winetools as per instructions found somewhere in this forum,  but when I try to run it the program fails as it can't find the gtk libraries. I do have them in /usr/lib I've checked. I've edited the ld.so.conf to include all the paths I could possibly have libraries in and it's made no difference. I've tried using the LD_LIBRARY_PATH in conjunction with launching wt, no avail.

I'm quite sure I'm missing something obvious as I am out of my element at the moment being new to all this. So what am I missing?

---

### Post by Kilz on 2006-06-04
[QUOTE=thelost]I recently installed ubuntu for the first time, and wine as well. I'm a  newb looking to switch and I've had fun so far, but I've reached a brick wall.

I installed winetools as per instructions found somewhere in this forum,  but when I try to run it the program fails as it can't find the gtk libraries. I do have them in /usr/lib I've checked. I've edited the ld.so.conf to include all the paths I could possibly have libraries in and it's made no difference. I've tried using the LD_LIBRARY_PATH in conjunction with launching wt, no avail.

I'm quite sure I'm missing something obvious as I am out of my element at the moment being new to all this. So what am I missing?[/QUOTE]

I bet winetools like wine is a 32 bit application. You may have to manualy add any lib's it needs to lib32. [Here is a good place to find those lib's.]("http://packages.ubuntu.com/")

---

### Post by thelost on 2006-06-04
[QUOTE=Kilz]I bet winetools like wine is a 32 bit application. You may have to manualy add any lib's it needs to lib32. [Here is a good place to find those lib's.]("http://packages.ubuntu.com/")[/QUOTE]

I've checked /usr/lib32 (i assume this where they go and libgtk2.0 is in there). there are libgtk1.2 files in /usr/lib. 

I literally installed dapper 2 days ago and this is my first go so yeah, at sea without a padel ;)

I think I have all the necessary libraries, so i can't imagine what else it could be. anyone?

---

### Post by Jiilik on 2006-06-04
from a console, type:
```
ldd `which wine`
```
and paste the output - that'll tell us exactly what's missing...

(note: those are back-quotes, the one on the ~ key....)

---

### Post by Jiilik on 2006-06-04
dupe

---

### Post by Jiilik on 2006-06-04
dupe

---

### Post by thelost on 2006-06-04
> 
        linux-gate.so.1 =>  (0xffffe000)
        libwine.so.1 => /usr/lib/libwine.so.1 (0x5557d000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0x55597000)
        libc.so.6 => /lib32/libc.so.6 (0x555aa000)
        libdl.so.2 => /lib32/libdl.so.2 (0x556d9000)
        /lib/ld-linux.so.2 (0x55555000)

        linux-gate.so.1 =>  (0xffffe000)
        libwine.so.1 => /usr/lib/libwine.so.1 (0x5557d000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0x55597000)
        libc.so.6 => /lib32/libc.so.6 (0x555aa000)
        libdl.so.2 => /lib32/libdl.so.2 (0x556d9000)
        /lib/ld-linux.so.2 (0x55555000)


this is the output I get.

---

### Post by Jiilik on 2006-06-04
Well, wine is definitely 32bit... that output didn't show anything missing - but try 
```
ldd /usr/lib/libwine.so.1
```
and see what that does for you as well...

---

### Post by thelost on 2006-06-04
linux-gate.so.1 =>  (0xffffe000)
        libdl.so.2 => /lib32/libdl.so.2 (0x55583000)
        libc.so.6 => /lib32/libc.so.6 (0x55586000)
        /lib/ld-linux.so.2 (0x56555000)

if it's helpful, when i run winetools I get this output:

> 
$ wt
detecting Wine version... done.
Drive C: is /home/nemof/.wine/drive_c
Wine 0.9.14
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0.9.14".
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Calls to wine are executed as  "wine".
Config is /home/nemof/.wine/winetools.log.
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


---

### Post by Jiilik on 2006-06-04
Try installing ia32-libs-gtk

Let me know if that changes anything...

---

### Post by flapane on 2006-06-05
[QUOTE=thelost]I recently installed ubuntu for the first time, and wine as well. I'm a  newb looking to switch and I've had fun so far, but I've reached a brick wall.

I installed winetools as per instructions found somewhere in this forum,  but when I try to run it the program fails as it can't find the gtk libraries. I do have them in /usr/lib I've checked. I've edited the ld.so.conf to include all the paths I could possibly have libraries in and it's made no difference. I've tried using the LD_LIBRARY_PATH in conjunction with launching wt, no avail.

I'm quite sure I'm missing something obvious as I am out of my element at the moment being new to all this. So what am I missing?[/QUOTE]

hi
please could you tell me how did you install wine on amd64?
wine isn't on dapper 64bit repos..

---

### Post by Kilz on 2006-06-05
[QUOTE=flapane]hi
please could you tell me how did you install wine on amd64?
wine isn't on dapper 64bit repos..[/QUOTE]

There are a few ways of getting wine to work. [I made a short howto not long ago.]("http://www.ubuntuforums.org/showthread.php?t=185557&highlight=wine+64")

---

### Post by flapane on 2006-06-05
thanks, it went;)

---

### Post by hannesz112 on 2006-06-14
HI 

I'm also trying to start winetools but also get de libgtk error message, en it seems i can't get ride of the error. Can someone help me with this problem and what to do?

this is the error message

```
no suitable Wine directory found...
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Wine 0.9.15
wine is executed as wine
Parameters are --noexit
Wine is not configured yet!
Browser is /usr/bin/firefox.
WINEVER is "0.9.15".
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Calls to wine are executed as  "wine".
Config is /home/johannes/.wine/winetools.log.
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```

thnx

---

### Post by Kilz on 2006-06-14
[QUOTE=hannesz112]HI 

I'm also trying to start winetools but also get de libgtk error message, en it seems i can't get ride of the error. Can someone help me with this problem and what to do?

this is the error message

```
no suitable Wine directory found...
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Wine 0.9.15
wine is executed as wine
Parameters are --noexit
Wine is not configured yet!
Browser is /usr/bin/firefox.
WINEVER is "0.9.15".
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Calls to wine are executed as  "wine".
Config is /home/johannes/.wine/winetools.log.
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```

thnx[/QUOTE]
It seems to be a wine tools problem. just courious. What is winetools used for?

---

### Post by hannesz112 on 2006-06-14
[QUOTE=Kilz]It seems to be a wine tools problem. just courious. What is winetools used for?[/QUOTE]

It's a easy tools for installing the windows apps, but i have to solve the problem before i can use it. 

So please help me

---

### Post by Kilz on 2006-06-14
[QUOTE=hannesz112]It's a easy tools for installing the windows apps, but i have to solve the problem before i can use it. 

So please help me[/QUOTE]
Thanks, I looked at the web site after you told me what its for. I also looked at the applications its supposed to install. There were a few applications on the list I already had installed like IE. But I do use sidenet to set up wine so maybe that's why I am not having problems.

---

### Post by hannesz112 on 2006-06-14
[QUOTE=Kilz]Thanks, I looked at the web site after you told me what its for. I also looked at the applications its supposed to install. There were a few applications on the list I already had installed like IE. But I do use sidenet to set up wine so maybe that's why I am not having problems.[/QUOTE]


thnx i wil give it a try :D

---

