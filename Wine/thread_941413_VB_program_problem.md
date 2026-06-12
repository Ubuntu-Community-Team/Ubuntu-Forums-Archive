---
title: "VB program problem"
date: 2008-10-08
forum: Wine
---

### Post by wkmok on 2008-10-08
I have a "small" vb program, that i want to run on the linux. But when I tried to running the above program, I got the following errors. 

err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:create_server class {ed8c108e-4349-11d2-91a4-00c04f7969e8} not registered
err:ole:CoGetClassObject no class object {ed8c108e-4349-11d2-91a4-00c04f7969e8} could be created for context 0x5

Please advise as detail as you can, it is because this is my first time to use wine and linux. Please help me. Thanks a lot 

wkmok

---

### Post by Johansen8 on 2008-10-08
hmm have you tried re-installing it?

---

### Post by wkmok on 2008-10-08
Dear Johansen8

Thanks your reply, you means re-install wine. If yes, that I re-install many times. If you means re-install vb program, I had also done that. Please help me to solve. Thanks

wkmok

---

### Post by Orange_and_Green on 2008-10-08
Dear wkmok,

Download [this script]("http://www.kegel.com/wine/winetricks"), make it executable (Right click->Properties->Permissions), run it, and install the support for the VB version you need.

Good luck :KS

---

### Post by wkmok on 2008-10-14
Hello anyone

Please help me to solve the problem, up to now I cannot solve it

I have the VB Program, I think the error is occur here when the program running

the code is as following 
set xmlserverhttp = createobject("microsoft.xmlhttp")
xmlserverhttp.open ...
xmlserverhttp.setrequestheader ....
xmlserverhttp.send

After running, I get the following error
fixme:msxml:httprequest_QueryInterface Unsupported interface {7fd52380-4e07-101b-ae2d-08002b2ec713}
fixme:msxml:httprequest_QueryInterface Unsupported interface {37d84f60-42cb-11ce-8135-00aa004bb851}
fixme:msxml:httprequest_open stub (0x12dd68)
fixme:msxml:httprequest_setRequestHeader stub (0x12dd68) L"Content-Type" L"application/x-www-form-urlencoded"
fixme:msxml:httprequest_send stub (0x12dd68)

However, I tried to changed the code to as following
set xmlserverhttp = createobject("msxml2.serverxmlhttp.3.0")
xmlserverhttp.open ...
xmlserverhttp.setrequestheader ....
xmlserverhttp.send

After running, I get the other error, like as following
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:create_server class {f5078f35-c551-11d3-89b9-0000f81fe221} not registered
err:ole:CoGetClassObject no class object {f5078f35-c551-11d3-89b9-0000f81fe221} could be created for context 0x5

Please advise as detail as you can, how to solve it? 

Thanks

wkmok

---

### Post by wkmok on 2008-10-14
Hello anyone

I tried to provide more information for your reference. The following message was got from when I install msxml3 by winetricks

Executing wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://download.microsoft.com/download/8/8/8/888f34b7-4f54-4f06-8dac-fa29b19f33dd/msxml3.msi](http://download.microsoft.com/download/8/8/8/888f34b7-4f54-4f06-8dac-fa29b19f33dd/msxml3.msi)
--16:52:05--  [http://download.microsoft.com/download/8/8/8/888f34b7-4f54-4f06-8dac-fa29b19f33dd/msxml3.msi](http://download.microsoft.com/download/8/8/8/888f34b7-4f54-4f06-8dac-fa29b19f33dd/msxml3.msi)
           => `msxml3.msi'
Resolving download.microsoft.com... 63.150.131.181, 63.150.131.180
Connecting to download.microsoft.com|63.150.131.181|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,070,592 (1.0M) [application/octet-stream]

100%[====================================>] 1,070,592    187.20K/s    ETA 00:00

16:52:14 (164.42 KB/s) - `msxml3.msi' saved [1070592/1070592]

Using native,builtin override for following DLLs: msxml3
Executing wine regedit /home/bestel/.wine/drive_c/winetrickstmp/override-dll.reg
Executing wine msiexec /i /home/bestel/.winetrickscache/msxml3.msi
fixme:advapi:LookupAccountNameW (null) L"bestel" (nil) 0x32f7fc (nil) 0x32f800 0x32f7f4 - stub
fixme:advapi:LookupAccountNameW (null) L"bestel" 0x14bb80 0x32f7fc 0x12d008 0x32f800 0x32f7f4 - stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 2 ignored L"Upgrade" table values
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 2 ignored L"Upgrade" table values
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:setupapi:SetupCopyOEMInfW install catalog file L"C:\\Program Files\\Common Files\\Microsoft Shared\\SFPCA Cache\\msxmlx.cat"
fixme:setupapi:SetupQueryInfOriginalFileInformationW (0x1aebf8, 0, (nil), 0x7e212fb8): semi-stub
fixme:setupapi:SetupPromptReboot 0x1ab568, (nil), 1
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 2 ignored L"Upgrade" table values
Install of msxml3 done
winetricks done.


Thanks very much

wkmok

---

