---
title: "Lord Of The Rings Online (LOTRO) Part 2"
date: 2011-07-10
forum: Wine
---

### Post by Ms_Angel_D on 2011-07-10
The original thread for LOTRO (found here [http://ubuntuforums.org/showthread.php?t=386480](http://ubuntuforums.org/showthread.php?t=386480)) has become cumbersome and long. In light of that I closed it and have begun a new thread.

---

### Post by Jaappiee1 on 2011-07-10
Than I shall ask my problem again :)

WHen i start op lotro via pylotro, i get a small blackscreen. Nothing changes it just stay's like that
but i use the classic  ubuntu interface. So i look down and see "game error 129" 

Can anyone help me? I patched completely, tried to see if something wrong with my videocard. But all is fine. Wenn i had windows Xp on this computer, lotro just ran perfect.

thanks already :)

---

### Post by ZekeGraal on 2011-07-11
> **Jaappiee1 said:**
> Than I shall ask my problem again :)

WHen i start op lotro via pylotro, i get a small blackscreen. Nothing changes it just stay's like that
but i use the classic  ubuntu interface. So i look down and see "game error 129" 

Can anyone help me? I patched completely, tried to see if something wrong with my videocard. But all is fine. Wenn i had windows Xp on this computer, lotro just ran perfect.

thanks already :)

