---
title: "Rosetta Stone"
date: 2008-10-04
forum: Wine
---

### Post by bigblackbunny on 2008-10-04
Hey guys, I'm having a little trouble getting my Rosetta Stone program to install, but I have heard of it running on linux before. I am using Ubuntu 8.04, and trying to install the v.2.1.5.1A version of Rosetta Stone. When trying to run the installer using the terminal, I got the code below.

```
alex@LYOKO:~$ wine /media/cdrom0/Setup.exe
fixme:advapi:RegisterEventSourceW ((null),L"AdobePlatform"): stub
fixme:advapi:RegisterEventSourceW ((null),L"Adobe Active File Monitor 4.0"): stub
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a060 0x1001818 1 0x33fe78 (null) (null) 0x100a068
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a080 0x1001808 1 0x33fe78 (null) (null) 0x100a088
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a0a0 0x10017f8 1 0x33fe78 (null) (null) 0x100a0a8
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a0c0 0x10017e8 1 0x33fe78 (null) (null) 0x100a0c8
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a0e0 0x10017d8 1 0x33fe78 (null) (null) 0x100a0e8
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a100 0x10017c8 1 0x33fe78 (null) (null) 0x100a108
fixme:win:RegisterDeviceNotificationW (hwnd=0x125640, filter=0x7e5fc90c,flags=0x00000001),
	returns a fake device notification handle!
cwd: C:\windows\temp\I1223098657\Windows
cmd: "C:\windows\temp\I1223098657\Windows\resource\jre\bin\javaw.exe" -Xms16777216 -Xmx50331648 -classpath "C:\windows\temp\I1223098657\InstallerData\IAClasses.zip;C:\windows\temp\I1223098657\Windows\resource\jdglue.zip;C:\windows\temp\I1223098657\InstallerData\Execute.zip;C:\windows\temp\I1223098657\Windows\InstallerData\Execute.zip;C:\windows\temp\I1223098657\InstallerData\Resource1.zip;C:\windows\temp\I1223098657\Windows\InstallerData\Resource1.zip;C:\windows\temp\I1223098657\InstallerData;C:\windows\temp\I1223098657\Windows\InstallerData;" com.zerog.lax.LAX "C:/windows/temp/I1223098657/Windows/Setup.lax" "C:/windows/temp/laxe058.tmp" 
fixme:msvcrt:MSVCRT__sopen : pmode 0x01b6 ignored
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems

An unexpected exception has been detected in native code outside the VM.
Unexpected Signal : EXCEPTION_ACCESS_VIOLATION occurred at PC=0x6D20349C
Function name=(N/A)
Library=C:\windows\temp\I1223098657\Windows\resource\jre\bin\fontmanager.dll

NOTE: We are unable to locate the function name symbol for the error
      just occurred. Please refer to release documentation for possible
      reason and solutions.



Current Java thread:
	at sun.awt.font.NativeFontWrapper.getFontMetrics(Native Method)
	at sun.awt.font.FontDesignMetrics.initMatrixAndMetrics(Unknown Source)
	at sun.awt.font.FontDesignMetrics.<init>(Unknown Source)
	at sun.awt.font.FontDesignMetrics.<init>(Unknown Source)
	at sun.awt.SunToolkit.getFontMetrics(Unknown Source)
	at sun.awt.windows.WToolkit.getFontMetrics(Unknown Source)
	at javax.swing.plaf.basic.BasicLabelUI.getPreferredSize(Unknown Source)
	at javax.swing.JComponent.getPreferredSize(Unknown Source)
	at javax.swing.plaf.basic.BasicComboBoxUI.getDefaultSize(Unknown Source)
	at javax.swing.plaf.basic.BasicComboBoxUI.getDisplaySize(Unknown Source)
	at com.sun.java.swing.plaf.windows.WindowsComboBoxUI.getMinimumSize(Unknown Source)
	at javax.swing.plaf.basic.BasicComboBoxUI.getPreferredSize(Unknown Source)
	at javax.swing.JComponent.getPreferredSize(Unknown Source)
	at java.awt.GridBagLayout.GetLayoutInfo(Unknown Source)
	at java.awt.GridBagLayout.preferredLayoutSize(Unknown Source)
	at java.awt.Container.preferredSize(Unknown Source)
	at java.awt.Container.getPreferredSize(Unknown Source)
	at javax.swing.JComponent.getPreferredSize(Unknown Source)
	at java.awt.GridBagLayout.GetLayoutInfo(Unknown Source)
	at java.awt.GridBagLayout.ArrangeGrid(Unknown Source)
	at java.awt.GridBagLayout.layoutContainer(Unknown Source)
	at java.awt.Container.layout(Unknown Source)
	at java.awt.Container.doLayout(Unknown Source)
	at ZeroGcj.a(DashoA8113)
	at ZeroGcj.a(DashoA8113)
	at ZeroGcm.<init>(DashoA8113)
	at ZeroGcj.<init>(DashoA8113)
	at ZeroGci.a(DashoA8113)
	at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
	at com.zerog.ia.installer.LifeCycleManager.f(DashoA8113)
	at com.zerog.ia.installer.LifeCycleManager.g(DashoA8113)
	at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
	at com.zerog.ia.installer.Main.main(DashoA8113)
	at java.lang.reflect.Method.invoke(Native Method)
	at com.zerog.lax.LAX.launch(DashoA8113)
	at com.zerog.lax.LAX.main(DashoA8113)

Dynamic libraries:
0x00400000 - 0x00405000 	C:\windows\temp\I1223098657\Windows\resource\jre\bin\javaw.exe
0x7BC10000 - 0x7BCA6000 	C:\windows\system32\ntdll.dll
0x7B820000 - 0x7B93C000 	C:\windows\system32\KERNEL32.dll
0x7EE20000 - 0x7EE65000 	C:\windows\system32\advapi32.dll
0x7ECE0000 - 0x7EE11000 	C:\windows\system32\user32.dll
0x7EC40000 - 0x7ECC8000 	C:\windows\system32\gdi32.dll
0x7EBD0000 - 0x7EC2A000 	C:\windows\system32\msvcrt.dll
0x7EA50000 - 0x7EAD0000 	C:\windows\system32\winex11.drv
0x7E8D0000 - 0x7E8EE000 	C:\windows\system32\imm32.dll
0x6D420000 - 0x6D4F8000 	C:\windows\temp\I1223098657\Windows\resource\jre\bin\hotspot\jvm.dll
0x7E820000 - 0x7E8A7000 	C:\windows\system32\winmm.dll
0x7E7F0000 - 0x7E815000 	C:\windows\system32\winealsa.drv
0x7E700000 - 0x7E708000 	C:\windows\system32\msacm32.drv
0x7E6D0000 - 0x7E6F1000 	C:\windows\system32\msacm32.dll
0x7E7D0000 - 0x7E7E0000 	C:\windows\system32\midimap.dll
0x6D220000 - 0x6D227000 	C:\windows\temp\I1223098657\Windows\resource\jre\bin\hpi.dll
0x6D3B0000 - 0x6D3BD000 	C:\windows\temp\I1223098657\Windows\resource\jre\bin\verify.dll
0x6D250000 - 0x6D268000 	C:\windows\temp\I1223098657\Windows\resource\jre\bin\java.dll
0x6D3C0000 - 0x6D3CD000 	C:\windows\temp\I1223098657\Windows\resource\jre\bin\zip.dll
0x6D020000 - 0x6D12B000 	C:\windows\temp\I1223098657\Windows\resource\jre\bin\awt.dll
0x7DD90000 - 0x7DDC1000 	C:\windows\system32\winspool.drv
0x7DCA0000 - 0x7DD8C000 	C:\windows\system32\ole32.dll
0x7DC30000 - 0x7DC83000 	C:\windows\system32\rpcrt4.dll
0x7DC10000 - 0x7DC1E000 	C:\windows\system32\iphlpapi.dll
0x6D1E0000 - 0x6D21B000 	C:\windows\temp\I1223098657\Windows\resource\jre\bin\fontmanager.dll
0x10000000 - 0x10053000 	C:\windows\temp\I1223098657\Windows\resource\iawin32.dll
0x7D6A0000 - 0x7D7A5000 	C:\windows\system32\shell32.dll
0x7D640000 - 0x7D68B000 	C:\windows\system32\shlwapi.dll
0x7D580000 - 0x7D631000 	C:\windows\system32\comctl32.dll
0x7D540000 - 0x7D570000 	C:\windows\system32\uxtheme.dll
0x6D2C0000 - 0x6D2DB000 	C:\windows\temp\I1223098657\Windows\resource\jre\bin\jpeg.dll
0x7D3E0000 - 0x7D3F6000 	C:\windows\system32\imagehlp.dll
0x7D3A0000 - 0x7D3DF000 	C:\windows\system32\dbghelp.dll
0x7D380000 - 0x7D394000 	C:\windows\system32\psapi.dll

Local Time = Sat Oct  4 01:38:15 2008
Elapsed Time = 1
#
# The exception above was detected in native code outside the VM
#
# Java VM: Java HotSpot(TM) Client VM (1.3.1_11-b02 mixed mode)
#
# An error report file has been saved as hs_err_pid52.log.
# Please refer to the file for further information.
#
alex@LYOKO:~$ 
```

About the hs_err_pid52.log that it mentions, I can't find it. I even used the "Search for Files..." option
Any idea what to do?

---

