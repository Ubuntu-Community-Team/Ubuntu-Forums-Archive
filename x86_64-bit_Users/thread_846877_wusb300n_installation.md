---
title: "wusb300n installation"
date: 2008-07-01
forum: x86 64-bit Users
---

### Post by nyrb4life on 2008-07-01
I just installed Ubuntu 8.04 and I noticed that my wusb300n linksys wireless card doesn't work. I did this:[http://ubuntuforums.org/showthread.php?t=530772]("http://ubuntuforums.org/showthread.php?t=530772")

And I got pretty far until the "sudo dmesg | grep ndis" part. It said something along the lines of kernel is 64 bit, driver is 32 bit.

So I went along and downloaded 64 bit wusb300n drivers and uninstalled the old drivers. I went to the terminal and followed that tutorila again and the same error came up.

Is there any way I can install my wireless card?? i'm getting pretty desperate. Please give instructions in a way a noob like me can understand...Thanks

---

### Post by marcopolo1010 on 2008-08-05
Same issue here.  I've tried everything I can find online to get either my WUSB300N or my WUSB54GSC to work on 64-bit Ubuntu (installed via Wubi if it matters), but no success.

I can install the 32-bit drivers, but get the same error message as above about the kernel being 64-bit.  And ndiswrapper gives me an "invalid driver" error if I try with the Vista 64-bit drivers (WUSB54GSC-x64.inf).

Has anyone had any luck with either WUSB300N or WUSB54GSC on 64-bit Ubuntu?

---

### Post by lopallares@hotmail.com on 2008-10-06
Same problem here!
 Ubuntu works perfect on amd 64, but there is something wrong with the wireless, specially with this WUSB300N. I did over 4 days and 5 nights to solve it, but can t find (fix) it. 
 I tried lots of things, one it was tihs: [http://ubuntuforums.org/showthread.php?t=530772&highlight=wusb300n](http://ubuntuforums.org/showthread.php?t=530772&highlight=wusb300n)
 But when I get down to the line :
# sudo dmesg | grep ndis
Terminal answers me this:

riki@ubuntu64:~$ sudo dmesg | grep ndis
[   38.807663] ndiswrapper version 1.52 loaded (smp=yes, preempt=rt)
[   39.105232] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   39.105241] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   39.105248] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   39.105254] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   39.105274] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   39.105282] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   39.105289] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   39.105296] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   39.105302] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   39.105311] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   39.105321] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[   39.105328] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   39.105334] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   39.105341] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   39.105347] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   39.105354] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   39.105360] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   39.105367] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   39.105388] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[   39.105392] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[   39.105397] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[   39.105401] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   39.105414] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   39.105419] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   39.105422] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   39.105424] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netmw24c'
[   39.105766] ndiswrapper (load_wrap_driver:112): couldn't load driver netmw24c; check system log for messages from 'loadndisdriver'
[   39.105793] usbcore: registered new interface driver ndiswrapper
[ 1341.125680] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[ 1341.125902] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[ 1341.126073] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[ 1341.126243] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[ 1341.126422] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[ 1341.126618] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[ 1341.126794] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[ 1341.126964] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[ 1341.127137] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[ 1341.127321] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[ 1341.127496] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[ 1341.127676] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[ 1341.127844] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[ 1341.128024] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[ 1341.128184] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[ 1341.128357] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[ 1341.128525] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[ 1341.128718] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[ 1341.128900] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[ 1341.129104] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[ 1341.129269] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[ 1341.129438] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[ 1341.129650] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[ 1341.129816] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[ 1341.129976] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[ 1341.130135] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netmw24c'
[ 1341.130723] ndiswrapper (load_wrap_driver:112): couldn't load driver netmw24c; check system log for messages from 'loadndisdriver'

i dont know how to continue and cant find anything else on the web. Any idea?
Thanks to all for your contribution!

---

### Post by SuperD2000 on 2008-12-01
To my understanding, we need to get Win XP x64 drivers for the WUSB300N, Alas I have searched online and I have been unable to find drivers that work. Sorry.

---

