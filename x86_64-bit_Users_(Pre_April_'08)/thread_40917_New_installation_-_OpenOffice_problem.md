---
title: "New installation - OpenOffice problem"
date: 2005-06-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by wiraone on 2005-06-11
Hi all,

I've just got my AMD64 configured yesterday, spent until 2:30am in the morning trying to get Ubuntu64 working .. Thought everything should be alright, but now .. I couldn't run OpenOffice at all .. I'm getting the following error messages:

> mmisnan@wiraone:~$ oowriter
/usr/bin/oowriter: line 306: /usr/lib/openoffice/program/setofficelang.bin: No such file or directory
/usr/lib/openoffice/program/soffice: line 232: /usr/lib/openoffice/program/pagein: No such file or directory
/usr/lib/openoffice/program/soffice.bin.real: error while loading shared libraries: libvcl645li.so: cannot open shared object file: 
No such file or directory

What packages that I missed? I've this installed:

Version: 1.1.3-8ubuntu2.3

---

### Post by wiraone on 2005-06-11
Replying to my own post .. it is alright, I went back to the previous version and everything goes back to normal. It seems the updated openoffice has problem with many missing files ..

---

### Post by pmiddlem on 2005-06-12
[QUOTE=wiraone]Replying to my own post .. it is alright, I went back to the previous version and everything goes back to normal. It seems the updated openoffice has problem with many missing files ..[/QUOTE]


Hi Wiraone
I too am a newcomer and find that I have the same problem with Open Office.  I downloaded the Ubuntu AMD64 and loaded it today.
How did you get back to the previous version of Open Office?

Ta

---

### Post by wiraone on 2005-06-12
The easiest is to remove and reinstall openoffice .. but since I've so much problem, I went to install the whole Ubuntu32 .. but came back again to Ubuntu64 and I didn't do the upgrade .. anyway, you could do force version in Synaptic .. I haven't try it but my guess is .. it should work. BTW, I saw more files from security's repository .. check if your openoffice.org-bin is the latest .. , if not, update it .. it should solve this problem,

---

### Post by pmiddlem on 2005-06-12
Thanks
I will try try update first.

---

### Post by rsw on 2005-06-12
# dpkg -S /usr/lib/openoffice/program/setofficelang.bin
openoffice.org-bin: /usr/lib/openoffice/program/setofficelang.bin

# dpkg -l | grep openoffice
ii  openoffice.org 1.1.3-8ubuntu2 high-quality office productivity suite
ii  openoffice.org 1.1.3-8ubuntu2 OpenOffice.org office suite binary files
ii  openoffice.org 1.1.3-3+1ubunt Debian specific parts of OpenOffice.org
ii  openoffice.org 1.1.3-8ubuntu2 Gtk UI Plugin and GNOME File Picker for Open
ii  openoffice.org 1.1+20040420-2 OpenOffice.org office suite help (English)
ii  openoffice.org 20030813-3ubun English (GB) hyphenation pattern for OpenOff
ii  openoffice.org 20030813-3ubun English (US) hyphenation pattern for OpenOff
ii  openoffice.org 1.1.3-8ubuntu2 English (US) language package for OpenOffice
ii  openoffice.org 1.1.3-8ubuntu2 English (US) Thesaurus for OpenOffice.org

---

