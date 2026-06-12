---
title: "Using Wine on a USB"
date: 2008-03-21
forum: Wine
---

### Post by UbuRuss on 2008-03-21
Hello everyone. Has anybody got Wine to install/work on a USB pen? My reason is to try and save space on my ASUS eeepc (4G) running xubuntu 7.10. If I could just plug it in and then use whatever application I've put on it it would by good.

Thanks for any help.

---

### Post by aashay on 2008-03-21
You could move all(or atleast bigger ones) wine related files to the usb drive and then symlink them into the appropriate places on the root partition. Just a suggestion

---

### Post by aashay on 2008-03-21
The forum for some reason wouldn't let me edit the message. So had to double post...
/usr/share/wine
/usr/lib/wine
would be the folders to look into

---

### Post by UbuRuss on 2008-03-22
Thanks, I'll have go and let you know.

---

### Post by mikeyphi on 2008-03-23
> **UbuRuss said:**
> Hello everyone. Has anybody got Wine to install/work on a USB pen? My reason is to try and save space on my ASUS eeepc (4G) running xubuntu 7.10. If I could just plug it in and then use whatever application I've put on it it would by good.

Thanks for any help.

Installing Gutsy on USB: [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
This allows stored changes to your (USB) setup.

I installed onto a SD card which I've left permanently in my Eee pc and boots on start-up.
There is also the option of having your /home partition on an external card/USB.

---

