---
title: "Habbo Hotel on Ubuntu (I'm almost there!)"
date: 2008-08-09
forum: Wine
---

### Post by Virii on 2008-08-09
I'm so close and I just need a little bit of help, 
> 
1- Once taskset is installed, simply append taskset 01 before the command you use to run Firefox for Windows.
taskset 01 wine firefox.exe

All this does is cause Firefox to run on your first processor core, as the Shockwave + Firefox + Windows environment combination doesn't seem to enjoy multi-core systems.

To verify Firefox for Windows is indeed running on one core, enter
ps -A|grep firefox.exe
in a terminal. The far-left number will be the PID. Next, enter
taskset -p PID-from-previous-command
The result should be pid X's current affinity mask: 1

Enjoy your stable Habbo on Linux!

I followed that small tutorial, and i'm just getting this error in terminal, please help. I got all the fonts set right

This is from when I load the hotel 

```
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
wine: Call from 0x7b844360 to unimplemented function gdiplus.dll.GdipAddPathRectangleI, aborting
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

```

And i entered the 2 codes it said on that tut in a seperate terminal and i get this?

```
matt@office:~$ ps -A|grep firefox.exe
17316 pts/0    00:00:02 firefox.exe
matt@office:~$ taskset -p PID-from-previous-command
taskset (util-linux-ng 2.13.1)
usage: taskset [options] [mask | cpu-list] [pid | cmd [args...]]
set or get the affinity of a process

  -p, --pid                  operate on existing given pid
  -c, --cpu-list             display and specify cpus in list format
  -h, --help                 display this help
  -V, --version              output version information

The default behavior is to run a new command:
  taskset 03 sshd -b 1024
You can retrieve the mask of an existing task:
  taskset -p 700
Or set it:
  taskset -p 03 700
List format uses a comma-separated list instead of a mask:
  taskset -pc 0,3,7-11 700
Ranges in list format can take a stride argument:
  e.g. 0-31:2 is equivalent to mask 0x55555555
```

---

