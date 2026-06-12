---
title: "Matlab installed, but libncurses.so.5 error prevents running"
date: 2008-02-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by thinkgeek on 2008-02-14
I am currently trying to get Matlab installed and working on 64-bit Ubuntu Hardy. I do realize that this is a development release. I have gotten Matlab installed in Fedora 7 64-bit in the past (which I still have on another partition). Anyway, I followed all of the steps that I followed in the past that I documented in the Fedora Forums here:

[http://forums.fedoraforum.org/showthread.php?t=162424&highlight=matlab](http://forums.fedoraforum.org/showthread.php?t=162424&highlight=matlab)

I did get a few errors before I could get the installation script to work, but I eventually installed the correct packages to get that to work. Sorry I can't be more descriptive about which packages I installed, but I installed so many that I can't actually remember what they where and whether they were even needed. After the installation, I pasted my license info into the license.dat file. Then when I went to run it I get the following error.

[PHP]thinkgeek@thinkgeek-desktop:~$ /opt/matlab74/bin/matlab -glnx86
/opt/matlab74/bin/glnx86/MATLAB: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory
[/PHP]  

I've looked all around and I can't seem to find the correct package. If anyone can shed some light on this I would be very grateful. Thank you very much in advance.

---

### Post by Kilz on 2008-02-14
> **thinkgeek said:**
> I am currently trying to get Matlab installed and working on 64-bit Ubuntu Hardy. I do realize that this is a development release. I have gotten Matlab installed in Fedora 7 64-bit in the past (which I still have on another partition). Anyway, I followed all of the steps that I followed in the past that I documented in the Fedora Forums here:

[http://forums.fedoraforum.org/showthread.php?t=162424&highlight=matlab](http://forums.fedoraforum.org/showthread.php?t=162424&highlight=matlab)

I did get a few errors before I could get the installation script to work, but I eventually installed the correct packages to get that to work. Sorry I can't be more descriptive about which packages I installed, but I installed so many that I can't actually remember what they where and whether they were even needed. After the installation, I pasted my license info into the license.dat file. Then when I went to run it I get the following error.

[PHP]thinkgeek@thinkgeek-desktop:~$ /opt/matlab74/bin/matlab -glnx86
/opt/matlab74/bin/glnx86/MATLAB: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory
[/PHP]  

I've looked all around and I can't seem to find the correct package. If anyone can shed some light on this I would be very grateful. Thank you very much in advance.

is matlab a 32bit application?

---

### Post by thinkgeek on 2008-02-15
Yes, the version of Matlab I have is a 32-bit application. This is why I have to use the "glnx86" tag when I start and install it. That was something that I found out when I installed it in 64-bit Fedora.

---

### Post by Kilz on 2008-02-15
> **thinkgeek said:**
> Yes, the version of Matlab I have is a 32-bit application. This is why I have to use the "glnx86" tag when I start and install it. That was something that I found out when I installed it in 64-bit Fedora.

[Use Getlibs ]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs")to install that file since it is a 32bit library.

---

### Post by thinkgeek on 2008-02-15
Thank you very much, that has solved that problem. Matlab isn't working yet, but it's a completely different problem. A quick search suggests a Java issue. I'll have to do some searching on it. I encountered the same problem when I tried out Fedora 8, but I didn't have the time to fix it so I went back to Fedora 7.

Again, thanks for your help.

---

