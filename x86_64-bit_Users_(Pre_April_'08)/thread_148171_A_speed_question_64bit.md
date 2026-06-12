---
title: "A speed question 64bit"
date: 2006-03-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by welders4linux on 2006-03-21
Firstly I am pretty new to linux. So far I am very pleased as I can do anything that I used to do in windows.  

Don't laugh but I actually was one of the poor suckers that got Win ME.:eek: 
Im sure Bill doubled his security detail after that disaster.

Anyhow Im thinking of upgrading my computer, I am wondering if there is a significant increase in performance with 64 bit unbuntu compared to the 32 bit.

Thanks in advance for any advice you have

---

### Post by John.Michael.Kane on 2006-03-21
If your doing heavy compiling, graphics work, mathmatical computations. 64bit will show it strength. if you can live with out Flash, and codecs as well then 64bit is fine. you will be somewhat future proof going the 64bit way so that something to think about to.

---

### Post by krusbjorn on 2006-03-21
There are a lot of threads on this topic, some noticed a performance boost when switching to 64bit Ubuntu, some didnt. I didnt notice any difference at all, so I'm running 32bit on my Athlon64, since there still are problems with some stuff on 64bit.

---

### Post by Yagisan on 2006-03-22
My experience is that multimedia encoding is faster (barely, I've posted benchmarks here in a mencoder thread), encryption/decryption, compression/decompression, and software compilation is faster. Some improvement in native games but not much. Otherwise no speed difference to 32bit. I went with 64bit as for my work, the increased speed was worth it.

Why not give both a try if you have the time to spare ? Either is a fine choice.

---

### Post by welders4linux on 2006-03-24
Thanks fo rall your advice,

Im going to get into video # crunching,  so perhaps I will take the plunge into the
realm of 64bit computing...If that doesn't go well then Ill still have a faster machine @ 32bit

---

### Post by FluffyElmo on 2006-03-25
Back when I was doing video encoding *ffmpeg* announced it had added amd64 assembly code. I found the CVS version to be quite a bit faster on 64bit than 32bit. I didn't run any side-by-side benchmarks though so it could also have been my imagination or ineptitude:)

I'd definitely put it into your mix though and see what type of results you get. I had a few 30sec-1minute clips that I ran various encoders on to see what the performance/quality tradeoffs were.

---

### Post by pla7ma on 2006-03-25
i just solved some physics equations in both 64 bit and 32 bit on a pentium 4 650, it took 107s and 133s, so there is some difference. 
but from what i heard Intels EMT64 is not real 64bit, but using some tricks on a 32bit to make it look like a 64. I would therfore expect the difference on a AMD to be bigger

---

### Post by wmcbrine on 2006-03-26
[QUOTE=pla7ma]but from what i heard Intels EMT64 is not real 64bit, but using some tricks on a 32bit to make it look like a 64.[/QUOTE]
I don't think there's a difference in how they work, so much as in how they're characterized. For example, AMD refers to their architecture as "AMD64"; Intel borrows it, but labels it as "IA32e". Why? Because they'd rather be selling IA64, aka Itanium. Their grudging adoption of AMD64 is kind of an admission of defeat.

---

