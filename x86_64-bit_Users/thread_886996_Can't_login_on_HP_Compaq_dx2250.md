---
title: "Can't login on HP Compaq dx2250"
date: 2008-08-11
forum: x86 64-bit Users
---

### Post by Gael33 on 2008-08-11
I've loaded Ubuntu 8.04 64bit on my "newer" computer which has a AMD Athlon 64bit CPU. It loaded okay after I followed all the procedures including username and password. Yet, when I try to login it appears to want to go forward and then reboots itself. Incidentally, I have Windows XP Pro on another partition.
Is this a software problem or a problem within my computer. I've now tried both the 32bit and the 64bit and the same thing happens with both OS's.
Please help if you can ... I'm a Newbie :)

gael.

---

### Post by Thelasko on 2008-08-12
What kind of video card does it have?

---

### Post by ezphilosophy on 2008-08-12
Just got dealing with the same problem.

At the login screen, under options, I chose gnome failsafe.  Then, when I got in, ubuntu asked me to install the restricted ati drivers.  After doing so and rebooting, I could log in no problem.

---

### Post by Thelasko on 2008-08-12
HP says it comes with an ATI graphics card.  This is likely the culprit.  I'm not an expert on ATI cards but here is my suggestion.

Try to boot up in safe graphics mode and install the [ATI driver.]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by Thelasko on 2008-08-12
There you go, ezphilosophy beat me to it.

---

### Post by Gael33 on 2008-08-12
> **Thelasko said:**
> What kind of video card does it have?

Thanks for taking the time to ask :)
I have solved the problem thanks to someone else and I'll put it on the board for future reference.

gael.

---

### Post by Gael33 on 2008-08-12
Thanks to whoever sent me the answer to this problem, I'm very grateful. :KS
In the login window in the lower left of the screen is the "Options" button. Change the session to "Gnome Failsafe" and login using your usual username and password. 
I uninstalled the ATI driver (as suggested) using Synaptic. (exserver-xorg-video-ati) removed.
If the graphics have changed, once you are able to access your programs reinstall the ATI driver again using Synaptic Package Manager.
For some reason I didn't have to reinstall the ATI driver because it was already installed previously. 
Anyway, following that procedure fixed the problem I had in login.

Thanks to everyone who offered knowledgeable advice.

gael.:popcorn:

---

