---
title: "4GB RAM with 945P MCH chipset"
date: 2006-03-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by pla7ma on 2006-03-24
I have an Asus P5LD2 with an Intel Pentium 4 650 (EMT64) and 4GB of RAM. (wasn't my chioce, I would have gone for the AMD stuff). As I see in meminfo, only 3.2GB are recognized (the same under windows), in the BIOS it says total memory 4GB, and "appropriated memory 896MB". According to Asus, this is an addressing issue. Now I was wondering if this could be resolved by ubuntu 64Bit, or if the problem is really at BIOS level. Or if I could at least access my swap-space. (My computations always run out of memory at around 3GB). 
Any hints would be appreciated.

Here my meminfo:

MemTotal:      3242932 kB
MemFree:       2739104 kB
Buffers:         27452 kB
Cached:         267736 kB
SwapCached:          0 kB
Active:         342444 kB
Inactive:       119084 kB
HighTotal:     2358912 kB
HighFree:      1912120 kB
LowTotal:       884020 kB
LowFree:        826984 kB
SwapTotal:     4096564 kB
SwapFree:      4096564 kB
Dirty:             408 kB
Writeback:           0 kB
Mapped:         216476 kB
Slab:            21592 kB
CommitLimit:   5718028 kB
Committed_AS:   397392 kB
PageTables:       1736 kB
VmallocTotal:   114680 kB
VmallocUsed:     10424 kB
VmallocChunk:   103828 kB

Asus comment at

[http://support.asus.com/faq/faq_right_second_detail.aspx?kb_guid=D06D6034-D5C9-49C4-5E1B-CF724DB5C000&SLanguage=en-us](http://support.asus.com/faq/faq_right_second_detail.aspx?kb_guid=D06D6034-D5C9-49C4-5E1B-CF724DB5C000&SLanguage=en-us)

---

### Post by pla7ma on 2006-03-25
Update: 
After one day of investigation, I can add the following: Ubuntu 64bit doesn't resolve the problem. However, I can at least address my swap space now. For the lost 900MB of RAM I will most likely have to change my board to one with 955X chipset or something else that supports this "memory remapping". So pay attention to which chipset you choose if you think of getting an Intel EMT64.

---

### Post by kaffeine on 2006-03-26
the issue is not with the chipset - this is a kernel issue. i've run into the same problem with 4GB RAM on a 64-bit machine, and after days of mucking around i came to know that even on a system with 4GB physical RAM the usable RAM would only show up as 3.2GB - linux reserves the rest for the kernel, so you cannot address/access that part of the memory. the only way around this is to recompile the kernel with the switch HIGH_MEM (or smthg like that, google should know) and that will load some of the kernel in the swap space and allocate more RAM for your process. 
i haven't seen any working solution yet to this problem - if you come across one, please post!

~K

---

