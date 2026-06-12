---
title: "PSP&lt;-------&gt; USB connection problem"
date: 2009-03-25
forum: x86 64-bit Users
---

### Post by Chame_Wizard on 2009-03-25
Hello Good evening,

I bought today a PSP-2000(Ice Silver Slim&Lite),which works fine.

However,when I am plugging my PSP to my PC,my PC doesn't recognize the PSP as USB device immediately.

Instead ,it's keep trying to connect to the PSP(the PSP is then using USB mode),while the memory stick inside the PSP works good.

The stick is a San Disk 2 Ultra Memory Stick PRO Duo 8GB.:lolflag:
PSP firmware is 4.01.


So what cause the problem?Am I doing something wrong?:confused:

---

### Post by scottuss on 2009-03-25
I'm confused, does the Memory Stick show up as a USB device at all on your computer? What's the output of ```
lsusb
``` when the PSP is plugged in and in USB mode.

Also, just so you know, the actual PSP won't come up as a device, just the Memory Stick inside it.

---

### Post by Chame_Wizard on 2009-03-25
```

Bus 004 Device 011: ID 054c:02d2 Sony Corp. PSP
Bus 004 Device 002: ID 1058:0901 Western Digital Technologies, Inc. MyBook External HDD
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 04f3:0212 Elan Microelectronics Corp.
Bus 002 Device 003: ID 062a:0201 Creative Labs Defender Office Keyboard (K7310) S Zodiak KM-9010
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

my device notifier is blank and dolphin crashes:confused::(.

---

### Post by Chame_Wizard on 2009-03-26
When i plug the PSP in the PC of the school,it's work good.

maybe beause the school is using WIN XP Pro:lolflag:

---

### Post by scottuss on 2009-03-26
> **Chame_Wizard said:**
> When i plug the PSP in the PC of the school,it's work good.

maybe beause the school is using WIN XP Pro:lolflag:


Well Linux has picked up your PSP, the first entry is for it. Sounds like the file manager is having issues. Have you tried using a different file manager?

---

### Post by Chame_Wizard on 2009-03-26
Just came home,seems to work fine now.:popcorn:

```

chrishi@JMWF:~$ lsusb
Bus 004 Device 005: ID 054c:02d2 Sony Corp. PSP
Bus 004 Device 002: ID 1058:0901 Western Digital Technologies, Inc. MyBook External HDD
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 04f3:0212 Elan Microelectronics Corp.
Bus 002 Device 003: ID 062a:0201 Creative Labs Defender Office Keyboard (K7310) S Zodiak KM-9010
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by Chame_Wizard on 2009-03-26
```
chrishi@JMWF:~$ lsusb
Bus 004 Device 009: ID 054c:02d2 Sony Corp. PSP
Bus 004 Device 002: ID 1058:0901 Western Digital Technologies, Inc. MyBook External HDD
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 04f3:0212 Elan Microelectronics Corp.
Bus 002 Device 003: ID 062a:0201 Creative Labs Defender Office Keyboard (K7310) S Zodiak KM-9010
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

now what??:confused::(

---

