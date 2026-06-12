---
title: "PC Freezes! utorrent, wine?"
date: 2007-08-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by RichGuk on 2007-08-16
Hello,

My Kubuntu (64bit) Fiesty keeps freezes when I attempt to re-check a 15GB torrent file running utorrent under wine. I'm unsure if its utorrent, it uses 90% of the CPU when its re-checking the torrent, uses nothing (1-2%) when its not checkng. When not re-checking the torrent in utorrent the PC seems stable and has lasted a day and night without freezes but it'll get 30 seconds into checking the torrent and freeze.

The data of the torrent is stored on a mdadm raid5 array (which is degraded at the moment - harddrive failed although I think it still did it when it was running fine).

This is the first 64bit OS so I was unsure if this was the problem also. 

The output in /var/log/kern.log before I restart the PC seems to be this.


```
Aug 16 18:13:32 cylon kernel: [  130.907721] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich
Aug 16 18:13:32 cylon kernel: [  130.907967] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows/system32
Aug 16 18:13:32 cylon kernel: [  130.908253] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows/system32
Aug 16 18:13:32 cylon kernel: [  130.908596] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows/system32
Aug 16 18:13:32 cylon kernel: [  131.259676] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/Program Files/uTorrent
Aug 16 18:13:32 cylon kernel: [  131.259891] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich
Aug 16 18:13:32 cylon kernel: [  131.260139] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows/system32
Aug 16 18:13:32 cylon kernel: [  131.260429] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows/system32
Aug 16 18:13:32 cylon kernel: [  131.260779] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows/system32
Aug 16 18:13:32 cylon kernel: [  131.297356] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/Program Files/uTorrent
Aug 16 18:13:32 cylon kernel: [  131.297556] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich
Aug 16 18:13:32 cylon kernel: [  131.297802] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows/system32
Aug 16 18:13:32 cylon kernel: [  131.314272] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows/system
Aug 16 18:13:32 cylon kernel: [  131.314705] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows
Aug 16 18:13:32 cylon kernel: [  131.315454] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows/system32
Aug 16 18:13:32 cylon kernel: [  131.316096] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows

```

And another time I got this.

```

Aug 15 18:21:35 cylon kernel: [  120.135510] ioctl32(uTorrent.exe:6033): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows/system32
Aug 15 18:21:35 cylon kernel: [  120.135643] ioctl32(uTorrent.exe:6033): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows
Aug 15 18:30:14 cylon kernel: [  638.525686] Losing some ticks... checking if CPU frequency changed.
Aug 15 19:20:22 cylon kernel: [ 3643.184297]  CIFS VFS: server not responding
Aug 15 19:20:22 cylon kernel: [ 3643.184304]  CIFS VFS: No response for cmd 114 mid 1146
Aug 15 22:00:22 cylon kernel: [13231.642818]  CIFS VFS: server not responding
Aug 15 22:00:22 cylon kernel: [13231.642826]  CIFS VFS: No response for cmd 114 mid 1148
Aug 15 22:19:22 cylon kernel: [14370.284039]  CIFS VFS: server not responding
Aug 15 22:19:22 cylon kernel: [14370.284046]  CIFS VFS: No response for cmd 114 mid 251
Aug 16 02:38:59 cylon kernel: [29931.210780] warning: many lost ticks.
Aug 16 02:38:59 cylon kernel: [29931.210783] Your time source seems to be instable or some driver is hogging interupts
Aug 16 02:38:59 cylon kernel: [29931.210792] rip __do_softirq+0x54/0xd0
```

AMD cool'n'quite is disabled. The system specs:

DFI Lan Party UT SLI-D
AMD Althon X2 3800+
2GB PC4000 RAM

4 hard drives are attached using a promise SATA2 TX4 adaptor
and two harddrives are attached using the onboard sata ports.

the raid 5 goes accross the motherboard's ports and the controller.


Anyone got any ideas?

Thanks,

Rich :)

---

### Post by Kilz on 2007-08-16
> **RichGuk said:**
> Hello,

My Kubuntu (64bit) Fiesty keeps freezes when I attempt to re-check a 15GB torrent file running utorrent under wine. I'm unsure if its utorrent, it uses 90% of the CPU when its re-checking the torrent, uses nothing (1-2%) when its not checkng. When not re-checking the torrent in utorrent the PC seems stable and has lasted a day and night without freezes but it'll get 30 seconds into checking the torrent and freeze.

