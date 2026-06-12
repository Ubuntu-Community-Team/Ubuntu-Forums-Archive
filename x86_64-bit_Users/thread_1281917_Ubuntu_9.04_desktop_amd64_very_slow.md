---
title: "Ubuntu 9.04 desktop amd64 very slow"
date: 2009-10-03
forum: x86 64-bit Users
---

### Post by artg@cs.nyu.edu on 2009-10-03
Hello 

  	 	 	 	 	 	  I'm running Ubuntu 9.04 desktop amd64 on a laptop.     	 	 	 	 	 	  It's a MICRO-STAR INT'L, MS-1029, with an American Megatrends Inc. BIOS with an AMD Turion(tm) 64 Mobile Technology MT-40 running at 2200MHz. The Wireless interface is a RT2500 802.11g Cardbus/mini-PCI. (More info below.)

It runs unacceptably slowly. 

The wireless runs slow, inconsistent and hot. Data rates peak at 50 KB/sec, but often stall. Other, similarly powerful laptops obtain 400 KB/s transfer rates on the same wireless network. All transfers heat the box and rev the fan. 

Other processes run slowly also. E.g., the gnome-system-monitor uses 10% to 25% of the CPU by itself. However, some interactive progrems (e.g. chess, firefox when it's not using the internet, the text editor, seem to perform OK.

How should I debug this? 

Thanks for your help.

   	 	 	 	 	BR
A


More extensive info:



It's a MICRO-STAR INT'L, MS-1029, with an American Megatrends Inc. BIOS with capabilities: isa eisa pci pcmcia pnp upgrade shadowing escd cdboot bootselect edd int5printscreen int9keyboard int14serial int10video acpi usb agp smartbattery biosbootspecification
 

 the CPU is an AMD Turion(tm) 64 Mobile Technology MT-40
 running at 2200MHz
 width: 	64 bits
capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc cpufreq
 with L1-Cache 128KiB with pipeline-burst internal varies data
 System Memory 2GiB
 and Host bridge from Radeon Xpress 200 (RS480/RS482/RX480/RX482) Chipset - Host bridge
 vendor: 	ATI Technologies Inc
 description: 	Ethernet interface
 product: 	RTL-8139/8139C/8139C+
 vendor: 	Realtek Semiconductor Co., Ltd.
 

 description: 	Wireless interface
 product: 	RT2500 802.11g Cardbus/mini-PCI
 vendor: 	RaLink
 physical id: 	
 9
 bus info: 	
 pci@0000:02:09.0
 logical name: 	
 wmaster0
 version: 	01
 serial: 	00:13:d3:67:40:f3
 width: 	32 bits
 clock: 	33MHz
 capabilities: 	pm bus_master cap_list logical ethernet physical wireless
 configuration:	
 broadcast	=	yes
 driver	=	rt2500pci
 ip	=	192.168.1.4
 latency	=	64
 module	=	rt2500pci
 multicast	=	yes
 wireless	=	IEEE 802.11g

---

### Post by erilidon on 2009-10-03
I have the same processor and no problems here. Sounds to me like it may be a video problem, is you video card installed properly with the correct drivers and such?

---

### Post by Yellow Pasque on 2009-10-03
Possibly related: [https://bugs.launchpad.net/ubuntu/+source/rt2500/+bug/330739](https://bugs.launchpad.net/ubuntu/+source/rt2500/+bug/330739)
You could try to compile the legacy driver and use that: [http://sourceforge.net/projects/rt2400/files/Final%20software%20release/rt2500-legacy-final-cvs/rt2500-cvs-daily.tar.gz/download](http://sourceforge.net/projects/rt2400/files/Final%20software%20release/rt2500-legacy-final-cvs/rt2500-cvs-daily.tar.gz/download)

---

### Post by artg@cs.nyu.edu on 2009-10-04
Hi Guys

Thanks for your reply. 
WRT a video driver, how would I determine whether the "video card was installed properly with the correct drivers and such"? I'm new to Ubuntu.

I'll investigate the RT2500 driver.

A

---

### Post by cmallam on 2009-10-04
start, system, administration, hardware drivers.

---

### Post by artg@cs.nyu.edu on 2009-10-06
> **cmallam said:**
> start, system, administration, hardware drivers.
Thanks, but that just talks about 

"Software modem ... The SmartLink modem daemon is the application part of thedriver for recent modems produced by Smart Link Ltd."

No mention of display

---

### Post by artg@cs.nyu.edu on 2009-10-06
> **Temüjin said:**
> Possibly related: [https://bugs.launchpad.net/ubuntu/+source/rt2500/+bug/330739](https://bugs.launchpad.net/ubuntu/+source/rt2500/+bug/330739)
You could try to compile the legacy driver and use that: [http://sourceforge.net/projects/rt2400/files/Final%20software%20release/rt2500-legacy-final-cvs/rt2500-cvs-daily.tar.gz/download](http://sourceforge.net/projects/rt2400/files/Final%20software%20release/rt2500-legacy-final-cvs/rt2500-cvs-daily.tar.gz/download)

But [http://sourceforge.net/projects/rt2400/](http://sourceforge.net/projects/rt2400/) says

"The Legacy Ralink drivers have permanently been deprecated in favor of the in-kernel rt2x00 drivers. See [http://rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com/") for the rt2x00 project website."

---

### Post by Yellow Pasque on 2009-10-06
> **artg@cs.nyu.edu said:**
> But [http://sourceforge.net/projects/rt2400/](http://sourceforge.net/projects/rt2400/) says

"The Legacy Ralink drivers have permanently been deprecated in favor of the in-kernel rt2x00 drivers. See [http://rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com/") for the rt2x00 project website."
Yes, but they seem to work better ;)

---

