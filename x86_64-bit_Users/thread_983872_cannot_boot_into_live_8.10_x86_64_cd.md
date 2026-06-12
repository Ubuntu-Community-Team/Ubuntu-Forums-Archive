---
title: "cannot boot into live 8.10 x86_64 cd"
date: 2008-11-16
forum: x86 64-bit Users
---

### Post by adityadeva on 2008-11-16
:confused:

I can't boot into live cd desktop in my compaq laptop cq50-au106 using 8.10 amd 64 version. it hangs. configuration of my  laptop is amd 64 x2 1.9 Ghz, 3 gb ddr2 ram, 160 gb sata drive. 8.4.01 32 bit is working fine. athreos wificard. is also present 

**Pls help me out**

---

### Post by Linux user 66 on 2008-11-16
I see you've reported this before:

[http://georgia.ubuntuforums.org/showthread.php?t=966104](http://georgia.ubuntuforums.org/showthread.php?t=966104)

I was about to suggest that you press F6 twice in the CD boot menu to try booting with different options enabled (like acpi=off, noapic, etc.), but you've already tried that. 

This should probably be reported as a bug here:

[https://bugs.launchpad.net/ubuntu/+source/linux](https://bugs.launchpad.net/ubuntu/+source/linux)

---

### Post by felker2 on 2008-11-16
> **adityadeva said:**
> :confused:

I can't boot into live cd desktop in my compaq laptop cq50-au106 using 8.10 amd 64 version. it hangs. configuration of my  laptop is amd 64 x2 1.9 Ghz, 3 gb ddr2 ram, 160 gb sata drive. 8.4.01 32 bit is working fine. athreos wificard. is also present 

**Pls help me out**

"it hangs" is a bit too little information. Where does it hang? What do you see?

Advice:
1) use the "safe boot" from the boot option list to see what happens
and/or
2) remove "quiet splash" from the normal boot option list (use "e" to edit).

HTH

---

