---
title: "Suspend/Resume breaks PCMCIA aironet 350 card"
date: 2005-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by tardisx on 2005-10-16
Hi folks,

I am very impressed at how well Ubuntu breezy supports my G3 Powerbook (I had no end of trouble when I experimented with Gentoo).

I have only one issue (well one that I can't solve myself :-).

While suspend/resume does work, it breaks my PCMCIA wireless card (A cisco aironet 350), after resume it no longer works. Here's what I get in dmesg after a resume from sleep:

```

[  515.306274] airo: Doing fast bap_reads
[  515.325246] airo: MAC enabled eth2 0:7:85:92:8f:ed
[  515.847504] irq 22: nobody cared (try booting with the "irqpoll" option.
[  515.850761] Call trace:
[  515.854074]  [c003f6d0] __report_bad_irq+0x34/0xac
[  515.857591]  [c003f844] note_interrupt+0xe0/0x270
[  515.861178]  [c003f1b4] __do_IRQ+0x154/0x164
[  515.864834]  [c0006250] do_IRQ+0x38/0x98
[  515.868466]  [c0004f88] ret_from_except+0x0/0x1c
[  515.872152]  [c0188334] netpoll_trap+0x4/0xc
[  515.875893]  [cda33388] airo_event+0x8c/0x758 [airo_cs]
[  515.879784]  [cdaaecc8] send_event_callback+0x6c/0x74 [pcmcia]
[  515.883806]  [c0134eb8] __bus_for_each_dev+0x58/0xb0
[  515.887795]  [c0134f64] bus_for_each_dev+0x54/0xbc
[  515.891859]  [cdaaed28] send_event+0x58/0x7c [pcmcia]
[  515.896059]  [cdaaf2c0] ds_event+0x58/0x140 [pcmcia]
[  515.900339]  [cda866fc] send_event+0x70/0xcc [pcmcia_core]
[  515.904800]  [cda870c4] socket_resume+0x164/0x174 [pcmcia_core]
[  515.909350]  [cda87184] pcmcia_socket_dev_resume+0xb0/0x160 [pcmcia_core]
[  515.914070] handlers:
[  515.918668] [<cdad5900>] (airo_interrupt+0x0/0x1114 [airo])
[  515.923564] [<cda2b8cc>] (yenta_interrupt+0x0/0x10c [yenta_socket])
[  515.928552] Disabling IRQ #22

```

Naturally, I have tried adding the irqpoll option to the kernel boot options in yaboot.conf, but it made no difference.

The system is a Powerbook G3.

Any ideas?

---

### Post by ssam on 2005-10-16
if stop the network interface before suspending, then can you bring it back up after resuming?

there are scripts in /etc/apm that can suspend and resume services.

---

### Post by tardisx on 2005-10-16
[QUOTE=ssam]if stop the network interface before suspending, then can you bring it back up after resuming?

there are scripts in /etc/apm that can suspend and resume services.[/QUOTE]

I don't think so, but I will try again and give a more concrete answer tonight.

I might also be able to swap the aironet card for something else, which might be less effort :-)

---

### Post by tardisx on 2005-10-17
[QUOTE=tardisx]I don't think so, but I will try again and give a more concrete answer tonight.
[/QUOTE]

No go, still breaks if I stop networking first. I suspect possibly if I could remove and reload the module drivers for the airo/airo_cs and/or pcmcia it would again, but the airo drivers are always 'in use' so I can't unload them.

[QUOTE=tardisx]I might also be able to swap the aironet card for something else, which might be less effort :-)[/QUOTE]

I have borrowed a linksys card, I'll see how it goes tonight.

---

