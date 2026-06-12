---
title: "Res. is stuck."
date: 2006-08-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Wafflesomd on 2006-08-21
Hey, so I'm new, and I have searched about the resolution getting stuck, but I cant seem to follow it very well, so hopefully, you guys will go in mroe depth with me.

The title is pretty much self explanitory.  After my install, and update of ubuntu, my res is stuck at a max of 1024x768, and 60hz, which is killing my eyes.

So, I need help.

Now I did try installing the nvidia drivers, cept it gives me an error, heck, it gives me an error when I try to install anything.

This is the error I get,

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

Hope you can help me out.

---

### Post by Wafflesomd on 2006-08-21
Ok, I treid editing the xorg config thingy, it didnt seem to do anything.

---

### Post by juicemansam on 2006-08-21
I once had a similar problem. My monitor resolution was stuck at 800x600 on a 15" monitor (Compaq CV535). I could go lower, but not higher to it's max of 1152x864 (or anything in between). It was only until I found my monitor's horizontal/vertical frequencies that I could get all of the monitor's resolutions. If you have them available, you could enter them into your xorg.conf file. Then you'll be able to use adjust your resolution via conventional means, ie system tools and the like. If you don't have your monitor's frequencies avaiable, post your make/model here, and google a bit for it, and some of us can try to get them for you as well.

---

### Post by Wafflesomd on 2006-08-21
Well, I managed to open the xorg setup, so its all good now, problem solved.

---

