---
title: "Steam crashes under PlayOnLinux"
date: 2017-07-11
forum: Wine
---

### Post by gleedadswell on 2017-07-11
Hi everyone,

Native linux Steam runs just fine on my machine, but I have some windows only games in Steam so I'd like to try running Steam through PlayOnLinux.  I have installed a recent version (4.2.11) of PlayOnLinux using the PPA.  Steam successfully installs under it.  But it crashes when I try to run it.  On a fresh Steam install it downloads and installs Steam updates before crashing.  I have installed several versions of Wine under PlayOnLinux using the wine version manager and Steam crashes under every version I've tried.  I've also tried running with different Windows versions under the Wine configuration.  This changes the error log output, but it still crashes.  Some details:

My hardware:
HP Pavilion Laptop (I know that doesn't really mean much...)
Processor: AMD A10-5745M APU with Radeon(tm) HD Graphics × 4
Graphics: AMD Radeon R7 M260 (I know...yuck...)
64-bit

Ubuntu version: 14.04
```
geoff@kinetic-kubo:~$ uname -a
Linux kinetic-kubo 3.16.0-77-generic #99~14.04.1-Ubuntu SMP Tue Jun 28 19:17:10 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

Note: For some time the system has been telling me of an updated graphics stack to support the Radeon hardware.  In a previous installation of Ubuntu using that graphics stack I found that the computer would persistently overheat.  So I have not installed the updated graphics stack.

Here is the debug output from PlayOnLinux when I try to run Steam using wine-2.9-staging and WindowsXP:


```
[07/11/17 15:12:10] - Running wine-2.9-staging Steam.exe (Working directory : /home/geoff/.PlayOnLinux/wineprefix/Steam/drive_c/Program Files/Steam)
fixme:winediag:start_process Wine Staging 2.9 is a testing version containing experimental patches.
fixme:winediag:start_process Please mention your exact version when filing bug reports on winehq.org.
err:module:load_builtin_dll failed to load .so lib for builtin L"winebus.sys": libudev.so.0: cannot open shared object file: No such file or directory
err:winedevice:async_create_driver failed to create driver L"WineBus": c0000142
fixme:ver:GetCurrentPackageId (0x33e450 (nil)): stub
fixme:ntdll:EtwEventRegister ({47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f006760, 0x3f041d28, 0x3f041d20) stub.
fixme:ntdll:EtwEventRegister ({58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f006760, 0x3f041d60, 0x3f041d58) stub.
fixme:ntdll:EtwEventRegister ({3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f006760, 0x3f041cf0, 0x3f041ce8) stub.
fixme:ntdll:EtwEventRegister ({1432afee-73b0-42ce-9821-7e134361b433}, 0x3f006760, 0x3f041d98, 0x3f041d90) stub.
fixme:ntdll:EtwEventRegister ({4372afee-73b0-42ce-9821-7e134361b519}, 0x3f006760, 0x3f041dd0, 0x3f041dc8) stub.
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:ver:GetCurrentPackageId (0x33efd4 (nil)): stub
fixme:ntdll:EtwEventUnregister (deadbeef) stub.
fixme:ntdll:EtwEventUnregister (deadbeef) stub.
fixme:ntdll:EtwEventUnregister (deadbeef) stub.
fixme:ntdll:EtwEventUnregister (deadbeef) stub.
fixme:ntdll:EtwEventUnregister (deadbeef) stub. 

```

If I switch the configuration from WindowsXP to Windows8.1 I get this much shorter error log.

```
[07/11/17 15:20:07] - Running wine-2.9-staging Steam.exe (Working directory : /home/geoff/.PlayOnLinux/wineprefix/Steam/drive_c/Program Files/Steam)fixme:ver:GetCurrentPackageId (0x33e450 (nil)): stub
fixme:process:ProcessIdToSessionId Unsupported for other processes.


```

I looked at the advice on WineHQ for running Steam here

[HTML]https://appdb.winehq.org/objectManager.php?sClass=version&iId=19444[/HTML]

but didn't see anything that looked like it would address this specific problem.

Thanks!

---

### Post by sccman on 2017-07-11
Try installing the latest Wine Staging version (2.11) outside of PlayOnLinux and installing Steam through it. Wine gives you directions on how to do that on their website:

[https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)

Then enter **winecfg** into the terminal to set up Wine.

Once you've done that, you can install Steam through it by double clicking the installer or by entering **wine ****/path/to/installer**.

---

### Post by gleedadswell on 2017-07-11
Thanks sccman but that doesn't seem to have resolved it.

I installed the most recent staging version so now:

```
geoff@kinetic-kubo:~/Desktop$ wine --version
wine-2.11 (Staging)
```

Downloaded the Windows Steam install .exe and ran it from terminal using wine.  This produced a .desktop link for Steam.  Double clicking that launched Steam and it did its updates, then stopped doing anything (crashed from what I can tell).  Double clicking it again produced no visible behaviour.  Running ```
top -u geoff
``` didn't show wine running, so I assume it crashed fairly quickly.  Looking at the properties of the .desktop file and getting the command from it and running that at command line yielded:

```
geoff@kinetic-kubo:~/Desktop$ env WINEPREFIX="/home/geoff/.wine" /opt/wine-staging/bin/wine C:\\windows\\command\\start.exe /Unix /home/geoff/.wine/dosdevices/c:/users/Public/Desktop/Steam.lnk
fixme:winediag:start_process Wine Staging 2.11 is a testing version containing experimental patches.
fixme:winediag:start_process Please mention your exact version when filing bug reports on winehq.org.
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:exec:SHELL_execute flags ignored: 0x00004100
geoff@kinetic-kubo:~/Desktop$ fixme:ver:GetCurrentPackageId (0x33e440 (nil)): stub
fixme:ntdll:EtwEventRegister ({47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f006760, 0x3f041d28, 0x3f041d20) stub.
fixme:ntdll:EtwEventRegister ({58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f006760, 0x3f041d60, 0x3f041d58) stub.
fixme:ntdll:EtwEventRegister ({3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f006760, 0x3f041cf0, 0x3f041ce8) stub.
fixme:ntdll:EtwEventRegister ({1432afee-73b0-42ce-9821-7e134361b433}, 0x3f006760, 0x3f041d98, 0x3f041d90) stub.
fixme:ntdll:EtwEventRegister ({4372afee-73b0-42ce-9821-7e134361b519}, 0x3f006760, 0x3f041dd0, 0x3f041dc8) stub.
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:ver:GetCurrentPackageId (0x33efc4 (nil)): stub
fixme:ntdll:EtwEventUnregister (deadbeef) stub.
fixme:ntdll:EtwEventUnregister (deadbeef) stub.
fixme:ntdll:EtwEventUnregister (deadbeef) stub.
fixme:ntdll:EtwEventUnregister (deadbeef) stub.
fixme:ntdll:EtwEventUnregister (deadbeef) stub.


```

which looks a fair bit like the sort of errors I was getting running through PlayOnLinux.  I used winecfg to switch to a few different windows versions (XP, 8.1, 10) and got more or less the same output with all of them.

---

### Post by sccman on 2017-07-14
You can ignore the fixme's. They're for developers in debugging.

Check out these error messages in PlayOnLinux:

```
err:module:load_builtin_dll failed to load .so lib for builtin L"winebus.sys": libudev.so.0: cannot open shared object file: No such file or directory
err:winedevice:async_create_driver failed to create driver L"WineBus": c0000142
```

I know the first error says it's missing the library files libudev0. From what I researched, Ubuntu 14.04+ moved away from libudev0, but you could try downloading the .deb file and manually installing it through Ryan Critchen's suggestion [here]("https://askubuntu.com/questions/288821/how-do-i-resolve-a-cannot-open-shared-object-file-libudev-so-0-error"). 

The second one seems to be a driver issue. Maybe you can configure it in winecfg?

---

### Post by sccman on 2017-07-14
If that doesn't work, I can think of three other options you could do:

1) Try upgrading your software:
```
sudo apt update
sudo apt -y upgrade
```

2) Upgrade to Ubuntu 16.04:
```
sudo do-release-upgrade
```

3) Or reinstall Ubuntu. Burn an installation disc.

---

### Post by gleedadswell on 2017-07-15
Hooray!  It works!

Thanks very much sccman.  I installed the libudev0 as you suggested.  I didn't do anything about the driver.  I then tried running it and it works now (well, Steam loads - I haven't actually tried a game yet...).  So it is possible that the libudev0 fixed it.  It is also possible that the wine update (to 2.12) combined with steam updates at the same time might have fixed the problem.  I'll mark this as solved.

---

