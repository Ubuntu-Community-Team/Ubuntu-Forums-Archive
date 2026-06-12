---
title: "[SOLVED] bassbox 6 in wine ?s"
date: 2008-02-12
forum: Wine
---

### Post by rexxxlo on 2008-02-12
i have wine instaled and it works good considering all the complaining i read and see.

my question is for the only reason i use wine and its not WOW its speaker design.

i own and use bassbox 6, (its a loudspeaker design program) quite often it s a great program easy to use looks good and gets great results 

i have it installed in wine and it seems to work nicely but some text is displayed incorrectly it will move the text up or down and only display part of the text all over the screen 

i will include a screen shot of it in action  any ideas how to fix this ?

i can post the actual text if i boot up my xp pc in case anyone wants to know what it says 
thanks

---

### Post by happyhamster on 2008-02-13
- Looks like a font problem. Try installing msttcorefonts first:

sudo apt-get install msttcorefonts

- If that didn't do anything, try changing the (wine) font resolution:

winecfg

- In the Graphics tab, lower the screen resolution slider (dpi).
- If you can't (because it's at its lowest setting already), edit the registry:

regedit

- and do a search for "logpixels". It will find something close to:

LogPixels    REG_DWORD    0x00000060 (96)

- Right-click that line and choose modify. Enter a value (and be gentle, steps of -10 are huge for example). Accept and close regedit.

- Warning: if you choose a real small value, you will screw up your wine-installation, because you won't be able to read anything. In that case, you can reset things by pasting the following into a text file:

```

[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Hardware Profiles\Current\Software\Fonts]
"LogPixels"=dword:00000060
```

- Save it as: winefonts.reg or whatever.
- Import it into the registry:

wine winefonts.reg

- And everything should be back to normal.

Good luck, and let us know if it worked (or not).


[edit: used code tags]

---

### Post by happyhamster on 2008-02-13
[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Hardware Profiles\Current\Software\Fonts]
"LogPixels"=dword:00000060

```

[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Hardware Profiles\Current\Software\Fonts]
"LogPixels"=dword:00000060
```

Does anyone know why the first paste shows a space in "Hardware" while that space doesn't show when using the code-tags? The space doesn't show when trying to edit the post either.

Weird.


edit: Seen something like it before (post 6 in this thread):
[http://ubuntuforums.org/showthread.php?t=52020&highlight=pingus](http://ubuntuforums.org/showthread.php?t=52020&highlight=pingus)

---

### Post by rexxxlo on 2008-02-13
well thank you i didnt have msttcorefonts installed 

i bet it will fix that weird character that i have been seeing sometimes too 

thanks again

---

