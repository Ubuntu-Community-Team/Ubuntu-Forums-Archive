---
title: "Wacom Intuos 4 on most recent Ubuntu version, in 64 bit"
date: 2009-10-07
forum: x86 64-bit Users
---

### Post by L-hibou on 2009-10-07
I have been following various tutorials on doing this only to get nowhere.

I'm not sure if my haing a 64 bit setup is conflicting with its installation or what.  I had removed Ubuntu from my computer completely a while back and finally decided to come back to it and try it again. However, I and VERY new, so I'd appreciate step by step help, (help that's pretty "dumbed down" would be best, like what to click and select and type, move, stuff like that...).  Only way I can learn. =]

So if anyone can help me, please do, I'd appreciate help in this matter.

---

### Post by Favux on 2009-10-07
Hi L-hibou,

It's not a 64-bit problem.  The problem is the Intuos4 was new enough that the default linuxwacom drivers in Jaunty (9.04) don't support usb communications with the tablet.  To fix things read over post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)  Then follow the links.

Hope this helps.

Good luck!

---

### Post by L-hibou on 2009-10-07
I'm sorry; I've read through all those threads (all the pages in them) earlier, and all the links in them entirely, and I am still completely lost. It seems to speak of "moving" something but I really don't know how, the instructions there are too advanced for me.  

I think i need something put in simpler terms for me to understand...

Thank you for your response though. =]

---

### Post by Favux on 2009-10-07
OK.  To get a terminal go to Applications>Accessories>Terminal.  It should pop up.  Then when the instructions say to enter or type a command into the terminal just copy and paste the command into the terminal that popped up, one line at a time, and hit enter(return).

---

### Post by L-hibou on 2009-10-07
Okay, I tried this over, and I get stuck at "xsetwacom list"  This does nothing in the Terminal. =\  What could I have done wrong?

---

### Post by Favux on 2009-10-07
No sounds like you did it right.  A blank output is what you would expect with the default 10-wacom.fdi.  To see what HAL is calling things enter "xinput --list" in the terminal.  Remember you won't see your wacom devices yet.  You still have the default 0.8.2-2 wacom.ko (the usb kernel driver/module) that doesn't communicate with your tablet.

---

### Post by L-hibou on 2009-10-07
I did all this and then I got a problem at the bottom:


Says it couldn't find package. Did I do that right?

Nevermind. Copied it again and it went through...
I'll respond when if I get another problem.
Edit: Bleh, next step gave me the error:

```
rebecca@ubuntu:~/Desktop$ tar xjvf linuxwacom-0.8.4-2.tar.bz
tar: linuxwacom-0.8.4-2.tar.bz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
rebecca@ubuntu:~/Desktop$ 

```

This part

I tried extracting it, and I got this:

```
rebecca@ubuntu:~/Desktop$ rebecca@ubuntu:~/Desktop$ tar xjvf linuxwacom-0.8.4-2.tar.bz
bash: rebecca@ubuntu:~/Desktop$: No such file or directory
rebecca@ubuntu:~/Desktop$ tar: linuxwacom-0.8.4-2.tar.bz: Cannot open: No such file or directory
bash: tar:: command not found
rebecca@ubuntu:~/Desktop$ tar: Error is not recoverable: exiting now
bash: tar:: command not found
rebecca@ubuntu:~/Desktop$ tar: Child returned status 2
bash: tar:: command not found
rebecca@ubuntu:~/Desktop$ tar: Error exit delayed from previous errors
bash: tar:: command not found
rebecca@ubuntu:~/Desktop$ rebecca@ubuntu:~/Desktop$ 
bash: rebecca@ubuntu:~/Desktop$: No such file or directory
rebecca@ubuntu:~/Desktop$ 


```


EDIT: Nevermind, I copied everything again and I just got through the steps [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949) in section one. Must have had an incomplete copy or a typo of something...
What should I do next? I'm sort of confused as to what to do now...

Edit - I grabbed the wrong link.

---

### Post by Favux on 2009-10-07
Do you see "linuxwacom-0.8.4-2.tar.bz2" on your Desktop?  It should look like a box.  I just checked at LWP and it's there.  But the server is slow.

---

### Post by L-hibou on 2009-10-07
Yes, I have that there.

---

### Post by Favux on 2009-10-07
Alright, since you see it on the Desktop, my guess is that you somehow changed directories.  Enter in the terminal:
```
cd ./Desktop
```
and try the command to unpack the tar again.

---

### Post by L-hibou on 2009-10-07
I think that's what happened. I copied everything over again and I managed to get through to the end of that one part.  The computer still doesn't recognize my tablet yet. What would be the next step after this:

