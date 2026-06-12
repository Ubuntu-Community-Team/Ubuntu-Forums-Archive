---
title: "Hard crash"
date: 2009-05-26
forum: x86 64-bit Users
---

### Post by PerJ on 2009-05-26
Hi, 

I've recently done a clean install of Ubuntu 9.04 Desktop (64bit), on my laptop (a HP 2530p), but unfortunately I'm experiencing some instability.
From time to time (maybe a couple of times a day), the system freezes completely. The only way to recover seems to hold the powerbutton pressed until it reboots.
I have enabled the CTRL-ALT-BACKSPACE key-combo (with dontzap), but has no effect when the crash occurs.

The relevant log entrie seem to be:
```
May 26 10:37:53 pontifex kernel: [ 8476.803713] ------------[ cut here ]------------
May 26 10:37:53 pontifex kernel: [ 8476.803717] WARNING: at /build/buildd/linux-2.6.28/lib/kref.c:43 kref_get+0x2d/0x30()
May 26 10:37:53 pontifex kernel: [ 8476.803719] Modules linked in: hidp nfs lockd nfs_acl sunrpc cbc aes_x86_64 aes_generic binfmt_misc ppdev i915 drm bridge stp bnep input_polldev lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy arc4 snd_seq_oss ecb snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer iwlagn iwlcore leds_hp_disk snd_seq_device uvcvideo mac80211 snd led_class compat_ioctl32 videodev sdhci_pci iTCO_wdt soundcore joydev video tpm_infineon tpm psmouse pcspkr serio_raw v4l1_compat ricoh_mmc sdhci iTCO_vendor_support cfg80211 snd_page_alloc output tpm_bios intel_agp lis3lv02d btusb ohci1394 ieee1394 e1000e vesafb fbcon tileblit font bitblit softcursor
May 26 10:37:53 pontifex kernel: [ 8476.803771] Pid: 2873, comm: Xorg Not tainted 2.6.28-11-generic #42-Ubuntu
May 26 10:37:53 pontifex kernel: [ 8476.803773] Call Trace:
May 26 10:37:53 pontifex kernel: [ 8476.803778]  [<ffffffff802509bf>] warn_on_slowpath+0x5f/0x90
May 26 10:37:53 pontifex kernel: [ 8476.803782]  [<ffffffff8025c676>] ? lock_timer_base+0x36/0x70
May 26 10:37:53 pontifex kernel: [ 8476.803790]  [<ffffffffa03908ac>] ? i915_gem_object_pin_and_relocate+0x3c/0x2e0 [i915]
May 26 10:37:53 pontifex kernel: [ 8476.803794]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10
May 26 10:37:53 pontifex kernel: [ 8476.803799]  [<ffffffffa038b8d6>] ? i915_user_irq_put+0x46/0xb0 [i915]
May 26 10:37:53 pontifex kernel: [ 8476.803802]  [<ffffffff80419a8d>] kref_get+0x2d/0x30
May 26 10:37:53 pontifex kernel: [ 8476.803814]  [<ffffffffa036dfa2>] drm_gem_object_lookup+0x42/0x60 [drm]
May 26 10:37:53 pontifex kernel: [ 8476.803820]  [<ffffffffa038ea6f>] i915_gem_busy_ioctl+0x3f/0xd0 [i915]
May 26 10:37:53 pontifex kernel: [ 8476.803829]  [<ffffffffa036c7fa>] drm_ioctl+0x10a/0x330 [drm]
May 26 10:37:53 pontifex kernel: [ 8476.803835]  [<ffffffffa038ea30>] ? i915_gem_busy_ioctl+0x0/0xd0 [i915]
May 26 10:37:53 pontifex kernel: [ 8476.803839]  [<ffffffff802f631d>] vfs_ioctl+0x7d/0xa0
May 26 10:37:53 pontifex kernel: [ 8476.803842]  [<ffffffff802f6685>] do_vfs_ioctl+0x75/0x230
May 26 10:37:53 pontifex kernel: [ 8476.803845]  [<ffffffff802f68d9>] sys_ioctl+0x99/0xa0
May 26 10:37:53 pontifex kernel: [ 8476.803848]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
May 26 10:37:53 pontifex kernel: [ 8476.803850] ---[ end trace 3a69ab225c643128 ]---
May 26 10:37:53 pontifex kernel: [ 8476.803859] BUG: unable to handle kernel NULL pointer dereference at 0000000000000020
May 26 10:37:53 pontifex kernel: [ 8476.803863] IP: [<ffffffffa038ea7d>] i915_gem_busy_ioctl+0x4d/0xd0 [i915]
May 26 10:37:53 pontifex kernel: [ 8476.803869] PGD 13904f067 PUD 13a03e067 PMD 0 
May 26 10:37:53 pontifex kernel: [ 8476.803872] Oops: 0000 [#1] SMP 
May 26 10:37:53 pontifex kernel: [ 8476.803875] last sysfs file: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/rfkill/rfkill0/state
May 26 10:37:53 pontifex kernel: [ 8476.803879] Dumping ftrace buffer:
May 26 10:37:53 pontifex kernel: [ 8476.803881]    (ftrace buffer empty)
May 26 10:37:53 pontifex kernel: [ 8476.803883] CPU 1 
May 26 10:37:53 pontifex kernel: [ 8476.803884] Modules linked in: hidp nfs lockd nfs_acl sunrpc cbc aes_x86_64 aes_generic binfmt_misc ppdev i915 drm bridge stp bnep input_polldev lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy arc4 snd_seq_oss ecb snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer iwlagn iwlcore leds_hp_disk snd_seq_device uvcvideo mac80211 snd led_class compat_ioctl32 videodev sdhci_pci iTCO_wdt soundcore joydev video tpm_infineon tpm psmouse pcspkr serio_raw v4l1_compat ricoh_mmc sdhci iTCO_vendor_support cfg80211 snd_page_alloc output tpm_bios intel_agp lis3lv02d btusb ohci1394 ieee1394 e1000e vesafb fbcon tileblit font bitblit softcursor
May 26 10:37:53 pontifex kernel: [ 8476.803928] Pid: 2873, comm: Xorg Tainted: G        W  2.6.28-11-generic #42-Ubuntu
May 26 10:37:53 pontifex kernel: [ 8476.803930] RIP: 0010:[<ffffffffa038ea7d>]  [<ffffffffa038ea7d>] i915_gem_busy_ioctl+0x4d/0xd0 [i915]
May 26 10:37:53 pontifex kernel: [ 8476.803936] RSP: 0018:ffff880139063e38  EFLAGS: 00010246
May 26 10:37:53 pontifex kernel: [ 8476.803938] RAX: 0000000000000000 RBX: ffff88013988c380 RCX: 0000000000000000
May 26 10:37:53 pontifex kernel: [ 8476.803940] RDX: ffff88010bcfb500 RSI: 0000000000000082 RDI: ffff88013988c3e8
May 26 10:37:53 pontifex kernel: [ 8476.803942] RBP: ffff880139063e58 R08: 0000000000000006 R09: 0000000000000000
May 26 10:37:53 pontifex kernel: [ 8476.803944] R10: ffff880139063b66 R11: ffff880139063b58 R12: ffff88013819a000
May 26 10:37:53 pontifex kernel: [ 8476.803946] R13: ffff88010ed37c68 R14: ffff88013819a028 R15: 00000000c0086457
May 26 10:37:53 pontifex kernel: [ 8476.803948] FS:  00007f05a4326700(0000) GS:ffff88013b802d00(0000) knlGS:0000000000000000
May 26 10:37:53 pontifex kernel: [ 8476.803950] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
May 26 10:37:53 pontifex kernel: [ 8476.803952] CR2: 0000000000000020 CR3: 0000000139035000 CR4: 00000000000006a0
May 26 10:37:53 pontifex kernel: [ 8476.803954] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May 26 10:37:53 pontifex kernel: [ 8476.803956] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May 26 10:37:53 pontifex kernel: [ 8476.803958] Process Xorg (pid: 2873, threadinfo ffff880139062000, task ffff880139112cc0)
May 26 10:37:53 pontifex kernel: [ 8476.803960] Stack:
May 26 10:37:53 pontifex kernel: [ 8476.803961]  00000000fffffff4 ffff88013819a000 ffff88013988c380 ffff88010ed37c68
May 26 10:37:53 pontifex kernel: [ 8476.803964]  ffff880139063eb8 ffffffffa036c7fa 0000000139063e98 000007b5a9c576f5
May 26 10:37:53 pontifex kernel: [ 8476.803968]  ffffffffa038ea30 00007fffac3476d0 ffff88013819a044 ffff880138127480
May 26 10:37:53 pontifex kernel: [ 8476.803972] Call Trace:
May 26 10:37:53 pontifex kernel: [ 8476.803973]  [<ffffffffa036c7fa>] drm_ioctl+0x10a/0x330 [drm]
May 26 10:37:53 pontifex kernel: [ 8476.803983]  [<ffffffffa038ea30>] ? i915_gem_busy_ioctl+0x0/0xd0 [i915]
May 26 10:37:53 pontifex kernel: [ 8476.803988]  [<ffffffff802f631d>] vfs_ioctl+0x7d/0xa0
May 26 10:37:53 pontifex kernel: [ 8476.803992]  [<ffffffff802f6685>] do_vfs_ioctl+0x75/0x230
May 26 10:37:53 pontifex kernel: [ 8476.803995]  [<ffffffff802f68d9>] sys_ioctl+0x99/0xa0
May 26 10:37:53 pontifex kernel: [ 8476.803998]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
May 26 10:37:53 pontifex kernel: [ 8476.804001] Code: 89 f7 48 89 1c 24 48 89 d3 e8 80 e5 30 e0 41 8b 55 00 48 89 de 4c 89 e7 e8 f1 f4 fd ff 48 85 c0 48 89 c2 74 54 48 8b 48 38 31 c0 <8b> 79 20 85 ff 75 3c 48 89 d7 48 c7 c6 10 dd 36 a0 41 89 45 04 
May 26 10:37:53 pontifex kernel: [ 8476.804031] RIP  [<ffffffffa038ea7d>] i915_gem_busy_ioctl+0x4d/0xd0 [i915]
May 26 10:37:53 pontifex kernel: [ 8476.804037]  RSP <ffff880139063e38>
May 26 10:37:53 pontifex kernel: [ 8476.804038] CR2: 0000000000000020
May 26 10:37:53 pontifex kernel: [ 8476.804040] ---[ end trace 3a69ab225c643128 ]---
```

