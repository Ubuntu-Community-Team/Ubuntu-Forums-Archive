---
title: "Can I use Windows registry files to improve compatibility with WINE"
date: 2012-04-09
forum: Wine
---

### Post by cobaltwarrior19 on 2012-04-09
I'm not new to Linux, or Windows, but I do have a question that's been rattling around in my head for a few days now. I have a few programs that run in Windows but not too good in WINE, ("garbage" rating). I was wondering if it were possible to use the registry from a Windows XP installation to make these programs work properly?

---

### Post by cogadh on 2012-04-09
Nope. The Wine registry and the Windows registry are not the same thing at all. They have enough similarities to satisfy most applications, but dumping the XP registry into Wine will just result in a non-functional Wine prefix. More info on the Wine registry:
[http://www.winehq.org/docs/wineusr-guide/using-regedit](http://www.winehq.org/docs/wineusr-guide/using-regedit)
[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

---

### Post by forrestcupp on 2012-04-10
The registry is just a complex system of app settings. Wine doesn't do a bad job with that. 

The problem is more with things like dll files that they had to reverse engineer. In some cases, we use Windows dll's to get things working better, but it doesn't always work. Whenever you hear people say to use Winetricks to install some dll, that is what they are talking about. Also, whenever you see someone say to go into Winecfg and set an override for riched20 or something, what you're doing is setting it to use the Windows dll, instead of Wine's reverse engineered one. Sometimes, it helps a lot, and sometimes apps just aren't going to work with Wine no matter what.

You have to be selective, though, because in some cases, Wine works better with its own dll files. One time, I tried replacing all of Wine's dll's with the native Windows ones, and it didn't turn out to be a good idea.

---

