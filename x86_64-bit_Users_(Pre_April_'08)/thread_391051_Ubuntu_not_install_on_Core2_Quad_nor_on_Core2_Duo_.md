---
title: "Ubuntu not install on Core2 Quad nor on Core2 Duo 64 bit"
date: 2007-03-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by anton_most_muscular on 2007-03-22
Hi,

I have a 64-bit Core2 Quad and a 64-bit Core2 Duo desktop, and Ubuntu will not install on either of them.

Duo:
Install Edgy from desktop CD and menu come up,
but when install blue progress bar not displaying correctly and eventually stops
with tty error; symptomatic of motherboard not-supported

Quad:
Install Edgy from desktop CD and menu comes up,
but when install blue progress bar not displaying correctly and eventually stops
no further progress, no error message

I have seen similar posts, suggesting that this may be a CD-drive problem, but I don't think so.
More likely the hardware (motherboards?) is too new?

I have seen no evidence of anyone running Ubuntu on a Quad-core machine.

I want to use Kubuntu on my Quad, as the current Fedora C6 64 install is not handling my video conferencing software properly, and I know that it works properly on Kubuntu.

Is there a simple solution??

Could it be that I just need a newer kernel to support my hardware (I see Fedora is much more recent than Edgy) - could I try Feisty?

Thanks for any help

---

### Post by laredo7mm on 2007-03-24
I would try Feisty.  The Beta just came out and I have been running Feisty since Herd 3.  I run the 64bit Feisty on three dual core AMD's and they run Folding@Home 24/7.  No problems here.

Feisty is runing the 2.6.20 kernel and I think Edgy is down at 2.6.16 or something like that.  The kernel in Feisty has no problem with my Gigabyte Mother boards.  They all have the nforce 6150 or 6100 north bridege and the 430 south bridge.

Try out Feisty on the live CD or DVD, it can't hurt.

---

### Post by Unoone on 2007-03-24
> **laredo7mm said:**
> I would try Feisty.  The Beta just came out and I have been running Feisty since Herd 3.  I run the 64bit Feisty on three dual core AMD's and they run Folding@Home 24/7.  No problems here.

Feisty is runing the 2.6.20 kernel and I think Edgy is down at 2.6.16 or something like that.  The kernel in Feisty has no problem with my Gigabyte Mother boards.  They all have the nforce 6150 or 6100 north bridege and the 430 south bridge.

Try out Feisty on the live CD or DVD, it can't hurt.

I installed Edgy 32 and Edgy 64 bit systems on my Intel Core 2 Duos. I have had many problems that are data related such and permissions dropping, Firefox issues, etc. These problems were not present in Dapper. Dapper is a bit old as far as newer motherboard support and Edgy is well edgy. Do you think that moving to Feisty will offer better support for my new Intel Core to Duo's? 

BTW, I'm testing Dreamlinux on one of these computers. I can say that it's no replacement for Ubuntu but it's a bit more receptive to my new hardware. It's an unsatisfying 32bit hold over for my newer hardware instead of going back to Dapper. I really need a more stable version of Ubuntu right about now. Feisty looks good. You seem to be having much success with it what do you think?

I would like to upgrade to Feisty if it's not too early to do so.

---

### Post by uputer on 2007-03-25
I think it's due to the JMicron controller in most core2duo motherboards.   Just google or search the forum for this.   I did a search and that's what seems to be the case.  I was interested in this because I was thinking of buying a core2duo machine and installing ubuntu on it.   

It might be fixed at 2.6.20-13?   But, I'm a noob (with linux) and I don't know how you get to that version.   Can anyone explain?   They are probably getting close to solving the problem from what I've read.   It's a kernel problem and a bug, I think, as a google on JMicron and linux or any distro will get you several hits about this bug.  

I think I'm going to wait until it's truly fixed.

---

### Post by anton_most_muscular on 2007-03-25
Thanks for your replies.

I can tell you that Fedora Core 6 64 **definately** works, which is using the 2.6.19-X kernel.

If it is indeed a kernel problem, then I will be able to tell you in a short while, as I am currently downloading Feisty beta 2, which has an even newer kernel.

I agree; it would be worth waiting for a reliable Ubuntu release (mid April I believe) before buying new hardware, but until then, I can assure you that the Fedora C6 will work with just a bout any hardware you can throw at it.

Watch this space.

---

### Post by enopepsoo on 2007-03-25
Wow I've gotta upgrade.  I am still using dapper.  I think things would be better on the new system.

---

### Post by anton_most_muscular on 2007-03-25
Nope - still doesn't work, even with Feisty.

The [release notes for Feisty]("http://www.ubuntu.com/news/Ubuntu704Beta") list a known bug:

*Systems with JMicron IDE(PATA) chipsets may experience a crash on boot. This was not fixed in time for beta release, but a planned kernel upload just after release will rectify the problem. A work around has not been tested, but would involve blacklisting the `generic` kernel module. [https://launchpad.net/bugs/84964](https://launchpad.net/bugs/84964)*

...which sounds a lot like our problem. I can't actually get to that 'work around' page through my network, but I'll have a look later on.

It looks like the problem may be fixed with the final Feisty release iun a few weeks (it better be! as otherwise it means Ubuntu just won't work on the great bulk of the new generation of computers).

---

### Post by Kilz on 2007-03-25
> **enopepsoo said:**
> Wow I've gotta upgrade.  I am still using dapper.  I think things would be better on the new system.

IMHO Dapper is better than Edgy, It will also be supported longer. I would hold off of Feisty , at least untill its released. While things are in development , sometimes things break.

---

