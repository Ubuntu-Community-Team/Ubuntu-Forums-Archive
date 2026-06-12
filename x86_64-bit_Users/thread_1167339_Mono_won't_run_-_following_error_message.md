---
title: "Mono won't run - following error message"
date: 2009-05-22
forum: x86 64-bit Users
---

### Post by jeffcham on 2009-05-22
I'm running version 9.04 on my pc, when I try to run Mono from the menu the splash screen displays for a few seconds then disappears. When I run it from the terminal I get the following.

Any ideas on what the problem is

xxxxx@melb:~$ /usr/lib/monodevelop/bin/MonoDevelop.exe
WARNING [2009-05-23 08:49:36Z]: MonoDevelop failed to start. Rebuilding addins registry.

Unhandled Exception: System.InvalidOperationException: Add-in manager not initialized.
in <0x00058> Mono.Addins.AddinManager:CheckInitialized ()
in <0x00008> Mono.Addins.AddinManager:get_Registry ()
in <0x000bb> MonoDevelop.Startup.SharpDevelopMain:Main (System.String[] args)

---

### Post by directhex on 2009-05-23
Odd.

Try erasing ~/.config/MonoDevelop/addin*

---

### Post by jeffcham on 2009-05-23
Thanks for the reply however I've just checked ~/.config/MonoDevelop/ and there is nothing in there, so nothing to delete.


> **directhex said:**
> Odd.

Try erasing ~/.config/MonoDevelop/addin*

---

### Post by directhex on 2009-05-23
Strange. Can you write to that folder? Try "touch ~/.config/MonoDevelop/test"

---

### Post by jeffcham on 2009-05-23
Hi again,

No problem writing to the direcrtory. I have uninstalled it and tried reinstalling but still no luck.

I'm thinking that it is a problem with "Rebuilding addins registry" but what that means I'm not sure and what do I do to fix it.

---

### Post by directhex on 2009-05-23
> **jeffcham said:**
> Hi again,

No problem writing to the direcrtory. I have uninstalled it and tried reinstalling but still no luck.

I'm thinking that it is a problem with "Rebuilding addins registry" but what that means I'm not sure and what do I do to fix it.

It means, um, that it's rebuilding the addins registry. Which lives in ~/.config/MonoDevelop/addin*

---

### Post by jeffcham on 2009-05-24
I think I've got that part, it's fixing I'm now stuck on. Any suggestions?

> **directhex said:**
> It means, um, that it's rebuilding the addins registry. Which lives in ~/.config/MonoDevelop/addin*

---

### Post by jeffcham on 2009-06-01
I've gave up, backed up my system and rebuilt it. It's all working now.:D

---

