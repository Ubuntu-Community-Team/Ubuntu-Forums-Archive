---
title: "can I install 32 and 64 bit versions on the same system (preferably, same drive)?"
date: 2008-04-25
forum: x86 64-bit Users
---

### Post by rolandixor on 2008-04-25
:confused:
just wondering, I'd like to know if to do that. I once read that 32 bit versions on 64 bit systems are slightly slower. I would not NEED the 64 bit version (YET)-i (or sasquatch lol), but I wouldn't mind trying...

processor will be a Pentium D.

also, as a quick side note, will an ATI HD 2400 work (with desktop effects):)?

---

### Post by jespdj on 2008-04-25
32-bit software also works on 64-bit Ubuntu.

Ofcourse you can install 32-bit Ubuntu and 64-bit Ubuntu on different partitions on your harddisk. In the GRUB boot menu you'll be able to select which one you'll want to boot.

You can't install them on the same partition.

---

### Post by John.Michael.Kane on 2008-04-25
> **rolandixor said:**
> :confused:
just wondering, I'd like to know if to do that. I once read that 32 bit versions on 64 bit systems are slightly slower. I would not NEED the 64 bit version (YET)-i (or sasquatch lol), but I wouldn't mind trying...

processor will be a Pentium D.

also, as a quick side note, will an ATI HD 2400 work (with desktop effects):)?

Yes, you can run 32bit, and 64bit side by side on the same drive not the same partition, if you already have 32bit Ubuntu installed you could manually partition space for the second install or using the alternate/text mode iso allow it to partition automatically the free space for you, and install that way.

Regarding the speed issue. Speed is subjective. Some users feel there is no gains made while other say they have seen gains. At the end of day any speed you see will depend on the programs being used, and how the program has been written.

With respect to your ATI HD 2400 working with desktop effects, it should work provided you install the proper drivers for that particular card. Which according to this website [http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware) that card requires the fglrx driver 8.41.7 or higher version.

Some other info you might be interested in can be found in the thread below. [http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

---

### Post by rolandixor on 2008-04-25
thanks guys. I'll be setting up some time tonight!
I'll let you all know how it goes! :-)

---

### Post by rolandixor on 2008-05-02
Okay, all done. i skipped on 64bits for now. Everything works, including compiz (after installing fglrx) and now all I need to figure out is how to get my system sounds to work

---

### Post by jazzman65 on 2008-05-02
I did just that tonight:  installed 64 bit on the same drive as 32 bit but in a different partition of course.  So far, it's worked well, but I'm just now starting to really play with it.

The only thing that puzzles me is that the system monitor only reports 3.0 GB of RAM, even though the system has 4 GB.  My mobo definitely supports that much and reports that much, but Hardy doesn't report it.

Since I'm completely new to 64 bit, is the kernel the same as the 32 bit or is it called something different?  Seems like in the grub it reads the same as the 32 bit version.  Just seems strange that the system monitor reads pretty much exactly the same for both versions.  How would you tell the difference?

Thanks!

---

### Post by jazzman65 on 2008-05-02
I'm a noob, but at least I think I'm progressing!  :lolflag:

I think I've discovered that uname -a is the command that tells you exactly what version of kernel you have.  For example:

rodney@rodney-desktop:~$ uname -a
Linux rodney-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux

---

### Post by rolandixor on 2008-05-05
Hi jazzman65!
You'll know the difference when you get more RAM, lol...
It only makes a huge difference when you begin to use large, RAM hungry apps (like doing a fluid sim on blender that's big enough to make your system need more than 4GBs...

---

### Post by Kilz on 2008-05-05
> **rolandixor said:**
> Hi jazzman65!
You'll know the difference when you get more RAM, lol...
It only makes a huge difference when you begin to use large, RAM hungry apps (like doing a fluid sim on blender that's big enough to make your system need more than 4GBs...

Nope, there is an overall slight increase. Those that go from 32bit to 64bit report it all the time. Then there are application that get a 30% or more boost like rendering anything in blender, encoding things like when you rip cd's or backup dvd's, and any other application that crunches numbers. Its not just one app, but probably 10-20 you will use all the time.
Why not try the 64bit version since you planned to originally, odds are you are going to have to do no more setup than you did with the 32bit version.

---

### Post by jazzman65 on 2008-05-05
I got my 64 bit install up and running this weekend and so far, so good.  It's not that I really _need_ the extra horsepower, but if my system is equipped for it, I figured, why not?  :)

It sure seems to me that I can tell a difference in how the system performs, definitely for the better.  The only thing is that under System Monitor, it still only shows 3.0 GB, same as in 32 bit.  I kind of expected higher than that?  The mobo lists all 4 GB in the bios, so I'm not really sure why it's not fully listed in Hardy.  Not much of a complaint though.  Overall, it's fantastic!

Now that I've gotten 64 bit installed on a separate partition, how do you go about removing the other partition?  I'd like to get rid of the 32 bit partition and go with just the 64 bit partition.  A "noob" question I'm sure, but I'm not sure how to go about doing that.  With Gpartition editor?

Thanks!

---

### Post by Kilz on 2008-05-05
> **jazzman65 said:**
> I got my 64 bit install up and running this weekend and so far, so good.  It's not that I really _need_ the extra horsepower, but if my system is equipped for it, I figured, why not?  :)

It sure seems to me that I can tell a difference in how the system performs, definitely for the better.  The only thing is that under System Monitor, it still only shows 3.0 GB, same as in 32 bit.  I kind of expected higher than that?  The mobo lists all 4 GB in the bios, so I'm not really sure why it's not fully listed in Hardy.  Not much of a complaint though.  Overall, it's fantastic!

Now that I've gotten 64 bit installed on a separate partition, how do you go about removing the other partition?  I'd like to get rid of the 32 bit partition and go with just the 64 bit partition.  A "noob" question I'm sure, but I'm not sure how to go about doing that.  With Gpartition editor?

Thanks!

[http://ubuntuforums.org/showthread.php?t=782082](http://ubuntuforums.org/showthread.php?t=782082)

---

### Post by ASULutzy on 2008-05-05
Weird that Ubuntu doesn't see all 4 GB in the 64 bit version...

What's the output of```
free
```and ```
cat /proc/mtrr
```

---

### Post by jazzman65 on 2008-05-05
> **ASULutzy said:**
> Weird that Ubuntu doesn't see all 4 GB in the 64 bit version...

What's the output of```
free
```and ```
cat /proc/mtrr
```

rodney@rodney-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:       3097280     707536    2389744          0      15788     349148
-/+ buffers/cache:     342600    2754680
Swap:      8152948          0    8152948
rodney@rodney-desktop:~$ cat /proc/mtrr
reg00: base=0xc0000000 (3072MB), size=1024MB: uncachable, count=1
reg01: base=0x00000000 (   0MB), size=4096MB: write-back, count=1
rodney@rodney-desktop:~$

---

