---
title: "How to make Microsoft LifeCam VX-3000 work in Ubuntu?"
date: 2008-08-10
forum: x86 64-bit Users
---

### Post by HQLCD on 2008-08-10
Is it possible to make How to make Microsoft LifeCam VX-3000 work in Ubuntu? How?

---

### Post by cariboo on 2008-08-10
To get a working driver for your webcam go here:

[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

Once downloaded extract the files to a directory of your choice, I suggest creating a directory called sources and extracting it there, that way if you need it again for some reason you still have it. Read the read_and_install file, the part you really need is under the heading Compiling it, ignore the bit about compiling your kernel as it is not needed. Just as a precaution you should install the build-essential package before compiling the driver. The compile script does everything for you, once it finishes, open cheese and use your webcam.

Jim

---

### Post by iaskedalice09 on 2008-08-11
Which kernel does 8.04.1 use?

---

### Post by rizitis on 2008-08-11
when you dont know which  kernel you use 
open the terminal and command 
```
uname -r
```
press enter and you will see it...

---

### Post by iaskedalice09 on 2008-08-11
Got it. Thank you so much

---

### Post by farlander762 on 2008-08-16
OK, I did all that was asked, my VX-3000 still looks like a really dark negative and my Logitech Notebook QuickCam still doesn't work.  Any ideas?  How bad have I derailed the train?


```
lance@MEDION-Ubuntu:~$ cd .drivers
lance@MEDION-Ubuntu:~/.drivers$ ls
gspcav1-20071224  gspcav1-20071224.tar.gz
lance@MEDION-Ubuntu:~/.drivers$ cd gspcav1-20071224
lance@MEDION-Ubuntu:~/.drivers/gspcav1-20071224$ ls
changelog  Etoms         license       Pixart            Sunplus-jpeg
Conexant   gspca_build   Makefile      READ_AND_INSTALL  Transvision
cutlog.py  gspca_core.c  Makefile.kld  Sonix             utils
decoder    gspca.h       Mars-Semi     Sunplus           Vimicro
lance@MEDION-Ubuntu:~/.drivers/gspcav1-20071224$ sudo ./gspca_build
[sudo] password for lance: 

 REMOVE the old module if present

 CLEAN gspca source tree
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
	.gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
	*.symvers *.err

 COMPILE gspca Please Wait ....!!

 INSTALL gspca in the kernel binary tree
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
/sbin/depmod -ae

 LOAD gspca in memory 

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err 
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/lance/.drivers/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/lance/.drivers/gspcav1-20071224/gspca_core.o
  CC [M]  /home/lance/.drivers/gspcav1-20071224/decoder/gspcadecoder.o
  LD [M]  /home/lance/.drivers/gspcav1-20071224/gspca.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/lance/.drivers/gspcav1-20071224/gspca.mod.o
  LD [M]  /home/lance/.drivers/gspcav1-20071224/gspca.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
lance@MEDION-Ubuntu:~/.drivers/gspcav1-20071224$ sudo gspcagui -d /dev/video0
sudo: gspcagui: command not found
lance@MEDION-Ubuntu:~/.drivers/gspcav1-20071224$ 
lance@MEDION-Ubuntu:~/.drivers/gspcav1-20071224$ 


```

---

### Post by cariboo on 2008-08-17
There is no gspcagui source code in the driver you downloaded you have to download this file:

[http://mxhaard.free.fr/spca50x/Investigation/Gspca/gspca-20060930.tar.gz](http://mxhaard.free.fr/spca50x/Investigation/Gspca/gspca-20060930.tar.gz)

To get the gspcagui source. I also had to install libsdl-gfx1.2-dev, it is available in the repositories.

Once you have installed the libsdl headers just extract the file to where ever you want and then cd to the gspcagui directory and rum make and sudo make install. the new program will be located in /usr/local/bin. It takes acouple of minutes for it to run through all the settings, then you can use the controls to set the webcam up.


Jim

---

### Post by Prefix100 on 2008-08-20
I don't really get how to use this, if I click G for v4l it hangs, if I click p for avi and click the buttons above and stuff it does nothing to the camera in cheese, same for the tcp option.

Could you give a step by step on ho-to install the driver, and then the gui?

I'd really appreciate it, and it would help other people out too.

I get this error when trying to envoke ./gspca_build in one of the driver directorys.

```

jonny@jonny-desktop:~/Desktop/gspca-20060930/gspcav1$ sudo ./gspca_build

 REMOVE the old module if present
ERROR: Module gspca is in use

 CLEAN gspca source tree
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
	.gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
	*.symvers *.err

 COMPILE gspca Please Wait ....!!

 INSTALL gspca in the kernel binary tree
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1

 LOAD gspca in memory 

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err 
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/jonny/Desktop/gspca-20060930/gspcav1 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/jonny/Desktop/gspca-20060930/gspcav1/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/jonny/Desktop/gspca-20060930/gspcav1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2


```

Never mind!

Got it going using the sudo gspcagui -d /dev/video0 command
awesome.

---

### Post by jespdj on 2008-08-21
I had this webcam. There was no way to get it working properly with Linux, also not with Michel Xhaard's drivers. I've read several posts about this webcam on the forums here, but nobody seems to have it working.

I gave the webcam to my parents (who use Windows XP) and bought a Logitech webcam instead, which worked out-of-the-box on Ubuntu.

---

### Post by Prefix100 on 2008-08-21
well it works now using this tool I can tell you that.

My only grumblings is that you have to do it on every restart.

---

### Post by Penguins007 on 2008-10-31
I hope someone can come back and help me with this.  I was unable to make my vx-3000 works on my 8.10 Ubuntu.  I tried with 8.04, maybe similiar with 8.10?

I have followed the instruction from [http://ubuntuforums.org/showthread.php?t=885795&highlight=vx-3000+webcam](http://ubuntuforums.org/showthread.php?t=885795&highlight=vx-3000+webcam), and downloaded from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html). Then click gspcav1-20071224.

But seems my outcome is not what I expected?

root@localhost:/home/zeplinthree/Desktop# cd gspcav1-20071224
root@localhost:/home/zeplinthree/Desktop/gspcav1-20071224# dir
changelog  Etoms	 license       Pixart		 Sunplus-jpeg
Conexant   gspca_build	 Makefile      READ_AND_INSTALL  Transvision
cutlog.py  gspca_core.c  Makefile.kld  Sonix		 utils
decoder    gspca.h	 Mars-Semi     Sunplus		 Vimicro
root@localhost:/home/zeplinthree/Desktop/gspcav1-20071224# cd .drivers
bash: cd: .drivers: No such file or directory
root@localhost:/home/zeplinthree/Desktop/gspcav1-20071224# sudo ./gspca_build

 REMOVE the old module if present
ERROR: Module gspca does not exist in /proc/modules

 CLEAN gspca source tree
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
	.gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
	*.symvers *.err

 COMPILE gspca Please Wait ....!!

 INSTALL gspca in the kernel binary tree
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1

 LOAD gspca in memory 
FATAL: Module gspca not found.

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err 
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/zeplinthree/Desktop/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.o
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c: At top level:
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c:2609: error: unknown field ‘owner’ specified in initializer
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c:2609: warning: initialization from incompatible pointer type
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c:2611: error: unknown field ‘type’ specified in initializer
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/home/zeplinthree/Desktop/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/zeplinthree/Desktop/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [default] Error 2
root@localhost:/home/zeplinthree/Desktop/gspcav1-20071224#

---

### Post by javajeff1 on 2008-11-09
When I plug in my LifeCam VX-3000, the light stays on and nothing happens.  I get no functionality at all.

---

### Post by verlyn13 on 2008-12-31
I am trying to get my vx-3000 working in ubuntu
ibex 2.6.27-9-generic

I am new to linux, so I'm not sure what is going wrong.  I downloaded the above file and when I try to compile I get the following:

root@jefahnie-desktop:/home/jefahnie/Desktop/Misc Programs/webcam/gspcav1-20071224# ./gspca_build

 REMOVE the old module if present
ERROR: Module gspca does not exist in /proc/modules

 CLEAN gspca source tree
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
	.gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
	*.symvers *.err

 COMPILE gspca Please Wait ....!!

 INSTALL gspca in the kernel binary tree
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1

 LOAD gspca in memory 
FATAL: Module gspca not found.

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err 
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/jefahnie/Desktop/Misc Programs/webcam/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
make[1]: *** No rule to make target `Programs/webcam/gspcav1-20071224'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [default] Error 2

---

### Post by RobMongoose on 2009-01-02
I'm getting the same error when using the drivers linked to earlier in the thread, and a very similar one using the newer driver from the developer site. I'm trying to get a LifeCam VX-1000 working. 

lsusb shows it being detected, I've tried running easycam, but it seems I need to et this driver compiled and loaded.

Can anyone tell why this isn't working?

lsusb output
```
root@Rukia:~# lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00f7 Microsoft Corp. LifeCam VX-1000.
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

gspca-20060930 install output
```
root@Rukia:/home/rob/downloads/drivers/gspca-20060930/gspcav1# ./gspca_build                        

 REMOVE the old module if present                                                                   
ERROR: Module gspca does not exist in /proc/modules                                                 

 CLEAN gspca source tree                                                                            
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \                                              
        .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \                                           
        *.symvers *.err                                                                             

 COMPILE gspca Please Wait ....!!                                                                   

 INSTALL gspca in the kernel binary tree                                                            
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/                                          
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko                                   
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko                                   
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/                       
install: cannot stat `gspca.ko': No such file or directory                                          
make: *** [install] Error 1                                                                         

 LOAD gspca in memory                                                                               
FATAL: Module gspca not found.                                                                      

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err                                               
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/rob/downloads/drivers/gspca-20060930/gspcav1 CC=cc modules                                                                                          
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'                               
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/rob/downloads/drivers/gspca-20060930/gspcav1/Makefile". Fix it to use EXTRA_CFLAGS. Stop.                                                   
make[1]: *** [_module_/home/rob/downloads/drivers/gspca-20060930/gspcav1] Error 2                   
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'                                
make: *** [default] Error 2
```

gspcav1-20071224 installation output

```
root@Rukia:/home/rob/downloads/drivers/gspcav1-20071224# ./gspca_build                              

 REMOVE the old module if present                                                                   
ERROR: Module gspca does not exist in /proc/modules                                                 

 CLEAN gspca source tree                                                                            
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \                                              
        .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \                                           
        *.symvers *.err                                                                             

 COMPILE gspca Please Wait ....!!                                                                   

 INSTALL gspca in the kernel binary tree                                                            
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/                                          
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko                                   
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko                                   
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1

 LOAD gspca in memory
FATAL: Module gspca not found.

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/rob/downloads/drivers/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/rob/downloads/drivers/gspcav1-20071224/gspca_core.o
/home/rob/downloads/drivers/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/home/rob/downloads/drivers/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/home/rob/downloads/drivers/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/home/rob/downloads/drivers/gspcav1-20071224/gspca_core.c: At top level:
/home/rob/downloads/drivers/gspcav1-20071224/gspca_core.c:2609: error: unknown field ‘owner’ specified in initializer
/home/rob/downloads/drivers/gspcav1-20071224/gspca_core.c:2609: warning: initialization from incompatible pointer type
/home/rob/downloads/drivers/gspcav1-20071224/gspca_core.c:2611: error: unknown field ‘type’ specified in initializer
/home/rob/downloads/drivers/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/home/rob/downloads/drivers/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/home/rob/downloads/drivers/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/home/rob/downloads/drivers/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/home/rob/downloads/drivers/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/home/rob/downloads/drivers/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/rob/downloads/drivers/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [default] Error 2
```

Kernel headers and as many potential dependencies as I can think of are installed.

Any ideas?

---

### Post by rukhin on 2009-02-23
> **cariboo907 said:**
> To get a working driver for your webcam go here:

[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

Once downloaded extract the files to a directory of your choice, I suggest creating a directory called sources and extracting it there, that way if you need it again for some reason you still have it. Read the read_and_install file, the part you really need is under the heading Compiling it, ignore the bit about compiling your kernel as it is not needed. Just as a precaution you should install the build-essential package before compiling the driver. The compile script does everything for you, once it finishes, open cheese and use your webcam.

Jim


Thanks for the help, Jim.  This worked for me...

...however, my video has no sound (!). Do I need to get a separate mic.?  What do I need to do to get around this?

---

### Post by sansor on 2009-03-22
I tried to compile by gspca_build the driver in [http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz) which I thought would be for Intrepid 8.10. However, I could not compile because the header file "asm/semaphore.h" could not be found. I included "linux/semaphore.h" instead but now it gives the errors:

(I installed build-essential package and don't know if I had to do more to start compiling)

```
PRINT COMPILATION MESSAGES if ERRORS look kgspca.err 
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/yyetim/Desktop/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/yyetim/Desktop/gspcav1-20071224/gspca_core.o
/home/yyetim/Desktop/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/home/yyetim/Desktop/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/home/yyetim/Desktop/gspcav1-20071224/gspca_core.c: At top level:
/home/yyetim/Desktop/gspcav1-20071224/gspca_core.c:2604: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
/home/yyetim/Desktop/gspcav1-20071224/gspca_core.c:2609: error: unknown field ‘owner’ specified in initializer
/home/yyetim/Desktop/gspcav1-20071224/gspca_core.c:2609: warning: initialization from incompatible pointer type
/home/yyetim/Desktop/gspcav1-20071224/gspca_core.c:2611: error: unknown field ‘type’ specified in initializer
/home/yyetim/Desktop/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/home/yyetim/Desktop/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/home/yyetim/Desktop/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/home/yyetim/Desktop/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/home/yyetim/Desktop/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/home/yyetim/Desktop/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/yyetim/Desktop/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [default] Error 2

```

I guess "linux/semphore.h" isn't the same thing. I upgraded to Jaunty, I still have the same problems. Does anyone know how to compile this driver, or if VX-3000 will be supported as most of other webcams ??? Or is it a problem with the distro or kernel?

PS: I use 64-bit Desktop Edition

---

### Post by jesterthejedi on 2009-03-22
Working after 6 months of waiting and searching forums. My cam is the dreaded Microsoft VX-1000.

Do this:
Download driver:
[http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/)
grab the .bz2 file (top of page little text link called bz2)
extract archive (you can extract with nautilus)
in terminal "cd /Desktop/gspca" + <TAB> or exact name <ENTER>
in terminal type "make" no quotes takes about 5 mins
then type "sudo make install"
reboot

tested working on Intrepid With Cheese, Ekiga, Skype, GyachE, Xawtv

COLORS are fine! no more green/blue Hardy mess.
not working in Camorama, Camstream, errors in gqcam

installed xawtv, luvcview, and removed camserv.

I am so happy that I should pinch myself. I bought this webcam in June for my birthday and it was always a pain in the butt to solve. Success at last!

---

### Post by jesterthejedi on 2009-03-22
Also works in Jaunty J 9.04 Beta, but when your kernel/headers update you need to re-run the make, make install instructions, or you will see the green forever on webcam led.

---

### Post by sansor on 2009-03-22
I downloaded, compiled and installed this archive. I also rebooted the computer. Now all I can see is a green noise on "mplayer tv:// -tv driver=v4l:width=640:height=480:device=/dev/video0". Skype crashes when I try to use the webcam.  
Any suggestions? 
Do I need to blacklist any driver? Or do I need to do anything else?

---

### Post by sansor on 2009-03-22
> **jesterthejedi said:**
> Also works in Jaunty J 9.04 Beta, but when your kernel/headers update you need to re-run the make, make install instructions, or you will see the green forever on webcam led.

By the way, is jaunty 9.04 Beta released? I am using alpha 6 and I thought it was the most recent release... And did you try it on a 64-bit machine or a 32-bit one?

---

### Post by jesterthejedi on 2009-03-23
I do not know which Jaunty I use as I update when it tells me so. I do know that some programs it does not work in, ie camorama. My best guess is to try it with Cheese and Gyachi or test with ALT + F2 ¨gstreamer-properties¨ I know that some programs have trouble with ¨videoforlinux2¨ or v4l2 devices. If it works with Cheese or those others than its a v4l2 issue that those programs cannot support yet, and if its not working with any program its the drivers not correctly installed. When you plug in the webcam for the first time the green light stays on constantly. This goes away after the drivers and installed. Then it only turns on when requested by a program. Oh and I use 32 bit here.

---

### Post by sansor on 2009-03-23
Actually, the green light turned off and it turns on whenever I start mplayer or skype, which should be the case. I just realized that you use VX-1000, and I use VX-3000. 
I also tried it in 32-bit which didn't work. I guess I have to wait for the kernel guys to fix it.

---

### Post by jesterthejedi on 2009-03-23
Your mplayer code was bad, but I searched the forums and this way worked for me:

mplayer -tv driver=v4l2:gain=1:width=640:height=480:device=/dev/video0:fps=30:outfmt=yuy2 tv://

Oh and the chip inside the 1000 is the same as the 3000, AFAIK, the specs of the cam are different though. It took me 6 months to find the right procedure, I had to use an old laptop with XP on it to use my webcam, those days are gone :)

---

### Post by sansor on 2009-03-23
Thanks, it worked !!! But it still doesn't work in Skype 2.0.0.72.

Any suggestions how I can make it work in Skype?

---

### Post by sansor on 2009-03-23
Finally!! I need to run the command 
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
to start the Skype. Then it works great. 

Why don't they include "Jean-Francois Moine"s gspca driver into ubuntu instead of the old driver? Would be a good change for 9.04...

---

### Post by jesterthejedi on 2009-03-23
I&#7743; not sure it could be issues with other drivers. How did you use that code for Skype? Mine used to work fine, now its just a green haze of noise.

---

### Post by sansor on 2009-03-23
I entered that code as a command. Copy and paste to a terminal, that's all I did...

---

### Post by executorvs on 2009-03-24
No beta isn't out yet. I it should show up this Thursday. [https://wiki.ubuntu.com/JauntyReleaseSchedule](https://wiki.ubuntu.com/JauntyReleaseSchedule)

---

### Post by sansor on 2009-03-29
By the way, for 64-bit: 

skype works with 32 bit libraries. Therefore, for this command to work, I installed "lib32v4l-0" libraries from synaptic

---

### Post by jesterthejedi on 2009-03-31
It worked in terminal but not the run box, "<ALT> + <F2>".
Would be nicer if there was just a symlink or something that would do this automatically.

---

### Post by sansor on 2009-03-31
I created a file:

```
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

saved it as a file called "skype_lib", and create a "launcher" called "skype" on the desktop which targets "skype_lib". I just click on that launcher. 

PS: Another library (v4l2convert.so) in the same directory as v4l1compat.so also works. I don't know the difference, though...

---

### Post by 4ny0n3 on 2009-04-06
Hey jesterthejedi thanks for linking us to the Jfrancois driver, I managed to install it with no hassles whatsoever, and now the cam turns on only when I activate it, but problem is it only shows a black or distorted image... I followed every single step, not that there were many. What could be going wrong? I'm using Jaunty Jackalope and I have a VX1000.

EDIT: I found a way to fix it... I used the "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so + appname" command that sansor used and the cam works. Am I going to have to do this with every single app I use or is there a workaround to this?

---

### Post by ellwood00 on 2009-04-15
hey every time i try to install the driver i get this error can anyone help me 
ive tried everything on all the posts ive looked at and i trued the make and make install like the readme said but i still get errors

```
 COMPILE gspca Please Wait ....!!

 INSTALL gspca in the kernel binary tree
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1

 LOAD gspca in memory 
FATAL: Module gspca not found.

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err 
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/chris/Desktop/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/chris/Desktop/gspcav1-20071224/gspca_core.o
/home/chris/Desktop/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/home/chris/Desktop/gspcav1-20071224/gspca_core.c: In function &#8216;spca5xx_ioctl&#8217;:
/home/chris/Desktop/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function &#8216;video_usercopy&#8217;
/home/chris/Desktop/gspcav1-20071224/gspca_core.c: At top level:
/home/chris/Desktop/gspcav1-20071224/gspca_core.c:2609: error: unknown field &#8216;owner&#8217; specified in initializer
/home/chris/Desktop/gspcav1-20071224/gspca_core.c:2609: warning: initialization from incompatible pointer type
/home/chris/Desktop/gspcav1-20071224/gspca_core.c:2611: error: unknown field &#8216;type&#8217; specified in initializer
/home/chris/Desktop/gspcav1-20071224/gspca_core.c: In function &#8216;spca50x_create_sysfs&#8217;:
/home/chris/Desktop/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function &#8216;video_device_create_file&#8217;
/home/chris/Desktop/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function &#8216;video_device_remove_file&#8217;
/home/chris/Desktop/gspcav1-20071224/gspca_core.c: In function &#8216;spca5xx_probe&#8217;:
/home/chris/Desktop/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/home/chris/Desktop/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/chris/Desktop/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [default] Error 2
chris@ubuntu:~/Desktop/gspcav1-20071224$ 

```

---

### Post by sansor on 2009-04-15
I think you are using the old gspca driver. 
Try: 
[http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/)

---

### Post by jesterthejedi on 2009-04-16
Shortcut:

go to usr/bin "gksu nautilus" Need root to make these changes

create a text file, call it "skype", give it executable permissions "right click > properties > permissions > check box executable"

paste this in

#!/bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.real

save and close.

***IMPORTANT*** YOU MUST RENAME the old SKYPE to skype.real for this to work

---

### Post by jesterthejedi on 2009-04-16
This is the exact one you want:

[http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2)

---

### Post by mplexus on 2009-04-17
many thanks everyone! my VX-1000 now works with skype, cheese

and camorama (like sansor wrote for skype:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama )

cool!

now trying to get it working with command-line webcam (snapshots in public_html)
Edit: webcam done. (edited ~/.webcamrc)

---

### Post by executorvs on 2009-04-18
has anyone tried this in jaunty yet?

---

### Post by sansor on 2009-04-19
I have, and it works

---

### Post by Insane_Homer on 2009-04-20
> **jesterthejedi said:**
> Working after 6 months of waiting and searching forums. My cam is the dreaded Microsoft VX-1000.

Do this:
Download driver:
[http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/)
grab the .bz2 file (top of page little text link called bz2)
extract archive (you can extract with nautilus)
in terminal "cd /Desktop/gspca" + <TAB> or exact name <ENTER>
in terminal type "make" no quotes takes about 5 mins
then type "sudo make install"
reboot

tested working on Intrepid With Cheese, Ekiga, Skype, GyachE, Xawtv

COLORS are fine! no more green/blue Hardy mess.
not working in Camorama, Camstream, errors in gqcam

installed xawtv, luvcview, and removed camserv.

I am so happy that I should pinch myself. I bought this webcam in June for my birthday and it was always a pain in the butt to solve. Success at last!

=D>

Many, many thanks!

I just did this on my jaunty 9.04 x64 and I can see myself very nicely with cheese on my VX-3000

Now to install Skype...

---

### Post by tuiger on 2009-04-22
The cam works now fine in cheese and xawtv for me, thank you very much.


If I write this command

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

in a Terminal, skype works too. 


I run skype in pidgin

But, I can't change the Skype intu the skype.real-name, same as jesterthejedi did.

> **jesterthejedi said:**
> Shortcut:

go to usr/bin "gksu nautilus" Need root to make these changes

create a text file, call it "skype", give it executable permissions "right click > properties > permissions > check box executable"

paste this in

#!/bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.real

save and close.

***IMPORTANT*** YOU MUST RENAME the old SKYPE to skype.real for this to work


I tried, right mouseclick in the usr/bin/skype folder, but it dosen't work.
Any advise?

---

### Post by jeff_flynn on 2009-04-22
I am on Linux Ubuntu 7.10 The Gutsy Gibbon, and I have a VX1000 Microsoft Lifecam. Can someone tell me EXACTLY what to do in order to get it up and running with aMSN?

---

### Post by MasterPoulos89 on 2009-04-27
I've installed my lifecam vx-3000 like this and finally it works. But it does go slow. If I make a video the the words and the picture are obviously off. I am happy that I got it to work but I cant use it cause of how slow it works.

Is it going slow for anyone else or is it just me??

---

### Post by discovery on 2009-04-28
I did a fresh install of Jaunty 9.04 just for this camera.

I tried following the advice in this thread, and I still get a green screen in Skype, Camorama, mplayer, etc...

All of these applications have the same errors for libv4lconvert:

```

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffd9
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffd9
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffd9
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits


```

These errors occur constantly while the app is running. And again, all I see is a green screen.

All these apps see the camera in /dev/video0. The green light goes on/off with the given app, so this is major progress compared to when I started. 

Anyone have any idea? I've tried doing a google search but haven't had much luck. The success in this thread has given me hope!

---

### Post by jesterthejedi on 2009-04-28
> **tuiger said:**
> The cam works now fine in cheese and xawtv for me, thank you very much.


If I write this command

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

in a Terminal, skype works too. 


I run skype in pidgin

But, I can't change the Skype intu the skype.real-name, same as jesterthejedi did.




I tried, right mouseclick in the usr/bin/skype folder, but it dosen't work.
Any advise?

You need to be ROOT to rename skype to skype.real
use ALT+F2 gksu nautilus before you navigate to that location. Then use the F2 key when you highlight the file.

---

### Post by jesterthejedi on 2009-04-28
> **discovery said:**
> I did a fresh install of Jaunty 9.04 just for this camera.

I tried following the advice in this thread, and I still get a green screen in Skype, Camorama, mplayer, etc...

All of these applications have the same errors for libv4lconvert:

```

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffd9
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffd9
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffd9
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits


```

These errors occur constantly while the app is running. And again, all I see is a green screen.

All these apps see the camera in /dev/video0. The green light goes on/off with the given app, so this is major progress compared to when I started. 

Anyone have any idea? I've tried doing a google search but haven't had much luck. The success in this thread has given me hope!

Edit: There is another LD=preload option. Search this forum for the code.

---

### Post by MasterPoulos89 on 2009-04-29
I've only tried it with Cheese and it works. The color is good but it's just slow as I mentioned. What results do you get if you try it in Cheese.

Also when I uninstalled it and reinstalled it I got the green screen that u mention and had to do a fresh install to get it again. Maybe even though you said its a fresh install it might work if you try reinstalling again or it may just waste some time but at least you'll know thats not the problem.

---

### Post by sansor on 2009-04-30
There is also
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so camorama
However, I don't think it would work. You should try, though...

The problem might be related to the architecture. You might want to check the arch of camorama and the libraries.

---

### Post by discovery on 2009-04-30
> **sansor said:**
> There is also
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so camorama
However, I don't think it would work. You should try, though...

The problem might be related to the architecture. You might want to check the arch of camorama and the libraries.

Thank you for the replies.

I tried the other LD_PRELOAD command. No luck, same errors when I use Skype as my original post. Camorama gets a new error: Unable to capture image.

I am not sure how to check the architecture for any video capturing, this is all new for me. I wouldn't know if there was a problem if it was staring me in the face.

I did find gstreamer-properties where I can test video input between vl4 and vl42, no luck! Both have the same stream of messages as original post.

Is there any suggestions you can make to point me in the right direction?

Also, my ultimate goal is for the camera to work in Skype! just an fyi I guess...

---

### Post by sansor on 2009-04-30
Do you use 32-bit or 64-bit Jaunty?
if 64-bit, then try installing "lib32v4l-0" from Package Manager.
Then use:

LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype

to start skype . Don't use camorama to check if it works because I don't know if it works in camorama with that libraries. 
And you didn't do anything to the kernel right, you use the default kernel configuration that comes with Jaunty?

---

### Post by discovery on 2009-05-01
> **sansor said:**
> Do you use 32-bit or 64-bit Jaunty?
if 64-bit, then try installing "lib32v4l-0" from Package Manager.
Then use:

LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype

to start skype . Don't use camorama to check if it works because I don't know if it works in camorama with that libraries. 
And you didn't do anything to the kernel right, you use the default kernel configuration that comes with Jaunty?

Its 32-bit Jaunty. I did not touch the kernel.

I could not find that package in the package manager...probably because I am not running 64 bit.

Thanks again for trying, got anything else? heh heh

---

### Post by MasterPoulos89 on 2009-05-02
In Jaunty I just reinstalled on a fresh install again and now I can only get a green screen. So I guess its just not working properly on Jaunty. I think I'm just ganna buy a new cam. Ohh Well.

---

### Post by sansor on 2009-05-02
I tried it in both 32-bit and 64-bit Jaunty. It worked fine in both of them. I don't know what the issue might be. You can try the same steps on an old version of Ubuntu, 8.10 or 8.04 (or perhaps alpha 6 of Jaunty, the one I tried). It might be related to the new kernel in Jaunty. I'm sure in one of them, you can get it working. I think you shouldn't buy a new camera.

---

### Post by MasterPoulos89 on 2009-05-03
Even when I had it working in intrepid it was going to slow to use it. So even if I do get it to work in jaunty it will go to slow to actually use. better I just get one that works out of the box. Does it go slow for you? If not then maybe somehow im doing something wrong. IDK.

---

### Post by sansor on 2009-05-04
I also think that it is a little bit slow. So what you did was probably correct.

---

### Post by scottie_000 on 2009-05-04
I'm having the same problem as discovery, with the green screen (both in cheese and gstreamer-properties)
Using Jaunty 64-bit
Followed the instructions as above having lost the use of VX-1000 after upgrade from 8.10 to 9.04 :(

---

### Post by nick937 on 2009-05-10
same problem with jaunty...
DANG!
I was trying to install the old driver.. and then I found this thread and had some hope... and then I got the green screen :(

---

### Post by cmcginty on 2009-05-12
What does this output mean?
```
$ cheese
libv4l2: error dequeuing buf: Input/output error
libv4l2: error dequeuing buf: Input/output error
libv4l2: error dequeuing buf: Input/output error
```

What module should be loaded for VX-3000 camera? Everyone says > "it's working", but no one has provided any details? I'm running '**gspca_sonixj**'. Is this correct?

---

### Post by Kapurnicus on 2009-05-12
I am on 64-bit 9.04 as well. After compiling drivier (as suggested) I get green screen instead of no camera detected. Trying to Use Preload command I get same green screen. Output to console always says "need 3 more bits" or something of the like. I was trying to preload with /usr/lib32 library instead of lib. Although I probably have both installed.

Anyone have this configuration working? And if so, what modules are kernal loaded (and how do I remove the ones I don't need).

---

### Post by Uter on 2009-05-17
I am also have a green screen in cheese ;) 

```

libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits

```

I am using a 64 Bit veriosn of Jaunty. I didn't try the LD_Preload - Trick, has someone tries it and can give some feedback ?

---

### Post by Uter on 2009-05-17
so I tried: 

I installed libv4l-0 and then I typed this command:

LD_PRELOAD=/usr/lib64/libv4l/v4l1compat.so cheese

->

my screen is still green :(

---

### Post by teixidoj on 2009-05-17
This is why I dual boot. Until the device manufactures start making drivers/software for Linux we will always have this kind of challenge. I've emailed all of my hardware vendors who do not make drivers/software for Linux asking them when will they support Linux. It's all about supply and demand, if they don't see a demand, they won't make the supply.

 It the mean time; I would suggest that the next printer webcam etc. that you purchase in the future be supplied with Linux drivers/software at least make this part of your purchasing decision.

---

### Post by Uter on 2009-05-18
Sure we all know this kind of problem, but in this case the hardware already runs in an earlier ubuntu version (or kernel version). I know that the kernel - guys do a great job, but from time to time its a little annoying to update a version or a kernel and then the hardware suddenly doesn't work anymore. 

The same Problem happens with my TV card (hauppauge wintv nova-s), I used this hardware since Dapper but now it doesn't work anymore :( 

I hope that this will be better in future releases ;) 

cheers,
Uter

---

### Post by leachyboy2001 on 2009-05-25
interesting...I have the vx1000 working on a desktop that was upgraded to 9.04 betaan has all ubuntu updates installed.  I also have a laptop which was upgraded to 9.04 when it went mainstream and just tried to install the camera and it is not working, just getting the green screen.  I'm going to try the exact same driver from the desktop on the laptop now.

---

### Post by MasterPoulos89 on 2009-05-26
Hello All

I have a great success story for everyone. And I am quite excited to share my success story with everyone. Uninstall everything you have done to make your life cam work. Go to the following site and install Kernel Check.  

[http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/)  

This is a program that will safely upgrade your kernel to the newest stable version which at the moment is 2.6.29.4. The web cam will then be automatically supported. Let me say again. 
             !!!!!!!!!!!!AUTOMATICALLY!!!!!!!!!!!!

At the end of the update it acted like there was a big error but it was nothing. It couldn't reconfigure my x server but after reboot I just re-enabled my Nvidia restricted drivers and rebooted again and all was good. So don't be alarmed if this happens.

The program is quite simple. Press the big button that says get kernel information then go to the top where it says Program and click Build New Kernel.

I don't know if there are any conflicts with the new kernels and other programs. I just installed it. But it is a stable version so I think were safe.

Color is not perfect but is right next to perfect.

Edit: Just like to add that the KernelCheck version from the web site may not work in Jaunty and in that case go to terminal and type:

sudo apt-get install bzr
bzr branch lp:kernelcheck
cd kernelcheck
sudo python setup.py install

Then you'll find it in applications/system tools. It should be just as simple to use.

Edit:You may want to first deactivate restricted drivers and reboot and reactivate after upgrade.

---

### Post by stu_edgar on 2009-05-27
Mmmmm, new kernel sounds a little radical :-)

I have installed latest gspca and also have green screen problem

When I start cheese using preload command dsicussed above i get htis:

libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffd9
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffd9
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 6 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 

Help?
Stu

---

### Post by leachyboy2001 on 2009-05-27
Ok, I solved my issues,  I used the identical drivers and it is now working.
The driver that is working is gspca-d8d701594f71
You also must use ```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
```
I would upload the file as an attachment but its too big and I also can't find a link to it anywhere on the internet.  If you think you need it I can email it to you, let me know!

---

### Post by MasterPoulos89 on 2009-05-27
> **leachyboy2001 said:**
> Ok, I solved my issues,  I used the identical drivers and it is now working.
The driver that is working is gspca-d8d701594f71
You also must use ```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
```
I would upload the file as an attachment but its too big and I also can't find a link to it anywhere on the internet.  If you think you need it I can email it to you, let me know!


I was under the impression that it would not happen for Jaunty. But since you got it to work say a little of how it works. 

When I got it working in intrepid it was recording so slow and the words and movements were totally off.

In Jaunty with the updated kernel it works pretty perfect except the brightness messes up a little. 

Does it go slow the way you did it or is it pretty much as it should be?

---

### Post by osterchrisi on 2009-05-27
> **MasterPoulos89 said:**
> Hello All

I have a great success story for everyone. And I am quite excited to share my success story with everyone. Uninstall everything you have done to make your life cam work. Go to the following site and install Kernel Check.  

[http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/)  

This is a program that will safely upgrade your kernel to the newest stable version which at the moment is 2.6.29.4. The web cam will then be automatically supported. Let me say again. 
             !!!!!!!!!!!!AUTOMATICALLY!!!!!!!!!!!!

At the end of the update it acted like there was a big error but it was nothing. It couldn't reconfigure my x server but after reboot I just re-enabled my Nvidia restricted drivers and rebooted again and all was good. So don't be alarmed if this happens.

The program is quite simple. Press the big button that says get kernel information then go to the top where it says Program and click Build New Kernel.

I don't know if there are any conflicts with the new kernels and other programs. I just installed it. But it is a stable version so I think were safe.

Color is not perfect but is right next to perfect.

Worked for me too, thanks! :D

---

### Post by rbolio on 2009-05-28
"kernelcheck" worked for my Vx-1000...  A few notes tho....


After attempting to intall the kernel i got this message:
* dpkg returned error code (1)  *

so i couldn't finish installing the entire kernel

However.. the webcam worked properly without any hassle....


Another heads up: you have to restart the NVIDIA drivers...


Thanks for this!

...now back to making porn....   lol jk hahaha ;D

---

### Post by MasterPoulos89 on 2009-05-28
> **rbolio said:**
> "kernelcheck" worked for my Vx-1000...  A few notes tho....


After attempting to intall the kernel i got this message:
* dpkg returned error code (1)  *

so i couldn't finish installing the entire kernel

However.. the webcam worked properly without any hassle....


Another heads up: you have to restart the NVIDIA drivers...


Thanks for this!

...now back to making porn....   lol jk hahaha ;D


I think if you deactivate your restricted drivers before install and reactivate after reboot you may not get any errors at all.

When I got that error I fresh installed and didn't activate my drivers till after new kernel was installed and no errors.

Its prob not worth reinstalling though. It sounds like a minor error.

It's your time so your choice.

---

### Post by PAFS on 2009-05-30
```
(cheese:4597): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits

(cheese:4597): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

(cheese:4597): GStreamer-WARNING **: pad video_source:src returned caps which are not a real subset of its template caps
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 6 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffd9
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffd9
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 6 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 6 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 6 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 6 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 6 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits

```

and it goes on with "bits" the thing... i'm using jaunty, today my kernel was updated from 2.6.28-11 to 2.6.28-12.. and my VX-1000 that worked perfectly, has a green screen now... anyone have an idea?? i thought about the kernel thing.. but that sounds really drastic, plus i never did something like that.

---

### Post by MasterPoulos89 on 2009-05-30
No worries. A first time Ubuntu user could update to the newest kernel thanks to KernelCheck. You just select very basic options and the program does the rest for you. 

I would Suggest deactivating any restricted drivers first and reactivate them after the kernel upgrade.

---

### Post by PAFS on 2009-05-30
yeah...i don't see another option... i'll have to update my kernel
I read this [http://ubuntuforums.org/showthread.php?t=618563](http://ubuntuforums.org/showthread.php?t=618563)
i'll deactive my nvidia drivers, and i just have a doubt about the lumen version or stable version, since i'm using jaunty, i'd go for the lumen version, but the post is from 2007, so i'm not sure if the bug for jaunty still exist or not...
did you guys use the kernelcheck lumen version? or the stable version?

---

### Post by MasterPoulos89 on 2009-05-30
> **PAFS said:**
> yeah...i don't see another option... i'll have to update my kernel
I read this [http://ubuntuforums.org/showthread.php?t=618563](http://ubuntuforums.org/showthread.php?t=618563)
i'll deactive my nvidia drivers, and i just have a doubt about the lumen version or stable version, since i'm using jaunty, i'd go for the lumen version, but the post is from 2007, so i'm not sure if the bug for jaunty still exist or not...
did you guys use the kernelcheck lumen version? or the stable version?


I used the lumen version. It worked perfectly. Nothing went wrong. No need to worry about it being a beta version.

---

### Post by PAFS on 2009-05-30
mine went wrong, and for some reason the instalation stopped, so i saw that some people had the same problem, so i decided to reboot, then i saw that i had a new kernel 2.6.29.4 option, i logged on, and it's working just fine... 
i only have some brightness problem my cam is kind of dark, but if it works that's it! no more green screen! thank you MarsterPoulos89!

---

### Post by MasterPoulos89 on 2009-05-30
Mine had no problems. and It did not ask what kernel to use either. It automatically used newest. Guess I just got lucky. Also I fixed the brightness problem. Here is how.

I may be pushing it a little now but I fresh installed then upgraded to Karmic Koala. I know its in its alpha 1 stage but its uses the new kernel by default and has an updated cheese program with color controls (Brightness, Contrast and Hue). So you can set it to look as perfect as possible.

So far I have had no problems at all as far as crashes and I've yet to see any bugs. I'm sure I will as it updates but I'm still sticking with 9.10.

If you are ganna upgrade I recommend not using the alpha cd. It did not work. What works is typing in terminal:

update-manager --devel

The update manager shows up and shows 9.10 on top. Select upgrade.

Edit: Chances are you would just like the updated cheese version in Jaunty. Not sure if that's possible but I found the .deb package for cheese 2.27.2. 
Here is the site to download it. [http://packages.ubunut.com/hu/karmic/gnome/cheese](http://packages.ubunut.com/hu/karmic/gnome/cheese) Download from bottom of the page. Maybe it will work in Jaunty.

---

### Post by dave6779 on 2009-06-04
Hey i tried the install on jaunty, but no luck. It says there's a problem with dependencies. I might upgrade to 9.10. Hopefully there's no crash bugs. Still i've got it dual booting to windows if there's a problem. I'd rather no use windows tho. Let me know if you come across any bugs in 9.10 and i'll do the same.

Dave

---

### Post by MasterPoulos89 on 2009-06-05
> **dave6779 said:**
> Hey i tried the install on jaunty, but no luck. It says there's a problem with dependencies. I might upgrade to 9.10. Hopefully there's no crash bugs. Still i've got it dual booting to windows if there's a problem. I'd rather no use windows tho. Let me know if you come across any bugs in 9.10 and i'll do the same.

Dave



Firefox has crashed a couple of times but when you reopen it it restores your previous settings. Other then that everything seems to be working fine for now.

Also the method I mentioned above to upgrade may not be the best way to upgrade. It may give an error or say partial upgrade only. Another way that should work better is to first type in terminal:

sudo gedit /etc/apt/sources.list

then go to search/replace. Where it says "Search for" type: jaunty
Where it says "Replace with" type: karmic

Then type in terminal:

sudo apt-get update
sudo apt-get dist-upgrade

So far everything seems pretty good.

---

### Post by crazyfuturamanoob on 2009-06-07
> **MasterPoulos89 said:**
> Hello All

I have a great success story for everyone. And I am quite excited to share my success story with everyone. Uninstall everything you have done to make your life cam work. Go to the following site and install Kernel Check.  

[http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/)  

This is a program that will safely upgrade your kernel to the newest stable version which at the moment is 2.6.29.4. The web cam will then be automatically supported. Let me say again. 
             !!!!!!!!!!!!AUTOMATICALLY!!!!!!!!!!!!

At the end of the update it acted like there was a big error but it was nothing. It couldn't reconfigure my x server but after reboot I just re-enabled my Nvidia restricted drivers and rebooted again and all was good. So don't be alarmed if this happens.

The program is quite simple. Press the big button that says get kernel information then go to the top where it says Program and click Build New Kernel.

I don't know if there are any conflicts with the new kernels and other programs. I just installed it. But it is a stable version so I think were safe.

Color is not perfect but is right next to perfect.

Edit: Just like to add that the KernelCheck version from the web site may not work in Jaunty and in that case go to terminal and type:

sudo apt-get install bzr
bzr branch lp:kernelcheck
cd kernelcheck
sudo python setup.py install

Then you'll find it in applications/system tools. It should be just as simple to use.

Edit:You may want to first deactivate restricted drivers and reactivate after upgrade.

My VX1000 didn't work at all out of box. It wasn't even detected. But my laptop's built-in webcam worked great. I tried compiling and installing gspca from source. Device detected, but green picture in cheese. Removed gspca, and tried that kernel thing. It reported some kind of error, rebooted, and now neither the built in webcam nor VX1000 aren't detected. Is there some way to undo this kernel mess?

---

### Post by MasterPoulos89 on 2009-06-09
> **crazyfuturamanoob said:**
> My VX1000 didn't work at all out of box. It wasn't even detected. But my laptop's built-in webcam worked great. I tried compiling and installing gspca from source. Device detected, but green picture in cheese. Removed gspca, and tried that kernel thing. It reported some kind of error, rebooted, and now neither the built in webcam nor VX1000 aren't detected. Is there some way to undo this kernel mess?



If you want to use your previous kernel first install StartUp-Manager. Type in terminal:

sudo apt-get install startupmanager

then go to System/Administration/StartUp-Manager

then where it says Default operating system choose the kernel you want to use.

I don't know about removing the kernel. Maybe someone else can help with that. But using the previous one should be just as good.

I have lifecam vx-3000 and it worked better then ever before with the new kernel and I had no problems with the kernel upgrade. I thought others may have my same success but I guess not.

Maybe it doesn't work with vx-1000. IDK.

---

### Post by crazyfuturamanoob on 2009-06-09
> **MasterPoulos89 said:**
> If you want to use your previous kernel first install StartUp-Manager. Type in terminal:

sudo apt-get install startupmanager

then go to System/Administration/StartUp-Manager

then where it says Default operating system choose the kernel you want to use.

I don't know about removing the kernel. Maybe someone else can help with that. But using the previous one should be just as good.

I have lifecam vx-3000 and it worked better then ever before with the new kernel and I had no problems with the kernel upgrade. I thought others may have my same success but I guess not.

Maybe it doesn't work with vx-1000. IDK.

There is only 3 options in grub. Ubuntu, recovery mode and memtest. No previous kernel, because I got this in my /boot/grub/menu.lst:
```

# howmany=1

```

---

### Post by jesterthejedi on 2009-06-09
What version does it report? I am thinking your kernel was not updated. You can always try the trick I posted earlier to build the driver, I have had it working for months from that time. If you get the greens, you need to use the LD=preload trick for the app.

My previous attempt with the first howto in the beginning of this post NEVER worked for me, this did:

The EASY Method :)
Download driver:
[http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/)
grab the .bz2 file (top of page little text link called bz2)
extract archive (you can extract with nautilus)
in terminal "cd /Desktop/gspca" + <TAB> or exact name <ENTER>
in terminal type "make" no quotes takes about 5 mins
then type "sudo make install"
reboot

tested working on Intrepid With Cheese, Ekiga, Skype, GyachE, Xawtv

COLORS are fine! no more green/blue Hardy mess.
not working in Camorama, Camstream, errors in gqcam (requires LD preload trick)
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

installed xawtv, luvcview, and removed camserv.

---

### Post by crazyfuturamanoob on 2009-06-09
> **jesterthejedi said:**
> What version does it report? I am thinking your kernel was not updated. You can always try the trick I posted earlier to build the driver, I have had it working for months from that time. If you get the greens, you need to use the LD=preload trick for the app.

My previous attempt with the first howto in the beginning of this post NEVER worked for me, this did:

The EASY Method :)
Download driver:
[http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/)
grab the .bz2 file (top of page little text link called bz2)
extract archive (you can extract with nautilus)
in terminal "cd /Desktop/gspca" + <TAB> or exact name <ENTER>
in terminal type "make" no quotes takes about 5 mins
then type "sudo make install"
reboot

tested working on Intrepid With Cheese, Ekiga, Skype, GyachE, Xawtv

COLORS are fine! no more green/blue Hardy mess.
not working in Camorama, Camstream, errors in gqcam (requires LD preload trick)
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

installed xawtv, luvcview, and removed camserv.

I got the built-in camera working again. But still green screen with VX1000. LD_PRELOAD doesn't change anything. Kernel probably got updated because it spent 3 hours compiling the kernel.

```

arho@arho-laptop:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

(cheese:6665): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffd9
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff

(cheese:6665): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

(cheese:6665): GStreamer-WARNING **: pad video_source:src returned caps which are not a real subset of its template caps
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4l2: error requesting 4 buffers: Invalid argument

(cheese:6665): GStreamer-WARNING **: pad video_source:src returned caps which are not a real subset of its template caps
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 6 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits

```

---

### Post by MasterPoulos89 on 2009-06-12
This wont really help anyone without a working cam but for anyone who got their cam working may find this useful.

I managed to get the new Cheese version (Cheese 2.27.2) to install in jaunty.

The new version has color controls such as Brightness Contrast Saturation and Hue.

I made a script that downloads and installs Cheese 2.27.2 and all its dependencies.

I'm uploading the script to this post.

To install extract it go into the folder and just double click the "Install Cheese 2.27.2" file and click run in terminal. You may need to put in you password and press "y" when it asks to install dependencies. When its done the terminal will close.

When it's done you'll find Cheese in Sound and Video instead of in Graphics. I guess you can move it if you like.

Edit: It may install more dependencies then needed but most of them are from synoptic package manager so there stable.

Edit: I should also mention that this does not update gnome. It just installs the updated cheese version and 3 other dependensies. The only difference you should notice is you have the updated cheese version.

---

### Post by DLHmatt on 2009-06-16
> **MasterPoulos89 said:**
> Hello All

I have a great success story for everyone. And I am quite excited to share my success story with everyone. Uninstall everything you have done to make your life cam work. Go to the following site and install Kernel Check.  

[http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/)  

This is a program that will safely upgrade your kernel to the newest stable version which at the moment is 2.6.29.4. The web cam will then be automatically supported. Let me say again. 
             !!!!!!!!!!!!AUTOMATICALLY!!!!!!!!!!!!

At the end of the update it acted like there was a big error but it was nothing. It couldn't reconfigure my x server but after reboot I just re-enabled my Nvidia restricted drivers and rebooted again and all was good. So don't be alarmed if this happens.

The program is quite simple. Press the big button that says get kernel information then go to the top where it says Program and click Build New Kernel.

I don't know if there are any conflicts with the new kernels and other programs. I just installed it. But it is a stable version so I think were safe.

Color is not perfect but is right next to perfect.

Edit: Just like to add that the KernelCheck version from the web site may not work in Jaunty and in that case go to terminal and type:

sudo apt-get install bzr
bzr branch lp:kernelcheck
cd kernelcheck
sudo python setup.py install

Then you'll find it in applications/system tools. It should be just as simple to use.

Edit:You may want to first deactivate restricted drivers and reboot and reactivate after upgrade.

sorry i am a novice. i tried the install both ways as you stated and it wont run. i am running 9.04 with kernal 2.6.28-11-generic and gnome2.26.1

laptop:~$ sudo kernelcheck
Traceback (most recent call last):
  File "/usr/local/bin/kernelcheck", line 11, in <module>
    from KernelCheck.constants import *
ImportError: No module named constants

---

### Post by MasterPoulos89 on 2009-06-17
> **DLHmatt said:**
> sorry i am a novice. i tried the install both ways as you stated and it wont run. i am running 9.04 with kernal 2.6.28-11-generic and gnome2.26.1

laptop:~$ sudo kernelcheck
Traceback (most recent call last):
  File "/usr/local/bin/kernelcheck", line 11, in <module>
    from KernelCheck.constants import *
ImportError: No module named constants


I don't know why KernelCheck didn't install properly for you. Make sure all the lines are entered through terminal. Enter them in one line at a time.
```
sudo apt-get install bzr

bzr branch lp:kernelcheck

cd kernelcheck

sudo python setup.py install
```

Then you should see a shortcut in Applications/System Tools/KernelCheck.

If it still doesn't work for you then I don't know why.

---

### Post by MasterPoulos89 on 2009-06-17
^

---

### Post by DLHmatt on 2009-06-17
> **MasterPoulos89 said:**
> I don't know why KernelCheck didn't install properly for you. Make sure all the lines are entered through terminal. Enter them in one line at a time.
```
sudo apt-get install bzr

bzr branch lp:kernelcheck

cd kernelcheck

sudo python setup.py install
```

Then you should see a shortcut in Applications/System Tools/KernelCheck.

If it still doesn't work for you then I don't know why.

yeah man its there. when i click it i am asked to enter my admin password then it just wont start. when i try starting it from terminal i get what i posted. i copy and pasted each line you posted and it said everything installed and the shortcut is in my applications/system tools.

i even tried virtualbox and my itouch works but a stupid webcam wont.

<edit > seems to be because i haven't set up my launchpad login...
set that up and still no go still the same error message in terminal when i try and run it.

<EDIT> got it! had to purge it and reinstall it again.

---

### Post by DLHmatt on 2009-06-17
ok so kernel check worked and i have great picture in cheese. but skype is just green and crap scrolling.

---

### Post by MasterPoulos89 on 2009-06-17
> **DLHmatt said:**
> ok so kernel check worked and i have great picture in cheese. but skype is just green and crap scrolling.


I don't use skype but somewhere in this thread was mentioned a command to type in everytime that may help skype recognise the cam.

One of the following commands may help
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```

If it works you can make a script with the command as others have done so you don't have to type it in everytime.

---

### Post by DLHmatt on 2009-06-17
> **MasterPoulos89 said:**
> I don't use skype but somewhere in this thread was mentioned a command to type in everytime that may help skype recognise the cam.

One of the following commands may help
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```

If it works you can make a script with the command as others have done so you don't have to type it in everytime.

thanks a million man! i got everything like it should be now :D

---

### Post by paul_r on 2009-06-17
I have a Lifecam 5000 and I can get a clear picture using mplayer.

```
mplayer tv:///
```

If you have multiple video inputs, you need to specify this in the mplayer config file.

Edit ~/.mplayer/config

```
tv=device=/dev/video1
```

There is a beta screen capture on google code for linux though I couldn't get it to work (which lets you select a portion of screen) and then of course gstfakevideo to port to an app. Otherwise with mplayer you can record input whathaveyou.

---

### Post by MasterPoulos89 on 2009-06-20
Also I would like to add, I think some people may have gotten an error from the new kernel upgrade using kernelcheck because after deactivating restricted drivers you may not of rebooted.

If this is the case then you could try again. I don't know how to roll back the kernel version but you could fresh install and before activating restricted drivers you could first update the kernel then activate drivers on reboot.

If your upgrading to the new kernel for the first time first deactivate any restricted drivers you may have then reboot. Then upgrade kernel then reboot then activate drivers.

I Hope that stops anyone from running into errors.

---

### Post by kandrejk on 2009-06-22
Hey all I am brand new to running Ubuntu as a day-to-day desktop, and I have been trying to get my Vx-3000 working.

Has anyone tried running the new Kernelcheck Lumen released 6/20/09 yet? if so does this confirm that this is a fix for making the VX-3000 work in Jaunty?

Thanks

---

### Post by tuiger on 2009-06-24
Kernelcheck work for me fine. Kernel Linux 2.6.30-candela I've runing now.[http://ubuntuforums.org/images/smilies/icon_biggrin.gif](http://ubuntuforums.org/images/smilies/icon_biggrin.gif)

---

### Post by sansor on 2009-06-25
The cam works with the new kernel. The quality is the same as the gspca driver posted in this thread before. 

I would suggest installing the gspca driver and wait for ubuntu to include the kernel 2.6.30 as an update and install from the repos since compiling new kernel might require some modifications and you might have a system without proper graphics card driver.

Or, maybe ubuntu people may help kernelcheck become a program which updates the kernel with less effort.

---

### Post by MasterPoulos89 on 2009-06-27
I found a much better solution for upgrading the kernel.

Go to the following site:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/)

You need 3 files. It has i386 and amd64 .deb packages.

You need the 2 linux-header files and the linux-image file.

You do not need the linux-source file.

If you don't know if you use i386 or amd64 then chances are you use i386.

If any say missing dependencies then install one of the others first then go back to that one.

This will install kernel 2.6.30rc3.

Don't worry, it seems to work perfectly and installs quickly unlike with kernel-check.

If you want to upgrade your kernel the is an easier way to do so.

And the Microsoft Lifecam still works perfectly.

For those of you who already upgraded with kernel-check can probably still install this newer version because it is an update.

Hope this is helpfull.

---

### Post by limmer on 2009-07-06
I can confirm that the fix above works great! No more grain or green capture image and works MUCH faster than kernalcheck (which would take ~2-4 hours to compile the new kernal).

---

### Post by freackout on 2009-07-13
> **HQLCD said:**
> Is it possible to make How to make Microsoft LifeCam VX-3000 work in Ubuntu? How?

buy a logitech quickcam pro 9000 its uvc compatible ie works plug n play linux no modules/drivers needed but you will have to plug it in each time you want to use it (once) after booting. unless giving commands to see it whenever.

---

### Post by mplexus on 2009-08-03
Just installed 2.6.30.4 and I have a black screen just when gnome was supposed to load. I sense everything works fine except the nvidia driver.

EDIT: finally, after disabling the nvidia driver (now i use "nv" in /etc/X11/xorg.conf) the VX1000 actually does work with kernel 2.6.30, module gspca_sonixj and the LD_PRELOAD trick mentioned above. I should try to re-enable the nvidia driver..

---

### Post by Creap on 2009-09-02
It works for me in Jaunty with 2.6.28-15-generic, in Skype as well, but I get no sound from the built-in microphone. I have enabled the microphone everywhere in the sound mixer, but nothing. Any ideas?

(deal breaker to get the girlfriend to stay on Linux is that she can Skype..)

---

### Post by Kawaiii on 2009-09-08
I managed to get the VX-3000 to work with Ekiga, but I am trying to make it work with pidgin.

I can't seem to bring up the option for video in pidgin, when talking to someone on google talk that I know supports it. They tell me that they get the error that my "OS doesn't support it".  I'm running the newest version of pidgin.  What am I missing?

---

### Post by stanca on 2009-10-07
sudo apt-get install subversion build-essential linux-headers-$(uname -r) && wget [http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2) && tar xf tip.tar.bz2 && cd gspca-* && make && sudo make install && sudo depmod -ae $(uname -r) ;)

---

### Post by underboom on 2009-10-31
> **stanca said:**
> sudo apt-get install subversion build-essential linux-headers-$(uname -r) && wget [http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2]("http://linuxtv.org/hg/%7Ejfrancois/gspca/archive/tip.tar.bz2") && tar xf tip.tar.bz2 && cd gspca-* && make && sudo make install && sudo depmod -ae $(uname -r) ;)

Not work on  9.10 32 bit  :( very bad. I have  green screen in all application .

---

### Post by dhaynie on 2009-11-01
Hello,

Was wondering if any help or insight could be provided. I followed the instructions about getting bz2 file from jfrancois and installing. here is output.```
dave@dave:~$ cd Desktop
dave@dave:~/Desktop$ ls
gspca-10a3d7d4646d
dave@dave:~/Desktop$ ls 
gspca-10a3d7d4646d
dave@dave:~/Desktop$ cd gspca-10a3d74646d
bash: cd: gspca-10a3d74646d: No such file or directory
dave@dave:~/Desktop$ cd gspca-10a3d7d4646d
dave@dave:~/Desktop/gspca-10a3d7d4646d$ make
make -C /home/dave/Desktop/gspca-10a3d7d4646d/v4l 
make[1]: Entering directory `/home/dave/Desktop/gspca-10a3d7d4646d/v4l'
No version yet, using 2.6.31-14-generic
make[1]: Leaving directory `/home/dave/Desktop/gspca-10a3d7d4646d/v4l'
make[1]: Entering directory `/home/dave/Desktop/gspca-10a3d7d4646d/v4l'
scripts/make_makefile.pl
Updating/Creating .config
Preparing to compile for kernel version 2.6.31

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.

If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.

Vanilla kernels are available at http://kernel.org.
On most distros, this will compile a newly downloaded kernel:

cp /boot/config-`uname -r` <your kernel dir>/.config
cd <your kernel dir>
make all modules_install install

Please see your distro's web site for instructions to build a new kernel.

Created default (all yes) .config file
./scripts/make_myconfig.pl
make[1]: Leaving directory `/home/dave/Desktop/gspca-10a3d7d4646d/v4l'
make[1]: Entering directory `/home/dave/Desktop/gspca-10a3d7d4646d/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.31-14-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
ln -sf . oss
make -C firmware prep
make[2]: Entering directory `/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firmware'
make[2]: Leaving directory `/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firmware'
  CC  ihex2fw
Generating vicam/firmware.fw
Generating dabusb/firmware.fw
Generating dabusb/bitstream.bin
Generating ttusb-budget/dspbootcode.bin
Generating cpia2/stv0672_vp4.bin
Generating av7110/bootcode.bin
make[2]: Leaving directory `/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firmware'
Kernel build directory is /lib/modules/2.6.31-14-generic/build
make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/dave/Desktop/gspca-10a3d7d4646d/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/tuner-xc2028.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/tuner-simple.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/tuner-types.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/mt20xx.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/tda8290.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/tea5767.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/tea5761.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/tda9887.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/tda827x.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/au0828-core.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/au0828-i2c.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/au0828-cards.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/au0828-dvb.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/au0828-video.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/au8522_dig.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/au8522_decoder.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/flexcop-pci.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/flexcop-usb.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/flexcop.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/flexcop-fe-tuner.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/flexcop-i2c.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/flexcop-sram.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/flexcop-eeprom.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/flexcop-misc.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/flexcop-hw-filter.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/flexcop-dma.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/bttv-driver.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/bttv-cards.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/bttv-if.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/bttv-risc.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/bttv-vbi.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/bttv-i2c.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/bttv-gpio.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/bttv-input.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/bttv-audio-hook.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cpia2_v4l.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cpia2_usb.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cpia2_core.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx18-driver.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx18-cards.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx18-i2c.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx18-firmware.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx18-gpio.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx18-queue.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx18-streams.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx18-fileops.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx18-ioctl.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx18-controls.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx18-mailbox.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx18-vbi.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx18-audio.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx18-video.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx18-irq.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx18-av-core.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx18-av-audio.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx18-av-firmware.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx18-av-vbi.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx18-scb.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx18-dvb.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx18-io.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx231xx-audio.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx231xx-video.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx231xx-i2c.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx231xx-cards.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx231xx-core.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx231xx-avcore.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx231xx-pcb-cfg.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx231xx-vbi.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx23885-cards.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx23885-video.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx23885-vbi.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx23885-core.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx23885-i2c.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx23885-dvb.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx23885-417.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx23885-ioctl.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx23885-ir.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx23885-input.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx23888-ir.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/netup-init.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cimax2.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/netup-eeprom.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx25840-core.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx25840-audio.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx25840-firmware.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx25840-vbi.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx88-video.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx88-vbi.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx88-mpeg.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx88-cards.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx88-core.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx88-i2c.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx88-tvaudio.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx88-dsp.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cx88-input.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dvbdev.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dmxdev.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dvb_demux.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dvb_filter.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dvb_ca_en50221.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dvb_frontend.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dvb_net.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dvb_ringbuffer.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dvb_math.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/av7110_hw.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/av7110_v4l.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/av7110_av.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/av7110_ca.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/av7110.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/av7110_ipack.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/av7110_ir.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/a800.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/af9005-remote.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/af9005.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/af9005-fe.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/af9015.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/anysee.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/au6610.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/ce6230.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cinergyT2-core.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cinergyT2-fe.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/cxusb.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dib0700_core.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dib0700_devices.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dibusb-common.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dibusb-mb.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dibusb-mc.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/digitv.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dtt200u.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dtt200u-fe.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dtv5100.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dw2102.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/friio.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/friio-fe.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/gl861.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/gp8psk.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/gp8psk-fe.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/m920x.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/nova-t-usb2.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/opera1.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/ttusb2.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/umt-010.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/vp702x.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/vp702x-fe.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/vp7045.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/vp7045-fe.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dvb-usb-firmware.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dvb-usb-init.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dvb-usb-urb.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dvb-usb-i2c.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dvb-usb-dvb.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/dvb-usb-remote.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/usb-urb.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/pt1.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/va1j5jf8007s.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/va1j5jf8007t.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/em28xx-audio.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/em28xx-video.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/em28xx-i2c.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/em28xx-cards.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/em28xx-core.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/em28xx-input.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/em28xx-vbi.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/et61x251_core.o
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/et61x251_core.c: In function 'et61x251_ioctl_v4l2':
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/et61x251_core.c:2493: warning: the frame size of 1408 bytes is larger than 1024 bytes
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/et61x251_tas5130d1b.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-avc.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-ci.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-dvb.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-fe.o
  CC [M]  /home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.o
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:22:21: error: csr1212.h: No such file or directory
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:23:23: error: highlevel.h: No such file or directory
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:24:19: error: hosts.h: No such file or directory
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:25:22: error: ieee1394.h: No such file or directory
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:26:17: error: iso.h: No such file or directory
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:27:21: error: nodemgr.h: No such file or directory
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:37: warning: 'struct hpsb_iso' declared inside parameter list
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:37: warning: its scope is only this definition or declaration, which is probably not what you want
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c: In function 'rawiso_activity_cb':
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:53: error: dereferencing pointer to incomplete type
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:54: error: implicit declaration of function 'hpsb_iso_n_ready'
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:61: error: dereferencing pointer to incomplete type
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:62: error: implicit declaration of function 'dma_region_i'
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:62: error: dereferencing pointer to incomplete type
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:62: error: expected expression before 'unsigned'
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:63: warning: assignment makes pointer from integer without a cast
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:64: error: dereferencing pointer to incomplete type
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:68: error: dereferencing pointer to incomplete type
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:82: error: implicit declaration of function 'hpsb_iso_recv_release_packets'
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c: In function 'node_of':
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:87: error: dereferencing pointer to incomplete type
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:87: warning: type defaults to 'int' in declaration of '__mptr'
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:87: warning: initialization from incompatible pointer type
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:87: error: invalid use of undefined type 'struct unit_directory'
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c: In function 'node_lock':
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:92: error: implicit declaration of function 'hpsb_node_lock'
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:92: error: 'EXTCODE_COMPARE_SWAP' undeclared (first use in this function)
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:92: error: (Each undeclared identifier is reported only once
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:92: error: for each function it appears in.)
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:93: error: 'quadlet_t' undeclared (first use in this function)
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:93: error: expected ')' before 'arg'
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c: In function 'node_read':
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:98: error: implicit declaration of function 'hpsb_node_read'
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c: In function 'node_write':
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:103: error: implicit declaration of function 'hpsb_node_write'
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c: In function 'start_iso':
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:114: error: implicit declaration of function 'hpsb_iso_recv_init'
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:114: error: dereferencing pointer to incomplete type
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:116: error: 'HPSB_ISO_DMA_DEFAULT' undeclared (first use in this function)
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:118: warning: assignment makes pointer from integer without a cast
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:125: error: implicit declaration of function 'hpsb_iso_recv_start'
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:128: error: implicit declaration of function 'hpsb_iso_shutdown'
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c: In function 'stop_iso':
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:139: error: implicit declaration of function 'hpsb_iso_stop'
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c: At top level:
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:154: warning: 'struct hpsb_host' declared inside parameter list
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c: In function 'fcp_request':
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:167: error: dereferencing pointer to incomplete type
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:168: error: dereferencing pointer to incomplete type
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c: In function 'node_probe':
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:182: error: dereferencing pointer to incomplete type
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:182: warning: type defaults to 'int' in declaration of '__mptr'
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:182: warning: initialization from incompatible pointer type
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:182: error: invalid use of undefined type 'struct unit_directory'
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:187: error: dereferencing pointer to incomplete type
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:187: error: 'quadlet_t' undeclared (first use in this function)
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:188: error: implicit declaration of function 'CSR1212_TEXTUAL_DESCRIPTOR_LEAF_DATA'
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:188: error: dereferencing pointer to incomplete type
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:188: warning: assignment makes pointer from integer without a cast
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c: At top level:
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:243: warning: 'struct unit_directory' declared inside parameter list
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c: In function 'node_update':
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:245: error: dereferencing pointer to incomplete type
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c: At top level:
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:253: error: variable 'fdtv_driver' has initializer but incomplete type
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:254: error: unknown field 'name' specified in initializer
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:254: warning: excess elements in struct initializer
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:254: warning: (near initialization for 'fdtv_driver')
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:255: error: unknown field 'update' specified in initializer
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:255: warning: excess elements in struct initializer
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:255: warning: (near initialization for 'fdtv_driver')
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:256: error: unknown field 'driver' specified in initializer
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:256: error: extra brace group at end of initializer
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:256: error: (near initialization for 'fdtv_driver')
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:259: warning: excess elements in struct initializer
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:259: warning: (near initialization for 'fdtv_driver')
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:262: error: variable 'fdtv_highlevel' has initializer but incomplete type
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:263: error: unknown field 'name' specified in initializer
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:263: warning: excess elements in struct initializer
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:263: warning: (near initialization for 'fdtv_highlevel')
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:264: error: unknown field 'fcp_request' specified in initializer
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:264: warning: excess elements in struct initializer
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:264: warning: (near initialization for 'fdtv_highlevel')
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c: In function 'fdtv_1394_init':
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:271: error: implicit declaration of function 'hpsb_register_highlevel'
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:272: error: invalid use of undefined type 'struct hpsb_protocol_driver'
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:273: error: implicit declaration of function 'hpsb_register_protocol'
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:276: error: implicit declaration of function 'hpsb_unregister_highlevel'
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.c:283: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/dave/Desktop/gspca-10a3d7d4646d/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/dave/Desktop/gspca-10a3d7d4646d/v4l'
make: *** [all] Error 2
dave@dave:~/Desktop/gspca-10a3d7d4646d$ sudo make install
[sudo] password for dave: 
make -C /home/dave/Desktop/gspca-10a3d7d4646d/v4l install
make[1]: Entering directory `/home/dave/Desktop/gspca-10a3d7d4646d/v4l'
-e 
Removing obsolete files from /lib/modules/2.6.31-14-generic/kernel/drivers/media/video:

-e 
Removing obsolete files from /lib/modules/2.6.31-14-generic/kernel/drivers/media/dvb/cinergyT2:

-e 
Removing obsolete files from /lib/modules/2.6.31-14-generic/kernel/drivers/media/dvb/frontends:

Installing kernel modules under /lib/modules/2.6.31-14-generic/kernel/drivers/media/:
/sbin/depmod -a 2.6.31-14-generic 
make -C firmware install
make[2]: Entering directory `/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firmware'
Installing firmwares at /lib/firmware: vicam/firmware.fw dabusb/firmware.fw dabusb/bitstream.bin ttusb-budget/dspbootcode.bin cpia2/stv0672_vp4.bin av7110/bootcode.bin 
make[2]: Leaving directory `/home/dave/Desktop/gspca-10a3d7d4646d/v4l/firmware'
make[1]: Leaving directory `/home/dave/Desktop/gspca-10a3d7d4646d/v4l'
dave@dave:~/Desktop/gspca-10a3d7d4646d$ 
```

Ayn help would be appreciated. Running a Vx-3000 in Karmic and can only get green screen. Changed my kernel last night to an earlier kernel to try and make it work and it killed my system, my  2.6.31-14-generic kernel would not boot, the older 2.6.30-rc3 kernel would work and boot, but would not have sound in any app. Reformatted and reinstalled 9.10. Tried again, following instructions completely, and to no avail. 

Weird because I was just able to make it work just fine 2 days ago usign jfrancois' drivers and jaunty. But I love Karmic, don't want to go back or dual boot really. Will dual boot if I need to.

---

### Post by daniroma on 2009-11-02
It's happening to me!
in /home/dave/Desktop/gspca-10a3d7d4646d/v4l
# cd v4l
# make all
# make install

then I edited /etc/modprobe.d/blacklist-custom and added:
blacklist sn9c102

# reboot

If it still make problems try to :

cd gspca-*/linux/drivers/media/dbv/firewire
and edit Makefile as in image as follows:
##obj-$(CONFIG_DVB_FIREDTV) += firedtv.o

##firedtv-y := firedtv-avc.o firedtv-ci.o firedtv-dvb.o firedtv-fe.o
##firedtv-$(CONFIG_DVB_FIREDTV_IEEE1394) += firedtv-1394.o
##firedtv-$(CONFIG_DVB_FIREDTV_INPUT)    += firedtv-rc.o

##ccflags-y += -Idrivers/media/dvb/dvb-core
##ccflags-$(CONFIG_DVB_FIREDTV_IEEE1394) += -Idrivers/ieee1394

For me it Works!

---

### Post by lilie on 2009-11-03
> **jesterthejedi said:**
> What version does it report? I am thinking your kernel was not updated. You can always try the trick I posted earlier to build the driver, I have had it working for months from that time. If you get the greens, you need to use the LD=preload trick for the app.

My previous attempt with the first howto in the beginning of this post NEVER worked for me, this did:

The EASY Method :)
Download driver:
[http://linuxtv.org/hg/~jfrancois/gspca/]("http://linuxtv.org/hg/%7Ejfrancois/gspca/")
grab the .bz2 file (top of page little text link called bz2)
extract archive (you can extract with nautilus)
in terminal "cd /Desktop/gspca" + <TAB> or exact name <ENTER>
in terminal type "make" no quotes takes about 5 mins
then type "sudo make install"
reboot

tested working on Intrepid With Cheese, Ekiga, Skype, GyachE, Xawtv

COLORS are fine! no more green/blue Hardy mess.
not working in Camorama, Camstream, errors in gqcam (requires LD preload trick)
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

installed xawtv, luvcview, and removed camserv.

Hi Jesterthejedi and daniroma, 

I think that you could solve my problem. It is pretty much the same problem as 4ny0n3 (cf page 4 , Aprith 6th, 2009).

I have a Ubuntu distrib , GNOME, v2.24.1
And a webcam LifeCam VX-3000

I tried Jesterthejedi's Easy Method, doesn't work at first.

Then I did as daniroma told (today) : 
> **daniroma said:**
> It's happening to me!
in /home/dave/Desktop/gspca-10a3d7d4646d/v4l
# cd v4l
# make all
# make install

then I edited /etc/modprobe.d/blacklist-custom and added:
blacklist sn9c102

# reboot

If it still make problems try to :



Then, my webcam was recognized, and with Camorama or Skype, LD_PRELOAD=... command or not, the image is like grey black white lines, and in Camorama "Unable to capture image"

I can't make the last lines written by daniroma because I don't find the repertory /linux/drivers/media/dbv/firewire


Thak you for your help


__

---

### Post by Arup on 2009-11-03
I have a iBall C12.0 which is essentialy a MS VX-6000 with LED lights. It has the same Microdia chipset. Earlier on I was using compiled drivers from Google Microdia project, the image was nothing to talk about but at least it was passable and most important, the led worked. Now with Karmic, the kernel supports the cam out of box, sad part is that the driver is just not capable in any way, the LEDs stopped working. The image is just too dark, fixing it with v4l2ucp or xawtv either brightens the image out and washes it totally or it remains dark. The exposure values just can't be set right. Color cast is another permanent issue, it can never balance itself. I seriously think the drivers are getting the wrong parameters from the chip. Hope they get it right in the next kernel.

---

### Post by daniroma on 2009-11-04
Hi Lilie!
Second solution I gave to [dhaynie]("http://ubuntuforums.org/member.php?u=943714") is for his problem : error on compiling firedtv - 1394.c

In your case the driver installation was OK? - without any errors?
Your web cam works well in skype with "LD_PRELOAD=..."?

---

### Post by lilie on 2009-11-05
Hi Daniroma


The driver installation was okay : no warning, no error

About the webcam in skype with "LD_PRELOAD = ...", the view is very bad : just a grey square .. The command puts the following lines, which I can't solve ..


laptop:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
Starting the process...
Skype Xv: Xv ports available: 16
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 57


Thank you

---

### Post by daniroma on 2009-11-05
Hi lilie.
Apparently you use bluetooth devices. If so, please specify.
If not: try to disable bluetooth from "Services that start when system starts" - find in "Preferences" menu. Then reboot.

Have you installed cheese? or any program that handle web cam, other than skype?
Are these programs work well (can you see image?).

---

### Post by lilie on 2009-11-05
I don't want to use bluetooth, so I deactivated it.
After rebooting, command lines when trying to start skype are as following, and the image is also a grey square :

> laptop:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Starting the process...
Skype Xv: Xv ports available: 16
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 57


I didn't managed to install cheese software.. Not able to launch "make" command
The other software that I've got is Camorama which says "Not able to capture image"

---

### Post by daniroma on 2009-11-06
> **lilie said:**
> I don't want to use bluetooth, so I deactivated it.
After rebooting, command lines when trying to start skype are as following, and the image is also a grey square :



I didn't managed to install cheese software.. Not able to launch &quot;make&quot; command
The other software that I've got is Camorama which says &quot;Not able to capture image&quot;

 Maybe this will help you: [http://ubuntuforums.org/archive/index.php/t-997807.html](http://ubuntuforums.org/archive/index.php/t-997807.html)

---

### Post by stanca on 2009-11-07
It doesn't work for me too in the new Karmic and I tried all the known ways,tips and tricks.

---

### Post by daniroma on 2009-11-08
Hi Stanca.
I use new Karmic Koala 9.10. It works for me with a little bit change of your solution.
sudo apt-get install subversion build-essential linux-headers-$(uname -r)go to site 
[http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2) Download ”tip.tar.bz2” file.
Untar it. You will have one folder named gspca*.
cd gspca*/v4l (* = rest of folder name)
make all
sudo make install

Note: **1** You can configure drivers you may want to install:
sudo apt-get install subversion build-essential linux-headers-$(uname -r) 
~/gspca-18a214ccf825$ make menuconfig
now choose options for suitable drivers.
just be sure you choose gspca and sonixj
**2 **I am Romanian too. Daca iti este mai usor, putem discuta. Si eu am instalat destul de greu camera asta. Dar informatiile tale mi-au fost de un real folos.

---

### Post by tuiger on 2009-11-08
Hi helpers

I tried 4 weeks ago Stancas version [http://ubuntuforums.org/showpost.php?p=8065893&postcount=104]("http://ubuntuforums.org/showpost.php?p=8065893&postcount=104"), but it didnt work out for me.
Can anyone tell me what (uname -r) means?

And if I donload [http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2]("http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2"), I get allway this gspca-d02c6bb76ff43tar.bz2 driver.

An other thing is, if unpack this .tar, I don't get a gspca-FOLDDER. It opens just all the files in my departure-folder and I get no v4l- file only
v4l2.

I hope somebody can help me


thank u  tuiger

---

### Post by daniroma on 2009-11-09
Hi Tuiger!

When you click your gspca-d02c6bb76ff43tar.bz2 file, file roller or any program  that handles archives should open and you should see a folder named same as file. Opening this folder should see files and folder tree. In this tree you should see **v4l** folder.
Check file roller options to unzip files as in archive.

---

### Post by timjohn7 on 2009-11-09
After considering the manhours that I spent trying to get this camera to work under Ubuntu in all the various applications (Skype, Cheese, wxcam) I found that the best solution was to buy a Logitech webcam.

---

### Post by tuiger on 2009-11-09
The gspca-89baaa2d664b3tar3bz2 from Stanca:

In the gspca-89baaa2d664b3tar3bz2 [http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2]("http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2"), I get this 780 files, but no v4l, only v4l2.

```
/home/ice/Videos/Webcam/montag/a800.c
/home/ice/Videos/Webcam/montag/adv7170.c
/home/ice/Videos/Webcam/montag/adv7175.c
/home/ice/Videos/Webcam/montag/adv7180.c
/home/ice/Videos/Webcam/montag/adv7343.c
/home/ice/Videos/Webcam/montag/adv7343_regs.h
/home/ice/Videos/Webcam/montag/af9005.c
/home/ice/Videos/Webcam/montag/af9005.h
/home/ice/Videos/Webcam/montag/af9005-fe.c
/home/ice/Videos/Webcam/montag/af9005-remote.c
/home/ice/Videos/Webcam/montag/af9005-script.h
/home/ice/Videos/Webcam/montag/af9013.c
/home/ice/Videos/Webcam/montag/af9013.h
/home/ice/Videos/Webcam/montag/af9013_priv.h
/home/ice/Videos/Webcam/montag/af9015.c
/home/ice/Videos/Webcam/montag/af9015.h
/home/ice/Videos/Webcam/montag/anysee.c
/home/ice/Videos/Webcam/montag/anysee.h
/home/ice/Videos/Webcam/montag/API.html
/home/ice/Videos/Webcam/montag/arv.c
/home/ice/Videos/Webcam/montag/at76c651.c
/home/ice/Videos/Webcam/montag/at76c651.h
/home/ice/Videos/Webcam/montag/au0828.h
/home/ice/Videos/Webcam/montag/au0828-cards.c
/home/ice/Videos/Webcam/montag/au0828-cards.h
/home/ice/Videos/Webcam/montag/au0828-core.c
/home/ice/Videos/Webcam/montag/au0828-dvb.c
/home/ice/Videos/Webcam/montag/au0828-i2c.c
/home/ice/Videos/Webcam/montag/au0828-reg.h
/home/ice/Videos/Webcam/montag/au0828-video.c
/home/ice/Videos/Webcam/montag/au6610.c
/home/ice/Videos/Webcam/montag/au6610.h
/home/ice/Videos/Webcam/montag/au8522.h
/home/ice/Videos/Webcam/montag/au8522_decoder.c
/home/ice/Videos/Webcam/montag/au8522_dig.c
/home/ice/Videos/Webcam/montag/au8522_priv.h
/home/ice/Videos/Webcam/montag/audio.xml
/home/ice/Videos/Webcam/montag/av7110.c
/home/ice/Videos/Webcam/montag/av7110.h
/home/ice/Videos/Webcam/montag/av7110_av.c
/home/ice/Videos/Webcam/montag/av7110_av.h
/home/ice/Videos/Webcam/montag/av7110_ca.c
/home/ice/Videos/Webcam/montag/av7110_ca.h
/home/ice/Videos/Webcam/montag/av7110_hw.c
/home/ice/Videos/Webcam/montag/av7110_hw.h
/home/ice/Videos/Webcam/montag/av7110_ipack.c
/home/ice/Videos/Webcam/montag/av7110_ipack.h
/home/ice/Videos/Webcam/montag/av7110_ir.c
/home/ice/Videos/Webcam/montag/av7110_v4l.c
/home/ice/Videos/Webcam/montag/avermedia.txt
/home/ice/Videos/Webcam/montag/bcm3510.c
/home/ice/Videos/Webcam/montag/bcm3510.h
/home/ice/Videos/Webcam/montag/bcm3510_priv.h
/home/ice/Videos/Webcam/montag/biblio.xml
/home/ice/Videos/Webcam/montag/board-ap325rxa.c
/home/ice/Videos/Webcam/montag/bsbe1.h
/home/ice/Videos/Webcam/montag/bsru6.h
/home/ice/Videos/Webcam/montag/bt8xx.txt
/home/ice/Videos/Webcam/montag/bt819.c
/home/ice/Videos/Webcam/montag/bt848.h
/home/ice/Videos/Webcam/montag/bt856.c
/home/ice/Videos/Webcam/montag/bt866.c
/home/ice/Videos/Webcam/montag/bt878.c
/home/ice/Videos/Webcam/montag/bt878.h
/home/ice/Videos/Webcam/montag/btcx-risc.c
/home/ice/Videos/Webcam/montag/btcx-risc.h
/home/ice/Videos/Webcam/montag/bttv.h
/home/ice/Videos/Webcam/montag/bttv-audio-hook.c
/home/ice/Videos/Webcam/montag/bttv-audio-hook.h
/home/ice/Videos/Webcam/montag/bttv-cards.c
/home/ice/Videos/Webcam/montag/bttv-driver.c
/home/ice/Videos/Webcam/montag/bttv-gpio.c
/home/ice/Videos/Webcam/montag/bttv-i2c.c
/home/ice/Videos/Webcam/montag/bttv-if.c
/home/ice/Videos/Webcam/montag/bttv-input.c
/home/ice/Videos/Webcam/montag/bttvp.h
/home/ice/Videos/Webcam/montag/bttv-risc.c
/home/ice/Videos/Webcam/montag/bttv-vbi.c
/home/ice/Videos/Webcam/montag/budget.c
/home/ice/Videos/Webcam/montag/budget.h
/home/ice/Videos/Webcam/montag/budget-av.c
/home/ice/Videos/Webcam/montag/budget-ci.c
/home/ice/Videos/Webcam/montag/budget-core.c
/home/ice/Videos/Webcam/montag/budget-patch.c
/home/ice/Videos/Webcam/montag/bw-qcam.c
/home/ice/Videos/Webcam/montag/bw-qcam.h
/home/ice/Videos/Webcam/montag/ca.sgml
/home/ice/Videos/Webcam/montag/ca.xml
/home/ice/Videos/Webcam/montag/cafe_ccic
/home/ice/Videos/Webcam/montag/cafe_ccic.c
/home/ice/Videos/Webcam/montag/cafe_ccic-regs.h
/home/ice/Videos/Webcam/montag/capture.c.xml
/home/ice/Videos/Webcam/montag/CARDLIST.au0828
/home/ice/Videos/Webcam/montag/CARDLIST.bttv
/home/ice/Videos/Webcam/montag/CARDLIST.cx88
/home/ice/Videos/Webcam/montag/CARDLIST.cx23885
/home/ice/Videos/Webcam/montag/CARDLIST.em28xx
/home/ice/Videos/Webcam/montag/CARDLIST.ivtv
/home/ice/Videos/Webcam/montag/CARDLIST.saa7134
/home/ice/Videos/Webcam/montag/CARDLIST.saa7164
/home/ice/Videos/Webcam/montag/CARDLIST.tuner
/home/ice/Videos/Webcam/montag/CARDLIST.usbvision
/home/ice/Videos/Webcam/montag/cards.txt
/home/ice/Videos/Webcam/montag/Cards
/home/ice/Videos/Webcam/montag/ce6230.c
/home/ice/Videos/Webcam/montag/ce6230.h
/home/ice/Videos/Webcam/montag/ci.txt
/home/ice/Videos/Webcam/montag/cimax2.c
/home/ice/Videos/Webcam/montag/cimax2.h
/home/ice/Videos/Webcam/montag/cinergyT2.h
/home/ice/Videos/Webcam/montag/cinergyT2-core.c
/home/ice/Videos/Webcam/montag/cinergyT2-fe.c
/home/ice/Videos/Webcam/montag/clock.c
/home/ice/Videos/Webcam/montag/common.xml
/home/ice/Videos/Webcam/montag/compat.xml
/home/ice/Videos/Webcam/montag/contributors.txt
/home/ice/Videos/Webcam/montag/CONTRIBUTORS
/home/ice/Videos/Webcam/montag/controls.xml
/home/ice/Videos/Webcam/montag/COPYING
/home/ice/Videos/Webcam/montag/cpia.c
/home/ice/Videos/Webcam/montag/cpia.h
/home/ice/Videos/Webcam/montag/cpia2.h
/home/ice/Videos/Webcam/montag/cpia2_core.c
/home/ice/Videos/Webcam/montag/cpia2dev.h
/home/ice/Videos/Webcam/montag/cpia2_overview.txt
/home/ice/Videos/Webcam/montag/cpia2patch.h
/home/ice/Videos/Webcam/montag/cpia2_registers.h
/home/ice/Videos/Webcam/montag/cpia2_usb.c
/home/ice/Videos/Webcam/montag/cpia2_v4l.c
/home/ice/Videos/Webcam/montag/cpia_pp.c
/home/ice/Videos/Webcam/montag/cpia_usb.c
/home/ice/Videos/Webcam/montag/c-qcam.c
/home/ice/Videos/Webcam/montag/CQcam.txt
/home/ice/Videos/Webcam/montag/crop.gif
/home/ice/Videos/Webcam/montag/crop.pdf
/home/ice/Videos/Webcam/montag/cs53l32a.c
/home/ice/Videos/Webcam/montag/cs5345.c
/home/ice/Videos/Webcam/montag/cs8420.h
/home/ice/Videos/Webcam/montag/custom.dsl
/home/ice/Videos/Webcam/montag/custom.xsl
/home/ice/Videos/Webcam/montag/cx18.txt
/home/ice/Videos/Webcam/montag/cx18-audio.c
/home/ice/Videos/Webcam/montag/cx18-audio.h
/home/ice/Videos/Webcam/montag/cx18-av-audio.c
/home/ice/Videos/Webcam/montag/cx18-av-core.c
/home/ice/Videos/Webcam/montag/cx18-av-core.h
/home/ice/Videos/Webcam/montag/cx18-av-firmware.c
/home/ice/Videos/Webcam/montag/cx18-av-vbi.c
/home/ice/Videos/Webcam/montag/cx18-cards.c
/home/ice/Videos/Webcam/montag/cx18-cards.h
/home/ice/Videos/Webcam/montag/cx18-controls.c
/home/ice/Videos/Webcam/montag/cx18-controls.h
/home/ice/Videos/Webcam/montag/cx18-driver.c
/home/ice/Videos/Webcam/montag/cx18-driver.h
/home/ice/Videos/Webcam/montag/cx18-dvb.c
/home/ice/Videos/Webcam/montag/cx18-dvb.h
/home/ice/Videos/Webcam/montag/cx18-fileops.c
/home/ice/Videos/Webcam/montag/cx18-fileops.h
/home/ice/Videos/Webcam/montag/cx18-firmware.c
/home/ice/Videos/Webcam/montag/cx18-firmware.h
/home/ice/Videos/Webcam/montag/cx18-gpio.c
/home/ice/Videos/Webcam/montag/cx18-gpio.h
/home/ice/Videos/Webcam/montag/cx18-i2c.c
/home/ice/Videos/Webcam/montag/cx18-i2c.h
/home/ice/Videos/Webcam/montag/cx18-io.c
/home/ice/Videos/Webcam/montag/cx18-io.h
/home/ice/Videos/Webcam/montag/cx18-ioctl.c
/home/ice/Videos/Webcam/montag/cx18-ioctl.h
/home/ice/Videos/Webcam/montag/cx18-irq.c
/home/ice/Videos/Webcam/montag/cx18-irq.h
/home/ice/Videos/Webcam/montag/cx18-mailbox.c
/home/ice/Videos/Webcam/montag/cx18-mailbox.h
/home/ice/Videos/Webcam/montag/cx18-queue.c
/home/ice/Videos/Webcam/montag/cx18-queue.h
/home/ice/Videos/Webcam/montag/cx18-scb.c
/home/ice/Videos/Webcam/montag/cx18-scb.h
/home/ice/Videos/Webcam/montag/cx18-streams.c
/home/ice/Videos/Webcam/montag/cx18-streams.h
/home/ice/Videos/Webcam/montag/cx18-vbi.c
/home/ice/Videos/Webcam/montag/cx18-vbi.h
/home/ice/Videos/Webcam/montag/cx18-version.h
/home/ice/Videos/Webcam/montag/cx18-video.c
/home/ice/Videos/Webcam/montag/cx18-video.h
/home/ice/Videos/Webcam/montag/cx231xx.h
/home/ice/Videos/Webcam/montag/cx231xx-audio.c
/home/ice/Videos/Webcam/montag/cx231xx-avcore.c
/home/ice/Videos/Webcam/montag/cx231xx-cards.c
/home/ice/Videos/Webcam/montag/cx231xx-conf-reg.h
/home/ice/Videos/Webcam/montag/cx231xx-core.c
/home/ice/Videos/Webcam/montag/cx231xx-dvb.c
/home/ice/Videos/Webcam/montag/cx231xx-i2c.c
/home/ice/Videos/Webcam/montag/cx231xx-input.c
/home/ice/Videos/Webcam/montag/cx231xx-pcb-cfg.c
/home/ice/Videos/Webcam/montag/cx231xx-pcb-cfg.h
/home/ice/Videos/Webcam/montag/cx231xx-reg.h
/home/ice/Videos/Webcam/montag/cx231xx-vbi.c
/home/ice/Videos/Webcam/montag/cx231xx-vbi.h
/home/ice/Videos/Webcam/montag/cx231xx-video.c
/home/ice/Videos/Webcam/montag/cx2341x.c
/home/ice/Videos/Webcam/montag/cx22700.c
/home/ice/Videos/Webcam/montag/cx22700.h
/home/ice/Videos/Webcam/montag/cx22702.c
/home/ice/Videos/Webcam/montag/cx22702.h
/home/ice/Videos/Webcam/montag/cx23418.h
/home/ice/Videos/Webcam/montag/cx23885.h
/home/ice/Videos/Webcam/montag/cx23885-417.c
/home/ice/Videos/Webcam/montag/cx23885-cards.c
/home/ice/Videos/Webcam/montag/cx23885-core.c
/home/ice/Videos/Webcam/montag/cx23885-dvb.c
/home/ice/Videos/Webcam/montag/cx23885-i2c.c
/home/ice/Videos/Webcam/montag/cx23885-input.c
/home/ice/Videos/Webcam/montag/cx23885-input.h
/home/ice/Videos/Webcam/montag/cx23885-ioctl.c
/home/ice/Videos/Webcam/montag/cx23885-ioctl.h
/home/ice/Videos/Webcam/montag/cx23885-ir.c
/home/ice/Videos/Webcam/montag/cx23885-ir.h
/home/ice/Videos/Webcam/montag/cx23885-reg.h
/home/ice/Videos/Webcam/montag/cx23885-vbi.c
/home/ice/Videos/Webcam/montag/cx23885-video.c
/home/ice/Videos/Webcam/montag/cx23888-ir.c
/home/ice/Videos/Webcam/montag/cx23888-ir.h
/home/ice/Videos/Webcam/montag/cx24110.c
/home/ice/Videos/Webcam/montag/cx24110.h
/home/ice/Videos/Webcam/montag/cx24113.c
/home/ice/Videos/Webcam/montag/cx24113.h
/home/ice/Videos/Webcam/montag/cx24116.c
/home/ice/Videos/Webcam/montag/cx24116.h
/home/ice/Videos/Webcam/montag/cx24123.c
/home/ice/Videos/Webcam/montag/cx24123.h
/home/ice/Videos/Webcam/montag/cxusb.c
/home/ice/Videos/Webcam/montag/cxusb.h
/home/ice/Videos/Webcam/montag/demux.h
/home/ice/Videos/Webcam/montag/demux.xml
/home/ice/Videos/Webcam/montag/dev-capture.xml
/home/ice/Videos/Webcam/montag/dev-codec.xml
/home/ice/Videos/Webcam/montag/dev-effect.xml
/home/ice/Videos/Webcam/montag/devices.c
/home/ice/Videos/Webcam/montag/dev-osd.xml
/home/ice/Videos/Webcam/montag/dev-output.xml
/home/ice/Videos/Webcam/montag/dev-overlay.xml
/home/ice/Videos/Webcam/montag/dev-radio.xml
/home/ice/Videos/Webcam/montag/dev-raw-vbi.xml
/home/ice/Videos/Webcam/montag/dev-rds.xml
/home/ice/Videos/Webcam/montag/dev-sliced-vbi.xml
/home/ice/Videos/Webcam/montag/dev-teletext.xml
/home/ice/Videos/Webcam/montag/dib07x0.h
/home/ice/Videos/Webcam/montag/dib0070.c
/home/ice/Videos/Webcam/montag/dib0070.h
/home/ice/Videos/Webcam/montag/dib0700.h
/home/ice/Videos/Webcam/montag/dib0700_core.c
/home/ice/Videos/Webcam/montag/dib0700_devices.c
/home/ice/Videos/Webcam/montag/dib3000.h
/home/ice/Videos/Webcam/montag/dib3000mb.c
/home/ice/Videos/Webcam/montag/dib3000mb_priv.h
/home/ice/Videos/Webcam/montag/dib3000mc.c
/home/ice/Videos/Webcam/montag/dib3000mc.h
/home/ice/Videos/Webcam/montag/dib7000m.c
/home/ice/Videos/Webcam/montag/dib7000m.h
/home/ice/Videos/Webcam/montag/dib7000p.c
/home/ice/Videos/Webcam/montag/dib7000p.h
/home/ice/Videos/Webcam/montag/dib8000.c
/home/ice/Videos/Webcam/montag/dib8000.h
/home/ice/Videos/Webcam/montag/dibusb.h
/home/ice/Videos/Webcam/montag/dibusb-common.c
/home/ice/Videos/Webcam/montag/dibusb-mb.c
/home/ice/Videos/Webcam/montag/dibusb-mc.c
/home/ice/Videos/Webcam/montag/dibx000_common.c
/home/ice/Videos/Webcam/montag/dibx000_common.h
/home/ice/Videos/Webcam/montag/digitv.c
/home/ice/Videos/Webcam/montag/digitv.h
/home/ice/Videos/Webcam/montag/dm1105.c
/home/ice/Videos/Webcam/montag/dmxdev.c
/home/ice/Videos/Webcam/montag/dmxdev.h
/home/ice/Videos/Webcam/montag/driver.xml
/home/ice/Videos/Webcam/montag/drx397xD.c
/home/ice/Videos/Webcam/montag/drx397xD.h
/home/ice/Videos/Webcam/montag/drx397xD_fw.h
/home/ice/Videos/Webcam/montag/dsbr100.c
/home/ice/Videos/Webcam/montag/dst.c
/home/ice/Videos/Webcam/montag/dst_ca.c
/home/ice/Videos/Webcam/montag/dst_ca.h
/home/ice/Videos/Webcam/montag/dst_common.h
/home/ice/Videos/Webcam/montag/dst_priv.h
/home/ice/Videos/Webcam/montag/dtt200u.c
/home/ice/Videos/Webcam/montag/dtt200u.h
/home/ice/Videos/Webcam/montag/dtt200u-fe.c
/home/ice/Videos/Webcam/montag/dtv5100.c
/home/ice/Videos/Webcam/montag/dtv5100.h
/home/ice/Videos/Webcam/montag/dvbapi.sgml
/home/ice/Videos/Webcam/montag/dvbapi.xml
/home/ice/Videos/Webcam/montag/dvb-bt8xx.c
/home/ice/Videos/Webcam/montag/dvb-bt8xx.h
/home/ice/Videos/Webcam/montag/dvb_ca_en50221.c
/home/ice/Videos/Webcam/montag/dvb_ca_en50221.h
/home/ice/Videos/Webcam/montag/dvb_demux.c
/home/ice/Videos/Webcam/montag/dvb_demux.h
/home/ice/Videos/Webcam/montag/dvbdev.c
/home/ice/Videos/Webcam/montag/dvbdev.h
/home/ice/Videos/Webcam/montag/dvb_dummy_fe.c
/home/ice/Videos/Webcam/montag/dvb_dummy_fe.h
/home/ice/Videos/Webcam/montag/dvb_filter.c
/home/ice/Videos/Webcam/montag/dvb_filter.h
/home/ice/Videos/Webcam/montag/dvb_frontend.c
/home/ice/Videos/Webcam/montag/dvb_frontend.h
/home/ice/Videos/Webcam/montag/dvb_math.c
/home/ice/Videos/Webcam/montag/dvb_math.h
/home/ice/Videos/Webcam/montag/dvb_net.c
/home/ice/Videos/Webcam/montag/dvb_net.h
/home/ice/Videos/Webcam/montag/dvb-pll.c
/home/ice/Videos/Webcam/montag/dvb-pll.h
/home/ice/Videos/Webcam/montag/dvbproperty.xml
/home/ice/Videos/Webcam/montag/dvb_ringbuffer.c
/home/ice/Videos/Webcam/montag/dvb_ringbuffer.h
/home/ice/Videos/Webcam/montag/dvbstb.pdf
/home/ice/Videos/Webcam/montag/dvbstb.png
/home/ice/Videos/Webcam/montag/dvb-ttusb-budget.c
/home/ice/Videos/Webcam/montag/dvb-ttusb-dspbootcode.h
/home/ice/Videos/Webcam/montag/dvb-usb.h
/home/ice/Videos/Webcam/montag/dvb-usb-common.h
/home/ice/Videos/Webcam/montag/dvb-usb-dvb.c
/home/ice/Videos/Webcam/montag/dvb-usb-firmware.c
/home/ice/Videos/Webcam/montag/dvb-usb-i2c.c
/home/ice/Videos/Webcam/montag/dvb-usb-ids.h
/home/ice/Videos/Webcam/montag/dvb-usb-init.c
/home/ice/Videos/Webcam/montag/dvb-usb-remote.c
/home/ice/Videos/Webcam/montag/dvb-usb-urb.c
/home/ice/Videos/Webcam/montag/dw2102.c
/home/ice/Videos/Webcam/montag/dw2102.h
/home/ice/Videos/Webcam/montag/eds1547.h
/home/ice/Videos/Webcam/montag/et61x251.txt
/home/ice/Videos/Webcam/montag/examples.xml
/home/ice/Videos/Webcam/montag/extract_xc3028.pl
/home/ice/Videos/Webcam/montag/faq.txt
/home/ice/Videos/Webcam/montag/fdl-appendix.xml
/home/ice/Videos/Webcam/montag/fieldseq_bt.gif
/home/ice/Videos/Webcam/montag/fieldseq_bt.pdf
/home/ice/Videos/Webcam/montag/fieldseq_tb.gif
/home/ice/Videos/Webcam/montag/fieldseq_tb.pdf
/home/ice/Videos/Webcam/montag/firedtv.h
/home/ice/Videos/Webcam/montag/firedtv-1394.c
/home/ice/Videos/Webcam/montag/firedtv-avc.c
/home/ice/Videos/Webcam/montag/firedtv-ci.c
/home/ice/Videos/Webcam/montag/firedtv-dvb.c
/home/ice/Videos/Webcam/montag/firedtv-fe.c
/home/ice/Videos/Webcam/montag/firedtv-rc.c
/home/ice/Videos/Webcam/montag/flexcop.c
/home/ice/Videos/Webcam/montag/flexcop.h
/home/ice/Videos/Webcam/montag/flexcop-common.h
/home/ice/Videos/Webcam/montag/flexcop-dma.c
/home/ice/Videos/Webcam/montag/flexcop-eeprom.c
/home/ice/Videos/Webcam/montag/flexcop-fe-tuner.c
/home/ice/Videos/Webcam/montag/flexcop-hw-filter.c
/home/ice/Videos/Webcam/montag/flexcop-i2c.c
/home/ice/Videos/Webcam/montag/flexcop_ibi_value_be.h
/home/ice/Videos/Webcam/montag/flexcop_ibi_value_le.h
/home/ice/Videos/Webcam/montag/flexcop-misc.c
/home/ice/Videos/Webcam/montag/flexcop-pci.c
/home/ice/Videos/Webcam/montag/flexcop-reg.h
/home/ice/Videos/Webcam/montag/flexcop-sram.c
/home/ice/Videos/Webcam/montag/flexcop-usb.c
/home/ice/Videos/Webcam/montag/flexcop-usb.h
/home/ice/Videos/Webcam/montag/friio.c
/home/ice/Videos/Webcam/montag/friio.h
/home/ice/Videos/Webcam/montag/friio-fe.c
/home/ice/Videos/Webcam/montag/frontend.xml
/home/ice/Videos/Webcam/montag/func-close.xml
/home/ice/Videos/Webcam/montag/func-ioctl.xml
/home/ice/Videos/Webcam/montag/func-mmap.xml
/home/ice/Videos/Webcam/montag/func-munmap.xml
/home/ice/Videos/Webcam/montag/func-open.xml
/home/ice/Videos/Webcam/montag/func-poll.xml
/home/ice/Videos/Webcam/montag/func-read.xml
/home/ice/Videos/Webcam/montag/func-select.xml
/home/ice/Videos/Webcam/montag/func-write.xml
/home/ice/Videos/Webcam/montag/fw-calling.txt
/home/ice/Videos/Webcam/montag/fw-decoder-api.txt
/home/ice/Videos/Webcam/montag/fw-decoder-regs.txt
/home/ice/Videos/Webcam/montag/fw-dma.txt
/home/ice/Videos/Webcam/montag/fw-encoder-api.txt
/home/ice/Videos/Webcam/montag/fw-memory.txt
/home/ice/Videos/Webcam/montag/fw-osd-api.txt
/home/ice/Videos/Webcam/montag/fw-upload.txt
/home/ice/Videos/Webcam/montag/get_dvb_firmware
/home/ice/Videos/Webcam/montag/gl861.c
/home/ice/Videos/Webcam/montag/gl861.h
/home/ice/Videos/Webcam/montag/gp8psk.c
/home/ice/Videos/Webcam/montag/gp8psk.h
/home/ice/Videos/Webcam/montag/gp8psk-fe.c
/home/ice/Videos/Webcam/montag/gspca.txt
/home/ice/Videos/Webcam/montag/hauppauge-wintv-cx88-ir.txt
/home/ice/Videos/Webcam/montag/hgimport
/home/ice/Videos/Webcam/montag/HOWTO-use-the-demux-api
/home/ice/Videos/Webcam/montag/HOWTO-use-the-frontend-api
/home/ice/Videos/Webcam/montag/ibmcam.txt
/home/ice/Videos/Webcam/montag/ICs
/home/ice/Videos/Webcam/montag/Insmod-options
/home/ice/Videos/Webcam/montag/INSTALL
/home/ice/Videos/Webcam/montag/intro.xml
/home/ice/Videos/Webcam/montag/io.xml
/home/ice/Videos/Webcam/montag/ir-functions.c
/home/ice/Videos/Webcam/montag/ir-keymaps.c
/home/ice/Videos/Webcam/montag/isl6405.c
/home/ice/Videos/Webcam/montag/isl6405.h
/home/ice/Videos/Webcam/montag/isl6421.c
/home/ice/Videos/Webcam/montag/isl6421.h
/home/ice/Videos/Webcam/montag/isl6423.c
/home/ice/Videos/Webcam/montag/isl6423.h
/home/ice/Videos/Webcam/montag/itd1000.c
/home/ice/Videos/Webcam/montag/itd1000.h
/home/ice/Videos/Webcam/montag/itd1000_priv.h
/home/ice/Videos/Webcam/montag/Kconfig
/home/ice/Videos/Webcam/montag/kdapi.xml
/home/ice/Videos/Webcam/montag/keytable.c.xml
/home/ice/Videos/Webcam/montag/ksym_mx1.c
/home/ice/Videos/Webcam/montag/l64781.c
/home/ice/Videos/Webcam/montag/l64781.h
/home/ice/Videos/Webcam/montag/lgdt330x.c
/home/ice/Videos/Webcam/montag/lgdt330x.h
/home/ice/Videos/Webcam/montag/lgdt330x_priv.h
/home/ice/Videos/Webcam/montag/lgdt3304.c
/home/ice/Videos/Webcam/montag/lgdt3304.h
/home/ice/Videos/Webcam/montag/lgdt3305.c
/home/ice/Videos/Webcam/montag/lgdt3305.h
/home/ice/Videos/Webcam/montag/lgs8gl5.c
/home/ice/Videos/Webcam/montag/lgs8gl5.h
/home/ice/Videos/Webcam/montag/lgs8gxx.c
/home/ice/Videos/Webcam/montag/lgs8gxx.h
/home/ice/Videos/Webcam/montag/lgs8gxx_priv.h
/home/ice/Videos/Webcam/montag/libv4l.xml
/home/ice/Videos/Webcam/montag/lifeview.txt
/home/ice/Videos/Webcam/montag/lnbh24.h
/home/ice/Videos/Webcam/montag/lnbp21.c
/home/ice/Videos/Webcam/montag/lnbp21.h
/home/ice/Videos/Webcam/montag/m920x.c
/home/ice/Videos/Webcam/montag/m920x.h
/home/ice/Videos/Webcam/montag/m5602.txt
/home/ice/Videos/Webcam/montag/MAKEDEV
/home/ice/Videos/Webcam/montag/Makefile
/home/ice/Videos/Webcam/montag/mc44s803.c
/home/ice/Videos/Webcam/montag/mc44s803.h
/home/ice/Videos/Webcam/montag/mc44s803_priv.h
/home/ice/Videos/Webcam/montag/media.tmpl
/home/ice/Videos/Webcam/montag/media-entities.tmpl
/home/ice/Videos/Webcam/montag/media-indices.tmpl
/home/ice/Videos/Webcam/montag/memory.h
/home/ice/Videos/Webcam/montag/meye.txt
/home/ice/Videos/Webcam/montag/Modprobe.conf
/home/ice/Videos/Webcam/montag/Modules.conf
/home/ice/Videos/Webcam/montag/mt20xx.c
/home/ice/Videos/Webcam/montag/mt20xx.h
/home/ice/Videos/Webcam/montag/mt312.c
/home/ice/Videos/Webcam/montag/mt312.h
/home/ice/Videos/Webcam/montag/mt312_priv.h
/home/ice/Videos/Webcam/montag/mt352.c
/home/ice/Videos/Webcam/montag/mt352.h
/home/ice/Videos/Webcam/montag/mt352_priv.h
/home/ice/Videos/Webcam/montag/mt2060.c
/home/ice/Videos/Webcam/montag/mt2060.h
/home/ice/Videos/Webcam/montag/mt2060_priv.h
/home/ice/Videos/Webcam/montag/mt2131.c
/home/ice/Videos/Webcam/montag/mt2131.h
/home/ice/Videos/Webcam/montag/mt2131_priv.h
/home/ice/Videos/Webcam/montag/mt2266.c
/home/ice/Videos/Webcam/montag/mt2266.h
/home/ice/Videos/Webcam/montag/mx1_camera.h
/home/ice/Videos/Webcam/montag/mx1_camera_fiq.S
/home/ice/Videos/Webcam/montag/mx3_camera.h
/home/ice/Videos/Webcam/montag/mxl5005s.c
/home/ice/Videos/Webcam/montag/mxl5005s.h
/home/ice/Videos/Webcam/montag/mxl5007t.c
/home/ice/Videos/Webcam/montag/mxl5007t.h
/home/ice/Videos/Webcam/montag/net.xml
/home/ice/Videos/Webcam/montag/netup-eeprom.c
/home/ice/Videos/Webcam/montag/netup-eeprom.h
/home/ice/Videos/Webcam/montag/netup-init.c
/home/ice/Videos/Webcam/montag/netup-init.h
/home/ice/Videos/Webcam/montag/not-in-cx2388x-datasheet.txt
/home/ice/Videos/Webcam/montag/nova-t-usb2.c
/home/ice/Videos/Webcam/montag/nxt200x.c
/home/ice/Videos/Webcam/montag/nxt200x.h
/home/ice/Videos/Webcam/montag/nxt6000.c
/home/ice/Videos/Webcam/montag/nxt6000.h
/home/ice/Videos/Webcam/montag/nxt6000_priv.h
/home/ice/Videos/Webcam/montag/opera1.c
/home/ice/Videos/Webcam/montag/opera-firmware.txt
/home/ice/Videos/Webcam/montag/or51132.c
/home/ice/Videos/Webcam/montag/or51132.h
/home/ice/Videos/Webcam/montag/or51211.c
/home/ice/Videos/Webcam/montag/or51211.h
/home/ice/Videos/Webcam/montag/ov511.txt
/home/ice/Videos/Webcam/montag/pcm990-baseboard.c
/home/ice/Videos/Webcam/montag/pixfmt.xml
/home/ice/Videos/Webcam/montag/pixfmt-grey.xml
/home/ice/Videos/Webcam/montag/pixfmt-nv12.xml
/home/ice/Videos/Webcam/montag/pixfmt-nv16.xml
/home/ice/Videos/Webcam/montag/pixfmt-packed-rgb.xml
/home/ice/Videos/Webcam/montag/pixfmt-packed-yuv.xml
/home/ice/Videos/Webcam/montag/pixfmt-sbggr8.xml
/home/ice/Videos/Webcam/montag/pixfmt-sbggr16.xml
/home/ice/Videos/Webcam/montag/pixfmt-sgbrg8.xml
/home/ice/Videos/Webcam/montag/pixfmt-sgrbg8.xml
/home/ice/Videos/Webcam/montag/pixfmt-uyvy.xml
/home/ice/Videos/Webcam/montag/pixfmt-vyuy.xml
/home/ice/Videos/Webcam/montag/pixfmt-y16.xml
/home/ice/Videos/Webcam/montag/pixfmt-y41p.xml
/home/ice/Videos/Webcam/montag/pixfmt-yuv410.xml
/home/ice/Videos/Webcam/montag/pixfmt-yuv411p.xml
/home/ice/Videos/Webcam/montag/pixfmt-yuv420.xml
/home/ice/Videos/Webcam/montag/pixfmt-yuv422p.xml
/home/ice/Videos/Webcam/montag/pixfmt-yuyv.xml
/home/ice/Videos/Webcam/montag/pixfmt-yvyu.xml
/home/ice/Videos/Webcam/montag/pluto2.c
/home/ice/Videos/Webcam/montag/PROBLEMS
/home/ice/Videos/Webcam/montag/pt1.c
/home/ice/Videos/Webcam/montag/pxa_camera.txt
/home/ice/Videos/Webcam/montag/qt1010.c
/home/ice/Videos/Webcam/montag/qt1010.h
/home/ice/Videos/Webcam/montag/qt1010_priv.h
/home/ice/Videos/Webcam/montag/radio-aimslab.c
/home/ice/Videos/Webcam/montag/radio-aztech.c
/home/ice/Videos/Webcam/montag/radio-cadet.c
/home/ice/Videos/Webcam/montag/radio-gemtek.c
/home/ice/Videos/Webcam/montag/radio-gemtek-pci.c
/home/ice/Videos/Webcam/montag/radio-maestro.c
/home/ice/Videos/Webcam/montag/radio-maxiradio.c
/home/ice/Videos/Webcam/montag/radio-mr800.c
/home/ice/Videos/Webcam/montag/radio-rtrack2.c
/home/ice/Videos/Webcam/montag/radio-sf16fmi.c
/home/ice/Videos/Webcam/montag/radio-sf16fmr2.c
/home/ice/Videos/Webcam/montag/radio-si470x.h
/home/ice/Videos/Webcam/montag/radio-si470x-common.c
/home/ice/Videos/Webcam/montag/radio-si470x-i2c.c
/home/ice/Videos/Webcam/montag/radio-si470x-usb.c
/home/ice/Videos/Webcam/montag/radio-si4713.c
/home/ice/Videos/Webcam/montag/radio-tea5764.c
/home/ice/Videos/Webcam/montag/radio-terratec.c
/home/ice/Videos/Webcam/montag/radiotrack.txt
/home/ice/Videos/Webcam/montag/radio-trust.c
/home/ice/Videos/Webcam/montag/radio-typhoon.c
/home/ice/Videos/Webcam/montag/radio-zoltrix.c
/home/ice/Videos/Webcam/montag/readme.txt
/home/ice/Videos/Webcam/montag/README
/home/ice/Videos/Webcam/montag/README.CABLE
/home/ice/Videos/Webcam/montag/README.cpia
/home/ice/Videos/Webcam/montag/README.cpia2
/home/ice/Videos/Webcam/montag/README.cx88
/home/ice/Videos/Webcam/montag/README.dvb-usb
/home/ice/Videos/Webcam/montag/README.EON
/home/ice/Videos/Webcam/montag/README.freeze
/home/ice/Videos/Webcam/montag/README.hm12
/home/ice/Videos/Webcam/montag/README.ir
/home/ice/Videos/Webcam/montag/README.ivtv
/home/ice/Videos/Webcam/montag/README.patches
/home/ice/Videos/Webcam/montag/README.pvrusb2
/home/ice/Videos/Webcam/montag/README.quirks
/home/ice/Videos/Webcam/montag/README.saa7134
/home/ice/Videos/Webcam/montag/README.valgrind
/home/ice/Videos/Webcam/montag/README.vbi
/home/ice/Videos/Webcam/montag/README.WINVIEW
/home/ice/Videos/Webcam/montag/remote_controllers.xml
/home/ice/Videos/Webcam/montag/s5h1409.c
/home/ice/Videos/Webcam/montag/s5h1409.h
/home/ice/Videos/Webcam/montag/s5h1411.c
/home/ice/Videos/Webcam/montag/s5h1411.h
/home/ice/Videos/Webcam/montag/s5h1420.c
/home/ice/Videos/Webcam/montag/s5h1420.h
/home/ice/Videos/Webcam/montag/s5h1420_priv.h
/home/ice/Videos/Webcam/montag/s921_core.c
/home/ice/Videos/Webcam/montag/s921_core.h
/home/ice/Videos/Webcam/montag/s921_module.c
/home/ice/Videos/Webcam/montag/s921_module.h
/home/ice/Videos/Webcam/montag/saa7146_core.c
/home/ice/Videos/Webcam/montag/saa7146_fops.c
/home/ice/Videos/Webcam/montag/saa7146_hlp.c
/home/ice/Videos/Webcam/montag/saa7146_i2c.c
/home/ice/Videos/Webcam/montag/saa7146_vbi.c
/home/ice/Videos/Webcam/montag/saa7146_video.c
/home/ice/Videos/Webcam/montag/se401.txt
/home/ice/Videos/Webcam/montag/setup.c
/home/ice/Videos/Webcam/montag/si21xx.c
/home/ice/Videos/Webcam/montag/si21xx.h
/home/ice/Videos/Webcam/montag/si470x.txt
/home/ice/Videos/Webcam/montag/si4713.txt
/home/ice/Videos/Webcam/montag/si4713-i2c.c
/home/ice/Videos/Webcam/montag/si4713-i2c.h
/home/ice/Videos/Webcam/montag/sms-cards.c
/home/ice/Videos/Webcam/montag/sms-cards.h
/home/ice/Videos/Webcam/montag/smscoreapi.c
/home/ice/Videos/Webcam/montag/smscoreapi.h
/home/ice/Videos/Webcam/montag/smsdvb.c
/home/ice/Videos/Webcam/montag/smsendian.c
/home/ice/Videos/Webcam/montag/smsendian.h
/home/ice/Videos/Webcam/montag/smsir.c
/home/ice/Videos/Webcam/montag/smsir.h
/home/ice/Videos/Webcam/montag/smssdio.c
/home/ice/Videos/Webcam/montag/smsusb.c
/home/ice/Videos/Webcam/montag/sn9c102.txt
/home/ice/Videos/Webcam/montag/soc-camera.txt
/home/ice/Videos/Webcam/montag/Sound-FAQ
/home/ice/Videos/Webcam/montag/sp887x.c
/home/ice/Videos/Webcam/montag/sp887x.h
/home/ice/Videos/Webcam/montag/sp8870.c
/home/ice/Videos/Webcam/montag/sp8870.h
/home/ice/Videos/Webcam/montag/Specs
/home/ice/Videos/Webcam/montag/stb0899_algo.c
/home/ice/Videos/Webcam/montag/stb0899_cfg.h
/home/ice/Videos/Webcam/montag/stb0899_drv.c
/home/ice/Videos/Webcam/montag/stb0899_drv.h
/home/ice/Videos/Webcam/montag/stb0899_priv.h
/home/ice/Videos/Webcam/montag/stb0899_reg.h
/home/ice/Videos/Webcam/montag/stb6000.c
/home/ice/Videos/Webcam/montag/stb6000.h
/home/ice/Videos/Webcam/montag/stb6100.c
/home/ice/Videos/Webcam/montag/stb6100.h
/home/ice/Videos/Webcam/montag/stb6100_cfg.h
/home/ice/Videos/Webcam/montag/stv090x.c
/home/ice/Videos/Webcam/montag/stv090x.h
/home/ice/Videos/Webcam/montag/stv090x_priv.h
/home/ice/Videos/Webcam/montag/stv090x_reg.h
/home/ice/Videos/Webcam/montag/stv0288.c
/home/ice/Videos/Webcam/montag/stv0288.h
/home/ice/Videos/Webcam/montag/stv0297.c
/home/ice/Videos/Webcam/montag/stv0297.h
/home/ice/Videos/Webcam/montag/stv0299.c
/home/ice/Videos/Webcam/montag/stv0299.h
/home/ice/Videos/Webcam/montag/stv680.txt
/home/ice/Videos/Webcam/montag/stv0900.h
/home/ice/Videos/Webcam/montag/stv0900_core.c
/home/ice/Videos/Webcam/montag/stv0900_init.h
/home/ice/Videos/Webcam/montag/stv0900_priv.h
/home/ice/Videos/Webcam/montag/stv0900_reg.h
/home/ice/Videos/Webcam/montag/stv0900_sw.c
/home/ice/Videos/Webcam/montag/stv6110.c
/home/ice/Videos/Webcam/montag/stv6110.h
/home/ice/Videos/Webcam/montag/stv6110x.c
/home/ice/Videos/Webcam/montag/stv6110x.h
/home/ice/Videos/Webcam/montag/stv6110x_priv.h
/home/ice/Videos/Webcam/montag/stv6110x_reg.h
/home/ice/Videos/Webcam/montag/tda80xx.c
/home/ice/Videos/Webcam/montag/tda80xx.h
/home/ice/Videos/Webcam/montag/tda826x.c
/home/ice/Videos/Webcam/montag/tda826x.h
/home/ice/Videos/Webcam/montag/tda827x.c
/home/ice/Videos/Webcam/montag/tda827x.h
/home/ice/Videos/Webcam/montag/tda1002x.h
/home/ice/Videos/Webcam/montag/tda1004x.c
/home/ice/Videos/Webcam/montag/tda1004x.h
/home/ice/Videos/Webcam/montag/tda8083.c
/home/ice/Videos/Webcam/montag/tda8083.h
/home/ice/Videos/Webcam/montag/tda8261.c
/home/ice/Videos/Webcam/montag/tda8261.h
/home/ice/Videos/Webcam/montag/tda8261_cfg.h
/home/ice/Videos/Webcam/montag/tda8290.c
/home/ice/Videos/Webcam/montag/tda8290.h
/home/ice/Videos/Webcam/montag/tda9887.c
/home/ice/Videos/Webcam/montag/tda9887.h
/home/ice/Videos/Webcam/montag/tda10021.c
/home/ice/Videos/Webcam/montag/tda10023.c
/home/ice/Videos/Webcam/montag/tda10048.c
/home/ice/Videos/Webcam/montag/tda10048.h
/home/ice/Videos/Webcam/montag/tda10086.c
/home/ice/Videos/Webcam/montag/tda10086.h
/home/ice/Videos/Webcam/montag/tda18271.h
/home/ice/Videos/Webcam/montag/tda18271-common.c
/home/ice/Videos/Webcam/montag/tda18271-fe.c
/home/ice/Videos/Webcam/montag/tda18271-maps.c
/home/ice/Videos/Webcam/montag/tda18271-priv.h
/home/ice/Videos/Webcam/montag/tdhd1.h
/home/ice/Videos/Webcam/montag/tea5761.c
/home/ice/Videos/Webcam/montag/tea5761.h
/home/ice/Videos/Webcam/montag/tea5767.c
/home/ice/Videos/Webcam/montag/tea5767.h
/home/ice/Videos/Webcam/montag/technisat.txt
/home/ice/Videos/Webcam/montag/tef6862.c
/home/ice/Videos/Webcam/montag/THANKS
/home/ice/Videos/Webcam/montag/ttpci-eeprom.c
/home/ice/Videos/Webcam/montag/ttpci-eeprom.h
/home/ice/Videos/Webcam/montag/ttusb2.c
/home/ice/Videos/Webcam/montag/ttusb2.h
/home/ice/Videos/Webcam/montag/ttusb_dec.c
/home/ice/Videos/Webcam/montag/ttusb-dec.txt
/home/ice/Videos/Webcam/montag/ttusbdecfe.c
/home/ice/Videos/Webcam/montag/ttusbdecfe.h
/home/ice/Videos/Webcam/montag/tua6100.c
/home/ice/Videos/Webcam/montag/tua6100.h
/home/ice/Videos/Webcam/montag/tuner-i2c.h
/home/ice/Videos/Webcam/montag/Tuners
/home/ice/Videos/Webcam/montag/tuner-simple.c
/home/ice/Videos/Webcam/montag/tuner-simple.h
/home/ice/Videos/Webcam/montag/tuner-types.c
/home/ice/Videos/Webcam/montag/tuner-xc2028.c
/home/ice/Videos/Webcam/montag/tuner-xc2028.h
/home/ice/Videos/Webcam/montag/tuner-xc2028-types.h
/home/ice/Videos/Webcam/montag/udev.txt
/home/ice/Videos/Webcam/montag/umt-010.c
/home/ice/Videos/Webcam/montag/usb-urb.c
/home/ice/Videos/Webcam/montag/v4l2.xml
/home/ice/Videos/Webcam/montag/v4l2-framework.txt
/home/ice/Videos/Webcam/montag/v4l2grab.c.xml
/home/ice/Videos/Webcam/montag/v4lgrab.c
/home/ice/Videos/Webcam/montag/va1j5jf8007s.c
/home/ice/Videos/Webcam/montag/va1j5jf8007s.h
/home/ice/Videos/Webcam/montag/va1j5jf8007t.c
/home/ice/Videos/Webcam/montag/va1j5jf8007t.h
/home/ice/Videos/Webcam/montag/valgrind-1.0.4.diff
/home/ice/Videos/Webcam/montag/valgrind-1.9.4.diff
/home/ice/Videos/Webcam/montag/valgrind-20030716.diff
/home/ice/Videos/Webcam/montag/vbi_525.gif
/home/ice/Videos/Webcam/montag/vbi_525.pdf
/home/ice/Videos/Webcam/montag/vbi_625.gif
/home/ice/Videos/Webcam/montag/vbi_625.pdf
/home/ice/Videos/Webcam/montag/vbi_hsync.gif
/home/ice/Videos/Webcam/montag/vbi_hsync.pdf
/home/ice/Videos/Webcam/montag/ves1x93.c
/home/ice/Videos/Webcam/montag/ves1x93.h
/home/ice/Videos/Webcam/montag/ves1820.c
/home/ice/Videos/Webcam/montag/ves1820.h
/home/ice/Videos/Webcam/montag/video.xml
/home/ice/Videos/Webcam/montag/videodev2.h.xml
/home/ice/Videos/Webcam/montag/vidioc-cropcap.xml
/home/ice/Videos/Webcam/montag/vidioc-dbg-g-chip-ident.xml
/home/ice/Videos/Webcam/montag/vidioc-dbg-g-register.xml
/home/ice/Videos/Webcam/montag/vidioc-encoder-cmd.xml
/home/ice/Videos/Webcam/montag/vidioc-enumaudio.xml
/home/ice/Videos/Webcam/montag/vidioc-enumaudioout.xml
/home/ice/Videos/Webcam/montag/vidioc-enum-fmt.xml
/home/ice/Videos/Webcam/montag/vidioc-enum-frameintervals.xml
/home/ice/Videos/Webcam/montag/vidioc-enum-framesizes.xml
/home/ice/Videos/Webcam/montag/vidioc-enuminput.xml
/home/ice/Videos/Webcam/montag/vidioc-enumoutput.xml
/home/ice/Videos/Webcam/montag/vidioc-enumstd.xml
/home/ice/Videos/Webcam/montag/vidioc-g-audio.xml
/home/ice/Videos/Webcam/montag/vidioc-g-audioout.xml
/home/ice/Videos/Webcam/montag/vidioc-g-crop.xml
/home/ice/Videos/Webcam/montag/vidioc-g-ctrl.xml
/home/ice/Videos/Webcam/montag/vidioc-g-enc-index.xml
/home/ice/Videos/Webcam/montag/vidioc-g-ext-ctrls.xml
/home/ice/Videos/Webcam/montag/vidioc-g-fbuf.xml
/home/ice/Videos/Webcam/montag/vidioc-g-fmt.xml
/home/ice/Videos/Webcam/montag/vidioc-g-frequency.xml
/home/ice/Videos/Webcam/montag/vidioc-g-input.xml
/home/ice/Videos/Webcam/montag/vidioc-g-jpegcomp.xml
/home/ice/Videos/Webcam/montag/vidioc-g-modulator.xml
/home/ice/Videos/Webcam/montag/vidioc-g-output.xml
/home/ice/Videos/Webcam/montag/vidioc-g-parm.xml
/home/ice/Videos/Webcam/montag/vidioc-g-priority.xml
/home/ice/Videos/Webcam/montag/vidioc-g-sliced-vbi-cap.xml
/home/ice/Videos/Webcam/montag/vidioc-g-std.xml
/home/ice/Videos/Webcam/montag/vidioc-g-tuner.xml
/home/ice/Videos/Webcam/montag/vidioc-log-status.xml
/home/ice/Videos/Webcam/montag/vidioc-overlay.xml
/home/ice/Videos/Webcam/montag/vidioc-qbuf.xml
/home/ice/Videos/Webcam/montag/vidioc-querybuf.xml
/home/ice/Videos/Webcam/montag/vidioc-querycap.xml
/home/ice/Videos/Webcam/montag/vidioc-queryctrl.xml
/home/ice/Videos/Webcam/montag/vidioc-querystd.xml
/home/ice/Videos/Webcam/montag/vidioc-reqbufs.xml
/home/ice/Videos/Webcam/montag/vidioc-s-hw-freq-seek.xml
/home/ice/Videos/Webcam/montag/vidioc-streamon.xml
/home/ice/Videos/Webcam/montag/vp702x.c
/home/ice/Videos/Webcam/montag/vp702x.h
/home/ice/Videos/Webcam/montag/vp702x-fe.c
/home/ice/Videos/Webcam/montag/vp7045.c
/home/ice/Videos/Webcam/montag/vp7045.h
/home/ice/Videos/Webcam/montag/vp7045-fe.c
/home/ice/Videos/Webcam/montag/w9966.txt
/home/ice/Videos/Webcam/montag/w9968cf.txt
/home/ice/Videos/Webcam/montag/xc5000.c
/home/ice/Videos/Webcam/montag/xc5000.h
/home/ice/Videos/Webcam/montag/z0194a.h
/home/ice/Videos/Webcam/montag/zc0301.txt
/home/ice/Videos/Webcam/montag/zl10036.c
/home/ice/Videos/Webcam/montag/zl10036.h
/home/ice/Videos/Webcam/montag/zl10039.c
/home/ice/Videos/Webcam/montag/zl10039.h
/home/ice/Videos/Webcam/montag/zl10353.c
/home/ice/Videos/Webcam/montag/zl10353.h
/home/ice/Videos/Webcam/montag/zl10353_priv.h
/home/ice/Videos/Webcam/montag/Zoran
/home/ice/Videos/Webcam/montag/zr364xx.txt
```


If I go to the linuxtv.org page, I get this link [http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2]("http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2") with 732 files and also no v4l.

```
/home/ice/Videos/Webcam/sonntag/gspca/a800.c
/home/ice/Videos/Webcam/sonntag/gspca/adv7170.c
/home/ice/Videos/Webcam/sonntag/gspca/adv7175.c
/home/ice/Videos/Webcam/sonntag/gspca/adv7180.c
/home/ice/Videos/Webcam/sonntag/gspca/adv7343.c
/home/ice/Videos/Webcam/sonntag/gspca/adv7343_regs.h
/home/ice/Videos/Webcam/sonntag/gspca/af9005.c
/home/ice/Videos/Webcam/sonntag/gspca/af9005.h
/home/ice/Videos/Webcam/sonntag/gspca/af9005-fe.c
/home/ice/Videos/Webcam/sonntag/gspca/af9005-remote.c
/home/ice/Videos/Webcam/sonntag/gspca/af9005-script.h
/home/ice/Videos/Webcam/sonntag/gspca/af9013.c
/home/ice/Videos/Webcam/sonntag/gspca/af9013.h
/home/ice/Videos/Webcam/sonntag/gspca/af9013_priv.h
/home/ice/Videos/Webcam/sonntag/gspca/af9015.c
/home/ice/Videos/Webcam/sonntag/gspca/af9015.h
/home/ice/Videos/Webcam/sonntag/gspca/anysee.c
/home/ice/Videos/Webcam/sonntag/gspca/anysee.h
/home/ice/Videos/Webcam/sonntag/gspca/API.html
/home/ice/Videos/Webcam/sonntag/gspca/arv.c
/home/ice/Videos/Webcam/sonntag/gspca/at76c651.c
/home/ice/Videos/Webcam/sonntag/gspca/at76c651.h
/home/ice/Videos/Webcam/sonntag/gspca/au0828.h
/home/ice/Videos/Webcam/sonntag/gspca/au0828-cards.c
/home/ice/Videos/Webcam/sonntag/gspca/au0828-cards.h
/home/ice/Videos/Webcam/sonntag/gspca/au0828-core.c
/home/ice/Videos/Webcam/sonntag/gspca/au0828-dvb.c
/home/ice/Videos/Webcam/sonntag/gspca/au0828-i2c.c
/home/ice/Videos/Webcam/sonntag/gspca/au0828-reg.h
/home/ice/Videos/Webcam/sonntag/gspca/au0828-video.c
/home/ice/Videos/Webcam/sonntag/gspca/au6610.c
/home/ice/Videos/Webcam/sonntag/gspca/au6610.h
/home/ice/Videos/Webcam/sonntag/gspca/au8522.h
/home/ice/Videos/Webcam/sonntag/gspca/au8522_decoder.c
/home/ice/Videos/Webcam/sonntag/gspca/au8522_dig.c
/home/ice/Videos/Webcam/sonntag/gspca/au8522_priv.h
/home/ice/Videos/Webcam/sonntag/gspca/audio.xml
/home/ice/Videos/Webcam/sonntag/gspca/av7110.c
/home/ice/Videos/Webcam/sonntag/gspca/av7110.h
/home/ice/Videos/Webcam/sonntag/gspca/av7110_av.c
/home/ice/Videos/Webcam/sonntag/gspca/av7110_av.h
/home/ice/Videos/Webcam/sonntag/gspca/av7110_ca.c
/home/ice/Videos/Webcam/sonntag/gspca/av7110_ca.h
/home/ice/Videos/Webcam/sonntag/gspca/av7110_hw.c
/home/ice/Videos/Webcam/sonntag/gspca/av7110_hw.h
/home/ice/Videos/Webcam/sonntag/gspca/av7110_ipack.c
/home/ice/Videos/Webcam/sonntag/gspca/av7110_ipack.h
/home/ice/Videos/Webcam/sonntag/gspca/av7110_ir.c
/home/ice/Videos/Webcam/sonntag/gspca/av7110_v4l.c
/home/ice/Videos/Webcam/sonntag/gspca/avermedia.txt
/home/ice/Videos/Webcam/sonntag/gspca/bcm3510.c
/home/ice/Videos/Webcam/sonntag/gspca/bcm3510.h
/home/ice/Videos/Webcam/sonntag/gspca/bcm3510_priv.h
/home/ice/Videos/Webcam/sonntag/gspca/biblio.xml
/home/ice/Videos/Webcam/sonntag/gspca/board-ap325rxa.c
/home/ice/Videos/Webcam/sonntag/gspca/bsbe1.h
/home/ice/Videos/Webcam/sonntag/gspca/bsru6.h
/home/ice/Videos/Webcam/sonntag/gspca/bt8xx.txt
/home/ice/Videos/Webcam/sonntag/gspca/bt819.c
/home/ice/Videos/Webcam/sonntag/gspca/bt848.h
/home/ice/Videos/Webcam/sonntag/gspca/bt856.c
/home/ice/Videos/Webcam/sonntag/gspca/bt866.c
/home/ice/Videos/Webcam/sonntag/gspca/bt878.c
/home/ice/Videos/Webcam/sonntag/gspca/bt878.h
/home/ice/Videos/Webcam/sonntag/gspca/btcx-risc.c
/home/ice/Videos/Webcam/sonntag/gspca/btcx-risc.h
/home/ice/Videos/Webcam/sonntag/gspca/bttv.h
/home/ice/Videos/Webcam/sonntag/gspca/bttv-audio-hook.c
/home/ice/Videos/Webcam/sonntag/gspca/bttv-audio-hook.h
/home/ice/Videos/Webcam/sonntag/gspca/bttv-cards.c
/home/ice/Videos/Webcam/sonntag/gspca/bttv-driver.c
/home/ice/Videos/Webcam/sonntag/gspca/bttv-gpio.c
/home/ice/Videos/Webcam/sonntag/gspca/bttv-i2c.c
/home/ice/Videos/Webcam/sonntag/gspca/bttv-if.c
/home/ice/Videos/Webcam/sonntag/gspca/bttv-input.c
/home/ice/Videos/Webcam/sonntag/gspca/bttvp.h
/home/ice/Videos/Webcam/sonntag/gspca/bttv-risc.c
/home/ice/Videos/Webcam/sonntag/gspca/bttv-vbi.c
/home/ice/Videos/Webcam/sonntag/gspca/budget.c
/home/ice/Videos/Webcam/sonntag/gspca/budget.h
/home/ice/Videos/Webcam/sonntag/gspca/budget-av.c
/home/ice/Videos/Webcam/sonntag/gspca/budget-ci.c
/home/ice/Videos/Webcam/sonntag/gspca/budget-core.c
/home/ice/Videos/Webcam/sonntag/gspca/budget-patch.c
/home/ice/Videos/Webcam/sonntag/gspca/bw-qcam.c
/home/ice/Videos/Webcam/sonntag/gspca/bw-qcam.h
/home/ice/Videos/Webcam/sonntag/gspca/ca.sgml
/home/ice/Videos/Webcam/sonntag/gspca/ca.xml
/home/ice/Videos/Webcam/sonntag/gspca/cafe_ccic
/home/ice/Videos/Webcam/sonntag/gspca/cafe_ccic.c
/home/ice/Videos/Webcam/sonntag/gspca/cafe_ccic-regs.h
/home/ice/Videos/Webcam/sonntag/gspca/capture.c.xml
/home/ice/Videos/Webcam/sonntag/gspca/CARDLIST.au0828
/home/ice/Videos/Webcam/sonntag/gspca/CARDLIST.bttv
/home/ice/Videos/Webcam/sonntag/gspca/CARDLIST.cx88
/home/ice/Videos/Webcam/sonntag/gspca/CARDLIST.cx23885
/home/ice/Videos/Webcam/sonntag/gspca/CARDLIST.em28xx
/home/ice/Videos/Webcam/sonntag/gspca/CARDLIST.ivtv
/home/ice/Videos/Webcam/sonntag/gspca/CARDLIST.saa7134
/home/ice/Videos/Webcam/sonntag/gspca/CARDLIST.saa7164
/home/ice/Videos/Webcam/sonntag/gspca/CARDLIST.tuner
/home/ice/Videos/Webcam/sonntag/gspca/CARDLIST.usbvision
/home/ice/Videos/Webcam/sonntag/gspca/cards.txt
/home/ice/Videos/Webcam/sonntag/gspca/Cards
/home/ice/Videos/Webcam/sonntag/gspca/ce6230.c
/home/ice/Videos/Webcam/sonntag/gspca/ce6230.h
/home/ice/Videos/Webcam/sonntag/gspca/ci.txt
/home/ice/Videos/Webcam/sonntag/gspca/cinergyT2.h
/home/ice/Videos/Webcam/sonntag/gspca/cinergyT2-core.c
/home/ice/Videos/Webcam/sonntag/gspca/cinergyT2-fe.c
/home/ice/Videos/Webcam/sonntag/gspca/clock.c
/home/ice/Videos/Webcam/sonntag/gspca/common.xml
/home/ice/Videos/Webcam/sonntag/gspca/compat.xml
/home/ice/Videos/Webcam/sonntag/gspca/contributors.txt
/home/ice/Videos/Webcam/sonntag/gspca/CONTRIBUTORS
/home/ice/Videos/Webcam/sonntag/gspca/controls.xml
/home/ice/Videos/Webcam/sonntag/gspca/COPYING
/home/ice/Videos/Webcam/sonntag/gspca/cpia.c
/home/ice/Videos/Webcam/sonntag/gspca/cpia.h
/home/ice/Videos/Webcam/sonntag/gspca/cpia2.h
/home/ice/Videos/Webcam/sonntag/gspca/cpia2_core.c
/home/ice/Videos/Webcam/sonntag/gspca/cpia2dev.h
/home/ice/Videos/Webcam/sonntag/gspca/cpia2_overview.txt
/home/ice/Videos/Webcam/sonntag/gspca/cpia2patch.h
/home/ice/Videos/Webcam/sonntag/gspca/cpia2_registers.h
/home/ice/Videos/Webcam/sonntag/gspca/cpia2_usb.c
/home/ice/Videos/Webcam/sonntag/gspca/cpia2_v4l.c
/home/ice/Videos/Webcam/sonntag/gspca/cpia_pp.c
/home/ice/Videos/Webcam/sonntag/gspca/cpia_usb.c
/home/ice/Videos/Webcam/sonntag/gspca/c-qcam.c
/home/ice/Videos/Webcam/sonntag/gspca/CQcam.txt
/home/ice/Videos/Webcam/sonntag/gspca/crop.gif
/home/ice/Videos/Webcam/sonntag/gspca/crop.pdf
/home/ice/Videos/Webcam/sonntag/gspca/cs53l32a.c
/home/ice/Videos/Webcam/sonntag/gspca/cs5345.c
/home/ice/Videos/Webcam/sonntag/gspca/cs8420.h
/home/ice/Videos/Webcam/sonntag/gspca/custom.dsl
/home/ice/Videos/Webcam/sonntag/gspca/custom.xsl
/home/ice/Videos/Webcam/sonntag/gspca/cx18.txt
/home/ice/Videos/Webcam/sonntag/gspca/cx18-audio.c
/home/ice/Videos/Webcam/sonntag/gspca/cx18-audio.h
/home/ice/Videos/Webcam/sonntag/gspca/cx18-av-audio.c
/home/ice/Videos/Webcam/sonntag/gspca/cx18-av-core.c
/home/ice/Videos/Webcam/sonntag/gspca/cx18-av-core.h
/home/ice/Videos/Webcam/sonntag/gspca/cx18-av-firmware.c
/home/ice/Videos/Webcam/sonntag/gspca/cx18-av-vbi.c
/home/ice/Videos/Webcam/sonntag/gspca/cx18-cards.c
/home/ice/Videos/Webcam/sonntag/gspca/cx18-cards.h
/home/ice/Videos/Webcam/sonntag/gspca/cx18-controls.c
/home/ice/Videos/Webcam/sonntag/gspca/cx18-controls.h
/home/ice/Videos/Webcam/sonntag/gspca/cx18-driver.c
/home/ice/Videos/Webcam/sonntag/gspca/cx18-driver.h
/home/ice/Videos/Webcam/sonntag/gspca/cx18-dvb.c
/home/ice/Videos/Webcam/sonntag/gspca/cx18-dvb.h
/home/ice/Videos/Webcam/sonntag/gspca/cx18-fileops.c
/home/ice/Videos/Webcam/sonntag/gspca/cx18-fileops.h
/home/ice/Videos/Webcam/sonntag/gspca/cx18-firmware.c
/home/ice/Videos/Webcam/sonntag/gspca/cx18-firmware.h
/home/ice/Videos/Webcam/sonntag/gspca/cx18-gpio.c
/home/ice/Videos/Webcam/sonntag/gspca/cx18-gpio.h
/home/ice/Videos/Webcam/sonntag/gspca/cx18-i2c.c
/home/ice/Videos/Webcam/sonntag/gspca/cx18-i2c.h
/home/ice/Videos/Webcam/sonntag/gspca/cx18-io.c
/home/ice/Videos/Webcam/sonntag/gspca/cx18-io.h
/home/ice/Videos/Webcam/sonntag/gspca/cx18-ioctl.c
/home/ice/Videos/Webcam/sonntag/gspca/cx18-ioctl.h
/home/ice/Videos/Webcam/sonntag/gspca/cx18-irq.c
/home/ice/Videos/Webcam/sonntag/gspca/cx18-irq.h
/home/ice/Videos/Webcam/sonntag/gspca/cx18-mailbox.c
/home/ice/Videos/Webcam/sonntag/gspca/cx18-mailbox.h
/home/ice/Videos/Webcam/sonntag/gspca/cx18-queue.c
/home/ice/Videos/Webcam/sonntag/gspca/cx18-queue.h
/home/ice/Videos/Webcam/sonntag/gspca/cx18-scb.c
/home/ice/Videos/Webcam/sonntag/gspca/cx22700.c
/home/ice/Videos/Webcam/sonntag/gspca/cx22700.h
/home/ice/Videos/Webcam/sonntag/gspca/cx22702.c
/home/ice/Videos/Webcam/sonntag/gspca/cx22702.h
/home/ice/Videos/Webcam/sonntag/gspca/cx24110.c
/home/ice/Videos/Webcam/sonntag/gspca/cx24110.h
/home/ice/Videos/Webcam/sonntag/gspca/cx24113.c
/home/ice/Videos/Webcam/sonntag/gspca/cx24113.h
/home/ice/Videos/Webcam/sonntag/gspca/cx24116.c
/home/ice/Videos/Webcam/sonntag/gspca/cx24116.h
/home/ice/Videos/Webcam/sonntag/gspca/cx24123.c
/home/ice/Videos/Webcam/sonntag/gspca/cx24123.h
/home/ice/Videos/Webcam/sonntag/gspca/cxusb.c
/home/ice/Videos/Webcam/sonntag/gspca/cxusb.h
/home/ice/Videos/Webcam/sonntag/gspca/demux.h
/home/ice/Videos/Webcam/sonntag/gspca/demux.xml
/home/ice/Videos/Webcam/sonntag/gspca/dev-capture.xml
/home/ice/Videos/Webcam/sonntag/gspca/dev-codec.xml
/home/ice/Videos/Webcam/sonntag/gspca/dev-effect.xml
/home/ice/Videos/Webcam/sonntag/gspca/devices.c
/home/ice/Videos/Webcam/sonntag/gspca/dev-osd.xml
/home/ice/Videos/Webcam/sonntag/gspca/dev-output.xml
/home/ice/Videos/Webcam/sonntag/gspca/dev-overlay.xml
/home/ice/Videos/Webcam/sonntag/gspca/dev-radio.xml
/home/ice/Videos/Webcam/sonntag/gspca/dev-raw-vbi.xml
/home/ice/Videos/Webcam/sonntag/gspca/dev-rds.xml
/home/ice/Videos/Webcam/sonntag/gspca/dev-sliced-vbi.xml
/home/ice/Videos/Webcam/sonntag/gspca/dev-teletext.xml
/home/ice/Videos/Webcam/sonntag/gspca/dib07x0.h
/home/ice/Videos/Webcam/sonntag/gspca/dib0070.c
/home/ice/Videos/Webcam/sonntag/gspca/dib0070.h
/home/ice/Videos/Webcam/sonntag/gspca/dib0700.h
/home/ice/Videos/Webcam/sonntag/gspca/dib0700_core.c
/home/ice/Videos/Webcam/sonntag/gspca/dib0700_devices.c
/home/ice/Videos/Webcam/sonntag/gspca/dib3000.h
/home/ice/Videos/Webcam/sonntag/gspca/dib3000mb.c
/home/ice/Videos/Webcam/sonntag/gspca/dib3000mb_priv.h
/home/ice/Videos/Webcam/sonntag/gspca/dib3000mc.c
/home/ice/Videos/Webcam/sonntag/gspca/dib3000mc.h
/home/ice/Videos/Webcam/sonntag/gspca/dib7000m.c
/home/ice/Videos/Webcam/sonntag/gspca/dib7000m.h
/home/ice/Videos/Webcam/sonntag/gspca/dib7000p.c
/home/ice/Videos/Webcam/sonntag/gspca/dib7000p.h
/home/ice/Videos/Webcam/sonntag/gspca/dib8000.c
/home/ice/Videos/Webcam/sonntag/gspca/dib8000.h
/home/ice/Videos/Webcam/sonntag/gspca/dibusb.h
/home/ice/Videos/Webcam/sonntag/gspca/dibusb-common.c
/home/ice/Videos/Webcam/sonntag/gspca/dibusb-mb.c
/home/ice/Videos/Webcam/sonntag/gspca/dibusb-mc.c
/home/ice/Videos/Webcam/sonntag/gspca/dibx000_common.c
/home/ice/Videos/Webcam/sonntag/gspca/dibx000_common.h
/home/ice/Videos/Webcam/sonntag/gspca/digitv.c
/home/ice/Videos/Webcam/sonntag/gspca/digitv.h
/home/ice/Videos/Webcam/sonntag/gspca/dm1105.c
/home/ice/Videos/Webcam/sonntag/gspca/dmxdev.c
/home/ice/Videos/Webcam/sonntag/gspca/dmxdev.h
/home/ice/Videos/Webcam/sonntag/gspca/driver.xml
/home/ice/Videos/Webcam/sonntag/gspca/drx397xD.c
/home/ice/Videos/Webcam/sonntag/gspca/drx397xD.h
/home/ice/Videos/Webcam/sonntag/gspca/drx397xD_fw.h
/home/ice/Videos/Webcam/sonntag/gspca/dsbr100.c
/home/ice/Videos/Webcam/sonntag/gspca/dst.c
/home/ice/Videos/Webcam/sonntag/gspca/dst_ca.c
/home/ice/Videos/Webcam/sonntag/gspca/dst_ca.h
/home/ice/Videos/Webcam/sonntag/gspca/dst_common.h
/home/ice/Videos/Webcam/sonntag/gspca/dst_priv.h
/home/ice/Videos/Webcam/sonntag/gspca/dtt200u.c
/home/ice/Videos/Webcam/sonntag/gspca/dtt200u.h
/home/ice/Videos/Webcam/sonntag/gspca/dtt200u-fe.c
/home/ice/Videos/Webcam/sonntag/gspca/dtv5100.c
/home/ice/Videos/Webcam/sonntag/gspca/dtv5100.h
/home/ice/Videos/Webcam/sonntag/gspca/dvbapi.sgml
/home/ice/Videos/Webcam/sonntag/gspca/dvbapi.xml
/home/ice/Videos/Webcam/sonntag/gspca/dvb-bt8xx.c
/home/ice/Videos/Webcam/sonntag/gspca/dvb-bt8xx.h
/home/ice/Videos/Webcam/sonntag/gspca/dvb_ca_en50221.c
/home/ice/Videos/Webcam/sonntag/gspca/dvb_ca_en50221.h
/home/ice/Videos/Webcam/sonntag/gspca/dvb_demux.c
/home/ice/Videos/Webcam/sonntag/gspca/dvb_demux.h
/home/ice/Videos/Webcam/sonntag/gspca/dvbdev.c
/home/ice/Videos/Webcam/sonntag/gspca/dvbdev.h
/home/ice/Videos/Webcam/sonntag/gspca/dvb_dummy_fe.c
/home/ice/Videos/Webcam/sonntag/gspca/dvb_dummy_fe.h
/home/ice/Videos/Webcam/sonntag/gspca/dvb_filter.c
/home/ice/Videos/Webcam/sonntag/gspca/dvb_filter.h
/home/ice/Videos/Webcam/sonntag/gspca/dvb_frontend.c
/home/ice/Videos/Webcam/sonntag/gspca/dvb_frontend.h
/home/ice/Videos/Webcam/sonntag/gspca/dvb_math.c
/home/ice/Videos/Webcam/sonntag/gspca/dvb_math.h
/home/ice/Videos/Webcam/sonntag/gspca/dvb_net.c
/home/ice/Videos/Webcam/sonntag/gspca/dvb_net.h
/home/ice/Videos/Webcam/sonntag/gspca/dvb-pll.c
/home/ice/Videos/Webcam/sonntag/gspca/dvb-pll.h
/home/ice/Videos/Webcam/sonntag/gspca/dvbproperty.xml
/home/ice/Videos/Webcam/sonntag/gspca/dvb_ringbuffer.c
/home/ice/Videos/Webcam/sonntag/gspca/dvb_ringbuffer.h
/home/ice/Videos/Webcam/sonntag/gspca/dvbstb.pdf
/home/ice/Videos/Webcam/sonntag/gspca/dvbstb.png
/home/ice/Videos/Webcam/sonntag/gspca/dvb-ttusb-budget.c
/home/ice/Videos/Webcam/sonntag/gspca/dvb-ttusb-dspbootcode.h
/home/ice/Videos/Webcam/sonntag/gspca/dvb-usb.h
/home/ice/Videos/Webcam/sonntag/gspca/dvb-usb-common.h
/home/ice/Videos/Webcam/sonntag/gspca/dvb-usb-dvb.c
/home/ice/Videos/Webcam/sonntag/gspca/dvb-usb-firmware.c
/home/ice/Videos/Webcam/sonntag/gspca/dvb-usb-i2c.c
/home/ice/Videos/Webcam/sonntag/gspca/dvb-usb-ids.h
/home/ice/Videos/Webcam/sonntag/gspca/dvb-usb-init.c
/home/ice/Videos/Webcam/sonntag/gspca/dvb-usb-remote.c
/home/ice/Videos/Webcam/sonntag/gspca/dvb-usb-urb.c
/home/ice/Videos/Webcam/sonntag/gspca/dw2102.c
/home/ice/Videos/Webcam/sonntag/gspca/dw2102.h
/home/ice/Videos/Webcam/sonntag/gspca/eds1547.h
/home/ice/Videos/Webcam/sonntag/gspca/et61x251.txt
/home/ice/Videos/Webcam/sonntag/gspca/examples.xml
/home/ice/Videos/Webcam/sonntag/gspca/extract_xc3028.pl
/home/ice/Videos/Webcam/sonntag/gspca/faq.txt
/home/ice/Videos/Webcam/sonntag/gspca/fdl-appendix.xml
/home/ice/Videos/Webcam/sonntag/gspca/fieldseq_bt.gif
/home/ice/Videos/Webcam/sonntag/gspca/fieldseq_bt.pdf
/home/ice/Videos/Webcam/sonntag/gspca/fieldseq_tb.gif
/home/ice/Videos/Webcam/sonntag/gspca/fieldseq_tb.pdf
/home/ice/Videos/Webcam/sonntag/gspca/firedtv.h
/home/ice/Videos/Webcam/sonntag/gspca/firedtv-1394.c
/home/ice/Videos/Webcam/sonntag/gspca/firedtv-avc.c
/home/ice/Videos/Webcam/sonntag/gspca/firedtv-ci.c
/home/ice/Videos/Webcam/sonntag/gspca/firedtv-dvb.c
/home/ice/Videos/Webcam/sonntag/gspca/firedtv-fe.c
/home/ice/Videos/Webcam/sonntag/gspca/firedtv-rc.c
/home/ice/Videos/Webcam/sonntag/gspca/flexcop.c
/home/ice/Videos/Webcam/sonntag/gspca/flexcop.h
/home/ice/Videos/Webcam/sonntag/gspca/flexcop-common.h
/home/ice/Videos/Webcam/sonntag/gspca/flexcop-dma.c
/home/ice/Videos/Webcam/sonntag/gspca/flexcop-eeprom.c
/home/ice/Videos/Webcam/sonntag/gspca/flexcop-fe-tuner.c
/home/ice/Videos/Webcam/sonntag/gspca/flexcop-hw-filter.c
/home/ice/Videos/Webcam/sonntag/gspca/flexcop-i2c.c
/home/ice/Videos/Webcam/sonntag/gspca/flexcop_ibi_value_be.h
/home/ice/Videos/Webcam/sonntag/gspca/flexcop_ibi_value_le.h
/home/ice/Videos/Webcam/sonntag/gspca/flexcop-misc.c
/home/ice/Videos/Webcam/sonntag/gspca/flexcop-pci.c
/home/ice/Videos/Webcam/sonntag/gspca/flexcop-reg.h
/home/ice/Videos/Webcam/sonntag/gspca/flexcop-sram.c
/home/ice/Videos/Webcam/sonntag/gspca/flexcop-usb.c
/home/ice/Videos/Webcam/sonntag/gspca/flexcop-usb.h
/home/ice/Videos/Webcam/sonntag/gspca/friio.c
/home/ice/Videos/Webcam/sonntag/gspca/friio.h
/home/ice/Videos/Webcam/sonntag/gspca/friio-fe.c
/home/ice/Videos/Webcam/sonntag/gspca/frontend.xml
/home/ice/Videos/Webcam/sonntag/gspca/func-close.xml
/home/ice/Videos/Webcam/sonntag/gspca/func-ioctl.xml
/home/ice/Videos/Webcam/sonntag/gspca/func-mmap.xml
/home/ice/Videos/Webcam/sonntag/gspca/func-munmap.xml
/home/ice/Videos/Webcam/sonntag/gspca/func-open.xml
/home/ice/Videos/Webcam/sonntag/gspca/func-poll.xml
/home/ice/Videos/Webcam/sonntag/gspca/func-read.xml
/home/ice/Videos/Webcam/sonntag/gspca/func-select.xml
/home/ice/Videos/Webcam/sonntag/gspca/func-write.xml
/home/ice/Videos/Webcam/sonntag/gspca/fw-calling.txt
/home/ice/Videos/Webcam/sonntag/gspca/fw-decoder-api.txt
/home/ice/Videos/Webcam/sonntag/gspca/fw-decoder-regs.txt
/home/ice/Videos/Webcam/sonntag/gspca/fw-dma.txt
/home/ice/Videos/Webcam/sonntag/gspca/fw-encoder-api.txt
/home/ice/Videos/Webcam/sonntag/gspca/fw-memory.txt
/home/ice/Videos/Webcam/sonntag/gspca/fw-osd-api.txt
/home/ice/Videos/Webcam/sonntag/gspca/fw-upload.txt
/home/ice/Videos/Webcam/sonntag/gspca/get_dvb_firmware
/home/ice/Videos/Webcam/sonntag/gspca/gl861.c
/home/ice/Videos/Webcam/sonntag/gspca/gl861.h
/home/ice/Videos/Webcam/sonntag/gspca/gp8psk.c
/home/ice/Videos/Webcam/sonntag/gspca/gp8psk.h
/home/ice/Videos/Webcam/sonntag/gspca/gp8psk-fe.c
/home/ice/Videos/Webcam/sonntag/gspca/gspca.txt
/home/ice/Videos/Webcam/sonntag/gspca/hauppauge-wintv-cx88-ir.txt
/home/ice/Videos/Webcam/sonntag/gspca/hgimport
/home/ice/Videos/Webcam/sonntag/gspca/HOWTO-use-the-demux-api
/home/ice/Videos/Webcam/sonntag/gspca/HOWTO-use-the-frontend-api
/home/ice/Videos/Webcam/sonntag/gspca/ibmcam.txt
/home/ice/Videos/Webcam/sonntag/gspca/ICs
/home/ice/Videos/Webcam/sonntag/gspca/Insmod-options
/home/ice/Videos/Webcam/sonntag/gspca/INSTALL
/home/ice/Videos/Webcam/sonntag/gspca/intro.xml
/home/ice/Videos/Webcam/sonntag/gspca/io.xml
/home/ice/Videos/Webcam/sonntag/gspca/ir-functions.c
/home/ice/Videos/Webcam/sonntag/gspca/ir-keymaps.c
/home/ice/Videos/Webcam/sonntag/gspca/isl6405.c
/home/ice/Videos/Webcam/sonntag/gspca/isl6405.h
/home/ice/Videos/Webcam/sonntag/gspca/isl6421.c
/home/ice/Videos/Webcam/sonntag/gspca/isl6421.h
/home/ice/Videos/Webcam/sonntag/gspca/isl6423.c
/home/ice/Videos/Webcam/sonntag/gspca/isl6423.h
/home/ice/Videos/Webcam/sonntag/gspca/itd1000.c
/home/ice/Videos/Webcam/sonntag/gspca/itd1000.h
/home/ice/Videos/Webcam/sonntag/gspca/itd1000_priv.h
/home/ice/Videos/Webcam/sonntag/gspca/Kconfig
/home/ice/Videos/Webcam/sonntag/gspca/kdapi.xml
/home/ice/Videos/Webcam/sonntag/gspca/keytable.c.xml
/home/ice/Videos/Webcam/sonntag/gspca/ksym_mx1.c
/home/ice/Videos/Webcam/sonntag/gspca/l64781.c
/home/ice/Videos/Webcam/sonntag/gspca/l64781.h
/home/ice/Videos/Webcam/sonntag/gspca/lgdt330x.c
/home/ice/Videos/Webcam/sonntag/gspca/lgdt330x.h
/home/ice/Videos/Webcam/sonntag/gspca/lgdt330x_priv.h
/home/ice/Videos/Webcam/sonntag/gspca/lgdt3304.c
/home/ice/Videos/Webcam/sonntag/gspca/lgdt3304.h
/home/ice/Videos/Webcam/sonntag/gspca/lgdt3305.c
/home/ice/Videos/Webcam/sonntag/gspca/lgdt3305.h
/home/ice/Videos/Webcam/sonntag/gspca/lgs8gl5.c
/home/ice/Videos/Webcam/sonntag/gspca/lgs8gl5.h
/home/ice/Videos/Webcam/sonntag/gspca/lgs8gxx.c
/home/ice/Videos/Webcam/sonntag/gspca/lgs8gxx.h
/home/ice/Videos/Webcam/sonntag/gspca/lgs8gxx_priv.h
/home/ice/Videos/Webcam/sonntag/gspca/libv4l.xml
/home/ice/Videos/Webcam/sonntag/gspca/lifeview.txt
/home/ice/Videos/Webcam/sonntag/gspca/lnbh24.h
/home/ice/Videos/Webcam/sonntag/gspca/lnbp21.c
/home/ice/Videos/Webcam/sonntag/gspca/lnbp21.h
/home/ice/Videos/Webcam/sonntag/gspca/m920x.c
/home/ice/Videos/Webcam/sonntag/gspca/m920x.h
/home/ice/Videos/Webcam/sonntag/gspca/m5602.txt
/home/ice/Videos/Webcam/sonntag/gspca/MAKEDEV
/home/ice/Videos/Webcam/sonntag/gspca/Makefile
/home/ice/Videos/Webcam/sonntag/gspca/mc44s803.c
/home/ice/Videos/Webcam/sonntag/gspca/mc44s803.h
/home/ice/Videos/Webcam/sonntag/gspca/mc44s803_priv.h
/home/ice/Videos/Webcam/sonntag/gspca/media.tmpl
/home/ice/Videos/Webcam/sonntag/gspca/media-entities.tmpl
/home/ice/Videos/Webcam/sonntag/gspca/media-indices.tmpl
/home/ice/Videos/Webcam/sonntag/gspca/memory.h
/home/ice/Videos/Webcam/sonntag/gspca/meye.txt
/home/ice/Videos/Webcam/sonntag/gspca/Modprobe.conf
/home/ice/Videos/Webcam/sonntag/gspca/Modules.conf
/home/ice/Videos/Webcam/sonntag/gspca/mt20xx.c
/home/ice/Videos/Webcam/sonntag/gspca/mt20xx.h
/home/ice/Videos/Webcam/sonntag/gspca/mt312.c
/home/ice/Videos/Webcam/sonntag/gspca/mt312.h
/home/ice/Videos/Webcam/sonntag/gspca/mt312_priv.h
/home/ice/Videos/Webcam/sonntag/gspca/mt352.c
/home/ice/Videos/Webcam/sonntag/gspca/mt352.h
/home/ice/Videos/Webcam/sonntag/gspca/mt352_priv.h
/home/ice/Videos/Webcam/sonntag/gspca/mt2060.c
/home/ice/Videos/Webcam/sonntag/gspca/mt2060.h
/home/ice/Videos/Webcam/sonntag/gspca/mt2060_priv.h
/home/ice/Videos/Webcam/sonntag/gspca/mt2131.c
/home/ice/Videos/Webcam/sonntag/gspca/mt2131.h
/home/ice/Videos/Webcam/sonntag/gspca/mt2131_priv.h
/home/ice/Videos/Webcam/sonntag/gspca/mt2266.c
/home/ice/Videos/Webcam/sonntag/gspca/mt2266.h
/home/ice/Videos/Webcam/sonntag/gspca/mx1_camera.h
/home/ice/Videos/Webcam/sonntag/gspca/mx1_camera_fiq.S
/home/ice/Videos/Webcam/sonntag/gspca/mx3_camera.h
/home/ice/Videos/Webcam/sonntag/gspca/mxl5005s.c
/home/ice/Videos/Webcam/sonntag/gspca/mxl5005s.h
/home/ice/Videos/Webcam/sonntag/gspca/mxl5007t.c
/home/ice/Videos/Webcam/sonntag/gspca/mxl5007t.h
/home/ice/Videos/Webcam/sonntag/gspca/net.xml
/home/ice/Videos/Webcam/sonntag/gspca/not-in-cx2388x-datasheet.txt
/home/ice/Videos/Webcam/sonntag/gspca/nova-t-usb2.c
/home/ice/Videos/Webcam/sonntag/gspca/nxt200x.c
/home/ice/Videos/Webcam/sonntag/gspca/nxt200x.h
/home/ice/Videos/Webcam/sonntag/gspca/nxt6000.c
/home/ice/Videos/Webcam/sonntag/gspca/nxt6000.h
/home/ice/Videos/Webcam/sonntag/gspca/nxt6000_priv.h
/home/ice/Videos/Webcam/sonntag/gspca/opera1.c
/home/ice/Videos/Webcam/sonntag/gspca/opera-firmware.txt
/home/ice/Videos/Webcam/sonntag/gspca/or51132.c
/home/ice/Videos/Webcam/sonntag/gspca/or51132.h
/home/ice/Videos/Webcam/sonntag/gspca/or51211.c
/home/ice/Videos/Webcam/sonntag/gspca/or51211.h
/home/ice/Videos/Webcam/sonntag/gspca/ov511.txt
/home/ice/Videos/Webcam/sonntag/gspca/pcm990-baseboard.c
/home/ice/Videos/Webcam/sonntag/gspca/pixfmt.xml
/home/ice/Videos/Webcam/sonntag/gspca/pixfmt-grey.xml
/home/ice/Videos/Webcam/sonntag/gspca/pixfmt-nv12.xml
/home/ice/Videos/Webcam/sonntag/gspca/pixfmt-nv16.xml
/home/ice/Videos/Webcam/sonntag/gspca/pixfmt-packed-rgb.xml
/home/ice/Videos/Webcam/sonntag/gspca/pixfmt-packed-yuv.xml
/home/ice/Videos/Webcam/sonntag/gspca/pixfmt-sbggr8.xml
/home/ice/Videos/Webcam/sonntag/gspca/pixfmt-sbggr16.xml
/home/ice/Videos/Webcam/sonntag/gspca/pixfmt-sgbrg8.xml
/home/ice/Videos/Webcam/sonntag/gspca/pixfmt-sgrbg8.xml
/home/ice/Videos/Webcam/sonntag/gspca/pixfmt-uyvy.xml
/home/ice/Videos/Webcam/sonntag/gspca/pixfmt-vyuy.xml
/home/ice/Videos/Webcam/sonntag/gspca/pixfmt-y16.xml
/home/ice/Videos/Webcam/sonntag/gspca/pixfmt-y41p.xml
/home/ice/Videos/Webcam/sonntag/gspca/pixfmt-yuv410.xml
/home/ice/Videos/Webcam/sonntag/gspca/pixfmt-yuv411p.xml
/home/ice/Videos/Webcam/sonntag/gspca/pixfmt-yuv420.xml
/home/ice/Videos/Webcam/sonntag/gspca/pixfmt-yuv422p.xml
/home/ice/Videos/Webcam/sonntag/gspca/pixfmt-yuyv.xml
/home/ice/Videos/Webcam/sonntag/gspca/pixfmt-yvyu.xml
/home/ice/Videos/Webcam/sonntag/gspca/pluto2.c
/home/ice/Videos/Webcam/sonntag/gspca/PROBLEMS
/home/ice/Videos/Webcam/sonntag/gspca/pt1.c
/home/ice/Videos/Webcam/sonntag/gspca/pxa_camera.txt
/home/ice/Videos/Webcam/sonntag/gspca/qt1010.c
/home/ice/Videos/Webcam/sonntag/gspca/qt1010.h
/home/ice/Videos/Webcam/sonntag/gspca/qt1010_priv.h
/home/ice/Videos/Webcam/sonntag/gspca/radio-aimslab.c
/home/ice/Videos/Webcam/sonntag/gspca/radio-aztech.c
/home/ice/Videos/Webcam/sonntag/gspca/radio-cadet.c
/home/ice/Videos/Webcam/sonntag/gspca/radio-gemtek.c
/home/ice/Videos/Webcam/sonntag/gspca/radio-gemtek-pci.c
/home/ice/Videos/Webcam/sonntag/gspca/radio-maestro.c
/home/ice/Videos/Webcam/sonntag/gspca/radio-maxiradio.c
/home/ice/Videos/Webcam/sonntag/gspca/radio-mr800.c
/home/ice/Videos/Webcam/sonntag/gspca/radio-rtrack2.c
/home/ice/Videos/Webcam/sonntag/gspca/radio-sf16fmi.c
/home/ice/Videos/Webcam/sonntag/gspca/radio-sf16fmr2.c
/home/ice/Videos/Webcam/sonntag/gspca/radio-si470x.h
/home/ice/Videos/Webcam/sonntag/gspca/radio-si470x-common.c
/home/ice/Videos/Webcam/sonntag/gspca/radio-si470x-i2c.c
/home/ice/Videos/Webcam/sonntag/gspca/radio-si470x-usb.c
/home/ice/Videos/Webcam/sonntag/gspca/radio-si4713.c
/home/ice/Videos/Webcam/sonntag/gspca/radio-tea5764.c
/home/ice/Videos/Webcam/sonntag/gspca/radio-terratec.c
/home/ice/Videos/Webcam/sonntag/gspca/radiotrack.txt
/home/ice/Videos/Webcam/sonntag/gspca/radio-trust.c
/home/ice/Videos/Webcam/sonntag/gspca/radio-typhoon.c
/home/ice/Videos/Webcam/sonntag/gspca/radio-zoltrix.c
/home/ice/Videos/Webcam/sonntag/gspca/readme.txt
/home/ice/Videos/Webcam/sonntag/gspca/README
/home/ice/Videos/Webcam/sonntag/gspca/README.CABLE
/home/ice/Videos/Webcam/sonntag/gspca/README.cpia
/home/ice/Videos/Webcam/sonntag/gspca/README.cpia2
/home/ice/Videos/Webcam/sonntag/gspca/README.cx88
/home/ice/Videos/Webcam/sonntag/gspca/README.dvb-usb
/home/ice/Videos/Webcam/sonntag/gspca/README.EON
/home/ice/Videos/Webcam/sonntag/gspca/README.freeze
/home/ice/Videos/Webcam/sonntag/gspca/README.hm12
/home/ice/Videos/Webcam/sonntag/gspca/README.ir
/home/ice/Videos/Webcam/sonntag/gspca/README.ivtv
/home/ice/Videos/Webcam/sonntag/gspca/README.patches
/home/ice/Videos/Webcam/sonntag/gspca/README.pvrusb2
/home/ice/Videos/Webcam/sonntag/gspca/README.quirks
/home/ice/Videos/Webcam/sonntag/gspca/README.saa7134
/home/ice/Videos/Webcam/sonntag/gspca/README.valgrind
/home/ice/Videos/Webcam/sonntag/gspca/README.vbi
/home/ice/Videos/Webcam/sonntag/gspca/README.WINVIEW
/home/ice/Videos/Webcam/sonntag/gspca/remote_controllers.xml
/home/ice/Videos/Webcam/sonntag/gspca/s5h1409.c
/home/ice/Videos/Webcam/sonntag/gspca/s5h1409.h
/home/ice/Videos/Webcam/sonntag/gspca/s5h1411.c
/home/ice/Videos/Webcam/sonntag/gspca/s5h1411.h
/home/ice/Videos/Webcam/sonntag/gspca/s5h1420.c
/home/ice/Videos/Webcam/sonntag/gspca/s5h1420.h
/home/ice/Videos/Webcam/sonntag/gspca/s5h1420_priv.h
/home/ice/Videos/Webcam/sonntag/gspca/s921_core.c
/home/ice/Videos/Webcam/sonntag/gspca/s921_core.h
/home/ice/Videos/Webcam/sonntag/gspca/s921_module.c
/home/ice/Videos/Webcam/sonntag/gspca/s921_module.h
/home/ice/Videos/Webcam/sonntag/gspca/saa7146_core.c
/home/ice/Videos/Webcam/sonntag/gspca/saa7146_fops.c
/home/ice/Videos/Webcam/sonntag/gspca/saa7146_hlp.c
/home/ice/Videos/Webcam/sonntag/gspca/saa7146_i2c.c
/home/ice/Videos/Webcam/sonntag/gspca/saa7146_vbi.c
/home/ice/Videos/Webcam/sonntag/gspca/saa7146_video.c
/home/ice/Videos/Webcam/sonntag/gspca/se401.txt
/home/ice/Videos/Webcam/sonntag/gspca/setup.c
/home/ice/Videos/Webcam/sonntag/gspca/si21xx.c
/home/ice/Videos/Webcam/sonntag/gspca/si21xx.h
/home/ice/Videos/Webcam/sonntag/gspca/si470x.txt
/home/ice/Videos/Webcam/sonntag/gspca/si4713.txt
/home/ice/Videos/Webcam/sonntag/gspca/si4713-i2c.c
/home/ice/Videos/Webcam/sonntag/gspca/si4713-i2c.h
/home/ice/Videos/Webcam/sonntag/gspca/sms-cards.c
/home/ice/Videos/Webcam/sonntag/gspca/sms-cards.h
/home/ice/Videos/Webcam/sonntag/gspca/smscoreapi.c
/home/ice/Videos/Webcam/sonntag/gspca/smscoreapi.h
/home/ice/Videos/Webcam/sonntag/gspca/smsdvb.c
/home/ice/Videos/Webcam/sonntag/gspca/smsendian.c
/home/ice/Videos/Webcam/sonntag/gspca/smsendian.h
/home/ice/Videos/Webcam/sonntag/gspca/smsir.c
/home/ice/Videos/Webcam/sonntag/gspca/smsir.h
/home/ice/Videos/Webcam/sonntag/gspca/smssdio.c
/home/ice/Videos/Webcam/sonntag/gspca/smsusb.c
/home/ice/Videos/Webcam/sonntag/gspca/sn9c102.txt
/home/ice/Videos/Webcam/sonntag/gspca/soc-camera.txt
/home/ice/Videos/Webcam/sonntag/gspca/Sound-FAQ
/home/ice/Videos/Webcam/sonntag/gspca/sp887x.c
/home/ice/Videos/Webcam/sonntag/gspca/sp887x.h
/home/ice/Videos/Webcam/sonntag/gspca/sp8870.c
/home/ice/Videos/Webcam/sonntag/gspca/sp8870.h
/home/ice/Videos/Webcam/sonntag/gspca/Specs
/home/ice/Videos/Webcam/sonntag/gspca/stb0899_algo.c
/home/ice/Videos/Webcam/sonntag/gspca/stb0899_cfg.h
/home/ice/Videos/Webcam/sonntag/gspca/stb0899_drv.c
/home/ice/Videos/Webcam/sonntag/gspca/stb0899_drv.h
/home/ice/Videos/Webcam/sonntag/gspca/stb0899_priv.h
/home/ice/Videos/Webcam/sonntag/gspca/stb0899_reg.h
/home/ice/Videos/Webcam/sonntag/gspca/stb6000.c
/home/ice/Videos/Webcam/sonntag/gspca/stb6000.h
/home/ice/Videos/Webcam/sonntag/gspca/stb6100.c
/home/ice/Videos/Webcam/sonntag/gspca/stb6100.h
/home/ice/Videos/Webcam/sonntag/gspca/stb6100_cfg.h
/home/ice/Videos/Webcam/sonntag/gspca/stv090x.c
/home/ice/Videos/Webcam/sonntag/gspca/stv090x.h
/home/ice/Videos/Webcam/sonntag/gspca/stv090x_priv.h
/home/ice/Videos/Webcam/sonntag/gspca/stv090x_reg.h
/home/ice/Videos/Webcam/sonntag/gspca/stv0288.c
/home/ice/Videos/Webcam/sonntag/gspca/stv0288.h
/home/ice/Videos/Webcam/sonntag/gspca/stv0297.c
/home/ice/Videos/Webcam/sonntag/gspca/stv0297.h
/home/ice/Videos/Webcam/sonntag/gspca/stv0299.c
/home/ice/Videos/Webcam/sonntag/gspca/stv0299.h
/home/ice/Videos/Webcam/sonntag/gspca/stv680.txt
/home/ice/Videos/Webcam/sonntag/gspca/stv0900.h
/home/ice/Videos/Webcam/sonntag/gspca/stv0900_core.c
/home/ice/Videos/Webcam/sonntag/gspca/stv0900_init.h
/home/ice/Videos/Webcam/sonntag/gspca/stv0900_priv.h
/home/ice/Videos/Webcam/sonntag/gspca/stv0900_reg.h
/home/ice/Videos/Webcam/sonntag/gspca/stv0900_sw.c
/home/ice/Videos/Webcam/sonntag/gspca/stv6110.c
/home/ice/Videos/Webcam/sonntag/gspca/stv6110.h
/home/ice/Videos/Webcam/sonntag/gspca/stv6110x.c
/home/ice/Videos/Webcam/sonntag/gspca/stv6110x.h
/home/ice/Videos/Webcam/sonntag/gspca/stv6110x_priv.h
/home/ice/Videos/Webcam/sonntag/gspca/stv6110x_reg.h
/home/ice/Videos/Webcam/sonntag/gspca/tda80xx.c
/home/ice/Videos/Webcam/sonntag/gspca/tda80xx.h
/home/ice/Videos/Webcam/sonntag/gspca/tda826x.c
/home/ice/Videos/Webcam/sonntag/gspca/tda826x.h
/home/ice/Videos/Webcam/sonntag/gspca/tda827x.c
/home/ice/Videos/Webcam/sonntag/gspca/tda827x.h
/home/ice/Videos/Webcam/sonntag/gspca/tda1002x.h
/home/ice/Videos/Webcam/sonntag/gspca/tda1004x.c
/home/ice/Videos/Webcam/sonntag/gspca/tda1004x.h
/home/ice/Videos/Webcam/sonntag/gspca/tda8083.c
/home/ice/Videos/Webcam/sonntag/gspca/tda8083.h
/home/ice/Videos/Webcam/sonntag/gspca/tda8261.c
/home/ice/Videos/Webcam/sonntag/gspca/tda8261.h
/home/ice/Videos/Webcam/sonntag/gspca/tda8261_cfg.h
/home/ice/Videos/Webcam/sonntag/gspca/tda8290.c
/home/ice/Videos/Webcam/sonntag/gspca/tda8290.h
/home/ice/Videos/Webcam/sonntag/gspca/tda9887.c
/home/ice/Videos/Webcam/sonntag/gspca/tda9887.h
/home/ice/Videos/Webcam/sonntag/gspca/tda10021.c
/home/ice/Videos/Webcam/sonntag/gspca/tda10023.c
/home/ice/Videos/Webcam/sonntag/gspca/tda10048.c
/home/ice/Videos/Webcam/sonntag/gspca/tda10048.h
/home/ice/Videos/Webcam/sonntag/gspca/tda10086.c
/home/ice/Videos/Webcam/sonntag/gspca/tda10086.h
/home/ice/Videos/Webcam/sonntag/gspca/tda18271.h
/home/ice/Videos/Webcam/sonntag/gspca/tda18271-common.c
/home/ice/Videos/Webcam/sonntag/gspca/tda18271-fe.c
/home/ice/Videos/Webcam/sonntag/gspca/tda18271-maps.c
/home/ice/Videos/Webcam/sonntag/gspca/tda18271-priv.h
/home/ice/Videos/Webcam/sonntag/gspca/tdhd1.h
/home/ice/Videos/Webcam/sonntag/gspca/tea5761.c
/home/ice/Videos/Webcam/sonntag/gspca/tea5761.h
/home/ice/Videos/Webcam/sonntag/gspca/tea5767.c
/home/ice/Videos/Webcam/sonntag/gspca/tea5767.h
/home/ice/Videos/Webcam/sonntag/gspca/technisat.txt
/home/ice/Videos/Webcam/sonntag/gspca/tef6862.c
/home/ice/Videos/Webcam/sonntag/gspca/THANKS
/home/ice/Videos/Webcam/sonntag/gspca/ttpci-eeprom.c
/home/ice/Videos/Webcam/sonntag/gspca/ttpci-eeprom.h
/home/ice/Videos/Webcam/sonntag/gspca/ttusb2.c
/home/ice/Videos/Webcam/sonntag/gspca/ttusb2.h
/home/ice/Videos/Webcam/sonntag/gspca/ttusb_dec.c
/home/ice/Videos/Webcam/sonntag/gspca/ttusb-dec.txt
/home/ice/Videos/Webcam/sonntag/gspca/ttusbdecfe.c
/home/ice/Videos/Webcam/sonntag/gspca/ttusbdecfe.h
/home/ice/Videos/Webcam/sonntag/gspca/tua6100.c
/home/ice/Videos/Webcam/sonntag/gspca/tua6100.h
/home/ice/Videos/Webcam/sonntag/gspca/tuner-i2c.h
/home/ice/Videos/Webcam/sonntag/gspca/Tuners
/home/ice/Videos/Webcam/sonntag/gspca/tuner-simple.c
/home/ice/Videos/Webcam/sonntag/gspca/tuner-simple.h
/home/ice/Videos/Webcam/sonntag/gspca/tuner-types.c
/home/ice/Videos/Webcam/sonntag/gspca/tuner-xc2028.c
/home/ice/Videos/Webcam/sonntag/gspca/tuner-xc2028.h
/home/ice/Videos/Webcam/sonntag/gspca/tuner-xc2028-types.h
/home/ice/Videos/Webcam/sonntag/gspca/udev.txt
/home/ice/Videos/Webcam/sonntag/gspca/umt-010.c
/home/ice/Videos/Webcam/sonntag/gspca/usb-urb.c
/home/ice/Videos/Webcam/sonntag/gspca/v4l2.xml
/home/ice/Videos/Webcam/sonntag/gspca/v4l2-framework.txt
/home/ice/Videos/Webcam/sonntag/gspca/v4l2grab.c.xml
/home/ice/Videos/Webcam/sonntag/gspca/v4lgrab.c
/home/ice/Videos/Webcam/sonntag/gspca/va1j5jf8007s.c
/home/ice/Videos/Webcam/sonntag/gspca/va1j5jf8007s.h
/home/ice/Videos/Webcam/sonntag/gspca/va1j5jf8007t.c
/home/ice/Videos/Webcam/sonntag/gspca/va1j5jf8007t.h
/home/ice/Videos/Webcam/sonntag/gspca/valgrind-1.0.4.diff
/home/ice/Videos/Webcam/sonntag/gspca/valgrind-1.9.4.diff
/home/ice/Videos/Webcam/sonntag/gspca/valgrind-20030716.diff
/home/ice/Videos/Webcam/sonntag/gspca/vbi_525.gif
/home/ice/Videos/Webcam/sonntag/gspca/vbi_525.pdf
/home/ice/Videos/Webcam/sonntag/gspca/vbi_625.gif
/home/ice/Videos/Webcam/sonntag/gspca/vbi_625.pdf
/home/ice/Videos/Webcam/sonntag/gspca/vbi_hsync.gif
/home/ice/Videos/Webcam/sonntag/gspca/vbi_hsync.pdf
/home/ice/Videos/Webcam/sonntag/gspca/ves1x93.c
/home/ice/Videos/Webcam/sonntag/gspca/ves1x93.h
/home/ice/Videos/Webcam/sonntag/gspca/ves1820.c
/home/ice/Videos/Webcam/sonntag/gspca/ves1820.h
/home/ice/Videos/Webcam/sonntag/gspca/video.xml
/home/ice/Videos/Webcam/sonntag/gspca/videodev2.h.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-cropcap.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-dbg-g-chip-ident.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-dbg-g-register.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-encoder-cmd.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-enumaudio.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-enumaudioout.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-enum-fmt.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-enum-frameintervals.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-enum-framesizes.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-enuminput.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-enumoutput.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-enumstd.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-g-audio.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-g-audioout.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-g-crop.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-g-ctrl.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-g-enc-index.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-g-ext-ctrls.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-g-fbuf.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-g-fmt.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-g-frequency.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-g-input.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-g-jpegcomp.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-g-modulator.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-g-output.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-g-parm.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-g-priority.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-g-sliced-vbi-cap.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-g-std.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-g-tuner.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-log-status.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-overlay.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-qbuf.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-querybuf.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-querycap.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-queryctrl.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-querystd.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-reqbufs.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-s-hw-freq-seek.xml
/home/ice/Videos/Webcam/sonntag/gspca/vidioc-streamon.xml
/home/ice/Videos/Webcam/sonntag/gspca/vp702x.c
/home/ice/Videos/Webcam/sonntag/gspca/vp702x.h
/home/ice/Videos/Webcam/sonntag/gspca/vp702x-fe.c
/home/ice/Videos/Webcam/sonntag/gspca/vp7045.c
/home/ice/Videos/Webcam/sonntag/gspca/vp7045.h
/home/ice/Videos/Webcam/sonntag/gspca/vp7045-fe.c
/home/ice/Videos/Webcam/sonntag/gspca/w9966.txt
/home/ice/Videos/Webcam/sonntag/gspca/w9968cf.txt
/home/ice/Videos/Webcam/sonntag/gspca/xc5000.c
/home/ice/Videos/Webcam/sonntag/gspca/xc5000.h
/home/ice/Videos/Webcam/sonntag/gspca/z0194a.h
/home/ice/Videos/Webcam/sonntag/gspca/zc0301.txt
/home/ice/Videos/Webcam/sonntag/gspca/zl10036.c
/home/ice/Videos/Webcam/sonntag/gspca/zl10036.h
/home/ice/Videos/Webcam/sonntag/gspca/zl10039.c
/home/ice/Videos/Webcam/sonntag/gspca/zl10039.h
/home/ice/Videos/Webcam/sonntag/gspca/zl10353.c
/home/ice/Videos/Webcam/sonntag/gspca/zl10353.h
/home/ice/Videos/Webcam/sonntag/gspca/zl10353_priv.h
/home/ice/Videos/Webcam/sonntag/gspca/Zoran
/home/ice/Videos/Webcam/sonntag/gspca/zr364xx.txt
```

```
ice@ice-desktop:~$ cd '/home/ice/Videos/Webcam/montag' 
ice@ice-desktop:~/Videos/Webcam/montag$ make
make -C /home/ice/Videos/Webcam/montag/v4l 
make: *** /home/ice/Videos/Webcam/montag/v4l: No such file or directory.  Schluss.
make: *** [all] Fehler 2
ice@ice-desktop:~/Videos/Webcam/montag$ 

```

---

### Post by MasterPoulos89 on 2009-11-10
Just download and install the latest kernel. Worked for me....even in Karmic.

Here is the site: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I will confirm kernel 2.6.32-r6 works for my lifecam-vx3000 in Karmic.

Hope this helps.

---

### Post by stanca on 2009-11-10
> **daniroma said:**
> Hi Stanca.
I use new Karmic Koala 9.10. It works for me with a little bit change of your solution.
sudo apt-get install subversion build-essential linux-headers-$(uname -r)go to site 
[http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2) Download ”tip.tar.bz2” file.
Untar it. You will have one folder named gspca*.
cd gspca*/v4l (* = rest of folder name)
make all
sudo make install

Note: **1** You can configure drivers you may want to install:
sudo apt-get install subversion build-essential linux-headers-$(uname -r) 
~/gspca-18a214ccf825$ make menuconfig
now choose options for suitable drivers.
just be sure you choose gspca and sonixj
**2 **I am Romanian too. Daca iti este mai usor, putem discuta. Si eu am instalat destul de greu camera asta. Dar informatiile tale mi-au fost de un real folos.

I followed exactly your solution from the first but it didn't work.Maybe because I have the vx-1000 version?:mad:

---

### Post by ventper on 2009-11-12
> **MasterPoulos89 said:**
> Just download and install the latest kernel. Worked for me....even in Karmic.

Here is the site: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I will confirm kernel 2.6.32-r6 works for my lifecam-vx3000 in Karmic.

Hope this helps.

worked on my sister's ubuntu karmic install.

[LIST=1]
[*]downloaded the kernel image above/\
[*]navigate to where the image downloaded to
[*]```
sudo dpkg -i linux-image-2.6.32*******
```**********(whichever image you received)**
[*]reboot
[*]load the installed linux-image
[/LIST]
video on LifeCam VX-3000 up n runnin'

thanks to;
MasterPoulos89
 bribera: [http://preview.tinyurl.com/briberaPost33](http://preview.tinyurl.com/briberaPost33)

---

### Post by ctomayer on 2009-11-13
I just updated my kernel to 2.6.32-r6 in 9.10, but no luck in Skype - just a fairly garbled/blocky picture.  What app are you using the camera with?

Thanks.

---

### Post by daniroma on 2009-11-14
Hi Stanca
It use the same driver sonixj. if VX-1000 works, then VX-3000 work too.
Maybe something is missing in kernel.
My first installation failed. So I make this:
/your gspca_folder$sudo make rminstall

Then try to reinstall driver. Maybe you can send some feedback from your console.

Maybe they fix this in last kernel as [MasterPoulos89]("http://ubuntuforums.org/member.php?u=724912") described in his post. Who knows? You should try.

Good Luck!

---

### Post by stanca on 2009-11-14
I hope for new kernel updates too,or maybe mr. Jean Francois comes with a new better working driver.;)
Thanks anyway.

---

### Post by tenshi_jpn on 2009-11-17
hi, just downloaded the new version of kernel 2.6.32 for 32bits and installed the image first.
the installation was ok but when i tried to install the linux headers for 2.6.32 i got missing dependencies message error.

how should i solve this error?

any help?

---

