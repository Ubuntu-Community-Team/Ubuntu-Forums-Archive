---
title: "Counterstrike freezing with wine"
date: 2006-08-12
forum: Wine
---

### Post by maka on 2006-08-12
Just updated to the latest wine...

been experiencing freezing in game recently.  play for a couple minutes den it freezes.

anyone share this problem?](*,)

---

### Post by Concrete on 2006-08-12
Did ubuntu show some error window or just freezes all game?

---

### Post by HAARP on 2006-08-12
Start a terminal and cd to the folder steam is installed in. Type
```
wine steam.exe
```
There should be console output. What does it say?

---

### Post by maka on 2006-08-21
> **HAARP said:**
> Start a terminal and cd to the folder steam is installed in. Type
```
wine steam.exe
```
There should be console output. What does it say?

thanks in advance. this is the output:
```


-desktop:~/.wine/drive_c/Program Files/Steam$ wine Steam.exe
fixme:shdocvw:ViewObject_SetAdvise (0xd83ae58)->(1 00000002 0x10f17f0)
fixme:shdocvw:PersistStreamInit_InitNew (0xd83ae58)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xd83ae58)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xd83ae58)->(ffffffff)
fixme:shdocvw:WebBrowser_put_Silent (0xd83ae58)->(ffffffff)
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0xd83aef4)->((null) 1 0x33d410 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd83aef4)->((null) 25 0 0x33d424 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd83aef4)->((null) 26 0 0x33d424 (nil))
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d378 0x33d3c4 (nil) 0x33d388)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d338 0x33d384 (nil) 0x33d348)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d378 0x33d3c4 (nil) 0x33d388)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d338 0x33d384 (nil) 0x33d348)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d378 0x33d3c4 (nil) 0x33d388)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d378 0x33d3c4 (nil) 0x33d388)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d378 0x33d3c4 (nil) 0x33d388)
fixme:shdocvw:ClientSite_GetContainer (0xd83aef4)->(0x33d450)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd83aef4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33d554 (nil))
fixme:mshtml:PersistMoniker_Load not supported pibc
err:systray:delete_icon invalid tray icon ID specified: 1d
fixme:process:SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless
fixme:mshtml:HlinkTarget_SetBrowseContext (0xd8b6fe8)->((nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0xd83aef4)->((null) 1 0x33d410 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd83aef4)->((null) 25 0 0x33d424 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd83aef4)->((null) 26 0 0x33d424 (nil))
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d378 0x33d3c4 (nil) 0x33d388)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d338 0x33d384 (nil) 0x33d348)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d378 0x33d3c4 (nil) 0x33d388)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d338 0x33d384 (nil) 0x33d348)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d378 0x33d3c4 (nil) 0x33d388)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d378 0x33d3c4 (nil) 0x33d388)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d378 0x33d3c4 (nil) 0x33d388)
fixme:shdocvw:ClientSite_GetContainer (0xd83aef4)->(0x33d450)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd83aef4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33d554 (nil))
fixme:mshtml:PersistMoniker_Load not supported pibc
fixme:mshtml:HlinkTarget_SetBrowseContext (0xd8b6fe8)->((nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0xd83aef4)->((null) 1 0x33d330 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd83aef4)->((null) 25 0 0x33d344 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd83aef4)->((null) 26 0 0x33d344 (nil))
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d298 0x33d2e4 (nil) 0x33d2a8)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d258 0x33d2a4 (nil) 0x33d268)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d298 0x33d2e4 (nil) 0x33d2a8)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d258 0x33d2a4 (nil) 0x33d268)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d298 0x33d2e4 (nil) 0x33d2a8)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d298 0x33d2e4 (nil) 0x33d2a8)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d298 0x33d2e4 (nil) 0x33d2a8)
fixme:shdocvw:ClientSite_GetContainer (0xd83aef4)->(0x33d370)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd83aef4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33d474 (nil))
fixme:mshtml:PersistMoniker_Load not supported pibc
fixme:mshtml:HlinkTarget_SetBrowseContext (0xd8b6fe8)->((nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0xd83aef4)->((null) 1 0x33d330 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd83aef4)->((null) 25 0 0x33d344 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd83aef4)->((null) 26 0 0x33d344 (nil))
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d298 0x33d2e4 (nil) 0x33d2a8)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d258 0x33d2a4 (nil) 0x33d268)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d298 0x33d2e4 (nil) 0x33d2a8)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d258 0x33d2a4 (nil) 0x33d268)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d298 0x33d2e4 (nil) 0x33d2a8)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d298 0x33d2e4 (nil) 0x33d2a8)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d298 0x33d2e4 (nil) 0x33d2a8)
fixme:shdocvw:ClientSite_GetContainer (0xd83aef4)->(0x33d370)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd83aef4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33d474 (nil))
fixme:mshtml:PersistMoniker_Load not supported pibc
fixme:mshtml:HlinkTarget_SetBrowseContext (0xd8b6fe8)->((nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0xd83aef4)->((null) 1 0x33d330 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd83aef4)->((null) 25 0 0x33d344 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd83aef4)->((null) 26 0 0x33d344 (nil))
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d298 0x33d2e4 (nil) 0x33d2a8)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d258 0x33d2a4 (nil) 0x33d268)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d298 0x33d2e4 (nil) 0x33d2a8)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d258 0x33d2a4 (nil) 0x33d268)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d298 0x33d2e4 (nil) 0x33d2a8)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d298 0x33d2e4 (nil) 0x33d2a8)
fixme:shdocvw:ClDispatch_Invoke (0xd83aef4)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d298 0x33d2e4 (nil) 0x33d2a8)
fixme:shdocvw:ClientSite_GetContainer (0xd83aef4)->(0x33d370)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd83aef4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33d474 (nil))
fixme:mshtml:PersistMoniker_Load not supported pibc
fixme:process:SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless

```

