---
title: "Ubuntu crashes every time I access my home folder... something to do with compiz?"
date: 2008-07-16
forum: x86 64-bit Users
---

### Post by nickdiacre on 2008-07-16
Hi There,

Title says it all... Ubuntu crashes every time I access my home folder. I have been pretty stable til recently, now this!

I can't find any error messages or anything in the log.

It also craches at other moments. 


If I disable Compiz it stops crashing...

How can I resolve this?

ATIX1600 128 meg - ATI propprietary drivers 8.6 - dual head
Targe MT34 Traveller 2 GB ram 1.6 GHZ AMD Turion 64


Thanks in advance

Nick

---

### Post by Sef on 2008-07-16
1) What version of Compiz are you using?

2) How did you download it?

3) What version of Ubuntu are you using?

---

### Post by nickdiacre on 2008-07-16
Sorry...

Hardy 8.04... reinstalled compiz this morning so the latest version from the repo... 0.7.4

It crashes if I access any folders on my desktop.

If I sudo nautilus, I can access the home folder fine.

Tanks for your help.

---

### Post by mdsharp24 on 2008-07-19
I was having the same problems. Compiz is pretty, but once I went into synaptic, searched "compiz" and removed ALL compiz associated apps, my desktop is rock solid. It's not time for compiz yet on amd64.

Michael

---

### Post by nickdiacre on 2008-07-25
The only yhing I really wanted it for is the dock... awn

Any non-compiz dock apps out there?

Regards

Nick

---

### Post by Cappy on 2008-07-25
Run
```
nautilus
```
in the terminal. Get it to crash and post the error.

---

### Post by VoyeurOne on 2008-08-03
I have the same problem, started on 02 aug o8, I did not install any new software or change any config files, one minute it was working fine , I rebooted and the problem appeared, now when I go to home folder Nautilus crashes, if I force quit I loose my desktop icons, nautilus returns and crashes, the only way to solve the problem is to <ctrl><alt><backspace> or reboot the computer.

I tried running from terminal to see a crash report but I get none.
When I got to Home folder drive spins up and CPU usage goes to 70% on both CPU's

I can browse guest accounts and home folder no problem.

If I sudo Nautilus I can browse to my home folder with no problem.

I hope someone has an idea how to fix this

Thanks

---

### Post by Cappy on 2008-08-03
I had a problem like this once and I installed "thunar" and it told me the error was an invalid directory icon. You could try that.

---

### Post by VoyeurOne on 2008-08-04
Thanks for the reply, I installed Thunar and it works, no error messages or lockup so I'll just continue using it till someone comes up with  fix.





> **Cappy said:**
> I had a problem like this once and I installed "thunar" and it told me the error was an invalid directory icon. You could try that.

---

### Post by VoyeurOne on 2008-08-07
Well this has been sitting for a week or so and still no solution.  Thunar works fine but I prefer Nautilus version 2.22.3 BTW.

---

### Post by VoyeurOne on 2008-08-07
Ok I completely un-installed Nautilus, including config files, basically anything that said nautilus in Synaptic was set for complete removal, which for some reason uninstalls the desktop and a few other goodies.  After the re-install I have complete access to my home directory again.  A rather strange problem to show up out of the blues and God only knows what other functionality I compromised by going radical but whatever works I guess.

---

### Post by philinux on 2008-08-07
I've been radical too. I turned off compiz. Fed up of loosing window decorations and weird crashes. Without it it's much better. Hope they fix it in Intrepid.

---

### Post by VoyeurOne on 2008-08-07
unfortunately that didn't help me as for Compiz it's been my experience that one release works great with Beryl and the next with Compiz or is it my computer??? anyway Beryl might be worth a looksee for your system. All is fine with compiz and Hardy here,  my problem is Miro and I don't think there's a replacement for that program.

---

### Post by davidallan on 2008-09-26
I have the same problem accessing any personal folder ie docs / music / pics etc, X just reboots every time. seemed to be after some OS updates downloaded this week. I've now disabled compiz and now all is fine. Running 8.04 64bit. Ati 1600. AMD.

---

