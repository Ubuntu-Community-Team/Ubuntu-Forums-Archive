---
title: "sudo apt-get update
sudo apt-get upgrade error"
date: 2008-01-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by FrankM77 on 2008-01-10
Hello,
I am running Ubuntu Release 7.10 Kernel Linux 2.6.22-14-generic.

Everytime I try to install anything I get error messages associated with 3 packages:

cupsys
cupsys-driver-gutenprint
hplip

Below is an example of the errors I get when I try installing any packages:

frank@frank-desktop-linux:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  initramfs-tools initscripts
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up cupsys (1.3.2-1ubuntu7.3) ...
Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on cupsys (>= 1.1.20); however:
  Package cupsys is not configured yet.
dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cupsys-driver-gutenprint:
 cupsys-driver-gutenprint depends on cupsys (>= 1.2.5) | cups (>= 1.2.5); however:
  Package cupsys is not configured yet.
  Package cups is not installed.
dpkg: error processing cupsys-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cupsys
 hplip
 cupsys-driver-gutenprint
E: Sub-process /usr/bin/dpkg returned an error code (1)

Running sudo apt-get install -f does not work.  It just gives the same errors.

Running sudo dselect shows these 3 packages to be broken, but synaptic package mananger shows them installed with no errors. 

Can anyone please help, this is driving me nuts.

---

### Post by Kilz on 2008-01-10
> **FrankM77 said:**
> Hello,
I am running Ubuntu Release 7.10 Kernel Linux 2.6.22-14-generic.

Everytime I try to install anything I get error messages associated with 3 packages:

cupsys
cupsys-driver-gutenprint
hplip

Below is an example of the errors I get when I try installing any packages:

frank@frank-desktop-linux:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  initramfs-tools initscripts
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up cupsys (1.3.2-1ubuntu7.3) ...
Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on cupsys (>= 1.1.20); however:
  Package cupsys is not configured yet.
dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cupsys-driver-gutenprint:
 cupsys-driver-gutenprint depends on cupsys (>= 1.2.5) | cups (>= 1.2.5); however:
  Package cupsys is not configured yet.
  Package cups is not installed.
dpkg: error processing cupsys-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cupsys
 hplip
 cupsys-driver-gutenprint
E: Sub-process /usr/bin/dpkg returned an error code (1)

Running sudo apt-get install -f does not work.  It just gives the same errors.

Running sudo dselect shows these 3 packages to be broken, but synaptic package mananger shows them installed with no errors. 

Can anyone please help, this is driving me nuts.

Have you tried removing them , cleaning the cashe, then reinstalling them?
```
sudo apt-get clean
``` will clean the cashe.

---

### Post by FrankM77 on 2008-01-30
OK
I uninstalled cupsys, hplip, and cupsys-driver-gutenprint

I then opened terminal and typed "sudo apt-get clean"  (nothing appeared to happen at this point)

I then reinstalled the 3 packages that were uninstalled.

Lastly, this did not solve the problem.  I still get the same errors whenever I try to install any package.

Do you or anybody else have any other ideas???

---

