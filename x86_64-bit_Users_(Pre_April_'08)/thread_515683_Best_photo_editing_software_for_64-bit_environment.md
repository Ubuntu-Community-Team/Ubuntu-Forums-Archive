---
title: "Best photo editing software for 64-bit environment?"
date: 2007-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Midahed on 2007-08-02
Can any of you 64-bit users recommend a photo editing package that will run on Ubuntu 7.04 Feisty 64-bit?

I'm looking for something that does 'quick and easy' photo retouching at a fairly simple level, and was originally drawn to LightZone, but having looked into it a bit further it appears that LightZone requires a 32-bit environment. :(

I'm sure that Gimp could do a lot of what I want, but I'd prefer something that's easier to use.

I still use Windows occasionally (running under VMware Server), and could do my photo editing in Windows, but I'm really trying to make the switch to Linux as far as I can...

Any suggestions?

Thanks,

Mike

---

### Post by dabl on 2007-08-02
gimp is probably the answer.  I find it comparable to PaintShop Pro that I used to use in Windows, in ease of use (i.e. not terribly easy).  But if you are like me, there only 3 or 4 things that you routinely need to do, so you just figure out how to do those things and leave the other 27,000 things that it can do unlearned.  :)

---

### Post by rsambuca on 2007-08-02
I second that.  Learn to use the gimp for your quick retouches and you can learn new stuff as you need it.  There are many tutorial pages for helping with red-eye, fixing blemishes,etc.  A good start is something like the [[COLOR="Red"]tutorials on this site[/COLOR]]("http://www.gimpguru.org/Tutorials/").  They are well written and easy to follow.

If you require further help with using gimp, you can post a question in the "Art & Design" section of these forums and I am sure you will get help.  If you want to see a few examples of some quick touch-ups I have done using gimp, look [[COLOR="Red"]here[/COLOR]]("http://www.members.shaw.ca/northcottwedding/photoediting.html").

---

### Post by Midahed on 2007-08-02
Thanks both!

rsambuca (Richie?) - your photo editing demo was interesting. To be honest I've never really bothered to apply that level of enhancement to my photos, but I guess it's worthwhile if you have an otherwise good photo that's spoilt by closed eyes or whatever.  

I tried Paintshop Pro when I was a Windows user and found all that graphics-related techie speak (layers, masks, alpha and gamma, etc) very off-putting.  All I wanted at that time was the ability to remove red-eye and correct over or under exposure, and I never did really get to grips with Paintshop Pro.  But OK, you've convinced me - I guess I have to give gimp a try.

Mike

---

### Post by stmiller on 2007-08-02
[Digikam]("http://www.digikam.org/")

Has incredible plugins, support for 16bit RAW camera data, and tons of other stuff. It's in the apt-get repos.

Or Picasa.

I would not recommend GIMP as it does not handle the ICC profiles from photos, and can only do 8bit images/math.

---

### Post by dabl on 2007-08-02
Digikam is fine for JUST photos, and no other graphics work.  :)

---

### Post by rsambuca on 2007-08-02
> **stmiller said:**
> [Digikam]("http://www.digikam.org/")

Has incredible plugins, support for 16bit RAW camera data, and tons of other stuff. It's in the apt-get repos.

Or Picasa.

I would not recommend GIMP as it does not handle the ICC profiles from photos, and can only do 8bit images/math.

Certainly both of those will do the trick!  However, I have been a gnome user for a while and thus tend to go with gimp over digiKam as I have avoided mixing libraries on my current rig.  Picasa isn't opensource either, so if there is a decent opensource alternative, I'll usually take it.

ICC profiles, RAW, etc, are not really a concern for the most users.

That is the great thing about the linux world - many great choices.  Toughest thing is to find time to try them all!

---

### Post by Midahed on 2007-08-02
Agreed.  Digikam looks very good but, like rsambuca, I'm a Gnome user and really don't want to mix libraries, especially just for one application.  I'd consider Picasa, but that's effectively running under Wine as far as I'm aware...

Mike

---

### Post by Kilz on 2007-08-02
You could also try cinepaint (in the repo's), which is based on the gimp. But is designed more for photo work.

---

### Post by stmiller on 2007-08-02
> **Midahed said:**
> Agreed.  Digikam looks very good but, like rsambuca, I'm a Gnome user and really don't want to mix libraries, 


It does not slow your computer down at all to use different KDE or Gnome apps. Not sure what you are talking about when you say 'mixing libraries.' 
You are missing out on K3B, Amarok, Ktorrent and other major Linux apps...

---

### Post by rsambuca on 2007-08-02
> **stmiller said:**
> It does not slow your computer down at all to use different KDE or Gnome apps. Not sure what you are talking about when you say 'mixing libraries.' 
You are missing out on K3B, Amarok, Ktorrent and other major Linux apps...

Those are some good apps for sure, but I have found gtk based apps that will do what I want.

As far as the mixed libraries go, it certainly CAN slow your computer down (depending on how much memory you have), as well as take up more hard drive space.  Also, there is the different look of those apps!  To each his own.

---

### Post by stmiller on 2007-08-03
Wow gtk purists. Very interesting. We need a new subforum. :)

---

### Post by rsambuca on 2007-08-03
> **stmiller said:**
> Wow gtk purists. Very interesting. We need a new subforum. :)

