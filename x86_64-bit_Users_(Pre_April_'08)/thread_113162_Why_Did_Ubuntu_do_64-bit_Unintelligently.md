---
title: "Why Did Ubuntu do 64-bit Unintelligently?"
date: 2006-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by APwrs on 2006-01-05
For all the good that Ubuntu is, they really dropped the ball with their 64-bit version, especially when it comes to 32-bit application support.  Other distros have worked out 32-bit application compatibility much better, so that things &#8220;just work&#8221;.  Ubuntu is not one of them.

Some distros solve this problem by placing their 32-bit libraries in &#8220;/usr/lib&#8221; and their 64-bit libraries in &#8220;/usr/lib64&#8221;.  This way, regular 32-bit programs will look for their libs in the regular place, and they'll just work.  Most 64-bit programs (all that I've encountered) are set to look in &#8220;/usr/lib64&#8221;, so those just work too.

However, Ubuntu has this backwards.  Ubuntu uses &#8220;/usr/lib32&#8221; for 32-bit and &#8220;/usr/lib&#8221; for 64-bit.  If you download a 32-bit application off the Internet and try to use it, like Firefox for instance, it won't work because it will be looking for its libraries in &#8220;/usr/lib&#8221;.  The same goes for OpenOffice.org.

Other distros keep their 32-bit libraries in the location that the downloaded programs expect to find them, so they work.  They keep their 64-bit libraries in the location that 64-bit programs expect to find them, so those work too.  In Ubuntu, you have to set up a chroot environment, or jump through some other hoops, in order to get 32-bit programs to work.  And even at that, some of those programs may not work very well.

The way Ubuntu handles 32-bit compatibility is just nonsense.  Other distros do it much better.

I'm fine with recommending 32-bit Ubuntu, but until Ubuntu learns from others, I simply cannot recommend Ubuntu 64.

---

### Post by ATAQ on 2006-01-06
In synaptic search for the program "linux32"
Then download a 32-bit app.
then run the program with "linux32" before it.
for example linux32 sh firefox.sh

But I do understand what you are saying, this should work most of the time, but where as games are involved on 64 backward compatibility is a bit rough or so I found anyways.

Regards,

---

### Post by queenorych on 2006-01-06
Ubuntu 64 is what is called a pure64 distribution.  It's from the debian amd64 port.  The idea is instead of having mixed libraries the entire system is 64 bit.  This works great except for a few programs, such as wine, openoffice, flash, etc.  So a chroot is suggested.  As I see it people got lazy and added this emu and lib32 stuff.  It's ok when it's contained, but it is still messy.  See the amd64 debian homepage for a good explanation.

For complete(as complete as any other distribution) 32bit compatability, just use a chroot!  It's not hard to setup, and once setup you can just run aptitude within the chroot to install and update programs.  In fact I'm running a debian sid 32 bit chroot.  To run 32bit firefox just a dchroot -d firefox.  I think this is the best solution to run those non-ported programs for now.

I think runing 32bit libraries in /lib for a 64bit system is a mistake.  yea compiling firefox in 64 bit doesn't add to any sizable speed increase, it's just a lot cleaner having everything 64bit, and not half 32 half 64.

Just my opinion.

---

### Post by ATAQ on 2006-01-06
Very true, personally I donts see the logic in running 32bit code on a 64bit machine,
but then again sometimes its needed.
Have you any luck recompiling 32 bit games?

---

### Post by APwrs on 2006-01-06
I understand all of your various points, but we're all here to expand the use of Linux, and you have to look at it from the point of view of the competition.

There will be many users that want things to "just work", and they will be turned off by having to go through a lot of extra steps to get things to work.  They will have some 32-bit programs that they want or need to run, and they want them to work.

As for the competition, when people install Win64, they will expect it to "just work".  When they come and try Linux, they will expect the same thing.  While it's good to have strong 64-bit support, there also needs to be good 32-bit support.  This will attract the most users, and make it the easiest for everyone.

---

### Post by John Jason Jordan on 2006-01-06
[QUOTE=queenorych]For complete(as complete as any other distribution) 32bit compatability, just use a chroot!  It's not hard to setup, and once setup you can just run aptitude within the chroot to install and update programs.  In fact I'm running a debian sid 32 bit chroot.  To run 32bit firefox just a dchroot -d firefox.  I think this is the best solution to run those non-ported programs for now.[/QUOTE]
Yay! Thanks for that statement. I already had chroot installed and used it to get Acrobat 7 running. But I've been trying and trying to get RealPlayer working, and by adapting your line to "dchroot -d realplay" I finally got it to work!

Now, for my next exercise I want to get it recognized by Firefox so when I click on a web link to streaming sound it will work. Right now if I click on web link that calls RealPlayer all that happens is that RealPlayer appears for a brief moment, then disappears, and then Firefox disappears too.

I'm sure it's some kind of a Firefox link issue. But rather than hijack this thread I'll google for a bit and maybe start a new thread for the Firefox issue if I can't figure it out. Meantime, thanks for posting that -- it gave me the insight I needed to at least get RealPlayer to launch.

---

### Post by heftigrat on 2006-01-06
[QUOTE=APwrs]I understand all of your various points, but we're all here to expand the use of Linux, and you have to look at it from the point of view of the competition.[/QUOTE]

You might suggest this to the developers of Ubuntu, or become one yourself.  I see that you are new to the forums and so far you haven't posted anything of any real value.  You might want to think about that.  **queenorych** has already explained why Debian distros use a "pure64" format.  If you really don't like it, find another distro.

---

### Post by minstrel on 2006-01-06
I am new to this community.  However, according to what you wrote, a short term work around for the 32Bit apps on the 64 Bit version could possibly be to create a &#8220;/usr/lib&#8221; folder and copy the libs to this folder from &#8220;/usr/lib32&#8221; .

---

### Post by APwrs on 2006-01-06
When I see something that could use some improvement, one of the first places I bring those comments to are the community surrounding the thing that could be improved.  I'm sorry if that makes you uncomfortable heftigrat.

As for your suggestion Minstrel, I do appreciate the input, the only problem is that "/usr/lib" is already being used by the 64-bit libraries.

---

### Post by heftigrat on 2006-01-06
[QUOTE=APwrs]When I see something that could use some improvement, one of the first places I bring those comments to are the community surrounding the thing that could be improved.  I'm sorry if that makes you uncomfortable heftigrat.[/QUOTE]

Not uncomfortable, irritated.  I believe [this]("http://www.ubuntulinux.org/community/participate") is what you were looking for.  Have fun with that.

---

### Post by APwrs on 2006-01-07
That's fine.  I didn't expect my statements to be popular.  I figured some would read them, and just think.  I thought some would read them, and agree.  I thought still others would read them and offer up advice.  And then I knew others yet would read and react as you have done.  I will refrain from using the term "fanboy".  I didn't expect my statements to be popular, no, but they still needed to be said.

---

### Post by gil-galad on 2006-01-07
Eh, its just the price of being based on debian packages instead of RPM.  RPM distros are designed to easily mix 32bit and 64bit resources.  Debian just isn't.  It's not really Ubuntu's fault.  

Although, I would like if they included more 32bit libraries by default.

---

### Post by heftigrat on 2006-01-07
[QUOTE=APwrs]That's fine.  I didn't expect my statements to be popular.  I figured some would read them, and just think.  I thought some would read them, and agree.  I thought still others would read them and offer up advice.  And then I knew others yet would read and react as you have done.  I will refrain from using the term "fanboy".  I didn't expect my statements to be popular, no, but they still needed to be said.[/QUOTE]

Well, you didn't refrain from using the term "fanboy", so you are again being needlessly insulting and childish.  My problem with people like you is you just like to complain.  I have read all your posts and so far you have only succeeded in drawing attention to yourself form a moderator and complaining about how Ubuntu should provide better 32 bit support.  You have given no useful insight, nor have you really contributed to the Linux, Debian, or Ubuntu communities.  So again, I will direct you to contact the Debian developers about the issue of 32 bit compatibility on 64 bit versions of deb-based distros like Ubuntu, or become a developer yourself.  Might I stress again that it's not that difficult to run your 32 bit applications in a 32 bit chroot environment, as **queenorych** has already so graciously pointed out.

Bottom line, I will cease to have a problem with your asinine rambling when...

1.  < 100% of your posts center around pointing out Ubuntu's faults.
2.  You show a genuine interest in the Ubuntu community, and the Ubuntu distro in general.
3.  You post something useful or insightful.
4.  You actually contact the Debian developers, and show proof of such contact, before you continue this rant of yours.

I eagerly await your useless reply.

---

### Post by APwrs on 2006-01-07
Gil-Galad, I realize the reason for the library situation is because of the way Debian is set up.  My assertions are simply that Ubuntu is trying to become the most user-friendly Linux distribution out there, so when they went to tackle the 64-bit environment, they had a chance to innovate.  Ubuntu already encourages you not to mix Debian and Ubuntu package repositories, so differing from Debian at that point wouldn't have ultimately made much difference.

And as for you heftigrat, I'm actually not annoyed or irritated by you at all.  Sorry.  I am however quite amused by how much time you're putting into this.  If you don't agree with my statements, that's fine.  Move along.  As I already stated, my issue isn't just with the 32-bit compatibility or lack thereof, it's with what Ubuntu is trying accomplish, compared to their 32-bit compatibility.  If it was simply Debian doing this, I could care less.  But with the goals that Ubuntu is trying to achieve, it needs to be more user-friendly than the base Debian system.

My statements are such based upon extensive testing of both the 32-bit and 64-bit distributions.  I always do extensive testing before forming any opinions.  As to your quip about my first post, that was more of a test than anything, to gauge the technical level of the forum in general.  The reply I received was only partially correct, but lacked a lot.  Which is not a slight at that particular moderator at all... simply an observation of the aim of the forum as a whole.  Which really just supports my previous statements about what Ubuntu is trying to accomplish, and how they could better get there.

For me, this is certainly no waste of time.  I'm actually rather enjoying it, and the longer it continues, the more people will read my comments and think about them.  Which was the whole point to begin with... getting people to think about things.  To realize that there could be a better way to achieve user-friendliness.  But if you wish to continue spending your time doing this, be my guest.  I will be happy to reply each and every time.

---

### Post by heftigrat on 2006-01-07
oh, you're so clever.  let's continue this in [the backyard]("http://ubuntuforums.org/showthread.php?t=114082").

---

### Post by hentaidan on 2006-01-07
[QUOTE=APwrs]Some distros solve this problem by placing their 32-bit libraries in “/usr/lib” and their 64-bit libraries in “/usr/lib64”.[/QUOTE]

32-bit libraries in a 32-bit system go in /usr/lib;
64-bit libraries in a 64-bit system go in /usr/lib.

Anything else seems nonsensical to me, and just plain confusing.

---

### Post by poofyhairguy on 2006-01-07
[QUOTE=APwrs]Gil-Galad, I realize the reason for the library situation is because of the way Debian is set up.  My assertions are simply that Ubuntu is trying to become the most user-friendly Linux distribution out there, so when they went to tackle the 64-bit environment, they had a chance to innovate.  Ubuntu already encourages you not to mix Debian and Ubuntu package repositories, so differing from Debian at that point wouldn't have ultimately made much difference.[/QUOTE]

Hmm...time for a little Ubuntu backround. Ubuntu is not a complete fork from Debian. It resyncs with Sid every six months.

[IMG]http://mako.cc/writing/tfontf-picture-01.png[/IMG]

> 
every six months we take a snapshot of Debian's unstable distribution, apply any outstanding patches from our last release to it and spend a couple of months testing and bug-fixing it.


From:

[http://mako.cc/writing/to_fork_or_not_to_fork.html](http://mako.cc/writing/to_fork_or_not_to_fork.html)

The reason we say not to mix with Debian is because of the modifications made to Sid during each Ubuntu development period. But make no doubt- both the 32 bit and 64 bit versions of Ubuntu rsync with Sid twice a year. Without that the Universe would not get new versions of software.

So since Ubuntu is a branch of Debian Sid, it cannot make any huge changes that would not allow for a resync. And yes....changing where the libs are is a HUGE change that would prevent resyncing.

So until Debian fixes this problem, Ubuntu CAN'T. Thats the breaks. So if you really want this to change I suggest you go ask some people on some Debian mailing lists. They are tired of hearing from Ubuntu developers demanding changes. But be careful- they might not like your ideas. 

Making life easier for the user is nice and all....but apt-get was never meant to deal with multiple archs at once. To fix the problem would require changing the basics of how Debian works. Ubuntu cannot do this itself or it could no longer sync with Sid. Stop the syncing with Sid and Ubuntu dies....

Sure it sucks that other distros lack these problems. Yet they are their own island (aka they don't have a Sid to resync with) so they can do these things. If you prefer that then use another distro- no one here will mind.

Just know that this is not an Ubuntu "problem," its a Debian problem. Its one of the (and maybe the worst) downsides with Ubuntu relying on Sid. I think its worth it for the 17000+ packages though. I would love to see any of the RPM distros with a more intellegent 64 bit version match that. They can't, I've looked at them all.

Chroot ain't that bad....

---

### Post by rplantz on 2006-01-07
[QUOTE=APwrs]... we're all here to expand the use of Linux, and you have to look at it from the point of view of the competition.[/QUOTE]

I'm not sure who you include in "we", but I'm here to learn more and to enjoy myself. And I'm not here to compete with anyone nor to expand the use of Linux. In fact, when people ask me what OS to get, I ask what they want to do. The best response, in my opinion, is seldom Linux. (I've been in the business for some 40 years, so I get asked that question a lot.)

On the other hand, I appreciate good solutions to problems, whether they come from me or from somebody else. So I think it's healthy to discuss the various ways of implementing a 64-bit system.

I'm a long-time Mac user -- got my first one in March '84. And I saw the system that lead to the Mac when I interviewed with Xerox PARC in '78. (Another person got the job.) I'm not sure how one determines the "intelligence" of a design, but these two experiences convince me that the most intelligent one does not always "win." (I realize that "win" is in the eye of the beholder.)

---

### Post by hoodwink on 2006-01-07
[QUOTE=poofyhairguy]Hmm...time for a little Ubuntu backround. Ubuntu is not a complete fork from Debian. It resyncs with Sid every six months.

[ rest of excellent explanation snipped ]

[/QUOTE]
Thanks for clarifying this without attacking the original poster. Would that some others would choose to follow your example.

---

### Post by APwrs on 2006-01-08
Very interesting responses with a lot of good information.  I can see how some things are tied very much to Debian and how that might frustrate the Ubuntu developers.  Very informative.  I can also see the appeal of having a very large package repository.  Some things I like to get from repositories, and some things I like to either get directly from the developers or compile it myself, but that's just a matter of preference.  I can understand the appeal of having a huge amount of software just a few commands or clicks away.

And again, as for heftigrat, I have no desire to take this thread anywhere else.  Even though I know you didn't intend to, you've actually helped out quite a bit.  This thread probably would have faded into the background by now, but because of all your replies, it's stayed on top and gotten a lot more viewers.

I think the statements I've presented here are valuable, of course, and especially now that this thread contains some history thanks to Poofyhairguy, I think this thread is doubly valuable.

And so, I would like to thank everyone for their replies.  It's all a lot of good information.

---

### Post by KiwiNZ on 2006-01-08
I believe this thread has out lived its usefulness

---

