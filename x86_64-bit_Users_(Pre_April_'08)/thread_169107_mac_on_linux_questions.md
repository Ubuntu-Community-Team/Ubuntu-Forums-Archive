---
title: "mac on linux questions"
date: 2006-05-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by seatea on 2006-05-01
I installed MOL today and, to my amazement, Mac OS 9.2.2 booted up. I just have to figure  out how  to connect to the internet now. I am still a little puzzled as to what I have done though. MOL is not an emulator, so is  it now part of  my kernel? When MOL is running, can I switch  to a console and back to MOL or is X not runnig while MOL is? 

It was nice  to be able  to access the Mac OS without  all the reboots. I hope this doesn't do anything bad to my Mac OS while it is running in Linux.

---

### Post by ristosu on 2006-05-02
/etc/mol/tunconfig should open up the route to the Internet through your Linux box.

I guess you could say that MOL is part of your kernel.

X is running as usual, you can use Ctrl-Alt-F7 and -F8 to switch back and forth.

---

### Post by ssam on 2006-05-02
did you look at [https://wiki.ubuntu.com/MacOnLinuxHowto](https://wiki.ubuntu.com/MacOnLinuxHowto) that has a bit about networking, though it may not work with mac os 9

---

### Post by seatea on 2006-05-02
Thanks for  your replies. I started up MOL today and now I can connect to the internet. I am not sure why, but I am grateful it is  working. I did make  the  change to the sound output after installing the MOL audio extension, so maybe  that did it. My current snag  is  that  I can't switch back to MOL once I  use Ctl-Alt-F7 to get to Linux by using Ctl-Alt-F8. No other combinations  seem to work either. I even tried using Clt-Command-F8. I had  to restart my whole system to stop MOL which led to  Mac OS 9 not being shutdown  properly. Any thoughts on this  problem.

---

