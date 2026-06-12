---
title: "32 turned into 64?"
date: 2008-07-15
forum: x86 64-bit Users
---

### Post by chrispottrell on 2008-07-15
Hi guys,

I've been using an image of a 32bit Ubuntu installation on a 64bit chip machine. This has been copied to approx 30 machines.

uname -m returns i836, so I assumed all was well, a 32bit OS was running on a 64bit chip machine.

A couple of the machines which have been manually updated are now showing via uname -m that they are 64bit!

Has the kernel been updated to a 64 from 32, or is this not possible?!

---

### Post by jespdj on 2008-07-15
A 32-bit Ubuntu installation does not automatically convert itself to 64-bit through automatic updates - that's impossible. It's currently not possible to upgrade a 32-bit installation to 64-bit; you'd have to reinstall the whole operating system.

What do you see if you type uname -m? If you have installed 64-bit Ubuntu, it will show x86_64. And if you see that, then you have (or someone else has) installed 64-bit Ubuntu.

---

### Post by chrispottrell on 2008-07-15
This is my PC that nobody else has access to, I don't even have the 64bit CD burnt!

How the 'ell did that happen then I wonder. I know I have been doing a lot of updating on it to keep it up to date.

Mine gives x86_64, another one from the same image returns i836.

---

### Post by philinux on 2008-07-15
Have a look at firefox, help, About mozilla.

See if it's the 64 bit version installed.

---

