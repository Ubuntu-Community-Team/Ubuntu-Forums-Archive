---
title: "[SOLVED] Flash for AMD64?"
date: 2007-02-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by defenestratos on 2007-02-09
Will there ever be flash for AMD 64 so I can dig the vids on Utube etc? I'm hanging out.

---

### Post by John Jason Jordan on 2007-02-09
> **defenestratos said:**
> Will there ever be flash for AMD 64 so I can dig the vids on Utube etc? I'm hanging out.
I have Flash working with 64-bit Firefox 2.0 under Ubuntu Edgy amd64. It's a bit of work to get it working. The instructions are here:

[http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727)

---

### Post by Ravanous on 2007-02-09
From what I read on this [Adobe Blog]("http://blogs.adobe.com/penguin.swf/2006/10/whats_so_difficult_64bit_editi.html"), it's kinda like  Duke Nukem Forever - It'll be ready whenever it's ready :lol:

In the meantime, I got mine by following the steps in [this post](http://ubuntuforums.org/showpost.php?p=2072904&postcount=30). (It's almost the same as alternative 2 in the post above mine)

---

### Post by bigd0gg on 2007-02-10
I used Automatix2, it did everything for me,  Everything works but it's a 32bit version of Firefox.  This method is really easy though.

---

### Post by tomdkat on 2007-02-10
> **Ravanous said:**
> From what I read on this [Adobe Blog]("http://blogs.adobe.com/penguin.swf/2006/10/whats_so_difficult_64bit_editi.html"), it's kinda like  Duke Nukem Forever - It'll be ready whenever it's ready :lol:
  And we can't forget about [this](http://www.mozilla.com/en-US/press/mozilla-2006-11-07.html).  :)

Peace...

---

### Post by WalmartSniperLX on 2007-02-10
woahh I dont get the flash problems, I just downloaded flash 9 and copy/pasted libflash.so into my browser's folders (/usr/lib/opera/plugins and /usr/lib/firefox/plugins) Worked flawlessly, well as far as flash works flawlessly :P

---

### Post by flammenwurfer on 2007-02-10
Are you sure your browsers aren't 32bit?   because I did the same thing at first and it didn't work.  Then I had to use nspluginwrapper.

---

### Post by Ravanous on 2007-02-11
> **flammenwurfer said:**
> Are you sure your browsers aren't 32bit?   because I did the same thing at first and it didn't work.  Then I had to use nspluginwrapper.

I didn't try the copy method that WalmartSniperLX mentioned, but the method I have linked to in my earlier post got it working on my 64 bit version of firefox (using nsplugginwrapper of course).

---

### Post by defenestratos on 2007-02-11
> **WalmartSniperLX said:**
> woahh I dont get the flash problems, I just downloaded flash 9 and copy/pasted libflash.so into my browser's folders (/usr/lib/opera/plugins and /usr/lib/firefox/plugins) Worked flawlessly, well as far as flash works flawlessly :P

How do I get my permissions to let me write to the /usr/lib/firefox/plugins directory. My machine says 'You do not have permissions to write to this folder.'

---

### Post by Kilz on 2007-02-11
> **defenestratos said:**
> How do I get my permissions to let me write to the /usr/lib/firefox/plugins directory. My machine says 'You do not have permissions to write to this folder.'

```
gksudo nautilus
``` will open up nautilus with root permissions. But copying in a 32bit flash plugin, and there is no 64bit flash plugin, will not work with a 64bit browser. 32bit plugins are incompatible with the 64bit browser.
The person who posted that either runs the 32bit version, or has a 32bit browser installed somehow.

---

### Post by WalmartSniperLX on 2007-02-11
> **Kilz said:**
> ```
gksudo nautilus
``` will open up nautilus with root permissions. But copying in a 32bit flash plugin, and there is no 64bit flash plugin, will not work with a 64bit browser. 32bit plugins are incompatible with the 64bit browser.
The person who posted that either runs the 32bit version, or has a 32bit browser installed somehow.

Yes that is correct I was using Firefox 2, the 32-bit download from the website. Im running dapper so I installed firefox 2.0 since dapper has an older version. Sorry for not clarifying. I wouldnt want many people reading this being confused because this method wont work for them :)

---

### Post by WalmartSniperLX on 2007-02-11
> **flammenwurfer said:**
> Are you sure your browsers aren't 32bit?   because I did the same thing at first and it didn't work.  Then I had to use nspluginwrapper.

yeah theyre 32bit browsers :S sorry for misleading

---

### Post by WalmartSniperLX on 2007-02-11
Just wondering but what is the advantage of a 64bit browser over a 32bit browser?

---

### Post by John Jason Jordan on 2007-02-11
> **WalmartSniperLX said:**
> Just wondering but what is the advantage of a 64bit browser over a 32bit browser?
It makes you cool. :)

---

### Post by Kilz on 2007-02-12
> **WalmartSniperLX said:**
> Just wondering but what is the advantage of a 64bit browser over a 32bit browser?

There is little to none, or none a human can notice. Its 32bit code compiled to run on a 64bit system. It is not a true 64bit application written for 64bit to take advantage of 64bit. The disadvantages of no plugins are greater. IMHO those that are running nspluginwrapper are not getting much improvement either. Because there is an interface between the 32bit plugin and the 64bit browser.

---

### Post by defenestratos on 2007-02-25
It did work actually and I can now watch my movies in Youtube.
Thanks everyone

---

### Post by defenestratos on 2007-02-26
its going. Thanks everyone!

---

### Post by taco man2 on 2008-04-29
> **Kilz said:**
> ```
gksudo nautilus
``` will open up nautilus with root permissions. But copying in a 32bit flash plugin, and there is no 64bit flash plugin, will not work with a 64bit browser. 32bit plugins are incompatible with the 64bit browser.
The person who posted that either runs the 32bit version, or has a 32bit browser installed somehow.

THANKS A MILLION TIMES! 
I have been searching for weeks on how to make the flash player work and you just saved a hell lot of time. Dude you rock :popcorn:

---

