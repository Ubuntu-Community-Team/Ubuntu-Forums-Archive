---
title: "Dreamweaver 8 + Wine + 64Bits 8.04"
date: 2008-05-19
forum: x86 64-bit Users
---

### Post by Celingest on 2008-05-19
Hi friends,

Maybe im asking something solved already, but im not able to find a clear solution.

I have a problem running Dreamweaver 8 using wine on a 64Bits Ubuntu, had it solved on a 32Bits which is running it without problems.

This is the error i got when i tried to run it:

err:module:attach_process_dlls "**odbc32.dll**" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Macromedia\\Dreamweaver 8\\Dreamweaver.exe" failed, status c0000005

I saw some workarounds telling me to move DLL or Disable it but i can't see clear what to do.

Thanx in advance for your time,

---

### Post by Kilz on 2008-05-19
> **Celingest said:**
> Hi friends,

Maybe im asking something solved already, but im not able to find a clear solution.

I have a problem running Dreamweaver 8 using wine on a 64Bits Ubuntu, had it solved on a 32Bits which is running it without problems.

This is the error i got when i tried to run it:

err:module:attach_process_dlls "**odbc32.dll**" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Macromedia\\Dreamweaver 8\\Dreamweaver.exe" failed, status c0000005

I saw some workarounds telling me to move DLL or Disable it but i can't see clear what to do.

Thanx in advance for your time,

A simple forum search for the error [turned up this post]("http://ubuntuforums.org/showthread.php?t=753649&highlight=odbc32.dll"), there were only 6 results. Take a look at post 10.

---

### Post by Celingest on 2008-05-20
Thanx, im gonna try again, that's the post i saw before but i dont know where is obdcint.dll ?

---

### Post by Celingest on 2008-05-20
> **Celingest said:**
> Thanx, im gonna try again, that's the post i saw before but i dont know where is obdcint.dll ?

Just solved, moving odbc32.dll from my old-windows-no-more to the system32 directory of wine, then overriding it from configuration to force use it instead of builtin one of wine.

Thx

---

### Post by TechZilla on 2009-06-13
I was able to get it working w/ wine 1.0

but i had to get these 2 dlls, and make them load as native.
 
ODBC32.DLL 
odbcint.dll

---

