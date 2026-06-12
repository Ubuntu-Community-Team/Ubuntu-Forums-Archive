---
title: "not a problem but a curious question"
date: 2007-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by rexxxlo on 2007-11-18
i have the setup listed n my signature and have noticed that under certain circumstances if i look at the system monitor under resources the 2 processors will do exact mirror images to each other.

what causes this and if you feel ambitious why?

here is a screen shot

[http://i232.photobucket.com/albums/ee266/psychoacoustics/processor2.png](http://i232.photobucket.com/albums/ee266/psychoacoustics/processor2.png)

---

### Post by Ocxic on 2007-11-19
in your bios (mine at least) there is a cpu spread option ussually this optin is set to "center" which basically try's to keep the to cores running at the same load level,, never maxing out just one,, if you disable this option as i have it lets your 2 cpus run indepentantly of each other giving a small boost in performance,, i reccommend disab;ing the center spread

---

### Post by Jouke74 on 2007-11-19
Oh really? Which also means you are limiting your processor cache to use mostly just half of it...

---

### Post by binary_bob on 2007-11-19
rexxxlo,
What causes this...
Normal processor behavior under certain circumstances.
Why....
See above.

---

### Post by rexxxlo on 2007-11-19
um im not really sure what causes it next time i see it i will see what processes are using the processor  and try to figure out a pattern


oh wait i just re read your post and i thing you are stating a fact not asking a question ??? am i correct?


in my bios i do not have that option..... i don't think i will check. there is not any specific processor areas although there are some things that i do not understand  such as  shadowing and something to do with 64 or 32 bit something or other

---

### Post by binary_bob on 2007-11-19
rexxxlo,
correct.
on a more serious note, the traces are not mirror images.
Look carefully and you can see cpu1 and cpu2 are working on data differently. 
The traces would suggest cpu1 and cpu2 are sharing the workload,( perhaps a feature of dual core under heavy workloads.)
Try loading the processor with lots of applications and see if this induces the same effect.
If that doesn't repeat the effect and you don't do large scale number crunching, then maybe  your curious question is a problem after all!

---

### Post by Jouke74 on 2007-11-19
No Ocxic is right, but it is not only the BIOS which is balancing the load of the processor. Both the linux kernel as well  as the windows kernel will do the same. Maybe there is an option in his BIOS to change the way the handling is done, but I haven't got it myself (AMD X2). Also there are tools under linux and windows to set the affinity of a processor manually. 

Anyway, the disadvantage is that you will see the switching of your single heavy duty job to both cores. Of course the switching takes "some" time so that would make things "slower". The usage max of one process is one core for max  100 and the other 0%. When divided it will use 40/60 50/50 90/10 etc. If more than 100% is used another job is doing stuff as well. That's why they are not exact mirrors.

The advantages are that the full cache of the processor is used for all your jobs. The high temperature is divided over both cores and you're not wearing out just one core. Also technically there can be speed gains, but current programming is not made for that.

---

### Post by rexxxlo on 2007-11-20
so are you telling me that i have a high horsepower muscle car and snow tires ?

---

### Post by Jouke74 on 2007-11-20
I am telling you everything is fine with your car.... enjoy the ride.

---

### Post by Krydahl on 2007-11-20
If I load my system with a single process - mprime - I get a very similar pattern to yours.

If I run Mprime and do something else demanding - burn a CD say - I start to see both CPUs being used (one at nearly 100%, the other at about 40 in this case, but that's just because burning the CD doesn't require 100% of even a single core).

(Running an AMD X2 4200+ by the way.)

As I understand it, it's not practical to split the processing for a single process across both cores.

---

### Post by rexxxlo on 2007-11-20
> **Jouke74 said:**
> I am telling you everything is fine with your car.... enjoy the ride.

oh i will linux is so fun i have really began to enjoy my computer it is a total learning experience
i finally deleted xp completely its no looking back now  whooohoo


actually i would like to do something that requires 100% load to test it out kinda like a benchmark there were a few programs in xp but i don't know in linux ? any suggestions ?

although sometimes it does hiccup my old p4 2.8 occed to a 3.2 ran like a champ i would load it down with adaware, spybot, avg antivirus, utorrent and dc++  then go get on the web and watch a video to keep an eye on the temps just for fun i have a very large passively cooled watercooling setup so it never more than a few degrees above room temp 

what programs could i use in linux cuz the first 3 aren't applicable i take it no viruses and such!

and what programs would you guys recommend to overclock or should i just do it in the bios also what program should i use to keep an eye on the temps ?

thanks

---

### Post by Jouke74 on 2007-11-20
The easiest to get your processors at 100% is to open two calculators. Then in both of them enter some some funny number like 123 and use the x^y function (don't know what that is in English) with some extremely large number i.e. 123^12939473272. That will get things going. Afterwards you might want to kill the processes, so make sure that your process manager is open.

---

### Post by rexxxlo on 2007-11-20
wow well thats funny i never thought to use the calculator to make the processor max out it defiantly worked

---

