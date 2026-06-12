---
title: "64-bit Linux: D-Link DWA-552 &amp; ndiswrapper"
date: 2008-03-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by jsym on 2008-03-21
I would like to get a D-Link DWA-522 working on my 64-bit Ubuntu machine, but I am having some difficulty making this happen.  MadWiFi doesn't seem to support the card at all, so I have been led to believe that ndiswrapper is the way to go.

Installing ndiswrapper is no problem through syanptic and it LOOKS like installing the driver works just fine too, with the exception of some "forcing parameter" statements: ```
$ sudo ndiswrapper -i net5416.inf 
installing net5416 ...
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
```
The driver file (net5416.inf) I am using is the one off the CD and not from their website (some other forum threads seemed to believe that the downloadable version is bad and I can confirm this sine it is what I started with and it wouldn't even make it this far).

Running **ndiswrapper -l** gives all the appropriate responses; however, the wireless card is never actually detected in any useful way.  Yes, I can see it through **lspci**, but that's it.  I looked at **dmesg** and found the following: ```
$ dmesg | grep ndis
[   68.386504] ndiswrapper version 1.45 loaded (smp=yes)
[   68.456956] ndiswrapper (check_nt_hdr:153): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   68.456963] ndiswrapper (load_sys_files:216): couldn't prepare driver 'net5416'
[   68.457419] ndiswrapper (load_wrap_driver:118): couldn't load driver net5416; check system log for messages from 'loadndisdriver'
[   68.459902] usbcore: registered new interface driver ndiswrapper
```
I took this to mean that I better go an find a 64-bit driver.
The only 64-bit driver for the card on dlink.com is the Vista64 bit driver (netantrx.inf).  Downloading and installing it seems to go well (there are no forcing parameter statements and it gets listed via **ndiswrapper -l**), but again I can't actually get the card to work.  **dmesg** returns the following:
```
$ dmesg | grep ndis
[   67.264615] ndiswrapper version 1.45 loaded (smp=yes)
[   67.356534] ndiswrapper (import:245): unknown symbol: ntoskrnl.exe:'KeInitializeGuardedMutex'
[   67.356543] ndiswrapper (import:245): unknown symbol: ntoskrnl.exe:'KeAcquireGuardedMutex'
[   67.356548] ndiswrapper (import:245): unknown symbol: ntoskrnl.exe:'KeReleaseGuardedMutex'
[   67.356563] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   67.356580] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   67.356586] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   67.356592] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   67.356598] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisRetreatNetBufferDataStart'
[   67.356604] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   67.356610] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[   67.356615] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   67.356631] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   67.356637] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   67.356643] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   67.356649] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   67.356655] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   67.356663] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   67.356672] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   67.356678] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   67.356697] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   67.356706] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   67.356714] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   67.356724] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   67.356730] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   67.356736] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   67.356744] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   67.356750] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   67.356756] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   67.356761] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   67.356768] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   67.356775] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[   67.356781] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[   67.356789] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   67.356795] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   67.356801] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   67.356807] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[   67.356813] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   67.356818] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   67.356825] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   67.356830] ndiswrapper (load_sys_files:216): couldn't prepare driver 'netathrx'
[   67.357296] ndiswrapper (load_wrap_driver:118): couldn't load driver netathrx; check system log for messages from 'loadndisdriver'
[   67.359787] usbcore: registered new interface driver ndiswrapper
```

So, am I out of luck until ndiswrapper supports one of the two drivers I've tried or is there a way to convince everything to work just as it is?

---

### Post by firecat53 on 2008-03-21
You might try downloading the source code for ndiswrapper from their website and compiling it. I've had to do this in the past when the version in the repos is not new enough to work with some hardware. There's lots of tutorials on compiling .... basically you need to install build-essential, unpack the source code, type './configure' (not always...might not be needed for ndiswrapper....can't remember), 'make', and then 'sudo make install'. Remove the /etc/ndiswrapper folder and try your installation steps again.

Good luck!
Scott

---

