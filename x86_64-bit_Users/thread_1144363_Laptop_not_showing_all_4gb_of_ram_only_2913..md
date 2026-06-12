---
title: "Laptop not showing all 4gb of ram only 2913."
date: 2009-04-30
forum: x86 64-bit Users
---

### Post by brendanbbaker on 2009-04-30
I have an Acer Aspire 5735Z and just installed 4gb total ram. When I type in "free -m" in the console it only shows a total of 2913. I pressed F2 at start up but it doesnt show the ram ammount. Any ideas on how to get this to work? I am running x86_64.

EDIT: I did see that it says 4028 mb for the memory but only 2913 shows up in "free -m".

---

### Post by dcstar on 2009-05-01
> **brendanbbaker said:**
> I have an Acer Aspire 5735Z and just installed 4gb total ram. When I type in "free -m" in the console it only shows a total of 2913. I pressed F2 at start up but it doesnt show the ram amount. Any ideas on how to get this to work? I am running x86_64.

EDIT: I did see that it says 4028 mb for the memory but only 2913 shows up in "free -m".

Check any BIOS options for memory remapping etc.

---

### Post by sanderj on 2009-05-01
> **brendanbbaker said:**
> I have an Acer Aspire 5735Z and just installed 4gb total ram. When I type in "free -m" in the console it only shows a total of 2913. I pressed F2 at start up but it doesnt show the ram ammount. Any ideas on how to get this to work? I am running x86_64.

EDIT: I did see that it says 4028 mb for the memory but only 2913 shows up in "free -m".

This is a FAQ. See [http://ubuntuforums.org/showthread.php?t=1140922](http://ubuntuforums.org/showthread.php?t=1140922)

In short, do and post the output of this:

First
```
sudo lshw -short | grep memory
```
to show the physical memory installed.

Then
```
dmesg | grep e820
```
to show whether your Mobo and BIOS support memory remapping / hoisting. The important line is something like:
```
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
```
If there is no such line, upgrade your BIOS and/or search your BIOS for "memory remapping / hoisting".



Then
```
uname -a 
```
to get the bitness of the OS you're running.

Then
```
grep ' lm ' /proc/cpuinfo
``` to check that your CPU supports Long Mode meaning 64-bit

Then
```
free -m
``` to show the memory seen by the OS.

---

### Post by brendanbbaker on 2009-05-02
I see all these images online when people press F2 theres a "TOOLS" tab in that menu. Mine just shows basic junk and the boot order. Nothing else. I've only been using ubuntu for 10 days. Is there some type of button order or code or something that I press to force it to remap? When I did one of those codes in the terminal I did see that it said (2) 2gb ram 667mhz on the list.

---

