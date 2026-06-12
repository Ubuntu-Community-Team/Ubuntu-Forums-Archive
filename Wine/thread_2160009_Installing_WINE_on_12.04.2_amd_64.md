---
title: "Installing WINE on 12.04.2_amd_64"
date: 2013-07-05
forum: Wine
---

### Post by alvinmoneypit on 2013-07-05
So I have a brande new 12.04.2_amd_64 install with only a z600 printer driver installed above the initial install.  When I go to software center to add programs, the first one I wish to add is WINE immediately get an error that I will have to delete 4 packages to install it, one of them is alien.  

What should I do?  I use alien, too.

---

### Post by gordintoronto on 2013-07-05
When I used Software Centre to install WINE Windows Program Loader version 1.4 in Ubuntu 12.04, nothing was removed. I currently have five different variations of Ubuntu installed, most of them have WINE installed. Installation has never removed another program, to the best of my memory. What were the other programs to be removed?

Did you use "Printing" to install your printer, or some other method?

Oh, I just noticed that there is a default option to add CUPS - BSD commands. Perhaps if you de-select that, it will solve your problem.

---

### Post by alvinmoneypit on 2013-07-05
yes, I installed the CUPS BSD commands as I did not know what exactly they do, so I installed them.  I went ahead and installed anyway and this deleted the 4 programs.  I reinstalled alien and at least one other of the deleted packages came with it (deb-helper, I think).  I don't remember what the others were but seeing them I thought they seemed inconsequential.  I'll post back here if I have any trouble running wine since I reinstalled alien.

Printing didn't work well for my old printer, but I did use it to install the PPD file and I had to download all the 32-bit libs to support it- that is what probably caused the conflict I'm guessing.

---

