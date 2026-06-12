---
title: "-ksh: wine: not found [No such file or directory]  :confused:"
date: 2011-12-01
forum: Wine
---

### Post by mathgirl on 2011-12-01
This is seriously mysterious, wine exists in /usr/bin, but is uncallable:
```

macubuntu$ which wine
/usr/bin/wine
macubuntu$ file $(which wine)
/usr/bin/wine: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped
macubuntu$ file iclicker.exe 
iclicker.exe: PE32 executable for MS Windows (GUI) Intel 80386 32-bit
macubuntu$ /usr/bin/wine iclicker.exe 
-ksh: /usr/bin/wine: not found [No such file or directory]
macubuntu$ 

```
:confused:

I'm in 64-bit oneiric.

---

### Post by mathgirl on 2012-01-17
Any ideas?

---

### Post by oldrocker99 on 2012-01-17
Wine is in a hidden directory called .wine. Enable "Show hidden files" and it'll become visible.

---

### Post by mathgirl on 2012-01-17
> Wine is in a hidden directory called .wine. Enable "Show hidden files" and it'll become visible.

What?  This is all happening in a terminal.  There's no enabling "Show hidden files".  Are you saying there's a copy of the wine executable in $HOME/.wine ?

:confused::confused:

---

### Post by dino99 on 2012-01-18
nautilus setting: show hidden folder/file
terminal: ctrl+h

sometimes .wine is borked, so rename it and make a clean wine install again

---

### Post by mathgirl on 2012-01-18
Okay, I see what you mean.  After moving .wine and reinstalling, I still get the problem, though

```

$ mv .wine was_dot_wine
$ sudo apt-get purge wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  wine1.3-gecko wine1.3 lib32nss-mdns winetricks ttf-droid
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  wine*
0 upgraded, 0 newly installed, 1 to remove and 188 not upgraded.
After this operation, 69.6 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 324379 files and directories currently installed.)
Removing wine ...
$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 188 not upgraded.
Need to get 0 B/3,592 B of archives.
After this operation, 69.6 kB of additional disk space will be used.
Selecting previously deselected package wine.
(Reading database ... 324377 files and directories currently installed.)
Unpacking wine (from .../wine_1.2.3-0ubuntu1_amd64.deb) ...
Setting up wine (1.2.3-0ubuntu1) ...
$ wine
-ksh: wine: not found [No such file or directory]
$ which wine
/usr/bin/wine
$ 

```

---

### Post by ergo-proxy on 2012-01-19
Hmm do you have wine ppa added?

---

### Post by drmrgd on 2012-01-19
This might be a dumb question, but I'll give it a shot.  By chance have you lost /usr/bin in your $PATH for ksh?  If you just type $PATH, can you see /usr/bin listed?  

It seems clear that you've installed wine, and it's installed to /usr/bin, but it still doesn't launch.  I know that before you reinstalled, it did look like you tried to execute it from /usr/bin, but maybe this was a compound problem and the combination of reinstalling plus checking your PATH variable will help.

---

### Post by mathgirl on 2012-01-19
I don't think I have the wine ppa
```

$ grep -i wine /etc/apt/sources.list 
$ grep -i wine /etc/apt/sources.list* 
$ 

```

I think my $PATH is okay
```

$ echo $PATH
/home/username/maple15/bin:/home/username/bin:/home/username/maple15/bin:/home/username/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
$ /usr/bin/wine
-/usr/bin/ksh: /usr/bin/wine: not found [No such file or directory]
$ file /usr/bin/wine
/usr/bin/wine: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped
$ 

```

Thanks for all the help so far!

---

### Post by drmrgd on 2012-01-19
OK, I think I found something interesting.  You're not running a 64-bit system by chance, are you?  I found this bug report for people running some 32-bit applications on amd64 architecture here:

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101]("https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101")

Seems it throws the error you're seeing.  Also seems like a quick fix / workaround if it's the case by reinstalling libc6-i386:

```
sudo apt-get install --reinstall libc6-i386
```

Try that and see if you get anywhere with it.

---

### Post by mathgirl on 2012-01-19
:):):)

drmrgd:  Thank you!  That actually worked!  I remember when the problem first came up thinking it was a 64-bit vs. 32-bit issue with wine.  But asking explicitly about that never brought up the bug you mentioned.  Thank you so much!  Wine now works!

---

### Post by drmrgd on 2012-01-19
Cool!  I'm glad that worked.  That one was driving me crazy.  What a great example of a meaningless (and misleading) error message :D

---

### Post by mungatsuma on 2012-01-23
Thanks a lot had the same problem and tried lots of stuff which did not work. Your solution worked like a charm. Now wine is up and about again after 4 fruitless days.

---

### Post by kubug on 2012-02-28
> **drmrgd said:**
> OK, I think I found something interesting.  You're not running a 64-bit system by chance, are you?  I found this bug report for people running some 32-bit applications on amd64 architecture here:

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101]("https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101")

Seems it throws the error you're seeing.  Also seems like a quick fix / workaround if it's the case by reinstalling libc6-i386:

```
sudo apt-get install --reinstall libc6-i386
```

Try that and see if you get anywhere with it.

That did it. Thanks so much. I had the same issue after I purged some PPA's to get GIMP 2.7 installed (installing those PPAs borked my desktop colors).

---

