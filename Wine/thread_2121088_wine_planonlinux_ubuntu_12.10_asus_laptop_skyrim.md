---
title: "wine planonlinux ubuntu 12.10 asus laptop skyrim"
date: 2013-02-28
forum: Wine
---

### Post by worthspending on 2013-02-28
Hello:

I'm trying to get Skyrim game to run on my newphew's laptop.  Here are a few specs.

link to a video showing the problem.  at the end of the youtube video you will see that the display looks like static on a TV.
[http://youtu.be/fIx_R5FUNXc](http://youtu.be/fIx_R5FUNXc)

link to the actual specs for the laptop:  [http://support.asus.com/knowledge.aspx?SLanguage=en&p=3&s=264&m=U52F&os=30&hashedid=n/a](http://support.asus.com/knowledge.aspx?SLanguage=en&p=3&s=264&m=U52F&os=30&hashedid=n/a)

link to the processor: [http://ark.intel.com/products/50179/Intel-Core-i5-460M-Processor-3M-Cache-2_53-GHz](http://ark.intel.com/products/50179/Intel-Core-i5-460M-Processor-3M-Cache-2_53-GHz)

some output from the console

lspci -nnk
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 18)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1c22]
	Kernel driver in use: i915
	Kernel modules: i915

lshw

*-display
description: VGA compatible controller
product: Core Processor Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 18
width: 64 bits
clock: 33MHz
capabilities: msi pm vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:44 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:e080(size=8)

Originally, I was getting some type of error stating: Shader Model 3 error. blah, blah.  I finally got past that error, however, the youtube video shows the current state of the laptop.  It was about a month ago, so, I don't remember what I did to get it to the current state.

Any help moving forward would be deeply appreciated.

Thanks!!

---

### Post by ripps818 on 2013-03-01
I can't be certain, but I don't think the hardware in that laptop is capable of playing skyrim. From what I understand of the hardware, the integrated graphics would be having a real hard time handling it, even in Windows. With the computational overhead of using Wine in Linux, it's probably not possible. I have a desktop with an Intel Core i5, 16gb ddr3 ram, and a Nvida GT240 gddr5 and the performance takes a pretty big hit in Wine.

From what I recall, the i915 intel gpus are pretty poor at 3d acceleration and aren't really meant to play games like skyrim at all. I'm betting what's happening is that, somehow, Skyrim thinks you're using a better gpu than you have, and is trying to issue instructions to it that it and it's driver are unable to use. So instead your screen is getting all that static garbage instead.

You can ask about it in the Wine AppDB, but they'll probably tell you that it would be very difficult with that hardware. [http://appdb.winehq.org/objectManager.php?sClass=version&iId=24749](http://appdb.winehq.org/objectManager.php?sClass=version&iId=24749)

---

### Post by worthspending on 2013-03-01
Thank you very much.  You were very helpful.

---

