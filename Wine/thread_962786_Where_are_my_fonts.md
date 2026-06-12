---
title: "Where are my fonts?"
date: 2008-10-29
forum: Wine
---

### Post by matthewblair on 2008-10-29
Hey everyone, I finally got the one thing that was holding me to windows working in Wine, Guitar Pro 5. The only thing is, I can't see any text on the windows. I've attached a screenshot so you can see what I mean. How would I fix this?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=90133&stc=1&d=1225311508[/IMG]

Thanks, Matthew.

---

### Post by Dark9204 on 2008-10-29
Just copy all fonts from windows to wine.

---

### Post by matthewblair on 2008-10-29
I tried that, but it didn't help. Do I need to reinstall GP5 or Wine?

---

### Post by Dark9204 on 2008-10-30
Well, your could run Window xp/vista in virtualbox.

---

### Post by Dark9204 on 2008-11-01
i just checked the Wine AppDB
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3782](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3782)

And i found this:
"I've just experienced the font issue (i.e. no notes, fret numbers or notation marks would appear in the tablature window) after reinstalling GP5 and I've discovered a solution that works in certain circumstances. You see, I had Guitar Pro.ttf installed system-wide after I copied over all the fonts from my Windows installation. Removing this font from ~/.wine/drive_c/windows/fonts resolved the problem. I'm not sure of how the font rendering is handled, but it appears as though there could be a conflict between fonts installed in X.org and in Wine, or perhaps in the windows/fonts directory, as there's many more Wine fonts in /usr/share that don't cause problems."

---

