---
title: "AMD 64 over 32bit chips?"
date: 2005-04-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by sladed1 on 2005-04-28
Hi linuxeariens

Im relitivly new to linux, I'm due to upgrade the mobo, cpu & ram of my main box soon and i was giving AMD64 serious consideration, I was wondering what people's experiences are really like. I've asked a couple of people in my dept (IS) and they have said they are not too impressed, but we are running pretty heavy servers with latest MS software  ](*,) & P4 chips so that kinda of taints there bias. 

What are the good things and what are the bad things? is it worth waiting a couple more months before investing in the latest AMD offering? 

Thanks very much for your time. \\:D/

---

### Post by psoulocybe on 2005-04-28
AMD Athlon64 chipsets are great.  Especially if you have socket 939.

I am running Ubuntu64, and it's great.  However, it is not for the n00b.  It is limited since there are not a ton of application compiled for 64bit... but most 32 bit applications run in a 64bit OS anyway.  The problems come in when you want 32bit libraries.  Things like flash are not so hot in the 64bit market right now. 
Running 32bit ubuntu on a 64bit chipset is nothing to be ashamed of though.  The A64s run 32bit Operating systems as well as anything else out there.  Thats a great way to go until the 64bit community is a little stronger.

There are great tutorials on this forum for using chroot and debootstrap that will allow you to run instances of 32bit applications.

linux32 is also a great command for running 32 bit applications.

Overall, I would urge you to get into the socket 939 market and pick up a A64.  It gives you great performance now, and a lot of flexibility to grow with market in the future.

Their current performance is great.  The scalability in the future is top notch.  The socket939 motherboards are going to support the dual-core Athlons, so that's something to be aware of as well.  939 handles dual channel DDR400 which it's predessesor the 754 does not.  
939 also provides you with the best memory to CPU bandwidth on the market.
If you are into overclocking, this chipset is for you.  I run a A64 3000+ winchester overclocked from 1.8ghz @ 2.4ghz with stock heatseak and fan, with a voltage of  1.5V

We are all anxiously awaiting the next few months as leaps are made in 64bit computing, and it looks like linux is going to be the route to take us there.

---

### Post by wmcbrine on 2005-05-04
[QUOTE=sladed1]
I've asked a couple of people in my dept (IS) and they have said they are not too impressed, but we are running pretty heavy servers with latest MS software  ](*,) & P4 chips so that kinda of taints there bias. 
[/quote]
Sounds like a real bright crew.  :roll: 

The Athlon 64 is a killer processor even if you never run a byte of 64-bit code. It's much better value for money than a Pentium 4.

> is it worth waiting a couple more months before investing in the latest AMD offering?
No more so than with everything else in computing. (Price drops, performance improves; and if you wait for that to stop, you'll never buy anything, ever.)

---

### Post by coolmike890 on 2005-05-05
I would encourage you to take the Athlon64 plunge! In my opinion, AMD has been the performance leader for a long time, with the exception of maybe a year while they were transitioning. I have a 939 nForce 4-SLI rig, and it is extremenly solid. I've built many systems around the Athlon CPU's of various types, and have been quite pleased with them all.

Intel's great strenght is still their manufacturing capability. They make tons of chips, they make them well, and they are cost effective. AMD leads them by a considerable margin in design and innovation. The on-die memory controller is probably the best idea they've had. Their Hypertransport bus is great, and their 64-bit CPU's were designed with Hypertransport links from the outset to enable multi-core implementations without crippling bottlenecks.

On the server front, it is going slowly for AMD because the industry is slow to change. I still run into people who think that AMD CPU's aren't "compatible". Does someone want to provide an example? It is certainly not commonplace. I expect things will improve quite a bit for AMD in the server arena once the possibilities of the nForce 4 pro are realized.

One last thing...I fired up a 939 3000+ the other day with a copper heatsink and a small ff 60mm fan. I had Cool&Quiet running, and the CPU idle temp was 22 degrees C (room temp was about 18 degrees C ). I was pleasantly surprised.

Good luck with your decision, and let us know if you would like further suggestions.

---

