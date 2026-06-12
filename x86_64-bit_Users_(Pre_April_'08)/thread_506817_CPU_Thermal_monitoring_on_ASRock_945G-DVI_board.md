---
title: "CPU Thermal monitoring on ASRock 945G-DVI board"
date: 2007-07-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by nimrod_abing on 2007-07-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/120615](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/120615) [br].[/br] ---------------------------- [br].[/br] [br].[/br]                 Hello,

I just recently bought a new motherboard and CPU:

ASRock ConRoe945G-DVI
Intel Core 2 Duo E4300

I am running into an issue with ACPI thermal_zone. I think the following bug report summarizes this problem:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/120615](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/120615)

I have already flashed my motherboard's BIOS to the latest version (from factory provided v1.30 to v1.90) but still /proc/acpi/thermal_zone is empty.

Will be willing to provide more info if needed. For now, here is some info as stated in [https://wiki.ubuntu.com/KernelTeamBugPolicies:](https://wiki.ubuntu.com/KernelTeamBugPolicies:)

```
nimrod@iwojima:~$ cat /proc/cmdline 
root=UUID=bfb425a3-abb5-4f99-9179-909de0b6485d ro quiet splash
nimrod@iwojima:~$ uname -a
Linux iwojima 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux
nimrod@iwojima:~$ cat /proc/version_signature 
Ubuntu 2.6.20-16.29-generic
```dmesg and lspci -vvnn output is in the attachment.

---

