---
title: "Two questions regarding AMD Athlon X2"
date: 2007-05-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ramaddan on 2007-05-03
Hi,

I)
I was planning to buy an AMD Athlon X2 processor, Socket AM2.

I was just wondering, how compatible and prepared is Ubuntu for this?

The question might sound weird, but I have never tried 64bits yet, and let alone these new processors,
so I do not know how things fair.


II)
If I were to do the above, and get the processor (after getting a motherboard), is it possible to use my previous hard drive which had the 32-bits version of Ubuntu installed, or do I have to re-install everything from scratch?

Is it as simple as just booting in using the 32-bits generic kernel for pentium 4s currently on my drive, and then install the 64 bits kernel specific kernel, and then reboot, or are things much more complicated?

Can I just install the general kernel that works on all things, before removing the drive, and then boot and log in using it, and then install the 64 bits version, or am I totally outside the radar in terms of understanding this?

Thanks for your help, and I'm really loving Feisty.

---

### Post by rai4shu2 on 2007-05-03
My system is using "AMD Athlon(tm) 64 X2 Dual Core Processor 4200+" and so far I haven't had any problems with any type of x86 environment (32 or 64 bit). My problems have all been USB-related.

---

### Post by Coucouf on 2007-05-03
I'm using Festy x86-64 on my Athlon X2 since it was released and it works perfectly.

I didn't really catch your plan of operation I must say... :)
If you want the x86-64 version of Ubuntu wou will probably have to install it from the x86-64 desktop/alternate CD.
I've not heard of any kind of 32-bit to 64-bit upgrade process.

You can maybe reuse your hard drive as is, but then it will just load the 32-bit version of Ubuntu.
If fact the AMD64 processors are fully compatible with the classical x86 32-bit mode, so your system will just work as it used to.
Well, and that would probably be a best case. Because some things like the path to your hard disk drive(s) (/dev/hd? or /dev/sd?) may change from one motherboard to the other. And then fixing it involves editing the GRUB options and maybe some other parameters...

---

### Post by Ramaddan on 2007-05-03
Thank you everyone for the replies, it really gives me confidence.

> **Coucouf said:**
> 
Well, and that would probably be a best case. Because some things like the path to your hard disk drive(s) (/dev/hd? or /dev/sd?) may change from one motherboard to the other. And then fixing it involves editing the GRUB options and maybe some other parameters...

I'm ok editing Grub and so on as long as I can change my current installed system to a 64bits system.

---

### Post by Kilz on 2007-05-03
> **Ramaddan said:**
> Thank you everyone for the replies, it really gives me confidence.



I'm ok editing Grub and so on as long as I can change my current installed system to a 64bits system.

That is not a good idea. You would be better off creating a separate 64bit partition and installing it there. Then mountint the 32bit partition as a folder. Then copying the home directory and your data over. If you run into trouble you would have a functioning 32bit install to boot up and get information with.

---

### Post by creolbuay on 2007-05-03
Hi,

I just built myself a system using the same type processor. Below is my config and all I had to do was upgrade my bios and it worked perfectly. 

AMD Athlon 64 X2 3600+ Brisbane 1.9GHz 2 x 512KB L2 Cache Socket AM2 Processor
Western Digital Caviar SE16 WD4000KS 400GB 7200 RPM SATA 3.0Gb/s Hard Drive
ASUS M2N32-SLI Deluxe Wireless Edition Socket AM2 NVIDIA nForce 590 SLI MCP ATX AMD Motherboard
OCZ Gold 512MB 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) total ram: 1.5 Gigs
BIOSTAR V6202EL16 GeForce 6200 LE 256MB TurboCache(128M VRAM on board) GDDR2 PCI Express x16

Depending on which hardware you use there maybe different procedures to get it installed.  Best of luck...

---

### Post by dptxp on 2007-05-04
Just take care that your hardware (MOBO and add-on cards) are 100% compatible so that you do not run around later looking for drivers and edit here and there. CPU is not a problem. Use 512 MB RAM min.

---

### Post by Ramaddan on 2007-05-04
Hi,

I)
I've usually had very good results with Asus, so I got myself an ASUS M2N32-SLI Deluxe MOBO,
which **creolbuay** who posted earlier, also tried and tested it, so he relieved me,
since I was kind of worried.

So the MOBO should be fine (hopefully), and the RAM I'm assuming should be fine,
so I'm left with Hard drives and Graphic card as the two main elements (I guess).

Please point out if I left out anything important.

II)
Thinking about the "upgrade" from 32 bits to 64 bits, I guess is not possible, or waste of
efficiency and so on, because one has its programs compiled using 32 bits machine code,
and the other using 64 bits.

Since one is 32 bits and the other 64 bits, I'm assuming that the assembly code for both are different,
at least different size registers, and considerations as to how to handle the difference in bits,
by the assembly code, and thus different on a machine code level.

