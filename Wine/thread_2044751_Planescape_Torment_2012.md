---
title: "Planescape Torment: 2012"
date: 2012-08-19
forum: Wine
---

### Post by aaeamdar on 2012-08-19
So I know there's already a few posts, both in this forum and elsewhere, about running Planescape: Torment with WINE, but I've found most of these to be highly outdated (6+ years) and referencing broken links. With that in mind, I'm creating a newer thread that will hopefully help me as well as anyone else who wants to run this great game.

As a preface my own technical abilities are pretty lacking so please be detailed.

So here's where I am:

1. I've found that multiple-CD games like Planescape: Torment benefit from making ISO images before installing.

a. I used Brasero to create the ISO images

b. I used AcetoneISO to mount them

(If anyone needs help with that step it's really pretty simple, but I will post if requested).


2. I've installed the game.

a. I followed the "guided" install path in PlayOnLinux, which is based on this script:  
([http://www.playonlinux.com/sv/topic-2593-script_Planescape_Torment.html](http://www.playonlinux.com/sv/topic-2593-script_Planescape_Torment.html))

b. During install I chose not to install Acrobat Reader or reinstall DirectX, since the installer told me I already had a compatible DirectX version.

c. I encountered issues with this so I also tried a manual install. I then spent a while in wine config trying to make it see the CD. Again, I can post about that if needed. 

3. However, when actually running the game, I get messages about how the fact that I'm not in 16-bit color could make things difficult.  Then, it crashes before I get anywhere. This is the part I could use help with. I've monkeyed around with various settings (the debug report recommended I try Windows NT 4.0 or Windows 3.1, and I tried both of those) but nothing gets me beyond this crash. 


That's pretty much it. I'm in Ubuntu 12.04 and Wine 1.4, if that helps. I'm definitely going to continue trying different things but if anyone has hints, they'd be much appreciated. And when I get this solved I'll come back and update the thread with the final solution. 

Thanks in advance!

---

### Post by c_cinq on 2012-08-21
+1 for classic rpg.

[winehq]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=294") could be a resource.

---

### Post by aaeamdar on 2012-08-21
OK my first instinct is to post something really sarcastic like "Wow, winehq - why didn't I think of that?" But in the spirit of not being mean to people who are well-intentioned, I'm going to refrain from doing that and instead be straightforward.

I guess you are also pretty new to the forum and I appreciate that you are trying to help, but your suggestion is basically equivalent to "Google "running Planescape: Torment on Linux" ", i.e. anyone who has half a brain and isn't completely lazy would have already tried that.

Those types of suggestions tend to make people who already have spent many hours searching pretty irritated, which is what happened here. In my opinion, and others may disagree, I think you should refrain from posting stuff like that unless it looks like the poster really has not done any work and might be helped by the simple suggestion, i.e. if my post looked like this:

> how do u run planescape torment on linux i am stuk

---

### Post by thatguruguy on 2012-08-21
I'm not new to the forum, and referring people to WineHQ is the first thing I usually do. It's clear you've already researched the issue, though, so I'll assume you don't need any further help.

Good luck.

---

### Post by aaeamdar on 2012-08-21
First off, I'm assuming that your post is just a sarcastic way of saying "don't disrespect people who are trying to help. The only other conclusion would be that you didn't actually read what I said, since I was very clear about the fact that I do need help.

> I'm not new to the forum, and referring people to WineHQ is the first thing I usually doThat's fair. However, there's a difference between it being the *first* thing you do and it being the *only* thing you do. I think I was pretty clear in my post about the reason why I found c_cinq's post frustrating and unhelpful. I've followed at least a half-dozen guides on how to supposedly make this game go; none of them did the trick. Then I get the equivalent of "did you try google?"

I responded to that in an assertive fashion, trying to describe what I found frustrating and unhelpful rather than just being sarcastic. If you don't like it, tough.

---

### Post by thatguruguy on 2012-08-21
> **aaeamdar said:**
> First off, I'm assuming that your post is just a sarcastic way of saying "don't disrespect people who are trying to help. The only other conclusion would be that you didn't actually read what I said, since I was very clear about the fact that I do need help.

That's fair. However, there's a difference between it being the *first* thing you do and it being the *only* thing you do. I think I was pretty clear in my post about the reason why I found c_cinq's post frustrating and unhelpful. I've followed at least a half-dozen guides on how to supposedly make this game go; none of them did the trick. Then I get the equivalent of "did you try google?"

I responded to that in an assertive fashion, trying to describe what I found frustrating and unhelpful rather than just being sarcastic. If you don't like it, tough.

I did read what you read. I've also read the post I just quoted.

This is a forum in which volunteers help other users. No one here *has* to help you. The way you respond to those who choose to help you will impact the willingness of others to offer help in the future. If you found his post frustrating and unhelpful, you could have ignored it, rather than giving him a disincentive to help others, and giving everyone else a disincentive to help you.

I haven't seen you offer help to anyone yet, and I've now seen you act in a condescending manner to someone offering help to you. I would humbly suggest that you be more respectful to other users.

---

### Post by aaeamdar on 2012-08-22
> **thatguruguy said:**
> I haven't seen you offer help to anyone yet, and I've now seen you act in a condescending manner to someone offering help to you. I would humbly suggest that you be more respectful to other users.

First, I feel that I am not qualified to offer help to anyone as I know basically nothing about Ubuntu/Linux. I made a mistake by switching to Linux without doing much research (I had previously had a dual-boot install where I could do things in whichever OS was easier, boring story) without having the ability to go back to Windows (really, *really* dumb).

Long boring story aside, I hear your point, and I understand your logic. It was certainly never my intention to be condescending to either you or c_cinq. If it came across that way, it was because of my poor wording and I apologize. I do maintain that it is, in a general sense, legitimate to let someone know when they have aggravated you (intentionally or otherwise), provided that it is done assertively and respectfully. I felt that my reply was mostly within those bounds, though I can understand why you might feel otherwise.

I'm not trying to steal the last word here; your reply to any of the above is welcome. However, I'm done talking about this whole chain. If anyone is interested in talking about the original subject, details of running P:T and ideally creating a walkthrough for the modern version, I will endeavour to not shoot down any ideas you might have.

---

### Post by aaeamdar on 2012-08-23
No progress thus far. I also tried a complete manual installation (bypassing PlayOnLinux and just running wine from the console) - no difference ultimately. The angle I'm looking at now is trying to run wine in 16-bit color. I would think that this would be an option in winecfg, but it doesn't seem to be (am I missing something?). I took a look at this page:

[http://wiki.winehq.org/256ColorMode](http://wiki.winehq.org/256ColorMode)

and tinkered around with the "Xnest" section, but failed, largely because I have no clue what the X server is, or what any of the other info on the page means. I also don't see how it's connected to wine other than it being on the winehq website. If anyone has any thoughts about how to run WINE in different color modes, or if this Xnest or Xephyr thing is the right place to look, I'm all ears. Same goes for general ideas for P:T.

I also tried the "beta" version of wine (1.5) which didn't seem to make any difference. This was based on looking at this "Platinum" rating for P:T with Ubuntu 12.04 and WINE 1.5.3  ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=22661](http://appdb.winehq.org/objectManager.php?sClass=version&iId=22661)). I can't figure out what about my setup is so different. For others it seems to just work straight out of the box, no troubleshooting needed.

---

### Post by aaeamdar on 2012-08-26
I found a pretty recent guide through following the link here:

[http://www.gog.com/en/forum/planescape_torment/planescape_on_linux_wine_howto](http://www.gog.com/en/forum/planescape_torment/planescape_on_linux_wine_howto)

Direct link is here:

[http://www.neant.ro/2011/12/planescapetorment-on-linux/](http://www.neant.ro/2011/12/planescapetorment-on-linux/)

I was optimistic about this working since it was so recent. I had to make a few adjustments that I can detail if anyone is interested, since I'm using the "2 CDs version" rather than the gog.com version and Ubuntu rather than Debian. However, it didn't end up working for me - again, I can give details if anyone is interested.

I'm now working with something called GemRB. I'll come back with details.
Link: [http://www.gemrb.org/wiki/doku.php?id=start](http://www.gemrb.org/wiki/doku.php?id=start)

---

