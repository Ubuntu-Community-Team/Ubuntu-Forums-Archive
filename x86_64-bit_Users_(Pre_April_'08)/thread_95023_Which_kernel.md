---
title: "Which kernel?"
date: 2005-11-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by rplantz on 2005-11-25
I think that I once saw a howto about picking the best kernel, but cannot locate it again.

I'm currently running 2.6.12-9-amd64-generic on an AMD athlon 3200. Motherboard is abit nf8-v. Video is nvidia geforce fx5200.

When I was running hoary, I ran a k8 kernel. I tried that a while back with breezy, and it would not boot. (I don't recall all the issues.)

Update manager suggests that I should go to:
linux-amd64-generic
linux-image-2.6.12-10-amd64-generic
liunx-image-amd64-generic

I'm inclined to go with:
linux-amd64-k8
linux-image-2.6.12-10-amd64-k8
liunx-image-amd64-k8

This leads me to several questions.
1. What are the differences between these three files?
2. Will I have to change other things?
3. Is this the best thing to do in my setup?

My machine is not in a critical path. I'm an old retired guy who simply likes to play with this stuff. (The biggest perk of being retired is avoiding critical paths.  :-))

I would appreciate any pointers to places where I can learn more about this.

---

### Post by earobinson on 2005-11-25
I serched the forums for (kernel) and I found this [http://www.ubuntuforums.org/showthread.php?t=85917&highlight=kernel](http://www.ubuntuforums.org/showthread.php?t=85917&highlight=kernel)

---

### Post by rplantz on 2005-11-25
[QUOTE=earobinson]I serched the forums for (kernel) and I found this [http://www.ubuntuforums.org/showthread.php?t=85917&highlight=kernel](http://www.ubuntuforums.org/showthread.php?t=85917&highlight=kernel)[/QUOTE]

Thank you. I had just come from there when I posted my request because it says > 
- This guide does not apply to the PPC or 64 bit version of Ubuntu.

Since I'm running 64-bit, I'm nervous about following it. If I can't find anything else, I will probably follow it and fill in the (64-bit) blanks as best I can.

---

### Post by teaker1s on 2005-11-25
look [here]("http://ubuntuforums.org/showthread.php?t=85917")

---

### Post by earobinson on 2005-11-25
lol sorry about that, sometimes i miss read things hope the link above helps (which wont because its the same as mine lol) this may help
[http://www.ubuntuforums.org/showthread.php?t=75827&highlight=64-bit+kernel](http://www.ubuntuforums.org/showthread.php?t=75827&highlight=64-bit+kernel)

*extra points for searching before you post btw*

---

### Post by rplantz on 2005-11-25
I followed the links provided and read through them. Neither gave the full answer, but they provided hints. So I simply used Synaptic to install linux-amd64-k8, which installed the required pakages for 2.6.12.16.1. I rebooted and found myself in a k8 kernel.

Then I decided to update my linux-amd64-generic kernel to have a fallback.

Now I find that the generic kernel is the default, and I must pause grub and tell it to run k8.

So now I'm trying to figure out how to make the k8 kernel the default. So far I've figured out that I need to do something to /boot/grub/menu.lst and to change the initrd.img and vmlinuz links in /boot/grub. But I don't know what else I need to do. I will continue my search, but any hints are very welcome.

(edit)
Oh, I only have ubuntu on my system, no other operating systems.

---

### Post by rplantz on 2005-11-26
I think that I've figured it out. At least it seems to be working.

I simply changed the default parameter in /boot/grub/menu.lst to be the number of the kernel entry I wish to use as default. In my case this is 4. (Keep in mind that they are numbered from 0.)

When I look at
```

kernel          /boot/vmlinuz-2.6.12-10-amd64-k8 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-amd64-k8

```
I see that the correct vmlinuz and initrd.img files are specified.

The 0th entry in the table still points to the linked names:
```

kernel          /boot/vmlinuz root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img

```
and I realize that I should **not** change the links in case I wish to boot into the 0th kernel in the future.

To check which kernel I'm running:
```

$ uname -r
2.6.12-10-amd64-k8
$

```

---

