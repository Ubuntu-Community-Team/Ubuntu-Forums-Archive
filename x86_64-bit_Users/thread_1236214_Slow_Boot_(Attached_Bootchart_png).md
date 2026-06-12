---
title: "Slow Boot (Attached Bootchart png)"
date: 2009-08-10
forum: x86 64-bit Users
---

### Post by PranavRam on 2009-08-10
Hello all,

I'm new to Linux and I am experiencing very slow boot times ( greater than 3 minutes). After installation Ubuntu would boot fine, but after updating it to the latest kernel it takes forever to boot.

At about 10% on the progress bar, my computer shows inactivity. And then after about 2 minutes it moves straight to the end and boots up.

Attached is my bootchart file which I have no clue about understanding. I would greatly appreciate your help in doing so to fix this problem.

Thank you.

---

### Post by warp99 on 2009-08-10
You should first see what is hanging the system during boot and to do this we need to temporarily remove the splash screen. So during boot up at the "Grub Loading" line press the esc key. The kernel that you normally boot to will be highlighted. Press 'e' for edit, highlight the line 'kernel' and press 'e' again. At the end of the line remove the option 'quiet' and 'splash'. Press esc, then 'b' for boot.

For this boot session your splash will be removed so you can watch the boot messages. You can now see exactly were the system is hanging. Once you figure this out we can try and fix this.

---

### Post by PranavRam on 2009-08-10
Hello,

Thank you for the quick reply. I did as you told me and removed the splash screen while loading. And guess what? It booted within 10 seconds. Now I restarted the computer and the problem persists when the splash screen is enabled. It takes the same 3 minutes to boot.

Is there some graphics issue with the splash screen?

Thank you.

---

### Post by warp99 on 2009-08-10
Interesting, we at least narrowed the problem down. :) 

You can rebuild the boot image with the following command to see if this helps:

```
sudo update-initramfs -c -k `uname -r`
```

If that doesn't work you can remove the splash screen for now until you can locate the problem. Just do the following:

```
sudo gedit /boot/grub/menu.lst
```

Edit the following line removing the word splash:

```
# defoptions=quiet splash
```

Update the grub menu:

```
sudo update-grub
```

That way when you do find an answer you can test the changes by editing the menu during boot up like before, then make it permanent by adding the splash option back into the menu.lst file.

---

