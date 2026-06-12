---
title: "Ubuntu Dapper 64-bit problems; can't update to Fiesty!"
date: 2007-08-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sedivy 94 on 2007-08-13
**[SIZE="5"]This may be a possible repeat; so please retain from flaming![/SIZE]**


I tried installing Linux Dapper Drake last week, and it was a success. I chose the 64-bit version, thinking it would be significantly faster. But immediatly I ran into problems. Programs weren't working, wine didn't have 64-bit support for Dapper, and even Adobe Flash didn't work! 

So here I am, pulling my hair out. I've searched for "Update Dapper to Fiesty" on Google and found very little.  So what I need to do now is update DApper Drake 64-bit to Fiesty Fawn (64-bit of course). I DID find one tutorial to update Dapper, but I couldn't even access and modify my sources.list

I am a noob. So now that I've admitted it, don't give me any crap.  I'm very unfamilliar with the terminal and Linux's filesystem...  Help would be desired.

---

### Post by Kilz on 2007-08-13
> **Sedivy 94 said:**
> **[SIZE="5"]This may be a possible repeat; so please retain from flaming![/SIZE]**


I tried installing Linux Dapper Drake last week, and it was a success. I chose the 64-bit version, thinking it would be significantly faster. But immediatly I ran into problems. Programs weren't working, wine didn't have 64-bit support for Dapper, and even Adobe Flash didn't work! 

So here I am, pulling my hair out. I've searched for "Update Dapper to Fiesty" on Google and found very little.  So what I need to do now is update DApper Drake 64-bit to Fiesty Fawn (64-bit of course). I DID find one tutorial to update Dapper, but I couldn't even access and modify my sources.list

I am a noob. So now that I've admitted it, don't give me any crap.  I'm very unfamilliar with the terminal and Linux's filesystem...  Help would be desired.

Wine and Flash still require setup on Fiesty, you will not avoid it by upgrading. You will have to upgrade to Edgy, then to Feisty if you want Feisty. 
But the upgrade is not needed. In fact, Dapper has a longer lifespan ahead of it (2009) than Fiesty (2008 ) because Dapper is a long term release. The next long term release will be the one after Gutsy and may have a way to upgrade from Dapper to it.

[Take a look here for how to install Wine.]("http://ubuntuforums.org/showthread.php?t=185557")
Look in my signature for ways of running Flash

---

### Post by Sedivy 94 on 2007-08-13
> **Kilz said:**
> Wine and Flash still require setup on Fiesty, you will not avoid it by upgrading. You will have to upgrade to Edgy, then to Feisty if you want Feisty. 
But the upgrade is not needed. In fact, Dapper has a longer lifespan ahead of it (2009) than Fiesty (2008 ) because Dapper is a long term release. The next long term release will be the one after Gutsy and may have a way to upgrade from Dapper to it.

[Take a look here for how to install Wine.]("http://ubuntuforums.org/showthread.php?t=185557")
Look in my signature for ways of running Flash


Thankyou so much for the help! Really, thankyou!

Ok, now I understand a little bit more. But the reason I want to upgrade to Fiesty is because wine has 64-bit support. I have tried to force install the 32-bit version of Wine for Dapper, but I'm not terminal savvy....

Also, how long will it take for the next release to be, well.... released. :)

---

### Post by Kilz on 2007-08-13
> **Sedivy 94 said:**
> Thankyou so much for the help! Really, thankyou!

Ok, now I understand a little bit more. But the reason I want to upgrade to Fiesty is because wine has 64-bit support. I have tried to force install the 32-bit version of Wine for Dapper, but I'm not terminal savvy....

Also, how long will it take for the next release to be, well.... released. :)

Gutsy still hasnt been released, and it will be 6 months after it is. But you can update now, in stages. But you cant go from Dapper to Feisty.
The wine howto is a copy and paste howto. Its just a few lines. Copy them and paste them right into a terminal. Wine is a 32bit application layer. Even the package for Fiesty is a 32bit application layer. You gain no performance. It has to be to run Windows applications, they are all 32bit.
Also , you do understand that wine isnt an application. There is no menu item for wine. If you type ```
winecfg
``` in a terminal and the config window shows, its installed.

---

