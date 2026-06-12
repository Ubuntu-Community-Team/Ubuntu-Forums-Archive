---
title: "Curse Client Won't Install"
date: 2015-10-16
forum: Wine
---

### Post by lkYHlakj^61 on 2015-10-16
I'm trying to install curse client. When I start the the downloaded setup.exe file, .Net installation gets to 11% and then throws:

```
An error occured while installing system components for CurseClient.
Setup cannot continue until all system components have been successfully installed.
```
Details>>>
```
Component .NET Framework Client Profile has failed to install with the following error message:"Installation failure. "


The following components failed to install:
- .NET Framework Client Profile


See the setup log file located at 'C:\users\USERNAME\Temp\VSDc43.tmp\install.log' for more information.
```

How can I get around this?

---

### Post by lkYHlakj^61 on 2015-10-17
Okay, I've managed to get past this point by installing IE8 .Net2 and .Net packages through winetricks.

Now when I try to run the installer, it starts by trying to install a .net client profile, but then quickly exits and opens IE with ```
 http://clientupdate-v5.curse.com/CurseClient.application 
``` in the address bar.

I'm going to remove .Net2 and replace it with .Net4.5 to see if that does anything.

---

