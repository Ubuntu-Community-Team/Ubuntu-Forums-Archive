---
title: "default depth for xorg.conf?"
date: 2006-05-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by davygravy on 2006-05-06
My current default depth for xorg.conf is 24.

What are the other options?

What are the pros & cons of decreasing this?

Can I get better 2D performance (like dragging windows) with a lower bit depth?

How much will image quality suffer at the lower bit depths?

thanks

davygravy

---

### Post by jazzmuzik on 2006-05-06
I found this in 'man xorg':

> -depth n
               Sets the default color depth.  Legal values are 1, 4, 8, 15, 16, and 24.  Not all drivers support all values.

Lowering the DefaultDepth value in xorg.conf to one of the above values may speed up your system. Image quality with 1 bit would be black and white. 4 would be a bit better, like a 1980 computer. A value of 8 would make photos look like gif images. 16 might look pretty good. At that point you're getting into more of a photographic look. Just raise 2 to the power of the bit to find the max number of colors. 

2^16 = 65536 (or 65,536 possible colors)

2^1 = 2 (2 colors, generally black and white)

2^24 = 16,777,216

You can get more help on the settings in xorg.conf by running:

```
man xorg.conf
```

'man' means "show me the manual"

---

### Post by davygravy on 2006-05-06
thanks, jazzmuzik.

I know about the man pages... just wanted to here the user perspective of it...

Do some programs override the default value?  If so, which ones?

Is there a way to specify certain programs getting a greater number of colors? 

Is there an interface that allows one to switch bit depth on-the-fly?

---

### Post by jazzmuzik on 2006-05-06
I'm not sure about your questions, only that pressing Ctrl-Alt-Plus or Ctrl-Alt-Minus cycles through the resolutions, but I don't think that will change the bit depth.

Note that the plus/minus keys are the keys on the numeric keyboard.

---

### Post by davygravy on 2006-05-06
Thanks, that last tip is worthy of mention.

Neat.  I'd never seen that before.  Cool.

Is there a "master list of cool key commands" out there anywhere?

---

### Post by slux on 2006-05-06
Changing bit depth for a running X server is not possible for now.  I don't know if it's planned by Xorg, they already made resolution changes where the actual desktop changes it's size as well (unlike Ctrl-Alt-+/-) possible so it doesn't seem that far fetched.

Bit depth also can't be specified separately for specific apps and no app can override it. For games this would be somewhat useful...

---

