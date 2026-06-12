---
title: "EVE Online?"
date: 2012-12-04
forum: Wine
---

### Post by Gotti on 2012-12-04
Has anyone got eve online working on 12.10? Google doesn't produce much on the topic.

When I try to run it in wine I get:

```
jason@kaito:~/.wine/drive_c/Program Files/CCP/EVE$ wine eve.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:gameux:GameExplorerImpl_VerifyAccess (0x138908, L"C:\\Program Files\\CCP\\EVE\\eve.exe", 0x32fd98)
jason@kaito:~/.wine/drive_c/Program Files/CCP/EVE$ WARNING: gnome-keyring:: couldn't connect to: /run/user/jason/keyring-NTkH3B/pkcs11: No such file or directory
00:28:23: Debug: src/helpers.cpp(140): 'CreateActCtx' failed with error 0x00000103 (no more data available.).
fixme:iphlpapi:NotifyAddrChange (Handle 0x33cfd0, overlapped 0x3bbaf50): stub
fixme:winsock:WSALookupServiceBeginW (0x33d030 0x00000ff0 0x33d020) Stub!
[1204/002823:ERROR:network_change_notifier_win.cc(111)] WSALookupServiceBegin failed with: 8
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x48b000 0 0x33f31c 4
Network layer using: CarbonIO
Terminating process by request - returning 0
```

The last two lines come up after I hit play on the launcher. (The launcher seems to come up fine)

I've already installed vcrun2005, vcrun2008, vcrun2010, d3dx9, and mscore fonts.

Any help would be awesome

---

### Post by Gotti on 2012-12-17
It's been a week...a bump's allowed, no?

BUMP!

---

### Post by Bölvaður on 2012-12-18
> **Gotti said:**
> It's been a week...a bump's allowed, no?

BUMP!
Bumping is allowed after 24 hours.
Eve-Online used to have it's own WINE wrapper, but they dropped it as the latest WINE seemed to work better for players.

The goto site about WINE is the WINE website.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=25823](http://appdb.winehq.org/objectManager.php?sClass=version&iId=25823)
Here you will probably solve all of your problems with the help of other people's comments and solutions.

---

