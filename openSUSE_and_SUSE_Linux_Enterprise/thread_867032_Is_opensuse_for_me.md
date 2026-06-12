---
title: "Is opensuse for me?"
date: 2008-07-22
forum: openSUSE and SUSE Linux Enterprise
---

### Post by 7raTEYdCql on 2008-07-22
I have been using ubuntu for five months now and am loving it. Thinking of changing to something new. Thought of opensuse. I am using an Acer5920, is the distro suited for my laptop. Any suggestions? Any one faced ant problem when making the transition?

---

### Post by dca on 2008-07-22
Their KDE (3.5.x, not 4) is more polished and better looking than Kubuntu.  On the Gnome front asides from YaST (SuSE config control center) there's not much difference.  Certain legal ceodecs are installed by default.
 
In the end, (someone correct me if I'm wrong) the installs & usage on the desktop are similar when it comes to say the top six current distros on distrowatch...

---

### Post by king.pest on 2008-07-22
> **dca said:**
> Their KDE (3.5.x, not 4) is more polished and better looking than Kubuntu.  On the Gnome front asides from YaST (SuSE config control center) there's not much difference.  Certain legal ceodecs are installed by default.

Yes, KDE in openSUSE is more polished, also SUSE has a great support for KDE4. However, I'd say GNOME in SUSE is a bit different than in Ubuntu (I mean configuration tools especially, and the YaST-based tools you've mentioned), and there's less packages available. All in all, it's generally similar in every day's use.

---

### Post by RiceMonster on 2008-07-22
Why don't you try a live cd and find out for yourself?

---

### Post by L815 on 2008-07-22
Maybe, you should try it yourself and find out.

If you want kde3.x.x, you will have to use the install DVD. 
It's what I'm doing right now. I had a few issues with Kde3 on Debian I don't have time to sort out, and OpenSUSE seems to do majority out of the box for you already (Like *butu's).

---

### Post by 7raTEYdCql on 2008-07-22
Just wanted to know does Opensuse have the add/remove programs option just like the one on ubuntu or is it that i have to end up compiling all the packages, something i am not familiar with.

---

### Post by king.pest on 2008-07-23
Yes, openSUSE uses RPM package management system, and there is a YaST module for installing/managing software. More than that: in openSUSE's modified GNOME menu (called SLAB) you can right click on a program's icon and then choose to remove it -- no need to search for it in a package management tool.

---

### Post by ibutho on 2008-07-23
> **king.pest said:**
> Yes, KDE in openSUSE is more polished, also SUSE has a great support for KDE4. However, I'd say GNOME in SUSE is a bit different than in Ubuntu (I mean configuration tools especially, and the YaST-based tools you've mentioned), and there's less packages available. All in all, it's generally similar in every day's use.
I wouldn't say openSUSE has less packages available. If you add the openSUSE Build Service and Community repositories, you end up with more or less the same number of packages as Ubuntu.

---

### Post by king.pest on 2008-07-23
oh ok, I haven't considered that. it's just that I wasn't able to find some particular packages that I need once I've tried openSUSE 11.0 beta, guess I didn't spend enough time searching for a solution:)

---

### Post by Joeb454 on 2008-07-23
> **ibutho said:**
> I wouldn't say openSUSE has less packages available. If you add the openSUSE Build Service and Community repositories, you end up with more or less the same number of packages as Ubuntu.

Ubuntu apparently has around 32,000 packages in the repo's (incl. universe & multiverse).

```
:~$ sudo apt-get install 
Display all 32168 possibilities? (y or n)
```

2 presses of tab will get you that response (you can use tab complete :))

---

### Post by RS3York on 2008-07-24
openSUSE does have a lot of packages once you add the Packman and some openSUSE Build Service (OBS) repos.  But I would not say the OBS is equal to the Ubuntu default repositories.

If you are looking to see if openSUSE has a package you can try on this page, [http://packages.opensuse-community.org/](http://packages.opensuse-community.org/)

The thing with direct package count comparisons is that they assume everything is packaged the same in both distros.  For example, the "restricted-extras" and "build-essential" packages do not have software themselves, but instead pull in a number of other packages.  Yet those 2 metapackages are included in the software count (along with the real software they install).  Similarly, openSUSE used to have metapackages for some software that was broken up in Debian & Ubuntu such as "koffice-wordprocessing" which included KWord + KThesaurus, but there was no way to get just one or the other.  Suse has gotten better at breaking up these packages into smaller pieces, but in these instances the count comparison will show a difference in "amount of software available" that doesn't really exist.

As of last week the Build Service has over 47,000 packages ([http://en.opensuse.org/OpenSUSE_Weekly_News/31](http://en.opensuse.org/OpenSUSE_Weekly_News/31)).  However, if you do a search for "monodevelop" we see that 9 different Build Service repos are carrying a version of that package for openSUSE 11, there are another 6 for openSUSE 10.3.  

I'm a big fan of the openSUSE Build Service because it's better than Ubuntu's '*-backports' system when it comes to delivering new software on an older distro.  However, as long as there are literally thousands of small repos in it with very few large 'master repos'...it is not an ideal solution for the individual user to close the gap in the number of packages available.

---

### Post by RedDwarf on 2008-07-24
> **RS3York said:**
> The thing with direct package count comparisons is that they assume everything is packaged the same in both distros.
Exactly."smart stats" says I have 24644 packages available, but that doesn't means too much.
What I can say is I don't have a single program installed from source, nearly everything I have ever needed is available in Packman, official repos or the Build Service. And I always have the latest versions of games and "user apps" (I don't update system libraries and apps).
The few things that weren't available weren't neither for Debian/Ubuntu ([http://retrospec.sgn.net/users/ignacio/dfli.htm](http://retrospec.sgn.net/users/ignacio/dfli.htm))... and I just packaged them in my personal Build Service repository.

---

