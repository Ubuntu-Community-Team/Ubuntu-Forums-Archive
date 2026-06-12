---
title: "Major help with wireless"
date: 2006-04-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Toddney on 2006-04-10
Ok, I've read through the HowTo's and everything, but can't seem to get my Wireless Adapter to work.  It's a linksys WMP54 G ver. 4.  I've went to the Synaptic Package Manager and searched for "ndis" and installed the one package that came up.

After this i went to System-->Admin, but couldn't find anything about wireless configuration.  Can anyone help me or give me step-by-step instuctions? 

I have a class right now so I'll check this when I get back,  thanks so much for those who can help.  Btw..I am dual-booting Ubuntu/XP Pro and can only access the internet on XP.  I can't get an internet connection on Ubuntu.  Thanks so much!

---

### Post by Toddney on 2006-04-10
Any help at all?

---

### Post by heislord5 on 2006-04-10
Have you tried the wiki?

[https://wiki.ubuntu.com/NetworkDevices](https://wiki.ubuntu.com/NetworkDevices)

Also try the linsys website for drivers.

Also try [www.google.com/linux](www.google.com/linux) search

---

### Post by Toddney on 2006-04-10
yes, i've tried the wiki and my driver isn't on taht other website. 

here's an update:

i copied over the .inf file for the driver for my card.  apparently ndiswrapper is installed but i don't have the gtk for it so i have to use the terminal.  i typed in "ndiswrapper -i bcmwl5.inf" to install the driver..and first time i got an error or something...but then i typed "ndiswrapper -l" and it says "bcmwl5 driver not compatible" or something like that.  so then i tried putting the .inf file in the right folder ..under /ect/ndiswrapper/bcmwl5....but it says i don't have permission.  how can i not have permissioN?  there is only one user adn that's me and i log in under it.  

i'm having major problems for somethign that seems so simple by all these FAQs and guides.  does anyoen have suggestions OTHER than posting a link to a guide that i've already seen a billion times?

---

### Post by taipan on 2006-04-11
type **sudo -s** to gain root access

that should allow you to change the permissions of the file

use **chmod ** to change permissions

---

