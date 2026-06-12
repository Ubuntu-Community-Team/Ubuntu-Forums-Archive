---
title: "Shutdown doesn't work"
date: 2006-07-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by s_h_a_d_o_w_s on 2006-07-29
Nothing of that sort works. New login, shutdown, switch user, dosn't work,

I think mayber I need to get the right drivers.

ecs-rs482-m

radeon express 200 graphics

ATI chipset  AMD 64 proc.

I got the ATI drivers for linux from their website,but ecs doesn't offer any drivers for linux. what should I do?

---

### Post by Ziox on 2006-07-29
umm..just wondering..does sudo reboot or sudo poweroff work?

---

### Post by s_h_a_d_o_w_s on 2006-07-29
sudo poweroff seems to,

it closes X, the it asks me to login, but in a terminal, after a few seconds, it shuts down.

---

### Post by Ziox on 2006-07-29
yeah i get that when using the normal shutdown mode (via buttons), but perhaps it has something to do with acpi...i have no idea why it won't shut down correctly, I just know a few commands to test somethings out...

sorry i couldn't be more helpful

---

### Post by s_h_a_d_o_w_s on 2006-07-29
Thanks anyway! I think I might go back to 32-bit on my 64 proc, but the only problem is that there are random freezes

---

### Post by Kilz on 2006-07-29
The problem is probably the 8.25.18 drivers. It will effect either 32bit or 64bit. Switching will be a waste of time, the 8.25.18 drivers are in the repositories for both. [I would sugest upgrading to the 8.27.10 drivers following this howto.]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually") Welcome to the club of people bitten by this bug. I also have radon express 200 graphics.

---

