---
title: "Fam doesn't work"
date: 2006-09-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by EvilGrin on 2006-09-22
I have an AMD64 based LAMP server. I've done a 'LAMP' install from the AMD64 server iso. I want to use the package 'apachetop' to monitor apache2. This pulls in fam as a dependancy. Now as far as I can tell the fam init script is broken. I get the following when I attempt to run '/etc/init.d/fam start'.
```
root@anubis:~# /etc/init.d/fam start
 * -n                                                                  [ ok ]
```

But no fam is running according to apachetop..
```

root@anubis:~# apachetop
cannot connect to fam: Connection refused
```

Any clues?

---

### Post by Wasca on 2007-07-04
[SIZE="5"]**A MORE UP TO DATE FIX FOR THIS CAN BE FOUND [HERE]("http://ubuntuforums.org/showthread.php?t=491733")**[/SIZE]

Hi All

If your reading this I bet your apachetop install is not working right?

Well good news I worked out how to get it working.

This is the scenario, you have installed Ubuntu Dapper 6.06-LTS and installed apachetop but it's not working. 

The following commands assume you are running as root, if your not you will need to type sudo in front of all the commands e.g. **sudo apt-get install apachetop**

1. Uninstall fam

```
root@server1:# apt-get remove fam
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  apachetop fam
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 365kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 18585 files and directories currently installed.)
Removing apachetop ...
Removing fam ...
 * Stopping file alteration monitor...
   ...done.
```

This should remove apachetop also

2. Install Portmap

```
root@sserver1:# apt-get install portmap
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  portmap
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.0kB of archives.
After unpacking 147kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com dapper/main portmap 5-16ubuntu2 [30.0kB]
Fetched 30.0kB in 2s (10.8kB/s)         
Preconfiguring packages ...
Selecting previously deselected package portmap.
(Reading database ... 18572 files and directories currently installed.)
Unpacking portmap (from .../portmap_5-16ubuntu2_i386.deb) ...
Setting up portmap (5-16ubuntu2) ...
 * Starting portmap daemon...
   ...done.
```

3. Install Apachetop

```
root@sserver1:# apt-get install apachetop
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  fam
The following NEW packages will be installed:
  apachetop fam
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/97.8kB of archives.
After unpacking 365kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package fam.
(Reading database ... 18567 files and directories currently installed.)
Unpacking fam (from .../fam_2.7.0-8ubuntu1_i386.deb) ...
Selecting previously deselected package apachetop.
Unpacking apachetop (from .../apachetop_0.12.5-7_i386.deb) ...
Setting up fam (2.7.0-8ubuntu1) ...
 * Starting file alteration monitor...
   ...done.

Setting up apachetop (0.12.5-7) ...
```

4. Now type apachetop and all should be good. :)
[SIZE="5"]
**GO TO [THIS FORUM POST]("http://ubuntuforums.org/showthread.php?t=491733") TO GET THIS WORKING**[/SIZE]

---

