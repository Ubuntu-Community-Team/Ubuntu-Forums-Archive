---
title: "Chowned some system files to user lavel..."
date: 2009-02-25
forum: x86 64-bit Users
---

### Post by goxmir on 2009-02-25
Hi!
I came from the Fedora distro to Ubuntu, and was quite happy with it, till one day, I was trying to change permissions on www folder in comand prompt, and by error i started changing permissions on whole system(typed / to start), I realized what I am doing, and stoped the process, but after restart I cant seem to be able to go online(network manager does not start), not able to start "services" from admin menu, unable to mount any media(i can see it thought). X server runs ok, I am not getting any errors, but can nod do much with the system. I do have access to command prompt and i viewed root folder list, most of folders are under root user, /lib was under my user name, as well as / i cvhanged the first one to root, recursively...rebooted, and nothing chaged, /home folder as also under my user name...
Please help! 
I want to fix this, and I got couple filers in that system, that I really-really need, and I can not move them to any media location, or net...

---

### Post by jocko on 2009-02-26
The only fix I know of is to find out exactly which permissions each file should have and set them correctly. But as there are probably around 200,000 files in / I think it's probably **a lot** easier to do a clean reinstall.

If you have files you want to keep, I'd suggest you shrink your ubuntu partition as much as possible (run gparted from a live cd), and make a new ext3 partition.
Move everything from your /home folder to this new partition (so instead of /home/username you will have something like /media/disk/username).
If you had a lot of data in your /home, you can probably shrink the ubuntu / partition even more after moving everything in /home and give more space to the new partition (when you have a separate /home partition, / shouldn't need to be more than 10 Gb. My / is 12 Gb, but I have more than 50% free space).
Then just reinstall ubuntu, but when you get to the partitioning part, use the advanced method to set up your partitions.
The old ubuntu partition needs to be formatted (to ext3, unless you prefer another linux filesystem) and the mount point should be set to "/".
The new (/home) partition should **NOT** be formatted, and it's mount point should be set to "/home".
If you need more specific instructions, look at [this page]("http://www.psychocats.net/ubuntu/separatehome"), but as you need to reinstall ubuntu you can skip the parts that describes changing the fstab file and instead go directly to reinstalling ubuntu.

---

