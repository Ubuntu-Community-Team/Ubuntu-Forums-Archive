---
title: "What successes with WIN firmware-update utilities in general?"
date: 2016-12-09
forum: Wine
---

### Post by bcschmerker on 2016-12-09
I have been unable to obtain information on upgrading firmware on a Mitsumi® FA404M combination disquette drive, Compact Flash interface, and SD/MMC/MS interface in the LinUX environment; the FA404M's Carry Computer Engineering USB 2.0 interface chip (ID: 07cc:0301) is incompatible with existing LinUX firmware-get/put binaries.  The few available closed-source binaries for the task, e.g. $USER/Downloads/FA404M-405MX_SDHC_FW9325.exe (courtesy OwlTech Ltd.), are all built for Microsoft® Windows® 5.*n* (XP 5.1.2600 to 5.2.3790 inclusive); several attempts to run the Executable cited in Windows 6.1.7601 failed with a "device not present" error.  Have others at these Forums attempted firmware updates to various hardware components in Wine; and if so, which releases had the best successes for what equipments?

---

### Post by bcschmerker on 2017-01-17
**Update:**  Wine installation on the Hot Rod gPC went without apparent incident.  The Mitsumi® FA404M on which I am attempting to upgrade firmware is described in sudo lsusb -d 07cc:0301 -v as follows:
```

Bus 001 Device 005: ID 07cc:0301 Carry Computer Eng., Co., Ltd 6-in-1 Card Reader
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x07cc Carry Computer Eng., Co., Ltd
  idProduct          0x0301 6-in-1 Card Reader
  bcdDevice            0.05
  iManufacturer           1         Ltd
  iProduct                2 Winter Ver1.3   
  iSerial                 3 392673724128
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              4 1.06.69.0630
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

```

Attempting wine $HOMEDIR/Downloads/FA404M-405MX_SDHC_FW9325.exe (provided by OwlTech Ltd. of Japan) from GNOME Terminal, unfortunately, failed to update the Carry Computer interface chip in the FA404M-BK; Terminal relayed the following error chain:
```
fixme:shell:SHAutoComplete stub
fixme:exec:SHELL_execute flags ignored: 0x00000180
fixme:win:RegisterDeviceNotificationA (hwnd=0x2006c, filter=0x33ea40,flags=0x00000000) returns a fake device notification handle!
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d004 (device=4 access=3 func=401 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d004 (device=4 access=3 func=401 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d004 (device=4 access=3 func=401 method=0)

```
What could give in this situation?

---

