---
title: "PKR help"
date: 2007-04-16
forum: Wine
---

### Post by MikeSz on 2007-04-16
Hello all - im just wondering if anyone has tried to get PKR ([www.PKR.com](www.PKR.com)) working through Ubuntu.  I have used it in Windows and quite liked it so wouldnt mind installing it.  I have WINE if thats going to be of any use?  

Ive checked on here and there are no related threads, it doesnt appear in the database for WINE and ive emailed PKE who say that officially, they dont support Linux, but thats not to say it cant be made to work.  

Any suggestions / ideas anyone?

Mike

---

### Post by lakersforce on 2007-04-16
Why dont you give it a go through Wine and tell us how it went :)

---

### Post by MikeSz on 2007-04-16
I tried it initially - not that great - Wine launches in the background but I get a message telling me I need to update my internet explorer in order to be able to install.  Ive attached a screenshot but not sure how well it will come out.  Not much I can do after that as I take it that as I dont have Internet Explorer, I cant upgrade it!

---

### Post by MikeSz on 2007-04-16
Please does anyone have any experience with this?

---

### Post by Sethalos on 2007-05-10
Same question. It doesn't seem to want to run in Wine.  This is pretty much the only online game I play at the moment, and I'd like to have it installed with my Ubuntu install rather than have to dual boot WinXP.

---

### Post by Sethalos on 2007-05-19
Still looking for some type of solution here, anyone get this working yet?  I've considered trying to install IE 6.0, but not sure if that would work to solve the IE issues raised when trying to install it.

---

### Post by wilhel1812 on 2007-05-19
i installed wine, ie6 and pkr and it worked at my crappy old laptop with lag. i guess it would work fine on a good computer

---

### Post by MikeSz on 2007-05-23
Hi wilhel - could you by any chance say how you did this?  From what I remember, you cant download IE as an executable (this making it easy to run in wine), instead, it downloads a launcher which then connects to to an active install download (whatever you call them) via the microsoft site.

---

### Post by wilhel1812 on 2007-05-23
I can't remember exactly what i did, but i downloaded an exe file with IE 6.x from microsoft. I installed the EXE and PKR ran. i can not run IE. I think PKR only need IE for the splash screen.

---

### Post by masnadiero on 2007-06-03
I followed the guide [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page) to install IE and then i did pkr install , but the pkr program is quite slow and mouse is not working at the login popup. Any suggestion?

PS: VMware even with 3D enable will give failure and so the other emulators like virtualbox..

PS2: msg for the gurus, give it a try :p

---

### Post by MikeSz on 2007-06-04
I havent been able to get it working at all.  Im just going to run it through windows on a dual boot, ive come to the conclusion that whilst I love Ubuntu, I really dont have the time to spend 3 hours getting a single program sort of working when I can do the same thing in 5 minutes in windows.  As much as I love Ubuntu and dislike windows, somethings are just easier in windows.

---