I have this exact same problem, only I'm a noobie to lotro and cannot seem to get past error 129 either. However, I'm not a Ubuntu noob and I'm trying to find a way to fix it by scouring the interwebs. My card DOES have compression support, I just checked using ```
glxinfo | grep direct
```... If I find anything I'll post back here..

---

### Post by Jaappiee1 on 2011-07-11
if you have a solution thanks ;D

---

### Post by ZekeGraal on 2011-07-12
Update: I have made a little progress, but I ditched Wine and am trying Crossover Games. My last lotro install worked using pylotro, but when I logged in, it said "could not find bottle 'lord'" I can run the native launcher too, but it gives a dx install error and I can't log in. (I already read that the native launcher didn't work :P) I am now installing it again, (3 hours left), and will report back when it's done. IF CROSSOVER WORKS, I will tell you, there is a 7 day trail too, it's very nice. You can choose install games, then community supported and then click Lord of the Rings Online. There's no error 129 either, but I will see if this works correctly and update here.

---

### Post by ajackson on 2011-07-13
> **ZekeGraal said:**
> My card DOES have compression support, I just checked using ```
glxinfo | grep direct
```... If I find anything I'll post back here..

What graphics card do you have?

LotRO does a check of graphical capabilities and seems to use the same error code if it's requirements aren't met. It could be that the linux drivers for your card don't implement the required functions even if the card is capable.

In the past it used to be only nVida cards that worked, now ATI cards are working due to improvements in their linux drivers but a lot of the Intel ones you tend to find in laptops still don't work due to the drivers being rubbish.

---

### Post by ZekeGraal on 2011-07-13
> **ajackson said:**
> What graphics card do you have?

LotRO does a check of graphical capabilities and seems to use the same error code if it's requirements aren't met. It could be that the linux drivers for your card don't implement the required functions even if the card is capable.

In the past it used to be only nVida cards that worked, now ATI cards are working due to improvements in their linux drivers but a lot of the Intel ones you tend to find in laptops still don't work due to the drivers being rubbish.

Good point, I have an Intel 945GM Express, and I *don't* have good drivers I believe. I ran the game on my windows 64 bit, and I'm still on the tut, but I am going to try and move the program files from that pc to my linux, but I don't think that will do anything..

---

### Post by ZekeGraal on 2011-07-13
Okay, I found out how to get past error 129. Download driconf from the Ubuntu Software Center. (The Search will come up as '3D Acceleration'). Open it by going to System>Preferences>3D Acceleration after you have installed it. Click the 'Image Quality' tab and hit the 'No' button next to 'Enable S3TC texture compression even if software support is not available.' the 'No' Should turn to 'Yes.' Hit the close button at the bottom and fire up PyLoTRO and log in. No error 129! I heard Gandalf talking in the intro video, and now I just need to tweak my userpreferences.ini file to make everything work correctly. Jaappiee1, this shold work for you since you could run it before. Good luck!

---

### Post by Jaappiee1 on 2011-07-14
> **ZekeGraal said:**
> Okay, I found out how to get past error 129. Download driconf from the Ubuntu Software Center. (The Search will come up as '3D Acceleration'). Open it by going to System>Preferences>3D Acceleration after you have installed it. Click the 'Image Quality' tab and hit the 'No' button next to 'Enable S3TC texture compression even if software support is not available.' the 'No' Should turn to 'Yes.' Hit the close button at the bottom and fire up PyLoTRO and log in. No error 129! I heard Gandalf talking in the intro video, and now I just need to tweak my userpreferences.ini file to make everything work correctly. Jaappiee1, this shold work for you since you could run it before. Good luck!

dude,
you are AWESOME. It works ;3. You're THE man ;).

thanks :)

---

### Post by athang3 on 2011-07-14
Thanks for separating the thread.  I've been reading it for days now and I think I've tried everything, lol.  I've been trying to get this going on an old laptop that played it in windows (albeit not greatly).  My graphics card is a radeon Xpress 1150.  Now with all the problems I've heard about that and wine, that may just be the issue.  However, I thought I'd check.  I've done wine, and now have crossover trial, but both just ended up at error 129.  I downloaded the dri program like above, but the options in image quality did not look the same.  Mine only says "support larger textures not guaranteed to fit into graphics memory."  The options are no, at least 1 texture must fit, and announce hardware limits.

If it matters, I've also tried with both free and proprietary drivers for the card.

It may just be a fail card with no hope.  It just doesn't make sense that I know the card can play the game, but it won't in this form.

Thanks in advance.

---

### Post by ZekeGraal on 2011-07-15
> **athang3 said:**
> Thanks for separating the thread.  I've been reading it for days now and I think I've tried everything, lol.  I've been trying to get this going on an old laptop that played it in windows (albeit not greatly).  My graphics card is a radeon Xpress 1150.  Now with all the problems I've heard about that and wine, that may just be the issue.  However, I thought I'd check.  I've done wine, and now have crossover trial, but both just ended up at error 129.  I downloaded the dri program like above, but the options in image quality did not look the same.  Mine only says "support larger textures not guaranteed to fit into graphics memory."  The options are no, at least 1 texture must fit, and announce hardware limits.

If it matters, I've also tried with both free and proprietary drivers for the card.

It may just be a fail card with no hope.  It just doesn't make sense that I know the card can play the game, but it won't in this form.

Thanks in advance.

It's a problem in wine I believe, I know my card can handle it too, but Wine/Linux just doesn't utilize it correctly. I'll look around and see what I can find. I got my game to run, but there are *apparently* too many textures for my card, but it can handle it on Windows. I'll post if I find anything. :D

---

### Post by ajackson on 2011-07-15
> **ZekeGraal said:**
> It's a problem in wine I believe, I know my card can handle it too, but Wine/Linux just doesn't utilize it correctly. I'll look around and see what I can find. I got my game to run, but there are *apparently* too many textures for my card, but it can handle it on Window$. I'll post if I find anything. :D

If that is the case then that almost certainly is a graphics driver problem rather than a problem with wine itself.

---

### Post by Fuzzybair on 2011-07-27
I have a feature request. some how i got a "free to play" account attached to my lotro account. i think it was created when my vip account lapsed. after calling trubine they said there was no way to remove the extra game account. their solution is to rename the extra account to "z do not use" or something like it so the one i want will be the first in the list. i tried that and it worked on windows so i tried linux and it did not change the order the free to play account is always the first in the list. it seems that the sorting is done client side. 

my request is to have an option to remember which one i chose last and automaticly load that that game, or if that is too difficult to do add sorting to the drop down list so that it behaves like the windows client so i can rename things so the one i want is the top one.
Thanks

---

### Post by thom_raindog on 2011-07-31
I saw lotro on a friends 2+ years old windows PC and it did not make me happy. He plays with EVERY graphic setting to the very max on the same resolution I am using and gets over 50 fps out of it (I pointed him to the max-fps slider at that point) where my no 2 month old PC is lucky to get 10 to 20fps with medium-ish settings, carefully hand-balanced between looks and playability.

Without posting a long list of PC specs for now: Is linux such a horrible bottle neck there, or am I doing something wrong? Just to compare, WoW runs fine on my wifes near 3 year old PC with linux and pretty well maxed settings...)

---

### Post by thom_raindog on 2011-08-03
As for driconf: I can install it from the normal repos just fine. But running it results in a little pop-up that tells me: ```
XDriInfo returned with non-zero exit code.
``` and ```
libGL is too old
``` in the console... what is this supposed to mean? I can not upgrade libGL as it is...

---

### Post by thom_raindog on 2011-08-07
Did this thread go by unnoticed? It appears very dead, which is highly unfortunate.

---

### Post by schtufbox on 2011-08-10
> **thom_raindog said:**
> I saw lotro on a friends 2+ years old windows PC and it did not make me happy. He plays with EVERY graphic setting to the very max on the same resolution I am using and gets over 50 fps out of it (I pointed him to the max-fps slider at that point) where my no 2 month old PC is lucky to get 10 to 20fps with medium-ish settings, carefully hand-balanced between looks and playability.

Without posting a long list of PC specs for now: Is linux such a horrible bottle neck there, or am I doing something wrong? Just to compare, WoW runs fine on my wifes near 3 year old PC with linux and pretty well maxed settings...)

What video card is your PC using?

---

### Post by ZekeGraal on 2011-08-10
I *somehow* got the client to run perfectly with PyLotRO after installing some libraries from the xorg-edgers ppa. The next day I log on: boom; It doesn't work? I'm sitting there going: 'ha ha ha.. why am I laughing?' I have a windows pc to run it on, but I just WANT to get it working on here. If anyone could point me to which of these packages might be keeping it from running correctly, that'd be great:
libglapi-mesa
libgl1-mesa-dri-experimental
libllvm2.9
libtxc-dxtn0

After I installed those it ran PERFECTLY, but it would not run the next day. PyLotRO just outputs ***Finished*** and I have no idea of any log files I could look at.

Any ideas?

---

### Post by Pantalaimon on 2011-08-15
Strange little issue here. Finally got Pylotro to open up. Been reading information and documentation.

I'm on ubuntu 11.04 with the newest version of Pyl from the alanjackson ppa.

I'm attempting to play DDO. already have it installed and all that jazz.

As I understand it, after looking at the error I'm getting.
(((E02 : No language files found)))

As far as I can understand what I'm supposed to do is go into tools->settings wizard

Then select my game and click find games.

All well and good. But after clicking find games. nothing happens. NOTHING.

If somebody can tell me how to run this from a command line I'll let you know the output of that.

Any help is appreciated.
Thanks in advance.

---

### Post by Pantalaimon on 2011-08-16
Any help would be appreciated

---

### Post by thom_raindog on 2011-08-20
> **Pantalaimon said:**
> Any help would be appreciated

Personally I never had any luck with the automagic tool. Just open the toosl > options dialog and  set your wine-prefix correctly (that is JUST the /home/your_username/.wine-whatever-folder-you-created-for-lotro) and pick your Game Directory (in your prefix folder and then something like /drive_c/your/game/directory). Keep the rest as it is (fixme-all, hires enabled or disabled, depending on the power level of your pc, but try DISabled first to make sure thats not biting you in the backside).
Save and try.

---

### Post by thom_raindog on 2011-08-20
> **ZekeGraal said:**
> 
libgl1-mesa-dri-experimental


I am by far not an expert in these matters (as seen in my own cry for help, as yet unanswered...) but: Isn't that a package that is used by nouveau as a driver, not the nvidia one? It sounds familiar from my own - failed - attempts at nouveau a while back....

---

### Post by thom_raindog on 2011-08-21
> **schtufbox said:**
> What video card is your PC using?

Nvidia 8400GS. Nothing fancy, I know, but I still feel like it should perform better, especially considering how near perfect WoW seems to run on wine with it.

---

### Post by SNy on 2011-08-25
> **bentron said:**
> I'm having a problem with LOTRO registering unmodified mouse clicks. Right after launching the game everything functions normally and as expected, but after some time (I've yet to notice anything that directly causes it) the game no longer registers unmodified mouse clicks on objects in the world (ie, shift+right click to auto loot a corpse/resource node works, but plain right click to loot or left click to target do not)...

Hey, I started having this very problem about two weeks ago.
As your wine bug-report states, only unmodified clicks are affected and I was as clueless to any possible cause as you.

I have, however, found the cause (for me, anyway) today. Thought I might check direct input stuff and looked for some test program. Not having found anything I somehow got to the wine debug channel page and found 'dinput' as valid channel, so I tried WINEDEBUG="fixme-all,+dinput".
Turns out the xbox controller sent a lot of updates, seemingly spamming the game in a way it would cause the mouse clicks to get lost. Unloaded the controller driver and voila.

HTH,
SNy

---

### Post by ZekeGraal on 2011-08-28
> **thom_raindog said:**
> I am by far not an expert in these matters (as seen in my own cry for help, as yet unanswered...) but: Isn't that a package that is used by nouveau as a driver, not the nvidia one? It sounds familiar from my own - failed - attempts at nouveau a while back....
Thanks for pointing that out, I must have been very tired xD

---

### Post by thom_raindog on 2011-09-02
> **ZekeGraal said:**
> Thanks for pointing that out, I must have been very tired xD

Glad I could help :)
Now if only I would get more input on my own stuff... :/

---

### Post by SNy on 2011-09-12
> **thom_raindog said:**
> Nvidia 8400GS. Nothing fancy, I know, but I still feel like it should perform better, especially considering how near perfect WoW seems to run on wine with it.

Just took a look at what an 8400gs would be capable of and truth be told, your performance issue would be the card's fault. Look at openbenchmarking.org and see for yourself:
 [http://openbenchmarking.org/result/1101018-IV-GEFORCE1908](http://openbenchmarking.org/result/1101018-IV-GEFORCE1908)

Not really suitable for gaming, it seems, and while wine is in amazing shape wrt. the level of support for the game, it's not native and that shows in the performance.
Myself, I am still using an 8800gts which runs OK (about 25fps, though I did dial the settings back, it doesn't look nearly as good as it could, postprocessing off etc. due to me raiding much and prefering playability over stunning looks [visuals are overrated, anyway]).

Doesn't help much, I know, but at least a heads up as in: no, it wouldn't be you doing something wrong.

SNy

---

### Post by Jobaz on 2011-09-17
Hi everyone,

I'm having some troubles as well concerning lotro.

I have followed the "unofficial" install for lotro on  [http://lorebook.lotro.com/wiki/LOTRO_under_Linux_and_Mac_OS/X](http://lorebook.lotro.com/wiki/LOTRO_under_Linux_and_Mac_OS/X) but when I try to launch the game, I get the following error  (which basically says my launcher version is not up to date ): 

[IMG]http://img856.imageshack.us/img856/68/capturemrk.png[/IMG]

I' ve also tried to follow these instructions : [http://www.bmx-chemnitz.de/~mfr/LOTRO/](http://www.bmx-chemnitz.de/~mfr/LOTRO/) but I have to say that I'm quite a noob on Linux, I just moved from vista. (btw so far so great, except that lotro issue ruinning my geek life .. ^^)

Is there someone to help me ? 

Cheers

---

### Post by Ms_Angel_D on 2011-09-17
I don't speak french but that looks like a client mismatch error. You might need to update your game.

---

### Post by _d_ on 2011-09-17
> **Ms_Angel_D said:**
> I don't speak french but that looks like a client mismatch error. You might need to update your game.

If it makes a difference here is the error message translated by Google:

> Failed to connect:
 The current version of client is not the one you have installed.

So you might have just hit the head on the nail with the mismatch. :P

---

### Post by Jobaz on 2011-09-18
Right, so the thing is, when i try to patch pylotro, it only displays *FINISHED*, which means it's not patching (did'nt know that yesterday). 

Looks like the bug's been reported before on : [https://bugs.launchpad.net/pylotro/+bug/424910](https://bugs.launchpad.net/pylotro/+bug/424910)

Yet I'm not sure how to solve it anyway :/

EDIT : I've downloaded the patch as A. Jackson is talking about in the bug report, and replace the old one on the lotro root, looks like it's gonna work.

EDIT 2 : Now it's working, thanks a lot for pointing out the issue ;)

---

### Post by martialartist81 on 2011-09-18
> **Jobaz said:**
> 

EDIT : I've downloaded the patch as A. Jackson is talking about in the bug report, and replace the old one on the lotro root, looks like it's gonna work.

EDIT 2 : Now it's working, thanks a lot for pointing out the issue ;)

Thanks for posting results!  It's this kind of "give back" in these threads that help a lot of folks (like me) out!  Glad to hear you're back up and running, Jobaz!

Again, special thanks to ajackson and SNy.  Both of your guys' contributions to getting and keeping LOTRO running on Linux have been absolutely stellar!

---

### Post by wulvyrn on 2011-09-19
i installed pylotro but i'm not getting any menus to show at the top.

ubuntu 11.04 64bit.


there is no menu items at the top to patch, etc.  any ideas?

---

### Post by thom_raindog on 2011-09-20
> **wulvyrn said:**
> i installed pylotro but i'm not getting any menus to show at the top.

ubuntu 11.04 64bit.


there is no menu items at the top to patch, etc.  any ideas?

I assume you use Unity as a "windowmanager" as it is standard in Ubuntu these days... Just go ahead and start pylotro, then move your mouse ALL the way up to the end of your screen - voila :)

---

### Post by wulvyrn on 2011-09-20
wow thanks, i had to maximize it to full screen to see those menu options.  thanks.

---

### Post by thom_raindog on 2011-09-21
> **wulvyrn said:**
> wow thanks, i had to maximize it to full screen to see those menu options.  thanks.

No problem. Though you should not have to maximize, just move the mouse to the top edge of your screen, is all. In any case, glad I could help :)

---

### Post by Salmanazar on 2011-10-06
> **ZekeGraal said:**
> Okay, I found out how to get past error 129. Download driconf from the Ubuntu Software Center. (The Search will come up as '3D Acceleration'). Open it by going to System>Preferences>3D Acceleration after you have installed it. Click the 'Image Quality' tab and hit the 'No' button next to 'Enable S3TC texture compression even if software support is not available.' the 'No' Should turn to 'Yes.' Hit the close button at the bottom and fire up PyLoTRO and log in. No error 129! I heard Gandalf talking in the intro video, and now I just need to tweak my userpreferences.ini file to make everything work correctly. Jaappiee1, this shold work for you since you could run it before. Good luck!

This solved the "black screen and error 129" issue for me on a Toshiba Satellite L300 with an Intel graphics card.

---

### Post by Jobaz on 2011-10-20
Hi there, 

Since the new ROI update, I've managed to update the client but nothing happens when I click "login", just displays the window "*FINISHED*. I tried to apply some advices from here : [http://forums.lotro.com/showthread.php?421807-Any-linux-wine-pylotro-users-able-to-patch](http://forums.lotro.com/showthread.php?421807-Any-linux-wine-pylotro-users-able-to-patch)

Didn't work obviously. Any ideas ?

---

### Post by ajackson on 2011-10-20
I'm not 100% but the problem could be with vcrun2005, I think Turbine use a function from an update, re-installing using an up to date version of winetricks should fix it.

Most people seem to have updated with no trouble which makes troubleshooting hard, especially since my update went smoothly even if I have only managed a couple of hours play since ROI came out, got to love RL problems :-)

---

### Post by cumbrian on 2011-10-22
I was very happy with Ubuntu until this afternoon when I upgraded. Now my LOTRO won't work:(

It just checks the worlds, updates the launcher message, I log on, it checks my account and goes right to the Exit page without ever loading the game. It exits without any error.

It was working well this morning on 11.04 but is broken this afternoon on 11.10. I tired a few ideas:

1) Changed Wine to use the latest Wine HQ repo and upgraded
2) Removed old wine (checked using wine --version reports wine-1.3.30)
3) Tried to reinstall DX9 winetricks says it's already installed
4) Checked pyLotro has all the correct settings, they seem ok (I'm using the wine version of pyLotro; the native version says [E04] Error accessing GLS data centre.)
5) Tried reinstalled the ATI drivers from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)
6) I tried re-installing pyLotro

None of that worked. I wish I hadn't installed the update now, chromium seems a bit faster but other than that it just seems to have made things more annoying. :(

---

### Post by lostmymind on 2011-10-22
I too am having problems since the up date to 11.10, with Lotro

Mine is saying I don't have DX9 yet I have checked everything and it is saying I do (wine etc..):confused:

---

### Post by ergo-proxy on 2011-10-23
Run ./winetricks d3dx9_36 and use pylotro.

---

### Post by lostmymind on 2011-10-23
> **ergo-proxy said:**
> Run ./winetricks d3dx9_36 and use pylotro.
 
tried that and still getting no dx

---

### Post by Jobaz on 2011-10-24
> **ajackson said:**
> I'm not 100% but the problem could be with vcrun2005, I think Turbine use a function from an update, re-installing using an up to date version of winetricks should fix it.



Thanks for the reply but it didn't work, still not lauching the lotro window ..

---

### Post by SNy on 2011-10-24
I don't think the vc runtime 2005 suffices anymore.

Try
 winetricks vcrun2005sp1 vcrun2008

to also install the 2005 SP1 and 2008 versions.

SNy

---

### Post by ajackson on 2011-10-24
> **SNy said:**
> I don't think the vc runtime 2005 suffices anymore.

Try
 winetricks vcrun2005sp1 vcrun2008

to also install the 2005 SP1 and 2008 versions.

SNy

I thought that sp1 was pulled in automatically when using vcrun2005 with winetricks but I did forget about the need for vcrun2008.

---

### Post by hemna on 2011-10-25
I just got lotro starting in linux with pylotro.   The problem I'm seeing now is that when lotro starts it loads the main character selection screen but I can't click on anything in the right hand panel.  I want to adjust the options, or even enter the world, but that right panel doesn't work :(

---

### Post by ergo-proxy on 2011-10-26
> **hemna said:**
> I just got lotro starting in linux with pylotro.   The problem I'm seeing now is that when lotro starts it loads the main character selection screen but I can't click on anything in the right hand panel.  I want to adjust the options, or even enter the world, but that right panel doesn't work :(

I had the same problem, enter the game and change it from there.

---

### Post by Inkpot on 2011-10-29
So I'm trying to install PyLotRO, but can't seem to add the PPA to my sources. Does anyone have the latest?

---

### Post by ergo-proxy on 2011-10-30
First link from google...

download pylotro-setup.exe

---

### Post by Inkpot on 2011-10-30
No need to be snarky, I just don't know how to run that file in Ubuntu.

---

### Post by Ms_Angel_D on 2011-10-31
You can just add the repo and change oneiric to natty after you add it and it will still work it's just the repo hasn't been updated for some reason.

---

### Post by ergo-proxy on 2011-10-31
> **Inkpot said:**
> No need to be snarky, I just don't know how to run that file in Ubuntu.

Oh come on ;) Open a terminal and type: wine pylotro_setup.exe and follow the instructions.

---

### Post by Inkpot on 2011-10-31
> **Ms_Angel_D said:**
> You can just add the repo and change oneiric to natty after you add it and it will still work it's just the repo hasn't been updated for some reason.

I officially love you.

---

### Post by Suroh66 on 2011-11-01
I've had the problems as the original poster I just ended up getting tired of it lol and removing wine and all of it's components I reinstalled made sure I put the propper dlls in   made sure it was patched etc. and grabed the newest proprietary driver ( for my Ati Raedon Hd 4200) how ever I have a laptop running with an intel gma express family chipset ( intel gma x4500) that is running lotro with around 10 fps and I followed the same steps as I did on my desktop except for getting a propietary driver lol. The only remaining problem I'm having is pulse audio crashes every now and then. Nothings perfect though I guess... To Inkpot Pylotro has not been updated I tried to get it multiple ways with no good results the only way I was able to get it was through a friend using this which i didn't think would work to begin with but sure enough it did check this out to any one who is interested [http://ubuntuforums.org/showthread.php?t=249439](http://ubuntuforums.org/showthread.php?t=249439). Note that you will need to know some one else who has this other wise my advice isn't going to help but again it was the only solution I found :(

---

### Post by SNy on 2011-11-16
Hey, something I wanted to share.

Just started updating the Bullroarer client to check out some of the new set stuff, when my patch output told me it downloaded the following:

   1%                    OpenGLGraphicsCore.dll  23/41  Done.           

Interesting, that they would now include a GL graphics core alongside D3D10 and D3D11 versions, no?

Does anyone know of plans to a Mac version or something?

SNy

---

### Post by Robertjm on 2011-11-20
There all sorts of driver quality issues with thebRadeon Xpress cards as I remember it. Not just LOTR but anything remotely graphical. Turn down the graphics acceleration to see if that helps.

Good luck!!

Robert

[/B][/B]> **athang3 said:**
> Thanks for separating the thread.  I've been reading it for days now and I think I've tried everything, lol.  I've been trying to get this going on an old laptop that played it in windows (albeit not greatly).  My graphics card is a radeon Xpress 1150.  Now with all the problems I've heard about that and wine, that may just be the issue.  However, I thought I'd check.  I've done wine, and now have crossover trial, but both just ended up at error 129.  I downloaded the dri program like above, but the options in image quality did not look the same.  Mine only says "support larger textures not guaranteed to fit into graphics memory."  The options are no, at least 1 texture must fit, and announce hardware limits.

If it matters, I've also tried with both free and proprietary drivers for the card.

It may just be a fail card with no hope.  It just doesn't make sense that I know the card can play the game, but it won't in this form.

Thanks in advance.

---

### Post by krustykrabs on 2011-12-03
I don't have a video card right now so I've been using my onboard video to play DDO in Windows.  It's a GeForce 7025 and it's pretty sucky, but it could play the game decently on medium graphics, smooth on low.  My HDD crashed so I decided to give ubuntu another try (I try it every year or two).  Ubuntu has made great strides since my last try, nearly everything has a gui interface now, and 99% of the things I have tried to do have not only worked, but were simple to accomplish with just a few clicks of the mouse, I'm extremely impressed.  I was thinking of buying Windows 7, but I'm quite happy with Ubuntu now and very glad I gave it another try.

I was going to setup a dual boot with XP to run DDO when I remembered reading in the forums about some people getting DDO to run in Linux with Wine.  I was surprised to find that I too got DDO running in Linux with minimal effort, a huge thanks to the creators and maintainers of the launcher!  Great job guys!

However, I have a major problem with DDO that makes it quite unplayable.  Every 3 seconds the game pauses for 1.5 seconds.  The frame rate display shows ~30 then 3 then 4 then ~30 over and over again.  Particle effects stand still, then move seamlessly, then stand still, over and over.  If I try to move, I move seamlessly, then freeze, over and over again.

Text chat works in party and guild chat.  Voice chat seems to work, although the person I tested it with me could always hear me flawlessly, while I only heard him once.

I imagine it's probably my onboard video is too sucky to handle it, but it seems like the frame rate would always be 3 if that were the case.  So I figured asking if anyone else has had this problem is a good idea before scrapping it altogether until I get a new video card (which could be long after the holidays).

Any help is appreciated, and thanks again to the developers and maintainers that have made this all possible.

**** edit ****

I've been playing around with this for quite a few hours now and came across something very interesting.  At the character screen in DDO the particle effect in the water fountain behind the character would flow and freeze, flow and freeze as described above, so I could change a setting and see if it had any effect without having to actually go into the game each time.  I played with more settings than you can imagine, changing them one at a time and changing them back when they didn't have any effect.

I tried every graphical setting I could find but nothing helped, so I gave up and decided to figure out how to get rid of unity.  I downloaded gnome-shell and spent awhile trying to figure out how to launch it and close unity (turns out you simply select it on the login screen).  When I finally got that setup the way I liked, I decided to give DDO another shot just for the heck of it.  To my surprise, on the character screen the particle effects in the water fountain were flowing seamlessly without hesitation or interruption of any kind!  However, when I got into the game there was still the constant and rapidly recurrent freezes, but they did seem a bit less obtrusive.

I knew I was on to something, getting rid of Unity had a marked effect.  So I looked up other window managers and found fluxbox, described to be as light as they come.  With Fluxbox the particle effects on the character select screen looked absolutely smooth as silk.  I was hoping that fixed the problem altogether, but alas, in game there is still a rapidly recurrent freeze, but it is so much better the game is almost playable.

Before with Unity the framerate display would show 30 3 4 30 4 5 30.  With Fluxbox the framerate displays as 30 28 5 30 29 5 28 29 3.  In other words, it's about a 33% improvement, so instead of being frozen 66% of the time it's now only frozen 33% of the time.

The game is still pretty unplayable, even walking from one place to another is a chore, but I'm even more convinced this isn't because my onboard video can't handle it, but rather because of a setting or conflict that can be resolved.

I'll keep at it and update with the results.

---

### Post by SNy on 2011-12-05
Well, that sounds rather odd as the wine performance for LotRO (and I suppose DDO as well) is actually rather good.

A few items that come to mind:
[LIST]
[*]Do you use the latest available version of wine, ie, as of time of writing, 1.3.34 or at least 1.3.x in general?
[*]Which settings do you use for wine, most notably the windows version to use as well as settings under 'Graphics' (hardware acceleration etc.)?
[*]Does any other stuff run on the machine or does that stuttering occur regardless of load on the machine (think: updates for search indices, man pages etc.)?
[*]Do you lack physical and/or video RAM? For LotRO at least, you should consider 2 GB for physical and 256, better yet 512 MB for video RAM.
[/LIST]
Also, if you can test the setup with some other games (both native and wine, if possible), it might help to see if DDO is at fault or the system itself has issues.

HTH,
SNy

---

### Post by krustykrabs on 2011-12-08
I've been working on my problem a lot less because I've pretty much run out of ideas.  I'm going to have to just go with the premise that the onboard video just can't handle it and hope things improve when I get a new video card after the holidays.

To answer SNy's questions...

Latest version.
I've tried literally every possible combination of graphic settings in Wine.
4 cores, all stay under 50% the entire time.
4 gigs RAM, 256K video RAM.

I've thought about trying something else 3D in Wine and that is my next step, I've just come up empty on what to try.  As far as native 3D apps, the few I've tried have run just fine.  (Tuxracer/Billiards 3D)

When I get a video card (something I've planned on doing eventually no matter what, but just can't afford one now) I'll report back as to whether or not it solved my problems.

LOVING! Ubuntu, by the way.

---

### Post by SNy on 2011-12-11
Hm. In that case maybe you could try and let wine display more of its warnings and debug information.
There's a setting in the launchers, should be set to "fixme-all" in the default configuration.

Have a look at wine's [debug channel page]("http://wiki.winehq.org/DebugChannels") for what you can set there.

I don't know about DDO specifically, but you could try some trouble shooting settings there. LotRO has a few of those, like engine speed and somesuch, that you can set and experiment a bit.

HTH,
SNy

---

### Post by Faffin on 2011-12-17
> **Ms_Angel_D said:**
> You can just add the repo and change oneiric to natty after you add it and it will still work it's just the repo hasn't been updated for some reason.

This worked for me. I edited the repo in the software manager, but then I had to do "sudo apt-get update" to see it, then "sudo apt-get install pylotro" to install it. Is there a better way?

By the way, LotRo is working about as well as it ever did in WinXP :)

---

### Post by Inkpot on 2011-12-24
Hmm...I'm experiencing frequent crashing (about once or twice per session) with the following error(s) output in pyLOTRO:



ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe

ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side

ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)

ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)

ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream

Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

err:alsa:ALSA_CheckSetVolume Could not find '{PCM,Line} Playback Volume' element

err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb75c02b8
wine client error:9: write: Bad file descriptor

err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb410ab19
wine client error:9: write: Bad file descriptor
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb410ab19
wine client error:9: write: Bad file descriptor
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb410ab19
wine client error:9: write: Bad file descriptor
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb410ab19
wine client error:9: write: Bad file descriptor
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb410ab19
wine client error:9: write: Bad file descriptor
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb410ab19
wine client error:9: write: Bad file descriptor
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb410ab19
wine client error:9: write: Bad file descriptor
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb410ab19
wine client error:9: write: Bad file descriptor
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb410ab19
wine client error:9: write: Bad file descriptor
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb410ab19
wine client error:9: write: Bad file descriptor
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb410ab19
wine client error:9: write: Bad file descriptor
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb410ab19
wine client error:9: write: Bad file descriptor
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb410ab19
wine client error:9: write: Bad file descriptor
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb410ab19
wine client error:9: write: Bad file descriptor
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb410ab19
wine client error:9: write: Bad file descriptor
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb410ab19
wine client error:9: write: Bad file descriptor
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb410ab19
wine client error:9: write: Bad file descriptor
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb410ab19
wine client error:9: write: Bad file descriptor
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb410ab19
wine client error:9: write: Bad file descriptor
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xb410ab19
wine client error:9: write: Bad file descriptor

*** Finished ***


Anyone else experiencing this or have any solutions? I'd really appreciate it!

---

### Post by Eisdiele on 2011-12-27
Hi,

I'm having a lot of trouble of getting LotRO tu run.

Right now I was able to install the game and even patch it normally but when I try to start it, it only shows the output window. I already tried a fresh install of PyLotro and the game itself.

 I'm using Ubuntu 11.10 and followed several How-Tos using the stand alone PyLotro client, the most acutual wine environment 1.3.35 and I downloaded Lotro with the original pando downloader. I think that I installed all the directx and dll stuff with wine tricks. I have a nvidia graphics card with the newest drivers.

I don't have any other idea what to do. I found some post with a similar problem but none of them said what their solution was.

I'd be happy about any help/ideas/links.

Thanks a lot

---

### Post by Eisdiele on 2011-12-28
Terminal Output shows:
```
xxx@xxx:~/.wine/drive_c/Programme/PyLotRO$ wine pylotro
fixme:system:SetProcessDPIAware stub!
fixme:win:FlashWindowEx 0x32e5ec
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:imm:ImmReleaseContext (0x10072, (nil)): stub
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:win:FlashWindowEx 0x32ad84

