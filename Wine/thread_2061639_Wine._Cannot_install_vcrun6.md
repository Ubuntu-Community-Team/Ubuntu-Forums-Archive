---
title: "Wine. Cannot install vcrun6"
date: 2012-09-23
forum: Wine
---

### Post by ABOBA on 2012-09-23
Cannot install vcrun6. I tried to do it with winetricks and manually (download vcredist.exe and install), but nothing. Launching in terminal gives the following
  ```
_user@_user-machine:~$ WINEPREFIX="/home/_user/.wine" wine "C:/vcredist.exe" 
fixme:setupapi:SetupDefaultQueueCallbackW notification 262144 params 32f63c,0 
err:setupapi:SetupDefaultQueueCallbackW copy error 0 L"C:\\users\\_user\\Temp\\IXP000.TMP\\comcat.dll" -> L"C:\\windows\\system32\\comcat.dll"
fixme:setupapi:SetupDefaultQueueCallbackW notification 262144 params 32f63c,0 
err:setupapi:SetupDefaultQueueCallbackW copy error 0 L"C:\\users\\_user\\Temp\\IXP000.TMP\\msvcrt.dll" -> L"C:\\windows\\system32\\msvcrt.dll"
fixme:setupapi:SetupDefaultQueueCallbackW notification 262144 params 32f63c,0 
err:setupapi:SetupDefaultQueueCallbackW copy error 0 L"C:\\users\\_user\\Temp\\IXP000.TMP\\oleaut32.dll" -> L"C:\\windows\\system32\\oleaut32.dll"
fixme:setupapi:SetupDefaultQueueCallbackW notification 262144 params 32f63c,0 
err:setupapi:SetupDefaultQueueCallbackW copy error 0 L"C:\\users\\_user\\Temp\\IXP000.TMP\\olepro32.dll" -> L"C:\\windows\\system32\\olepro32.dll"
fixme:setupapi:SetupDefaultQueueCallbackW notification 262144 params 32f63c,0 
err:setupapi:SetupDefaultQueueCallbackW copy error 0 L"C:\\users\\_user\\Temp\\IXP000.TMP\\stdole2.tlb" -> L"C:\\windows\\system32\\stdole2.tlb"   
```
Distributive is Ubuntu Studio 12.04.1 64bit, wine1.4, (and i tried it with last wine 1.5, same results)

  Thanks in advance

---

### Post by cwwilson721 on 2012-09-23
Using winetricks, I had same issue.

Instead of plain old vcrun6, I installed vcrun6sp
```
env WINEPREFIX=/home/<USER>/<Whatever prefix you want> winetricks vcrun6sp6
```

Works perfect

---

### Post by ABOBA on 2012-09-23
OMG, It works! 
Great thanx))[-o<

---

