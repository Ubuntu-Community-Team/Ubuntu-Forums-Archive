---
title: "Dual-Boot Ubuntu/SuSe"
date: 2006-12-16
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Linuxer-In-Training on 2006-12-16
I currently run openSuSE but would like to switch to Ubuntu.  Just in case, though, is it possible to dual-boot Ubuntu (which will use most of the space) and just keep SuSE on the side just in case?

---

### Post by firecrotch on 2006-12-16
Yeah, it's definitely possible to do this.  When you are installing Ubuntu, it will ask how you want to partition your drive.  Just set it up to use the free space from your existing SuSE partition.  You can use the same swap partition that you used with SuSE.  Basically, you'll just be shrinking the SuSE partition and putting Ubuntu on the free space.  The Ubuntu installer will set up GRUB to dual boot your system.

---

### Post by Linuxer-In-Training on 2006-12-16
Would I have had to set the partition up originally with SuSE to leave empty space, or can I completely do it now with Ubuntu while not deleting anything currently on SuSE?  Also, will I be able to set how much space is allotted to each one?  Thank you.

---

### Post by firecrotch on 2006-12-17
You don't have to leave any unpartitioned space.  The Ubuntu installer will shrink the SuSE partition and install Ubuntu on the new free space.  There will be a slider that lets you choose how much space to devote to each operating system.

---

### Post by Linuxer-In-Training on 2006-12-18
I guess this is why I added "in-training" to my name, but I can't figure out if moving the slider to the left gives Ubuntu more space, or moving it to the right does.  To the left has a lower percentage and the right obviously has a higher percentage.  If I want to give Ubuntu the maximum possible space, do I slide it to the left or right?  Thank you for your patience.

---

### Post by lunamystry on 2007-09-02
I feel this is possibly a SUSE question but I cant find a forum quick enough there are so many. 

I have two hard drives, a 160GB and 80GB. The 160GB has Kubntu feisty installed and the 80GB I yesterday installed SUSE on ( to see how it looks). 
I now cannot boot ubuntu, I think SUSE has its own version of grub or somethng and its not recognizing ubuntu. This may be due to the way that I installed SUSE, i disconnected the 160GB hard drive, installed SUSE on the 80GB then connected them after which is when Ubuntu did not recognize. 
 
How do I dual boot Ubuntu and SUSE after SUSE install.

---

