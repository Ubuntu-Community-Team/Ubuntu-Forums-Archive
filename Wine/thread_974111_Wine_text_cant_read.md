---
title: "Wine text cant read"
date: 2008-11-07
forum: Wine
---

### Post by dhtj on 2008-11-07
Hi all!
I installed wine 4 days ago and I play CS 1.6 without problems:)
But my wine menu, and menus of progs mounted with wine is wooking
like this:
[IMG]http://store.picbg.net/pubpic/B4/A8/2dfa713a58dab4a8.png[/IMG]

---

### Post by bukzor on 2008-11-08
Mine looks exactly the same...
--Buck

---

### Post by bhall430 on 2008-11-15
exact same problem as well

---

### Post by mister_k81 on 2008-11-15
Yup, same issue as well... 

My only solution is to go into the "Configure Wine" (winecfg) options menu, click on the Graphics tab and turn up the screen resolution dpi slider. Anything under 150dpi for me looks garbled and unreadable. Also, I should say that I'm using Ibex...I never used to have this problem with Hardy. ](*,)

---

### Post by mister_k81 on 2008-11-15
Ok, I investigated this a bit more, and Wine seems to have a problem rendering the tahoma font properly. 

I don't know of any real solutions to fix this, but what I did instead was replace the "tahoma.ttf" and "tahomabd.tff" files (located in: "*/usr/share/wine/fonts*") with "DejaVuSans.ttf" and "DejaVuSans-Bold.ttf" that I copied and pasted from: */usr/share/fonts/truetype/ttf-dejavu*. I also had to rename: DejaVuSans.ttf and DejaVuSans-Bold.ttf to: tahoma.ttf and tahomabd.ttf. 

It's a cheap trick... but it works anyway. \\:D/

---

### Post by Chronos6 on 2008-11-16
This helped me.
6.19. Using wine over remote X11 sessions and No text or damaged text displayed

Please make sure not have added any fonts to wine. Font conflicts can sometimes cause a similar issue. If a fresh wine prefix.(A copy of wine that nothing has been done to yet) Is having this problem. Try setting following in registry

[HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"ClientSideWithRender"="N"

Place above in text file and it can be inserted into registry by "regedit settings.txt".

This was report as been required of OS X on the 1 Dec 2007. This may change. Please apply only as required.

---

### Post by Mike08857 on 2008-11-16
I also am having the same problem with wine & codewavers.

I have tried everything and still have the same problem.

:confused:

---

### Post by mister_k81 on 2008-11-16
> **Chronos6 said:**
> This helped me.
6.19. Using wine over remote X11 sessions and No text or damaged text displayed

Please make sure not have added any fonts to wine. Font conflicts can sometimes cause a similar issue. If a fresh wine prefix.(A copy of wine that nothing has been done to yet) Is having this problem. Try setting following in registry

[HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"ClientSideWithRender"="N"

Place above in text file and it can be inserted into registry by "regedit settings.txt".

This was report as been required of OS X on the 1 Dec 2007. This may change. Please apply only as required.


I reverted all the fonts I changed back to their defaults and tried this. It worked! Thanks.

---

### Post by outerspacerace on 2008-11-16
I can't read enough to try the above suggestions, my text is garbled/flickers on for a split second only when I click it.

Is there anything else I can try?

---

### Post by outerspacerace on 2008-11-16
P.S. I have a fresh wine install on AMD 64 bit Intrepid.

---

### Post by mplexus on 2008-11-18
> **outerspacerace said:**
> I can't read enough to try the above suggestions, my text is garbled/flickers on for a split second only when I click it.

Is there anything else I can try?


Same problem here.

You can try to edit user.reg located in wine directory (e.g. ~/.wine/user.reg)

In my user.reg I found these lines:

```

[Software\\Wine\\X11 Driver] 1210627404
"Desktop"="800x600"
"DXGrab"="Y"
"Managed"="Y"

```

and added the above line that Chronos6 pointed, resulting in:

```

[Software\\Wine\\X11 Driver] 1210627404
"Desktop"="800x600"
"DXGrab"="Y"
"Managed"="Y"
"ClientSideWithRender"="N"

```

I suppose if no such entry exists in your user.reg file you can always add it..

Now most fonts are readable. Only a small number of fonts remains absent from some buttons - i'll be working on that too..

NEW EDIT: i copied some true type fonts (/usr/share/fonts/truetype/xxx/yyy.ttf) into ~/.wine/drive_c/windows/Fonts and now all fonts (including non english) are visible. cool 8)

(by the way, AMD64 Intrepid as well)

---

### Post by outerspacerace on 2008-11-18
I remembered doing just that under Hardy before I saw your post, I added in the microsoft fonts, though I hadn't tried it out yet under Intrepid so cheers for the tip ;)

It's probably a basic WIne thing in a FAQ somewhere I haven't checked out maybe?

I know by default there's no fonts in the folder...

---

### Post by p2k on 2008-11-21
> **mplexus said:**
> Same problem here.

You can try to edit user.reg located in wine directory (e.g. ~/.wine/user.reg)

In my user.reg I found these lines:

```

[Software\\Wine\\X11 Driver] 1210627404
"Desktop"="800x600"
"DXGrab"="Y"
"Managed"="Y"

```

and added the above line that Chronos6 pointed, resulting in:

```

[Software\\Wine\\X11 Driver] 1210627404
"Desktop"="800x600"
"DXGrab"="Y"
"Managed"="Y"
"ClientSideWithRender"="N"

```

I suppose if no such entry exists in your user.reg file you can always add it..

Now most fonts are readable. Only a small number of fonts remains absent from some buttons - i'll be working on that too..

NEW EDIT: i copied some true type fonts (/usr/share/fonts/truetype/xxx/yyy.ttf) into ~/.wine/drive_c/windows/Fonts and now all fonts (including non english) are visible. cool 8)

