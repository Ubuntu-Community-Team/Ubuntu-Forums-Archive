---
title: "Please help reverse engineer this Windows freak..."
date: 2007-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by capecove on 2007-06-06
Okay, another potentially stupid question. 

So, why is it that some folks are still using Dapper and Edgy? In Windows land we are always instructed to march to the beat of the Bill Gates drummer and UPGRADE. In fact, we are punished for not upgrading, conforming as the brainwashing machine has instructed. *NO! Please don't hook that thing up to my head anymore!*

I am, having just installed my first Ubuntu release last Friday, running Feisty. I can imagine a better familiarity with the issues of past releases, since they have been around for a longer period of time. But, do you folks on the older releases lose any functionality? If not, what is to be gained by upgrading?

:)

---

### Post by Lord Illidan on 2007-06-06
There is a nice quote :

If it ain't broken don't fix it.

Some people still run MS-DOS. It isn't broken for them, they don't need any new functionality..it gives them all they need, same issue here. I upgrade because I like the thrill!

---

### Post by Kilz on 2007-06-06
> **capecove said:**
> Okay, another potentially stupid question. 

So, why is it that some folks are still using Dapper and Edgy? In Windows land we are always instructed to march to the beat of the Bill Gates drummer and UPGRADE. In fact, we are punished for not upgrading, conforming as the brainwashing machine has instructed. *NO! Please don't hook that thing up to my head anymore!*

I am, having just installed my first Ubuntu release last Friday, running Feisty. I can imagine a better familiarity with the issues of past releases, since they have been around for a longer period of time. But, do you folks on the older releases lose any functionality? If not, what is to be gained by upgrading?

:)

I run Dapper Drake. Not only on my Desktop , but also on my server. Why?
1. There is support untill 2009!!!
2. Its still being secure.
3. There is no reason to upgrade. Dapper dose all I need it to. The releases after that dont offer any more functionality that I need.
4. Its stable as can be! A lot of the small bugs that happen to every release were patched long ago.
5. I know it like an old friend.

One thing I learned long ago when dealing with linux is that a release is not always the most stable. Software is released and the community helps find the bugs and reports them to be fixed. 
So getting the just released version tends to be an exercise in frustration. When I do upgrade it wont be for at least a month after a release.
I will probably hold off untill the the next long term support version to upgrade. That way I will have a long time to use it without the constant update and install cycle. You also have the situation that some software isnt released for a version until a after the os release. I know I will on the server. I have no need to mess whith what works. If it isnt broke, dont fix it. If some needed feature comes out for the desktop, maybe ill upgrade it sooner.
But think about this. Dapper was released in June of 06. Its only a year old. Dont think I havent tested Edgy and Feisty. I have them as virtual machines.

I forgot one of the most important reasons, All the time I spent getting the desktop and menus like I want the. Take a look at the screenshot.

---

### Post by jrocket on 2007-06-06
> **Kilz said:**
> I forgot one of the most important reasons, All the time I spent getting the desktop and menus like I want the. Take a look at the screenshot.

Cool screenshot, and I mean no offense by this, since your posts have helped me a lot in the past.  However, it really wouldn't take long to go from a default setup to what you have there, as far as the screenshot shows.  Set the panels to full transparency, install your clock and monitor apps, set the wallpaper and you're good to go.

---

### Post by Kilz on 2007-06-07
> **jrocket said:**
> Cool screenshot, and I mean no offense by this, since your posts have helped me a lot in the past.  However, it really wouldn't take long to go from a default setup to what you have there, as far as the screenshot shows.  Set the panels to full transparency, install your clock and monitor apps, set the wallpaper and you're good to go.

Plus
1. Add the launchers for my favorite programs.
2. remove menu bar and put in drop down menu.
3. Change the desktop background for when its booting up
4. Configure all the desklets in one form or another
5. Change the color in the background of Nautilus. (to match the gold everyware else)
6. Change the colors in the terminal (got to have gold text and a black background)
7. Install the login screen to match the wallpaper.
8. Hack my favorite Silver cursor into place. (I like things to sparkle and shine)
9. Replace the icons
10. Replace the desktop switcher with 3ddesk

