---
title: "Please....help me do what I want to do. (WIne &amp; Steam)"
date: 2007-01-02
forum: Wine
---

### Post by CDiablo on 2007-01-02
Im a n00b to Ubuntu... and I love it. Id really like to get away from windows but I love my gaming. I've been playing around with steam and wine for a while and am having some troubles. Ive looked all over the forums (which have been a help with my problems thus far) but have not been able to find an anwser to my problems. So heres what I want to do:

1) I want to run steam in fullscreen in its own window. I hae tried wine with the -fullscreen tag but I get errors

2) I want to be able to run Half-Life Episode 1: but I get the error [SteamStartup() failed: SteamStartup(0xf,0x0034E064) failed with error 1: The registry is in use by another process, timeout expired]

3) Any tweaks to get up the framerate? (I get 50-60 fps but It dont hurt to have more)

Thanks all for the help.

---

### Post by haxer on 2007-01-02
[http://www.ubuntuforums.org/showthread.php?p=1540434](http://www.ubuntuforums.org/showthread.php?p=1540434)

This is the easiest way.

BTW this guide is only for dapper if you have edgy please post it in forum and ill help you:)

---

### Post by KuriKai on 2007-01-02
> I want to be able to run Half-Life Episode 1: but I get the error [SteamStartup() failed: SteamStartup(0xf,0x0034E064) failed with error 1: The registry is in use by another process, timeout expired]
watch the terminal when you close steam does it say something like "erro,r can not delete shorcuts.dat"?
If it says that, load up steam, then create a new file in your steam folder and name it "shortcuts.dat" then close steam.
That should fix it

---

### Post by CDiablo on 2007-01-03
Duh.....I forgot to say that I was running edgy....

I got HL episode 1 to work thanks KuriKai

Thanks for the help guys.

---

### Post by mp_officer on 2007-01-09
I seem to be haveing this problem to. Error comes up saying...... The registry is in use by another process. Now i never had any problems before this new update what has kinda pissed me of. Can anyone help? thanks

---

### Post by Thiesen on 2007-04-01
> **KuriKai said:**
> watch the terminal when you close steam does it say something like "erro,r can not delete shorcuts.dat"?
If it says that, **load up steam, then create a new file in your steam folder and name it "shortcuts.dat" then close steam**.
That should fix it


You are a little bit unclear to me if I should do that while Steam is up and running or or before I even start Steam??

Hmmm... that file doesn't even exist?? No wonder why Steam gives this error... :-)

Well... I'll do it your way then... :-)

Well... your way didn't do it either...

```

$ env WINEPREFIX="/home/thiesen/.wine" wine "C:\Program Files\Steam\steam.exe" -applaunch 240
fixme:process:IsWow64Process (0xffffffff 0xc07e4c) stub!
fixme:shdocvw:ViewObject_SetAdvise (0xda6f5c8)->(1 00000002 0x1252c18)
fixme:shdocvw:PersistStreamInit_InitNew (0xda6f5c8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xda6f5c8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xda6f5c8)->(ffffffff)
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:systray:delete_icon invalid tray icon ID specified: 1d
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0xdacea40)->(1 00000002 0x12533d0)
fixme:shdocvw:PersistStreamInit_InitNew (0xdacea40)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xdacea40)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xdacea40)->(ffffffff)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0xdacea40)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0xdacea40)
fixme:shdocvw:OleObject_Close (0xdacea40)->(1)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0xda6f5c8)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0xda6f5c8)
fixme:shdocvw:OleObject_Close (0xda6f5c8)->(1)
**Unable to remove c:\program files\steam\shortcuts.dat!**
Shutting down. . .

```Hmmm... I think I'll have to do that manually?? I think it's safe... but then again I'm not afraid of a little breakage now and then... :-)

---

### Post by joos13 on 2007-07-06
> **KuriKai said:**
> watch the terminal when you close steam does it say something like "erro,r can not delete shorcuts.dat"?
If it says that, load up steam, then create a new file in your steam folder and name it "shortcuts.dat" then close steam.
That should fix it

I've got the "registry" bug and in the terminal log, and steam does complain about not being able to delete "shortcuts.dat" at shutdown.  However, the workaround of manually creating "shortcuts.dat" does not work.  Any new ideas?

---

### Post by samtfaulkner on 2007-09-11
My problem is that steam loads up fine. but when i start Condition Zero it comes up with the Failed error 1 message

I agree. Creating the file shortcuts.dat doesnt seem to work.

anyone got any other ideas?



Sam the noobuntu on 7.04

---

