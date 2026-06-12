---
title: "SPSS 20 Through wine"
date: 2012-09-04
forum: Wine
---

### Post by Sylos on 2012-09-04
So, Im trying to get SPSS 20 running (its a genuine copy) running on Ubuntu 10.04 64 through wine. And the damn thing wont play ball with me.

The install went ok - had some problems with the authentication wizard but got that licked in the end.

Now when I try to run it I get the following:

```
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub
fixme:advapi:RegisterEventSourceA ((null),"IBM Java"): stub
fixme:advapi:RegisterEventSourceW (L"",L"IBM Java"): stub
err:module:import_dll Library dbgwrapper.dll (which is needed by L"C:\\PROG~FBU\\SPSS\\JRE\\bin\\java.dll") not found
fixme:time:GetSystemTimes (0x62c9e4,0x62c9ec,0x62c9f4): Stub!
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
err:module:import_dll Library dbgwrapper.dll (which is needed by L"C:\\PROG~FBU\\SPSS\\JRE\\bin\\java.dll") not found
fixme:thread:NtQueryInformationThread Cannot get kerneltime or usertime of other threads
fixme:dwmapi:DwmIsCompositionEnabled 0x62dc84
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:advapi:RegisterEventSourceA ((null),"IBM Java"): stub
fixme:advapi:RegisterEventSourceW (L"",L"IBM Java"): stub
fixme:time:GetSystemTimes (0x74ca9c,0x74caa4,0x74caac): Stub!
fixme:thread:NtQueryInformationThread Cannot get kerneltime or usertime of other threads
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:RegisterEventSourceA ((null),"IBM Java"): stub
fixme:advapi:RegisterEventSourceW (L"",L"IBM Java"): stub
fixme:time:GetSystemTimes (0x74ca9c,0x74caa4,0x74caac): Stub!
fixme:thread:NtQueryInformationThread Cannot get kerneltime or usertime of other threads


fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:win:EnumDisplayDevicesW ((null),0,0x33ecdea4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x33ecdea4,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x33ecdb4c,0x00000000), stub!
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d1400
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d1400
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d1400
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d1400
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub
err:winediag:FILE_CreateFile Too many open files, ulimit -n probably needs to be increased
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library SPSSWCIS.dll (which is needed by L"C:\\Program Files\\SPSS\\spsswctl.dll") not found
err:ntdll:RtlpWaitForCriticalSection section 0x5a7a70 "?" wait timed out in thread 0056, blocked by 0054, retrying (60 sec)
err:winediag:FILE_CreateFile Too many open files, ulimit -n probably needs to be increased
org.apache.xml.serializer.utils.WrappedRuntimeException: [ERR 0437] The propery file 'output_xml.properties' for output method 'xml' could not be loaded. Check the classpath.
	at org.apache.xml.serializer.OutputPropertiesFactory.getDefaultMethodProperties(Unknown Source)
	at com.ibm.xtq.xslt.jaxp.TransformerImpl.setDefaults(Unknown Source)
	at com.ibm.xtq.xslt.jaxp.TransformerImpl.createOutputProperties(Unknown Source)
	at com.ibm.xtq.xslt.jaxp.TransformerImpl.<init>(Unknown Source)
	at com.ibm.xtq.xslt.jaxp.TransformerImpl.<init>(Unknown Source)
	at com.ibm.xtq.xslt.jaxp.AbstractTransformerFactory.newTransformer(Unknown Source)
	at com.spss.java_client.core.xml.DOMWriter.writeDOM(Unknown Source)
	at com.spss.java_client.core.template.chart.ChartUserOptions.createOptionsTemplate(Unknown Source)
	at com.spss.java_client.core.common.prefs.ExecStartupPreferences.prepareChartSetPrefs(Unknown Source)
	at com.spss.java_client.core.common.prefs.ExecStartupPreferences.loadDynamicKeys(Unknown Source)
	at com.spss.java_client.core.common.prefs.ExecStartupPreferences.doStartupExecPrefs(Unknown Source)
	at com.spss.java_client.core.common.prefs.ExecStartupPreferences.<init>(Unknown Source)
	at com.spss.java_client.core.server.DataServerProxy.connect(Unknown Source)
	at com.spss.java_client.core.common.LogonMgr.logon(Unknown Source)
	at com.spss.java_client.core.common.LogonMgr.logon(Unknown Source)
	at com.spss.java_client.core.documents.AppMgr.startLogonSequence(Unknown Source)
	at com.spss.java_client.core.documents.AppMgr.runClient(Unknown Source)
	at com.spss.java_client.core.common.Driver.main(Unknown Source)
Caused by: java.io.IOException: Stream closed
	at java.io.BufferedInputStream.getInIfOpen(BufferedInputStream.java:145)
	at java.io.BufferedInputStream.read1(BufferedInputStream.java:267)
	at java.io.BufferedInputStream.read(BufferedInputStream.java:328)
	at java.io.BufferedInputStream.fill(BufferedInputStream.java:229)
	at java.io.BufferedInputStream.read(BufferedInputStream.java:248)
	at java.util.Properties.isAscii(Properties.java:301)
	at java.util.Properties.load(Properties.java:288)
	at org.apache.xml.serializer.OutputPropertiesFactory$SerializerProps.load(Unknown Source)
	at org.apache.xml.serializer.OutputPropertiesFactory.loadPropertiesFile(Unknown Source)
	... 18 more
org.apache.xml.serializer.utils.WrappedRuntimeException: [ERR 0437] The propery file 'output_xml.properties' for output method 'xml' could not be loaded. Check the classpath.
	at org.apache.xml.serializer.OutputPropertiesFactory.getDefaultMethodProperties(Unknown Source)
	at com.ibm.xtq.xslt.jaxp.TransformerImpl.setDefaults(Unknown Source)
	at com.ibm.xtq.xslt.jaxp.TransformerImpl.createOutputProperties(Unknown Source)
	at com.ibm.xtq.xslt.jaxp.TransformerImpl.<init>(Unknown Source)
	at com.ibm.xtq.xslt.jaxp.TransformerImpl.<init>(Unknown Source)
	at com.ibm.xtq.xslt.jaxp.AbstractTransformerFactory.newTransformer(Unknown Source)
	at com.spss.java_client.core.xml.DOMWriter.writeDOM(Unknown Source)
	at com.spss.java_client.core.template.chart.ChartUserOptions.createDefaultTemplate(Unknown Source)
	at com.spss.java_client.core.common.prefs.ExecStartupPreferences.prepareChartSetPrefs(Unknown Source)
	at com.spss.java_client.core.common.prefs.ExecStartupPreferences.loadDynamicKeys(Unknown Source)
	at com.spss.java_client.core.common.prefs.ExecStartupPreferences.doStartupExecPrefs(Unknown Source)
	at com.spss.java_client.core.common.prefs.ExecStartupPreferences.<init>(Unknown Source)
	at com.spss.java_client.core.server.DataServerProxy.connect(Unknown Source)
	at com.spss.java_client.core.common.LogonMgr.logon(Unknown Source)
	at com.spss.java_client.core.common.LogonMgr.logon(Unknown Source)
	at com.spss.java_client.core.documents.AppMgr.startLogonSequence(Unknown Source)
	at com.spss.java_client.core.documents.AppMgr.runClient(Unknown Source)
	at com.spss.java_client.core.common.Driver.main(Unknown Source)
Caused by: java.io.IOException: Stream closed
	at java.io.BufferedInputStream.getInIfOpen(BufferedInputStream.java:145)
	at java.io.BufferedInputStream.read1(BufferedInputStream.java:267)
	at java.io.BufferedInputStream.read(BufferedInputStream.java:328)
	at java.io.BufferedInputStream.fill(BufferedInputStream.java:229)
	at java.io.BufferedInputStream.read(BufferedInputStream.java:248)
	at java.util.Properties.isAscii(Properties.java:301)
	at java.util.Properties.load(Properties.java:288)
	at org.apache.xml.serializer.OutputPropertiesFactory$SerializerProps.load(Unknown Source)
	at org.apache.xml.serializer.OutputPropertiesFactory.loadPropertiesFile(Unknown Source)
	... 18 more
err:ntdll:RtlpWaitForCriticalSection section 0x5a7a70 "?" wait timed out in thread 0054, blocked by 0056, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x5a7a70 "?" wait timed out in thread 0055, blocked by 0056, retrying (60 sec)

```

