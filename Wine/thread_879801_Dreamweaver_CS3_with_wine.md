---
title: "Dreamweaver CS3 with wine"
date: 2008-08-04
forum: Wine
---

### Post by Bendude on 2008-08-04
Hello all, this is my first post and a troublesome one aswell.

Ive been using Ubuntu hardy heron for around 2months and now i like it more and more the final step for me to leave windows is to get dreamweaver cs3 working.

I have wine 1.0 installed
I did not do any configuration. Only tried the add app from winecfg

I followed these instructions
[http://noteearty.blogspot.com/2008/01/how-to-run-dreamweaver-cs3-in-ubuntu.html](http://noteearty.blogspot.com/2008/01/how-to-run-dreamweaver-cs3-in-ubuntu.html)

but when i run it in a terminal i just get heaps of errors all which mean nothing to me.

```
john@ubuntu-desktop:~/.wine/drive_c/Program Files/Adobe/Adobe Dreamweaver CS3$ wine Dreamweaver.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\xerces-c_2_6.dll") not found
err:module:import_dll Library xerces-c_2_6.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\AdobePSL.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\AdobePSL.dll") not found
err:module:import_dll Library AdobePSL.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Fireworks Library.dll") not found
err:module:import_dll Library Fireworks Library.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\CoreTypes.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\CoreTypes.dll") not found
err:module:import_dll Library CoreTypes.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\NetIO.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\NetIO.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\NetIO.dll") not found
err:module:import_dll Library NetIO.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\CoreTypes.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\CoreTypes.dll") not found
err:module:import_dll Library CoreTypes.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\LIBCURL.dll") not found
err:module:import_dll Library LIBCURL.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\ahclient.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\ahclient.dll") not found
err:module:import_dll Library ahclient.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\xerces-c_2_6.dll") not found
err:module:import_dll Library xerces-c_2_6.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Workspace.dll") not found
err:module:import_dll Library MFC80U.DLL (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Workspace.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Workspace.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Workspace.dll") not found
err:module:import_dll Library Workspace.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
err:module:import_dll Library MFC80U.DLL (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe" failed, status c0000135
john@ubuntu-desktop:~/.wine/drive_c/Program Files/Adobe/Adobe Dreamweaver CS3$ wine Dreamweaver.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\xerces-c_2_6.dll") not found
err:module:import_dll Library xerces-c_2_6.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\AdobePSL.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\AdobePSL.dll") not found
err:module:import_dll Library AdobePSL.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Fireworks Library.dll") not found
err:module:import_dll Library Fireworks Library.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\CoreTypes.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\CoreTypes.dll") not found
err:module:import_dll Library CoreTypes.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\NetIO.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\NetIO.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\NetIO.dll") not found
err:module:import_dll Library NetIO.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\CoreTypes.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\CoreTypes.dll") not found
err:module:import_dll Library CoreTypes.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\LIBCURL.dll") not found
err:module:import_dll Library LIBCURL.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\ahclient.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\ahclient.dll") not found
err:module:import_dll Library ahclient.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\xerces-c_2_6.dll") not found
err:module:import_dll Library xerces-c_2_6.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Workspace.dll") not found
err:module:import_dll Library MFC80U.DLL (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Workspace.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Workspace.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Workspace.dll") not found
err:module:import_dll Library Workspace.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
err:module:import_dll Library MFC80U.DLL (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe" failed, status c0000135
john@ubuntu-desktop:~/.wine/drive_c/Program Files/Adobe/Adobe Dreamweaver CS3$ 

```


I know this is a big ask but it would be very much appreciated if someone has some spare time to give me a few hints in the right direction.

Ben

---

### Post by RussianPhysicsGuy on 2008-08-04
Have you got Dreamweaver CS3 installed on your Windows partition? It looks like Wine just needs a bunch of dll files - you can find these in your system32 folder in Windows, and just copy them into the system32 folder on the Wine c:\ drive.

---

### Post by Bendude on 2008-08-04
Yes i have Dreamweaver installed and working under windows.

The instructions i followed did not mention copying files from system32 only windows, common files, program files, and application data.

I tried to find MSVCR80.dll file in windows but i couldn't.

Thanks for the reply

---

### Post by Bendude on 2008-08-04
maybe im getting somewhere you was right i found msvcr80.dll and now i only have this error

```
john@ubuntu-desktop:~/.wine/drive_c/Program Files/Adobe/Adobe Dreamweaver CS3$ wine Dreamweaver.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\AdobePSL.dll") not found
err:module:import_dll Library AdobePSL.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Fireworks Library.dll") not found
err:module:import_dll Library Fireworks Library.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\CoreTypes.dll") not found
err:module:import_dll Library CoreTypes.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\NetIO.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\NetIO.dll") not found
err:module:import_dll Library NetIO.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\CoreTypes.dll") not found
err:module:import_dll Library CoreTypes.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\ahclient.dll") not found
err:module:import_dll Library ahclient.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MFC80U.DLL (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Workspace.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Workspace.dll") not found
err:module:import_dll Library Workspace.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
err:module:import_dll Library MFC80U.DLL (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe" failed, status c0000135
john@ubuntu-desktop:~/.wine/drive_c/Program Files/Adobe/Adobe Dreamweaver CS3$ 



```

Will keep trying to find them dll files that might fix it

---

### Post by Seti on 2008-08-04
<troll>
all these WYSIWYG editors are a crutch, learn to code using vi. It will set you free.
</troll>

---

### Post by Bendude on 2008-08-04
I can code i dont use the wysiwyg part of dream weaver at all apart from to quickly view what things are looking like in the design stage.

The best features for me are the way it offers style properties, html properties and even php globals. Make life alot faster.

Maybe you could suggest some linux program with the same types of features that i could try. would be very helpful to me.

Anyways back to the problem

```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MFC80U.DLL (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Workspace.dll") not found
err:module:import_dll Library Workspace.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
err:module:import_dll Library MFC80U.DLL (which is needed by L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe" failed, status c0000135

```

This one i have no ideas about
```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"

```
i have searched for it and found the files but i have already copied them across into wine.

```
MFC80U.DLL
```

This file is also already in wine?

```
 Workspace.dll
```

this i can not find even on windows

```
LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe" failed, status c0000135
```

dont no about this one aswell??

Going to go google the error messages but will be staying online if anyone has some more suggestions.

---

### Post by Bendude on 2008-08-04
installing this got it to run

 [www.microsoft.com/downloads/thankyou.aspx?familyId=32bc1bee-a3f9-4c13-9c99-220b62a191ee&displayLang=en](www.microsoft.com/downloads/thankyou.aspx?familyId=32bc1bee-a3f9-4c13-9c99-220b62a191ee&displayLang=en)

but still i cant get past the agreement section its just frozen

---

### Post by Bendude on 2008-08-04
solved had to use a crack to get past the licenseing part

---

