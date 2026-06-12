---
title: "Fail to install any programs in wine"
date: 2008-09-16
forum: Wine
---

### Post by Rufusz on 2008-09-16
I am having difficulties installing any programs in wine. Have tried to install a few programs but all crash during install.

In the terminal it looks like:
```
root@ru-laptop:/media/cdrom0# wine setup.exe
wine: created the configuration directory '/root/.wine'
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Could not load Mozilla. HTML rendering will be disabled.
wine: configuration in '/root/.wine' has been updated.
fixme:advapi:LookupAccountNameW (null) L"root" (nil) 0x33f7fc (nil) 0x33f800 0x33f7f4 - stub
fixme:advapi:LookupAccountNameW (null) L"root" 0x12d5a0 0x33f7fc 0x12d500 0x33f800 0x33f7f4 - stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 1 ignored L"Upgrade" table values
err:ole:CoGetClassObject class {88d96a05-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d96a05-f192-11d4-a65f-0040963251e5} could be created for context 0x1
err:ole:CoGetClassObject class {88d969c0-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d969c0-f192-11d4-a65f-0040963251e5} could be created for context 0x1
fixme:msxml:DllCanUnloadNow 
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:msi_unimplemented_action_stub RemoveRegistryValues -> 10 ignored L"RemoveRegistry" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 2 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 7 ignored L"CreateFolder" table values
err:ole:CoGetClassObject class {88d96a05-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d96a05-f192-11d4-a65f-0040963251e5} could be created for context 0x1
err:ole:CoGetClassObject class {88d969c0-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d969c0-f192-11d4-a65f-0040963251e5} could be created for context 0x1
fixme:msxml:domdoc_createNode unhandled node type 2
fixme:msxml:DllCanUnloadNow 
err:msi:custom_get_thread_return Invalid Return Code -2302
err:msi:ITERATE_Actions Execution halted, action L"InstallExecute" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603

```

It still copies some files at the installation directory, but most of them are missing. In some cases even the start menu items in wine are created but not working.
Any ideas what can be the problem?

---

### Post by aoanla on 2008-09-17
Well, for a start, why the heck are you installing programs in wine as root?

---

### Post by jacksaff on 2008-09-17
As said above, you are running wine as root which is absolutely not recommended.
Apart from security problems and the fact that running as root wine can now write to ALL files and so hose your system, it also means that any apps you install will be in root's .wine folder and fake windows directory and not yours. If you then try and run the apps as a normal user the files won't be in the right place.
I would remove the .wine files in both root's and your home directories and then remove and reinstall wine if you've been mucking about with it as root.
Install programs using wine as a normal user.

---

### Post by Rufusz on 2008-09-17
First time I tried from my own login several times then I gave it a go from root to see if it works.
Normally I try to avoid installing anything as root.

I just tried to install an other program from my own login:
```
ru@ru-laptop:/media/share/ehh$ wine setup.exe
fixme:advapi:LookupAccountNameW (null) L"ru" (nil) 0x33f7fc (nil) 0x33f800 0x33f7f4 - stub
fixme:advapi:LookupAccountNameW (null) L"ru" 0x12ccb0 0x33f7fc 0x12e4b0 0x33f800 0x33f7f4 - stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 1 ignored L"Upgrade" table values
err:ole:CoGetClassObject class {88d96a05-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d96a05-f192-11d4-a65f-0040963251e5} could be created for context 0x1
err:ole:CoGetClassObject class {88d969c0-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d969c0-f192-11d4-a65f-0040963251e5} could be created for context 0x1
fixme:msxml:DllCanUnloadNow 
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 2 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 4 ignored L"CreateFolder" table values
err:ole:CoGetClassObject class {88d96a05-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d96a05-f192-11d4-a65f-0040963251e5} could be created for context 0x1
err:ole:CoGetClassObject class {88d969c0-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d969c0-f192-11d4-a65f-0040963251e5} could be created for context 0x1
fixme:msxml:domdoc_createNode unhandled node type 2
fixme:msxml:DllCanUnloadNow 
err:msi:custom_get_thread_return Invalid Return Code -2302
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603

```

So still not working...

---

### Post by aoanla on 2008-09-17
Right.

So, what programs are you trying to install? Have you checked the Wine AppDB (link in one of the forum stickies) for any issues they may have?

---

### Post by Rufusz on 2008-09-17
Rosetta Stone and Tell Me More (an other language program). Yes I have checked the AppDB, and both programs should be ok according to that.

---

