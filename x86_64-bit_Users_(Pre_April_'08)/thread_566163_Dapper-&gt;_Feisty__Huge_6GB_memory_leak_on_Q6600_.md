---
title: "Dapper-&gt; Feisty : Huge 6GB memory leak on Q6600 and AMD64X2"
date: 2007-10-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by remi_2 on 2007-10-03
Hi, 

I was running 6.06.1 LTS on a Q6600/8gigs machine and two AMD64x2 machines for months.

Last friday I upgraded the all machines to 7.04, and am now experiencing big memory consumption problems :

On the Q6600, after 3 days up (staying idle most of the time), top reports that 6.7Gigs out of my 8Gigs are comsumed, but there are no process reporting such a figure.

Same deal on the AMD64X2 machines.

I browsed the ubuntu bug reports on launchpad and found no trace of a similar problem, except for a known leak in Xorg 7.2 which has been fixed since  this summer.

Thank you for any info on that topic, 

:confused::confused::confused:

---

### Post by Nunslaughter on 2007-10-03
it's probably cache memory...if you add those meters to your panel (don't know the english term), you can see what your ram is doing...

---

### Post by Phelan on 2007-10-03
Total newb probably not offering any help at all, but is the interest of cache usage, what is your swap set at?  Default of 60?

---

### Post by Jouke74 on 2007-10-03
Don't underestimate the total newbies on the forum, post count does can say little about experience with a OS. I also think that your memory is being consumed /used as your disk cache. Open a terminal, and type "free [enter]" what does this say? 

Have you accessed many different files during those days?

---

### Post by remi_2 on 2007-10-03
Hi guys,
thanks for giving a hand

I indeed am a total newbie to linux

and you were right, the disk cache was the explanation ! during these last 4 days there have been lots of disk IO.

If the disk cache usage goes high like that, will applications swap, or will the kernel give the memory back to processes when they need it ?

How can I configure the behaviour of the disk cache?

thanks a lot I feel better about that move

---

### Post by Jouke74 on 2007-10-03
The kernel will give back memory when needed, swapping will be done when all memory is in use for applications Although sometimes things seem to be put into swap when not used for a long time (have not been able to figure that one out yet).

---

### Post by praxis22 on 2007-10-03
[http://ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43)

Try that for a quick tut on controlling swap.

---

### Post by John.Michael.Kane on 2007-10-03
> **remi_2 said:**
> Hi guys,
thanks for giving a hand

I indeed am a total newbie to linux

and you were right, the disk cache was the explanation ! during these last 4 days there have been lots of disk IO.

If the disk cache usage goes high like that, will applications swap, or will the kernel give the memory back to processes when they need it ?

How can I configure the behaviour of the disk cache?

thanks a lot I feel better about that move

Cached memory is essentially free,That can be replaced quickly if a running or newly starting program needs the memory.

Unused memory is wasted memory. Thus Linux uses so much memory for disk cache.

Keeping cache is a measure done in case something needs the same data again,It's a good chance it will still be in the cache in memory. Allowing fetching of the info from there quicker than refetching it from the hard disk, however.If the info is not found in the cache, The hard disk will be reread, but in that case nothing has been lost in time.

You can run the command below to gage how much memory is free for applications to use,
```
free -m
```

To adjust swapping out to cache
```
sudo gedit /etc/sysctl.conf
```

At the bottom of the file add the line below.
vm.swappiness=0 <----The zero can be adjusted from 0-100 to change the balance between swapping and freeing cache.

After applying the setting you want. Reset the file using the command below.
```
sudo sysctl -p
```

At 100, the kernel will always prefer to find inactive pages and swap them out,in other cases, whether a swapping out occurs depends on the application memory footprint being used among other things.

The default swappiness is 60. A value of 0 gives something close to the old behavior where applications that wanted memory could shrink the cache to a tiny fraction of RAM. 

Also Setting it to 100, the highest, allows swapping to take place quite frequently. something you might not want.

Hope this helps.

---

### Post by remi_2 on 2007-10-04
Thanks again a lot for your help, you guys rock :guitar: !

---

