---
title: "64bit vs. 32bit benchmark ! (not a request :-)"
date: 2008-05-13
forum: x86 64-bit Users
---

### Post by mzruya on 2008-05-13
Ok.. so i downloaded in installed ubuntu hardy 64bit alongside my 32bit installation just to test things out,
my system is - intel e6300 running @ 1.86GHZ, 2gb of 666mhz memory, and a geforce 7300gt .. ok..

i run a few tests, the first one is using the hardinfo package (apt-get install hardinfo) and the second and third ones are javascript related tests - sunspider by webkit and dromaeo by mozilla (all on firefox beta5).




Hardinfo_________________32bit__________64bit



CPU Fibonacci____________4.628________5.399    (Seconds, lower better)
CPU MD5________________ 61.243________46.045   (MiB/Seconds, higher better)
CPU SHA1________________68.792________70.679   (MiB/Seconds, higher better)
CPU Blowfish____________17.541________17.929   (Seconds, lower better)
FPU Raytracing__________23.978________11.534   (Seconds, lower better)

Sunspider________________32bit________64bit
______________________ 4037.8ms ____3560.8ms


Dromaeo________________32bit________________64bit
______________________[2028.80ms]("http://dromaeo.com/?id=10039")____[1610.40ms]("http://dromaeo.com/?id=9960")


In contrary to what most people say, that when using 64bit in a desktop enviroment you wont feel a change on things like firefox because it depends on you're connection, as we see, is not true, on heavy sites such as netvibes you can actually feel a difference, hint, try moving the widgets a little bit.

to summarize everything, who's the winner 64bit ? i don't know, you decide, what do you think about these results and do u have anything like this to compare by.

---

### Post by enchantedsky on 2008-05-13
To be fair, it's not a true test if you're testing a 64-bit system with 32-bit applications. Test a 64-bit OS with 64-bit applications and call me in the morning :)

---

### Post by mzruya on 2008-05-14
who said the applications werent 64bit ?
i'm not sure, but installing from repository, arent they suppose to be 64 bit by default ?

---

### Post by dnns123 on 2008-05-14
Aren't the apps 32-bit? these things dont have 64-bit versions yet.
If these things are 64-bit, we'd see some real improvement

---

### Post by Jouke74 on 2008-05-14
Actually he only needed to have installed the 32bit Hardinfo on i386 system and 64bit Hardinfo on AMD64 system. If the program is 64 bit then the within tests will be as well, if they are all optimized for 64 bit is something else. Using synaptic I cannot imagine that thing going wrong, and I actually think he has done it right. Both MD5 checksum and the Raytracing show huge improvements, excactly two tests with most intensive calculations.

The java scripts are interesting because the scripts probably don't change. That means that the whole Java enigine (which one?) is doing it's work quicker in 64bit environment vs 32 bit. Even if he would be running 32 bits under 64 bits OS, it's funny to see it's faster.

---

### Post by Sef on 2008-05-14
Going to 64-bit from 32-bit won't make a big difference with speed unless you do gaming, video editing, or other intensive memory processes.  I had 3000 files with about 2/3 photos, and it took me about 20-30 minutes to download the files to the usb key; once on 64-bit, it took less than 4 minutes to upload them.

---

### Post by mzruya on 2008-05-14
that's because usb stick write and read speeds are on two completely opposite sides of the scale :-) not much to do with 32/64bit

---

### Post by Vadi on 2008-05-14
Hardinfo does *not* give reliable results, it's author told me. Use the Phoronix Test Suite instead for benchmarking.

---

