---
title: "Wine Help"
date: 2008-06-18
forum: Wine
---

### Post by HxC69 on 2008-06-18
I can install programs okay, but when i try to open them, it terminates right away, sometimes it will give me the alert, "There is a Problem with your memory"

Any help is appreciated.

---

### Post by VMC on 2008-06-18
> **HxC69 said:**
> I can install programs okay, but when i try to open them, it terminates right away, sometimes it will give me the alert, "There is a Problem with your memory"

Any help is appreciated.

Run the program from a Terminal and save the error output and post it back here again for us to read. I use to have a memory error problem, but a patch fixed it. Now with the newest Wine, everything works okay.

---

### Post by HxC69 on 2008-06-18
Since the Program terminates itself so fast, i couldn't copy the text, so i had to take a Screen Shot

[IMG]http://i29.tinypic.com/20thuyp.png[/IMG]

---

### Post by cogadh on 2008-06-18
The error message from the application is usually useless, what is useful is the information in the terminal. Not just any one error message in it, but all of the output. Since the app was still running when you took that screenshot, we can't see the full terminal output. Unfortunately, all the messages we can see are simple "fixme" messages, which are just developer notes and not really errors. They usually indicate some function that is incomplete or has not been implemented at all in Wine yet. Most applications run with Wine will encounter a few of them and will still run anyway.

Re-run the application from the terminal and let it finish erroring out, then copy the text from terminal into a post here.

BTW - What application are you trying to run? It might help to know that, since with that info we can offer some application-specific advice.

---

### Post by HxC69 on 2008-06-18
Okay, I Alt+F2, then i run it with the terminal, and it pops up with te program and the terminal with the fix mes, then it closed both terminal and program right after i start it.

And the program is: Ulead COOL 3D 3.5

---

### Post by HxC69 on 2008-06-18
bump

---

### Post by HxC69 on 2008-06-18
This is the only output i get.

```
fixme:win:EnumDisplayDevicesW ((null),0,0x33f220,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_Release (0x14a638) Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0x14a4b8 with type 1,WINED3DRTYPE_SURFACE
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:shdocvw:PersistStreamInit_InitNew (0x182f80)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x182f80)->(0)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x182f80)->(0)
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:shdocvw:WebBrowser_Stop (0x182f80)

```

---

### Post by cogadh on 2008-06-18
Don't use ALT+F2, open an actual terminal window then run the app, that way the terminal won't close when the app does. Also, you still haven't told us what you are trying to run.

---

### Post by HxC69 on 2008-06-18
Okay this is the only output i get

```
fixme:win:EnumDisplayDevicesW ((null),0,0x33f220,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_Release (0x14a640) Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0x14a4c0 with type 1,WINED3DRTYPE_SURFACE
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:shdocvw:PersistStreamInit_InitNew (0x182f88)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x182f88)->(0)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x182f88)->(0)
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:shdocvw:WebBrowser_Stop (0x182f88)

```

This is what im trying to run:
```
http://appdb.winehq.org/objectManager.php?sClass=application&iId=1705
```

---

### Post by cogadh on 2008-06-19
Its really odd that you don't get any kind of further error output when the app crashes. Wine should either be showing a whole bunch more errors or memory dump when an application does that. 

Well, based on the limited info in that AppDB entry, Cool3D requires Quicktime, which doesn't actually work in Wine, unless you have an old version of it (pre version 7, I believe). However, the Ulead site only says you need that if you want the output in Quicktime format, so I'm guessing that it still should run without it. Also, some of those errors would seem to indicate that the app is trying launch an internet browser. Have you installed the Wine Gecko engine yet? If not, just run this, then try Cool3d again:
```
wine iexplore http://www.winehq.org/
```
Follow the prompts and it will insstall the engine for you. When the install is complete, the WineHQ website will be displayed.

---

