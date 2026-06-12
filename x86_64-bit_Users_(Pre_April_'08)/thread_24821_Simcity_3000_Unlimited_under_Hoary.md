---
title: "Simcity 3000 Unlimited under Hoary"
date: 2005-04-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Equinox on 2005-04-08
(AMD64)
Anyone been able to run this?  I get something like:

sc3u: relocation error: ./sc3u symbol _dl_global-scope, version GLIBC_2.0 not defined in file ld-linux.so.2 with link time reference

Any advise?

Trying the 2.0a patch I get:

Verifying archive integrity...OK
Uncompressing SimCity 3000 Unlimited 2.0a Updatetrap: usage: trap [-lp] [arg signal_spec ...]

Maybe the 64-bit thing is killing it?

---

### Post by jdodson on 2005-04-08
[QUOTE=Equinox](AMD64)
Anyone been able to run this?  I get something like:

sc3u: relocation error: ./sc3u symbol _dl_global-scope, version GLIBC_2.0 not defined in file ld-linux.so.2 with link time reference

Any advise?

Trying the 2.0a patch I get:

Verifying archive integrity...OK
Uncompressing SimCity 3000 Unlimited 2.0a Updatetrap: usage: trap [-lp] [arg signal_spec ...]

Maybe the 64-bit thing is killing it?[/QUOTE]

i recommend running a google search with the error message as the search string.  i have found problems to most all of my questions that way.

---

### Post by Equinox on 2005-04-08
I had no luck with google.. It had hard to find AMD64 and even harder to find Ubuntu stuff.. And it may be specific to one of those two things.

So I thought I'd try here and see if anyone on my architecture/distribution got it to work.

---

### Post by sonny on 2005-04-08
I've the same problem... with my AMD32... can't get it work... also try some google; without answer, though.

Any one here help us...please

The error message from the console is this:

sc3u: relocation error: sc3u: symbol _dl_global_scope, version GLIBC_2.0 not defined in file ld-linux.so.2 with link time reference

---

### Post by skoal on 2005-04-08
[QUOTE=Equinox][...]
Uncompressing SimCity 3000 Unlimited 2.0a Updatetrap: usage: trap [-lp] [arg signal_spec ...][/QUOTE]

Somewhere in another thread about Loki games, I gave some instructions on how to get SC3U working with Ubuntu.

For the specific problem you are having, you can either do one of 2 things for that 'trap' problem:

1. export _POSIX2_VERSION=199209

or

2. use '/bin/bash <patch>' instead of 'sh <patch>'

---

### Post by Rehevkor on 2005-04-22
I installed the 2.0a patch successfully, but now I get Segmentation Fault whenever I try to run the game.

I'm beginning to realize that "linux gaming" is a bit of an oxymoron :roll:

Edit: Nevermind, I just found a [thread](http://ubuntuforums.org/showthread.php?t=21087&page=1&highlight=sim+city+3000+unlimited)  that got it working for me.

It does run, but there's no sound. Do any of you have it working with sound?

---

### Post by blahrus on 2005-04-22
[QUOTE=Rehevkor]I installed the 2.0a patch successfully, but now I get Segmentation Fault whenever I try to run the game.

I'm beginning to realize that "linux gaming" is a bit of an oxymoron :roll:

Edit: Nevermind, I just found a [thread](http://ubuntuforums.org/showthread.php?t=21087&page=1&highlight=sim+city+3000+unlimited)  that got it working for me.

It does run, but there's no sound. Do any of you have it working with sound?[/QUOTE]
 might want to kill esd and let it use alsa or oss emulation

---

### Post by Rehevkor on 2005-04-22
[QUOTE=blahrus]might want to kill esd and let it use alsa or oss emulation[/QUOTE]

Thanks! That worked :)

Is there an easy way to restart esd after I run the game? I lose sound in Gnome after I kill esd, and it just beeps and sits there when I try to restart esd from the terminal.

---

