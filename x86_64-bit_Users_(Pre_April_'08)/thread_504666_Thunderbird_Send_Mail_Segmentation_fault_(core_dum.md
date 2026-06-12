---
title: "Thunderbird Send Mail Segmentation fault (core dumped)"
date: 2007-07-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Thene on 2007-07-19
(I know there's another post regarding a Segmentation fault (core dumped), unfortunately none of the solutions seemed to apply or work for this problem.)

I've encountered a Segmentation fault (core dumped) when trying to send mail. Other than that, Thunderbird works perfectly. When I try to send an email, Thunderbird simply disappears.

There is an output file in /var/crash/_usr_lib_thunderbird_thunderbird-bin.1000.crash, however I have no idea where to start looking for a clue to what's causing it to disappear.

My email was working fine until Wednesday, I actually didn't notice that the send mail wasn't working because of my Beryl effects.

Since then, I've turned Beryl off, I updated Thunderbird to Thunderbird 2 thinking it might help. I uninstalled SCIM (referring to other Thunderbird Segmentation fault thread).

I reinstalled the updates that appeared on Wednesday (OpenOffice, libmagick9, imagemagick & python-uno).

I also completely removed Thunderbird 2 & reinstalled it. As well as rebuilding the index files & compacting the email folders.

I also removed idefisk which I installed on the same evening, but to no avail.

Other than that, I have absolutely no idea what has caused the problem.

I would really appreciate it if someone could shed some light on this or give me some idea where to look. :confused: Thanks!

(Am running Thunderbird 2 from Iuculano's debian packages v7.04 - but I don't think that's the problem, as I had the problem before I upgraded.)

---

### Post by gbendotti on 2007-07-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/126690](https://bugs.launchpad.net/bugs/126690) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I can't shed much more light on this for you, other than a "me too" which I generally detest; but at least you know you are not alone.

I have a bug report at launchpad (see below)  but things have gotten quiet on that front.

It seems to be related to the 64 bit vs, I have the same issue with a VMWare install of Gutsy and on the host OS of Fiesty, both 64 bit.

All 32 bit OS's I have TB works fine, 1 Ubuntu7.04/XP dual boot Destop; 1 Kubuntu 7.04 /Vista dual boot laptop.

My problems started around the same time as yours.

---

### Post by Thene on 2007-07-28
Thanks for the reply. :)

I've also reported it at Launchpad [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/127679](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/127679). (It seems I don't have permission to access your Lauchpad link.)

It's completely odd. I work a lot late at night, so I was sending an email off before going to bed & I think it happened & I didn't realise because I use HK Suite effect in Beryl.

Anyhow, since trying fix it, I've had to move my TB to my Windows laptop so I can answer emails. I noticed in the Repository that TB 2.0.0.5 was released. I updated, & unfortunately that made no difference.

I'm a little surprised as well. I started using Ubuntu Dapper & of course running 64bit, I've encountered many problems, but not with TB. Considering that - Fiesty so far has been the best. I don't use any packages that require force architecture, I compile where I can (give up when I can't) or use packages that are generously built by other 64bit users.

So I hadn't installed anything recently except what had been coming through the Update Manager. 

Lol, it's all speculative on my end.

Not to say that I'm glad you're having problems, but it's good there's more than one incident. I was worried it might be an anomaly. :)

---

### Post by roncrump on 2007-07-30
> **Thene said:**
> 
Not to say that I'm glad you're having problems, but it's good there's more than one incident. I was worried it might be an anomaly. :)
You can add me to the list. I'm getting the same thing.
Ron.

---

### Post by roncrump on 2007-07-31
Any idea how to get this bug given a higher priority in Launchpad?
Thunderbird is unusable in this state, as it crashes, without sending, everytime I click on send.
Ron.

---

### Post by mdr on 2007-08-01
add me to the list

---

### Post by Cardboard Cutout on 2007-08-05
Hi,
I'll do a ME TOO as well.
I've uninstalled, reinstalled, copied backups of configs across all to no avail.

Hopefully someone will work this out.

CC.

---

### Post by Thene on 2007-08-13
Sorry Ron, I have no idea. I do hope it's something that can be fixed soon - unfortunately there's a lot of bugs that take precedence over this one.

In the meantime I've switched my TB over to my laptop, it would be just my luck that I needed a new HD last week. ](*,) Thank goodness it's not OS dependent.

> **roncrump said:**
> Any idea how to get this bug given a higher priority in Launchpad?
Thunderbird is unusable in this state, as it crashes, without sending, everytime I click on send.
Ron.

---

### Post by nanotube on 2007-08-24
not really a fix, but a workaround:
try using ubuntuzilla to install the official mozilla build of thunderbird. maybe that one won't segfault on you.
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by Thene on 2007-10-22
It seems that version 2.0.0.6 fixes this problem.

I have been able to compose email and send it without Thunderbird hanging or closing. :)

---

### Post by Sabaki on 2007-10-23
I'm running tb 2.0.0.6 on Ubuntu64 'Gutsy'  but I'm still getting this segfault problem, so this is a 'me too' post.

It crashes whenever I click on a mail.  My mail is retrieved from my uw imap server, but when I click on a mail message it crashes every time.