```

I don't understand a word but maybe somebody can help me.

---

### Post by ergo-proxy on 2011-12-29
Ok follow me,
did you install the latest wine from wine ppa?
do you have installed propietary dirvers?
did you install vcrun2008 and dx9_36 on a clean wineprefix?
did you install the game (for example: GC_DONT_GC=1 wine lotrohigh.exe) 
did you patch the game using pylotro?
did you run the game using the latest pylotro? ([http://crossover.codeweavers.com/redirect/pylotro](http://crossover.codeweavers.com/redirect/pylotro))

---

### Post by Eisdiele on 2011-12-29
Hi ergo-proxy,

Thanks for your reply. Thats exactly how I did it. The only thing is, that the clean wine install isn't as clean anymore because I tried several direct x  and vcrun versions. But I can try it with a complete new one and only the ones you named this evening.

So thanks for your efforts.

---

### Post by ergo-proxy on 2011-12-29
What GPU do you have? You can also try with the stable wine version (1.2.3)

---

### Post by Eisdiele on 2011-12-29
I tried everything again from the beginning but still the same problem. For the nvidia driver I have version 280.13 and a 3100m notebook gpu. I also tried the slightly newer driver(but not "recommended" one) and disabeling the driver for tv-cards but it doesnt make any difference.

 The only thing I didn't do was downloading it again. But I did so 3 times before and this exactly download works well under windows. But it patches allright so I don't think its less a problem with the game then with my wine config. I bet its something stupid but I don't get it...

Thanks

---

### Post by ergo-proxy on 2011-12-30
Did you try with wine 1.2.3? (it's available in a repository)

---

### Post by Eisdiele on 2011-12-30
Jepp i did. But then I got different kind of trouble. It didn't even patch allright. Maybe I can try it again later with the fresh install, but I don't think that this will solve it.

---

### Post by ergo-proxy on 2011-12-30
Is your oneiric a fresh install or did you upgrade it?

---

### Post by Eisdiele on 2011-12-30
It's only upgraded.

---

### Post by ergo-proxy on 2011-12-30
One of my last options would be to reinstall wine again and mike sure you have correct wine ppa:
 
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get purge wine wine1.2 wine-dev wine1.2-dev wine1.3 wine1.3-dev
sudo apt-get -f install
sudo apt-get install wine1.3
 
and paste the output when starting lotro

---

### Post by Eisdiele on 2012-01-02
I reinstalled wine with exactly your code but its still the same. Only the last line in the following log seems to be new. But a short research says that it should*t cause any troubles...

So even if its not really working, thanks for your help and happy new year...

```
fixme:system:SetProcessDPIAware stub!
fixme:win:FlashWindowEx 0x32e5ec
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:imm:ImmReleaseContext (0x10076, (nil)): stub
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:win:FlashWindowEx 0x32a9d4
err:ntdll:RtlDeleteResource Deleting active MRSW lock (0x1134bc), expect failure
```

---

### Post by Gnome Defender on 2012-01-11
Hi,

I've only put ten minutes into reading this thread, so I'm pretty clueless.  But I'd like to know if there's a tutorial for installing Lotro for Ubuntu 11.10.

Thanks,
Gnome

---

### Post by ergo-proxy on 2012-01-12
Yes there is, on winehq.

---

### Post by chrionix on 2012-01-29
Hi all, unlike the second previous poster, I've spent a little longer reading posts etc trying to work out my problem. I keep getting the error: err:module:import_dll Library QtSvg4.dll (which is needed by L"C:\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found

I'm hoping this is the crux of my problem, this is my first attempt at using wine, and so far it's going appallingly. I've copied my windows 7 install of lotro to the local .wine\drive_c\Program Files\Turbine directory, and installed PyLotro.

PyLotro boots, and shows the news in the panel, but when I click connect, it pops up an output box that says **finished** or some such, but lotro never loads, and I get the above error in the terminal.

Any help greatly appreciated.
Cheers.

---

### Post by MusicJunkie08 on 2012-01-29
I am having a rather strange problem. I transferred the game files from  my Windows 7 desktop into Wine, installed PyLotrO, and opened the game.  At first I got a black screen after startup, so I followed the steps  here:
> **ZekeGraal said:**
> Okay, I found out how to get past error 129. Download driconf from the Ubuntu Software Center. (The Search will come up as '3D Acceleration'). Open it by going to System>Preferences>3D Acceleration after you have installed it. Click the 'Image Quality' tab and hit the 'No' button next to 'Enable S3TC texture compression even if software support is not available.' the 'No' Should turn to 'Yes.' Hit the close button at the bottom and fire up PyLoTRO and log in. No error 129! I heard Gandalf talking in the intro video, and now I just need to tweak my userpreferences.ini file to make everything work correctly. Jaappiee1, this shold work for you since you could run it before. Good luck!
That worked for me and the game started just fine. However, when I go to select my character, all she is a torso, head and arms! No legs and no helmet. When I actually get into the game to play (which loads with no problem), she goes between this and just a mass of random graphics. I am thinking this is a problem with my graphics card (Intel 945 ME Express), because game play is a little slow. All the graphics settings in the game are on the lowest setting.

Has anyone else had this problem? I am running 11.10.

TIA

EDIT: Forgot to add, all the other graphics in the game are fine. My character is the only one off.

---

### Post by ajackson on 2012-03-20
**Oneiric PyLotRO 0.1.15 build**

Some people have been asking for a build for oneiric even though the previous one will work. It's done and it's on the ppa.

Due to changes in personal circumstances PyLotRO is being set free, I don't have the time nor do I play either of the games it supports. It is under a GPL license so it is free for other to take up, build upon, etc.

**Note:** Do not PM me about support for PyLotRO please.

---

### Post by schtufbox on 2012-03-20
Alan,
I haven't played LoTRO for a long time, but I remember all the help and effort you've put into this over the years, so I'll take this opportunity to say thanks..again :):guitar:
Was it you that wrote the Tabula Rasa launcher too, I can't remember..still think it's a shame that game shut down!

---

### Post by ajackson on 2012-03-20
> **schtufbox said:**
> Alan,
I haven't played LoTRO for a long time, but I remember all the help and effort you've put into this over the years, so I'll take this opportunity to say thanks..again :):guitar:
Was it you that wrote the Tabula Rasa launcher too, I can't remember..still think it's a shame that game shut down!

Ah yes good old ULL, handled most of the NCSoft games that used their universal launcher, Tabula Rasa was a good game, I was pretty dire at it but liked it :-)

---

### Post by steelsnake on 2012-03-24
Just FYI, Precise beta broke something - not sure what exactly but regardless of what (linux-)launcher one uses, GLSAuth fails. Using the Windows version of PyLOTRO works though.

On the plus side, someone on the Wine AppDB said they got the original launcher to work under Linux with .NET and the latest Wine 1.5 - so the days of needing a specialized launcher might be over.

---

### Post by ajackson on 2012-03-24
> **steelsnake said:**
> Just FYI, Precise beta broke something - not sure what exactly but regardless of what (linux-)launcher one uses, GLSAuth fails. Using the Windows version of PyLOTRO works though.

On the plus side, someone on the Wine AppDB said they got the original launcher to work under Linux with .NET and the latest Wine 1.5 - so the days of needing a specialized launcher might be over.

Looking at another post it is failing getting the web response, the code is valid python 2.7 so it could well be a bug in python or some change caught mid implemented that will get resolved.

---

### Post by steelsnake on 2012-03-25
> **ajackson said:**
> Looking at another post it is failing getting the web response, the code is valid python 2.7 so it could well be a bug in python or some change caught mid implemented that will get resolved.

I should have been more clear - your code is fine, they broke something in a library. Because the fetch fails in wget as well. The breakage occurred with one of the patches pushed out Thursday/Friday. It worked fine on Thu, but didn't on Fri.

Since the Windows pylotro works, it's not really a huge deal.

---

### Post by icefire227 on 2012-03-30
How do I get PyLotro up and running on 12.04 beta 2?

---

### Post by steelsnake on 2012-03-30
Install the Windows version of PyLotRO: [http://crossover.codeweavers.com/redirect/pylotro](http://crossover.codeweavers.com/redirect/pylotro)

---

### Post by CheatCat on 2012-03-31
I suddenly got the following error when trying to log in via pylotro:

```
Traceback (most recent call last):
  File "/media/debhdd/home/katt/Games/PyLotRO/PyLotROLauncher/MainWindow.py", line 295, in txtPasswordEnter
    self.btnLoginClicked()
  File "/media/debhdd/home/katt/Games/PyLotRO/PyLotROLauncher/MainWindow.py", line 289, in btnLoginClicked
    self.AuthAccount();
  File "/media/debhdd/home/katt/Games/PyLotRO/PyLotROLauncher/MainWindow.py", line 306, in AuthAccount
    self.uiMain.txtPassword.text(), self.baseConfig.gameName, self.valHomeDir, self.osType)
  File "/media/debhdd/home/katt/Games/PyLotRO/PyLotROLauncher/PyLotROUtils.py", line 532, in __init__
    if webresp.status == 500:
