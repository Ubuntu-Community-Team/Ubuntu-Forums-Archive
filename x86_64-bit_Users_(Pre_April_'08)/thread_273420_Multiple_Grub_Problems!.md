---
title: "Multiple Grub Problems!"
date: 2006-10-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by s_spiff on 2006-10-08
Well, I tried finding something on how to remove the grub but couldn't find anything that solves my problem : 
I have a x64windows xp running on a 40gb partition of a 80gb hdd. So I install DD x64 on the remaining 34.5 gb. The first install was done in OEM mode[ I don't know what it is, but wanted to give it a try. ]. I tried logging on, but the password kept giving a error. Anyways, I thought, this is stupid, so logged onto windows using the grub, and deleted my 34gb partition and rebooted.  the grub gave me an error naturally. So I reinstalled DD again this time including the grub in the 'text mode', and everything worked fine, except that now I have two grubs. The first one gives me a error and the  second one actually selects the OS. If someone could walk me through of making a clean install without damage to my Windows, I would highly appreciate it.](*,)

---

### Post by s_spiff on 2006-10-08
can someoe please help me in removing these grubs? and make a clean linux install?

---

### Post by juicemansam on 2006-10-09
You could try removing the existing bootloader that lives in the MBR from a DOS boot disk with *fdisk /mbr*. That will just restore the DOS/Windows bootloader.

---

### Post by s_spiff on 2006-10-10
hey thanks for the reply, I did try that using a windows setup cd and all using the restore menthod blah blah. didnt work. no mbr was replaced. So I just formatted my 80gb hdd, didnt have anything imp on it which wasn't backed up anyways. So thanks again, next time will give the dos route  shot ;)

---

