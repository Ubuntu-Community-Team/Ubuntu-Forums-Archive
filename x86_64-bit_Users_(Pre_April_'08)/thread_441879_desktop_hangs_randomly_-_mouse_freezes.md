---
title: "desktop hangs randomly - mouse freezes"
date: 2007-05-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by GOwin on 2007-05-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/114365](https://bugs.launchpad.net/ubuntu/+bug/114365) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm using 64-bit Feisty Fawn on an MSI S270 machine.  I've had no problem with the system prior to upgrading from Dapper (decided to skip Edgy).

I've been on Feisty for about 10-days now and I'm going crazy with the desktop hanging on me while I use the mouse to work. This could happen while dragging a file from one location to another, or adjusting columns in a spreadsheet. I've never experienced this with prior Ubuntu versions. (The mouse pointer would freeze to an icon relaed to what it's doing - ie, hand icon while moving a window, or a copy icon when copying files, or pointer for adjusting columns when adjusting spreadsheets)

What I do is restart X (since I noted that the caps lock key still  work)  and log again. I'm getting irritated by this. Anyone experiencing the same problem?

By the way, I'm using an usb optical mouse from Logitech.

---

### Post by Cappy on 2007-05-13
Yes and although I've fixed other problems, this one still persists. I've been trying to narrow it down. I removed Flash 9, thinking it might be that but it still happens. Running Opera 9, Nvidia proprietary drivers, gaim, and apache2. I've been trying to narrow down the problem this week. Exactly the same problem.

Using USB Logitech G5 mouse with mouse polling set to 2. USB Creative Fata1ty keyboard.

---

### Post by Fredman on 2007-11-22
I've got the same problem here: my Microsoft Wireless Laser Mouse 5000 freezes randomly. I can work all day without a hitch, but can have multiple hangs in an hour a day later. 

At first I thought it to be a Firefox / Flash problem, but after a few hangs without having used Firefox at all I've changed my mind. It happens when using Nautilus to copy files, reading mail using Thunderbird, etc.

I tried to see if it's an USB problem, so the next time the mouse hanged I plugged in an USB memory stick to see if it would *do* something. Worked flawlessly: the memory stick was recognized and usable. The mouse on the other hand, was still as dead as before. It was back in the land of the living after a reboot though.

No problems in Vista or XP, but the GParted live CD I used to repartition my drives had the same problem. 

Looks like a kernel-thingy....or something...

---

