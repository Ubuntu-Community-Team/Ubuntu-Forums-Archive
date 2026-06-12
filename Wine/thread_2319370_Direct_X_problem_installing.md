---
title: "Direct X problem installing"
date: 2016-04-03
forum: Wine
---

### Post by dvlnchrs on 2016-04-03
While following this thread:

 [http://www.dedoimedo.com/games/wine-directx.html](http://www.dedoimedo.com/games/wine-directx.html)

I got to the part asking you to test DirectX 9.0c and tried the command (in terminal):

wine ~/.wine/drive_c/windows/system32/dxdiag.exe

Received this report:

err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\dxdiagn.dll"
err:ole:CoGetClassObject no class object {a65b8071-3bfe-4213-9a5b-491da4461ca7} could be created for context 0x1
err:dxdiag:collect_dxdiag_information IDxDiagProvider instance creation failed with 0x80070005
err:dxdiag:wWinMain DxDiag information collection failed

Seems to be a missing dll?

Any help appreciated. Or a redirect to relevant thread.

Thanks for reading

P.S. The smileys shouldn't be there...should both be (err: ole) minus the space

---

