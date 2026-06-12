---
title: "Gvim not available on x86 64 architacture?"
date: 2008-03-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by portilhe on 2008-03-27
When I choose to add "Gvim" to the applicatios menu it says:
"GVim Text Editor cannot be installed on your computer type (amd64). Either the application requires special hardware features or the vendor decided to not support your computer type."

I also tried to install it via apt-get and aptitude but got the messages:

":~$ sudo apt-get install vim-full
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vim-full is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package vim-full has no installation candidate"

":~$ sudo aptitude install vim-full vim-gnome vim-ruby
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No candidate version found for vim-full
No candidate version found for vim-gnome
No candidate version found for vim-ruby
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done"

respectively...

Any ideas? :S

---

### Post by gaussian on 2008-03-27
Do you have Universe repos enabled?

---

### Post by EnkiduinNZ on 2008-03-27
I have GVim on my x64 box. I *don't* have vim-full. Try dropping that out. I do have th following:

```
vim
vim-common
vim-doc
vim-gnome
vim-gtk
vim-gui-common
vim-runtime
vim-tiny
```

Cheers,

Cliff

---

### Post by portilhe on 2008-03-27
My apologies, but I am too newbie to know what Universe repos are (is?)... 
How can I drop vim-full? I *do* have vim installed (it runs on the terminal window)... just not the gui. It was what was instaled by default from the live dvd.

---

### Post by Jouke74 on 2008-03-27
Also you need to check the main menu editor System > preferences > Main menu.
Gvim won't show up there unless you explicitly check into the accessories menu.

---

### Post by gaussian on 2008-03-27
> **portilhe said:**
> My apologies, but I am too newbie to know what Universe repos are (is?)... 
How can I drop vim-full? I *do* have vim installed (it runs on the terminal window)... just not the gui. It was what was instaled by default from the live dvd.

1. Open System/Administration/Software Sources
2. Select Universe (I would recommend select everything from the Ubuntu tab) from the first tab

Now you can try Synaptic again to find the Vim packages you need.

---

### Post by EnkiduinNZ on 2008-03-28
> **portilhe said:**
> My apologies, but I am too newbie to know what Universe repos are (is?)... 
How can I drop vim-full? I *do* have vim installed (it runs on the terminal window)... just not the gui. It was what was installed by default from the live dvd.

To answer the second part, use synaptic or apt-get to install vim-gnome and vim-gtk (I don't know if you need both) and DON'T select vim-full.

Cheers,

Cliff

---

### Post by portilhe on 2008-03-28
Great!!! :) Thank you all for the input. The Universe repos check did the trick. As you can guess I'm really new to Ubuntu (and quite new to linux).

---

