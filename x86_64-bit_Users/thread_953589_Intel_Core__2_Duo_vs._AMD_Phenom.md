---
title: "Intel Core  2 Duo vs. AMD Phenom"
date: 2008-10-20
forum: x86 64-bit Users
---

### Post by benoybose on 2008-10-20
Which processor gives best performance for an Ubuntu 8.04 Server Installation

a) Intel Code 2 Duo 2.6 Ghz
b) AMD Phenom 8500 2.1 Ghx

More over, Is there any issue in installing 32 Bit x86 version of Ubuntu 8.04 in a Intel's/AMD's 64 Bit machine ...?

---

### Post by Burigufutsushide on 2008-10-20
You are not very specific about which Intel CPU you mean, as there exists several Core 2 Duo 2.6 Ghz which vary in production technology and amount of cache on the die but Im assuming you mean the E4700 processor. Im also assuming you mean the AMD Phenom X3 8450 processor. 

As to which gives the best performance, most of the benchmarks I have read on these processors gives the impression that Intel is generally faster in running single processes, but the Phenoms extra core will give it an advantage when you run multi-threaded application. As your intending to use this for a server, I would expect the Phenom to perform better even though it has a lower clock-speed. 

32bit software is directly compatible with 64bit, so you should experience no issues in running a 32bit OS hardware. However, if you go with 32bit, you will have the normal 32bit limitations, like being unable to use more than 4 GB memory. But I would recommend you to run the 64bit OS unless you have very good reasons not to, as it would utilise your new hardware better.

---

### Post by ykanello on 2008-10-20
I would agree with benoybose, on the phenom/core 2 duo comparison. Something that is even more worth checking is opteron/xeon where recently I changed webservers from intel to amd, and from the data traffic and server performance I can see that the opterons can handle about 80% more traffic per core. Its not very correct to say per core, as I think in single core cpu the intel would win again. But i use this metric to explain the vast difference i see.
I measure cpu usage from snmp versus hits/sec on the httpd. 
same content for both systems. 
my 2 cents.
Y.

---

### Post by stchman on 2008-10-20
> **benoybose said:**
> Which processor gives best performance for an Ubuntu 8.04 Server Installation

a) Intel Code 2 Duo 2.6 Ghz
b) AMD Phenom 8500 2.1 Ghx

More over, Is there any issue in installing 32 Bit x86 version of Ubuntu 8.04 in a Intel's/AMD's 64 Bit machine ...?

The Core 2 line of processors are better performing than the Phenom.  That being said both will work.

---

