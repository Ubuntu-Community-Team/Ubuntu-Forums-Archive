---
title: "Troubles with nxserver on 64bit Kubuntu"
date: 2007-02-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by CaptSaltyJack on 2007-02-17
I've tried desperately to get the NX stuff working on Kubuntu Edgy.  I managed to install the right .deb packages, but nothing in /usr/NX/bin will run.  It acts like the files don't exist, but they do.. my best guess is that these are strictly 32-bit binaries that won't run on my 64-bit OS.

```
~$ /usr/NX/bin/nxserver --status
-bash: /usr/NX/bin/nxserver: No such file or directory
~$ ls -l /usr/NX/bin/nxserver
-rwxr-xr-x 1 root root 18611844 2007-01-29 11:54 /usr/NX/bin/nxserver

```

Really weird, eh?

---

### Post by wesley_of_course on 2007-02-18
Wesley here ;

where'd  the "n,N ' s "  come from ?

---

### Post by CaptSaltyJack on 2007-02-18
This isn't X server i'm talking about.. this is something different.  NX.  It's a way to remotely connect to a computer, like Remote Desktop for Windows.

[http://www.nomachine.com/](http://www.nomachine.com/)

---

### Post by jackocleebrown on 2007-05-30
Hi CaptSaltyJack,

I've got the same problem! I don't think that this is just 32/64bit incompatibility - I've had NXclient and server working on 64bit Ubuntu before but I can't remember the trick.

I'll let you know if I get a solution.

Jack.

---

### Post by CaptSaltyJack on 2007-05-30
I already got NX working.  It works great on 32-bit.  64-bit...not so much. :)  I ditched the 64-bit platform.

---

### Post by jackocleebrown on 2007-05-30
Hi,

Got it working by doing this:

1) get some dependencies. (this bit gets rid of your error)
"sudo apt-get install openssh-server ia32-libs"

2) NX requires libstdc++2.10-glibc2.2 which is not available in a 64bit package. However as it is only used by NX it is pretty safe to use a 32bit one. Get the 32bit deb package from here:

[http://packages.ubuntu.com/feisty/libs/libstdc++2.10-glibc2.2](http://packages.ubuntu.com/feisty/libs/libstdc++2.10-glibc2.2)

click on the 386 link, download the package and force install with something like

"sudo dpkg -i --force-architecture libstdc++2.10-glibc2.2_2.95.4-24_i386.deb"

3) Install NXclient. Download deb package from here:

[http://www.nomachine.com/download-client-linux.php](http://www.nomachine.com/download-client-linux.php)

make sure that you get the one labelled "NX Client for Linux not requiring the XFT libraries".
force install like this:

"sudo dpkg -i --force-architecture nxclient_2.1.0-17_i386.deb "

4) Do the same for the other NX packages that you need.


Hope this fixes your problem.

Jack.

---

### Post by jackocleebrown on 2007-05-30
arg didn't see your response! Might be useful for someone anyway. (and probably me next time I do it!)

---

### Post by Didjit on 2007-05-31
Curious, anyone get sound to work on the remote machine? I use GNOME, so I was able to get the gnome event sounds, but not other media sounds (flash, movies, MP3), they still play on the target machine.

Didjit

---

### Post by jackocleebrown on 2007-05-31
Sorry not tested the multimedia support at-all... sounds a bit strange - perhaps it depends which audio sink the different bits of software are using, esd, alsa, oss etc?

---

### Post by jwbrown on 2007-06-03
Thanks Jack,
I previously had nxserver working on kubuntu daper amd64, with your tip to add the "ia32-libs", I now have it working on kubuntu feisty amd64. I am curious, how did you know to include the ia32-libs?

Jack #2

PS
Does anyone know if the 30 day trial period is something new and now applies to Linux installations?

---

### Post by jackocleebrown on 2007-06-04
Hi jwbrown,

Glad it was useful!
I managed to find this doc on nomachine web site outlining installation in debian amd64 which mentioned the package.

[http://www.nomachine.com/ar/view.php?ar_id=AR05E00459](http://www.nomachine.com/ar/view.php?ar_id=AR05E00459)

Perhaps I was just more determined because I knew it could be done (I was rebuilding a machine).

There is a "free forever" version of the sever which has unlimited license but the limitation is that you can only make two client connections simultaneously. Check you got the right deb for "nxserver free edition" from nomachine.

Jack.

---

### Post by yurtboy on 2007-11-03
This worked great for me on a 32bit

---

