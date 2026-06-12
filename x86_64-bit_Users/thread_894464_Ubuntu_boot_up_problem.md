---
title: "Ubuntu boot up problem"
date: 2008-08-19
forum: x86 64-bit Users
---

### Post by Torqumada286 on 2008-08-19
I have GG on my wife's computer.  She told me that her computer stopped working.  The boot up process would just hang, looking for a drive.  Since she doesn't really do much beyond surf the internet and check her email, I decided to just install HH.  However, when I try to install it, I get the same message that I was getting the same message.  Since I hadn't seen the the error message for that particular drive in some time, I didn't catch if before.  Ubuntu is looking for a floppy drive, both on the GG bootup and HH install.  It didn't do this when I installed it last year.  There isn't a floppy drive on my wife's system.  It isn't even listed in the BIOS.  Any idea how I can get the computer to stop looking for the FD and either boot up or install?

Torqumada

---

### Post by Torqumada286 on 2008-08-19
6 hours and no answers?

Torqumada

---

### Post by VeeDubb on 2008-08-19
I know you said that there's no floppy listed in the bios, but my first suggestion would be to check again, and see if there is a setting in there somewhere to actually disable floppy support.

I have used motherboards that didn't even have a floppy connector, that still had bios options for whether on not you wanted to enable and internal floppy.

If that's not it, my next guess would be that it's not the floppy, but really some other drive causing problems.  A hard drive failing in the right manner, could easily cause those symptom.

It could be that the installer is checking for a floppy, and then hanging the instant it tries checking for hard drives because you've got a dead hard drive in there, and the floppy seek is the last thing reported, so it 'looks' like it's hanging up looking for the floppy.

---

### Post by Nysomin on 2008-08-20
If I'm not mistaken there are some drivers still require to be put on a floppy and installed from there(RAID comes to mind).  When installing 8.04 there should be an option for drivers(F5 or 6 maybe?) in the boot menu.  I also have been having a problem with grub that's similar.  I actually have a floppy drive(from my first 1995 Packard Bell no less), and normally grub will leave it alone, but every one in a while it will start searching on it and hang.  I just hit the restart button and it will usually start up fine.

---

