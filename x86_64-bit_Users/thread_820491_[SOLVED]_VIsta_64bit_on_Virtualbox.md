---
title: "[SOLVED] VIsta 64bit on Virtualbox"
date: 2008-06-06
forum: x86 64-bit Users
---

### Post by argail1980 on 2008-06-06
Hi everyone,
I'm running hardy 64bit desktop on an intel core 2 duo E6750@2.66GHz. Now I want to (let's call it "have to") install Vista in a Virtual box (version 1.6.2, installed the binary package). The Developer HP says it is supported, but everytime I start the maschine, the istallation routine stops and says the cpu did not support 64bit.

Am I making a stupid mistake, do I have to enable 64bit somehow? could that be remains from the installation of an older VBox version?

Thanks for helping

---

### Post by Kilz on 2008-06-06
> **argail1980 said:**
> Hi everyone,
I'm running hardy 64bit desktop on an intel core 2 duo E6750@2.66GHz. Now I want to (let's call it "have to") install Vista in a Virtual box (version 1.6.2, installed the binary package). The Developer HP says it is supported, but everytime I start the maschine, the istallation routine stops and says the cpu did not support 64bit.

Am I making a stupid mistake, do I have to enable 64bit somehow? could that be remains from the installation of an older VBox version?

Thanks for helping

No you didnt make any mistakes. [Virtualbox cant run 64bit operating systems.]("http://ubuntuforums.org/showthread.php?t=773248") If you need virtulazation that can run 64bit operating systems try [vmware server.]("https://help.ubuntu.com/community/VMware/Server")

---

### Post by insane_alien on 2008-06-06
try qemu. that can run 64-bit OSes.

---

### Post by argail1980 on 2008-06-09
I tried qemu, which gets me a little further than VirtualBox, but then Vista gives me a bluescreen during install. I favored VirtualBox to this point because it's really easy to use and works fine. I think I just have to move to VMWare.

Thanks for the help so far.

---

### Post by zimiq on 2008-06-09
Try kvm (is like qemu) with -no-kvm option.

---

### Post by argail1980 on 2008-06-09
ok, I'll try that. I'm takin a few days anyway, 'cause I don't have the PC here.

---

### Post by argail1980 on 2008-06-12
Hi everyone,

I kinda chose the easy solution. I simply got a 32bit version of windows and it works perfectly.

---

