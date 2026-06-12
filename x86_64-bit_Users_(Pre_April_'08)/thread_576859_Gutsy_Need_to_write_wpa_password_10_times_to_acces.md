---
title: "Gutsy: Need to write wpa password 10 times to access wireless network"
date: 2007-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by kwaanens on 2007-10-15
Just like the subject says.
Counted on login right now: 9 times. I know I punched the correct password every time.
Intel 3495 card.

Has not failed me on Feisty i386

Not sure if this is a 64 bit problem.

Does anyone have any hints?

- Ketil

---

### Post by praxis22 on 2007-10-15
are you opening a tabset with firefox? What exactly are you doing, how is the password dialog appearing?

---

### Post by kwaanens on 2007-10-15
I boot in and nm-applet is started. First I enter my keyring password for nm-applet, and then it doesn't connect.

Just thought of something: I have automatic login set up, is that a possible reason for this?

- Ketil

---

### Post by kwaanens on 2007-10-15
> **kwaanens said:**
> Just thought of something: I have automatic login set up, is that a possible reason for this?

Looks like it might be, or else my restart was a fluke. I'll see the next couple of days.

- Ketil

---

### Post by saru411 on 2007-10-16
ive found on my laptop, vostro 1500 with dell wireless g min card, tends to do this on curtain networks. the network at work and one of the coffee shops i frequent will not connect. i also use the auto connect configuration and i have to use ndswrapper to get my wifi working properly on my laptop. ive noticed if i hit configure manually and make a fake connection point, then after it tries to connect to this fake connection change it to your true wifi in the area it works just fine. not sure why i have to do this because at home it works just fine every time. try manually connecting to a network that does not exist and then connecting to your real network. it works for me.

---

