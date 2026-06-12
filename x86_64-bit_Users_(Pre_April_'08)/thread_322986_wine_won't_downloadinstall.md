---
title: "wine won't download/install"
date: 2006-12-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by atarileaf on 2006-12-21
Ok, I've tried downloading and installing wine via the instructions on this wiki link:

[https://help.ubuntu.com/community/WineForAMD64](https://help.ubuntu.com/community/WineForAMD64)

I follow the instructions but I get stonewalled with an error that it couldn't find the wine installation. I copy and pasted the terminal so you could see what I'm getting. I'm a newb and have no idea what all this gobbledy gook is so if someone could break it down into the english language and let me know where I'm going wrong, it would be appreciated.

Thanks


michea@michea-desktop:~$ cd ~/Desktop/wine
michea@michea-desktop:~/Desktop/wine$ ./wine
Password:
Reading package lists... Done
Building dependency tree... Done
dpkg-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
--11:33:16--  [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.25~winehq0~ubuntu~6.06-1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.25~winehq0~ubuntu~6.06-1_i386.deb)
           => `wine_0.9.25~winehq0~ubuntu~6.06-1_i386.deb'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
11:33:17 ERROR 404: Not Found.

dpkg: error processing wine_0.9.25~winehq0~ubuntu~6.06-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 wine_0.9.25~winehq0~ubuntu~6.06-1_i386.deb
--11:33:17--  [http://ubuntu.mirrors.tds.net/ubuntu/pool/main/libx/libxxf86dga/libxxf86dga1_1.0.0-0ubuntu3_i386.deb](http://ubuntu.mirrors.tds.net/ubuntu/pool/main/libx/libxxf86dga/libxxf86dga1_1.0.0-0ubuntu3_i386.deb)
           => `libxxf86dga1_1.0.0-0ubuntu3_i386.deb'
Resolving ubuntu.mirrors.tds.net... 216.165.129.138
Connecting to ubuntu.mirrors.tds.net|216.165.129.138|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10,062 (9.8K) [text/plain]

100%[====================================>] 10,062        64.65K/s

11:33:18 (64.48 KB/s) - `libxxf86dga1_1.0.0-0ubuntu3_i386.deb' saved [10062/10062]


ERROR: Could not find wine installation.
       Setup wine first.
Setup aborted.

---

### Post by Azakus on 2006-12-21
It was an old link. Here's the good link
[http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.27~winehq0~ubuntu~6.10-1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.27~winehq0~ubuntu~6.10-1_i386.deb)

---

### Post by ubdai on 2006-12-24
This link seems dead?

ubdai:confused:

---

### Post by b0le on 2006-12-24
Try looking at this: [http://ubuntuforums.org/showthread.php?t=297280](http://ubuntuforums.org/showthread.php?t=297280)

---

