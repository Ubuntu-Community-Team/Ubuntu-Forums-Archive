---
title: "two problems: can't edit grub settings, can't boot ubunt"
date: 2007-05-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Osvaldas on 2007-05-19
Hi there,

I am a total newbie in Linux so don't get annoyed because of my stupid questions.

I have managed to install Ubuntu on my AMD 2x 64bit system (laptop HP Pavilion dv6000) using this command to disable APIC:

```
NOAPIC NOAPCI NOIRQPOLL NOSMP
```

After few seconds of happiness I was frustrated because of this message which I've got trying to boot installed Ubuntu: *Cannot mount selected partition Error 17*.

I booted system from LiveCD, tried many things: reinstall grub, use root (hd0,6) commands an so on, but nothing is changed on menu.lst file. There is a setting in this file *root (hd0,5)*, but there should be 6, not 5! And as I said, nothing helps me to make this change!!!!

Is there any ways left for me to update this nonsense?

Secondly, how can I make my system boot from hard disk by disabling APIC? I mean what I need to do to disable this APIC forever?
This is a [description]("https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)") at the "Installation" gap but I am too stupid to understand it! 

Thanks a lot for any kind of help!

---

### Post by shad0w_walker on 2007-05-19
Reboot your computer, when you get to grub highlight the entry you need to change and press 'e'. This will let you change the boot options as you need to. when you are done press 'b' to boot with those settings.These changes only last for one boot.

When your system has booted, open a command prompt and run:

```
 sudo gedit /boot/grub/menu.lst 
```

You can edit the boot settings you need to from there. Save and close the file when you are done then run: 

```
 sudo update-grub 
```

This should update your grub settings to the ones you need.

---

### Post by Osvaldas on 2007-05-19
> **shad0w_walker said:**
> Reboot your computer, when you get to grub highlight the entry you need to change and press 'e'. This will let you change the boot options as you need to <...>

Yes, I need to disable APIC. But, what do I need to type in order to boot system successfully? I tried to enter *NOAPIC NOAPCI NOIRQPOLL NOSMP* but this didn't work out!

---

### Post by shad0w_walker on 2007-05-19
The lines that appear when you edit your grub entry should look something like

```
(hd0,0)
/boot/vmlinuz-2.6.20-15-generic root=UUID=535b61fc-9977-44ba-a0ce-f5011f55ed44 ro quiet splash noapic <Insert extra options here>
/boot/initrd.img-2.6.20-15-generic

```

You need to add the option you want to use at the end of the second line.

P.S.

I have a X2 processor as well and just disabling APIC works fine, so unless you know you need to disable the other bits i would leave them be.

---

### Post by Osvaldas on 2007-05-19
Thanks for the info *shad0w_walker*! These problems are now solved.

---

### Post by shad0w_walker on 2007-05-19
Most welcome, enjoy your Ubuntu setup. :)

---

