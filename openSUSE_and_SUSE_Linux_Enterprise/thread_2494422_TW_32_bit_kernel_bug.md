---
title: "TW 32 bit: kernel bug ?"
date: 2024-01-16
forum: openSUSE and SUSE Linux Enterprise
---

### Post by maketopsite on 2024-01-16
USB stick not visible in output of
```
fdisk -l
```

Problem has appeared after latest upgrade. There is no USB cable.

```
Jan 16 07:53:21 maketopsite systemd[1]: Finished dracut initqueue hook.
Jan 16 07:53:21 maketopsite kernel: usb usb4-port1: unable to enumerate USB device
Jan 16 07:53:21 maketopsite kernel: usb usb4-port1: Cannot enable. Maybe the USB cable is bad?
Jan 16 07:53:19 maketopsite kernel: usb usb4-port1: Cannot enable. Maybe the USB cable is bad?
Jan 16 07:53:17 maketopsite kernel: usb usb4-port1: attempt power cycle
Jan 16 07:53:17 maketopsite kernel: usb usb4-port1: Cannot enable. Maybe the USB cable is bad?
Jan 16 07:53:15 maketopsite kernel: usb usb4-port1: Cannot enable. Maybe the USB cable is bad?
Jan 16 07:53:13 maketopsite kernel: usb usb4-port1: unable to enumerate USB device
Jan 16 07:53:13 maketopsite kernel: usb 4-1: device not accepting address 9, error -62
Jan 16 07:53:13 maketopsite kernel: xhci_hcd 0000:02:00.0: Timeout while waiting for setup device command
Jan 16 07:53:08 maketopsite kernel: usb 4-1: Device not responding to setup address.
Jan 16 07:53:08 maketopsite kernel: usb 4-1: new high-speed USB device number 9 using xhci_hcd
Jan 16 07:53:08 maketopsite kernel: usb usb4-port1: Cannot enable. Maybe the USB cable is bad?
Jan 16 07:53:06 maketopsite kernel: usb usb4-port1: attempt power cycle
Jan 16 07:53:06 maketopsite kernel: usb usb4-port1: Cannot enable. Maybe the USB cable is bad?
Jan 16 07:53:04 maketopsite kernel: usb usb4-port1: Cannot enable. Maybe the USB cable is bad?
Jan 16 07:53:01 maketopsite kernel: usb usb4-port1: unable to enumerate USB device
Jan 16 07:53:01 maketopsite kernel: usb 4-1: device not accepting address 5, error -62
Jan 16 07:53:01 maketopsite kernel: xhci_hcd 0000:02:00.0: Timeout while waiting for setup device command
Jan 16 07:52:56 maketopsite kernel: usb 4-1: Device not responding to setup address.
Jan 16 07:52:56 maketopsite kernel: usb 4-1: new high-speed USB device number 5 using xhci_hcd
Jan 16 07:52:55 maketopsite kernel: usb 4-1: device not accepting address 4, error -62
Jan 16 07:52:55 maketopsite kernel: xhci_hcd 0000:02:00.0: Timeout while waiting for setup device command
Jan 16 07:52:49 maketopsite kernel: usb 4-1: Device not responding to setup address.
Jan 16 07:52:49 maketopsite kernel: usb 4-1: new high-speed USB device number 4 using xhci_hcd
Jan 16 07:52:48 maketopsite kernel: usb usb4-port1: attempt power cycle
Jan 16 07:52:48 maketopsite kernel: usb usb4-port1: Cannot enable. Maybe the USB cable is bad?
Jan 16 07:52:46 maketopsite kernel: xhci_hcd 0000:02:00.0: WARN Event TRB for slot 2 ep 0 with no TDs queued?
Jan 16 07:52:31 maketopsite kernel: [drm] amdgpu kernel modesetting enabled.
Jan 16 07:52:30 maketopsite kernel: usb 4-1: device descriptor read/64, error -71
Jan 16 07:52:30 maketopsite kernel: usb 4-1: new high-speed USB device number 3 using xhci_hcd
Jan 16 07:52:30 maketopsite kernel: usb usb4-port1: Cannot enable. Maybe the USB cable is bad?
Jan 16 07:52:30 maketopsite systemd[1]: Reached target Initrd Root Device.

maketopsite@maketopsite:~> uname -a
Linux maketopsite 6.6.11-1-pae #1 SMP PREEMPT_DYNAMIC Thu Jan 11 08:01:39 UTC 2024 (05ae4ad) i686 athlon i386 GNU/Linux
```

---

### Post by maketopsite on 2024-01-21
There is no problem on another port.

---

