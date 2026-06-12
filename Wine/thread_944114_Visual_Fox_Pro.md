---
title: "Visual Fox Pro"
date: 2008-10-11
forum: Wine
---

### Post by PoopyTheJ on 2008-10-11
Ok, I'm working with my company to attempt to migrate to Ubuntu. Currently our IMS and POS is built using VFP7, the database simply will not run without it. The company actually uses a moderately modified version of VFP7 which I don;t really understand everything changed just enough to understand it's slightly off from a standard install. Anyways, they gave me the installer for their VFP7 environment and it installed fine, however when attempting to run the IMS program it can't find the .dbf and .dbc files it wants to use. It's looking outside the standard wine directory almost as though it recognizes it's on a different OS. It's truly wierd. Anyways when attempting to start the program it's looking for the .dbf and .dbc files in /home/username/ and not at all within the so called "C:" directory that Wine uses. What am I missing here, any idea on where to start would be very helpful. This is probably far beyond my level of expertise, however if I don't try the difficult things I'll never learn anything. It's not a rush, and I'll take as much time to learn what I need to know, and I know it's a lot, however if anyone wouldn't mind taking me under their wing so to speak and getting me started on the right path I'd really appreciate it. Let me know what other info I can provide as well to help.
Thanks!

---

### Post by asdfoo on 2008-10-11
> **PoopyTheJ said:**
> Ok, I'm working with my company to attempt to migrate to Ubuntu. Currently our IMS and POS is built using VFP7, the database simply will not run without it. The company actually uses a moderately modified version of VFP7 which I don;t really understand everything changed just enough to understand it's slightly off from a standard install. Anyways, they gave me the installer for their VFP7 environment and it installed fine, however when attempting to run the IMS program it can't find the .dbf and .dbc files it wants to use. It's looking outside the standard wine directory almost as though it recognizes it's on a different OS. It's truly wierd. Anyways when attempting to start the program it's looking for the .dbf and .dbc files in /home/username/ and not at all within the so called "C:" directory that Wine uses. What am I missing here, any idea on where to start would be very helpful. This is probably far beyond my level of expertise, however if I don't try the difficult things I'll never learn anything. It's not a rush, and I'll take as much time to learn what I need to know, and I know it's a lot, however if anyone wouldn't mind taking me under their wing so to speak and getting me started on the right path I'd really appreciate it. Let me know what other info I can provide as well to help.
Thanks!

Hi

Well, the only reason it might be looking your home directory is that Z: is mapped to /home/username so perhaps it's trying to search all drives...

If I were attempting this, I would first make sure that I can do a successful install on a fresh install of Windows and if that goes to plan then you can then say that the issue is with Wine.

The reason I say this, is I know all too well this sort of "non-standard" modifications for ERP type software and that it can be a headache when sometimes there are registry keys to be set or slight changes to configuration files when reinstalling from scratch.

---

### Post by PoopyTheJ on 2009-01-20
I'm going to ressurect this simply because I got the directory issue worked out, however when attempting to access a database/table which is remote through our POS system I get a "OLE error code 0x80004001: Unknown COM status code." Error. Anyone know a good place to start looking to resolve this. I tried updated VFP to 9 but that just doesn't fly with this program, I'm stuck with 7.

---

