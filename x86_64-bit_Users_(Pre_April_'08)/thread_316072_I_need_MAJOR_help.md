---
title: "I need MAJOR help"
date: 2006-12-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by blu3sman on 2006-12-10
Ok 1st up, I'm EXTREMELY new to Ubuntu and have absolutlely no idea what i'm doing so go easy on me lol :) 

I was trying to install ATI drivers using this guide [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

when suddenly Ubuntu shutdown and now i cant get back into it normally or using safemode.

in normal mode i get this message
INIT: cannot execute "/etc/init.d/rcS"
INIT: entering run level: 2
INIT: cannot execute "/etc/init.d/rc"

what have i done and is there any way to fix this other than reinstall Ubuntu?? ( please in noob terminology thankyou )

---

### Post by Paul41 on 2006-12-10
I have not seen this problem before, but since it says something about run level 2 you could see if a different run level has the same problem. Run levels 3 through 5 are clones of level 2

Type:

```
sudo nano /etc/inittab
```

Then look for the line:

```
id:2:initdefault:
```

Change the 2 to a 3 then save the file and reboot.

---

### Post by prince_niceguy on 2006-12-10
seems you have changed the permission on the files. make them executable.

boot with your ubuntu disc then change the file permissions.

you can do it through nautilus or command prompt. nautilus go to the folder described above and change. 

from command line you can use

chmod 755 [filename]. 

hope this helped.

---

