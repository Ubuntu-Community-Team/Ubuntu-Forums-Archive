---
title: "Enumerated Font Name Differs Between Windows &amp; Ubuntu"
date: 2013-12-15
forum: Wine
---

### Post by sudleyplace on 2013-12-15
I have a font file "SImPL-Medium.ttf" whose internal name is "SImPL medium".  On a WinXP, Win7/64, and Ubuntu/64 systems, when I run my app (under Wine64 1.4 on the Ubuntu/64 system), it first searches to see if that font has been installed as yet using the Windows API <EnumFonts>.  From debugging messages inside <EnumFonts>, I can see that under both WinXP and Win7/64 the incoming enumerated font name is "SImPL medium" (as expected), but with Ubuntu/64 with Wine64, the incoming enumerated font name is "SImPL medium Medium".  As my program is looking for "SImPL medium", it constantly tries to install the font (which doesn't succeed, but that's another matter -- one problem at a time).  Version 1.4 is the latest 64-bit Wine available from the Synaptics Package Manager.

Any idea of why the enumerated internal font names are different between the two Windows systems and Ubuntu?

---

### Post by sudleyplace on 2013-12-18
Upgraded the OS to 12.10 and Wine to 1.6 and all is well.

---

