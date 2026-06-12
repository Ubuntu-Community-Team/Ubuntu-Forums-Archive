---
title: "Athlon 64 X2 3800+ with feisty + kvm"
date: 2007-03-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by lupus247 on 2007-03-06
Hey all,

I feel the need...the need for virtualization speed! According to [dox I encountered on the web]("http://wiki.xensource.com/xenwiki/HVM_Compatible_Processors"), an Athlon 64 X2 3800+ should feature AMD-V (aka SVM) virtualization support. I've got one, yet "svm" does not show up in the /proc/cpuinfo "flags" line after I installed Feisty Herd 5. I see on the KVM wiki ([http://kvm.qumranet.com/kvmwiki/FAQ]("http://kvm.qumranet.com/kvmwiki/FAQ")) that "Some manufacturers disable VT in the machine's BIOS, in such a way that it cannot be re-enabled". 

Anybody know if I'm just trying to roll unmentionables uphill, or if I'm simply missing something silly? I'd really love to use KVM if at all possible, I do a lot with virtualization. (For one thing, it'd be nice to have Flash working again, even if I have to run a VM to get it.)

Oh wait, is it because I've got a Socket 939 mobo and CPU? That would be too bad. It would be the very first time I've ever said "shucks" about this chip, it really has been a honey. It runs Virtual PC under Windows and VMWare Server under Linux wicked fast, but I'd hoped for even faster (and something with sound, which VMWare Server doesn't do)...

Thanks for your help,

rw

---

### Post by RAOF on 2007-03-07
Your chip doesn't have the required virtualisation hardware to use KVM.  Only the socket AM2 (I think) or newer chips do.

---

### Post by lupus247 on 2007-03-07
Thanks. I was afraid of that. It's always somethin', eh? Well, at least I got 14 months out of this box before I had to say "Dang, it won't do that." Must be a record.

rw

---

### Post by bluesox on 2007-03-07
> **lupus247 said:**
> .....and VMWare Server under Linux wicked fast, but I'd hoped for even faster (and something with sound, which VMWare Server doesn't do)...

Thanks for your help,

rw

[delurking & very off-topic]

Umm, I have the same set up (Athlon 64 X2 3800 Skt 939, etc, but using Edgy) and I managed to get VMServer working with sound really easily. You go to the VM | Settings menu and add a sound adaptor. I restarted the VM and it autodetected the linux device no problem and plays audio as you would expect.

Sorry if I got the wrong end of the stick, this is blindingly obvious and isn't useful for you....

[relurking]

---

### Post by lupus247 on 2007-03-07
OMG. Bluesox, you are a winner. And, yes, it was blindingly obvious...in hindsight! That Add... button was staring me in the face the whole time, and I just kept looking at the device list going "Gee, there's no sound device".

My only defense is that I distinctly remember reading on the Web that VMWare Server doesn't provide sound. And if it's on the Web, we all know it's gospel, right?

You rock, Ubuntans. Thank you, thank you. If only I'd thought to ask this before the Jolt Awards were done, I would have spent much less time cussing!

---

