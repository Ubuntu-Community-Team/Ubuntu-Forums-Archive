---
title: "Thinking of upgrading to 64 bit but..."
date: 2008-02-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by doorknob60 on 2008-02-20
Well, I'm thinking of upgrading my Ubuntu 32 bit installation to 64 bit when Hardy comes out (maybe sooner). The only problem is I have Broadcom wifi and it works fine with ndiswrapper in 32 bit, but what would I have to do to make it work in 64 bit? To get it to work in 32 bit, I compiled ndiswrapper and used the driver and it worked fine. Does ndiswrapper support 64 bit? If so, do I use 32 bit or 64 bit drivers? Also, is there a way to upgrade to 64 bit WITHOUT reformatting/reinstalling?

---

### Post by Yellow Pasque on 2008-02-21
No, you can't upgrade to 64-bit without a reinstall, but you can re-use your /home folder if you move it to another partition.

ndiswrapper works the same way on 64-bit, except that you'll need 64-bit Windows drivers.

---

### Post by doorknob60 on 2008-02-21
OKay, 64 bit drivers shouldn't be too hard to find because the computer's only a year old :) Also, would there be any issues or incompatibilites using the same home folder? I might even consider upgrading today now :D

---

### Post by John Jason Jordan on 2008-02-21
> **doorknob60 said:**
> OKay, 64 bit drivers shouldn't be too hard to find because the computer's only a year old :) Also, would there be any issues or incompatibilites using the same home folder? I might even consider upgrading today now :D
Using the same home folder should be no problem at all.

I would start by copying my entire home folder to external media someplace for safekeeping, just in case things get mucked up. A lot of people like to put their home folder on a different partition just so they can wipe out their Linux installation without affecting ~/home. You might want to consider this for the future.

Once you have your home folder secure, do the 64-bit installation, then restore ~/home. In Linux practically all software configuration files are in your home folder. This means that after you reinstall your favorite applications they will come up complete with all the personal settings that you had before. Software config files are usually invisible, that is, they have a . in front of the file or folder name.

As for Broadcom, you might want to try the bcm43xx driver. It is open source and works with most Broadcom chips. If it works you won't have to mess with ndisrwapper at all. Before doing this I would search these forums on "broadcom" and read extensively. My old computer had a Broadcom chip but I could never get the bcm43xx driver to work, so I used ndiswrapper. Setting up ndiswrapper is not especially hard and is well documented on these forums. But the bcm43xx driver is better if you can get it to work. In fact, in most cases it finds your Broadcom chip and autoconfigures itself. Whether bcm43xx works for you or you need to go to ndiswrapper, one way or the other I can give you a 99%+ probability that you will be able to get your Broadcom wireless working on 64-bit Ubuntu.

And if things totally blow up and you can't get something working that is essential, well you can always reinstall 32-bit Ubuntu. So go for it. We're all eagerly awaiting another 64-bit convert!

---

### Post by doorknob60 on 2008-02-21
I've tried bcm43xx and for me it's slow and unreliable, but ndiswrapper works just fine, so I'll do that. Also, I think I might have set /home as it's own partition, I don't remember :P I'll go check :D

Dang, I think I got rid of the separate /home partition :( Oh well I'm backing it up to my iPod right now while I download the Ubuntu AMD64 Live CD :D I'm gonna scrap WIndows too, unless VMWare player doesn't work. (It does work right??)

---

### Post by John Jason Jordan on 2008-02-21
> **doorknob60 said:**
> IDang, I think I got rid of the separate /home partition :( Oh well I'm backing it up to my iPod right now while I download the Ubuntu AMD64 Live CD :D I'm gonna scrap WIndows too, unless VMWare player doesn't work. (It does work right??)
VirtualBox is better than VMware and is listed in Synaptic. I found it a snap to install Windows in it.

---

### Post by doorknob60 on 2008-02-22
Yeah I use Virtualbox on my other computer and I like it better but I couldn't get it to work right on here, and my Dad needs his data (Turbotax) that's in VMWare. ANyways, I got it working and it's going good so far, including Wireless :D

EDIT: Wow! It boots up so much faster now! Woot! Now I wish my Desktop had 64 bit :P

---