```

             xidump - yes 
        libwacomcfg - yes
         libwacomxi - yes
          xsetwacom - yes
              hid.o - no 
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - Uninit-called IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------
rebecca@ubuntu:~/Desktop/linuxwacom-0.8.4-2$ make
Making all in src
make[1]: Entering directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src'
Making all in .
make[2]: Entering directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src'
rm -f wacom.4x.gz
gzip -9c < ./wacom.4x > wacom.4x.gz
make[2]: Leaving directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src'
Making all in wacomxi
make[2]: Entering directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/wacomxi'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacomxi.lo -MD -MP -MF .deps/wacomxi.Tpo -c -o wacomxi.lo wacomxi.c
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I../../src/include -Wall -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacomxi.lo -MD -MP -MF .deps/wacomxi.Tpo -c wacomxi.c  -fPIC -DPIC -o .libs/wacomxi.o
 gcc -DHAVE_CONFIG_H -I. -I../../src/include -Wall -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacomxi.lo -MD -MP -MF .deps/wacomxi.Tpo -c wacomxi.c -o wacomxi.o >/dev/null 2>&1
mv -f .deps/wacomxi.Tpo .deps/wacomxi.Plo
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -no-undefined  -o libwacomxi.la -rpath /usr/lib/TkXInput wacomxi.lo -L/usr/lib -lX11 -lXi 
gcc -shared  .libs/wacomxi.o  -L/usr/lib -lX11 -lXi  -Wl,-soname -Wl,libwacomxi.so.0 -o .libs/libwacomxi.so.0.0.0
(cd .libs && rm -f libwacomxi.so.0 && ln -s libwacomxi.so.0.0.0 libwacomxi.so.0)
(cd .libs && rm -f libwacomxi.so && ln -s libwacomxi.so.0.0.0 libwacomxi.so)
ar cru .libs/libwacomxi.a  wacomxi.o
ranlib .libs/libwacomxi.a
creating libwacomxi.la
(cd .libs && rm -f libwacomxi.la && ln -s ../libwacomxi.la libwacomxi.la)
make[2]: Leaving directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/wacomxi'
Making all in util
make[2]: Entering directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/util'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg   -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c -o wacomcfg.lo wacomcfg.c
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I../../src/include -Wall -pedantic -I/usr/include/xorg -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c  -fPIC -DPIC -o .libs/wacomcfg.o
 gcc -DHAVE_CONFIG_H -I. -I../../src/include -Wall -pedantic -I/usr/include/xorg -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c -o wacomcfg.o >/dev/null 2>&1
mv -f .deps/wacomcfg.Tpo .deps/wacomcfg.Plo
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg   -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -no-undefined -version-info 0:1:0  -o libwacomcfg.la -rpath /usr/lib wacomcfg.lo -L/usr/lib -lX11 -lXi 
gcc -shared  .libs/wacomcfg.o  -L/usr/lib -lX11 -lXi  -Wl,-soname -Wl,libwacomcfg.so.0 -o .libs/libwacomcfg.so.0.0.1
(cd .libs && rm -f libwacomcfg.so.0 && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so.0)
(cd .libs && rm -f libwacomcfg.so && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so)
ar cru .libs/libwacomcfg.a  wacomcfg.o
ranlib .libs/libwacomcfg.a
creating libwacomcfg.la
(cd .libs && rm -f libwacomcfg.la && ln -s ../libwacomcfg.la libwacomcfg.la)
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg   -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacdump.o -MD -MP -MF .deps/wacdump.Tpo -c -o wacdump.o wacdump.c
mv -f .deps/wacdump.Tpo .deps/wacdump.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg   -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacscrn.o -MD -MP -MF .deps/wacscrn.Tpo -c -o wacscrn.o wacscrn.c
mv -f .deps/wacscrn.Tpo .deps/wacscrn.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg   -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wactablet.o -MD -MP -MF .deps/wactablet.Tpo -c -o wactablet.o wactablet.c
mv -f .deps/wactablet.Tpo .deps/wactablet.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg   -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacserial.o -MD -MP -MF .deps/wacserial.Tpo -c -o wacserial.o wacserial.c
wacserial.c: In function &#8216;WacomFlush&#8217;:
wacserial.c:1345: warning: ignoring return value of &#8216;read&#8217;, declared with attribute warn_unused_result
mv -f .deps/wacserial.Tpo .deps/wacserial.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg   -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wacusb.o -MD -MP -MF .deps/wacusb.Tpo -c -o wacusb.o wacusb.c
mv -f .deps/wacusb.Tpo .deps/wacusb.Po
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg   -g -O2 -D__amd64__ -I/usr/include/tcl8.4   -o wacdump wacdump.o wacscrn.o wactablet.o wacserial.o wacusb.o -lncurses 
gcc -Wall -pedantic -I/usr/include/xorg -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -o wacdump wacdump.o wacscrn.o wactablet.o wacserial.o wacusb.o  -lncurses  
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg   -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT xidump.o -MD -MP -MF .deps/xidump.Tpo -c -o xidump.o xidump.c
xidump.c: In function &#8216;main&#8217;:
xidump.c:1131: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
xidump.c:1135: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
mv -f .deps/xidump.Tpo .deps/xidump.Po
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg   -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -L/usr/lib -lX11 -lXi -lm  -o xidump xidump.o wacscrn.o -lncurses 
gcc -Wall -pedantic -I/usr/include/xorg -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -o xidump xidump.o wacscrn.o  -L/usr/lib -lX11 -lXi -lm -lncurses  
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg   -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT xsetwacom.o -MD -MP -MF .deps/xsetwacom.Tpo -c -o xsetwacom.o xsetwacom.c
mv -f .deps/xsetwacom.Tpo .deps/xsetwacom.Po
gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic -I/usr/include/xorg   -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -MT wcmAction.o -MD -MP -MF .deps/wcmAction.Tpo -c -o wcmAction.o wcmAction.c
mv -f .deps/wcmAction.Tpo .deps/wcmAction.Po
/bin/bash ../../libtool --tag=CC   --mode=link gcc -Wall -pedantic -I/usr/include/xorg   -g -O2 -D__amd64__ -I/usr/include/tcl8.4   -o xsetwacom xsetwacom.o wcmAction.o libwacomcfg.la 
gcc -Wall -pedantic -I/usr/include/xorg -g -O2 -D__amd64__ -I/usr/include/tcl8.4 -o .libs/xsetwacom xsetwacom.o wcmAction.o  ./.libs/libwacomcfg.so -L/usr/lib -lX11 -lXi 
creating xsetwacom
make[2]: Leaving directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/util'
Making all in xdrv
make[2]: Entering directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/xdrv'
gcc -MM -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -I../include -I/usr/include/xorg  -I/usr/include/xorg -I/usr/include/pixman-1   ./xf86Wacom.c ./wcmSerial.c ./wcmUSB.c ./wcmISDV4.c ./wcmXCommand.c ./wcmCommon.c ./wcmCompat.c ./wcmConfig.c ./wcmFilter.c ./wcmTilt2Rotation.c > .depend
make[2]: Leaving directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/xdrv'
make[2]: Entering directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/xdrv'
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  -I/usr/include/xorg -I/usr/include/pixman-1   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o xf86Wacom.o -c ./xf86Wacom.c
In file included from ./xf86Wacom.h:27,
                 from ./xf86Wacom.c:92:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./xf86Wacom.c:92:
./../include/xdrv-config.h:11:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./xf86Wacom.c:92:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./xf86Wacom.c:92:
./../include/xdrv-config.h:9:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  -I/usr/include/xorg -I/usr/include/pixman-1   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmSerial.o -c ./wcmSerial.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmSerial.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmSerial.c:20:
./../include/xdrv-config.h:11:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmSerial.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmSerial.c:20:
./../include/xdrv-config.h:9:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  -I/usr/include/xorg -I/usr/include/pixman-1   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmUSB.o -c ./wcmUSB.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmUSB.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmUSB.c:20:
./../include/xdrv-config.h:11:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmUSB.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmUSB.c:20:
./../include/xdrv-config.h:9:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  -I/usr/include/xorg -I/usr/include/pixman-1   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmISDV4.o -c ./wcmISDV4.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmISDV4.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmISDV4.c:20:
./../include/xdrv-config.h:11:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmISDV4.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmISDV4.c:20:
./../include/xdrv-config.h:9:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  -I/usr/include/xorg -I/usr/include/pixman-1   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmXCommand.o -c ./wcmXCommand.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmXCommand.c:32:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmXCommand.c:32:
./../include/xdrv-config.h:11:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmXCommand.c:32:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmXCommand.c:32:
./../include/xdrv-config.h:9:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  -I/usr/include/xorg -I/usr/include/pixman-1   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmCommon.o -c ./wcmCommon.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmCommon.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmCommon.c:20:
./../include/xdrv-config.h:11:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmCommon.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmCommon.c:20:
./../include/xdrv-config.h:9:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  -I/usr/include/xorg -I/usr/include/pixman-1   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmCompat.o -c ./wcmCompat.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmCompat.c:19:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmCompat.c:19:
./../include/xdrv-config.h:11:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmCompat.c:19:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmCompat.c:19:
./../include/xdrv-config.h:9:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  -I/usr/include/xorg -I/usr/include/pixman-1   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmConfig.o -c ./wcmConfig.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmConfig.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmConfig.c:20:
./../include/xdrv-config.h:11:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmConfig.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmConfig.c:20:
./../include/xdrv-config.h:9:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  -I/usr/include/xorg -I/usr/include/pixman-1   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmFilter.o -c ./wcmFilter.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmFilter.h:23,
                 from ./wcmFilter.c:20:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmFilter.h:23,
                 from ./wcmFilter.c:20:
./../include/xdrv-config.h:11:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmFilter.h:23,
                 from ./wcmFilter.c:20:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmFilter.h:23,
                 from ./wcmFilter.c:20:
./../include/xdrv-config.h:9:1: warning: this is the location of the previous definition
gcc -g -O2 -D__amd64__ -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  -I/usr/include/xorg -I/usr/include/pixman-1   \
		-D_XSERVER64 -I/usr/include/xorg -I/usr/include/pixman-1   \
		-o wcmTilt2Rotation.o -c ./wcmTilt2Rotation.c
In file included from ./xf86Wacom.h:27,
                 from ./wcmTilt2Rotation.c:19:
/usr/include/xorg/xorg-server.h:105:1: warning: "XKB" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmTilt2Rotation.c:19:
./../include/xdrv-config.h:11:1: warning: this is the location of the previous definition
In file included from ./xf86Wacom.h:27,
                 from ./wcmTilt2Rotation.c:19:
/usr/include/xorg/xorg-server.h:195:1: warning: "XFree86LOADER" redefined
In file included from ./xf86Wacom.h:25,
                 from ./wcmTilt2Rotation.c:19:
./../include/xdrv-config.h:9:1: warning: this is the location of the previous definition
gcc -shared -nostdlib -o wacom_drv.so xf86Wacom.o wcmSerial.o wcmUSB.o wcmISDV4.o wcmXCommand.o wcmCommon.o wcmCompat.o wcmConfig.o wcmFilter.o wcmTilt2Rotation.o -Bstatic -lgcc
make[2]: Leaving directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/xdrv'
Making all in 2.6.28
make[2]: Entering directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/2.6.28'
cp -f ../2.6.27/wacom.h .
    Building linuxwacom drivers for 2.6 kernel.
***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built
make -C /lib/modules/2.6.28-15-generic/build M=/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/2.6.28
make[3]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  LD      /home/rebecca/Desktop/linuxwacom-0.8.4-2/src/2.6.28/built-in.o
  CC [M]  /home/rebecca/Desktop/linuxwacom-0.8.4-2/src/2.6.28/wacom_wac.o
  CC [M]  /home/rebecca/Desktop/linuxwacom-0.8.4-2/src/2.6.28/wacom_sys.o
  LD [M]  /home/rebecca/Desktop/linuxwacom-0.8.4-2/src/2.6.28/wacom.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/rebecca/Desktop/linuxwacom-0.8.4-2/src/2.6.28/wacom.mod.o
  LD [M]  /home/rebecca/Desktop/linuxwacom-0.8.4-2/src/2.6.28/wacom.ko
make[3]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make[2]: Leaving directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/2.6.28'
make[1]: Leaving directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src'
make[1]: Entering directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2'
rebecca@ubuntu:~/Desktop/linuxwacom-0.8.4-2$ sudo make install
[sudo] password for rebecca: 
Making install in src
make[1]: Entering directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src'
Making install in .
make[2]: Entering directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src'
make[3]: Entering directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/man/man4" || /bin/mkdir -p "/usr/share/man/man4"
 /usr/bin/install -c -m 644 'wacom.4x.gz' '/usr/share/man/man4/wacom.4x.gz'
make[3]: Leaving directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src'
make[2]: Leaving directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src'
Making install in wacomxi
make[2]: Entering directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/wacomxi'
make[3]: Entering directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/wacomxi'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/bin" || /bin/mkdir -p "/usr/bin"
 /usr/bin/install -c 'wacomcpl' '/usr/bin/wacomcpl'
 /usr/bin/install -c 'wacomcpl-exec' '/usr/bin/wacomcpl-exec'
test -z "/usr/lib/TkXInput" || /bin/mkdir -p "/usr/lib/TkXInput"
 /usr/bin/install -c -m 644 'pkgIndex.tcl' '/usr/lib/TkXInput/pkgIndex.tcl'
test -z "/usr/lib/TkXInput" || /bin/mkdir -p "/usr/lib/TkXInput"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'libwacomxi.la' '/usr/lib/TkXInput/libwacomxi.la'
/usr/bin/install -c .libs/libwacomxi.so.0.0.0 /usr/lib/TkXInput/libwacomxi.so.0.0.0
(cd /usr/lib/TkXInput && { ln -s -f libwacomxi.so.0.0.0 libwacomxi.so.0 || { rm -f libwacomxi.so.0 && ln -s libwacomxi.so.0.0.0 libwacomxi.so.0; }; })
(cd /usr/lib/TkXInput && { ln -s -f libwacomxi.so.0.0.0 libwacomxi.so || { rm -f libwacomxi.so && ln -s libwacomxi.so.0.0.0 libwacomxi.so; }; })
/usr/bin/install -c .libs/libwacomxi.lai /usr/lib/TkXInput/libwacomxi.la
/usr/bin/install -c .libs/libwacomxi.a /usr/lib/TkXInput/libwacomxi.a
chmod 644 /usr/lib/TkXInput/libwacomxi.a
ranlib /usr/lib/TkXInput/libwacomxi.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib/TkXInput
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/TkXInput

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/wacomxi'
make[2]: Leaving directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/wacomxi'
Making install in util
make[2]: Entering directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/util'
make[3]: Entering directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/util'
test -z "/usr/lib" || /bin/mkdir -p "/usr/lib"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'libwacomcfg.la' '/usr/lib/libwacomcfg.la'
/usr/bin/install -c .libs/libwacomcfg.so.0.0.1 /usr/lib/libwacomcfg.so.0.0.1
(cd /usr/lib && { ln -s -f libwacomcfg.so.0.0.1 libwacomcfg.so.0 || { rm -f libwacomcfg.so.0 && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so.0; }; })
(cd /usr/lib && { ln -s -f libwacomcfg.so.0.0.1 libwacomcfg.so || { rm -f libwacomcfg.so && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so; }; })
/usr/bin/install -c .libs/libwacomcfg.lai /usr/lib/libwacomcfg.la
/usr/bin/install -c .libs/libwacomcfg.a /usr/lib/libwacomcfg.a
chmod 644 /usr/lib/libwacomcfg.a
ranlib /usr/lib/libwacomcfg.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/bin" || /bin/mkdir -p "/usr/bin"
  /bin/bash ../../libtool   --mode=install /usr/bin/install -c 'wacdump' '/usr/bin/wacdump'
/usr/bin/install -c wacdump /usr/bin/wacdump
  /bin/bash ../../libtool   --mode=install /usr/bin/install -c 'xidump' '/usr/bin/xidump'
/usr/bin/install -c xidump /usr/bin/xidump
  /bin/bash ../../libtool   --mode=install /usr/bin/install -c 'xsetwacom' '/usr/bin/xsetwacom'
/usr/bin/install -c .libs/xsetwacom /usr/bin/xsetwacom
test -z "/usr/libexec" || /bin/mkdir -p "/usr/libexec"
test -z "" || /bin/mkdir -p ""
test -z "/usr/include/wacomcfg" || /bin/mkdir -p "/usr/include/wacomcfg"
 /usr/bin/install -c -m 644 'wacomcfg.h' '/usr/include/wacomcfg/wacomcfg.h'
make[3]: Leaving directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/util'
make[2]: Leaving directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/util'
Making install in xdrv
make[2]: Entering directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/xdrv'
make[3]: Entering directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/xdrv'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/xorg/modules/input" || /bin/mkdir -p "/usr/lib/xorg/modules/input"
 /usr/bin/install -c -m 644 'wacom_drv.so' '/usr/lib/xorg/modules/input/wacom_drv.so'
make[3]: Leaving directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/xdrv'
make[2]: Leaving directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/xdrv'
Making install in 2.6.28
make[2]: Entering directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/2.6.28'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src/2.6.28'
make[1]: Leaving directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2/src'
make[1]: Entering directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2'
make[2]: Entering directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2'
make[1]: Leaving directory `/home/rebecca/Desktop/linuxwacom-0.8.4-2'
rebecca@ubuntu:~/Desktop/linuxwacom-0.8.4-2$ sudo cp ./src/2.6.28/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
rebecca@ubuntu:~/Desktop/linuxwacom-0.8.4-2$ lsmod
Module                  Size  Used by
usbhid                 47040  0 
binfmt_misc            18572  1 
radeon                357792  2 
ppdev                  16904  0 
drm                   123232  3 radeon
bridge                 63776  0 
stp                    11140  1 bridge
bnep                   22912  2 
input_polldev          12688  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
arc4                   10240  2 
ecb                    11392  2 
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_hda_intel         559028  3 
snd_rawmidi            33920  1 snd_seq_midi
uvcvideo               69640  0 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath9k                 310584  0 
compat_ioctl32         18304  1 uvcvideo
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                99464  2 snd_hda_intel,snd_pcm_oss
videodev               45184  2 uvcvideo,compat_ioctl32
mac80211              251528  1 ath9k
snd_timer              34064  2 snd_seq,snd_pcm
snd                    78920  15 snd_seq_oss,snd_hda_intel,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_pcm,snd_timer
soundcore              16800  1 snd
leds_hp_disk           11400  0 
psmouse                64028  0 
i2c_piix4              20112  0 
v4l1_compat            23940  2 uvcvideo,videodev
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
video                  29844  0 
joydev                 20864  0 
pcspkr                 11136  0 
serio_raw              14468  0 
cfg80211               43680  1 mac80211
lis3lv02d              19408  0 
output                 11648  1 video
shpchp                 44572  0 
sdhci_pci              16896  0 
sdhci                  27396  1 sdhci_pci
led_class              13064  2 ath9k,leds_hp_disk
r8169                  46596  0 
mii                    14464  1 r8169
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
rebecca@ubuntu:~/Desktop/linuxwacom-0.8.4-2$ modinfo -d wacom
USB Wacom Graphire and Wacom Intuos tablet driver
USB Wacom Graphire and Wacom Intuos tablet driver
rebecca@ubuntu:~/Desktop/linuxwacom-0.8.4-2$ 



