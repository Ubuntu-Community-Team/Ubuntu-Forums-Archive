---
title: "How to allow myself to delete something from filesystem"
date: 2008-05-09
forum: x86 64-bit Users
---

### Post by DachaArh on 2008-05-09
I need to delete firefox 3 folder and profile from firefox 2 but now I can't

---

### Post by Jouke74 on 2008-05-09
Well the way I do those sort of nasty things is to open a terminal and type "sudo nautilus". This will open Nautilus in "root" mode and you can delete or make files and directories all over the linux root system. Mind yourself greatly, this is **very dangerous**. If you do something wrong accidentally you cannot undo things.

---

### Post by Aearenda on 2008-05-09
You can delete your own firefox3 profile from nautilus without sudo - just click on view->show hidden files and you will see all the hidden folders. All filenames starting with a dot are hidden. Look in .mozilla/firefox.

You should NOT just delete the firefox3 program folders - it will leave things in a mess. Instead, use system->administration->Synaptic package manager and remove the firefox3 package.

Also, to start nautilus as root, you can press ALT and F2, type ```
gksudo nautilus
```No need for a terminal. As Jouke74 says, this is dangerous - you can easily render your system unbootable if you make a mistake.

And another edit: you don't need to delete it - see [http://ubuntuforums.org/showpost.php?p=4901423&postcount=2](http://ubuntuforums.org/showpost.php?p=4901423&postcount=2)

---

