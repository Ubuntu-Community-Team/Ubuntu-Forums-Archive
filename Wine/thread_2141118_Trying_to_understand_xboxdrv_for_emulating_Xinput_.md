---
title: "Trying to understand xboxdrv for emulating Xinput under Wine with a non-Xinput gamep."
date: 2013-05-01
forum: Wine
---

### Post by Erquint on 2013-05-01
Hope I chose the right subforum.

Well, I have the greatest, *in my opinion*, gamepad of all -- **Thrustmaster Dual Trigger 3-in-1**. I love it.
But you all know that almost all of **Windows** games require **Xinput**-compatible controller. (***Microsoft**'s indirect monopoly enforcing...*)
In my experience with **Windows** -- I used to employ **x360ce** **Xinput**-emulator and it was doing the job perfectly fine fooling those games.
The problem is -- it doesn't seem to work under **Wine**. Every time the **xinput_3.dll** wrapper library is loaded -- **Wine** crashes.
I tried installing **xinput** dlls with **winetricks**, since **x360ce** uses native **MS** libraries being a wrapper, but to no avail.
Considering **x360ce** translates **Dinput** to **Xinput** and there's no actual **Dinput** under **Linux** -- the use of **x360ce** seems inadequate anyway.

So I heard about **xboxdrv** and, as I understand, *though it is not the main intended use of it* -- it is possible to use it for **Xinput** emulation for games running under **Wine**.
But the [huge manual to **xboxdrv**]("http://pingus.seul.org/~grumbel/xboxdrv/xboxdrv.html")  doesn't fit in my mind. I feel like I'm at a loss. Could someone clarify things for me or, *if possible*, help me configuring it properly for my gamepad?

[HR][/HR]From freedom came elegance

---

