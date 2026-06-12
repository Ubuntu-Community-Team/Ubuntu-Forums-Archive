---
title: "Firefox 3 Beta 64 bits"
date: 2008-03-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by DREMA on 2008-03-12
Its there a way to get the real and oficial Firefox 3 Beta 4 running natively in 64 bits?
Because the one on the mozilla web is 32-bits and the other one on the repositories looks and feel very different. Also, I dont want the Iceweasel one.

So, can I compile it or something?

Thanks.

---

### Post by Kilz on 2008-03-12
> **DREMA said:**
> Its there a way to get the real and oficial Firefox 3 Beta 4 running natively in 64 bits?
Because the one on the mozilla web is 32-bits and the other one on the repositories looks and feel very different. Also, I dont want the Iceweasel one.

So, can I compile it or something?

Thanks.

Compiling Firefox is one of the hardest things to do, I gave up on it. If you want to try [here is a link to the instructions.]("http://developer.mozilla.org/en/docs/Build_Documentation") Since its a beta and only meant to test and not to be used as an everyday application you may just want to use the 32bit version.

---

### Post by Maelgwyn on 2008-03-12
Install Hardy? :P About Firefox tells me it's X86_64... :)

---

### Post by DREMA on 2008-03-13
Damn yeah it looks difficult.

So another way to get the FF 3b4 on 64 bits?

Or how can I make the flash to work with the 32 bit version ?

Thanks a lot!

---

### Post by Kilz on 2008-03-13
> **DREMA said:**
> 
Or how can I make the flash to work with the 32 bit version ?

Thanks a lot!

Copy the libflashplayer.so from /usr/lib/mozilla/plugins to the plugin folder in the 32bit firefox beta.

---

### Post by DREMA on 2008-03-15
I suppose that, but I wasn't sure.

I have to change the paths; /usr/lib/flashplugin-nonfree/libflashplayer.so /path_to_FF3b4/plugins, and that totally did the trick!

Thanks a lot Kilz :)

---

### Post by jespdj on 2008-03-16
> **DREMA said:**
> So another way to get the FF 3b4 on 64 bits?
I am testing the next version of Ubuntu (Hardy Heron, which is coming out on 24 April) on one of my computers. FF3b4 is included there as a native 64-bit executable. Installing Flash is also very easy, if you install flashplugin-nonfree then it automatically installs nspluginwrapper to make the 32-bit Flash plugin work in 64-bit FF3b4.

---

