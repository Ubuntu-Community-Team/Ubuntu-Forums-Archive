---
title: "Installing Steam With Wine (Bug)"
date: 2013-12-25
forum: Wine
---

### Post by viktor-hubinette on 2013-12-25
[COLOR=#333333][FONT=UbuntuRegular]Hi When i try to install steam with wine and winetricks its only says[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Checksum for /home/viktor/.cache/winetricks/steam/SteamInstall.msi did not match, retrying download[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]and[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]sha1sum mismatch! Rename /home/viktor/.cache/winetricks/steam/SteamInstall.msi and try again.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]and then it just closes down please can someone help me to fix this? thanks[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular](i open up winetricks and click on add app and i scrolling down to steam and then the things i said above happen)[/FONT][/COLOR]

---

### Post by The Cog on 2013-12-25
Moved to Wine sub-forum.

---

### Post by Mocker on 2013-12-27
This problem is caused by winetricks being out of date (the checksum it has for the steam installer seems out of date... one wonders why they bother keeping a checksum for it, or at the very least, why couldn;t they not hard code it, but instead retrieve it online...?). Anyhow, you can get around this by adding the Wine PPA software source to your system, doing an update, then upgrading wintricks. See [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

The problem is, this gets Steam installed... but it then crashes shortly after asking me to enter a verfification code that they email to me. This is teh detailed error message (or at least he start of it)

Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x7bc5787b).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7bc5787b ESP:06e5b29c EBP:06e5b384 EFLAGS:00210206(  R- --  I   - -P- )
 EAX:00000000 EBX:7bcc8000 ECX:00000000 EDX:00000010
 ESI:00000002 EDI:06e5b6c4
Stack dump:
0x06e5b29c:  06e5b308 06e5b3ec 0000000c 001cd608
0x06e5b2ac:  00000000 06e5b310 7bc4bc31 001cd620
0x06e5b2bc:  00000002 001cd608 00000001 00000000
0x06e5b2cc:  001cd620 06e5b310 7bc48937 00000000
0x06e5b2dc:  06e5b3e8 06e5b3f8 7bc33f00 00000354
0x06e5b2ec:  ffffffff 06e5b310 7bc34b47 00110064
Backtrace:
=>0 0x7bc5787b NtAdjustPrivilegesToken+0x1ed() in ntdll (0x06e5b38
. . .


I'll have to head over to the Wine site to see if anyone has solved this.

---

