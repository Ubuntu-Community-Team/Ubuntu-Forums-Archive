---
title: "kernel recompile 1000mhz help."
date: 2008-02-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sir Jake on 2008-02-17
Hello there, I am still pretty new to Linux, I am running a server on Ubuntu 7.10 Desktop.

Computer specs are.
two quad core xeon e5320 1.86ghz 1066mhz 2x4 cache
tyan mother board 4 gigs of ram
two 250G harddrives in Raid 1

When I type 'uname -r'  
2.6.22-14-rt
is what I get.
 
I need to setup the kernel so it's 1000mhz
As I will be running gaming servers off of this server.
Coud someone please help setup this?
What tool will I need, if any?
I looked around on here for a few things.
Thanks for any help in advance.

---

### Post by khensucat on 2008-02-17
You'll have to recompile your own kernel if the timing in the RT kernel isn't what you need.

---

### Post by Sir Jake on 2008-02-18
So how does one go about changing it to 1000mhz?
I tried something on here but it went way off and never worked. Had to reload my old one.  The mhz is all I need to change. :)
If someone could post a link even that would be great. Thanks.

---

### Post by khensucat on 2008-02-18
Well, if you are recompiling and using the old make config files, you won't see the custom options. You'll want to do it the long way, and to through all of the options and modules until you find the setting for that kernel, set it to how you want, and then compile fresh ;-)

---

### Post by jespdj on 2008-02-18
> **khensucat said:**
> You'll have to recompile your own kernel if the timing in the RT kernel isn't what you need.
As far as I know an RT version of the kernel is also available in the Ubuntu repository, so you can just install it via Synaptic - no need to do difficult kernel compilation things yourself.

---

### Post by Sir Jake on 2008-02-18
So, I just did a fresh install again because I was stupid and changed root options that I seen on here for something. 
 
"As far as I know an RT version of the kernel is also available in the Ubuntu repository, so you can just install it via Synaptic - no need to do difficult kernel compilation things yourself."

I thought there would be a real time kernel custom made to 1000mhz that I could just download and use for myself?
Am I able to do this?
If so that would be best for me, as I am way to new to do
"the long way, and to through all of the options and modules until you find the setting for that kernel, set it to how you want, and then compile fresh"

I think I tried something like that yesterday with some program I downloaded. It was just asking me yes or no for like 10 minutes. 
I never knew what I was doing so I had to stop it. :)
Even a good link to a good tutorial on how to edit my own. 
How do I find out what the rt kernel mhz is?

---

### Post by thaumielx72 on 2008-02-18
If you are setting up a server I think you need to go in the other direction.  Someone with more Linux/Ubuntu experience correct me if I'm wrong:  What the 1000mhz signifies is that all programs running will check with the kernel every 1000mhz, meaning all processes will be interrupted a couple hundred (thousand) times a second to see if there is any input from the keyboard, mouse, or any other program.

A server (to me) means you will be running pretty much one program so you want it to be interrupted As Little As Possible - not As Much As.

That would mean you would want as low a mhz as you can get, not as high as.

:)

---

### Post by Yellow Pasque on 2008-02-19
[http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)

---

### Post by Sir Jake on 2008-02-19
I'm not sure myself, I was told from a bunch of people that my kernel needs to be 1000mhz inorder for the gaming servers I run on them to have higher fps.
Right now with the stock kernel I am getting 122fps on the server.
befor when I used the real time kernel it would go up to 240fps.
It's for srcds "Counter Strike Source Server"

---

### Post by Sir Jake on 2008-02-19
Thanks Temüjin, just seen this today. I guess I never seen your post when I did my reply.

---

### Post by CarVac on 2008-06-15
On my server, I get 246 Hz, both before and after I recompiled the kernel. I can't figure out what to change; as far as I know, the configuration I do is ignored by fakeroot, or whatever it is that's actually compiling the kernel. I've tried it many different ways, but the kernel apparently still is 250 Hz.

---

