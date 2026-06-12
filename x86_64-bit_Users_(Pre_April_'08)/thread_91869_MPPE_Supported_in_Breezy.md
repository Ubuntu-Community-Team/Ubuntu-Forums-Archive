---
title: "MPPE Supported in Breezy"
date: 2005-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by alesdoc on 2005-11-18
Hi guys,

i've to connect my laptop through a VPN. I read in a lot a post that MPPE is native supported in the Breezy Kernel.

Why isn't it on my kernel supported?

If i write:

modprobe ppp-mppe

i receive an error message.

Today i try to fix the problem with pptpconfig and then i try to connect my laptop.

Do you know why is mppe on my kernel (i use the standard kernel that is supplied from ubuntu) not supported

Thanks.

---

### Post by dcroal on 2005-11-18
In Breezy the module is now called ppp_mppe_mppc. If you upgraded from an earlier version you may have to edit /etc/modprobe.d/aliases and change 

alias ppp-compress-18 ppp_mppe
to
alias ppp-compress-18 ppp_mppe_mppc

Regards,
Dave Croal

---

### Post by alesdoc on 2005-11-18
...thanks a lot.

I wil try later.

I hope i will connect as soon as possible my laptop.

If i´ve problem can i ask you for help?

Thanks.

Bye

---

### Post by dcroal on 2005-11-18
I don't have AMD 64 hardware but will try to help with generic questions if I can.

DC

---

### Post by alesdoc on 2005-11-19
Hi,

thanks for your help. I'v done

[HTML]sudo modprobe ppp_mppe_mppc[/HTML]

and i receive no message...:) that's mean that the module is supported

I've another question....i hope you can help me.

I followed this post [http://ubuntuforums.org/showthread.php?t=31516](http://ubuntuforums.org/showthread.php?t=31516) to install pptpconfig, but the two repositories for the libraries are down.

Do you know how can i have this two libraries?

thanks

---

