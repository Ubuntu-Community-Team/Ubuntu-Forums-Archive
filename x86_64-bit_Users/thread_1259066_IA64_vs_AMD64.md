---
title: "IA64 vs AMD64"
date: 2009-09-05
forum: x86 64-bit Users
---

### Post by lduperval on 2009-09-05
Hi,

When choosing a 64-bit system, what difference in performance and compatibility is there between an Intel and an AMD system?

Also, is an ia64 download warranted (if I choose the Intel) or is i386 sufficient?

L

---

### Post by lduperval on 2009-09-05
Never mind...

L

---

### Post by michael37 on 2009-09-05
:-)

I haven't seen a real ia64 system in several years.

---

### Post by 3rdalbum on 2009-09-06
> **lduperval said:**
> Hi,

When choosing a 64-bit system, what difference in performance and compatibility is there between an Intel and an AMD system?

Also, is an ia64 download warranted (if I choose the Intel) or is i386 sufficient?

L

ia64 is something completely different to what you're talking about. It's Itanium processors.

If you have a 64-bit AMD or Intel processor, then you might as well run a 64-bit operating system. Intel currently has the edge in terms of raw processing power but this is not the only measure you should use when buying a CPU.

---

### Post by bobince on 2009-09-07
I wish the amd64 arch could be renamed to something vendor-neutral. This always confuses everyone.

---

### Post by falconindy on 2009-09-07
> **bobince said:**
> I wish the amd64 arch could be renamed to something vendor-neutral. This always confuses everyone.
Technically, the terms i386 and x86 aren't vendor neutral either. They originate from Intel products.

---

### Post by lduperval on 2009-09-07
Ah! Well thanks for the pointer. I thought the amd64 architecture was for AMD CPUs, not 64-bit CPUs. So I guess I'll install from the amd64 version I have.

What else should I look at before choosing? I currently have an AMD64 machine, but they are getting rarer and rarer. I received a loaner from a store, which was an AMD but the graphics card was an Intel (I think -- or a Radeon, can't remember), and I lost the acceleration features that I have on my nVidia card. Plus, I had sound trouble.

L

---

### Post by bobince on 2009-09-08
Shrug, any modern Core 2/i7 or Phenom II processor is plenty capable for most things you'd ever want to do. Intel are generally considered to have the lead on performance at the moment, though AMD have some niches and as always compete on price. AMD historically had a better early implementation of pure 64-bit code, but I'm not sure that plays much of a part any more.

If you are looking for integrated graphics, the AMD (really ATI) motherboard chipsets are quite attractive. If you're thinking of using a discrete graphics card it doesn't really matter.

---

### Post by FunkyRes on 2009-09-09
> **bobince said:**
> I wish the amd64 arch could be renamed to something vendor-neutral. This always confuses everyone.

If I'm not mistaken, there's some history to it.

Intel basically copied AMD's work but didn't properly credit AMD so Linus stated he would call it the AMD64 port to make it clear that Intel, having failed to come up with an ISA that people wanted, basically copied AMD.

---

### Post by FunkyRes on 2009-09-09
[http://www.theinquirer.net/inquirer/news/1008092/intel-should-be-ashamed-of-itself-over-amd-64-torvalds-says](http://www.theinquirer.net/inquirer/news/1008092/intel-should-be-ashamed-of-itself-over-amd-64-torvalds-says)

---

### Post by FunkyRes on 2009-09-09
OK - I got the history wrong.

AMD came out with 64-bit and the linux distro's called it AMD64 but it was always x86_64 in the kernel source. Linux distro's called it AMD64 because AMD was the company making it, Intel was doing IA64 which was not compatible.

Intel then released what they called IA64e which was really the same thing as x86_64 but didn't give any AMD credit in their release or documentation, but the reason why distro's call it AMD64 is not because of Linus but because that's what they called it when AMD was the one making an x86_64 processor.

---

### Post by dcstar on 2009-09-10
> **FunkyRes said:**
> 
.........
Intel then released what they called IA64e which was really the same thing as x86_64 but didn't give any AMD credit in their release or documentation, but the reason why distro's call it AMD64 is not because of Linus but because that's what they called it when AMD was the one making an x86_64 processor.

Which is fair enough as just about all previous CPU's that hit the market first had their names adopted for that particular architecture.

Intel have enjoyed this for decades when they led the market, so why not other CPU vendors if they get there first?

---