And I am well stuck. FWIW, the dbgwrapper.dll file it says is missing is definitely in the JRE folder. I even tried changing all the file permissions for the JRE contents but still not getting it.

So, anyone help a man down on his luck? If I dont get it working I'll be getting raw grief from the good lady who wants this.

Cheers

EDIT: Wine version is 1.2.2

---

### Post by oldos2er on 2012-09-04
Moved to Wine.

---

### Post by Sylos on 2012-09-05
> **oldos2er said:**
> Moved to Wine.

Thanks for that - didnt think of looking in Gaming and Leisure.

---

### Post by Lars Noodén on 2012-09-05
Since it is java, can you run it natively in Linux without WINE?

---

### Post by Sylos on 2012-09-05
> **Lars Noodén said:**
> Since it is java, can you run it natively in Linux without WINE?

They do offer a linux version but it isnt on the disc we have - and getting a copy of the linux version is looking difficult. Obviously all the installation files and run files are .exe so I assume not. But then Im not very well informed.

If you have any ideas on how then I would give it a shot.

Cheers

---

### Post by nixxon on 2012-10-11
> **Sylos said:**
> They do offer a linux version but it isnt on the disc we have - and getting a copy of the linux version is looking difficult. Obviously all the installation files and run files are .exe so I assume not. But then Im not very well informed.

If you have any ideas on how then I would give it a shot.

Cheers

In the past I've been able to download the demo version of SPSS from the IBM web page (googling "SPSS 20 linux demo" found it pretty quickly). The authentication code for the Windows version allowed me to license the product. 

But currently I'm unable to get SPSS to run on Ubuntu 12.04 64-bit. It worked when I had 32-bit Ubuntu installed, so I'm wondering if there are compatibility issues with the 64-bit OS. It installs fine, and when I try to run the software the initial splash screen appears but then it just goes away again...

---

