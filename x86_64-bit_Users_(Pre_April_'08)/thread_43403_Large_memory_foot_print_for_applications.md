---
title: "Large memory foot print for applications"
date: 2005-06-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by vandal43 on 2005-06-21
Hi guys,

I have an Asus Z80k laptop running 64 bit Ubuntu and it only has 512 mb of ram and I was noticing that the memory foot print for apps is much larger on this machine than say on my 32 bit x86 ubuntu install. I.E. Nautilus is currently in at 123 mb in my system monitor whereas it's only 37 mb on my x86??? Anyone have an idea what might be the issue here. So far it's only been a performance problem for games.

---

### Post by Optimal Aurora on 2005-06-21
I think its because of the 64bit programming (it requires a little more code) than a 32bit program...

And hay they are some girls here too...

---

### Post by FluffyElmo on 2005-06-21
Interesting, it's odd that the 32bit and 64bit versions would be different...I've never though to try that. 

I've read that system monitor is not accurate since for one it isn't thread aware. The recommended way to find out how much memory a program actually uses is to run top and note the total system memory used before and after the program is started.

Even within system monitor the memory usage seems misleading since it shows the total memory including virtual memory. Nautilus currently shows 136.8MB used, but only 20.7MB of that is resident memory the rest is virtual memory and thus may not have an effect on performance?

It's still a lot though so hopefully someone with more actual knowledge will chime in:)

PS: If it's only gaming that's slow might it be due to other issues like video drivers or whatnot? Can't think of another memory hungry app to test offhand...video encoding maybe?

---

### Post by Optimal Aurora on 2005-06-21
More knowledgeable, you got to be kidding me...

Here is a quote from another forum dealing with what I meant, (I'm not trolling, neither)...

> 64 bits has the potential to address this in 2 ways. The first is granularity. In a 32 bit number space, you can count to just over 4 billion, 4294967296 to be exact, or 4294967295 if you count from 0 like you really should. The 64 bit number space extends that to 18446744073709551616, which even the most casual observer will notice has a lot more digits. With the ability to map position things to the mm level, you get a worldspace of just over 4000km, not bad, but a little limiting if you are flying a plane, and woefully inadequate if you are in a spaceship needing to dock at anything other than a blobby thing with no discernable features. Jumping to 64 bit numbers for mapping, you can have both the mm accuracy, and a detailed space station. That is a huge advantage for anyone who gets annoyed by small, discrete levels that take forever to load. Think about an MMORPG where you can fit a much more detailed world into a single zone, and you are on the right track.


At the Athlon64 launch, there were a ton of games, and a few game developers on display as well. With no offence meant to the Epic guys, I know it was a port, there was only one team who got it, and that was Crytek. Their game Far Cry was on display, and it used 64 bits right. The demo showed the usual lush island jungle with a MWABAG (Man With A Big Ass Gun) running through it. Ho hum. It was very detailed, and smooth, as you would expect from a next generation game about to be released. You could see the leaves on the trees, and the level of detail showed clearly. Then they went into god mode and zoomed out. You could see the entire island, and you didn't lose any detail in the things up close. That is what 64 bit buys you when you 'get it'.

-Nic from techspot.com  
This is because it the processor takes and utilizes more code and memory to get the this better picture and graphics, that is why 64bit OS are good for graphics... You will find that a 32bit system running 32bit processor Hyper-Threaded or not will take less memory usage than my system running the same program in Windows 32bit mode on my 64bit system...

---

### Post by FluffyElmo on 2005-06-21
A 64bit processor *can* access more memory, and it can process it in bigger chunks. This makes it very good for graphics, video processing and games.

Applications ported to 64bit will also usually have a bigger memory footprint, since (among other things) variables are larger...an integer now takes 64bits of space instead of 32bits.

I just wouldn't expect an application to be *3 times* as large...which makes me wonder if something else is going on. I'll play with my 32bit install at work tomorrow though and see what I come up with.

I could be dead wrong though, since while I understand a wee bit about Linux memory usage, what I don't understand would probably fill a very large book:)

---

### Post by vandal43 on 2005-06-22
Hi Guys/Gals/Somewhere betweens,

Thanks for the quick replies. I just went and ran top, and while nothing seems specificially to take up large percentages of memory, here's what top is presenting as a snapshot of my system memory:
```
Mem:    507044k total,   396924k used,   110120k free,    28220k buffers
```

Seems overly memory hungry to me still. I don't think Win XP even uses that much, but I could be wrong.

---

### Post by FluffyElmo on 2005-06-22
I'm on my 32bit system right now and for nautilus the resident memory is about the same...but it uses much less virtual memory. So long as virtual memory isn't being hit much I wouldn't expect there to any real difference in performance though. Memory paging is somewhat CPU dependent, so maybe it's done differently in 64bit mode than 32bit compatibility mode?

Check if there is much virtual memory activity using *vmstat 1*. If there is a lot of swapping then you will notice it, especially with a laptop hard disk. 

As for XP, Linux will always use more memory than XP on a system. Linux is much more aggressive about allocating free RAM for disk caching and other purposes, this memory is freed when a program needs it though.

---

### Post by roboguy on 2005-06-24
[QUOTE=vandal43]Hi guys,

I have an Asus Z80k laptop running 64 bit Ubuntu and it only has 512 mb of ram and I was noticing that the memory foot print for apps is much larger on this machine than say on my 32 bit x86 ubuntu install. I.E. Nautilus is currently in at 123 mb in my system monitor whereas it's only 37 mb on my x86??? Anyone have an idea what might be the issue here. So far it's only been a performance problem for games.[/QUOTE]

Hi Vandal,

The reason you are seeing a larger memory requirement for you 64 bit apps vs the 32 bit version of the same size will be largely because of pointer size. One of the most fundamental differences between 64 and 32 bit systems is their ability to address memory. 32 bit systems can address 2^32 locations in memory where as 64 bit systems can address 2^64 memory locations ( a much larger number  :smile: ).  

However, with this benifit also comes a cost. In order to be able to address that large a space, on a 64 bit system all pointers are 64 bits long, twice the size of their 32 cousins. Similarly on a 64 bit linux system a "long" in C is 64 bits compared to only 32 bits on a 32 bit system. The net effect of this is as you have seen, programs using more space in memory while running.

Another benefit of 64 bit systems is their ability to perform mathematical operations on floating point numbers in fewer cpu cycles than a 32 bit system. This is because the 64 bit system can load each of the 64 bit operands in one clock cycle due to it's 64 bit data bus and perform the operation in one additional cycle. A 32 bit system takes 2 cycles to load each operand, then 2 cycles to perform the operation. This makes a huge performance difference if you have an application that is very floating point intensive.

HTH,
Roboguy

---

