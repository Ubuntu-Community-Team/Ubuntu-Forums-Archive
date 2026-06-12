---
title: "Grub error 28 after adding KDE Desktop in Ubuntu 8.10 - 64 bit"
date: 2009-01-12
forum: x86 64-bit Users
---

### Post by CD2000 on 2009-01-12
Hi.
I have 2 - 320 Gig SATA HDs: On the first one, I have 4 partitions, the first partition holds Ubuntu 8.10 (now Kubuntu), second partition is my Home partition, third is SWAP and the fourth one holds Windows XP Pro. On my second HD, I have Windows Vista Ultimate 64 bit using the whole drive. The default boot loader was installed with Ubuntu as my default OS, and all was great until last week.

I prefer KDE over Gnome so I decided to install the KDE desktop using Synaptic. Since then, whenever I try to load either XP or Vista at the bootloader screen, I get an "error 28: Selected item cannot fit into memory, Press any key to continue." and it brings me back to the Grub menu.

Does anyone know how I can fix this? I googled for the answer without luck.

Kind regards,
CD2000

---

### Post by caljohnsmith on 2009-01-12
Sounds like a strange problem to have after installing KDE, so in order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

