---
title: "Gutsy problem...Help"
date: 2007-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by FerBatista on 2007-10-24
I’m using Gutsy 64bit since beta version without any issues, but now from time to time it crashes without notice, it’s like pressing ctrl+alt+backspace. 
I’m using an AMD x2 4200, with 4Gb and a Nvidia 7600 card, the setup is the same as I was using with the 32bit version except for the memories with I only had 1Gb at the time. 

Any ideas on what to check that could be doing this?


Thanks a lot
Fernando

---

### Post by FerBatista on 2007-10-24
BTW the last two times it happened, one I was working on Gimp with two images opened and digikam, when suddently back to the login screen. The other I was running firefox, started the terminal and it didn't respond, it appeared briefly on the taskbar but never started, I tried starting terminal again and suddenly back to the login screen again.

I hope this info gives someone an ideia of what is happening. 

The computer don't reboot it just goes back to the login screen, just like pressing ctrl+alt+backspace.

---

### Post by AegisTalons on 2007-10-24
You may want to check session and see if anything that starts up is forcing you to login/logout. Also try start in "safe mode", it a special session that starts up with the absolute basic programs running. Then run each program one at a time from the session from the terminal and see if you get output.

As for the problem, I have no freaking clue. I occasionally have that problem, but the computer restarts and thats probably because of the Overclocking versus Ubuntu

---

### Post by FerBatista on 2007-10-24
Hi thanks for the ideia, I tried starting in safe mode, as far as I can tell the extra processes running on my regular session are:

-dbus launch
-ssh agent

What are these processes and how do I disable them? If it's safe to do so?

Other than that there's also two compiz related processes witch I now disabled just to check.

---

