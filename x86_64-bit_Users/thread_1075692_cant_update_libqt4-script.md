---
title: "cant update libqt4-script"
date: 2009-02-20
forum: x86 64-bit Users
---

### Post by earthtux on 2009-02-20
I just wonder if anyone else cannot upgrade this package
I am using 8.10, x61t lenovo laptop
after searching through the forum, some similar problems refer to the configuration of qt3 and qt4
anyone knows what exactly should both be configured?
thx!

---

### Post by Yellow Pasque on 2009-02-20
Can you post the output of:
```
sudo dpkg --configure -a
```

---

### Post by earthtux on 2009-02-23
```
dpkg: dependency problems prevent configuration of libqt4-designer:
 libqt4-designer depends on libqt4-script (= 4.4.3-0ubuntu1.2); however:
  Package libqt4-script is not installed.
dpkg: error processing libqt4-designer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-qt3support:
 libqt4-qt3support depends on libqt4-designer (= 4.4.3-0ubuntu1.2); however:
  Package libqt4-designer is not configured yet.
dpkg: error processing libqt4-qt3support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libqt4-designer
 libqt4-qt3support

```

hope this helps
thx for your reply :)

---

### Post by Yellow Pasque on 2009-02-23
> hope this helps
A little, but I probably should have told you to run:
```
sudo apt-get update
```
and then look at the output of:
```
sudo apt-get install libqt4-script
```

---

### Post by earthtux on 2009-02-24
the output of sudo apt-get install libqt4-script:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt4-qt3support libqt4-designer libqt4-network libqt4-sql libqt4-sql-mysql
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  libqt4-script
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 0B/436kB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 160355 files and directories currently installed.)
Preparing to replace libqt4-script 4.4.3-0ubuntu1.1 (using .../libqt4-script_4.4.3-0ubuntu1.2_amd64.deb) ...
Unpacking replacement libqt4-script ...
dpkg: error processing /var/cache/apt/archives/libqt4-script_4.4.3-0ubuntu1.2_amd64.deb (--unpack):
 unable to move aside `./usr/share/doc/libqt4-script' to install new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libqt4-script_4.4.3-0ubuntu1.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
thank you !

---

### Post by Yellow Pasque on 2009-02-24
> unable to move aside `./usr/share/doc/libqt4-script' to install new version: Operation not permitted
Hmm. That's one I haven't seen before. Someone recently filed this bug in Launchpad: [https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/331847](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/331847)
(Was that you?)
Let's check the permissions on it. Please post output of:
```
ls -la /usr/share/doc | grep libqt4-script
```

---

### Post by earthtux on 2009-02-24
ya that was me :P
```
----r-s-wT    1 537199049 2810314796 2078764171748 1922-12-15 22:47 libqt4-script

```
I dont understand what that T means?
even i change to root, I still cant remove it via rm.........
really appreciate!

---

### Post by Yellow Pasque on 2009-02-24
Those are strange permissions and I'm wondering if they were set that way intentionally. All of the entries in my /usr/share/doc directory are either directories or symbolic links.
Can you post output of:
```
file /usr/share/doc/libqt4-script
```
Also, take a look at the other files in /usr/share/doc and see if any other entries have those permissions:
```
cd /usr/share/doc
ls -la
cd libqt4-script
```

---

### Post by earthtux on 2009-02-24
```
j$ file /usr/share/doc/libqt4-script
/usr/share/doc/libqt4-script: setgid sticky writable, executable, regular file, no read permission

```

i cant cd into libqt4-script, got this error
```
bash: cd: libqt4-script: Not a directory

```
thx
other files / directories dont have T in their attribute..... only libqt4-script....

---

### Post by Yellow Pasque on 2009-02-24
See if you can change the permissions on it.
```
cd /usr/share/doc
sudo chown root:root libqt4-script
sudo chmod 755 libqt4-script
```

At this point, I would strongly recommend booting to a LiveCD environment, unmounting your hard disk partitions and running a check on your Ubuntu partition. For example, if it's sda1:
```
sudo e2fsck -c /dev/sda1
```

