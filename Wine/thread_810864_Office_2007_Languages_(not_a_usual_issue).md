---
title: "Office 2007 Languages (not a usual issue)"
date: 2008-05-28
forum: Wine
---

### Post by _DD_ on 2008-05-28
I installed Office 2007 this afternoon and it mostly works apart from, as expect, bullet points!

Now I've read the fix is to go into languages settings and remove all languages apart from the one you're using, but when I go to the language settings there are no languages displayed and the add/remove buttons are blanked out.

One thing to note is that I didn't do a full install (because I didn't want all of the extra stuff that came with Office Enterprise) but instead just installed Word, Excel and Powerpoint. Having said that its still obviously installed all the core office stuff and the language settings manager is there, so I don't see why it wouldn't be complete?

Any ideas?

I can run the programs from the terminal and see if there are any errors if anyone wants that.

On another note, Powerpoint won't actually run. If I run it from the terminal then it runs and then exits with no actual errors, only a few stub warning things which you see all the time anyway.

Thanks :D!

---

### Post by Kidfork on 2008-05-28
To fix issues with fonts, bullets, and numbering, click the office button, go into Word options, then into language settings. Here, delete all languages except for your own. This has been tested with US English, which works. It is possible that other language packs, even with all the others uninstalled, may cause the issue. If so, I would suggest you post which packs do not work to help the developers.

---

### Post by _DD_ on 2008-05-28
As said in my first post, I've already tried that.

My issue is that there are no languages listed in the langauge settings for me to remove!

---

### Post by Kinst on 2008-05-28
```
wget http://www.kegel.com/wine/winetricks
sh winetricks riched20 riched30
```

---

### Post by _DD_ on 2008-05-29
Thanks, that sorted it :KS

---

### Post by Kinst on 2008-05-29
:)

---

### Post by kalmi on 2008-08-19
Thanks
(btw in my case I had only English (US) in the listbox on the right before doing "sh winetricks riched20 riched30", after that I lot of the others got magically enabled too...)

---

### Post by narx on 2008-09-08
Guys,

At the moment my bullets are appearing as "35/17" icons and some other pretty ugly bullet point, any solution to solve this?

Thanks!

---

### Post by michaelkahl on 2008-10-20
Same issue for me.  35/17 and other weird bullets, but number bullets seem to work fine.

---

