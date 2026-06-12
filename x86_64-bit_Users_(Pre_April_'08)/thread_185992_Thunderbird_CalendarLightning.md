---
title: "Thunderbird Calendar/Lightning"
date: 2006-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by t.n. on 2006-06-01
Did anyone mange to get Thunderbird extensions Calendar or the Lightning running? As 64bit binaries, of course. The website only provides 32bit XPIs and I did not manage to compile it myself (strange linker errors). I would be very grateful for 64bit XPIs...

---

### Post by mike.thorton on 2006-08-16
Hey,

I've got the same problem!

Have you solved it yet? Thanks..

---

### Post by t.n. on 2006-08-18
> **mike.thorton said:**
> Have you solved it yet?

yes, kind of. If you checkout the Mozilla source on the trunk you can compile the Lightning plugin. The exact build instructions are somewhere on the Mozilla page (very hard to find tough, using Google is probably a good idea). The plugin works, but also requires Thunderbird from the trunk, so you cannot use the Thunderbird provided by Ubuntu.

It would be better to use the plugin from the 1.8 branch (which is compatible with the Ubuntu Thunderbird), but I always got build errors on x86_64. The fixes are apparently only in the trunk.

---

### Post by mrpurple on 2007-06-17
did anyone solve it ?

---

### Post by t.n. on 2007-06-17
As I said, building from source works. But there are no premade XPIs available that I know of.

---

### Post by mrpurple on 2007-06-17
ok ... the problem is that im a new linux user ... so maybe i need to get some more practice before do that ....  or You know a guide step by step in how to do that ?

---

### Post by t.n. on 2007-06-17
Unfortunately building the plugin is not trivial. [Here]("http://www.mozilla.org/projects/calendar/lightning/build.html") are the official instructions, but if you are not used to building your own software they will probably not help a lot. The Mozilla build system is not very user friendly.

But some other people with the same problem seem to have started publishing XPIs for x86_64. The [0.3 Release]("http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.3/contrib/lightning-0.3.linux-x86_64-gcc3.xpi") includes an XPI in contrib, and newer versions seem to be available from private papers. You might have to google around a bit.

---

### Post by michael37 on 2007-08-10
Lightning how-to [https://help.ubuntu.com/community/ThunderbirdLightning](https://help.ubuntu.com/community/ThunderbirdLightning) is now live.

Enjoy.

---

### Post by Kilz on 2007-09-24
The latest build of Swiftdove (a optimized build of thunderbird) has lightning installed by default. [http://swiftweasel.sourceforge.net/](http://swiftweasel.sourceforge.net/)

---

### Post by mojoman on 2007-09-25
> **Kilz said:**
> The latest build of Swiftdove (a optimized build of thunderbird) has lightning installed by default. [http://swiftweasel.sourceforge.net/](http://swiftweasel.sourceforge.net/)

How come they decided to do that?


> From swiftweasel's projects homepage:
You may notice some changes :) I am going to be building an email client per a request from Kilz.

:lolflag:

---

### Post by Kilz on 2007-09-25
> **mojoman said:**
> How come they decided to do that?




:lolflag:

I requested the email client. I didnt ask for the lightning.

---

### Post by mojoman on 2007-09-26
> **Kilz said:**
> I requested the email client. I didnt ask for the lightning.

Ok. It's just that sometimes I just get the impression that you're somehow involved in every step forward that is made for us 64-bit users. I'll be trying out the swiftfox any day now.  :smile: 

best regards
/mojoman

---

### Post by Kilz on 2007-09-26
> **mojoman said:**
> Ok. It's just that sometimes I just get the impression that you're somehow involved in every step forward that is made for us 64-bit users. I'll be trying out the swiftfox any day now.  :smile: 

best regards
/mojoman

I look for the best way to help for my ability. I just see that 64bit is the future and since I have a 64bit computer I might as well help. I know there are a lot of others who do the same thing. Its what make Linux and Ubuntu in particular had to beat.
I cant wait until the 64bit version becomes a focus, and 32bit is a sub forum. Then we will really see things happen.

---

### Post by michael37 on 2007-09-29
> **Kilz said:**
> I look for the best way to help for my ability. I just see that 64bit is the future and since I have a 64bit computer I might as well help. I know there are a lot of others who do the same thing. Its what make Linux and Ubuntu in particular had to beat.
I cant wait until the 64bit version becomes a focus, and 32bit is a sub forum. Then we will really see things happen.

We are halfway there.  The 64-bit SwiftDove (Nocona optimized) worked perfectly on my 64-bit Ubuntu Fiesty laptop.

The 32-bit SwiftDove (Athlon XP optimized)  crashes and produces core dumps on my older Ubuntu Fiesty desktop,

---

### Post by Kilz on 2007-09-29
> **michael37 said:**
> We are halfway there.  The 64-bit SwiftDove (Nocona optimized) worked perfectly on my 64-bit Ubuntu Fiesty laptop.

The 32-bit SwiftDove (Athlon XP optimized)  crashes and produces core dumps on my older Ubuntu Fiesty desktop,

Is the 32bit version running on a 32bit Ubuntu install?

---

### Post by Ledah on 2007-09-29
I tried SwiftDove too and I like it. Well, is there a way to change the language? I didn't find one.

---

### Post by michael37 on 2007-09-29
> **Ledah said:**
> I tried SwiftDove too and I like it. Well, is there a way to change the language? I didn't find one.

No, not really.  You need thunderbird (and locale package in your language) for that.  Look at the "repository method" in [https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion).

---

### Post by Kilz on 2007-09-29
> **michael37 said:**
> No, not really.  You need thunderbird (and locale package in your language) for that.  Look at the "repository method" in [https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion).

That is incorrect, [You can go here]("http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.6/linux-i686/xpi/") to get a language pack for Swiftdove 2.0.0.6 and 2.0.0.7. Right click on the xpi file and save as, then use the install button in the Tools >Add-ons window to install it. You will then need to [install this extension]("https://addons.mozilla.org/en-US/thunderbird/addon/1333") to switch the language. Once installed it will be under the Tools menu as Quick Local Switcher.

---

### Post by Ledah on 2007-09-30
Thank you :)

---

### Post by Pitt Stains on 2007-12-05
Anyone looking for the Lightning 0.7 plugin for Mozilla Thunderbird on 64-bit systems can find it here:

[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.7/contrib/linux-x86-64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.7/contrib/linux-x86-64/)

---

### Post by ViRMiN on 2007-12-05
Was going to say that it's in Universe but it's v0.5... must've got it direct from the Mozilla's website...

---

### Post by michael37 on 2007-12-07
> **Pitt Stains said:**
> Anyone looking for the Lightning 0.7 plugin for Mozilla Thunderbird on 64-bit systems can find it here:

[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.7/contrib/linux-x86-64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.7/contrib/linux-x86-64/)

Thank you, updated instructions in the wiki at [https://help.ubuntu.com/community/ThunderbirdLightning](https://help.ubuntu.com/community/ThunderbirdLightning)

Yes, lightning 0.5 with Gutsy is covered there too.

---

### Post by LRT on 2007-12-09
i've posted my problem on another thread, but am not getting much help. i'm trying to install lightning 0.7 on gutsy and thunderbird 2.0.0.6. but the calendar just shows a bunch of colored bars.
i'm not sure if its because of my architecture. how can i tell what architecture i am using? i have a AMD Athlon(tm) 64 Processor 3500+ cpu, does this mean i am using a 64-bit architecture and am therefore running a 64-bit version of ubuntu gutsy? if i am not mistaken, i believe my cpu can run both 32-bit and 64-bit applications and i believe i am running 32-bit ubuntu so i don't think i need to install the 64-bit version of lighnting.
having said that why doesn't lightning 0.7 work for me when i try to install it from the .xpi ???([https://addons.mozilla.org/en-US/thunderbird/addon/2313]("https://addons.mozilla.org/en-US/thunderbird/addon/2313"))

---

### Post by drs305 on 2007-12-09
> **LRT said:**
> i've posted my problem on another thread, but am not getting much help. i'm trying to install lightning 0.7 on gutsy and thunderbird 2.0.0.6. but the calendar just shows a bunch of colored bars.
i'm not sure if its because of my architecture. how can i tell what architecture i am using? i have a AMD Athlon(tm) 64 Processor 3500+ cpu, does this mean i am using a 64-bit architecture and am therefore running a 64-bit version of ubuntu gutsy? if i am not mistaken, i believe my cpu can run both 32-bit and 64-bit applications and i believe i am running 32-bit ubuntu so i don't think i need to install the 64-bit version of lighnting.
having said that why doesn't lightning 0.7 work for me when i try to install it from the .xpi ???([https://addons.mozilla.org/en-US/thunderbird/addon/2313]("https://addons.mozilla.org/en-US/thunderbird/addon/2313"))

64 bit Swiftdove and the new .7 lightning. Doesn't work for me either. Have the same display problems in calendar mode: horizontal lines,my events are gone and I can't change dates or insert new events.

Edit: Just upgraded to the AMD64 Swiftdove 2.0.0.9 and then reinstalled the new Lightning plugin .7 . Both show installed but still not working correctly even after multiple restarts (see above)

Edit 2  Success:  After above, decided to completely uninstall Lightning. When I restarted Swiftdove, not only was Lightning still installed, it was working correctly!  Go figure...

---

### Post by Kilz on 2007-12-09
> **drs305 said:**
> 64 bit Swiftdove and the new .7 lightning. Doesn't work for me either. Have the same display problems in calendar mode: horizontal lines,my events are gone and I can't change dates or insert new events.

Edit: Just upgraded to the AMD64 Swiftdove 2.0.0.9 and then reinstalled the new Lightning plugin .7 . Both show installed but still not working correctly even after multiple restarts (see above)

Edit 2  Success:  After above, decided to completely uninstall Lightning. When I restarted Swiftdove, not only was Lightning still installed, it was working correctly!  Go figure...

Swiftdove has lightning installed by default. It also importts your existing thunderbird setup. Its possible you had conflicting lightning plugins. When you removed the one you installed , the default plugin worked.

---

### Post by drs305 on 2007-12-09
Kilz,

Thanks for the explanation. Makes sense. I see by way of your explanation why things may have gotten messed up once I updated to Swiftdove 2.0.0.9 and then tried the manual Lightning update.

Now I have a question about the problem I, and maybe the OP, had. I saw there was a new version of Lightning (.7). I was running Swiftdove 2.0.0.7 and tried to replace Lightning .7pre with .7 . I downloaded the .xpi and manually installed it. That didn't work and is when I had the problems with Lightning (horizontal lines and event errors).  Should that method have worked? 

Obviously now that I and others are aware there is a 2.0.0.9 version of Swiftdove that incorporates Lightning .7 a separate download wouldn't be necessary.

---

### Post by jsubl2 on 2007-12-11
If you read the download information it points you to the ftp site for other systems. the lightning for thunderbird 64 bit is there.  here is the link

[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.7/contrib/linux-x86-64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.7/contrib/linux-x86-64/)

I use it with the google provider to access my google calendar from home and work on my kubuntu 64 bit.

:-) Jim.

---

### Post by michael37 on 2007-12-11
Troubleshooting for colored bars problem has been on the wiki page that I mentioned in post #22 ([http://ubuntuforums.org/showpost.php?p=3906976&postcount=22](http://ubuntuforums.org/showpost.php?p=3906976&postcount=22)) for a few months by now... it's a wrong architecture of plugin.

---

### Post by gmc on 2007-12-12
> **Pitt Stains said:**
> Anyone looking for the Lightning 0.7 plugin for Mozilla Thunderbird on 64-bit systems can find it here:

[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.7/contrib/linux-x86-64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.7/contrib/linux-x86-64/)


Perfect! Thanks for this tip. I was wondering if there was a 64 bit version.

Gord

---

### Post by shane2peru on 2008-03-29
Hey sorry to dig up an old thread, but this seemed the most appropriate place to post this!  Ok, I have switched back to Thunderbird from Evolution.  So I went straight for SwiftDove, and am very impressed with it.  Then I realized, you can sync your google calendar with the lightning ext!  Wow, that is great for me, just download the extention from here:  [https://addons.mozilla.org/en-US/sunbird/addon/4631](https://addons.mozilla.org/en-US/sunbird/addon/4631)  and then install it!  So I did, and ... it didn't work. :)  Ok, here is what I get:  When I go to addons it shows up there, and then I noticed it says:  > Requires additional items  Sooooo, what additional items could it require?  I'm thinking this is a 64bit missing library or something, because from searching the forums, it seems that 32bit people have this working without a problem.  I can't really confirm that though, just the conclusion I came to. 
     In case you are wondering, I did download and install Thunderbird and the Lightning Extension, then the Google Calendar thing, and well, same results.  Perhaps there is a log somewhere that would tell me what I'm missing?  If anyone has any ideas on this, please let me know.  Thanks!  

Shane

---

### Post by bismark on 2008-03-29
You need the Provider plugin [https://addons.mozilla.org/en-US/thunderbird/addon/4631](https://addons.mozilla.org/en-US/thunderbird/addon/4631) to sync two way with Google Calendar.

Using it right now.

---

### Post by shane2peru on 2008-03-29
> **bismark said:**
> You need the Provider plugin [https://addons.mozilla.org/en-US/thunderbird/addon/4631](https://addons.mozilla.org/en-US/thunderbird/addon/4631) to sync two way with Google Calendar.

Using it right now.

That is what I have.  :confused:   :confused:   :confused:   I downloaded that same file.  I re-downloaded it, and installed it again, and I still have the same issue, it says in the addon part, Requires additional items.  Do you have any other extensions?  Are you using SwiftDove?  Thanks for the help!

Shane

---

### Post by Icebear on 2008-03-30
Hi 

I have lightning working with 64 architecture. If I remember rightly I downloaded lightning at 
[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.7/contrib/linux-x86-64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.7/contrib/linux-x86-64/)

also a older version is in synaptic

---

### Post by shane2peru on 2008-03-30
I have Lightning working, it is the calendar sync function with Google Calendar and [this extension]("https://addons.mozilla.org/en-US/thunderbird/addon/4631") that I can't get to work.  It is another extension.  Any ideas would be greatly appreciated.  Also I'm using SwiftDove, not Thunderbird, although I did install thunderbird and lightning (both easily and both work) it is that Provider Google Calendar sync extension that doesn't work with actual Thunderbird either.

Shane

---

### Post by shane2peru on 2008-03-30
This is fixed!  See [this post here.]("http://swiftweasel.tuxfamily.org/forum/viewtopic.php?id=77")

Shane

---

