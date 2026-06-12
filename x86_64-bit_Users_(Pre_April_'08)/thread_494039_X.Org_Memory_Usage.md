---
title: "X.Org Memory Usage"
date: 2007-07-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Major_Kong on 2007-07-06
The xorg process keeps eating up more memory until it reaches a 80/90 MB usage. Is this 'normal' ?

EDIT: I'm using ubuntu 7.04 with the "restricted drivers" enabled.

---

### Post by david_2001 on 2007-07-06
Yes, it's probably quite normal.  Take a look at [http://techpatterns.com/forums/about687.html](http://techpatterns.com/forums/about687.html).

---

### Post by Major_Kong on 2007-07-06
Thx. 

I can't really analyse the output of pmap -d. But if 80MB it's within "normal"...

---

### Post by Major_Kong on 2007-07-06
What's the average memory usage for xorg around here ?

I just can't shake the feeling that it's using too much when i've seen in other installations xorg using around ~40 MB max.

---

### Post by david_2001 on 2007-07-06
I don't really think that this is something to worry about unless system slowdown happens to accompany increased memory usage by Xorg.  For example, after 4 hours 33 minutes uptime this evening System Monitor on my PC is showing Xorg apparently using 52.8Mb but everything still works just fine.

---

### Post by John.Michael.Kane on 2007-07-06
May help if we knew the system spec's.  

Also it's not odd to see Xorg using what seems to be a high amount of memory. 

Are you using beryl or compiz?

On my day old install Xorg is using 37.3mb

---

### Post by gaylapdancer on 2007-07-07
27.2mb here

Are you using Beryl or Compiz?

---

### Post by Major_Kong on 2007-07-07
No.

Specs:
AMD Sempron 3100+
Asrock K8NF4-SATA2
2 x 512MB DDR

---

### Post by fabertawe on 2007-07-07
You might want to check out **[this thread]("http://ubuntuforums.org/showthread.php?t=440038")** also. Xorg guzzles memory here, currently using 49.6 MB with Metacity. It is usually well over 100 MB but I have 'vm.swappiness=0' so the memory cache will build up over time. Nothing to worry about, it'll be cleared if needed.

---

### Post by Major_Kong on 2007-07-07
Updated the nvidia driver to the "new" version in the repos, don't know if it was related but memory usage seems now to be kept below the 55 MB mark. An improvement from the 90 MB mark...

fabertawe, saw the thread but i'm a little suspicious of actually being a "feature".

---

### Post by fabertawe on 2007-07-10
> **Major_Kong said:**
> fabertawe, saw the thread but i'm a little suspicious of actually being a "feature".

I only know what I've read in that thread but it makes sense to me that memory would be cached to improve performance. After a few hours yesterday Xorg was hogging 185 MB which does seem a tad excessive though. It would be nice to have a clear explanation from someone intimate with the inner workings of these things.

I just wish the Main Menu was permanently cached at start up, it really bugs me having to wait about 4 to 5 seconds for it to appear!

---

### Post by Major_Kong on 2007-07-10
> **Major_Kong said:**
> Updated the nvidia driver to the "new" version in the repos, don't know if it was related but memory usage seems now to be kept below the 55 MB mark. An improvement from the 90 MB mark...

fabertawe, saw the thread but i'm a little suspicious of actually being a "feature".

Scratch that it still reaches 70/80 MB, it just takes more time...

PS: Found something weird too, nautilus jumps to insane amounts of memory too, it reached 100 MB and stayed there until i killed it.

---

### Post by jagolis on 2007-07-20
Wish that my xorg stayed down low like that. It's at 115m right now, it can go to several hundred, and cause Counter Strike (hl2.exe) to get out of memory errors. Of course FireFox taking up 230m, and hl2.exe taking up 501m might have something to do with it. :D I do tend to have a combined total of about 15 - 20 tabs open at any given time. No swap file, and 7.04 here (upgraded from 6.10). NVIDIA drivers.

---

