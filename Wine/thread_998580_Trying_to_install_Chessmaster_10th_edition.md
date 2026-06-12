---
title: "Trying to install Chessmaster 10th edition"
date: 2008-11-30
forum: Wine
---

### Post by Arukas on 2008-11-30
I try installing chessmaster 10th edition from the cds and I get fatal error 1603

Listed below is what wine barfs out.  I seen a few where people said they had the same problem but it looks like they didn't get to the solution.  I went to the wine website, and they say it should install fine.

```
revenant@Alexandria:~$ winefile
fixme:advapi:LookupAccountNameW (null) L"revenant" (nil) 0x33be80 (nil) 0x33be84 0x33be78 - stub
fixme:advapi:LookupAccountNameW (null) L"revenant" 0x166700 0x33be80 0x166308 0x33be84 0x33be78 - stub
err:msi:ITERATE_DuplicateFiles Original file unknown L"F1319_IDriver.exe"
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 2 ignored L"CreateFolder" table values
fixme:advapi:LookupAccountNameW (null) L"revenant" (nil) 0x33cecc (nil) 0x33ced0 0x33cec4 - stub
fixme:advapi:LookupAccountNameW (null) L"revenant" 0x16a748 0x33cecc 0x166740 0x33ced0 0x33cec4 - stub
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
fixme:storage:StgCreateDocfile Storage share mode not implemented.
fixme:advapi:LookupAccountNameW (null) L"revenant" (nil) 0x7d306360 (nil) 0x7d306364 0x7d306358 - stub
fixme:advapi:LookupAccountNameW (null) L"revenant" 0x18ec270 0x7d306360 0x18e8dc8 0x7d306364 0x7d306358 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:ole:NdrClearOutParameters (0x33bd94,0x7e8385da,0x1cb6cc0): stub
fixme:msi:msi_unimplemented_action_stub UnregisterFonts -> 1 ignored L"Font" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 5 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 14 ignored L"CreateFolder" table values
err:msi:ACTION_InstallFiles Failed to copy L"E:\\Data\\TData\\JWAudio.dat" to L"C:\\Program Files\\Ubisoft\\Chessmaster 10th Edition\\Data\\TData\\JWAudio.dat" (3)
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
err:ole:ClientRpcChannelBuffer_SendReceive called from wrong apartment, should have been 0x1c00000038
err:ole:xCall RpcChannelBuffer SendReceive failed, 8001010e
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3000-00001c000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3000-00001c000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3000-00001c000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3000-00001c000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3000-00001c000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
```

---

