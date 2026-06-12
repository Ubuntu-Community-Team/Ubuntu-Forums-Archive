---
title: "xvid playback crashes X"
date: 2006-10-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by aljaz on 2006-10-11
I'm having this weird problem and do not know where to look, anymore. I've searched forums but nothing useful came out.

I have a fresh install of Ubuntu Dapper (from the CD) and updated to the very last of updates. I have installed the new ATI drivers (8.29...) and compiled the fglrx module as suggested [here]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") (Method 2).
Everything is ok. The screen is clean and graphics is fast, fglrxinfo says I have the fglrx installed.

I have installed these drivers, because the original installation has "vesa" drivers in xorg.conf and the display is fuzzy (running on 75 Hz on a 60Hz LCD). I first installed the repository drivers (8.25.18 ) but X failed to start.

Apart from the guides I have not done any manual modifications of xorg.conf (aticonfig does the work).

And now the problem:
whenever I start an xvid (or alike) movie file, the X restarts, nothing is played back. Normal, uncompressed movies (the ones made by a Canon digital camera) are played back without any problems.
I've installed the necessary files based on the Ubuntu Wiki for the restricted formats (though I could not find this one in the repositories: gstreamer0.10-pitfdll).

this is in the syslog:

> 
Oct 11 23:32:26 slash kernel: [  529.103822] scheduling while atomic: Xorg/0x00000001/4553
Oct 11 23:32:26 slash kernel: [  529.105884] 
Oct 11 23:32:26 slash kernel: [  529.105885] Call Trace:<ffffffff803154ca>{schedule+122} <ffffffff80134da3>{__wake_up_common+67}
Oct 11 23:32:26 slash kernel: [  529.105914]        <ffffffff80134e23>{__wake_up+67} <ffffffff8841dd12>{:fglrx:firegl_irq_cleanup+274}
Oct 11 23:32:26 slash kernel: [  529.105950]        <ffffffff8841d269>{:fglrx:firegl_takedown+2249} <ffffffff8841c144>{:fglrx:firegl_release+260}
Oct 11 23:32:26 slash kernel: [  529.105989]        <ffffffff80191a72>{__fput+178} <ffffffff8018e928>{filp_close+104}
Oct 11 23:32:26 slash kernel: [  529.106002]        <ffffffff8013f59a>{put_files_struct+122} <ffffffff801407a7>{do_exit+599}
Oct 11 23:32:26 slash kernel: [  529.106017]        <ffffffff8014a9d8>{__dequeue_signal+536} <ffffffff8014130c>{do_group_exit+252}
Oct 11 23:32:26 slash kernel: [  529.106031]        <ffffffff8014c07a>{get_signal_to_deliver+1498} <ffffffff8010f5ad>{do_signal+157}
Oct 11 23:32:26 slash kernel: [  529.106046]        <ffffffff801aa4c5>{dput+165} <ffffffff8014a358>{sigprocmask+248}
Oct 11 23:32:26 slash kernel: [  529.106060]        <ffffffff8014a3f3>{sys_rt_sigprocmask+99} <ffffffff8014a358>{sigprocmask+248}
Oct 11 23:32:26 slash kernel: [  529.106072]        <ffffffff8010ff47>{sysret_signal+28} <ffffffff8011022f>{ptregscall_common+103}
Oct 11 23:32:26 slash kernel: [  529.106084]        
Oct 11 23:32:26 slash gdm[4552]: Error reinitilizing server
Oct 11 23:32:27 slash kernel: [  530.284660] ACPI: PCI Interrupt 0000:07:00.0[A] -> Link [APC6] -> GSI 16 (level, low) -> IRQ 98
Oct 11 23:32:30 slash kernel: [  532.450655] [fglrx] total      GART = 134217728
Oct 11 23:32:30 slash kernel: [  532.450759] [fglrx] free       GART = 118226944
Oct 11 23:32:30 slash kernel: [  532.450823] [fglrx] max single GART = 118226944
Oct 11 23:32:30 slash kernel: [  532.450887] [fglrx] total      LFB  = 258523136
Oct 11 23:32:30 slash kernel: [  532.450952] [fglrx] free       LFB  = 243060736
Oct 11 23:32:30 slash kernel: [  532.451015] [fglrx] max single LFB  = 243060736
Oct 11 23:32:30 slash kernel: [  532.451078] [fglrx] total      Inv  = 0
Oct 11 23:32:30 slash kernel: [  532.451139] [fglrx] free       Inv  = 0
Oct 11 23:32:30 slash kernel: [  532.451195] [fglrx] max single Inv  = 0
Oct 11 23:32:30 slash kernel: [  532.451250] [fglrx] total      TIM  = 0


I can not make anything out of it. Anybody else?

I have also tried compiling mplayer like suggested here in this forum for the wmv formats where people said it is working. I, however, do not have this luck.

Any ideas?

My computer is AMD X2 4200+ on Asus M2N-E (bios 0304) motherboard with a Gigabyte X1300PRO (ATI) PCI-E video card.

---

### Post by aljaz on 2006-11-03
Just an update: I made a clean install of ubuntu edgy 64 bit, installed the new ati drivers (8.30) and the problem persists.

Under dapper I also tried the kernel 2.6.19rc3 with the (new?) build in vesa drivers which at least gave me the proper picture on lcd (60Hz instead of the default 85Hz). And the playback was working!!! So something is wrong either with X or with ati fglrx module.

Anyone from ubuntu/ati reading this or can some other user at least reproduce the problem?

---

