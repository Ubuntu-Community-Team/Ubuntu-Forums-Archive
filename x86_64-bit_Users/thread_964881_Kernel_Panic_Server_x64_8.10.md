---
title: "Kernel Panic Server x64 8.10"
date: 2008-10-31
forum: x86 64-bit Users
---

### Post by qaiser on 2008-10-31
I get a Kernel panic when running a hellanzb (pythin twisted news client, par2 and unrar)  It could be related to hardware.  The screen shows the call trace, which I have photographed.  File server runs perfectly otherwise.  Problem is repeatable and occure after about 4GB is downloaded, but thus varies.  Hardware has worked fine for over 18 mths.

  Call trace shows:
? enqueue_hrtimer+0x8a/0x140
error_entry+0x50/0x62
? search_extable+0x4c/0x80
? search_extable+0x9/0x80
search_exception_tables+0x21/0x50
fixup_exception+0x0/0x40
do_page_fault+0x19e/0x750
? set_cyc2ms_scale+0x26/0xb0
? getnstimeofday+0x57/0xd0
? set_normalized_timespec+0x32/0x90
? sys_nanoslep+0x20/0x80
? sched_clock_cpu+0x74/0x160
? enqueue_hrtimer+0x40/0x140
error_exit+0x0/0x70

Hardware info and full call trace in attachments.

Thank you for help in how to troubleshoot this!

---

### Post by qaiser on 2008-10-31
Sorry, now uploaded correct hardware information.

:)

---

