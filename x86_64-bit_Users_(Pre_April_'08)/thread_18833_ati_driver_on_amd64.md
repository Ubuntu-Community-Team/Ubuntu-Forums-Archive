---
title: "ati driver on amd64"
date: 2005-03-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by caracho on 2005-03-09
Hi !

I have some problems installing new ati drivers on amd64.

I can't convert rpm to deb file, the error message says

```


dpkg-gencontrol: error: current build architecture amd64 does not appear in pack age's list (x86_64)


```

I don't get where is the problem ???

Thanks in advance 

Cara

---

### Post by Pse on 2005-03-09
Are you sure you downloaded ATI's drivers for x86_64? Beware, in their page there are 2 links: one for ATI's Linux driver, and the other for ATI's Linux x86_64 driver.
You should check that.
Simply doing a "alien [filename].rpm" should convert your driver to .deb.

---

### Post by caracho on 2005-03-09
The file name is fglrx64_4_3_0-8.10.19-1.x86_64.rpm, for XFree86...
I think it's the good driver.

---

### Post by Pse on 2005-03-09
This might be an off-topic question, but are you sure you're using XFree86? (You should be, unless you've installed Hoary).
Could it be an error in ATI's package for XFree86? I've succesfully converted the Xorg package. I'll download the XFree package and convert it myself, to see if it works.

---

### Post by Pse on 2005-03-09
OK, I've done it and it works, here's the output:

```
pse@A64LIN:~/Desktop$ sudo alien *.rpm
fglrx64-4-3-0_8.10.19-2_amd64.deb generated
pse@A64LIN:~/Desktop$
```

Either you have some configuration files messed a bit, or you're doing something wrong. Try downloading it again, maybe the package got corrupted somehow.

[EDIT] I have just noticed your package is older! Luck at the numbers there, the last digit before "amd64" is a "2". Yours is a "1". Just download the file from ATI again, perhaps you got the older package! =)

---

### Post by caracho on 2005-03-09
Thanks for your help !

When I download the driver I get the "1 version", do you download th driver from this page ? [https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

---

### Post by caracho on 2005-03-09
Here is the entire message from alien :

```

root@ubuntu:/home/alex/Desktop # ls
fglrx64_4_3_0-8.10.19-1.x86_64.rpm
root@ubuntu:/home/alex/Desktop # alien fglrx64_4_3_0-8.10.19-1.x86_64.rpm
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/fglrx64-4-3-0
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: format of libfglrx_gamma.1 not recognized
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path /usr/X11R6/lib32/li bXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path /usr/X11R6/lib32/lib X11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path /usr/lib32/libstd c++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path /usr/X11R6/lib32/lib X11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path /usr/X11R6/lib32/li bXext.so.6, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (x86_64)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Erreur 1
find: fglrx64_4_3_0-8.10.19: Aucun fichier ou répertoire de ce type
root@ubuntu:/home/alex/Desktop #



```

I tried xorg too and it does not work, perhaps a package is missing in my installation, and that wierd you got a different version of the driver. 

I'll let you know if I find a solution

---

### Post by Pse on 2005-03-09
OK, now, that's wierd! I clicked your link and now I can only download the "-1" driver O_O. The strange thing is that I was downloading it from the same location. I've kept my older .deb package for Xorg and it is the "-2" version, but I have erased the .rpm and .deb for XFree.
I'll have a look again tomorrow, I'm afraid it's too late now. If you manage to solve this, please post about it =).

---

