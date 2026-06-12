---
title: "Top question re: # CPUs"
date: 2005-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by viniosity on 2005-10-27
I have a dual AMD64 system and I am running the 2.6.10 smp kernel. (output from uname -r is 2.6.10-5-amd64-k8-smp)

I'm not sure if I'm actually using both processors though. Is there an easy way to tell?  Here is my output from top.. I only see stats from one processsor:

```

top - 13:15:52 up 5 days,  2:54,  2 users,  load average: 0.02, 0.02, 0.00
Tasks:  75 total,   1 running,  74 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.2% us,  0.2% sy,  0.0% ni, 99.7% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:   2053364k total,  1977988k used,    75376k free,   126324k buffers
Swap:  3188860k total,       48k used,  3188812k free,  1427700k cached

```

How can I be certain I'm using both CPUs?

---

### Post by smurfDK on 2005-10-27
You propably are using both cpu's 

Try pressing the '1' key in top. This toggles the individual cpu view on and off. Then you should get something like this:

```

top - 20:10:25 up  1:06,  5 users,  load average: 0.13, 0.21, 0.26
Tasks: 115 total,   1 running, 114 sleeping,   0 stopped,   0 zombie

Cpu0  :  4.7% us,  0.3% sy,  0.0% ni, 95.0% id,  0.0% wa,  0.0% hi,  0.0% si
Cpu1  :  0.7% us,  0.7% sy,  0.0% ni, 98.3% id,  0.0% wa,  0.0% hi,  0.3% si
Mem:   2052420k total,   840640k used,  1211780k free,    32572k buffers
Swap:  1959912k total,        0k used,  1959912k free,   497556k cached

```


Also try "cat /proc/cpuinfo" and check if there is two cpu sections in the output.

Hope this helps.

---

### Post by agsansoo on 2005-10-27
Try gnome-system-monitor , to view both cpu's activities. Or 
try gkrellm ... Hope this helps !

---

### Post by viniosity on 2005-10-27
Pressing "1" did the trick.  Also confirmed via your cat /proc/cpuinfo tip.  Thanks very much for your help!  I guess I'll have to start hunting elsewhere as to why everything is so slow.. :)

---

### Post by fakie_flip on 2007-08-05
How can you get both cpu usage info to show automatically when starting top instead of having to push "1" and the same with "z". I like the colors from pushing "z".

---

### Post by Butthead on 2007-08-06
Hmm, using Dapper's amd64-generic kernel (not the k8 one) on my X2 processor shows two CPU cores showing for me up after issuing the "top" command in konsole. :confused:

When I try installing the amd64-k8 kernel (strangely referred to as "Edgy" in Adept), and rebooting, it promptly locks up the computer on me.

Any idea what might be wrong?  Do I have to compile the new kernel in some way so it will possibly work for me under Dapper 6.06?

Thanks for any help!

---

### Post by Butthead on 2007-08-07
Disregard last posting.  I'm perfectly satisfied with the performance of Dapper's 2.6.15-28-amd64-generic kernel. :guitar:

---

### Post by fakie_flip on 2007-08-08
> **Butthead said:**
> Disregard last posting.  I'm perfectly satisfied with the performance of Dapper's 2.6.15-28-amd64-generic kernel. :guitar:

There should be a configuration in a configuration file that would allow for what I said. I'd like to have top automatically start with some features instead of having to push "z" and "1" each time i start top.

---

### Post by eentonig on 2007-08-08
I use htop. It gives the dual processor output by default. And allows a lot more flexibility (adjust niceness, kill, ....)

---

### Post by fakie_flip on 2007-08-08
there should be a way to configure it with top, but i dont understand from the man page how to do it.

---

### Post by fakie_flip on 2007-08-08
> **eentonig said:**
> I use htop. It gives the dual processor output by default. And allows a lot more flexibility (adjust niceness, kill, ....)

That's not more functionality. Top does all of that too. You need to push h for help while using top and do some reading on it before you say it's missing functionality. If I want to renice a process, I push r. If I want to kill a process, I push k. Simple!

---

### Post by Butthead on 2007-08-08
> **fakie_flip said:**
> There should be a configuration in a configuration file that would allow for what I said. I'd like to have top automatically start with some features instead of having to push "z" and "1" each time i start top.

Well, Linux technically *IS* open source...;)

---

