---
title: "how to forward email in evolution"
date: 2009-03-08
forum: x86 64-bit Users
---

### Post by gretarsson on 2009-03-08
Hi there I was looking for rule to create so my evolution can automatic le forward email from some special sender to another email ; I did use it a lot in outlook but I can not find how to make this rule in evolution, some idea plx

---

### Post by lensman3 on 2009-03-09
From my HOWTO directory. 

How to forward an entire mailbox to a new address

formail -Y -s sendmail [email]person@new_address.com[/email] </var/spool/mail/mail-file


Then delete the file "/var/spool/mail/mail-file.


You will have to go find formail, but I think it already installed.  "formail" has been around since the '80's".  This might get you banned, since it is a very aggressive email forwarder.  Also "sendmail" will have to be installed so that it can forward  legitimately.

---

### Post by gretarsson on 2009-03-09
> **lensman3 said:**
> From my HOWTO directory. 

How to forward an entire mailbox to a new address

formail -Y -s sendmail [email]person@new_address.com[/email] </var/spool/mail/mail-file


Then delete the file "/var/spool/mail/mail-file.


You will have to go find formail, but I think it already installed.  "formail" has been around since the '80's".  This might get you banned, since it is a very aggressive email forwarder.  Also "sendmail" will have to be installed so that it can forward  legitimately.
Hi and thanks for reply but I am talking about single email not all emails. like if some person are sending email and I want to forward that email every time to another person, in outlook was rule so you can do this. any another idea.

---

### Post by philinux on 2009-03-09
> **gretarsson said:**
> Hi there I was looking for rule to create so my evolution can automatic le forward email from some special sender to another email ; I did use it a lot in outlook but I can not find how to make this rule in evolution, some idea plx

From the tool bar. Message>Create Rule.

---

### Post by gretarsson on 2009-03-10
> **philinux said:**
> From the tool bar. Message>Create Rule.

Hi I know about this tool bar but it is no rule there for forward email from special sender to another email like it was in outlook I was just asking if some one know about easy way to do this in evolution

---

### Post by coolhandluke on 2009-03-11
From what I hear, I think you're (currently) out of luck.  You could try Mozilla's Thunderbird and associated products; popular and a similar look...

---

### Post by msknight on 2009-03-19
Hi,

Just like to add my voice to this; I wish Evolution to forward specific messages to my mobile phone, but there is no forward rule.

Where do we go to ask for this feature please?

---

### Post by dcstar on 2009-03-20
Ok, I have the **postfix** package installed, configured and working on my machine.

Create a set mail forwarding file (somewhere in your home folder) called "forward-1" (or whatever containing the following:

```
!/bin/sh

sendmail address-to-forward-to@whatever.it.is

exit 0
```

Then make the file executable. The create an Incoming rule in Evolution that uses the "Pipe to Program" action to the file you have just created with a "Filter Criteria" that you want.

Now when mail arrives that matches your "Filter Criteria", it will be passed to the mail forwarding file which will then send it to the address you have set in it.

You have to set up a separate file for each rule, but it is not that difficult.

---

### Post by msknight on 2009-03-20
Hi DCStar,

If you're part of the team and are aware of this being added, then sure, I'm happy to wait. I wanted the link to the team because I've got a few other things and I dare say that I'll find more :D

In fact, I came over from Kmail after it started scrunching up the paragraphs in the mails I was sending; this happened after the last update and I couldn't find out how to revert it. I thought Evolution would be more advanced than Kmail, but the more I'm using it (and indeed I'm now forced to use Outlook at work - we've just moved over from Groupwise) there are a few little quirks that I either used in Kmail and I can't in Evolution, or might be an idea to incorporate.

I found in the rules, that if I wanted to move an item in to the trash, I had to add the condition to stop rule processing. Where do I find the generic option which enables all rules to stop after one  finds a match please?

The rule search isn't automatically case insensitive; how do we get around this, will it accept standard pattern matching? Is it a feasible option for the system to offer the user a tick box for case insensitivity and alter the search pattern for us?

Obviously, the forwarding issue is a biggie for me; I use it to forward the important stuff to my mobile.

I think the default installation has double-booked the CTRL+M shortcut both for displaying/hiding the message window and also marking it as iMportant. I think it's the CTRL+M anyway, I tried CTRL+W to mark a mail as, "work," to see if it was the CTRL+ or the ALT+ but Evolution bombed out with no error. The ALT+W didn't do anything to the mail.

The ability in Outlook to drag and drop mails in to the ToDo list helps me a lot in my work. Any idea if this is on the ToDo list of the Evolution team please? Also, having a little ToDo window always open on the right, with an appointment reminder window,assists me greatly with my self organisation *(because I'm a dumb idiot and can't remember my appointments!) *

Other than these things, I'm loving Evolution. It has the promise to give me my life in one screen, and the ability to back it up to a file and presumably restore it to another copy of Evolution on another machine promises to make my life easier to swap my organisation between a powerful desktop and an, "on the road" machine.

Another suggestion ... how about a, "remote folter," so that Evolution can work from a mounted USB stick or a network share ... that would really make the system ultra portable without the user having to mount the USB volume in to the home directory. Probably a far fetched, stupid idea; I know; I'm full of them!

Michelle.

---

### Post by dcstar on 2009-03-22
All applications have their own development forums/maintainers, this is an Ubuntu help forum.

---

### Post by msknight on 2009-03-26
Hi dcstar,

That's fine.

I just got the impression from your previous post that you were part of the team.

In which case, I return to my other question ... where is the Evolution support forum/place please?

After a short while of using it, I think I'm going to go back to kmail ... so I'm actually going to have to start another thread for advice on that.

Michelle.

---

### Post by oldos2er on 2009-03-26
[http://projects.gnome.org/evolution/](http://projects.gnome.org/evolution/)

---

### Post by msknight on 2009-03-26
Thanks Ann,

Much appreciated.

---

