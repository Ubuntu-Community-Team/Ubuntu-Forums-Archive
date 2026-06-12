---
title: "Using Windows .dll-s with Wine"
date: 2008-06-15
forum: Wine
---

### Post by andriy.kostyuk on 2008-06-15
I tried to install a widows program under wine, but it does not work complaining that it does not find .dll files it needs.

I do have these *.dll files with these names on my windows partition. Can I copy these files from the windows partition to the Ubuntu one and make "wine" to use them?
Is there a HowTo about doing it?

Thanks in advance.

---

### Post by DJ_Peng on 2008-06-15
It's hard to suggest anything when you don't say what program it is you're trying to install. You can also check the [Wine Application Database]("http://appdb.winehq.org/") to see if there's any advice there for your specific program.

---

### Post by cogadh on 2008-06-15
Short answer (assuming the missing DLLs are in Windows system32 directory):[list=1]
[*]Copy the DLLs the application is looking for from the Windows drive to /home/<username>/.wine/drive_c/windows/system32
[*]Run winecfg, go to the Libraries tab and add an override for each DLL copied.[/list]
Thats' all there is to it.

If the DLLs are not in the Windows system32 directory, you usually just have to place them wherever the app is looking for them and you don't have to apply an override for them.

EDIT - Almost forgot, never override kernel32.dll, gdi32.dll, user32.dll or ntdll.dll. Doing so will break Wine.

---

### Post by itchanddino on 2008-07-11
Is there a way to use a native windows dll without overriding the wine one?  Thanks!

---

### Post by Prefix100 on 2008-07-11
Why isn't there a project that is like wine but requires that you have a windows license and uses ALL the windows library?

So it acts simply as a translator.

---

### Post by Drk Guy on 2008-07-11
It couldn't be GNU, and, as the Windows API is really obscure, dlls wouldn't  be called the way they workm i think that would be most of the issue

---

### Post by itchanddino on 2008-07-12
So you can't have the wine and the windows dlls coexist in the system32 folder?

---

### Post by Drk Guy on 2008-07-12
You can do it, but it is not encouraged unless you REALLY need to use them for a specific app...

---

