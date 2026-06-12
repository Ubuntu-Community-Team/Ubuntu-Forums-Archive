---
title: "The ram being used is too high i think help."
date: 2008-05-28
forum: x86 64-bit Users
---

### Post by aloasi on 2008-05-28
Hello everyone, I am new to Ubuntu/linux so I have read some threads here and found an interesting command to know how much free ram the computer has and when it showed me it was less that 1/4 of the ram installed. Then I checked the system monitor it said that i was only using around 400mb instead of the 1500mb it said it was using with the command free a-.This is what it says with the command.

pagan@pagan-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2014       1922         92          0        600        931
-/+ buffers/cache:        390       1624
Swap:          953          0        953

 So if anybody can help me understand thank you very much.

---

### Post by soxs on 2008-05-28
I've got average 540 MB / 4Gb used, running exaile, firefox and pidgin. If you are idle with no apps runnning, you should check wether tracker is eating your mem

---

### Post by aloasi on 2008-05-28
how do i check if the tracker is eating the memory? I am new to ubuntu and linux OS, so sorry if I appear to ask too much. Thank You

---

### Post by soxs on 2008-05-28
Goto System -> System...blah -> System-monitor -> Goto the tab processes. Then you should order them by clicken ascending to memory usage, so you see the guilty apps.
Note: You may need to set under *view*  and select show all.

---

### Post by aaron.d on 2008-05-28
The "system Monitor" does not take into account buffers or cache, since they are technically available to the kernel when needed.

In 'free', what you are seeing as used is almost entirely buffers and cache (last two columns in first row). You dont even have to do the math, if you look at the second row ( -/+ buffers/cache: ) you will see it telling you that buffers and cache aside, you have only USED ~390MB and have 1624MB free (for the kernel to use). This is, presumably, where "system monitor" gets its figure.

So, in effect, you have a lot of memory left, and you are not swapping at all (third row in "free") which is the key.

You can watch free with:

```
watch free
```
or with the -s option and a delay number
```
free -s 3
```

If you suspect a memory leak.

enjoy

---

### Post by movieman on 2008-05-28
So long as you're not swapping, you have nothing to worry about.

Linux will use all available memory to cache commonly-accessed disk files in RAM, so you should generally expect to see close to 100% usage; if your programs need more memory then the disk cache will be reduced in size to provide it. It's only when programs start getting swapped out to disk that you really have a lack of memory.

---

### Post by Kilz on 2008-05-28
> **movieman said:**
> So long as you're not swapping, you have nothing to worry about.

Linux will use all available memory to cache commonly-accessed disk files in RAM, so you should generally expect to see close to 100% usage; if your programs need more memory then the disk cache will be reduced in size to provide it. It's only when programs start getting swapped out to disk that you really have a lack of memory.

Quoted for truth, totally free memory is wasted memory. Linux does a wonderful job of using memory.

---

### Post by aloasi on 2008-05-28
thank you for the kind help everyone!!!

---