```

This is how far i've gotten. (There have been a few terminals before this but this is my latest set of steps.) 
Edit:Ugh, I keep having trouble trying to copy everything, sorry. =[ I think I got it now

---

### Post by Favux on 2009-10-07
Hi L-hibou,

Oops!

You were not suppose to do "sudo make install".  You were suppose to follow Section 1 in this HOW TO in post #104 here: [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)  All you wanted was the wacom.ko.  Now you've installed linuxwacom 0.8.4-2 over the Jaunty default version of 0.8.2-2!

We can uninstall it or you could see if it works with the modified wacom.fdi or with xorg.conf.

Did you reboot?

---

### Post by L-hibou on 2009-10-07
I had to reboot once during the procedure.... Not after this part though, no.  
I could have sworn that was from that page... =\ Well, the cursor moves, but when I press it it sticks for a moment. None of the buttons or anything work, and it's not mapped out to the tablet yet. 

What woud be the best option for me to fix this?

---

### Post by Favux on 2009-10-07
Let's see if the modified wacom.fdi works.  Install it and reboot.  The "purge" line in the HOW TO you used should have erased all of the default Jaunty 0.8.2-2 linuxwacom stuff.  So right now you probably don't have a wacom.fdi and a mouse .fdi has taken control.  0.8.4-2 is probably better for the Intuos4 anyway, if we can get it to work.  But at least you now have usb communication to the tablet!

---

### Post by L-hibou on 2009-10-07
Okay, I've rebooted. however the Tablet stopped responding at all. only has a little white light next t the touch ring.

---

### Post by Favux on 2009-10-07
You installed the modified wacom.fdi?  Verify it by using Places to navigate to it and right click on it to look at it in Text Editor (gedit).  The copy command in post #176 has the path to it.  Then try rebooting again.

If nothing, in a terminal enter:
```
dmesg | grep [Ww]acom
```
and let's look at the output.

---

### Post by L-hibou on 2009-10-07
It's not finding the wacom.fdi

And when I put what you told me into the Terminal it does this:

```
rebecca@ubuntu:~$ dmesg | grep [Ww]acom
rebecca@ubuntu:~$ 

