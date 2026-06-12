---
title: "[SOLVED] testing repo for x64"
date: 2008-03-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by keratos on 2008-03-17
hi

what line do i need to add the the sources.conf file in order to access the testing repo for x64

There are lots of packages I would like, that are not listed in synaptic for x64 but are for i32 builds.

too many to mention, just the correct apt sources.conf line would be appreciated.

thanks

---

### Post by Kilz on 2008-03-17
duplicate post.

---

### Post by Kilz on 2008-03-17
> **keratos said:**
> hi

what line do i need to add the the sources.conf file in order to access the testing repo for x64

There are lots of packages I would like, that are not listed in synaptic for x64 but are for i32 builds.

too many to mention, just the correct apt sources.conf line would be appreciated.

thanks

There is no testing repository. There is a development version, but the repositories are for Hardy Heron the next release of Ubuntu currently in Alpha testing. Adding a repo from Hardy to say Gutsy would not work as it would be a upgrade, and not done the correct way. 
Are you 100% sure all those packages are not in the 64bit repos? Why not list a few for curiosities sake. Otherwise its a version upgrade for the os. [Alternately you can search for packages here]("http://packages.ubuntu.com/") to make sure they are not in the repo's. The nice thing is you can also look at the Hardy Heron repos to se if the system upgrade would be worth it.

---

### Post by keratos on 2008-03-17
sure..

well I have kind of got slightly frustrated at repos not offering what I was looking for over recent weeks since installing x64, but today I was looking for:

icecat (aka iceweasel)

---

