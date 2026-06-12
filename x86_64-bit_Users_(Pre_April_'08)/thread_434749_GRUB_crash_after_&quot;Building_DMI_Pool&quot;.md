---
title: "GRUB crash after &quot;Building DMI Pool&quot;"
date: 2007-05-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by mschmoelzer on 2007-05-06
Hi,

i am expieriencing boot problems on an AMD64 machine with Ubuntu Feisty: The whole BIOS POST stuff runs normally, until it displays either "Verifying DMI Pool Data" or "Building DMI Pool.....Flash ROM protected". In the first case, after a few seconds of displaying this message, GRUB shows up and allows booting my Feisty installation or a Windows XP installation. In the latter case (after showing "Building DMI Pool.....Flash ROM protected", which occurs after changing some settings in the system's BIOS), GRUB displays "GRUB loading stage 1.5" and then hangs there forever. If I reset the computer and boot it again, the behavior is exactly the same: "Verifying DMI Pool Data" means the system will boot fine, "Building DMI Pool.....Flash ROM protected" means the system will hang in a few moments.

I have tried the following to solve the problem:
[list][*]Reinstalling GRUB to the MBR of the hard disk from the Feisty installation and from the Desktop CD
[*]Upgrading the BIOS to the newest version F8
[*]Deactivating onboard components (unused S-ATA-channels, parallel port, serial port)
[*]Eliminating possible hardware errors (I have installed Ubuntu on an identical system)
[*]Installing an older version of GRUB failed (would not compile)
[*]Installing GRUB2 1.95 failed (losing Bootloader NTFS support would be acceptable because I use Windows only for a few Applications that do not run on Linux) -> will not compile on AMD64 system
[*]Installing LILO failed (did not recognize GCC compiler)[/list]

Nothing helped so far :(
Now I am absolutely clueless about what's wrong with the system - any help would be appreciated :)

**System specs**
-
AMD Athlon 64 X2 4000+ 65nm
Gigabyte GA-M57SLI-S4 Rev. 1.0
2GB Kingston 800MHz DDR2-RAM (2x 1GB)
Gainward BLISS 7600GS PCIe Graphics Card
Seagate Barracuda 7200.10 250GB 16MB Cache, S-ATA
rather old HP DVD-RW, P-ATA

---

### Post by pelish on 2007-05-07
Hi

I installed Feisty amd64a few days ago and have the very same problem. I didn't tried to solve it    but the reason i'm posting this is becouse i have very similar hardware configuration:

AMD Athlon 64 X2 3800+ AM2
Gigabyte GA-M57SLI-S4 Rev. 1.0
2GB Teamgroup 667MHz DDR2-RAM (2x 1GB)
Gigabyte 7600GT (GV-NX76T) PCIe Graphics Card
Seagate Barracuda 320GB, SATAII

and i think becouse i have the same motherboard it might have something to do with it!!

P.S.: I have the latest bios version installed (F8 -date:2007/03/20) and when i get "Building DMI Pool.....Flash ROM protected" grub still freezes.

Maybe this info can somehow help.

---

