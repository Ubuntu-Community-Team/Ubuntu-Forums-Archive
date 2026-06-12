---
title: "Which Kernel should I be using. 4gb. 64bit gusty"
date: 2007-11-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Underpants on 2007-11-05
[[IMG]http://img249.imageshack.us/img249/5268/4gbgustyke2.th.png[/IMG]](http://img249.imageshack.us/my.php?image=4gbgustyke2.png)

This is what is detected


Linux boxen 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux


Do I need to install a different Kernel for my machine to take advantage of everything it's got?

---

### Post by PmDematagoda on 2007-11-05
According to your title you are asking if you can use all of your RAM, so with the kernel you have right now, yes, you can use every bit of your RAM using Ubuntu 64 bit, but according to your phrase:-
> 
 Do I need to install a different Kernel for my machine to take advantage of everything it's got?


Could you please elaborate on what you want the kernel to take advantage of in your PC?

---

### Post by rsambuca on 2007-11-05
> **veerakumar said:**
> You have quite a recent kernel

[[img]http://sfx-images.mozilla.org/affiliates/Buttons/firefox2/foxkeh-fx2-300x250.png[/img]](http://www.spreadfirefox.com/?q=affiliates&amp;id=211983&amp;t=223)

Since firefox is installed by default in Ubuntu, and these are the Ubuntu forums, the picture and link in  your post is nothing more than annoying.

---

### Post by orthopod on 2007-11-05
You are running a SMP core which are designed for multi-core chips, also 64 bit.  If you do have a dual core, or lucky ******* - quad core, then I'd say yes.

---

### Post by dcstar on 2007-11-06
> **Underpants said:**
> 
.........
Linux boxen 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux


Do I need to install a different Kernel for my machine to take advantage of everything it's got?

I recommend the "-rt" versions of all the Ubuntu kernels, they are optimised for Real Time performance (more interrupts so your keyboard responds better under load etc.) than the genericl or server kernels.

Just find them in Synaptic and install then try them.

---

