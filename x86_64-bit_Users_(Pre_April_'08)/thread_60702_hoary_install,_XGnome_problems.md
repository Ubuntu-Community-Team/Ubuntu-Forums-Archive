---
title: "hoary install, X/Gnome problems"
date: 2005-08-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by dreamersrevenge on 2005-08-28
Ok, I've just installed Hoary 5.04 on my Athlon64 system. The installation went fine until I went to login. The login screen displays just fine, but when it goes to load gnome all I get is a brown screen with the cursor. After it reaches that point, I can't switch to a console, restart X or anything. I wind up having to restart the PC via the restart button. While at the login screen I can switch to a console and login to a prompt or restart X, but that's about it. My system is an athlon64 3200+, Geforce 6200 PCI-E, 512mb ram, and the install is on a 20gig maxtor.

---

### Post by weekend warrior on 2005-08-29
Did you make sure to use the AMD64 install CD and check the MD5SUMS?

---

### Post by dreamersrevenge on 2005-08-29
I'm not really sure how to check the md5sums in Windows.

---

### Post by heimo on 2005-08-29
md5sum links
[http://www.nullriver.com/index/products/winmd5sum](http://www.nullriver.com/index/products/winmd5sum)
[http://www.kana.homeip.net/index.php?i=45](http://www.kana.homeip.net/index.php?i=45)
[https://wiki.ubuntu.com/VerifyIsoHowto](https://wiki.ubuntu.com/VerifyIsoHowto)
[http://www.openoffice.org/dev_docs/using_md5sums.html](http://www.openoffice.org/dev_docs/using_md5sums.html)
[http://www.md5summer.org/](http://www.md5summer.org/)
[http://www.linuxiso.org/viewdoc.php/verifyiso.html](http://www.linuxiso.org/viewdoc.php/verifyiso.html)

---

### Post by Dagger28256 on 2005-08-29
I had the same problem, and in order to fix it, you need to use a framebuffer driver instead of the default ATI driver. It doesn't look as nice as it could, and if you have a widescreen, you will need to figure that out.

I was wondering if anyone knew of how to get a proper working ATI driver. I have an HP Pavilion zv6000 laptop, and am looking for a proper driver to make it work.

---

### Post by dreamersrevenge on 2005-08-29
[QUOTE=Dagger28256]I had the same problem, and in order to fix it, you need to use a framebuffer driver instead of the default ATI driver. It doesn't look as nice as it could, and if you have a widescreen, you will need to figure that out.

I was wondering if anyone knew of how to get a proper working ATI driver. I have an HP Pavilion zv6000 laptop, and am looking for a proper driver to make it work.[/QUOTE]


Would this problem also be fixable by installing the latest nVidia drivers? I saw a guide here somewhere but I'll hafta search for it. The only thing that really gets me on that is the kernel module bit, but if I have a tutorial link I can read it on the laptop and get things setup. I'm no expert, but just an idea. :)

edit: no widescreen either, just a regular 17" CRT at the moment.

---

### Post by DancingSun on 2005-08-29
[QUOTE=dreamersrevenge]Would this problem also be fixable by installing the latest nVidia drivers? I saw a guide here somewhere but I'll hafta search for it. The only thing that really gets me on that is the kernel module bit, but if I have a tutorial link I can read it on the laptop and get things setup. I'm no expert, but just an idea. :)

edit: no widescreen either, just a regular 17" CRT at the moment.[/QUOTE]
Are you speaking of tseliot's how-to?  I remember tseliot saying that he also owns a GeForce 6200, and that it didn't work with the drivers in the Ubuntu repositories.  He had to install the latest nVidia drivers to get it to work, which is why he made the how-to on installing the latest nVidia drivers.

I would definitely encourage you to try out the latest drivers, as it seems that you might be having the same problem that he had.

---

### Post by dreamersrevenge on 2005-08-29
Ok, I'll see what that does and post back. I'll have to wget the drivers from the console, but that'll more than likely be the most difficult part of it.

---

### Post by dreamersrevenge on 2005-08-29
[QUOTE=dreamersrevenge]Ok, I'll see what that does and post back. I'll have to wget the drivers from the console, but that'll more than likely be the most difficult part of it.[/QUOTE]
 Ok, I've finally managed to get X to somewhat cooperate. I went into the xorg.conf file and edited the section under display where it says driver. I changed that from nvidia (or whatever it was, cant remember off-hand) to vesa. X starts and is functional, but the refresh rate is horrible. I tried to install the nVidia drivers, but it needs the kernel source installed. I'm not too sure how to do that. :/

---

### Post by DancingSun on 2005-08-29
[QUOTE=dreamersrevenge]Ok, I've finally managed to get X to somewhat cooperate. I went into the xorg.conf file and edited the section under display where it says driver. I changed that from nvidia (or whatever it was, cant remember off-hand) to vesa. X starts and is functional, but the refresh rate is horrible. I tried to install the nVidia drivers, but it needs the kernel source installed. I'm not too sure how to do that. :/[/QUOTE]
Ok, I dug up tseliot's guide on [How To Install the Lastest nVidia Drivers](http://ubuntuforums.org/showthread.php?t=57368&highlight=nvidia).

---

### Post by dreamersrevenge on 2005-08-30
I'll try that tomorrow now that I know how to get X somewhat useable so I can run synaptic. Also, do I have to use the nvidias glx or can I use the already installed openGL?

---

### Post by DancingSun on 2005-08-30
[QUOTE=dreamersrevenge]I'll try that tomorrow now that I know how to get X somewhat useable so I can run synaptic. Also, do I have to use the nvidias glx or can I use the already installed openGL?[/QUOTE]
You'll need to install GLX.  GLX stands for "OpenGL Extension to the X Window System".   Which means any X application that uses OpenGL goes through the GLX api.

---

### Post by dreamersrevenge on 2005-08-30
Ok, I read something on the tutorial about removing the default installed (is that right?) gl libraries/drivers (what are they called? sorry, n00b). I know that was causing somewhat of a fit when I tried to install the drivers last night.

---

### Post by dreamersrevenge on 2005-09-01
I used the tutorial and it worked like a charm. Everything is up and running.

---

### Post by DancingSun on 2005-09-01
Sweet!

---

### Post by dreamersrevenge on 2005-09-02
Now I'm beginning to think something went wrong.. I use Windows on this system as well as ubuntu, but it's been booted to windows for awhile now. I just went to boot into ubuntu earlier and now it says it cannot load the nvidia kernel module. I tried to startx after changing the driver to "vesa", but as my luck would have it I kept getting font renderer errors. It seems I'm having the worst of luck with this thing as of late. :/

---

### Post by DancingSun on 2005-09-03
Try booting into Ubuntu using the old kernel

---

### Post by dreamersrevenge on 2005-09-03
I think I tried that but I'll doublecheck. Tomorrow I'm going to reinstall it again and go all through it. It could also be something I've grabbed from apt as well. guess I poked around too much.

I thought I heard a doughboy noise....

---

