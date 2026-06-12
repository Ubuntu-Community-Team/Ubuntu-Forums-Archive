---
title: "64-bit Ubuntu and Core 2 Duo"
date: 2007-03-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tanker Bob on 2007-03-05
I am about to build a new PC around a Core 2 Duo E6700 CPU, MSI P6N Platinum motherboard, and an NVidia GeForce 7950GT video card.  I see that the only 64-bit Ubuntu is for AMD64.  Will that run correctly on an Intel Core 2?  Do the current NVidia 64-bit drivers labeled AMD64 work on the Core 2?  Any gotchas here as far as the CPU/bridge architecture is concerned?  Thanks for any help you can provide.

---

### Post by Kilz on 2007-03-05
> **Tanker Bob said:**
> I am about to build a new PC around a Core 2 Duo E6700 CPU, MSI P6N Platinum motherboard, and an NVidia GeForce 7950GT video card.  I see that the only 64-bit Ubuntu is for AMD64.  Will that run correctly on an Intel Core 2?  Do the current NVidia 64-bit drivers labeled AMD64 work on the Core 2?  Any gotchas here as far as the CPU/bridge architecture is concerned?  Thanks for any help you can provide.

AMD64 is the generic name for the 64bit version. It runs all the amd 64bit chips and the 64bit modern 64bit intel chips like the Core 2 Duo. The reason its named that is because AMD was the one that made the 64bit design popular.
The only known areas to be aware of are that a few (<10) proprietary 32bit applications may need to be installed because there is not a good 64bit version available. An example of this is the flash plugin for Firefox. Nothing to hard, nothing there isnt a howto or setup script avilable to accomplish the task.

---

### Post by mixium on 2007-03-05
> **Tanker Bob said:**
> I am about to build a new PC around a Core 2 Duo E6700 CPU, MSI P6N Platinum motherboard, and an NVidia GeForce 7950GT video card.  I see that the only 64-bit Ubuntu is for AMD64.  Will that run correctly on an Intel Core 2?  Do the current NVidia 64-bit drivers labeled AMD64 work on the Core 2?  Any gotchas here as far as the CPU/bridge architecture is concerned?  Thanks for any help you can provide.

Hi,

I am currently running Ubuntu 6.10 on a Core 2 Duo laptop with 2 GB of ram and an nVidia Geforce Go 7400. It runs extremely well. The only two gotchas were discovered after updating the system. I recomend you installing the proprietary nVidia drivers as per the instructions here: [http://www.ubuntuforums.org/showthread.php?t=263851&highlight=nvidia+beryl+option+2](http://www.ubuntuforums.org/showthread.php?t=263851&highlight=nvidia+beryl+option+2)

My other gotcha was that my headphone jack stopped working after updating the kernel and I'm in my second day of trying to solve this.

Other than those two issues I **HIGHLY** recommend Ubuntu AMD 64 6.10.

As a side note, the testing version of GCC-4.3 will offer the CFLAGS=core2. This should give both you and I optimal performance. However, I have no idea what Ubuntu's plans are. It would be nice of them to offer an x86_64 version but still, this AMD is quite nice!

:)

Michael

---

### Post by juanhunglow on 2007-03-05
> **Tanker Bob said:**
> I am about to build a new PC around a Core 2 Duo E6700 CPU, MSI P6N Platinum motherboard, and an NVidia GeForce 7950GT video card.  I see that the only 64-bit Ubuntu is for AMD64.  Will that run correctly on an Intel Core 2?  Do the current NVidia 64-bit drivers labeled AMD64 work on the Core 2?  Any gotchas here as far as the CPU/bridge architecture is concerned?  Thanks for any help you can provide.

Bob,
I built a core 2 system a few months ago and have been using Edgy 64 (and trying/testing Feisty 64) ever since.  I was also fairly new to Ubuntu in general so things were not always smooth.
With the help of the forums and the ability to install things like Firefox32 using Kilz script it can be kinda easy.  There are some things that requrie tweaking, but it can be fun.  I also must admit to using Automatix for some things.  For someone new it can really make life a lot easier.  I know that some on these forums don't promote Automatix, but to get up and going fast I would recommend you try it.
Be careful of 3rd party repos, but I have had much success using the [**janvitus **]("http://www.janvitus.netsons.org/")repo and the RAOF repo.  Check the janvitus website or search the posts, also look at RAOF's profile for a link to that repo.

