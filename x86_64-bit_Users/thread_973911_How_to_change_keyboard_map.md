---
title: "How to change keyboard map?"
date: 2008-11-07
forum: x86 64-bit Users
---

### Post by Che.SSL on 2008-11-07
Hi,

I`d like to change my keyboard map, in particular I need to switch CAPS LOCK by DELETE and the other way around (please don`t ask why).
On Ubuntu 8.04 (32bit) this was done by changing the entries in xfree86 under /usr/share/X11/xkb/keycodes.
Unfortunately this doesn`t work anymore under Ubuntu 8.10 (64bit).

Does anybody have an idea on this?

Thanks.

---

### Post by Jalden on 2008-11-08
I also want to know how to do this!

I bought a dell mini 9, and can't stand where the "/' key is. It significantly slows down my typing. I would like to switch it with the :/; key.

EDIT: I have the same version of Ubuntu.

---

### Post by Icebear on 2008-11-09
Hi Jalden
I would first add a additional latin bases keyboard so if you make a mistake you can change to the second keyboard and correct any changes. 
To do this goto System>Preferances>Keyboard an  hit the layouts tab and choose a layout the Finnish keyboard is similar to the us keyboard.
If you need to change  the keyboard I think the default keys to change the keyboard is the both alt keys. 

Then I think what  you want to do is do 
sudo cp /usr/share/X11/xkb/symbols/us /usr/share/X11/xkb/symbols/us_BU

then sudo gedit /usr/share/X11/xkb/symbols/us

then find the following

 key <AC10> {	[ semicolon,	colon		]	};

and change it to

 key <AC10> {	[ 	slash,	question	]	};

then find the following line 

 key <AB10> {	[     slash,	question	]	};

and change it to 

 key <AB10> {	[     semicolon,	colon	]	};

hope it works out for you!!

---

### Post by Jalden on 2008-11-14
Thanks!

[INDENT]*sudo cp /usr/share/X11/xkb/symbols/us /usr/share/X11/xkb/symbols/us_BU*[/INDENT]

When I type this I get "command not found".

"sudo gedit /usr/share/X11/xkb/symbols/us"

This worked, and I was able to edit the keys.  But after saving, it did not seem to change the output when I type with those keys.

Any suggestions?

---

### Post by Icebear on 2008-11-14
Maybe you could add a new US keyboard layout.
Then go System>preferences>Keyboard
hit layout tab
hit the + button
choose country United States
variants USA

Then in the panel (the very top part of the screen) hit with right mouse button >add to panel

and scroll down to keyboard indicator and click

then hit +add

then click with mouse to USA2
and hopefully you will be in luck
keep me posted

---