The data of the torrent is stored on a mdadm raid5 array (which is degraded at the moment - harddrive failed although I think it still did it when it was running fine).

This is the first 64bit OS so I was unsure if this was the problem also. 

The output in /var/log/kern.log before I restart the PC seems to be this.


```
Aug 16 18:13:32 cylon kernel: [  130.907721] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich
Aug 16 18:13:32 cylon kernel: [  130.907967] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows/system32
Aug 16 18:13:32 cylon kernel: [  130.908253] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows/system32
Aug 16 18:13:32 cylon kernel: [  130.908596] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows/system32
Aug 16 18:13:32 cylon kernel: [  131.259676] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/Program Files/uTorrent
Aug 16 18:13:32 cylon kernel: [  131.259891] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich
Aug 16 18:13:32 cylon kernel: [  131.260139] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows/system32
Aug 16 18:13:32 cylon kernel: [  131.260429] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows/system32
Aug 16 18:13:32 cylon kernel: [  131.260779] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows/system32
Aug 16 18:13:32 cylon kernel: [  131.297356] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/Program Files/uTorrent
Aug 16 18:13:32 cylon kernel: [  131.297556] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich
Aug 16 18:13:32 cylon kernel: [  131.297802] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows/system32
Aug 16 18:13:32 cylon kernel: [  131.314272] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows/system
Aug 16 18:13:32 cylon kernel: [  131.314705] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows
Aug 16 18:13:32 cylon kernel: [  131.315454] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows/system32
Aug 16 18:13:32 cylon kernel: [  131.316096] ioctl32(uTorrent.exe:6106): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows

```

And another time I got this.

```

Aug 15 18:21:35 cylon kernel: [  120.135510] ioctl32(uTorrent.exe:6033): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows/system32
Aug 15 18:21:35 cylon kernel: [  120.135643] ioctl32(uTorrent.exe:6033): Unknown cmd fd(9) cmd(82187201){02} arg(00221000) on /home/rich/.wine/drive_c/windows
Aug 15 18:30:14 cylon kernel: [  638.525686] Losing some ticks... checking if CPU frequency changed.
Aug 15 19:20:22 cylon kernel: [ 3643.184297]  CIFS VFS: server not responding
Aug 15 19:20:22 cylon kernel: [ 3643.184304]  CIFS VFS: No response for cmd 114 mid 1146
Aug 15 22:00:22 cylon kernel: [13231.642818]  CIFS VFS: server not responding
Aug 15 22:00:22 cylon kernel: [13231.642826]  CIFS VFS: No response for cmd 114 mid 1148
Aug 15 22:19:22 cylon kernel: [14370.284039]  CIFS VFS: server not responding
Aug 15 22:19:22 cylon kernel: [14370.284046]  CIFS VFS: No response for cmd 114 mid 251
Aug 16 02:38:59 cylon kernel: [29931.210780] warning: many lost ticks.
Aug 16 02:38:59 cylon kernel: [29931.210783] Your time source seems to be instable or some driver is hogging interupts
Aug 16 02:38:59 cylon kernel: [29931.210792] rip __do_softirq+0x54/0xd0
```

AMD cool'n'quite is disabled. The system specs:

DFI Lan Party UT SLI-D
AMD Althon X2 3800+
2GB PC4000 RAM

4 hard drives are attached using a promise SATA2 TX4 adaptor
and two harddrives are attached using the onboard sata ports.

the raid 5 goes accross the motherboard's ports and the controller.


Anyone got any ideas?

Thanks,

Rich :)

I think, not 100% sure, but since wine is a windows application layer. It may have file size limits like windows. 15gb may be to big. You might want to start up a linux bit torrent clicnt to check the file.

---

### Post by RichGuk on 2007-08-17
I've tried doing the same using Azureus and it got a little further into re-checking but the system still locks up. I'll try running memtest tonight.

Anyone got any other ideas?

Thanks,

Rich

---

### Post by reverend_HH on 2007-11-12
i've had this happen to me a few times already but not when checking. it seems to just randomly freeze if i leave it for sometime, there have only been a couple of times when it completely locked the system and i had to restart it. im running wine version 0.9.41 and a 32bit OS if that makes any difference.

---

### Post by fastest963 on 2008-01-02
try this:
open terminal

winecfg

Applications tab -> Change to Windows XP
Addlications tab -> Add Application -> <utorrent.exe>

That Helped Me!
Also, you might try adding some dlls to the libraries tab?

---

