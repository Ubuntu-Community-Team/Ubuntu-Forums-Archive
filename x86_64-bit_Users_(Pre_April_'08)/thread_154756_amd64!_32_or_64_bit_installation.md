---
title: "amd64! 32 or 64 bit installation?"
date: 2006-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by crazedcougar on 2006-04-03
Hi,

I am thinking from switching from 32 bit gentoo to either 64 or 32 bit ubuntu.  Here are my specs, in brief:

> athlon amd64 3000+
ati radeon 9600 SE
nec dvd burner with dual layer capabilities
epson perfection 1240U scanner
crt monitor
logitech 10 button mouse (mx510)

And heres what I hope to do:
> Cedega
3d acceleration
Wine (optional but preferable)
Flash
wmv, rm

What do you guys think?  I currently have all of those working fine with gentoo, but it is becoming a bit much to maintain.  Will all of those work out-of-the-box with 64 bit ubuntu? 32 bit? If not, how much hassle is involved achiving eternal happiness?

Thanks for input!
--crazedcougar

---

### Post by johnnymac on 2006-04-03
All of that should work fine...except the wine thing.  Gentoo does a bit better at "automatically" working in 32-bit environment for you; whereas, ubuntu will require a 32-bit chroot environment for wine.  But...all you other goodies should work with minimal hassle.  

I myself came over from Gentoo because of the BS that's involved with maintaining a Gentoo installation as a workstation - great for servers but crappy for a working unit.

---

### Post by skylark on 2006-04-04
Maybe I'm mistaken but Macromedia flash player plugin doesn't work under 64 bit either. I've had to set up firefox and flash in my 32 bit chroot as well as wine.

Edit: 
Sorry, looks like I've been living in the dark ages again. According to [https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava) it is possible to install flash without a 32-bit chroot.

---

### Post by johnnymac on 2006-04-04
No...your right there....but I've put a 32-bit firefox on my system....there's a good how-to somewhere here on the forums regarding setting up AMD64 system, firefox, and flash

---

### Post by rplantz on 2006-04-04
[QUOTE=johnnymac]No...your right there....but I've put a 32-bit firefox on my system....there's a good how-to somewhere here on the forums regarding setting up AMD64 system, firefox, and flash[/QUOTE]

And when I did that on my 64-bit installation yelp broke. I suspect there's a way to fix this, but I gave up. I use the static 32-bit opera for flash, and I kept the default 64-bit firefox for yelp, etc.

I'm running 64-bit because I am learning the 64-bit instruction set (assembly language) and I like playing with things. But I'm retired and don't have to meet deadlines and stuff like that. :)

If my primary goal was to be productive, I would do a 32-bit installation. You probably lost any time advantage of the 64-bit install by simply reading this thread.  :)

---

### Post by johnnymac on 2006-04-04
Good-on-ya-there....

......the 32-bit firefox is so I can monkey and play those annoying flash games during coffee breaks :) and breaks between code-slinging

---

### Post by crazedcougar on 2006-04-05
So what i'm seeing here is that firefox only works in 64 if its built in 32 bits?  If so will it run flash?  How about direct rendering?  Having put alot of effort into getting it working on gentoo, will it work by default with ubuntu?  Yes, i am deciding which dvd to download, and i don't wast to get both for my direct rendering....  So that means 32 bit sounds the way to go, there being more disadvantages than advantages for 64 bit.  On the other hand, how much speedup does 64 bit get on cedega? the gimp/script fu? movie editing? booting?

Thanks!

---

### Post by spartan777 on 2006-04-06
by merely installing gentoo, you can demonstrate that you are more proficient at linux than me, but from what i can tell, unless you have a load of ram- 1.5-2+ gigs of ram- 64 bit isn't really worth the speed increase, and i doubt cedega would be much faster either. 

just listen to rplantz;

[QUOTE=rplantz] ...If my primary goal was to be productive, I would do a 32-bit installation. You probably lost any time advantage of the 64-bit install by simply reading this thread.  :)[/QUOTE]


so really, 64 bit is for those with lots of ram, or who want to be on the cutting edge. i can't wait until the transition to 64 bit is (for the most part) complete. there's too much confusion in between 32 and 64 bit.

