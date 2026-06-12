---
title: "Problem with guild wars"
date: 2007-11-06
forum: Wine
---

### Post by giggity02 on 2007-11-06
Does anyone know how to fix this (please look at screenshot) i get this message when i open up GW:confused:

---

### Post by giggity02 on 2007-11-06
any ideas?

---

### Post by dorath on 2007-11-07
Try opening a terminal and entering:```
wineserver -k
```Then see if Guild Wars will start.  Please let us know either way. :)

---

### Post by Entity` on 2008-02-20
My problem is this:

[IMG]http://ubuntuforums.org/g/images/202730/large/1_Screenshot.png[/IMG]

Most of the text is there, but you can see other problems too.

[IMG]http://ubuntuforums.org/g/images/202730/large/1_Screenshot1.png[/IMG]

There's a turquoise line on the top.

[IMG]http://ubuntuforums.org/g/images/202730/large/1_Screenshot2.png[/IMG]

...yea that's a problem there...

[IMG]http://ubuntuforums.org/g/images/202730/large/1_Screenshot3.png[/IMG]

...Look!  No text!

It runs at a very nice framerate and all, but there is a lot more for me to do now.  Sound also works just fine.

System Configuration:

Intel P4 1.8GHz cpu
ATI Radeon 9500 gpu
512Mb of ram (normally 1GB but my brother borrowed half of it, I should be getting it back soon)
Ubuntu 7.10 with wine 0.9.46

Can someone please help me?

---

### Post by Ferrat on 2008-02-21
It's due to your ATi card, there is a problem with Z-lenght in the fglrx drivers that due to a major fix in wine 0.9.45 I think it was, broke GW for ATi cards.. 

You can try editing regedit, it's not really a nice work around but worked for me when I played GW on my old ATi card
HKEY>>Software>>Wine>>Direct3D
DisabledExtensions = GL_ARB_draw_buffers

this should help with the 3D models showing, altho the text will prolly still be weird.

or you can revert back to wine 0.9.44, I think that's the version that works good with ATi cards

---

### Post by Entity` on 2008-02-21
Thank you for the help.  I was thinking it was due to my old ATI card, but its all I have right now.  I really like ATI, but for my next big upgrade, I might just go with an nVidia card.  Who knows?

---

### Post by Entity` on 2008-02-25
I finally got my ram back, so now im back on linux again.  However, I cant find the file or directory that the registry value is located in.  Yea, im an idiot when it comes to even simple programming, but im smart enough to ask for help when I need it before I end up breaking something.

---

