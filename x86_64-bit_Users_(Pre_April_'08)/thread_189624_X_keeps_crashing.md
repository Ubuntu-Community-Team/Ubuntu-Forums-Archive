---
title: "X keeps crashing"
date: 2006-06-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by markus79 on 2006-06-05
I just installed Dapper on my AMD64 box and X keeps crashing. It flickers for a second as it attempts to load the startup grahpics and login screen. I then get an error that says:

```
The display server has shut down about 6 times in the last 90 seconds. It is likely that something bad is going on.  Waiting for 2 minutes before trying again on display :0
```

Here is xorg.conf:

[http://www.markknutson.com/linux/xorg.conf](http://www.markknutson.com/linux/xorg.conf)

Here is error log:

[http://www.markknutson.com/linux/Xorg.0.log](http://www.markknutson.com/linux/Xorg.0.log)

Any ideas? Thanks!

markus

---

### Post by JoWilly on 2006-06-05
Seems your busid is wrong.

Try changing it to : BusID PCI:5:0:1 (you can also try to comment it out); in the device section.

---

### Post by markus79 on 2006-06-05
[QUOTE=JoWilly]Seems your busid is wrong.

Try changing it to : BusID PCI:5:0:1 (you can also try to comment it out); in the device section.[/QUOTE]

Commenting it out did not change anything.

However, changing the BusID brought a different error:

```
"Failed to start the X server... No devices detected."
```

---

### Post by JoWilly on 2006-06-05
Is it working if you put "ati" or "radeon" instead of fglrx ?

hmm.. your xorg log looks good. Dri is enabled and all....
What card is it, an x800xl ?

---

### Post by markus79 on 2006-06-05
Its a Radeon X800XL (R430)

And making those changes did not help. When I changed it it comes back with the "Failed to start the X server... No devices detected."  I had to use the fglrx with 5.10.

---

### Post by markus79 on 2006-06-05
I saw somewhere it may be an issue with GDM login?? This is where it starts flashing but its never able to load the screen where you login.

---

### Post by JoWilly on 2006-06-05
Well, you won't lose anything if you try to reinstall gdm (sudo apt-get install --reinstall gdm)

Try to post for help in the video section, and don't forget to post a bug report on launchpad (search first).

I hope some kind hearted ati user can help you.

Good luck ;)

---

### Post by markus79 on 2006-06-05
That didn't solve it...

Thanks for your help anyway!

---

