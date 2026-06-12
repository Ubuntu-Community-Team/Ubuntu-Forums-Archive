---
title: "Java error on wine"
date: 2011-10-04
forum: Wine
---

### Post by ilcontegis on 2011-10-04
I have just updated to ubuntu 11.10 64bit, on my DELL latitude E6320. I use the latest version of wine 1.3 and I have the following issue when I try to launch the software Dinamica EGO:
```
wine: Call from 0x7ed22639 to unimplemented function msvcp90.dll.??0?$basic_ofstream@DU?$char_traits@D@std@@@std@@QAE@PBDHH@Z, aborting
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:win:EnumDisplayDevicesW ((null),0,0x1760db04,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x1760db04,0x00000000), stub!
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  EXCEPTION_ACCESS_VIOLATION (0xc0000005) at pc=0xf75df740, pid=31, tid=46
#
# JRE version: 6.0_22-b04
# Java VM: Java HotSpot(TM) Client VM (17.1-b03 mixed mode windows-x86 )
# Problematic frame:
# C  0xf75df740
#
fixme:msvcrt:MSVCRT__sopen_s : pmode 0x01b6 ignored
# An error report file with more information is saved as:
# C:\Program Files\Dinamica EGO\hs_err_pid31.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

```
With ubuntu 11.04 it worked smoothly without any issue.
I already try to un-install Dinamica EGO, wine, java (both the sun and icetea). I also deleted the folders and reinstalled everything. The problem still persist.

Do you have any suggestions?

Thank you

---

