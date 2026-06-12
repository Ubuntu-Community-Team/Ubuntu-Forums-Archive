---
title: "I don't hear sound effects in UndertaleDemo.exe but only the backround music"
date: 2016-02-03
forum: Wine
---

### Post by michael337 on 2016-02-03
so, I don't know if this is an issue with the wine driver or uses a sound system that's partially incomplete, or I need to download a community-made driver in order to make it work fully, but this sounds like an issue with the drivers wine provided as default :\. so can somebody tell me the solution to this problem?

I run wine 1.8 in ubuntu 15.10 
Thank you

---

### Post by michael337 on 2016-02-04
here's the output:
> ~$ wine '/home/michael/Downloads/UndertaleDemo/UndertaleDemo.exe' 
err:ntdll:NtQueryInformationToken Unhandled Token Information class 29!
err:service:service_send_command service protocol error - failed to write pipe!
fixme:service:scmdatabase_autostart_services Auto-start service L"Hamachi2Svc" failed to start: 1053
fixme:heap:RtlSetHeapInformation 0x240000 0 0x23fd90 4 stub
fixme:process:SetProcessDEPPolicy (1): stub
fixme:wincodecs:IcoDecoder_GetFrame Unrecognized ICO frame magic: a0386e31
err:menubuilder:convert_to_native_icon error 0x80004005 getting frame 7
err:menubuilder:convert_to_native_icon error 0x88982F04 committing encoder
fixme:heap:RtlSetHeapInformation 0x750000 0 0x23f800 4 stub
fixme:advapi:SetEntriesInAclW unhandled access mode 4
fixme:advapi:SetEntriesInAclW unhandled access mode 4
fixme:advapi:SetEntriesInAclW unhandled access mode 4
fixme:advapi:SetEntriesInAclW unhandled access mode 4
err:service:service_send_command service protocol error - failed to write pipe!
fixme:service:scmdatabase_autostart_services Auto-start service L"LMIGuardianSvc" failed to start: 1053
fixme:wincodecs:IcoDecoder_GetFrame Unrecognized ICO frame magic: a0386e31
err:menubuilder:convert_to_native_icon error 0x80004005 getting frame 7
err:menubuilder:convert_to_native_icon error 0x88982F04 committing encoder
fixme:wincodecs:IcoDecoder_GetFrame Unrecognized ICO frame magic: a0386e31
err:menubuilder:convert_to_native_icon error 0x80004005 getting frame 7
err:menubuilder:convert_to_native_icon error 0x88982F04 committing encoder
fixme:dwmapi:DwmIsCompositionEnabled 0x58d554
fixme:wincodecs:IcoDecoder_GetFrame Unrecognized ICO frame magic: a0386e31
err:menubuilder:convert_to_native_icon error 0x80004005 getting frame 7
err:menubuilder:convert_to_native_icon error 0x88982F04 committing encoder
err:dmloader:IDirectMusicLoaderImpl_SetObject : could not attach stream to file
fixme:dmime:IDirectMusicPerformance8Impl_InitAudio (0x1b49d0, (nil), (nil), 0x1008c, 8, 64, 3f, (nil)): to check
fixme:dmime:IDirectMusicPerformance8Impl_InitAudio return dsound(0x16ee4c,0)
fixme:dmime:IDirectMusicPerformance8Impl_Init (iface = 0x1b49d0, dmusic = (nil), dsound = 0x16ee4c, hwnd = 0x1008c)
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, 0, 0x1b4b9c): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1c0570, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0x206bda4): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1c0d58, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1c1778, 0x1c14d8): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1c1110, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1c1110, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1c0d58, 0, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1c0d58, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0x228bcd8): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1c1c50, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1c23a0, 0x1c15e0): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1c1fd8, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1c1fd8, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1c1c50, -1440, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1c1c50, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0x228bcec): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1c2878, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1c2ff8, 0x1c2fc8): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1c2c00, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1c2c00, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1c2878, 0, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1c2878, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0x228bd00): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1c3500, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1c3cb0, 0x1c3c80): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1c38b8, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1c38b8, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1c3500, 0, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1c3500, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0x21c0424): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1c41a0, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1c4950, 0x1c4920): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1c4558, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1c4558, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1c41a0, 0, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1c41a0, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0x21c0438): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1c4e80, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1c5630, 0x1c5600): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1c5238, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1c5238, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1c4e80, -480, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1c4e80, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0x21c044c): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1c5b18, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1c62c8, 0x1c6298): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1c5ed0, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1c5ed0, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1c5b18, 0, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1c5b18, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0x21c0460): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1c6800, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1c6fb0, 0x1c6f80): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1c6bb8, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1c6bb8, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1c6800, 0, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1c6800, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0x21c0474): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1c7498, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1c7c48, 0x1c7c18): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1c7850, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1c7850, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1c7498, 0, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1c7498, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0x21c0488): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1c8188, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1c8908, 0x1c88d8): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1c8510, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1c8510, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1c8188, 0, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1c8188, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0x201e5ec): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1c8e10, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1c95c0, 0x1c9590): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1c91c8, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1c91c8, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1c8e10, 0, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1c8e10, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0x201e600): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1c9b08, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1ca288, 0x1ca258): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1c9e90, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1c9e90, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1c9b08, -1920, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1c9b08, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0x201e614): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1ca790, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1caf40, 0x1caf10): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1cab48, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1cab48, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1ca790, -960, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1ca790, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0x201e628): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1cb490, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1cbc10, 0x1cbbe0): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1cb818, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1cb818, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1cb490, -768, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1cb490, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0x201e63c): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1cc0f8, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1cc8a8, 0x1cc878): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1cc4b0, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1cc4b0, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1cc0f8, -576, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1cc0f8, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0x201e650): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1cce00, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1cd580, 0x1cd550): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1cd188, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1cd188, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1cce00, 0, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1cce00, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0x201e664): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1cda68, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1ce218, 0x1ce1e8): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1cde20, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1cde20, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1cda68, -480, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1cda68, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0x201e678): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1ce778, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1ceef8, 0x1ceec8): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1ceb00, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1ceb00, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1ce778, 0, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1ce778, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0x201e68c): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1cf3e0, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1cfb90, 0x1cfb60): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1cf798, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1cf798, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1cf3e0, -960, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1cf3e0, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0x201e6a0): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1d00f8, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1d0878, 0x1d0848): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1d0480, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1d0480, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1d00f8, -672, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1d00f8, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0x201e6b4): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1d0d60, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1d1510, 0x1d14e0): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1d1118, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1d1118, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1d0d60, -2016, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1d0d60, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0x201e6c8): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1d1a80, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1d21d0, 0x1d00c8): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1d1e08, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1d1e08, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1d1a80, 0, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1d1a80, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0x201e6dc): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1d26d0, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1d2e80, 0x1d2e50): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1d2a88, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1d2a88, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1d26d0, 0, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1d26d0, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0xcb86d0): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1d33f8, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1d3b48, 0x1d1a48): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1d3780, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1d3780, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1d33f8, -1440, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1d33f8, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0xcb86e4): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1d4048, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1d47f8, 0x1d47c8): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1d4400, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1d4400, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1d4048, -1152, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1d4048, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0xcb86f8): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1d4d78, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1d54c8, 0x1d33b8): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1d5100, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1d5100, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1d4d78, -1056, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1d4d78, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0xcb870c): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1d59c8, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1d6178, 0x1d6148): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1d5d80, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1d5d80, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1d59c8, 0, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1d59c8, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0xcb8720): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1d6700, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1d6e50, 0x1d4d30): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1d6a88, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1d6a88, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1d6700, 0, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1d6700, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0xcb8734): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1d7350, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1d7b00, 0x1d7ad0): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1d7708, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1d7708, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1d7350, 0, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1d7350, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0xcb8748): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1d8070, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1d87c0, 0x1d66b0): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1d83f8, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1d83f8, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1d8070, -960, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1d8070, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0xcb875c): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1d8c98, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1d9448, 0x1d9418): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1d9050, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1d9050, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1d8c98, 0, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1d8c98, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0xcb8770): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1d99e0, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1da130, 0x1d8018): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1d9d68, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1d9d68, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1d99e0, 0, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1d99e0, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0xcb8784): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1da608, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1dadb8, 0x1dad88): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1da9c0, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1da9c0, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1da608, -1056, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1da608, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0xcb8798): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1db358, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1dbaa8, 0x1d9980): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1db6e0, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1db6e0, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1db358, -1248, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1db358, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0xcb87ac): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1dbf80, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1dc730, 0x1dc700): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1dc338, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1dc338, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1dbf80, 0, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1dbf80, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0xcb87c0): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1dccd8, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1dd428, 0x1db2f0): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1dd060, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1dd060, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1dccd8, -864, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1dccd8, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x1b49d0)->(8, 64, -1, 0xcb87d4): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_Activate (0x1dd900, -1): stub
fixme:dmfile:IPersistStreamImpl_Load : WAVE form (loading to be checked)
fixme:dswave:IPersistStreamImpl_Load (0x1de0b0, 0x1de080): loading not implemented yet (only descriptor is loaded)
fixme:dmime:IDirectMusicSegment8Impl_SetParam (0x1ddcb8, GUID_IgnoreBankSelectForGM, -1, 0, 0, (nil)): stub
fixme:dmime:IDirectMusicSegment8Impl_Download (0x1ddcb8, 0x1b49d0): stub
fixme:dmime:IDirectMusicAudioPathImpl_SetVolume (0x1dd900, -960, 0): stub
fixme:dmime:IDirectMusicAudioPathImpl_GetObjectInPath (0x1dd900, -5, 24576, 0, {00000000-0000-0000-0000-000000000000}, 0, {6825a449-7524-4d82-920f-50e36ab3ab1e}, 0x32fb0c): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f694,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ddf4,0x00000000), stub!
fixme:ddraw:ddraw7_WaitForVerticalBlank iface 0x345d998, flags 0x1, event (nil) stub!
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub
fixme:dmime:IDirectMusicPerformance8Impl_StopEx (0x1b49d0, 0x1c1fd8, 0x0, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_PlaySegmentEx (0x1b49d0, 0x1c1fd8, (nil), (nil), 128, 0x0, 0x32f2f0, (nil), 0x1c1c50): stub



---

