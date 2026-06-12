---
title: "Wine + Final Fantasy XIV issues"
date: 2015-11-08
forum: Wine
---

### Post by MasterSageSteven on 2015-11-08
I have been struggling with this for a few days now. Recently I have decided to go pure linux and so far the only issue I have is I cannot get Final Fantasy XIV to work.

I used the following guides:

[https://www.reddit.com/r/ffxiv/comments/3al9na/psa_ffxiv_linux_winestaging/](https://www.reddit.com/r/ffxiv/comments/3al9na/psa_ffxiv_linux_winestaging/)
[http://www.gamersonlinux.com/forum/threads/guide-final-fantasy-xiv-a-realm-reborn-on-gnu-linux.1113/](http://www.gamersonlinux.com/forum/threads/guide-final-fantasy-xiv-a-realm-reborn-on-gnu-linux.1113/)

Everything is setup and I can launch the launcher. However, the launcher gives and https error. I then opened ie8 under wine and it fails to launch and when it does launch it cannot access any websites. I thought, may I had an dns issue and found a post saying to install lib32nss-mdns or remove libnss-mdns and that should fix the issue. I did not.

 I installed firefox under wine to see if it could connect to the internet and it performs flawlessly and it can even access https sites.

Here is the output of launching the game launcher.

```

err:winediag:schan_imp_init Failed to load libgnutls, secure connections will not be available.
err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a060, {485e7de8-0a80-11d8-ad15-505054503030}, 1, 0x33fdd0, (null), (null), 0x100a068): stub
fixme:advapi:RegisterTraceGuidsW   register trace class {485e7de8-0a80-11d8-ad15-505054503030}
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a080, {485e7de9-0a80-11d8-ad15-505054503030}, 1, 0x33fdd0, (null), (null), 0x100a088): stub
fixme:advapi:RegisterTraceGuidsW   register trace class {485e7de9-0a80-11d8-ad15-505054503030}
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a0a0, {485e7dea-0a80-11d8-ad15-505054503030}, 1, 0x33fdd0, (null), (null), 0x100a0a8): stub
fixme:advapi:RegisterTraceGuidsW   register trace class {485e7dea-0a80-11d8-ad15-505054503030}
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a0c0, {485e7deb-0a80-11d8-ad15-505054503030}, 1, 0x33fdd0, (null), (null), 0x100a0c8): stub
fixme:advapi:RegisterTraceGuidsW   register trace class {485e7deb-0a80-11d8-ad15-505054503030}
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a0e0, {485e7dec-0a80-11d8-ad15-505054503030}, 1, 0x33fdd0, (null), (null), 0x100a0e8): stub
fixme:advapi:RegisterTraceGuidsW   register trace class {485e7dec-0a80-11d8-ad15-505054503030}
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a100, {485e7ded-0a80-11d8-ad15-505054503030}, 1, 0x33fdd0, (null), (null), 0x100a108): stub
fixme:advapi:RegisterTraceGuidsW   register trace class {485e7ded-0a80-11d8-ad15-505054503030}
fixme:win:RegisterDeviceNotificationW (hwnd=0x12fba8, filter=0x64e8ac,flags=0x00000001) returns a fake device notification handle!
fixme:ole:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
steven@finch-pc:~$ fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:msg:ChangeWindowMessageFilter 4a 00000001
fixme:win:EnumDisplayDevicesW ((null),0,0x33f278,0x00000000), stub!
err:winediag:schan_imp_init Failed to load libgnutls, secure connections will not be available.
err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
fixme:winsock:WSALookupServiceBeginW (0x33ec40 0x00000ff0 0x33ec88) Stub!
[1108/141148:ERROR:network_change_notifier_win.cc(160)] WSALookupServiceBegin failed with: 8
fixme:iphlpapi:NotifyAddrChange (Handle 0x33eb18, overlapped 0x376adc8): stub
fixme:winsock:WSALookupServiceBeginW (0x33ec80 0x00000ff0 0x33ecc8) Stub!
[1108/141148:ERROR:network_change_notifier_win.cc(160)] WSALookupServiceBegin failed with: 8
fixme:ras:RasEnumConnectionsW (0x1961d8,0x424e704,0x42e0004),stub!
fixme:ras:RasEnumConnectionsW RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ole:NdrCorrelationInitialize (0x5e7dea4, 0x5e7df80, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x5e7de64, 0x5e7df40, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x5e7de74, 0x5e7df50, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x5e7de34, 0x5e7df10, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x5e7de74, 0x5e7df50, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x5e7de34, 0x5e7df10, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x5e7df14, 0x5e7dff0, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x5e7df14, 0x5e7dff0, 1024, 0x0): semi-stub
fixme:ole:NdrCorrelationInitialize (0x5e7df14, 0x5e7dff0, 1024, 0x0): semi-stub
fixme:iphlpapi:CancelIPChangeNotify (overlapped 0x376adc8): stub
fixme:msg:ChangeWindowMessageFilter 4a 00000002

```

Any advice or solution would be greatly appreciated

---

### Post by howefield on 2015-11-08
Thread moved to the "*Wine*" forum.

---

### Post by MasterSageSteven on 2015-11-08
I fixed the following line by installing winbind

```

err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.

```

still not running but it has one less error

I fixed the following error

```

err:winediag:schan_imp_init Failed to load libgnutls, secure connections will not be available.

```

the post at [https://bugs.winehq.org/show_bug.cgi?id=38466](https://bugs.winehq.org/show_bug.cgi?id=38466) gave a nice quick fix to it. Just have to run the following command

```

[COLOR=#000000]sudo cp /usr/lib/i386-linux-gnu/libgnutls-deb0.so.28 /usr/lib/i386-linux-gnu/libgnutls.so.26
[/COLOR]
```

Fixed the following error

```

fixme:ras:RasEnumConnectionsW RAS support is not implemented! Configure program to use LAN connection/winsock instead!

```

Per suggestion found in the post at [https://forum.winehq.org/viewtopic.php?t=4317](https://forum.winehq.org/viewtopic.php?t=4317) I added the [COLOR=#000000][FONT=Verdana]rasapi32 library to my wine bottle and set it to native[/FONT][/COLOR]

Alright, after doing all those fixes, I deleted the [FONT=monospace].wine32-ffxiv directory and resetup the game with the guide at [/FONT]https://www.reddit.com/r/ffxiv/comments/3al9na/psa_ffxiv_linux_winestaging/ and it runs now.

Additional Note: if using wine-staging, make sure the libsystemd-dev library is installed prior to setting up the game

---

