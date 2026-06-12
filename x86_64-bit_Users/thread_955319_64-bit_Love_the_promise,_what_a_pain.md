---
title: "64-bit: Love the promise, what a pain"
date: 2008-10-22
forum: x86 64-bit Users
---

### Post by figgles on 2008-10-22
Does 8.10 substantially change the dynamic for 64-bit users? I've been running Heron in 64-bit. I love the difference in the base system but it ends there. Extending my platform invariably hits snags. One simple example: google docs. They only support 32-bit. Having to compile so frequently moots the advantage of the base system.

---

### Post by sethvath on 2008-10-22
The advantage of x86_64 is multi cores and >4gb ram support, compiling for your architecture actually boosts your system speed. Shouldnt be an issue with compiling the odd program or two, have you tried gentoo? Come back after you give it a try, you might appreciate having some prepackaged binaries.

---

### Post by figgles on 2008-10-22
> **sethvath said:**
> The advantage of x86_64 is multi cores and >4gb ram support, compiling for your architecture actually boosts your system speed. Shouldnt be an issue with compiling the odd program or two, have you tried gentoo? Come back after you give it a try, you might appreciate having some prepackaged binaries.

Yea, that's what I had thought. There are other matters, like ndiswrapper for my broadcom card. Yes, I can make it work on 64-bit, but there's more overhead than I'd rather deal with. I avoid Gentoo for that very reason (besides, there dev cycle seems to have significantly slowed down). That said, does 8.10 change this dynamic?

I love to "geek about" but I love getting paid even more.

---

### Post by felker2 on 2008-10-22
> **figgles said:**
>  One simple example: google docs. They only support 32-bit. 

Google Docs 32-bit? Please explain; as far as I know and use it, Google Docs is a web app and does not know about the number of bits the client is using.

---

### Post by figgles on 2008-10-22
> **felker2 said:**
> Google Docs 32-bit? Please explain; as far as I know and use it, Google Docs is a web app and does not know about the number of bits the client is using.Details, details... ;) I meant "[Google Gears]("http://gears.google.com/")" the offline component.

---

### Post by felker2 on 2008-10-22
> **figgles said:**
> Details, details... ;) I meant "[Google Gears]("http://gears.google.com/")" the offline component.

Aha. So you're talking about software that's not part of the Ubuntu repositories. 

Based on my experience in both the 32-bit and 64-bit world, I only install software that's part of the Ubuntu repositories, just to avoid any compiling and installing problems. So I would not use the info on [http://www.techrecipes.net/linux/google-gears-in-64-bit-linux.html](http://www.techrecipes.net/linux/google-gears-in-64-bit-linux.html) ;-)

I don't think Ubuntu / Canonical can change a lot about Google's behavior on 64-bit Google Gears. It's probably more effective if 64-bit users like you and me ask Google for 64-bit software.

---

### Post by figgles on 2008-10-22
> **felker2 said:**
> ...It's probably more effective if 64-bit users like you and me ask Google for 64-bit software.Yea, I understand and support the chicken-and-egg dilemma towards platform support, but back to my main point. Unless there's some significant rejiggering of the 64-bit platform on ubuntu (in ways only the FLOSS braniacs think about these things AND that these changes will ripple out in other ways, not necessarily the Google Gears one) then I might keep it. As of today, that's not likely.

Now then, yea, sure, I've read up on compiling GG -- been there, done that. Someone also compiled a 64-bit *.xpi but he hasn't tracked the Gears updates. That goes back to my main point -- keeping a 64-bit system current becomes a death of a thousand cuts. Forget the GG-specific example. There are myriad ways that I hit my head against the 32-bit-support-only-wall. I'm not tasking or blaming Cannonical, Google, Intel, or Haliberton; if anything, kudos to Cannonical for offering the 64-bit version. I'm just observing that running a 64-bit system's pros and cons may weigh too far to the "maintenance overhead" problem in keeping a system up-to-date. I didn't qualify that this is a for-profit computer, not a game or home computer. (Yes, I believe that ubuntu is a great professional OS)

If I come off as being too strong (hopefully not offensively so) its because I'm fishing for a stronger reason to stay 64-bit. I don't do so to flame anyone's choice.

---

### Post by joey-elijah on 2008-10-22
I used 64bit hardy for a while, but, like you, there just became too many insistences of "this" app not working, or "that" app unavailable.

I've tried compiling, but i'm a n0ob, and sometime the sanctimonious attitude of people on forums (not necessarily this one) when you ask for help just pummels the whole deal for me.

I got the "main" apps working - firefox, flash, java etc, but i miss that "layer" you get in Vista 64 that lets you run 32bit apps on a 64 bit machine. Sure, what's the point? Productivity. 

Not everyone comes to Ubuntu etc because of some vegan-like diet for open-source-compile-it-yourself-and-don't-grumble shiz.

Whilst it's not ubuntu's problem that certain applications aren't 64bit, the vicious circle can only be put up with so long before you have to go back to 32bit. 

Maybe there should be a community effort/project to help compile the most wanted 32bit apps to 64bit? If i learned a bit more i'd happily help out on that.

---

