---
title: "MSSQL Access and WINE"
date: 2008-01-17
forum: Wine
---

### Post by onegreenparker on 2008-01-17
I need to run a Windows application from my Ubuntu box, I can run the application but when I need to connect to the MSSQL database, I get the following:

```

err:ole:CoGetClassObject class {ecabb0c0-7f19-11d2-978e-0000f8757e2a} not registered
err:ole:CoGetClassObject no class object {ecabb0c0-7f19-11d2-978e-0000f8757e2a} could be created for context 0x1

```

as well as:

```

OLE error80004005

```

I am using WINE 0.9.53, installed I have MySQL Connector/ODBC 3.51. overides are odbc32 and odbccp32.

---

### Post by hikaricore on 2008-01-17
> **onegreenparker said:**
> I need to run a Windows application from my Ubuntu box, I can run the application but when I need to connect to the** MSSQL** database, I get the following:

```

err:ole:CoGetClassObject class {ecabb0c0-7f19-11d2-978e-0000f8757e2a} not registered
err:ole:CoGetClassObject no class object {ecabb0c0-7f19-11d2-978e-0000f8757e2a} could be created for context 0x1

```

as well as:

```

OLE error80004005

```

I am using WINE 0.9.53, installed I have **MySQL** Connector/ODBC 3.51. overides are odbc32 and odbccp32.


Let me get this straight.

You're trying to connect to a **My**SQL database with an **MS**SQL application?

I'm a bit confused to say the least.  As far as the WINE Application Database, this is all I could find: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1032](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1032)
Doesn't look promising if this is the same software.  You may need to consider running a VM.

---

### Post by onegreenparker on 2008-01-17
No, I am trying to connect to the MSSQL db from a MSSQL app.
I tried MySQL method on the off chance that it might work, but I get the exact same errors with or without the MySQL Connector.

---

### Post by onegreenparker on 2008-01-21
My searches lead me to the same WINE page.....
I'm avoiding a VM as far as I can, so that will be a last resort.

Any other ideas before I go down VM Street

EDIT: Can't install VMWare anyway,  Add/Remove tells me that "VMware Player cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."

---

### Post by onegreenparker on 2008-01-21
A little more info...


