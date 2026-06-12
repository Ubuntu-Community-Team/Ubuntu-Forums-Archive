---
title: "Dapper vs. Hardy"
date: 2008-05-02
forum: x86 64-bit Users
---

### Post by Doctor J on 2008-05-02
I have a system that's running 64 bit Dapper, and have held off updating as Edgy, etc. didn't seem to make things any easier on 64 bit users.  Dapper's got about another year's support on it...  If i jump to Hardy, how many hoops will i have to jump through this time to get all codecs, etc. working?

P.S. Is it yet possible to run BOINC and have the client get crunchers w/o bending over backwards?

---

### Post by Half-Left on 2008-05-02
Hardy prompts you to install the right codecs, VLC plays alot of formats anyway.

---

### Post by ASULutzy on 2008-05-02
Hmmm, when I get home I'll test the difficulty in getting Boinc going.

I had it running on Gutsy 32 with no problem, but I'll have to see about Hardy 64

---

### Post by jamesford on 2008-05-02
cant remember having had those problems you are describing (then again dapper was a long time ago and my memory isnt the best)

---

### Post by old_geekster on 2008-05-02
I have not used "Dapper", but I have to believe that Ubuntu has come along way since then.  Yes, it isn't perfect at this point, but I expect it to get much better as folks make updates.  HH has come along way since Edgy.  I know that for a fact.

---

### Post by Kilz on 2008-05-02
> **Doctor J said:**
> I have a system that's running 64 bit Dapper, and have held off updating as Edgy, etc. didn't seem to make things any easier on 64 bit users.  Dapper's got about another year's support on it...  If i jump to Hardy, how many hoops will i have to jump through this time to get all codecs, etc. working?

P.S. Is it yet possible to run BOINC and have the client get crunchers w/o bending over backwards?

I read someplace that those wanting to upgrade from dapper-Hardy might want to wait for the 8.04.1 release (june sometime).

---

### Post by LO Matt on 2008-05-03
> **Doctor J said:**
> I have a system that's running 64 bit Dapper, and have held off updating as Edgy, etc. didn't seem to make things any easier on 64 bit users.  Dapper's got about another year's support on it...  If i jump to Hardy, how many hoops will i have to jump through this time to get all codecs, etc. working?

P.S. Is it yet possible to run BOINC and have the client get crunchers w/o bending over backwards?

As far as boinc goes, you shouldn't have problems.  Any back bending (which I think would be app_info.xml files) should stay there after upgrade.  To play it safe, backup copies of those files.

Actually, these days the main projects will send out work to 64-bit clients automatically if you have a new enough client.  I would think the client in Hardy would be new enough so it should be easier.  I haven't looked, but I'm upgrading (from gusty) right now.

Hardy here I come . . .

---

### Post by Sef on 2008-05-04
> I have a system that's running 64 bit Dapper, and have held off updating as Edgy, etc. didn't seem to make things any easier on 64 bit users. Dapper's got about another year's support on it... If i jump to Hardy, how many hoops will i have to jump through this time to get all codecs, etc. working?

Installing codecs is a lot simpler than in Dapper.  Either click on the box that pops up, or go into Add/Remove to install them.

---

### Post by Bubba64 on 2008-05-04
> **Sef said:**
> Installing codecs is a lot simpler than in Dapper.  Either click on the box that pops up, or go into Add/Remove to install them.

Thats a fact people want to do all kinds of specialized installs when it's all in add remove, or at least most of it.

---

### Post by autocrosser on 2008-05-04
I'm running the testing 6.1.17 version of BOINC on Hardy (32bit)--I don't install thru the repositories, just run it in my user /home--No special things to make it run....

If you run the last 5 series (5.10.45) the manager app will auto-start the client--no hoops to run thru here---We are having some problems with the 6 series & auto-start right now--should be ironed out with the 6.1.20 release. 

As far as Hardy itself--I alpha'd & beta'd the whole 6 months--only reinstalled during Alpha2 (my mistake), other than that Hardy was a fairly smooth sail for me---Using a custom-built Core-duo unit built just for Linux compat & testing use.

Any BOINC info you need--just ask (PM me):)

---

### Post by Doctor J on 2008-05-06
> **Kilz said:**
> I read someplace that those wanting to upgrade from dapper-Hardy might want to wait for the 8.04.1 release (june sometime).

Well, i was thinking of doing a backup and clean install.  However, since i'm expected to be busy with end-of-semester issues, i could wait for the update.  Do we have a clue as to what differences will be in the 8.04.1?

---

### Post by Doctor J on 2008-05-06
> **LO Matt said:**
> As far as boinc goes, you shouldn't have problems.  Any back bending (which I think would be app_info.xml files) should stay there after upgrade.  To play it safe, backup copies of those files.

Actually, these days the main projects will send out work to 64-bit clients automatically if you have a new enough client.

Well, i never did figure out precisely what i was supposed to put in that xml file, and thus gave up altogether.  As for the clients, when i was looking into this [long time ago] very few projects were making 64 bit clients.  Those that did, mostly didn't have much work to do.  Perhaps they've gotten better, but i expect those projects have a fairly limited number of programmers to do such.  It's just a shame they won't release their crunchers as OS, this would free them from having to create and support all clients.  Of course, then they'd have to be concerned about a doctored client sending fraudulent data...

---

### Post by Doctor J on 2008-05-06
> **autocrosser said:**
> Any BOINC info you need--just ask (PM me):)

I'll certainly keep that in mind, thanks!

---

### Post by hodge24 on 2008-05-06
> **Doctor J said:**
> I have a system that's running 64 bit Dapper, and have held off updating as Edgy, etc. didn't seem to make things any easier on 64 bit users.  Dapper's got about another year's support on it...  If i jump to Hardy, how many hoops will i have to jump through this time to get all codecs, etc. working?

P.S. Is it yet possible to run BOINC and have the client get crunchers w/o bending over backwards?

Codecs etc. are automatically detected when you open a file, and the option is given to install if you don't already have them.

I have written a simple Perl script for displaying BOINC data in Conky, which can be downloaded either from [http://www.64bitjungle.com/tech/boinc-and-setihome-with-conky-on-ubuntu/]("http://www.64bitjungle.com/tech/boinc-and-setihome-with-conky-on-ubuntu/") or from the [Forum]("http://ubuntuforums.org/showthread.php?t=722200")

---

