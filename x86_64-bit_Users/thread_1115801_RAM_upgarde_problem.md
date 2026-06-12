---
title: "RAM upgarde problem"
date: 2009-04-04
forum: x86 64-bit Users
---

### Post by manishk on 2009-04-04
I added 2GB more memory to my existing 512MB RAM.

GNOME is not starting. I just get a blank screen and sometimes it reboots.

BIOS was able to identify the new memory module. memtest works fine. Recovery mode works fine.

Any idea about what the problem could be?

P.S: I am really sorry if this was asked earlier...I just couldn't find the answer.

---

### Post by Yellow Pasque on 2009-04-04
It sounds like a problem with the RAM settings in the BIOS (or possibly bad RAM).
You added a 2GB SO-DIMM in the expansion slot?

I wish I could help more, but Compaq's documentation is pretty generic and lacks details about the RAM specifications.

---

### Post by Kareeser on 2009-04-04
Did you make sure not to mix different amounts of RAM in the dual-channel slots?

---

### Post by phlembob on 2009-04-04
hi, RAM are finicky things.  Are all 512 units the same make and number?  The delays need to match.  A problem occurred with 2 gb or with more than 2 gb.  4 gb sometimes won't read complete.  3 gb seems to read ok though.  If you can be a little more specific --- we can help you better.
:guitar:

---

### Post by manishk on 2009-04-04
Oops...I never knew SO many things are involved. Thanks for letting me know!!

I'll try to find out more about what exactly I did and get back to you guys. As of now, I know...

There are two modules: 512MB (HP) + 2GB (Kingston)

I added it in the DIMM expansion slot.

The only thing I verified was if the new RAM was DDR2, 667 MHz.

I also read somewhere that it could be due to the video card using the main memory (since only GNOME seems to be affected).

---

### Post by lindsay7 on 2009-04-04
how many memory slots did you have. If you just have two and added the extra 2 gigs to the 512 and they do not match up, that could be you problem. Try taking out the 512 and put the 2 gig stick in the first memory slot and see if your computer will start like it should. If it does you can add the 512 stick in the second slot and then try to see if your computer starts and runs like it should. Go with whatever arrangements works best. It could be that you can not use the 512 with your new 2 gigs.

---

### Post by phlembob on 2009-04-05
OK, a quick fix should be in line with your want of more memory.  Take out the HP memory.  Replace the HP memory with the Kingston.  If I understand correctly you should then have 2 gb memory.  If your Kingston are the same this should work.

Now a quick lesson --- Your computer is a HP, I assume this because it came with HP memory.  Your computer will have a memory rating --- This will tell you if you have Dual Channel capability or not.  Non-dual channel memory will work in the memory slots at reduced speed.  Your bios will see the change and it should make the automatic adjustments.  This should stop the machine confusion of what memory is installed.

Make a statement after you have done this and if you have more questions we can go on.
:guitar:

---

### Post by manishk on 2009-04-05
Here is what my memory slot looks like:
[http://tinypic.com/view.php?pic=2mrbhjm&s=3](http://tinypic.com/view.php?pic=2mrbhjm&s=3)
(The yellowish thing towards the bottom of the pic)

All I could see was one memory slot and the new stick was inserted into it.

And this is the specification sheet for my laptop (yes, it is a HP)
[http://h18000.www1.hp.com/products/quickspecs/12447_na/12447_na.HTML](http://h18000.www1.hp.com/products/quickspecs/12447_na/12447_na.HTML)

I guess the other memory slot is buried inside and I need to hunt for that kind of screw driver (which will be probably take another day or two for me) before I can continue with the experiments!!

I;ll do that and tell you what happens.

Thanks phlembob and lindsay ;)

---

### Post by phlembob on 2009-04-05
Ok, it is a HP laptop. I am not that familar with laptops but I'm sure the same things apply with a difference in physical design.  Dual Core Turion will make the most likely RAM Dual channel.  Your new Kingston looks like the HP RAM and will fit in the same place or no?  I don't want to mess things up because I mainly play with Desktops, however back years ago I did work on a couple of laptops.  Things have changed and RAM is one thing changing with newer processors.  Because laptops have many little access points you will need to read the service manual for where and how to install the RAM.
Keep on Jammin:guitar:

---

### Post by lindsay7 on 2009-04-05
What you show in the picture is the place where both memory sticks go. They are placed one on top of the other. Take out the 512 stick and put the 2 gig stick in its place and see if that solves the problem. If it does you can add the 512 stick to the second slot and then see if your computer will boot with in included, if not just go with the 2 gig memory.

---

