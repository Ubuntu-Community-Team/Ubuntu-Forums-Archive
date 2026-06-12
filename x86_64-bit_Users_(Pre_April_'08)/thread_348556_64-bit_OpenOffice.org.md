---
title: "64-bit OpenOffice.org"
date: 2007-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2007-01-28
After upgrading from Dapper amd64, where I had OOo 2.02, I have discovered serious bugs with OOo 2.04 that the upgrade installed. For example, drag and drop text editing does not work, although it works in other applications (e.g., AbiWord). I have reinstalled with Synaptic, but no change. I have googled, asked on e-lists and here, but have received no responses. I really, really need this functionality.

I'd like to install 2.1, either that or go back to 2.02. If you go to OpenOffice.org and look through all the pages for downloads there is not one word anywhere whether a given download version is for 32-bit or 64-bit. Synaptic lists only 2.04 now, since the upgrade.

Is there a 64-bit version of OOo 2.1 or 2.02 that I can install on Edgy? If so, where do I get it and how do I install it?

---

### Post by rsambuca on 2007-01-29
According to the OO wiki, the 64bit port is still under development and not ready for use by non-developers.

[[COLOR="Red"]See link[/COLOR]]("http://wiki.services.openoffice.org/wiki/Porting_to_x86-64_%28AMD64%2C_EM64T%29")

---

### Post by John Jason Jordan on 2007-01-29
> **rsambuca said:**
> According to the OO wiki, the 64bit port is still under development and not ready for use by non-developers.
OK, evidently it will be a long time before there will be a usable 64-bit version of 2.1. Then can I uninstall 2.04 and install 2.02 instead? I never had a problem with 2.02. Version 2.02 is no longer listed in Synaptic after upgrading to Edgy. How can I go back to it? Thanks!

---

### Post by rsambuca on 2007-01-29
I assume there is a way, but I am afraid I know not what it is.

---

### Post by kvorg on 2007-02-14
Okey, it is 2007 now, and I just checked on this families 64-bit Ubuntu laptop:**OO Writer drag and drop is still not functiona** on 64-bit Edgy Eft.

This is getting ridiculous: a supported application simply should not have such a **serious and basic bug** for such a long time. So I am assuming I am overlooking something massively simple.

*Please, enlighten & advise!*

(While waiting, I am considering hopeless things, such as going the apt-build way and staring at an openoffice build from Debian source. I just don't know for sure I have the stamina for that, though).

---

### Post by John Jason Jordan on 2007-02-14
> **kvorg said:**
> Okey, it is 2007 now, and I just checked on this families 64-bit Ubuntu laptop:**OO Writer drag and drop is still not functiona** on 64-bit Edgy Eft.

This is getting ridiculous: a supported application simply should not have such a **serious and basic bug** for such a long time. So I am assuming I am overlooking something massively simple.

*Please, enlighten & advise!*

(While waiting, I am considering hopeless things, such as going the apt-build way and staring at an openoffice build from Debian source. I just don't know for sure I have the stamina for that, though).

<Pardon in advance for what is going to be a long post.>

I have been bitten by this as well, and have posted a couple times about it. This morning I received an email from another forum user asking about this issue. I took the time just now to write down the whole, long, bloody story and send it to him. Here is what I said:

------
I do not have a solution yet. The following is a rough log of all that
I have done in an attempt to fix the problem. However, before I start I
should also add that I have an additional problem. When I go into 
Tools > Options > Writer > General there is a space to change the
default tab stop setting. By default it is set to 2 cm, or .79 inches
or 57.6 points. I use points, so I changed it to 21.6 points (.3
inches). But the setting is not saved in the default template or
anywhere. The next time I open a new document the setting is back to
57.6 points. If I set it to 21.6 points it will stay that way for that
document, but only until I close the document. The next time I open the
document the setting is back to 57.6 points and all the tab settings I
used are wrong and the formatting is messed up. I don't know if this is
part of the same problem, but it would be helpful if you could check to
see if this happens for you as well.

I started using OOo back in the days of StarOffice 5.something, and I
never had a problem with this before. Along the way I switched to Linux
(Ubuntu amd64), starting with Hoary, then Breezy, then Dapper, and
never had a problem. The first time the problem appeared was after
upgrading Dapper to Edgy. Note that the upgrade from Dapper to Edgy
also upgraded OOo from 2.02 to 2.04. I assumed, therefore, that the
problem was in OOo 2.04. 

I posted on the Ubuntu 64-bit forum, and I also found two posts by
others (jkwarras and cogitordi) who had posted the same problem:

[http://ubuntuforums.org/showthread.php?t=296702&highlight=drag+drop](http://ubuntuforums.org/showthread.php?t=296702&highlight=drag+drop)

And in addition crazedgremlin responded to another of my posts in a
separate thread. So now there are five of us that I know of. I sent
private messages to both jkwarras and cogitordi asking if they had
found a solution. Both responded that they had not, nor has
crazedgremlin found a solution

I have not found any complaints about this from 32-bit users. Nor has
google found any complaints from users of other 32- or 64-bit Linuxes.

A couple days ago I filed a bug report with OOo:

[http://www.openoffice.org/issues/show_bug.cgi?id=74478](http://www.openoffice.org/issues/show_bug.cgi?id=74478)

Unfortunately, the bug report was assigned to someone named mru, who
closed the issue without even reading the bug report.

While fuming about mru's having closed the issue so I can't even post
to it any more, I decided to see if it might be possible to install OOo
2.04 or 2.1 from the download files at OOo instead of using the
Ubuntuized versions in Synaptic. After much googling and searching I
found .deb files for OOo 2.1 here:

[http://www.nic.funet.fi/pub/misc/openoffice/localized/finnish/stable/2.1.0/20061213/?C=S;O=A](http://www.nic.funet.fi/pub/misc/openoffice/localized/finnish/stable/2.1.0/20061213/?C=S;O=A)

Last night I successfully installed OOo 2.1. But I am very unhappy with
2.1 -- the menu fonts have changed and the interface is ugly and hard
to read. Moreover, I tested it with a file containing fields tied to a
database and discovered that it could not read tables in a Base file
created in 2.02. Worse, installing 2.1 did not fix the drag and drop or
default tab problems. I have decided to give up completely on 2.1 and
uninstall it.

But installing 2.1 did demonstrate one thing: The problem is in Edgy,
not in OOo. After all, I completely uninstalled 2.0.4 before installing
2.1, so the problem has to be in Edgy. 

I will be most interested in hearing any suggestions you can offer.
--------

That's all I know for now, except that now I can add kvorg as another user who has the problem. That makes about six of us. Doubtless there are many more who never complained.

---

### Post by John Jason Jordan on 2007-02-14
I just posted a bug report here:

[https://launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/85248](https://launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/85248)

---

