---
title: "Unable to update apt-sources for PPC"
date: 2005-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by moly on 2005-10-16
This is the error message I get when I try apt update. It has been this way for a week or so. I used a virgin sources.list before trying this time. Any suggestions?

moly@laptop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Reading task descriptions... Done
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Reading task descriptions... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: You may want to update the package lists to correct these missing files
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: You may want to update the package lists to correct these missing files

---

### Post by craks on 2005-10-17
[QUOTE=moly]This is the error message I get when I try apt update. It has been this way for a week or so. I used a virgin sources.list before trying this time. Any suggestions?

moly@laptop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Reading task descriptions... Done
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Reading task descriptions... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: You may want to update the package lists to correct these missing files
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: You may want to update the package lists to correct these missing files[/QUOTE]


you may paste the content of /etc/apt/sources.list here and check your dns has no problem, and your network works fine.

---

### Post by closet geek on 2005-11-18
[QUOTE=craks]you may paste the content of /etc/apt/sources.list here and check your dns has no problem, and your network works fine.[/QUOTE]

I have the same problem, did anyone solve this?

cg

---

### Post by bugrider on 2005-11-18
Check your proxy settings/application ! you're attempting to forward this traffic to port 80 on  the loopback (localhost) interface :

 Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)

---

### Post by iconoclasm on 2006-02-10
I have the very same problem: [http://ubuntuforums.org/showthread.php?p=721491#post721491](http://ubuntuforums.org/showthread.php?p=721491#post721491)

I've disabled all my proxies and checked all my confs, lists, and resolv.conf files. I can ping and host the domain archive.ubuntu.com and otherwise it looks great... but apt/synaptic are throwing a hairy trying to resolve the domain as 127.0.0.1 ...

if there is any hope for a solution.. I could use it right about now.

---

