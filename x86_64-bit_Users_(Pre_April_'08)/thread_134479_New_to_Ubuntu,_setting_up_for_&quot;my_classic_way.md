---
title: "New to Ubuntu, setting up for &quot;my classic way&quot;"
date: 2006-02-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by spydirweb on 2006-02-22
I've been using linux for years.  this past summer I built a new AMD64 system and wanted to run native 64.  Early I used Mandrake, than went to Slackware for years.  This past summer the best distro option I saw for native 64 for gentoo, but I got fed up with the constant changes in portage.

Last month I setup my laptop for dualbooting and was recommended to use ubuntu.   I liked it and read the 64-bit version was fairly stable, so I decided I'd switch.  So far I'm really liking it, but I have a few current "gripes."

1. The system is definately set up for "typical end user."  I noticed off the bat that make and gcc aren't shipped with the default system.  That, at first, made me FLIP OUT.  I couldn't believe it.  I started goofing around with synaptic though and wow...that's cool.  I was able to get all of that setup for myself.  I understood then why it was all left out, too.  Although, I am now curious if there is a developer based ubuntu package?  One that ships with all those goodies.

2. The system also doesn't come with the typical servers, like apache, *ftpd, etc.  Although that was easy to fix, just had to install them with synaptic.  This has just posed a problem for me, though.  I installed apache2 because I've used it for a while on my other systems and trust it, but I just rebooted the system and for some reason it said there was an apache 1.3.33 running some where.  I was able to get it off and restart with /etc/init.d/apache2 and it was fine again.  I'm horribly confused about this, though.  is it apache-ssl or something?  Also, when installing a ftpd I figured I'd try twoftpd.  I installed it, than read a little deeper into it and decided against it.  I than installed pureftpd.  no matter what i do I CANNOT get pureftpd to run.  what's up with that?

3. after install I immediately ran the update manager and got everything up to date, ran through and installed all sorts of extras, and got the system pretty much up to my usual "ok, it's useable," status.  Earlier today I ran the updater again and two packages were updated.  I can't recall which but I started having problems after that.  I have to su to root to run synaptic and the like (programs that need root access), and if I try to do log in with the gtk pop up that asks for your user password I get an error saying something like:  Failed to run /usr/sbin/synaptic as user root: Unable to copy the user's Xauthorization file.  I was getting this with a lot of stuff, and noticed a few other applications were complaining about accessing /tmp.  After some goofing around I figured I could add my user to the root group and change /tmp to 775 and everything started running normally again...thing is I hate doing this.  /tmp SHOULD be 755'd and I also shouldn't be having these problems.  Does this sound familiar at all?

I know this was really long winded, and I thank you for actually reading all of this if you did.  Any help would be greatly appreciated.  These last few final configuration points are the last bits I need.  as an 7 year linux vet I feel kind of stupid that I can't figure it out on my own, but I really need to get to sleep tonight! :p

---

