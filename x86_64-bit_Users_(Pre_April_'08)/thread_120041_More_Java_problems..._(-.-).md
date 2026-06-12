---
title: "More Java problems... (-.-)"
date: 2006-01-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Fork on 2006-01-20
Ok, so I was reading the java insturctions [https://wiki.ubuntu.com/JavaPPC]("here") and I got to the part where i had to "Now convert the TGZ and install the resulting DEB:" but when i typed in the stuff i got this:

```
dave@Dave:~$ make-jpkg /home/dave/Desktop/ibm-java2-ppc-50.tgz
Creating temporary directory: /tmp/make-jpkg.XXXXFBRkZ5
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)

No matching plugin was found.
Removing temporary directory: done
dave@Dave:~$
```

What am I doing wrong? :confused:

---

### Post by felix_stegerman on 2006-01-20
The java-package in breezy doesn't support IBM Java 1.5.0 (5.0) yet.

You could either get a newer version from Debian unstable,
or patch the current one with the instructions I posted here:
[http://ubuntuforums.org/showthread.php?t=78804](http://ubuntuforums.org/showthread.php?t=78804)


Felix

edit: java-package from Debian unstable can be found here: [ftp://ftp.nl.debian.org/debian/pool/contrib/j/java-package/java-package_0.27_all.deb](ftp://ftp.nl.debian.org/debian/pool/contrib/j/java-package/java-package_0.27_all.deb)

---

