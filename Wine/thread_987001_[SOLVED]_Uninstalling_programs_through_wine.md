---
title: "[SOLVED] Uninstalling programs through wine"
date: 2008-11-19
forum: Wine
---

### Post by Jacob Collstrup on 2008-11-19
I don't know if the title makes sense...but here we go,

I have installed textpad on ubuntu (hardy heron) through wine. And it doesn't work after I updated wine. So I thought I'd reinstall textpad. But it doesn't seem to uninstall. I searched for 'uninstall through wine' and I found a topic telling that wine does uninstall things, but just leaves the shortcuts. But I seem to still be able to 'run' the program even though its uninstalled.

So, how do I completely remove textpad from my system? I installed it through wine...

Jacob

---

### Post by Meow27 on 2008-11-19
remove the shortcut by your menu preferences. then go to your home folder, press ctrl+h, go to .wine, go to ur c drive then your program files and manually remove the program (a dirt way to do it but if an automatic installer wont work then i dont see another solution...but again i myself am not very fluent in Wine)

---

### Post by Jacob Collstrup on 2008-11-19
> **Meow27 said:**
> remove the shortcut by your menu preferences. then go to your home folder, press ctrl+h, go to .wine, go to ur c drive then your program files and manually remove the program (a dirt way to do it but if an automatic installer wont work then i dont see another solution...but again i myself am not very fluent in Wine)

I don't know how to remove anything from the wine menu...

Jacob

---

### Post by Meow27 on 2008-11-19
right click the menu bar 
click "edit menus"
there is an items column and a menu column 
focus on the menu column
click the arrow next to the wine icon
do the same for the programs folder
uncheck what you need (you can do that from the program files folder as well but this should suffice)

i dont know of any permanent way to do this....

---

### Post by Jacob Collstrup on 2008-11-20
> **Meow27 said:**
> right click the menu bar 
click "edit menus"
there is an items column and a menu column 
focus on the menu column
click the arrow next to the wine icon
do the same for the programs folder
uncheck what you need (you can do that from the program files folder as well but this should suffice)

i dont know of any permanent way to do this....

I can't find this 'menu bar' you speak of...is it under 'Configure Wine', if so its missing...there must be something I have overlooked...

Jacob

---

### Post by Brain-free on 2008-11-20
You have to right-click on the upper bar where it says "Applications", "Places" etc.

But, in case you don't have one, do:
```
sudo alacarte
```
give your password and then follow Meow27's instructions from the third line:

[I]there is an items column and a menu column
focus on the menu column
click the arrow next to the wine icon
do the same for the programs folder
uncheck what you need (you can do that from the program files folder as well but this should suffice)[/I]

---

### Post by Jacob Collstrup on 2008-11-20
Thanks,

Made it work now (the removing shortcut part), now I just need to remove the folders.

I really like that 'alacarte' command! :grin:

Jacob

---

