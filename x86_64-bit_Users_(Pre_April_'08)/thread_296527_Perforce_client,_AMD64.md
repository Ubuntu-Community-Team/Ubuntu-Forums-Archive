---
title: "Perforce client, AMD64"
date: 2006-11-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by cogitordi on 2006-11-09
There is a 64-bit Perforce server. I can't get the Perforce client (p4 and p4v) to run. Perforce says that these client tools are compiled to run in a 64-bit world. Do I still have to install the 32-bit libraries?

---

### Post by cogitordi on 2006-11-29
I've confirmed with Perforce that there is no 64-bit Perforce client.

---

### Post by cporter71 on 2006-12-28
So I am in the midst of this battle myself - Perforce claims the 32-bit versions should work but I have had no luck.  Anyone have any advice here?  The 32-bit binary was looking for 32-bit libs (of course) so I sym-linked one:

ld-linux.so.2 -> /lib/ld-linux-x86-64.so.2

... but this did not work!  When I try to execute the 'p4' library I get:

$ ./p4
bash: ./p4: Accessing a corrupted shared library

The shared component would be a result of the sym-link!

Perforce claims:
This 32-bit product release is compatible to run on systems configured to run either 32-bit or 64-bit executables.

Any advice is appreciated.  

I will also post to perforce as this is not an Ubuntu problem.

cporter

---

### Post by Ravi Chintakunta on 2007-01-02
[FONT="Courier New"]sudo apt-get install ia32-libs[/FONT]

should fix the problem.


- Ravi Chintakunta

---

### Post by Azakus on 2007-01-02
I would also recommend installing linux32. It fools programs into thinking they are running in a 32 bit version of the kernel instead of the 64 bit. Example
```
dan@dan-desktop:~$ uname -m
x86_64
dan@dan-desktop:~$ linux32 uname -m
i686

```

---

### Post by cporter71 on 2007-01-03
Excellent.  Indeed this does work.  I did install (apt-get) the following packages:
   * ia32-libs
   * libc6-dev-i386

Installing those packages puts libs in /lib32 and /usr/lib32.

From the Perforce website I [**_downloaded_**]("http://www.perforce.com/perforce/downloads/linux26x86.html") the "p4" and "p4v" 32-bit binaries for kernel 2.6 (running Edgy here).  I renamed the binaries and created "p4" and a "p4v" startup scripts with a LD_LIBRARY_PATH defined specifically for these apps/processes:

```
LD_LIBRARY_PATH=/lib32:/usr/lib32
export LD_LIBRARY_PATH

/usr/local/bin/p4.lib32.bin $*
```

In the above script, the file p4.lib32.bin is the renamed binary downloaded from the Perforce website.  I did the same for the "p4v" binary (renamed and wrapped in a script).

I hope this helps someone else.

cporter

---

### Post by pavkb on 2007-07-16
There is x86_64 bit command line version of p4 now available to download from perforce.com

---

