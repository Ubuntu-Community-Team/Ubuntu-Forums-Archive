---
title: "Install WINE on computer w/o internet"
date: 2008-08-29
forum: Wine
---

### Post by Keatoru on 2008-08-29
My brother wiped out his computer and now needs drivers for his wireless card. He has a cd with them but he needs wine to use the exe on the cd. where can i get WINE to burn on a cd then put it on his computer via cd?

---

### Post by sidewinder46 on 2008-08-29
You could always download the wine source, then compile it.  Even easier than that is to download the .deb and burn it. [Wine .deb packages]("http://wine.budgetdedicated.com/archive/index.html").

---

### Post by mocoloco on 2008-08-29
On either system:
[LIST]
[*]Open Synaptic (in System -> Administration)
[*]Find and mark any packages you want to get
[*]Click File -> Generate package download script. Save it with any name you want.
[*]If you do this on the non-connected machine, put the file one a USB drive or something
[/LIST]

On the machine with the internet connection:
[LIST]
[*]Create a folder for the files you'll download
[*]put the saved script in that folder
[*]Open a terminal, navegate (cd for change directory) to the folder
[*]Type "sh <yourfilename>" to run it, and let it download all the stuff
[*]Burn those files to a disc using anything you want, (eg, Places -> CD/DVD Creator)
[/LIST]

Back on the machine without connectivity:
[LIST]
[*]Open synaptic.
[*]Click File -> Add downloaded packages
[*]Select the CD or folder where you've got them, and they'll be installed
[/LIST]

---

### Post by Keatoru on 2008-08-29
i had dled that right after i posted but when i copied the file onto the disk it said that there was attached files that wouldn't be copied(something like that) and when i tried installing it didn't work. i'm using windows atm. to lazy to switch lol

---

### Post by mocoloco on 2008-08-29
Oh yeah, sidewinder46's suggestion is much easier if all you want is wine, just do that :).  If you decide you need more stuff from the repos though synaptic's download script makes it easy.

---

