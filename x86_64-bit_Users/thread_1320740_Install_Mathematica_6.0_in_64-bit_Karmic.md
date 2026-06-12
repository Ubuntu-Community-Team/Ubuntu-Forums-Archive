---
title: "Install Mathematica 6.0 in 64-bit Karmic"
date: 2009-11-09
forum: x86 64-bit Users
---

### Post by maddojf on 2009-11-09
I took me all morning to figure this out so I thought I would share in case others have the same problem.  

When trying to install Mathematica 6.0 in 64-bit Ubuntu 9.10 Karmic Koala, the installer would fail.  I forget what the exact error message was, but it would occur before the installer reached the registration part.  Most of the file were written before the installer failed, so I tried running the program and got the following error:
```
/usr/local/Wolfram/Mathematica/6.0/SystemFiles/FrontEnd/Binaries/Linux-x86-64/Mathematica: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory  
```

The problem is that there is no libstdc++5 package in the karmic repos.

After searching the forums I found a number of threads about various 32-bit apps giving similar errors in 9.10.  The solution that was given was to install the 32-bit version of the library and do some sym-linking.  However, Mathematica is looking for the 64-bit version of the library so this didn't work.

The 64-bit version of the library can be downloaded from either:
[http://packages.ubuntu.com/jaunty/amd64/libstdc++5/download](http://packages.ubuntu.com/jaunty/amd64/libstdc++5/download)
or
[http://packages.debian.org/lenny/amd64/libstdc++5/download](http://packages.debian.org/lenny/amd64/libstdc++5/download)

After installing the 64-bit version of the package (libstdc++5_3.3.6-17ubuntu1_amd64.deb or libstdc++5_3.3.6-18_amd64.deb) I reran the installer and everything worked.

---

### Post by calimenio on 2009-11-16
hi I have Mathematica 6.0 and my laptop has ubuntu 9.10, I tried to do the same like you but the problem is that it is not possible to install libstdc++5 for 64 bit, always when I tried to install this package, it  appears in my package installer shell this message in status:  Status Error: Wrong architecture 'amd64' do you know what is the problem? If you can help me I would appreciate  thanks in advance

---

### Post by maddojf on 2009-11-17
Sorry, I entered the link from memory incorrectly.  I left out the /amd64/ portion of the address.  Anyway, I have updated the original post so try that link.

---

