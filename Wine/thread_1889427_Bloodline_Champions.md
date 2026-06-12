---
title: "Bloodline Champions"
date: 2011-12-01
forum: Wine
---

### Post by killra on 2011-12-01
Well u have been trying to get it to work sometime now. But i stopped making progress so I'll ask for help.

First i just tested to install it in wine beta release. Didn't work so i checked  a little on winehq and found this [http://appdb.winehq.org/objectManager.php?sClass=version&iId=23809](http://appdb.winehq.org/objectManager.php?sClass=version&iId=23809).

I tried to install dotnet30 and dotnet35 didn't work reinstalled wine still didn't work installed it on a different computer and moved the windows folder to my main computer after reinstalling wine again. 
 
After that i started the loader and it asked me to install dotnet35 sp1 so i tried but it 
failed.

The .NET Runtime Optimization Service is started and paused.
fixme:clusapi:GetNodeClusterState ((null),0x33ec34) stub!
fixme:advapi: DecryptFileA "c:\\56058e82940ca4606a35e2b9cbffc7\\" 00000000
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme: ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:advapi:LsaOpenPolicy ((null),0x33efa8,0x00000001,0x33efc0) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LsaOpenPolicy ((null),0x33e62c,0x00000001,0x33e644) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d0c00 (device=2d access=0 func=300 method=0)
fixme:advapi:LsaOpenPolicy ((null),0x33dd98,0x00000001,0x33ddb0) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:msi:MsiGetFeatureValidStatesW 1 L"NetFX_LangPack_x86_ptg_DDF" 0x33a978 stub returning 8
fixme:msi:MsiGetFeatureValidStatesW 1 L"CSharp_x86_ptg_DDF" 0x339ed8 stub returning 8
fixme:msi:MsiGetFeatureValidStatesW 1 L"NetFX35_EXP_ptg_x86_net_SETUP" 0x33a978 stub returning 8
fixme:msi:MsiGetFeatureValidStatesW 1 L"Servicing_Key" 0x33a978 stub returning 8
fixme:msi:MsiGetFeatureValidStatesW 1 L"NETFXM_Only_Feature_LP" 0x33a978 stub returning 8
fixme:msi:MsiGetFeatureValidStatesW 1 L"Cartman_Required_SystemFolder" 0x33a978 stub returning 8
fixme:msi:MsiGetFeatureValidStatesW 1 L"CDFGREEN_CA_x86_ptg_DDF" 0x33a978 stub returning 8
fixme:msi:determine_patch_sequence patch ordering not supported
fixme:msi:determine_patch_sequence patch ordering not supported
fixme:msi:determine_patch_sequence patch ordering not supported
fixme:msi:determine_patch_sequence patch ordering not supported
fixme:msi:determine_patch_sequence patch ordering not supported
err:msi:ITERATE_Actions Execution halted, action L"CA_BlockNetFX20SP1_x86_ptg.3643236F_FC70_11D3_A536_0090278A1BB8" returned 1603
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is started and paused.
fixme:imm:ImmDisableIME (-1): stub
err: ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err: ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
err: ole:CoUninitialize Mismatched CoUninitialize
err: ole:CoUninitialize Mismatched CoUninitialize
fixme: ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err: ole:CoRevokeClassObject called from wrong apartment, should be called from 2600000027
Microsoft (R) CLR Native Image Generator - Version 2.0.50727.42
Copyright (C) Microsoft Corporation 1998-2002. All rights reserved.

The .NET Runtime Optimization Service is running.

Please help :(

---

### Post by killra on 2011-12-04
guess not

---