Also if I am putting in a new install
1. Replace the dozen or so symlinks to my /files partition to the Media folder on the desktop and my home folder
2. Reinstall Neverwinter , Descent rebirth 1 and 2 and quake 2 to linux.
3. Reinstall 7 games after Cedega
4. Add in 10-20 small programs that are in the repos that dont get installed normally 
5. Reinstall vmware and appliances
6. Reinstall nfs and configure it to automount shares.
7. Edit Fstab to mount extra partitions for media and other files

Im not going to even think about what needs to be done if I were to reinstall my server os.

Maybe it would be worth all the work if there was a killer application or another good reason to replace Dapper. But its only a year old. I would rather have fun and play some games or surf the net.  :D

---

### Post by RelativelyQuantum on 2007-06-07
How would one get that clock app? I've seen it a few times, and I like it. Are there others like it?

---

### Post by Kilz on 2007-06-07
> **RelativelyQuantum said:**
> How would one get that clock app? I've seen it a few times, and I like it. Are there others like it?

The clock is a desklet, part of gdesklets. The monitors are also desklets. The packages are in the repos.

---

### Post by tgalati4 on 2007-06-07
If you compile any of your own programs or if you compile some packages from scratch, you will have to recompile them by going to a new kernel.  If you have a lot of packages and a lot of customization, then going from Dapper to Edgy or Feisty can be a pain.  If you have customized your desktop for the past year and you have gotten 165 days of continuous uptime, you tend to be shy about upgrading.

The latest kernels appear to be geared toward supporting new hardware--dual-core processors, mega-SATA drives, new RAID configurations, etc.  If you are running 5-year-old hardware (P4 2.8 GHz) then the new kernels (from the past year) are not going to give you increased functionality.

Finally, Linux is all about the packages.  I have yet to find a Linux application that will not run on Dapper but will run on Feisty--requiring an upgrade to run that particular package.  Windows and Mac OS X are full of examples of programs that simply will not run on previous versions of the OS.

Want parental conrol in Safari?  You must upgrade to Tiger (10.4.X) because the version of Safari in 10.3.9 doesn't support parental control.  But if you have a 5-year old G3 machine, then it won't take Tiger if it is missing firewire ports.  

The corporate world has done a fine job of planned obsolesence.  Have you ever had a printer stop printing in black and white when the color cartridge was out of ink?  Or the cartridge was expired even though you just installed it, or the ink counter says it's empty, but you can shake the cartridge and hear the ink splashing around?

Linux is about taking the computer back and making it do what you want it to do.  If Dapper is doing the job then who's forcing me to upgrade to Feisty?

---

### Post by capecove on 2007-06-07
[I]
Linux is about taking the computer back and making it do what you want it to do. If Dapper is doing the job then who's forcing me to upgrade to Feisty?[/I]

What an exciting concept. Actually making the computer fit the user, not making the user fit the computer. I think I understand now and am glad that I asked. I am looking forward to eeking out another 6-7 years out of this hardware (if possible). I am pretty frugal. LOL... :D

---

### Post by PatrickMay16 on 2007-06-07
I would still be with hoary, if not for the fact that some packages I need were not made available. Right now I've been with dapper for about a year. It works great, and does all I need it to do. No need to upgrade for me.
Plus, the newer versions of ubuntu seem bloated compared to dapper.

I'm also reluctant to update because I'm worried about hosing my system. I installed that system in September 2005 with hoary and upgraded to Breezy and then Dapper (without reinstalling). I would not like mess it up and have to rebuild it all over again, because I might never get it quite how it used to be.

---

### Post by lazyart on 2007-06-07
I was thinking some time ago about the stark difference between Windows & Ubuntu.  Consider the 3-4 year development cycle vs. six months.  I started with Dapper right before Edgy was release and held onto for quite a while because I was new to Linux and needed all the support I could get.  I've gone to Edgy and then Feisty, then moved everything to a new box (reinstall) and finally from 32 to 64 bit (cough reinstall).

There's a pretty good chance that I will skip on Gutsy, especially if I've gotten Flash running before then (I know, but I just need to sit down and do it).

By the same token I haven't been burned by an upgrade.  I've learned the importance of a /home partition.  I'm still working on reinstalling my stuff and that does take a while to do.