After you do that, boot back to your Ubuntu partition, and hopefully this will work:
```
sudo apt-get --reinstall install libqt4-script
```

---

### Post by earthtux on 2009-02-25
hi
the weird thing is that I cannot change the permission of that libqt4-script directory

after I do the e2fsck

that folder still has T attributes with it

here are the output
```
/usr/share/doc$ ls libqt4-script
libqt4-script
/usr/share/doc$ ls -al libqt4-script
----r-s-wT 1 537199049 2810314796 2078764171748 1922-12-15 22:47 libqt4-script
/usr/share/doc$ sudo apt-get --reinstall install libqt4-script
Password or swipe finger: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-json python-openssl libqt4-network deluge-torrent-common libqt4-sql
  python-pyopenssl libqt4-sql-mysql
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  libqt4-script
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/436kB of archives.
After this operation, 0B of additional disk space will be used.
Selecting previously deselected package libqt4-script.
(Reading database ... 159479 files and directories currently installed.)
Preparing to replace libqt4-script 4.4.3-0ubuntu1.1 (using .../libqt4-script_4.4.3-0ubuntu1.2_amd64.deb) ...
Unpacking replacement libqt4-script ...
dpkg: error processing /var/cache/apt/archives/libqt4-script_4.4.3-0ubuntu1.2_amd64.deb (--unpack):
 unable to move aside `./usr/share/doc/libqt4-script' to install new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libqt4-script_4.4.3-0ubuntu1.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
thx!
btw 
that libqt4-script should be directory right?

---

### Post by earthtux on 2009-02-26
bump bump
anyone?

---

### Post by Yellow Pasque on 2009-02-26
Yeah, it's supposed to be a directory, but it seems corrupted :/  The next thing I would suggest is to try removing it manually.
```
sudo rm -f /usr/share/doc/libqt4-script
```

---

### Post by earthtux on 2009-02-26
> **Temüjin said:**
> Yeah, it's supposed to be a directory, but it seems corrupted :/  The next thing I would suggest is to try removing it manually.
```
sudo rm -f /usr/share/doc/libqt4-script
```

that cannot remove it T_T
```
~$ sudo rm -f /usr/share/doc/libqt4-script
 
rm: cannot remove `/usr/share/doc/libqt4-script': Operation not permitted

```

---

### Post by Yellow Pasque on 2009-02-26
There's probably an easy way to axe the file that I'm unaware of, so hopefully, a real Linux guru comes along and schools me.

In the mean time, can you post output of:
```
lsattr /usr/share/doc/libqt4-script
```

---

### Post by earthtux on 2009-02-26
> **Temüjin said:**
> There's probably an easy way to axe the file that I'm unaware of, so hopefully, a real Linux guru comes along and schools me.

In the mean time, can you post output of:
```
lsattr /usr/share/doc/libqt4-script
```

really appreciate your patience to bear with me!
I tried the above command and found it's immutable
the output was
```
lsattr libqt4-script
--S--aiA---X------- libqt4-script

```
then I issued 
```
$:  chattr -i libqt4-script
$: lsattr libqt4-script
--S--a-A---X------- libqt4-script


```
but i still cant remove it via rm
after i done these
```

/usr/share/doc# sudo rm -rf libqt4-script
rm: cannot remove `libqt4-script': Operation not permitted

```
man how come XD
thx again

---

### Post by Yellow Pasque on 2009-02-26
> A file with the 'a' attribute set can only be open in append mode for writing. Only the superuser or a process possessing the CAP_LINUX_IMMUTABLE capability can set or clear this attribute. 

```
sudo chattr -a libqt4-script
```

---

### Post by earthtux on 2009-02-27
> **Temüjin said:**
> ```
sudo chattr -a libqt4-script
```

thx god this "a" and "i" did the trick now i can remove it
thx so much Temüjin, cant say how much I appreciate you here!!!!

btw how do I check if my hard disk has bad block?
the e2fsck didnt show me if I have bad block or not after it finish!

cause I googled around some said this kind of file corruption is caused by hard disk bad block

man why linux has this hidden a and i attributes?
guess I need to dig out more about linux filesystem.
thx again!!!

---

