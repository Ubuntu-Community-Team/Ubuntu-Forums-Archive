---
title: "wine error: asr3234.dll"
date: 2007-08-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by bosscar on 2007-08-20
wine "C:\Program Files\eLanguage\Learn To Speak Spanish\LSSE95.exe"
**err:module:import_dll Library[COLOR="Red"] ASR3234.DLL[/COLOR] (which is needed by L"C:\\Program Files\\eLanguage\\Learn To Speak Spanish\\LSSE95.exe") not found**
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\eLanguage\\Learn To Speak Spanish\\LSSE95.exe" failed, status c0000135

What the reason for this error?  How can I fix this?

Thanks, B

---

### Post by kostkon on 2007-08-20
It looks like that you are missing a DLL file. *Wine* does not come with this specific DLL file, I suppose.

Now, what you can do to solve the problem. First of all, you could search the source of your application, I mean the CD or the site, in general from where you got it, to see if you can find the DLL there.

Another option is to search in Google for this, but I don't know how safe that is. There are some sites that offer collections of DLL files to download for free. You have to be sure that you are getting it from a safe source.

Also, if you have a Windows machine, try to search for this file in your drive.

In any case, if you find the file, try copying it to the *system32* folder of the Wine *windows* folder. That is
```
./wine/drive_c/windows/system32
```
Another option would be to copy it to your application's folder.

There is a possibility of version mismatch; your may find the file, but maybe there would be a case where your application will ask for a different version of the DLL, and it will refuse to work. Thus, it is not going to be a sure success even if you manage to find the file somewhere.

---

