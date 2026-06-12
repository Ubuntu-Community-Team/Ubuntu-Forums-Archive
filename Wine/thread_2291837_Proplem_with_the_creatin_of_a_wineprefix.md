---
title: "Proplem with the creatin of a wineprefix"
date: 2015-08-23
forum: Wine
---

### Post by realnewbie2 on 2015-08-23
Hey guys,


i have a problem creating a new wineprefix on ubuntu 14.04 32-bit an i have  installed wine 1.6.2. i am running the command

WINEPREFIX=/media/vaggkall/FILES/games/.tera winecf

to create the wineprefix but, although the wineprefix root folder has been created, the creation of every other folders in this failed to be created
here is what the output of the command is in the first lines

wine: created the configuration directory '/media/vaggkall/FILES/games/tera'
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:wineboot:main Cannot set the dir to L"C:\\windows" (2)
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 2
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:setupapi:SetupDefaultQueueCallbackW copy error 2 L"\\\\?\\unix\\usr\\share\\wine\\l_intl.nls" -> L"C:\\windows\\system32\\l_intl.nls"
err:setupapi:SetupDefaultQueueCallbackW copy error 3 L"\\\\?\\unix\\usr\\share\\wine\\l_intl.nls" -> L"C:\\windows\\system32\\l_intl.nls"
err:setupapi:create_dest_file failed to create L"C:\\windows\\rundll.exe" (error=3)
err:setupapi:create_dest_file failed to create L"C:\\windows\\twain.dll" (error=3)
err:setupapi:create_dest_file failed to create L"C:\\windows\\twain_32.dll" (error=3)
err:setupapi:create_dest_file failed to create L"C:\\windows\\winhelp.exe" (error=3)
err:setupapi:create_dest_file failed to create L"C:\\windows\\winhlp32.exe" (error=3)
err:setupapi:create_dest_file failed to create L"C:\\windows\\command\\start.exe" (error=3)
err:setupapi:create_dest_file failed to create L"C:\\windows\\system\\ddeml.dll" (error=3)
err:setupapi:create_dest_file failed to create L"C:\\windows\\system\\mmsystem.dll" (error=3)
err:setupapi:create_dest_file failed to create L"C:\\windows\\system32\\ddhelp.exe" (error=3)
err:setupapi:create_dest_file failed to create L"C:\\windows\\system32\\dosx.exe" (error=3)
err:setupapi:create_dest_file failed to create L"C:\\windows\\system32\\dsound.vxd" (error=3)
err:setupapi:create_dest_file failed to create L"C:\\windows\\system32\\winhlp32.exe" (error=3)
err:setupapi:create_dest_file failed to create L"C:\\windows\\explorer.exe" (error=3)
err:setupapi:create_dest_file failed to create L"C:\\windows\\hh.exe" (error=3)
err:setupapi:create_dest_file failed to create L"C:\\windows\\notepad.exe" (error=3)
err:setupapi:create_dest_file failed to create L"C:\\windows\\regedit.exe" (error=3)
err:setupapi:create_dest_file failed to create L"C:\\windows\\system32\\explorer.exe" (error=3)
err:setupapi:create_dest_file failed to create L"C:\\windows\\system32\\iexplore.exe" (error=3)
err:setupapi:create_dest_file failed to create L"C:\\windows\\system32\\notepad.exe" (error=3)
err:setupapi:create_dest_file failed to create L"C:\\windows\\system32\\winetest.exe" (error=3)
err:setupapi:create_dest_file failed to create L"C:\\windows\\system32\\drivers\\mountmgr.sys" (error=3)

thank u for the help

---

