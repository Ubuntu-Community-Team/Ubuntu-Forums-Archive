---
title: "Constant Powernow-k8 Updating???"
date: 2007-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by ncreek on 2007-10-30
I seem to have my share of problems with dear ol' Ubuntu. Well I beleive this to be a problem??? i am relatively new to the Linus/ubuntu scene, but this seems to be amiss. Every 2 secends the following line is entered in both the SYSLOG and the KERN.LOG.

"Oct 30 22:17:19 main kernel: [22437.012933] powernow-k8: failing targ, change pending bit set"

the Address and offset are constant indexed upward. This goes on constantly day and nite. What is going on here?:confused:

---

### Post by MrFSL on 2007-10-31
I have read a lot about people patching powernow-k8 due to error messages derived I believe from non standard bios'.

In all cases a kernel upgrade fixed it.

---

### Post by wiresquire on 2007-10-31
I used to have a horrible time with the acpi logging which would prevent the disk spinning down.

It caused a huge number of events in /var/log/acpid. These were not the same as yours - I think it was a description of CPU state.

Anyways, to get rid of the logging once I was happy that ACPI was working as good as it could, I set the log file to /dev/null by editing the /etc/init.d/acpid file.

I changed the lines
```

                echo -n "Starting acpid "
                startproc $ACPID_BIN

```
to
```

                echo -n "Starting acpid "
                #Modified to redirect log file to /dev/null
                startproc $ACPID_BIN -l /dev/null

```

Also, needed to edit /etc/init.d/powersaved as only it is called during boot.
changed
  $ACPID_BIN -c /etc/acpi/events.ignore
to
 $ACPID_BIN -c /etc/acpi/events.ignore -l /dev/null

hth
ws

---

### Post by bford16 on 2008-02-05
Same problem on my machine (AMD Athlon 64 X2 Dual Core on ASUS A8V-VM with standard BIOS settings).  I have seen dozens of threads all over the place, reporting the exact same problem.  No solution to date.

I tried installing the latest version of powernowd (version 1.00), and I thought the problem was solved.  Until I rebooted.  What I did was:

sudo apt-get remove powernowd

Then, I downloaded the "final release": [http://www.deater.net/john/powernowd-1.00.tar.gz](http://www.deater.net/john/powernowd-1.00.tar.gz)

A simple "make" then "sudo make install," and the latest version was installed.  So far so good, except that when I restarted the computer, it informed me that "CPU frequency scaling is not supported!" I don't know what I did wrong. It looked like cpufreqd was removed when i removed powernowd, so I reinstalled it, then restarted.  And it seemed to work, until tonight's kernel update.  once I did that, and restarted, powernow failed almost immediately.

Back to square one.

*EDIT:  *Good news!!  I think I found the cause and solution, at least for my machine.  On a whim (actually on a Saturday), I purchased a new video card for my computer.  I had been using an NVIDIA GeForce 6200 LE with 256 MB RAM; my new card is an NVIDIA GeForce 8400 GS with 512 MB RAM.  There is little difference in performance, but the constant "failing targ" errors are gone.

Speculation: The "failing targ" error was due to sharing RAM with the video card.  No sharing, no errors.  Coincidence?  Maybe, but who cares?  Now my Linux box rocks!

---

### Post by bford16 on 2008-03-25
> **ncreek said:**
> I seem to have my share of problems with dear ol' Ubuntu. Well I beleive this to be a problem??? i am relatively new to the Linus/ubuntu scene, but this seems to be amiss. Every 2 secends the following line is entered in both the SYSLOG and the KERN.LOG.

"Oct 30 22:17:19 main kernel: [22437.012933] powernow-k8: failing targ, change pending bit set"

the Address and offset are constant indexed upward. This goes on constantly day and nite. What is going on here?:confused:

I found that my "failing targ" problem went away after upgrading to an NVIDIA GeForce 8400 GS card with 512 MB RAM.  I speculate that the problem was cause by sharing RAM between the kernel and the video card.  But I'm not qualified to say...I'm just happy my system is stable now.

---

