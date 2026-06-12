---
title: "Cant Login After System Went Off"
date: 2008-07-28
forum: x86 64-bit Users
---

### Post by magosla2001 on 2008-07-28
After a fatal shutdown of my system with ubuntu 8.04 (64bit) when I was downloading and installing updates my I tried booting in restore mode which required me to use fsck  as it could not be fixed automatically. When I get to the login screen and login using my username and password, 

I receive an error dialog message;
"Your session only lasted less than 10 seconds. if you have not logged out yourself this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the filesafe sessions to see if you can fix the problem"

From the ~/.xsession-errors file

/etc/gdm/xsession: begining session setup
setting IM through im.switch for local=en_NG
start IM through /etc/xll/xinit/xinput-d/all_ALL linked to /etc/xll/xinit/xinput.d/default
/usr/bin/seahorse-agent: error while loading shared libraries: libgnutls.so.13: cannot open shared object file: no such file in directory.


Try loggin with filesafe GNOME it send me back to login screen and still the same problem.

How do I get this problem fixed?

---

### Post by tamoneya on 2008-07-28
when grub loads hit "esc" and select ubuntu recovery.  Once you get to prompt run this:```
dpkg-reconfigure libgnutls13
```Then try restarting and logging in again.

---

### Post by magosla2001 on 2008-07-29
> **tamoneya said:**
> when grub loads hit "esc" and select ubuntu recovery.  Once you get to prompt run this:```
dpkg-reconfigure libgnutls13
```Then try restarting and logging in again.

where is the grud? If it is the bar that loads, I hit "esc" and nothing happen. I had to use the recovery mode form the boot menu, and I got to a prompt where I typed ```
dpkg-reconfigure libgnutls13
```

and error was below
> /usr/sbin/dpkg-reconfigure: libnutls13 is broken or not fully installed

---

### Post by tamoneya on 2008-07-29
> **magosla2001 said:**
> where is the grud? If it is the bar that loads, I hit "esc" and nothing happen. I had to use the recovery mode form the boot menu, and I got to a prompt where I typed ```
dpkg-reconfigure libgnutls13
```

and error was below

You did the grub thing correctly.  Basically we go into a command prompt.  Since that didnt work try this:```
apt-get update
apt-get check
apt-get remove libgnutls13
apt-get install libgnutls13
```

---

### Post by magosla2001 on 2008-07-29
> **tamoneya said:**
> You did the grub thing correctly.  Basically we go into a command prompt.  Since that didnt work try this:```
apt-get update
apt-get check
apt-get remove libgnutls13
apt-get install libgnutls13
```


Still no success

apt-get update : does not execute successfully and still suggests I run apt-get update

apt-get check : executes successfully

apt-get remove libgnutls13 : does not go well

apt-get install libgnutls13: does not go well and suggests I run apt-get -f

---

### Post by tamoneya on 2008-07-29
so what happens when you do as it says: ```
apt-get -f
```

---

### Post by cariboo on 2008-07-30
If apt-get update isn't working, you may not have a working network connection try:

```
dhclient ethx
```

where ethx is your network card, usually it is eth0.

Jim

---

### Post by magosla2001 on 2008-07-30
> **tamoneya said:**
> so what happens when you do as it says: ```
apt-get -f
```

Results from running

apt-get update:
Last four section
> W: Failed to fetch [http://ng.archive.ubuntu.com/ubuntu/dists/hardy-security/release.gpg](http://ng.archive.ubuntu.com/ubuntu/dists/hardy-security/release.gpg) Counld not resolve 

'security.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/release.gpg) Counld not resolve 

'security.ubuntu.com'
W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct problems


apt-get update:
Last line 
> E: Unmet dependencies. Try using -f
which corrects dependencies when done

apt-get remove libgnutls13
> Last line
E: Counln't find package libgnutls13

apt-get install libgnutls13

> Reading package lists... Done
Building dependency tree
Reading state information... Done
libgnutls13 is already the newest version.
you might want to run 'apt-get -f install' to correct these:
the following packages have unmet dependencies:
 evolution: Depends evolution-common (= 2.22.2-0ubuntu1.2) but 2.22.1-0ubuntu3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



apt-get -f install:
Part of the message

> (Reading database ... dpkg: error processing /var/cache/apt/archives/evolution-common_2.22.2-0ubuntu1.2_all.deb 

(--unpack):
 files list file for package 'linux-restricted-modules-common' is missing final newline
Error were encountered while processing:
/var/cache/apt/archives/evolution-common_2.22.2-0ubuntu1.2_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

