---
title: "Bad page state ??"
date: 2008-04-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by rgeddes on 2008-04-09
I'm using Gutsy on an AMD Athlon X2, 4 GB memory, running a homegrown number crunching program.  The machine is about 7 - 8 months old.Yesterday I got this message in the /var/log/kern.log file:

---- snip

Apr  8 00:18:16 rg-server kernel: [2367988.866042] Bad page state in process 'ns'
Apr  8 00:18:16 rg-server kernel: [2367988.866044] page:ffff81023d67c550 flags:0x0200000000000000 mapping:0000010000000000 mapcount:0 count:0
Apr  8 00:18:16 rg-server kernel: [2367988.866046] Trying to fix it up, but a reboot is needed
Apr  8 00:18:16 rg-server kernel: [2367988.866047] Backtrace:
Apr  8 00:18:16 rg-server kernel: [2367988.866109] 
Apr  8 00:18:16 rg-server kernel: [2367988.866109] Call Trace:
Apr  8 00:18:16 rg-server kernel: [2367988.866123]  [bad_page+96/160] bad_page+0x60/0xa0
Apr  8 00:18:16 rg-server kernel: [2367988.866127]  [get_page_from_freelist+1255/1456] get_page_from_freelist+0x4e7/0x5b0
Apr  8 00:18:16 rg-server kernel: [2367988.866134]  [__alloc_pages+88/848] __alloc_pages+0x58/0x350
Apr  8 00:18:16 rg-server kernel: [2367988.866139]  [__handle_mm_fault+2422/2912] __handle_mm_fault+0x976/0xb60
Apr  8 00:18:16 rg-server kernel: [2367988.866147]  [do_page_fault+508/2160] do_page_fault+0x1fc/0x870
Apr  8 00:18:16 rg-server kernel: [2367988.866151]  [do_mmap_pgoff+1560/2160] do_mmap_pgoff+0x618/0x870
Apr  8 00:18:16 rg-server kernel: [2367988.866155]  [do_munmap+657/752] do_munmap+0x291/0x2f0
Apr  8 00:18:16 rg-server kernel: [2367988.866160]  [error_exit+0/132] error_exit+0x0/0x84
Apr  8 00:18:16 rg-server kernel: [2367988.866166] 

---- snip
'ns' is the name of the number crunching program I'm running.


Today the computer froze.  I had to reboot the system.

Does this look like a hardware problem?  Should I be looking in other log files for clues of the problem? Any advise is greatly appreciated.  

Thanks
R

---

### Post by kuja on 2008-04-09
Well it's either hardware or software, the hardware is easy to check, you'd want to reboot into memtest and let it run for up to a day. If the memory checks out okay I would assume it's a software problem.

---

