---
title: "Turn off gray startup mode"
date: 2006-11-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by rcg on 2006-11-05
Is possible turn of bug gray startup mode and boot in text mode in Edgy 64 ?

---

### Post by John.Michael.Kane on 2006-11-05
Sudo gedit /boot/grub/menu.lst

```

**Find the line that says:**
# defoptions=quiet splash

**remove the "splash" so it looks like:**
# defoptions=quiet

**For changes to take effect, after saving your edits, you will need to run the command:**
sudo update-grub

Then reboot

```

---

### Post by almalaci on 2006-11-05
And then how do you make it appear in color mode like it was in dapper?

---

### Post by RAOF on 2006-11-05
AFAIK, you don't.  Grayscale only on x86-64, to work around a bug which would make uspash segfault (after a couple of minutes sitting at 100% CPU utilisation) without fail.

Expect a return to colour in Feisty :)

---

### Post by almalaci on 2006-11-06
OK. In the meantime I tried the 1386 install and the colors are great! :)
Will Feisty be more supportive to amd64 CPUs? It's not just the boot screen I'm talking about but the other bugs I have with an x86_64 install and don't with an i386 makes me think edgy is too edgy for us amd64 users..

---

### Post by pony-tail on 2006-11-06
I doubt that it could be worse - the issues I am having are incredible - most things work but just not quite right - it's mostly just small but annoying things - I am still dual booting with "Dapper" because of this - I do not quite trust "Edgy64" for full time use

---

### Post by Kilz on 2006-11-06
With all the complaints Im reading I may just skip Edgy. Dapper works just great. It has a lot of time left for security updates. To tell the truth the only thing I see as a must have was Firefox 2.0. But I have that on Dapper thanks to my script.

---

### Post by Dazed_75 on 2006-11-06
> **SD-Plissken said:**
> Sudo gedit /boot/grub/menu.lst

```

**Find the line that says:**
# defoptions=quiet splash

**remove the "splash" so it looks like:**
# defoptions=quiet

**For changes to take effect, after saving your edits, you will need to run the command:**
sudo update-grub

Then reboot

```

Thanks for this.  BTW, if you change the "quiet" to "verbose" you can get some of the messages back as well.  At least on the i386 version.  Still have not found any way to use a better (wider/higher) vga mode or to use the color variable usefully, but it is an improvement over the dead screen waiting of the quiet splash screen meant for people who don't care if anything is actually happening.

---

### Post by rcg on 2006-11-08
verbose looks fine. Thanks.

---

