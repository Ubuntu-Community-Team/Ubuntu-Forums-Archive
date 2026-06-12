---
title: "i need help fast!!!"
date: 2007-08-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by M@TR!X on 2007-08-18
well my problem is that i just made the ISO image onto my cd and now i dont know what to do...do i put the cd into my laptop and then restart or what???i really need help thank you:confused:

---

### Post by Kilz on 2007-08-18
> **M@TR!X said:**
> well my problem is that i just made the ISO image onto my cd and now i dont know what to do...do i put the cd into my laptop and then restart or what???i really need help thank you:confused:

yes put the cd into my laptop and then restart

---

### Post by JAPrufrock on 2007-08-19
Don't forget that you have to go into your bios setup to change the boot option to boot from your CD drive first. Also use the live cd check disk option to make sure that your iso disk was copied correctly before you go ahead and install it.

---

### Post by damansandhu on 2007-08-19
yea , follow post number three

---

### Post by Jouke74 on 2007-08-21
You did not burn the iso file to the disk in such way that the directory listing now says 

Ubuntu-7.04-desktop-amd64.iso 

did you????

---

### Post by M@TR!X on 2007-08-28
well umm instead of using the CD i burned i just bought it but im still having problems heres the link for my other post
[http://ubuntuforums.org/showthread.php?t=537122](http://ubuntuforums.org/showthread.php?t=537122)
please try and help me
thank you

---

### Post by John.Michael.Kane on 2007-08-28
> **M@TR!X said:**
> well umm instead of using the CD i burned i just bought it but im still having problems heres the link for my other post
[http://ubuntuforums.org/showthread.php?t=537122](http://ubuntuforums.org/showthread.php?t=537122)
please try and help me
thank you

Looks like a boot issue. Try rebooting the machine with the ubuntu cd/dvd in the drive. At the boot/install prompt (make sure to hit F6 first), and add the command below to the boot parameter.
```
nosplash noapic nolapic
```  
note: do not remove any of the commands already shown in the boot line. just add the above commands to it. This should allow the machine to boot as normal.

Also just posting that xyz cd does not boot will not garner the help you may need. When posting for help please include your system specs.

---

### Post by very_japi on 2007-08-29
does it get to the stage where some green letters scater acrross the top of the screen and a  progress bars says "loading kernel" ?

---

### Post by funrider on 2007-08-29
maybe ur laptop screen resolution runs out of range during installation?

---

