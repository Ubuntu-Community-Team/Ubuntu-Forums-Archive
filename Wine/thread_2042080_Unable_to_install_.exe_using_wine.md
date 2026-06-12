---
title: "Unable to install .exe using wine"
date: 2012-08-13
forum: Wine
---

### Post by spatel88 on 2012-08-13
This is the message I get when I attempt to install the .exe:

shetal@shetal:~$ wine /home/shetal/Desktop/NetworkSetupTool.exe 
wine: Install Mono for Windows to run .NET 2.0 applications.
shetal@shetal:~$

So I installed Mono Complete since I am using Ubuntu 12.04.  After this I am not sure how to get the application to install.  I am an amateur at using Ubuntu, so I appreciate all the help I can get.

I tried typing mono /path/to/file.exe instead of wine but it gave me this message:

Unhandled Exception: System.TypeLoadException: Could not load type 'NetworkSetupTool.NetworkSetupTool' from assembly 'NetworkSetupTool, Version=0.7.4.2, Culture=neutral, PublicKeyToken=null'.
[ERROR] FATAL UNHANDLED EXCEPTION: System.TypeLoadException: Could not load type 'NetworkSetupTool.NetworkSetupTool' from assembly 'NetworkSetupTool, Version=0.7.4.2, Culture=neutral, PublicKeyToken=null'.

This program is vital for me to be able to use my computer at school, so I would LOVE a solution if there is one.

---

### Post by sienile on 2012-08-13
Have you tried installing .NET with winetricks?

---

### Post by directhex on 2012-08-14
> **spatel88 said:**
> This is the message I get when I attempt to install the .exe:

shetal@shetal:~$ wine /home/shetal/Desktop/NetworkSetupTool.exe 
wine: **Install Mono for Windows** to run .NET 2.0 applications.
shetal@shetal:~$

So I installed Mono Complete since I am using Ubuntu 12.04.  After this I am not sure how to get the application to install.  I am an amateur at using Ubuntu, so I appreciate all the help I can get.

I tried typing mono /path/to/file.exe instead of wine but it gave me this message:

Mono for Windows, not Mono for Linux.

Download and install Mono for Windows from mono-project.com, run with "wine c:\program files (x86)\Mono\bin\mono.exe myapp.exe" or equivalent.

---

### Post by oldos2er on 2012-08-14
Moved to Wine.

---

