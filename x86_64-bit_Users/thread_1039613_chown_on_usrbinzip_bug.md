---
title: "chown on /usr/bin/zip* bug"
date: 2009-01-14
forum: x86 64-bit Users
---

### Post by ghtspoon on 2009-01-14
hallo ubuntu64 user

i have install the 2.6.24-22-server version of ubuntu

in a script i use the command:

root@local:~# chmod -vf 700 /usr/bin/zip*
mode of `/usr/bin/zip' retained as 0700 (rwx------)
mode of `/usr/bin/zipcloak' retained as 0700 (rwx------)
mode of `/usr/bin/zipgrep' retained as 0700 (rwx------)
mode of `/usr/bin/zipinfo' changed to 0700 (rwx------)
mode of `/usr/bin/zipnote' retained as 0700 (rwx------)
mode of `/usr/bin/zipsplit' retained as 0700 (rwx------)

the problem ist this command chown /usr/bin/unzip also to chmod 0700

```
root@local:~# dir /usr/bin/unzip
-rwxr-xr-x 2 root root 125K 2008-03-21 11:41 /usr/bin/unzip
root@local:~# chmod -vf 700 /usr/bin/zip*
mode of `/usr/bin/zip' retained as 0700 (rwx------)
mode of `/usr/bin/zipcloak' retained as 0700 (rwx------)
mode of `/usr/bin/zipgrep' retained as 0700 (rwx------)
mode of `/usr/bin/zipinfo' changed to 0700 (rwx------)
mode of `/usr/bin/zipnote' retained as 0700 (rwx------)
mode of `/usr/bin/zipsplit' retained as 0700 (rwx------)
root@local:~# dir /usr/bin/unzip
-rwx------ 2 root root 125K 2008-03-21 11:41 /usr/bin/unzip
```

system is a
AMD X2  5600+ with 2GB RAM on a MSI Board

can anyone please check this on your system?
the problem is only the command chown.

its a bug or a feature?!? :D 

sorry, i cant test this at 32bit. at this time.

```
root@local:~# cp -pR /usr/bin/zip* /root/temp/
root@local:~# dir /root/temp/
total 324K
drwx------ 2 root root 4,0K 2009-01-14 23:09 .
drwx------ 8 root root 4,0K 2009-01-14 22:30 ..
-rwx------ 1 root root  74K 2006-07-10 15:07 zip
-rwx------ 1 root root  33K 2006-07-10 15:07 zipcloak
-rwx------ 1 root root 1,2K 2008-03-21 11:41 zipgrep
-rwx------ 1 root root 125K 2008-03-21 11:41 zipinfo
-rwx------ 1 root root  29K 2006-07-10 15:07 zipnote
-rwx------ 1 root root  29K 2006-07-10 15:07 zipsplit
```

---

### Post by albinootje on 2009-01-14
> **ghtspoon said:**
> 
root@local:~# chmod -vf 700 /usr/bin/zip*
mode of `/usr/bin/zip' retained as 0700 (rwx------)
mode of `/usr/bin/zipcloak' retained as 0700 (rwx------)
mode of `/usr/bin/zipgrep' retained as 0700 (rwx------)
mode of `/usr/bin/zipinfo' changed to 0700 (rwx------)
mode of `/usr/bin/zipnote' retained as 0700 (rwx------)
mode of `/usr/bin/zipsplit' retained as 0700 (rwx------)

the problem ist this commend chown /usr/bin/unzip also to chmod 0700


I just tried on a 32 bit 8.04.1 installation.
I've first copied /usr/bin/zip* and /usr/bin/unzip to /tmp/test and ran the same command on those files, which worked it should.
After that I repeated what you did, and /usr/bin/unzip stayed the same as it was before.
```

# chmod -vf 700 /usr/bin/zip*
mode of `/usr/bin/zip' changed to 0700 (rwx------)
mode of `/usr/bin/zipcloak' changed to 0700 (rwx------)
mode of `/usr/bin/zipgrep' changed to 0700 (rwx------)
mode of `/usr/bin/zipinfo' changed to 0700 (rwx------)
mode of `/usr/bin/zipnote' changed to 0700 (rwx------)
mode of `/usr/bin/zipsplit' changed to 0700 (rwx------)
# ls -la /usr/bin/unzip
-rwxr-xr-x 1 root root 121680 2008-03-21 11:29 /usr/bin/unzip

```

