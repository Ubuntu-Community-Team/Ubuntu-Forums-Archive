---
title: "Time to rename the 64 bits release, please"
date: 2007-03-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by HugoPalma on 2007-03-07
I understand the history behind the name AMD64, but isn't it time for the name to change ? I think it causes confusion, and i see lots of posts from people with Intel processors asking if the AMD64 image works for them, just because of the name.

I guess the iso name could be ***-***-64.iso instead of ***-***-AMD64.iso. Any name sugestions would be very welcome.

---

### Post by incubus on 2007-03-07
Hugo,

I agree with your point.  I've seen many many people confused by the AMD64 label as well.  It made sense in the beginning, because we had different 64bit technologies.  Now it seems to be the most popular.

However, this convention is followed in lots of different places.  Not only other distros, but also developers usually make packages using the name AMD64.

One way of remedying this -- and I've proposed this before -- would be to improve the AMD64 description of the download page.  It's too confusing.  Really poor English, in my opinion.  It's no wonder that so many people can't make sense of it.

> 
For computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon). It is not necessary for all (even most) processors made by AMD -- only their 64 bit chips.


Now do you think a non-techie person would be able to make any sense of that?  The last sentence seems to imply that you actually NEED this image if you have an AMD64 processor.

incubus

---

### Post by HugoPalma on 2007-03-07
> **incubus said:**
> However, this convention is followed in lots of different places.  Not only other distros, but also developers usually make packages using the name AMD64.
I agree, but we have to start somewhere. I don't think that renaming the iso file and changing the download page to not call this AMD64 would break anything.

> **incubus said:**
> 
One way of remedying this -- and I've proposed this before -- would be to improve the AMD64 description of the download page.  It's too confusing.  Really poor English, in my opinion.  It's no wonder that so many people can't make sense of it.
I agree that this really needs to be changed. I had noticed that before when i had to read it several times before making any sense of it.

---

### Post by melancholeric on 2007-03-07
"You may use this if you have a 64-bit AMD or intel (list of compatible intels here*) processor. However, the i386 version will work too."

Something like that maybe?

*What are those? Xeon, Core 2, Pentium 4, others?

---

### Post by incubus on 2007-03-07
Hugo, let's wait for more comments, but if this idea gets acceptance, should we file a wishlist entry at launchpad?  We may need to file one for renaming the iso and another for changing the description.

melancholeric, I like that description.  Simple yet complete.  Something in those lines would be enough to make me stop complaining.  : )

It might be a good idea to create a wiki entry for the descriptions. 

incubus

---

### Post by HugoPalma on 2007-03-07
> **incubus said:**
> Hugo, let's wait for more comments, but if this idea gets acceptance, should we file a wishlist entry at launchpad?  We may need to file one for renaming the iso and another for changing the description.
I think a launchpad entry would do the trick.

---

### Post by HugoPalma on 2007-03-07
> **melancholeric said:**
> "You may use this if you have a 64-bit AMD or intel (list of compatible intels here*) processor. However, the i386 version will work too."

Something like that maybe?

*What are those? Xeon, Core 2, Pentium 4, others?

I like that. 

I agree with incubus also, if we go ahead with the change proposal a wiki page should be created where all text proposal should be placed.

---

### Post by BIGtrouble77 on 2007-03-07
It's called amd64 because AMD developed the royalty free standard.  Intel added nothing to the specification.  People always refered to i386 as Intel platform so why should this be any different?  Just so you know, Intel's 64bit instruction set is called emt64, a slightly stripped down version of amd64.

Many people, including myself, are a little bitter that Intel's plan was to destroy competition by forcing the Itanium architecture on consumers (something it was completely ill-suited for).  Intel finally had to adopt the amd64 instruction set because Itanium was a huge failure in almost every respect, not because they wanted to.  I remember reading a post by Linus Tovalds that basically said he was going to label everything as AMD64 simply because he wanted to give credit where credit was due.

IMO, this isn't something the developers should be wasting time on.  It will also fragment Ubuntu from just about every other 64bit distro out there.  You also have the problem of compatibility with Debian code base.

---

### Post by HugoPalma on 2007-03-07
BIGtrouble,

i have to admit that i wasn't aware of the reasoning you just presented. Still, understand that i asked for the name change not because i want to take any credit from anyone but because i don't want to see more Ubuntu users confused when they go to the download page and are led to think that AMD64 distr is for AMD computers only.

So, given all this, i guess what would make everyone happy would be to just change the description on the download page to something more clear that everyone can understand. Everyone agree?

---

### Post by BIGtrouble77 on 2007-03-07
> **HugoPalma said:**
> BIGtrouble,

i have to admit that i wasn't aware of the reasoning you just presented. Still, understand that i asked for the name change not because i want to take any credit from anyone but because i don't want to see more Ubuntu users confused when they go to the download page and are led to think that AMD64 distr is for AMD computers only.

So, given all this, i guess what would make everyone happy would be to just change the description on the download page to something more clear that everyone can understand. Everyone agree?

I agree 100%.  People should not be confused thinking their core (duo) processors will not work with the amd64 distro releases.  I haven't checked the download page, but it should be made very clear if it isn't.

---

### Post by NeilBlanchard on 2007-03-07
Hello,

To quote myself, from another thread:

> AMD designed it, and at first they used a name like AMD64, but I think they realized that if they wanted Intel to adopt it as a standard, they had to change the name; and EMT64 was Intel's renamed clone. x86-64 is best, I think.

