---
title: "Why is Gutsy being left behind?"
date: 2008-05-10
forum: Wine
---

### Post by cogadh on 2008-05-10
I understand that Hardy is the latest and greatest and that you (the Ubuntu devs and Canonical) would prefer that everyone upgrade to it, but some of us either can't or don't want to. Those of us who are in that situation are stuck with the last official Wine package in the Gutsy repositories (0.9.59). In the past, when a new version of Ubuntu was released, there was always a significant amount of overlap in the packages produced for each version (Dapper, Edgy, Feisty and Gutsy all had packages produced through 0.9.59), yet since the release of Hardy, this has stopped. With the release of the first 1.0 RC for Wine, Gutsy users are now left even further behind in this respect. _Why_? 

BTW - I know I could compile newer versions of Wine for myself, but I prefer using the official packages as it makes it easier to troubleshoot problems I might have (or might help others with).

---

### Post by dmn_clown on 2008-05-10
If you want an "official" package you could always learn to build your own debs, and then volunteer to build them for the wine project.

---

### Post by ajackson on 2008-05-10
> **cogadh said:**
> Those of us who are in that situation are stuck with the last official Wine package in the Gutsy repositories (0.9.59).
The last official version of wine in the Ubuntu reps for Gutsy was 0.9.46. Don't confuse the WineHQ reps with the Ubuntu ones.

Your complaint is with the person who maintains the Ubuntu reps over at WineHQ, not the Ubuntu developers.

I'm fairly sure he said he'd backport wine 1.0 to Gutsy when it came out but I guess for now he only wants to maintain the Hardy version.

My personal opinion is that the releases that aren't LTS are pretty much redundant when the next one comes along but that is purely a personal opinion.

---

### Post by cogadh on 2008-05-10
The person who maintains the Wine repo _is_ one of the Ubuntu devs (Scott Ritchie, also known as YokoZar here on the forums). In fact, he is the same person who builds the packages for the Ubuntu repos.

---

### Post by swankyfb on 2008-05-10
in my opinion, even though i liked 7.10 because 8.04 is glitchy to me, Gutsy may be left behind because right after the new versions of ubuntu come out, then the older versions become outdated under some peoples eyes and then becomes less and less supported over time.

i may be wrong; i may be lying.

just my opinion.

---

### Post by inportb on 2008-05-10
Don't forget that this is only for Wine. Or have you complaints about other packages too?

---

### Post by cogadh on 2008-05-10
I only "complain" (it was not a complaint, it was a question) about Wine because of the well-established, long history of maintaining updated package verions with previous Ubuntu releases:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

I would understand if Wine package support for some of the older Ubuntu versions was dropped once Hardy came out, but this hasn't really happened since support for Breezy was dropped well after Dapper's release (Breezy actually had parallel packages with Dapper until 0.9.19). Dapper, Edgy and Feisty all maintained parallel packages with Gutsy right up until Hardy was released as well. Dropping support for Edgy would make sense, it has officially reached end-of-life. Dapper still has a year of life left to it (in terms of security and maintenance update support), but I don't think many people are actually still using it, so maybe dropping that would make sense as well. It really doesn't make sense to drop Feisty and Gutsy so unceremoniously right after the release Hardy, especially with how buggy it is (the bugs prevent me from using it at all).

---

### Post by nick09 on 2008-05-10
Well I guess if it is so, you are just gonna have to use hardy to get 1.0rc1.

Also make sure you download the latest updates for Hardy.

---

### Post by cogadh on 2008-05-10
As I already said, the bugs currently in Hardy prevent me from using it. I can install it and it does boot, but the performance is absolutely horrible and the Nvidia drivers don't work correctly at all (and no, it has nothing to do with my hardware being lackluster). Additionally, Pulse Audio is a giant steaming pile IMO, but I can get around that problem by using Kubuntu. 

Gutsy does not have any of these problems, so I shouldn't be forced to upgrade to an inferior Hardy just for the latest Wine package. It wouldn't really matter anyway, I primarily use Wine for gaming, so as long as the video drivers don't work, the latest Wine is pretty much useless to me on Hardy. If I have to compile it myself, I will, but I would like to hear something from the Ubuntu devs explaining why they decided to leave Gutsy users out in the cold like this.

EDIT - Well, I found a partial, but very confusing answer to my question in the Ubuntu community docs:
> Support from Winehq unofficial repository as discontinued for the following Ubuntu distributions:

[INDENT]Ubuntu 7.10 (Gutsy Gibbon) Ubuntu 7.04 (Feisty Fawn) Ubuntu 6.10 (Edgy Eft) Ubuntu 6.06 LTS (Dapper Drake)[/indent]

The repositories is still there for regression testing reasons only at this time could be taken off line at any time. Please do not copy our instructions here. Support on Winehq unofficial repository for Ubuntu Hardy (8.04) is currently in limbo. If Ubuntu keeps on producing working packages upto date packages build for Ubuntu maybe removed completely from the Winehq unofficial repositories.

Slight little note we have found that most problems in a support channel have been caused by Ubuntu Package builder back porting parts. It is 100 percent wished this does not happen. Makes giving support on the software imposable. If Ubuntu keeps on doing this It would be kind if they take all the support issues with the altered versions.

For anyone with no longer supported Ubuntu Distributions building from source will be required at this stage to get support threw winehq support systems. 
Copied verbatim (typos and all) from here: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

From the looks of this, there may not even be Hardy packages on the WineHQ repositories eventually. Now I _really_ want to know what the Ubuntu devs are doing about providing continued Wine package support.

EDIT2 - And now just to add to my frustration, 3 straight attempts at compiling 1.0-rc1 produced Wine that can launch winecfg, but locks up if I try to test the sound. Sound does actually work, as the lockup occurs after the test "bloop" noise. If I try to install anything, the installer launches, then promptly locks up as well, before I can even click on "Next". Nothing like this has happened when I have previously compiled Wine (I used to keep multiple Wine versions on my machine). I really hope this isn't an indication that Gutsy users actually *can't* use the latest Wine.

---

### Post by Mr_Congeniality on 2008-05-11
I've said this in a previous topic but now that Ubuntu 7.10 and lower are being abandoned and wrongfully so, I am compiling and building debian packages for Ubuntu 7.10 and posting them on my website, so do not fear, help is here!

[http://mcstudios.x10hosting.com/wine/index.html](http://mcstudios.x10hosting.com/wine/index.html)

Repository is coming online soon

---

### Post by Mr_Congeniality on 2008-05-11
Anybody wanna try them out and see if it works for them?

---

### Post by cogadh on 2008-05-11
No offense intended, but if given a choice between sticking with an old version from a well known source or trying a new version from an unknown (and therefore untrusted) source, I'll take the old version.

---

