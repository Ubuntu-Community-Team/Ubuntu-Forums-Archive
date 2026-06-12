---
title: "Creating a folder shortcut"
date: 2017-03-18
forum: Wine
---

### Post by natesnape on 2017-03-18
Hello, I was tinkering with wine and I finally got borderlands editor to work with it, now my problem is when I launch the app, then try to navigate to my save location the save edition is unable to access the hidden folders of lubuntu, I was thinking that I can create a folder on my desktop and put the shortcut of the save file folder on that folder, or just create a shortcut of the save file folder directly to my desktop, this way the save editor will have access to the save file folder, is that possible?

---

### Post by howefield on 2017-03-19
Thread moved to the "*Wine*" forum.

---

### Post by vanadium on 2017-03-19
Quite likely a symbolic link will do the job fine. Locate the folder you want to link to under the hidden .wine folder. Right-click, select "Create link". This creates a symbolic link, named "Link to ...". Move it outside the .wine folder tree to where you want to use it and rename it to the name of the linked folder.

---

### Post by natesnape on 2017-03-20
> **vanadium said:**
> Quite likely a symbolic link will do the job fine. Locate the folder you want to link to under the hidden .wine folder. Right-click, select "Create link". This creates a symbolic link, named "Link to ...". Move it outside the .wine folder tree to where you want to use it and rename it to the name of the linked folder. I'm using Lubuntu and the folder that I want to have a shortcut is under my .local/share folder. When I right click the said folder I don't see a "link" option.

---

### Post by howefield on 2017-03-21
Try using the terminal command..

```
ln -s sourcepath destinationpath
```

If you are using paths outside your /home folder you'll probably need to use sudo.

See

```
man ln
```

for more details if interested.

---

