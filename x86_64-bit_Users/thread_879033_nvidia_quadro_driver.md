---
title: "nvidia quadro driver"
date: 2008-08-03
forum: x86 64-bit Users
---

### Post by kyo007 on 2008-08-03
hi, i have downloaded quadro fx driver from nvida but i can't install it. how can i install it ?

file name : NVIDIA-Linux-x86_64-173.14.12-pkg2.run
i use ubuntu 8 x64.

Thanks.

---

### Post by tamoneya on 2008-08-03
this is all assuming the driver is on the desktop.

Open terminal (applications -> accessories -> terminal) and run:```
cd ~/Desktop
chmod +x NVIDIA-Linux-x86_64-173.14.12-pkg2.run
sudo ./NVIDIA-Linux-x86_64-173.14.12-pkg2.run
```

---

### Post by kyo007 on 2008-08-03
when i write chmod +x NVIDIA-Linux-x86_64-173.14.12-pkg2.run , it's not working and driver file on my desktop, i need to move it ? 


[ATTACH]80072[/ATTACH]

---

### Post by tamoneya on 2008-08-03
you didnt run this command:```
cd ~/Desktop

```

---

### Post by kyo007 on 2008-08-03
i write it but nothing changed .. what is problem ? 

[ATTACH]80075[/ATTACH]

---

### Post by tamoneya on 2008-08-03
okay that doesnt make any sense.  That says you dont have a desktop.  Please run this command.  i want to figure out what is going on.```
ls -l ~
```

EDIT: it is easier to copy and paste from terminal instead of screenshotting.  The only difference is the shortcut in terminal is ctrl-alt-c instead of ctrl-c.

---

### Post by kyo007 on 2008-08-03
how can i disable x server ? or change default level ? 

thanks

---

### Post by xen-uno on 2008-08-03
It doesn't get better than this ...

[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

---

