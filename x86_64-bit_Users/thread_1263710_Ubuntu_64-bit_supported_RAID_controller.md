---
title: "Ubuntu 64-bit supported RAID controller"
date: 2009-09-11
forum: x86 64-bit Users
---

### Post by jmarks on 2009-09-11
I am looking to rebuild my system, adding a "decent" RAID controller (i.e. not PCI x1) to my system that I will then install 64 bit Jaunty on. Looking at the adaptec site, for example, there are linux drivers available for some cards, openSuse, RedHat.
My plan is to install XP to get the system up, then add Jaunty 64 as a dual boot, then install virtualbox for "essential" windows applications so I never have to boot Windows again.

I have several questions:
1. Is there built-in generic RAID controller support in Jaunty 64-bit?

2. If not, how can I tell what manufacturer supplied drivers are Jaunty 64-compatible?

3. How do I get Jaunty up and running if I have to supply RAID drivers, and I am installing the OS onto the RAID array?

Thanks for everyone's help!

---

### Post by punkybouy on 2009-09-12
Why install Windows at all?  I installed Hardy 64 and boot that.  In Hardy I run Vbox with a Vista guest used for any Windows programs I need.  I also have an XP guest and even a W2K guest although I have not run Windows 2000 in months.
I should point out my Windows guests are all 32 bit and Hardy is 64.  Works great.

---

### Post by jmarks on 2009-09-12
> **punkybouy said:**
> Why install Windows at all?  I installed Hardy 64 and boot that.  
I should point out my Windows guests are all 32 bit and Hardy is 64.  Works great.
I may install Jaunty first and not go to a Windows system at all. My problem, however, is that I don't know how to install Linux when a hardware RAID controller is controlling all the discs.

For its RAID controllers, Adaptec supplies 64-bit drivers for Red Hat Enterprise Linux 4 and 5 as .img files. I have no idea whether which, if either, of these distros is compatible with Jaunty 64. Could the one I need for 64-bit Jaunty be AAC-RHEL4-x86_64.img?

If this img file is correct, how and when do you provide the RAID drivers during the install process?

thanks for your help.

---

