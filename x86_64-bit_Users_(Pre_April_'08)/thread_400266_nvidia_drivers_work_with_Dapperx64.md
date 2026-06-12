---
title: "nvidia drivers work with Dapperx64"
date: 2007-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by nss0000 on 2007-04-03
Gents:

Running Dapperx64 / NV7600gs vidcard:

Many thanks to various posters for instructions on installing NV_glx drivers. Install from Synaptic worked the-1st-time. Very speedy output. And even GoogleEarth has stopped crashing!  The new U_splashscreen is just great. Who woulda thunkit ?

Instead of that cheezy-brown-spray that reminded me of chocolate-covered-peanuts there's the new shot of two-dead-salmon at Pikes Place Market with the words ... VISTA, where do you want to go today? .... ! WooHoo, that  and the narrators ... some guy named "clippy" and another called BOB ! Boy what great rap. 

One thing I don't understand is why those two-guys are talking about downloading drivers? And what's a registration number...??

Anyrate nice job UBUNTU Forums ....:) 


nss
***********

---

### Post by dannyboy79 on 2007-04-03
could you post the output of

sudo lspci -vv

so we can see what controllers are on your motherboard? also, can you post the output from

dmesg | grep NVIDIA

so we can see what driver you're using. did you happen to try the Envy script from tseliot? his real name is alberto milone or something like that. ( [http://albertomilone.com/index.html](http://albertomilone.com/index.html) )
anyway, so others can get this working. please let us know. also, post the output from

uname -r

thanks

---

### Post by nss0000 on 2007-04-03
BigD:

<dmesg | grep NVIDIA >

[   31.374473] nvidia: module license 'NVIDIA' taints kernel.
[   31.378498] NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-8776  Mon Oc t 16 21:53:43 PDT 2006

That's true ... and still a shock-to-me, since I thought NV_drivers would NOT support under DAPPERx64. Not the only shock, as *.mid & *.mp3 are now supported by what MUST(?) be x64_code -- I have not fudged with Automatix. No streaming video yet, however.

Otherwise ... about the fish etcetc ... oops, I missed April_1 .

nss
************

---

