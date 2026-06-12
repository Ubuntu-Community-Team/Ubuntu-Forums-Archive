---
title: "Can't find Microsoft executables in Wine browse C:"
date: 2013-03-19
forum: Wine
---

### Post by zaospawn on 2013-03-19
Hello world. I am new to Ubuntu and Linux as a whole and I am also an aspiring computer programmer (as a hobby, really). On my computer I have Ubuntu 12.10 through Wubi dual boot with Windows 7. I want to use my Ubuntu desktop for work more than Windows because I am more productive with Ubuntu. Anyways, I use Microsoft Power Point a lot so I recently installed Wine Browse C: and I cannot find my executable for Power Point nor can I find any of my files saved on my Windows 7. When I access my .wine directory and type ls here's all I get:

> 
[email]brian@ubuntu:~/.wine[/email]$ ls
dosdevices  drive_c  system.reg  user.reg  userdef.reg

When I browse it using the GUI and even hit ctrl+H there is nothing hidden and nothing available in my Program Files folder or anywhere on my C drive through Wine. I am not sure if there is something broken in Wine, if I am doing something wrong, or if I am missing a step after installation where I could even access my C drive. The worse part is I am not really sure where to start in asking for help. How can I find or access anything on my C drive? I have tried using ctrl+H but nothing shows up and I cannot find any of my files or executables.

---

### Post by coldraven on 2013-03-19
I have never used Wubi but I think you are looking in the wrong place, wine has nothing to do with your Windows system.
In Nautilus file browser can you see any other file systems, possibly labelled "Devices"?

---

### Post by Mark Phelps on 2013-03-19
In Wubi systems, your "C" drive is automatically mounted under /host.

But ... be careful ... modifying, deleting, or adding files to your  "C" partition from inside Wine risks corrupting the Win7 filesystem -- and could render it unbootable.

Also, Powerpoint does not work well under Wine.  It gets at best a Silver rating: 

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=13]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=13")

---

