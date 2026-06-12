---
title: "Changing Icon theme does not change Firefox icon"
date: 2009-11-13
forum: x86 64-bit Users
---

### Post by Sir Rodness on 2009-11-13
Hi all,

Using Ubuntu 9.10 64bit and ran into an odd problem. I actually even tried to reinstall figuring I must of over looked something. It seems that no matter what icon theme I pick my default firefox icon will not change to match the new theme. It just always stays the same while all the other icons change to the selected icon theme no problem at all. This is the first time I've run into this. I imagine its a quick fix, I just don't know where to look.

---

### Post by Ginsu543 on 2009-11-13
Are you talking about the Firefox icon in the menu (Applications --> Internet)? You can manually change that icon by going to System --> Preferences --> Main Menu. Navigate to and click on the Firefox entry, and click on the Properties (or Edit) button on the right. That should bring up the launcher properties window. If you click on the Firefox icon image, it will bring up a dialog box that will let you replace the icon with whatever icon you want (in .png format).

---

### Post by vrhahaha on 2009-11-14
I guess he is talking about the icon in the taskbar. This is not specific to 64bit because i had the very same problem when i was using 32bit. I could offer no help, but i believe there is a tool out there that can change the icon.

---

### Post by Sir Rodness on 2009-11-14
Hi there,

Thanks for the responses. I can definitely manually change the icon to whatever I want its that the firefox icon system wide does not change when I change my icon theme. It's simply just locked as the default regardless of the icon theme picked (Unless of course I change it manually). Its not an unbearable bug, but I was curious if anyone else experienced it before.

---

### Post by Ginsu543 on 2009-11-14
I see now what you are getting at. Are you certain that all these themes have their own separate icon for Firefox? I would think that since Firefox is a third-party program (granted it is included in the base installation), most themes would keep its icon as is. Just brainstorming with you.

---

### Post by HalfEmptyHero on 2009-11-14
I don't know how to change the icon in the taskbar, but the reason the other icon doesn't change when you change themes is because there is most likely not a firefox-3.5 icon in the theme. Go to the app folder of the icon theme and make a copy of the firefox icon (or the symbolic link if there is one) and rename that one to firefox-3.5.png or whatever file format it is.

---

### Post by Sir Rodness on 2009-11-14
HalfEmpty you're my Hero.
 
Went to the .icons folder and picked my current theme. Made a copy of the firefox icon and changed the name to firefox-3.5 instead of firefox-3.0. Never even crossed my mind that it would be that simple of a fix. Will have to make the adjustment to some other themes, but that's fine. Learned something new today about Linux and icon themes. Thanks a lot.

---

