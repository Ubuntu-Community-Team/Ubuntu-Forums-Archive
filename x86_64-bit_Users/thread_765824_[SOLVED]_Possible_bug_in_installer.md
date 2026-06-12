---
title: "[SOLVED] Possible bug in installer?"
date: 2008-04-24
forum: x86 64-bit Users
---

### Post by adza on 2008-04-24
Hi there, just thought i would share my experience this morning with the install of Hardy, and see if anyone else experienced this...

I installed of the live-cd (after successfully running the cd check), using the guided partitioner (i usually do this with every release.. consider a cleanup!), using full disk install and formatting the gutsy disk - 160GB Maxtor IDE drive, running as master on the IDE bus. Install appeared to go smoothly, really nicely in fact and in no time at all i was rebooting with anticipation of the hardy experience! 
This is where things started to go bad, when i got the the grub bootloaded screen, i selected the 8.04 option to boot from and got the error:

Error 17: Unable to boot from partition.

This is when i then selected the windows partition to boot from (a slight panic starting to set in) and got another error;

Error 13: Incorrect executable cannot boot from exe

Okay, really concerned here.. So another go at the installation was attempted - same results. 

To fix this, i installed for a third time, this time using the manual installer - and all good!!! 

So short story, manual partitioner was all good, the guided partitioner however was a disaster! So if anyone is reading this in the state of panic that i was, try the manual partitioner!! 

System specs: AMD64 4200, Asus A8NSLI Delux, Nvidia 7600GT, Maxtor 160GB IDE boot drive....

---

