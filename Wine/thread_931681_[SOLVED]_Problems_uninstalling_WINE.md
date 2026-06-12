---
title: "[SOLVED] Problems uninstalling WINE"
date: 2008-09-27
forum: Wine
---

### Post by cha0sthe0ry on 2008-09-27
I need to reinstall WINE completely, as if WINE had never been on my computer.  However, I can't get rid of all the files.  Every time I uninstall WINE, when I reinstall it all the files are still the same way they were before i uninstalled.  I tried the other "Problems uninstalling WINE" thread in the forum, it did not help, same result.  I also tried add/remove programs, and synaptic, all leave the files on there, and one I erased the files manually after last uninstall, I tried reinstalling WINE, and it didn't replace any of the files I deleted, even when I reinstalled it.  Any Ideas?

---

### Post by Patrick793 on 2008-09-27
Open a terminal and enter this command.
```
sudo apt-get remove wine
```
To obviously uninstall wine, and then to remove the configuration files and virtual c:\ drive, enter this.
```
rm -rf ~/.wine
```

---

### Post by forrestcupp on 2008-09-27
You also could have done a 
```
sudo apt-get --purge remove wine
```

Also, Synaptic has an option to remove completely.  Either way, it removes the configuration files.

But Patrick is right.  You didn't even need to remove it and reinstall it.  All you needed to do was delete the hidden directory **.wine** and rerun the configuration for wine.

---

### Post by cha0sthe0ry on 2008-09-29
Thank you for the help with that, I actually had to use the rm -rf command.  I did not know about that.  Until then I had no Idea about how to delete directory trees.  Thanks again

---

### Post by aoanla on 2008-09-30
> **cha0sthe0ry said:**
> Thank you for the help with that, I actually had to use the rm -rf command.  I did not know about that.  Until then I had no Idea about how to delete directory trees.  Thanks again

It's in the man pages for it (if you don't know about man, either:

man command 

gives you a text manual for that command ). In more detail:

-r tells rm to recursively delete things within the target directory.
-f tells rm to not check with you before deleting things - otherwise, you'd have to confirm the deletion of each individual file in the directory structure.

---

