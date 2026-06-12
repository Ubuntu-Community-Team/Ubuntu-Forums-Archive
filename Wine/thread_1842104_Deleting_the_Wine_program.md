---
title: "Deleting the Wine program"
date: 2011-09-10
forum: Wine
---

### Post by alexis44 on 2011-09-10
I want to completely delete the Wine program.  I may have done it wrong.  First I deleted the three programs that I was using from windows.  Then, I went to the Synaptic and deleted the program.  I can still see it in my Home folder under the Wine folder.  It still has the dos devices folder and the Dive C folder.  Will it go away if I just delete the Wine folder, or is there something else I can do to completely delete it? :confused:

---

### Post by ajgreeny on 2011-09-10
If you chose "Completely remove" in synaptic it will have removed the wine program itself, including all the system-wide configuration files and folders for wine.  It will not, however, have removed anything in your home folder, and that is not a bug or anything, it is designed that way.

Remove the hidden folder **/home/*<user>*/.wine** in your home and you will get rid of everything related to wine. Use ctrl+H to see hidden folders and files in nautilus.

---

