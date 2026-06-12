---
title: "Dotnet 2.0 Issues"
date: 2015-08-05
forum: Wine
---

### Post by persontheguy123 on 2015-08-05
[B]I'm fairly new to linux and this is my first post here so please let me know if I'm doing something wrong.

[/B]Running Ubuntu 14.04
Wine version: 1.6.2

Whenever I try to install Dotnet 2.0 using winetricks I get the following output:
```

------------------------------------------------------
Executing w_do_call dotnet20
Executing load_dotnet20
Executing w_do_call remove_mono
Executing load_remove_mono
------------------------------------------------------
Mono does not appear to be installed.
------------------------------------------------------
Executing w_do_call fontfix
Executing load_fontfix
Setting Windows version to win2k
Executing winetricks_early_wine regedit C:\windows\Temp\_dotnet20\set-winver.reg
Current wine does not have wine bug 30845, so not applying workaround
Executing wine dotnetfx.exe
err:winediag:xrandr12_init_modes Broken NVIDIA RandR detected, falling back to RandR 1.0. Please consider using the Nouveau driver instead.
fixme:advapi:DecryptFileA ("C:\\users\\jai\\Temp\\IXP000.TMP\\", 00000000): stub
err:winediag:xrandr12_init_modes Broken NVIDIA RandR detected, falling back to RandR 1.0. Please consider using the Nouveau driver instead.
err:secur32:SECUR32_initSchannelSP TLS library not found, SSL connections will fail
fixme:advapi:LsaOpenPolicy ((null),0x33f2e4,0x00000001,0x33f2d0) stub
fixme:advapi:LsaClose (0xcafe) stub
err:msidb:get_tablecolumns column 1 out of range
err:msidb:get_tablecolumns column 2 out of range
------------------------------------------------------
Note: command 'wine dotnetfx.exe' returned status 84.  Aborting.
------------------------------------------------------
```


I don't know what most of this means, I also tried to switch from Nvidia driver 331.113 (nvidia-331) but it won't let me even after killing all programs. I have this error: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1401591](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1401591)
Although I wouldn't think that would be a problem for this because I've never had a problem with it before but I'm not sure.


[s]EDIT: I have no idea why emoticons appeared in the error and I don't know how to fix it.[/s]

---

### Post by ruzekle on 2015-08-05
It may be because you still have the broken driver. The user schlypel's suggested this solution in the bug report you posted. Did you already follow these steps?

> I found that the process of removing nvidia driver / returning to nouveau is prevented by a running service (nvidia-persistenced).
to get rid of the proprietary driver, do: "sudo kill <id of  process>" and then you can use the hardware driver dialog to return  to nouveau.
To find the id just do "ps -e | grep nvidia-persistenced"



---

### Post by persontheguy123 on 2015-08-06
I attempted that which resulted in my system attempting to restart, and after 3 hours I forced the power off and restarted it. It then booted up with driver 346.59 (nvidia-346) and from then I attempted to switch to the nouveau driver but it instead switched to nvidia331.113 and no longer even lets me try and change drivers. When I click apply it instantly switches the icon back to nvidia331.113 as if I had clicked "revert"

---

### Post by ruzekle on 2015-08-06
You might have to use your terminal for this. Here's a wiki with more information on troubleshooting: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

