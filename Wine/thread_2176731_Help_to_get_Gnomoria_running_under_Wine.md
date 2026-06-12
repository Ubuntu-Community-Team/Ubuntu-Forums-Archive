---
title: "Help to get Gnomoria running under Wine"
date: 2013-09-25
forum: Wine
---

### Post by rolltide101x on 2013-09-25
I want to find a way to get Gnomoria running under Wine
[www.gnomoria.com/](www.gnomoria.com/)

and then get a script written so it will install all the dependencies of Gnomoria so it can be packaged and sent in as the Ubuntu version of the game. For him to port the game to Linux or OSX it would require alot of work/time/money he does not have so this will be the next best thing. So does anyone have any ideas? Thanks

---

### Post by rolltide101x on 2013-09-25
Trying to get the demo running I run into this error

```
clate@clate-N56VZ:~$ env WINEPREFIX="/home/clate/.wine" wine C:\\windows\\command\\start.exe /Unix /home/clate/.wine/dosdevices/c:/users/Public/Desktop/Gnomoria\ Demo.lnk
fixme:service:scmdatabase_autostart_services Auto-start service L"UMWdf" failed to start: 2
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:exec:SHELL_execute flags ignored: 0x00004100
err:module:import_dll Library mscoree.dll (which is needed by L"C:\\Program Files (x86)\\Gnomoria Demo\\Gnomoria.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files (x86)\\Gnomoria Demo\\Gnomoria.exe" failed, status c0000135
clate@clate-N56VZ:~$ env WINEPREFIX="/home/clate/.wine" wine C:\\windows\\command\\start.exe /Unix /home/clate/.wine/dosdevices/c:/users/Public/Desktop/Gnomoria\ Demo.lnk
fixme:service:scmdatabase_autostart_services Auto-start service L"UMWdf" failed to start: 2
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:exec:SHELL_execute flags ignored: 0x00004100
clate@clate-N56VZ:~$ 

```

I placed "mscoree.dll" into the folder and I get an error seen in the picture below

---

### Post by rolltide101x on 2013-09-25
Ok, I removed my .wine folder and created a fresh 32 bit prefix

WINEARCH=win32 WINEPREFIX=~/.wine winecfg 


Then I installed .NetFramework4.0
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17886](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17886)

And XNA4.0
winetricks xna40

and I get the following error. Any ideas? I had to delete smileys in this so there will be weird spaces

Also check out the text file I have attached


