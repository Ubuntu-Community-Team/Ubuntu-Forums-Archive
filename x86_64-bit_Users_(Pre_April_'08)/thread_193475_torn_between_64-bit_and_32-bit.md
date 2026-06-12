---
title: "torn between 64-bit and 32-bit"
date: 2006-06-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by GOwin on 2006-06-10
I'm thinking of making 32-bit dapper my main working environment because problems with drivers or availability (or lack thereof) of some programs.

but i don't want to totally leave 64-bit. Isn't it possible to install both the 32-bit dapper and the 64-bit dapper separately?

since i keep my /home separately, this shouldn't be a problem, right?

---

### Post by Patsoe on 2006-06-10
[QUOTE=GOwin]I'm thinking of making 32-bit dapper my main working environment because problems with drivers or availability (or lack thereof) of some programs.

but i don't want to totally leave 64-bit. Isn't it possible to install both the 32-bit dapper and the 64-bit dapper separately?

since i keep my /home separately, this shouldn't be a problem, right?[/QUOTE]

There's a few little things that may go wrong - for example, I think I had a problem with Firefox saving plugins somewhere in my homedir - if you get the 64bit version to load the 32bit plugins, it exits... took me a while to understand why it crashed every time a visited a flash site :)

Other than that it will be fine. There are other solutions though, like chroot environments etc. It depends on your needs which will suit you...

---

### Post by bonzodog on 2006-06-10
There is very few problems with using 64 bit now, unless you are stuck on getting flash or Wine. Even then, RAOF has very kindly built Gnash (GNU Flash) for us for 64 bit, but it doesn't have a mozilla plugin.

---

### Post by skippy81 on 2006-06-10
I run 64bit and have never encountered any stability issues.  

A 32bit chroot can be used for installing i386 packages, as well as non-64 packages like flash and wine.  I just use my chrooted firefox with java and flash for surfing the net, runs like a dream.   Installing the chrrot is pretty easy, search the forums for "dapper chroot script", some nice guy has made it an even easier process.  

I personally don't have any reasons not to use 64bit now.

---

### Post by Kilz on 2006-06-10
Another thing is that a chroot is no longer absolutely necessary. 64 bit Dapper unlike Breezy will run 32 bit applications without a chroot. There are howto's for installing most common 32 bit applications into dapper 64 without the chroot. Wine, firefox, acrobat, mplayer, cedega etc all function as 32 bit without a chroot. You can still set one up if you want, but it isn't necessary.

---

### Post by JoWilly on 2006-06-11
[quote=bonzodog]There is very few problems with using 64 bit now, unless you are stuck on getting flash or Wine. Even then, RAOF has very kindly built Gnash (GNU Flash) for us for 64 bit, but it doesn't have a mozilla plugin.[/quote] 
The gnash in the raof repo includes the mozilla plugin. Works fine here on firefox64 (only problem: it does not play all flash videos yet).


... also confirming what Klitz says : 32bit apps are easily installable without a chroot.

---

### Post by RAOF on 2006-06-12
[QUOTE=JoWilly]The gnash in the raof repo includes the mozilla plugin. Works fine here on firefox64 (only problem: it does not play all flash videos yet).
...[/QUOTE]
...and it occasionally just plain breaks :(  I really should stop trying the experimental cairo interface ;).  If your firefox starts mysteriously crashing, there's a good chance gnash is the culprit.

Actually, it also lacks the ability to be used for navigation.  I'm eagerly awaiting the time it will pass the homestarrunner test!

---

### Post by JoWilly on 2006-06-12
[quote=RAOF]...and it occasionally just plain breaks :(  I really should stop trying the experimental cairo interface ;).  If your firefox starts mysteriously crashing, there's a good chance gnash is the culprit.

Actually, it also lacks the ability to be used for navigation.  I'm eagerly awaiting the time it will pass the homestarrunner test![/quote] 
Hey RAOF,

I'm taking this opportunity to thank you for providing this nice repo. Yesterday you have again updated xgl/compiz; I'm very pleased with it :)

Best Wishes.

---

### Post by RAOF on 2006-06-12
[QUOTE=JoWilly]Hey RAOF,

I'm taking this opportunity to thank you for providing this nice repo. Yesterday you have again updated xgl/compiz; I'm very pleased with it :)

Best Wishes.[/QUOTE]
Thanks.  Just make sure to remember the mirror:
[http://ubuntu.moshen.de/](http://ubuntu.moshen.de/)
When the raof.dyndns.org repository breaks, or isn't up 'cause I've turned off the computer, that should still work :)

---