---

### Post by Cannonzim on 2008-06-14
im getting the same problem

here is my output
abdullah@abdullah-desktop:~$ wine steam.exe
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"C:\\windows\\system32\\steam.exe": Module not found
abdullah@abdullah-desktop:~$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

---

### Post by Fred_E _krugar on 2008-06-14
I know this may sound strange but try to turn the resolution down in the game.

---

### Post by Cannonzim on 2008-06-14
I tried but it just messes it up even more

---

### Post by Fred_E _krugar on 2008-06-14
I am sorry that didnt help but that was what I had to do to play Counter-Strike.

---

### Post by Cannonzim on 2008-06-14
its alright thanks for tryin though

anyone else have any ideas?

---

### Post by Fred_E _krugar on 2008-06-14
Well when you do get it running you can come buy and frag me a few times lol.

---

### Post by Cannonzim on 2008-06-15
anyone have any other suggestions?

---

### Post by connorh123 on 2008-07-07
> **Cannonzim said:**
> anyone have any other suggestions?

Well first of all, do you have the latest update of wine 1.0? Second, is it the freezing problems or keyboard problems. Because I had the keyboard problems but fixed it. Freezing problems I used OSS drivers instead of ALSA drivers. Of course that means that you can't hear the sound but for me, I'll do anything to get counter strike working fine. Try doing what I suggested and see what it does for you.

---

### Post by ooobuntooo on 2008-07-07
> **maka said:**
> Just updated to the latest wine...

been experiencing freezing in game recently.  play for a couple minutes den it freezes.

anyone share this problem?](*,)

I get this problem a lot!
I keep having to hard boot and it wrecks my computer!

---

### Post by connorh123 on 2008-07-07
Freezing? Or keyboard problems? I sometimes think that the sound may cause the lag. Because I disabled the ALSA drivers in winecfg and enabled OSS drivers. Again, this stops the sound. But I have been experiencing less freezing when I did this.

---

### Post by jualin on 2008-07-07
Maybe disabling Compiz? Just a shot in the dark.

---

### Post by connorh123 on 2008-07-10
Yeah. If you're having freezing problems, disabled ALSA in winecfg, and enable OSS. That should work

---

### Post by Akingboy on 2008-07-12
Got the same problem!
Wine 1.1.0
EDIT: Just updated to 1.1.1 but haven't tested crashing yet...

After playing like minute or two your screen freezes and must boot.
Tried disabling ALSA and enabling OSS but it just caused me to lose my sound completely and it didn't make the freezing go away.
Maybe lost sound because I don't have OSS even installed.


BTW what I heard is the safest way to boot if freezing happens is:
Hold alt+printscreen and type reisub
That boots safely your computer even if it locks up.

---

### Post by connorh123 on 2008-07-14
Yeah that's the whole point. Usually sound causes freezing or lagging, when you disable ALSA you lose sound, and enable OSS. Wow that's odd that you still can't play.

---

### Post by daniel7860 on 2008-07-19
i have ALSA disabled and i use OSS, 
i have sound and the game works perfectly for a few minutes then i freezes...... :( 
so i have to hold my poer button for 6secs. or sumthing, to shut down.. :(
it used to work good, without freezing.

---

### Post by connorh123 on 2008-07-21
Well thats the problem. Turn off you're sound from where ever you have it coming out of. Then try running it.

---