AttributeError: 'NoneType' object has no attribute 'status'
```

Can anyone help me?

---

### Post by steelsnake on 2012-03-31
Still the same advice: Run the **WINDOWS** version of PyLOTRO. It avoids a lot of headaches.

---

### Post by icefire227 on 2012-04-01
> **steelsnake said:**
> Still the same advice: Run the **WINDOWS** version of PyLOTRO. It avoids a lot of headaches.

I am running the windows version of PyLotro, as you linked above, and I can't logon. It just sits at Checking Account Details.

---

### Post by CheatCat on 2012-04-01
> **steelsnake said:**
> Still the same advice: Run the **WINDOWS** version of PyLOTRO. It avoids a lot of headaches.

Yes, thank you, that actually worked... So the pylotro isn't open source nowsadays?

---

### Post by schtufbox on 2012-04-01
> **CheatCat said:**
> Yes, thank you, that actually worked... So the pylotro isn't open source nowsadays?

It's still open source, however due to personal reasons the developer is no longer updating it, as posted a few posts ago..nothing to stop others taking over however...

---

### Post by CheatCat on 2012-04-02
> **icefire227 said:**
> I am running the windows version of PyLotro, as you linked above, and I can't logon. It just sits at Checking Account Details.

Check the console output or try the source version. I got the source version running now. I think I found a bug in the code tho, I will learn some python and try to fix it.

---

### Post by icefire227 on 2012-04-10
> **CheatCat said:**
> Check the console output or try the source version. I got the source version running now. I think I found a bug in the code tho, I will learn some python and try to fix it.

```
Traceback (most recent call last):
  File "PyLotRO\build\pyi.win32\pylotro\outPYZ1.pyz/PyLotROLauncher.MainWindow",
 line 291, in txtPasswordEnter
  File "PyLotRO\build\pyi.win32\pylotro\outPYZ1.pyz/PyLotROLauncher.MainWindow",
 line 285, in btnLoginClicked
  File "PyLotRO\build\pyi.win32\pylotro\outPYZ1.pyz/PyLotROLauncher.MainWindow",
 line 302, in AuthAccount
  File "PyLotRO\build\pyi.win32\pylotro\outPYZ1.pyz/PyLotROLauncher.PyLotROUtils
