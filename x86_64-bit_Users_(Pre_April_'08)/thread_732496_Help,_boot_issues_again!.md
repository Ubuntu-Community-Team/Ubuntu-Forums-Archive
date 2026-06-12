---
title: "Help, boot issues again!"
date: 2008-03-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by annihilan on 2008-03-23
I'm posting this in lieu of looking at the other threads because I believe my problem is slightly more 'unique' than the others. Allow me to describe my problem:

1) I put the 64-bit Gutsy 7.10 CD I burned in, and boot from it.
2) I get the brief messages of booting before it shifts.
3) I see that entrancing Orange Bar that slides to and fro.
4) I hear the enchanting African Drum.
5) I get a black screen that advances nil.

Sounds almost like a poem, eh?

I've tried booting in Safe Graphics mode, to no avail.

My specs are (if it helps):
M2N-SLI Deluxe
4GB Kingston Ram
3.0GHz Dual Core Athlon X64
320GB Western Digital SATA, which I'm trying to install to.
I believe this problem is unique because most other people encounter boot problems *after* Ubuntu installed, whereas I get it trying to boot from it.
Help and constructive criticism about not reading the related posts appreciated.

I think I just need to re-burn the disc, but all help is appreciated.

---

### Post by annihilan on 2008-03-23
Come on guys, I really need help.

Bumps!

---

### Post by annihilan on 2008-03-23
Please, I really need help XD!

---

### Post by firecrow8 on 2008-03-27
I had the same issue. and several other people have aswell. it's under the term 'blank screen' and 'monitor issue' or 'video issue'

what's happening is that ubuntu is detecting the wrong monitor or video card drivers. 

you have to manually set some variables at the end of the boot string.

when you get to the install screen press F6, this is the one that lists the options, before the one with the orange loading bar thingy, 
you should see a string of information. this is your boot string.

at the end you'll have to add the new variables.

here's what worked for me

noapic nalapic vga=792

but the vga setting will vary depending on your monitor/video card.

it'll be a little trial and error until you get it right and then it'll work fine and even redetect.

also look into reconfiguring your xserver. there are lot's of posts on how to do this.

and there is an alternate installer that you can download that installs from a text interface so you can set it up without depending on your monitor settings.  this can be downloaded on the same page as the regular download by checking the box at the bottom of the page that says "alternate installation"

hope that helps. I spent a few days until I got my settings right and it's run great ever since. the information is out there.

post your questions if any of this doesn't make sense.

and feel free to hit me with a direct message.

---

### Post by Yellow Pasque on 2008-03-27
It would've helped if you had told us what video card you have since you're having video problems. ;)

---

