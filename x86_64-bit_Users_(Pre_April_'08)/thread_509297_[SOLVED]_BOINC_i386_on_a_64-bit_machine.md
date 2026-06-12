---
title: "[SOLVED] BOINC i386 on a 64-bit machine"
date: 2007-07-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tonohono on 2007-07-25
Howdy folks,

Due to the vast majority of BOINC projects disregarding 64-bit users, I'm curious to know how I could install the 32-bit BOINC client on my 64-bit machine. 
I've already attempted to install the 32 bit package via --force-architecture. The client seems to run find, but I ran into some issues with the manager (wrong ELF class: ELFCLASS64).

Any help would be appreciated, whether it be instructions on installing the official 32-bit packages, link to a community provided 32-bit package for 64-bit machines, etc.

---

### Post by John.Michael.Kane on 2007-07-25
You have two options.

1) Try installing the ia32-libs and all it's dependencies.

2) Use the 64bit version from [getdeb]("http://www.getdeb.net/release.php?id=906")

---

### Post by Tonohono on 2007-07-25
Alrighty.

I have ia32-libs and all dependencies installed, though I don't believe 32-bit BOINC is utilizing the libraries.

I can install boinc-client and boinc-manager using --force-architecture, though when I attempt to the run the manager, I receive the error:
```
boincmgr: error while loading shared libraries: libwx_gtk2u_xrc-2.6.so.0: cannot open shared object file: No such file or directory
```

libwx_gtk2u_xrc-2.6.so.0 resides in /usr/lib, so I copied it to /lib32, and now receive this error:
```
boincmgr: error while loading shared libraries: libwx_gtk2u_xrc-2.6.so.0: wrong ELF class: ELFCLASS64
```

The "64" in "ELFCLASS64" leads me to believe BOINC is not utilizing the ia32-libs.

What steps must I take in order to verify whether or not BOINC is utilizing ia32-libs? Or have I simply hit a dead end?

---

### Post by John.Michael.Kane on 2007-07-25
> **Tonohono said:**
> Alrighty.

I have ia32-libs and all dependencies installed, though I don't believe 32-bit BOINC is utilizing the libraries.

I can install boinc-client and boinc-manager using --force-architecture, though when I attempt to the run the manager, I receive the error:
```
boincmgr: error while loading shared libraries: libwx_gtk2u_xrc-2.6.so.0: cannot open shared object file: No such file or directory
```

libwx_gtk2u_xrc-2.6.so.0 resides in /usr/lib, so I copied it to /lib32, and now receive this error:
```
boincmgr: error while loading shared libraries: libwx_gtk2u_xrc-2.6.so.0: wrong ELF class: ELFCLASS64
```

That error looks like a references to libraries that conflict.

At this stage your best off undoing what you did eg: the coping of the file to /lib32, and trying to install using the 64bit version from the link above.

---

### Post by Cappy on 2007-07-25
It means you copied a 64-bit library where there should have been a 32-bit library. You can use getlibs for a 32-bit library: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
but I too would recommend the 64-bit version since that is what I use.

---

### Post by Tonohono on 2007-07-25
Getlibs seems to have put me on the right track, thanks.
However, I've run into another problem... getlibs keeps wanting to install libcurl.so.3 libkrb5support.so.0
No matter how many times the libraries are installed, it keeps listing the same libraries as new dependencies.
```

getlibs /usr/bin/boincmgr
Matched library libcurl.so.3 to /feisty/libs/libcurl3
Matched library libgssapi_krb5.so.2 to /feisty/libs/libkrb53
Matched library libk5crypto.so.3 to /feisty/libs/libkrb53
Matched library libkrb5.so.3 to /feisty/libs/libkrb53
Matched library libkrb5support.so.0 to /feisty/libs/libkrb53
The following i386 libraries will be installed:
/feisty/libs/libcurl3
/feisty/libs/libkrb53
Continue? (y/n) y
DownloadingInstalling libraries ...
New depedencies have been detected:
libcurl.so.3
Matched library libcurl.so.3 to /feisty/libs/libcurl3
The following i386 libraries will be installed:
/feisty/libs/libcurl3
Continue? (y/n) y
DownloadingInstalling libraries ...
New depedencies have been detected:
libcurl.so.3



libkrb5support.so.0
Matched library libcurl.so.3 to /feisty/libs/libcurl3
Matched library libkrb5support.so.0 to /feisty/libs/libkrb53
The following i386 libraries will be installed:
/feisty/libs/libcurl3
/feisty/libs/libkrb53
Continue? (y/n)

```
etc, etc.

I also attempted
```
getlibs -32 libcurl.so.3
```
but the aforementioned loop continues regardless.


And I'm staying away from installed 64-bit BOINC due to many projects lack of work for 64-bit platforms... Unless ye happen to know how to grab work intended for 32-bit users from the servers, resolving the "platform 'x86_64-pc-linux-gnu' not found" error.

---

### Post by Cappy on 2007-07-25
That's weird, the page for these two files to download don't follow any I've seen.

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fc%2Fcurl%2Flibcurl3_7.15.5-1ubuntu2.1_i386.deb&md5sum=c8847b248ea0a07c2880a39e8c273b24&arch=i386&type=security](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fc%2Fcurl%2Flibcurl3_7.15.5-1ubuntu2.1_i386.deb&md5sum=c8847b248ea0a07c2880a39e8c273b24&arch=i386&type=security)

It will need to be done manually
```

wget -q http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3_7.15.5-1ubuntu2.1_i386.deb
wget -q http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb53_1.4.4-5ubuntu3.1_i386.deb
dpkg -x libcurl3_7.15.5-1ubuntu2.1_i386.deb boinclibs
dpkg -x libkrb53_1.4.4-5ubuntu3.1_i386.deb boinclibs
cp -R boinclibs/usr/lib/* /usr/lib32/

```

---

### Post by Tonohono on 2007-07-25
Excellent~

Now have 32-bit BOINC running smoothly, and am able to obtain work from 32-bit only projects. Thanks much for the help~

---

