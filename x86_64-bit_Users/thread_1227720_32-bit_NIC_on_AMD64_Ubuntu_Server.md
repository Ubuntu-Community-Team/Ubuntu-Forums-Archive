---
title: "32-bit NIC on AMD64 Ubuntu Server?"
date: 2009-07-31
forum: x86 64-bit Users
---

### Post by JedMeister on 2009-07-31
This may be a stupid question but anyway here goes:

I am looking to set up a Server. I will need 64-bit Ubuntu to be able to fully utilise the 8GB of RAM I have. I am only using a desktop board with a single NIC and want to add a couple more. I will be getting 2x Gigabit ethernet cards. 64-bit ones are a lot more expensive than 32-bit ones. oes the 32-bit refer to the interface with the PC or the onboard processing chip (or both)?
So is it possible to run a 32-bit NIC on 64-bit Ubuntu? D

On a side note - I am planning to run it as a virtual machine host OS. I hope to use Xen ideally. Does any one see any major hurdles with that idea?

---

### Post by dcstar on 2009-07-31
> **JedMeister said:**
> This may be a stupid question but anyway here goes:

I am looking to set up a Server. I will need 64-bit Ubuntu to be able to fully utilise the 8GB of RAM I have. I am only using a desktop board with a single NIC and want to add a couple more. I will be getting 2x Gigabit ethernet cards. 64-bit ones are a lot more expensive than 32-bit ones. oes the 32-bit refer to the interface with the PC or the onboard processing chip (or both)?
So is it possible to run a 32-bit NIC on 64-bit Ubuntu? D


I would speculate that a lot of NICs used on 64-bit systems now are 32-bit hardware just because there is not much need/advantage to using (wasting?) 64-bit on something that needs so little "horsepower".

My current system has a 64-bit bus for the built-in NIC, I seem to recall that the 64-bit M/B that I replaced a few weeks ago used 32-bit for the NIC bus.

Unless you are pumping Gigabit Ethernet traffic out of it I'd say that it is not a problem (as long as your M/B takes a 32-bit card).

---

### Post by JedMeister on 2009-07-31
Thanks for your input dcstar. 

I had a suspicion that the 32/64 bit reference on NICs was to do with their internal processing rather than the requirements of their PCI/PCI-Ex interface. I have since (I posted this thread) spoken to someone who has a number of 32-bit PCI NICs running fine on a Windows x64 system, so at this point I will assume that its do-able.

There will be heavy traffic at times but not even nearly enough to warrant the price difference between a 32-bit & 64-bit NIC. As you suggest, it probably wouldn't make that much difference anyway unless they were being contantly hammered. 

I think I have a couple of old 10/100 Mb PCI NICs laying around somewhere, I guess I'll test with them and see how we go.

Thanks again :)

---

