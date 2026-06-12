---
title: "Wine won't uninstall MS Office 2000?"
date: 2008-10-28
forum: Wine
---

### Post by WillBMX on 2008-10-28
I am using Ubuntu (up to date) and Wine, I installed MS office 2000 but couldn't register it properly, so decided to uninstall it... I go to Wine and use the uninstaller on MS office 2000, it goes through the process of uninstalling it... and it's still on the list of things I can uninstall. I have uninstalled it about 10 times now... haha, and I've tried doing it then rebooting, but doesn't work.

Shouldn't have got tied up with Microsoft again I guess.

Anyway, anyone got and fancy codes I can paste into terminal and wipe it off completely? Or any other methods?

Thanks.

---

### Post by Kinst on 2008-10-29
Hey dude...there's a hidden folder in your home directory called '.wine'. Just delete that. 

Then put this in the terminal to get a new one:
```
winecfg
```

---

### Post by WillBMX on 2008-10-29
Hi, thanks, I can't find the .wine folder, I have ticked 'Show hidden files and folders' but no luck.
If I can find this and do it then will it not affect the other programs I have installed with Wine?

Thanks

Edit: Settings didn't apply until I closed down the file browser and opened it up again. So I went into the .wine folder and deleted the MS Office folder in it. I still have the shortcuts to the MS Office applications, but now they don't work obviously. I can't see any way to delete the shortcuts now :confused: haha

---

### Post by Potters Son on 2009-04-06
Right click on Applications > Edit Menus.

Navigate to Applications>Wine>Programs in the left Pane, select MS Office XYZ in right pane, click Delete

---

### Post by 0cton on 2009-04-06
It may seem unrelated
but why do you need ms office 2000?
Open office can do everything could ms office 2000 (and more)
and it can open and save microsofts proprietary formats
Just wondering why?

---

