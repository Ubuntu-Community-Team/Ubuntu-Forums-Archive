---
title: "Asus M2N-E Help =)"
date: 2007-05-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cormin on 2007-05-25
does fiesty fawn support the onboard ethernet for asus M2N-E ?  im stuck on getting an ip which is very odd :(

---

### Post by ©TriMoon® on 2007-05-25
Try to narrow down your problem and post more &#305;nfo about your onboard card, l&#305;ke pci device info etc, so others can help you more focused.
fe: &#304;f you can get your onboard card working using a manual &#304;P setup, then there is no problem with the drivers.

*ed&#305;t*
&#304;f you are stuck at the installer doing its DHCP config, then you could try some kernel options to enable you to do a static-IP setup.
fe: "priority=low" appended to the kernel options, will enable "expert mode", asking you all kind of questions that are normaly auto-fullfilled by the installer...

---

### Post by Cormin on 2007-05-25
i dont have a network pci device, ive been using my onboard ethernet thru winblows for a while... but i just remember seeing that neither sound, nor ethernet were supported on the M2N-E... luckily enough for me i have a pci sound card =P

just no internet


EDIT:  heres a link to my mobo

```
http://www.newegg.com/Product/Product.aspx?Item=N82E16813131022
```


im sorry if im a little slow right now, havent slept in 2 days ><

---

### Post by Cormin on 2007-05-25
it just hangs on ip configuration started   (57%)

ive tried so many different settings, idk whats up :(

---

### Post by ©TriMoon® on 2007-05-25
The PC&#304; reference i used in my reply didn´t imply i refered to an external pci card...
Onboard cards are all accessed using the pci bus ;)
Without me knowing if your MB is or isn´t supported, which i don´t, i just tried to guide you into a direction where others might be able to help you better...

Even if your MB isn´t supported at this moment in time, that info could be used to get it supported &#305;n feature ;)
> **Cormin said:**
> it just hangs on ip configuration started   (57%)

ive tried so many different settings, idk whats up :(
Try todo an expert-install like i said using kernel boot options, who knows maybe you can get further in the install process that way...

---

### Post by Cormin on 2007-05-25
ill have to try that tomarrow, after i get some sleep, right now i cant even think of what an expert-install is... so ill be back, thanks for your help tho :popcorn:

---

### Post by nss0000 on 2007-05-25
My ASUS-m2n ethr_port is NOT supported by Dapperx64. I installed a legacy NIC and it works without issue.

nss
******

---

