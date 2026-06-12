---
title: "CPU Usage"
date: 2008-11-20
forum: x86 64-bit Users
---

### Post by Thelasko on 2008-11-20
When I open the system monitor, it says that neither of my cores are dropping below 10%.  They usually bounce between 10 and 20%.  The only programs I have open is Pidgin and the System Monitor.  Under the processes tab it says that the system monitor is using 1-5%, everything else is zero.  I have an Intel Core 2 Duo processor @ 1.8GHz and a Intel 965 integrated graphics card.  Is this normal?

---

### Post by The Doell on 2008-11-20
Hi, Thelasko

You could run the command

$ top

It will show all the process with their CPU%  and some other useful information.  Hopefully this will help show you what is causing this.

---

### Post by teddks on 2008-11-20
You should also make sure System Monitor is configured to show all processes running on the system, not just your own.

---

### Post by Thelasko on 2008-11-20
> **The Doell said:**
> Hi, Thelasko

You could run the command

$ top

It will show all the process with their CPU%  and some other useful information.  Hopefully this will help show you what is causing this.

```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5574 root      20   0  511m 102m 9180 S    1 10.3 118:55.61 Xorg               
31039 lasko     20   0  253m  22m  10m S    1  2.3   0:00.42 gnome-terminal     
    1 root      20   0  4020  888  600 S    0  0.1   0:02.22 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.46 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.10 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:02.76 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:05.92 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   44 root      15  -5     0    0    0 S    0  0.0   0:00.02 kblockd/0          
   45 root      15  -5     0    0    0 S    0  0.0   0:00.02 kblockd/1          
   48 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid             
   49 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify       

```
Edit: right after I posted this, the system monitor showed the processors running at 10% and 6%.

---

### Post by Thelasko on 2008-11-20
> **teddks said:**
> You should also make sure System Monitor is configured to show all processes running on the system, not just your own.

How would I do that?

---

### Post by zzHanks on 2008-11-20
> **Thelasko said:**
> How would I do that?
System Monitor > View > All Processes

Note: It takes some CPU to view the resources - I added System Monitor to my panel, more accurate.

---

### Post by Arup on 2008-11-21
Better way to monitor is to install GkrellM from the repos, it gives you a clear real time core by core read out of CPU load, if you have lm-sensors and hdd temp installed, you also get the core temp, fan speed, voltage and hdd temp as well. All in a slick inteface which can be placed anywhere on the desktop and monitored from time to time. It also shows disk activity and net banwidth.

---

### Post by aboud on 2008-11-21
hi there..

view > all porseccess is disabled even i tried,  

sudo gnome-system-monitor

all the list is gray.

i have similar problem but i now the culprit. usr/bin/X, it's not going below 20 of CPU, bouncing 20 to 40, even 50 or 60. 
firefox is not going under 10 either. :(

nice- isn't helping to.

ubuntu 8.04/sonyVaio.

---

### Post by teddks on 2008-11-21
Firefox is probably using a lot of X calls which are making it do a lot of work, hence your CPU problem.

Firefox is heavyweight by nature, and slimming it down is a challenge. I've found a few things that help. Installing the noscript plugin (in the package mozilla-noscript) disables javascript by default according to a blacklist/whitelist will reduce a lot of X usage. It will also block flash, which reduces the load on X even further. You can also avoid behaviors that stress out Firefox, like opening a lot of tabs at once.

---

### Post by Thelasko on 2008-11-21
> **teddks said:**
> Firefox is probably using a lot of X calls which are making it do a lot of work, hence your CPU problem.
This is with Firefox closed.  I've noticed that Firefox uses a lot of CPU, but I'm more concerned about idle, and any excess heat/electricity.

---

