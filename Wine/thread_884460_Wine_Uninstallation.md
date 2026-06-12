---
title: "Wine Uninstallation"
date: 2008-08-09
forum: Wine
---

### Post by rajarshi on 2008-08-09
Hi,

I'd installed Wine sometime eariler, and through it, had installed a program called 'yWriter4'. Thing is that now I can't seem to install yWriter. There is an uninstall for yWriter, but it doesn't seem to do much. Have tried removing it from Wine, but it doesn't go away either.

Lastly, tried uninstalling wine as well, but although wine was uninstalled, I still have the menu entry for yWriter4 in Applications menu.

Where did I go wrong?

---

### Post by hocksal on 2008-08-09
If you want to receive automatic updates of the latest development release of Wine, you can follow the instructions here:

[ Wine Club ](http://www.wineclubdirectory.net)

---

### Post by hackerlife on 2008-08-11
funny as that may be, it is very unhelpful and it is very late here and am not in a good mood and i happen to have the very same problem as our friend rajarshi.

i was trying to install a program under wine, and the install was never ending (i think because it was trying to access the internet and wine doesnt support that) so i restarted and tryed to uninstall it and nothing happened 

i then preceded to uninstall wine, but it left inside applications, wine-programs-the program i cant uninstall.

any help???

---

### Post by /////// on 2008-08-11
You can uninstall WINE by doing the following:
In terminal type sudo apt-get remove wine
Then go to /home/(username)/ in your file browser
Show hidden files (usually ctrl+h)
delete the .wine folder
Go to System>Preferences>Main Menu
Remove the wine entries
And now your WINE should be uninstalled

---

### Post by lamda-core on 2008-08-11
I seem to have the exact same problem. 
@/////// it aint uninstalling wine.

i installed mediamonkey over wine recently. wine seems to uninstal it too. but the entry in the appicationmenu remains and several processes named "mediamonkey" keep poping up in system monitor eating the resources.

---

### Post by Java Geek on 2008-08-11
How do you do it in Xubuntu? I ahve uninstalled wine and removed .wine... now what?

---

### Post by /////// on 2008-08-12
@lamda-core what do you mean it ain't uninstalling wine, do you mean that the command sudo apt-get remove wine doesn't work? If so please post the output of the terminal after you type the command

---

### Post by ShelJ on 2008-08-18
Hi,

I keep running into this problem, removing applications in wine do not completely remove them, and it takes literally hours to find a sol'n here, so I wrote down on that I found sometime in the past.  Try this, it works for me: go to
```
/home/[COLOR=Red]"user"[/COLOR]/.local/share/applications/wine/programs
```  and remove the programs you want, or the entire wine folder if you no longer have wine installed.

I hope that this helps.

ShelJ

---

