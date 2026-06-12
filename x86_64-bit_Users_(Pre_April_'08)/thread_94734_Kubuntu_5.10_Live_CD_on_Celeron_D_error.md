---
title: "Kubuntu 5.10 Live CD on Celeron D error"
date: 2005-11-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by RedShirt on 2005-11-24
I downloaded the AMD 64 version of the Live CD having been told the EM64T and AMD64 would both use the same AMD64 labelled platform. Having seen a few distros(SuSE and Slackware) with x86_64 and many with ia64 and some with AMD64 versions, I decided to try and track down the differences. Supposedly the ia64(Itanium) would be incompatible and the AMD64 and x86_64 would be compatible with Intel D series processors.

So I decided to try the 64bit Live CD of a few versions because I wanted to test around. So far I have used SuSE and been very pleased, but have not yet tried the 64bit version(awaiting 5 CD download as I type.) But I was able to get the AMD64 Kubuntu Live CD, which I thought would be great for testing it out as well, as Gentoo and Kubuntu both interested me to test anywho. Upon firing it up, I get this message: "Your CPU does not support long mode. Use a 32-bit distrobution." This is very perplexing. Are AMD64 and x86_64 not so compatible after all?

EDIT: I guess I should mention I am using an IBM Laptop, G41, Celeron D 2.4Ghz.

---

### Post by RedShirt on 2005-11-25
Well, after getting the SuSE 10.0 x86_64 and recieving a similar error, I don't think this is a Ubuntu error, I think this is a laptop thinking it is only 32bit error, and so even after a BIOS update recieving the same message on both again, I am going to have a chat with IBM about this.
Sorry to clutter the boards.

---

### Post by Ribs on 2005-11-25
You said your laptop has a Celeron D CPU. Sorry to break it to you, but a Celeron D is only a 32-bit CPU. Therefore, you'd need to download the i386 version of Ubuntu/KUbuntu for it to be of any use...

For reference... a x86_64 release of a distro should work on any ia64 or amd64 based CPU. You can tweak ubuntu to run better on a AMD64 cpu after installation...

---

### Post by RedShirt on 2005-11-26
[QUOTE=Ribs]You said your laptop has a Celeron D CPU. Sorry to break it to you, but a Celeron D is only a 32-bit CPU. Therefore, you'd need to download the i386 version of Ubuntu/KUbuntu for it to be of any use...

For reference... a x86_64 release of a distro should work on any ia64 or amd64 based CPU. You can tweak ubuntu to run better on a AMD64 cpu after installation...[/QUOTE]

From Intel's Website: "Intel Celeron D processors support Intel® EM64T". This is 64 bit, and x86_64 is compatible with the EM64T instructions. Supposedly AMD64 is as well, but I cannot confirm this. I don't know about ia64, my guess is incompatible, but who knows. That also goes for Pentium 4 D, in case you were wondering. The D series is 64 bit enabled, and many people run 64bit distros on them, check out the Linux Questions.org forums, hundreds do it successfully. This is because the D series is 64 bit, assuming it is set up properly, which obviously the laptop I have was not, and the limited BIOS from IBM doesn't allow me to check anything. Which yes, I did update it to their latest.

And being as the processor shows up as "Celeron 2.4" with no mention of D in the BIOS and "Celeron 2.4x2" in Windows XP Pro, again no D mocicor, I would think the laptop was hosed by IBM before it was sent out. As such I have to wait till Monday when Lenovo opens to see what the deal is with that. As from Thursday to Monday, they are closed for holiday and the 24hour support does not deal with misshippment/setup errors.

---

