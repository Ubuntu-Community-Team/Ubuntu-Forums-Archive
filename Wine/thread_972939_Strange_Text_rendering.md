---
title: "Strange Text rendering"
date: 2008-11-06
forum: Wine
---

### Post by solitaire on 2008-11-06
I've just installed Wine in 8.10. 

All the text looks like it's been scribbled out in the Wine Menus!
Also programs within Wine have the same issue.
(See Screen shots)

Also Menus are blank untill you roll the mouse over them.

I'm Running the latest Nvidia 96.##.09 drivers.

Can anyone help?

---

### Post by asdfoo on 2008-11-06
> **solitaire said:**
> I've just installed Wine in 8.10. 

All the text looks like it's been scribbled out in the Wine Menus!
Also programs within Wine have the same issue.
(See Screen shots)

Also Menus are blank untill you roll the mouse over them.

I'm Running the latest Nvidia 96.##.09 drivers.

Can anyone help?

have you tried disabling compiz?

---

### Post by solitaire on 2008-11-06
compiz is not installed. 
my Laptop graphics card only has 16Mb so Compiz does not work.

---

### Post by DJ_Peng on 2008-11-06
You may want to try the advise in this entry on the [WINE FAQ]("http://wiki.winehq.org/FAQ#head-dec980f6deabdb11b789c981bf49e10e70929eaf"). Don't feel bad if you missed that info, I started a topic about missing text the other day and it took until someone posted a link to it on a Nvidia bug before I saw it. And I'd checked the WINE FAQ several times before starting my topic.

---

### Post by prshah on 2008-11-06
> **solitaire said:**
> 
All the text looks like it's been scribbled out in the Wine Menus!
Also programs within Wine have the same issue.


Looks to me like a fonts issue; can you try (re)installing the core fonts? Open a terminal (Applications-Accessories-Terminal) and give the command ```
sudo apt-get install --reinstall msttcorefonts
``` Make sure wine is not running first!

Failing that, try [adding the wine repositories]("http://www.winehq.org/site/download-deb") to get the latest WINE. While we're at that, what version of WINE are you using?```
wine --version
```

---

### Post by solitaire on 2008-11-06
I've reinstalled 'msttcorefonts' and this made no difference
I'm running wine-1.0.1

I'm just going to get the latest version.

*Update*

Updated to Wine 1.1.7

Still having the same issues.. :(

---

### Post by prshah on 2008-11-06
> **solitaire said:**
> Still having the same issues.. :(

Did you see DJ_Peng's post earlier? It links to the WINE FAQ which suggests a registry setting to change.. worth a try.

---

### Post by solitaire on 2008-11-06
Yeh! just tried the registry fix.

It Worked :D:D

---

### Post by DJ_Peng on 2008-11-06
Glad that was able to help. I was tearing out my hair until I found that solution.

---

### Post by Sugi on 2008-11-06
Wow, that is so odd.  It looks like you took it into Gimp (or Photoshop for Windows Users).

Sugi

---

### Post by cjchand on 2008-11-09
Just wanted to confirm that the same works here, both in Wine and Crossover Office. 

Just to clarify the steps:
1) Open the following file with gedit (or the editor of your choosing):
```
/home/<username>/.wine/user.reg
``` (Note that if you don't see ".wine" in Nautilus, hit Ctrl-H to show hidden folders)

2) Go to the bottom of the file
3) Ensuring there is a blank line after the last entry, add this on a new line:
```
[Software\\Wine\\X11 Driver] 1226210902
"ClientSideWithRender"="N"
```
4) Close and save the file
5) Enjoy the ability to actually friggin' see what the text is in Menus and Install dialogs ;)

The steps are the same in Crossover Office, except the path the the file is:
```
/home/<username>/.cxoffice/user/<bottlename>/user.reg
```

You *might* be able to do that to the user.reg in /default and have it work, but I suspect it is bottle-specific.

Hope that helps!

Cheers,
CJC

---

### Post by DJ_Peng on 2008-11-09
That's the ticket. 8-)

---

### Post by K.Mandla on 2008-11-12
Thanks, this worked for me too.

---

### Post by yugo on 2008-11-19
fonts are now ok for me but some elements are not displayed then (full tilt poker app).
see bug [http://bugs.winehq.org/show_bug.cgi?id=13202](http://bugs.winehq.org/show_bug.cgi?id=13202)
switching back to nv driver fixes the problem (without the ClientSideWithRender key)

---

### Post by Zupp on 2008-11-20
Hey guys, I'm new around here, I wanted to confirm that the reg fix worked for me too. Also thanks to cjchand for the short tutorial :D. I'm new at this and I really didn't know which file to modify.

---

