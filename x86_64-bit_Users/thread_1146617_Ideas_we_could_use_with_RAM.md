---
title: "Ideas we could use with RAM"
date: 2009-05-02
forum: x86 64-bit Users
---

### Post by Dwood15 on 2009-05-02
Disclaimer: Don't know where this goes on the forums so i'll put it here. :KS

So, with the new generations of Mobo's and DDR coming out, mostly all 64 bit and with the capability each brings I have SEVERAL ideas which need to be asked and I don't think anyone has asked them.

Live Switching: What if I have a mobo with 16(or 8, or even just 4) GB of RAM?

 Live Switching is what I call it when you switch between Operating Systems without having to shut one down and restart the computer or, alternatively, use a Virtual machine. 

 I know many of you can think of several instances where such a thing would be useful to you. 

  Whether or not each OS could be aware of the other is up to the people who decide this idea is worthwhile.

Thoughts? ideas? love?

---

### Post by cariboo on 2009-05-03
I run XP Pro, Vista and Windows 7 in vm's. I find that XP especially seems to boot faster in a vm than it does in a normal installation.

---

### Post by dcstar on 2009-05-03
> **Dwood15 said:**
> 
Live Switching is what I call it when you switch between Operating Systems without having to shut one down and restart the computer or, alternatively, use a Virtual machine. 


RAM is irrelevant, it is only one component of a very complex underlying set of hardware that makes up a computer, and that computer still needs one solitary Operating System to manage all the other components.

VMs are the current answer to simultaneously utilising one set of physical hardware, and there are very good reasons as to why there is no other alternative solution around at the moment.

One of those reasons is that you cannot have multiple things alter or control the underlying filesystems, such things lead to disaster (as is made obvious by those who insist on using physical filesystems from within a VM while the host OS also uses them - and then jump on forums saying "my system is borked - help me.....").

---

