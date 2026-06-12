---
title: "Wine won't completely uninstall programs?"
date: 2007-11-13
forum: Wine
---

### Post by cisforcojo on 2007-11-13
Couple questions here:

1. How can I uninstall Far Cry so that it's gone from my Gnome menu and also gone from my .wine directory? Uninstalling it with the wine option didn't seem to do that.

2. I have the same problem with Microsoft Office. I can't get rid of it for the life of me (without completely wiping WINE.) I'm really just looking for a more efficient method of adding/removing apps when using WINE and making sure my registry is clean. Anyone have any tips on removing Microsoft Office 2003 and/or running it in WINE? I'm getting bizarre questions about my user name and it's saying that the current user isn't permitted to run it.

3. Editing the GNOME menu, how can I DELETE entries? The best I've been able to do is hide 'em using System->Prefs->Main Menu

Thanks!

---

### Post by JasonF on 2007-11-13
For wine, I prefer to install everything into its own fake windows drive. [http://frankscorner.org/index.php?p=wineprefix](http://frankscorner.org/index.php?p=wineprefix) describes a method of doing it.

For the gnome menu, right click on an item you don't want and select delete.

---

### Post by cisforcojo on 2007-11-13
I should note that I'm using Linux Mint 3.1 Celena. This might be a distro difference but I cannot remove ANYTHING from the menu. I see the option but only for individual items. How can I edit the actual menu entries (I want to change the icon for the wine category for example)

---

### Post by JasonF on 2007-11-13
> **cisforcojo said:**
> I should note that I'm using Linux Mint 3.1 Celena. This might be a distro difference but I cannot remove ANYTHING from the menu. I see the option but only for individual items. How can I edit the actual menu entries (I want to change the icon for the wine category for example)

I can edit the menu entries by selecting the 'Applications' in the left list, and editing in the right. It seems you can't right-click on anything in the right list. Also to be sure, I'm using the program 'alacarte' which is the default for menu editing in gutsy, try launching it from a terminal to make sure that's what you are using to.

---

### Post by cisforcojo on 2007-11-13
Great! Now Got it, thanks. Now anyone know how to completely get rid of MS Office 2003? I'll use the MS uninstaller but when I pop the CD in after, it'll act like I'm just repairing a previous install. It should be GONE! Any help?

---

### Post by cogadh on 2007-11-13
If the Wine "uninstaller" app didn't work, the just go into your .wine directory and delete the program directory for the app you are trying to remove. The run the Wine uninstaller again, select the app from the list and it will detect that the application is no longer present and delete the registry entry.

If that still doesn't help. then delete the entire .wine directory and start over with a fresh one.

Just a bit of advice for using Wine. Since you never know what is going to happen when you install something new in Wine, it is usually helpful to create a test or lab .wine directory to mess with your installs and configurations. Once you have an application figured out, then you can install it in your normal .wine directory without fear of screwing up anything else. To create a new "Wine lab":
```
wineprefixcreate .winetest
```
To use the new lab:
```
env WINEPREFIX=~/.winetest wine executablename.exe
```

---

### Post by cisforcojo on 2007-11-13
That is some excellent advice. Thanks, cogadh! I knew you'd probably post on this thread haha.

---

### Post by cogadh on 2007-11-13
What, am I that predictable? :)

---

### Post by Mad_Max_1412 on 2007-11-17
> **JasonF said:**
> For the gnome menu, right click on an item you don't want and select delete.

When I go to Applications --> Wine --> Programs --> 2K Games --> BioShock and right click , I don't get the option to delete.  The only options I get are:

1) Add this launcher to panel
2) Add this launcher to desktop
3) Entire Panel
    3.1) Add this as draw to panel
    3.2) Add this as menu to panel


Am I doing something wrong?

---

### Post by JasonF on 2007-11-17
Use System->Preferences->Main Menu and delete the entry from there.

---

### Post by Frak on 2007-11-17
> **cogadh said:**
> What, am I that predictable? :)
Yes

@Mad_Max
How did you get Bioshock installed in the first place? Wine lacks DX10 support.

---

### Post by cogadh on 2007-11-17
BioShock doesn't require DX10, it has optional features that can take advantage of DX10 interfaces, if present. Otherwise, it is just a DX9 game. It still doesn't work in Wine though.

---

### Post by Mad_Max_1412 on 2007-11-17
Yep, found out it didn't work, so I've uninstalled it but needed to clean up the menu.

