---
title: "[SOLVED] Loading screen looks erratic"
date: 2007-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by FUbuf on 2007-10-26
I don't know what is happening but this is what I see when Ubuntu is loading.

And sorry, it's a real screenshot because I couldn't use software at that point. ;)

[[IMG]http://picozilla.com/files/138353timgp0814.jpeg[/IMG]](http://picozilla.com/en/138353/imgp0814.jpeg.html)

---

### Post by kuja on 2007-11-01
When the splash screen is yielding these sorts of problems, it's usually best to just turn of the splash screen.

To do so, look for a line in /boot/grub/menu.lst like this:
# defoptions=quiet splash
Remove the word splash from the end, and then run the command "sudo update-grub"

---

### Post by FUbuf on 2007-11-05
Thanks, I turned splashscreen of and now it's ok.

---

