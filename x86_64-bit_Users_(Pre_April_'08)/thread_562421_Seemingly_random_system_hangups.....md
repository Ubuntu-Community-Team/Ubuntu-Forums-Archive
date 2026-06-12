---
title: "Seemingly random system hangups...."
date: 2007-09-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by ljoslin on 2007-09-28
I just built a new computer and I am having some random hangups, it really doesn't seem to have any pattern. Here are my system specs

MSI K9N Neo V3 board
AMD X2 Athelon 
NVidia GeForce 7200 GS
2 Gig Ram
22" wide screen w/ resolution at   1680X1050

Ubuntu Fiesty


The only errors I can find in the area of the hang ups are 

[ 3487.888728] NVRM: Xid (0004:00): 26, Ch 000001ff M 00001ffc D ffffffff intr ffffffff

in Kern.log

the hang ups seem to happen randomly but will happen more often while playing video or switching desktops.  They are 5-20secs long

any help would be greatly appreciated!  If you need anymore info please ask!

-=ljoslin=-

---

### Post by Cappy on 2007-09-29
Try booting with
```
noapic nolapic
```
or
```
noapic acpi=off
```

If you need to know how to add boot params to grub look here:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by ljoslin on 2007-09-29
> **Cappy said:**
> Try booting with
```
noapic nolapic
```
or
```
noapic acpi=off
```

If you need to know how to add boot params to grub look here:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

I'm giving that a try....I'll tell you how it works out!  Thanks for the help!

-=ljoslin=-

---

### Post by Cappy on 2007-09-29
I searched and found that the latest binary driver fixes your issue.

```

sudo apt-get --purge remove nvidia-glx* nvidia-settings linux-restricted-modules*
sudo apt-get install build-essential xserver-xorg-dev

```

and then install envy from here:
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu11_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu11_all.deb)

Hopefully that will give you the newest nvidia driver.

---

### Post by ljoslin on 2007-09-30
> **Cappy said:**
> I searched and found that the latest binary driver fixes your issue.

```

sudo apt-get --purge remove nvidia-glx* nvidia-settings linux-restricted-modules*
sudo apt-get install build-essential xserver-xorg-dev

```

and then install envy from here:
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu11_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu11_all.deb)

Hopefully that will give you the newest nvidia driver.

I used envy to install the drivers the first time, I will try and re-install them just for the fun of it.  I tried the first section of code from the other post, only thing that did was make the hang ups into lock ups :( I'm going to try the second set tonight/tomorrow, weekends are rough for me because of work.

Thanks for the help,

-=Ljoslin=-

---

