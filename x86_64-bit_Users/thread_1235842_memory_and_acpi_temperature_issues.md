---
title: "memory and acpi temperature issues"
date: 2009-08-09
forum: x86 64-bit Users
---

### Post by def_mornahan on 2009-08-09
I have an Acer 5102 WLMi, three years old. It has spent a lot of that time in the basement, which does get moist sometimes when it rains. I ran a memtest before installing Xubuntu the other day and noticed that it popped up some errors, but since it had been running fine for years, I went ahead and installed and started ripping my CDs (both of these were projects I'd been planning to do for a while). It's been ripping CDs for two days. I put conky on it and noticed that the temperature was running in the 70s C. I put a game on it and it was running buggy under Wine, so I tested the memory again and made more careful note of what happened:
 
Test 2:
Pass 0, Failing Address 0000000000 - 0.0 Mb, Good ffffffff, Bad 00000000, etc.
 
Test 3:
Several errors, all of the same form. The Good pattern changes through the progress of the test, the Bad is always 00000000.
 
Test 4: Most of the way through this test, the computer will power itself down without warning.
 
I found that this will happen whether the computer has both memory sticks in it or either one by itself. I tried to boot up after the last test and was told that the temperature was over the danger line of 95 C and the machine was shutting down. Then the graphic for booting up continued for a while before it starting shutting down. I took the cover back off and cleaned out the fan, which was indeed quite dusty, let it cool down a few minutes, but more or less the same thing happened. I left the computer over the air conditioning vent for a hour and booted it again. Same thing. It is definitely not 95 C now...
 
So anyway, I have two worries:
- I doubt that both memory sticks are screwed up in exactly the same way, so I'm concerned that something on the motherboard is broken between the memory and the rest of the system.
- I wonder if I've melted or permanently damaged the temperature sensor and/or other things on the board by running it too hot and/or too humid.
 
Is there something I can do besides get a new laptop? The temperature thing really has me confused. I ordered two sticks of memory the other day and will try them tomorrow, but if the computer won't boot anyway, it's not much interest...

---

### Post by shane2peru on 2009-08-11
You didn't mention an much about the specs of the computer, so this is kind of a shot in the dark.  What kind of hardware do you have?  I have ATI video on my laptop, and as a results it overheats with the default ubuntu stuff installed.  I had to install the proprietary drivers.  As I stated, this may not be your issue at all.  It would be good to mention the specs of the computer.  

As for your memory sticks, I doubt it is this, because if you tried each one individually and it didn't seem to have a problem, it is doubtful, but still a possibility.  Seems to me that something else is not right.

Shane

---

### Post by tgalati4 on 2009-08-11
Try cleaning your memory sticks with an eraser.  Use a q-tip and alcohol to clean up afterwards.  Ground yourself so that static electricity won't do any more damage.

If your RAM fails memtest after cleaning, then it's time for new RAM.

To be confident in your RAM, you should run memtest for 30 complete cycles.  Statistically this represents a large test population.  It will probably take overnight to finish.

Any errors during the 30 cycles means that your system will be unreliable. It could be the RAM or motherboard (perhaps corrosion due to moisture) or bad soldering of the sockets (a common problem).

Google your model number.  Perhaps others are having the same problem.

---

### Post by Yellow Pasque on 2009-08-11
Try the new memory. If you still get errors, then my guess would be a bad memory controller (the memory controller is integrated into the CPU on AMD systems). You would need to replace the CPU.

---

### Post by shane2peru on 2009-08-11
Ahh like I said it was kind of a shot in the dark.  I would go with the above mentioned things first.  Perhaps they are more on the right track.

Shane

---

