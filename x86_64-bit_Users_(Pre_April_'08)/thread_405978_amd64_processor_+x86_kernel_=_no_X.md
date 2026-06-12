---
title: "amd64 processor +x86 kernel = no X?"
date: 2007-04-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by go_dragons on 2007-04-10
I have an amd64 and I have been using 64 bit Ubuntu since the days of Dapper. I have never experienced any problems. When Feisty Fawn came out, I decided to do a fresh install of the x86 Ubuntu in order to have better software support and so I wouldnt have to bother with 32 bit libraries, etc. All was fine until just a few days ago when I did an automatic update with synaptic and it automatically updated my computer into a nonworking state. 

What happened with that particular update, is it updated my kernel. now if I want to use X server I have to use only the generic kernel. It worked before on the 386 kernel, but now If I try to use the 386 kernel, X fails to load.  I have now waited through one more kernel update, hoping that the problem would fix itself when the kernel got updated again, but the problem is still here. I am still able to use X only if I load the generic kernel from the GRUB menu.

Should I run dpkg-reconfigure? it doesnt seem like that would do anything since everything is fine using the generic kernel. All of my information is correct on my xorg.conf. Everything works perfectly with the generic kernels, and the problem only exists when I try to run the 386 kernels.  I know other people out there use 32 bit operating systems all the time on 64 bit processors. This one Has me stumped. Can anyone help me out?

---

### Post by mbobak on 2007-04-10
"...X fails to load..."

Ok, specifically, what happens?  What errors do you see in /var/log/Xorg.0.log ??

-Mark

---

### Post by Kilz on 2007-04-10
This is a 32bit and Feisty problem. You might get more help in the [Feisty Section]("http://ubuntuforums.org/forumdisplay.php?f=179") of the forum.

---

### Post by go_dragons on 2007-04-14
**Here is the output of /var/log/Xorg.0.log** I hope it helps.

---

