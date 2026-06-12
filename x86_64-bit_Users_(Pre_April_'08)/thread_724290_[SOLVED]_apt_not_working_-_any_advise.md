---
title: "[SOLVED] apt not working - any advise"
date: 2008-03-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2008-03-14
I can't get my updates and I can't seem to repair the package manager.  Have a look and tell me what to try next.

charles@Gigabyte-K7:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxine1-gnome tk8.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
dpkg: parse error, in file `/var/lib/dpkg/available' near line 9:
 missing package name
E: Sub-process /usr/bin/dpkg returned an error code (2)
charles@Gigabyte-K7:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxine1-gnome tk8.4
The following packages will be REMOVED:
  libxine1-gnome tk8.4
0 upgraded, 0 newly installed, 2 to remove and 5 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 2769kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/available' near line 9:
 missing package name
E: Sub-process /usr/bin/dpkg returned an error code (2)
charles@Gigabyte-K7:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/available' near line 9:
 missing package name
charles@Gigabyte-K7:~$

---

### Post by jeffus_il on 2008-03-14
First try: ```
sudo aptitude update
```

---

### Post by crjackson on 2008-03-14
> **jeffus_il said:**
> First try: ```
sudo aptitude update
```

No change.  Same issues...

---

### Post by sisco311 on 2008-03-14
Is something wrong with the /var/lib/dpkg/available file.

Try to restore the file:
```
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
```

---

### Post by NullHead on 2008-03-14
I would look at /var/lib/dpkg/available and at line 9. 

```
gksudo gedit /var/lib/dpkg/available
```

---

### Post by crjackson on 2008-03-14
> **sisco311 said:**
> Is something wrong with the /var/lib/dpkg/available file.

Try to restore the file:
```
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
```

The file didn't seem to exist any more.  This fixed the problem, thanks.

---

### Post by NullHead on 2008-03-14
A corrupt file perhaps? How does a file that root only access just get removed with out the user knowing??

---

### Post by crjackson on 2008-03-14
> **NullHead said:**
> A corrupt file perhaps? How does a file that root only access just get removed with out the user knowing??

Probably because my 4 teenage children are the users.  I've noticed lately that they have been rebooting from a locked desktop using the reset button.  I suspect the file became unreadable during one of these escapades...

---

