---
title: "Wine menus looking weird (like winecfg)"
date: 2008-03-23
forum: Wine
---

### Post by Morph-------------- on 2008-03-23
Hello,

I've just installed wine to start playing SA-MP (GTA:SA). But i've a weird problem now. 
This is the guide i've followed:
[http://forum.sa-mp.com/index.php?topic=16885.0](http://forum.sa-mp.com/index.php?topic=16885.0)

So basicly the only change that i've made is this:

```
Click on the "Libraries" tab at the top of the window, then in the box under "New override for library:" put "d3d9.dll", ensure that the box below now contains "d3d9 (native, builtin)", if it says d3d9 followed by something other than that, select it, hit the "Edit" button, select "Native then Builtin", and press OK.
```

But now my winecfg (and the sa-mp menu and basicly everything) looks like this: 
[IMG]http://img374.imageshack.us/img374/9281/screenshotfv6.png[/IMG]

I've already tried 
```
sudo aptitude remove --purge wine
sudo aptitude install wine
```

Does anyone have a idea?

Wine version: wine-0.9.46
PS: The winecfg have worked but doesn't anymore, the only game i've installed is GTA:SA+wine and i 
had the d3d9.dll library overide (native, builtin) but i don't know if it still exists after the purge.
winecfg gives no output in the terminal

---

### Post by happyhamster on 2008-03-23
You'll probably have to get rid of the .wine folder to get things to work again (which means you'll have to re-install GTA). Go to Places-->Home Folder and press ctrl-h to be able to see hidden files. Delete or move the .wine folder. Then run winecfg to create a fresh .wine dir.

BTW: setting d3d9.dll to native usually isn't successful. If you want to try, a safer way is doing it from a terminal like this:

WINEDLLOVERRIDES="d3d9=n" wine program.exe

Advantage is that it's only temporary, and you'll be able to see useful debugging output. To get rid of debug-messages append:

WINEDEBUG=-all 

For more info, see:
[http://www.winehq.org/site/docs/wine...de/x543#AEN877](http://www.winehq.org/site/docs/wine...de/x543#AEN877)

[http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332)

---

### Post by Morph-------------- on 2008-03-23
Really thanks for the answer. I can't try it now sine i'm not able to at the moment but i'll try it tommorow and i'll let you know if it worked.

Thanks! Morph

---

### Post by Morph-------------- on 2008-03-24
Thanks, i got the window properly working again!

---

