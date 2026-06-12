---
title: "two versions of wine installed and i can't remove either"
date: 2012-10-22
forum: Wine
---

### Post by bilmas on 2012-10-22
hey all! hit a bit of a roadblock and i thought maybe this was the best place to find an answer
it seems that i have installed Wine1.3 and 1.4.  I can no longer add or remove packages nor can the upgrade to 12.10 happen until this is resolved. i used -f to try to solve the problem as well as autoremove.  here is the output:

> david@david:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  ttf-umefont fonts-horai-umefont libcapi20-3 unixodbc wine-gecko1.4
  winetricks webaccounts-extension-common libmpg123-0 libodbc1 ttf-droid
  libtiff5 libjbig0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libjbig0 libtiff5
The following packages will be REMOVED:
  limbo wine wine1.3 wine1.4 wine1.4-amd64 wine1.4-common
The following NEW packages will be installed:
  libjbig0 libtiff5
0 upgraded, 2 newly installed, 6 to remove and 1977 not upgraded.
15 not fully installed or removed.
Need to get 0 B/196 kB of archives.
After this operation, 114 MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error: parsing file '/var/lib/dpkg/status' near line 31989 package 'librtmp0:i386':
 blank line in value of field 'Original-Maintainer'
E: Sub-process /usr/bin/dpkg returned an error code (2)


Does anybody have any ideas how to fix this?

thanks so much!

---

### Post by Tweak42 on 2012-10-23
A google serch for the error nets: [http://askubuntu.com/questions/109994/dpkg-error-parsing-file-var-lib-dpkg-status-near-line-6449](http://askubuntu.com/questions/109994/dpkg-error-parsing-file-var-lib-dpkg-status-near-line-6449)

That may point you in the right direction.  I vaguely had a simular problem like that before and the solution was something like deleting or resetting an dpkg file.  You may try installing synaptic to see if it can figure it out.

---

### Post by bilmas on 2012-10-24
thanks for the tip.  i tried followed the advice on that page but still had no luck.  synaptic still can't resolve the broken packages

---

### Post by ivotkl on 2012-11-29
OK, so it seems as if I had removed completely wine, but it still appears on the "open with" and I have tried installing BIN files and it worked. As far as I'm concerned they are no longer supported on Ubuntu according to something I read somewhere.

Thanks in advanced. How do I completely removed it?

Already tried:
```
$ wine
The program 'wine' is currently not installed.  You can install it by typing:
sudo apt-get install wine1.2
```

```
sudo apt-get update
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
```

Autoclean returned:
```
Del winetricks 0.0+20120308~ppa1 [147kB]
Del wine 1.2.3-0ubuntu1~ppa2~lucid1 [42.0kB]
Del ttf-symbol-replacement-wine1.3 1.4-0ubuntu1~ppa1~lucid1 [61.0kB]
Del wine1.3-gecko 1.4.0+1 [49.6MB]
Del wine1.3 1.4-0ubuntu1~ppa1~lucid1 [12.1MB]
```

***EDIT:*** I' ve tried opening a text file with wine's wordpad, it tried to, but did not. (Opening [txtfilename]...) on lower taskbar.

Also tried below commands with no relevant results:
```
sudo apt-get install --fix-missing
sudo dpkg --clear-avail
```

---

### Post by Tweak42 on 2012-11-30
Just because a program shows up under "Open with" doesn't mean the program is actually installed.  I'm pretty sure that is a Nautilus file association setting but I can't find where that is configured at the moment.

I'm not sure what you mean by BIN files having anything to do with wine.  From my experience they are either cd images (simular to iso) or a typical a linux program installation package you run at the command line.

---

### Post by ivotkl on 2012-11-30
Thanks for the help. =)
I' ll just install it and search Nautilus dissociation later. If any problems arise, you shall here from me.

---

### Post by Sigshane on 2012-12-04
Hmm, did you try including the --purge flag with the remove command? That might have positive results.

Also, you might try removing multiple files at once, i.e. 

```
sudo apt-get --purge wine wine1.4 winetricks
```

This helped me overcome the circular dependency problems mentioned numerous times on this forum.

Shane

---

