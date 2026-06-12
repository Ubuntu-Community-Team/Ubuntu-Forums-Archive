---
title: "Why do this happen when i try to install xmms through &quot;add/remove aplications?&quot;"
date: 2006-09-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by emiln on 2006-09-12
```
Selecting previously deselected package libgtk1.2-common.
(Reading database ... 72065 files and directories currently installed.)
Unpacking libgtk1.2-common (from .../libgtk1.2-common_1.2.10-18_all.deb) ...
Selecting previously deselected package libglib1.2.
Unpacking libglib1.2 (from .../libglib1.2_1.2.10-10.1build1_amd64.deb) ...
Selecting previously deselected package libgtk1.2.
Unpacking libgtk1.2 (from .../libgtk1.2_1.2.10-18_amd64.deb) ...
Selecting previously deselected package xmms.
Unpacking xmms (from .../xmms_1.2.10+cvs20050809-4ubuntu5_amd64.deb) ...
Setting up sun-java5-doc (1.5.0-06-1) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/j2se/1.5.0/download.html

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

```

I assume it has something to do with something that happened when i tried to install Java, but why does it interrupt the installation of xmms? and also, how do i fix it? :)

---

### Post by Kilz on 2006-09-12
> **emiln said:**
> ```
Selecting previously deselected package libgtk1.2-common.
(Reading database ... 72065 files and directories currently installed.)
Unpacking libgtk1.2-common (from .../libgtk1.2-common_1.2.10-18_all.deb) ...
Selecting previously deselected package libglib1.2.
Unpacking libglib1.2 (from .../libglib1.2_1.2.10-10.1build1_amd64.deb) ...
Selecting previously deselected package libgtk1.2.
Unpacking libgtk1.2 (from .../libgtk1.2_1.2.10-18_amd64.deb) ...
Selecting previously deselected package xmms.
Unpacking xmms (from .../xmms_1.2.10+cvs20050809-4ubuntu5_amd64.deb) ...
Setting up sun-java5-doc (1.5.0-06-1) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/j2se/1.5.0/download.html

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

```

I assume it has something to do with something that happened when i tried to install Java, but why does it interrupt the installation of xmms? and also, how do i fix it? :)

Because the java install never completed. So each time you run apt it will try and complete it.
```
sudo apt-get -f install
``` 
May solve the problem.

---

### Post by emiln on 2006-09-12
ok thanx,
that didn't actually solve it, it just gave the same response again. But i read more carefully and did what it asked me for and it worked. :D thanks again.

---