```

It returns me back to the place you type and does nothing.

And i can't find where it is in "Places" .
Only found it on the desktop. (in the text format I had to download)

---

### Post by Favux on 2009-10-07
In Places click on 'File System' and then navigate up from there.

In a terminal enter:
```
lsmod
```
and see if 'wacom' is one of the listed modules.

---

### Post by L-hibou on 2009-10-07
I don't have the option "File System" under Places, but I tried running a file search for it and it did not come up.  Also, running lsmod did not come up with any Wacom module...

---

### Post by Favux on 2009-10-07
Hi L-hibou,

Let's hope the fix is simple.  Try adding "wacom" without the quotes to the bottom of the file 'modules' in "/etc/":
```
gksudo gedit /etc/modules
```
Save, close and then reboot.

Both sudo and gksudo make you root/super user which let's you modify system files.  You use gksudo with graphical (gui) programs like gedit.  That's Gnome editor which Ubuntu calls Text Editor.  The path to the file 'modules' is "/etc/modules".  Which means 'modules' is the the "/etc/" directory.

---

### Post by L-hibou on 2009-10-07
YESSS! It's moving at least now! How now can I set up the pen and buttons and map it and everything?

---

### Post by Favux on 2009-10-07
Hi L-hibou,

Outstanding!  Nice job.

So try the commands again.  Is the 'wacom' module now active and present in "lsmod"?:
```
lsmod
```
does dmesg show usb communication:
```
dmesg | grep [Ww]acom
```
with your tablet showing up in the output?

And most important, do your wacom devices show up in?:
```
xsetwacom list
```

---

### Post by L-hibou on 2009-10-07
The first two: YES!

The last one still does nothing...

---

### Post by Favux on 2009-10-07
Hi L-hibou,

Good.  Things are basically working.  So now you have to deal with the .fdi.  Try again navigating to the wacom.fdi you installed with Places (Nautilus).  File System should be listed in the left hand window.

Or try reinstalling the modified wacom.fdi in #176 and reboot.

Oh and to see what HAL is calling your wacom devices enter:
```
xinput --list
```

---

### Post by L-hibou on 2009-10-07
Would it be in one of these folders in the attached image?

If it's just in File System, then I don't see it there.  

I'll try reinstalling it via the post 176 and reboot if you can confirm it's not there.

Thank you so much for your help so far though; I really appreciate it. =]

---

### Post by Favux on 2009-10-07
Hi L-hibou,

Sure.

You're at the right place.  Double click on the 'usr' folder.  Then find the 'share' folder and double click on it.  And so on.  Following the path in the copy command.

---

### Post by L-hibou on 2009-10-07
YESSS! FINALLY figured out how to navigate files in this OS (I'm so used to Vista xD) And it wasn't there, but I reinstalled it via the post and voila! Now the tablet is mapped, I can click, and right click works too. =]

All i need to do now is figure out how to customize and activate the buttons on the tablet (and ensure pressure sensitivity is working). 

Thank you soooo much so far!

---

### Post by Favux on 2009-10-07
Hi L-hibou,

Wow!  Great.

Now see if "xsetwacom list" returns the device names.

---

### Post by L-hibou on 2009-10-07
It returns this:

```
rebecca@ubuntu:~$ xsetwacom list
stylus           stylus    
rebecca@ubuntu:~$ 

