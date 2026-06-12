---
title: "Ubuntu 8.10, x64, nforce 630, troubleshooting"
date: 2008-12-22
forum: x86 64-bit Users
---

### Post by mind5 on 2008-12-22
Hardware: AMD64, 2GB, Abit AN-M2HD (nforce 630a). I have installed Ubuntu 8.10 (x64). Currently running nvidia graphics driver 177. I installed all patches/updates via the icon at the top of desktop.

Sounds are working. First I only had max res of 800x600, but now it appears I have no problem with graphics, nvidia control panel works, resolutions work, etc.

Problem: during boot time, it takes several minutes. Below is copy/paste from syslog. I understand something is wrong, but I don't know what.

Dec 22 13:58:21 kone syslogd 1.5.0#2ubuntu6: restart.
Dec 22 13:58:21 kone kernel: Inspecting /boot/System.map-2.6.27-9-generic
Dec 22 13:58:21 kone kernel: Cannot find map file.
Dec 22 13:58:22 kone kernel: Loaded 67322 symbols from 77 modules.
Dec 22 13:58:22 kone kernel: 3] irq 10: nobody cared (try booting with the "irqpoll" option)
Dec 22 13:58:22 kone kernel: [    9.572717] Pid: 1383, comm: modprobe Not tainted 2.6.27-9-generic #1
Dec 22 13:58:22 kone kernel: [    9.572719] 
Dec 22 13:58:22 kone kernel: [    9.572719] Call Trace:
Dec 22 13:58:22 kone kernel: [    9.572721]  <IRQ>  [<ffffffff8029e91b>] __report_bad_irq+0x2b/0x90
Dec 22 13:58:22 kone kernel: [    9.572732]  [<ffffffff8029eab7>] note_interrupt+0x137/0x170
Dec 22 13:58:22 kone kernel: [    9.572735]  [<ffffffff8029f24d>] handle_fasteoi_irq+0xed/0x110
Dec 22 13:58:22 kone kernel: [    9.572738]  [<ffffffff8021417c>] ? call_softirq+0x1c/0x30
Dec 22 13:58:22 kone kernel: [    9.572741]  [<ffffffff80215b16>] do_IRQ+0x86/0x100
Dec 22 13:58:22 kone kernel: [    9.572744]  [<ffffffff80212f0e>] ret_from_intr+0x0/0x29
Dec 22 13:58:22 kone kernel: [    9.572745]  <EOI>  [<ffffffff8021a521>] ? native_read_tsc+0x11/0x30
Dec 22 13:58:22 kone kernel: [    9.572753]  [<ffffffff803aafbc>] ? delay_tsc+0x4c/0x90
Dec 22 13:58:22 kone kernel: [    9.572758]  [<ffffffff803ab093>] ? __const_udelay+0x53/0x60
Dec 22 13:58:22 kone kernel: [    9.572764]  [<ffffffffa0119298>] ? ohci1394_stop_context+0x58/0xe0 [ohci1394]
Dec 22 13:58:22 kone kernel: [    9.572769]  [<ffffffffa01194b2>] ? initialize_dma_trm_ctx+0x22/0x80 [ohci1394]
Dec 22 13:58:22 kone kernel: [    9.572773]  [<ffffffffa01198c4>] ? ohci_initialize+0x184/0x360 [ohci1394]
Dec 22 13:58:22 kone kernel: [    9.572778]  [<ffffffffa011ddf1>] ? ohci1394_pci_probe+0x451/0x66f [ohci1394]
Dec 22 13:58:22 kone kernel: [    9.572783]  [<ffffffff803bc100>] ? pci_device_probe+0xe0/0x140
Dec 22 13:58:22 kone kernel: [    9.572788]  [<ffffffff8034b623>] ? sysfs_create_link+0x13/0x20
Dec 22 13:58:22 kone kernel: [    9.572792]  [<ffffffff80430542>] ? really_probe+0x72/0x1a0
Dec 22 13:58:22 kone kernel: [    9.572796]  [<ffffffff804306c0>] ? driver_probe_device+0x50/0x60
Dec 22 13:58:22 kone kernel: [    9.572799]  [<ffffffff8043075b>] ? __driver_attach+0x8b/0x90
Dec 22 13:58:22 kone kernel: [    9.572802]  [<ffffffff804306d0>] ? __driver_attach+0x0/0x90
Dec 22 13:58:22 kone kernel: [    9.572805]  [<ffffffff8042fccb>] ? bus_for_each_dev+0x6b/0xa0
Dec 22 13:58:22 kone kernel: [    9.572809]  [<ffffffff802e1ecb>] ? kmem_cache_alloc+0x8b/0xd0
Dec 22 13:58:22 kone kernel: [    9.572813]  [<ffffffffa0125000>] ? ohci1394_init+0x0/0x25 [ohci1394]
Dec 22 13:58:22 kone kernel: [    9.572816]  [<ffffffff804303a1>] ? driver_attach+0x21/0x30
Dec 22 13:58:22 kone kernel: [    9.572819]  [<ffffffff8042f538>] ? bus_add_driver+0x1f8/0x270
Dec 22 13:58:22 kone kernel: [    9.572823]  [<ffffffffa0125000>] ? ohci1394_init+0x0/0x25 [ohci1394]
Dec 22 13:58:22 kone kernel: [    9.572826]  [<ffffffff80430955>] ? driver_register+0x75/0x170
Dec 22 13:58:22 kone kernel: [    9.572830]  [<ffffffffa0125000>] ? ohci1394_init+0x0/0x25 [ohci1394]
Dec 22 13:58:22 kone kernel: [    9.572833]  [<ffffffff803bc402>] ? __pci_register_driver+0x72/0xc0
Dec 22 13:58:22 kone kernel: [    9.572837]  [<ffffffffa0125000>] ? ohci1394_init+0x0/0x25 [ohci1394]
Dec 22 13:58:22 kone kernel: [    9.572841]  [<ffffffffa0125023>] ? ohci1394_init+0x23/0x25 [ohci1394]
Dec 22 13:58:22 kone kernel: [    9.572844]  [<ffffffff8020a041>] ? do_one_initcall+0x41/0x170
Dec 22 13:58:22 kone kernel: [    9.572848]  [<ffffffff8026c261>] ? __blocking_notifier_call_chain+0x21/0x90
Dec 22 13:58:22 kone kernel: [    9.572852]  [<ffffffff8027d085>] ? sys_init_module+0xb5/0x1f0
Dec 22 13:58:22 kone kernel: [    9.572856]  [<ffffffff8021285a>] ? system_call_fastpath+0x16/0x1b
Dec 22 13:58:22 kone kernel: [    9.572858] 
Dec 22 13:58:22 kone kernel: [    9.572859] handlers:
Dec 22 13:58:22 kone kernel: [    9.572861] [<ffffffffa011cbf0>] (ohci_irq_handler+0x0/0x850 [ohci1394])
Dec 22 13:58:22 kone kernel: [    9.572866] Disabling IRQ #10
Dec 22 13:58:22 kone kernel: [    9.573733] ohci1394: fw-host1: Runaway loop while stopping context: ...
Dec 22 13:58:22 kone kernel: [    9.573738] ohci1394: fw-host1: OHCI-1394 165.165 (PCI): IRQ=[10]  MMIO=[fd080000-fd0807ff]  Max Packet=[65536]  IR/IT contexts=[32/32]
Dec 22 13:58:22 kone kernel: [    9.576004] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [    9.677024] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [    9.776308] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [    9.875589] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [    9.974876] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   10.074160] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   10.173445] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   10.272730] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   10.372013] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   10.471293] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   10.570577] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   10.669860] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   10.769144] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   10.868426] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   10.967708] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   11.066990] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   11.166274] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   11.265556] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   11.364839] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   11.464121] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   11.563100] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   11.662383] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   11.761668] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   11.860950] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   11.960233] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   12.059514] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   12.158799] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   12.258080] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   12.357364] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   12.456645] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   12.551932] ohci1394: fw-host1: Serial EEPROM has suspicious values, attempting to set max_packet_size to 512 bytes
Dec 22 13:58:22 kone kernel: [   12.555929] ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   12.653850] ohci1394 0000:01:02.0: can't derive routing for PCI INT A
Dec 22 13:58:22 kone kernel: [   12.653854] ohci1394 0000:01:02.0: PCI INT A: no GSI - using IRQ 10
Dec 22 13:58:22 kone kernel: [   12.804004] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   12.966315] ohci1394: fw-host2: Runaway loop while stopping context: ...
Dec 22 13:58:22 kone kernel: [   13.030601] ohci1394: fw-host2: Runaway loop while stopping context: ...
Dec 22 13:58:22 kone kernel: [   13.094736] ohci1394: fw-host2: Runaway loop while stopping context: ...
Dec 22 13:58:22 kone kernel: [   13.158837] ohci1394: fw-host2: Runaway loop while stopping context: ...
Dec 22 13:58:22 kone kernel: [   13.158847] ohci1394: fw-host2: OHCI-1394 165.165 (PCI): IRQ=[10]  MMIO=[fd081000-fd0817ff]  Max Packet=[65536]  IR/IT contexts=[32/32]
Dec 22 13:58:22 kone kernel: [   13.160004] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   13.262140] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   13.361429] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   13.460713] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   13.559678] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   13.658970] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   13.758258] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   13.857542] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   13.956829] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   14.056114] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   14.155404] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   14.254689] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   14.353977] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   14.453262] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   14.552550] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   14.651837] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   14.751126] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   14.850410] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   14.949697] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   15.048981] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   15.148273] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   15.247556] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   15.346849] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   15.446133] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   15.545422] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   15.644611] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   15.743899] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   15.843182] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   15.942470] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   16.041754] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   16.137050] ohci1394: fw-host2: Serial EEPROM has suspicious values, attempting to set max_packet_size to 512 bytes
Dec 22 13:58:22 kone kernel: [   16.141046] ohci1394: fw-host1: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   16.246152] ohci1394 0000:01:03.0: can't derive routing for PCI INT A
Dec 22 13:58:22 kone kernel: [   16.246158] ohci1394 0000:01:03.0: PCI INT A: no GSI - using IRQ 10
Dec 22 13:58:22 kone kernel: [   16.282961] irq 10: nobody cared (try booting with the "irqpoll" option)
Dec 22 13:58:22 kone kernel: [   16.282966] Pid: 1383, comm: modprobe Not tainted 2.6.27-9-generic #1
Dec 22 13:58:22 kone kernel: [   16.282968] 
Dec 22 13:58:22 kone kernel: [   16.282968] Call Trace:
Dec 22 13:58:22 kone kernel: [   16.282970]  <IRQ>  [<ffffffff8029e91b>] __report_bad_irq+0x2b/0x90
Dec 22 13:58:22 kone kernel: [   16.282980]  [<ffffffff8029eab7>] note_interrupt+0x137/0x170
Dec 22 13:58:22 kone kernel: [   16.282983]  [<ffffffff8029f24d>] handle_fasteoi_irq+0xed/0x110
Dec 22 13:58:22 kone kernel: [   16.282987]  [<ffffffff8021417c>] ? call_softirq+0x1c/0x30
Dec 22 13:58:22 kone kernel: [   16.282990]  [<ffffffff80215b16>] do_IRQ+0x86/0x100
Dec 22 13:58:22 kone kernel: [   16.282992]  [<ffffffff80212f0e>] ret_from_intr+0x0/0x29
Dec 22 13:58:22 kone kernel: [   16.282994]  <EOI>  [<ffffffff8021a51a>] ? native_read_tsc+0xa/0x30
Dec 22 13:58:22 kone kernel: [   16.283001]  [<ffffffff803aafbc>] ? delay_tsc+0x4c/0x90
Dec 22 13:58:22 kone kernel: [   16.283006]  [<ffffffff803ab093>] ? __const_udelay+0x53/0x60
Dec 22 13:58:22 kone kernel: [   16.283012]  [<ffffffffa0119195>] ? ohci_soft_reset+0x35/0x60 [ohci1394]
Dec 22 13:58:22 kone kernel: [   16.283017]  [<ffffffffa011dc7d>] ? ohci1394_pci_probe+0x2dd/0x66f [ohci1394]
Dec 22 13:58:22 kone kernel: [   16.283022]  [<ffffffff803bc100>] ? pci_device_probe+0xe0/0x140
Dec 22 13:58:22 kone kernel: [   16.283026]  [<ffffffff8034b623>] ? sysfs_create_link+0x13/0x20
Dec 22 13:58:22 kone kernel: [   16.283031]  [<ffffffff80430542>] ? really_probe+0x72/0x1a0
Dec 22 13:58:22 kone kernel: [   16.283034]  [<ffffffff804306c0>] ? driver_probe_device+0x50/0x60
Dec 22 13:58:22 kone kernel: [   16.283038]  [<ffffffff8043075b>] ? __driver_attach+0x8b/0x90
Dec 22 13:58:22 kone kernel: [   16.283041]  [<ffffffff804306d0>] ? __driver_attach+0x0/0x90
Dec 22 13:58:22 kone kernel: [   16.283044]  [<ffffffff8042fccb>] ? bus_for_each_dev+0x6b/0xa0
Dec 22 13:58:22 kone kernel: [   16.283048]  [<ffffffff802e1ecb>] ? kmem_cache_alloc+0x8b/0xd0
Dec 22 13:58:22 kone kernel: [   16.283052]  [<ffffffffa0125000>] ? ohci1394_init+0x0/0x25 [ohci1394]
Dec 22 13:58:22 kone kernel: [   16.283055]  [<ffffffff804303a1>] ? driver_attach+0x21/0x30
Dec 22 13:58:22 kone kernel: [   16.283058]  [<ffffffff8042f538>] ? bus_add_driver+0x1f8/0x270
Dec 22 13:58:22 kone kernel: [   16.283062]  [<ffffffffa0125000>] ? ohci1394_init+0x0/0x25 [ohci1394]
Dec 22 13:58:22 kone kernel: [   16.283065]  [<ffffffff80430955>] ? driver_register+0x75/0x170
Dec 22 13:58:22 kone kernel: [   16.283069]  [<ffffffffa0125000>] ? ohci1394_init+0x0/0x25 [ohci1394]
Dec 22 13:58:22 kone kernel: [   16.283073]  [<ffffffff803bc402>] ? __pci_register_driver+0x72/0xc0
Dec 22 13:58:22 kone kernel: [   16.283076]  [<ffffffffa0125000>] ? ohci1394_init+0x0/0x25 [ohci1394]
Dec 22 13:58:22 kone kernel: [   16.283080]  [<ffffffffa0125023>] ? ohci1394_init+0x23/0x25 [ohci1394]
Dec 22 13:58:22 kone kernel: [   16.283083]  [<ffffffff8020a041>] ? do_one_initcall+0x41/0x170
Dec 22 13:58:22 kone kernel: [   16.283088]  [<ffffffff8026c261>] ? __blocking_notifier_call_chain+0x21/0x90
Dec 22 13:58:22 kone kernel: [   16.283092]  [<ffffffff8027d085>] ? sys_init_module+0xb5/0x1f0
Dec 22 13:58:22 kone kernel: [   16.283097]  [<ffffffff8021285a>] ? system_call_fastpath+0x16/0x1b
Dec 22 13:58:22 kone kernel: [   16.283098] 
Dec 22 13:58:22 kone kernel: [   16.283099] handlers:
Dec 22 13:58:22 kone kernel: [   16.283101] [<ffffffffa011cbf0>] (ohci_irq_handler+0x0/0x850 [ohci1394])
Dec 22 13:58:22 kone kernel: [   16.283106] [<ffffffffa011cbf0>] (ohci_irq_handler+0x0/0x850 [ohci1394])
Dec 22 13:58:22 kone kernel: [   16.283111] Disabling IRQ #10
Dec 22 13:58:22 kone kernel: [   16.396004] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   16.561984] ohci1394: fw-host3: Runaway loop while stopping context: ...
Dec 22 13:58:22 kone kernel: [   16.629121] ohci1394: fw-host3: Runaway loop while stopping context: ...
Dec 22 13:58:22 kone kernel: [   16.696293] ohci1394: fw-host3: Runaway loop while stopping context: ...
Dec 22 13:58:22 kone kernel: [   16.763413] ohci1394: fw-host3: Runaway loop while stopping context: ...
Dec 22 13:58:22 kone kernel: [   16.763425] ohci1394: fw-host3: OHCI-1394 165.165 (PCI): IRQ=[10]  MMIO=[fd082000-fd0827ff]  Max Packet=[65536]  IR/IT contexts=[32/32]
Dec 22 13:58:22 kone kernel: [   16.764005] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   16.866720] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   16.966018] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   17.065304] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   17.164599] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   17.263888] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   17.363179] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   17.462468] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   17.561757] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   17.661044] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   17.760339] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   17.859625] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   17.958914] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   18.058199] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   18.157495] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   18.256780] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   18.356071] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   18.455356] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   18.554650] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   18.653939] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   18.753229] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   18.852514] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   18.951804] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   19.051090] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   19.150386] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   19.249671] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   19.348961] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   19.448245] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   19.547536] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   19.646703] ohci1394: fw-host3: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   19.741998] ohci1394: fw-host3: Serial EEPROM has suspicious values, attempting to set max_packet_size to 512 bytes
Dec 22 13:58:22 kone kernel: [   19.745992] ohci1394: fw-host2: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   19.853001] ohci1394 0000:01:04.0: PCI INT A -> Link[APCM] -> GSI 21 (level, low) -> IRQ 21
Dec 22 13:58:22 kone kernel: [   20.004004] ohci1394: fw-host4: Set PHY Reg timeout [0xffffffff/0x00004000/100]
Dec 22 13:58:22 kone kernel: [   20.117076] irq 10: nobody cared (try booting with the "irqpoll" option)
Dec 22 13:58:22 kone kernel: [   20.117079] Pid: 1383, comm: modprobe Not tainted 2.6.27-9-generic #1
Dec 22 13:58:22 kone kernel: [   20.117081] 
Dec 22 13:58:22 kone kernel: [   20.117082] Call Trace:
Dec 22 13:58:22 kone kernel: [   20.117084]  <IRQ>  [<ffffffff8029e91b>] __report_bad_irq+0x2b/0x90
Dec 22 13:58:22 kone kernel: [   20.117093]  [<ffffffff8029eab7>] note_interrupt+0x137/0x170
Dec 22 13:58:22 kone kernel: [   20.117096]  [<ffffffff8029f24d>] handle_fasteoi_irq+0xed/0x110
Dec 22 13:58:22 kone kernel: [   20.117100]  [<ffffffff8021417c>] ? call_softirq+0x1c/0x30
Dec 22 13:58:22 kone kernel: [   20.117103]  [<ffffffff80215b16>] do_IRQ+0x86/0x100

(continues for several kbs...)

---

### Post by tigerstripedcat on 2008-12-22
My first guess is that it's an irq conflict or you might need to pass some arguments to the kernel (which is odd, as ubuntu is getting better at dealing with badly designed hardware).  Do yourself a favor and go into the BIOS and find "reset configuration data" and reset it, and also disable all parallel, serial, or any other ports you don't use, they just use up resources that could be causing this problem.

Make sure it doesn't happen with the stock "nv" driver.  Check the forums and nvnews.com and make sure no one else is getting this problem.  Try and older driver and see if you get the same problem.  What does your xorg.conf look like?  Install bootchart and see if you can narrow down the process that is causing this:
[http://ubuntuforums.org/showthread.php?t=241604](http://ubuntuforums.org/showthread.php?t=241604)

It seems to be kernel-level, though. Have you tried installing a new kernel?  You can try an vanilla kernel with easy by using kernelcheck.

Hope something here helps.
TSC

---

