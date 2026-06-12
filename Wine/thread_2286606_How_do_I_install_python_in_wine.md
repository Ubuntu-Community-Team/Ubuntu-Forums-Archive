---
title: "How do I install python in wine?"
date: 2015-07-13
forum: Wine
---

### Post by Robbyx on 2015-07-13
I have tried  clicking on it using the wine wondows program loader and nothing appeared on the screen.

Should I use winetricks instead  to install python on Wine?  I have downloaded python-3.5.0b3.exe. I have run winetricks python-3.5.0b3.exe in the terminal and it reports Unknown arg python-3.5.0b3.exe.

I am running 
Ubuntu 14.04 AMD 64.  
Wine 1:1.7.44-0ubuntu1
Winetricks: 0.0+20140302-0ubuntu2

---

### Post by CitadelUniversal on 2015-07-13
Hi Robbyx, have you opened up the gnome-terminal and typed the command wine along with the link to the windows software? so it should read something like "wine '<program link>' and then enter....

---

### Post by Robbyx on 2015-07-13
I tried your suggestion. This is what  I get:

robins@robins-desktop:~/Desktop$ wine python3.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:ntdll:NtQueryInformationToken QueryInformationToken( ..., TokenElevation, ...) semi-stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:ntdll:NtQueryInformationToken QueryInformationToken( ..., TokenElevation, ...) semi-stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:advapi:DecryptFileW (L"C:\\users\\robins\\Temp\\{8e60ea0f-d310-4ea6-be0c-bc8e7a6879c4}\\", 00000000): stub

---

### Post by CitadelUniversal on 2015-07-13
What about 
[I]wine msiexec /i python-X.x.x.msi
[/I]The .x should be the version[I]...
[/I]

---

### Post by Robbyx on 2015-07-13
I am not sure if I am trying to install the right version. My Ubuntu system is 64bit but I am installing python into wine. Assuming it is right this is what I get:

> robins@robins-desktop:~/Desktop$ wine msiexec /i python-2.7.10.amd64.msi 
fixme:storage:create_storagefile Storage share mode not implemented.
robins@robins-desktop:~/Desktop$ 


What is storage share mode in this context?

---

### Post by CitadelUniversal on 2015-07-14
It sounds like you've downloaded the wrong python version if you have downloaded the python x86 version, and have not set the wine software to 32-bit - it'll default to the 64-bit wine, please download [https://www.python.org/downloads/release/python-2710/](https://www.python.org/downloads/release/python-2710/) again and use x86-64 msi version if your's is set to 64-bit wine...

---

### Post by Robbyx on 2015-07-14
Thank you. I did the following:

robins@robins-desktop:~$ wine msiexec /i python-2.7.10.msi
robins@robins-desktop:~$ 

No messages followed the command line. I am wondering how to check if it worked. Python in the terminal activates  the ubuntu version.

---

