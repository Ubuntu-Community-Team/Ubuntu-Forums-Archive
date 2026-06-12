---
title: "Questions about windows emulation"
date: 2007-12-01
forum: Wine
---

### Post by Mysticle31 on 2007-12-01
I have finally got ubuntu up and running!

I have a question about running some windows software on Linux.

So far I know about Crossover, Wine, Parallels and of cource the ability to create virtual machines.

What is the difference of the three?  To they all emulate windows APIs?  Which one is "better"?  Are they seamless integrations? 

Is there a way to give virtual machine booting on my grub menu so it can have direct access to my hardware when necessary?

---

### Post by cogadh on 2007-12-01
CrossOver and Wine are virtually the same thing (CrossOver is based on Wine). They are both alternative implementations of the Windows API that allows Windows applications to run "natively" in the Linux environment (basically seamless). Wine is an ongoing project, so the ability to run a particular application may not be available yet, but it will be eventually.

Parallels is just one of many virtual machine products. A virtual machine requires you to install Windows into a virtual environment, nothing at all like Wine or CrossOver. You can set some virtual machines to access your previously installed OSes through raw disk access, but it is not recommended. If you want to be able to get to Windows through the boot menu, then you should just set up a dual boot system.

---

### Post by WarMonkey on 2007-12-01
> **Mysticle31 said:**
> Which one is "better"?

I use Wine, it runs pretty much all of my Windows programs (except some complex ones like Partition Magic).

---

### Post by hikaricore on 2007-12-01
> **WarMonkey said:**
> I use Wine, it runs pretty much all of my Windows programs (except some complex ones like Partition Magic).

You would never want to run anything like Partition Magic under WINE anyway.
That's a massive recipe for disaster, not to mention with tools like gparted silly.  ^_^

---

### Post by Mysticle31 on 2007-12-02
OK cool.  I had wondered about that.  

I've played with virtual machines with VMWare (before MSFT bought them).  

I just remember seeing ZEN in the SUSE grub menu and wonderd if I could boot into a virtual machine.

What do you pay for when you use CrossOver?  What does it do "better" or "worse" than wine?  Why buy it rather than use and work on Wine?

---

### Post by cogadh on 2007-12-02
CrossOver is about $40 US, but it does have a free 30 day trial. It is "better" than Wine in that it has a user friendly GUI and guaranteed support for certain applications. The only reasons to buy CrossOver are its general stability, the customer support you get as part of your purchase and that satisfaction of knowing that a large ammount of the money you spend on the product goes towards supporting the further development of Open Source software.

Wine is mostly terminal based and any support is community-based only. Wine does integrate itself into the system when installed (it becomes the default application used for .exe files and any installed apps do get an Application menu entry), but it is still usually best to use it from the terminal until whatever application you are trying to run is configured and working to your liking. Wine tends to be a little more buggy than CrossOver, but the odds that an application will work with Wine is slightly greater than on CrossOver.

---

