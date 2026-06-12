---
title: "Installation Help"
date: 2006-07-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by darkzar99 on 2006-07-09
When installing I get an error saying that X11 could not be set up.  I viewed the Xorg.0.log file and towards the end it said something like "Display can not be found" what should I do? :confused:

BTW The Graphics Card I Use Is an ATI RADEON X700 Pro PCI-E

---

### Post by Kilz on 2006-07-09
> **darkzar99 said:**
> When installing I get an error saying that X11 could not be set up.  I viewed the Xorg.0.log file and towards the end it said something like "Display can not be found" what should I do? :confused:

BTW The Graphics Card I Use Is an ATI RADEON X700 Pro PCI-E
[You may need to install the binary driver.]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25")
Follow them up to
```
The following steps did not work for me. In exchange to the next steps enter  'dpkg-reconfigure xserver-xorg' and choose 'fglrx'.
```

---

### Post by darkzar99 on 2006-07-09
Sorry, that didnt work,  Istill get the same error

It says ```
"Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you liketo view the X server output to diagnose the problem?"
```

---

### Post by darkzar99 on 2006-07-16
I can not figure this out, anyone have any suggestions? does Ubuntu have PCI-Express support?

---

### Post by Kilz on 2006-07-16
> **darkzar99 said:**
> I can not figure this out, anyone have any suggestions? does Ubuntu have PCI-Express support?

[The radon x700 is listed as a compatible card.]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards")
Please open a terminal and type in
```
lspci
```
Then copy/paste the results to a post.

---