```

---

### Post by Favux on 2009-10-07
Shoot.

The installed wacom.fdi is the same as the modified one you downloaded?

Try in a terminal:
```
xinput --list
```
and see what HAL's calling things.

---

### Post by L-hibou on 2009-10-07
It should be the same..... this is what i get with that script:

```
rebecca@ubuntu:~$ xinput --list
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=4	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"stylus"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 44704
		Resolution is 5080
	Axis 1 :
		Min_value is 0
		Max_value is 27940
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 2047
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is -900
		Max_value is 899
		Resolution is 1
"SynPS/2 Synaptics TouchPad"	id=6	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 1472
		Max_value is 5472
		Resolution is 1
	Axis 1 :
		Min_value is 1408
		Max_value is 4448
		Resolution is 1
rebecca@ubuntu:~$ 


```

---

### Post by Favux on 2009-10-07
Hi L-hibou,

It should have your other devices even if incorrectly named.  Can you navigate back to your installed wacom.fdi and post what's in it?

---

### Post by L-hibou on 2009-10-07
This is inside it:

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="input.originating_device" contains="if0">
      <match key="info.product" contains="Wacom">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="info.product" type="string">stylus</merge>
          <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
          <append key="wacom.types" type="strlist">eraser</append>
          <append key="wacom.types" type="strlist">cursor</append>
          <append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="eraser">
      <merge key="info.product" type="string">eraser</merge>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="cursor">
      <merge key="info.product" type="string">cursor</merge>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="pad">
      <merge key="info.product" type="string">pad</merge>
    </match>
  </device>
</deviceinfo>
```

