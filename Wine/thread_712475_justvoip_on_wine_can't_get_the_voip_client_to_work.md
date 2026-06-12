---
title: "justvoip on wine: can't get the voip client to work on wine"
date: 2008-03-01
forum: Wine
---

### Post by akuli on 2008-03-01
I tried to install and run justvoip under wine on my Ubuntu Gutsy.

But it says "The application crashed due to an unexpected event."
Here are the details of my wine version and the logs. Any inputs will be appreciated.

Version : 0.9.55   OS Version: Windows XP  Library overrides: none   Audio settings: OSS Driver   Graphics settings: "Allow the windows managet to control the windows"

m@m-pc:~/Desktop$ wine setupjustvoip.exe 
fixme:system:SetProcessDPIAware stub!
fixme:system:SetProcessDPIAware stub!
fixme:reg:GetNativeSystemInfo (0x34fea0) using GetSystemInfo()
fixmerocess:IsWow64Process (0xffffffff 0x34fe9c) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x131da0 0x34fe1c) stub!
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Program Files\\JustVoip.com\\JustVoip\\unins000.exe") stub
fixme:shell:IPersistFile_fnGetCurFile (0x157490)
fixme:shell:IPersistFile_fnGetCurFile (0x157490)
fixme:shell:IPersistFile_fnGetCurFile (0x157490)
fixme:shellllCanUnloadNow stub
fixme:shellllCanUnloadNow stub
fixme:shellllCanUnloadNow stub
fixme:shellllCanUnloadNow stub
m@m-pc:~/Desktop$ errle:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
errle:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
errle:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
errle:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
fixmele:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
errle:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x17
errle:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded

---

### Post by Acunga on 2008-03-14
the same here :(

---

### Post by babuz' on 2008-03-22
no luck for me as well...

---

### Post by Stratok on 2008-07-17
looks like virtual box or vmware are the only options

---

