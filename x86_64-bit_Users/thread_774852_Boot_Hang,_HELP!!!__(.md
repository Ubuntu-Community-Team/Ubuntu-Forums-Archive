---
title: "Boot Hang, HELP!!! : ("
date: 2008-04-29
forum: x86 64-bit Users
---

### Post by linuxfreak778 on 2008-04-29
I Have been trying to install Ubuntu 8.04 x86_x64 with wubi under Windows XP Pro SP2. I can't boot into Ubuntu. It just pauses once loading the sound, then it hangs starting the bluetooth. I've heard of issues before, but I couldn't find a solution. Help Please! :confused::confused::confused:

My system:
ECS A-780GM-A
AMD athlon 64 x2 4400
2 Gb ram
NEC optiarc 2ox lightscribe burner
Sound Blaster Live! Sound card (2000)

---

### Post by linuxfreak778 on 2008-04-29
oh and the last version of ubuntu i could ever install was 6.06 i think.

---

### Post by ago on 2008-04-30
You might need some acpi hacks and such and/or blacklist some hardware and/or disable bluetooth. Trying out the 32 bit version might also help. Try to boot in a more verbose mode (or in rescue mode) get the exact errors and a listing of your hardware via "lspci -vn". Also can you boot successfully from the Live CD? It does not really look wubi related though.

---

### Post by linuxfreak778 on 2008-04-30
no, i can't boot from the live CD either. I tried the 32 bit version but it does the same thing. other linux distro's work, just not ubuntu, the one i want to use. :(

---

