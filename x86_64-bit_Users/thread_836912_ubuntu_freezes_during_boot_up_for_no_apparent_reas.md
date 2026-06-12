---
title: "ubuntu freezes during boot up for no apparent reason"
date: 2008-06-22
forum: x86 64-bit Users
---

### Post by slymi2005 on 2008-06-22
All right so I'm using ubuntu 64 bit with a dual boot of vista 64 bit and sometimes I am able to get on ubuntu and it works fine but other times it just freezes during the boot up where it says ubuntu and it has that bar loading. I don't know why it does this and alt f1 doesnt do anything and neither does ctrl alt delete/backspace so I have to restart it by holding down the power button. I try logging into recovery mode and that freezes sometimes as well at the moment when it says something about eth0. Also I was able to get on once and the internet didn't work so I'm thinking it has to do with the internet locking it up or something maybe vista is not letting it gain access to the internet. I don't know why it freezes on start up and it would be nice to get it to work if anyone has any idea of what I could do to fix this. I'm using an nvidia 8500 gt video card if that has anything to do with it. When I first installed ubuntu last night it was at 800x600 and that was causing me trouble. Anyway any help would be great.

---

### Post by dragonfyre13 on 2008-06-22
random guess, you're using a realtek gigabit card too? I have the exact same issue, except I NEVER get mine to boot. 100% of the time (save the one time it booted to install it, and never did again when booting to the CD) it freezes during boot up.

I've installed 32bit for now, and while 64bit is almost ready, I actually have to use this system, and not play with it anymore. So I lose a bit of memory, and that sucks, but at least it's usable. I just wish that it didn't break whenever I've tried 64bit. :( (end of "pity me" whining. ^_^)

---

### Post by slymi2005 on 2008-06-24
Yeah I am and it's really annoying because internet works fine in vista but when I restart to log in to ubuntu the internet is turned off. Ubuntu still freezes on start up sometimes but when it works it would be nice if the internet worked as well. I know this  has to be a vista problem so if anyone is dual booting with both os's please help.

---

### Post by hopelessone on 2008-06-24
I disabled the ACPI in GRUB and have have no freezes..

Hope helps..

---

### Post by slymi2005 on 2008-06-25
How to I do that? Do I have to go into recovery mode and type it in there. This is so frustrating, every time I get something to work fine in ubuntu something else breaks, I wish it would just work. Does anyone know if it would be a better experience with ubuntu 32 bit rather than 64 bit. I'd hate to have to reinstall ubuntu but if it would solve the problem then I would.

---

### Post by slymi2005 on 2008-06-25
I've posted my problem over at the vista forums, see who helps me first.

---

### Post by slymi2005 on 2008-06-26
It didn't freeze and I got on ubuntu and I have internet. This is freaking me out and making me mad at the same time.

---

### Post by slymi2005 on 2008-07-01
Does anyone know if my realtek rtl8168c/8111c family pci-e gigabit ethernet nic works in ubuntu 7.10 I was thinking about uninstalling ubuntu 8.04 and just trying 7.10. Also is there anywhere I can track progress on this network card to see if it may be supported in ubuntu 8.04.1 or 8.10? 

Edit: What changes can we expect for 8.04.1 anyway?

---

### Post by slymi2005 on 2008-07-02
It's like I'm talking to myself. I remember the forums being more helpful in the past, does everyone take a vacation over the summer?:lolflag:

---

### Post by slymi2005 on 2008-07-04
All right so I read somewhere something about something. I apologize but not only do I not remember much but I also didn't understand much. It had something to do with hal and dbus I think and it talked about how one would start before the other and it would cause the freezing. And someone suggested doing the below and I did and so far so good.

Anyway what I did was go to system->administration->services->scroll down to system administration bus (dbus)-> then right click->properties->and changed all the values that were 12 to 13. 

Thank you to whoever it was that helped. Also what exactly did I just do and is it bad. Maybe someone will be helped by this.

---

### Post by stabu on 2008-07-04
It's kind of scary to reply 'cos you ask so many questions, it's hard to know where to start.

I can't say I have an actual answer, but I can give some advice. Bookmark the special linux google "www.google.com/linux" and do a search on the critical components of your hardware (the "lspci" command will give you these).

Also a handy tool to have is a live linux CD for diagnostics purposes, Preferably this should not be the nsame as the linux you intend to install on HD, but a completely different one (Knoppix comes to mind). Knoppix v4 installs on virtually everything, even on dead badgers apparently (so a certain book says) so you can use that to do an lspci.

Search on linux google will give you the state of development of linux drivers for your hardware, and you may find somebody with similar hardware to yourself which will help alot.

My final point is about using cheatcodes, which are options you include on the kernel booting command. (type "kernel cheatcodes" in goog). 

Unfortunately these suggestions are time consuming, but it's not a bad idea to know your hardware well.

---

### Post by slymi2005 on 2008-07-04
haha. I'm sorry I can't help it. The "fix" that I did wasn't really a fix since it froze during boot up twice today. Also once I was able to get on the internet didn't work. My realtek 8168c/8111c nic is making me mad. I read someones post saying that the freezing stopped after switching to 32 bit and I thought of doing that but I think I can live with this. Maybe by 8.10 all will be well, maybe.

Also you suggested lspci but for my network card it says this: 02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

Which isn't correct as I said before it's a RTL8168C/8111C Family PCI-E Gigabit Ethernet. Anyone know why this is.

---

### Post by slymi2005 on 2008-07-15
The fix is here: [http://www.jamesonwilliams.com/hardy-r8168.html](http://www.jamesonwilliams.com/hardy-r8168.html) yay everything works fine now.

---

### Post by penquin on 2008-07-31
I am trying to get my ubuntu partion up and running again and I don't know what to do.  It worked perfectly before I did my standard update upgrade and now after reboot nada.  I can't even get into recovery mode. any suggestions?

---

