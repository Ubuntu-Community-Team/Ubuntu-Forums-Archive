---
title: "I have Broke Wine need help please"
date: 2014-05-27
forum: Wine
---

### Post by andrea_dixon2 on 2014-05-27
:(Hi, I was Installing a program and I broke wine, I'm using Xubuntu I have went to the software center and removed all the wine programs but, when I reinstall its still broken, how do I get ride of it all and start a new installation.:)
Thanks

---

### Post by deadflowr on 2014-05-27
When you uninstall wine, try removing the .wine folder as well.
A simple command would be
```
rm -rf ~/.wine
```
Then reinstall wine, and that folder will get re-added cleanly.

If I was more familiar with xubuntu's file manager(thunar), I'd say to use that to remove the folder.
But, like I alluded to, I'm not that familiar with it. 
(I've used it, but not to the extend of knowing it's quirks)
I think, though, that you can access that folder in the file manager(thunar) with the common keyboard shortcut,  ctrl + H.
Which will show hidden folders and files.
(the dot before a folder/file means that it is hidden from normal viewing)

---

### Post by andrea_dixon2 on 2014-05-27
Ok Im going to try that now thanks.

---

