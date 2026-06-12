---
title: "Manual: Eclipse on amd64 works!"
date: 2006-01-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by ruudiculus on 2006-01-02
Hi,

I've got eclipse working on my amd64. I've installed a amd64 JDK from Sun and Eclipse from [www.eclipse.org](www.eclipse.org). Haven't tried everything extensively though.

Please return remarks on the manual here.

Good luck.
[ATTACH]5025[/ATTACH]

---

### Post by Jave27 on 2006-01-13
Thanks, great tutorial!  However, I'm having an issue with the gdb debugger in the CDT plugin now.  I've gone through a whole laundry list of errors, the most recent being the following:

Stopped due to shared library event     *(quite a few of these)*
mi_cmd_stack_list_frames: No stack.

I've searched around on google and haven't found a good solution yet.  It seems like an issue with Eclipse & GDB & Makefiles.  I can get the debugger to work correctly on a single cpp file w/o a Makefile.

Oh well, back to Anjuta, I suppose.

---

### Post by ruudiculus on 2006-01-13
Well Anjuta gives initial errors too and it sometimes just hangs when you try to add/include libraries. In my case it missed glib first, so now that's fixed.

I really don't know where the errors you have come from, I've only added the C-plugin and I haven't one anything with it yet.

Hope you'll get rid of them! And please post the solution here off course! Then you can help me out :)

---