---

### Post by Kilz on 2007-06-07
> **lazyart said:**
> I was thinking some time ago about the stark difference between Windows & Ubuntu.  Consider the 3-4 year development cycle vs. six months.  I started with Dapper right before Edgy was release and held onto for quite a while because I was new to Linux and needed all the support I could get.  I've gone to Edgy and then Feisty, then moved everything to a new box (reinstall) and finally from 32 to 64 bit (cough reinstall).

There's a pretty good chance that I will skip on Gutsy, especially if I've gotten Flash running before then (I know, but I just need to sit down and do it).

By the same token I haven't been burned by an upgrade.  I've learned the importance of a /home partition.  I'm still working on reinstalling my stuff and that does take a while to do.

[Here is the flash solution ]("http://ubuntuforums.org/showthread.php?t=425672") 10 seconds and you have flash on your 64bit browser.

---

### Post by No Whammies on 2007-06-10
Quoted for truth.  Seriously, there's no reason for me to use a non-LTS release.  On my old computer, I upgraded to Edgy, but didn't see much of a difference.  It ran about the same speed, ran all the same programs and was a positive experience just like Dapper.

When I got my new computer, I tried feisty, but unfortunately the install didn't work.  I took my old DVD of Dapper, fired it up and here I am a couple of weeks later with a stable system and current versions of all my software (had to read up a bit to compile/find them, but it was worth the 90 minutes to hook my system up right.).  I won't be upgrading at all unless it's an LTS, and even then, not until 2 or 3 months after it's made available, to avoid the rush to download.

Now, a question, is it going to be possible to go from LTS to LTS for an upgrade, or will a reinstall be mandatory?

> **Kilz said:**
> Plus
1. Add the launchers for my favorite programs.
2. remove menu bar and put in drop down menu.
3. Change the desktop background for when its booting up
4. Configure all the desklets in one form or another
5. Change the color in the background of Nautilus. (to match the gold everyware else)
6. Change the colors in the terminal (got to have gold text and a black background)
7. Install the login screen to match the wallpaper.
8. Hack my favorite Silver cursor into place. (I like things to sparkle and shine)
9. Replace the icons
10. Replace the desktop switcher with 3ddesk

Also if I am putting in a new install
1. Replace the dozen or so symlinks to my /files partition to the Media folder on the desktop and my home folder
2. Reinstall Neverwinter , Descent rebirth 1 and 2 and quake 2 to linux.
3. Reinstall 7 games after Cedega
4. Add in 10-20 small programs that are in the repos that dont get installed normally 
5. Reinstall vmware and appliances
6. Reinstall nfs and configure it to automount shares.
7. Edit Fstab to mount extra partitions for media and other files

Im not going to even think about what needs to be done if I were to reinstall my server os.

Maybe it would be worth all the work if there was a killer application or another good reason to replace Dapper. But its only a year old. I would rather have fun and play some games or surf the net.  :D

---

### Post by Kilz on 2007-06-10
> **No Whammies said:**
> Quoted for truth.  Seriously, there's no reason for me to use a non-LTS release.  On my old computer, I upgraded to Edgy, but didn't see much of a difference.  It ran about the same speed, ran all the same programs and was a positive experience just like Dapper.

When I got my new computer, I tried feisty, but unfortunately the install didn't work.  I took my old DVD of Dapper, fired it up and here I am a couple of weeks later with a stable system and current versions of all my software (had to read up a bit to compile/find them, but it was worth the 90 minutes to hook my system up right.).  I won't be upgrading at all unless it's an LTS, and even then, not until 2 or 3 months after it's made available, to avoid the rush to download.

Now, a question, is it going to be possible to go from LTS to LTS for an upgrade, or will a reinstall be mandatory?

I remember reading someplace (but I cant remember where) that it is in the plans for the next  LTS. But, with 4 or 6 versions between it and Dapper. I know Im going to do a clean install. I think the time invested in setting up will be far more enjoyable than the same amount of time hunting down problems because of files I have added.

---

### Post by kevinlyfellow on 2007-06-10
> **Lord Illidan said:**
> There is a nice quote :

If it ain't broken don't fix it.

