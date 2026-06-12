---
title: "has wine given up on 64bit?"
date: 2007-06-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by jmac19 on 2007-06-19
Any1 got any idea why the 64bit wine builds are 2 versions behind av they given up or what?

---

### Post by capecove on 2007-06-19
I would guess they have not given up. The 64 bit platform is the future of computing unless something wild happens (like we lose all electricity). ;) 

If you can use IRC, check this out...

[http://www.winehq.org/site/irc](http://www.winehq.org/site/irc)

They may be able to help you with a question like that there.

Let us know if you hear anything definitive from them.

---

### Post by Kilz on 2007-06-19
> **jmac19 said:**
> Any1 got any idea why the 64bit wine builds are 2 versions behind av they given up or what?

Is there a new feature in the 9.39 version?

---

### Post by jmac19 on 2007-06-19
> **Kilz said:**
> Is there a new feature in the 9.39 version? not 100% sure wut u mean ?? wouldn't release a version if the wasn't any change or do you mean changes specific to the 64bit version?

---

### Post by incubus on 2007-06-19
> **jmac19 said:**
> not 100% sure wut u mean ?? wouldn't release a version if the wasn't any change or do you mean changes specific to the 64bit version?

I think he meant any specific feature that you need from the new release.

See, it's not very uncommon for this kind of thing to happen.  I think what we should to is email the person/team who is responsible for the amd64 packaging, and ask them to keep the package up-to-date.  And offer them help, if they need it.

incubus

---

### Post by jmac19 on 2007-06-19
> **incubus said:**
> I think he meant any specific feature that you need from the new release.

See, it's not very uncommon for this kind of thing to happen.  I think what we should to is email the person/team who is responsible for the amd64 packaging, and ask them to keep the package up-to-date.  And offer them help, if they need it.

incubuswouldnt have asked if i didnt need the latest version kinda dont matter anyway cus the latest version is in the archive, though not in repo yet guess he/she mite have read this:D

---

### Post by Kilz on 2007-06-20
What exactly in the new release is important to you, other than the fact its a new release? Is there some feature that was added?

---

### Post by incubus on 2007-06-20
jmac19,

I understand.  But I don't recommend getting into so much trouble unless you really need something from the new release (as Kilz says, other than the fact that it is a new release).  As they say, "if it ain't broke..."  Some people just love upgrading for the sake of it, but remember you may be giving up stability and convenience.

Anyway, I'm sending Scott an email to ask if he needs help.

I'll let you guys know.

incubus

---

### Post by scourge on 2007-06-20
> **Kilz said:**
> Is there a new feature in the 9.39 version?

Here's a detailed report: [http://www.winehq.org/?announce=latest](http://www.winehq.org/?announce=latest)
There's a ton of fixes, resulting in improved stability and win32 compatibility. That's a good reason for anyone to upgrade.

---

### Post by Kilz on 2007-06-20
> **scourge said:**
> Here's a detailed report: [http://www.winehq.org/?announce=latest](http://www.winehq.org/?announce=latest)
There's a ton of fixes, resulting in improved stability and win32 compatibility. That's a good reason for anyone to upgrade.

The question I would add to that is, what bugs were you experiencing? 
To many users have what I think of as "newitis". They must have whats new , even if they have no idea why. Often times, especially with Beta software, you are jumping into more problems doing this. Wine is beta software. Its current version is 0.9.39, until it reaches 1.0 its a beta. A subversion may work in your favor, but it may not, you are a beta tester. That it is a sub sub version increese, I just wonder, what exactly is the exact reason for the need? The generic answer of " it has lots of fixes" doesnt answer that question.

---

### Post by jmac19 on 2007-06-20
Kilz's why exactly did you post to this thread?

---

### Post by incubus on 2007-06-20
Guys, take it easy.

Let's stick to the original question: is there a reason why the amd64 package for wine is a little behind compared to i386?  That's a legitimate and harmless question, whether or not you want to upgrade.  I would imagine that the answer is that the maintainer is pretty busy now.

I've sent Scott an email, but no reply yet.  Now that I think about it, I sent it to his ubuntu email, but he may not check it very often.  I'll also forward it to another address.

incubus

---

### Post by Enverex on 2007-06-20
It was a simple case that no-one had gotten around to building one. It's not like there is some sort of conspiaracy.

If anyone is desperate you can ask me to build one. I've had a copy of .39 in my own personal repo for a few days now. Anyways, .39 has been uploaded to the official WineHQ repo earlier today.

---

### Post by Kilz on 2007-06-20
> **jmac19 said:**
> Kilz's why exactly did you post to this thread?

To ask a question (one you never answered). This is a free forum. If you dont like people posting to your thread, dont make one.

---

### Post by Enverex on 2007-06-20
It's generally required for you to post to the AppDB, post bugs or request help to be running the latest version of Wine. But as I said, it was simply because there was no-one to do it. If you're that desperate then you could join in and do it yourself...

---

### Post by jmac19 on 2007-06-20
> **Kilz said:**
> To ask a question (one you never answered). This is a free forum. If you dont like people posting to your thread, dont make one.didnt answer it because it had no relevance to my post, also because i knew from some of your other forum posts where this was heading but nuff said am not gonna let this denigrate to that level

---

### Post by jmac19 on 2007-06-20
@Enverex instead of clogging up the wine appdb with help requests etc would it not be better creating a separate forum?

---

### Post by Kilz on 2007-06-20
> **jmac19 said:**
> didnt answer it because it had no relevance to my post, also because i knew from some of your other forum posts where this was heading but nuff said am not gonna let this denigrate to that level

Why am I not surprised by that answer from someone who has 11 posts? Next time why not save us all some time and not post questions about when wine will be ready on the Ubuntu forum.

---

### Post by scourge on 2007-06-20
> **Kilz said:**
> The question I would add to that is, what bugs were you experiencing? 
To many users have what I think of as "newitis". They must have whats new , even if they have no idea why. Often times, especially with Beta software, you are jumping into more problems doing this. Wine is beta software. Its current version is 0.9.39, until it reaches 1.0 its a beta. A subversion may work in your favor, but it may not, you are a beta tester. That it is a sub sub version increese, I just wonder, what exactly is the exact reason for the need? The generic answer of " it has lots of fixes" doesnt answer that question.

I wouldn't say that I suffer from newitis. I don't need the latest Photoshop when the 5.5 release does everything I want without ever crashing. Wine however is beta software, like you said. That's exactly why I want to keep it up to date. That's what I'm expected to do when I use beta software. Telling people to use old versions of Wine is like telling them to install Tribe 1 of Gutsy Gibbon and disable the update manager until the final version is released.

---

### Post by Kilz on 2007-06-20
> **scourge said:**
> I wouldn't say that I suffer from newitis. I don't need the latest Photoshop when the 5.5 release does everything I want without ever crashing. Wine however is beta software, like you said. That's exactly why I want to keep it up to date. That's what I'm expected to do when I use beta software. Telling people to use old versions of Wine is like telling them to install Tribe 1 of Gutsy Gibbon and disable the update manager until the final version is released.

Negitive, its like saying  watch what you allow to update. Because you may be worse off (example is updating Gutsy with update and finding X11 crashes). Wait for the next major release, like tribe 2.
0.9.39 is a sub sub sub release.

---

### Post by YokoZar on 2007-06-20
So, I saw this thread earlier but didn't reply to it since I had already uploaded 0.9.39 for both arches.  Then someone emailed me today, and it seems like an explanation is needed.

The full story is this: 0.9.38 never got built for amd64 because my amd64 build machine blew up at the same time as real life happened.

0.9.38 was a broken release in many ways with a lot of serious regressions, leading to many users downgrading to 0.9.37 eg to run steam.  So I didn't make any serious effort to build it, and instead waited for 0.9.39.

It took about a day or two longer than I expected to get the amd64 build out the door and uploaded, though.  But the 0.9.39 amd64 version has been in the winehq repositories for at least a day now.


Anyway, real life should be kept to a minimum from now on, as I don't expect to be graduating college on the day of a Wine release again ;)

---

### Post by darknightuk on 2007-06-20
thx for the explanation always fun when ur system goes bang an real life stick's it's nose in;)
keep up the hard work always appreciated

