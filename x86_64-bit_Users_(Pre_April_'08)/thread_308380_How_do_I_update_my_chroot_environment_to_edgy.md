---
title: "How do I update my chroot environment to edgy"
date: 2006-11-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Saubazi on 2006-11-28
Just came across this dilemma - I was thinking about updating my chroot environment to edgy but actually how do I do it?

I originally went with this:
[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

Now I am thinking whether I should change the stuff in sources.list to 
point to edgy and then what... sudo aptitude update && sudo apt-get upgrade
but do I need to something else?

I am thinking of this bit:
    * sudo apt-get install dchroot debootstrap
    * sudo mkdir /chroot/
    * sudo gedit /etc/dchroot.conf
          o Add this line: hoary /chroot
    * sudo debootstrap --arch i386 hoary /chroot/ [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
    * sudo chroot /chroot/
    * dpkg-reconfigure locales

Do I need to redo deboostrap for edgy?
Do I need to remodify sudo gedit /etc/dchroot.conf for edgy?

---

### Post by incubus on 2006-11-28
Saubazi,

Actually what you would need is:
```

$ sudo apt-get update
$ sudo apt-get dist-upgrade

```

Now, the thing is: I don't know if things are going to break.  If you can afford (read: have space), why don't you make a backup of your chroot directory first?  By the way, if you don't have so many things in you chroot environment, you could just create another environment.  Then you can switch smoothly.  You know you can have many chroot environments anyway.

Yes, to upgrade you just need to replace "hoary" for "edgy" in the sources.list of the chroot.  If you want to debootstrap (create another chroot), you may need to get the Edgy debootstrap package to create an Edgy chroot.

incubus

PS: You typed "hoary" in your steps, but I'm assuming you meant "edgy".

---

### Post by Saubazi on 2006-11-29
> **incubus said:**
> Saubazi,

Actually what you would need is:
```

$ sudo apt-get update
$ sudo apt-get dist-upgrade

```

Now, the thing is: I don't know if things are going to break.  If you can afford (read: have space), why don't you make a backup of your chroot directory first?  By the way, if you don't have so many things in you chroot environment, you could just create another environment.  Then you can switch smoothly.  You know you can have many chroot environments anyway.

Yes, to upgrade you just need to replace "hoary" for "edgy" in the sources.list of the chroot.  If you want to debootstrap (create another chroot), you may need to get the Edgy debootstrap package to create an Edgy chroot.

incubus

PS: You typed "hoary" in your steps, but I'm assuming you meant "edgy".

Ok, yes I meant edgy actually - I just copied those commands from the Howto. Anyway. For the moment I decided to delete whole chroot environment and try to get the 32bit part running under 64bit - let's see. There was nothing of importance there. Only getting some libraries into /usr/lib32 was easier by using chroot environment and installing packages there and copying stuff over. Thx

---

