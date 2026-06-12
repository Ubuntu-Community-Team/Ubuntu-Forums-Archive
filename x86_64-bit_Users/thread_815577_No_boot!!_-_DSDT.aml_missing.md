---
title: "No boot!! - DSDT.aml missing"
date: 2008-06-01
forum: x86 64-bit Users
---

### Post by jecompton on 2008-06-01
I can't get my machine to boot using any of my grub entries (including recovery modes and a win2k). I can't even boot from a cdrom.

When I try to boot from a recovery mode I get more information, but it halts on the following step:
```
ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
```

This is on a compaq presario v5000 laptop. :(

---

### Post by jecompton on 2008-06-01
Well, I fixed it I guess...

I just unplugged my logitech usb laser mouse and rebooted. I have no idea why it worked, but it did.

---

### Post by trepid666 on 2009-02-15
> **jecompton said:**
> I can't get my machine to boot using any of my grub entries (including recovery modes and a win2k). I can't even boot from a cdrom.

When I try to boot from a recovery mode I get more information, but it halts on the following step:
```
ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
```

This is on a compaq presario v5000 laptop. :(



I get this error at start-up as well, but it doesn't affect the boot.
Just noticed it actually.

---

### Post by Yellow Pasque on 2009-02-15
> The purpose of this optional kernel feature, enabled by "CONFIG_ACPI_CUSTOM_DSDT_INITRD=y" in the kernel .config at build-time, is to allow the user to replace the BIOS Advanced Configuration & Power Interface (ACPI) Differentiated System Description Table (DSDT) with one that has been modified to solve problems in the BIOS shipped by manufacturers.

The message you see is correct. As far as the kernel is concerned it is an error because it is told to expect to find a replacement DSDT.aml and it isn't there. However the message could be altered somewhat to make it sound less harsh.

Put succinctly, you **should** experience this "error" unless you're using a custom DSDT. The wording of this kernel message was changed in Ubuntu 8.10/Intrepid because of people reporting errors such as:
[https://launchpad.net/ubuntu/+source/initrd-tools/+bug/58386](https://launchpad.net/ubuntu/+source/initrd-tools/+bug/58386)

This warning message had nothing to do with the OP's issue, and users should look elsewhere for the cause of their issues.

---

