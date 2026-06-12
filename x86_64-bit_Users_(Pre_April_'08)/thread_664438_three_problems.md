---
title: "three problems"
date: 2008-01-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by supersonic on 2008-01-11
I installed 32bit version on my 64 processor version.Is this ok ?

I have very big problems to watch TV on my Ubuntu, I cannot setup my TV card.Can anyone help me.
The card is Asus MyCinema p7131 hybrid.

This showes up when I start my ubuntu, and everything is ok, but why is this ?Can I setup this, so this wont buggin' me anymore?

Starting up .......

[         0.520000] ..MP-BIOS bug: 8254 timer not connected to I0-APIC




Thanks in advance,


Eno from Montenegro.

---

### Post by dcstar on 2008-01-12
> **supersonic said:**
> I installed 32bit version on my 64 processor version.Is this ok ?

I have very big problems to watch TV on my Ubuntu, I cannot setup my TV card.Can anyone help me.
The card is Asus MyCinema p7131 hybrid.

This showes up when I start my ubuntu, and everything is ok, but why is this ?Can I setup this, so this wont buggin' me anymore?

Starting up .......

[         0.520000] ..MP-BIOS bug: 8254 timer not connected to I0-APIC


1) Yes, but you are wasting the capabilities of your hardware.

2) Don't know, it may not be supported - do a search.

3) Don't worry about it - a lot of BIOS put out this message without any adverse outcomes (like mine).

---

### Post by supersonic on 2008-01-12
thank you very much.

I'll install now 64bit version ;)

---

### Post by guren on 2008-01-12
Hmm for the tv tuner, i don't have the same card but i'm using **tvtime** to watch TV.

try to see if your tv tuner was detected
> lsmod | grep video

then install tvtime. try to point tvtime to /dev/video0
Enjoy!

---

