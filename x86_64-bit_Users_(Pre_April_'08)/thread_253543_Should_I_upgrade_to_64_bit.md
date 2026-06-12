---
title: "Should I upgrade to 64 bit?"
date: 2006-09-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by cookfromfrozen on 2006-09-08
Hi

I currently am running the 32-bit (or whatever the name is for it)  Ubuntu 6.06. 

I have now upgraded to an Athlon 64 CPU.

Do you think it is worth me upgrading to the 64 bit version of Ubuntu?  Will I gain a noticeable difference in performance and are there any things I should know about?

thank you

---

### Post by KhaaL on 2006-09-08
regarding performance: I did a Dhrystone calculation on my cpu (amd64 3 GHz with SSE2) on both linux 64bit and windows xp 32bit. The score was this:

Linux: 3950
Windows: 3321

as you can see there is a 20% performance gain for amd64 users to run on a 64bit OS. However, you'd need packaged (.deb files) that are for that specific architecture. Some programs still only exist on 32bit (or their later versions are released later for 64bit). Still, you can always compile things yourself if you're up to it...

IMO, 64bit means more performance, but also more tweaking and fiddling with stuff since it's not completly standard yet. you can still gain some performance by running a kernel specific for your cpu in 32bit (I'd guess the 32bit K7 version if you're on amd64), but the decision is really yours.

---

### Post by Heinali on 2006-09-08
> **Khalid Rashid said:**
> regarding performance: I did a Dhrystone calculation on my cpu (amd64 3 GHz with SSE2) on both linux 64bit and windows xp 32bit. The score was this:

Linux: 3950
Windows: 3321


Any results on other possible combinations (both 32bit; linux 32bit & winxp 64bit)? that would be interesting!

---

### Post by Kilz on 2006-09-08
> **Heinali said:**
> Any results on other possible combinations (both 32bit; linux 32bit & winxp 64bit)? that would be interesting!

[http://www.linuxhardware.org/article.pl?sid=05/02/24/1747228](http://www.linuxhardware.org/article.pl?sid=05/02/24/1747228)

Depending on the application, there is a 30% increese in some applications. The reason is some applications have not been written to take advantage of the 64bit archetechure. But look at the mencoder results, lower is better.

---

### Post by kleeman on 2006-09-09
I have a dual xeon em64t system which is intels version of x86_64 and there is a very big difference in responsiveness of the gnome desktop using the 64bit OS versus 32bit.

---

### Post by Sloth on 2006-09-09
I must be in the minority, but I don't notice any particular speed boost from the 64-bit version.  For a while, I had identical systems, one at home, one at work, one 64-bit, one 32, and they were the same as far as I could tell.  AMD Athlon 64 X2, 4600.

The 64-bit version could use an extra 1G of RAM, and when I needed that, I noticed the difference.

---

### Post by KhaaL on 2006-09-09
> **Heinali said:**
> Any results on other possible combinations (both 32bit; linux 32bit & winxp 64bit)? that would be interesting!

I don't have acess to 64bit win, I do however want to do a test on i386 ubuntu aswell on it with a kernel optimized for K7 and see if it makes any diffrence for the very same application.. 

But I think most of the information regarding 32/64bit performance gain can be seen on the post from kilz

---

