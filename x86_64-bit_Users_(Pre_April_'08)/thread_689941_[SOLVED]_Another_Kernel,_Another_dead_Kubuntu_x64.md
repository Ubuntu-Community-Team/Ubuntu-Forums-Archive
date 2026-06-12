---
title: "[SOLVED] Another Kernel, Another dead Kubuntu x64"
date: 2008-02-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by hangfire on 2008-02-06
Adept brought home kernel 2.6.22-14-generic today, and it's installer immediately made a mess of my /etc/grub/menu.lst and set itself, and the previous kernel to boot off of a root of hd(1,0). Well, on my machine, which does have two disks, /boot is (hd0,0). Quick use of the 'e' key in grub got me here, but...

Why does it keep doing this?

Is there any way to stop it?

Where do I file the bug report?

I suspect that my "problem" is that I boot off of SATA but there is an IDE drive present with an old Linux on it. Or maybe it's 64 bit. Or the combination. I don't know.

Frustrated and annoyed,
-HF

---

### Post by Yellow Pasque on 2008-02-07
I got tired of this BS too. I rolled my own 2.6.24 kernel with only the stuff I needed and uninstalled the Ubuntu kernel stuff. Problem solved and system runs much faster. That solution isn't for everyone though...

---

### Post by John Jason Jordan on 2008-02-07
> **hangfire said:**
> Adept brought home kernel 2.6.22-14-generic today, and it's installer immediately made a mess of my /etc/grub/menu.lst and set itself, and the previous kernel to boot off of a root of hd(1,0). Well, on my machine, which does have two disks, /boot is (hd0,0). Quick use of the 'e' key in grub got me here, but...

Why does it keep doing this?

Is there any way to stop it?

Where do I file the bug report?

I suspect that my "problem" is that I boot off of SATA but there is an IDE drive present with an old Linux on it. Or maybe it's 64 bit. Or the combination. I don't know.

Frustrated and annoyed,
-HF
I used to have problems like that too - every time there would be a kernel upgrade it would set the machine to boot off of a different partition. I finally learned where the problem was and fixed it. It seems that the menu.lst file contains lines with no #, lines with one #, lines with two #s, and lines with three #s. Lines with one # are ignored unless you are upgrading the kernel, then grub reads them. One of the lines is #groot=, and it was set to the bogus partition. I changed it to the correct partition and haven't had a problem since.

---

### Post by Yellow Pasque on 2008-02-07
True, you can edit menu.lst, but Ubuntu shouldn't bork your already customized menu.lst just because you got an updated kernel.

---

### Post by utUtu on 2008-02-07
> **Temüjin said:**
> True, you can edit menu.lst, but Ubuntu shouldn't bork your already customized menu.lst just because you got an updated kernel.

It does because of the stupid 'update-grub'.

---

### Post by stringkarma on 2008-02-07
The top part of /etc/grub/menu.lst is what will create a new grub when you do a grub update or when you get the new kernel. Edit this part (I needed a kernel option) and then it will appear after updates. I know there are threads on how to do this. I will find them if you can't, just let me know.

---

### Post by Yellow Pasque on 2008-02-07
> **stringkarma said:**
> The top part of /etc/grub/menu.lst is what will create a new grub when you do a grub update or when you get the new kernel. Edit this part (I needed a kernel option) and then it will appear after updates. I know there are threads on how to do this. I will find them if you can't, just let me know.
Ah, I see it now, in /boot/grub/menu.lst
> ## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

Thanks, bro! I like to keep the stock Ubuntu kernel as a backup. This will make it less annoying to update.

---

### Post by hangfire on 2008-02-13
Setting groot from the wrong value to the right value of (hd0,0) worked, I just survived a kernel update unscathed. I have no idea how that comment was created with the wrong value in the first place.

-HF

---

