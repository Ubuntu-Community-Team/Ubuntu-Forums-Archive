---
title: "chroot questions.."
date: 2005-10-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by kb_ganesh on 2005-10-02
i have installed firefox 32-bit version using chroot as detailed in [this post]("http://ubuntuforums.org/showthread.php?t=24575") ..now, i tried installing the flash plugin by going to a website with flash content..i installed the plugin using the automatic plugin finder service..everything goes fine..but though the window says it is installed, it doesnt show up when the same site reloads..and is not there in about:plugins either..i tried things like installing on a new profile, rebooting and then installing..no use..same thing happens again and again.. any idea why this is happening? and one other thing is that..i would like to know how to ascertain that i am indeed using the 32 bit version and not the 64 bit version when i run firefox32?
thanks for any help!!

EDIT(3/10):- installing x-window-system-core solved the problem :)
noticed that the command line gives an error when i visit any flash site...
```
libXmu.so.6: cannot open shared object file: No such file or directory
```
after a bit of googling, i saw on some debian mailing list, someone's suggestion to install x-window-system-core..i did just that and after that, flash works fine :)

---

