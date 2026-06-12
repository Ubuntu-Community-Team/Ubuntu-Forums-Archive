---
title: "ati catalyst 8.5 --buildpkg error"
date: 2008-05-26
forum: x86 64-bit Users
---

### Post by bebox on 2008-05-26
why is buildpkg not working...can anybody help me???


dpkg-shlibdeps: warning: symbol XauFileName used by debian/xorg-driver-fglrx/usr/sbin/atieventsd found in none of the libraries.
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd shouldn't be linked with libXrender.so.1 (it uses none of its symbols).
dpkg-shlibdeps: failure: couldn't find library libfglrx_gamma.so.1 needed by debian/xorg-driver-fglrx/usr/bin/fglrx_xgamma (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: *** [binary] Error 1
dpkg-buildpackage: failure: debian/rules binary gave error exit status 2

---

### Post by Jouke74 on 2008-05-26
I guess you need to install the development packages of a few programs X for example & probably also some libraries. Did you install all required dependencies beforehand?

^
EDIT: Above probably not required.

---

### Post by bebox on 2008-05-26
> **Jouke74 said:**
> I guess you need to install the development packages of a few programs X for example & probably also some libraries. Did you install all required dependencies beforehand?

yes...i followed this..[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) manual installation...i when i come to the part where i have to make deb's it fails...what did you say i should install?

---

### Post by Jouke74 on 2008-05-26
Switch to the directory you downloaded this into and the run the following. (Make sure universe and multiverse are enabled in your repository sources).

sudo apt-get update
sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r)

This installs the dependencies for the installer.

If you are using the x86_64 architecture (64 bit), be sure to inst **"ia32-libs" before proceeding!** Also, if you have a problem getting the libGL.so.1, create a symbolic link to it:

[B]sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1
[/B]

Here it goes wrong probably.

See also  "Additional 64-bit instructions" a bit further down. You probably need to force install it.

---

### Post by peakshysteria on 2008-05-26
Solutions here:

[http://ubuntuforums.org/showthread.php?t=789641&page=2](http://ubuntuforums.org/showthread.php?t=789641&page=2)

and here:

[http://ubuntuforums.org/showthread.php?t=785107&page=2](http://ubuntuforums.org/showthread.php?t=785107&page=2)

Read carefully. I had the same issue. The solution is explained on the last pages of both links. But read the whole posts anyway and you'll get there :)

Myself, I've given ATI a rest for now (once again)....waiting for better times or expert help on phd. level.....

---

### Post by bebox on 2008-05-27
> **peakshysteria said:**
> Solutions here:

[http://ubuntuforums.org/showthread.php?t=789641&page=2](http://ubuntuforums.org/showthread.php?t=789641&page=2)

and here:

[http://ubuntuforums.org/showthread.php?t=785107&page=2](http://ubuntuforums.org/showthread.php?t=785107&page=2)

Read carefully. I had the same issue. The solution is explained on the last pages of both links. But read the whole posts anyway and you'll get there :)

Myself, I've given ATI a rest for now (once again)....waiting for better times or expert help on phd. level.....

thank's peakshysteria !!! it's working :)

---

### Post by peakshysteria on 2008-05-27
Goodgood man. Nice to see that some of us can make ATI run :) I wish there would be a simpler way. ENVYNG doesn't work at all in my end either. Not but a manual install seems to work. But there is way to much terminal for me. I've tried many times and almost made it. But there seems to be some small thing I always do wrong....and it f***s up everything. Not to keen on getting there once again...... :lolflag: Last time it took me all night to get my resolution back.

---

### Post by Jouke74 on 2008-05-27
Ah again more issues than the standard. Sorry for the above posts. I stayed with the Ubuntu 8.4's... They work, sort of, and I will await the UBuntu repro update.

Thanks for the info peakshysteria.

---

