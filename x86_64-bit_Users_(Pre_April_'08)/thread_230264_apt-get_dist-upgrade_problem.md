---
title: "apt-get dist-upgrade problem"
date: 2006-08-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by cosmoshell on 2006-08-05
i keep getting this when i use apt-get dist upgrade.
you might want to run `apt-get -f install' to currect these.
the following packages have umet dependencies: ftp: Depends: libreadline5 (>= 5.1) but 5.0-10 is installed
initramfs-tools: depends: volumeid but it is not installed
parted: Depends: libreadline5 (>= 5.1) but 5.0-10 is installed
ubuntu-minimal: depends: wpasupplicant but is not installed
E: unmet dependencies. try using -f.

---

### Post by cocteau on 2006-08-05
I've gotten that a couple of times. It went away for me if you do what it asks you to in the first line. Type 'sudo apt-get -f install' in a terminal.

---

### Post by cosmoshell on 2006-08-06
sudo apt-get -f install

pressed y when asked and 

preconfiguring packages ...
(reading database ,... 13132 files and directories currently installed.)
unpacking volumeid (from .../volumeid_093-0ubuntu8_amd64.deb (--unpack):
trying to overwrite `/sbin/vol_id', witch is also in package udev errors where encounterd while processing:
/var/cache/apt/archives/volumeid_093-0ubuntu8_amd64.deb
E: Sub-process /usr/bin/dpkg returned and error code (1)

---

### Post by cocteau on 2006-08-06
That looks strange. My best guess would to try and clean out apt's cache by doing:

sudo apt-get autoclean

and then try again. I know there is also a way to get dpkg to reconfigure itself but I'll be damned if I can remember what it is. I've googled for it but can't seem to find it. Anyway, it's late for me now. I'll look in the mourning.

---

### Post by cocteau on 2006-08-06
Yeah, I know... I couldn't let it go...

The dpkg command is:

sudo dpkg --configure -a

Hope that helps.

---

### Post by cosmoshell on 2006-08-06
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of parted;
 parted depends on libreadline5 (>= 5.1); however: Verison of libreadline5 on system os 5.0-10 dpkg: error processing parted(--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ftp:
ftp depends on libreadline5 (>= 5.1); however: Verison of libreadline5 on system os 5.0-10 dpkg: error processing parted(--configure):
dpkg: error processing ftp (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
ubuntu-minimal depends on initramfs-tools; however:
package initramfs-tools is not configured yet.
 ubuntu-minimal depends on wpasupplicant; however:
package wpasupplicant is not installed.
dpkg: eror proccesing ubuntu-minimal (--configure):
dependency problems - leaving unconfigured
Erors were encountered while processing:
initramfs-tools
parted
ftp
ubuntu-minimal
#

---

### Post by Kilz on 2006-08-06
> **cosmoshell said:**
> dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of parted;
 parted depends on libreadline5 (>= 5.1); however: Verison of libreadline5 on system os 5.0-10 dpkg: error processing parted(--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ftp:
ftp depends on libreadline5 (>= 5.1); however: Verison of libreadline5 on system os 5.0-10 dpkg: error processing parted(--configure):
dpkg: error processing ftp (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
ubuntu-minimal depends on initramfs-tools; however:
package initramfs-tools is not configured yet.
 ubuntu-minimal depends on wpasupplicant; however:
package wpasupplicant is not installed.
dpkg: eror proccesing ubuntu-minimal (--configure):
dependency problems - leaving unconfigured
Erors were encountered while processing:
initramfs-tools
parted
ftp
ubuntu-minimal
#

Try this to purge the cashe

```
sudo apt-get clean
```

---

### Post by cosmoshell on 2006-08-06
still doesent work same erors

---

### Post by ergo_pro on 2006-10-26
Getting same problem when trying to upgrade from 5.10 to 6.10 (edgy)

I'm getting that

trying to overwrite `/sbin/vol_id', witch is also in package udev

---

### Post by kuja on 2006-10-26
Remove the packages that have the broken dependencies, do the apt-get -f install, do the rest of the  upgrade, then reinstall the programs (ftp, parted, initramfs, ubuntu-minimal). Then do reinstall the desktop package too just-in-case.

Don't reboot before the entire upgrading process is complete or your system will be severely broken.

---

### Post by cristianoparis on 2006-11-04
I fixed the problem about volume_id using this command:

dpkg --force-overwrite -i /var/cache/apt/archives/volumeid_093-0ubuntu18_i386.deb /var/cache/apt/archives/initramfs-tools_0.69ubuntu20_all.deb

which installs volumeid overwriting /sbin/vol_id, which is in the udev package as well (don't ask why).

Then apt-get dist-upgrade and everything went just fine.

---

