---
title: "Flash and amd64, again"
date: 2006-10-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by lintila on 2006-10-03
Hi All

Sorry to bother with this boring subject, but Flash and amd64 seem to be a real problem.

I have tried the suggestions on nearly every post. I installed Firefox32 and Flash32 and they both both work just like the 64 bit version -- craptastically.

When i open either Firefox32 or 64 and go to a site with Flash on it, the flash movie may or may not play with varying degrees of success, almost always choppy with sound not synced and within a click or two, firefox crashes.

Surely there has to be a way to make this work. Flash is a pretty big thing for distro to just ignore.

Any help with this would be highly apprecieated!

Thanks 
Lintila

---

### Post by RAOF on 2006-10-03
> **lintila said:**
> ...
I have tried the suggestions on nearly every post. I installed Firefox32 and Flash32 and they both both work just like the 64 bit version -- craptastically.

When i open either Firefox32 or 64 and go to a site with Flash on it, the flash movie may or may not play with varying degrees of success, almost always choppy with sound not synced and within a click or two, firefox crashes.

Unless you've installed Gnash, you should get **nothing** on a flash site with a 64bit Firefox.  There just isn't a 64bit flash plugin.

I'd suggest removing Gnash and trying again.  Maybe the gnash plugin is taking priority over the official plugin?  Maybe you've installed nspluginwrapper and it's conflicting?

> **lintila said:**
> 
Surely there has to be a way to make this work. Flash is a pretty big thing for distro to just ignore.
...

It's not that Ubuntu ignores the problem, it's that there's nothing they can reasonably do.  It **can't** work in a 64bit browser, baring experimental 32bit bridge plugins, and they feel the effort required to support a 32bit firefox merely to support proprietry plugins (on a minority architecture) would be better spent elsewhere.

---

### Post by lintila on 2006-10-03
Well, when I seach the Snaptic Package Manager for 'gnash' or 'nspluginwrapper' I find nothing  :( 

I know what you mean about spending time supporting propretary pluggins, I wish the world didnt use them.

lintila

---

### Post by kuja on 2006-10-03
You'd be amazed what a distro would ignore :( 

Flash 7 for Linux in general is craptastic. Fortunately it's not long til Flash 9. 

As per ndiswrapper for running the plugin in a 64-bit browser, I've heard it's pretty unstable. Granted, since I've not heard anything other than that, I never bothered to install it myself. Until I start hearing otherwise I probably won't.

As for using it in a 32-bit firefox, I've not really tried that much. I've been using the flash plugin within Opera (32-bit) myself, and it seems to work okay for me. It's really, really hard to tell why Flash is unstable for you though.

---

### Post by RAOF on 2006-10-03
> **lintila said:**
> Well, when I seach the Snaptic Package Manager for 'gnash' or 'nspluginwrapper' I find nothing  :( 

I know what you mean about spending time supporting propretary pluggins, I wish the world didnt use them.

lintila

If you use the standard, Ubuntu, version of Firefox, you should see a "please install plugin" button when visiting a flash site, like [www.homestarrunner.com](www.homestarrunner.com).  If you see something other than that, you've got some sort of 64bit flash plugin installed.  Check whether you have libflash-mozplugin installed?

---

### Post by x64Jimbo on 2006-10-03
Argh! Use 32bit wine to run windows firefox. Flash works fine that way.

---

