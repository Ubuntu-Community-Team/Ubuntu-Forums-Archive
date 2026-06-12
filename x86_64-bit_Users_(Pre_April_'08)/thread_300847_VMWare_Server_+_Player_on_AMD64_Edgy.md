---
title: "VMWare Server + Player on AMD64 Edgy"
date: 2006-11-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by camilluk on 2006-11-16
Does anyone know if VMWare Server + Player work on an AMD64 running  Edgy?

Like most people here, I also need to run a couple of Windows-based applications... can anybody suggest a tested VM software to achieve this on a machine like the above?

Thank you!
Cam :-k

---

### Post by kuja on 2006-11-16
They do. I used to have a vmware server setup, but I don't currently.

---

### Post by fabertawe on 2006-11-16
> **camilluk said:**
> Does anyone know if VMWare Server + Player work on an AMD64 running  Edgy?

Like most people here, I also need to run a couple of Windows-based applications... can anybody suggest a tested VM software to achieve this on a machine like the above?

Thank you!
Cam :-k

I installed the server version a couple of days ago for the first time and it is amazing! I used XP to try it with. XP sees VMWare as the machine it is running on, you can even press F2 while booting to enter the BIOS!

You configure the hardware for each guest OS independently and can plug and unplug devices (CDROM, USB etc) whilst running. You can only use hardware that will work with the parent OS (Edgy in my case) in theory but it's actually better than that! My scanner (parallel port) does not work with Ubuntu but works in the VMWare hosted XP :D  It also appears that anything USB will work too, it picked up my webcam no problem with the XP driver. I'm not sure whether the USB device has to be connected before you run VMWare though.

XP seems to run pretty near normal speed and boots a lot quicker than from  it's partition (this could be because it's not as bloated though). I like the way you can auto-fit the desktop to the VMWare window size!

Copying files back and forth took me a while to sort out using Samba but is working perfectly now. Apparently the install gives you the option to use VMWare's built in networking but I must have missed it. VMWare hosted XP has it's own IP on the home network and can see and be seen by the other physical XP machine here.

I would say try it, it's a free download (weighing in around 100Mb). Now I can easily try out different flavours of Linux etc.

Paul

---