Thunderbird is still unusable here on my amd64, although it still works fine on my 32-bit computers.


Chuck

---

### Post by Thene on 2007-10-23
> **Sabaki said:**
> I'm running tb 2.0.0.6 on Ubuntu64 'Gutsy'  but I'm still getting this segfault problem, so this is a 'me too' post.

It crashes whenever I click on a mail.  My mail is retrieved from my uw imap server, but when I click on a mail message it crashes every time.

Thunderbird is still unusable here on my amd64, although it still works fine on my 32-bit computers.


Chuck

I can't comment on Gusty because I'm still using Feisty Fawn.

I probably wasn't very helpful in my last post. I only discovered it working yesterday when I tested it after months of using Thunderbird on my laptop.

As you probably know - to get certain software working on 64bit can be challenge - I've done my fair share of trying out programs & trying to find solutions.

Since Thunderbird stopped working for me - the only thing I've done really - is kept administering the automatic updates.

Yesterday however, I unsuccessfully spent several hours trying to get Adobe CS3 Creative Suite running on Ubuntu through WINE. Some of the instructions recommended **sudo apt-get install -f** when I was having trouble with the installation.

I can't remember what instructions I was following & I can't recommend it unless you know what you're doing - especially considering the amount of instructions & repositories I've used trying to get things to work & finding they've not worked or half worked - over time - & without documenting them.

When I did that - it affected my 32bit Firefox which I needed to reinstall - but it wasn't hassle since Kilz has done such great work with a script that I used without a hitch.

The only other thing I can think of which is most likely irrelevant was that I had to force downgrade a package to install WINE because dependencies couldn't be satisfied with the latest one. (It might've been libc6 - I think.)

I've since uninstalled WINE. Then I just happened to be curious about Thunderbird, & obviously you can imagine my surprise when a test email worked.

So they are absolutely all the steps I did yesterday before finding it was working again. It could've been a conflicting package - I just don't know.

There hasn't really been much movement with the bug at launchpad - I hope you find a solution.

---

### Post by JayBee on 2007-10-25
I will add myself to the list of affected users when trying to read HTML email.

Here is my (basic) setup; someone let me know if I can provide further info.

- AMD64 - (Athlon 64 X2 on an Asus M2A-VM HDMI Motherboard)
- Ubuntu Gutsy Gibbon 7.10
- Thunderbird 2.0.0.6 -- straight from Ubuntu's repositories.
- Pulling email via IMAP.
- Extensions:
* Unselect Message v1.3 [Disabled -- incompatible w/TB2]
* Lightning v0.5 [Enabled]
* Allow HTML temp v1.0.3 [Enabled] -- "Allow temporarily HTML in a selected message"

So, I also get a Segmentation Fault crash when selecting an HTML message. I, too, am using an IMAP server to retrieve my email.

I have noticed that if I select a (previously seen) text-only message, TB stays put. But if I select an HTML message immediately after that, the window goes away.

I had initially suspected an issue rendering HTML. But interestingly, the "Allow HTML tmp" seems to be ineffective, or the problem lies in the execution path before it reaches the extension for execution. I now doubt my HTML rendering theory because: a) it would have to happen after the extension runs, and b) other gecko-based applications would be affected too.

---

### Post by Sabaki on 2007-10-25
So, I did an apt-get update and apt-get upgrade and saw it said it upgraded thunderbird to  thunderbird-2.0.0.8. I had hopes this would fix the problem, but it hasn't. Thunderbird still crashes when trying to retrieve mail from my uw-imap server. It retrieves the headers OK, but usually, but not always, crashes when I click on an email.

And this is strange... What I see in Synaptic is
thunderbird-2.0.0.8~pre071022+nobinonly-0ubuntu0.7.10

But when I look at the <help> <About Mozilla Thunderbid> I see
version 2.0.0.6 (20071022)

So, it looks to me like this isn't really 2.0.0.8

Anyway, Thunderbird is still unusable when it keeps crashing, and Thunderbird an application I've been using reliably for many years  and depend on a lot.  I'm trying to use Evolution meanwhile, but it is really slow awkward with the quantities of email and contacts I deal with.

I sure hope this gets fixed soon.

Anybody know what bug report(s), if any, have been filed or if this has been reported?


Chuck

---

### Post by lsilver on 2008-03-10
Hello.

This thread exactly details what I am now experiencing after a recent upgrade of Thunderbird on my AMD64 machine.  However, the discussion stops back in October with now resolution.  Did you get a fix for this problem?

Regards, Leo.

---

### Post by Thene on 2008-03-11
Just wanting to update - I am running Gusty & my version of Thunderbird is now 2.0.0.12.

I've had no issues since my last post.

Perhaps those of you who are experiencing the IMAP issue, might find it different from what I initially encountered as I retrieving from a POP account (although I note they are both segmentation faults).

IMAP users may be able to find some useful information in _[Thunderbird Support]("http://forums.mozillazine.org/viewforum.php?f=39&sid=d02fe67411acfc06e7ff2b21b5b4eb01")_ or _[Thunderbird Bugs]("http://forums.mozillazine.org/viewforum.php?f=31")_ at MozillaZine.

I hope this may shed some light on situation. :)

---

