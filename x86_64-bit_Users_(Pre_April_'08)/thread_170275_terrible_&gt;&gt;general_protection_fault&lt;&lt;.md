---
title: "terrible &gt;&gt;general protection fault&lt;&lt;"
date: 2006-05-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by nortoncillo on 2006-05-04
my kern.log sais this before my machine yell's "kernel panic"

May  3 14:06:50 ns kernel: [ 7017.452901] general protection fault: 0000 [1] SMP
May  3 14:06:50 ns kernel: [ 7017.452936] CPU 0
May  3 14:06:50 ns kernel: [ 7017.452960] Modules linked in: iptable_filter iptable_mangle iptable_nat ip_conntrack ip_tables capability commoncap quota_v2 evdev psmouse mousedev ide_generic unix
May  3 14:06:50 ns kernel: [ 7017.453068] Pid: 7248, comm: java Not tainted 2.6.12-horacio
May  3 14:06:50 ns kernel: [ 7017.453097] RIP: 0010:[inet_stream_connect+296/768] <ffffffff8040e968>{inet_stream_connect+296}
May  3 14:06:50 ns kernel: [ 7017.453132] RSP: 0018:ffff8100235b7e18  EFLAGS: 00010246
May  3 14:06:50 ns kernel: [ 7017.453178] RAX: 7fffffffffffffff RBX: ffff81002a9e4280 RCX: 0000000000000002
May  3 14:06:50 ns kernel: [ 7017.453212] RDX: ffff810001e0d900 RSI: 0000000000000296 RDI: ffff81002a9e4658
May  3 14:06:50 ns kernel: [ 7017.453244] RBP: ffff8100235b7ed8 R08: 0000000000000bb8 R09: 0000000000000000
May  3 14:06:50 ns kernel: [ 7017.453276] R10: 0000000000000000 R11: 00000000000000df R12: 00000000ffffff8d
May  3 14:06:50 ns kernel: [ 7017.453308] R13: ffff81001031d880 R14: 000000000000000c R15: 0000000000000002
May  3 14:06:50 ns kernel: [ 7017.453341] FS:  00000000432ed960(0063) GS:ffffffff805ee640(0000) knlGS:0000000000000000
May  3 14:06:50 ns kernel: [ 7017.453389] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
May  3 14:06:50 ns kernel: [ 7017.453419] CR2: 00002aaaefe65000 CR3: 000000000465c000 CR4: 00000000000006e0
May  3 14:06:50 ns kernel: [ 7017.453453] Process java (pid: 7248, threadinfo ffff8100235b6000, task ffff810016e562f0)
May  3 14:06:50 ns kernel: [ 7017.453500] Stack: ffff810016e56500 7fffffffffffffff ffff8100235b7cc8 ffff8100235b7e74
May  3 14:06:50 ns kernel: [ 7017.453540]        0000000000000040 ffffffff803c6832 ffff8100235b7e78 ffffffff803c9ea9
May  3 14:06:50 ns kernel: [ 7017.453597]        ffff81002be599c0 ffff81002b5b2680
May  3 14:06:50 ns kernel: [ 7017.453629] Call Trace:<ffffffff803c6832>{move_addr_to_user+66} <ffffffff803c9ea9>{release_sock+25}
May  3 14:06:50 ns kernel: [ 7017.453690]        <ffffffff801765db>{fget+91} <ffffffff803c826c>{sys_connect+140}
May  3 14:06:50 ns kernel: [ 7017.453751]        <ffffffff801764fd>{__fput+333} <ffffffff80174bfe>{filp_close+126}
May  3 14:06:50 ns kernel: [ 7017.453809]        <ffffffff8010e465>{error_exit+0} <ffffffff8010da66>{system_call+126}
May  3 14:06:50 ns kernel: [ 7017.453868]
May  3 14:06:50 ns kernel: [ 7017.453908]
May  3 14:06:50 ns kernel: [ 7017.453909] Code: 44 89 f0 d3 f8 a8 01 0f 84 30 01 00 00 48 83 7c 24 08 00 0f
May  3 14:06:50 ns kernel: [ 7017.454023] RIP <ffffffff8040e968>{inet_stream_connect+296} RSP <ffff8100235b7e18>

beleave me any idea will be thanked

---

### Post by nortoncillo on 2006-05-05
UPDATE!!..

today in the morning it has the nice and beauty message
>>>Kernel panic<<<

---

### Post by henriquemaia on 2006-05-05
Did you install any specif kernel? Have you updated your kernel recently? Did that just happened without any particular reason?

---

