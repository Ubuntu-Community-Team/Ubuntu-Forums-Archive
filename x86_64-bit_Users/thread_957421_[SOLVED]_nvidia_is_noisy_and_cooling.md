---
title: "[SOLVED] nvidia is noisy and cooling"
date: 2008-10-24
forum: x86 64-bit Users
---

### Post by bro on 2008-10-24
Hi, I just upgraded from 32-bit hardy to 64-bit intrepid. I installed the restricted driver for Nvidia, version 177. I rebooted. It's fan is blowing. it started on - off - on - off but now is on permanently. What the?!?! Can this be handeled by nvidia-settings? Has this something to do with 64-bit? or with the updated driver?

---

### Post by xen-uno on 2008-10-24
My guess is ... If Compiz is running, then so is OpenGL, and that's using your graphics processor with the driver probably setting the performance to max, which should also max out your fan speed. The X-windows system is OpenGL based too, AFAIK. This behavior is new though, eh? You might try installing NVidia's latest driver ...

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

then look at this ...

[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

It worked for me with Gutsy & Hardy (from a driver upgrade standpoint), should work for Intrepid.

[color=blue]edit:[/color] The above may not work (it may fail on compiling) after looking at a few threads here ...

[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

I think you may have to give both the Ubuntu dev's and NVidia some time to sort it out.

---

### Post by jpkotta on 2008-10-24
Check out nvclock.  Possibly you can control the fan with it.

I've had trouble with nvidia drivers and fans in Hardy.  My solution was to manually install old drivers (in my case, version 100-something, the ones in Gutsy).

---

### Post by bro on 2008-10-25
Thanks but the problem is solved. Another look around the forums solved it :) I don't where it starts (the new kernel, the new driver - I suppose the driver) but it can be solved by upgrading the BIOS to version A12. More people with a Dell and Nvidia have this issue, the upgrade solved instantly. So... many thanks to Dell for keeping their BIOS's updated too.

---

