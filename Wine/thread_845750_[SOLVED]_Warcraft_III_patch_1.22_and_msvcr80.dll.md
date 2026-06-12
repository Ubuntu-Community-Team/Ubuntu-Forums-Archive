---
title: "[SOLVED] Warcraft III patch 1.22 and msvcr80.dll"
date: 2008-06-30
forum: Wine
---

### Post by no1wantdthisname on 2008-06-30
[COLOR="Gray"]After the latest patch, Warcraft III no longer runs.  It was working fine before.  Here's the output:
```

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Warcraft III\\Storm.dll") not found
err:module:import_dll Library Storm.dll (which is needed by L"C:\\Program Files\\Warcraft III\\war3.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Warcraft III\\war3.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Warcraft III\\war3.exe" failed, status c0000135

```

So I got msvcr80.dll from a windows install but it still complains with a popup saying:
```

Runtime Error!
Program C:\Program Files\Warcraft III\war3.exe
R6034
An application has made an attempt to load the C runtime library incorrectly.
Please contact the application's support team for more information.

```

So far, I've already tried reinstalling warcraft 3, changing windows version, and also trying older various versions of wine.  Nothing seems to work.  Anyone have an ideas?
[/COLOR]
EDIT: Scratch that, thought it was a wine problem, but was just a Warcraft III problem.  Here's the fix for anyone facing this problem.  Used winetricks at [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks) and ran 
```

sh winetricks vcrun2005sp1 vcrun2005

```

---

### Post by amba on 2008-07-01
thank you very much! It worked !
Now we got new counters in ROC Dota, denied creeps, and last-hit.
Imba!!

---

### Post by haukew on 2008-07-02
Hey, thanks for the post, but it didn't fix it for me. I tried both, downloading the dll manually and the winetricks-tip. Both don't make the popup you posted disappear, it just stays.

```
Runtime Error!
Program C:\Program Files\Warcraft III\war3.exe
R6034
An application has made an attempt to load the C runtime library incorrectly.
Please contact the application's support team for more information.
```

Any ideas how i can fix it?

This is the complete terminal-output:

```
hauke ~ > winetricks vcrun2005 vcrun2005sp1
Setting Windows version to win2k
Executing wine regedit /home/hauke/.wine/drive_c/winetrickstmp/set-winver.reg
fixme:advapi:SetEntriesInAclA 1 0x33f79c (nil) 0x33f7d4
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f788 (nil) 0x33f7d0
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f7a8 (nil) 0x33f7f0
fixme:advapi:SetSecurityInfo stub
Executing wine /home/hauke/.winetrickscache/vcrun2005/vcredist_x86.exe
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d7cd9f8, overlapped 0x7d7cd9dc): stub
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP001.TMP\\" 00000000
fixme:advapi:LookupAccountNameW (null) L"hauke" (nil) 0x33f8ac (nil) 0x33f8b0 0x33f8a4 - stub
fixme:advapi:LookupAccountNameW (null) L"hauke" 0x1323f8 0x33f8ac 0x12dae8 0x33f8b0 0x33f8a4 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 10 ignored L"MsiAssembly" table values
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
Clearing Windows version back to default
Executing wine regedit /home/hauke/.wine/drive_c/winetrickstmp/unset-winver.reg
Install of vcrun2005 done
Executing wine /home/hauke/.winetrickscache/vcrun2005sp1/vcredist_x86.exe
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP001.TMP\\" 00000000
fixme:advapi:LookupAccountNameW (null) L"hauke" (nil) 0x33f8ac (nil) 0x33f8b0 0x33f8a4 - stub
fixme:advapi:LookupAccountNameW (null) L"hauke" 0x131b50 0x33f8ac 0x1314c8 0x33f8b0 0x33f8a4 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 10 ignored L"MsiAssembly" table values
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
Install of vcrun2005sp1 done
winetricks done.
hauke ~ > wine ~/.wine/drive_c/Programme/Warcraft\ III/war3.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:winspool:CUPS_LoadPrinters printer 'DCP150C' not added by AddPrinterA (error 1797)
fixme:advapi:SetEntriesInAclA 1 0x33f79c (nil) 0x33f7d4
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f788 (nil) 0x33f7d0
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f7a8 (nil) 0x33f7f0
fixme:advapi:SetSecurityInfo stub
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d7d29f8, overlapped 0x7d7d29dc): stub
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Programme\\Warcraft III\\war3.exe" failed, status c0000142
hauke ~ >

```