EDIT:  I use 'envy' to install nvidia drivers.  Search the forums or look here [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Tanker Bob on 2007-03-05
Many thanks to all for your replies.  You have all been very encouraging and I will definitely give 64-bit a good run.

One last question.  My initial plan is to simply plug my current hard drives into the new box after dropping to the open source NVidia driver in the old box.  After the hardware comes together, I will boot the current hard drive with 32-bit 6.10 to ensure all the hardware works together.  From there, can I install the 64-bit 6.10 over the 32-bit or do I have to install the 64-bit from scratch?  If the former, what's the best way to intall over the 32-bit version?

---

### Post by juanhunglow on 2007-03-06
> **Tanker Bob said:**
> Many thanks to all for your replies.  You have all been very encouraging and I will definitely give 64-bit a good run.

One last question.  My initial plan is to simply plug my current hard drives into the new box after dropping to the open source NVidia driver in the old box.  After the hardware comes together, I will boot the current hard drive with 32-bit 6.10 to ensure all the hardware works together.  From there, can I install the 64-bit 6.10 over the 32-bit or do I have to install the 64-bit from scratch?  If the former, what's the best way to intall over the 32-bit version?

I'm not sure I understand the question but I don't think you can 'upgrade' from 32 to 64 if that is what you mean.  I've always done a clean install of my root and home partitions (I have a separate /documents partition where I keep all my media files so I don't have back them up as often and they won't get accidentally lost if I re-install).  I like the clean install b/c I know there shouldn't be any conflicts to cause me problems.  

Others might be able to tell you more but I would save all your important stuff and do a clean install.

Also, something I do that you might want to think about is keep an install log (just an open office doc file).  From start to the current date I keep track of the changes I've made with links to the forum posts that help.  Makes life a lot easier if you have to reinstall  b/c something broke.

Any more questions, let them fly.

---

### Post by kragen on 2007-03-06
Just a thought - but "because it says AMD - will my core 2 duo work on it" is the first thing I thought of too, and I expect it will be the first thing a lot of people think. Do you think its worth changing the name, or at least the text on the links, to try and prevent confusion? Using the name of the architecture (EM64T) might be an idea...

Just a thought.

---

### Post by mixium on 2007-03-06
> **kragen said:**
> Just a thought - but "because it says AMD - will my core 2 duo work on it" is the first thing I thought of too, and I expect it will be the first thing a lot of people think. Do you think its worth changing the name, or at least the text on the links, to try and prevent confusion? Using the name of the architecture (EM64T) might be an idea...

Just a thought.

I agree with that, but I think x86_64 would be more appropriate since (EM64T) is an Intel designation. x86_64 is the generic architecture designation.

:)

Michael

---

### Post by NeilBlanchard on 2007-03-06
Hello,

I agree with Michael -- AMD designed it, and at first they used a name like AMD_64, but I think they realized that if they wanted Intel to adopt it as a standard, they had to change the name; and EMT64 was Intel's renamed clone.  x86_64 is best, I think.

[/meta discussion]

---

### Post by Tanker Bob on 2007-03-06
> **juanhunglow said:**
> I'm not sure I understand the question but I don't think you can 'upgrade' from 32 to 64 if that is what you mean.  I've always done a clean install of my root and home partitions (I have a separate /documents partition where I keep all my media files so I don't have back them up as often and they won't get accidentally lost if I re-install).  I like the clean install b/c I know there shouldn't be any conflicts to cause me problems.  

Others might be able to tell you more but I would save all your important stuff and do a clean install.

Also, something I do that you might want to think about is keep an install log (just an open office doc file).  From start to the current date I keep track of the changes I've made with links to the forum posts that help.  Makes life a lot easier if you have to reinstall  b/c something broke.

Any more questions, let them fly.
Thank you!  "Upgrading" was indeed what I had in mind.  I'm always looking for an easy way, but I prepared for that eventuality on initial install.  My home directory is another partition like yours, so I don't have to worry about my data.

I like your idea of keeping a log.  I sort of do that now on my website, but only in a general sense.  I hope to catch up my blog on [MobileTechReview](http://www.mobiletechreview.com/ubbthreads/postlist.php?Cat=&Board=tankerbobblog) so that I can keep a running account there to help other folks.

I'll be back when I've built my new system.  I'm sure I'll have at least a few questions, although the HOWTOs on 64-bit look very good.  My thanks to everyone who has taken time to create them.

---

### Post by Tanker Bob on 2007-03-06
FWIW, I'd also vote for a name change of the 64-bit package to x86_64.  When I first looked through the supported architecture list, I didn't think the Core 2 Duo was supported at 64-bits because of the AMD64 designation, hence my initial post here.  I'm sure that I'm not the only one.

---