", line 527, in __init__
AttributeError: 'NoneType' object has no attribute 'status'
```

There is the console output.

---

### Post by MusicJunkie08 on 2012-05-14
Has anyone been able to get the launcher to work? Mine patched fine, but it stays stuck on checking account details. I can't seem to get it to actually launch the game.

---

### Post by brainwash on 2012-05-14
> **MusicJunkie08 said:**
> Has anyone been able to get the launcher to work? Mine patched fine, but it stays stuck on checking account details. I can't seem to get it to actually launch the game.
Try this shell script instead:

[http://www.bmx-chemnitz.de/~mfr/LOTRO/lotrolauncher.script]("http://www.bmx-chemnitz.de/%7Emfr/LOTRO/lotrolauncher.script")

Like mentioned in the info text you will also need to download another file and rename it to "urlencode.sh":

[http://www.shelldorado.de/scripts/cmds/urlencode.txt](http://www.shelldorado.de/scripts/cmds/urlencode.txt)

You might need to open lotrolauncher.script and edit the wine prefix. Then simply execute the script:
```
bash /path/to/both/files/lotrolauncher.script
```

---

### Post by ajackson on 2012-05-14
The library that pylotro uses for secure web requests has a bug, so pylotro can't complete the process. The bug is known but a proper fix is still being worked out. Sadly there isn't much that can be done with pylotro to fix it.

I'm keeping my eye on the bug report in case the solution requires a tweak to pylotro but right now it is a waiting game. The windows version of pylotro should still work.

---

### Post by Scryer on 2012-05-15
I "upgraded" to Ubuntu 12.04.  Running the windows version of PyLotRO doesn't work for me - pylotro.exe from the command line.  However, the error message said nvfx threw an error.  Tracking that further I found I was running nouveau instead of nvidia driver; I thought I'd gone through a bunch of bumf to get nvidia in before because nouveau didn't do something important on LotRO - something about textures, perhaps.  I assume the 12.04 upgrade replaced that for me.  (Thanks so much.)

Does anybody successfully run LotRO with a nouveau driver?  If I replace that with nvidia is it likely I'll be able to run with the windows executable while waiting for the fix ajackson said will eventually be coming?

---

### Post by steelsnake on 2012-05-15
The windows pylotro does indeed still work.

Playing just about any 3D game with the nouveau driver isn't going to work well, if at all. So the only choice you have is to install the proprietary driver (thankfully you can do that via apt) and run the windows pylotro.

Btw, the commandline launcher suffers from the same problem - in 12.04 it won't work (at least it didn't last I checked).

---

### Post by ancalima on 2012-05-20
I understand at this point we should be using the windows version of pylotro.  This is what happens when I try to run it:
```

