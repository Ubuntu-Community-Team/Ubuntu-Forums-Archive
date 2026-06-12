---
title: "Karmic and system freeze due to high disk activity"
date: 2009-10-30
forum: x86 64-bit Users
---

### Post by john_navarro on 2009-10-30
I did a fresh install on Karmic on a  Dell D630. All was working great for hours then the system froze. I rebooted and things were working great for an hour or so and then it froze again. But this time I noticed that the disk drive activity was very active. System was unresponsive - couldn't Alt-F2 - mouse clicks didn't work either. Had to force shut down by holding the power button. Not sure what's causing this but thought I'd post something in case others notice this behavior as well.

Dell D630 Laptop
2GB RAM
120GB hard drive
Ext4

---

### Post by cybrsaylr on 2009-10-30
I did a clean install of Karmic also.
I've had a couple lockups also with Karmic since installing yesterday. Haven't had to 'hard shutdown' yet. Both times I had multiple browser tabs open when things froze on me. Then when I was able to close the last tab Karmic unfroze. 

So far Karmic seems a bit slower and more erratic than Jaunty was. At times browser pages take too long to load. Other times Karmic is very snappy. Wonder if Ext4 has something to do with this. This is the first time trying Ext4.

---

### Post by XyzzyZork on 2009-10-31
I'm seeing the same problem, also in a clean install but on an old Centrino laptop... I agree that it seems somehow related to disk activity, because it seems to be taking place primarily when Deluge or Synaptic are active.

