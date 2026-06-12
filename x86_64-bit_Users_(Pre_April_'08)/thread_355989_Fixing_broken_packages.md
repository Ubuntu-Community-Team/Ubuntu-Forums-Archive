---
title: "Fixing broken packages"
date: 2007-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2007-02-07
Update Manager listed several packages to upgrade, one of which was samba. I told it to go ahead and it upgraded all but samba. For samba it gave me a popup that said 

E: /var/cache/apt/archives/samba_3.0.22-1ubuntu4.1_amd64.deb: subprocess new pre-removal script returned error exit status 102.

It also suggested that I use either Synaptic or sudo apt-get install -f to fix the problem. I tried Synaptic first but it failed to fix the problem. It won't upgrade samba (same error message) and it won't allow me to remove it so I can reinstall it.

Then I tried sudo apt-get install -f and got:

```
jjj@Devil5:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python2.5-minimal python2.5
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3410kB of archives.
After unpacking 16.4kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 177375 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu4 (using .../samba_3.0.22-1ubuntu4.1_amd64.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu4.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu4.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Meantime I can still get to my Windows desktop, so samba must be still running OK. But I need to fix this problem. And this is not the first time I have had a broken package that refused to be fixed. I need an industrial strength package fixer.

---

### Post by amohanty on 2007-02-08
How about purging it (backup config files first and then reinstalling it)

apt-get --purge remove samba
apt-get install samba

AM

---

### Post by John Jason Jordan on 2007-02-08
> **amohanty said:**
> How about purging it (backup config files first and then reinstalling it)
apt-get --purge remove samba
apt-get install samba
Thanks for the suggestion. I'm still new to Linux and didn't know about --purge. Sadly, it did not work:

```
jjj@Devil5:~$ sudo apt-get --purge remove samba
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python2.5-minimal python2.5 samba
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  samba*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 8376kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 177374 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--purge):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
jjj@Devil5:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python2.5-minimal python2.5
Use 'apt-get autoremove' to remove them.
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3410kB of archives.
After unpacking 16.4kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 177375 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu4 (using .../samba_3.0.22-1ubuntu4.1_amd64.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu4.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu4.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jjj@Devil5:~$ 
jjj@Devil5:~$ jjj@Devil5:~$ sudo apt-get --purge remove samba
bash: jjj@Devil5:~$: command not found
jjj@Devil5:~$ Password:
bash: Password:: command not found
jjj@Devil5:~$ Reading package lists... Done
bash: Reading: command not found
jjj@Devil5:~$ Building dependency tree       
bash: Building: command not found
jjj@Devil5:~$ Reading state information... Done
bash: Reading: command not found
jjj@Devil5:~$ The following packages were automatically installed and are no longer required:
bash: The: command not found
jjj@Devil5:~$   python2.5-minimal python2.5 samba
bash: python2.5-minimal: command not found
jjj@Devil5:~$ Use 'apt-get autoremove' to remove them.
bash: Use: command not found
jjj@Devil5:~$ The following packages will be REMOVED:
bash: The: command not found
jjj@Devil5:~$   samba*
bash: samba*: command not found
jjj@Devil5:~$ 0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
bash: 0: command not found
jjj@Devil5:~$ Need to get 0B of archives.
bash: Need: command not found
jjj@Devil5:~$ After unpacking 8376kB disk space will be freed.
bash: After: command not found
jjj@Devil5:~$ Do you want to continue [Y/n]? y
bash: Do: command not found
jjj@Devil5:~$ (Reading database ... 177374 files and directories currently installed.)
bash: Reading: command not found
jjj@Devil5:~$ Removing samba ...
bash: Removing: command not found
jjj@Devil5:~$ invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
bash: invoke-rc.d:: command not found
jjj@Devil5:~$ dpkg: error processing samba (--purge):
bash: syntax error near unexpected token `('
jjj@Devil5:~$  subprocess pre-removal script returned error exit status 102
bash: subprocess: command not found
jjj@Devil5:~$ Errors were encountered while processing:
bash: Errors: command not found
jjj@Devil5:~$  samba
bash: samba: command not found
jjj@Devil5:~$ E: Sub-process /usr/bin/dpkg returned an error code (1)
bash: syntax error near unexpected token `('
jjj@Devil5:~$ jjj@Devil5:~$ sudo apt-get install samba
bash: jjj@Devil5:~$: command not found
jjj@Devil5:~$ Reading package lists... Done
bash: Reading: command not found
jjj@Devil5:~$ Building dependency tree       
bash: Building: command not found
jjj@Devil5:~$ Reading state information... Done
bash: Reading: command not found
jjj@Devil5:~$ The following packages were automatically installed and are no longer required:
bash: The: command not found
jjj@Devil5:~$   python2.5-minimal python2.5
bash: python2.5-minimal: command not found
jjj@Devil5:~$ Use 'apt-get autoremove' to remove them.
bash: Use: command not found
jjj@Devil5:~$ Recommended packages:
bash: Recommended: command not found
jjj@Devil5:~$   smbldap-tools
bash: smbldap-tools: command not found
jjj@Devil5:~$ The following packages will be upgraded:
bash: The: command not found
jjj@Devil5:~$   samba
bash: samba: command not found
jjj@Devil5:~$ 1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bash: 1: command not found
jjj@Devil5:~$ Need to get 0B/3410kB of archives.
bash: Need: command not found
jjj@Devil5:~$ After unpacking 16.4kB of additional disk space will be used.
bash: After: command not found
jjj@Devil5:~$ Preconfiguring packages ...
bash: Preconfiguring: command not found
jjj@Devil5:~$ Selecting previously deselected package samba.
bash: Selecting: command not found
jjj@Devil5:~$ (Reading database ... 177375 files and directories currently installed.)
bash: Reading: command not found
jjj@Devil5:~$ Preparing to replace samba 3.0.22-1ubuntu4 (using .../samba_3.0.22-1ubuntu4.1_amd64.deb) ...
bash: syntax error near unexpected token `('
jjj@Devil5:~$ invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
bash: invoke-rc.d:: command not found
jjj@Devil5:~$ dpkg: warning - old pre-removal script returned error exit status 102
bash: dpkg:: command not found
jjj@Devil5:~$ dpkg - trying script from the new package instead ...
dpkg: need an action option
Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].
Options marked [*] produce a lot of output - pipe it through `less' or `more' !
jjj@Devil5:~$ invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
bash: invoke-rc.d:: command not found
jjj@Devil5:~$ dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu4.1_amd64.deb (--unpack):
bash: syntax error near unexpected token `('
jjj@Devil5:~$  subprocess new pre-removal script returned error exit status 102
bash: subprocess: command not found
jjj@Devil5:~$ Errors were encountered while processing:
bash: Errors: command not found
jjj@Devil5:~$  /var/cache/apt/archives/samba_3.0.22-1ubuntu4.1_amd64.deb
bash: /var/cache/apt/archives/samba_3.0.22-1ubuntu4.1_amd64.deb: Permission denied
jjj@Devil5:~$ E: Sub-process /usr/bin/dpkg returned an error code (1)
bash: syntax error near unexpected token `('
jjj@Devil5:~$ jjj@Devil5:~$ 
bash: jjj@Devil5:~$: command not found
```
I hope the error messages in there will help someone tell me what I need to do to fix it.

---

### Post by JAPrufrock on 2007-02-11
Try this link:

[http://ubuntuforums.org/archive/index.php/t-6318.html](http://ubuntuforums.org/archive/index.php/t-6318.html)

---

