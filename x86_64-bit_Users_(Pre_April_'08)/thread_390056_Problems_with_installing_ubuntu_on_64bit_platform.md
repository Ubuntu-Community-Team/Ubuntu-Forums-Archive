---
title: "Problems with installing ubuntu on 64bit platform"
date: 2007-03-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by fr33ze on 2007-03-21
Hello
I have 64bit Notebook, Dell inspiron 1501, Amd Turion64, hdd 80gb sata, and i have some problems with it.
No1 :
I want to install ubuntu 6.10, and it was all fine with the live cd, the wizard, worked fine, but on step 5, when i had to choose the partition where to install it, he said : no disk available, or something like that. I have 3 ntfs partitions and 10gb free space , for installing ubuntu. 
Is there a problem with my sata hdd or what should i do to resolve this problem ?

No2:
Why couldn't i install ubuntu for 32bit on my notebook ?

Please help me. Thenk you. 
Mihai

---

### Post by mjhb on 2007-03-21
By googling around it seems you need to add some arguments to grub when you boot from the CD. Here's some info: [http://ubuntu1501.blogspot.com/2007/01/installing-ubuntu-on-your-dell-1501.html]("http://ubuntu1501.blogspot.com/2007/01/installing-ubuntu-on-your-dell-1501.html")

>  This is where the magic happens. Ubuntu will not be able to find your SATA hard disk without adding pci=nomsi to the very end of this command line.

---

### Post by dptxp on 2007-03-22
Use the 64-bit version. I am using it and sticking to it. On Turion-64 notebook.

---

### Post by Kilz on 2007-03-22
> **fr33ze said:**
> 
No2:
Why couldn't i install ubuntu for 32bit on my notebook ?

Please help me. Thenk you. 
Mihai


32bit Ubuntu is not guaranteed to install and run on 64bit hardware. There are cases of problems doing it. It isnt the easy way out some people report it to be.

---

### Post by Lonthong on 2007-03-22
both 64bit version of Dapper & Edgy detected & installed fine on my Turion X2 lappy with SATA hard drive
(BenQ P41).

---

