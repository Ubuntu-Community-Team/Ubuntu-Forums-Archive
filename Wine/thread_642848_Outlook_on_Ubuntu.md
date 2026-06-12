---
title: "Outlook on Ubuntu?"
date: 2007-12-17
forum: Wine
---

### Post by GordonCopestake on 2007-12-17
Apologies if this has been covered before but searching didn't uncover much. Is there any way I can install Outlook (xp/2003/2007) in Ubuntu, using Wine or any other way? I am happy to use evolution and open office but need access to my Exchange server at work so have to use Outlook as I believe it's the only MAPI client?
Any info would be appreciated

---

### Post by AlanRogers on 2007-12-17
If you're using Ubuntu, as opposed to X/Kubuntu, then use Evolution which is installed by default. I haven't tried it but I'm told that it interacts well with Exchange.

---

### Post by macogw on 2007-12-17
Evolution can only interact with Exchange as a proxy through the web interface for Outlook.  If the mail server doesn't have the web interface enabled, Evolution won't work.

Crossover Office might be able to do it.

---

### Post by ChrisMoore0908 on 2007-12-25
Guys, I hope this is a helpful post. I have just installed Ubuntu 7.10, Crossover 6.2, and installed my copy of Outlook 2003 and I am pleased to advise that Outlook works perfectly. Everything - calendar, email, tasks etc. Attachments open perfectly in their native Linux applications, so a word attachment will open in Open Office, for example. Outlook is downloading from my POP3 account and my MS Exchange account. So I can synch my Blackberry pearl pda from the MS Exchange, and use either Evolution or Outlook as I please. I am VERY impressed with Crossover. I am using the trial version, but see no reason not to purchase it.

As I said, I hope this helps anyone thinking of running Outlook under Linux.

Any questions?

---

### Post by hikaricore on 2007-12-25
I was under the impression that the trial version of Crossover was a 30 day limited copy?
Remember that Crossover works with and supports the WINE project directly, so your money wouldn't be going to waste.

^_^

---

### Post by bimmerd00d on 2007-12-25
Lol, i suppose one of us has to do it.  What's wrong with Evolution or Thunderbird?  I've waved bye to Outlook 2003, which was probably the best Microsoft app.  Even if it did crash on me quite a bit, but that may have been due to  XP/Vista moreso than Outlook itself.  I went the route of Swiftdove with the lightning calendar plugin and haven't looked back.

---

### Post by cogadh on 2007-12-25
I believe there are third-party plugins for Evolution that allow it to access an Exchange server through MAPI, just like Outlook. I think the Evolution Brutus plugin is the one that can do that. The standard Evolution Exchange plugin is the one that only allows web interface access.

---

### Post by TolTime on 2007-12-26
At work we can only access our mail trough the web.
so evolution works well with transferring from outlook or would another email service be better?

---

### Post by Wiebelhaus on 2007-12-26
I think I just puked alittle.

But no , not now , rumors have it Fedora has got something cooking , not sure about the specifics.

---

### Post by baxterdog on 2007-12-26
Are you serious that you can't imap or pop into your email with another client. Are you federal? Because the latest word is that the hand has come down that fed's (even noaa, nmfs, et al) have to use IE and outlook on their 'puters.

---

### Post by TolTime on 2007-12-26
no im not federal, 
im a part time student and i work for the IT department for my school
The whole department switched from groupwise to outlook.
every part timer has to access our mail through webmail.***.edu.
and it annoying because it logs us out after 5-6 min, and we have to constantly send emails.

i was just wondering if there was any way for evolution to access outlook?

---

### Post by baxterdog on 2007-12-26
You don't need evolution or outlook to access .edu accounts. Have you tried using a terminal and shelling in?
<code>ssh -l loginname site</code>

---

### Post by baxterdog on 2007-12-27
OK, so I haven't figured out how to show code in the proper window, but the terminal command is;

ssh -l 'yourusername' 'youruniversityserver'

It will ask for you to accecpt the license, then ask for your passcode. At the prompt type 'pine' or 'elm'. Try pine first. 

Also, try looking at your university computing department website. Some are C&C. They will have step-by-step how-tos for most email clients.

---

### Post by TolTime on 2007-12-27
i will work on it and see if i can get it working.
im not sure of the server name i will have to find that out

---

