---
title: "Trouble installing libc6-dev-amd64 (Newbie question, please don't flame)"
date: 2006-08-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by earnoth on 2006-08-10
I'm trying to install libc6-dev-amd64 on a fresh Ubuntu 6.06 AMD64 install.  I get the error that it can't find the package, but I see it in dapper:  [http://packages.ubuntulinux.org/dapper/libdevel/libc6-dev-amd6]("http://packages.ubuntulinux.org/dapper/libdevel/libc6-dev-amd64")

Here's the guts of my /etc/apt/sources.list:
```
root@atlas:~# grep -v "^#" /etc/apt/sources.list|grep -v "^$"
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
```

---

### Post by Kilz on 2006-08-10
> **earnoth said:**
> I'm trying to install libc6-dev-amd64 on a fresh Ubuntu 6.06 AMD64 install.  I get the error that it can't find the package, but I see it in dapper:  [http://packages.ubuntulinux.org/dapper/libdevel/libc6-dev-amd6]("http://packages.ubuntulinux.org/dapper/libdevel/libc6-dev-amd64")

Here's the guts of my /etc/apt/sources.list:
```
root@atlas:~# grep -v "^#" /etc/apt/sources.list|grep -v "^$"
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
```


One of the best things about Ubuntu is that newbies dont get flamed for asking questions most of the time. I know it turned me off of another distro, one of the main reasons I switched to Ubuntu. :D  
The package you linked to is a i386 version for developing for amd64. [You may want to look here]("http://packages.ubuntulinux.org/dapper/libdevel/libc6-dev") for a package for the amd64 version of Dapper or search for libc6-dev in apt or synaptic.

---

### Post by earnoth on 2006-08-10
> **earnoth said:**
> I'm trying to install libc6-dev-amd64 on a fresh Ubuntu 6.06 AMD64 install.  I get the error that it can't find the package, but I see it in dapper:  [http://packages.ubuntulinux.org/dapper/libdevel/libc6-dev-amd6]("http://packages.ubuntulinux.org/dapper/libdevel/libc6-dev-amd64")

Here's the guts of my /etc/apt/sources.list:
```
root@atlas:~# grep -v "^#" /etc/apt/sources.list|grep -v "^$"
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
```

Thanks much for the help, and the encouragement for posting "dumb" questions (it does get tedious when Linux sub-communities flame the newbies - and then wonder why Linux isn't on the desktop ;).  I checked and I've already got libc6-dev installed to the latest version.  I've still got issues now, and I wonder if their related to what you told me.

I'm trying to install VMware Server on AMD64 Ubuntu host, per this howto:  [http://www.howtoforge.com/ubuntu_vmware_server]("http://www.howtoforge.com/ubuntu_vmware_server")

However, when I get to a certain portion of the install, I receive the following error:
```
Generating SSL Server Certificate

Unable to get the last modification timestamp of the destination file
/etc/vmware/ssl/rui.key.

Execution aborted.
```

Having googled the issue like a good Geek, I find the following clue from here:[http://www.vmware.com/community/message.jspa?messageID=450264]("http://www.vmware.com/community/message.jspa?messageID=450264")
This is in response to someone with the exact same error I received.
> You are using 64bit CentOS, without any 32bit compatibility packages. Please install them, you need 32bit glibc, 32bit X libraries, 32bit pam modules - at bare minimum. 32bit gnome/gtk, and 32bit openssl certainly helps as well, but they are not mandatory.

So it sounds like I need 32bit compatibility packages.  What might those be on Ubuntu?

---

### Post by John.Michael.Kane on 2006-08-10
Have you tried installing the ia32-libs/ia32-libs-gtk. these seem to pull down the packages you need.

---

### Post by Kilz on 2006-08-10
> **earnoth said:**
> Thanks much for the help, and the encouragement for posting "dumb" questions (it does get tedious when Linux sub-communities flame the newbies - and then wonder why Linux isn't on the desktop ;).  I checked and I've already got libc6-dev installed to the latest version.  I've still got issues now, and I wonder if their related to what you told me.

I'm trying to install VMware Server on AMD64 Ubuntu host, per this howto:  [http://www.howtoforge.com/ubuntu_vmware_server]("http://www.howtoforge.com/ubuntu_vmware_server")

However, when I get to a certain portion of the install, I receive the following error:
```
Generating SSL Server Certificate

Unable to get the last modification timestamp of the destination file
/etc/vmware/ssl/rui.key.

Execution aborted.
```

Having googled the issue like a good Geek, I find the following clue from here:[http://www.vmware.com/community/message.jspa?messageID=450264]("http://www.vmware.com/community/message.jspa?messageID=450264")
This is in response to someone with the exact same error I received.


So it sounds like I need 32bit compatibility packages.  What might those be on Ubuntu?

In Ubuntu those packages start with ia32 [Here is the search results for those packages.]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ia32&searchon=names&subword=1&version=dapper&release=all") [The linux32]("http://packages.ubuntu.com/dapper/utils/linux32") is also nice to have. You may also find some usefull info on the Ubuntu wiki about [installing the vm server]("https://help.ubuntu.com/community/VmwareServer"). Im not sure, but it never hurts to have [more info.]("https://help.ubuntu.com/community/VMware_Guide%3a_Installing_VMware_Server_on_Ubuntu_6%2e06_LTS_amd64")

---

### Post by earnoth on 2006-08-10
Thanks to SD-Plissken and Kilz for their replies.  I installed ia32-libs and ia32-libs-gtk, that worked like a champ!

Everything is working now, thanks much guys.  :)

---

