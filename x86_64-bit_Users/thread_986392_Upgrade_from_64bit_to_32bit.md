---
title: "Upgrade from 64bit to 32bit"
date: 2008-11-18
forum: x86 64-bit Users
---

### Post by Lobais on 2008-11-18
Hi,
I've been using 64bit Ubuntu for a while, but I've come to think, that I might not actually need it, and it just makes using homebank and stuff harder.

Now I wanted to upgrade from 8.4 to 8.10, and I thought if it was possible to upgrade using the 32bit cd's, and in that way "downgrade" my architecture?

Thanks, Thomas

---

### Post by clhsharky on 2008-11-18
8,10 64 bit is better for me.
Open Jdk Java works with all sites I have used, and 64 bit flash alfa. now out, Works good to. 64 bit is getting better!

---

### Post by jespdj on 2008-11-18
Just like there is no way to upgrade from 32-bit to 64-bit, there is no way to downgrade from 64-bit to 32-bit. You'll have to reinstall.

---

### Post by dcstar on 2008-11-19
> **Lobais said:**
> 
........
Now I wanted to upgrade from 8.4 to 8.10, and I thought if it was possible to upgrade using the 32bit cd's, and in that way "downgrade" my architecture?


Simply create a separate /home partition (search for instructions), then install the 32 bit version of 8.10 using that partition (either overwriting the existing install or in spare space).

All your user files and settings will be preserved.

---

### Post by steveneddy on 2008-11-19
I can't think of any reason why anyone would actually want to use 32 bit with a 64 bit machine, but a total re-install will be in order if you were needing to go 32.

---

### Post by crazyness003 on 2008-11-19
> **steveneddy said:**
> I can't think of any reason why anyone would actually want to use 32 bit with a 64 bit machine, but a total re-install will be in order if you were needing to go 32.

+1

If you are 100% sure you wanna do this, reinstall is the only way. But why? 8.10 makes 64 bit-ing OVER9000 easier, and its all 64bitty!

Seriously, you use the 100% potential of your 64 bit architecture.

---

### Post by steveneddy on 2008-11-20
I also might add that since the alpha version of the 64 bit Flash out now, it just gets easier.

The new Flash 64 bit is truly amazing.

Just drop the .so in the folder and now Flash works like it should.

Of course you have to uninstall all of the nswrapper stuff you did before to get 32 bit Flash to work.

---

### Post by mikewhatever on 2008-11-20
> **steveneddy said:**
> I can't think of any reason why anyone would actually want to use 32 bit with a 64 bit machine, but a total re-install will be in order if you were needing to go 32.

Nspluginwrapper is a good reason for me.:)

---

### Post by crazyness003 on 2008-11-22
> **mikewhatever said:**
> Nspluginwrapper is a good reason for me.:)

no need for that anymore. 
yay adobe! finally doing the right thing.

---

### Post by duanedesign on 2008-11-22
Adobe actually released the 64 bit version of flash player for Linux first. It is nice to get something first for a change. here is a link with more info.

