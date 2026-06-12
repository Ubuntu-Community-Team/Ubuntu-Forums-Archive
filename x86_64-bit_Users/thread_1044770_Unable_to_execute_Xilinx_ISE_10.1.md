---
title: "Unable to execute Xilinx ISE 10.1"
date: 2009-01-19
forum: x86 64-bit Users
---

### Post by vertago1 on 2009-01-19
I installed ISE Webpack 10.1 successfully but after making settings64.sh executable and running it I get no output from the console. Also I noticed there is no "ise" file in the bin/lin64/ folder. Does anyone have any suggestions? thanks

---

### Post by vertago1 on 2009-01-21
I have tried to understand the 10.1 section of this page ([https://help.ubuntu.com/community/XilinxISE]("https://help.ubuntu.com/community/XilinxISE")) but I haven't gotten anywhere except that I know that /opt/Xilinx/10.1/ISE/bin/lin64/ise or /opt/Xilinx/10.1/ISE/bin/lin/ise do not exist

I have two different 64bit machines running kubuntu 8.10 and both have the same issue with ise not existing. Please help!

I am going to try to not use the web install and see if the 2.2gb installer works better

---

### Post by vertago1 on 2009-01-21
No progress at all, the full install rejects the x86_64 arc

---

### Post by cheebi on 2009-03-02
> **vertago1 said:**
> No progress at all, the full install rejects the x86_64 arc

Does anyone have a solution on this problem? ...

---

### Post by sansor on 2009-03-28
I installed 32-bit version on 64-bit Intrepid. And on top of it, I installed EDK. Both work great (I also installed them on opensuse but it freezed a lot. Ubuntu is much better)

1- Install ia32 libraries from Synaptic.
2- start setup by: $ linux32 ./setup

Then it will setup bin/lin/ise. You can start it by 
$ source ISE/settings32.sh
$ linux32 ISE/bin/lin/ise

Also I installed EDK with
$ linux32 ./setup 
$ source ISE/settings32.sh
$ source EDK/settings32.sh
$ linux32 EDK/bin/lin/xps

All works great without freeze...

---

### Post by xur17 on 2009-04-19
I got xilinx ISE 10.1 to work on my 64 bit copy of ubuntu intrepid (now jaunty).  I posted the details of it here:

[http://www.tuxguides.com/2009/04/17/xilinx-ise-101/](http://www.tuxguides.com/2009/04/17/xilinx-ise-101/)

---

### Post by wiznillyp on 2009-09-22
> **xur17 said:**
> I got xilinx ISE 10.1 to work on my 64 bit copy of ubuntu intrepid (now jaunty).  I posted the details of it here:

[http://www.tuxguides.com/2009/04/17/xilinx-ise-101/](http://www.tuxguides.com/2009/04/17/xilinx-ise-101/)Were you able to get the Simulator working with 10.1?

I have tried this: [https://help.ubuntu.com/community/XilinxISE](https://help.ubuntu.com/community/XilinxISE) to no avial.

I am also using 64-bit Ubuntu and 10.1.

---

### Post by xur17 on 2009-09-23
> **wiznillyp said:**
> Were you able to get the Simulator working with 10.1?

I have tried this: [https://help.ubuntu.com/community/XilinxISE](https://help.ubuntu.com/community/XilinxISE) to no avial.

I am also using 64-bit Ubuntu and 10.1.

No, I just got the programming part of it to work (it has been a while since I have used the program).  Also, to make it even more fun, my board could not be programmed with xilinx, but instead I had to use a separate program.  This program only worked in Windows, but did not work in Virtualbox with shared usb.  I had to use qemu instead.  I had windows installed in qemu specifically for programming the board.

In hindsight, I probably should have used windows...  But I am stubborn...

---

### Post by wiznillyp on 2009-09-23
Exactly what I am doing now.

I just got VirtualBox going with a Windows XP install. And of course... I lost my CD key (whatever that is). Google is an asset as times.  :)

So, getting the Simulator to work with 10.1 is just insanely difficult, the ISE directory structure is complicated as hell.

One of these days, someone that is a lot smarter than me is going to figure this **** out... hopefully they document it well.

Though, I wonder if the Simulator even works in RedHat 64 (which is supposedly supported), I can't imagine there being that much difference in the distros...

---

