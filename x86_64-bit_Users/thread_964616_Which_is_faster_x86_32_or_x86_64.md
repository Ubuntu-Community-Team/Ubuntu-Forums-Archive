---
title: "Which is faster? x86_32 or x86_64"
date: 2008-10-31
forum: x86 64-bit Users
---

### Post by neoflight on 2008-10-31
I have an assembled PC with 64 bit capability. 
I have been running both 64 and 32 bit linux (ubuntu,fedora,debian,centOS) on and off. Finally decided to stick with 32bit. 

The argument goes in terms of using 64bit when the hardware is designed for it. 

My conclusions based on typical desktop usage along with some heavy duty number crunching:

I do not see any kind of performance or speed improvement when using 64bit. I feel like the memory usage is more when 64b is used, which is expected. 
I have 4gb ram which is very well seen by a i386/i686 PAE kernel. So addressing  >4gb ram is not an issue. 

I must say that I have not done any scientific comparison. 
Just some thoughts. I would like to know your experience?

---

### Post by trekrem on 2008-10-31
No scientific tests but I have found 8.10 32-bit seems faster than 64-bit.

(I also found this even more so with openSUSE 11).

But again like I said no scientific test.

---

### Post by Tindytim on 2008-10-31
> **neoflight said:**
> My conclusions based on typical desktop usage along with some heavy duty number crunching:
Are you using 64bit applications?


> **neoflight said:**
> I have 4gb ram which is very well seen by a i386/i686 PAE kernel. So addressing  >4gb ram is not an issue.
Many 32 bit operating systems can acknowledge more than >4GB of RAM (Vista can) but it still cannot address it all, and that 4GB limitation includes VRAM.

---

### Post by neoflight on 2008-10-31
> **Tindytim said:**
> Are you using 64bit applications?


I was using 64bit applications while running 64b kernel


> **Tindytim said:**
> Many 32 bit operating systems can acknowledge more than >4GB of RAM (Vista can) but it still cannot address it all, and that 4GB limitation includes VRAM.

PAE (physical address extension) kernel can do that. Different distro calls that by different names. Debian calls it bigmem kernel. CentOS calls it PAE kernel.

---

### Post by Arup on 2008-10-31
x64 way faster with heavily loaded apps like programming etc as well as multimedia editing. Operax64 loads faster and runs way faster than its x32 counterpart, so do other programs.

---

### Post by Marshal0505 on 2008-10-31
My experience is that 32 bit is faster in some areas and 64 bit in its turn is faster in other areas or apps.Bottom line, with typical (!!) desktop use they both about even out in terms of speed.But..... the differences are so small that the only reliable way of comparing would be to actually benchmark apps.
So i'm not sure if my or other people's subjective impressions actually mean something here.

I still prefer 64 bit because i'm using 4gb memory and I have absolutely no issues with drivers/software running on 64 bit.

---

### Post by davidw89 on 2008-10-31
x64 is way faster. Just check the load time on Firefox 3 and you will see what i mean. This is because you must be running a relatively new CPU..like the Intel Duo Core or the Quad Core.

---

### Post by Marshal0505 on 2008-10-31
> **davidw89 said:**
> x64 is way faster. Just check the load time on Firefox 3 and you will see what i mean. This is because you must be running a relatively new CPU..like the Intel Duo Core or the Quad Core.

Let me rephrase:
64 bit can be faster but it also depends on what you are doing.64 bit is not faster than 32 bit all the time.

Some apps are faster, others are slower under 64bit.This is what i was trying to say in my earlier post.This is why I think speed really should not be a criterion when it comes to trying to decide for either 64bit or 32bit.
You'll either be disappointed by its lack of speed gains or you'll end up overemphasizing the improved speed of individual apps.

That said, I believe if your hardware allows you to run 64bit and your software is available in 64bit I believe you should at least give it a shot.
This has been the case for me since 1,5 or 2 years, and I've used it ever since.

---

### Post by Archmage on 2008-10-31
> **Tindytim said:**
> Many 32 bit operating systems can acknowledge more than >4GB of RAM (Vista can) but it still cannot address it all, and that 4GB limitation includes VRAM.

I'm sorry to tell you, but Vista can't do this either. :)

---

### Post by neoflight on 2008-10-31
oops..!

[Is such a system actually created for speed? ]("http://en.wikipedia.org/wiki/X86-64#History_of_AMD64")

---

