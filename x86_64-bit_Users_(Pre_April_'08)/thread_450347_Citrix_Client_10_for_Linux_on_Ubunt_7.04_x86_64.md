---
title: "Citrix Client 10 for Linux on Ubunt 7.04 x86_64"
date: 2007-05-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by mickail on 2007-05-21
Hi!
Don't have much of experience with Linux.  Was previously using Ubuntu 6.10 x86.  Upgraded to Ubuntu 7.04 x64 few days back, am trying to install Citrix Client 10 on the system and getting the following error.  Citirx Client 9 used to work  fine on Ubuntu 6.10, same gives me the same error on Ubuntu 7.04 x64.  The error is as follows,

root@invind1:/home/mickailr/Inst/Citrix# ./setupwfc 
/home/mickailr/Inst/Citrix/./linuxx86/hinst: 236: /home/mickailr/Inst/Citrix/./linuxx86/echo_cmd: not found
/home/mickailr/Inst/Citrix/./linuxx86/hinst: 237: /home/mickailr/Inst/Citrix/./linuxx86/echo_cmd: not found
/home/mickailr/Inst/Citrix/./linuxx86/hinst: 238: /home/mickailr/Inst/Citrix/./linuxx86/echo_cmd: not found
/home/mickailr/Inst/Citrix/./linuxx86/hinst: 239: /home/mickailr/Inst/Citrix/./linuxx86/echo_cmd: not found
/home/mickailr/Inst/Citrix/./linuxx86/hinst: 4011: /home/mickailr/Inst/Citrix/./linuxx86/echo_cmd: not found
/home/mickailr/Inst/Citrix/./linuxx86/hinst: 4043: /home/mickailr/Inst/Citrix/./linuxx86/echo_cmd: not found
/home/mickailr/Inst/Citrix/./linuxx86/hinst: 4043: /home/mickailr/Inst/Citrix/./linuxx86/echo_cmd: not found
/home/mickailr/Inst/Citrix/./linuxx86/hinst: 4043: /home/mickailr/Inst/Citrix/./linuxx86/echo_cmd: not found
/home/mickailr/Inst/Citrix/./linuxx86/hinst: 4043: /home/mickailr/Inst/Citrix/./linuxx86/echo_cmd: not found

---

### Post by AreEK on 2007-09-23
You are probably missing som libraries. Try
sudo apt-get install ia32-libs

---

### Post by jeducana on 2007-10-31
Ok. Thanks a lot, It Works.

---

