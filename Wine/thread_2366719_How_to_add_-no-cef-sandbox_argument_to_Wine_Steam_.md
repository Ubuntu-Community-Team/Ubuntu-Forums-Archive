---
title: "How to add -no-cef-sandbox argument to Wine Steam startup?"
date: 2017-07-21
forum: Wine
---

### Post by noxarcz on 2017-07-21
[B]_Solved! Solution at the bottom of this post!_
[/B]
As you propably know, wine Steam cannot display the store page since the chrome extension thing, the workaround is to apply the argument **-no-cef-sandbox** to Steam.exe

This can easily be done if you use PlayOnLinux, simply adding that line into startup options, i don't use it because in my experience manually tweaked wine works better.
I was looking for a way to apply this argument to the exe without PlayOnLinux, but i couldn't find anything on the internet.

If you could guide me how to permanently add this argument to the Steam.exe file i would be grateful.
Sorry if this a repost but despite trying to find it here on Ubuntu forums, i couldn't.
[B][U]
SOLUTION:[/U]
[/B]First, install Windows version of Steam with wine
Exit Steam, make sure its process is terminated
Then go into your **home/username/** folder and locate folder called **.local **If you can't see it, press **CTRL +H** (shows hidden files)
Go into **.local/share/applications/wine/Programs/Steam**
Open file **Steam.desktop** with a text editor (mousepad,...)
The third line should say Exec=env WINEPREFIX=....
add the argument **-no-cef-sandbo**x at the end of the line
Start Wine Steam
Now your store page should be fully functional!

---

### Post by sccman on 2017-07-23
I'm running Lubuntu, but I'd imagine you could search for the shortcut in Xubuntu's GUI, and right click on it for Properties. Somewhere in Properties you should find a textbox that begins with [I]env WINEPREFIX=...

[/I]You can add **-no-cef-sandbox** to the end of it and it should work fine.

---

### Post by noxarcz on 2017-08-04
Holy bananas, it works!

Tbh i almost forgot about this thread, expected it to be burried under other posts without a reply!
It just so happened that i was deleting non functional shortcuts, so i knew exactly which file you meant, many thanks! :D

---

