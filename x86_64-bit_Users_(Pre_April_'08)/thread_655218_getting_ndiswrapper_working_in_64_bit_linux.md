---
title: "getting ndiswrapper working in 64 bit linux"
date: 2008-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by go_beep_yourself on 2008-01-01
The problem with ndiswrapper is that I'm using a 32 bit Windows driver and a 64 bit Linux kernel. What is the solution to this? I've looked all over the internet, but haven't found a 64 bit .inf driver except for vista. Other drivers I found were not .sys or .inf files. My wireless usb network adapter is a trednet twe-424ub. Here is what dmesg says.

```
[  540.118116] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  540.118125] ndiswrapper (load_sys_files:216): couldn't prepare driver 'net8187b'
[  540.119153] ndiswrapper (load_wrap_driver:118): couldn't load driver net8187b; check system log for messages from 'loadndisdriver'
```

---

### Post by firecat53 on 2008-01-01
What wireless card are you using? With my Broadcom card, I just use the normal 32 bit drivers downloaded for my machine from the HP website. Are you using the stock ndiswrapper in Gutsy? And you have both ndiswrapper-common and ndiswrapper-utils-1.9 installed, right?

I'm using Gutsy 64-bit.
Good luck!  Scott

---

### Post by go_beep_yourself on 2008-01-01
> **firecat53 said:**
> What wireless card are you using? With my Broadcom card, I just use the normal 32 bit drivers downloaded for my machine from the HP website. Are you using the stock ndiswrapper in Gutsy? And you have both ndiswrapper-common and ndiswrapper-utils-1.9 installed, right?

I'm using Gutsy 64-bit.
Good luck!  Scott

First I tried ndiswrapper-common and ndiswrapper-utils-1.9. Then I realized that the Ubuntu packages are messed up. I do not have ndiswrapper-buginfo with them. Then I compiled ndiswrapper from the latest stable source code.

---

### Post by frogotronic on 2008-03-29
> **firecat53 said:**
> What wireless card are you using? With my Broadcom card, I just use the normal 32 bit drivers downloaded for my machine from the HP website. Are you using the stock ndiswrapper in Gutsy? And you have both ndiswrapper-common and ndiswrapper-utils-1.9 installed, right?

I'm using Gutsy 64-bit.
Good luck!  Scott

Really?  So you just install ndiswrapper from the repos and used the Windows XP Professional drivers from HP?  Cool.  I'm considering switching to 64 bit for Hardy and wanted to know if this would work...

I've got an HP 6910p with a Broadcom 4312 a/b/g card.

- CH

---

### Post by Jouke74 on 2008-03-29
If you are using Hardy, good luck. I have failed in Hardy also getting it to work using the method I have always used :( There is a Kernel conflict + ssb + ohci_hcd +  ndiswrapper drivers in Hardy until now. It installs and loads, but fails to connect.

For Gutsy I am using a 64 bit winXp driver and the standard ndiswrapper plus utils from the Gusty repository. What wireless card are you using (or chipset)? Please give the output of the command "lspci" in terminal?

---

### Post by rfs1970 on 2008-04-26
Its sad but its true...
Using Hardy this solution doesn't work at all

Any other idea on how to solve this issue?

Thank you,

---

### Post by rfs1970 on 2008-04-26
Its sad but its true...
Using Hardy this solution doesn't work at all

Any other idea on how to solve this issue?

Thank you,

---

### Post by frogotronic on 2008-04-26
> **Jouke74 said:**
> If you are using Hardy, good luck. I have failed in Hardy also getting it to work using the method I have always used :( There is a Kernel conflict + ssb + ohci_hcd +  ndiswrapper drivers in Hardy until now. It installs and loads, but fails to connect.

For Gutsy I am using a 64 bit winXp driver and the standard ndiswrapper plus utils from the Gusty repository. What wireless card are you using (or chipset)? Please give the output of the command "lspci" in terminal?

SOLUTION:

[http://ubuntuforums.org/showthread.php?t=734003](http://ubuntuforums.org/showthread.php?t=734003)

---

### Post by rfs1970 on 2008-04-27
Hi Cement_head!

The post that you sugest is for wireless (chipset) issue

And the problem is to set/configure a usb wireless via ndiswrapper
using a 32 bit windows driver

Unhappily I couldn't find any 64 bit version (in fact I found
for vista, but it doesn't work).

Anyway, thank you !


r.

---

### Post by Patsoe on 2008-04-27
I think there's some confusion over the HP drivers being 32bit and working on a 64bit machine... The driver package from HP that I use (labeled SP33008.exe) contains both 32bit and 64bit drivers.

So yeah, I think you do need WinXP's 64bit drivers. Plus you need the link cement_head posted.

---

### Post by frogotronic on 2008-04-27
> **Patsoe said:**
> I think there's some confusion over the HP drivers being 32bit and working on a 64bit machine... The driver package from HP that I use (labeled SP33008.exe) contains both 32bit and 64bit drivers.

So yeah, I think you do need WinXP's 64bit drivers. Plus you need the link cement_head posted.


Yep, Patsoe is correct.  That's exactly what I found with HP drivers for XP.  It's confusing and unfortunate that they are not labelled as such...BUT this means that if you can find an HP with used the same card as you have, you should be able to use their XP drivers to install on a 64 bit machine.  I did when I tried out Hardy x64.

- CH

---