### Post by soxs on 2008-03-17
Ubuntu made a deal with firefox to be allowed to ship firefox with it. So there is no iceweasel required. But if you still want 100% free browser I suggest you to use swiftweasel, a optimized build of icewaesel (you can get it here: [http://sourceforge.net/project/showfiles.php?group_id=195473](http://sourceforge.net/project/showfiles.php?group_id=195473)). Otherwise you could simply dl the debian bleeding edge version.

---

### Post by keratos on 2008-03-17
> **soxs said:**
> Ubuntu made a deal with firefox to be allowed to ship firefox with it. So there is no iceweasel required. But if you still want 100% free browser I suggest you to use swiftweasel, a optimized build of icewaesel (you can get it here: [http://sourceforge.net/project/showfiles.php?group_id=195473](http://sourceforge.net/project/showfiles.php?group_id=195473)). Otherwise you could simply dl the debian bleeding edge version.

I certainly do not like the "there is no iceweasel required"

Dear Sir, I will be the judge of what is required and I look with disdain on a proposal that firefox has an exclusive right to be in a build.

Er, HELLO, Microsoft/IE.

Hell NO.

Okay, at least you've answered the question and I now know that "open" doesnt always mean OPEN.

:-)

---

### Post by Sukarn on 2008-03-18
> **keratos said:**
> I certainly do not like the "there is no iceweasel required"

Dear Sir, I will be the judge of what is required and I look with disdain on a proposal that firefox has an exclusive right to be in a build.

Er, HELLO, Microsoft/IE.

Hell NO.

Okay, at least you've answered the question and I now know that "open" doesnt always mean OPEN.

:-)

Its as open as open can be.

As far as I know, the only difference between firefox and iceweasel is the name and the logo. That is it.

That difference is not major enough to incorporate iceweasel instead of firefox into the distro and to put off new users with thinking that they will have to use a new browser which they were completely unaware even existed.

A lot of people all over the world know about and use firefox, and not many people use iceweasel in comparison to firefox.

Its just not worth it to replace firefox with iceweasel, and the name and logo are not enough of a reason to add another package for the developers to package and keep up to date.

This is no way seems like Microsoft/IE to me. You do need a browser installed on an OS, and a free one that is known world over and which works well with websites is a good thing for an OS. No need to put off users with an unknown browser.

Believe me, people coming from the MS world might know about firefox, but there's very little chance of them knowing about iceweasel.

---

### Post by keratos on 2008-03-18
Mmm

I have to say I vermently disagree with almost everything you said and I would even go as far as to suggest that you are either misinformed or highly confused.

Although some readacorss and code port may be true, my analysis indicates faster loading times, better performance in iceweasel. Indeed, you will see this app loaded into thin distros such as Zenwalk to name but one. Firefox is incredibly bloated since v1. Where are you getting your results from one wonders?

In terms of O/S shipping with a browser , as you argue , OMG!! How can this not be compared to Windows and IE god only knows. Your remarks although I'm sure you belive them, are totally unacceptable to me and go against everything that open source and choice stands for.

Back to the question,

Does someone have a sensible suggestion on a testing rep.

I am through with the firefox et.al debate and merely wish someone to help and provide the testing repo - if there is one?

Thanks

---

### Post by Sukarn on 2008-03-18
**On-topic:**

You can add the swiftweasel repo, but I am not aware of any repo for iceweasel.

**Off-topic:**

I just want to add, I do not find anything wrong with IE being shipped with Windows.

Would you rather that you were given an OS without any web browser, and left typing commands at a terminal (DOS in this case) trying to get a web-browser just so you could visit facebook or access yahoo mail or something? I know more than enough people who would rather that they were just given the web browser by default. They don't care what they're given as long as alternatives can be installed if they wished to install them.

People who do not know how to install an application, but just want to browse the web would be left stumped if they were given an OS without a browser. If it was something like no IM application installed by default, they could just go on the web and search for or ask how to get one, but in case of a web browser, how do you expect someone new to an OS to find out how to install a web browser when there is no way for them to go on the web? This would be just like that error in Windows that tells people that drivers for their modem were not found and asks whether they want to search for the drivers online. People who just had dial-up connections used to be left wondering how in the world they're supposed to go online to search for the drivers when the modem does not work.

If you do not want any browser installed by default in an OS, go try arch linux. Its stable, its fast, and its so lightweight that you have to install even GNOME, KDE or whatever you wish by the terminal. You can leave out parts of the desktop environment if you so wished (like installing GNOME without gnome-about). Arch does not even recognize my router is connected, and it has to be told about it by modifying configuration files.

Normal users do not want that. That kind of stuff is for power users, and there are more than enough distros for that.

Normal users just want to be given something that works.

---

### Post by rsambuca on 2008-03-18
> **keratos said:**
> Mmm

I have to say I vermently disagree with almost everything you said and I would even go as far as to suggest that you are either misinformed or highly confused.

Although some readacorss and code port may be true, my analysis indicates faster loading times, better performance in iceweasel. Indeed, you will see this app loaded into thin distros such as Zenwalk to name but one. Firefox is incredibly bloated since v1. Where are you getting your results from one wonders?

In terms of O/S shipping with a browser , as you argue , OMG!! How can this not be compared to Windows and IE god only knows. Your remarks although I'm sure you belive them, are totally unacceptable to me and go against everything that open source and choice stands for.

Back to the question,

Does someone have a sensible suggestion on a testing rep.

I am through with the firefox et.al debate and merely wish someone to help and provide the testing repo - if there is one?

Thanks
As Kilz tried to explain earlier, there is  no such thing as a testing repo for Ubuntu.  Because of the short release cycle, the repo's are essentially frozen except for minor updates and bug fixes.  

If you want a "testing repo", in Ubuntu, then you need to use the latest development version, which is currently Hardy.  The Hardy repo's probably won't work very well with the Gutsy kernel and other Gutsy repos.

---

### Post by keratos on 2008-03-19
Okay acknowledge that.

Here in debian land we wait eagerly for stable updates to be carried by the wind evey 1,2 or sometimes 3 yrs.

"Sid" is our saviour!

Thanks for the feedbacl and eduction.

Marking thread solved.

---

### Post by TimelessRogue on 2008-03-19
Solved or not, it appears from your attitude and response  to other forum members that you REALLY want Iceweasel though none can figure why.  So ... you can cruise to the Debian site at  [http://packages.debian.org/etch/amd64/iceweasel/download](http://packages.debian.org/etch/amd64/iceweasel/download)   for the installation package.  Now, a further note:  You will have to uninstall Firefox before you can install Iceweasel since there are conflicts with overwriting some of the Firefox dependencies.  Have at it, dude, and take a step back in time ...

---

### Post by keratos on 2008-03-19
> **TimelessRogue said:**
> Solved or not, it appears from your attitude and response  to other forum members that you REALLY want Iceweasel though none can figure why.  So ... you can cruise to the Debian site at  [http://packages.debian.org/etch/amd64/iceweasel/download](http://packages.debian.org/etch/amd64/iceweasel/download)   for the installation package.  Now, a further note:  You will have to uninstall Firefox before you can install Iceweasel since there are conflicts with overwriting some of the Firefox dependencies.  Have at it, dude, and take a step back in time ...

My attitude!

Look pal, I asked a simple question about iceweasel availability. You then set about telling ME what i wanted and have failed to provide a valid justification for such a steer other than "it is what it is". I dont have a problem with my "attitude" but I have a <BIG> problem with yours.

As I said, thread closed, end of post , dada etc. etc.

Thank you for your feedback and good luck in in your life

---

### Post by LaRoza on 2008-03-19
[http://www.stylesen.org/iceweasel_2_0_deb_file_available_for_ubuntu_all_versions](http://www.stylesen.org/iceweasel_2_0_deb_file_available_for_ubuntu_all_versions)

I found this for Ubuntu.

Keep it civil people, the UF CoC applies everwhere.

---

### Post by st0nedpenguin on 2008-03-19
> **keratos said:**
> In terms of O/S shipping with a browser , as you argue , OMG!! How can this not be compared to Windows and IE god only knows. Your remarks although I'm sure you belive them, are totally unacceptable to me and go against everything that open source and choice stands for.

The quite large difference between the Ubuntu/Firefox and Windows/IE situation is that with Ubuntu/Firefox it's simply a software choice, Firefox isn't tied into the core of the OS from the get go, if you don't like/want it you can simply uninstall it and do whatever the hell you want whereas removing IE from a Windows install is a much more complicated and potentially disastrous undertaking.

You can't really compare the two directly.

---

