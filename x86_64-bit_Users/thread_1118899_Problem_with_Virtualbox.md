---
title: "Problem with Virtualbox"
date: 2009-04-07
forum: x86 64-bit Users
---

### Post by paul_holmes on 2009-04-07
I am trying to install Kubuntu 9.04 as a guest in Virtualbox on top of Ubuntu 9.04. I am getting an error message saying Kubuntu was expecting an x86-64 cpu but can only detect an i686 cpu. I originally used the Sun version specifically meant for amd64 type CPUs but am now using the open source edition from the repositories. Both give the same message. Can anybody help?

---

### Post by Slim Odds on 2009-04-07
> **paul_holmes said:**
> I am trying to install Kubuntu 9.04 as a guest in Virtualbox on top of Ubuntu 9.04. I am getting an error message saying Kubuntu was expecting an x86-64 cpu but can only detect an i686 cpu. I originally used the Sun version specifically meant for amd64 type CPUs but am now using the open source edition from the repositories. Both give the same message. Can anybody help?

Is your Ubuntu 9.04 the 32 bit version?

You probably need to read this:
> 1.6 64-bit guests
Starting with Version 2.0, VirtualBox also supports 64-bit guest operating systems.
Starting with Version 2.1, you can even run 64-bit guests on a 32-bit host operating
system, so long as you have sufficient hardware.
In detail, 64-bit guests are supported under the following conditions:
1. You need a 64-bit processor with hardware virtualization support (see chapter
1.2, Software vs. hardware virtualization (VT-x and AMD-V), page 10).
2. You must enable hardware virtualization for the particular VM for which you
want 64-bit support; software virtualization is not supported for 64-bit VMs.
Note: On most systems, the hardware virtualization features first need to be
enabled in the BIOS before VirtualBox can use them.
3. If you want to use 64-bit guest support on a 32-bit host operating system, you
must also select a 64-bit operating system for the particular VM. Since supporting
64 bits on 32-bit hosts incurs additional overhead, VirtualBox only enables this
support upon explicit request.
On 64-bit hosts, 64-bit guest support is always enabled, so you can simply install
a 64-bit operating system in the guest.

---

### Post by paul_holmes on 2009-04-07
No the host OS is the 64 bit version.

---

### Post by Slim Odds on 2009-04-07
> **paul_holmes said:**
> No the host OS is the 64 bit version.

Did you read any of the rest of the post?

Do you have hardware virtualization turned on?

In the BIOS also?

---

### Post by kevmitch on 2009-04-07
Most notably, did you for example select "Ubuntu 64 bit" when you set up the guest OS?

---

### Post by Slim Odds on 2009-04-07
> **kevmitch said:**
> Most notably, did you for example select "Ubuntu 64 bit" when you set up the guest OS?

Won't matter what you do if it's not enabled in the BIOS

---

### Post by dacorr on 2009-04-07
i did not think virtualbox could emulate a 64bit guest...

---

### Post by Slim Odds on 2009-04-07
> **dacorr said:**
> i did not think virtualbox could emulate a 64bit guest...

Please feel free to go ahead and read the previous posts:> 1.6 64-bit guests
Starting with Version 2.0, VirtualBox also supports 64-bit guest operating systems.
Starting with Version 2.1, you can even run 64-bit guests on a 32-bit host operating
system, so long as you have sufficient hardware.

From the VirtualBox manual.

---

### Post by paul_holmes on 2009-04-09
Thank you for your help Slim Odds. I had thought that hardware virtualization had been turned on ages ago, but it wasn,t. Kubuntu is now installing. Thanks again.

---

### Post by Slim Odds on 2009-04-09
> **paul_holmes said:**
> Thank you for your help Slim Odds. I had thought that hardware virtualization had been turned on ages ago, but it wasn,t. Kubuntu is now installing. Thanks again.

Glad to help. Glad you got it working.... (which is much more fun).

---

