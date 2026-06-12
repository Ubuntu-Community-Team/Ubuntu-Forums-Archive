---
title: "MTP - can't connect to device after 9.10 upgrade"
date: 2009-11-15
forum: x86 64-bit Users
---

### Post by mashedbear on 2009-11-15
Hello,
I am having problems using Sony Walkman device following upgrade to 9.10. I use banshee-1.

When I run mtp-detect I get the following:

```
sudo mtp-detect 
libmtp version: 0.3.7

Listing raw device(s)
   Found 1 device(s):
   Sony: Walkman NWZ-B135 (054c:036e) @ bus 0, dev 10
Attempting to connect device(s)
PTP_ERROR_IO: Trying again after re-initializing USB interface
LIBMTP PANIC: Could not open session! (Return code 767)
  Try to reset the device.
Unable to open raw device 0
OK.

```

banshee log shows:
```
PTP_ERROR_IO: Trying again after re-initializing USB interface
LIBMTP PANIC: Could not open session! (Return code 767)
  Try to reset the device.
[Warn  10:36:53.858] Caught an exception - Connecting (in `Mtp')
  at Mtp.Error.CheckError (ErrorCode errorCode) [0x00000] 
  at Mtp.MtpDevice.GetConnectedDevices (System.IntPtr& list) [0x00000] 
  at Mtp.MtpDevice.Detect () [0x00000] 
  at Banshee.Dap.Mtp.MtpSource.DeviceInitialize (IDevice device) [0x00000] 
```

When the sony device is connected via usb banshee sleeps - futex_wait_queue_me - and process has to be killed.

Any help appreciated.

---

