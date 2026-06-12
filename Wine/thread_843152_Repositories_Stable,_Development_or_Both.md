---
title: "Repositories: Stable, Development or Both?"
date: 2008-06-28
forum: Wine
---

### Post by JupiterV2 on 2008-06-28
With 1.0, and 1.1.0 now released, which tree be available in repos or will both be available? If both will be available, what do I need to do to properly choose which tree I would prefer? 

I would, of course, prefer the development version.

---

### Post by Sukarn on 2008-06-28
> **JupiterV2 said:**
> With 1.0, and 1.1.0 now released, which tree be available in repos or will both be available? If both will be available, what do I need to do to properly choose which tree I would prefer? 

I would, of course, prefer the development version.

The Ubuntu repos stick with one version of wine and do not keep updating wine when newer versions are released.

If you want newer version then enable the [winehq](www.winehq.org) repository.

Its up to you which one you want to use, but I'll be willing to bet that the Ubuntu hardy repo won't be updating past wine 1.0.0 except if someone backports a newer version.

---

### Post by JupiterV2 on 2008-06-28
I realize that I made a mistake. I was in fact, speaking of winehq's repos maintained by Scott Ritchie. It seems I didn't need to ask since wine was updated in the repos to 1.1.0 this morning.

---

### Post by cogadh on 2008-06-28
Last I heard, the plan was to update the official Ubuntu repositories (not the WineHQ ones) with only stable releases and that future stable releases will get backported. The development tree is only going to be available through the WineHQ repositories, but most users will want to stay away from the development tree, since we now have a stable release in 1.0.
> **JupiterV2 said:**
> I realize that I made a mistake. I was in fact, speaking of winehq's repos maintained by Scott Ritchie. It seems I didn't need to ask since wine was updated in the repos to 1.1.0 this morning.
Just a FYI - Scott Ritchie maintains both the WineHQ repository and the official Ubuntu repository packages for Wine. The 1.0 package that is in the WineHQ repository is the exact same package that is/will be in the official repository.

---

### Post by Sukarn on 2008-06-28
> **cogadh said:**
> Last I heard, the plan was to update the official Ubuntu repositories (not the WineHQ ones) with only stable releases and that future stable releases will get backported. The development tree is only going to be available through the WineHQ repositories, but most users will want to stay away from the development tree, since we now have a stable release in 1.0.

You do know that wine 1.0 is not really a "stable" release, right? Its (from my perspective) just a more polished version of wine than we've had before it.

There was a post on WineHQ a few months ago that said that they had no plans of branching it to form a stable release tree since wine development was so fast that nobody liked to be left using old versions. I don't know what their current status is on this issue since I haven't actually been reading up on them lately.

---

### Post by Bakon Jarser on 2008-06-28
It is stable.  They did lots of regression testing for 1.0

From winehq

> The Wine team is proud to announce that Wine 1.0 is now available. This is the first stable release of Wine after 15 years of development and beta testing.

---

### Post by Sukarn on 2008-06-28
> **Bakon Jarser said:**
> It is stable.  They did lots of regression testing for 1.0

Like I said, a more polished version of wine.

Its not completely stable. Regression testing is for removing bugs that are introduced from changes in codes (bugs which did not exist in previous versions).

They also released a 1.0 release at this time because wine development was just going on and on (with very good results) but new versions of Windows were (are) also being developed at the same time. wine developers have been doing a very good job of implementing the Windows API but its not perfect, not even close. They said on the main website that they chose to release 1.0 to mark its 15th aniversary (or else my memory has gone haywire) because they had been wanting to make a 1.0 release for a long time but some show stopper bugs in their critical application list kept stopping them.

This release marks some of those applications as working very well, but they post-poned fixing some of the bugs for past-1.0 because they were unable to fix them in time, and I do not blame them.

Please understand that I'm not trying to blame them for anything at all. I appreciate their work a lot, and I've been using wine to run some of my home-brewn software I wrote on Windows ages ago to do some simple stuff and which I've been too lazy to port over to Linux.

I'm just saying that people should not consider this like a top of the shelf release from WineHQ. They're still improving on it. They made this release to mark their achievements so far.

---

### Post by Bakon Jarser on 2008-06-28
Yeah, it's definitely far from complete.  I think they said something like 60% of the windows API is complete.  But I think you and I just have different definitions of "stable".  Wine 1.0 is considered stable because upgrading to it from previous versions shouldn't cause any new problems.  Likewise you should be able to safely upgrade from 1.0 to 1.1 without experiencing any new bugs.  That's why they are calling it a stable release.  They've still got *lots* of existing bugs.  But they've done, and continue to do, a great job.

---

### Post by ajackson on 2008-06-29
> **Sukarn said:**
> You do know that wine 1.0 is not really a "stable" release, right? A lot of people seem to be fooled into thinking that its a stable release, whereas its (from my perspective) just a more polished version of wine than we've had before it.
It is the stable release in the wine context so don't go splitting hairs :)

The idea is the development branch has the normal changes (which is where most regressions come from), once they are happy or the two are getting too far apart the changes get ported across to stable.

So by stable they mean it's not likely to break every fortnight as there is a new testing ground to iron out those issues.

---

### Post by cogadh on 2008-06-29
Stable, in terms of software releases, does not mean the software is complete or bug-free, it just means that it is a version of the software that will not be changing as fequently and is less likely to have new code related bugs (i.e. regressions) than the development tree will have. Stable versions are meant for everyday usage by "regular" users, while the development version is meant for programmers, testers and users who are willing to take risks. It is a complete misunderstanding on the part of everyone if you all expected "stable" to mean a completely functional version of Wine.

---

### Post by Sukarn on 2008-06-29
I'm sorry to have taken this so offtopic.

My apologies.

Now you can all stop posting more explanations in this thread of why I am wrong.

---

### Post by Bakon Jarser on 2008-06-30
> **Sukarn said:**
> I'm sorry to have taken this so offtopic.

My apologies.

Now you can all stop posting more explanations in this thread of why I am wrong.

It wasn't off topic at all.  One thing I like about forums is you can get different answers from different people.  Relying on one answer from one person doesn't quite set the mind at ease.

---

### Post by Robertjm on 2008-07-04
Hi all,

Maybe I'm missing something, but when I use Synaptic it still tells me I have the latest WINE installed on my machine... 0.9.59-0ubuntu5.

It says the same for the development files too.

However, if I add the backports repository 1.01 shows up. How long will it take before v1.0 is actually in the normal repos??

Robert

---

### Post by Sukarn on 2008-07-04
> **Robertjm said:**
> Hi all,

Maybe I'm missing something, but when I use Synaptic it still tells me I have the latest WINE installed on my machine... 0.9.59-0ubuntu5.

It says the same for the development files too.

However, if I add the backports repository 1.01 shows up. How long will it take before v1.0 is actually in the normal repos??

Robert

I don't think it would make it to the main repositories.

wine has typically been the same version in the main ubuntu repositories in the past releases of ubuntu. It has only changed in the backports repository and the winehq repository.

---

### Post by cogadh on 2008-07-04
You are correct, it will not be going into the main repository. If Wine starts doing stable releases along a similar schedule to Ubuntu, then each new version of Ubuntu wil have its own stable version of Wine available in the main repos, otherwise, it will be made available through the backports repository only.

---

