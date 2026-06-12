---
title: "Ansys 11 Installation on AMD64 Gutsy"
date: 2007-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by eloydark on 2007-11-22
Hi everyone, I am having a problem installing Ansys 11 on my Linux PC. I have ubuntu 7.10 64bit on an AMD 64 configuration. When I do the install I get the following message:
```
~/Ansys$ sudo ./INSTALL
copying necessary files to /tmp/ans_install_tmp12319/
 Executing /tmp/ans_install_tmp12319/common/../tcl/linop64/wish
Error in startup script: invalid command name ""
    while executing
"$globalVars(manifest) documentElement"
    (procedure "SortManifestByPlatform" line 4)
    invoked from within
"SortManifestByPlatform"
    (procedure "CreateDOMManifest" line 9)
    invoked from within
"CreateDOMManifest"
    (file "/tmp/ans_install_tmp12319/common/InstallMain.tcl" line 1744)

```
I believe this happens because a required program is missing but I can't understand which one.
Can anyone help me?
Thx in advance!

---

### Post by Kilz on 2007-11-22
> **eloydark said:**
> Hi everyone, I am having a problem installing Ansys 11 on my Linux PC. I have ubuntu 7.10 64bit on an AMD 64 configuration. When I do the install I get the following message:
```
~/Ansys$ sudo ./INSTALL
copying necessary files to /tmp/ans_install_tmp12319/
 Executing /tmp/ans_install_tmp12319/common/../tcl/linop64/wish
Error in startup script: invalid command name ""
    while executing
"$globalVars(manifest) documentElement"
    (procedure "SortManifestByPlatform" line 4)
    invoked from within
"SortManifestByPlatform"
    (procedure "CreateDOMManifest" line 9)
    invoked from within
"CreateDOMManifest"
    (file "/tmp/ans_install_tmp12319/common/InstallMain.tcl" line 1744)

```
I believe this happens because a required program is missing but I can't understand which one.
Can anyone help me?
Thx in advance!

Ansys 11 is a commercial product. You might want to contact them for support seeing as you bought the application from them. Seeing how there are a whopping 7 posts (of which this topic is one) on the forums you may not get many responses here.

---

### Post by eloydark on 2007-11-22
> **Kilz said:**
> Ansys 11 is a commercial product. You might want to contact them for support seeing as you bought the application from them. Seeing how there are a whopping 7 posts (of which this topic is one) on the forums you may not get many responses here.

Unfortunately I am a student and I use Ansys Educational with the University Licence Server. I do not own the program so it would be somewhat weird contacting them for support. I have no problem using it under windows with the same Licence Server. The problem itself exists only because I cannot complete the installation. If someone could help, I would greatly appreciate.

---

### Post by Kilz on 2007-11-22
> **eloydark said:**
> Unfortunately I am a student and I use Ansys Educational with the University Licence Server. I do not own the program so it would be somewhat weird contacting them for support. I have no problem using it under windows with the same Licence Server. The problem itself exists only because I cannot complete the installation. If someone could help, I would greatly appreciate.

If you got it through the University, you may want to contact them as to where to get support.

---

### Post by eloydark on 2007-11-23
> **Kilz said:**
> If you got it through the University, you may want to contact them as to where to get support.

I 'll give it a shot on Monday, though they never used the Linux version. I believe they will let me take the Linux installation manual with me to see for myself the actual process.
Thx for your time mate :)

---