Some people still run MS-DOS. It isn't broken for them, they don't need any new functionality..it gives them all they need, same issue here. I upgrade because I like the thrill!

I ran win95 until 03.  But I upgrade Ubuntu every chance I get!  Linux is much more exciting than windows ever was.

---

### Post by Kilz on 2007-06-10
> **kevinlyfellow said:**
> I ran win95 until 03.  But I upgrade Ubuntu every chance I get!  Linux is much more exciting than windows ever was.

Exactly what features did you get, that you use, in the last version upgrade?

---

### Post by kevinlyfellow on 2007-06-10
> **Kilz said:**
> Exactly what features did you get, that you use, in the last version upgrade?

Well, in feisty, my computer stopped crashing as often (a big plus) and gave me compiz without having to install anything extra (I could have done compiz in edgy, yes, but I was using beryl and didn't consider compiz).  Rhythmbox plugins came about (hooray!).  I'm not sure if it was in edgy, but I'm using the integrated python console in gedit along with the file browser side bar.  I play Suduku every once and a while, as well as the new version of frozen-bubble (with online games, too bad no one is ever on).  gstreamer on feisty is awesome, I'm using totem to play much more movies now (and also I installed my media codecs using the new automatic codec installation feature, very cool)!!!  The theme editor now has support of changing colours in some themes, which I use.  Network printer support for feisty is very nice and allowed me to find and configure the printer in my office in no time at all (couldn't do it in edgy).  

I use plenty of feisty specific features.

Edit: I also use apt-get autoremove feature and gnome-terminal lets me autofill in a lot more places than before (like in apt or man or just about anything).

Edit Again:  I also see your using dapper.  I move from dapper to edgy for 3d desktop.

---

### Post by djchandler on 2007-06-10
> **Kilz said:**
> Exactly what features did you get, that you use, in the last version upgrade?

I'm getting administrative application windows (as gksu) that freeze. I'm OK as sudo in the terminal, but that's not necessarily a plus in my book. I'm rebuilding the hardware that I run Ubuntu on soon, different motherboard, cpu and way bigger hdd. I may go back to Dapper after the rebuild.  I didn't have the freeze problem before Feisty, and I only upgraded to Edgy so I could install Feisty. I wanted to see if it was worth the trouble after Dell made the deal with Canonical to sell boxes with Feisty installed. So far, I'd say it's not been all that positive for me.

That's probably not the answer you were looking for, Kilz, but I see you are still on Dapper. If it's good enough for you, it probably is for me as well. Feisty seemed a little faster, but I think the hardware upgrade I'm working on is a better way to go to get the speed I really want.

---

### Post by Kilz on 2007-06-11
> **kevinlyfellow said:**
> Well, in feisty, my computer stopped crashing as often (a big plus) and gave me compiz without having to install anything extra (I could have done compiz in edgy, yes, but I was using beryl and didn't consider compiz).  Rhythmbox plugins came about (hooray!).  I'm not sure if it was in edgy, but I'm using the integrated python console in gedit along with the file browser side bar.  I play Suduku every once and a while, as well as the new version of frozen-bubble (with online games, too bad no one is ever on).  gstreamer on feisty is awesome, I'm using totem to play much more movies now (and also I installed my media codecs using the new automatic codec installation feature, very cool)!!!  The theme editor now has support of changing colours in some themes, which I use.  Network printer support for feisty is very nice and allowed me to find and configure the printer in my office in no time at all (couldn't do it in edgy).  

I use plenty of feisty specific features.

Edit: I also use apt-get autoremove feature and gnome-terminal lets me autofill in a lot more places than before (like in apt or man or just about anything).

Edit Again:  I also see your using dapper.  I move from dapper to edgy for 3d desktop.

I see you like eye candy. Did you have a problem playing movies? Did you have all your codecs installed on Edgy?


> **djchandler said:**
> I'm getting administrative application windows (as gksu) that freeze. I'm OK as sudo in the terminal, but that's not necessarily a plus in my book. I'm rebuilding the hardware that I run Ubuntu on soon, different motherboard, cpu and way bigger hdd. I may go back to Dapper after the rebuild.  I didn't have the freeze problem before Feisty, and I only upgraded to Edgy so I could install Feisty. I wanted to see if it was worth the trouble after Dell made the deal with Canonical to sell boxes with Feisty installed. So far, I'd say it's not been all that positive for me.

**That's probably not the answer you were looking for,** Kilz, but I see you are still on Dapper. If it's good enough for you, it probably is for me as well. Feisty seemed a little faster, but I think the hardware upgrade I'm working on is a better way to go to get the speed I really want.

Actually, it was an answer I was looking for. When I ask what features, Im more interested in applications than eye candy.  Dont get me wrong, some people like it. The auto this and auto that are nice for new users.
 But IMHO a lot of Ubuntu users have "newitis". They must have it because its shiny and new. They look to be trapped in a never ending update cycle, always looking for that next update "fix". Its like an addiction.
Personally I could care less about wobbly transparent windows. Been there , done that on SuSE. Turned XGL off a day after I turned it on. It doesnt add anything to me.
I have all media formats playing fine. I took a look at Edgy and Feisty as virtual machines. I didnt see any "must have" applications that are missing from Dapper.  At least none that I couldnt compile and install if I really wanted them. After all its only been a year since Dapper was released.

---

### Post by kevinlyfellow on 2007-06-11
> **Kilz said:**
> I see you like eye candy. Did you have a problem playing movies? Did you have all your codecs installed on Edgy?


I've been using xine since 02, and I know how to deal with xine codecs.  The madness that was gstreamer codecs (gstreamer-old,new,good,bad,ugly,night,day ok, fine I'm exaggerating) just made it a hassle to manage.  xine was easy and its codecs seemed to work better.  But gstreamer has seemed to improve its codecs (sometimes it performs better than the xine codecs now) and I don't need to worry about which sets to install since its automated.  It's not that I don't know how, I just don't want to deal with those types of things on my primary computer which I just want to work smoothly.

And yes, desktop eyecandy is nice... but actually, I'm just horribly curious and I got hooked.  For whatever reason wobbly windows seems much more natural to me.  Besides, its always cool when people take notice at how nice a linux desktop looks.

> **Kilz said:**
> 
Actually, it was an answer I was looking for. When I ask what features, Im more interested in applications than eye candy.  Dont get me wrong, some people like it. The auto this and auto that are nice for new users.
 But IMHO a lot of Ubuntu users have "newitis". They must have it because its shiny and new. They look to be trapped in a never ending update cycle, always looking for that next update "fix". Its like an addiction.
Personally I could care less about wobbly transparent windows. Been there , done that on SuSE. Turned XGL off a day after I turned it on. It doesnt add anything to me.

I'm really curious and excited as to where linux is headed towards.  You know, I always used to hate updating things, but what is coming out for linux is really exciting.  My desire to upgrade has nothing to do with being unsatisfied with the previous version.  My desire to upgrade has to do with seeing what is new (and in the linux world, better).  If I really wanted to, I could just do a debian base install and install the bare minimum.  If I was interested in sticking with the same thing for a long time, I'd undoubtedly be using debian and not ubuntu.  But that's not why I'm here and I'm not new linux.  You obviously don't care about linux doing cool tricks, but a lot of us do.  I don't understand why people being excited by new software technologies bothers you, but we aren't likely to go away anytime soon.  Better get used to it.

> **Kilz said:**
> 
I didnt see any "must have" applications that are missing from Dapper.  At least none that I couldnt compile and install if I really wanted them. After all its only been a year since Dapper was released.

So what exactly did you ask the question for?  You want specific applications that are available for feisty that cannot be compiled for dapper?  That seems like a rhetorical question since you should be able to compile most applications on dapper's kernel (so long as you spend the time to resolve the dependencies).  I'd wager you could have the latest gnome if you wanted to.  But I'm not interested in doing all that work, because I can just do a dist-upgrade and not have to compile anything.  

I think that feisty is a lot nicer than dapper, but it admittedly is only marginally more functional for most people.  I'm not asking you to upgrade.  If your satisfied with the status quo, then stick with it.  My enthusiasm and curiosity for linux is not a bad thing, and I don't see why you frown on this.  I admit that upgrading every six to eighteen months is not for everyone, which is why I'm glad that there are LTS releases.  Likewise, sticking with the LTS is not for everyone.

---

