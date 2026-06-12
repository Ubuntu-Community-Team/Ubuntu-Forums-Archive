---
title: "Need Help with error when installing a package"
date: 2009-07-31
forum: x86 64-bit Users
---

### Post by cchester on 2009-07-31
Hello,

I had previously had this working and had to reinstall Ubuntu 9.04 64bit. Now I am trying to reinstall lightscribe software that I was using before and I get the following error after doing the force option from the command line.

Here it is:

I ran this first :

sudo dpkg --force-architecture -i lightscribe-1.18.6.1-linux-2.6-intel.deb

Then I get the following error:

dpkg-deb: --control lightscribe-1.18.6.1-linux-2.6-intel.deb /var/lib/dpkg/tmp.ci
(Reading database ... 152920 files and directories currently installed.)
Unpacking lightscribe (from lightscribe-1.18.6.1-linux-2.6-intel.deb) ...
dpkg-deb: --fsys-tarfile lightscribe-1.18.6.1-linux-2.6-intel.deb
cp: cannot stat `lightscribe-1.18.6.1-linux-2.6-intel.deb': No such file or directory
cd: 52: can't cd to debian/*/
dpkg: error processing lightscribe-1.18.6.1-linux-2.6-intel.deb (--install):
 corrupted filesystem tarfile - corrupted package archive
Errors were encountered while processing:
 lightscribe-1.18.6.1-linux-2.6-intel.deb


I have redownloaded the file numerous times and I have even tried using previous versions of the file that worked in the past and now for some reason it would work.

I installed the ia32-libs like I did before but nothing works. So does anyone have any ideas?

Thanks.

Me an others all get this error so I don't know if it is a bug in 9.04 Ubuntu 64bit or what exactly.

Never mind I created a 64bit version and it works fine now. Please disregard.

---

### Post by slightlystoopid on 2009-08-26
I'm getting this error as well with a different 32 bit package. I did a clean install of ubuntu 9.04 command line only from the alternate cd onto a usb device, then did a dist-upgrade, installed xfce4 and ia32-libs, then tried installing the .deb off my hard drive. I don't get this error on my regular system.

Some more information here: [http://ubuntuforums.org/showthread.php?p=7832187#post7832187](http://ubuntuforums.org/showthread.php?p=7832187#post7832187)

---

