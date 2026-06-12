---
title: "64 bit woes..."
date: 2008-06-01
forum: x86 64-bit Users
---

### Post by joey-elijah on 2008-06-01
Hey all. I run Vista 64 bit with no problems at all! [surprisingly!] and i have just installed Ubutnu HARDY 64 bit, having used ubuntu GUTSY 32 bit last time. I also have Ubuntu Gutsy 32 on my little eeepc which runsa  treat.

I was kind of expecting to be able to get the same level of productivity out of Hardy 64 as i got from Vista straight away... but it seems i have a few problems. And although i have a dual core 3.0ghz processor and 4gb ram, the system as a whole doesn't feel as responsive as i thought it would... ubuntu on my eeepc feel a lot smoother.

**Firefox and Flock. **
I would prefer the 32 bit editions, as the deb i got from deb.net [or something] installs but never opens. Firefox 32 is preferred for plug-in's i use. [things like Mozilla Prism, Weave etc] How do i get them? i tried using a 3in1 install thingy from these very forums, but it doesn't install after showing a java agreement form in terminal - of which i can't click "ok" , "y" or "1" to.

**Compiz**
Having installed compiz, in the "appearance" menu i have no option of "custom" regarding the changes i have made to compiz settings... i only have the three default choice. which means any time i need to switch off compiz, i have to manually go back and reset all my preferences. IS this a known issue? 
[B]
Emerald[/B]
Emerald themes do not work. They did last time i logged in... the "window decoration" in compiz is set to /usr/bin/emerald - and thought it worked before, it doesn't work now - no matter how much i click on the themes!

**How can i remove firefox 64 and flock 64? **
package "flock" isn't found, and firefox goes to some java terms and conditions screen that has no option to proceed. Is there anyway to forceably remove them?



i have searched the forums but either found no solution applicable, or the solution applicable doesn't work.

Is there any package/libary that i can install that will let me run 32 bit applications?

I know my wifi won't ever be able to work in Ubuntu - it's a USB SMC EZ connect N dongle, but the SMC website doesn't have any linux drivers listed for it. grr. You'd think companies would want to ensure maximum compatibility... 

Whilst i like having natively 64 applications, it's a shame it's not a hybrid like Vista.

ANy solutions/links would be very much appreciated. I'm not toally a n0ob when it comes to linux - that said i still have to follow a step through for .tar.bz's ..... lol

thanks!

---

### Post by Julius on 2008-06-01
mm
to install skype I think I did
getlibs -i skypewhatever.deb

then
dpkg --force-all -i skypewhatever.deb

it works just fine

---

### Post by joey-elijah on 2008-06-01
okay - thanks i will try that.

Any idea how to get firefox 32 and flock 32 to work? espically with flash etc?

---

### Post by ne3e on 2008-06-01
I have had no issues with the 64 bit version.
I installed 7.04 and recently upgraded to 8.04 Kubuntu.
I upgraded using the installed scripts.  I'm using an AMD 64 X2 and running KDE4, Gnome, blackbox, ICEWM.  I'm also using it as a PDC on my home network and using it as a WINS server.


John

---

### Post by soxs on 2008-06-01
32bit firefox with flash and java: [http://ubuntuforums.org/showthread.php?t=202537&highlight=Kilz+32+firefox](http://ubuntuforums.org/showthread.php?t=202537&highlight=Kilz+32+firefox)
About flock, I must say I never heard about it *g*
Edit: Flock can be found at the same page.

---

### Post by waspbr on 2008-06-01
weird, I run hardy 64 on y hp tx1320us notebook and it works very well, emerald, firefox (aside from the flash crashing but with is also on the 32 bit version) also works well, surprisingly enough flash and java work well, you just need to install them from synaptic [openjdk and flash] provided you add your medibuntu repos.

---

### Post by WeEatVista on 2008-06-01
I know what you mean...I'm running 64 bit also, but I have a solution to one of your problems.

> i tried using a 3in1 install thingy from these very forums, but it doesn't install after showing a java agreement form in terminal - of which i can't click "ok" , "y" or "1" to.


I had this problem, and after hitting literally EVERY key, I figured this out:
Use the arrow keys to scroll down to the bottom, then hit space. When another message pops up, use the arrow keys to highlight YES and hit space again. The installation will finish! (well, it worked for me)

Hope this works,
WeEatVista

P.S. I am a newb too, just installed 8.04 this morning. I am going to stick with it though, just some things take a LONG time to figure out.

---

### Post by joey-elijah on 2008-06-01
hey all thanks for the replies! I'll certainly give things a go in a bit and let you all know.

Should i uninstall emerald etc and reinstall to see if that works? 

and thanks WeEatVista for that tip! I'm gonna jump on and do that asap - mainly to have the satisfaction of getting past that bloody screen! 

anymore tips solutions?

I'm thinking of putting up a clear and concise setp through for new 64 users on my blog - once i get things sorted myself. A lot of people are dubious of 64 bit, but it seems a lot of you get on fine with it.. so I'm gonna stick with it!

---

