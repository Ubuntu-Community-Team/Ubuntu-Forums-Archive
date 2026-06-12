---
title: "Diablo 3 graphics problem"
date: 2014-11-30
forum: Wine
---

### Post by sh00t on 2014-11-30
Trying to get Diablo 3 up and running on Ubuntu 14.04 LTS
Graphics on the battle.net screen during install are all messed up, here's a screenshot;

[ATTACH=CONFIG]258299[/ATTACH]

Misc info;
Intel® Celeron(R) CPU N2930 @ 1.83GHz × 4 
Graphics card; Intel® Bay Trail 
64 bit OS
Ubuntu 14.04 LTS
VGA compatible controller; Intel Corp Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register (rev 0e)
Acer Aspire E 15 Touch E5-511P-C98M

---

### Post by QIII on 2014-11-30
When using large images, please use the attachment functionality by clicking on the paperclip icon above the text entry box.

Please be courteous to those with slow connections or data limits.

---

### Post by sh00t on 2014-12-01
QIII, sorry about the picture, will be more attentive in the future.

Jenifer, I just got the laptop about two months ago, immediately installed Ubuntu. Didn't have to mess with it, 14.04 ran perfect with everything.
here's the output of **lspci -nnk | grep -i vga -A3**
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display [8086:0f31] (rev 0e)
	Subsystem: Acer Incorporated [ALI] Device [1025:0905]
	Kernel driver in use: i915
00:13.0 SATA controller [0106]: Intel Corporation Device [8086:0f23] (rev 0e)

---

### Post by sffvba[e0rt on 2014-12-01
From that output I would be surprised if you got it to work.  I can't even find any information on the performance of the graphics system on our CPU but as soon as I see Celeron and Atom I see low performance.

As for the Battlenet app that should work at least and as Intel graphics typically just work I have to assume that something is wrong or missing in the Wine side of things.  How did you install and configure your system to run Battlenet?

---

### Post by sh00t on 2014-12-01
it works fine on Windows 8...

---

### Post by sffvba[e0rt on 2014-12-01
> **sh00t said:**
> it works fine on Windows 8...

> **not found said:**
> How did you install and configure your system to run Battlenet?

Did you just install Wine and tried to run the Executable or are you using something to assist in setting up your environemnt properly for the client to work (something like Crossover or PlayOnLinux etc)?

---

### Post by sh00t on 2014-12-01
I used PlayOnLinux and Crossover both

---

### Post by howefield on 2014-12-01
Thread moved to the *"Wine"* forum.

---

### Post by Mark Phelps on 2014-12-02
This is the link to the Wine page for Diablo 3 -- notice the mention of a bug with Intel graphics: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=29952]("https://appdb.winehq.org/objectManager.php?sClass=version&iId=29952")

---

