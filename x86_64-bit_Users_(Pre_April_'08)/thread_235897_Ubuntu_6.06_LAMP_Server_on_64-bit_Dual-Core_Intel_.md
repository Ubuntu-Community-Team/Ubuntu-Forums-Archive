---
title: "Ubuntu 6.06 LAMP Server on 64-bit Dual-Core Intel Xeon “Woodcrest” ?"
date: 2006-08-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by yellowtip on 2006-08-13
Hi,

I need to setup a high performance production server for a web appplication that runs on Apache2,MySQL5 and PHP5.

My Plan is to install the Ubuntu 6.06 LAMP Server.

The server has *2* 64-bit Dual-Core Intel Xeon “Woodcrest” processors.

My main questions are:
- Do I need the 64bit Ubuntu Server CD for these processors? Or does that CD only work for AMD processors.
- Do I need to install a special kernel for a multi-processor setup? Or Does Ubuntu Server install this automatically?
- Does anybody have a similar setup? Could you please offer any advise on the installation?

Thanks in advance.

---

### Post by Kilz on 2006-08-13
> **yellowtip said:**
> Hi,

I need to setup a high performance production server for a web appplication that runs on Apache2,MySQL5 and PHP5.

My Plan is to install the Ubuntu 6.06 LAMP Server.

The server has *2* 64-bit Dual-Core Intel Xeon “Woodcrest” processors.

My main questions are:
- Do I need the 64bit Ubuntu Server CD for these processors? Or does that CD only work for AMD processors.
- Do I need to install a special kernel for a multi-processor setup? Or Does Ubuntu Server install this automatically?
- Does anybody have a similar setup? Could you please offer any advise on the installation?

Thanks in advance.
The amd64 or 64bit server cd will work with your processor. There is a xeon kernel in the repositories you may be interested in using once the install is done.
64bit kernels are all smp from what I have read. So you wont need anything extra for the multi processor setup from what I understand.
The only advice is be aware the server cd will not install a desktop. Most people who want a server know this. But some dont and are surprised to find only the command line when the install is finished.

---

### Post by yellowtip on 2006-08-14
Kilz,

Thanks for the info!

---

### Post by Kilz on 2006-08-14
> **yellowtip said:**
> Kilz,

Thanks for the info!

Your welcome, dont be put off by the no desktop, one can be added with a single command if you want one. Though I would recommend one of the lighter desktops like Xfce for a server.

---

### Post by yellowtip on 2006-08-26
One more question on this topic:

Does Ubuntu actually take advantage of the dual cores?

In other words: if you have a 2 processor Dual Core Xeon setup...will Ubuntu use this as if you had 4 processors?

---

### Post by fistfullofroses on 2006-08-26
If you were going to want a desktop.... I wouldn't even bother with trying to get XFCE or Gnome or KDE... I would go with fluxbox, or evilwm. Even fluxbox would be a bit much for a server. It is likely that ratpoison or evilwm would work best.

---

### Post by yellowtip on 2006-08-27
fistfullofroses,

I'm afraid I can't follow you at all. What are Fluxbox/evilwrm and how do they relate to my question about dual core processors?

---

### Post by fistfullofroses on 2006-08-27
The other guy mentioned that he would run some GUI that is light weight on a server. If I were running Ubuntu on a server I wouldn't even bother with a desktop environment. I would use a window manager... which is what fluxbox and evilwm are.

---

### Post by yellowtip on 2006-08-27
Thanks for that info. Could you please tell me what the difference is between a desktop and a window manager?

---

### Post by kuja on 2006-08-28
I doubt the amd64-generic kernel will take advantage of hyperthreading (I could be wrong), but the amd64-xeon kernel definitely should.

---

### Post by mw888 on 2006-08-29
> **kuja said:**
> I doubt the amd64-generic kernel will take advantage of hyperthreading (I could be wrong), but the amd64-xeon kernel definitely should.
The Core processors don't support Hyper-Threading.

---

### Post by kuja on 2006-08-29
Hmm, when googling around about it, I think I ran into something saying that it was being disabled due to some sort of security issue, that wouldn't be why would it?

---