Yeah, LOL :-?

Actually, I am not a purist by any means.  Just trying something different for a change.  I also have a couple of KDE distros going on my rig, although I seem to end up in ubuntu for the most part.

---

### Post by Midahed on 2007-08-03
Is it common practice to mix KDE and Gnome environments, then?  I'm not a Gnome purist - I chose it over KDE on the flip of a coin.  I'd just assumed it would not be a good idea to have both - presumably having KDE installed as a dependency for Digikam would require all the KDE-related libraries to be loaded into memory as well.  My system is based on an Athlon 64 3700+ with a gig or RAM, so it's not scratching around for resources, but I don't want to adversely affect a system that is running very well at the moment.

Mike

---

### Post by Kilz on 2007-08-03
I run a mixed setup. I like some kde aps like k3band and k9copy. I also wouldt change to kde for all the tea in china. with that setup i dont think you will notice more than a few seconds in slow startup of kde apps.

---

### Post by Midahed on 2007-08-03
> **Kilz said:**
> .....Wiith that setup i dont think you will notice more than a few seconds in slow startup of kde apps.
My old Windows XP system was sooooooooo slow - mainly because it hadn't been re-installed in ages and was suffering the usual Windows registry 'bloat and rot'.  My Ubuntu system is lovely and fast - a 'few seconds' more to load apps is an eternity! ;)

Mike

---

### Post by rsambuca on 2007-08-03
> **Midahed said:**
> Is it common practice to mix KDE and Gnome environments, then?  I'm not a Gnome purist - I chose it over KDE on the flip of a coin.  I'd just assumed it would not be a good idea to have both - presumably having KDE installed as a dependency for Digikam would require all the KDE-related libraries to be loaded into memory as well.  My system is based on an Athlon 64 3700+ with a gig or RAM, so it's not scratching around for resources, but I don't want to adversely affect a system that is running very well at the moment.

Mike

Most people nowadays run both KDE and Gnome apps on their systems.  With your rig, you probably won't notice much difference at all.

---

### Post by Midahed on 2007-08-03
> **rsambuca said:**
> Most people nowadays run both KDE and Gnome apps on their systems.  With your rig, you probably won't notice much difference at all.
Thanks!  I've read quite a few threads on the subjects of 'Gnome v KDE' and the problems/advantages of running both environments.  It seems that quite a few people elect to run Gnome and KDE so that they have the pick of the best apps from both camps.  Maybe I'll give Digikam a try - it does seem to do everything I want.  I can always dump it again if having all that KDE stuff hits performance too much.

Mike

---

### Post by kuja on 2007-08-03
Also take a look at digikam's sister project, showfoto. 

As per the performance hit on loading apps, it should only hit the first apps startup time, after which the kde & qt libraries will already be in memory and won't need to be reloaded.

---

### Post by hodge24 on 2008-04-21
My apologies for reviving an old thread, but I've found that the latest Beta version of LightZone 3.4 works fantastically on my 64 Bit platform. It's certainly set to become one of my major tools of choice for Digital Darkroom work - it's just unfortunate that there's no commercial version available for Linux yet (the Beta version is available for download, but expires pretty soon).

I've also found UFRaw great for processing my RAW files, and CinePaint is also fantastic for touching up photos. The huge bonus with these is that they're free, and maintained by the community.

---

### Post by Half-Left on 2008-04-21
> **stmiller said:**
> [Digikam]("http://www.digikam.org/")

Has incredible plugins, support for 16bit RAW camera data, and tons of other stuff. It's in the apt-get repos.

Or Picasa.

I would not recommend GIMP as it does not handle the ICC profiles from photos, and can only do 8bit images/math.

GIMP 2.4 does have ICC profile support and extra profiles in the repos in Hardy.

---

### Post by ArtInvent on 2008-04-25
> **hodge24 said:**
> My apologies for reviving an old thread, but I've found that the latest Beta version of LightZone 3.4 works fantastically on my 64 Bit platform. It's certainly set to become one of my major tools of choice for Digital Darkroom work - it's just unfortunate that there's no commercial version available for Linux yet (the Beta version is available for download, but expires pretty soon).

I've also found UFRaw great for processing my RAW files, and CinePaint is also fantastic for touching up photos. The huge bonus with these is that they're free, and maintained by the community.

That's good news about LightZone 3.4 in Ubuntu 64. Now if they would just release a real version. It says it expires in 5 days or so. Ugh. One of the few proprietary software packages I might have to buy. There really is nothing like it for raw processing.

Still debating switching to 64 bit OS, mostly because Cinelerra is supposed to work better/faster that way. But there are still so many iffy things: I use tons of software and hate to part with any of it.

---

### Post by Kilz on 2008-04-25
> **ArtInvent said:**
> That's good news about LightZone 3.4 in Ubuntu 64. Now if they would just release a real version. It says it expires in 5 days or so. Ugh. One of the few proprietary software packages I might have to buy. There really is nothing like it for raw processing.

Still debating switching to 64 bit OS, mostly because Cinelerra is supposed to work better/faster that way. **But there are still so many iffy things: I use tons of software and hate to part with any of it.**

Its been said a lot, that the 64bit repositories contain the exact same number of applications as the 32bit ones. If you have doubts [search for yourself.]("http://packages.ubuntu.com/")

---

