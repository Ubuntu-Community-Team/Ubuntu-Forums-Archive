---
title: "Migrating from Mac OSX"
date: 2005-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by amanda on 2005-10-19
I just installed Ubuntu on a PowerBook and am now faced with all kinds of migration challenges. On OSX I was using Mail for some accounts and Thunderbird for others. The idea was that I was going to test things out but then it stuck and I just left it like that. Each account has a dozen mail filters that sort list messages into folders and the like (and some cool ones that move read or unread newsletters I subscribe to to the trash after a week). 

I'd really like to just migrate the Mail rules and Thunderbird filters into Evolution -- can I do that?

Ditto for Thunderbird to Evolution or just OSX Thunderbird to Ubuntu Thunderbird. 

Any ideas?

---

### Post by amanda on 2005-10-19
I'd also like to get my hands on some kind of weather pop-like widget for Ubuntu. I am about to go buy myself a snack, and I realized just how addicted I've become to being able to see the current temperature on my screen. 

I know that there is some comparable widget out there. or i hope their is.

---

### Post by poofyhairguy on 2005-10-19
Wrong forum so I moved it.

---

### Post by autocrosser on 2005-10-19
Well--The easiest way is to move the Thunderbird filters--in OSX you just find mozilla in your User's folder--browse it & pull what you need--In Ubuntu you need the enable hidden files--then look for thunderbird.(there may be permission problems--post if this happens)
 
As for temp--Install gDesklets & then google gDesklets--this will land you at their home where you can download all kinds of widgets.:D

---

### Post by jdp on 2005-10-19
As for the weather applet, just right-click on the top bar of the screen.  Then select "Add to Panel..."  Select "Weather Report" from the list.  Then right click on the new icon and configure it to your local and prefs.  Very simple. :)

---

### Post by amanda on 2005-10-19
[QUOTE=jdp]just right-click ....  Then right click ...  Very simple. :)[/QUOTE]

Which raises another question: how do I right click?

Or, more comprehensively, what do I have to do to restore my command key to relevance and relegate my control key to helping me right click?

And in the meantime, Is there another way to right click?

---

### Post by autocrosser on 2005-10-19
Very interesting--I use a Dual 1.25 with the Apple keyboard & a Logitech trackman--The trackman cost me $29 at Circuit City--that would be the fastest answer--I don't know my way around the Xorg keyboard configure to help you re-assign keys---I know several people here are using 'books & would have the answer--post that question & I'd bet you will get a quick answer.

How are you doing with the mail issue?

[quote=amanda]Which raises another question: how do I right click?[/quote]

---

### Post by ssam on 2005-10-20
right click = F12, middle click = F11

i have done similar, mail.app -> thunderbird on mac -> thunderbird on linux.

the thunderbird folder from mac os x works fine in linux. you just need to workout where it is in mac os x, and where it should go in linux (run thunderbird, find its folder (show hidden files in your home folder)).

mail.app -> thunderbird is probably best done in mac os x, then move the whole thunderbird profile to linux. it used to be fairly easy (pre tiger) as mail.app uses the standard mbox format. you just need to create the account in thunderbird, locate its mbox, and swap in the mbox from apple. (quit thunderbird before mess with its profile.) one gotcha (if i remember right) is that mail.app's profile folder has .mbox files which are actually packages. ctrl-click and go to view package contents to see the actual files.

in tiger i beleive that the file format changes so that spotlight works better, with the effect that there are not mbox files anymore. there may be an export as mbox.

you might have to do the filters by hand.

**an important note.**
in thunderbird edit-> account settings, go to server settings, and select leave messages on server. normally when you check a pop email account the mail program downloads the emails, and deletes them from the server. while you are moving between systems it may be wise to let everything stay on the server. the email program should not repeatedly download the emails. once you are happly migrated then you can set it to delete the email off the server as you download it.

sam

---

### Post by gaz_666 on 2005-10-20
i have never thought of installing linux on a mac, i know os is built on unix and therefore is possible but i just like mac os too much, what were your reasons for installing it?

---

### Post by autocrosser on 2005-10-20
Hi Gaz--
This looks like a posting hyjack--but--I was tired of the constant round-n-round of upgrades--I do graphic design & having been on macs for over 15 years-you can guess how much "old" software I own--Linux "seems" to now be on it's feet enough for me to use it on a more or less daily basis--with Gimp-Inkscape-Bluefish & several other very nice (& free) apps--I can do much of my work in this home.

[quote=gaz_666]i have never thought of installing linux on a mac, i know os is built on unix and therefore is possible but i just like mac os too much, what were your reasons for installing it?[/quote]

---

### Post by amanda on 2005-10-20
1) After upgrading to Jaguar and then upgrading to Panther I refuse to buy Tiger, just on principle.  

2) I really like OSX, but since we have a spare PowerBook in the office I wanted to test out a Linux desktop. 

3) We do a lot of training and tech consulting and people often ask if Linux is a good option. I figured I should try and spend some time using it as a workstation.

4) I want to start doing some audio projects on my own, and I'd like to see if I can get started without spending a ton of money on software. 

Those are my reasons, for the most part.

---

### Post by autocrosser on 2005-10-20
I agree!!
 
I hate to think of the thousands of $'s in outmoded software I own--Anyone want System 6 stuff?? How about a box set of 7.1??? This is a better, more cost effective way to compute--I looked at Linux about 3 years ago & thought "well, it's almost ready"-- looked again at Yellowdog at the first of the year (not quite up to the task) & then a friend said "have you seen the new Ubuntu?"--I must confess, the people are great & the software is unsurpassed.
 
End of Story.

---

### Post by amanda on 2005-10-21
Oh, and, I almost forgot. Mac OSX Help is useless and makes me scream.

---

