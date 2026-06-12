---
title: "WINE Prefix Question"
date: 2008-08-11
forum: Wine
---

### Post by trixter76 on 2008-08-11
Hi all, I am currently trying to install the WoW expansion Wrath of the Lich King (beta) and I am having an issue.  I have found a fix for hte issue, but I am not quite linux-competent enough to understand the directions that were given here:  

> It's a problem with the HTML controls. 

[http://bugs.winehq.org/show_bug.cgi?id=13321](http://bugs.winehq.org/show_bug.cgi?id=13321) 

I got it to install by using ies4linux, shudder. [http://www.tatanka.com.br/ies4linux/page/Installation](http://www.tatanka.com.br/ies4linux/page/Installation) 

Run BC once using ies4's wineprefix to create the proper registry entries, then run the wrath installer using ies4's prefix, then move wrath to your regular wineprefix and create shortcuts as necessary. 

$ WINEPREFIX=~/.ies4linux/ie6 wow 
$ WINEPREFIX=~/.ies4linux/ie6 /path/to/Wrath/Installer 
$ mv ~/.ies4linux/ie6/drive_c/Program\ Files/Wrath ~/.wine/drive_c/Program Files/Wrath 

$ cat ~/bin/wrath 

#!/bin/bash
cd /home/<me>/.wine/drive_c/Program\ Files/Wrath\ of\ the\ Lich\ King\ Beta/
wine explorer /desktop=wow,1440x900 Launcher.exe "$@"&

I was able to get ies4linux installed, but I'm unsure what I am supposed to do when it comes to changing the prefix.  Is anyone well versed enough to understand this and dumb it down a little for me?  Thanks for any/all help.

---

### Post by kdorf on 2008-08-11
All you need to do to get wine to run in another prefix is prefix your command with:

env WINEPREFIX=/path/to/your/prefix

At the terminal, you can shorthand it by removing "env " from the front, but if you are running a BASH script it must be included.

---

### Post by trixter76 on 2008-08-11
Okay Cool!  Thanks for the help!  

If there is another prefix there already, will I need to delete/replace it with what I want or can I put more than one WINEPREFIX there?

---

### Post by kdorf on 2008-08-11
One prefix basically is like one installation of Windows. You have separate DLLs and overrides, and different registries. You can't have two prefixes in exactly the same directory, but you can have multiple prefixes under one directory. I have several in my ~/.wine directory instead of actually putting one in .wine.

For example, ~/.wine/War3, ~/.wine/Diablo2, ~/.wine/WoW, etc.

---

### Post by Boyohazard on 2008-08-21
Did you get it to work trixter76? I am having some problems as well.

When I run this command in the console
```
 WINEPREFIX=~/.ies4linux/ie6 ~/desktop/WotLK-Beta/Installer.exe 
```
I get a "No such file or directory error"

It's probably something really obvious but I can't see where I am going wrong. Can someone point me in the right direction please?

---

### Post by Boyohazard on 2008-08-21
I realise where I went wrong I missed out the **wine** command thus:

```
WINEPREFIX=~/.ies4linux/ie6 wine ~/desktop/WotLK-Beta/Installer.exe
```

---

### Post by lckeeper1 on 2008-09-02
Hey all,

Just a heads up. This is now fixed in wine 1.13 so no need for the ie6 prefix.

Also a quick question. I used the ie6 prefix earlier and installed into wine's drive_c. Now I'm trying to delete that installation, but can not find it anywhere, so I'm a bit lost. Doesn't show up under any search or anything. I don't want to lose 7gb of disk space for nothing.

---

