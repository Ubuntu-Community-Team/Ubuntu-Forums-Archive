---
title: "Captvty:  dependencies clearly missing after upgrade to 22.04"
date: 2022-07-16
forum: Wine
---

### Post by shantiq on 2022-07-16
not loading up but it was fine under 20.04

got Dotnet40 45 and 46 installed and ie7

this is the reading i get   ....     clearly some dependencies are absent hence the problems   ....     any Wine gurus present could see from this what it might be perhaps
Thanx in advance (tried a few things already 3 or 4 hours worth :)


```
 wine Captvty.exe0068:err:ntdll:RtlpWaitForCriticalSection section 7BC62360 "dlls/ntdll/loader.c: loader_section" wait timed out in thread 0068, blocked by 0074, retrying (60 sec)
003c:err:service:process_send_command receiving command result timed out
MESA-INTEL: warning: Performance support disabled, consider sysctl dev.i915.perf_stream_paranoid=0


00d8:err:ole:CoGetContextToken apartment not initialised
0024:err:eventlog:ReportEventW L"Application: Captvty.exe\nFramework Version: v4.0.30319\nDescription: The process was terminated due to an internal error in the .NET Runtime at IP 014AE7E0 (014A0000) with exit code 80131506.\n"
shan@shan-Aspire-XC-780:~/captvty-2.9.8 12 mai/captvty 2.9.8$ 00b0:err:rpc:I_RpcReceive we got fault packet with status 0x1c010003



```

or this 
```
shan@shan-Aspire-XC-780:~/captvty-2.9.8 12 mai/captvty 2.9.8$ wine Captvty.exeMESA-INTEL: warning: Performance support disabled, [COLOR=#b22222]consider sysctl dev.i915.perf_stream_paranoid=0[/COLOR]


00c8:err:ole:CoGetContextToken apartment not initialised
0024:err:eventlog:ReportEventW L"Application: Captvty.exe\nFramework Version: v4.0.30319\nDescription: The process was terminated due to an internal error in the .NET Runtime at IP 014AE7E0 (014A0000) with exit code 80131506.\n"
shan@shan-Aspire-XC-780:~/captvty-2.9.8 12 mai/captvty 2.9.8$ 00a4:err:rpc:I_RpcReceive we got fault packet with status 0x1c010003



```


this is what I have installed thus far (some of those are for others exe programs)


```
winetricks list-installed

Executing mkdir -p /home/shan
Using winetricks 20220411-next - sha256sum: 9013b68a97e1f6e7c660b605af27a196509ba2f00cd72bf614cbf79651dad222 with wine-6.0.3 (Ubuntu 6.0.3~repack-1) and WINEARCH=win32
andale
arial
comicsans
courier
georgia
impact
times
trebuchet
verdana
webdings
corefonts
d3dcompiler_42
w_workaround_wine_bug-24013
d3dcompiler_43
d3dcompiler_46
d3dcompiler_47
d3drm
d3dx10
d3dx10_43
d3dx11_42
d3dx11_43
d3dx9
d3dx9_24
d3dx9_25
d3dx9_26
d3dx9_27
d3dx9_28
d3dx9_29
d3dx9_30
d3dx9_31
d3dx9_32
d3dx9_33
d3dx9_34
d3dx9_35
d3dx9_36
d3dx9_37
d3dx9_38
d3dx9_39
d3dx9_40
d3dx9_41
d3dx9_42
d3dx9_43
w_workaround_wine_bug-34803
remove_mono
winxp
dotnet40
remove_mono
remove_mono
winxp
dotnet40
remove_mono
remove_mono
winxp
dotnet40
dotnet45
vcrun2012
remove_mono
dotnet46
xinput
gdiplus
comctl32
msls31



```


EDIT:     ok threw everything at it including the kitchen sink and it is back on working as well almost as it was on 20.04  still some fine tuning    had to do [this here]("https://ubuntuforums.org/showthread.php?t=2457426")   and it may have swung it but as oftentimes with Wine and generally computers I am not sure why it works now and did not before :o  but marked as solved

---

