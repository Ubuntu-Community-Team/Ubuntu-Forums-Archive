---
title: "how to swap ctrl and caps lock on ibook"
date: 2005-11-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by craks on 2005-11-23
I know something about caps_lock's abnormal status on ibook, but i want to use  emacs, so swapping this two buttons is very important. Any one can share me your experience, thx!

---

### Post by hentaidan on 2005-11-23
Go to System | Preferences | Keyboard, click on Layout Options, click on the arrow next to Control key position and you select "Swap Control and Caps Lock".

---

### Post by craks on 2005-11-24
[QUOTE=hentaidan]Go to System | Preferences | Keyboard, click on Layout Options, click on the arrow next to Control key position and you select "Swap Control and Caps Lock".[/QUOTE]
You may try it, then you will find it doesn't work fine if you use ibook/powerbook. The reason i have said before for the caps_lock doesn't work like normal, so I can give one way to solve it, but not perfect:

cd /usr/src/

then cd into your kernel source dir

and for 2.6 kernels use this:

--snip--

288,316c288
< #if 1
< 	static int caps_lock_down = 0;
< #endif
<  
< #if 1
< 	if (1) {
< 	  /* HACK to fix caps-lock on Powerbook(?) keyboards */
< 	  switch (keycode) {
< 	  case 0x39:
< 		caps_lock_down = 1;
< 		break;
< 	  case 0xff:
< 		if (caps_lock_down) {
< 		  /* 'caps-lock' is down, must be
< 		   * 'caps-lock' being released
< 		   */
< 		  caps_lock_down = 0;
< 		  keycode = 0xb9;
< 		} else {
< 		  /* must be 'caps-lock' being pressed
< 		   */
< 		  keycode = 0x39;
< 		}
< 		break;
< 	  }
< 	}
< #endif
<  
<  
---
> 
322d293
< 	  if(0) {
327,330c298
< 	  } else {
< 		break;
< 	  }
< 	  return;
---
> 		return;


--snap--

patch your  kernel source and remake it

that works fine for me except for the led of caps_lock:( :( :( :( :(

---

### Post by hentaidan on 2005-11-24
[QUOTE=craks]You may try it, then you will find it doesn't work fine if you use ibook/powerbook.[/QUOTE]

What do you mean it doesnt work properly? It (appears) to work fine on my iBook G4, though as you say the LED doesnt come on.

---

### Post by craks on 2005-11-25
[QUOTE=hentaidan]What do you mean it doesnt work properly? It (appears) to work fine on my iBook G4, though as you say the LED doesnt come on.[/QUOTE]

you mean you can directly swap the caps_lock and ctrl, so the result is caps_lock is ctrl, and ctrl is caps_lock? That works fine for you? I am using ibook g4 too. when i swap it, ctrl is caps_lock but caps_lock is nothing.

---

### Post by hentaidan on 2005-11-26
Now I see the problem!

Nope capslock as control doesnt work.

---

### Post by hatefulthreatening on 2005-11-27
I see we have two threads on this topic running..

I just want some consistent way to save my pinky from that awfully placed control button. Something I can count on behaving the same on all my machines.

I thought I had a good solution. Bind the left alt key on my x86 machine and my left apple key on my ibook to be control. That way my powerful thumbs can do all the work for control and alt.

But no! Apple has to "think broken" once again make both apple keys indistinguishable. They are both keycode 115/Super_L.

---

### Post by craks on 2005-11-30
[QUOTE=hatefulthreatening]I see we have two threads on this topic running..

I just want some consistent way to save my pinky from that awfully placed control button. Something I can count on behaving the same on all my machines.

I thought I had a good solution. Bind the left alt key on my x86 machine and my left apple key on my ibook to be control. That way my powerful thumbs can do all the work for control and alt.

But no! Apple has to "think broken" once again make both apple keys indistinguishable. They are both keycode 115/Super_L.[/QUOTE]

Ja, that is one way, but i prefer caps_lock to be ctrl:rolleyes: , and i should rebuild kernel:(

---

