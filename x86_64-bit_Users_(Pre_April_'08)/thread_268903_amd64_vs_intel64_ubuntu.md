---
title: "amd64 vs intel64 ubuntu"
date: 2006-09-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by morequarky on 2006-09-30
Ubuntu has a amd64 bit version I use on a intel 64 bit processor.

Is there a need for a intel64 Ubuntu version?  What is different about intel64 vs amd64?  Am I missing speed or funtionality by using amd64bit ubuntu on a intel machine?  Are their any bugs?

Thanks

---

### Post by kleeman on 2006-09-30
I assume you are using the em64t intel cpu. If so the amd64 64 bit Ubuntu is fine. 

If you have a xeon then the amd64-xeon kernel gives you a little extra in my experience. Reason? The em64t is intel's response to the amd64 and the technology was actually obtained in the main from amd.

---

### Post by morequarky on 2006-10-01
How would I know which 64bit processor I had and if I ever came across the Xeon how would I install the new kernel.

What would happen if I used the xeon kernel on the em64t?


thanks

---

### Post by Kilz on 2006-10-01
> **morequarky said:**
> How would I know which 64bit processor I had and if I ever came across the Xeon how would I install the new kernel.

What would happen if I used the xeon kernel on the em64t?


thanks

You can install different kernels in synaptic. They are then added to the grub menu. If you try to run something that isnt compatible it may not run, or run right. You could always reboot and select another kernel. Thats one reason why its always advisable to keep more than one avilable in the grub menu.

---

### Post by djRobbieF on 2006-10-01
My Pentium 4 D obviously is an emt64 processor, and after trying the amd64 kernel, I immediately reinstalled ubuntu 386 and upgraded to the 686-smp kernel.  The amd64 was WAY slower than the 686-smp.  I mean, noticably.

morequarky:  you would probably know if you had a xeon processor, because I reckon you bought the computer?  Or at least you know if it's either a Pentium or a Xeon.  Pretty straightforward.

---

### Post by kleeman on 2006-10-01
> **djRobbieF said:**
> My Pentium 4 D obviously is an emt64 processor, and after trying the amd64 kernel, I immediately reinstalled ubuntu 386 and upgraded to the 686-smp kernel.  The amd64 was WAY slower than the 686-smp.  I mean, noticably.
Interesting. I have a dual xeon with em64t and noticed exactly the opposite. When I installed 64bit Ubuntu a lot of desktop apps opened twice as fast as when I was using the 32bit install with the 686-smp kernel.

---

### Post by Kilz on 2006-10-01
> **djRobbieF said:**
> My Pentium 4 D obviously is an emt64 processor, and after trying the amd64 kernel, I immediately reinstalled ubuntu 386 and upgraded to the 686-smp kernel.  The amd64 was WAY slower than the 686-smp.  I mean, noticably.

morequarky:  you would probably know if you had a xeon processor, because I reckon you bought the computer?  Or at least you know if it's either a Pentium or a Xeon.  Pretty straightforward.

I could see if you said it wasn't noticeably faster. But saying its slower isn't reality. Nor is it something that others should take into consideration.

---

### Post by Relain on 2006-10-02
yeah amd64 was faster for me with a 3.4ghz, pentium D. I did tests on code and everything! :KS

---

### Post by fatsheep on 2006-10-02
> **Kilz said:**
> I could see if you said it wasn't noticeably faster. But saying its slower isn't reality. Nor is it something that others should take into consideration.

It is possible.  

[http://www.tbreak.com/reviews/article.php?cat=cpu&id=295&pagenumber=2](http://www.tbreak.com/reviews/article.php?cat=cpu&id=295&pagenumber=2)
[http://techgage.com/article/enthusiast_look_windows_xp_32-bit_versus_64-bit/3](http://techgage.com/article/enthusiast_look_windows_xp_32-bit_versus_64-bit/3)
[http://www.osnews.com/story.php/5768/Are-64-bit-Binaries-Really-Slower-than-32-bit-Binaries/page2/](http://www.osnews.com/story.php/5768/Are-64-bit-Binaries-Really-Slower-than-32-bit-Binaries/page2/)

Depending on what application your running 64-bit can actually be slower...  It's not the fault of the architecture of course.  It' just the fact that program's are still predominantly written for the 32-bit architecture.

---

### Post by Kilz on 2006-10-02
> **fatsheep said:**
> It is possible.  

[http://www.tbreak.com/reviews/article.php?cat=cpu&id=295&pagenumber=2](http://www.tbreak.com/reviews/article.php?cat=cpu&id=295&pagenumber=2)
Sandra scores show the memory tests to post identical numbers, however CPU and Multimedia tests show some difference.
> **fatsheep said:**
> [http://techgage.com/article/enthusiast_look_windows_xp_32-bit_versus_64-bit/3](http://techgage.com/article/enthusiast_look_windows_xp_32-bit_versus_64-bit/3)
"We can see from the results, that the 64-Bit performed lower in the '03 tests, but higher in the '05. Once again though, the differentials in between the scores are so little, that we may as well consider them equal."
> **fatsheep said:**
> [http://www.osnews.com/story.php/5768/Are-64-bit-Binaries-Really-Slower-than-32-bit-Binaries/page2/](http://www.osnews.com/story.php/5768/Are-64-bit-Binaries-Really-Slower-than-32-bit-Binaries/page2/)


"The problem is that benchmarks, by their very nature, are narrow in scope and fail to encompass the complexity of an operating system, application, or hardware platform. As a result, someone with even a mediocre knowledge of the technology can easily poke holes, and make themselves seem smart in the process."


Most of the benchmarks in the links are close, so close that a human couldnt tell the difference. 3% of cpu cycles is nanoseconds. The poster I quoted said it was noticably slower.
Also by the above quote they can be inacurate at times.
Could it happen, well anything is possible. But is it normal and going to happen to a lot of people? Mostl likely not.

---

