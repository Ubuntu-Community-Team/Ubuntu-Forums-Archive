---
title: "Wine  menu question, odd behavior"
date: 2014-06-18
forum: Wine
---

### Post by drfox on 2014-06-18
I'm running Xubuntu 14.04. 
I prefer the normal Applications menu, but when running WINE I only see "Browse C, Configure Wine, Uninstall Wine, and WineTricks"
With WhiskerMenu, I also see the Programs Folder. I would like to see the Programs Folder in the non-Whisker menu. Any idea how to do that?
Also, how do I get an application that doesn't need installation (just a regular EXE file) to show up on the menu?
Thanks for any ideas I can try.

---

### Post by Toz on 2014-06-19
> **drfox said:**
> I'm running Xubuntu 14.04. 
I prefer the normal Applications menu, but when running WINE I only see "Browse C, Configure Wine, Uninstall Wine, and WineTricks"
With WhiskerMenu, I also see the Programs Folder. I would like to see the Programs Folder in the non-Whisker menu. Any idea how to do that?
Looks like a bug. Just verified that it works fine on Xfce 4.10, but seems broken in newer versions. I've just created a [launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/xfce4-panel/+bug/1332385") for it. Also created an Xfce bug report which is noted in the launchpad report.

> Also, how do I get an application that doesn't need installation (just a regular EXE file) to show up on the menu?
Thanks for any ideas I can try.
If you want it in the Wine Programs menu, we'll have to wait until the above bug gets fixed. If you just want it in the regular menu, then basically, figure out the command to run the application, then create a .desktop file for it. As an example, to run the Windows version of putty through wine and have it display in the "Internet" folder, I create **~/.local/share/applications/putty-wine.desktop** with the following content:
```
[Desktop Entry]
Version=1.0
Name=PuTTY SSH Client (Wine)
GenericName=PuTTY
Comment=Connect to an SSH server with PuTTY
Type=Application
Exec=wine /home/toz/Downloads/putty.exe
Icon=putty
Categories=GTK;Network;

```

You can also install alacarte then right-click on the Applications Menu plugin, select "Properties" and then "Edit Menu" to use a graphical menu-creation app, but keep in mind that alacarte is buggy.

---

### Post by drfox on 2014-06-19
Thank you. I have subscribed to the launchpad bug mail list, and I'll play with the menu based on what you've shown me. I'll mark the thread solved.

---

