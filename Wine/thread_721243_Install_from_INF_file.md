---
title: "Install from INF file"
date: 2008-03-11
forum: Wine
---

### Post by SuperBo on 2008-03-11
How can I install a program from a INF file. It's a program, not driver.
Please help me, thank you.
In window:
```
You can manually install these nLite addons on your current PC without the need to integrate them:
1- Extract the files from the *.rar archive
2- Right click on the *.inf
3- Choose Install from the context menu
4- Pay attention to the message boxes
5- Enjoy
```

---

### Post by jken146 on 2008-03-11
That is a Windows way of installing software.  I'm afraid that won't work in Linux.

---

### Post by SuperBo on 2008-03-11
I want to install it on wine. Please help me.

---

### Post by jken146 on 2008-03-11
I've no idea how to do it -- sorry.  What are you trying to install, anyway?  Perhaps I can suggest a native linux app that does the same thing.

---

### Post by SuperBo on 2008-03-22
I want to install Universal Share Downloader to download from share website.
```
http://www.wincert.net/forum/index.php?showtopic=1065
```

---

### Post by hasinasi on 2009-03-23
I was able to install the huffyuv codec in wine that is usually installed via .inf execution. For this codec, only one dll is installed. I simply added this dll to the system32 directory. 
Then, I looked into the inf file (plain text). It obviously contained several registry keys. I chose two of these keys that looked most important and added them to the registry manually (I ignored "uninstall" related keys). The codec was then recognized by VirtualDub as usual! 
Send me a message if you need more detailed instructions.

---

### Post by hasinasi on 2009-03-23
I just found another hint how to do it. It looks like a more complete way of doing it. I haven't tried it, though. This is the link:[http://nerds-central.blogspot.com/2007/10/huffyuv-codec-or-any-other-under-wine.html]("http://nerds-central.blogspot.com/2007/10/huffyuv-codec-or-any-other-under-wine.html").

In case this page won't exist in the future, let me just repeat the most important command here. You just have to execute the following. ```
rundll32 setupapi.dll,InstallHinfSection DefaultInstall 128 ./huffyuv.inf
```
(Assuming you are in the directory where the inf file, in this case huffyuv.inf, is sitting.)

---

### Post by NightMKoder on 2009-03-23
> **SuperBo said:**
> How can I install a program from a INF file. It's a program, not driver.
Please help me, thank you.
In window:
```
You can manually install these nLite addons on your current PC without the need to integrate them:
1- Extract the files from the *.rar archive
2- Right click on the *.inf
3- Choose Install from the context menu
4- Pay attention to the message boxes
5- Enjoy
```

What you found was an nLite addon that installs a specific application. This isn't the application itself (nLite is used to pre-build windows so that you have certain applications when you install it).

The actual application is found in the first post of the thread you link to: [http://forum.ru-board.com/topic.cgi?forum=5&topic=26900&glp](http://forum.ru-board.com/topic.cgi?forum=5&topic=26900&glp) .

Now, since I know a little russian, this gets you to [http://forum.ru-board.com/topic.cgi?forum=5&topic=26900&start=0&limit=1&m=2#1](http://forum.ru-board.com/topic.cgi?forum=5&topic=26900&start=0&limit=1&m=2#1) . I believe you need the link that says "USDownloader + &#1074;&#1089;&#1077; &#1087;&#1083;&#1072;&#1075;&#1080; + &#1103;&#1079;&#1099;&#1082;&#1080; (link2, link3, link4)" which says "USDownloader + all plugins + languages".

See if this helps.

---

