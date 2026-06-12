---
title: "textsize"
date: 2008-01-18
forum: Wine
---

### Post by krestenbuch on 2008-01-18
HI all.

I have got some programs running in wine, but the tekst in the menus is so small that I hardly cant read it.

Is there any way to change that?

Mvh Kresten

---

### Post by ajgreeny on 2008-01-18
Go to System>Preferences>Appearance and on the Font tab change the "Application" font size to something larger.  That should do it for you.

---

### Post by krestenbuch on 2008-01-18
Doesn't help. It changes the text in the rest of the system, but the applications that runs under wine is not affected.

Thanks anyway.
Kresten

---

### Post by ajgreeny on 2008-01-18
Thanks for that info.  I don't  really use wine so wasn't aware of the situation and it's worth knowing for future reference.

---

### Post by earther on 2008-05-23
So is there a solution for this?  At 1280x1024 the defaut system font size in Wine is almost unreadable.  All apps running under Wine have the same problem.  As noted above, changing font size in Ubuntu has no effect on Wine.  Note that I am able to change font size within applications but not the application font itself - File, Edit, View etc..

---

### Post by cogadh on 2008-05-24
Run winecfg, go to the Graphics tab and move the Screen resolution slider up to something higher. Don't go too high or you'll end up with font sizes that are so large that you won't be able to use Wine and will only be able to fix it with a manual Wine registry edit.

---

### Post by earther on 2008-05-24
> **cogadh said:**
> Run winecfg, go to the Graphics tab and move the Screen resolution slider up to something higher. Don't go too high or you'll end up with font sizes that are so large that you won't be able to use Wine and will only be able to fix it with a manual Wine registry edit.
I did that and it had no effect on the Wine system default font size.  It did change the font size within an app (like text area) but I was already able to do that from within the app itself. Frustrating . . .  Thanks for trying though.  Any other thoughts (other than a hammer!)

---

### Post by cogadh on 2008-05-24
I think your problem may have more to do with the app you are running rather than Wine. Changing the setting as I described is the same as telling Wine that all apps should use that size for all default fonts. However, some applications will ignore that and use whatever they want to anyway. This is not actually a Wine problem, as those apps will do the same thing when run natively in Windows.

---

### Post by earther on 2008-05-24
> **cogadh said:**
> I think your problem may have more to do with the app you are running rather than Wine. Changing the setting as I described is the same as telling Wine that all apps should use that size for all default fonts. However, some applications will ignore that and use whatever they want to anyway. This is not actually a Wine problem, as those apps will do the same thing when run natively in Windows.OK.  I upped the screen resolution from  96 to 120 dpi and this was the result:

[IMG]http://www.eartherdesigns.com/ss/font_size.gif[/IMG]

The Wine system font is still too small.

---

### Post by cogadh on 2008-05-24
That's not the Wine system font size at fault, its exactly as I described, the app is just ignoring the setting you configured. I've never used NoteTab in Windows, but I would guess that it does the same thing.

---

### Post by earther on 2008-05-24
All the apps I am running in Wine do exactly the same thing - that includes Photoshop 7, TextDiff, Easy Thumbnailer and TimeStamp.  Makes me think it's something other than the apps causing it.

I never had a problem with system font sizing in Windows but it's been so long since I've booted XP, I can't really remember.  (And that's a good thing.)  Thanks for trying to help.

---