```
clate@clate-N56VZ:~$ env WINEPREFIX="/home/clate/.wine" wine C:\\windows\\command\\start.exe /Unix /home/clate/.wine/dosdevices/c:/users/Public/Desktop/Gnomoria\ Demo.lnk
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessShutdownParameters (00000380, 00000000): partial stub.
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:exec:SHELL_execute flags ignored: 0x00004100
clate@clate-N56VZ:~$ fixme:module:GetModuleHandleExW should pin refcount for 0x79000000
fixme:thread:SetThreadStackGuarantee (0x33fc04): stub
err le:CoGetContextToken apartment not initialised
fixme:shell:URL_ParseUrl failed to parse L"Gnomoria&"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.Xna.Framework.Game"
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.Xna.Framework.Graphics"
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.Xna.Framework"
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.Xna.Framework.Input.Touch"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms"
fixme:shell:URL_ParseUrl failed to parse L"Accessibility"
fixme:shell:URL_ParseUrl failed to parse L"irrKlang.NET4"
irrKlang sound library version 1.4.0
fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project
fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit [http://ubuntuforums.org/showthread.php?t=1960599](http://ubuntuforums.org/showthread.php?t=1960599)
Using DirectSound8 driver
err:wgl:has_opengl Failed to load libGL: libGL.so.1: cannot open shared object file: No such file or directory
err:wgl:has_opengl OpenGL support is disabled.
fixme:d3d9 3DPERF_SetOptions (0x2) : stub
fixme:advapi:RegisterTraceGuidsW (0xb36ad2, (nil), {8e9f5090-2d75-4d03-8a81-e5afbf85daf1}, 1, 0x33af4c, (null), (null), 0xf1cb18,): stub
clate@clate-N56VZ:~$ fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:fusion:InitializeFusion 
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
fixme:module:GetModuleHandleExW should pin refcount for 0x79000000
fixme:thread:SetThreadStackGuarantee (0x33ef60): stub
err le:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
fixme:shell:URL_ParseUrl failed to parse L"System.ServiceModel.Activation"
fixme:shell:URL_ParseUrl failed to parse L"System.Runtime.DurableInstancing"
fixme:shell:URL_ParseUrl failed to parse L"System.ServiceModel.Activities"
fixme:shell:URL_ParseUrl failed to parse L"System.Activities"
fixme:shell:URL_ParseUrl failed to parse L"System.Xaml.Hosting"
fixme:shell:URL_ParseUrl failed to parse L"System.Activities.DurableInstancing"
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.VisualBasic.Activities.Compiler"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.EnterpriseServices"
fixme:shell:URL_ParseUrl failed to parse L"System.Configuration"
fixme:shell:URL_ParseUrl failed to parse L"System.ServiceModel"
fixme:shell:URL_ParseUrl failed to parse L"System.Transactions"
fixme:shell:URL_ParseUrl failed to parse L"System.Xml"
fixme:shell:URL_ParseUrl failed to parse L"System.ServiceModel.Activation"
fixme:shell:URL_ParseUrl failed to parse L"System.Runtime.DurableInstancing"
fixme:shell:URL_ParseUrl failed to parse L"System.ServiceModel.Activities"
fixme:shell:URL_ParseUrl failed to parse L"System.Activities"
fixme:shell:URL_ParseUrl failed to parse L"System.Xaml.Hosting"
fixme:shell:URL_ParseUrl failed to parse L"System.Activities.DurableInstancing"
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.VisualBasic.Activities.Compiler"
fixme:shell:URL_ParseUrl failed to parse L"System.DirectoryServices"
fixme:shell:URL_ParseUrl failed to parse L"System.Web"
fixme:shell:URL_ParseUrl failed to parse L"System.Runtime.Serialization"
fixme rocess:FlushProcessWriteBuffers : stub
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err le:StdMarshalImpl_UnmarshalInterface Apartment not initialized
err le:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800401f0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err le:StdMarshalImpl_UnmarshalInterface Apartment not initialized
err le:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800401f0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err le:StdMarshalImpl_UnmarshalInterface Apartment not initialized
err le:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800401f0
fixme :heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
fixme:module:GetModuleHandleExW should pin refcount for 0x79000000
fixme:thread:SetThreadStackGuarantee (0x33ef60): stub
err le:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
err le:CoGetContextToken apartment not initialised
fixme:shell:URL_ParseUrl failed to parse L"System.Deployment"
fixme rocess:FlushProcessWriteBuffers : stub
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err le:StdMarshalImpl_UnmarshalInterface Apartment not initialized
err le:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800401f0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err le:StdMarshalImpl_UnmarshalInterface Apartment not initialized
err le:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800401f0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
fixme:module:GetModuleHandleExW should pin refcount for 0x79000000
fixme:thread:SetThreadStackGuarantee (0x33ef60): stub
err le:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
err le:CoGetContextToken apartment not initialised
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.Build"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.Build.Framework"
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.Build"
fixme:shell:URL_ParseUrl failed to parse L"System.Xml"
fixme:shell:URL_ParseUrl failed to parse L"Microsoft.Build.Engine"
fixme:shell:URL_ParseUrl failed to parse L"System.Core"
fixme:shell:URL_ParseUrl failed to parse L"System.Configuration"
fixme:shell:URL_ParseUrl failed to parse L"System.Security"
fixme:shell:URL_ParseUrl failed to parse L"System.Data.SqlXml"
fixme:shell:URL_ParseUrl failed to parse L"System.Xaml"
fixme:shell:URL_ParseUrl failed to parse L"System.Numerics"
fixme rocess:FlushProcessWriteBuffers : stub
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err le:StdMarshalImpl_UnmarshalInterface Apartment not initialized
err le:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800401f0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err le:StdMarshalImpl_UnmarshalInterface Apartment not initialized
err le:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800401f0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err le:StdMarshalImpl_UnmarshalInterface Apartment not initialized
err le:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800401f0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err le:StdMarshalImpl_UnmarshalInterface Apartment not initialized
err le:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800401f0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err le:StdMarshalImpl_UnmarshalInterface Apartment not initialized
err le:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800401f0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err le:StdMarshalImpl_UnmarshalInterface Apartment not initialized
err le:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800401f0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err le:StdMarshalImpl_UnmarshalInterface Apartment not initialized
err le:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800401f0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err le:StdMarshalImpl_UnmarshalInterface Apartment not initialized
err le:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800401f0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err le:StdMarshalImpl_UnmarshalInterface Apartment not initialized
err le:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800401f0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err le:StdMarshalImpl_UnmarshalInterface Apartment not initialized
err le:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800401f0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err le:StdMarshalImpl_UnmarshalInterface Apartment not initialized
err le:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800401f0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err le:StdMarshalImpl_UnmarshalInterface Apartment not initialized
err le:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800401f0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err le:StdMarshalImpl_UnmarshalInterface Apartment not initialized
err le:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800401f0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
fixme:module:GetModuleHandleExW should pin refcount for 0x79000000
fixme:thread:SetThreadStackGuarantee (0x33ef60): stub
err le:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
err le:CoGetContextToken apartment not initialised
fixme:shell:URL_ParseUrl failed to parse L"System.Runtime.DurableInstancing"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.ServiceModel"
fixme:shell:URL_ParseUrl failed to parse L"System.ServiceProcess"
fixme:shell:URL_ParseUrl failed to parse L"System.Runtime.DurableInstancing"
fixme:shell:URL_ParseUrl failed to parse L"SMDiagnostics"
fixme:shell:URL_ParseUrl failed to parse L"System.Messaging"
fixme:shell:URL_ParseUrl failed to parse L"System.Configuration"
fixme:shell:URL_ParseUrl failed to parse L"System.Xml"
fixme rocess:FlushProcessWriteBuffers : stub
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err le:StdMarshalImpl_UnmarshalInterface Apartment not initialized
err le:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800401f0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err le:StdMarshalImpl_UnmarshalInterface Apartment not initialized
err le:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800401f0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err le:StdMarshalImpl_UnmarshalInterface Apartment not initialized
err le:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800401f0
clate@clate-N56VZ:~$ fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
fixme:module:GetModuleHandleExW should pin refcount for 0x79000000
fixme:thread:SetThreadStackGuarantee (0x33ef60): stub
err le:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
err le:CoGetContextToken apartment not initialised
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.ServiceProcess"
fixme:shell:URL_ParseUrl failed to parse L"System.Management"
fixme:shell:URL_ParseUrl failed to parse L"System.Configuration"
fixme:shell:URL_ParseUrl failed to parse L"System.Xml"
fixme rocess:FlushProcessWriteBuffers : stub
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme rocess:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme le:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err le:StdMarshalImpl_UnmarshalInterface Apartment not initialized
err le:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x800401f0
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime Optimization Service"): stub
fixme:advapi eregisterEventSource (0xcafe4242) stub
fixme:win:GetWindowPlacement not supported on other process window 0x20094

Unhandled Exception: System.TypeInitializationException: The type initializer for 'Microsoft.Xna.Framework.Graphics.GraphicsAdapter' threw an exception. ---> System.NullReferenceException: Object reference not set to an instance of an object.
   at Microsoft.Xna.Framework.Graphics.GraphicsAdapter.InitializeAdapterList()
   at Microsoft.Xna.Framework.Graphics.GraphicsAdapter..cctor()
   --- End of inner exception stack trace ---
   at Microsoft.Xna.Framework.Graphics.GraphicsAdapter.get_Adapters()
   at Microsoft.Xna.Framework.GraphicsDeviceManager.AddDevices(Boolean anySuitableDevice, List`1 foundDevices)
   at Microsoft.Xna.Framework.GraphicsDeviceManager.FindBestPlatformDevice(Boolean anySuitableDevice)
   at Microsoft.Xna.Framework.GraphicsDeviceManager.FindBestDevice(Boolean anySuitableDevice)
   at Microsoft.Xna.Framework.GraphicsDeviceManager.ChangeDevice(Boolean forceCreate)
   at Microsoft.Xna.Framework.GraphicsDeviceManager.Microsoft.Xna.Framework.IGraphicsDeviceManager.CreateDevice()
   at Microsoft.Xna.Framework.Game.RunGame(Boolean useBlockingRun)
   at A.cebc1c67c4a164a49b1c279b0006957be.c49a93168dc3d77742f5742786a5b60b9(String[] c51864dddd6353b79e1a34e131a62f09a)
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
err le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
error le:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
clate@clate-N56VZ:~$ 

```

---

### Post by Toz on 2013-09-25
*Fixed code tags and moved to the **Wine** subforum.*

Have you seen the instructions noted [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=26693")?

---

