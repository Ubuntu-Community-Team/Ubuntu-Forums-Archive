---
title: "Wine doesn't  load profile/saves"
date: 2008-08-05
forum: Wine
---

### Post by iption on 2008-08-05
I use tell me more software. It doesn't work because it can't load my profile. Here is the output:

> fixme:ntoskrnl:KeInitializeTimerEx 0x111768 0
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on ATI IXP Modem, disabling mixer
fixme:system:SystemParametersInfoW Unimplemented action: 8192 (SPI_GETFOREGROUNDLOCKTIMEOUT)
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
fixme:quartz:MPEGSplitter_query_accept MPEG-1 system streams not yet supported.
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
err:quartz:FilterGraph2_AddSourceFilter Load (80070002)
fixme:storage:StgOpenStorage STGM_PRIORITY mode not implemented correctly
fixme:storage:StgOpenStorage STGM_PRIORITY mode not implemented correctly
err:virtual:map_file_into_view shared writable mmap not supported, broken filesystem?
err:virtual:NtMapViewOfSection map_file_into_view 0x1920000 1000 000000000 failed
fixme:storage:StgCreateDocfile Transacted mode not implemented.
err:virtual:map_file_into_view shared writable mmap not supported, broken filesystem?
err:virtual:NtMapViewOfSection map_file_into_view 0x1920000 1000 000000000 failed
err:storage:ImplBIGBLOCKFILE_WriteAt Unable to get a page to write. This should never happen
err:virtual:map_file_into_view shared writable mmap not supported, broken filesystem?
err:virtual:NtMapViewOfSection map_file_into_view 0x1920000 1000 000000000 failed
err:storage:ImplBIGBLOCKFILE_WriteAt Unable to get a page to write. This should never happen
err:virtual:map_file_into_view shared writable mmap not supported, broken filesystem?
err:virtual:NtMapViewOfSection map_file_into_view 0x1920000 1000 000000000 failed
fixme:storage:StgOpenStorage STGM_PRIORITY mode not implemented correctly
fixme:storage:StgOpenStorage STGM_PRIORITY mode not implemented correctly
fixme:winmm:MMDRV_Exit Closing while ll-driver open
err:msacm:MSACM_GetRegistryKey No alias needed for registry entry


---

