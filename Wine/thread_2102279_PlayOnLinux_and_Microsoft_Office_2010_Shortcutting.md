---
title: "PlayOnLinux and Microsoft Office 2010 Shortcutting"
date: 2013-01-06
forum: Wine
---

### Post by SirLouen on 2013-01-06
I've found an strange issue: Everytime I open and **save** a microsoft office document file (docx, pptx or xlsx) with my Office 2010 tools instaled on PlayOnLinux, the system automatically creates a new file as a .Ink shortcut in the folder where the file exists.

Example, if the document is in /home/user/documents/myfile.docx it will create in the same directory:
myfile.docx.ink
myfile.docx (2).ink
myfile.docx (3).ink

I can't understand why is this happening, I've been googling around but found anything regarding this issue, any ideas?

---

### Post by fx_viallon on 2013-06-04
same problem here, using Ubuntu 13.04 64bits, PlayonLinux 4.2.1, Wine 1.5.16, Office 2010 (14.0.6024.1000) SP1 MSO (14.0.6023.1000).
However, in my case, the .ink file is not systematically created in the same directory. Sometimes it is, sometimes it appears in /home/user/. When or why it does this remains a mystery.

---

