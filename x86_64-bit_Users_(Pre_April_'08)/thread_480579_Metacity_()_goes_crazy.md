---
title: "Metacity (?) goes crazy"
date: 2007-06-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Major_Kong on 2007-06-21
Whenever i visit (using Firefox) certain japanese sites (e.g.: [http://homepage3.nifty.com/blacksword/](http://homepage3.nifty.com/blacksword/) ) the window manager goes berserk, and i have to restart gnome altogether.

Anyone else has this problem ? Or knows what's wrong ?

---

### Post by Major_Kong on 2007-06-21
Not even a "works fine with me" ?

---

### Post by kleeman on 2007-06-21
Works fine for me in both firefox and konqeror. Might be a font problem with the Japanes characters, Does it work with your konqueror?

---

### Post by Major_Kong on 2007-06-22
I don't have konqueror installed. I'm running ubuntu 7.04 .

The page renders, the problem is just that the window manager goes crazy in doing so.

---

### Post by Major_Kong on 2007-06-22
This also happens when i visit [www.hotmail.co.jp](www.hotmail.co.jp) , but it doesn't happen in all japanese site. e.g.: [http://www.geocities.jp/aoyoume/aotuv/](http://www.geocities.jp/aoyoume/aotuv/) - no problems with this site.

By using the command line to restart metacity (i checked it crashes), i get the following error, if i leave the page opened:

> *** glibc detected *** metacity: free(): invalid next size (fast): 0x0000000000ac1780 ***


EDIT: Found the bug report: [https://bugs.beta.launchpad.net/ubuntu/+bug/104710](https://bugs.beta.launchpad.net/ubuntu/+bug/104710) - But no solution...

EDIT: Checked the blacksword site, it was made wih Frontpage Express... Content-Type: text/html; charset=x-sjis (Shift_JIS) . The charset must be what's causing the problems...

EDIT: Also happens with ISO-2022-JP charset.

Any ideas ?

---

### Post by kleeman on 2007-06-22
That looks like a rather strange bug. If I was you I would view the pages with another browser (opera, konqueror, epithany etc) to see whether you can work round it.

---

### Post by Alex&amp;Linux on 2007-06-22
Seconded!
Make sure your system is update, and perhaps try another browser (or try reinstalling firefox!)
Additionally, it may be useful to try another window manager (beryl/compiz/Kwin)
Hope you can resolve this issue :)

---

### Post by Major_Kong on 2007-06-22
> **kleeman said:**
> That looks like a rather strange bug. If I was you I would view the pages with another browser (opera, konqueror, epithany etc) to see whether you can work round it.

I saved the page (.html) to disk, and tried to open it with geditor, the same thing happened. I was wrong, it's not browser related.


> **Alex&Linux said:**
> Seconded!
Make sure your system is update, and perhaps try another browser (or try reinstalling firefox!)
Additionally, it may be useful to try another window manager (beryl/compiz/Kwin)
Hope you can resolve this issue :)

Activated compiz using with ubuntu wizard, almost the same happened, only not so "violent". 

It's some problem with the charset...

EDIT: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_improve_sub-pixel_font_rendering_for_Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_improve_sub-pixel_font_rendering_for_Feisty) - (out of ideas...) did anyone with this installed checked the website ?

---

### Post by Major_Kong on 2007-06-22
Problem Solved.

Well, kind of... the problem was really the patched freetype libraries (or at least when i "downgraded" them the problem vanished).

---

### Post by Major_Kong on 2007-06-25
After some help from [mlind](http://ubuntuforums.org/member.php?u=52272), i recompiled the freetype, libcairo and xft  packages from source ( [http://www.telemail.fi/mlind/ubuntu/pool/fonts/](http://www.telemail.fi/mlind/ubuntu/pool/fonts/) ). It works fine now, so i can keep the improved subrendering.


PS: Besides this problem, the amd64 packages in the moshen repo are somewhat outdated. Until an update it's probably not a good idea to install them from the repo.

---

