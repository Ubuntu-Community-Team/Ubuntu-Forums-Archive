---
title: "CPU Frequency scaling will not stay set"
date: 2008-12-27
forum: x86 64-bit Users
---

### Post by TouchuvGrey on 2008-12-27
I just upgraded to 8.10 from 8.04, finally got frequency 
scaling supported but now the setting will not stay where i 
want it. i set it to 1.80ghz and a minute later it's at 
"Userspace 800 Mhz (44%)"
HP Pavillion dv8000 laptop with an AMD Turion64.

---

### Post by itix on 2008-12-29
That is the automatic frequency scaling... it is constructed that way. 

I had that on my Eee 901 until just recently. I have read a number of different threads about disabling the automatic frequency scaling and replacing it with constant frequency scaling, however I can't find any right now.

I don't know why mine is the way it is, but I suspect that it is due to the fact that I updated to 8.10. I now have the choice of automatic frequency scaling based on different situations i.e. conservative, on demand, performance and powersaving, or constant frequency of 800 MHz, 1070 MHz, 1330 MHz and 1600 MHz.

I however don't know how to configure yours to be like mine so let's hope someone comes along that DO know.

...so BUMP :)

---

### Post by Yellow Pasque on 2008-12-29
Your CPU underclocks itself at idle to save power and extend battery life. If you want the ability to change it with a click (i.e. so you can run it at constant full speed under AC power), add the CPU Frequency monitor to your GNOME panel (right-click on a panel, "Add to panel"). Then, you can left-click it to select the CPU scaling policy.

---

### Post by itix on 2008-12-29
I thought he already had thought of that.

I have my cpu-frequency scaling monitors for my "two" cores (hyperthreading) in a drawer on the panel together with cpu-load and stuff :)

Just click on the monitor and select behavior.

---

### Post by dcstar on 2008-12-29
> **itix said:**
> I thought he already had thought of that.

I have my cpu-frequency scaling monitors for my "two" cores (hyperthreading) in a drawer on the panel together with cpu-load and stuff :)

Just click on the monitor and select behavior.

Do you still have to manually set root privileges in 8.10 for this?

---

### Post by itix on 2008-12-29
Root privileges? I don't need to do anything as root to change the cpu-frequency scaling. I didn't in 8.04 either.

---

### Post by ctarwater on 2008-12-29
I'm pretty sure that's no longer necessary, at least I didn't have to.

---

### Post by TouchuvGrey on 2008-12-29
> **Temüjin said:**
> Your CPU underclocks itself at idle to save power and extend battery life. If you want the ability to change it with a click (i.e. so you can run it at constant full speed under AC power), add the CPU Frequency monitor to your GNOME panel (right-click on a panel, "Add to panel"). Then, you can left-click it to select the CPU scaling policy.

    I do have the CPU frequency monitor set up and i have
 set it to full speed ( 1.80ghz ) it keeps resetting to a
slower speed. Though i set it at 1.60 ghz 24 hours ago 
and it's stayed there.

---

### Post by TouchuvGrey on 2009-01-04
> **TouchuvGrey said:**
> I do have the CPU frequency monitor set up and i have
 set it to full speed ( 1.80ghz ) it keeps resetting to a
slower speed. Though i set it at 1.60 ghz 24 hours ago 
and it's stayed there.

     and now it is reverting to 800mhz ( 44% ) again <sigh>. I keep it plugged  in to AC all the time.

---

### Post by itix on 2009-01-04
Does this happen while running?

Does the computer automatically scale back up when under heavy load (e.g. when you open a large program or convert mp3 to ogg...)?

---

### Post by TouchuvGrey on 2009-01-04
> **itix said:**
> Does this happen while running?

Does the computer automatically scale back up when under heavy load (e.g. when you open a large program or convert mp3 to ogg...)?  

      The only thing i have consistantly running on that computer
is [SETI@Home]("http://setiathome.berkeley.edu/")

---

### Post by steeleyuk on 2009-01-04
This is a feature of AMD processors called Cool N Quiet. You need to disable it in the BIOS if you want to stop the CPU scaling. I don't see the point though really as it justs wastes power when you're doing nothing. The CPU will scale back up to full speed as soon as you start doing something with it and will stay there until the job completes or is stopped/paused.

I also need root privileges to change the scaling in Intrepid for some reason.

---

### Post by itix on 2009-01-05
Aaah. That solves it. I was beginning to wonder if it was something like that.

---

