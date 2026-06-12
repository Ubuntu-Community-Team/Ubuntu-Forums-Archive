---
title: "Freeze at Login Screen"
date: 2006-09-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by napsilan on 2006-09-13
My system is K/X/Ubuntu 64 bit, installed in a fakeraid 0 using the fakeraid wiki.  I recently added the kubuntu.org repositories and upgraded kde.  Now, when I boot ubuntu normally, it goes through the boot splash, and the login screen background appears for a second, and then the "kubuntu" boot splash re-appears and the system freezes.  I can, however, boot into recovery mode, and hit "startx" and everything work just fine.  I have the binary "nvidia-glx" driver installed via apt.

Edit:If I boot normally, and hit "ctrl+alt+f1" at the frozen boot splash and then "ctrl+alt+f7", It will usually work as normal.

---

### Post by kuja on 2006-09-13
If it doesn't boot right when usplash is being used, then perhaps it's the problem. Try editing your /boot/grub/menu.lst file.

Look for this section:
```

1:title           Ubuntu, kernel 2.6.15-26-amd64-k8
2: root            (hd0,4)
3: kernel          /boot/vmlinuz-2.6.15-26-amd64-k8 root=/dev/mapper/nvidia_gfdcfcfd5 ro quiet
4: initrd          /boot/initrd.img-2.6.15-26-amd64-k8
5: savedefault
6: boot
```

Near the end of the line I marked #2, Remove the word splash. It should make it boot normal, though not as pretty as before. It does shave a couple seconds off of the boot time too though, so it's not really a horrible deal.

---

### Post by napsilan on 2006-09-13
Thank for the reply.  I'll try that, however, I think I already found a way to get it to work.  

My /etc/X11/default-display-manager file was empty, I tried putting in /usr/bin/kdm (or /usr/sbin/gdm for gnome iirc) into that file and it seemed to work.  Only tried it once so far.  reference site was [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