err:module:import_dll Library QtSvg4.dll (which is needed by L"C:\\Program Files\\PyLotRO\\qt4_plugins\\iconengines\\qsvgicon4.dll") not found
err:module:import_dll Library QtSvg4.dll (which is needed by L"C:\\Program Files\\PyLotRO\\qt4_plugins\\imageformats\\qsvg4.dll") not found
Traceback (most recent call last):
  File "<string>", line 34, in <module>
  File "PyLotRO\build\pyi.win32\pylotro\outPYZ1.pyz/PyLotROLauncher.Runner", line 33, in main
  File "PyLotRO\build\pyi.win32\pylotro\outPYZ1.pyz/PyLotROLauncher.MainWindow", line 130, in __init__
  File "PyLotRO\build\pyi.win32\pylotro\outPYZ1.pyz/PyLotROLauncher.MainWindow", line 403, in InitialSetup
  File "PyLotRO\build\pyi.win32\pylotro\outPYZ1.pyz/PyLotROLauncher.MainWindow", line 541, in GetHomeDir
AttributeError: 'NoneType' object has no attribute 'endswith'

```

running Debian squeeze, wine version 1.0.1

---

### Post by steelsnake on 2012-05-20
Wine 1.0.1 won't work.

---

### Post by ancalima on 2012-05-20
that's really odd that it won't because it's what I've been using for the past year quite successfully.  I will try to upgrade somehow, but I'm not seeing many options.  Building failed today, so we'll see what happens.

---

### Post by ajackson on 2012-06-16
I've had several requests to build a Precise version of PyLotRO, so it is now built.

---

### Post by abajto on 2012-06-18
Any idea?
I am trying to patch, but i got following text:

   rundll32.exe patchclient.dll,Patch patch.lotro.com:80 --language English --productcode LOTRO --filesonly --highres
 Connecting to patch.lotro.com:80
 

 fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
 

 Checking files...
 fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
 

 files to patch: 53 bytes to download: 143489272
 

 Patching files:
 

 err:wininet:HTTP_HttpOpenRequestW Unable to escape string!(L"/lotro/patch/1206081303/all/fr/Licenses/LUA/LUA License.txt") (-2147467261)
 

 err:wininet:HTTP_HttpOpenRequestW Unable to escape string!(L"/lotro/patch/1206081303/all/de/Licenses/LUA/LUA License.txt") (-2147467261)
 

 fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
 

 err:wininet:HTTP_HttpOpenRequestW Unable to escape string!(L"/lotro/patch/1206081303/all/fr/Licenses/LUA/LUA License.txt") (-2147467261)
 

 fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
 

 err:wininet:HTTP_HttpOpenRequestW Unable to escape string!(L"/lotro/patch/1206081303/all/de/Licenses/OggVorbis/ogg legal.txt") (-2147467261)
 

 Downloading de/Licenses/LUA/LUA License.txtFailed!
 

  Failed!
 

 fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
 

 fixme:faultrep:ReportFault 0x33f6b4 0x0 stub
 

 fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!

---

### Post by ajackson on 2012-06-19
Looks more like a problem on the patch server than anything your end. I'd try again later, maybe hit the lotro forums to see if it a known problem.

---

### Post by AshShields on 2012-07-21
So, I've been reading over this thread (and the previous) for the past two or three hours, and I've got LotRO installed and running, for the most part.

Except it crashes as soon as it encounters any major CPU, I guess. The majority of the time, I'll be able to get into the game itself, and often I can play for a while (though usually never longer than a minute or two) before the game starts to lag heavily, seemingly computer-side, as menus and things lag too. The screen periodically flashes black (usually a good ten seconds between flashes) and I am slowly able to change settings and things. I set the graphics to the lowest possible settings, and this improves, but eventually, it begins again, and crashes, giving me this error message in Wine:

```
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded

