---
title: "ATI drivers, no sound =/ How ?"
date: 2005-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by ChaperonNoir on 2005-03-04
Hello.

I just installed Ubuntu linux for A64 (hoary version).

im having 2 problems 


1- Sound
First of, i have no sound.

I have my headset plugged on my integrated sound card.

My motherboard is the Chaintech VNF3-250 (socket 754).

I have tried alsamixer, i dont really know what to do but it does not seem to work.

2- ATI drivers.

My friends tell me its incredibly hard with an ATI card on linux.

My card is an ati 9800 pro 128 mb . What should i do ? try to install with the instructions on the ati website [https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

or using this. [http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

The commands dont seem to work with me.... strange.

heres what i get 
 ```
sudo apt-get install linux-686
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package linux-686

```

---

### Post by kubla on 2005-03-05
[QUOTE=ChaperonNoir]Hello.

or using this. [http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

The commands dont seem to work with me.... strange.

heres what i get 
 ```
sudo apt-get install linux-686
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package linux-686

```[/QUOTE]

Which kernel are you running? (get the output from 'sudo uname -a')

You probably want to replace linux-686 in your apt-get install line with linux-amd64-generic

But first, double-check the output of uname!

Ian

---

### Post by ChaperonNoir on 2005-03-05
Hello
My kernel is :
```
Linux amd64 2.6.10-3-amd64-generic #1 Tue Feb 15 20:46:55 UTC 2005 x86_64 GNU/Linux
``` 

From what i can see on the tutorial, the proper kernel is older so im okay.

Im blocked damnit !

At the step ( use the package name in the error message)

```
root@amd64:/home/edmond # apt-get install fglrx-driver
Reading Package Lists... Done
Building Dependency Tree... Done
Package fglrx-driver is a virtual package provided by:
  xorg-driver-fglrx 6.8.0-8.8.25-0ubuntu6
  xfree86-driver-fglrx 4.3.0-8.8.25-0ubuntu6
You should explicitly select one to install.
E: Package fglrx-driver has no installation candidate
root@amd64:/home/edmond # apt-get install xorg-driver
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package xorg-driver
root@amd64:/home/edmond # apt-get install xorg-driver-fglrx
Reading Package Lists... Done
Building Dependency Tree... Done
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/6542kB of archives.
After unpacking 20.1MB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 90213 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu6_amd64.deb) ...
dpkg-divert: `diversion of /usr/lib32/libGL.so.1 to /usr/lib32/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx' clashes with `diversion of /usr/lib32/libGL.so.1to /usr/lib32/libGL.so.1.distrib by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu6_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu6_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@amd64:/home/edmond # apt-get install xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu6_amd64.deb
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu6_amd64.deb
root@amd64:/home/edmond #   
``` 

As you can see, when i use the package name given in the error message, i get a could not find the package

And i want the xorg package. Hope this helps.

---

### Post by BigCdaAnswer3 on 2005-03-05
i know the xorg-fglrx-drivers are included in the restricted packages section, are you sure you have your /etc/apt/sources.list file setup correctly?

---

### Post by kubla on 2005-03-05
The key is in this line:

dpkg-divert: `diversion of /usr/lib32/libGL.so.1 to /usr/lib32/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx' clashes with `diversion of /usr/lib32/libGL.so.1to /usr/lib32/libGL.so.1.distrib by xorg-driver-fglrx'

I don't know if there's a way to "clear" existing diversions.

You could try to install the package using dpkg and using some force options but I'm hoping someone might have some better advice.

Ian

---

### Post by kubla on 2005-03-05
[QUOTE=kubla]The key is in this line:

dpkg-divert: `diversion of /usr/lib32/libGL.so.1 to /usr/lib32/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx' clashes with `diversion of /usr/lib32/libGL.so.1to /usr/lib32/libGL.so.1.distrib by xorg-driver-fglrx'

I don't know if there's a way to "clear" existing diversions.

You could try to install the package using dpkg and using some force options but I'm hoping someone might have some better advice.

Ian[/QUOTE]

Now I'm on to it... type:

dpkg-divert --list | grep /usr/lib32/libGL.so.1

That should show the current diversions for the file.

Now, try:

dpkg-divert --remove /usr/lib32/libGL.so.1

Then:

dpkg -i /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu6_amd64.deb

Ian

---

### Post by ChaperonNoir on 2005-03-05
```
**root@amd64:/home/edmond # dpkg-divert --list | grep /usr/lib32/libGL.so.1**
diversion of /usr/lib32/libGL.so.1 to /usr/lib32/libGL.so.1.distrib by xorg-driver-fglrx
diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/libGL.so.1.2.distrib by xorg-driver-fglrx
**root@amd64:/home/edmond # dpkg-divert --remove /usr/lib32/libGL.so.1**
Removing `diversion of /usr/lib32/libGL.so.1 to /usr/lib32/libGL.so.1.distrib by xorg-driver-fglrx'
**root@amd64:/home/edmond # dpkg -i /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu6_amd64.deb**
(Reading database ... 90212 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu6_amd64.deb) ...
dpkg-divert: `diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx' clashes with `diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/libGL.so.1.2.distrib by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu6_amd64.deb (--install):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu6_amd64.deb
``` 


 :-k  I don't know whats wrong. I must say i don't understand this step. What is a diversion :p

---

### Post by kubla on 2005-03-06
[QUOTE=ChaperonNoir]```
**root@amd64:/home/edmond # dpkg-divert --list | grep /usr/lib32/libGL.so.1**
diversion of /usr/lib32/libGL.so.1 to /usr/lib32/libGL.so.1.distrib by xorg-driver-fglrx
diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/libGL.so.1.2.distrib by xorg-driver-fglrx
**root@amd64:/home/edmond # dpkg-divert --remove /usr/lib32/libGL.so.1**
Removing `diversion of /usr/lib32/libGL.so.1 to /usr/lib32/libGL.so.1.distrib by xorg-driver-fglrx'
**root@amd64:/home/edmond # dpkg -i /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu6_amd64.deb**
(Reading database ... 90212 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu6_amd64.deb) ...
dpkg-divert: `diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx' clashes with `diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/libGL.so.1.2.distrib by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu6_amd64.deb (--install):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu6_amd64.deb
``` 


 :-k  I don't know whats wrong. I must say i don't understand this step. What is a diversion :p[/QUOTE]
 
OK, so it seems there are two existing diverts that are causing you grief.

Try:

dpkg-divert --remove /usr/lib32/libGL.so.1

dpkg-divert --remove /usr/lib32/libGL.so.1.2

then:

dpkg -i /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.8.25-0ubuntu6_amd64.deb

What's a divert? From the manpage (man dpkg-divert):

DESCRIPTION
       File  `diversions' are a way of forcing dpkg not to install a file into
       its location, but to a `diverted'  location.  Diversions  can  be  used
       through the Debian package scripts to move a file away when it causes a
       conflict. System administrators can also use it to override some  pack-
       age's  configuration  file, or whenever some files (which aren't marked
       as 'conffiles') need to be preserved by dpkg, when installing  a  newer
       version of a package which contains those files.

---

### Post by ChaperonNoir on 2005-03-06
Kubla.. Its working  :grin:  :grin:  \\:D/ 

After your steps, i just followed the guide, pasted a few lines, reboot and now it works.

Thank you for your help ;)

---

### Post by kubla on 2005-03-06
Ah, cool. Glad to have been able to help.

Ian

---

### Post by ChaperonNoir on 2005-03-06
It works great. But the drivers are really bad thought. I guess it will take some time for ATI to make better drivers  :roll:

---

### Post by n0mad on 2005-03-15
I don't see how this helps solve sound problem, though. I'm having the same problem with sound. I have amd64 2800+ and Chaintech nForce3 250 VNF3. Installed hoary, and everything seems to run fine, but i get no sound output. I tweaked alsamixer (and all the other existing mixers in the world), still no output.
Any thoughts on this?

---

### Post by ChaperonNoir on 2005-03-16
I tried many things n0mad.

Nothing seems to work..

Maybe we should install the Nforce 3 drivers ( 64 bits )

[http://www.nvidia.com/object/linux_nforce_amd64_1.0-0292.html](http://www.nvidia.com/object/linux_nforce_amd64_1.0-0292.html)

THe installation doent recognise my kernel thouight

---