I just checked the AMD web site, and they tend to use AMD64 more often, but they do say x86-64, as well.  AMD invented it, and it is a 64bit extension of the x86 architecture.

I do remember having to install things called Pentium... on Athlon systems; knowing that they were compatible.  Often when I recommended an Athlon system to someone, they had to be reassured that it would fully compatible with all their programs.  So, maybe what is good for the goose, is also good for the gander?

---

### Post by incubus on 2007-03-07
Alright, guys, check this out:

[https://wiki.ubuntu.com/UsabilityTesting/DownloadDescriptions](https://wiki.ubuntu.com/UsabilityTesting/DownloadDescriptions)

Please, feel free to edit there and comment here.  I have exams, so I won't be able to help much till Friday.

incubus

---

### Post by incubus on 2007-03-07
PS: Interesting, if you go to AMD64 on wikipedia you're redirected to x86_64.  It's probably good that we all read that page, by the way.

[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

---

### Post by incubus on 2007-03-07
Launchpad entry: [https://launchpad.net/ubuntu/+bug/90552](https://launchpad.net/ubuntu/+bug/90552)

Remember the developers are more active there than here.

Alright, now I have to study.

incubus

PS: If you guys feel we should also change the file names, don't hesitate to file another bug report there and change the wiki page accordingly.

---

### Post by Tanker Bob on 2007-03-08
I agree with changing the name to x86-64 or something similar.  This generic-type designation presents a clearer idea of what is supported by the distribution.  

I read the Wikipedia article, but most folks don't care about the politics of the names.  If people new to Linux or Ubuntu don't see that their hardware is supported, they will go elsewhere to distributions that are clearer on what they support.  

If you want to diss intel, then just don't buy from or recommend them.  Please don't use Linux distributions to make a political point.

---

### Post by Tanker Bob on 2007-03-08
> **incubus said:**
> Alright, guys, check this out:

[https://wiki.ubuntu.com/UsabilityTesting/DownloadDescriptions](https://wiki.ubuntu.com/UsabilityTesting/DownloadDescriptions)

Please, feel free to edit there and comment here.  I have exams, so I won't be able to help much till Friday.

incubus

Nice, simple, and clear.  As a relatively new user, I like what you have suggested there.

---

### Post by incubus on 2007-03-08
Tanker,

Thanks for the feedback.  I absolutely agree with you.  I myself don't care much about the name.  The big issue is if it is feasible at all to change the name at this point, though.  Too many things are interconnected to what we have now, including Debian as somebody pointed out before.

The descriptions, on the other hand, are completely independent of packages.  : )

Keep an eye open on the wiki page.  English is not my first language, so there are mistakes there for sure.

incubus

---

### Post by Tanker Bob on 2007-03-08
incubus,

Your English looks great there.  I'm not very knowlegable about the file naming of the different distributions.  Fixing the description will go a long way towards ending the confusion about which iso works for what CPU.  Thank you for tackling this issue.

---

### Post by NickK1066 on 2007-03-09
Dare I say that "x86" is in reference to Intel's 86,286,386,...,686 instruction set too :) :p

I tend to use x86-64 rather than amd64 but pretty much exclusively use AMD CPUs at home and work.

---

### Post by John.Michael.Kane on 2007-03-09
This thread has the needed info for those with intel hardware,and it should help.

[**Please Read First Advantages and Disadvantages of 64bit.**]("http://www.ubuntuforums.org/showthread.php?t=368607")

---

### Post by HugoPalma on 2007-03-09
> **SD-Plissken said:**
> This thread has the needed info for those with intel hardware,and it should help.

[**Please Read First Advantages and Disadvantages of 64bit.**]("http://www.ubuntuforums.org/showthread.php?t=368607")

I'm sure it does, but why should a user have to come search the forums just to download the correct iso ?  I thought it was Ubuntu goal to make it as easy as possible for everyone, it doesn't strike me as "easy" having to browse forums just to find out which file i have to download.

---

### Post by John.Michael.Kane on 2007-03-09
The info is there you can use it or ignore it. The choice is yours,and the endusers.

---

### Post by HugoPalma on 2007-03-09
> **SD-Plissken said:**
> The info is there you can use it or ignore it. The choice is yours,and the endusers.

Of course, but i understood from you post that you were saying that that post would be enough and so no change in either name or download page would be required. Sorry if i missunderstood you.

---

### Post by John.Michael.Kane on 2007-03-09
I was not inferring that what you suggested was not valid,however. until such time as the download page is changed/updated. The end user has another avenue to find the info they need.

---

### Post by HugoPalma on 2007-03-09
> **SD-Plissken said:**
> until such time as the download page is changed/updated. The end user has another avenue to find the info they need.

agreed 100%

---

### Post by incubus on 2007-03-09
Hey guys,

Since I'm very impatient, I sent an email to Matthew  Nuzum, whose work is related to the download page.  I will keep you updated as soon as I get his reply (and permission to reproduce what he says).

incubus

---

### Post by FUbuf on 2007-10-24
> **HugoPalma said:**
> I'm sure it does, but why should a user have to come search the forums just to download the correct iso ?  I thought it was Ubuntu goal to make it as easy as possible for everyone, it doesn't strike me as "easy" having to browse forums just to find out which file i have to download.

Laugh! Guess twice why I'm just right now browsing this thread... Yes. Reason is that I got Quad Core Intel, and I were very unsure if AMD64 version would run with this.

So I totally agree with you.

---

