---
title: "Nvidia driver stop working after reboot! :("
date: 2006-02-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by selinake on 2006-02-12
So..you read the title...my nvidia driver stop working if i reboot :(
i can't start x. So i install Nvidia driver again and it work again..:S 
Can anybody help me with this? :rolleyes: 


Thanks,
Selina

---

### Post by Parkotron on 2006-02-12
You probably forgot to uninstall the packaged version that came with Ubuntu before you installed the new one. Try
```
sudo apt-get remove linux-restricted-modules-`uname -r`
```

---

### Post by selinake on 2006-02-12
Nope, it didn't work.....:(

---

### Post by codejunkie on 2006-02-12
[QUOTE=selinake]Nope, it didn't work.....:([/QUOTE]
running this in the terminal should fix it ```
sudo apt-get remove --purge nvidia*
```this will remove the conflicting nvidia packages in synaptic
if it still doesn't work you might have to completly remove and reinstall the nvidia driver you downloaded from [www.nvidia.com](www.nvidia.com) you can remove the nvidia driver like this. 
```
sudo nvidia-installer --uninstall
```
hope this helps.

---

### Post by selinake on 2006-02-12
Thanks a lot! 

sudo apt-get remove --purge nvidia*

it works :)

---