So since the programs have already been compiled to work either in 32 bits or 64 bits,
we can't really "upgrade" them, unless they are re-compiled into their respective machine code.

Which would really mean that running a 32 bit program on a 64 bit machine will entail lots of waste
of resources, as in they will have to handle the extra wasted 32 bits in some way or form when
running a 32 bits program on a 64 bits machine.

In either case, if the above does not make sense to you, don't worry about it,
but I was just trying to apply what I have learnt studying, so I think I answered my question.

And if you know what I'm talking about, then please correct my mistakes in deduction,
as I am sure that there are some, as I am far from experienced.

III)
Thanks for everyone's help, and I will try to keep everyone posted, so that the information
can be used in the community in terms of compatible hardware and so on on Ubuntu.

However, it might take me a long time to get the machine assembled, since I am not that
free with money, and will try to find bargains (anyone know of any?).

Also, please feel free to advise me on what to get and not to get (if you have the time),
as this is my first time building a 64 bits machine (and I also seem to have gotten outdated
by what is available on the market today).

Thanks again.

---

### Post by dptxp on 2007-05-04
Why do you need a separate graphics card ? You got it in MOBO. You need
no cards. You get LAN, sound, USB etc all in MOBO.
Hard Disks have no compatibility problems with Ubuntu.
Buy 120 to 200 GB.
And a TFT (LCD) monitor.

64 bit works fine (normally). The performance boost at present is not very high.

---

### Post by Ramaddan on 2007-05-04
> **dptxp said:**
> Why do you need a separate graphics card ? You got it in MOBO. You need
no cards. You get LAN, sound, USB etc all in MOBO.
Hard Disks have no compatibility problems with Ubuntu.
Buy 120 to 200 GB.
And a TFT (LCD) monitor.

64 bit works fine (normally). The performance boost at present is not very high.

Hi,

Even though I have not seen the board yet, but these are the specs for the MOBO:

[http://www.asus.com/products4.aspx?modelmenu=2&model=1163&l1=3&l2=101&l3=0&l4=0]("http://www.asus.com/products4.aspx?modelmenu=2&model=1163&l1=3&l2=101&l3=0&l4=0")

I tried to choose one without a Graphic Card, so I can get one later myself,
but I did not mind the integrated sound card, which seems to be decent.

However, I will hold off the Graphic Card till I receive the MOBO, and take a look.

Thanks for the heads up.

Also, you said:
"64 bit works fine (normally). The performance boost at present is not very high."

How come?

Thanks.

---

### Post by dptxp on 2007-05-04
You will get good performance boost in data crunching applications.

It is like if you got 4 persons to travel, and you got one vehicle, you will reach destination in same time whether you got a car or bus.

If you got 40 persons, bus will take you in same time, you need 10 trips by car. Exclude the return time, still 10 times of time is needed by car, or bus takes 1/10 time.

Most of the time there will be 4 persons, so you do not benefit.

Also many softwares are not yet rewritten to take 64 bit advantage fully.

I use 64 bit, shortly everything will be 64 bit. We had started with 4 bit, next 8 and so on.

---

### Post by nss0000 on 2007-05-06
Gents:

Dapperx64 installed (with known issues) and zips along on my ASUS-m2n / AMD5400+ am2 / NV7600 system. Running 2.0 gigs of Crucial ram(667 not 800) and 250g sata.

Known-issues for my mobo are: 1.9 volt ram, non-functional onboad sound and ether_port. So I dropped down one notch in ram, got  SB16 and legacy NIC cards ... both automagically recognized.

CPU runs at 50-C using AMD heatsink&heatpad. I have not updated original BIOS or NV vidcard drivers.

nss
******

---

### Post by Ramaddan on 2007-06-12
Hi,

As I promised earlier, I am giving an update on my specs,
and status for future Ubuntu compatibility database entries.

System being used: Feisty Fawn 7.04

- M2N32-SLI Deluxe/Wireless Edition Motherboard
- AMD Athlon 64 X2 Dual-Core 5600+
- nVidia GeForce 7600 GS Graphic Card
- 2GB OCZ PC2 6400 Platinum Edition XTC DDR2 800 (Dual channel configuration at 800Mhz)
- Seagate 250GB Barracuda 7200.9 SATA Hard Drive (ST3250824AS)
- Pioneer DVD-RW 18x (SATA)
- Thermaltake Matrix VX Chasis

I tried both 32-bits and 64-bits version of Feisty Fawn 7.04.
The 64-bits worked significantly faster for me.

**Everything worked great, with no problems encountered.**
Hope this helps others thinking of building a system for Ubuntu in the future.

---

### Post by jusmurph on 2007-06-13
How many programs in Linux are ready for multiple Processors?

---

