---
title: "I messed up on the windows size when installing, and now cant resize wine"
date: 2008-03-20
forum: Wine
---

### Post by JaredsaNOOB on 2008-03-20
I made the wine size too small, so when I go into configure wine I cant get to the part that says the size of the window, and in add/remove programs I unchecked the wine box, applied changes, then checked it again and installed it assuming I would get to setup again but no luck. I'm running ubuntu 7.10 any suggestions?:confused:

---

### Post by happyhamster on 2008-03-21
- Copy & paste the next two lines into an empty text file. 

> 
[HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"Desktop"="1024x768"

- Instead of "1024x768" choose the resolution you want. Save the file as "rescue.reg". Open a terminal and navigate to where you saved the file. Then import it into the wine registry using:

wine regedit rescue.reg

---

### Post by MrShurr on 2008-03-21
This happened to me, too. Just run

> rm -R ~/.wine

in the terminal

Thanks to: [http://ubuntuforums.org/showthread.php?t=156571](http://ubuntuforums.org/showthread.php?t=156571)

---

