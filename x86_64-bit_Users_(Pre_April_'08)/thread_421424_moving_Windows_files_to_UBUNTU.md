---
title: "moving Windows files to UBUNTU"
date: 2007-04-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by nss0000 on 2007-04-24
Gents:

I've got important text datafiles stored in various Windows formats(?) on floppy disks and a legacy WinME system. I want to transition these datafiles -- in a usable way -- to one of my UBUNTU boxes;  old Win-hardware will then be scrapped so I can rebuild into the valuable Antec tower case. 

I really don't want to lose/corrupt/bury...  these legacy datum, but re-incorporate it on modern kit and within the functions of UBUNTU ( I use DAPPER ) . What are my options for the transition? Bulletproof would be nice.

1) yes, I have a rarely_used USB ZIP-drive. Obscure *nix function.
2) yes, the boxes are eth-cabled to a router, but no LAN function. Non-trivial.
3) no, the WinME floppy function no longer works    

nss
*******

---

### Post by brew1brew on 2007-04-24
If you have IP working on the winME and Ubuntu boxes I would 

1. install SSH server on the Ubuntu box 
2. install winSCP on the winME box 
3. open an SFTP session from winME to Ubuntu
4. drag and drop files to the Ubuntu box

Les

---