---

### Post by henriquemaia on 2006-04-06
[QUOTE=spartan777]by merely installing gentoo, you can demonstrate that you are more proficient at linux than me, but from what i can tell, unless you have a load of ram- 1.5-2+ gigs of ram- 64 bit isn't really worth the speed increase, and i doubt cedega would be much faster either. 

just listen to rplantz;




so really, 64 bit is for those with lots of ram, or who want to be on the cutting edge. i can't wait until the transition to 64 bit is (for the most part) complete. there's too much confusion in between 32 and 64 bit.[/QUOTE]

But why so much ram? Any particular reason? Just to understand a bit more. I'm in between an 32 or 64 instalation also.

---

### Post by crazedcougar on 2006-04-06
I thought it only made a difference if it was over 4gb.... Ah well, ill start downloading 32bit dvd tonight, thanks for the help!

---

### Post by spartan777 on 2006-04-18
the limit of ram is related to the bits the operating system runs. its similar to house addressing. if a town uses 3 digits for addressing, like 321 main street, there could be 999 addresses, and then they'd either reuse numbers, or expand to 4 digits. this situation is similar to memory addressing in pc's. with 32 bits, you can only address so much memory. i think the cut-off is somewhere between 3-4 gigs. so if you have 3+ gigs of ram, or manipulate very large files often, there is not much of an advantage.

---

### Post by Burke on 2006-04-19
If I have:

AMD Mobile Athlon™ Processor 4000+ (2.6GHz)
1024MB DDR (2 x 512MB)
([http://www.gateway.com/home/products/ret/ret_mx7525.shtml](http://www.gateway.com/home/products/ret/ret_mx7525.shtml))

should I install dapper32 or dapper64?

I'm going to university for computer engineering this september.

Thanks!

---

### Post by hajk on 2006-04-20
Student eh? Go for the 64-bit, you'll impress your fellow students (and teachers) with it. :wink: 

I paged through the packages to be included in upcoming Dapper AMD64, didn't see any obvious omissions in the computer science field -- gcc, clisp, g77, haskell/hugs, teTeX... all there.

Should there be the odd package that is only available as 32-bit, then that will also run under 64-bit kernel, as long as it does not use shared 64-bit system libraries. That's why the 32-bit static-library version of Opera will just run in 64-bit system (without having to chroot), since it was compiled with statically linked 32-bit libraries. So, you can use Flash with 32-bit Opera.

But even chrooting should be no problem for a CS student, right?

---

### Post by Burke on 2006-04-20
[QUOTE=hajk]But even chrooting should be no problem for a CS student, right?[/QUOTE]

Heh, I suppose not. Thanks very much, I'll install the 64-bit version.

---

### Post by spartan777 on 2006-04-24
[QUOTE=Burke]If I have:

AMD Mobile Athlon™ Processor 4000+ (2.6GHz)
1024MB DDR (2 x 512MB)
([http://www.gateway.com/home/products/ret/ret_mx7525.shtml](http://www.gateway.com/home/products/ret/ret_mx7525.shtml))

should I install dapper32 or dapper64?

I'm going to university for computer engineering this september.

Thanks![/QUOTE]


if you aren't much of a pro with linux don't do 64-bit. chrooting around... meh. not for beginners. its just better to go 32-bit. you won't really experience any real noticeable difference in speed, and i'm sure your engineering buddies won't really care whether your linux install is 32 or 64 bit. maybe if they were comp science majors, but not engineers. sorry hajk.

---

### Post by Burke on 2006-04-26
[QUOTE=spartan777]if you aren't much of a pro with linux don't do 64-bit. chrooting around... meh. not for beginners. its just better to go 32-bit. you won't really experience any real noticeable difference in speed, and i'm sure your engineering buddies won't really care whether your linux install is 32 or 64 bit. maybe if they were comp science majors, but not engineers. sorry hajk.[/QUOTE]

Well, I wouldn't exactly call myself a beginner. I think I'll give 64 a whirl and if it's too much of a pain in the posterior, I'll dump it for 32. As for your last comment, I agree, I doubt anyone other than myself will care very much.

---

