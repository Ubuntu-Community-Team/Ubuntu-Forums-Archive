---
title: "Just installed uTorrent, did I screw up?"
date: 2008-09-24
forum: Wine
---

### Post by Oplix on 2008-09-24
First off, yeah, I know there's native torrent clients for Linux, but I'm a member of a torrent community which is sort of selective of which clients its members use.

The versions of Transmission and Ktorrent offered in the add/remove programs was not a version the community approved of. Finding a newer version would have required me to compile the source code, which I've never done, and which seemed like a headache to learn all at once JUST to get some torrents going. 

So I have utorrent installed. It seems to be downloading fine as well.

However I seem to be getting some messages in my terminal window which I'm not sure whether they should be there or not...

So this is what I get when I start up utorrent with 1 file downloading...

```
fixme:heap:HeapSetInformation 0x110000 0 0x46ee6c 4
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
fixme:heap:HeapSetInformation 0x640000 0 0x46ee6c 4
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
WARNING: Trying to create a socket of type SOCK_RAW, this will fail unless you have special permissions.
WARNING: Trying to create a socket of type SOCK_RAW, this will fail unless you have special permissions.
err:ole:CoGetClassObject class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
err:ole:CoGetClassObject class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
err:ole:create_server class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} could be created for context 0x17
err:ole:CoGetClassObject class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
err:ole:CoGetClassObject class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
err:ole:create_server class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} could be created for context 0x17
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 16 lpiArray 0x33f030
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 1 lpiArray 0x33f0b0
fixme:keyboard:UnregisterHotKey (0x14008e,1): stub
oplis@Kublu:~$ err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
fixme:ntdll:server_ioctl_file Unsupported ioctl 900c4 (device=9 access=0 func=31 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 900c4 (device=9 access=0 func=31 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 940cf (device=9 access=1 func=33 method=3)
fixme:ntdll:server_ioctl_file Unsupported ioctl 940cf (device=9 access=1 func=33 method=3)
fixme:ntdll:server_ioctl_file Unsupported ioctl 940cf (device=9 access=1 func=33 method=3)
fixme:ntdll:server_ioctl_file Unsupported ioctl 940cf (device=9 access=1 func=33 method=3)
fixme:ntdll:server_ioctl_file Unsupported ioctl 900c4 (device=9 access=0 func=31 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 900c4 (device=9 access=0 func=31 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 940cf (device=9 access=1 func=33 method=3)
fixme:ntdll:server_ioctl_file Unsupported ioctl 940cf (device=9 access=1 func=33 method=3)
fixme:heap:RtlCompactHeap (0x640000, 0x0) stub
```

This is what I get when I try to run the speed test in the configuration.

```
err:winebrowser:get_url_from_dde Unabled to retrieve URL from string L"\""
err:winebrowser:wmain Usage: winebrowser URL
```

The file seems to be downloading fine and all, so I'm sure if anything it's not a huge problem. It would be nice to know whether or not I've got this installed and running properly though, or if there's something I should know about here.

THANKS!

---

### Post by asdfoo on 2008-09-24
> **Oplix said:**
> First off, yeah, I know there's native torrent clients for Linux, but I'm a member of a torrent community which is sort of selective of which clients its members use.

The versions of Transmission and Ktorrent offered in the add/remove programs was not a version the community approved of. Finding a newer version would have required me to compile the source code, which I've never done, and which seemed like a headache to learn all at once JUST to get some torrents going. 

So I have utorrent installed. It seems to be downloading fine as well.

However I seem to be getting some messages in my terminal window which I'm not sure whether they should be there or not...

So this is what I get when I start up utorrent with 1 file downloading...

```
fixme:heap:HeapSetInformation 0x110000 0 0x46ee6c 4
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
fixme:heap:HeapSetInformation 0x640000 0 0x46ee6c 4
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
WARNING: Trying to create a socket of type SOCK_RAW, this will fail unless you have special permissions.
WARNING: Trying to create a socket of type SOCK_RAW, this will fail unless you have special permissions.
err:ole:CoGetClassObject class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
err:ole:CoGetClassObject class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
err:ole:create_server class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} could be created for context 0x17
err:ole:CoGetClassObject class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
err:ole:CoGetClassObject class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
err:ole:create_server class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} could be created for context 0x17
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 16 lpiArray 0x33f030
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 1 lpiArray 0x33f0b0
fixme:keyboard:UnregisterHotKey (0x14008e,1): stub
oplis@Kublu:~$ err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
fixme:ntdll:server_ioctl_file Unsupported ioctl 900c4 (device=9 access=0 func=31 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 900c4 (device=9 access=0 func=31 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 940cf (device=9 access=1 func=33 method=3)
fixme:ntdll:server_ioctl_file Unsupported ioctl 940cf (device=9 access=1 func=33 method=3)
fixme:ntdll:server_ioctl_file Unsupported ioctl 940cf (device=9 access=1 func=33 method=3)
fixme:ntdll:server_ioctl_file Unsupported ioctl 940cf (device=9 access=1 func=33 method=3)
fixme:ntdll:server_ioctl_file Unsupported ioctl 900c4 (device=9 access=0 func=31 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 900c4 (device=9 access=0 func=31 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 940cf (device=9 access=1 func=33 method=3)
fixme:ntdll:server_ioctl_file Unsupported ioctl 940cf (device=9 access=1 func=33 method=3)
fixme:heap:RtlCompactHeap (0x640000, 0x0) stub
```

This is what I get when I try to run the speed test in the configuration.

```
err:winebrowser:get_url_from_dde Unabled to retrieve URL from string L"\""
err:winebrowser:wmain Usage: winebrowser URL
```

The file seems to be downloading fine and all, so I'm sure if anything it's not a huge problem. It would be nice to know whether or not I've got this installed and running properly though, or if there's something I should know about here.

THANKS!

Lines starting with fixme: are information messages only, reminders to developers that something could do with improvement.  Lines starting with err: are usually related to small things which Wine does not yet support but as you say, the program appears to work fine.    It's normal behaviour.

---

