---
title: "Post install oddness"
date: 2006-05-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by RichyL on 2006-05-21
Hi

just installed Ubuntu 5.10 and it went fine. When the machine boots I get to the logon screen as normal. I can log in but the desktop does not appear correctly. I can see a brown screen with a mouse pointer. There is no menu bar or other wallpaper. I don't see any splash screen for Gnome (I'm assuming one would appear). Also, my keyboard does not appear to work - so I cannot get to a terminal to look at stuff. My only option is to restart the machine.

I noticed that if I choose the "select language" on the logon screen I get a white box which does not contain anything. I cannot get rid of this box and I have to restart the machine.

I've done the install twice and both times get the same issue. I can start it in safe mode and get to a terminal session and things look OK as far as I can tell. 

Has anyone seen this before? I've got some linux experience on Red Hat but not Ubuntu.

Thanks in advance,

RichyL

---

### Post by RichyL on 2006-05-21
Update: saw this [http://www.ubuntuforums.org/showthread.php?t=112747](http://www.ubuntuforums.org/showthread.php?t=112747) and tried making a new user and leaving it longer to logon and still no joy.

If anyone has any ideas I would be very gratful.

Cheers,

RichyL

---

### Post by RichyL on 2006-06-01
Found the answer. It was the x configuration. I highlighted out the glx module and lowered the colour depth and screen resolution and I could log on. I have Nvidia graphics card so I am hoping putting on these drivers will then give me a tip-top display.

---

