---
title: "Turion 64 laptop; is it really worth it?"
date: 2006-04-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by rozojc on 2006-04-13
Hi everyone.
I am planning to go to the US in the summer, and I hope I will be able to buy a good laptop. Now, my budget is not enough for an Intel Dual Core based laptop, so I don't know if I should buy a Centrino or a Turion based laptop.

At the begginning I thought I was definitely going to buy a Turion based laptop, and I was planning to use Kubuntu for 64 bits, but I then read that some people have had problems running common applications such as OO, Firefox, etc... I don't really know if it's true or not, so I would like to hear some of your opinions... Is buying the Turion based laptop really worth it? 

Will I get a better (noticeably better) performance running Kubuntu 64 over a Turion than just the regular Kubuntu over a Pentium M?

If I buy the Turion, will I have any kind of problems, or is it just like the regular Kubuntu but with a better performance?

---

### Post by Monster_user on 2006-04-13
You shouldn't have a problem with a Turion laptop, unless it uses a chipset created in the last six to eight months. If so, then Dapper Drake might be needed, followed by an installation of kde. Unless you don't mind waiting untill June or July for the Kubuntu version of Dapper.

The 64-bit versions of any OS are not yet ready for prime time. Support is still a good bit better on 32-bit versions. So there are going to be more problems.

For one, the Linux version of Flash requires 32-bit libs, and etc. Several media codecs, such as the WMV codec also requires 32-bit libs, and etc. You basically have to install half of the 32-bit Ubuntu, to get 64-bit Ubuntu to work for the most common tasks.

That being said, I do think that a Turion 64 laptop is a good investment. I think AMD has finally gotten a laptop that has decent battery life. Just use the standard 32-bit Kubuntu. You could use the K7 kernel to get a little more performance, than with the i386 kernel.

---

### Post by rozojc on 2006-04-13
[QUOTE=Monster_user]You shouldn't have a problem with a Turion laptop, unless it uses a chipset created in the last six to eight months. If so, then Dapper Drake might be needed, followed by an installation of kde. Unless you don't mind waiting untill June or July for the Kubuntu version of Dapper.

The 64-bit versions of any OS are not yet ready for prime time. Support is still a good bit better on 32-bit versions. So there are going to be more problems.

For one, the Linux version of Flash requires 32-bit libs, and etc. Several media codecs, such as the WMV codec also requires 32-bit libs, and etc. You basically have to install half of the 32-bit Ubuntu, to get 64-bit Ubuntu to work for the most common tasks.

That being said, I do think that a Turion 64 laptop is a good investment. I think AMD has finally gotten a laptop that has decent battery life. Just use the standard 32-bit Kubuntu. You could use the K7 kernel to get a little more performance, than with the i386 kernel.[/QUOTE]
What about Intel core Duo, is it really THAT much better? If I had the money, does the Core Duo really improve performance significantly?

Also, another question: If I were to use the 32 bit Kubuntu, would it really be necessary to buy a Turion based when I could just as well buy a Sempron 3200+ ?

---

### Post by Monster_user on 2006-04-14
That Core Duo? It is hard to tell. It is actually **SLOWER** than comparable processors. The ones I have found have two 2.0gz processors. That comes to 4.0ghz. **IF** the program supports dual core. If not, then it will be running off of a 2.0ghz core. I don't think they get over 3.0ghz per core. If even that in a laptop...

It is the same for all dual cores, including the Pentium D, and the Athlon 64 FX2. The Athlon is raved as being the best comsumer processor on the market. Not the most powerfull, but it has the best performance. It really depends on what your needs are, as to which is better. 

[QUOTE=rozojc]Also, another question: If I were to use the 32 bit Kubuntu, would it really be necessary to buy a Turion based when I could just as well buy a Sempron 3200+ ?[/QUOTE]
No it is not neccessary. If you don't mind having to upgrade to a Turion in a few years.

I don't know if the Sempron has as good a battery life, being a desktop processor. If you are not getting a Turion, then you should probably get a Centrino based laptop.

---

### Post by rozojc on 2006-04-14
[QUOTE=Monster_user]That Core Duo? It is hard to tell. It is actually **SLOWER** than comparable processors. The ones I have found have two 2.0gz processors. That comes to 4.0ghz. **IF** the program supports dual core. If not, then it will be running off of a 2.0ghz core. [/QUOTE]
Ok, I'm oficially VERY confused:

So, Core Duo is only faster if the programs support that processor and if not then only one of the two processors run?
Another question: is it the programs the ones that have to support that technology, or the OS itself?

---

### Post by killerrobot on 2006-04-15
[QUOTE=Monster_user]That Core Duo? It is hard to tell. It is actually **SLOWER** than comparable processors. The ones I have found have two 2.0gz processors. That comes to 4.0ghz. **IF** the program supports dual core. If not, then it will be running off of a 2.0ghz core. I don't think they get over 3.0ghz per core. If even that in a laptop...

It is the same for all dual cores, including the Pentium D, and the Athlon 64 FX2. The Athlon is raved as being the best comsumer processor on the market. Not the most powerfull, but it has the best performance. It really depends on what your needs are, as to which is better. 


No it is not neccessary. If you don't mind having to upgrade to a Turion in a few years.

I don't know if the Sempron has as good a battery life, being a desktop processor. If you are not getting a Turion, then you should probably get a Centrino based laptop.[/QUOTE]

I don't think it actually works this way...  Adding up the GHz is an analogy at best, and probably not a good one, but I do think that the max right now is 2GHz (for laptop.  I don't think there is even a desktop version yet)  Also, dual core machines do give a good advantage even without specially written code.  The reason is multi-tasking.  Most of us run many programs at once and have some daemon or other doing something in the background.  All of these processes can be divided among the cores to reduce the load on each.  There is a small overhead cost for dealing with multi-cores, but that has been partially mitigated by having very fast memory busses.  The core-duo is a much better and truer implementation of a dual-core than the pentium D, from my understanding.      

Read some reviews and see how the core-duo does much better  than pentium-m.  I just got a core-duo instead of a turion.  I don't see how 64 bit would help me at thte moment

---

### Post by Monster_user on 2006-04-16
[QUOTE=rozojc]So, Core Duo is only faster if the programs support that processor and if not then only one of the two processors run?[/quote]
Yes

[QUOTE=rozojc]Another question: is it the programs the ones that have to support that technology, or the OS itself?[/QUOTE]
Both. Even if the program supports it, it won't work if the OS does not support it.

Linux has supported "Dual Processors" for years. Windows NT/2000/XP supports "Dual Processors" as well. So they support the Core Duo.

killerrobot mentioned Multitasking. 

Basically, the OS is faster, but there is little or no speed increase for the individual programs. There is a lot less slowdown when running more than one program.

---

### Post by tsb on 2006-04-29
Wait and save.

The notebook version of Conroe is coming Q4.  Nothing will touch it.  (Even AMD insiders have told me this.)

---

