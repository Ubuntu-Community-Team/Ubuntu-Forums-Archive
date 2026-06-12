---
title: "error during installation of MAX/MSP 5"
date: 2008-11-18
forum: Wine
---

### Post by themusicalduck on 2008-11-18
I'm trying to install MAX/MSP 5 under wine, I can start the .msi file and get through the first stages of the installation. After it seems to do a few things and copy a few files, the installer says it has been interrupted and stopped.

This is the output from the wine console -

```
fixme:advapi:LookupAccountNameW (null) L"theo" (nil) 0x32f88c (nil) 0x32f890 0x32f884 - stub
fixme:advapi:LookupAccountNameW (null) L"theo" 0x137b30 0x32f88c 0x137d80 0x32f890 0x32f884 - stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 2 ignored L"Upgrade" table values
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ControlEvent_HandleControlEvent unhandled control event L"Reinstall" arg(L"All")
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 2 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 2 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 2 ignored L"MsiAssembly" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 4 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 3 ignored L"CreateFolder" table values
fixme:shell:DllCanUnloadNow stub
fixme:mscoree:LoadLibraryShim (0x7ee3d72c L"fusion.dll", (nil), (nil), 0x32f9a4): semi-stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:advapi:CheckTokenMembership ((nil) 0x137588 0x33fb08) stub!
fixme:setupapi:pSetupGetGlobalFlags stub
fixme:wintrust:CryptCATAdminCalcHashFromFileHandle 0x2c 0x33f3a0 0x33fa14 0
fixme:wintrust:WinVerifyTrust unimplemented for 3
wine: Unhandled page fault on read access to 0x00000000 at address 0xf7cb9796 (thread 0045), starting debugger...
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1627
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1627

```

The installer does seem to copy the files over to the C drive, but if I try to run the Max.exe file, I get -

```
wine: Call from 0x7b845880 to unimplemented function ntoskrnl.exe.KeInitializeMutex, aborting
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
err:winedevice:ServiceMain driver L"TPkd" failed to load
Segmentation fault

```

Anyone know how to fix it?

---

### Post by themusicalduck on 2008-11-19
bump

---

### Post by themusicalduck on 2008-11-19
bump

---

### Post by cmbryan on 2008-12-06
Trying to solve this as well...

---

