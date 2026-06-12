---
title: "File or path not exists: &quot;/usr/lib/wine&quot;"
date: 2012-10-10
forum: Wine
---

### Post by manolomanolo on 2012-10-10
Hi to all.
I always get the error reported in the title of this thread, each time that I try and run a windows application through Wine.
Last time I got it, it was when installing FreeGate:
> 
Error while loading application settings by key: 'WineLibs'. File or path not exists: "/usr/lib/wine"
Please, go to q4wine options dialog and set it.

After ignoring the error message, the application installation failed with the error shown in the attached picture.

Any clue?
Thanks.
Regards.

---

### Post by SuDuMa on 2012-10-10
If it were me i might would try to reinstall wine. If that fails check the configs for the program or try to debug it. Hope that helps at least a little i could be completely off as i have never installed the program you mentioned.

[http://www.winehq.org/download/](http://www.winehq.org/download/)

---

### Post by manolomanolo on 2012-10-11
Hi SuDuMa,
thanks for your reply. Also, thanks for your suggestion.
However, let me clarify 2 important points:
[LIST=1]
[*]the problem persists no matter the software I try to install: each windows software causes that error
[*]unfortunately the "windows style" solutions (uninstall/reinstall or close/reopen and similar) have been already tried both before writing this post and also after just following your suggestion
[/LIST]

That's frustrating.
Any other suggestion, please?
Thank you so much.
Regards.

---

### Post by manolomanolo on 2012-10-11
I've been asking on the Wine IRC channel. Someone (frostwork) said I should add some path to some wine libs but that kind person left the channel before me (nu_dorm) understand what to do.

That's our conversation on the channel:
```
nu_dorm	Hi to all, I've the problem reported here: http://ubuntuforums.org/showthread.php?p=12290306 any suggestion, please? Thanks
	frostwork	I'd go to q4wine options dialog and set it?
	frostwork	you apparently use q4wine and this needs to be configured so it can find its wine libraries
	frostwork	maybe .../lib64/...
	nu_dorm	frostwork: thanks for your reply, I've been there but not sure about what to put into the corresponding field
	nu_dorm	frostwork: could you give me more detail, please?
	frostwork	nu_dorm, check if you have a /usr/lib32/wine/ directory. if so use that in the field
	frostwork	the path shouldn't be hardcoded at all but that not your fault oc :}
	nu_dorm	frostwork: I don't understand
	frostwork	nu_dorm, you're using the gui q4wine, right?
	nu_dorm	frostwork: yes
	frostwork	nu_dorm, so checked your options there?
	frostwork	nu_dorm, assuming your on a 64bit system set Libs (32bit) to /usr/lib32/wine/ and Libs (64bit) to /usr/lib64/wine/
	EndU	hi
	frostwork	if both paths are valid for your system thatshould be everything you have to do, but I don't use ubuntu and or q4wine, nu_dorm
```
After that, I could not find frost anymore on the channel. However, hope someone could help me understanding what to set and where.
Last but not the least, that's what I found on my computer about wine:
```
**sudo find / -iname wine**
    /proc/sys/fs/binfmt_misc/wine
    /home/superman/.local/share/applications/wine
    /home/superman/.PlayOnLinux/wine
    /home/superman/.PlayOnLinux/wine/linux-x86/1.3.6/lib/wine
    /home/superman/.PlayOnLinux/wine/linux-x86/1.3.6/bin/wine
    /home/superman/.PlayOnLinux/wine/linux-x86/1.3.6/share/wine
    /usr/lib/i386-linux-gnu/wine
    /usr/bin/wine
    /usr/include/wine
    /usr/share/doc/wine
    /usr/share/binfmts/wine
    /usr/share/wine
    /var/lib/binfmts/wine

```

Also, please find in attachment the pictures of the window that opens after clicking "OK" on the previous window (the one with the error message).

What should I do now?
Thanks,
regards.

---

### Post by Shtonchjo on 2013-05-04
I looked into the files to be installed when installing wine 1.3 (they can be seen in the attributes, when using Synaptic). There appears this "usr/lib/mime" in the list, which I tried, and it worked for me.
Ihope it can help.

> **manolomanolo said:**
> Hi to all.
I always get the error reported in the title of this thread, each time that I try and run a windows application through Wine.
Last time I got it, it was when installing FreeGate:


After ignoring the error message, the application installation failed with the error shown in the attached picture.

Any clue?
Thanks.
Regards.

---

### Post by xp15 on 2013-09-17
Found the solution:

For 32 bit system:
/usr/lib/i386-linux-gnu/wine

For 64 bit systems:
/usr/lib/x86_64-linux-gnu/wine

&#1513;&#1502;&#1495;&#1514;&#1497; &#1500;&#1506;&#1494;&#1493;&#1512; :D
(In case that I put a mistake, navigate to the folder, enter her Properties, copy her path to the Q4wine, and just add "/wine" at the end [no ""]. click next)
if you can't and no success, I will try to help:
[EMAIL="yinonzadok@gmail.com"]yinonzadok@gmail.com[/EMAIL]

Got it! If you copy the path by Double-Click, a space is copied too before the path, so it is " /usr..." instaed "/usr...". Just delete this space or copy by Marking the path (Holding a Click and Dargging while you still Hold until you mark all of what you want).
Remember, you need it WITHOUT the SPACE. YOU NEED [COLOR=#008000]"/USR..."[/COLOR] and NO [COLOR=#ff0000]" /usr"[/COLOR].

Source:
[http://ubuntuforums.org/showthread.php?t=1973282](http://ubuntuforums.org/showthread.php?t=1973282)
Thank you "sdd" !

---

