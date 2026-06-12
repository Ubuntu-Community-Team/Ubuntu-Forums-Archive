---
title: "NFS and ubuntu 64 problem - system freezes"
date: 2005-08-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by ispmarin on 2005-08-30
Hello all.
I have just finished installing a athlon amd64 on asus sli with nforce 4 chipset. I configured correctly the nis (I hope so!) and configured also nfs. I have installed the nfs-common and the nfs-server-kernel. I am trying to mount a nfs home from a fedora 2 box. The filesystem is correctly mounted, and the directories are correctly listed, but when I try to access any file inside the nfs home, the terminal that I am using just freezes. When I open a new terminal, using the root account, the system is still responding, but the terminal with my normal user using the nfs home is completely freezed. I cannot even kill the pid for that process from the freezed terminal. I have also installed the nforce drivers from nvidia, and the network is working correctly. I have tried to uninstall and install again the nfs several times, and even tried to use the nfs-user-kernel, with the same results. Just now I am trying to compile a new kernel (2.6.13) to see if it helps, but I am afraid it will not.

Any ideas...

Thank you!


Ivan

Update: The new kernel 2.6.13 did not solve the problem. I managed to get the error message from the terminal:
/nfs: server 172.26.10.34 not responding, still trying
But all the other machines that uses the same nfs server works correctly...

---

### Post by ispmarin on 2005-08-30
Hello all.
After a very frustrating afternoon, only one thing was left to do: do a dd from another machine with the exact same configuration that worked. The installation on both machines was the same, but in my box the network card worked intermitently. After a dd and some headaches, everything works now. Very frustrating. I have tried to install now the NFORCE driver from nvidia, and this driver screwed everything, so I just uninstalled and now I am using the module that the kernel autoloads. 
If anybody got any clue, i will thank you a lot...
bye.

Ivan

---

### Post by ispmarin on 2005-09-06
I will not give up!!!

---

