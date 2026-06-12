---
title: "Can't see all my 4GB Memory"
date: 2009-01-15
forum: x86 64-bit Users
---

### Post by goldleader on 2009-01-15
I have just installed the 64 bit version of Ubuntu 8.10 but can only see 3.4Gb of my 4GB of memory?  Can anyone help?

My system:
Asrock 4Core1333-FullHD Motherboard
Intel Core 2 Quad Q6600 2.4Ghz CPU
Nvidia 512MB PCI-E Graphics card
4GB Memory

I have updated the bios for the motherboard to the latest from the Asrock website.

Is there any reason it is only showing 3.4Gb instead of 4GB.

---

### Post by dcstar on 2009-01-15
> **goldleader said:**
> I have just installed the 64 bit version of Ubuntu 8.10 but can only see 3.4Gb of my 4GB of memory?  Can anyone help?

My system:
Asrock 4Core1333-FullHD Motherboard
Intel Core 2 Quad Q6600 2.4Ghz CPU
Nvidia 512MB PCI-E Graphics card
4GB Memory

I have updated the bios for the motherboard to the latest from the Asrock website.

Is there any reason it is only showing 3.4Gb instead of 4GB.

There are numerous posts already dealing with this exact same question, have a look at them and find one that works for you.

---

### Post by stmiller on 2009-01-16
If it's the 64bit version, it should detect all 4GB.

This is Kubuntu 8.10 64bit with 4GB of ram:

```
stmiller@brahms:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3959       2658       1301          0        108       1865
-/+ buffers/cache:        685       3274
Swap:         2439          0       2439

```

I would mess around with BIOS settings and see what might be causing issues. Here is a good thread on this: [http://ubuntuforums.org/archive/index.php/t-1001793.html](http://ubuntuforums.org/archive/index.php/t-1001793.html)

---

### Post by goldleader on 2009-01-16
Thanks for the reply.  I have searched the forums and i see there is lots of these threads, sorry for not doing that in the first place.

---

### Post by stchman on 2009-01-16
> **goldleader said:**
> I have just installed the 64 bit version of Ubuntu 8.10 but can only see 3.4Gb of my 4GB of memory?  Can anyone help?

My system:
Asrock 4Core1333-FullHD Motherboard
Intel Core 2 Quad Q6600 2.4Ghz CPU
Nvidia 512MB PCI-E Graphics card
4GB Memory

I have updated the bios for the motherboard to the latest from the Asrock website.

Is there any reason it is only showing 3.4Gb instead of 4GB.

To me it sounds like a BIOS issue.  I have 6GB on my C2Q PC running Hardy and its sees all of it.

---

### Post by felker2 on 2009-01-16
It's indeed a FAQ, so you could check the other threads.

Or ... I can test my script on you. Put this into a script, or just copy-paste it unto the command line:

```

grep lm /proc/cpuinfo
uname -a | grep x86_64
dmesg | grep e820  | grep usable | grep -vi 'BIOS-e820: 00000000'
free -m | grep Mem | awk '{ print $2 }'
echo "Ready and done"

```

Post the output here. Hint: in the ideal case, the first three lines should post output.

---

### Post by Krupski on 2009-01-16
> **felker2 said:**
> It's indeed a FAQ, so you could check the other threads.

Or ... I can test my script on you. Put this into a script, or just copy-paste it unto the command line:

```

grep lm /proc/cpuinfo
uname -a | grep x86_64
dmesg | grep e820  | grep usable | grep -vi 'BIOS-e820: 00000000'
free -m | grep Mem | awk '{ print $2 }'
echo "Ready and done"

```

Post the output here. Hint: in the ideal case, the first three lines should post output.

How about just "free -kolt"?

Here's what mine yields:

```

root@storage:/# free -kolt
             total       used       free     shared    buffers     cached
Mem:       8107564     211112    7896452          0      38864      71272
Low:       8107564     211112    7896452
High:            0          0          0
Swap:      2097144          0    2097144
Total:    10204708     211112    9993596

```

Makes sense as I have 8GB ram installed in the server...

Maybe the OP's problem is an improper BIOS setting causing a huge chunk of ram to be set aside for video (like a legacy AGP mode maybe?).

-- Roger

---

