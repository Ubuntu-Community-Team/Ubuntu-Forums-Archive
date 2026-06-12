---
title: "how to cancel the swap?"
date: 2006-06-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by erez1012 on 2006-06-10
my hdd is doing noise and i want to use him minimal i can!!

so how i want to cancel the swap and then the hdd dont work all the time

thanks

---

### Post by mcduck on 2006-06-10
You can adjust the use of swap on the fly with this command:

```
sudo sysctl -w vm.swappiness=xx
```

xx is a number  between 0 and 100.

0 means that when a program needs more memory cache will be reduced as much as needed. 100 means that old stuff will be moved from cache to swap. Default is 60, and for a machine with enough memory 20 or 10 might be a good setting if you don't want the HDD to spin..

When you have found setting that suits you, add this to /etc/sysctl.conf:

```

# Control how much the kernel should favor swapping out applications (0-100)
vm.swappiness = xx

```

---

### Post by erez1012 on 2006-06-10
as root its write permission denied!!

---

### Post by erez1012 on 2006-06-10
[QUOTE=erez1012]as root its write permission denied!![/QUOTE]
when i write the conf file

---

### Post by xyz on 2006-06-10
Hi-
Would you, by any chance, know what the default value is for a laptop (Toshiba Satellite A40) with 512MB ram?
Thanks.

---

### Post by mcduck on 2006-06-10
> **xyz]Hi-
Would you, by any chance, know what the default value is for a laptop (Toshiba Satellite A40) with 512MB ram?
Thanks.[/QUOTE]
The default is 60, no matter what your setup is. 

As I haven't had a change to test different values on different machines, I cannot tell what's the best value for you. I haven't even changed this on my own machine, as I have 1GB of ram and swap is never used anyway  said:**
> as root its write permission denied!!How are you opening it for editing? Try 'sudo gedit /etc/sysctl.conf'

By default, that file is owned by root, and root also has read and write rights.  And if you are using the default setup of Ubuntu, with no root account, your first created user has same rights if you use the 'sudo' command.

---

### Post by xyz on 2006-06-10
Thanks mcduck
If you haven't had to change anything with your 1GB of ram...I don't see any good reason to change anything with my 512! 
But someday this info may come in handy!

---

### Post by mcduck on 2006-06-11
[QUOTE=xyz]Thanks mcduck
If you haven't had to change anything with your 1GB of ram...I don't see any good reason to change anything with my 512! 
But someday this info may come in handy![/QUOTE]
The default setting is pretty good indeed. Using setting like 10 is still useful if you have a laptop, and you want to allow the hard disk to stop to save power and battery life..

---

### Post by xyz on 2006-06-12
Great! I do have a Toshiba Satellite A40 laptop and setting it to 10 will surely be helpful.
Thanks/Have a good day.

---