Any ideas to what may cause this to happen?

---

### Post by clhsharky on 2009-05-26
Its I815 & drm

Bug #342122 in xserver-xorg-video-intel (Ubuntu): “[i815] [drm ...

[http://bugs.launchpad.net/bugs/342122](http://bugs.launchpad.net/bugs/342122)

looks like posible fix at bottem of page.

---

### Post by PerJ on 2009-05-26
> **clhsharky said:**
> Its I815 & drm

Bug #342122 in xserver-xorg-video-intel (Ubuntu): “[i815] [drm ...

[http://bugs.launchpad.net/bugs/342122](http://bugs.launchpad.net/bugs/342122)

looks like posible fix at bottem of page.


Are you sure?

Is that bug applicapble for the Intel Mobile 4 chipset?

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

and lsmod shows the i915 driver is in use:
```
per@pontifex: ~$ lsmod | grep drm
drm                   123232  3 i915
```

Also, it seems that bug kept X from starting normally at all...

---

### Post by clhsharky on 2009-05-26
Sorry, I'm not sure

I didn't know your spec.
but your not alone

[http://www.google.com/cse?cx=001461844748502826593%3Ahh-ikmexth4&ie=UTF-8&q=i915+drm&sa=Search](http://www.google.com/cse?cx=001461844748502826593%3Ahh-ikmexth4&ie=UTF-8&q=i915+drm&sa=Search)

---

### Post by PerJ on 2009-05-27
Yes, this bug looks suspiciously like what I'm experiencing:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337451](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337451)

---

### Post by VincentLaw on 2009-07-31
Hi,

Exactly same symptoms like yours, Perj, even if my conf differs from your one (jaunty x86_64 on hp dv5 laptop, nvidia GC)
Complete system hangup, SysRq keys unusable, blinking CAPS LOCK led and forced to use the power button to stop and restart

In my case i suspect btusb module or maybe blueman from launchpad to be in fault because i noticed that without bluetooth usb stick plugged in, there is no crash at all ...

Knowing that i felt on your thread with the tree "ubuntu, btusb, crash" key words google search, could we consider this to be a coincidence  ?

For now i have not able to find revelant track to explore.
Recently I installed "linux-crashdump" but am still looking for informations on how to exploit the uniq vmcore i was able to generate.
What misery !!

I won't never ever laugh at the Windows blue screen ... nowadays, linux can do similar.

---

