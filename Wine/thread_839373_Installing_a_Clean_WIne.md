---
title: "Installing a Clean WIne"
date: 2008-06-24
forum: Wine
---

### Post by diegogranziol@gmail.com on 2008-06-24
Hey, I've just tried to install Both Adobe Photoshop along with Microsoft Office 2000 on Wine (KDE 4, Kubuntu) and both installations have gone **** shaped, i tried to uninstall and re-install, both the applications and wine, and all that happened was with both, that the applications didn't uninstall and when Wine Re-installed it was exactly the same, how can I completely re-install wine, that it recreates the .wine directory exactly as it was before anything was in there? (when i deleted it, it didn't re-install it)

thanks a lot!

---

### Post by jualin on 2008-06-24
> sudo apt-get purge wine This command will delete Wine and the .Wine directory. You can also try a different approach from the GUI using Synaptic and choosing "Complete Removal" when you right click on the wine package.

---

### Post by sgtbob on 2008-07-11
I tried both suggestions but Wine still shows in the Applications menu along with two programs entitled Legacy 5.0 and Legacy 6.0 that I had attempted to install (netiehr of which work BTW).  

I am unable to purge this mess so that I can start anew.  Tell me how to get rid of this stuff so I can attempt reinstall.  Nothing I've tried works.

Bob:(:confused::(:confused:

---

### Post by Drk Guy on 2008-07-11
If you want to remove menu entries, just do this: Alt+F2 -> Alacarte, i think you can work your way out from there

---

### Post by diegogranziol@gmail.com on 2008-07-12
Completely agree with sgtbob, unable to remove my mess of halfworking windows programs, that never seem to uninstall and if you delte the menu entry what good does that do? the program is still there and if you reinstall it it just doesn't show up!

---

### Post by schwarzeKunst on 2008-08-31
Hi had the same problem but with PhotoshopsXD found the solution on wine's wiki here's how to delete those dirty little applications entries:
"
3.1. How do I uninstall Windows applications?

Wine has its own built-in uninstaller - equivalent of Windows "add/remove programs" function for running standardized uninstallers. In recent version, a shortcut has been added in Wine's menu, along with a shortcut to winecfg.

The uninstaller does not remove menu entries. To remove all Wine created menu entries run the following commands

rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm
"

---

### Post by saeid on 2008-10-16
> **schwarzeKunst said:**
> 
The uninstaller does not remove menu entries. To remove all Wine created menu entries run the following commands

rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm
"

Thanks

---

