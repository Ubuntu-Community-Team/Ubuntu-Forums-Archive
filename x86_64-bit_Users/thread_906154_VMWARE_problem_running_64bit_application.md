---
title: "VMWARE problem running 64bit application"
date: 2008-08-31
forum: x86 64-bit Users
---

### Post by marcocanto on 2008-08-31
Hi,
I'm running ubuntu 8.04 64bit 2.6.24-19-generic on a new sony laptop VGN-FW11L based on the new core2 P8400 and as you can see from intel specification it's able to run vmware 64bit application : 
[http://processorfinder.intel.com/details.aspx?sSpec=SLB3R](http://processorfinder.intel.com/details.aspx?sSpec=SLB3R).
The requirement are : Intel® EM64T and Intel® Virtualization Technology.

But there is a problem, Intel EM64T/VT seem require also a BIOS support, obviously I have several computer and also an intel Quad Q6600 (where vmware run 64bit application) but in all my BIOS I have not any EM64T support option flagged.

I receive this kind of error from VMWARE :
This CPU is VT-capable, but VT is not enabled (check your BIOS settings).
You have configured this virtual machine as a 64-bit guest operating system.  However, this host's CPU is not capable of running 64-bit virtual machines or this virtual machine has 64-bit support disabled.
For more detailed information, see [http://www.vmware.com/info?id=152](http://www.vmware.com/info?id=152)

From vmware site seem a problem related to firmware/BIOS. 

Have someone an idea to workaround this issue ?
Maybe a bios / firmaware upgrade from Sony ?

Best regards

---

### Post by cliffa3 on 2008-09-14
I'm getting the same message, but mine had been working for months and just quit.  All I did was take some ubuntu updates and windows updates (vista 64 bit).  I don't think this is a config issue.  Hopefully we'll find something soon.

---

### Post by StormPCs on 2008-09-14
Try Sun's VirtualBox instead.  I have had a lot of luck with it.  I run 64 bit Vista and 32 bit XP Pro VM's simultaneously without issue.

---

### Post by cliffa3 on 2008-09-14
I paid for vmware workstation and it does work fine.  This issue would have been the same with anything else, because for some reason the VT was disabled on bootup.  Nothing but a cold boot will solve it, so even going into the BIOS and making sure it's set doesn't help because that's a warm boot.  Completely power off and power back on and it should work if it has worked before.  Read somewhere on an intel page that the VT enabled/disabled won't change unless it's a cold boot, and I didn't change mine either...just got in a messed up state somehow.  Hopefully that's your problem too, good luck.

---

### Post by StormPCs on 2008-09-14
> **cliffa3 said:**
> I paid for vmware workstation and it does work fine.  This issue would have been the same with anything else, because for some reason the VT was disabled on bootup.  Nothing but a cold boot will solve it, so even going into the BIOS and making sure it's set doesn't help because that's a warm boot.  Completely power off and power back on and it should work if it has worked before.  Read somewhere on an intel page that the VT enabled/disabled won't change unless it's a cold boot, and I didn't change mine either...just got in a messed up state somehow.  Hopefully that's your problem too, good luck.

Ubuntu is a free OS and is designed to run free software.  VMWare pretty much violates the spirit of Ubuntu (and other free distros).  If you want run software that you need to pay for you are better off running Windows or some other OS that is designed for running such software.  Why would anyone want to pollute their Ubuntu with such software?  Dual boot?

---

### Post by Kilz on 2008-09-14
> **StormPCs said:**
> Ubuntu is a free OS and is designed to run free software.  VMWare pretty much violates the spirit of Ubuntu (and other free distros).  If you want run software that you need to pay for you are better off running Windows or some other OS that is designed for running such software.  Why would anyone want to pollute their Ubuntu with such software?  Dual boot?

While some people may want to run a pure free system. There are others that feel that Linux should be able to run applications they buy. There is nothing wrong with paying for software if you feel you want to. Isnt there a freedom to run an application you want to? What difference should there be if I pay for it? Its still a freedom of choice.
Vmware is free as in beer for the player and server. The workstation is a pay product. Thats how they bring in some cash to develop the things they give away for free. VMware has Linux versions and is designed to run on Linux. They even have 64bit versions or are in the process of releasing 64bit versions.
This is not polluting anything. 
What version of Ubuntu do you run? Please point me to where it says that installing something I buy is wrong for that version.

---

### Post by sjbaugh on 2008-09-14
> Completely power off and power back on and it should work if it has worked before. 

On a laptop you may need to remove the main battery and wait for a bit before reconnecting it. (Remove the power and switch off the machine first!)

---

