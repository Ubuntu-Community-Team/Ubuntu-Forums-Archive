---
title: "[SOLVED] Slow booting"
date: 2008-11-24
forum: x86 64-bit Users
---

### Post by JeyPeyy on 2008-11-24
Yesterday I posted [this]("http://ubuntuforums.org/showthread.php?t=991303"), and I fixed one problem, but I still have other problems: The boot time is very long and I can't get compiz fusion working. 

The progress bar at boot gets up to about one tenth, after that it freezes for like 2 minutes, and then it boots up quite fast.

OpenGL works fine, but compiz-fusion just wont work. If I try to change the window manager to compiz with the fusion-icon, I get no frame and I can't move the windows.

I do not know if those things are caused by the same thing, but it occured at the same time.

---

### Post by cariboo on 2008-11-24
Install bootchart, this will list all the processes during startup. Bootchart is in the repositories, You can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

The chart will be located in /var/log/bootchart.

Jim

---

### Post by JeyPeyy on 2008-11-24
> **cariboo907 said:**
> Install bootchart, this will list all the processes during startup. Bootchart is in the repositories, You can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

The chart will be located in /var/log/bootchart.

Jim

I installed bootchart, but there is nothing in /var/log/bootchart.

---

### Post by JeyPeyy on 2008-11-24
bootchart just doesn't seem working. someone want to help me out?

---

### Post by JeyPeyy on 2008-11-25
Lol I feel like a total jackass. I didn't understand I had to reboot :P

Here's my chart. Looks like it has something to do with vol_id, but I'm not sure.

---

### Post by istblacken on 2008-11-25
> The progress bar at boot gets up to about one tenth, after that it freezes for like 2 minutes, and then it boots up quite fast.
this happens to me if i don t plug the ethernet cable while ubuntu is booting. try pluging the ethernet cable and make sure you are connected to the internet then boot into ubuntu that 2 minute freezing shouldn t occur as it was my case.

---

### Post by JeyPeyy on 2008-11-25
> **istblacken said:**
> this happens to me if i don t plug the ethernet cable while ubuntu is booting. try pluging the ethernet cable and make sure you are connected to the internet then boot into ubuntu that 2 minute freezing shouldn t occur as it was my case.

Don't think that's the problem. Ethernet is always connected and I don't have any problems with the internet.

---

### Post by JeyPeyy on 2008-11-25
Can someone please analyze the chart?

---

### Post by cariboo on 2008-11-25
I looks like udev is having a problem with some of your hardware, unfortunately it doesn't say what it is. It could be something is misconfigured, or it could be a hardware problem. could you paste the output of:

```
lspci
```

and

```
sudo lshw
```

in your next post.

Jim

---

### Post by JeyPeyy on 2008-11-25
I've attached the outputs:

---

### Post by DarkMartyr on 2008-11-25
I'm having a similar problem. Here is all my output.

---

### Post by JeyPeyy on 2008-11-26
Someone?

---

### Post by JeyPeyy on 2008-11-28
I couldn't wait anymore, so I reinstalled my computer. Should I mark this as solved?

---

### Post by scottuss on 2008-12-10
Is your problem solved? If you're still having issues let me know and I'll see what I can come up with.

Otherwise, yep just mark it as solved.

:p

---

### Post by bsmith1051 on 2008-12-12
> **cariboo907 said:**
> Install bootchart, this will list all the processes during startup. Bootchart is in the repositories, You can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

The chart will be located in /var/log/bootchart.
Great suggestion!  Is there a homepage for it, though, or other documentation for deciphering it?

UPDATE:
Nevermind, I can Google!  [http://www.bootchart.org/](http://www.bootchart.org/)

---

### Post by JeyPeyy on 2008-12-16
> **scottuss said:**
> Is your problem solved? If you're still having issues let me know and I'll see what I can come up with.

Otherwise, yep just mark it as solved.

:p


I reinstalled ubuntu, so I solved it that way. But now it seems like I have the same problem again!

Here's my output this time:

---

### Post by JeyPeyy on 2008-12-17
Please! I don't want to reinstall my computer again

---

### Post by scottuss on 2008-12-18
OK so what happens if you use the Compiz Icon to select the Metacity Window manager and GTK Window decorator?

---

### Post by scottuss on 2008-12-18
Just though also, when booting your PC, at the GRUB prompt where it says booting in... press ESC for a menu, press ESC, select your kernel that you would normally boot and edit the line where it says quiet take this out, then instead of showing the splash screen that keeps freezing it will show you exactly what the computer is doing at that point (it will only do it for one reboot, next time the splash will re appear)

Note down what is on the screen at the time of the long delay and post it here.


Sorry for the long post! :lolflag:

---

