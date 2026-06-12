---
title: "Hurray I managed to install Firefox 1.5 (w FLASH) without chroot or breaking ff 1.0.7"
date: 2005-12-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kuolio on 2005-12-16
I came across this while exploring howto install ff 1.5 on my ubuntu (BB 64bit). This is actualy a method combined from two how-to's: the [ "FireFoxNewVersion"]("https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29%7C%28new%29") and ["How To[AMD64]: 32bit Firefox and Flash, without the Chroot"]("http://www.ubuntuforums.org/showthread.php?t=90106")

Basicly this was what I did: I followed through the wiki-guide as it was. Then I tried to run ff with no luck and started to search google for answers. I came acros that how-to about installing 32bit FF 1.5RC on breezy, and did the following:

Installed the dependencies mentioned in it to get things working, noticed that the pango files (pango.rc and the other) were already there (maybe trying to run ff 1.5 installed the files?) and just made the 32bit launcher, the 5th section of the original how-to. I focked up 1st as I didn't put my correct path to FF executable in the firefox32 launcher, and then corrected it to point to /opt/firefox/firefox as there it is installed when you follow the 1st how-to, the wiki-one.

Then, with command "firefox32" my 32bit fully working 1.5 FF launched .. oh, beautifull, amazing experience!

To put it short: To install it.. Go through the Wiki-HowTo as it is, and then to get things working check out that second HowTo and make sure you have all the things it says you need to get it working in the beginning, and then check that you have the pongo files (section 4 of the how-to) and then do section 5. Simple, hope this helps someone.

After finishing this you have working ff 1.5 and (it seems this far, 6h testing now) that there is nothing broken.

---Edit 1---
Alas for me to say that! Few posts down and there is a problem amerging, I quote my reply: 

So, after all, I did brake something :????: Oh well, as a warning if someone tries to do this: You will break something having to do with launching programs from the ff-browser. But if this is a "no-issue" for you, I still recommend using ff 1.5. as it seems a lot snappier then before.

If there is anyone out there, who might have an idea about howto fix this, please step forward, your help will be most welcome

---

### Post by Bloot on 2005-12-16
Are all the icons ok? I mean when I tried RAOF's howto the gtk engine didn't work as it should.

Greetings.

---

### Post by etitor on 2005-12-16
Fascinating! Now I have Flash in FF 1.5 under my AMD64 without chroot!

But... Alas, File -> Send page (Archivo -> Enviar página) doesn't summon Evolution at all. And I use this constantly.

---

### Post by Kuolio on 2005-12-18
Now that you mention it, I've also lost the ability to launch bittornado from the "download" menus "open with.." dialog. I have to download my torrent files and launch them from nautilus.

So, after all, I did brake something :???:  Oh well, as a warning if someone tries to do this: You will break something having to do with launching programs from the ff-browser. But if this is a "no-issue" for you, I still recommend using ff 1.5. as it seems a lot snappier then before. 

If there is anyone out there, who might have an idea about howto fix this, please step forward, your help will be most welcome :)

---