Oh, you might want to use the Magic SysRq key (hold ctrl-alt and tap PrintScreen r e i s u b) to reboot -- it seems to work even in this situation, and is far less likely to corrupt the filesystem. (I'd link to a Wikipedia article on it, but the button seems to only bring up a blank popup for me right now.)

---

### Post by yosoyjay on 2009-11-01
I am seeing something similar after upgrading from 9.04 to 9.10.

Every 5 minutes, I can hear the disk spin up and it sounds like it's searching for something.  During this disk activity whatever window I have open becomes unresponsive and dims for about 10 seconds.

Is there a log or something that I can use to investigate the cause of this?

---

### Post by yosoyjay on 2009-11-01
Unfortunately, after some poking about I discovered two bad sectors on the drive that were heavily used causing the slow downs.

After the bad sectors were no longer used all of my problems disappeared.

---

### Post by MiddleRiver on 2009-11-01
I am having a similar problem on my Dell Dimension 2400.  I have a fresh install of Karmic and the only modification is the addition of my WG111v2 wireless driver using the Windows Driver utility.

How did you find the bad sectors?  I walk away from my computer and it hibernates and then locks.  It might be doing the search that you mentioned.  Hoping an update comes out soon.

---

### Post by coronacolada on 2009-11-03
I too am having the same problem. Once every 60-90 minutes, complete system freeze. Have to turn off at the power source and reboot. 

I've got an old Dell Dimension...2400? Something like that. I don't even remember. So far lots of us with the problem seem to be using Dells...

-tom

sic luceat lux

---

### Post by kgarbutt on 2009-11-03
I'm having the same problem too after a Jaunty to Karmic upgrade. Jaunty was very very stable on my hp Compaq d530 CMT. As for Karmic, it is very nice. I don't want to say a bad thing about it. My only problem with Karmic is that it freezes after a period of no use.

---

### Post by john_navarro on 2009-11-03
I'm confused because my system the lockup/sluggishness/freezing has occurred for different reasons. Perhaps there's a library common between them. These three applications have demonstrated memory leaks at different times and have been confirmed using System Monitor:

Empathy
PulseAudio
VLC

On the last instance VLC had over 1.6GB of memory used while playing a .mp3 file. Another big issue I've been having with VLC is that it will output loud static in the middle of playing an mp3 file.

I upgraded to the lastest VLC 1.03 using the PPA but I still get the memory leak and loud static noises. 

The tough part in diagnosing this is that once the system goes into this degraded state getting any further diagnostic info is very difficult.

---

### Post by josejuan05 on 2009-11-05
I'm not sure if there's any more of an official channel to communicate this through, but I'm experiencing much the same issues with VLC. Several times since I upgraded to Karmic I've had VLC playing some file (either an MP3 or an XviD AVI file with an mp3 audio stream, and the entire system suddenly became unresponsive. I would then notice my hard drive light blinking so much that the light was solidly lit up, and I couldn't hardly do anything until I opened a terminal and typed 'sudo killall vlc.'

I have also performed a variation on this procedure by pressing Alt+F2 and typing 'gksudo xkill' and then choosing the VLC window. 

The main point of my story is that it is most definitely VLC, although there may be some other daemon or program that it is acting disagreeably with. After roughly (and angrily) closing VLC my system always becomes completely responsive again, and I can even reopen VLC immediately and play through the file that had previously been playing without causing another crash.

The following showed up in dmesg after the most recent crash:
```
[12360.604048] INFO: task boinc:1233 blocked for more than 120 seconds.
[12360.604053] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[12360.604057] boinc         D c08145c0     0  1233      1 0x00000000
[12360.604064]  f1a35e3c 00000086 006a63ee c08145c0 f1c6f3a8 c08145c0 6c5efbcd 00000b15
[12360.604074]  c08145c0 c08145c0 f1c6f3a8 c08145c0 6c5e59cd 00000b15 c08145c0 f262ca00
[12360.604083]  f1c6f110 c180d5c0 00000002 f1a35e84 f1a35e48 c056ecbe f1a35e7c f1a35e50
[12360.604093] Call Trace:
[12360.604108]  [<c056ecbe>] io_schedule+0x1e/0x30
[12360.604115]  [<c01b2db5>] sync_page+0x35/0x40
[12360.604119]  [<c056f1f7>] __wait_on_bit_lock+0x47/0x90
[12360.604124]  [<c01b2d80>] ? sync_page+0x0/0x40
[12360.604128]  [<c01b2d69>] __lock_page+0x79/0x80
[12360.604135]  [<c015c2c0>] ? wake_bit_function+0x0/0x50
[12360.604141]  [<c01b4721>] find_lock_page+0x51/0x70
[12360.604145]  [<c01b4961>] filemap_fault+0x181/0x340
[12360.604150]  [<c01f2d85>] ? user_path_at+0x45/0x70
[12360.604156]  [<c0318e24>] ? copy_to_user+0x34/0x120
[12360.604160]  [<c01caa6b>] __do_fault+0x3b/0x470
[12360.604166]  [<c0127c38>] ? default_spin_lock_flags+0x8/0x10
[12360.604171]  [<c01cc264>] handle_mm_fault+0x134/0x380
[12360.604175]  [<c01f5918>] ? poll_select_copy_remaining+0x98/0x100
[12360.604181]  [<c0572cf8>] do_page_fault+0x148/0x380
[12360.604185]  [<c01f6ecd>] ? sys_select+0x3d/0xb0
[12360.604189]  [<c0572bb0>] ? do_page_fault+0x0/0x380
[12360.604194]  [<c0570be3>] error_code+0x73/0x80
[12360.604213] INFO: task wcg_hpf2_rosett:2671 blocked for more than 120 seconds.
[12360.604216] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[12360.604219] wcg_hpf2_rose D c08145c0     0  2671   1233 0x00000004
[12360.604225]  e5599e3c 00000086 e569a000 c08145c0 e5465a88 c08145c0 422e80b7 00000b15
[12360.604234]  c08145c0 c08145c0 e5465a88 c08145c0 00000000 00000b15 c08145c0 e603bc00
[12360.604244]  e54657f0 c180d5c0 00000002 e5599e84 e5599e48 c056ecbe e5599e7c e5599e50
[12360.604253] Call Trace:
[12360.604258]  [<c056ecbe>] io_schedule+0x1e/0x30
[12360.604262]  [<c01b2db5>] sync_page+0x35/0x40
[12360.604266]  [<c056f1f7>] __wait_on_bit_lock+0x47/0x90
[12360.604270]  [<c01b2d80>] ? sync_page+0x0/0x40
[12360.604274]  [<c01b2d69>] __lock_page+0x79/0x80
[12360.604278]  [<c015c2c0>] ? wake_bit_function+0x0/0x50
[12360.604282]  [<c01b4721>] find_lock_page+0x51/0x70
[12360.604286]  [<c01b4961>] filemap_fault+0x181/0x340
[12360.604292]  [<c0165316>] ? getnstimeofday+0x56/0x110
[12360.604296]  [<c01caa6b>] __do_fault+0x3b/0x470
[12360.604301]  [<c01501f6>] ? run_timer_softirq+0x156/0x200
[12360.604306]  [<c016a125>] ? tick_dev_program_event+0x45/0xe0
[12360.604310]  [<c01cc264>] handle_mm_fault+0x134/0x380
[12360.604315]  [<c0572cf8>] do_page_fault+0x148/0x380
[12360.604319]  [<c0572bb0>] ? do_page_fault+0x0/0x380
[12360.604323]  [<c0570be3>] error_code+0x73/0x80
[12360.604327] INFO: task wcg_hcc1_img_6.:2672 blocked for more than 120 seconds.
[12360.604329] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[12360.604332] wcg_hcc1_img_ D c08145c0     0  2672   1233 0x00000004
[12360.604338]  e569bf3c 00000086 f9168785 c08145c0 e5466718 c08145c0 46530c4d 00000b15
[12360.604347]  c08145c0 c08145c0 e5466718 c08145c0 463c782c 00000b15 c08145c0 e603aa00
[12360.604356]  e5466480 e569bf70 e5466480 e603aa38 e569bf68 c0570515 ffffffff f71d3780
[12360.604365] Call Trace:
[12360.604383]  [<f9168785>] ? cx88_core_irq+0x45/0x50 [cx88xx]
[12360.604388]  [<c0570515>] rwsem_down_failed_common+0x75/0x1a0
[12360.604393]  [<c057065d>] rwsem_down_write_failed+0x1d/0x30
[12360.604397]  [<c05706f6>] call_rwsem_down_write_failed+0x6/0x10
[12360.604401]  [<c056fc7f>] ? down_write+0x1f/0x30
[12360.604406]  [<c01cfc11>] sys_munmap+0x31/0x60
[12360.604410]  [<c010336c>] syscall_call+0x7/0xb
[12360.604414] INFO: task wcg_hcc1_img_6.:2694 blocked for more than 120 seconds.
[12360.604416] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[12360.604419] wcg_hcc1_img_ D c08145c0     0  2694   2672 0x00000000
[12360.604425]  e5739f18 00000086 1d000007 c08145c0 e54634d8 c08145c0 8eee47ae 00000b17
[12360.604434]  c08145c0 c08145c0 e54634d8 c08145c0 8eee0fea 00000b17 c08145c0 e603aa00
[12360.604443]  e5463240 e5739f4c e5463240 e603aa38 e5739f44 c0570515 fffeffff f285581c
[12360.604452] Call Trace:
[12360.604457]  [<c0570515>] rwsem_down_failed_common+0x75/0x1a0
[12360.604461]  [<c057068d>] rwsem_down_read_failed+0x1d/0x30
[12360.604465]  [<c05706e7>] call_rwsem_down_read_failed+0x7/0x10
[12360.604469]  [<c056fca7>] ? down_read+0x17/0x20
[12360.604474]  [<c0572f11>] do_page_fault+0x361/0x380
[12360.604478]  [<c0572bb0>] ? do_page_fault+0x0/0x380
[12360.604482]  [<c0570be3>] error_code+0x73/0x80
[12360.604486] INFO: task wcg_hcc1_img_6.:2695 blocked for more than 120 seconds.
[12360.604488] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[12360.604491] wcg_hcc1_img_ D c08145c0     0  2695   2694 0x00000000
[12360.604496]  e573be3c 00000086 e5770000 c08145c0 f267a848 c08145c0 464a1afd 00000b15
[12360.604506]  c08145c0 c08145c0 f267a848 c08145c0 00000001 00000b15 c08145c0 e603aa00
[12360.604515]  f267a5b0 c181d5c0 00000002 e573be84 e573be48 c056ecbe e573be7c e573be50
[12360.604524] Call Trace:
[12360.604529]  [<c056ecbe>] io_schedule+0x1e/0x30
[12360.604533]  [<c01b2db5>] sync_page+0x35/0x40
[12360.604537]  [<c056f1f7>] __wait_on_bit_lock+0x47/0x90
[12360.604541]  [<c01b2d80>] ? sync_page+0x0/0x40
[12360.604545]  [<c01b2d69>] __lock_page+0x79/0x80
[12360.604549]  [<c015c2c0>] ? wake_bit_function+0x0/0x50
[12360.604553]  [<c01b4721>] find_lock_page+0x51/0x70
[12360.604557]  [<c01b4961>] filemap_fault+0x181/0x340
[12360.604561]  [<c01caa6b>] __do_fault+0x3b/0x470
[12360.604565]  [<c01cc264>] handle_mm_fault+0x134/0x380
[12360.604570]  [<c0572cf8>] do_page_fault+0x148/0x380
[12360.604574]  [<c0572bb0>] ? do_page_fault+0x0/0x380
[12360.604578]  [<c0570be3>] error_code+0x73/0x80
[12360.604582] INFO: task wcg_hpf2_rosett:2696 blocked for more than 120 seconds.
[12360.604585] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[12360.604588] wcg_hpf2_rose D c08145c0     0  2696   2671 0x00000000
[12360.604593]  e576fe3c 00000086 002ea715 c08145c0 f2a46718 c08145c0 e17a429d 00000b16
[12360.604602]  c08145c0 c08145c0 f2a46718 c08145c0 e1796f4b 00000b16 c08145c0 e603bc00
[12360.604611]  f2a46480 c180d5c0 00000002 e576fe84 e576fe48 c056ecbe e576fe7c e576fe50
[12360.604621] Call Trace:
[12360.604625]  [<c056ecbe>] io_schedule+0x1e/0x30
[12360.604630]  [<c01b2db5>] sync_page+0x35/0x40
[12360.604633]  [<c056f1f7>] __wait_on_bit_lock+0x47/0x90
[12360.604637]  [<c01b2d80>] ? sync_page+0x0/0x40
[12360.604641]  [<c01b2d69>] __lock_page+0x79/0x80
[12360.604645]  [<c015c2c0>] ? wake_bit_function+0x0/0x50
[12360.604649]  [<c01b4721>] find_lock_page+0x51/0x70
[12360.604653]  [<c01b4961>] filemap_fault+0x181/0x340
[12360.604659]  [<c018f8fc>] ? handle_IRQ_event+0x4c/0x140
[12360.604663]  [<c01caa6b>] __do_fault+0x3b/0x470
[12360.604667]  [<c01915dd>] ? handle_fasteoi_irq+0x8d/0xd0
[12360.604671]  [<c01cc264>] handle_mm_fault+0x134/0x380
[12360.604676]  [<c0572cf8>] do_page_fault+0x148/0x380
[12360.604680]  [<c0572bb0>] ? do_page_fault+0x0/0x380
[12360.604684]  [<c0570be3>] error_code+0x73/0x80
[12360.604688] INFO: task wcg_hpf2_rosett:2697 blocked for more than 120 seconds.
[12360.604690] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[12360.604693] wcg_hpf2_rose D c08145c0     0  2697   2696 0x00000000
[12360.604699]  e5771e3c 00000086 f7390000 c08145c0 f68e4df8 c08145c0 464ae888 00000b15
[12360.604708]  c08145c0 c08145c0 f68e4df8 c08145c0 00000001 00000b15 c08145c0 e603bc00
[12360.604717]  f68e4b60 c181d5c0 00000002 e5771e84 e5771e48 c056ecbe e5771e7c e5771e50
[12360.604726] Call Trace:
[12360.604731]  [<c056ecbe>] io_schedule+0x1e/0x30
[12360.604735]  [<c01b2db5>] sync_page+0x35/0x40
[12360.604739]  [<c056f1f7>] __wait_on_bit_lock+0x47/0x90
[12360.604743]  [<c01b2d80>] ? sync_page+0x0/0x40
[12360.604747]  [<c01b2d69>] __lock_page+0x79/0x80
[12360.604751]  [<c015c2c0>] ? wake_bit_function+0x0/0x50
[12360.604755]  [<c01b4721>] find_lock_page+0x51/0x70
[12360.604759]  [<c01b4961>] filemap_fault+0x181/0x340
[12360.604763]  [<c01caa6b>] __do_fault+0x3b/0x470
[12360.604768]  [<c01cc264>] handle_mm_fault+0x134/0x380
[12360.604772]  [<c0572cf8>] do_page_fault+0x148/0x380
[12360.604776]  [<c0572bb0>] ? do_page_fault+0x0/0x380
[12360.604780]  [<c0570be3>] error_code+0x73/0x80
[12480.604128] INFO: task boinc:1233 blocked for more than 120 seconds.
[12480.604134] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[12480.604138] boinc         D c08145c0     0  1233      1 0x00000000
[12480.604145]  f1a35e3c 00000086 006a63ee c08145c0 f1c6f3a8 c08145c0 6c5efbcd 00000b15
[12480.604156]  c08145c0 c08145c0 f1c6f3a8 c08145c0 6c5e59cd 00000b15 c08145c0 f262ca00
[12480.604165]  f1c6f110 c180d5c0 00000002 f1a35e84 f1a35e48 c056ecbe f1a35e7c f1a35e50
[12480.604174] Call Trace:
[12480.604188]  [<c056ecbe>] io_schedule+0x1e/0x30
[12480.604195]  [<c01b2db5>] sync_page+0x35/0x40
[12480.604200]  [<c056f1f7>] __wait_on_bit_lock+0x47/0x90
[12480.604204]  [<c01b2d80>] ? sync_page+0x0/0x40
[12480.604208]  [<c01b2d69>] __lock_page+0x79/0x80
[12480.604214]  [<c015c2c0>] ? wake_bit_function+0x0/0x50
[12480.604218]  [<c01b4721>] find_lock_page+0x51/0x70
[12480.604223]  [<c01b4961>] filemap_fault+0x181/0x340
[12480.604228]  [<c01f2d85>] ? user_path_at+0x45/0x70
[12480.604234]  [<c0318e24>] ? copy_to_user+0x34/0x120
[12480.604239]  [<c01caa6b>] __do_fault+0x3b/0x470
[12480.604245]  [<c0127c38>] ? default_spin_lock_flags+0x8/0x10
[12480.604250]  [<c01cc264>] handle_mm_fault+0x134/0x380
[12480.604255]  [<c01f5918>] ? poll_select_copy_remaining+0x98/0x100
[12480.604260]  [<c0572cf8>] do_page_fault+0x148/0x380
[12480.604265]  [<c01f6ecd>] ? sys_select+0x3d/0xb0
[12480.604269]  [<c0572bb0>] ? do_page_fault+0x0/0x380
[12480.604274]  [<c0570be3>] error_code+0x73/0x80
[12480.604295] INFO: task wcg_hpf2_rosett:2671 blocked for more than 120 seconds.
[12480.604298] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[12480.604301] wcg_hpf2_rose D c08145c0     0  2671   1233 0x00000004
[12480.604307]  e5599e3c 00000086 e569a000 c08145c0 e5465a88 c08145c0 422e80b7 00000b15
[12480.604316]  c08145c0 c08145c0 e5465a88 c08145c0 00000000 00000b15 c08145c0 e603bc00
[12480.604325]  e54657f0 c180d5c0 00000002 e5599e84 e5599e48 c056ecbe e5599e7c e5599e50
[12480.604334] Call Trace:
[12480.604340]  [<c056ecbe>] io_schedule+0x1e/0x30
[12480.604344]  [<c01b2db5>] sync_page+0x35/0x40
[12480.604348]  [<c056f1f7>] __wait_on_bit_lock+0x47/0x90
[12480.604352]  [<c01b2d80>] ? sync_page+0x0/0x40
[12480.604356]  [<c01b2d69>] __lock_page+0x79/0x80
[12480.604361]  [<c015c2c0>] ? wake_bit_function+0x0/0x50
[12480.604365]  [<c01b4721>] find_lock_page+0x51/0x70
[12480.604370]  [<c01b4961>] filemap_fault+0x181/0x340
[12480.604376]  [<c0165316>] ? getnstimeofday+0x56/0x110
[12480.604380]  [<c01caa6b>] __do_fault+0x3b/0x470
[12480.604385]  [<c01501f6>] ? run_timer_softirq+0x156/0x200
[12480.604390]  [<c016a125>] ? tick_dev_program_event+0x45/0xe0
[12480.604395]  [<c01cc264>] handle_mm_fault+0x134/0x380
[12480.604400]  [<c0572cf8>] do_page_fault+0x148/0x380
[12480.604404]  [<c0572bb0>] ? do_page_fault+0x0/0x380
[12480.604408]  [<c0570be3>] error_code+0x73/0x80
[12480.604412] INFO: task wcg_hcc1_img_6.:2672 blocked for more than 120 seconds.
[12480.604415] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[12480.604418] wcg_hcc1_img_ D c08145c0     0  2672   1233 0x00000004
[12480.604424]  e569bf3c 00000086 f9168785 c08145c0 e5466718 c08145c0 46530c4d 00000b15
[12480.604433]  c08145c0 c08145c0 e5466718 c08145c0 463c782c 00000b15 c08145c0 e603aa00
[12480.604442]  e5466480 e569bf70 e5466480 e603aa38 e569bf68 c0570515 ffffffff f71d3780
[12480.604451] Call Trace:
[12480.604469]  [<f9168785>] ? cx88_core_irq+0x45/0x50 [cx88xx]
[12480.604476]  [<c0570515>] rwsem_down_failed_common+0x75/0x1a0
[12480.604481]  [<c057065d>] rwsem_down_write_failed+0x1d/0x30
[12480.604486]  [<c05706f6>] call_rwsem_down_write_failed+0x6/0x10
[12480.604490]  [<c056fc7f>] ? down_write+0x1f/0x30
[12480.604495]  [<c01cfc11>] sys_munmap+0x31/0x60
[12480.604499]  [<c010336c>] syscall_call+0x7/0xb
[12664.780415] __ratelimit: 6 callbacks suppressed
[12664.780422] deluged invoked oom-killer: gfp_mask=0x201da, order=0, oomkilladj=0
[12664.780431] deluged cpuset=/ mems_allowed=0
[12664.780438] Pid: 1271, comm: deluged Tainted: P           2.6.31-14-generic #48-Ubuntu
[12664.780444] Call Trace:
[12664.780461]  [<c01b5a0f>] oom_kill_process+0x9f/0x250
[12664.780470]  [<c01b601e>] ? select_bad_process+0xbe/0xf0
[12664.780477]  [<c01b60a1>] __out_of_memory+0x51/0xa0
[12664.780485]  [<c01b6143>] out_of_memory+0x53/0xb0
[12664.780493]  [<c01b83fe>] __alloc_pages_slowpath+0x42e/0x480
[12664.780501]  [<c01b855f>] __alloc_pages_nodemask+0x10f/0x120
[12664.780510]  [<c01bb012>] __do_page_cache_readahead+0xe2/0x190
[12664.780517]  [<c01bb0e1>] ra_submit+0x21/0x30
[12664.780524]  [<c01b2920>] do_sync_mmap_readahead+0x90/0xc0
[12664.780531]  [<c01b3c4d>] ? find_get_page+0x1d/0x90
[12664.780538]  [<c01b4af6>] filemap_fault+0x316/0x340
[12664.780546]  [<c01caa6b>] __do_fault+0x3b/0x470
[12664.780553]  [<c01cc264>] handle_mm_fault+0x134/0x380
[12664.780564]  [<c0572cf8>] do_page_fault+0x148/0x380
[12664.780571]  [<c0572bb0>] ? do_page_fault+0x0/0x380
[12664.780578]  [<c0570be3>] error_code+0x73/0x80
[12664.780583] Mem-Info:
[12664.780587] DMA per-cpu:
[12664.780591] CPU    0: hi:    0, btch:   1 usd:   0
[12664.780595] CPU    1: hi:    0, btch:   1 usd:   0
[12664.780599] Normal per-cpu:
[12664.780603] CPU    0: hi:  186, btch:  31 usd: 158
[12664.780608] CPU    1: hi:  186, btch:  31 usd: 185
[12664.780611] HighMem per-cpu:
[12664.780615] CPU    0: hi:   42, btch:   7 usd:  19
[12664.780619] CPU    1: hi:   42, btch:   7 usd:  38
[12664.780627] Active_anon:119443 active_file:355 inactive_anon:117257
[12664.780630]  inactive_file:445 unevictable:0 dirty:4 writeback:327 unstable:0
[12664.780632]  free:3088 slab:4937 mapped:1874 pagetables:2180 bounce:0
[12664.780640] DMA free:4060kB min:64kB low:80kB high:96kB active_anon:1476kB inactive_anon:1452kB active_file:0kB inactive_file:0kB unevictable:0kB present:15852kB pages_scanned:0 all_unreclaimable? no
[12664.780646] lowmem_reserve[]: 0 865 1000 1000
[12664.780660] Normal free:8076kB min:3728kB low:4660kB high:5592kB active_anon:413596kB inactive_anon:405264kB active_file:1088kB inactive_file:1396kB unevictable:0kB present:885944kB pages_scanned:32 all_unreclaimable? no
[12664.780666] lowmem_reserve[]: 0 0 1079 1079
[12664.780680] HighMem free:216kB min:132kB low:276kB high:420kB active_anon:62700kB inactive_anon:62312kB active_file:332kB inactive_file:476kB unevictable:0kB present:138120kB pages_scanned:64 all_unreclaimable? no
[12664.780686] lowmem_reserve[]: 0 0 0 0
[12664.780695] DMA: 7*4kB 12*8kB 38*16kB 16*32kB 0*64kB 0*128kB 1*256kB 1*512kB 0*1024kB 1*2048kB 0*4096kB = 4060kB
[12664.780719] Normal: 1841*4kB 1*8kB 0*16kB 2*32kB 2*64kB 2*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 8076kB
[12664.780742] HighMem: 28*4kB 5*8kB 2*16kB 1*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 216kB
[12664.780763] 24050 total pagecache pages
[12664.780767] 22823 pages in swap cache
[12664.780772] Swap cache stats: add 502138, delete 479315, find 24832/39112
[12664.780775] Free swap  = 0kB
[12664.780779] Total swap = 1502036kB
[12664.785361] 262128 pages RAM
[12664.785364] 34802 pages HighMem
[12664.785366] 5531 pages reserved
[12664.785369] 40129 pages shared
[12664.785371] 250401 pages non-shared
[12664.785376] Out of memory: kill process 26109 (vlc) score 501613 or a child
[12664.785438] Killed process 26109 (vlc)

```

I'm not an expert on this, but I noticed some mention of vlc, deluged, and boinc.

---

### Post by john_navarro on 2009-11-06
Yeah, there's definitely a memory leak with VLC. It might be with a shared library it uses - just don't know.

I started the following thread on the VLC forum:

[http://forum.videolan.org/viewtopic.php?f=13&t=67478]("http://forum.videolan.org/viewtopic.php?f=13&t=67478")

---

### Post by miki147 on 2009-11-07
Hi

Random freezes is my problem also, but I use 386.  I mention this because you may be interested in my history anyway:

This Summer I was given a Dell 2400 with celeron, integrated graphics and audio, 2 MB and I added a 16" monitor from 1998.  WinXP ran great, no problems.  I then added and dual booted (and since then just Linux on disc) but it froze under Linux from get-go.  I used Xubuntu to correct, no change.  Then Ubuntu, same, now I use Kubuntu, still randomly freezes.  Common problem is all 9.10 version with ext4.  Some with VLC, some without - Pulse audio, on, off, etc..  However Desktop audio or user modification attempts will kill it each time (FORGET compiz!).  One hint was that I was told by the computer that my integrated graphics driver was blacklisted last time I tried to activate desktop compiz and I did anyway and it froze (which is why I then went to Kubuntu).  I think it could be the common libs the apps use.  My disc does not run though.  (I also have to dance a jig every time it freezes because of the grub rewriting itself and that start up blank screen thingy is still a problem.)

Anyway I'm trying to disprove theories in an attemp to help get this resolved.  It is very frustrating!

PS I don't cross app (ie strictly xfce in xubuntu, gnome in ubuntu, and now just kde apps in kubuntu).  KCalendar will also freeze after an hour ob being on w/computer idle.

Good luck and may the Force be with you :popcorn:

Miki




edit 8 Nov:  Sorry to wimp out like this but I totally removed my netgear wireless card.  It's been a day and on and off usage and the computer is working like a charm.  No freezes, quick responses and nice sound.  Sorry if you aren't using a wireless card, but that was my problem on this Dell 2400 w/integrated graphic and sound.#-o

---

