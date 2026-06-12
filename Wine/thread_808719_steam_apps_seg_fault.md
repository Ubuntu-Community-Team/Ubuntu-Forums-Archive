---
title: "steam apps seg fault"
date: 2008-05-26
forum: Wine
---

### Post by javagamer on 2008-05-26
Hi,
   I recently upgraded to the 2.6.24-17-generic kernel and my graphics drivers got all messed up, so I reinstalled the OS, the drivers and everything seemed to work.  Then I installed wine every way I could find WineHQ method, synapic method, from source, and most recently the method stickied here (which seems to be the WineHQ way).  Each time I install it steam installs fine (after grabbing Gecko), but I can never install or launch (if I copy my old .wine folder) any games from steam.  They all end with a segmentation fault.
I'm on Hardy AMD64 and the results of uname -a are:
```
Linux javagamer-desktop 2.6.24-17-generic #1 SMP Thu May 1 13:57:17 UTC 2008 x86_64 GNU/Linux
```
and a copy of the terminal output from logging into steam to trying to install Counter Strike: Source (though this seems to happen to any games I attempt to install):
```

Omited: A large number of CellID lines and fixme lines.
fixme:win:SetLayeredWindowAttributes (0x400e2,0x00000000,230,2): stub!
fixme:win:SetLayeredWindowAttributes (0x400e2,0x00000000,230,2): stub!
fixme:win:SetLayeredWindowAttributes (0x400e2,0x00000000,206,2): stub!
fixme:win:SetLayeredWindowAttributes (0x400e2,0x00000000,206,2): stub!
fixme:win:SetLayeredWindowAttributes (0x400e2,0x00000000,154,2): stub!
fixme:win:SetLayeredWindowAttributes (0x400e2,0x00000000,154,2): stub!
fixme:win:SetLayeredWindowAttributes (0x400e2,0x00000000,82,2): stub!
fixme:win:SetLayeredWindowAttributes (0x400e2,0x00000000,82,2): stub!
fixme:win:SetLayeredWindowAttributes (0x400e2,0x00000000,37,2): stub!
fixme:win:SetLayeredWindowAttributes (0x400e2,0x00000000,37,2): stub!
fixme:win:SetLayeredWindowAttributes (0x400e2,0x00000000,14,2): stub!
fixme:win:SetLayeredWindowAttributes (0x400e2,0x00000000,14,2): stub!
fixme:win:SetLayeredWindowAttributes (0x400e2,0x00000000,0,2): stub!
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
Segmentation fault
```
Can anyone help? All I've done is reinstall, copy over some media files, and do a few minor audio changes (changing default sounds card and making sure everything uses ALSA).
Thanks in advance!

---

### Post by strongboww on 2008-05-26
windows fonts installed?

which wine version?

---

### Post by javagamer on 2008-05-26
Which fonts do I need?  When I tried to install Tahoma it said it was already there.
I tried Wine 1.0-rc2 for all and I also tried Wine 9.61 from source with the same result.

Edit: It turns out in the current installation I don't in fact have Tahoma, but after installing it nothing improved.
Edit2: Just tried installing core fonts from winetricks, arial.exe stopped it with error 127 and still nothing's changed.

---

### Post by swytz on 2008-11-27
I'm seeing the same issue:

```
s@k2:~/.wine/drive_c/Program Files/Steam$ uname -a
Linux k2 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64 GNU/Linux
```

Same segmentation fault, at least the end:

```
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x194008)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x194008)->(ffffffff)
fixme:win:RegisterDeviceNotificationA (hwnd=0x10090, filter=0x32df78,flags=0x00000004),
        returns a fake device notification handle!
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
Segmentation fault

```

I wonder if it has anything to do with the 64-bit arch?

---

