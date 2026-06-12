---
title: "Numlock on laptop"
date: 2007-07-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Paul820 on 2007-07-09
I have just recently installed the 64bit version of Ubuntu. I was using the x86 version and the numlock key was fine. Now, when i press the numlock key it makes the application go to full screen mode, so i'm thinking it's mapped wrong. The reason i need this to work is i am learning blender, and i need the numlock key to access the numpad embedded into the keyboard. The laptop is Acer Aspire 5100 using the UK keyboard layout. I have done a search but most of them explain how to turn it on a boot. Well i tried that and then i couldn't turn it off 
and on when needed, so when i typed some letters like OL etc i got numbers. I just need it to work as it's supposed to do, click on, click off. If anyone knows how to get it to work could you let me know how it's done? Thank you in advance.

EDIT: Doesn matter now, i edited my etc/X11/gdm/Init/Default file and entered some lines from another website:

if [ -x /usr/bin/numlockx ]; then
 /usr/bin/numlockx on
fi

rebooted and i couldn´t log back in as my keys were numbers. Anyway, i started pressing allsorts of keys and erm...found out i could turn numlock off and on by pressing the fn key and numlock button. So it´s working now. Sorry for the trouble.

---

