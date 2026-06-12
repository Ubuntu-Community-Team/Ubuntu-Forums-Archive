---
title: "Are we ready for 64-bit action with Edgy?"
date: 2006-11-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by kcallis on 2006-11-30
Once again, I am going to bite the bullet and try to do a 64-bit install of Edgy? I wonder if all the pain is really worth sticking with the 64-bit version as opposed to just doing another 32-bit install.

Putting optimization aside, what is the real benefit of going through with a 64 as opposed to going 32-bit? I have my torrents for both versions coming down. I am not opposed to blowing away my 6.06 32 bit version and starting from scratch. On the otherhand, I can afford to be down for a week as I try to get the machine squared away.](*,)

---

### Post by John.Michael.Kane on 2006-11-30
It's not really a matter of are we ready. The real question are you ready to use ubuntu 64. 

Theres no need to remove your 32bit ubuntu install the 64bit  and run them dual boot,and test it for yourself. this allows you to make your own judgments as
every end users experience with 64bit ubuntu or any 64bit OS will be different,and problems will be different if they have any.

Also theres many scripts/guides written that allow 64bit end users to add on programs it's just a matter of wanting to do the reading on that subject to get it done.

As to benefits it will come down to what you need the machine to do.

---

### Post by ziggykg on 2006-11-30
I'm running 64 bit Edgy (I'm using AMD 64 x2) which I upgraded to using the Edgy DVD from 64 bit Dapper.

I've got Firefox 2 (with Flash 9 and various other plugins) working.  I'm a Java developer so my Eclipse installation is running sweetly and quite fast coz of my dual core CPU.  I'm waiting to upgrade to the 2.6.18 kernel which has better handling of multi-core CPUs.

Of course I've had to compile some apps from source but I'm quite pleased with my installation at present.

---

### Post by xopher on 2006-11-30
> I'm waiting to upgrade to the 2.6.18 kernel which has better handling of multi-core CPUs.

Why not try the 2.6.19 kernel direct from feisty? It could work without a hitch. ;)

As said by Linus Torvalds, this is a rare "perfect" kernel (2.6.19)

---

### Post by Azakus on 2006-11-30
If you want your browsing to be easy without hassling with 64-bit firefox, try Swiftfox. 32 bit builds of Firefox optimized for your processor.
[http://getswiftfox.com/](http://getswiftfox.com/)

---

### Post by Kilz on 2006-11-30
> **Azakus said:**
> If you want your browsing to be easy without hassling with 64-bit firefox, try Swiftfox. 32 bit builds of Firefox optimized for your processor.
[http://getswiftfox.com/](http://getswiftfox.com/)

I wouldn't recommend anyone who prefers free as in freedom software to install Swiftfox.

---

### Post by Didjit on 2006-12-01
> **xopher said:**
> Why not try the 2.6.19 kernel direct from feisty? It could work without a hitch. ;)

As said by Linus Torvalds, this is a rare "perfect" kernel (2.6.19)

Is there a "clean" way to just install feisty's kernel w/out loading the whole release?

Dijdit

---

### Post by RAOF on 2006-12-01
> **Didjit said:**
> Is there a "clean" way to just install feisty's kernel w/out loading the whole release?

Dijdit

No.

---

### Post by radiobuzzer on 2006-12-02
I am so disappointed with Edgy. AMD 64 x2 here. Nothing works, I have struggled but there is not 5-minute way to have Flash or Java in your browser, I could find some solutions but they needed lots of things and I am too busy to try to fix things that should work by default. Seriously thinking to downgrade to Dapper.

---

### Post by RAOF on 2006-12-02
> **radiobuzzer said:**
> I am so disappointed with Edgy. AMD 64 x2 here. Nothing works, I have struggled but there is not 5-minute way to have Flash or Java in your browser, I could find some solutions but they needed lots of things and I am too busy to try to fix things that should work by default. Seriously thinking to downgrade to Dapper.

Flash and Java aren't **meant** to work by default on 64bit systems.  Adobe hasn't released a Flash player, and Sun haven't released a Java browser plugin.

Although it really shouldn't be that hard to install them.  If you want things to just work, I'd recommend a 32bit Edgy install.

And, of course, everything worked for me just fine :).

---

### Post by kcallis on 2006-12-04
You are quite right about the need and desire to install 64-bit Edgy. One becomes quite spoiled with the ease (or nearly ease) of installing 32-bit Edgy, that sometimes one take for granted the installation of 64-bit Edgy.

I am actually going to hold off on the install until I do a couple of things to my laptop (HP DV8040z), such as increase the RAM (there is go nothing wrong with having 2G in place) and replacing the hard drive (I currently have 80G at 5400rpm, and I am going to replace with 100GBx2 7200rpm drives.

Once that is in place, I will re-install VMware Server and go from there. I guess I really don't have a utilizational need for 64-bit, but I want in in place because after all I have a 64-bit processor! 8) 


> **SD-Plissken said:**
> It's not really a matter of are we ready. The real question are you ready to use ubuntu 64. 

Theres no need to remove your 32bit ubuntu install the 64bit  and run them dual boot,and test it for yourself. this allows you to make your own judgments as
every end users experience with 64bit ubuntu or any 64bit OS will be different,and problems will be different if they have any.

Also theres many scripts/guides written that allow 64bit end users to add on programs it's just a matter of wanting to do the reading on that subject to get it done.

As to benefits it will come down to what you need the machine to do.

---

### Post by Coldbird on 2006-12-04
64bit indeed is a bit of a hassle... but I like taking the best out of my Processor... :-)

It aint 64bit for no reason afterall... And Yes... AMD-X2 over here...

After you figure out how to install some 32bit Modules... You should be good to go on your way to figure out the rest...

Until now I managed about everything I want except Firefox Flash, VMWare and N64 Emulation I think... :P

I got ePSXe running 100% on it... Without using any of the Tutorials around... as they were sort of worthless... cause they didnt really explain what was the Problem and how to solve them on a 64bit System... probably the Reason why I posted my own ePSXe 64 bit setup in the faq section... waiting for a moderator to approve it...

Even WoW Wine works fine... :-)

As long as I got THAT game... Im kind of happy... Yeah! :D
And RBO / RO works fine with it aswell... ¯^¯

Now I only need the few currently non working things to run... then do a OEM Backup... and be happy cause even if i bust something... i can easily revert to a fully working 64bit edgy system... Cheerio! :D

---

### Post by kcallis on 2006-12-04
Well, the initial install went like a breeze, but of course the never ending battle with getting my ATI to work correctly. I really wish I had held out for a 64-bit with the X600 card in place instead of the sucky X200. I have been all through the forums, but no such luck. I really wanted to get the card working right before I started with the loading of software, but such it life.

It anyone has some decent recent experiences with the ATI X200, drop me a note!

---

### Post by ziggykg on 2006-12-05
> **Coldbird said:**
> 

Until now I managed about everything I want except Firefox Flash, VMWare and N64 Emulation I think... :P

I've got VMWare running on my 64bit Ubunutu.  I downloaded the .tar.gz file from vmware site and followed a HOW-TO in the forum.

Quite easy to install as the install script gives good defaults.

---

### Post by kcallis on 2006-12-05
> **ziggykg said:**
> I've got VMWare running on my 64bit Ubunutu.  I downloaded the .tar.gz file from vmware site and followed a HOW-TO in the forum.

Quite easy to install as the install script gives good defaults.
I was searching... Care to tell us the location of that how-to?

---

### Post by kuja on 2006-12-05
[https://help.ubuntu.com/community/VmwareServer](https://help.ubuntu.com/community/VmwareServer)

---

