---
title: "Wine can`t find other partitions"
date: 2008-06-15
forum: Wine
---

### Post by ^^viktor^^ on 2008-06-15
As the title says  Wine can`t find my other partitions.
For instance I run this
>  wine /media/sda1/Program Files/Notepad++/notepad++.exe
this is what i get
> wine: cannot find '/media/sda1/Program

If i try to run it with sudo, I get this
> wine: /home/viktor/.wine is not owned by you

What sholud I do.  Should I delete .wine or something? Help!!

---

### Post by leomelo on 2008-06-15
try:wine /media/sda1/'Program Files'/Notepad++/notepad++.exe

---

### Post by cogadh on 2008-06-15
You shouldn't run Windows programs from an existing Windows partition through Wine. Usually it won't work anyway, but it can also completely screw up your Windows drive and make unbootable. From the [Wine FAQ](http://wiki.winehq.org/FAQ):
> [B]1.5. I have lots of applications already installed in Windows. How do I run them in Wine?
[/B]
Short answer: You have to install them in Wine just like you did in Windows. Applications usually have a setup or installer program.

Long answer: Some applications can be copied from Windows to Wine and still work, but don't try this unless you like tinkering under the hood of your car while it's running.

Wine is not designed to interact with an existing Windows installation.

WARNING: Do not try to configure Wine to point to your actual Windows C:\ drive. We have tried to make this hard to do, so you probably cannot do it by accident. Wine may or may not continue to operate. Your Windows install will be 100 percent dead due to wine inserting its required parts windows that are ELF-PE. The only way to fix Windows after this has happened is to run a reinstall of Windows. 

---

### Post by ^^viktor^^ on 2008-06-15
@leomelo
Thanks dude, it worked fine.
@cogadh
About screwing up the  whole Windows drive, not thet i care :), but how can i perevent it?

---

### Post by cogadh on 2008-06-15
Like I said, don't run Windows apps in Wine from a Windows drive. You should just install them in Wine instead.

---

