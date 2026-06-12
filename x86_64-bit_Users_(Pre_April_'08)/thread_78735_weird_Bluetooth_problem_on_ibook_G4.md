---
title: "weird Bluetooth problem on ibook G4"
date: 2005-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by refdoc on 2005-10-18
I had bluetooth working absolutely fine on hoary and up until recently on breezy. during one of teh last updates ( I am not sure when as I do not tend to use bluetooth a lot)  it ceased working - at least at the GUI level.

The gnome bluetooth manager does not find anymore the device, despite it seemingly being recognised during boot up.

dmesg | grep Blue
[  281.642209] Bluetooth: Core ver 2.7
[  281.642233] Bluetooth: HCI device and connection manager initialized
[  281.642255] Bluetooth: HCI socket layer initialized
[  281.684055] Bluetooth: L2CAP ver 2.7
[  281.684067] Bluetooth: L2CAP socket layer initialized
[  281.725867] Bluetooth: RFCOMM ver 1.5
[  281.725890] Bluetooth: RFCOMM socket layer initialized
[  281.725911] Bluetooth: RFCOMM TTY layer initialized

rfcomm -a does not show any device though...

Teh device functions fine under OSX.

Any ideas?

Thanks

---

### Post by Jaapjan on 2005-10-19
This is a bug and has already been filed in bugzilla. You can look for it. The developer doesn't have a machine himself though, so ...

(it has originally been filed by me in fact)

---

### Post by refdoc on 2005-10-23
sudo hid2hci resolves it!

---

