---
title: "Top Panel folders opens with VLC"
date: 2008-11-01
forum: x86 64-bit Users
---

### Post by Bloemetjesgordijn on 2008-11-01
Hi,

I have just upgraded to Ibex. The stranges thing happens, when I click on my Top Panel "Locations - Desktop or any folder..." it doesnt use Nautilus but it tries to open my folder with VLC.

:confused:

Can anyone help me??

Kind regards,

Bloemetjesgordijn

---

### Post by prshah on 2008-11-01
> **Bloemetjesgordijn said:**
> 
I have just upgraded to Ibex. The stranges thing happens, when I click on my Top Panel "Locations - Desktop or any folder..." it doesnt use Nautilus but it tries to open my folder with VLC.


This is a known bug. Open "Computer" from the Places location, (or just run nautilus from the Alt+F2 "command" box). Now, navigate to your home directory, then right click any directory within it, and choose "Open With"-"Open with other application"; in the box that pops up, choose "File Browser".

From now on, it will open correctly.

---

### Post by Bloemetjesgordijn on 2008-11-02
Thx mate

It worked perfectly

---

### Post by ghetto2ivy on 2008-11-07
It works one time for me, but doesn't "stick". Afterwords it keeps opening up vlc.

---

### Post by prshah on 2008-11-07
> **ghetto2ivy said:**
> It works one time for me, but doesn't "stick". Afterwords it keeps opening up vlc.

Here's another way you can try; System-Preferences-File Management. If you can't find that option, press Alt+F2, and run ```
nautilus-file-management-properties
```

Then click the Behaviour tab, and select the option "Always open in browser windows", then click Close.

Now perform the earlier method again, and see if it "sticks"

If that doesn't work as well, right click any directory in your home directory, then choose Properties-Open With-File Browser-Close. If the "File Browser" option is not there, click on Add and locate "File Browser". If you still cannot find the option, at the bottom of the "Add Application" window, click on "Use a custom command" and give the command as ```
nautilus
```.

If things still don't work, what Ubuntu are you using? Kubuntu, XUbuntu? and version?

---

### Post by ghetto2ivy on 2008-11-09
Method 2 worked. For good measure, I went ahead and removed VLC and Totem as options...

The important thing for anyone else on this thread, is right click --> Properties *then*  go to the "open with" tab
**not** right click --> "open with".

Thanks!

---

### Post by prshah on 2008-11-10
> **ghetto2ivy said:**
> 
The important thing for anyone else on this thread, is right click --> Properties *then*  go to the "open with" tab
**not** right click --> "open with".


If you right-click a folder, you will get the "Open With" option in the context menu itself. If you don't get that option in the right click menu, you've right clicked the blank space and not a folder icon.

---

