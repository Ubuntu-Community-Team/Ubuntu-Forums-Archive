---
title: "Installing Windows XP on a Ubuntu system"
date: 2008-05-23
forum: x86 64-bit Users
---

### Post by kamale on 2008-05-23
Was wondering if thats possible, i've been tryin my best to search online. Because from what i see on the windows bootdisc, when u pop it in it always asks to format your C drive to partition it into the windows ready filesystem. But i don't want my Ubuntu to be uninstalled. I wanna dual boot windows XP from ubuntu. So my main system is ubuntu. :confused:

---

### Post by cariboo on 2008-05-23
The easy way is to install Windows in Virtual Box it's available in the repositories. The hard way is to start from scratch, install windows first, if you've only got one hard drive only partition half of it for Windows and then install Ubuntu on the other half.

Jim

---

### Post by kamale on 2008-05-23
Ah well thats what i thought. I opened another thread stating the problems i have with the xVM virtual machine LOL
[http://ubuntuforums.org/showthread.php?t=804321](http://ubuntuforums.org/showthread.php?t=804321)

---

### Post by warpuck on 2008-05-26
I seen a grub work around using 2 sata drives. It was a simple 2 line thjing Icant remember right now. Appeared to be some thing like dos 5 or 6 floppy swap. I dont believe it give you a menu choice when grub comes up. I think you have to grub at command line, make it reverse and boot linux by reversing it again.  
 I will see if it works when I get home. they wont let me try it here.

---

### Post by Sef on 2008-05-26
> Was wondering if thats possible, i've been tryin my best to search online. Because from what i see on the windows bootdisc, when u pop it in it always asks to format your C drive to partition it into the windows ready filesystem. But i don't want my Ubuntu to be uninstalled. I wanna dual boot windows XP from ubuntu. So my main system is ubuntu

Yes it is possible.  

1) Windows need to be on the first partition.

2) Set up a partition before installing Windows.

3) Before installing, get [Super GRUB Boot Disk]("http://supergrub.forjamari.linex.org/").  Windows will not recognize Ubuntu, and SGBD will reinstall GRUB.

4) There are tutorials and threads on this, and I will post a link when I have time to look for one.

---

