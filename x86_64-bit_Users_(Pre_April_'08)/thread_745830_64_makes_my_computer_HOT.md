---
title: "64 makes my computer HOT"
date: 2008-04-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by twist2b on 2008-04-04
When i installed 7.04 It works really nice. I dont get wireless and everythings NOT as good as 7.10 But i installed 7.10 and everythings smoother and nicer BUT my computer gets HOT unlike 7.04 were is always cool and they both are just as fast.

If I cant find a fix i will go back to the older (living without wireless internet for 28 more days is fine with me.... and better compiz....

I did not have 64 when using Feisty though.
The reason I got ubuntu was to stop the heat, which was a HUGE problem with VISTA and it was literally destroying my computer....

Its not that hot comparitively to vista but it still gets hot and the fan is load... feisty its almost always silent.
What i believe the problem is, my graphics are not working correctly.... maybe im wrong?
suggestions?

---

### Post by tamoneya on 2008-04-04
post the results of ```
top
``` when you are running 7.10

---

### Post by twist2b on 2008-04-04
craig@craig-laptop:~$ top

top - 23:22:38 up 45 min,  3 users,  load average: 0.26, 0.30, 0.32
Tasks: 115 total,   2 running, 113 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.5%us,  1.0%sy,  0.0%ni, 92.1%id,  0.0%wa,  2.3%hi,  0.2%si,  0.0%st
Mem:   1998028k total,   953116k used,  1044912k free,    15540k buffers
Swap:   473876k total,        0k used,   473876k free,   321488k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6089 craig     15   0  689m 145m  25m S    4  7.5   4:34.23 firefox-bin        
 5507 root      15   0  150m  55m  10m R    4  2.8   1:44.87 Xorg               
 5732 craig     15   0  283m  21m  14m S    1  1.1   0:10.54 gnome-panel        
 5836 craig     15   0  126m  11m 7488 S    1  0.6   0:07.81 gtk-window-deco    
 5965 craig     15   0  264m  26m  12m S    1  1.4   0:00.76 gnome-terminal     
 5734 craig     15   0  402m  21m  14m S    0  1.1   0:01.46 nautilus           
 6245 craig     15   0 18948 1320  972 R    0  0.1   0:00.07 top                
    1 root      15   0  5112 1968  572 S    0  0.1   0:01.68 init               
    2 root      11  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      10  -5     0    0    0 S    0  0.0   0:00.06 events/0           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1           


I only have 8 gig on the partition because of a mistake, Im going to add more later.... but that should not be the problem..... But when i had vista, It was not working with my graphics card like it should have, and this seems to be the case again, my graphics heat is 84 C which is way to much! it should be at 60 on avarage! and im only chilling on firefox........ i used envy, the trick might have not worked..

---

### Post by tamoneya on 2008-04-04
well there doesnt seem to be too much load on your processor so im going to guess that there is some sort of lmsensors/driver issue which has resulted in the computer thinking the cpu is hotter than it really is and therefore it turns the fan up higher.  As for how to fix this i dont really know.  Hopefully someone else does and will post on it.  In the meantime try searching through the forums and on google.  I'll let you know if i come across anything.

---

### Post by incubus on 2008-04-05
craig,

There are many factors in place, but before anything I think I did see something on Hardy that was supposed to improve the power efficiency for 64bit installations.  I have to say that I've been using 64bit ubuntu for almost two years now, with no heat problems at all.

Specifically for power, you probably want to try 'powertop', which will give you advice on what to do and what's consuming a lot of energy.  You can search for that on the forums or google it.

Also, if your graphics seem to be too slow, maybe you're not using acceleration correctly (although that's unlikely).  Double-check it with:
```

$ glxinfo | grep direct

```

Finally, of course remember that turning on too many graphics effects will increase the CPU usage and heat.  If you really want to minimize heat at all costs, try running a very spartan setup, meaning, no compiz effects, not many programs open at the same time, etc.  It's an obvious point, but sometimes even closing unnecessary websites with flash videos will make a difference.

Fortunately, it does look like power efficiency is high on ubuntu's priorities.

incubus

EDIT: I forgot to say, I'm assuming you have a laptop.

---

### Post by twist2b on 2008-04-07
Thank you for your posts. It was probably part of some installation driver. I loaded Feisty and installed gusty by using the update inside the update manager.
Worked like a charm. Everything works BEAUTIFULLY. When Heron comes out, I will be enthusiastic to try it out.

Thank you again for your posts.
I ran the exact same amount of processes and its still cool and quite.

---

