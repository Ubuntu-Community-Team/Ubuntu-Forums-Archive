---
title: "64 bit / amd64 : oom killer doesn't"
date: 2008-07-15
forum: x86 64-bit Users
---

### Post by mdmbkr on 2008-07-15
Hi,

I've experienced a few hard lockups due to an out of memory condition on an amd64 system.  It's my understanding that this shouldn't be possible - the kernel should start killing processes when memory runs out.

If I compile and run this little C program, a kernel panic will result:

```

#include <stdio.h>
#include <stdlib.h>

#define MEGABYTE 1024*1024

int main(int argc, char *argv[])
{
        void *myblock = NULL;
        int count = 0;

        while (1)
        {
                myblock = (void *) malloc(MEGABYTE);
                if (!myblock) break;
                count++;
                if (count % 1000 == 0) printf("Currently allocating %d MB\n", count);
        }
        
        exit(0);
}

```

One amd64 system I've run it on is equipped with two dual core opteron 265's, 8GB of physical memory, and 100MB of swap.  The above C program will allocate about 232,000MB before hanging.  About 30-45 minutes later, the kernel will panic.

A possibly related bug report (from 2005!): [http://bugzilla.kernel.org/show_bug.cgi?id=5665](http://bugzilla.kernel.org/show_bug.cgi?id=5665)

Any insight would be much appreciated.

---

### Post by Tomatz on 2008-07-16
<snip>

---

### Post by Tomatz on 2008-07-16
<snip>

---

### Post by mdmbkr on 2008-07-16
The swap space is small to prevent the kernel swapping out mysql's buffer.

But the above program doesn't write to memory, it just allocates it, and as far as I can tell, swap never even starts filling up when the machine stops responding.

I have a few amd64 systems at hand and they all seem to have the same behavior regardless of swap size.

They're all running up-to-date Hardy.

This is a major problem because users on these systems routinely use big chunks of memory for hours or days.  If one user asks for more than what's available, the machine DIES, taking everyone's work with it, instead of just killing one process!

---

### Post by mdmbkr on 2008-07-16
I just booted up 2.6.24-19-server.

```

# uname -a
Linux myhostname 2.6.24-19-server #1 SMP Fri Jul 11 21:50:43 UTC 2008 x86_64 GNU/Linux

```

Now the program can allocate over 1.3 terabytes before things hang up.  I modified the code so it only prints every 1000MB instead of each MB:

```

Currently allocating 1343000 MB
Currently allocating 1344000 MB
Currently allocating 1345000 MB
Currently allocating 1346000 MB

```

And then it hangs ...

At this time I can't provide the last moments of kernel logging since I don't have a camera at hand.  I will do that if I get a chance.

But I can see that the oom killer is operating.  It kills mysqld repeatedly (different PID's each time), as well as jsvc (I guess that's tomcat?).  But it doesn't kill the allocating program (I've called it 'memtest1' .. heh).

Meanwhile, until the panic, the machine responds to pings - and nothing else.

---

### Post by mdmbkr on 2008-07-16
Is it possible that by allocating so many chunks of memory to the test program, the kernel itself is using all the memory on the system?

Is there anything in place to deal with such a situation?

---

### Post by mdmbkr on 2008-07-16
Another data point.

I compiled and ran the following program (call it 'memtest2').  This is different from the first program in that it actually writes to the memory allocated to it.

```

#include <stdio.h>
#include <stdlib.h>

#define MEGABYTE 1024*1024

int main(int argc, char *argv[])
{
        void *myblock = NULL;
        int count = 0;

        while(1)
        {
                myblock = (void *) malloc(MEGABYTE);
                if (!myblock) break;
                memset(myblock,1, MEGABYTE);
                count++;
                if (count % 1000 == 0) printf("Currently allocating %d MB\n", count);
        }
        exit(0);
        
}

```

Note: I got both programs from [here]("http://www.linuxdevcenter.com/pub/a/linux/2006/11/30/linux-out-of-memory.html") and modified them to print only every 1000MB instead of every 1MB.

