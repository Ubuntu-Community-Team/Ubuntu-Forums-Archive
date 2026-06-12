---
title: "ndiswrapper errors again..."
date: 2005-09-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by jshein on 2005-09-26
I have read all the posts regarding using ndiswrapper. I still have no been able to solve my problem.

I have an acer travelmate 4400 with a Broadcom BCM94318MPG
( fcc id QDS-BRCM1016 )
I am using the amd 64 drivers from the Acer site.

The module shows an error inserting, but ndiswrapper indicates that the hardware is present.

output of dmesg:

 symbol x86_64_RtlAnsiStringToUnicodeString
[ 1252.659757] ndiswrapper: Unknown symbol x86_64_NdisInitializeReadWriteLock
[ 1252.659791] ndiswrapper: Unknown symbol x86_64_KeAcquireSpinLockRaiseToDpc
[ 1252.659842] ndiswrapper: Unknown symbol x86_64_KeAcquireSpinLockAtDpcLevel
[ 1252.659876] ndiswrapper: Unknown symbol x86_64_NdisFreeMemory
[ 1252.659910] ndiswrapper: Unknown symbol x86_64_ExQueryDepthSList
[ 1252.659944] ndiswrapper: Unknown symbol x86_64_NdisDprAcquireSpinLock
[ 1252.659980] ndiswrapper: Unknown symbol x86_64_NdisUnchainBufferAtBack
[ 1252.660015] ndiswrapper: Unknown symbol x86_64_NdisInitializeTimer
[ 1252.660055] ndiswrapper: Unknown symbol x86_64_NdisQueryBuffer
[ 1252.660089] ndiswrapper: Unknown symbol x86_64_rand
[ 1252.660122] ndiswrapper: Unknown symbol x86_64_InterlockedPushEntrySList
[ 1252.660171] ndiswrapper: Unknown symbol x86_64_KeLowerIrql
[ 1252.660228] ndiswrapper: Unknown symbol x86_64_NdisInterlockedInsertTailList
[ 1252.660263] ndiswrapper: Unknown symbol x86_64_NdisQueryBufferOffset
[ 1252.660297] ndiswrapper: Unknown symbol x86_64_ObfDereferenceObject
[ 1252.660331] ndiswrapper: Unknown symbol x86_64_NdisReadConfiguration
[ 1252.660365] ndiswrapper: Unknown symbol x86_64_RtlWriteRegistryValue
[ 1252.660399] ndiswrapper: Unknown symbol x86_64_USBD_ParseConfigurationDescriptor
[ 1252.660433] ndiswrapper: Unknown symbol x86_64_RtlFreeAnsiString
[ 1252.660467] ndiswrapper: Unknown symbol x86_64_IoDeleteSymbolicLink
[ 1252.660501] ndiswrapper: Unknown symbol x86_64_NdisMUnmapIoSpace
[ 1252.660542] ndiswrapper: Unknown symbol x86_64_NdisUnmapFile
[ 1252.660578] ndiswrapper: Unknown symbol x86_64_KefReleaseSpinLockFromDpcLevel
[ 1252.660612] ndiswrapper: Unknown symbol x86_64_NdisMSendComplete
[ 1252.660646] ndiswrapper: Unknown symbol x86_64_NdisInitializeEvent
[ 1252.660680] ndiswrapper: Unknown symbol x86_64_KeWaitForSingleObject
[ 1252.660714] ndiswrapper: Unknown symbol x86_64_KeQueryPriorityThread
[ 1252.660748] ndiswrapper: Unknown symbol x86_64_NdisOpenProtocolConfiguration
[ 1252.660786] ndiswrapper: Unknown symbol x86_64_NdisUnicodeStringToAnsiString
[ 1252.660835] ndiswrapper: Unknown symbol x86_64_NdisFreePacket
[ 1252.660871] ndiswrapper: Unknown symbol x86_64_MmIsAddressValid
[ 1252.660905] ndiswrapper: Unknown symbol x86_64_RtlIntegerToUnicodeString
[ 1252.660939] ndiswrapper: Unknown symbol x86_64_NdisAnsiStringToUnicodeString
[ 1252.660973] ndiswrapper: Unknown symbol x86_64_KeClearEvent
[ 1252.661030] ndiswrapper: Unknown symbol x86_64__allshl
[ 1252.661064] ndiswrapper: Unknown symbol x86_64_InterlockedExchange
[ 1252.661098] ndiswrapper: Unknown symbol x86_64__allshr
[ 1252.661132] ndiswrapper: Unknown symbol x86_64_READ_PORT_BUFFER_USHORT
[ 1252.661166] ndiswrapper: Unknown symbol x86_64_IofCallDriver
[ 1252.661200] ndiswrapper: Unknown symbol x86_64__win_memchr
[ 1252.661233] ndiswrapper: Unknown symbol x86_64__aullshl
[ 1252.661267] ndiswrapper: Unknown symbol x86_64_PoCallDriver
[ 1252.661301] ndiswrapper: Unknown symbol lin_to_win3
[ 1252.661335] ndiswrapper: Unknown symbol x86_64_NdisScheduleWorkItem
[ 1252.661369] ndiswrapper: Unknown symbol lin_to_win1
[ 1252.661402] ndiswrapper: Unknown symbol x86_64_DbgPrint
[ 1252.661436] ndiswrapper: Unknown symbol x86_64_NdisAllocatePacket
[ 1252.661470] ndiswrapper: Unknown symbol x86_64_NdisMRegisterIoPortRange
[ 1252.661504] ndiswrapper: Unknown symbol x86_64__allmul
[ 1252.661552] ndiswrapper: Unknown symbol x86_64_KfReleaseSpinLock
[ 1252.661586] ndiswrapper: Unknown symbol x86_64_NdisMFreeMapRegisters
[ 1252.661620] ndiswrapper: Unknown symbol x86_64__win_strlen
[ 1252.661656] ndiswrapper: Unknown symbol x86_64_NdisBufferVirtualAddress
[ 1252.661690] ndiswrapper: Unknown symbol x86_64_KeInitializeSpinLock
[ 1252.661724] ndiswrapper: Unknown symbol x86_64_NdisInterlockedInsertHeadList
[ 1252.661758] ndiswrapper: Unknown symbol x86_64_IoAllocateMdl
[ 1252.661792] ndiswrapper: Unknown symbol x86_64_NdisMInitializeTimer
[ 1252.661826] ndiswrapper: Unknown symbol x86_64__win_vsprintf
[ 1252.661860] ndiswrapper: Unknown symbol x86_64_NdisReadPcmciaAttributeMemory
[ 1252.661897] ndiswrapper: Unknown symbol x86_64_WRITE_PORT_UCHAR
[ 1252.661931] ndiswrapper: Unknown symbol x86_64_NdisWaitEvent
[ 1252.661965] ndiswrapper: Unknown symbol x86_64_MmMapLockedPages
[ 1252.661999] ndiswrapper: Unknown symbol x86_64_RtlCopyUnicodeString
[ 1252.662039] ndiswrapper: Unknown symbol x86_64_NdisMAllocateSharedMemory
[ 1252.662073] ndiswrapper: Unknown symbol x86_64_ExpInterlockedPopEntrySList
[ 1252.662108] ndiswrapper: Unknown symbol x86_64_ExfInterlockedRemoveHeadList
[ 1252.662142] ndiswrapper: Unknown symbol x86_64_USBD_CreateConfigurationRequestEx
[ 1252.662183] ndiswrapper: Unknown symbol x86_64_IoFreeMdl
[ 1252.662218] ndiswrapper: Unknown symbol x86_64_RtlEqualString
[ 1252.662252] ndiswrapper: Unknown symbol x86_64__aullmul
[ 1252.662288] ndiswrapper: Unknown symbol x86_64_RtlUnicodeStringToInteger
[ 1252.662322] ndiswrapper: Unknown symbol x86_64_IoWMIRegistrationControl
[ 1252.662356] ndiswrapper: Unknown symbol x86_64_READ_PORT_ULONG
[ 1252.662396] ndiswrapper: Unknown symbol x86_64_KeBugCheckEx
[ 1252.662430] ndiswrapper: Unknown symbol x86_64_IoCancelIrp
[ 1252.662481] ndiswrapper: Unknown symbol x86_64_NdisCloseConfiguration
[ 1252.662538] ndiswrapper: Unknown symbol x86_64__win__vsnprintf
[ 1252.662576] ndiswrapper: Unknown symbol x86_64_NdisInterlockedDecrement
[ 1252.662610] ndiswrapper: Unknown symbol x86_64_WRITE_REGISTER_ULONG
[ 1252.662644] ndiswrapper: Unknown symbol x86_64_NdisMGetDeviceProperty
[ 1252.662678] ndiswrapper: Unknown symbol x86_64_KfAcquireSpinLock
[ 1252.662712] ndiswrapper: Unknown symbol x86_64_NdisMRemoveMiniport
[ 1252.662746] ndiswrapper: Unknown symbol x86_64_KeReleaseSpinLock
[ 1252.662780] ndiswrapper: Unknown symbol x86_64_NdisMDeregisterIoPortRange
[ 1252.662814] ndiswrapper: Unknown symbol x86_64_ZwClose
[ 1252.662862] ndiswrapper: Unknown symbol x86_64_IoIsWdmVersionAvailable
[ 1252.662896] ndiswrapper: Unknown symbol x86_64_NdisWriteErrorLogEntry
[ 1252.662930] ndiswrapper: Unknown symbol lin_to_win6
[ 1252.662978] ndiswrapper: Unknown symbol x86_64_KeReleaseMutex
[ 1252.663012] ndiswrapper: Unknown symbol x86_64__win_strcmp
[ 1252.663053] ndiswrapper: Unknown symbol x86_64__win_vsnprintf
[ 1252.663087] ndiswrapper: Unknown symbol x86_64__win_memmove
[ 1252.663121] ndiswrapper: Unknown symbol x86_64_KeSetEvent
[ 1252.663165] ndiswrapper: Unknown symbol x86_64__win_strncmp
[ 1252.663202] ndiswrapper: Unknown symbol x86_64_NdisAllocateMemory
[ 1252.663250] ndiswrapper: Unknown symbol x86_64_USBD_CreateConfigurationRequest
[ 1252.663284] ndiswrapper: Unknown symbol x86_64_NdisMRegisterMiniport
[ 1252.663337] ndiswrapper: Unknown symbol x86_64_InterlockedDecrement
[ 1252.663371] ndiswrapper: Unknown symbol x86_64_NdisCopyFromPacketToPacket
[ 1252.663414] ndiswrapper: Unknown symbol x86_64_NdisBufferLength
[ 1252.663448] ndiswrapper: Unknown symbol x86_64__win_strcpy
[ 1252.663482] ndiswrapper: Unknown symbol x86_64_EthFilterDprIndicateReceive
[ 1252.663517] ndiswrapper: Unknown symbol x86_64_WRITE_PORT_BUFFER_USHORT
[ 1252.663568] ndiswrapper: Unknown symbol x86_64_NdisMTransferDataComplete
[ 1252.663603] ndiswrapper: Unknown symbol x86_64_NdisInterlockedIncrement
[ 1252.663637] ndiswrapper: Unknown symbol x86_64_KeAcquireSpinLock
[ 1252.663671] ndiswrapper: Unknown symbol x86_64_NdisOpenConfigurationKeyByName
[ 1252.663705] ndiswrapper: Unknown symbol x86_64_InterlockedCompareExchange
[ 1252.663739] ndiswrapper: Unknown symbol x86_64_NdisQueryBufferSafe
[ 1252.663785] ndiswrapper: Unknown symbol x86_64_READ_PORT_USHORT
[ 1252.663819] ndiswrapper: Unknown symbol x86_64_ObReferenceObjectByHandle
[ 1252.663853] ndiswrapper: Unknown symbol x86_64_EthRxIndicateHandler
[ 1252.663898] ndiswrapper: Unknown symbol x86_64_WRITE_REGISTER_USHORT
[ 1252.663932] ndiswrapper: Unknown symbol x86_64_IoInitializeIrp
[ 1252.663965] ndiswrapper: Unknown symbol x86_64_NdisMRegisterDevice
[ 1252.664003] ndiswrapper: Unknown symbol x86_64_IoCreateDevice
[ 1252.664058] ndiswrapper: Unknown symbol lin_to_win5
[ 1252.664092] ndiswrapper: Unknown symbol x86_64_NdisMCompleteBufferPhysicalMapping
[ 1252.664126] ndiswrapper: Unknown symbol x86_64_ObDereferenceObject
[ 1252.664160] ndiswrapper: Unknown symbol x86_64_ExDeleteNPagedLookasideList
[ 1252.664194] ndiswrapper: Unknown symbol x86_64_KfRaiseIrql
[ 1252.664228] ndiswrapper: Unknown symbol x86_64_IoDeleteDevice
[ 1252.664261] ndiswrapper: Unknown symbol x86_64_NdisAllocateMemoryWithTag
[ 1252.664312] ndiswrapper: Unknown symbol x86_64_RtlEqualUnicodeString
[ 1252.664346] ndiswrapper: Unknown symbol x86_64__win_snprintf
[ 1252.664380] ndiswrapper: Unknown symbol x86_64_EthRxComplete
[ 1252.664413] ndiswrapper: Unknown symbol x86_64__aullshr
[ 1252.664447] ndiswrapper: Unknown symbol x86_64_NdisMCoActivateVcComplete
[ 1252.664481] ndiswrapper: Unknown symbol x86_64_MmMapLockedPagesSpecifyCache
[ 1252.664516] ndiswrapper: Unknown symbol x86_64_NdisMQueryAdapterInstanceName
[ 1252.664556] ndiswrapper: Unknown symbol x86_64__alldiv
[ 1252.664602] ndiswrapper: Unknown symbol x86_64_NdisAllocateBufferPool
[ 1252.664636] ndiswrapper: Unknown symbol x86_64_NdisMAllocateMapRegisters
[ 1252.664670] ndiswrapper: Unknown symbol x86_64_NdisAllocatePacketPool
[ 1252.664704] ndiswrapper: Unknown symbol x86_64_NdisPacketPoolUsage
[ 1252.664738] ndiswrapper: Unknown symbol x86_64_KefAcquireSpinLockAtDpcLevel
[ 1252.664772] ndiswrapper: Unknown symbol x86_64_NdisCancelTimer
[ 1252.664821] ndiswrapper: Unknown symbol x86_64_NdisInitAnsiString
[ 1252.664855] ndiswrapper: Unknown symbol x86_64_NdisMFreeSharedMemory
[ 1252.664889] ndiswrapper: Unknown symbol x86_64_NdisInitializeString
[ 1252.664923] ndiswrapper: Unknown symbol x86_64_NdisMIndicateStatusComplete
[ 1252.664975] ndiswrapper: Unknown symbol x86_64_InterlockedPopEntrySList
[ 1252.665009] ndiswrapper: Unknown symbol x86_64_NdisMSleep
[ 1252.665049] ndiswrapper: Unknown symbol x86_64_NdisMIndicateReceivePacket
[ 1252.665087] ndiswrapper: Unknown symbol x86_64_NdisSetEvent
[ 1252.665126] ndiswrapper: Unknown symbol x86_64_IoAllocateWorkItem
[ 1252.665162] ndiswrapper: Unknown symbol x86_64_NdisMRegisterInterrupt
[ 1252.665196] ndiswrapper: Unknown symbol x86_64_NdisMDeregisterAdapterShutdownHandler
[ 1252.665230] ndiswrapper: Unknown symbol x86_64_KeGetCurrentThread
[ 1252.665264] ndiswrapper: Unknown symbol x86_64_NdisUnchainBufferAtFront
[ 1252.665298] ndiswrapper: Unknown symbol x86_64_IoFreeWorkItem
[ 1252.665347] ndiswrapper: Unknown symbol x86_64_NdisInitializeWrapper
[ 1252.665391] ndiswrapper: Unknown symbol x86_64_NdisMGetDmaAlignment
[ 1252.665425] ndiswrapper: Unknown symbol x86_64_NdisMCoDeactivateVcComplete
[ 1252.665471] ndiswrapper: Unknown symbol x86_64__win_atoi
[ 1252.665505] ndiswrapper: Unknown symbol x86_64_NdisOpenConfigurationKeyByIndex
[ 1252.665545] ndiswrapper: Unknown symbol x86_64_MmMapIoSpace
[ 1252.665579] ndiswrapper: Unknown symbol x86_64_NdisFreeBufferPool
[ 1252.665613] ndiswrapper: Unknown symbol x86_64_KeQueryTimeIncrement
[ 1252.665669] ndiswrapper: Unknown symbol x86_64_NdisDprAllocatePacket
[ 1252.665703] ndiswrapper: Unknown symbol x86_64_RtlCompareUnicodeString
[ 1252.665737] ndiswrapper: Unknown symbol x86_64_NdisCopyFromPacketToPacketSafe
[ 1252.665774] ndiswrapper: Unknown symbol x86_64_KeSetTimer
[ 1252.665808] ndiswrapper: Unknown symbol x86_64_IoGetDeviceProperty
[ 1252.665842] ndiswrapper: Unknown symbol x86_64_PsTerminateSystemThread
[ 1252.665876] ndiswrapper: Unknown symbol x86_64_NdisReleaseSpinLock
[ 1252.665927] ndiswrapper: Unknown symbol x86_64_MmBuildMdlForNonPagedPool
[ 1252.665971] ndiswrapper: Unknown symbol x86_64_PsCreateSystemThread
[ 1252.666006] ndiswrapper: Unknown symbol x86_64___C_specific_handler
[ 1252.666046] ndiswrapper: Unknown symbol x86_64_NdisInitString
[ 1252.666080] ndiswrapper: Unknown symbol x86_64_MmUnlockPages
[ 1252.666118] ndiswrapper: Unknown symbol x86_64_NdisMPciAssignResources
[ 1252.666152] ndiswrapper: Unknown symbol x86_64_NdisMSynchronizeWithInterrupt
[ 1252.666186] ndiswrapper: Unknown symbol x86_64_NdisInterlockedRemoveHeadList
[ 1252.666220] ndiswrapper: Unknown symbol x86_64_IoCreateUnprotectedSymbolicLink
[ 1252.666266] ndiswrapper: Unknown symbol x86_64_WmiQueryTraceInformation
[ 1252.666300] ndiswrapper: Unknown symbol x86_64_NdisGetSystemUpTime
[ 1252.666334] ndiswrapper: Unknown symbol x86_64__allrem
[ 1252.666367] ndiswrapper: Unknown symbol x86_64_RtlUnwind
[ 1252.666401] ndiswrapper: Unknown symbol x86_64__win_strstr
[ 1252.666435] ndiswrapper: Unknown symbol x86_64_NdisMRegisterAdapterShutdownHandler
[ 1252.666472] ndiswrapper: Unknown symbol x86_64_NdisAllocateSpinLock
[ 1252.666506] ndiswrapper: Unknown symbol x86_64_KeCancelTimer
[ 1252.666546] ndiswrapper: Unknown symbol x86_64__win_toupper
[ 1252.666580] ndiswrapper: Unknown symbol x86_64_IofCompleteRequest
[ 1252.666614] ndiswrapper: Unknown symbol x86_64__aullrem
[ 1252.666648] ndiswrapper: Unknown symbol x86_64_RtlInitString
[ 1252.666682] ndiswrapper: Unknown symbol x86_64_KeWaitForMultipleObjects
[ 1252.666716] ndiswrapper: Unknown symbol x86_64_NdisMRegisterUnloadHandler
[ 1252.666750] ndiswrapper: Unknown symbol x86_64__win_sprintf
[ 1252.666784] ndiswrapper: Unknown symbol x86_64_NdisAdjustBufferLength
[ 1252.666818] ndiswrapper: Unknown symbol lin_to_win2
[ 1252.666851] ndiswrapper: Unknown symbol lin_to_win4
[ 1252.666885] ndiswrapper: Unknown symbol x86_64_NdisCloseFile
[ 1252.666919] ndiswrapper: Unknown symbol x86_64_NdisMCancelTimer
[ 1252.666953] ndiswrapper: Unknown symbol x86_64_NdisGetBufferPhysicalArraySize
[ 1252.666990] ndiswrapper: Unknown symbol x86_64_KeGetCurrentIrql
[ 1252.667031] ndiswrapper: Unknown symbol x86_64_NdisTerminateWrapper
[ 1252.667081] ndiswrapper: Unknown symbol x86_64_KeQueryInterruptTime
[ 1252.667119] ndiswrapper: Unknown symbol x86_64_NdisWritePciSlotInformation
[ 1252.667153] ndiswrapper: Unknown symbol x86_64_MmSizeOfMdl
[ 1252.667191] ndiswrapper: Unknown symbol x86_64_RtlZeroMemory
[ 1252.667225] ndiswrapper: Unknown symbol x86_64_IoReleaseCancelSpinLock
[ 1252.667259] ndiswrapper: Unknown symbol x86_64_NdisOpenConfiguration
[ 1252.667293] ndiswrapper: Unknown symbol x86_64_KeInitializeDpc
[ 1252.667327] ndiswrapper: Unknown symbol x86_64_NdisFreeBuffer
[ 1252.667361] ndiswrapper: Unknown symbol x86_64_NdisInitUnicodeString
[ 1252.667395] ndiswrapper: Unknown symbol x86_64__win_srand
[ 1252.667429] ndiswrapper: Unknown symbol x86_64_NdisAllocateBuffer
[ 1252.667463] ndiswrapper: Unknown symbol x86_64__win_memset
[ 1252.667497] ndiswrapper: Unknown symbol x86_64_KfLowerIrql
[ 1252.667554] ndiswrapper: Unknown symbol x86_64_NdisFreePacketPool
[ 1252.667588] ndiswrapper: Unknown symbol x86_64_KeQueryPerformanceCounter
[ 1252.667623] ndiswrapper: Unknown symbol x86_64_ExInterlockedPopEntrySList
[ 1252.667657] ndiswrapper: Unknown symbol x86_64_InterlockedIncrement
[ 1252.667698] ndiswrapper: Unknown symbol x86_64_NdisMStartBufferPhysicalMapping
[ 1252.667732] ndiswrapper: Unknown symbol x86_64_DbgBreakPoint
[ 1252.667766] ndiswrapper: Unknown symbol x86_64_NdisMIndicateStatus
[ 1252.667809] ndiswrapper: Unknown symbol x86_64_IoAllocateIrp
[ 1252.667847] ndiswrapper: Unknown symbol x86_64_ExInterlockedAddLargeStatistic
[ 1252.667881] ndiswrapper: Unknown symbol x86_64_NdisMSetAttributesEx
[ 1252.667915] ndiswrapper: Unknown symbol x86_64_ExInitializeNPagedLookasideList
[ 1252.667949] ndiswrapper: Unknown symbol x86_64_NdisMSetInformationComplete
[ 1252.667983] ndiswrapper: Unknown symbol x86_64_NdisResetEvent





Any ideas? It would be really nice to get this working.

---

### Post by mlomker on 2005-09-26
> Any ideas? It would be really nice to get this working.

I spent some time searching but Acer's driver is the only one that I could locate.  I had Broadcom in my last laptop and purposefully avoided them on my new one because they won't work with open-source developers to create a linux driver.

The general advice is always to try a driver from another vendor.  Not all Broadcom drivers are the same--they are developed by the OEM that builds the machines (maybe Acer, maybe not).

---

### Post by NickB on 2005-09-26
I had the same problem with the stock ndiswrapper driver that comes with 2.6.12-9.  I compiled and installed my own from source to fix the problem.

Nick

---

