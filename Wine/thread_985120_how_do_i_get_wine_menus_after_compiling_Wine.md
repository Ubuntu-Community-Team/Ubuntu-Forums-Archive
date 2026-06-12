---
title: "how do i get wine menus after compiling Wine?"
date: 2008-11-17
forum: Wine
---

### Post by Meow27 on 2008-11-17
i have been been trying out some patches with Wine lately, obviously i have been compiling it (with the patches) and trying it out... the problem is si that when i remove wine (from synaptic)and then do make install for the patch, i lose my menus and can only use the terminal (i can run programs by double clicking as well.)

is there some way i can install a patched version of wine WITH getting the menus and everything?

thanks in advance 

(sorry if this is spam. i tried searching but nothing came up)

---

### Post by k@e on 2008-11-17
I had the same problem some time ago. By investigating the officially supported Wine package in Ubuntu's repos, I created a small package to bring back the Wine shortcuts in gnome menu.

Download this archive, extract it and execute "install.sh". Alternatively copy all .desktop files to ~/.local/share/applications.

```
http://www.megaupload.com/en/?d=VW2MXGD0
```

---

### Post by Meow27 on 2009-12-09
does anybody know how to do this plainly with the source?

i mean scott's debs have the pretty icons.....

---

