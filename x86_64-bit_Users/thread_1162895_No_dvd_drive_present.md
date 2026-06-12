---
title: "No dvd drive present"
date: 2009-05-18
forum: x86 64-bit Users
---

### Post by hounddog65 on 2009-05-18
Hi Guys
I am new to the Linux world so be gentle.

I have installed Ubuntu 9.04 finding my way around and getting used to things.
I have a dvd burner and  a cd rom. when both are connected the system will not find the dvd drive. if i disconnect the cd drive the I can read the dvd drive. Can you please help with a solution.
I have ran 
sudo lshw -C disk and the drive is not present.

---

### Post by Fir3chi3f on 2009-05-19
If you look at the backs of the drives make sure that the pins on both drives are either both set to CS (cable select) or master and slave. 

My motherboard actually wont except drives UNLESS they are all set to cable select.

hope this helps

---

