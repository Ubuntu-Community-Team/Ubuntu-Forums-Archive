---
title: "Running a process on a specific CPU"
date: 2008-04-30
forum: x86 64-bit Users
---

### Post by znoren on 2008-04-30
Hi,
I am running Hardy Heron on a Core 2 Duo, and would like to run processes on a specific CPU. How can I do this?
Thanks,

/znoren

---

### Post by soxs on 2008-04-30
Tested and works fine:
Quoted from: [http://www.cyberciti.biz/tips/setting-processor-affinity-certain-task-or-process.html](http://www.cyberciti.biz/tips/setting-processor-affinity-certain-task-or-process.html)
Under latest version of Debian / Ubuntu Linux taskset is installed by default using util-linux package. 

The CPU affinity is represented as a bitmask, with the lowest order bit corresponding to the first logical CPU and the highest order bit corresponding to the last logical CPU. For example:
```
0x00000001 is processor #0 (1st processor)
0x00000003 is processors #0 and #1
0x00000004 is processors #2 (3rd processor)
```

To set the processor affinity of process 13545 to processor #0 (1st processor) type following command:
# taskset 0x00000001 -p 13545

If you find a bitmask hard to use, then you can specify a numerical list of processors instead of a bitmask using -c flag:
```
taskset -c 1 -p 13545
taskset -c 3,4 -p 13545
```

Where,
```
-p
``` : Operate on an existing PID (you can obtain via ```
ps ax
```) and not launch a new task (default is to launch a new

Edit:
To launch a task (e.g. gimp) @ core 4 (phenom owns :-P):
```
taskset -c 4 gimp
```

Edit:
To check wether it works or not use one of those commands:
```
less /proc/interrupts
```
```
cd /sys/devices/system/cpu
ls
```
```
mpstat
```

---

### Post by Kilz on 2008-04-30
> **soxs said:**
> Tested and works fine:


You might want to consider writing a howto post for this.

---

