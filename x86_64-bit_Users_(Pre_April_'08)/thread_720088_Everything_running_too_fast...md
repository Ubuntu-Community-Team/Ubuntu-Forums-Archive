---
title: "Everything running too fast.."
date: 2008-03-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by gevie on 2008-03-09
I have recently installed Ubuntu 7.10 for AMD 64  on my computer. It is a built system  with an Abit mb, 1 g ram, I am just using the video and audio suplied on the motherboard. Since my install it seems that everything is running extremely fast.  The clock will register 3 or 4 minutes every minute.  When typing on the keyboard it will sometimes enter the same letter  3 to 5 times when I hit a letter once on the keyboard.  Trying to  play  a game like Breakout is impossible.  The ball moves so fast it  is almost impossible to hit.  I am pretty new to  computers but have used  Ubuntu for about a year on another machine. I am 65 years old and not very computer literate.  Any help I can get would be greatly  appreciated..

Thank you in advance..

Gevie

---

### Post by davarino on 2008-03-10
I'm going to make a fast guess and say that you possibly are running "over-clocked". This is indicated to me by you having speed-up problems with both keyboard and clock.

When you boot up next time, try to turn-down the clocking speed by getting into your BIOS. This may take several attempts because the instructions for getting into the BIOS will flash up on your screen within the first 15 seconds or so after you power on. Hitting the Delete, Backspace or F1 keys may bring you to the BIOS configuration menu.

If you get that far, look for the clock speed (it will show in MHz). Before you reset it, write down its present value. (You never know if you may need this information in the future). Reset it to a lower MHz speed and save it (probably by pressing F10 key).

Reboot. If I was right, you will see an instant improvement.

If not, go back and replace the old clock speed and get in touch with someone in a local Linux User Group.

Good luck!

---

### Post by gevie on 2008-03-10
Thank you for your prompt reply.  I did as you said and looked at the clock speed.    I  found the CPU frequency at 200 which was the minimum listed and also the PCIE  clock was shown as 100  MHZ also the minimum listed amount.    Another thing I forgot to mention previiously was that  when initially turning on the computer it takes almost 5 minutes before it even enters the boot menu.  So I didn't have any  problem being able to hit the del key to enter the bios.  When I found the frequencys at the minimum I decided not to make any changes.  I am beginning to think I may have either a bios or a hardware problem.
What do you think?

Thanx

Gevie

---

### Post by davarino on 2008-03-10
(message deleted)

---

### Post by jespdj on 2008-03-10
I don't think messing with clock settings in the BIOS is a good way to solve this problem!

I had a problem like this (the clock running much too fast) a few years ago, with an old 64-bit version of Ubuntu (I think 6.06) - at that time it was a bug in the Linux kernel which was solved in the next version of Ubuntu (6.10).

I'm sorry I don't have a real solution to the problem. You could try running the 32-bit version of Ubuntu to see if you have the same problem (when I had the problem above it was only in the 64-bit version), or you could try the latest alpha version of Ubuntu which is now in development - [Hardy alpha 6](https://wiki.ubuntu.com/HardyHeron/Alpha6).

---

### Post by Jouke74 on 2008-03-10
I also suggest to leave the BIOS clock and frequency settings as is, if you unsure about what you are doing. Nearly all important hardware might get damaged. 

Are you sure that your normal clock can synchronize? 
And is all your main hardware (CPU, Motherboard) correctly recognized?
Please open a terminal and type "dmesg" at the prompt. 
Report things which are out of the ordinary.

---

### Post by prshah on 2008-03-10
> **gevie said:**
> 
Since my install it seems that everything is running extremely fast.  The clock will register 3 or 4 minutes every minute.  When typing on the keyboard it will sometimes enter the same letter  3 to 5 times when I hit a letter once on the keyboard.  Trying to  play  a game like Breakout is impossible.  The ball moves so fast it  is almost impossible to hit.  

Gevie

Boot from a live CD (ubuntu install CD)... Dont install it, but use it for a couple of minites, does that work fine?

Or try to add the "noapictimer" when booting:

Press ESC when GRUB is loading,
the press "e" on the first line to edit
A new screen opens up, go to the last line and press "o" (lowercase o)
press down arrow, then "e" to edit
type in "noapictimer" (without the quotes)
press enter
continue booting (see options at the bottom of the screen on how to continue booting).

Cheers,
PRShah

---

### Post by gevie on 2008-03-16
I have tried all of your suggestions and nothing seems to work. I even did a fresh install with no luck.

Thanks to those who tried to help and If anyone has any new ideas I sure am open to them..

---

### Post by dptxp on 2008-03-16
As suggested earlier, try the 32 bit version or any other distro.
By overclocking too much, you may damage your hardware.

You can try 64-bit Ubuntu Hardy Heron to be released in April 2008.

I am using 64 bit on AMD-64 Turion, no problems.
You can post your machine specs. You may get better help.

---

