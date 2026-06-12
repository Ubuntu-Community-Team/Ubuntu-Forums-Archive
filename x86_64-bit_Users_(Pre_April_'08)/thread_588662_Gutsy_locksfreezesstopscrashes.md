---
title: "Gutsy locks/freezes/stops/crashes"
date: 2007-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by sewpafly on 2007-10-23
After doing a clean install of Gutsy to my laptop I experienced a series of lockups that I couldn't find any reason for.  It always seemed to be when firefox was opened.  However after using it for awhile (hard rebooting every 10 minutes) I know can crash it on demand.  After the system boots up I log in through the command line and try to run `sudo aptitude update`.  BAM!!!  Nothing will fix it except a hard reboot.

It does output this:
```

 BUG: scheduling while atomic: http/0x10000100/5563

```

In kern.log you can see this:
```

 BUG: scheduling while atomic: http/0x10000100/5563
 
 Call Trace:
  [thread_return+542/1737] thread_return+0x21e/0x6c9
  [add_partial+25/96] add_partial+0x19/0x60
  [__slab_free+346/800] __slab_free+0x15a/0x320
  [__cond_resched+28/80] __cond_resched+0x1c/0x50
  [cond_resched+50/64] cond_resched+0x32/0x40
  [mutex_lock+9/32] mutex_lock+0x9/0x20
  [sysfs_hash_and_remove+108/352] sysfs_hash_and_remove+0x6c/0x160
  [sysfs_slab_alias+113/160] sysfs_slab_alias+0x71/0xa0
  [sysfs_slab_add+300/416] sysfs_slab_add+0x12c/0x1a0
  [create_kmalloc_cache+158/224] create_kmalloc_cache+0x9e/0xe0
  [get_slab+479/528] get_slab+0x1df/0x210
  [_end+129484333/2130332920] :bcm43xx:bcm43xx_dma_tx+0x2f5/0x4e0
  [__kmalloc_node_track_caller+37/176] __kmalloc_node_track_caller+0x25/0xb0
  [__alloc_skb+125/368] __alloc_skb+0x7d/0x170
  [_end+129484333/2130332920] :bcm43xx:bcm43xx_dma_tx+0x2f5/0x4e0
  [_end+129415923/2130332920] :bcm43xx:bcm43xx_ieee80211_hard_start_xmit+0xab/0xb0
  [_end+129314159/2130332920] :ieee80211:ieee80211_xmit+0xa07/0xe10
  [_end+130895096/2130332920] :snd_via82xx:snd_via8233_interrupt+0x40/0x110
  [__qdisc_run+113/544] __qdisc_run+0x71/0x220
  [dev_queue_xmit+510/768] dev_queue_xmit+0x1fe/0x300
  [ip_output+465/928] ip_output+0x1d1/0x3a0
  [ip_queue_xmit+533/1104] ip_queue_xmit+0x215/0x450
  [default_wake_function+0/16] default_wake_function+0x0/0x10
  [default_wake_function+0/16] default_wake_function+0x0/0x10
  [tcp_transmit_skb+1133/2144] tcp_transmit_skb+0x46d/0x860
  [tcp_push_one+178/256] tcp_push_one+0xb2/0x100
  [tcp_sendmsg+685/3040] tcp_sendmsg+0x2ad/0xbe0
  [sock_aio_write+370/400] sock_aio_write+0x172/0x190
  [__wake_up+67/112] __wake_up+0x43/0x70
  [do_sync_write+217/288] do_sync_write+0xd9/0x120
  [autoremove_wake_function+0/48] autoremove_wake_function+0x0/0x30
  [vfs_write+383/400] vfs_write+0x17f/0x190
  [sys_write+83/144] sys_write+0x53/0x90
  [system_call+126/131] system_call+0x7e/0x83
 
```

Does anyone know how to further troubleshoot/fix?

---

### Post by kleeman on 2007-10-23
Sounds like a kernel bug. Which kernel are you using? (issue uname -a)

---

### Post by sewpafly on 2007-10-23
I'm using the kernel that ships with the amd64 gutsy gibbon release.  I believe that it's Ubuntu 2.6.22-14.46-generic.

---

### Post by nanbudh on 2007-10-23
I have similar problem. I don't like to see ubuntu perform this bad. i have been using 6.06 until now and it performed so well and was so stable that its a shame gutsy is behaving like this.
My box is also freezing at the slightest instance. Usually when Firefox is running but also with OO writer and at times with synaptic. Seems like the problem is increasing because when i installed gutsy i was able to surf the NET okay with it for a day. It started acting up a day later. Yesterday criss cross lines appeared on the whole desktop on booting up. it remained like that even after a couple of reboots. I am forced to use XP now.
I have not had the time to find out a way to make it freeze on demand yet.somebody please help
BTW i used ubuntu desktop amd live cd for install

---

### Post by sewpafly on 2007-10-24
I believe that I fixed my problem...  I was using the bcm43xx module for my wireless card.  (With firmware created with the bcm43xx-fwcutter), and I'm pretty sure that this was the problem.  I switched to ndiswrapper and have been surfing fine tonight and 'aptitude update' is working again.  Weird that it was working and then went funny.

---

### Post by kleeman on 2007-10-24
Bugs in kernel modules are hard to track down and there are sometimes regressions. Makes sense your problem was network related given your crash was with the browser. I have had a string of issues like these over the past 3 years but have picked them up first in the development version and lodged bugreports on launchpad. The devs are sensitive about regressions so fix things pretty fast.....

---

### Post by woZa on 2007-12-08
I have a similar issue with 7.10 that I believe is down to the rt61 module (from the ralink website - the serialmonkey one doesn't work for me...). Only locks up the internet connection and only when I have a constant connection for a while (ie streaming audio, running torrents etc...)

```
Call Trace:
Dec  8 12:27:18 mythbox kernel: [   48.027304]  [__kmalloc_node_track_caller+37/176] __kmalloc_node_track_caller+0x25/0xb0
Dec  8 12:27:18 mythbox kernel: [   48.027396]  [extract_buf+277/304] extract_buf+0x115/0x130
Dec  8 12:27:18 mythbox kernel: [   48.027443]  [_end+129354926/2130332920] :rt61:MlmeHardTransmit+0x2a6/0x380
```

---

