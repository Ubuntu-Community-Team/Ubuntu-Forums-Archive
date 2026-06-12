---
title: "Problems installing Steam on Wine"
date: 2012-01-20
forum: Wine
---

### Post by Darkness Des on 2012-01-20
So recently I got the urge to play my beloved Steam games again, and saw that my favorite (Team Fortress 2) had platinum level compatibility with Wine. So, I tried installing Steam with winetricks. After going through the usual install stuff, it said that everything worked perfectly. So when Steam ran, it updated and when it finally tried to run I got:

"Fatal Error: VGUI_Setup failed"

Does anybody know a fix for this?

---

### Post by ubudog on 2012-01-20
*Thread moved to Gaming & Leisure.*

---

### Post by ergo-proxy on 2012-01-23
Check installation steps provided on WineHQ.

---

### Post by rosshadden on 2012-02-01
I am getting this problem, too.  I have tried using both Wine and PlayOnLinux (which of course just uses wine).

I have tried on multiple versions of Wine, yet every time I launch Steam I receive this error.

Were you able to resolve your problem, and if so can you write about how?  I have perused the WineHQ instructions and followed verbatim.

---

### Post by Darkness Des on 2012-02-02
ergo-proxy: I did do that. It's the first thing I did before coming here and applied every possible fix.

rosshadden: The short answer is that I did indeed fix it. The long answer is all of the steps below, so bear with me.

At first, I switched to OpenSUSE due to a family member's persuasion and alleged advantages over Ubuntu it had for laptops.

Just for the record, it has none - Ubuntu wins out in my opinion with better dual monitor support. Anyways, back to the point.

I install Wine and Steam on there, and had some connection errors. I deleted the ClientRegistry.blob file and that resolved everything, but no VGUI errors.

Upon returning to Ubuntu after 18 hours, I installed Wine and Steam once more. Went off without a hitch. Now, here's what I noticed and may be of note to you:

Never once did I have an GTK3 libraries in either installation. OpenSUSE came with KDE by default, and since I loved using KDE on the install before that, I just went straight to Kubuntu instead of installing vanilla and then KDE from there. Everything worked out perfectly. To my best guess, it has to do with GTK3 libraries being...y'know...generally unaccepted by everything. I imagine Wine really hasn't had time to create a specialized compatibility layer to render in GTK3.

Given in my first install GTK3/Gnome Shell/Unity was installed first, everything believed it to be the default. To the best of my knowledge, this cannot be changed thoroughly and everything will still believe it to be your current desktop environment due to poor programming. Wine, "picking up" on this, will try to translate to GTK, which naturally doesn't do it's job very well. 

I'm imagining that you either did what I did and installed KDE afterwards or never did whatsoever and are just running Unity or the new Gnome Shell. 

You may private message me or continue the conversation in this thread, and I will help you to the best of my ability, if you would like.

---

### Post by winterhawk787 on 2012-07-04
I've just recently joined after a new journey to Ubuntu 12.04. I'm still fairly new; however, I've implemented a number of fixes for some issues I've run into. This was one of the more daunting ones.

After trying a number of fixes in deleting the old vgui_s file and ClientRegistry.blob, nothing seemed to work. But I think I found another solution that may work if you are running optimus.

I got a bit excited, so forgive me if the format isn't quite right here. I wanted to post a potential fix for this problem. Are you running Optimus? Basically, it's where you have an integrated graphics card and an nVidia dedicated card. To get this to work properly, you have to use something called bumblebee. This solved the problem for me.

First, install bumblebee: [https://wiki.archlinux.org/index.php/Bumblebee](https://wiki.archlinux.org/index.php/Bumblebee)

Then, in your terminal, change directories to where your Steam.exe file is. This will depend on how you're running WINE (as in, what version of Windows that WINE is emulating).

Finally, type the following in your terminal: ```
optirun wine Steam.exe
```I did this, and it solved the problem for me. I sincerely hope this helps, and I'm sorry for the shaky introduction!

---

### Post by ergo-proxy on 2012-07-05
> **Darkness Des said:**
> So recently I got the urge to play my beloved Steam games again, and saw that my favorite (Team Fortress 2) had platinum level compatibility with Wine. So, I tried installing Steam with winetricks. After going through the usual install stuff, it said that everything worked perfectly. So when Steam ran, it updated and when it finally tried to run I got:
 
"Fatal Error: VGUI_Setup failed"
 
Does anybody know a fix for this?
 
Create a new wineprefix and try installing Steam using instructions provided in winehq. Winetricks Steam version might be outdated.

---

### Post by pumrel on 2012-07-09
I had the same problem and it seems I found a fix.
First I downloded **glu32.dll** and **opengl32.dll** from this website [http://www.dll-files.com](http://www.dll-files.com) and I put them in the install dir of steam. I used the winehq howto so mine was

```
/home/petr/.local/share/wineprefixes/steam/drive_c/Program Files/Steam/
```

Then you have to run *wine configuration*. There open the *libraries tab*. 
Enter **glu32** in the box *New override for library. *Click [I]Add.
[/I]Repeat for **open32.dll**

Report ;)

---

### Post by rafaelpagliuca on 2013-01-02
Thanks, @pumrel. The opengl32.dll and glu32.dll fix worked for me.

But there's a typo in your instructions. In the end of the message, **open32.dll** should be replaced with **opengl32.dll**.

Also, I typed **glu32.dll** instead of simply **glu32** in the *New override for library* text box, but I'm not sure if that matters.

---

### Post by pumrel on 2013-01-02
I am sorry for the typo but am glad I could help. I can't test the games though as I have a really old graphics card that sucks :(

---