intel_do_flush_locked failed: Input/output error
```

I've been looking around the next for a half-hour or so now, and it seems that this problem (the input/output error specifically) isn't very common, effects not just LotRO, and has no apparent fix.

So, it may be a stretch, but I'm hoping someone here has encountered this and has a workaround. I'd be incredibly grateful.

Naturally, I've never encountered any graphical problems running it in Windows, but I still get the feeling it may be a graphics card/driver problem.

---

### Post by sunfromhere on 2012-09-07
I just spent a couple of hours messing with this so I will add my 2 cents in hope that Google will remember this and that the random unfortunate soul would not have to go trough my problems also. I hope I will help someone because I've run into many forum posts which go like this: Problem - exactly my problem. Solution - yeah, nvm, I fixed it. ](*,)

The Problem: After following the instructions on WineHQ for installation of LOTRO, and after running PyLotro, the PyLotro gives just a **_blank_** output screen. (not black, just white with no text and an abort button which doesn't work).

My solution: Add the PPA listed on WineHQ and install via terminal. Should an error occur, read the terminal output (mine was an issue with --force-yes part -> sudo apt-get update & sudo apt-get install --force-yes pylotro). Do not install windows exe. If the installation was successful, "pylotro" in the terminal should start it. If it wasn't, scroll trough the terminal and find what went wrong (it's a miraculous device). Do the Pylotro configuration written on the WineHQ.  This got me on the loading screen which said I was not up to date,_ afterwhich I did "winetricks ie7" _(ie6 gives an error for 64bit systems), and patched via pylotro. Ignore all the error messages and just let it run. Mine took cca half an hour. That got me to the loading screen where I discovered that dwarves in LOTRO have no females. :mad:

---

### Post by steelsnake on 2012-10-16
Just an FYI if anyone runs into it: The Rohan client released today will not work on Wine. There's a patch for it, either you'll have to recompile Wine yourself or wait until the patch trickles down into Ubuntu someday sooner or later.

Details here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=26663](http://appdb.winehq.org/objectManager.php?sClass=version&iId=26663)

---

