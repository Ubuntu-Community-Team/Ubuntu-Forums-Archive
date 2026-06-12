---
title: "Nvidia Drivers on 64bit Issue"
date: 2009-03-10
forum: x86 64-bit Users
---

### Post by Silkjc on 2009-03-10
Hey there, this problem has been griping me for a few days now.

I am using a Sony Vaio laptop with the 2.6.27-11 AMD64 kernel. When attempting to load the Nvidia drivers, I get 'Failed to insert Nvidia kernel module'. My system has two DIMMs in use, 2GB and 1GB. Video card is a Geforce Go 7400 with 128mb dedicated memory. If I physically remove the 1GB stick the Nvidia kernel module insertion works correctly and the drivers load fine. 

Attempting to emulate the physical removal of the second memory stick, I tried booting with mem=2048M passed to the kernel. This results in a garbled X display on boot. 

I'm looking for a way to resolve this, even if it means not using all the memory. However I wish to leave it physically installed as it is used by other operating systems installed. Since the laptop is Sony Vaio, there is no option in the bios to limit the memory usage.

---

### Post by athaki on 2009-03-10
Did you use the ubuntu provided drivers or did you download them from nvidia.com?

---

### Post by Silkjc on 2009-03-10
I have tried with the 173, 173 and 180 drivers provided by Ubuntu. I have also tried compiling and installing my own from the Nvidia site. They all present the same issue, failing to insert the kernel module, including the custom compiled one. On all driver versions the problem can be solved by removing the 1GB stick of memory.

---

### Post by Silkjc on 2009-03-11
I have also tried using the 32bit i386 version of Intrepid, seems to have the same problem.

---

### Post by 3Miro on 2009-03-11
> **Silkjc said:**
> I have tried with the 173, 173 and 180 drivers provided by Ubuntu. I have also tried compiling and installing my own from the Nvidia site. They all present the same issue, failing to insert the kernel module, including the custom compiled one. On all driver versions the problem can be solved by removing the 1GB stick of memory.

Did you use Ubuntu's hardware manager or did you run some script to edit xorg.conf

---

### Post by Silkjc on 2009-03-11
I used the Ubuntu hardware manager.

---

### Post by 3Miro on 2009-03-11
So you have couple of memory sticks and couple of memory slots. On a very old computer that I had, it made a difference which memory stick went where. Try inserting all of your memory using different slots.

Also look at the BIOS and see if anything about dual channel is enabled, it should not be since the different size memory modules would prevent you from running in dual channel memory mode.

It looks as the Video is trying to take up some of the system memory, I have an integrated 9300M and it uses 256MB of its own memory + 256 from the system.

---

### Post by bubwitmaingay on 2009-03-11
Sorry to disappoint you with my reply but I think the nvidia driver sucks because it caused an ugly display on my monitor after I installed it. Don't use it, I advise you. :evil:

---

### Post by stchman on 2009-03-11
> **bubwitmaingay said:**
> Sorry to disappoint you with my reply but I think the nvidia driver sucks because it caused an ugly display on my monitor after I installed it. Don't use it, I advise you. :evil:

I have three PCs that run Hardy with Nvidia cards.  They all work very well.  Two of the three PCs are 64 bit as well.

---

### Post by DeMus on 2009-03-11
> **stchman said:**
> I have three PCs that run Hardy with Nvidia cards.  They all work very well.  Two of the three PCs are 64 bit as well.

I agree. Once the driver is installed things work very well. No problems at all.

---

### Post by Silkjc on 2009-03-11
I have tried switching the DIMMs in which the memory is installed to no avail. The memory is not operating in dual channel mode, and as the system is running the Sony Vaio bios there are zero options in bios to change in regards to memory modes, timings, voltage, etc. After removing the second memory stick the machine is working perfectly with the Nvidia driver and full 3d acceleration.

---

