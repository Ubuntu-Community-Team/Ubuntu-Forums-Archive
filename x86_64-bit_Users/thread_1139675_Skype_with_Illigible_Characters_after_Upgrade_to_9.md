---
title: "Skype with Illigible Characters after Upgrade to 9.04"
date: 2009-04-27
forum: x86 64-bit Users
---

### Post by srangelov on 2009-04-27
Hi all!
I upgraded today my PC to Ubuntu 9.04 and my Skype is not showing correctly. All characters within the Skype window are not shown correctly - they are corrupted. Please, see the attached screenshot.
I tried reinstalling skype, msttcorefonts, NVIDIA graphic card driver 180. Nothing helped.
Does anyone any idea how to fix it?
Thank you,
Sotir
P.S. This is my 4-th upgrade to 9.04 on separate PCs and this is the first such issue. On the other 3 PCs Skype works correctly.

---

### Post by Psicolonia on 2009-04-27
uau! I'm gonna do this! This is what I call security! :)

Sorry for not being able to help, honestly.

---

### Post by srangelov on 2009-04-27
And the strange thing is that the characters are only corrupted within the Skype window. If you notice the window title is OK. I do not find this problem with any other program.

Sotir

---

### Post by srangelov on 2009-05-13
Here is the solution:

So if you are running into this error, all you have to do, is:

1. exit all qt applications,
2. go into &#8220;System>Preferences>Appearance>Fonts&#8221;,
3. change VRGB/BGR to RGB/BGR.

It is taken from [here]("http://ubuntuforums.org/showthread.php?t=1125382").

---

