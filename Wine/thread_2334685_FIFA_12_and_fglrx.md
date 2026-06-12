---
title: "FIFA 12 and fglrx"
date: 2016-08-21
forum: Wine
---

### Post by Dertuny on 2016-08-21
Hello!!

I'm trying to play Fifa 12 with PlayonLinux and really all works very well, but I have low fps if I configure medium or high detail on game. Well, here is the question: glxgears with opensource drivers gives 60fps, but, when I install fglrx writes around 650, then, with fgrlx isntalled, when I try to play Fifa, the game starts, but when I'm in the first selection language screen, and press enter or arrows to select, the system is freezed....that could be happening? What I can do to fix it?

Thank you!

---

### Post by T.J. on 2016-08-21
> **Dertuny said:**
> Hello!!

I'm trying to play Fifa 12 with PlayonLinux and really all works very well, but I have low fps if I configure medium or high detail on game. Well, here is the question: glxgears with opensource drivers gives 60fps, but, when I install fglrx writes around 650, then, with fgrlx isntalled, when I try to play Fifa, the game starts, but when I'm in the first selection language screen, and press enter or arrows to select, the system is freezed....that could be happening? What I can do to fix it?

Thank you!

I'm afraid there is not much that can be done to help you with the FGLRX driver.  The FGLRX driver is no longer maintained or updated by AMD. You pretty much have to take it as is, or not at all. There is a final beta driver, but it has been sitting in beta a long time. I do not recommend using it.  If your card is new enough, use the AMDGPU driver instead.

The best option for playing Windows games is to load a copy of Windows in a KVM, but in order to use DirectX in a KVM, you have to have two video cards - one for Windows and one for Linux.

 As I am aware, the majority of testing for Wine is actually done on Nvidia hardware in any case. The best advice I can give you besides using a KVM is not to use the FGLRX driver. I'd consider an inexpensive Nvidia replacement for your older AMD card instead.  It should work better with Wine.

---

### Post by Dertuny on 2016-08-22
Well, I installed Lubuntu 16 and with amdGPU is better, not perfect, but better. For me, problem solved, is perfectly playable and enjoyable. Thank you!

---

### Post by T.J. on 2016-08-26
Glad to hear it.  I am confused.  As far as I am aware, the AMDGPU driver does not support older hardware. I shall have to investigate further.

---

### Post by QIII on 2016-08-26
Development of the AMDGPU driver is now pushing back the support to earlier GCN versions -- back to GCN 1.0, which will provide support to HD 7000 series GPUs and later.  The improved Radeon driver will support all the others.

There is scuttlebutt indicating that fglrx may make a reappearance, but I don't know if that amounts to more than a curtain call.  fglrx is not gone yet, exactly.  AMD simply did not expend the resources to make it compatible with the version of X Server used by Xenial.  They were busy getting us really useful open source drivers like we've been demanding.

---

### Post by T.J. on 2016-08-28
> **QIII said:**
> Development of the AMDGPU driver is now pushing back the support to earlier GCN versions -- back to GCN 1.0, which will provide support to HD 7000 series GPUs and later. The improved Radeon driver will support all the others.

There is scuttlebutt indicating that fglrx may make a reappearance, but I don't know if that amounts to more than a curtain call. fglrx is not gone yet, exactly. AMD simply did not expend the resources to make it compatible with the version of X Server used by Xenial. They were busy getting us really useful open source drivers like we've been demanding.


Hello again, Qlll!  Good to see you. 

That AMDGPU is getting better support is good to hear.  As far as FGLRX, I sincerely hope it remains buried forever.  The breakaway was painful enough without prolonging it.  It was always buggy, especially on two displays or more.  I have no desire to see it return, and cause more support issues for users.  I agree with you.  They should stick with the new driver.

It is just as well. I have walked away from AMD's video hardware, and I encourage others to do so as well.  Not only are Nvidia's cards more compatible with Steam and its Linux offerings, they are now priced close to AMD's, work better with Wine, and generally speaking consume less power and generate less heat.  The fact that AMD's new card violates PCI-e standard unless you adjust it, was the final "the straw that broke the camel's back" of this once loyal AMD fan.  I can't believe they did something so egregiously stupid.  I've always been a strong believer in adhering to specifications because you don't know how much leeway the rest of your hardware is actually engineered for.  The new RX 480 drawing too much power from the PCI-e slot by default is asking for trouble. I expect in a year or two, AMD may even see a class action lawsuit if it fries enough motherboards belonging to non-techies.

---

### Post by QIII on 2016-08-29
The RX 480 power issue is an acknowledged design error and not a nose thumbing at the PCI-e power standard.  That is little consolation to someone spraying a fire extinguisher on his computer, though.

---

### Post by T.J. on 2016-08-29
> **QIII said:**
> The RX 480 power issue is an acknowledged design error and not a nose thumbing at the PCI-e power standard.  That is little consolation to someone spraying a fire extinguisher on his computer, though.

Honestly, I can't see it as a "design error."  That is not something that happens by accident.  Engineers don't design hardware without rigorously testing it. No, I don't believe for a second that this was an accident or oversight.  Nor do I believe it was done in ignorance.  Whatever else they might be, these people are professionals, and they know how to use a multimeter.

I think they decided that motherboard makers must build in a large enough voltage safety margin that no one would notice that they they were violating PCI-e standards.  Unfortunately for them, that is not always true.  Not all motherboards are created equal - and AMD got caught ignoring that fact.

That's not to say that Nvidia hasn't had their own kerfuffles in the past.  There was an instance of a bad driver that fried hardware, and another of failing to adhere to DirectX standards that were corrected in software after the fact.  These are bad, but they were software related, not engineered hardware. Software - especially Windows - is hard to debug when you don't have source code.  AMD's transgression takes it to a whole new level with hardware designed to break the standard.  The problem is that their actions create a real quandary for the rest of us.  The entire computer industry depends on adherence to standards in order to function.  The fact that AMD violated that trust for a marginal performance edge is going to taint everything they do for some time, at least among those of us who are sticklers for standards.

It's speculation, but I think that is one of the reasons that Zen was delayed again. They wanted to put some distance between it and this debacle, because AMD's future depends on its success.

What frightens me is that that thinking that you can ignore standards when you please is becoming pervasive in the industry, with the rise of mobile devices. Where the entire system is engineered end to end by one vendor, you can ignore cooperative standards.  Without those cooperative standards, proprietary hardware becomes more specialized, and prices go up on everything - the 1970s all over again.

---

### Post by QIII on 2016-08-29
Let's not forget the NVIDIA GTX 1080 power issue incident.

I doubt either NVIDIA or AMD thought they could get away with something without being caught, given how thoroughly things are reviewed on the web.

Again, that is little consolation to those who encounter catastrophe.

---

### Post by T.J. on 2016-08-30
> **QIII said:**
> Let's not forget the NVIDIA GTX 1080 power issue incident.

I doubt either NVIDIA or AMD thought they could get away with something without being caught, given how thoroughly things are reviewed on the web.

Again, that is little consolation to those who encounter catastrophe.


I'm afraid I haven't heard of any 1080 issues, but it is so costly that it is outside my purview. Please explain further.

---

