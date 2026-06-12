---
title: "CPU temp on 6.1"
date: 2007-05-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by colin59 on 2007-05-08
I have a Core 2 Duo proc, and i can't seem to get lm-sensors working. I've googled it and couldn't find an easy solution. I think one solution i found was to recompile the kernel, something a newbie like me does not know how to do. Is there any other solution?

---

### Post by DarkN00b on 2007-05-08
> **colin59 said:**
> I have a Core 2 Duo proc, and i can't seem to get lm-sensors working. I've googled it and couldn't find an easy solution. I think one solution i found was to recompile the kernel, something a newbie like me does not know how to do. Is there any other solution?

If you just want to see your cpu temp you can type

```
acpi -V
```

in a terminal window and it will give you your cpu temp. That's a capital V btw.

I use the 32 bit Ubuntu but this should work the same on 64.

Sorta off-topic: I wrote a script to be used with the doityourself addon for adesklets that displays this information on a continually updating basis. It ain't pretty to look at but it shows what I want to know. Actually it is just a modification of an existing script, but it uses acpi -V instead of lmsensors. Pic below:

---

### Post by colin59 on 2007-05-08
The script looks good. "no support for device type: thermal" is the message i get when i use that command.

---

### Post by DarkN00b on 2007-05-08
Its really just knocked together, plus you have to install adesklets and the doityourself addon to make it work. I'll post it here if you want it but like I said, its not pretty.

EDIT: I just re-read your post. The stupid script won't help you much if it can't read the temp from acpi. 

[img]http://www.cheesebuerger.de/images/smilie/konfus/c010.gif[/img]

Maybe your motherboard doesn't support acpi?

EDIT2: Cool! I just figured out how to make it semitransparent. :)

---

