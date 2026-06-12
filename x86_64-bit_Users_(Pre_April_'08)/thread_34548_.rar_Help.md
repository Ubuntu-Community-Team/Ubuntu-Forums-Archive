---
title: ".rar Help"
date: 2005-05-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by zxc on 2005-05-15
I don't know if anyone was having this problem but I couldn't get .rar files to work on my AMD64 Ubuntu Partition. I think it's a recognised problem?

If anyone has had this problem try downloading "unp" from synaptic and finding the file in terminal and typing "unp filename.rar".


This solved my problem. Thanks to **slept** for telling me how to do this.

---

### Post by bored2k on 2005-05-15
[QUOTE=zxc]I don't know if anyone was having this problem but I couldn't get .rar files to work on my AMD64 Ubuntu Partition. I think it's a recognised problem?

If anyone has had this problem try downloading "unp" from synaptic and finding the file in terminal and typing "unp filename.rar".


This solved my problem. Thanks to **slept** for telling me how to do this.[/QUOTE]
 Why dont you install rar or unrar-nonfree ? Or the rar from rarlabs?

---

### Post by zxc on 2005-05-16
As it didn't work for me so I checked out the AMD64 section and in this thread: [http://ubuntuforums.org/showthread.php?t=30303&highlight=rar](http://ubuntuforums.org/showthread.php?t=30303&highlight=rar) it mentioned there was a problem with the "Rar Archiver" so I used this alternative method.  ;-)

---

### Post by BigCdaAnswer3 on 2005-05-25
I needed the "rar" command for a program i was running so i got apt-got unrar-nonfree and symlinked the binary to /usr/bin/rar...works like a charm

---

### Post by rsw on 2005-05-25
i had no problems compiling unrar from rarlabs.

---

