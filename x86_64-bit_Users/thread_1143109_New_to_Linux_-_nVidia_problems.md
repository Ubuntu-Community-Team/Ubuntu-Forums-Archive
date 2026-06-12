---
title: "New to Linux - nVidia problems"
date: 2009-04-29
forum: x86 64-bit Users
---

### Post by NickSlade on 2009-04-29
Hi just recently installed **Ubuntu 9.04 64-bit Desktop**, thought I would give it a try.

After (the very quick) installation Ubuntu booted up and I was greeted with the new desktop. After messing around a bit and trying to find my way around (I'm a Windows user) I realised I was unable to enable Extra appearance features due to the need to update my nVidia drivers.

My problem is that however I install nvidia graphics driver package, after rebooting it hangs at Checking battery state... [OK].

I've tried installing by downloading and running 180.51 and 170 and the package, using Terminal, using Envy and nothing works - I get the same problem each time. I've looked at many different posts/threads and searched Google and can't seem to find an answer.

I was at one point able to boot into Ubuntu after uninstalling my nvidia drivers through recovery mode and using "sudo envyng -t" and then following the instructions.

I need help as I am looking forward to using Ubuntu but will not until this problem is solved.

*Also my sound isn't working but I'll get that sorted after my graphics problem.

System  Specs:

Intel Core 2 Quad Q6700 @ 2.67GHz
nForce 680i SLI motherboard
4GB RAM
nVidia 8800GTX x 2 SLI
Seagate 250GB x 2
WD Velociraptor 150GB
Using built-in 7.1 sound card

---

### Post by Kareeser on 2009-04-29
Hm. I'm wagering that the problem lies with the fact that you have an SLi setup.

Slick setup, by the way!!!

Try nvnews forums... they are probably better equipped to help you out. Keep checking back here, however. You never know when someone can help you out.

---

### Post by NickSlade on 2009-04-29
Thanks, I'll give nvnews a try and see what I can find.

EDIT: I have read on a few posts that SLI is possible with Ubuntu, and I've found many posts on how to get it working but my problem is actually getting Ubuntu to boot.

---

### Post by NickSlade on 2009-04-30
Anybody got any suggestions?

---

### Post by NickSlade on 2009-05-01
Well after trying and trying and reinstalling Ubuntu 3 times I finallly decided to remove one of my 8800GTX's... I was able to install nVidia drivers no problem and can now enable extra appearance features etc.

So with that working I shut down, inserted my other 8800GTX which I had previously removed, and back to the same problem - computer hangs at 'Checking battery state... [OK]'

Anybody no how to go about being able to use my second card? I don't want to have to remove it every time I want to use Ubuntu. I'm sure there is a way but I need some guidance.

---

### Post by johnnysoj on 2009-05-01
I'm in the same boat you're in.
Until someone comes up with some fix, the best bet would be to revert back to the stock vesa drivers.

---

### Post by Steve McDermott on 2009-05-01
Here you go guys:-

[http://ubuntuforums.org/showthread.php?t=1134465](http://ubuntuforums.org/showthread.php?t=1134465)

---

### Post by Kareeser on 2009-05-01
Give this a try. You might have to modify your xorg.conf settings by hand.

[http://us.download.nvidia.com/XFree86/Linux-x86/185.18.04/README/chapter-25.html](http://us.download.nvidia.com/XFree86/Linux-x86/185.18.04/README/chapter-25.html)

Be careful, and always back up your config before you do anything.

---

### Post by NickSlade on 2009-05-04
> **Kareeser said:**
> Give this a try. You might have to modify your xorg.conf settings by hand.

[http://us.download.nvidia.com/XFree86/Linux-x86/185.18.04/README/chapter-25.html](http://us.download.nvidia.com/XFree86/Linux-x86/185.18.04/README/chapter-25.html)

Be careful, and always back up your config before you do anything.


Thanks for the link, looks interesting, will have to give it a proper read this evening if i can - busy weekend and didn't get a chance to sit down at the computer.

---

