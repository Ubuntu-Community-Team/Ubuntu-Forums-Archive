---
title: "Install cd on laptop crashing"
date: 2009-02-21
forum: x86 64-bit Users
---

### Post by Boozin on 2009-02-21
Don't know if this is a bug, or known issue but when I try to "install" using the 64 bit image on my HP Pavilion dv5217cl (though it says it is a dv5000 on the screen), it locks up every time.  Now the interesting part is that I can install from the cd as normal if I boot it as a "livecd" and then start the installer.  

When it crashes with the "install" boot option everything goes fine, the kernel boot, window manager starts up, and it looks like a window starts to open.  The cursor changes to the "busy" icon for a bit, then freezes.  At this point the computer is locked solid, terminals can't be opened, numlock is frozen, etc.  

If someone wants to help me diagnose what is happening, I can help.

---

### Post by Yellow Pasque on 2009-02-21
Did you burn the CD yourself? If so, did you verify the md5 of the image before your burned it? Did you burn at low-speed and/or verify the burn?

If you **know** the CD/media is good, then I suggest running memtest86+ to rule out the possibility of bad RAM. (You can do that with the "Check Memory.." option on the LiveCD)

---

### Post by Boozin on 2009-02-22
Yes I burned the cd myself, and yes I ran the boot option to verify that the checksums were good.  It passed with no issues.  

I have no reason to believe there is any ram issue because ubuntu installed fine, and is running without glitches now.  Windows XP is also installed and working great as well.  

In short, the hardware seems to run solidly, without any flakeyness. 

The odd thing is that when the "install" boot option was selected, it would crash every time, yet when the livecd boot option was selected it would run with no issue.  Once the "live" version was loaded, the installer could be started and ran without issue.

---

