---
title: "Problems with vital researching tools!"
date: 2007-01-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by neo-monarchist on 2007-01-21
I've experienced two large obstacles with formats on Ubuntu Linux. If it helps, I am running Ubuntu 6.06 LTS on a hp Pavilion dv6000 laptop with an Intel Core 2 Duo processor.

1) My USB drive does not work as it should with Linux. Primarily, when I copy a file to my USB drive, it is essentially corrupt - 0kb with no data. The second issue is that I can not delete files on the USB drive. When I was managing my USB drive with Windows, what I had "deleted" was invisible on my Ubuntu machine and still existed on the USB drive as a ".username/Trash" folder. I absolutely can not use any other alternative - I have to transport files to and from school at times. 

2) The two word processors that I have used, OpenOffice.org and AbiWord, both have problems recognizing files that were saved from a Windows machine. I had some documents that were saved as .doc using WordPerfect for Windows, and upon transferring them, they would not open as .doc - my machine forces them into .rtf format. I changed the file extension to .rtf as demanded by my machine, and this allowed them to open as instructed. However, after I had made changes the files (such as correcting typos), they immediately stopped functioning as .rtf as well, and instead said that it was (according to my memory) an "executable text file", which, from what I have gathered with my Ubuntu experiences so far, means "is not going to run properly" (and in fact did not run properly). I need to be able to save as .doc, .rtf or another format that is compatible with MS-Word due to its ubiquity. In the past, I could manage to use .wpd without concern, but it is highly unlikely that any format specific to AbiWord or OpenOffice.org will be compatible with MS-Word due to Microsoft's reliance on Office's standardization to sell their software.

I have greatly enjoyed my experiences with the Ubuntu OS so far, but if I can not solve these two problems for means of smooth academic work then I will be, much against my wishes and philosophical beliefs, forced to use Windows Vista when it is released due to my need for efficient word processing. I hope this is not the case and I hope that, through assistance, I can solve these problems.

---

### Post by RAOF on 2007-01-22
I'm not sure about the second problem (which may well be an honest-to-goodness bug), but the first is probably because you are not unmounting your usb drive (Safely-remove-hardware, in windows-speak).  The Linux kernel aggressively caches writes to USB drives for a number of reasons, including speed, and the fact that the flash drive can be written to a limited number of times.  If you pull it out without unmounting it (or "eject"ing it), by right-clicking on it's icon and selecting "eject", there's no guarantee your data was properly written to the device.

This advice is also appropriate in windows, just less so.

Your ".username/Trash" folder is like the recycle bin in Windows, or the Trash in MacOS.  You can either manually delete this folder (you need to show hidden folders [ctrl-H] to see it) or you should be able to empty the trash.

---

### Post by neo-monarchist2 on 2007-01-22
(This is the same person, I lost the password for the original account)

I've managed to solve the problem of the regressing word documents. It appears that this is due to the files being transferred through USB. For some reason, both text files and word documents have had problems when transferring through USB.

Which ultimately roots my problem in the USB stick. I still have not managed to solve the issue of the unwritable USB stick. The problem seems unique from others - I can "write" files on it, but it does not actually affect the USB stick. For example, I can click on a file, click "move to trash" and it will vanish, but when I load the USB stick on Windows the file will be in a trash folder that was created on the USB stick. In the same vein, when I write a file onto the USB stick, it is a mere 0kb file when transferred to Windows.

I don't know how I can possibly get around this. I can't really use Windows just for a USB stick, and I can't use writable CDs because I transfer media too much. This is quite the problematic situation.

---

### Post by neo-monarchist2 on 2007-01-22
Ah, your response is a minute short from mine. I'll try that immediately and post the results.

---

