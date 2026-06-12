---
title: "Assign Processor Power To a Single Task"
date: 2007-01-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by t6435bm on 2007-01-24
Hi everyone.
I just installed edgy amd64 in my X2 3800+ box... everything runs OK! :D 

One thing I want to do with this box is rendering with blender. But I get something like (just an average) 33% more speed rendering than with 32bits windows... (:confused:  should be 100% more speed, I mean, near double so fast).

For example (taking the fastest speed from about 20 trys with the same file)
	Windows32:
                gui: 24.16s
		command line: 24.37s
	Ubuntu 64:
                gui: 18.72s
		console (without X running!): 18.37

Running "gnome-system-monitor" I can see that the processors are not being used 100%, but sometimes 90 - 85, sometimes 95 - 90, etc. Always at different loads! (so the renders are always at different speeds... sometimes SLOWER as Win32! :o ) 

I tried "nicing" the blender-bin with "top" and that puts the process "at top", but the processors won't work 100% anyway, the speeds are always different and not so fast as I expect... (just the same as without nice)

Any idea how I can manage to make the processors work 100% each while rendering, so I get always the same and the fastest speed???? 

Thanks!

---

### Post by kuja on 2007-01-24
If you're expecting >~30% improvement of performance, you're going to be sorely disappointed.

---

### Post by t6435bm on 2007-01-25
hi Kuja --- well i've read ~30% doesn't apply to rendering (in such tasks, 64 bits should be really double so fast,it has something to do with floating point operations).
googling i've found a site with some benchmarks
[http://www.eofw.org/bench/index.php?sortby=1](http://www.eofw.org/bench/index.php?sortby=1)
and I downloaded the test file... i had just experimented with a small file with the logo of my company, with the  benchmarks page test file I obtained these results:
Windows 32 Threads:
	02:12.82 (10.70) 
Ubuntu 64 Threads:
	01:26:15 
That's something nearer to that what i expected. Apparently with this longer time, the processors work almost 100% all the time --- but anyway, my question remains, because they go down to 99, 98, or 95 some times while rendering...
I attached 4 captures from gnome-system-manager taken while rendering. The question is: how do I tell the kernel to use both processors 100% while rendering? How do I obtain the same behavior each time I render the same file?

---

### Post by RAOF on 2007-01-25
Probably the lower-than-100% cpu usage is becuase there's not actually enough work for both processors.

Things like waiting for disc access or waiting for the results of an operation on the other core can mean that there's not actually enough work for a core - the kernel can't assign more work than there is :)

---

### Post by kuja on 2007-01-25
I gave it a whirl and it seems like it hit 100% pretty consistently, however, when one core was working the other was not ... probably some sort of threading issues. Anyways, it took my processor 1:58(though, I don't think the threading was working properly for me :\) , what processor do you have that yours did it in 1:26, only thing I can think of that would run away like that is a core2, am I right?

---

### Post by kuja on 2007-01-25
I take that back :D I found out how to enable the threading ... stupid me, anyhow, 1:03!

---

### Post by t6435bm on 2007-01-27
so... kernel assigns work... user has no control over it... am i right?
but --- there is at least a way to assign one of the cores exclusively to one or two jobs, isn't there?
inform me -- i'm just leaving my linux newbie level (what comes after newbie? is there a way to know when you stop being a newbie????? :( )

---

### Post by RAOF on 2007-01-28
> **t6435bm said:**
> so... kernel assigns work... user has no control over it... am i right?
but --- there is at least a way to assign one of the cores exclusively to one or two jobs, isn't there?
...

Yeah, the user has little control over how the work is assigned.  Nice-ing something is pretty much the level of control you have.

As for the "assign one core exclusively to a task", as far as I'm aware you can't.  And that it would also be a sub-optimal use of resources - something at nice -20 is already getting as much processor time as it can use.  Any fall from 100% CPU utilisation is a result of the process not being able to supply the CPU with enough work quickly enough!

Locking one core to be exclusively for a task would reduce CPU utilisation, and could possibly **slow down** the rendering task (because the spare CPU cycles won't be used for productive work, like pre-fetching stuff from the harddrive).

---

