---
title: "disabling graphical boot splash"
date: 2006-05-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by fjs on 2006-05-31
Hi

My first post. 
I am converting my ppc macs to ubuntu 5.10.  One of these is a G4 dandelion iMac 800 mHz 1024k RAM.  This machine has documented quirkiness with its screen display during boot, and Ubuntu displays its splash logo in ?inverted video.

I would like to boot in text mode, to remove this and to display messages of sufficient size for me to read.

I come from a mac background with a touch of SuSE. I cannot locate rc, rc.boot. rc.boot.local or anything handy to edit with vim.

I would appreciate any assistance as to what I should edit.

Thanks
fjs

---

### Post by engla on 2006-05-31
This is one way to disable the splash, without uninstalling anything. 

On a powerpc machine, look in the file /etc/yaboot.conf It's a very important file, so don't destroy anything though!

The yaboot entries are there, like this:
> image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="quiet **splash**"

And guess what, you want to remove that word in bold.

When you've saved changes to that file, you have to run *sudo ybin* to have it take effect.

---

### Post by fjs on 2006-05-31
Thank you /Tak.

fjs

---

