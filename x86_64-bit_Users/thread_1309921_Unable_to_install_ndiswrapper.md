---
title: "Unable to install ndiswrapper"
date: 2009-11-01
forum: x86 64-bit Users
---

### Post by gigurra on 2009-11-01
I'm quite new to ubuntu and linux but anyway, here goes.

I'm trying to install ndiswrapper (again) after I got a new wireless
adapter which will hopefully work (last one didnt).

Unfortunately I cannot even seem to install ndiswrapper, so getting to
the driver part is a long step ahead. :)

First I try the ubuntu apt-get way

```

jkjolhed@Gusaf:~$ sudo apt-get install ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed
  ndiswrapper-common
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
Need to get 0B/21.7kB of archives.
After this operation, 98.3kB of additional disk space will be used.
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 173053 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.54-2ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up ndiswrapper-common (1.54-2ubuntu1) ...
jkjolhed@Gusaf:~$ sudo apt-get install ndiswrapper-utils-1.9 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed
  ndiswrapper-utils-1.9
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
Need to get 0B/37.0kB of archives.
After this operation, 131kB of additional disk space will be used.
Selecting previously deselected package ndiswrapper-utils-1.9.
(Reading database ... 173064 files and directories currently installed.)
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.54-2ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up ndiswrapper-utils-1.9 (1.54-2ubuntu1) ...
jkjolhed@Gusaf:~$ 

```Running ndiswrapper after this yields segmentation fault:

```

jkjolhed@Gusaf:~$ ndiswrapper
Segmentation fault
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card

```Trying an ndiswrapper -l yields

```
jkjolhed@Gusaf:~$ ndiswrapper -l
Segmentation fault

```Right, something is clearly wrong there.
Dont know what 


Then I thought I could try downloading the source and compile it myself,
Update: 1.55 works, check new issue below

---

### Post by gigurra on 2009-11-01
Ok turns out I was trying to compile the wrong version of ndiswrapper

now I have a new issue :)

```

jkjolhed@Gusaf:~/belk$ sudo depmod -a
jkjolhed@Gusaf:~/belk$ sudo modprobe ndiswrapper
jkjolhed@Gusaf:~/belk$   tail /var/log/messages
Nov  1 20:18:51 Gusaf kernel: [ 4331.041812] modinfo[7715]: segfault at 2f ip 00007faaad131a87 sp 00007fff92bc4130 error 4 in libc-2.10.1.so[7faaad0e9000+166000]
Nov  1 20:18:53 Gusaf kernel: [ 4333.315407] modinfo[7725]: segfault at 2f ip 00007ffcea132a87 sp 00007fffa69db3d0 error 4 in libc-2.10.1.so[7ffcea0ea000+166000]
Nov  1 20:18:57 Gusaf kernel: [ 4337.819702] modinfo[7767]: segfault at 2f ip 00007f6412157a87 sp 00007fff98bb0950 error 4 in libc-2.10.1.so[7f641210f000+166000]
Nov  1 20:19:10 Gusaf kernel: [ 4349.900595] modinfo[7782]: segfault at 2f ip 00007f4d5228aa87 sp 00007fff48874b60 error 4 in libc-2.10.1.so[7f4d52242000+166000]
Nov  1 20:19:12 Gusaf kernel: [ 4352.725185] modinfo[7791]: segfault at 2f ip 00007f557ceafa87 sp 00007ffffa3cb790 error 4 in libc-2.10.1.so[7f557ce67000+166000]
Nov  1 20:36:18 Gusaf kernel: [ 5378.404010] npviewer.bin[8829]: segfault at ff99cd48 ip 00000000ff99cd48 sp 00000000ffb75f7c error 14
Nov  1 20:40:17 Gusaf kernel: [ 5616.745724] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Nov  1 20:40:17 Gusaf kernel: [ 5616.872871] usb 1-2: reset high speed USB device using ehci_hcd and address 2
Nov  1 20:40:17 Gusaf loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver netr28ux
Nov  1 20:40:17 Gusaf kernel: [ 5617.037914] usbcore: registered new interface driver ndiswrapper
jkjolhed@Gusaf:~/belk$ 


```The wireless adapter is a Belkin N150 USB adapter, and I installed it in win7 64 bit, 
from where I copied the inf and sys files into linux to try to run ndiswrapper on them

```

jkjolhed@Gusaf:~/belk$ sudo ndiswrapper -i netr28ux.inf
installing netr28ux ...
jkjolhed@Gusaf:~/belk$ ndiswrapper -l
netr28ux : driver installed
    device (050D:935A) present


```( i have also tried running a native linux driver but no luck, in that case i get stuck with "no network detected" 
[http://ubuntuforums.org/showthread.php?p=8217181#post8217181](http://ubuntuforums.org/showthread.php?p=8217181#post8217181) )

---

