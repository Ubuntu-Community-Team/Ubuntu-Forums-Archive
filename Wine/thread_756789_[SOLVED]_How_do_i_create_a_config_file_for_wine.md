---
title: "[SOLVED] How do i create a config file for wine?"
date: 2008-04-16
forum: Wine
---

### Post by nappymonster on 2008-04-16
Hi all,
I need to set some dlls to native windows, and to do that i need the wine config file (i think!), but i don't have one. All that is in my .wine folder is

dosdevices
drive_c
system.reg
user.reg
userdef.reg

and nothing else.
So how do i create this config file, and how do i then make these dlls native windows?

I'm following this guide:[Installing Office 2007 with Wine.]("http://wine-review.blogspot.com/2008/03/office-2007-on-linux-with-wine-install.html")

Thanks,
Nappymonster

---

### Post by aoanla on 2008-04-16
You don't "create a config file" - if you're following that howto, you'll notice that it tells you to run winecfg. This is how you configure things.

(So, in a terminal, type:

winecfg

)

---

### Post by nappymonster on 2008-04-18
Ok thanks, but i still don't know how to make some dlls native windows, but oh well. Thread solved i guess

---

### Post by thefishki345 on 2008-04-18
¨Ok thanks, but i still don't know how to make some dlls native windows, but oh well. Thread solved i guess¨

I think this is what you do. Go to libraries in winecfg, add your dlls.
then select your dlls, then select ¨edit¨ and then you can click on ¨native windows¨ or something.
Hope that helps.

---