Debug info:
```

cl1-poc@cl1-poc:~/CFL$ wineboot
cl1-poc@cl1-poc:~/CFL$ WINEDEBUG=+loaddll wine autorun.exetrace:loaddll:load_builtin_dll Loaded L"KERNEL32.dll" at 0x7b820000: builtin
trace:loaddll:load_builtin_dll Loaded L"KERNEL32.dll" at 0x7b820000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\wineboot.exe" at 0x7ee70000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\advapi32.dll" at 0x7eb00000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\gdi32.dll" at 0x7eb50000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\user32.dll" at 0x7ebf0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\shlwapi.dll" at 0x7ed10000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\comctl32.dll" at 0x7ea40000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\shell32.dll" at 0x7ed70000: builtin
trace:loaddll:load_native_dll Loaded L"Z:\\home\\cl1-poc\\CFL\\autorun.exe" at 0x400000: native
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\lz32.dll" at 0x7ea10000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\version.dll" at 0x7ea20000: builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "krnl386.exe" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module " system.drv" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "gdi.exe" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "user.exe" : builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\winex11.drv" at 0x7e860000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\imm32.dll" at 0x7c630000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\uxtheme.dll" at 0x7c5f0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\iphlpapi.dll" at 0x7c4b0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\rpcrt4.dll" at 0x7c4e0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\ole32.dll" at 0x7c540000: builtin
trace:loaddll:load_builtin_dll Loaded L"KERNEL32.dll" at 0x7b820000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\winedevice.exe" at 0x7ee60000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\advapi32.dll" at 0x7ee20000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\ntoskrnl.exe" at 0x7edf0000: builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "krnl386.exe" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "system.drv " : builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\msvcrt.dll" at 0x7eb70000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\mountmgr.sys" at 0x7eb50000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\advapi32.dll" at 0x7ec80000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\gdi32.dll" at 0x7ecc0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\user32.dll" at 0x7ed60000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\iphlpapi.dll" at 0x7eab0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\rpcrt4.dll" at 0x7eae0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\ole32.dll" at 0x7eb40000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\oleaut32.dll" at 0x7ebe0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\lz32.dll" at 0x7ea70000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\version.dll" at 0x7ea80000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\comctl32.dll" at 0x7e9b0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\winspool.drv" at 0x7e980000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\shlwapi.dll" at 0x7e820000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\shell32.dll" at 0x7e880000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\ws2_32.dll" at 0x7e7e0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\wsock32.dll" at 0x7e800000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\netapi32.dll" at 0x7e7b0000: builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "krnl386.exe" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "system.drv " : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "gdi.exe" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "user.exe" : builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\winex11.drv" at 0x7e600000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\imm32.dll" at 0x7c3d0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\uxtheme.dll" at 0x7c3a0000: builtin
trace:loaddll:load_builtin_dll Loaded L"KERNEL32.dll" at 0x7b820000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\explorer.exe" at 0x7ee70000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\advapi32.dll" at 0x7eda0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\iphlpapi.dll" at 0x7edf0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\rpcrt4.dll" at 0x7ee10000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\gdi32.dll" at 0x7ebd0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\user32.dll" at 0x7ec70000: builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "krnl386.exe" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module " system.drv" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "gdi.exe" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "user.exe" : builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\winex11.drv" at 0x7ea20000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\imm32.dll" at 0x7c7f0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\msvcrt.dll" at 0x7bbb0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\comdlg32.dll" at 0x7bb00000: builtin
trace:loaddll:load_native_dll Loaded L"C:\\windows\\system32\\MSDART.DLL" at 0x1f660000: native
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\Common files\\System\\ADO\\msado15.dll" at 0x1f430000: native
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\Common Files\\System\\OLE DB\\oledb32.dll" at 0x1f8a0000: native
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\Common Files\\System\\OLE DB\\OLEDB32R.DLL" at 0x1f910000: native
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\Common Files\\System\\OLE DB\\MSDATL3.dll" at 0x3b0000: native
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\Common Files\\System\\OLE DB\\sqloledb.dll" at 0x75370000: native
err:ole:CoGetClassObject class {ecabb0c0-7f19-11d2-978e-0000f8757e2a} not registered
err:ole:CoGetClassObject no class object {ecabb0c0-7f19-11d2-978e-0000f8757e2a} could be created for context 0x1
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\Common files\\System\\ADO\\msader15.dll" at 0x1f420000: native
trace:loaddll:free_modref Unloaded module L"C:\\Program Files\\Common files\\System\\ADO\\msader15.dll" : native
trace:loaddll:free_modref Unloaded module L"C:\\Program Files\\Common files\\System\\ADO\\msado15.dll" : native
trace:loaddll:free_modref Unloaded module L"C:\\Program Files\\Common Files\\System\\OLE DB\\sqloledb.dll" : native
trace:loaddll:free_modref Unloaded module L"C:\\Program Files\\Common Files\\System\\OLE DB\\MSDATL3.dll" : native

```

when I try to register msado32.dll (where I suspect the errors start):

```

Successfully registered DLL C:\Program Files\Common files\System\ADO\msado15.dll
DllInstall not implemented in DLL C:\Program Files\Common files\System\ADO\msado15.dll

```

and the same debug info is generated.

---

### Post by onegreenparker on 2008-01-28
Apparently I was on the wrong track altogether....

The actual problem was not being able to 'read' the database correctly. This is because OLE DB is not implemented in WINE, ODBC is, unfortunately the application I want to use was optimized to use OLE DB. 

In order to get my app working under WINE, we will need to rewrite some code.  :(  

A pity, but at least I've learned from the experience.....

---

