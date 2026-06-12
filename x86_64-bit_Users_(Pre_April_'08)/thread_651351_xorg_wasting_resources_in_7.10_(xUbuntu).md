---
title: "xorg wasting resources in 7.10 (xUbuntu)"
date: 2007-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by sredoje on 2007-12-27
Hello all;

I have an issue with Xorg that is quite annoying. Similar threads seem to be going in a wrong direction or to be inconclusive, so here I post

I am on AMD Athlon 3200+ with 2GB RAM and 80GB HDD (root 58% free, swap 4GB, /home 80% free). 

I was running 7.04 and recently upgraded to 7.10 (xUbuntu). The problem was present in both versions, though less in the new 7.10 one. Currently:

kernel: 2.6.22-14-generic

Xorg: 1.3.0 (April 2007)

video: ATI Radeon 9200 PRO (radeon driver) 
btw: what is "ATI driver wrapper"? I don't remember this before when I was running some other distros on this computer?

Anyways, the problem:

After login the machine is working just fine, very responsive and nice. However, I do not poweroff my computers. I just leave things running (all the programs, ... ). After some time (and I don't know how long exactly... a day, maybe? or is it the screen saver artifact?) the processor usage jumps to 58% in 7.10 by Xorg (it used to be 95% in 7.04 by Xorg). Killing the server helps (alt-control-bs) as everything returns to normal.

Also, the swiftweasel seems to be taking like 30% when running flash.

Anyone with similar problem? 

I switched to Ubuntu just so that I don't have to do upgrades myself and to keep up to date with software releases. Don't tell me I have to compile the Xorg cuz I could have done that while I was in Slack :) Anyone?

thanks,
rasha

---

### Post by nchase on 2008-01-09
Are you running gnome with session saver enabled?

If so, try this -- it seems to have helped me. Been running all morning with zero swap file/memory hogging problems from xorg:

[LIST][*]disable "Automatically remember running applications when logging out" in Sessions options (under preferences)
[*]delete ~/.gnome2/session (disabling the feature does not remove the current gnome session file, causing the session (and memory hogging behavior) to return on startup)
[*]:guitar:[/LIST]

---

### Post by Jouke74 on 2008-01-09
Before you kill the X-server next time can you state your memory usage? Check with the system monitor what is taking so much of resources. Killing X-server will kill the rest as well. Let's just say that it sounds familiar. Firefox is eating a lot of resources with me. I always assumed that it was the flash player plus wrapper.

---

### Post by sredoje on 2008-01-30
Hello all, and thanks for the responses!

Sorry for the late reply, I've been pretty much using other computers and didn't have time to bother with htis one. 

The problem occurred again. Here's TOP:

Tasks: 106 total,   3 running, 102 sleeping,   0 stopped,   1 zombie
Cpu(s): 99.7%us,  0.3%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1029164k total,  1018488k used,    10676k free,    48396k buffers
Swap:  2000084k total,   253676k used,  1746408k free,    79352k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4759 root      25   0  745m 393m 5868 R 99.2 39.1   3832:56 Xorg               
 4980 avahi     15   0 30188 1840 1116 S  0.3  0.2   3:24.46 avahi-daemon       
18890 rasha     16   0  559m 107m  24m S  0.3 10.7   5:33.35 firefox-bin        
    1 root      15   0  5116  592  516 S  0.0  0.1   0:00.75 init               
    2 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0  Tasks: 106 total,   3 running, 102 sleeping,   0 stopped,   1 zombie
Cpu(s): 99.7%us,  0.3%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1029164k total,  1018488k used,    10676k free,    48396k buffers
Swap:  2000084k total,   253676k used,  1746408k free,    79352k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4759 root      25   0  745m 393m 5868 R 99.2 39.1   3832:56 Xorg               
 4980 avahi     15   0 30188 1840 1116 S  0.3  0.2   3:24.46 avahi-daemon       
18890 rasha     16   0  559m 107m  24m S  0.3 10.7   5:33.35 firefox-bin        
    1 root      15   0  5116  592  516 S  0.0  0.1   0:00.75 init               
    2 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 events/0           
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   25 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0          
   26 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 events/0           
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   25 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0          
   26 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  
So it seems that it's Xorg on processor usage. Memory usage is strange but none of the processes is taking up way to much individually, though 30% of 1G for Xorg might be somewhat too much? :)

it just took me 30+ mins to write this and cut&paste :(

thanks,
ranko

p.s. sorry for the misleading first message.. I got my configurations all mixed up.

---

### Post by Jouke74 on 2008-01-30
Which driver are you using for ATI? FGLRX or the open source ATI Raedon?

Are you running XGL?

Did you turn on the composite extension effects in the XFCE windows manager?
> those eat a lot of resources.

Finally, are you running any KDE applications? I see a lot of k's in your top?

Try to see what happens if you don't use Firefox.... just leave it on for a day without doing anything (if possible).

---

