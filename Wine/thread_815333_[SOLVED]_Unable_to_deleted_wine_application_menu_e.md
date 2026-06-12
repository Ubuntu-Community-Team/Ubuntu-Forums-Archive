---
title: "[SOLVED] Unable to deleted wine application menu entries"
date: 2008-06-01
forum: Wine
---

### Post by pmaconi on 2008-06-01
I recently attempted to install iTunes in Wine. After seeing that it wasn't working correctly, I tried to uninstall it via the Wine add/remove programs gui. It said that the uninstall was successful, but the launcher entries remained under Applications -> Wine.

I removed my ~/.wine folder and completely reinstalled wine, hoping to get rid of them. No such luck. They just moved to Applications -> Other. I can't edit the menu and delete them through that (I tried, but it doesn't do anything). I also don't see them in the ~/.config menu file. Does anyone know any other way to delete the entries?

Thanks!

---

### Post by Dougie187 on 2008-06-01
You can right click on the menu bar, then click on edit entries. I think thats what its called at least (dont have ubuntu in front of me). Then you go through and find the ones you want to delete. They have to be on the right side, and you can simply delete them.

---

### Post by pmaconi on 2008-06-01
I tried that, the entries remain even after choosing the remove option.

---

### Post by Dougie187 on 2008-06-01
Hmm.... I dont think i have ever had that issue. I have always been able to remove the launchers using that edit menus option. I guess I will look around a bit later, when I get around ubuntu. I will let you know if I find anything.

---

### Post by temcat on 2008-06-03
> **pmaconi said:**
> I tried that, the entries remain even after choosing the remove option.

I've had that too - I choose Delete in the menu editor, but it stays intact th editor and the menu. It may be a bug in gnome-menus, alacarte (menu editor) or libgnome-desktop.

Anyway, when you choose to completely remove wine with configuration files in the Synaptic package manager, the menu items should go.

---

### Post by Kevanx on 2008-06-22
I have been plagued with this for a while now, and COMPLETE REMOVAL did NOT work. I found different solutions from a few places. I'm not sure which one is the real solution, but you probably want to do both just to be sure.

Please use this at your own risk. Also, whenever someone tells you to use the rm command in a terminal, be very careful! Here, you will only be removing old menus items for wine.

1. Remove menu items.
- open up a terminal under Applications -> Accessories
- type
```
cd /home/***your username here***/.config/menus
```
this takes you to the menus folder for wine. As far as I know, this is only for wine. It should have a bunch of entries for programs that you installed.
- enter ls to list the contents of that folder
- enter the following.
```
rm -r * 
```
It will remove everything in this folder. URGENT: I don't know what happens if you have anything currently installed under wine. I had wine uninstalled at this point, but if you use gedit to open the .menu files, you can probably remove things by hand as needed.

2. Remove the directories under the applications folder.
type
```
cd ~/.local/share/applications/wine/Programs/
```
then ls to see the contents of the directory.
once again use
```
rm -r [folder name]
```
to remove whatever folders don't belong.

Via: [http://techxplorer.com/2008/04/21/removing-wine-application-entries-on-ubuntu/](http://techxplorer.com/2008/04/21/removing-wine-application-entries-on-ubuntu/)

3. After everything, in the terminal again, type
```
killall gnome-panel
``` to restart gnome. Your applications shoudl all be gone, in theory, but I actually had two annoying applications sticking around. Fortunately, this time, going to Applications > Edit menus and then right-clicking and clicking Delete actually worked.

Hope this helps!

---

### Post by pmaconi on 2008-06-22
Ah. I had forgotten to mark this thread solved. Thanks to tinivole, I found the solution (in another thread). All of the wine entries were stored at:```
nautilus ~/.local/share/applications/wine
``` Once I removed them from that directory, they disappeared.

---

### Post by Benic on 2008-09-12
> **pmaconi said:**
> Ah. I had forgotten to mark this thread solved. Thanks to tinivole, I found the solution (in another thread). All of the wine entries were stored at:```
nautilus ~/.local/share/applications/wine
``` Once I removed them from that directory, they disappeared.

I had the same issue and I've tried everything (I messed up a lot...) but this line solved the whole problem. Thanks !

---

### Post by physeetcosmo on 2009-01-08
> **pmaconi said:**
> Ah. I had forgotten to mark this thread solved. Thanks to tinivole, I found the solution (in another thread). All of the wine entries were stored at:```
nautilus ~/.local/share/applications/wine
``` Once I removed them from that directory, they disappeared.

Thanks pmaconi, you helped this newbie figure out more of the file structure of Linux. Apps folders and directories stored in *username*/.local/share

Thanks all!

-Dustin:)

---

### Post by sarang031705 on 2011-08-28
thank you soooo much, it did solved my problems too:popcorn:

---

### Post by waqas_butt0071 on 2011-09-04
i got the solution from 

[http://wiki.winehq.org/FAQ#uninstall_app](http://wiki.winehq.org/FAQ#uninstall_app)

---

