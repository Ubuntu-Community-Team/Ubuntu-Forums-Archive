---
title: "Cronjob perl madness"
date: 2008-03-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by weezer316 on 2008-03-29
Hi,

This is my first post and im new to ubuntu, so please dont laugh to hard if i seem to be all over the place.

Basically, I have a script that does some bits and bobs, and creates a html file and uploads it to a webserver. 

When i try and run this with a cronjob, i get this:

Can't locate Mail/SendEasy.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /home/weezer/Documents/Perl/scripts/rbl_master.pl line 8.
BEGIN failed--compilation aborted at /home/weezer/Documents/Perl/scripts/rbl_master.pl line 8.


and the same for the packages i am trying to use!!

But....i have perl 5.10 installed and have had for some time. Why is cron using 5.8.8 and how can i change it to use the latest build?

---

### Post by dcstar on 2008-03-30
> **weezer316 said:**
> Hi,

This is my first post and im new to ubuntu, so please dont laugh to hard if i seem to be all over the place.

Basically, I have a script that does some bits and bobs, and creates a html file and uploads it to a webserver. 

When i try and run this with a cronjob, i get this:

Can't locate Mail/SendEasy.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /home/weezer/Documents/Perl/scripts/rbl_master.pl line 8.
BEGIN failed--compilation aborted at /home/weezer/Documents/Perl/scripts/rbl_master.pl line 8.


and the same for the packages i am trying to use!!

But....i have perl 5.10 installed and have had for some time. Why is cron using 5.8.8 and how can i change it to use the latest build?

Cron does not need changing - as it specifically says it is using "@INC" (whatever that is) and that is where the problem lies.

Cron runs in its own environment - not the environment you run in a user shell.

---

### Post by weezer316 on 2008-03-30
Right, that i kind of understand....so how do i set that environenmt to use the latest version of perl. I was going to remove 5.8.8 via synaptic but it told me the system may become unusable, so i cancelled that.

Any ideas? been reading up on cron but its a pretty complicated set up

---

### Post by doug_seay on 2008-04-30
Did you ever get an answer?

If you are seeing the wrong version of perl in crontab, the fix is to be explicit.  Make sure you launch "/local/per5.10/perl" or whatever it is on your machine instead of "perl".  You can also explicitly set PATH=... in the crontab file, but I don't like that approach as much.

FYI: The basic issue is that cron doesn't load your startup scripts (.profile, .login, or whatever else you are using) so it has a very generic environment.  Most likely whatever you did to add perl 5.10 didn't go into one of these generic locations.

- doug

---

