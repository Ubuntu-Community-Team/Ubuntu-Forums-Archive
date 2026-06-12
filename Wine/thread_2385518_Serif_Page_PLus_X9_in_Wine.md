---
title: "Serif Page PLus X9 in Wine"
date: 2018-02-21
forum: Wine
---

### Post by david.bowers on 2018-02-21
Hello,
        I cannot get Serif Page Plus X9 to install in Ubuntu 16.04.3 LTS via Wine.

latest wine was installed this week and successfully installed another windows program via wine. I am getting the below issue currently.
[ATTACH=CONFIG]278609[/ATTACH]
dave@dave-X556UAK:~/Desktop/Serif$ wine ppx9.exe
0036:fixme:shell:IQueryAssociations_fnInit unsupported flags: 4
0036:fixme:shell:IQueryAssociations_fnGetString 00000004: unimplemented flags
0036:fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
0038:fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
0038:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x33e360, 0x33e370 0x33e364
0038:fixme:nls:get_dummy_preferred_ui_language (0x38 0x33e360 0x33e370 0x33e364) returning a dummy value (current locale)
0038:fixme:module:load_library unsupported flag(s) used (flags: 0x00000060)
0038:fixme:module:load_library unsupported flag(s) used (flags: 0x00000060)
0038:fixme:msi:event_spawn_wait_dialog doing nothing
0038:fixme:msi:event_spawn_wait_dialog doing nothing
0038:fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
0038:fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
0038:fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
0052:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x54af010, 0x54af020 0x54af014
0052:fixme:nls:get_dummy_preferred_ui_language (0x38 0x54af010 0x54af020 0x54af014) returning a dummy value (current locale)
0052:fixme:module:load_library unsupported flag(s) used (flags: 0x00000060)
0052:fixme:module:load_library unsupported flag(s) used (flags: 0x00000060)
0055:err:module:import_dll Library MFC42u.DLL (which is needed by L"C:\\Program Files (x86)\\Serif\\PagePlus\\X9\\Program\\subinacl.exe") not found
0055:err:module:attach_dlls Importing dlls for L"C:\\Program Files (x86)\\Serif\\PagePlus\\X9\\Program\\subinacl.exe" failed, status c0000135
0038:err:msi:execute_script Execution of script 1 halted; action L"[\"C:\\Program Files (x86)\\Serif\\PagePlus\\X9\\Program\\subinacl.exe\" /noverbose /keyreg HKEY_LOCAL_MACHINE\\SOFTWARE\\Serif\\Common\\Registration /GRANT=S-1-1-0=F<=>S-1-5-21-0-0-0-1000<=>{E66C777A-BF1A-4ECA-811F-9ED530C31FC4}]QtExecDefCommon" returned 1603
0038:err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
0038:fixme:msi:internal_ui_handler internal UI not implemented for message 0x0b000000 (UI level = 5)
0038:fixme:msi:internal_ui_handler internal UI not implemented for message 0x0b000000 (UI level = 5)
0038:err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603

Serif Page Plus says "setup wizard ended prematurely".[ATTACH=CONFIG]278608[/ATTACH]

---

