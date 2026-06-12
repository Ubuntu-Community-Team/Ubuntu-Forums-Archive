---
title: "Many Cores and 64 Bit"
date: 2007-09-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Shin_Gouki2501 on 2007-09-10
Hello!
I dont know exactlyif this is the right forum to ask but i just go ahead ;)
What Linux applications for the Desktop ( Gnome, KDE, XFCE) would benefit from  a Quad Core CPU which runs also with x86-64?

Also could u say if there was a big  diffrence between Intel Quad and AMD Quad?

IMO some Apps which are used on desktop which benifite from Many Cores are:
Video Encoding Apps, 3D Renderer and maybe Desktop Search engines?

So what other application u know ( for desktop!!) could get a spped up by many cores?

wbr Shin Gouki

---

### Post by Jouke74 on 2007-09-10
I don't think many more, however the most gain is coming from the fact that you can run 4 CPU intensive programs at once.

---

### Post by Shin_Gouki2501 on 2007-09-10
thx  for reply!
Is there a software for Gnome or the others  were i can assign a certain Application towards an specific CPU?

---

### Post by John.Michael.Kane on 2007-09-10
> **Shin_Gouki2501 said:**
> thx  for reply!
Is there a software for Gnome or the others  were i can assign a certain Application towards an specific CPU?

Yes there is. 

You can use "schedutils" in synaptic - one of the tools is "taskset" for setting CPU affinity for a process.

Have a read this explains how to set it up.
[Linux Setting processor affinity for a certain task or process]("http://www.cyberciti.biz/tips/setting-processor-affinity-certain-task-or-process.html")

---

### Post by Shin_Gouki2501 on 2007-09-11
great... a chance for a GUI for this CLI  tool?

---

### Post by John.Michael.Kane on 2007-09-11
> **Shin_Gouki2501 said:**
> great... a chance for a GUI for this CLI  tool?

Not that I know of.

---

### Post by tszanon on 2007-09-11
As multicore cpus become more and more popular, developers (when needed) will take advantage of them. Today, most applications won't have any benefit from multicores, because they weren't written to use them.

But, of course, multiple cores let you run multiple applications truly simultaneously, as stated before. And it's an advantage by itself.

---

### Post by Jouke74 on 2007-09-13
The linux Kernel does a good job assigning & dividing the program load over cores itself also by the way.
It's best to see when using system monitor.

---

### Post by Sockerdrickan on 2007-09-13
There is a difference. AMD's upcoming CPUs are real quad while Intels are 2x2 cores on one CPU (bottlenecking etc, heat)

---

### Post by ukripper on 2007-09-13
It will be huge gain in processor intensive apps such as video transcoding, editing multimedia,  encoding and other scientific apps relying on processor too much such as breaking encryption.

---

