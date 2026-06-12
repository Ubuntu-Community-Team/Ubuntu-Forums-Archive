---
title: "How do I use the Glide wrapper on Diablo 2 with PlayOnLInux?"
date: 2017-11-01
forum: Wine
---

### Post by santtomas on 2017-11-01
Hi I just installed Diablo 2 via PlayOnLinux in my Netbook and now I  would like to know how to make the Glide Wrapper work. I also install  1.14d patch so I can play on BattleNet, but this patch disabled the  option for the game to automatically select the Glide wrapper. I know  that in Windows there's is a runaround for this which is to add the  parameter -3dfx in the properties of the D2 shortcut. Thing is I don't  know how to do this in PlayOnLinux nor do I know if it's the correct  way. So please can somebody tell me what to do?

---

### Post by Perfect Storm on 2017-11-02
Moved to Wine forum.

---

### Post by santtomas on 2017-11-02
ups, sorry tought the gaming sub-forum would be more appropiate.

---

### Post by adec2 on 2017-11-06
This is actually easy. Open up your playonlinux program and in the window highlight diablo 2 and select configure then under the miscellaneous tab press run a windows executable in this virtual drive then browse to your downloaded nglide exe. Run the installation....
After installation to change the nglide configuration just do the same thing to run a windows executable again and browse to your virtual drive and c:\windows\system32\nglide_config.exe and run that.
to add a command line argument just go back to the tab under general and there's an arguments field where you can add [COLOR=#000000]-3dfx
I use nglide as my glide wrapper[/COLOR]

---