(by the way, AMD64 Intrepid as well)

I had no [FONT="Courier New"][Software\\Wine\\X11 Driver][/FONT] section in my [FONT="Courier New"]user.reg[/FONT] file, adding the following lines at the end of the file worked for me on Ubuntu 8.10 Intrepid Ibex Intel 32bit:
```

[Software\\Wine\\X11 Driver] 1210627404
"ClientSideWithRender"="N"
```

Thanks!

---

### Post by barmaley on 2008-11-24
Thanks, people
Adding this row: "ClientSideWithRender"="N"

to the .wine/user.reg solved the problem for me.
Thanks a lot.

---

### Post by Thomas1477 on 2008-11-26
How do I get to.wine/user.reg to make the change?

---

### Post by MarimaX on 2008-11-27
Let me know if you get an answer

---

### Post by mister_k81 on 2008-11-28
> **Thomas1477 said:**
> How do I get to.wine/user.reg to make the change?

-Go into your Home Folder.
-Click 'View' in the top menu. 
-Checkmark the 'View Hidden Files' box, or just press 'Ctrl + H'. 
-Scroll down and look for the .wine folder.

---

### Post by Thomas1477 on 2008-11-28
Think you very very much.

---

### Post by toneman77 on 2008-12-06
I had the same problem and none of the above solutions worked for me.
What i had to do was:

edit
~/.google/picasa/3.0/user.reg
and add the apropriate line
```
"ClientSideWithRender"="N"
```
after that, everything was fine.

---

### Post by stinger30au on 2008-12-06
> **dhtj said:**
> Hi all!
I installed wine 4 days ago and I play CS 1.6 without problems:)
But my wine menu, and menus of progs mounted with wine is wooking
like this:
[IMG]http://store.picbg.net/pubpic/B4/A8/2dfa713a58dab4a8.png[/IMG]

its caused by the video driver.

i have the same issue in 8.10 wth my nvidia card.

---

### Post by dwasifar on 2008-12-09
I had a different problem: no fonts showing in Wine at all.  Blank tabs, blank buttons.  The only things showing were the hotkey underlines, with no letters over them.

But "ClientSideWithRender" = "N" fixed that too.

---

### Post by striants on 2009-01-11
Hello from me too. I had the exact same font problem and I followed the proposed solution.
The problem now is that the toolbar icons in Thunderbird portable are not visible (see attached screenshot)

any ideas on how to solve this?

---

### Post by undoIT on 2009-01-12
Imagine my surprise this morning at 6:30 AM when I opened my stock trading program Quotetracker in Wine and everything looked like it was in Arabic. Have I been hacked!!!?

Well, actually everything was in Tibetan, just the font is set too small to recognize it right away in Quotetracker. Over the weekend I had installed a Tibetan publishing tool called Pechamaker to attempt to send some Tibetan texts I had typed up years ago to somebody who had requested them. But I realized I wouldn't be able to print to PDF so I ended up using the Windows install in Virtualbox.

Deleting the Tibetan fonts that had been installed to this folder worked for me:

/.wine/drive_c/windows/Fonts

I guess that had gotten set as the system font.

---

### Post by zieglerj on 2009-01-16
I tried all of these fixes plus completely removing wine and all of its folders multiple times and I'm still having this problem. 
The folders I deleted when removing and reinstalling wine are: 
./usr/share/wine
./root/.wine
~/.wine
Are there any that I missed? 
Also my user file didn't look the way described the the messages at the top of the previous page either. I also tried just changing it to that but to no avail. 
Please help!
Thanks
The roaming gnome

---

### Post by hurtstotalktoyou on 2009-03-21
> **barmaley said:**
> Thanks, people
Adding this row: "ClientSideWithRender"="N"

to the .wine/user.reg solved the problem for me.
Thanks a lot.

Even if I change it as root (gksu gedit .wine/user.reg), the file just reverts back to its original form as soon as I run the wine version of firefox (and presumably any other wine application).  Any idea how to make the change stick?

---

