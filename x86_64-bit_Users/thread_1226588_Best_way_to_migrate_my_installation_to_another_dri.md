---
title: "Best way to migrate my installation to another drive?"
date: 2009-07-29
forum: x86 64-bit Users
---

### Post by niw_uk1964 on 2009-07-29
I have now got myself a nice installation running. I've decided to stick with Ubuntu 9.04 64-bit. However, I installed it on an old drive that is not exactly a high performer. I would like to move my installation to a newer SATA-II drive which, is also bigger. Is this possible or would it be easier and better to just start from scratch again?

---

### Post by loomsen on 2009-07-29
You could simply copy everything over, but you might run into unexpected problems afterwards (pretty untraceable as well)

I assume you have a separate /home partition, the easiest way would probably be to create a file holding your installed package selection

dpkg --get-selections >> mypackages.txt

Install a basic system to you new drive (I don't use ubuntu anymore, but I'm pretty sure there's a boot option to install a command line system only.)
Then, log in to your new installation and set your backed up selections

dpkg --set-selections << mypackages.txt

And use 
apt-get -u dselect-upgrade
actually install the packages (the dpkg commands only marks the pkges to be proceeded, apt-get then applies your selections)

Mount your home partition to your new install and you should reach exactly your current state, with a clean install.

---

### Post by niw_uk1964 on 2009-07-29
Yes I have separate partitions for \ , home and swap.

I'll give your suggestion a go. I've been playing around with Linux on/off for years, but I figured it's about time to make the jump fully :)

---

### Post by theozzlives on 2009-07-29
Just get you an encloser to turn SATA to external USB and use clonezilla to copy your partitions. You can use the encloser for your old drive to do backups and such. That's what I did.

---

