---
title: "Screen flickering with World of Warcraft when other players on screen"
date: 2017-02-27
forum: Wine
---

### Post by leopheard on 2017-02-27
Hi all,

I'm having issues with my screen flickering with this strange flickering matrix that appears only when there is another player on screen. There can be loads of activity going on on problem, but as soon as another user's player enters the screen, it grinds to a halt and this pattern starts to flicker. Good job I don't have epilepsy!

Here are the screen shots, it cycles through this a few times a second:

[https://www.dropbox.com/sc/r7tkxbvyhagijqa/AABXfqpE4U8TtuixsRexzqzia](https://www.dropbox.com/sc/r7tkxbvyhagijqa/AABXfqpE4U8TtuixsRexzqzia)

Any advice would be appreciated, I'm hoping it doesn't require a better graphics card as this is a laptop and therefore would require a new machine entirely. I'll post some system info below

Thanks

---

### Post by leopheard on 2017-02-27
lshw and release info:

LSB Version:    core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:printing-9.20160110ubuntu0.2-amd64:printing-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

description: Notebook
product: HP 2000 Notebook PC (C2M42UA#ABA)
vendor: Hewlett-Packard
version: 0888110003305910000620100
serial: 5CG23517R4
width: 64 bits
capabilities: smbios-2.7 dmi-2.7 vsyscall32
configuration: administrator_password=disabled boot=normal chassis=notebook family=103C_5335KV G=N L=CON B=HP S=PRE X=MIN frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=C2M42UA#ABA uuid=1F61AF6D-0824-84F9-BD59-2D95A75A481E
*-display
description: VGA compatible controller
product: 2nd Generation Core Processor Family Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 09
width: 64 bits
clock: 33MHz
capabilities: msi pm vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:27 memory:c2000000-c23fffff memory:b0000000-bfffffff ioport:4000(size=64)\

---