'memtest2' only makes it to 7000MB before the machine starts churning.  I don't know if it results in a panic, just an indefinite hang until a really long string of ^C's manages to find its way and kill the process.

dmesg shows that the OOM killer has struck everything but 'memtest2': apach2, java, even cron and bash.

Shouldn't 'memtest2' be the first and most obvious candidate for the OOM killer?

What's going on?

---

### Post by mdmbkr on 2008-07-16
By following the recommendations (regarding sysctl settings) [here]("http://ressukka.net/blog/tags/ubuntu/"), I can run the two memtest programs without crashing the system.

In short, add the following to sysctl.conf and issue a force-reload to /etc/init.d/procps:

```

vm.overcommit_ratio = 100
vm.overcommit_memory = 2
```

They both fail after 7000MB but before 8000MB on my system with 8GB memory and 100MB swap.

1) Why is this not the default configuration?

2) If there's a good answer to the above question, does this mean there is, after all, an issue with OOM killer behavior?

---

### Post by Tomatz on 2008-07-16
Is the problem only with the 64 bit kernel? If so have you thought about compiling your own?

---

### Post by mdmbkr on 2008-07-16
I have access to one 32 bit system:

```
Linux ut 2.6.24-19-386 #1 Fri Jul 11 22:45:14 UTC 2008 i686 GNU/Linux

```

memtest1:

```

joe@ut:~$ ./memtest1
Currently allocating 1000 MB
Currently allocating 2000 MB
Currently allocating 3000 MB
joe@ut:~$

```

(completes instantly)

memtest2:

```

joe@ut:~$ ./memtest2

```

(hangs)

Eventually it stopped responding to pings.  When I checked the console, xdm was still on the screen, but locked up hard.  So I'm not positive that it panic'd, but the lack of ping response points that way.

This system is equipped with 1GB memory and 100MB swap.

---

### Post by Tomatz on 2008-07-16
I wonder if this problem is just specific to the latest kernel (2.6.24-19-386)? I will see if i can replicate the problem in gutsy but it will have to be tomorow now as its nearly midnight here :)

---

### Post by mdmbkr on 2008-07-22
Any luck?

I tried changing overcommit_memory in /proc/sys/vm to "2", and setting the overcommit_ratio to 100.

It does seem to prevent the machine completely choking to death with no memory available.

But it also prevents some programs from running at all.  For instance, javac sometimes won't start, and I often see errors from tomcat 5.5 when shutting down.

All I want is to avoid my systems dropping to their knees any time some userland code asks for a bit too much memory!

---

### Post by centurian on 2008-10-10
Did you get a solution to the OOM problem?

---

### Post by mdmbkr on 2008-10-10
No.

I had some luck tweaking the overcommit settings.

To prevent the kernel allocating memory that doesn't exist, first make sure there is plenty of available memory, then insert the following into /etc/sysctl.conf and issue a force-reload to /etc/init.d/procps: 

vm.overcommit_ratio = 100
vm.overcommit_memory = 2

If there is not enough available memory at the time you call force-reload, things can go south.

But these settings don't really solve the problem, because there are many programs that routinely ask for massive amounts of memory that they will never use.  Sun javac appears to be one such program.  Using the above settings on a machine with 8GB of memory, javac will not run.

So, back to square one: rely on the OOM killer. The problem here is that it never seems to kill the right process; the system almost always just bogs down for a couple of hours. If you're lucky you can log in at the console or possibly through ssh and kill the troublemaker; if unlucky the system will need a hard reset (use the magic sysrq keys).

---

### Post by centurian on 2008-10-10
Thanks for the tip. 

I am not sure if sysrq will be usable over ssh when the remote system is already freezed.

---

### Post by mdmbkr on 2008-10-10
Nope, you'd have to use the real console.  And I suspect only a PS/2 keyboard would work, unless you keep a USB one plugged in all the time already.

AFAIK there's no way to send sysrq keys over ssh .. enlighten me if I'm wrong!

---

