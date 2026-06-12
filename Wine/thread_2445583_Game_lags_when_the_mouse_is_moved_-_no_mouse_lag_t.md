---
title: "Game lags when the mouse is moved - no mouse lag though"
date: 2020-06-16
forum: Wine
---

### Post by jcdenton1995 on 2020-06-16
Hello all,

So I've been playing a little bit of 'Commandos: Behind Enemy Lines' using WINE, it's old school!

But unfortunately there is a bug where when the mouse is moved, the game lags hard and all animations slow right down until the mouse is stationary again. Other than this the game runs fine, which I would think it should because hardly anything goes on in it.

So far I've tried...

[LIST]
[*]disable mouse acceleration
[*]disable touchpad
[*]tried another mouse - same problem
[*]tried the touch-pad - same problem but less noticeable
[*]tried changing the mouse polling rate via the usbhid module parameters but this doesn't result in any change in practice (as measured by evhz) despite a change in the value stored in /sys/module/usbhid/parameters/mousepoll
[/LIST]

I have searched online extensively but it's one of those problems that many people have had and there are many variations of it (I even think I've had it before on windows but I cant remember specifically where).

I know it's 'one of those' but just wondering if anyone has any ideas?

---

