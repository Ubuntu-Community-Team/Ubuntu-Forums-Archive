---
title: "Can Ubuntu take advantage of Core 2 Duo Q6600? Or should I put it in Core 2 Duo E4700"
date: 2009-03-03
forum: x86 64-bit Users
---

### Post by ncllc on 2009-03-03
I have purchased 2 Dell PC's:

First PC runs Intel Core 2 Quad Q6600 2.4GHz, second PC runs Intel Core 2 Duo E4700 2.6GHz.

I'm going to use one PC for the latest 64-bit version of Ubuntu. I read through multiple forums and still very unsure on whether Ubuntu 64-bit can fully take advantage of the Core 2 Quad Q6600. Can somebody clarify this?

If Ubuntu 64-bit can only utilize some computing power of the Core 2 Quad Q6600, then it makes more sense to put it in the Core 2 Duo E4700 instead.

Thanks.

---

### Post by balaknair on 2009-03-03
I've never heard of any issues with Ubuntu(or any Linux) being unable to utilize quad core set ups- in fact Linux runs on many(nearly all) of the top 500 Supercomputers with thousands of cores. Ubuntu 64 bit can handle upto 16 cores just fine, to the best of my knowledge, and though Ubuntu can utilize pretty much all the computing power you can throw at it, Linux is designed to use hardware resources economically and will run just as well on less powerful computers.

I'm curious as to where you got the idea that> Ubuntu 64-bit can only utilize some computing power of the Core 2 Quad Q6600

Could you post a link to the forum/s where you read this? Especially since I'm considering switching to quad core architecture myself.

---

### Post by fjgaude on 2009-03-03
I think many of the apps don't know much over two cores, maybe even only one. But if you are in a multiuser arena then more cores for many open apps, running.

I'm my own user, all alone, and chose to go with a fast, dual-core instead of quad. I'm happy. Notice my tag line.

---

### Post by tgalati4 on 2009-03-03
You're correct.  Most applications can't really use 4 cores.  Specialized applications such as rendering, some music/video production, and scientific number crunching can benefit from quad core.

You will get better performance by using a fast disk drive (such as a WD Raptor), overclocking your memory access (within reason, test extensively with memtest).

Depending on your needs and the price difference, I would consider overall system performance not just number of cores.

---

### Post by WiFi Ed on 2009-03-03
I have a Core2Quad Q6600 running Ubuntu 8.10 x64, Vista x64 and Windows 7 x64 and Ubuntu utilizes the 4 cores at least as well as Windows does. Which is to say, not very much at all unless the specific application running is multi-core aware.

In Windows, the only application that maxs out all 4 cores is rendering a video to DVD with Windows Moviemaker and the Vista DVD application. Then, it is a glorious sight to see all 4 cores running at 95% for 20 minutes or so. Otherwise, one core or another may max out for a moment or two while opening/closing windows while the other three bounce around at 2 or 3 percent.

In Ubuntu, watching streaming video from CNN or Fox will keep one core busy at 50-75% while the others idle away.

To be fair, my previous CPU, a Core2Duo 2.13GHz unit behaved in a similar manner with one core maxing out when opening/closing apps while the other idled. Sometimes both cores might go up to 40-50% but it was rare to see both near 100% unless rendering a video.

I agree with tgalati4 in that a fast hard drive like the Velociraptor will show a greater, across the board speed improvement. That's why I got one...

---

### Post by 3Miro on 2009-03-03
How could Ubuntu utilize the cores? The Desktop environment and the Kernel take as little resources as possible. Applications are those that use a lot of power and most applications can utilize only one core anyway.

If you are asking if Ubuntu would handle the problem of splitting all of your apps over all the cores and/or providing a single app with access to all cores and/or both, then Linux would do much better job than any windows.

---

