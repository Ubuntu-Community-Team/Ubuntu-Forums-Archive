---
title: "ie4linux and 8.4"
date: 2008-06-20
forum: Wine
---

### Post by RyanBFS on 2008-06-20
to make a long story short my entire office uses 8.4 and godaddy changed their webmail page so it won't work right with firefox on ubuntu.  I was hoping to use ie4linux as a workaround for this.

I use ie4linux on my desktop that I switched over from 7.10 and it works fine but every time I try and install it on a fresh install of 8.4 it will open just once and I can't get to open again.  The mouse pointer never starts thinking but it seems like it gets stuck somewhere.  I can still open notepad in wine so I know thats not locked up.  If I restart gnome with ctrl+alt+backspace all the explorer windows I clicked on will open as soon as I log back in.  The only thing I can think of is that we have two logins on each computer and I installed it on both so maybe installing it in two folders is causing a problem.  The link with instructions on how to install ie4linux on multiple logins is dead so I just installed it on both.  I'm not that experienced at wine or ie4linux so if this is a common problem sorry for starting a thread but I didn't find anything in my searches.

---

### Post by cogadh on 2008-06-20
What version of Wine are you using?

---

### Post by Fire_Chief on 2008-06-20
Might also consider trying Opera as it has a native Linux version.

---

### Post by RyanBFS on 2008-06-20
hey guys thanks for the response I'm using wine 1.0 and I would love to use Opera but unfortunately godaddy will not support it.  The only other browser that would be an option is safari but it seems that ie4linux is a bit more developed than anything I know of for safari

---

### Post by cogadh on 2008-06-20
Well, one of the updates in the 1.0 version of Wine broke ies4linux (started with the relase candidates). If you downgrade to a pre-rc version, you may be able to get it to work.

---

### Post by RyanBFS on 2008-06-20
ahhh I bet thats it I just checked my desktop that works and I'm using .9.  Should have checked for things more closely before I jumped on the forums.

Thanks I'll post back after I roll back

---

### Post by RyanBFS on 2008-06-20
well that didn't work, I did a fresh install of last version of wine .9 and ie4linux and same results.  It seems like ie gets stuck in some kind of loop where it doesn't effect anything else that requires wine.  For now I found a very ghetto fix for the godaddy attachment button.  Apparently if you right click and select switch page direction the button will start to work.  This seems to be a mapping issue inherent to firefox 2 and 3 on ubuntu but not on windows.

---

### Post by zeropaper on 2008-07-21
@cogadh
I just installed ie4linux with wine-1.0 on kubuntu 8.4... was not that difficult...
I opened the terminal, go into the ie4linux folder run "./ie4linux --no-gui" and it worked (even if i had a small red message about the Wine version).

I hope it will help you ;)

---

### Post by periphery on 2008-08-15
Thanks heaps zeropaper your solution worked perfectly for me.:)

---

### Post by bpl07 on 2008-08-16
You could also use [PlayOnLinux]("http://www.playonlinux.com/en/") to install ie4linux or safari.  It puts them in separate "bottles" too so they don't interfere with each other, and it would probably be using the pre-rc for the ie4linux install.

---

### Post by OhioLen on 2008-08-27
Workaround:  

I've found that after I close the window for IES4LINUX, I also need to go into system monitor and kill the WINESERVER process (which on my Dell Inspiron 1525n will continue to consume roughly 50% of the CPU until killed), IEXPLORE.EXE and EXPLORER.EXE. IES4LINUX **will not** load again until those 3 are cleared out of the memory. 

It looks like there's a bug in which closing the window doesn't actually end the program, since those 3 go into "sleeping" mode in the processes list. Kill them and IES4LINUX will work fine again. You have to do it every time you close the MSIE window, though.

---