---

### Post by Favux on 2009-10-07
Hi L-hibou,

Well you've got the .fdi right.  It doesn't work right in Jaunty with a compiled and installed linuxwacom, whereas it does the default Jaunty 0.8.2-2 linuxwacom.  I was afraid of that.  I don't know why because someone just compiled 0.8.4-2 in Karmic and used the tablet pc .fdi it's adapted from and it apparently works fine.

So you've got a choice.  We can go to the xorg.conf method.  But then you lose usb hot plugging.

Or we can uninstall the 0.8.4-2 and reinstall the default version.  With any luck the wacom.ko you copied in place will remain and you wouldn't have to do anything for it.

Which do you want to try?

---

### Post by L-hibou on 2009-10-07
Well, I'll try to reinstall the default... Do you have a step by step on how to do that? I'm afraid of more links lest I mess up again... =\

---

### Post by Favux on 2009-10-07
Hi L-hibou,

Don't worry.  You've learned a lot in a very short time.

You want to do Appendix 4 in the HOW TO where you compiled linuxwacom:  [http://ubuntuforums.org/showthread.php?p=6546012#post6546012](http://ubuntuforums.org/showthread.php?p=6546012#post6546012)

Then reinstall both wacom-tools & xserver-xorg-input-wacom with Synaptic Package Manager and reboot.  That will probably reinstall the default wacom.fdi so you'll have to replace that again.  And hopefully you'll be good to go.

---

### Post by L-hibou on 2009-10-07
I'm stuck where it says "Then change directory into the unpacked linuxwacom tar you used. Then change directory into the "prebuilt" folder."  Right before running "sudo ./uninstall".

How do I go about doing this?

---

### Post by Favux on 2009-10-07
That's what the cd command is for.  It means change directory.

So at the beginning of the HOW TO:
```
cd ./Desktop
```
is a shortcut.  You don't have to get fancy, you can just type the whole path like:
```
cd /home/yourusername/Desktop
```
So you could use:
```
cd /home/yourusername/Desktop/linuxwacom-0.8.4-2/prebuilt
```

---

### Post by L-hibou on 2009-10-07
Well, I did everything there, uninstalled, reinstalled, rebooted, and replaced the wacom.fdi contents, and now "xsetwacom list" does nothing again...

What could I do to find out what went wrong where?

---

### Post by Favux on 2009-10-07
Hi L-hibou,

Did you reboot after replacing the .fdi?

First check in Synaptic Package manager that both linuxwacom packages are installed, especially wacom-tools.  We might have to try reinstalling them but we'd lose the .fdi again!

If they are there try the 'dmesg' command and the 'xinput --list' command.


Here's some links that might be helpful:

[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

[http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)

---

### Post by L-hibou on 2009-10-07
Oh! Turns out I needed yet another restart but now I get this: 

```
rebecca@ubuntu:~$ xsetwacom list
stylus           stylus    
pad              pad       
cursor           cursor    
eraser           eraser    
rebecca@ubuntu:~$ 

```

after running xsetwacom list!

Whooo! Thank you soooo much for bearing with me. I'm so new at this xD Now what should I do?

---

### Post by Favux on 2009-10-07
Hi L-hibou,

Wow, great!  You're there!

Now we just need to set up wacomcpl for you and then you can go onto the link (in post #176 where the .fdi is) to where ceridwen shows you how to set up your pad.

So also linked in post #176 is "Section 3: Calibrating your Tablet" in the same HOW TO you compiled in and did Appendix 4:  [http://ubuntuforums.org/showthread.php?p=6546012#post6546012](http://ubuntuforums.org/showthread.php?p=6546012#post6546012)

---

### Post by Enriquecaribe on 2009-10-07
For the record, this thread is amazing.

---

### Post by L-hibou on 2009-10-07
I loaded wacomcpl and I get a little menu with different buttons in them, however I'm not sure which is assigned what. Also, I looked through the links and was unable to find the post by ceridwen? I must be missing it or something.  ^^;

---

### Post by Favux on 2009-10-08
Hi L-hibou,

Unfortunately there's no manual or help for wacomcpl.  So you'll need to play with it.

It's the last link just before it says it's in the Intuous4 thread.  Post #95 here:  [http://ubuntuforums.org/showthread.php?t=1120029&page=10](http://ubuntuforums.org/showthread.php?t=1120029&page=10)  And remember to see a hidden file click on "Show Hidden Files" in View in Places.

---

### Post by L-hibou on 2009-10-08
Where it wants to edit xintric, I don't have the same words I should be looking for in mine:

```
xsetwacom set stylus Suppress "4"
xsetwacom set stylus RawSample "4"
xsetwacom set stylus ClickForce "5"
xsetwacom set stylus PressCurve "0 0 100 100"
xsetwacom set stylus TPCButton "off"
xsetwacom set stylus mode "Absolute"
xsetwacom set stylus Button3 "Button 3"
xsetwacom set stylus Button2 "Button 2"
xsetwacom set stylus Button1 "Button 1"
xsetwacom set eraser Suppress "4"
xsetwacom set eraser RawSample "4"
xsetwacom set eraser ClickForce "5"
xsetwacom set eraser PressCurve "0 0 100 100"
# run the primary system script
. /etc/X11/xinit/xinitrc
```

---

### Post by Favux on 2009-10-08
Hi L-hibou,

Well pad showed up in your "xsetwacom list" output so its there.  Enter 'wacomcpl' in a terminal and then click on 'pad' in the left column and see if there's something you can set and then save.  Reboot and then recheck .xinitrc and see if pad is now in there.

---

### Post by L-hibou on 2009-10-08
I didn't see anything I could set nor save under pad in wacomcpl.  However, I restarted anyway and the xintric never changed.

---

### Post by Favux on 2009-10-08
Hmmm.  Don't know what's wrong.  Best thing to do is probably take a break and look at it fresh tomorrow. 

Or you could try manually adding this from ceridwen's post:
```
xsetwacom set pad Button4 "core key  NumpadMinus "
xsetwacom set pad Button3 "core key  NumpadPlus "
xsetwacom set pad Button2 "core key  F12 "
xsetwacom set pad Button1 "core key  Esc"
```
at the bottom of your .xinitrc but above
```
# run the primary system script
. /etc/X11/xinit/xinitrc
```
And then reboot with your fingers crossed hoping it doesn't break anything.

---

### Post by L-hibou on 2009-10-08
Yeah, I'll try to continue to-morrow after my class. xD  My eyes are starting to grow tired, so I think I'll call it an "Almost there!" for to-night. I must say I got a LOT further than I expected to.

Thank you so much for your help so far, it has been REALLY appreciated. =]
G'night!

---

### Post by Favux on 2009-10-08
Hi L-hibou,

You're welcome.  Good night.

---

### Post by L-hibou on 2009-10-08
I didn't put the pad stuff in yet, since i don't really think use the pad part with the terminal absWDn "+" stuff  on the tablet anyway, not even in Vista, (not really sure what it is anyway, 'cause everything else works on the tablet, so I left it alone). I suspect it MAY be the scrolling circle, but it already scrolls so I left it alone xD so I already went and followed the other instructions to make xinitrc executable and on startup, and added the code for this:

```
#buttons on the left side of the tablet
xsetwacom set pad Button1 "core key A " #button inside touchring
xsetwacom set pad Button2 "core key B " #top button
xsetwacom set pad Button3 "core key C "
xsetwacom set pad Button4 "core key D "
xsetwacom set pad Button5 "core key E "
xsetwacom set pad Button6 "core key F "
xsetwacom set pad Button7 "core key G "
xsetwacom set pad Button8 "core key H "
xsetwacom set pad Button9 "core key I " #bottom button
```

in xinitrc and restarted and now I can type ABCDEFGHI with the buttons! Sweet. Now I know which buttons are what. I just have to change them to the commands I want.  Do you know what kind of things I could enter in place of the "core key A" to make a button do "ctrl+z" and "ctrl++", "Ctrl+-"; "ctrl", "alt" and stuff like that? I'm not sure if there are differences between how the tablet defines them in Vista versus Ubuntu. If not I can just copy the little text version of each command and type it in the .xinitrc file here in Ubuntu. If not, I may need a little help here. xD

But wow, I'm almost there! Thank you so much for your help so far! I couldn't have learned so much so fast (only been two days using Ubuntu) if it wasn't for your help. xD

---

### Post by Favux on 2009-10-08
Hi L-hibou,

Good deal, you've got the pad working.

This page in the LWP's HOWTO shows you how to make the buttons do what you want:  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)

It looks like your set up now!  You're welcome.

---

### Post by L-hibou on 2009-10-08
I can't seem to get them to do what I want them to to... Seems only Letters work, but then near the bottom it said "Note: keystrokes and modifiers are only supported for Xorg 6.8 or later. " I don't remember working with something called Xorg. Do I even have it?

---

### Post by Favux on 2009-10-08
Hi L-hibou,

Yes you do.  I think it's Xorg 7.5 in Jaunty.  I know it's Xserver 1.6.  Xorg makes the OSS (open source) video drivers and the X windowing system.  Which draws the windows/graphics on the screen.

So changing:
```
xsetwacom set pad Button3 "core key C "
```
to say:
```
xsetwacom set pad Button3 "core key ctrl alt F2 "
```
doesn't work?

I don't know if you need the space before the trailing ", I don't think so.

---

### Post by L-hibou on 2009-10-08
I've tried it with and without the space, restarting after each change, and neither worked... Can't quite figure out what's wrong ...

---

### Post by Favux on 2009-10-08
Hi L-hibou,

After you restart and you look at .xinitrc, were your changes saved?

---

### Post by L-hibou on 2009-10-08
Yeah, they were saved.

---

### Post by Favux on 2009-10-08
Hi L-hibou,

So the only script you're running is the .xinitrc that wacomcpl "generates".  That should be the last thing run and it should "control".

I don't know what's wrong either.  I would think if you could add letters you should be able to add other stuff.

Looks like it's time to post on the Intuos4 thread (where ceridwen's post is) and ask for help.  Maybe one of the other Intuos4 users can help you.  You could also skim through the thread after ceridwen's post and see if anything useful comes up.

---

### Post by L-hibou on 2009-10-08
Yeah, I'll give that a shot. 

Thank you sooo much though; I appreciate your bearing with me though this, and you've helped me out a ton.  I'll go look through the thread and see if there's anything of help and post there if I don't find the solution.  I'll report back here when/if I fix it or not. =]

Thanks again!

---