[http://www.desktoplinux.com/news/NS5620144233.html](http://www.desktoplinux.com/news/NS5620144233.html)

---

### Post by mikewhatever on 2008-11-22
> **crazyness003 said:**
> no need for that anymore. 
yay adobe! finally doing the right thing.


> **duanedesign said:**
> Adobe actually released the 64 bit version of flash player for Linux first. It is nice to get something first for a change. here is a link with more info.

[http://www.desktoplinux.com/news/NS5620144233.html](http://www.desktoplinux.com/news/NS5620144233.html)

It looks like you guys have reading comprehension problem. Just read the word in red, and no hard feelings. 

> Adobe has released a 64-bit [SIZE="4"][COLOR="Red"]alpha[/COLOR][/SIZE] Linux version of its Flash Player 10

---

### Post by Sef on 2008-11-22
>  			 				Adobe has released a 64-bit [SIZE=4][COLOR=Red]alpha[/COLOR][/SIZE] Linux version of its Flash Player 10 			 		

True, but from what I have read, it is very good and not at all like typical alpha software.

---

### Post by crazyness003 on 2008-11-22
> **mikewhatever said:**
> It looks like you guys have reading comprehension problem. Just read the word in red, and no hard feelings.
its OVER9000 times better than the final release they had for flash 9.x 32bit, so yeah, it be an alpha...but a very successful alpha that pwns nspluginwrapper (hence the "no need for that anymore" part). And, no. there was no lack of comprehension. we all meant what we said. its cool tho.

'here, here' for adobe!

---

### Post by Spr0k3t on 2008-11-23
The 64bit alpha has been more stable on my system than the 32bit w/nspluginwrapper every was.  I can have multiple tabs open with multiple streams running and I have yet to make it crash.  The only problem I've found so far is with fullscreen, it's a little sluggish but then it's alpha.  I don't use a webcam or microphone with flash so it's damn near perfect.  The only reason I remotely have for using 32bit is the LogMeIn plugin software.  I'm sure the crew at LogMeIn will eventually finish the alpha plugin and pair it up with a 64bit release as well.

---

### Post by Kilz on 2008-11-23
Those that want to compare the flash **[COLOR="Red"]ALPHA[/COLOR]** with sliced bread I will give you something to think on.


When someone cant get it to run, you help them. Dont just tell them it works for you. Make it work for them, without issues. Because what it looks lik you are doing is lieing to them if they cant run it like you are. After all its more than an alpha to you. To me, I would tell them its an alpha and point them to adobes place for bugs when it isnt working.

By not pointing out its an alpha and in need of work you are going to have people who cant troubleshoot trying to fix something. Odds are they will break more and not even solve the issue. There will be an endless stream of "does anyone have any ideas" posts. When no one has a clue.

Lastly, even if you do solve a lot of little issues and people are running, you may make the final plugin awful. After all the people who you just helped are 99% of the time not going to file bug reports. Adobe will never fix the issues, and you better be ready to help the next 10,000 clueless newbies.

---

### Post by crazyness003 on 2008-11-23
> **Kilz said:**
> Those that want to compare the flash **[COLOR="Red"]ALPHA[/COLOR]** with sliced bread I will give you something to think on.


When someone cant get it to run, you help them. Dont just tell them it works for you. Make it work for them, without issues. Because what it looks lik you are doing is lieing to them if they cant run it like you are. After all its more than an alpha to you. To me, I would tell them its an alpha and point them to adobes place for bugs when it isnt working.

By not pointing out its an alpha and in need of work you are going to have people who cant troubleshoot trying to fix something. Odds are they will break more and not even solve the issue. There will be an endless stream of "does anyone have any ideas" posts. When no one has a clue.

Lastly, even if you do solve a lot of little issues and people are running, you may make the final plugin awful. After all the people who you just helped are 99% of the time not going to file bug reports. Adobe will never fix the issues, and you better be ready to help the next 10,000 clueless newbies.
+1 you have a point.

My apologies.

To get Flash 10 ALPHA running, i used the repos. Its the latest one. Search for 'flashplugin-nonfree' and lo. Version '10.0.12.36ubuntu1' will greet you for downloading and installing.

You can lso download from Adobe Labs as a TAR.GZ from here
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Go here to report bugs, request features you like (login is required, i think)
[http://bugs.adobe.com/flashplayer/](http://bugs.adobe.com/flashplayer/)

They also have a discussion forum here
[http://www.adobe.com/cfusion/webforums/forum/categories.cfm?forumid=72&catid=675](http://www.adobe.com/cfusion/webforums/forum/categories.cfm?forumid=72&catid=675)

All this info was taken from here (check this out)
[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

There you go. Flash 10 alpha on 64bit Linux

---

### Post by Yellow Pasque on 2008-11-23
> **Kilz said:**
> Because what it looks like you are doing is lying to them if they can't run it like you are.
...says the man who leads people to believe that running 64-bit is literally twice as fast as 32-bit.

> By not pointing out its an alpha and in need of work you are going to have people who can't troubleshoot trying to fix something.
I don't believe that small samples of user experience are often helpful, but I've seen many, many reports of users who prefer the native 64-bit "Alpha" over the "final/stable" 32-bit version of Flash10 running with the "stable" nspluginwrapper (1.1.2), enough to believe we may be on to something here. In fact, I don't recall reading many user accounts of Flash 10/nspluginwrapper working correctly as installed from the repo.

About the only thing users can troubleshoot with Flash is the way it's installed. Once it's installed and running correctly, any errors will be from non-working code. Of course, Flash is closed source, so the only choice comes down to reporting it to Adobe or not. If the user doesn't report it after being directed to the proper resource, he/she obviously doesn't care enough.

> After all the people who you just helped are 99% of the time not going to file bug reports.
Then that's their problem. As long as we point them in the proper direction, we've done our job. "You can lead a horse to water, but you can't make it drink."

> There will be an endless stream of "does anyone have any ideas" posts.How long is your stickied Flash thread again? (i.e. this is a bit unavoidable in a forum where the helpee/helper ratio is so high).

---

### Post by clhsharky on 2008-11-23
Thomas

   When I read your post (OP) and have gone through the same, I was trying to offer a little bit of hope. I can't do quick-fixes any more.

   I don't post much but read a lot, and have used Ubuntu since 7.04 thanks to this forum and Ubuntu.


   Good Luck :


                                   Charley

 [/LEFT]

---

### Post by Kilz on 2008-11-24
> **Temüjin said:**
> 
Then that's their problem. As long as we point them in the proper direction, we've done our job. "You can lead a horse to water, but you can't make it drink."

How long is your stickied Flash thread again? (i.e. this is a bit unavoidable in a forum where the helpee/helper ratio is so high).

No, imho what should be the normal course of events on an ALPHA is that people file bug reports. The code is then fixed. 
But I have noticed something over time. When anyone helps "fix" something 99% of the time  bug reports go unfilled. They consider the problem solved. Possibility because a lot of users think this forum is a way to let the developers know their opinions. (O how wrong this is in reality) 
So the code is never fixed for that issue. Why do you think the problems happen still with packages in the repository? Are we really helping anyone , because when its not reported, its never fixed. There ends up being an never ending series of posts on the same issue, its a giant rat race. 

The post of mine that is sticky, wasnt placed there by me, and was near the top of the page most of the time anyway. But you will find the alpha is listed, with warnings, and a link to the Adobe bug reports. You will notice all over it links to file bug reports. The focus is also off of scripts that magically solve issues and more on commands you should do.

I see my "job" here is to help new users, but are we really helping them if every one of them has to do some work around because the bugs are not reported?

---