---

### Post by prankst3r on 2007-06-20
> **jmac19 said:**
> Any1 got any idea why the 64bit wine builds are 2 versions behind av they given up or what?

Where are you getting your x64 builds from? I have mine set to pull directly from WineHQ - the x64 version is currently up to date from what I recall...

---

### Post by incubus on 2007-06-20
> **YokoZar said:**
> So, I saw this thread earlier but didn't reply to it since I had already uploaded 0.9.39 for both arches.  Then someone emailed me today, and it seems like an explanation is needed.

The full story is this: 0.9.38 never got built for amd64 because my amd64 build machine blew up at the same time as real life happened.

0.9.38 was a broken release in many ways with a lot of serious regressions, leading to many users downgrading to 0.9.37 eg to run steam.  So I didn't make any serious effort to build it, and instead waited for 0.9.39.

It took about a day or two longer than I expected to get the amd64 build out the door and uploaded, though.  But the 0.9.39 amd64 version has been in the winehq repositories for at least a day now.


Anyway, real life should be kept to a minimum from now on, as I don't expect to be graduating college on the day of a Wine release again ;)

YokoZar, thanks a lot.  We really appreciate your work.  Let us know if you need help with it.

incubus

---

### Post by jusmurph on 2007-06-20
> **YokoZar said:**
> So, I saw this thread earlier but didn't reply to it since I had already uploaded 0.9.39 for both arches.  Then someone emailed me today, and it seems like an explanation is needed.

The full story is this: 0.9.38 never got built for amd64 because my amd64 build machine blew up at the same time as real life happened.

0.9.38 was a broken release in many ways with a lot of serious regressions, leading to many users downgrading to 0.9.37 eg to run steam.  So I didn't make any serious effort to build it, and instead waited for 0.9.39.

It took about a day or two longer than I expected to get the amd64 build out the door and uploaded, though.  But the 0.9.39 amd64 version has been in the winehq repositories for at least a day now.


Anyway, real life should be kept to a minimum from now on, as I don't expect to be graduating college on the day of a Wine release again ;)

Cheers for stopping by mate.

---