Thanks for the tip about using the System --> Main Menu path. All fixed.

---

### Post by noremacyug on 2008-02-22
i'm having an issue with deleting an item from the menu as well.  i can wipe out the program and even uninstall wine, but the icon will stay.  i can hide it so i don't see it on my apps list, but i want it gone.  i've tried right clicking and selecting delete numerous times and it does nothing.  i've rebooted a couple times, reinstalled wine again, nothing.   it just isn't interested in leaving.  any ideas guys, it's driving me nuts!

oh, btw, it a left over icon from utorrent, don't know if that helps or not.

---

### Post by noremacyug on 2008-02-23
anyone??

---

### Post by noremacyug on 2008-02-23
did a little more googlin and found the solution to completely remove the icon.

---

### Post by ShelJ on 2008-03-06
Could you please elaborate?

---

### Post by noremacyug on 2008-03-06
> **ShelJ said:**
> Could you please elaborate?

i'm thinking this was the command line i used to locate any leftover files hanging around after an uninstall.

```
sudo find / | grep -i wine | less
```

of coarse alter "wine" to whatever file name you are looking for.

---

### Post by ShelJ on 2008-03-06
Worked, thanks!

---

### Post by ipa069 on 2008-04-02
thnxs everyone works for me cheers:guitar:

---

### Post by HunterK on 2008-04-02
Here is a useful tidbit to remember when uninstalling things via the "WINE Uninstaller Application".  It uses the same registry entries as the Windows Add/Remove program. 

So, if there is something in the list of the WINE uninstaller and you want it off that list (you already deleted the physical folder where the app is installed), you can remove it from that list by doing this:

Run the registry editor:
```
wine .wine/drive_c/windows/regedit.exe
```

Then browse to:

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Each key listed there represents a listing in the WINE Application Uninstaller.  If you delete the key, you will remove the application name from the list in the uninstaller.

---

### Post by TwistableLime on 2008-05-01
> **HunterK said:**
> Here is a useful tidbit to remember when uninstalling things via the "WINE Uninstaller Application".  It uses the same registry entries as the Windows Add/Remove program. 

So, if there is something in the list of the WINE uninstaller and you want it off that list (you already deleted the physical folder where the app is installed), you can remove it from that list by doing this:

Run the registry editor:
```
wine .wine/drive_c/windows/regedit.exe
```

Then browse to:

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Each key listed there represents a listing in the WINE Application Uninstaller.  If you delete the key, you will remove the application name from the list in the uninstaller.

Great! Thats exactly what I was looking for, thanks!

---

### Post by cogadh on 2008-05-01
> **HunterK said:**
> Here is a useful tidbit to remember when uninstalling things via the "WINE Uninstaller Application".  It uses the same registry entries as the Windows Add/Remove program. 

So, if there is something in the list of the WINE uninstaller and you want it off that list (you already deleted the physical folder where the app is installed), you can remove it from that list by doing this:

Run the registry editor:
```
wine .wine/drive_c/windows/regedit.exe
```

Then browse to:

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Each key listed there represents a listing in the WINE Application Uninstaller.  If you delete the key, you will remove the application name from the list in the uninstaller.
You don't actually need to run this long command:
```
wine .wine/drive_c/windows/regedit.exe
```
You can just open a terminal and type "regedit", it will launch Wine's registry editor without so much typing.

---

### Post by smrdelj on 2008-05-01
I've just removed all as this thread says. I removed Wine and Wine-Doors by all the ways here exposed. I uninstall the applications by "sudo apt-get remove" and also by the Wine Uninstaller. Then, I manually deleted all folders and "icons" from the Main Menu by erasing them from the "Main Menu editor" (System > Preferences > Main menu). Then, I execute the command "sudo find / | grep -i wine | less", that a user posted in these thread. Finally, I clean the registry entries doing exactly what HunterK says three posts above.

Results: all cleaned

But now, I reinstalled Wine and I don't know how to recover the Icons and Menu that used to previously created themselves in Gnome menu before the installation.

How can I solve it?

Thanks, bye

---

### Post by tibasic on 2008-08-19
I've run into this problem as well. I've had links that I've "deleted" with menu editor (which essentially hides them).

Anyway to remove the left over wine icons go in to the .local folder in your home directory. (Ex: ~/.local/share/ or /home/[yourname]/.local/share) All the 'extra' menu entries should be amongst these folders.

Another place is: (~/.config/menus/applications-merged or /home/[yourname]/.config/menus/applications-merged).

---