### Post by Fxy on 2007-06-04
Try these steps...
[CENTER]**1/**   Get on a computer with the latest version of IE installed

**2/**   Go2 where the IE folder is & copy it then paste it to wherever u want (e.g. portable device [memory stick etc] (makeing sure that it i accessible through Wine))...

**3/**   Get on Wine then locate the IE folder.  Once located get inside it & find the IE launcer etc...[/CENTER]

---

### Post by Sethalos on 2007-10-27
Bumping this as I'd like to someone with much more experience to see if they can get this running with the new version of Ubuntu.

---PKR ftw.

---

### Post by wilhel1812 on 2007-10-27
would have been interresting, i got it to work with little experience, laggy on a very old computer with 7.04. but many new versions o wine, ubuntu, ie and pkr has come since then so i guess someone will be able to get it running at full speed by now. good luck!

---

### Post by armandoxxx on 2007-10-28
Hello .. this is what happens here .. 

I installed IE 6 and PKR but after download is done in PKR nothing happens .. I get a splash screen with progressbar .. and in the background I see wine looping this 

fixme:shdocvw:WebBrowser_get_ReadyState (0x134a20)->(0x7cfcb96c)
fixme:shdocvw:WebBrowser_get_ReadyState (0x134a20)->(0x7cfcb96c)
fixme:shdocvw:WebBrowser_get_ReadyState (0x134a20)->(0x7cfcb96c)
fixme:shdocvw:WebBrowser_get_ReadyState (0x134a20)->(0x7cfcb96c)


Using ubuntu 7.10 latest & Wine package

Kind regards 

Armando

---

### Post by Macuyiko on 2007-10-29
Would love to know how some people could get it to work, especially with the Directx stuff going on.

In the attachment you can see how far I got... Thing is, the in game menu works surprisingly good. But once 2 seconds in game, it just freezes up.

---

### Post by bazzard on 2007-10-29
I have just installed Wine. Haven't used it at all yet. But one of the main reasons I wanted to use it was for PKR. Please could somebody tell us how to install it step by step using WINE for a n00b to linux like me. Cheers.

---

### Post by Sethalos on 2007-10-30
Bumpage to see if anyone has any clues on how to get this to run with the new 7.10 version.

Best poker site in the world, would be great to have this working with Ubuntu.

---

### Post by bazzard on 2007-10-31
Well! I thought I had succeeded, but turns out I hadn't. Manage to install PKR, It runs and works and everything is fine until you attempt to join a game. As soon as the textures on the characters start to load once you join a table, it freezes. I tried putting all the graphical settings on low but it didn't help.

I installed it by installing WINE first, then IE, then downloading PKR through IE and away I went. If someone else would like to give it a go and see if they can get it to work I'd be interested about your result.

Also, if anyone knows how to fix my problem of PKR hanging, please tell me how.

Cheers and I hope someone else may have better luck than I did.

---

### Post by stuart.crouch on 2007-10-31
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9231](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9231)

No one has got it to work yet.  In fact - you guys seem to have gotten further than any of the maintainers.  

The best way to get this resolved is to report your findings to the wine team as wine obviously isn't capable of playing your game yet.

---

### Post by bazzard on 2007-11-06
Just had another go, This time it worked fine! I was even playing a game for 5 minutes, then it crashed. But it worked! wooo hoo!

---

### Post by wilhel1812 on 2007-11-07
sweet! on what pc? a good one or?

---

### Post by bazzard on 2007-11-07
On a Sony Vaoi SZ3HP, I think the best is going to be for me to just run it on VirtualBox/VMWare

Intel® Core&#8482; 2 Duo Processor T5600, 1.83GHz
1GB DDR2 Memory
NVIDIA® GeForce® Go 7400

---

### Post by MikeSz on 2007-11-07
Wow - looks like ive created a monster!  Just come back to this thread to see how things are going and glad that its not just me who cant get this game working!

Ive just upgraded to 7.10, and put the latest wine on it so i'll have another go at PKR and post the results.

As a by-the-way thing, Pokerstars.com is the only other one which I have got to work perfectly on Ubuntu.  Plays perfectly fine and whilst its no-where near as good as PKR, its still a decent poker site.

---

### Post by bazzard on 2007-11-30
Got an XP install up and running on VirtualBox. PKR installs and everything as expected. But sadly, when I came to play I get a random error about D3D.

I fully updated XP and got the latest DIrectX stuff but no joy.

I presume it's due to VIrtualBox not having good graphics support or something. I really don't know what else I can do but be forced into dual booting Ubuntu with XP. I am trying to find out how to add an XP partition now because I can't get nokia pc suite working either, and I want to use itunes with my new ipod.

any other ideas, let us know.

cheers

---

### Post by MikeSz on 2007-12-03
I think for PKR the only way to play it is through an XP partition.  Ive tried a few things and just cant get it working (may also be down to my laptop which being honest, isnt the best when it comes to graphics).  Hopefully in the future it can be made to run - for now however, ive settled for running XP on a spare box for things like PKR - I also use if for things like Championship Manager which I have also been unable to make run in wine (well, the 01-02 version anyway) and for internet TV like channel 4 OD which also needs windows.

---

### Post by cogadh on 2007-12-03
Virtual machines cannot do accelerated graphics, they only do basic VGA and VESA emulation, which is not enough for D3D. Eventually accelerated graphics ability may be developed, but not with the current VMs available.

---

### Post by Smudger on 2008-04-21
Sorry to drag up an old topic, but has anyone got PKR working with Ubuntu yet?

I love this game and only after a few days I am beginning to really miss it.

---

### Post by SpirituZ on 2008-05-10
i also would like to know if someone has succeded on running this game.. i am really interested

---

### Post by wilhel1812 on 2008-05-10
I got i running on a really old and slow computer. It was really slow, but i'm sure that now, 1 year later, with updated versions of wine and so on it's possible to run it quite well on a fast computer.

---

### Post by kloos on 2008-06-02
The PKR site claim to be working on a version for the Mac.  I have no idea how long this is likely to take, but would that help us here?

---

### Post by gardara on 2008-10-07
> **MikeSz said:**
> 
As a by-the-way thing, Pokerstars.com is the only other one which I have got to work perfectly on Ubuntu.  Plays perfectly fine and whilst its no-where near as good as PKR, its still a decent poker site.


The web version of partypoker.com works well and is fun to play :)

---

### Post by linuxvacuum on 2009-04-20
If you use PKR with **wine**, the performance is great. The downside is that you are limited to one table at a time and there are minor graphical glitches. If you try more than one table, all the players and information are mixed together. Try it, it is fun to see :)

With **VMware Workstation** 6.5.2, the game is exactly the same as it would be in Windows. The performance is less than with wine but you can play more than one table at once now.

---

### Post by ariaworld on 2010-04-28
any news?

---

### Post by SEEYOUTHERE on 2010-06-13
Since you have internet and also have an XP conmputer using Ubuntu you could set up a remote desktop using Terminal Server Client it works pretty well

---

### Post by darthdamo on 2011-02-15
the only problem I have with pkr and wine is I get adobe flash player isuses i try to update but cant get any joy please help

---

