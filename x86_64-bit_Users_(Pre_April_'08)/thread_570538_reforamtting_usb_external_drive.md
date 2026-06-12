---
title: "reforamtting usb external drive"
date: 2007-10-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Guns90 on 2007-10-08
Good Morning.  I have a usb external drive that I copied a bunch of linux stuff on to.  I have since reformatted my computer and done a clean install of Fiesty 64-bit.  If I remember correctly, I used to be able to go into accessories and 'format' was listed in my old dapper 32-bit system.  It's no longer there in fisety 64-bit.  I can't figure out how to reformat this usb extenal drive so that I can use it exclusively on my son's 32-bit vista system.  I would appreciate some help, please.  Thanks

---

### Post by John.Michael.Kane on 2007-10-08
To format the USB drive:

Step1
Right click on the desktop icon of the USB drive and select unmount
Next:
Open Gparted and selecting that drive. If you don't have gparted install you will need to install it. 

To do so run the command below.
```
gksudo aptitude install gparted
```
 
Step2
Delete the current settings of that drive
Next:
Format the drive with ext2/ext3 or file format of your choice.

Step3
Unplug the USB Drive from the system and then Plug it back in, OS should now re detect it.

---

### Post by Guns90 on 2007-10-08
thanks, sd-plisskin.

---

### Post by John.Michael.Kane on 2007-10-08
> **Guns90 said:**
> thanks, sd-plisskin.

No problem, Please post if there are any further issues.

---

### Post by Guns90 on 2007-10-17
Post Deleted

---

### Post by John.Michael.Kane on 2007-10-17
> **Guns90 said:**
> Post Deleted

Gparted should work on 64bit the same as 32. What issues are you having with gparted?

---

