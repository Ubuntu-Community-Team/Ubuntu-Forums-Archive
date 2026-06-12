---
title: "x86 64-bit Users:  For the discussion of Ubuntu on the AMD 64 platform."
date: 2008-03-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kevin Funnell on 2008-03-03
G'Day All,
One quick question is the Heading for the Category correct  "For the discussion of Ubuntu on the AMD 64 platform" or for all 64-bit platforms?  Old Kevin

---

### Post by Kilz on 2008-03-03
> **Kevin Funnell said:**
> G'Day All,
One quick question is the Heading for the Category correct  "For the discussion of Ubuntu on the AMD 64 platform" or for all 64-bit platforms?  Old Kevin

That little sentance is a little misleading. It dose not refer to every 64bit platform. An example of this is the Sun Sparc, it is a 64bit chip, it has its own version of Ubuntu and [section of the forum]("http://ubuntuforums.org/forumdisplay.php?f=146").
This section is for every install of the AMD64 version of Ubuntu. While it is named AMD, there are also 64bit intel chips like the core 2 duo and Celeron D that are AMD64 compatible. If you have questions about a specific processor being compatible a look at the hardware manufacturers website will solve it. Intel calls their implementation EMT64.

---

### Post by Kevin Funnell on 2008-03-04
{SOLVED}   Thanks again, Kilz for putting me straight I agree it is misleadin.  I had read about Intel's implementation.  Old Kevin

---

### Post by jespdj on 2008-03-04
*rant mode on*

When is Ubuntu going to stop calling it "AMD64"?

IMO, it should be renamed to x86-64. The name "AMD64" is too confusing for people. The questions "Is this for AMD processors only? So I can't use this on my Intel Core 2 Duo? I have an AMD chip, now I must use the AMD64 version?" are asked too often.

I know that AMD invented the 64-bit extensions and that that's the reason why it's called "AMD64". But there's no reason to keep hanging on to that confusing name. Fedora Linux already calls it "x86-64".

](*,)

---

### Post by dptxp on 2008-03-04
AMD-64 was available long before Intel EMT-64 and helped in development of 64-bit OS for desktop, mainly 64-bit Linux.

I am not too sure about the compatibility of EMT-64 with AMD-64, but they are not identical. But as software were already developed for AMD-64, Intel had to ensure that the 64-bit stuff ran fine on their chips.

So the software has to run on AMD-64 first.

---

### Post by utUtu on 2008-03-04
The Intel EMT64T is not 100% AMD64 architecture but only compatible.  Intel had to do this to avoid paying royalties to AMD, and not put 'AMD64 Technology Inside' label on every Intel cpu.  

I don't see any confusion at all if they care to read the release info.

```

[B]64-bit PC (AMD64) alternate install CD
    Choose this to take full advantage of computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core 2). If you have a non-64-bit processor made by AMD, or if you need full support for 32-bit code, use the Intel x86 images instead[/B].  
```

---

### Post by Origin415 on 2008-03-04
> **jespdj said:**
> *rant mode on*

When is Ubuntu going to stop calling it "AMD64"?

IMO, it should be renamed to x86-64. The name "AMD64" is too confusing for people. The questions "Is this for AMD processors only? So I can't use this on my Intel Core 2 Duo? I have an AMD chip, now I must use the AMD64 version?" are asked too often.

I know that AMD invented the 64-bit extensions and that that's the reason why it's called "AMD64". But there's no reason to keep hanging on to that confusing name. Fedora Linux already calls it "x86-64".

](*,)

This discussion was had in the Gentoo mailing lists not too long ago, before that I was pro x86-64. THe arguement that the devs made basically came down to (besides the extensive work it would take to change to x86-64) that x86 was named that way because Intel did it first and named it that way, so why should we refer to another architecture which AMD now did first by Intel's original name. Besides, Intel doesn't call it x86-64, AMD doesnt call it x86-64, x86-64 as an architecture only exists in the minds of those who wish to keep their architiecture names seemingly vendor neutral.

A side note: EM64T was renamed Intel 64. Rolls off the tongue much better.

---

### Post by jespdj on 2008-03-05
> **utUtu said:**
> I don't see any confusion at all if they care to read the release info.
You're right, but there are so many people that don't read that info, because there are still lots of people in the forums asking questions about it.
> **Origin415 said:**
> Besides, Intel doesn't call it x86-64, AMD doesnt call it x86-64, x86-64 as an architecture only exists in the minds of those who wish to keep their architiecture names seemingly vendor neutral.
IMO, it doesn't matter if Intel or AMD doesn't call it x86-64; Ubuntu should use a (seemingly) vendor-neutral name to avoid the confusion that AMD64 is only for AMD processors, or (the other way around) that if you have an AMD processor you can only use the AMD64 version. (Fedora calls it x86-64 and the Fedora forums, unlike the Ubuntu forums, are not full of people who are confused about which version they should use).

Note that the [AMD64 page on Wikipedia](http://en.wikipedia.org/wiki/AMD64) automatically redirects to the x86-64 page... By the way, that page says:
> Since AMD64 and Intel 64 are substantially similar, many software and hardware products use one vendor-neutral term to indicate their support for both implementations. AMD's original designation for this processor architecture, "x86-64", is still sometimes used for this purpose, as is the variant "x86_64".[13] Other companies, such as Microsoft and Sun Microsystems, use "x64" (as a contraction of "x86-64") in marketing material.

---

