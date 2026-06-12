---
title: "Motherboard/Processor/Video Card recommendations"
date: 2006-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by RyanGT on 2006-10-15
I have been running 32-bit Ubuntu Breezy for 9-12 months.  I really like it.  I am getting ready to build my first 64-bit machine and I would like some help buying hardware that isn't going to cause me headaches.  Can you please recommend motherboards and processors that work well with Ubuntu (Dapper)?  I would like something dual-core, but in the $125-175 range (probably from newegg).  I have heard bad things about socket AM2.  Have those issues been resolved?  Is socket 939 likely to be less of a problem?  I was told that Nvidia nforce chipsets work very well with Ubuntu, but haven't read any success stories about the 500 series.  I would appreciate models numbers of cpu/motherboard combinations that work with little headache.

I think the video card is less of an issue.  As I understand, most Nvidia cards work well.  But I appreciate any recommendations there as well.  I was leaning toward a GeForce 7600 GS.

Thanks,

Ryan

---

### Post by kuja on 2006-10-15
After taking a look at your budget, then taking a look around newegg. I'd say something like a 939 4200+X2 would probably be right around the top of your price range for the processor(~$180). I'm not sure if the AM2 issues are resolved or not, they could be with Edgy, but I've not heard anything. The AM2's and 939's are priced about the same, and ironically, perform nearly the same. The differences being that there are no more 939's being made(last one made was the FX-62, 2.8GHz), and that's about it. Performance is similar. The main differences are that AM2 supports hardware virtualization, and uses DDR2 memory. DDR2 memory is more expensive, and is faster, but its latency is ugly. (The processor really does take advantage of low latencies with its on-die memory controller too, so it's your choice, latency or bandwidth, latency is the cheaper route)

I've had good luck with Asus motherboards. I'm using the A8N-SLI premium and the only real complaint I have is sound related - that is, Alsa treats master as my front speakers, and PCM as master. Weird, anyhow.

That isn't a bad video card, the 7600, I have one laying around somewhere, sold a 6600GT to a friend a while back, and I'm using a 7900GTX(found an openbox one on newegg... so like $100 off, got lucky) right now. All good cards. All _very_ well supported.

---

### Post by russianpirate on 2006-10-15
Budget setup:
[Athlon X2 3800+ or 4200+]("http://www.newegg.com/Product/Product.asp?Item=N82E16819103547")
[EPoX EP-9NPA+]("http://www.newegg.com/Product/Product.asp?Item=N82E16813123246")
[GeForce 7600GT]("http://www.newegg.com/Product/Product.asp?Item=N82E16814150182")

---

### Post by professor_b on 2006-10-15
I have an ASUS A8N5X and an AMD X2 Dual Core 3800+ socket 939. I also have a GeForce 6200 video card that functions flawlessly in dual-head mode. I bought these for compatibility, and they work very well. I think most of this stuff goes pretty cheap now...I know I didn't pay much for it when I built my whole system over the summer.

---

### Post by John.Michael.Kane on 2006-10-15
Heres the board/cpu/gpu I'm using

BioStar T-force 939 has onboard geforce 6100 
Socket 939 3000+

---

### Post by confusimo on 2006-10-15
I got an ECS-915P-A v1.2 from Frys' Electronics for only 12 dollars.  I know that's cheap but hey, if it aint broke don't fix it.  It works great.  And it was brand new, not used.  Seal and everything including manual and what have you.

Added to that 3.06 GHZ Celeoron D CPU and 1gb DDR.  Plus 160GB Sata HD and 250GB stata for backup.  And BFG NVIDIA 256 DDR PCI Express vidoeo card.

And DD 6.06 64 bit Ubuntu OS.

Thanks,
Confusimo

---