### Post by figgles on 2008-10-22
> **joey-elijah said:**
> [a concordant snip] Maybe there should be a community effort/project to help compile the most wanted 32bit apps to 64bit? If i learned a bit more i'd happily help out on that.There once was such a front-end and I liked what it did for 64-bit. Sorry I don't remember the name now. The developer, however, has moved on to other things. I second your idea, FWIW.

---

### Post by cariboo on 2008-10-22
Instead of complaining on the forums about no third party support for 64bit binairies, do like I do and complain to the authors of the software. If enough people do it maybe they will start supporting a modern architecture. Of course we could blame Microsoft for adding the 32bit->64bit layer to keep backwards compatibility, instead of making Adobe, Sun etc  create 64bit apps. :)

Jim

---

### Post by sethvath on 2008-10-22
> **joey-elijah said:**
> 
Maybe there should be a community effort/project to help compile the most wanted 32bit apps to 64bit? If i learned a bit more i'd happily help out on that.

There are many PPA with bleeding edge builds for 64 bit ubuntu but I dont recommended getting from them since most maintainers rarely have the patience to keep it updated for 6 months or more. 

[www.getdeb.net](www.getdeb.net) already has most of the popular software packaged in 32 and 64 bit. If you want to help, email the site admin and offer your assistance. Or if you want the easy way out like me just donate to keep their site up. I've used it plenty of times and its only fair you contribute in whatever way you can for the service you received. 

If 50% of all linux users contributed back to the project instead of waiting for someone else to prepackage a binary so they dont have to compile it themselves, I dare say linux would be a better alternative to OSX or windows by now. 

When I moved to ubuntu from osx, the selling point was never "It just works". Expect some things to not work, those that you break you fix it, and those that cant be fixed, offer what you found out about it to someone else more qualified. 

Lead or be led its an easy choice.

---

### Post by sethvath on 2008-10-22
> **cariboo907 said:**
> Instead of complaining on the forums about no third party support for 64bit binairies, do like I do and complain to the authors of the software. If enough people do it maybe they will start supporting a modern architecture. Of course we could blame Microsoft for adding the 32bit->64bit layer to keep backwards compatibility, instead of making Adobe, Sun etc  create 64bit apps. :)

Jim

Sun and Adobe do not have an obligation to 64 bit users, they have an obligation to their shareholders. As a shareholder I could care less what they do so long as they generate the most profit with minimal overhead and I get my dividends. Maximum profit and minimal overhead means allocating resources to what 80% of customers ask for, not the loud fringe 5% who repeatedly asks for native linux version of photoshop for instance. It makes economical sense to please the 80% first before they try to gain the goodwill of the 5%. 

In the corporate world there is a term for releasing something ahead of its time when the demand is not sufficient to warrant one. Its called a loss.

---

### Post by figgles on 2008-10-23
> **cariboo907 said:**
> Instead of complaining on the forums about no third party support for 64bit binairies, do like I do and complain to the authors of the software. [snip] JimComplaints are tiresome, I agree. I'm looking for a good reason not to leave 64-bit. I'm sorry to say that, from what I'm reading here, my analysis might be correct enough for my decision to go back to 32-bit. 

Now as for your advice; as I've written, been there, done that. Complaining to Google is like complaining to an 800 pound gorilla.  I understand why entities don't support 64-bit and I respect their choice. I know there's a lot of smart people here and I'm merely soliciting feedback on the matter. Yet, maybe there's an aspect I missed? Maybe not.

The other fair FLOSS retort is to make my cause my own project. However, I'm better suited for software documentation than for platform advocacy.

---

### Post by kramulous on 2008-10-23
What kind of work are you doing where 64bit Ubuntu poses a problem where 32bit does not?

I'm reasonably new to Linux, 100% usage since start of 2007 and have only used 64 bit in that time.  There was an adjustment period, sure, but that's over.  I've had to modify the workflow for certain types of jobs but that's all.

---

### Post by figgles on 2008-10-23
> **kramulous said:**
> What kind of work are you doing where 64bit Ubuntu poses a problem where 32bit does not?

I'm reasonably new to Linux, 100% usage since start of 2007 and have only used 64 bit in that time.  There was an adjustment period, sure, but that's over.  I've had to modify the workflow for certain types of jobs but that's all.I covered this in my earlier posts. Professionally I am a graphic arts consultant and web developer. I mostly use the command-line, quanta, git, for web dev, OpenOffice for documentation, (I *wish* there was a good PDF editor -- that's for another thread) All of these apps run great in 64-bit. (I haven't timed it but a 64-bit systems *feels* smoother performing than a 32-bit) Firefox oddities, and google gears remains an issue, (honestly gears has brought this to a head, but if it weren't for other issues, I'd deal with it) which I've covered. ndiswrapper and broadcom is another issue that I won't tackle due to time constraints. Again, its not about the litany of little issues, but that, overall, there's always "something new" to mollycoddle as I expand my platform because I'm on 64-bit.

---

### Post by figgles on 2008-11-13
Update: I've been running 8.10 since the second day of its release as a 32-bit OS, and I must say I love it. It "just works." No odd compilation requirement, no "run arounds." I have no doubt that 64-bit makes a lot of sense for certain vertical applications but I can't recommend it for general business usage. 

Thanks to all for the great feedback!

---