Thanks in advance, hauke

---

### Post by no1wantdthisname on 2008-07-02
What wine version are you using?  Because I'm actually using this repo:
```

deb http://ppa.launchpad.net/starfall87/ubuntu hardy main

```
for a patched wine 1.10 to fix the alt+tab and hosting issues.

Or try just doing only
```

sh winetricks vcrun2005sp1

```

When I think about it, vcrun2005sp1 might just be a set of updated versions of vcrun2005.  I noticed you switched the order, so vcrun2005 might be overwriting vcrun2005sp1 or vice versa.  If this doesn't work, try the original command.

---

### Post by haukew on 2008-07-02
Thanks for the help - i used the wine-version you mentioned, deleted all my Warcraft3 and reinstalled it. Now it works :popcorn:
[DOUBLESOLVED] :-)

---

### Post by eNTi on 2008-07-02
i'm getting the exact same errors as of today... can't fix them though.
```
hauke ~ > winetricks vcrun2005 vcrun2005sp1
Setting Windows version to win2k
Executing wine regedit /home/hauke/.wine/drive_c/winetrickstmp/set-winver.reg
fixme:advapi:SetEntrieseAclA 1 0x33f79c (nil) 0x33f7d4
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntrieseAclA 1 0x33f788 (nil) 0x33f7d0
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntrieseAclA 1 0x33f7a8 (nil) 0x33f7f0
fixme:advapi:SetSecurityInfo stub
Executing wine /home/hauke/.winetrickscache/vcrun2005/vcredist_x86.exe
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d7cd9f8, overlapped 0x7d7cd9dc): stub
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP001.TMP\\" 00000000
fixme:advapi:LookupAccountNameW (null) L"hauke" (nil) 0x33f8ac (nil) 0x33f8b0 0x33f8a4 - stub
fixme:advapi:LookupAccountNameW (null) L"hauke" 0x1323f8 0x33f8ac 0x12dae8 0x33f8b0 0x33f8a4 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 10 ignored L"MsiAssembly" table values
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
fixme:msi:MsiEnumProductsExA (null) (null) 4 0 0x7e160688 0x7e16066c (nil) (nil)
Clearing Windows version back to default
Executing wine regedit /home/hauke/.wine/drive_c/winetrickstmp/unset-winver.reg
Install of vcrun2005 done
Executing wine /home/hauke/.winetrickscache/vcrun2005sp1/vcredist_x86.exe
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP001.TMP\\" 00000000
fixme:advapi:LookupAccountNameW (null) L"hauke" (nil) 0x33f8ac (nil) 0x33f8b0 0x33f8a4 - stub
fixme:advapi:LookupAccountNameW (null) L"hauke" 0x131b50 0x33f8ac 0x1314c8 0x33f8b0 0x33f8a4 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 10 ignored L"MsiAssembly" table values
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
Install of vcrun2005sp1 done
winetricks done.
hauke ~ > wine ~/.wine/drive_c/Programme/Warcraft\ III/war3.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:winspool:CUPS_LoadPrinters printer 'DCP150C' not added by AddPrinterA (error 1797)
fixme:advapi:SetEntrieseAclA 1 0x33f79c (nil) 0x33f7d4
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntrieseAclA 1 0x33f788 (nil) 0x33f7d0
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntrieseAclA 1 0x33f7a8 (nil) 0x33f7f0
fixme:advapi:SetSecurityInfo stub
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d7d29f8, overlapped 0x7d7d29dc): stub
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdritializeThunk Main exe initialization for L"C:\\Programme\\Warcraft III\\war3.exe" failed, status c0000142
hauke ~ >

```

---

### Post by BashOrgRu on 2009-08-21
I solved this problem!! Copy warcraft from ntfs partition to ext3!!! Omg, stupid bug ((

---

