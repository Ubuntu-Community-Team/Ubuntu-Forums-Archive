---
title: "Wine doesn't run in full screen"
date: 2024-07-30
forum: Wine
---

### Post by somi91 on 2024-07-30
Hi 
I have Ubuntu 22.04.4 LTS installed on my HP laptop. Recently I installed Wine and Play on Linux to play some old games. However I am not able to run Games in Full screen . My Wine display settings are
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294034&stc=1[/IMG]
I get the following screen. 
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294035&stc=1[/IMG]
I unchecked 'emulate a virtual desktop' and I get following screen, and also I loose mouse control to right half of wine screen, which works perfectly fine in virtual desktop.  

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294036&stc=1[/IMG]

I have tried changing display resolution and it didn't work either. It stretches screen vertically out of scope. 
My system details are
HP Pavilion 15 Notebook  (x64 based) core i5
Ram 6GB
Graphics card is intel HD came in with laptop.

Please note that, I use to play these games on same laptop in windows, but since windows 10's annoying updates, I have moved to Ubuntu

Any help is appreciated. 
Thanks

---

### Post by Paddy Landau on 2024-07-31
PlayOnLinux is, I believe, no longer in development.

These days, it's recommended to use Bottles instead.

The only way to install Bottles is to do so via Flatpak. If you need instructions, let me know.

---

### Post by somi91 on 2024-08-02
Hi Paddy,

Thanks for reply. I tried Bottles and Lutris and still had same issue. Going through forums I found out, windows manager might be creating problems. My default windows manager was wayland. I installed Xorg and switched to Xorg, the problem has been resolved.


Thanks

---

### Post by Paddy Landau on 2024-08-03
That's interesting. Wayland is more secure than X11, but unfortunately it still has a long way to go before it's as competent.

I'm glad that you found out the problem. Please mark the thread as resolved.

---