---

### Post by lensman3 on 2009-01-14
Could be that zip and unzip are the same executable.  The program determines which execution path to due depending on how it is called.  On my Fedora Core 10-64, they are separate files.  Might try "ls -lai /usr/bin/unzip /usr/bin/zip*" and see if the inodes are the same.

---

### Post by ghtspoon on 2009-01-15
thanks for the first replys and the test on 32 bit.

i have search for symlinks on unzip yesterday with

```
find / -lname /usr/bin/unzip
```

but i found no symlink :/

at the first look unzip is a standalone binary/programm.

i will look again for symlinks, aliases etc and will try the "ls.." command.

... 
"why do you chown zip and let the user the option to unzip?"
its a server where you can use exec(); in php.

hope for more tips or any ideas, the problem ist not fixed yet.

its not a bad problem. because i can make a chown -vf 755 /usr/bin/unzip after chown zip*, but its not realy a good solution.

---

### Post by dcstar on 2009-01-15
> **ghtspoon said:**
> 
......
root@local:~# chmod -vf 700 /usr/bin/zip*
mode of `/usr/bin/zip' retained as 0700 (rwx------)
mode of `/usr/bin/zipcloak' retained as 0700 (rwx------)
mode of `/usr/bin/zipgrep' retained as 0700 (rwx------)
mode of `/usr/bin/zipinfo' changed to 0700 (rwx------)
mode of `/usr/bin/zipnote' retained as 0700 (rwx------)
mode of `/usr/bin/zipsplit' retained as 0700 (rwx------)

the problem ist this command chown /usr/bin/unzip also to chmod 0700

```

.......
root@local:~# dir /usr/bin/unzip
-rwx------** 2** root root 125K 2008-03-21 11:41 /usr/bin/unzip
```
.......

The "2" shows you that this file has a hard link (somewhere), that hardlink entry is probably what was changed.

BTW, your "zipinfo" is showing the same size as "unzip", that is a big coincidence if they are different binary files and the "zipinfo" man page says it is the same as "unzip" and is just a link to it.

---

### Post by lensman3 on 2009-01-15
It could be a hard link instead of a symlink.  Check the hard link field number with "ls -la".  It is the field right after the rwxrwxrwx field.  Most of the time it is a one.  If it is 2 or greater then the file is linked with something else.

Try this "ln -lai | sort | more".  This will sort on the inodes and look for files that have hard links.  The inodes will all be the same.

---

### Post by ghtspoon on 2009-01-18
thanks to all for the tips and your help. 

zipinfo is a hardlink to unzip. if i change the chmod of zipinfo to 700, the unzip chmod will be also change. after that, i have changed the chmod on unzip to 755 and the chmod of zipinfo was 700.

-> zipinfo is the hardlink to unzip -*** (ubuntu64) 

the best on this problem is:

zipinfo --help and unzip --help is diffrent :/

in suse [ i know its a bad word ;) ] is unzip and zipinfo standalone programms. so i was a little bit confused about that.

```
ls -lai > remember_ubuntu64.txt
```

---

### Post by lensman3 on 2009-01-18
Break them into two programs on your machine.

Delete one of them.  That will remove just the hard link.  Then copy the other one and rename. So if you do:

rm unzip          (This will decrease the hard link count by one for zip).
cp zip unzip

All done! The program will work correctly for both names.  It will just take twice as much space.

---

### Post by albinootje on 2009-01-18
> **lensman3 said:**
>  All done! The program will work correctly for both names.  It will just take twice as much space.

Interesting, but what will happen when dpkg/apt-get wants to upgrade to a newer version of zip/unzip ? What will it do ?

---

### Post by dcstar on 2009-01-20
> **albinootje said:**
> Interesting, but what will happen when dpkg/apt-get wants to upgrade to a newer version of zip/unzip ? What will it do ?

Possibly remove the chown changes made by the OP and set them all back to default........

You should really never change system files or packaged apps as there is always the risk an upgrade will revert everything back to the original settings - probably better to make softlinks (located in a early path) and let them point to whatever original files you need.

---