### Post by baxterdog on 2007-12-27
OK, it sounds like it's actually a webmail client. You should be able to log into your .edu account and click a link for your mail. (There is always an option for imap/pop, you just have to check your university website for info) 

Hope this helps.

---

### Post by TolTime on 2007-12-27
well i work for the IT department so i just have to ask my boss tomorrow.  i would like to use evolution for my laptop computer, due to being on it most of the time at work.

---

### Post by sucrou on 2008-09-03
Why do these threads evolve into suggestions for REPLACING Outlook?

There are a number of perfectly valid reasons why people who love Ubuntu may need (or want) to keep Outlook or some other Window$ program (iTunes comes to mind).

One reason for keeping Outlook is Nelson Email Organizer (NEO) Outlook add-on by Caelo Software.  This is the only software out there that provides multi vector indexing of email archives (every email, thread, correspondent, attachment, etc. can be indexed and referenced in multiple ways - by date, category/project, status, and so on), fast (and I mean FAST!) searches, threading that runs circles aroun Evolution, Gmail, Thunderbird, and excellent (keyboard-friendly) interface.  The amount of control and time saved by using NEO on top of Outlook is astonishing!

At present Caelo has no plans to support any email archive format  other than OST/PST files, and for me and others usability will have to trump (Linux) purity. (for the record, I moved the rest of my family onto Evolution :-)

Therefore, anyone out there who gets Outlook and NEO working on Ubuntu (be it via Wine, Crossover, Virtual Box or any other way), and posts detailed instructions on how to do it, will be doing us a favor.  Anyone who figures how to replicate the functionality directly to Ubuntu would be a hero!

You can also try NEO at [http://www.caelo.com/a/rl.php3?i=35WTC](http://www.caelo.com/a/rl.php3?i=35WTC) and see what I mean.

---

### Post by +Eric on 2008-09-03
Yeah, I'm not so sure why everyone suggest replacing outlook either, for some it's not a good option. It's been one of the things that I've put up with, but I really want outlook back.

I have a windows mobile smartphone that is sync'd with an exchange server. The only way I know of to get full benefit of that is to have outlook client running. It used to be sooo nice adding an appointment inside outlook and having it sent to my phone instantly without me having to do anything.

I can use outlook web client, but it's not very good. I really want outlook, and really don't like evolution (if not even mentioning it's lacking in working with exchange). I understand it's not anyone but MS's fault, but "replacing" outlook is not a good option for me.

---

### Post by SirDevan on 2008-09-04
I think people suggest leaving outlook because normally when someone goes to a Linux OS they are trying to get AWAY from Microsoft and/or a High Cost solution.

Personally I hate MS and Outlook and prefer Evolution. I just can't seem to get my old pst imported so I can move on with my life.

Devan

---

### Post by ThomasNovin on 2008-09-14
There is now a bug on LP about syncing OpenChange from Debian Lenny. This would add Exchange 2007 support to Ubuntu. The bug id is [260786]("https://bugs.launchpad.net/ubuntu/+bug/260786").

I think it is very possible to get the Debian version working in Ubuntu already though.

---

### Post by ThomasNovin on 2008-09-14
[http://lists.alioth.debian.org/pipermail/pkg-samba-maint/2008-January/003416.html](http://lists.alioth.debian.org/pipermail/pkg-samba-maint/2008-January/003416.html)

Edit: These packages are obsoleted by the ones in Debian Experimental.

---

### Post by mathanmohan on 2010-08-21
> **ChrisMoore0908 said:**
> Guys, I hope this is a helpful post. I have just installed Ubuntu 7.10, Crossover 6.2, and installed my copy of Outlook 2003 and I am pleased to advise that Outlook works perfectly. Everything - calendar, email, tasks etc. Attachments open perfectly in their native Linux applications, so a word attachment will open in Open Office, for example. Outlook is downloading from my POP3 account and my MS Exchange account. So I can synch my Blackberry pearl pda from the MS Exchange, and use either Evolution or Outlook as I please. I am VERY impressed with Crossover. I am using the trial version, but see no reason not to purchase it.
 
As I said, I hope this helps anyone thinking of running Outlook under Linux.
 
Any questions?
 Please Chris for god sake tell me how did you pull this trick,I tried hard to configure pop3 for outlook 2003 under crossover in ubuntu 10.04 platform it didnot work.
 
Thanks in advance.
Regards
Mathan.

---

