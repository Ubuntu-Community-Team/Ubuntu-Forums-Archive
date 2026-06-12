---
title: "Black Specks/Dashes on Menu Bar"
date: 2008-05-11
forum: x86 64-bit Users
---

### Post by remu on 2008-05-11
Hey,
Recently, some black specks have shown up on my menu bar out of nowhere. They don't go away even after restarting X, or the computer itself, or choosing another theme. I need help fixing this, I've attached a picture so you can see the problem. I think I had this problem once before, on Gutsy, but was never able to fix it (it was gone after I reinstalled for some other reason).

I'm sorry if I'm posting this in the wrong place.

My specs are in my signature.

edit: The problem solved it self when I created a new user account and logged into it to see if it was occurring there as well, when I came back to my account, the problem was gone...weird.

---

### Post by remu on 2008-05-13
I thought the problem was fixed, and it seemed to be, but now its back, its really weird, and extremely annoying, does anyone know how I might be able to fix this?

---

### Post by Rhubarb on 2008-05-13
Try installing envyng-gtk from the ubuntu repositories.
Or look here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

This will let you install the latest nvidia drivers, which may fix up your problem.

---

### Post by rubycodez on 2009-04-16
(8.10 on 64 bit desktop with "180" nvidia driver and NVidia 8400 GS PCI-E 16x) I had black dashes and black lines on menu bar and on some window title bars. I did a "dpkg -l" | grep nvid and uninstalled everything having to do with nvidia.  Then I downloaded NVIDIA-Linux-x86_64-180.44-pkg2.run from the nvidia website and ran it.  That fixed the black lines and dots

---

