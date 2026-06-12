---
title: "&quot;This kernal requires an x86-64 cpu&quot; - 64bit VPC and Virtual Box"
date: 2008-12-14
forum: x86 64-bit Users
---

### Post by Byrong_777 on 2008-12-14
Hello I am new with Linux and Ubuntu and wanted to see what the fuss is all about but am unable to install the 64 bit version as a guest on my pc.

I keep getting the "This kernal requires an x86-64 cpu" message when installing ubuntu on virtual machines.  I have tried both the 64 bit version of VPC and virtual box. My host pc has an AMD Phenom 9750 64 bit quadcore. I have no clue why its telling me there is no 64 bit cpu.  

Is the cpu in the 64 bit version of virtual box and vpc 32 bit?  Is there some issue with newer AMD 64bit CPU's.  Am I just stupid....whats the deal....HELP!!!! 

The 32 bit version is smokin good in virual box.. i would like to learn to overcome this issue in case i see this again....

---

### Post by amauk on 2008-12-14
In the virtual machine settings, set "Enable VT-x/AMD-V" (under General > Advanced)

this will enable the virtual machine to use the CPU's hardware virtualisation extensions

You should now be able to boot a 64-bit OS in VirtualBox

---

### Post by PatrickVogeli on 2008-12-14
is the host OS 64 bit? if it isn't, then you won't be able to use 64 bits guest.

---

