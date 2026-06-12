---
title: "Pidgin 2.5.6 for Hardy"
date: 2009-05-22
forum: x86 64-bit Users
---

### Post by noblerabbit on 2009-05-22
I'm really getting frustrated that so many programs arent updated in Hardy, despite LTS. hardy is the only one i can use with my wireless cards (both of them... neither work in ibex or jaunty)

but nothing seems to be supported, everything from the repos is old.. Im trying to work out VLC upgrading in another thread, now i want pidgin 2.5.6, because i wanna use webcam!

i got 2.5.5 but cant figure out how to get the new, improved version. does anyone have a deb or something that will work in Hardy?

---

### Post by CoreyB. on 2009-05-22
[http://www.getdeb.net/release/4387]("http://www.getdeb.net/release/4387"), assuming you have 64 bit or [http://www.getdeb.net/release/4386]("http://www.getdeb.net/release/4386") if you have 32 bit.  There are four debs that you will need.

EDIT: Uninstall you current pidgin first!  Then install in the following order: pidgin-data, libpurple0, libpurple-bin, pidgin.

---

### Post by eldragon on 2009-05-22
it seems you are not very familiar with how ubuntu releases software..

you will not see new versions for hardy, only security fixes. thats the point of a LTS.

if you still dont like how its done, i suggest you move to a rolling release distro. which is always up to date (or a couple of days behind) with upstream but its more prone to bugs.

---

### Post by noblerabbit on 2009-05-22
> **eldragon said:**
> it seems you are not very familiar with how ubuntu releases software..

you will not see new versions for hardy, only security fixes. thats the point of a LTS.

if you still dont like how its done, i suggest you move to a rolling release distro. which is always up to date (or a couple of days behind) with upstream but its more prone to bugs.

ive tried some different distros, there are so few that work out of the box. jaunty and ibex kind of did but X was a pain to configure and wireless, as mentioned, did not work.

i just wish like, when for example the new pidgin is released for jaunty that it would be released for hardy too.

@Corey, thanks i will give that a go.

---

### Post by noblerabbit on 2009-05-22
Thanks corey, thats done it! :D

Looks like i got a hwile to go yet before i can webcam in pidgin tho, just read this off their site:

```

**April 01, 2009 09:44 PM by [Casey Ho]("http://blog.caseyho.com/search/label/pidgin")**

   Yes, that's right ladies and gentlemen.

PIDGIN NOW HAS VOICE AND VIDEO CHAT SUPPORT!

I doubt much explanation is needed here. Video and voice chat 
has probably been the most requested Pidgin feature over the past five years.

Many thanks to [Maiku]("http://developer.pidgin.im/wiki/Maiku"), our Summer of Code student from 2008 who tirelessly 
spent many hours implementing this. This was a huge undertaking. Maiku has 
told me he will accept compensation in the form of pizzas.

We expect this functionality will be released sometime this month.  Stay tuned.


```which i had misread thinking webcam worked :(

besides that i need to find a driver to make my camera work now...

---

### Post by cmost on 2009-05-25
> i just wish like, when for example the new pidgin is released for jaunty that it would be released for hardy too.

Sorry bud, but it doesn't work that way with Ubuntu and it shouldn't.  LTS implies long-term-support.  It's Ubuntu's spin on Debian Stable!  Updated packages will not flow into that release, only security and bug-fixes.  In fact, updated software rarely flows into ANY released version of Ubuntu.  Once Ubuntu is released, that's it for that version and work begins on the next version.  My advice is to learn how to compile your own Debs so that you can keep your own system up to date with the packages you rely on.  Alternately, you can often find third party repositories that contain newer versions of popular software.  Finally, distributions like Fedora and OpenSUSE often DO provide updated versions of popular software, even after a version is released.  For example, Fedora updated KDE to 4.2.2 for Fedora 10 and reissued ISO images long after Fedora 10 officially hit the mirrors.

Here's where you can download updated Pidgin packages:
[https://launchpad.net/ubuntu/+source/pidgin](https://launchpad.net/ubuntu/+source/pidgin)

Here's a repository for the developer version of Pidgin, which is cutting edge - copy it into your /etc/apt/sources.list file; save; apt-get update && apt-get dist-upgrade.  Note:  You do realize that doing this will essentially defeat the purpose of running Ubuntu LTS.

## Pidgin developer repository
deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) hardy main

---

### Post by noblerabbit on 2009-05-25
> **cmost said:**
> .  Note:  You do realize that doing this will essentially defeat the purpose of running Ubuntu LTS.

yes. i would have the latest version (jaunty) if i could run it, but so far there is no fix for my internet issues (same issues occur in intrepid) so i use hardy out of necessity.

if jaunty worked i would use it. sadly it doesnt and i am not nearly competent enough to try to fix it myself, so until the bug is fixed i have to use hardy. when it does get fixed i will upgrade, but i fear that the next one after jaunty may have wireless issues again, thus i am always reluctant to upgrade when i have a working system.

this is the reason i use ubuntu to begin with, if i were an expert i wouldnt need to use it, i could use something more complex and customisable like slackware (Which i have used but just as a hobby, not as a main OS).

for my own purposes (having a reliable, stable, working OS) ubuntu hardy is the only one that will suit me (save going back to windows..)

---

