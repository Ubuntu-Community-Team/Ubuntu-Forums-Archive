---
title: "New Star Soccer 3"
date: 2008-06-19
forum: Wine
---

### Post by i_like_salmon on 2008-06-19
Hey I was wondering if anyone has an idea on this one.

I've been trying for the last week or so to get New Star Soccer 3 [URL="http://www.newstarsoccer.com/"] to run through Wine.

I can run the program until I get to the actual match engine where the screen goes completely black and eventually "crumbles" back to the desktop. 
And its recently giving a "Wrong Stream Access" error on occasion (or similar).


I'm not sure how you go about running it through the terminal, would this help determine the problem? 

Thanks v much!

---

### Post by cogadh on 2008-06-19
Yes, it would help a lot. Run it like this:
```
cd ~/.wine/drive_c/Program\ Files/<NS Soccer directory>
wine <NS Soccer executable>.exe
```

---

### Post by i_like_salmon on 2008-06-19
Ok using your code I get the following:

```
 preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
wine: could not load L"C:\\windows\\system32\\NewStarSoccer3.exe": Module not found 
```

and it will not start at all.

When I run it from the normal desktop shortcut it runs fine until I get the following error before entering the match engine: "Invalid Stream Handle".

---

### Post by cogadh on 2008-06-19
First. get rid of those preloader erors:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

Second, it looks like you had the path or file name wrong when you tried to run the game:
```
wine: could not load L"C:\\windows\\system32\\NewStarSoccer3.exe": Module not found
```
Wine usually produces that error when you try to run an application from the wrong directory or enter the executable name incorrectly.

---

### Post by i_like_salmon on 2008-06-19
Thanks! 

Ok I've sorted the preloads and found the correct path. I run the game, its all fine then when I go to the match engine it crashes etc... the terminal gives this: 

```

fixme:process:SetProcessShutdownParameters (00000100, 00000001): partial stub.
fixme:reg:RegSetKeySecurity :(0x7c,4,0x389fd8): stub
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x337733, 0x33772c): stub
fixme:urlmon:ObtainUserAgentString (0, 0x20a870, 0x33772c): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:EnumDisplayDevicesW ((null),0,0x33f940,0x00000000), stub!


```

---

### Post by cogadh on 2008-06-19
Well, you might be out of luck with this one. The "fixme" errors are developer notes about incomplete or unimplemented functions in Wine. Sometimes you can work around them and pretty much all applications run with Wine will encounter a few of them, but you can't actually do anything to fix them. Most of the ones you got also indicate they are "stubs", which is essentially just a placeholder for a completely missing function. If those functions are required for the game to work, it will never work with this version of Wine.

EDIT - I probably should have checked this from the start, but there is an AppDB entry for the game which gives it a "Garbage" rating, meaning it doesn't work at all in Wine:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10222](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10222)

---

### Post by i_like_salmon on 2008-06-20
Thanks very much for your help, that site looks pretty useful for future ref.

---

