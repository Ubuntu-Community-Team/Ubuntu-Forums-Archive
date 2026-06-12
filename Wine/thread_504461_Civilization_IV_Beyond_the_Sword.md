---
title: "Civilization IV Beyond the Sword"
date: 2007-07-19
forum: Wine
---

### Post by conjur3r on 2007-07-19
Great news to Civ fans.  The new expansion has made its way out.  It looks like it has put a lot more focus on the end game.  Check out [http://www.2kgames.com/civ4/beyondthesword/](http://www.2kgames.com/civ4/beyondthesword/) for more information.

Civ 4 and the Warlords expansion both worked great on Cedega.  I have had Civ 4 working splendidly.

Has anyone tried to install this yet?

---

### Post by Saner on 2007-07-20
Wont even install for me :(


Thats the error I get, shame I wanted to play the expansion 

[http://442forums.net/civ4bts.png](http://442forums.net/civ4bts.png)

Wine gets further, if I have the time later I will try installing Civ 4 and BTS via Wine and then running via cedega :eek: 

But Wine seems to process far enough for it to tell me Civ 4 is not installed :d

---

### Post by Saner on 2007-07-20
Installed Civ 4 via Wine, not Cedega (had to click cancel at direct X screen)
Installed Civ 4 patch 1.61 with wine (it cryed at the end of the setup, and seemed to lose my mouse too towards the end)
Installed Civ 4 BTS via Wine (and not Cedega) (it installed the latest Civ4 patch (again?? anyways it passed it)  urgh)

> 
[email]landv@landv-desktop:~/.wine[/email]/drive_c/Program Files/Firaxis Games/Sid Meier's Civilization 4/Beyond the Sword$ cedega Civ4BeyondSword.exe
/usr/lib/transgaming_cedega/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
**Segmentation fault (core dumped)**
[email]landv@landv-desktop:~/.wine[/email]/drive_c/Program Files/Firaxis Games/Sid Meier's Civilization 4/Beyond the Sword$            


Conclusions.

I swear too much
Winex was far easier to type and remember than Cedega
Wine is a hell of a lot quicker than Cedega 
Wine installs BTS, Cedega seems not to want too.
BTS didn't work still :( so I am going to go and cry

---

### Post by conjur3r on 2007-07-21
Darn!  Why would it be so difficult when the other expansion and the original works so well :(

Now we play the waiting with uncertainty game :~

---

### Post by nucleon2k on 2007-07-22
I *had* Civ4 Vanilla 1.61 working just fine in Ubuntu, until I tried to install BTS.

BTS failed on upgrading to 1.74, so I downloaded and installed the patch manually, it seemed to go ok.  Before installing BTS, I tried to start up Civ4 vanilla 1.74, but it now crashes due to MS updating their DirectX 9.0c and not telling anyone.

I added the d3dx_32.dll file that Civ4 was complaining about missing, but now it fails with a "Error Loading Shader Libraries" message.

So now my Civ4 is completely broken, can't even play vanilla.  BTS won't install, since it forces a DirectX install, which obviously crashes wine.

Anyone figured out how to get around the problems I've listed above?  I'm ready to reinstall Civ4 so I can at least get 1.61 working again.

---

### Post by KhaaL on 2007-07-22
I get the same error as Saner... 

Bah @ not being able to play this expansion! :(

---

### Post by nwadams on 2007-07-22
ya, same problem here, might have to go back to windows partition in my dual boot for the first time in 3 weeks:(

---

### Post by nwadams on 2007-07-23
bump

---

### Post by Biffa2001 on 2007-07-24
me too :-(

---

### Post by Biffa2001 on 2007-07-24
a bit of an update - I managed to install BTS with Wine (I believe I have the latest version that was auto update with Synaptic) and there were no errors..bu I couldn't get it to run.

I tried running it directly from within Cedega (pointing the shortcut to the Wine install BTS.exe) with no joy. 

So, I have backed up my cedega Civ IV directory and am at the moment copying my Wine Civ IV folder, which includes BTS, over to my Cedega directory. 

...I will update my progress in a mo...

---

### Post by Biffa2001 on 2007-07-24
.....and it didn't work! I set up a shortcut in my Civ IV Cedega folder with the same settings as Civ IV & Civ IV Warlords to no avail.

Warlords still loaded ok tho - odd! Any help????

---

### Post by nwadams on 2007-07-24
try installing with wine into the cedega directory,,,

---

### Post by Biffa2001 on 2007-07-24
will this work or is that just a shortcut to stop me copying folders over?

(as far as I cold see when I installed BTS I wasn't given an option to install anywhere else. As I was using Wine it jsut auto used my Wine Civ IV install instead of my cedega Civ IV install).

---

### Post by nwadams on 2007-07-24
edit, sorry, no idea what i was doing

but anybody got it to work yet?

---

### Post by dalphim on 2007-07-24
Try to install the patch first

[http://www.gamespot.com/pc/strategy/civilizationivbeyondthesword/news.html?sid=6175524&om_act=convert&om_clk=newsfeatures&tag=newsfeatures;title;2](http://www.gamespot.com/pc/strategy/civilizationivbeyondthesword/news.html?sid=6175524&om_act=convert&om_clk=newsfeatures&tag=newsfeatures;title;2)

Firaxis Games' Civilization IV and its expansions Beyond the Sword and Warlords all received new patches today, updating them to versions 1.74, 3.02, and 2.13, respectively. The vanilla Civ IV and Warlords updates include support for widescreen on laptops as well as a number of crash, exploit, and bug fixes. The Beyond the Sword patch synchronizes the US and EU editions and fixes several crashes in it.

---

### Post by Biffa2001 on 2007-07-25
Just so people are aware - all the above that I tried was with the latest patches as listed above. :-)

---

### Post by yohan on 2007-07-26
Has anyone gotten around this yet?

---

### Post by nwadams on 2007-07-26
obviously not, you think they did this on purpose or by accident?

---

### Post by KhaaL on 2007-07-27
Alright guys, according to what i've heard the developers decided to move from SDL to Python in BTS thus requiring all modders to rewrite their mods to the new code...

Thats propably why we're unable to run BTS through wine/cedega

---

### Post by nwadams on 2007-07-27
do you expect us to be able to get it to work eventually, maybe after a cedega update?

---

### Post by conjur3r on 2007-07-28
Yep.  I have alot of faith invested in Cedega to get this working.  It's only a matter of time.  I'm sure they would have alot of demand for it too.

---

### Post by Mr_Tricorder on 2007-07-28
I have Civ IV with the Warlords expansion working almost perfectly in Cedega (the wonder videos mess up, but that's about it), but whenever I try to install Beyond the Sword or even the Warlords 2.13 patch it gives me this error message.
> An error (-5003 : 0xffffec75) has occurred while running the setup.

Please make sure you have finished any previous setup and closed other applications.
If the error still occurs, please contact your vendor: Firaxis Games
([http://www.2kgames.com/civ4](http://www.2kgames.com/civ4)).

Does anyone have any idea how to fix this?

---

### Post by billT on 2007-07-29
Just a quick note here: you can run vanilla Civ IV with the 1.74 update using WINE by copying the d3dx9_31 and _32 dlls into the Windows/System32 folder.

---

### Post by kstabins on 2007-07-29
I got BTS to work.... I started with a fresh .wine install, then I installed Civ4 then BTS... Once i was here i added the d3dx9_32.dll to windows/system32 because it was complaining.  After doing that i got the "Error Loading Shader Libraries".  After i saw billT's post about adding the d3dx9_31 into windows/system32 directory I put both dll's in the folder and It worked. I am using wine-0.9.42... hope everyone can get it to work its a great game

---

### Post by nucleon2k on 2007-07-29
> **billT said:**
> Just a quick note here: you can run vanilla Civ IV with the 1.74 update using WINE by copying the d3dx9_31 and _32 dlls into the Windows/System32 folder.

Just want to confirm this does work, thanks billT! Looks like I was just missing the d3dx9_31.dll file.  Civ4 vanilla 1.74 works just as well as 1.61 did for me.

However, I still can't get BTS to install under wine since the installer keeps trying to install DirectX.  Anyone have a work-around so it doesn't auto-install DirectX?

---

### Post by conjur3r on 2007-07-30
Those who have ordinary Civ 4 running in wine, how does it compare to cedega?  Is it comparative or does one work better than the other?

I was quite happy with Civ 4 in cedega - it was the only option I had at the time.  Wine wasn't able to play it.

---

### Post by nucleon2k on 2007-07-30
> **conjur3r said:**
> Those who have ordinary Civ 4 running in wine, how does it compare to cedega?  Is it comparative or does one work better than the other?

I was quite happy with Civ 4 in cedega - it was the only option I had at the time.  Wine wasn't able to play it.

Civ4 runs great in Wine (running 9.4.1), only thing Wine has trouble with are the Great Wonder cutscenes and leader's heads not displaying.   Otherwise, just as good as Windows.

---

### Post by billT on 2007-07-31
> **nucleon2k said:**
> Civ4 runs great in Wine (running 9.4.1), only thing Wine has trouble with are the Great Wonder cutscenes and leader's heads not displaying.   Otherwise, just as good as Windows.

The leader's heads display fine, you just have to add a add an entry to the registry. The wonder videos are also fine for me (may also be related to the registry, I don't know). Check out the second to last comment on the [winehq page]("http://appdb.winehq.org/appview.php?iVersionId=5254") for details.

---

### Post by kuratko on 2007-07-31
> **kstabins said:**
> I got BTS to work.... I started with a fresh .wine install, then I installed Civ4 then BTS... Once i was here i added the d3dx9_32.dll to windows/system32 because it was complaining.  After doing that i got the "Error Loading Shader Libraries".  After i saw billT's post about adding the d3dx9_31 into windows/system32 directory I put both dll's in the folder and It worked. I am using wine-0.9.42... hope everyone can get it to work its a great game

kstabins, your BTS install did not try to install directx? How did you worked around it?

---

### Post by Mishok on 2007-07-31
I have also had problems installing BTS. Wine seems to crash just after checking for my DirectX info. If anybody knows how to fix this, your help would be greatly appreciated.

Ohh, and since this is my first post on the forums, I just want to say Hi to everyone :)

---

### Post by kstabins on 2007-08-01
I always just hit cancel when the DirectX tries to install...  It usually just skips it and tries to install the game.  After the game installs manually put the two DLL's into the windows system32 directory.

---

### Post by nucleon2k on 2007-08-01
> **kstabins said:**
> I always just hit cancel when the DirectX tries to install...  It usually just skips it and tries to install the game.  After the game installs manually put the two DLL's into the windows system32 directory.

BTS doesn't give you an option to cancel a pending DirectX install, it just goes right ahead and tries to install it without asking for your permission.  That's the problem we all seem to be having, how do you bypass an automatic installation?  Only Vanilla and Warlords give you an option to cancel a DirectX install.

---

### Post by kstabins on 2007-08-02
Ahh I understand now. Sorry I am using Gentoo not Ubuntu and i guess wine works differently on the Distros...  I just reinstalled the game to see what happens with DirextX and it completes with no complaints so im not sure what to tell you :(

sorry

---

### Post by conjur3r on 2007-08-04
Looks like there's been a bit of discussion over on the cedega forums: [http://www.cedega.com/forum/viewtopic.php?t=8658&highlight=civilization](http://www.cedega.com/forum/viewtopic.php?t=8658&highlight=civilization)

No successes yet though.  It's also got enough votes in order for the cedega team to look into it.

---

### Post by TabJones on 2007-08-22
i managed to install BTS with wine-0.9.43 and to play! what i did:

install civ4 normally, then i applied manually the 1.61 patch. after that i put into my system32 the d3dx9_26.dll lib and tried to play. everything works.

then i started to install BTS. the installer didn't try to install the directx (probably because i put that dll before install process, but i'm not sure about it) and installation went perfectly fine till the end.

After that i put another 2 dlls in system32 d3dx9_32.dll and d3dx9_31.dll and play.
Everything seems to work great so far. Enjoy! 

EDIT:someone told me that also d3dx9_33.dll is needed, you can try that dll too.

EDIT: i'm using Gentoo and not Ubuntu, i don't really know if this matters or not, but i guess you can still try this process on your ubuntu. hope this helps. bye bye

---

### Post by teo_m on 2007-08-23
> **TabJones said:**
> i managed to install BTS with wine-0.9.43 and to play! what i did:

install civ4 normally, then i applied manually the 1.61 patch. after that i put into my system32 the d3dx9_26.dll lib and tried to play. everything works.

then i started to install BTS. the installer didn't try to install the directx (probably because i put that dll before install process, but i'm not sure about it) and installation went perfectly fine till the end.

After that i put another 2 dlls in system32 d3dx9_32.dll and d3dx9_31.dll and play.
Everything seems to work great so far. Enjoy! 

EDIT:someone told me that also d3dx9_33.dll is needed, you can try that dll too.

EDIT: i'm using Gentoo and not Ubuntu, i don't really know if this matters or not, but i guess you can still try this process on your ubuntu. hope this helps. bye bye

Are you running x86 or amd64? Because on my Gentoo ~amd64 it keeps trying to install DirectX even with your dlls.

---

### Post by MFonville on 2007-08-24
After a lot of reading on the web and trying to decipher some Finnish on the Finnish ubuntu forum I found out how to install Civilization 4 WITH Beyond the Sword with the latest Wine on Linux

Copy from a windows install the files:
c:\windows\system32\msvcr71.dll msvcp71.dll d3dx9_31.dll d3dx9_32.dll d3dx9_33.dll msxml3.dll msxml3r.dll d3dx9.dll mscoree.dll

to your .wine/windows/system32/

Next install Civ4
Next install the Civ4 1.74 patch
Next install Civ4 BtS

Next follow the instructions from [http://wiki.winehq.org/NativeMSXML3](http://wiki.winehq.org/NativeMSXML3) to install MSXML3 (at least on amd64, not sure for i386)

Have fun playing!

(This worked for me on Kubuntu AMD64)

---

### Post by TabJones on 2007-08-25
> **teo_m said:**
> Are you running x86 or amd64? Because on my Gentoo ~amd64 it keeps trying to install DirectX even with your dlls.
~x86 arch.

---

### Post by Biffa2001 on 2007-08-28
> **MFonville said:**
> 
Copy from a windows install the files:
c:\windows\system32\msvcr71.dll msvcp71.dll d3dx9_31.dll d3dx9_32.dll d3dx9_33.dll msxml3.dll msxml3r.dll d3dx9.dll mscoree.dll

to your .wine/windows/system32/

d3dx9.dll doesnt seem to exist (on either my PC or the net) - do a google and you will find the same!

Where did you get it from please?

Cheers
Steve

---

### Post by teo_m on 2007-08-28
> **Biffa2001 said:**
> d3dx9.dll doesnt seem to exist (on either my PC or the net) - do a google and you will find the same!

Where did you get it from please?

Cheers
Steve

d3dx9.dll as I understand it, seems to be a copy of the most recent d3dx9_xx.dll.

---

### Post by Biffa2001 on 2007-08-28
ok - where can I get it from?

---

### Post by teo_m on 2007-08-28
> **Biffa2001 said:**
> ok - where can I get it from?

I made a copy of my d3dx9_33.dll

---

### Post by Biffa2001 on 2007-08-28
ok thanks, I will give that a try :-)

---

### Post by nucleon2k on 2007-08-28
I've tried it with the latest suggestions to include all d3d9 files including the d3dx9.dll file (a copy of the d3dx9_33.dll) and BTS still won't get past its attempt at installing DirectX.

If only Firaxis gave us a choice to install it or not ...

FYI running Ubuntu 7.04 32bit, Civ4 Vanilla 1.74.

---

### Post by lulu135 on 2007-08-30
You can fix the shader message by downloading d3dx9_31.dll from [http://www.dll-files.com/dllindex/dll-files.shtml?d3dx9_31](http://www.dll-files.com/dllindex/dll-files.shtml?d3dx9_31)

For some reason you need both 31 and 32.

---

### Post by lulu135 on 2007-08-30
I installed BTS on a real Windows machine and just copied the Beyond the Sword folder into my wine folder.  It starts up, but I get a "failed to initialize python" message at the initialization.  Anyone else get farther?

---

### Post by MFonville on 2007-08-31
> **nucleon2k said:**
> I've tried it with the latest suggestions to include all d3d9 files including the d3dx9.dll file (a copy of the d3dx9_33.dll) and BTS still won't get past its attempt at installing DirectX.

If only Firaxis gave us a choice to install it or not ...

FYI running Ubuntu 7.04 32bit, Civ4 Vanilla 1.74.

you can try to create a 'fresh' wine before install. It helped me in the process :)

If you have no other apps in wine installed you can delete .wine in your home folder, next run 'wineprefixcreate' from a console.

---

### Post by o3rat on 2007-09-05
> **MFonville said:**
> you can try to create a 'fresh' wine before install. It helped me in the process :)

If you have no other apps in wine installed you can delete in your home folder, next run 'wineprefixcreate' from a console.

Ok, i will try that. I installed civ4 just fine, but BTS install still crashes on directx.

---

### Post by conjur3r on 2007-09-08
I'm with nucleon_2k.  I can't get past the BtS directX install.  I've followed the instructions MFonville provided above twice (first cancelling the directx install from Civ4, and second accepting the install - wiping the wine directory in between).

It goes up to install directx and then a whole lot of messages are printed out in the console and then eventually dies and closes the window.

I've tried on Ubuntu 7.04, 32bits.

---

### Post by o3rat on 2007-09-09
Hmm, i have another problem now. I installed Civ4, patched it to 1.74. When I try to run it, it freezes on Init Audio. Any ideas?

---

### Post by nucleon2k on 2007-09-09
> **o3rat said:**
> Hmm, i have another problem now. I installed Civ4, patched it to 1.74. When I try to run it, it freezes on Init Audio. Any ideas?

Make sure you have all the d3dx9 DLL files that are discussed in this thread 28,29,30, etc).  That should resolve your issues with 1.74.

---

### Post by Micoz on 2007-09-21
After doing this:

> **MFonville said:**
> After a lot of reading on the web and trying to decipher some Finnish on the Finnish ubuntu forum I found out how to install Civilization 4 WITH Beyond the Sword with the latest Wine on Linux

Copy from a windows install the files:
c:\windows\system32\msvcr71.dll msvcp71.dll d3dx9_31.dll d3dx9_32.dll d3dx9_33.dll msxml3.dll msxml3r.dll d3dx9.dll mscoree.dll

to your .wine/windows/system32/

Next install Civ4
Next install the Civ4 1.74 patch
Next install Civ4 BtS

Next follow the instructions from [http://wiki.winehq.org/NativeMSXML3](http://wiki.winehq.org/NativeMSXML3) to install MSXML3 (at least on amd64, not sure for i386)

Have fun playing!

(This worked for me on Kubuntu AMD64)

I get bug with xml:
Caught unhandled exception creating XML parser object:
**[http://img519.imageshack.us/img519/681/xmlsb1.jpg]("http://img519.imageshack.us/img519/681/xmlsb1.jpg")**

Do you have any solutions?

---

### Post by MFonville on 2007-09-21
The step of:

[http://wiki.winehq.org/NativeMSXML3](http://wiki.winehq.org/NativeMSXML3) to install MSXML3 

should take care of that error :)

---

### Post by Micoz on 2007-09-21
Should have taken is well said. So any ideas what i should do to make it runnable? Ive done everything listed over this post, even with installation of native msxml3. Any specific clues with this instalation ?

---

### Post by MFonville on 2007-09-23
Hmm, have you tried setting your emulation to Windows XP with 'winecfg'?

---

### Post by Micoz on 2007-09-25
Will try soon and tell what results i was given.

---

### Post by Biffa2001 on 2007-09-25
very odd, I have just given it another try to install and this time it worked ok, ran all the way through and installed ok.....but it wont start at alll!!

I´ve not much hair left to pull out! :guitar:

---

### Post by Beamvr6 on 2007-10-03
I've just got BtS running in 6.0.6 with Cedega 6 something (from about June 2007) and got screenshots to prove. :) :) :)

I had done all the DirectX stuff already and still no go until I DLed the no-CD from Gamecopyworld today.

Worth noting is I only have Civ IV Vanilla installed thru Cedega and I run both Warlords and BtS from an XP install. Main reason for this is most mods from say CFC come with Windoze installers so easiest to install them there.

I really hope this helps other ppl to run BtS in Ubuntu even if you need to do the actual install in Windoze. Also I quit my Cedega account so if somebody can make it work this way and can post at Transgaming please spread the word!

---

### Post by Scotty562 on 2007-10-17
I got it running in wine, but all of the cities are very dark and I can't see the progress of production in my cities. Did any of you guys experience this and/or figure out how to fix it?

---

### Post by Yeeha on 2007-10-17
Yeah i got working too with wine 0.9.47 and 3.13 patch but most objects are black and it seems wine cant handle those objects since console spams - fixme:d3d:state_lastpixel Last Pixel Drawing Disabled, not handled yet.
But if i am wrong and theres a way to get game running without black objects tell how plz :).

---

### Post by beermotor on 2007-10-18
> **MFonville said:**
> After a lot of reading on the web and trying to decipher some Finnish on the Finnish ubuntu forum I found out how to install Civilization 4 WITH Beyond the Sword with the latest Wine on Linux

Copy from a windows install the files:
c:\windows\system32\msvcr71.dll msvcp71.dll d3dx9_31.dll d3dx9_32.dll d3dx9_33.dll msxml3.dll msxml3r.dll d3dx9.dll mscoree.dll

to your .wine/windows/system32/

Next install Civ4
Next install the Civ4 1.74 patch
Next install Civ4 BtS

Next follow the instructions from [http://wiki.winehq.org/NativeMSXML3](http://wiki.winehq.org/NativeMSXML3) to install MSXML3 (at least on amd64, not sure for i386)

Have fun playing!

(This worked for me on Kubuntu AMD64)


Ok, I've tried this a couple times now.  First, Vanilla installed fine, but then BTS crashed somehow during the install (it wouldn't recognize that I had CD2 in my other drive, and wouldn't let me eject CD1 to put in CD2) and so I did a sudo rm -R .wine and ran winecfg to set up wine again in my home directory.  Then I installed Vanilla which puked at the very end of installing the 1.74 patch.  No idea what happened - but now BTS refuses to install, says there is a previous install, etc etc.

What gives?  (Ubuntu P4 blah blah).

---

### Post by KhaaL on 2007-10-18
I envy you guys. I can't even run vanilla Civ4 because of the ""Caught unhandled exception creating XML parser object blah blah" error. Even though i copied over all the dll's.

I guess i should give it a new try...

---

### Post by Yeeha on 2007-10-19
i got that xml parser error when i had set win98 mode, so make sure u run in win2k mode.

---

### Post by zorkerz on 2007-10-23
check this out on the wine beyond the sword page [http://appdb.winehq.org/objectManager.php?sClass=version&iId=8788&iTestingId=15863](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8788&iTestingId=15863)
It requires installing and cracking everything in xp then copying it over. So obviously this will not work for many unless you use a friend and an external drive or something. Im finally going to put my vista partition to good use and see if it works with windows besides xp.
hope that helps someone
cheers

---

### Post by nucleon2k on 2007-10-23
> **zorkerz said:**
> check this out on the wine beyond the sword page [http://appdb.winehq.org/objectManager.php?sClass=version&iId=8788&iTestingId=15863](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8788&iTestingId=15863)
It requires installing and cracking everything in xp then copying it over. So obviously this will not work for many unless you use a friend and an external drive or something. Im finally going to put my vista partition to good use and see if it works with windows besides xp.
hope that helps someone
cheers

I will confirm this solution works perfectly.  I set up a Windows XP virtual machine, installed Civ4 + BTS, installed no-cd cracks and then copied the folder over to Linux.  Both vanilla Civ4 and BTS work great.

---

### Post by zorkerz on 2007-10-24
help im close. I followed the instructions from the link in post 64 with only three differences that I do not think matter.
-> civ was installed in vista not xp
-> used version 1.74 of civ IV (not 1.61) and 2.13 of warlords not (2.08)
-> have the civ file on a different install path

It takes an extremely long time for either of the three to open. Like in the range of 5 to 10 minutes.

Once in a can navigate the menus but before i start a game the colors get distorted and I am logged off of ubuntu.

Is the terminal output saved anywhere so that I can see what happened?

any other ideas?

This is a thinkpad x61 with intel x3100 graphics running 64 but gutsy and wine 0.9.47 -> let me know if anything else is helpful

thanks

Update: 5 to ten minutes may have been an underestimate its now been 21 minutes and BTS has still not gone into full screen. The computer is not showing any cpu load during this time its even in C3 sleep state according to powertop.

Here is my terminal output of the currently attempting to start BTS in case anyone is interested.
```

wine '/home/estle/media/games/civiv/Beyond the Sword/Civ4BeyondSword.exe' 
ALSA lib ../../src/conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for Z:\home\estle\media\games\civiv\Beyond the Sword\Logs.lnk
fixme:shell:DllCanUnloadNow stub
fixme:winhttp:WinHttpCheckPlatform stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for Z:\home\estle\media\games\civiv\Beyond the Sword\Saves.lnk
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for Z:\home\estle\media\games\civiv\Beyond the Sword\CivilizationIV.ini.lnk
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10024 0x00000000
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "<string>", line 2, in ?
IOError: [Errno 2] No such file or directory: 'c:\\windows\\profiles\ninor\\My Documents\\My Games\\Beyond the Sword\\Logs\\PythonErr2.log'
fixme:win:EnumDisplayDevicesW ((null),0,0x33ef88,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f4c0,0x00000000), stub!
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:system:SystemParametersInfoW Unim

```
oh there it goes it started after 30 minutes.

---

### Post by Biffa2001 on 2007-10-24
I also get the following error:

```
]fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x8b0, disabling mixer
fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\Firaxis Games\Sid Meier's Civilization 4\Beyond the Sword\Logs.lnk
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\Firaxis Games\Sid Meier's Civilization 4\Beyond the Sword\Saves.lnk
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:msxml:schema_cache_add (0x15aee8)->(L"x-schema:CIV4GameInfoSchema.xml", var(vt 9)): stub
fixme:msxml:domdoc_putref_schemas (0x15af00): semi-stub
fixme:msxml:domdoc_putref_schemas (0x15af00): semi-stub
wine: Unhandled page fault on read access to 0x00000000 at address 0x1d89cad (thread 002d), starting debugger...
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x01d89cad).
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\Firaxis Games\Sid Meier's Civilization 4\Beyond the Sword\CivilizationIV.ini.lnk
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:01d89cad ESP:0033fa60 EBP:01d87f20 EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000000 EBX:00000000 ECX:00000000 EDX:014e004c
 ESI:0a0eb0c0 EDI:00000000
Stack dump:
0x0033fa60:  004d49ef 00000000 0a0e9a3c 0a0e53e4
0x0033fa70:  014e52c4 0000000d 004d47d8 014e52c4
0x0033fa80:  0033fa98 00a6c30b 00000007 004d4981
0x0033fa90:  0a0eb0c0 0a0eb0c0 0033fbe4 00a7a29b
0x0033faa0:  00000000 0040b0fa 014e5230 014e5360
0x0033fab0:  014e5230 00000000 0a0e9b14 00000000
Backtrace:
=>1 0x01d89cad in cvgamecoredll (+0xc9cad) (0x01d87f20)
  2 0xccccc300 (0x000016b8)
  3 0x00000000 (0x00000000)
0x01d89cad: movl        0x0(%eax),%eax
Modules:
Module  Address                 Debug info      Name (102 modules)
PE        340000-  353000       Deferred        zlib1
PE        360000-  36e000       Deferred        hapdbg
PE        400000- 1057bc2       Deferred        civ4beyondsword
PE       1060000- 13cf000       Deferred        d3dx9_33
PE       1cc0000- 2164000       Export          cvgamecoredll
PE      10000000-1002b000       Deferred        boost_python-vc71-mt-1_32
PE      18000000-18038000       Deferred        binkw32
PE      1e000000-1e1ca000       Deferred        python24
PE      21100000-2118c000       Deferred        mss32
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
PE      7c340000-7c396000       Deferred        msvcr71
PE      7c3a0000-7c41b000       Deferred        msvcp71
ELF     7c4a9000-7c4c9000       Deferred        mpr<elf>
  \-PE  7c4b0000-7c4c9000       \               mpr
ELF     7c4c9000-7c513000       Deferred        wininet<elf>
  \-PE  7c4d0000-7c513000       \               wininet
ELF     7c513000-7c54f000       Deferred        urlmon<elf>
  \-PE  7c520000-7c54f000       \               urlmon
ELF     7c54f000-7c583000       Deferred        libxslt.so.1
ELF     7c583000-7c6a0000       Deferred        libxml2.so.2
ELF     7c6a0000-7c6cd000       Deferred        msxml3<elf>
  \-PE  7c6b0000-7c6cd000       \               msxml3
ELF     7c6cd000-7c6e2000       Deferred        midimap<elf>
  \-PE  7c6d0000-7c6e2000       \               midimap
ELF     7c6e2000-7c708000       Deferred        msacm32<elf>
  \-PE  7c6f0000-7c708000       \               msacm32
ELF     7c708000-7c720000       Deferred        msacm32<elf>
  \-PE  7c710000-7c720000       \               msacm32
ELF     7c720000-7c7e5000       Deferred        libasound.so.2
ELF     7c7f8000-7c82e000       Deferred        winealsa<elf>
  \-PE  7c800000-7c82e000       \               winealsa
ELF     7c86b000-7c888000       Deferred        imm32<elf>
  \-PE  7c870000-7c888000       \               imm32
ELF     7d493000-7d4c5000       Deferred        uxtheme<elf>
  \-PE  7d4a0000-7d4c5000       \               uxtheme
ELF     7d4c5000-7d4ca000       Deferred        libxfixes.so.3
ELF     7d4ca000-7d4d3000       Deferred        libxcursor.so.1
ELF     7d4d3000-7d4db000       Deferred        libxrender.so.1
ELF     7da14000-7e29a000       Deferred        libglcore.so.1
ELF     7e29a000-7e326000       Deferred        libgl.so.1
ELF     7e326000-7e32b000       Deferred        libxdmcp.so.6
ELF     7e32b000-7e41c000       Deferred        libx11.so.6
ELF     7e41c000-7e42a000       Deferred        libxext.so.6
ELF     7e42a000-7e42f000       Deferred        libxxf86vm.so.1
ELF     7e42f000-7e447000       Deferred        libice.so.6
ELF     7e447000-7e450000       Deferred        libsm.so.6
ELF     7e453000-7e459000       Deferred        libxrandr.so.2
ELF     7e463000-7e4ee000       Deferred        winex11<elf>
  \-PE  7e470000-7e4ee000       \               winex11
ELF     7e5f7000-7e617000       Deferred        libexpat.so.1
ELF     7e617000-7e642000       Deferred        libfontconfig.so.1
ELF     7e642000-7e656000       Deferred        libz.so.1
ELF     7e656000-7e6c1000       Deferred        libfreetype.so.6
ELF     7e6c1000-7e70a000       Deferred        dsound<elf>
  \-PE  7e6d0000-7e70a000       \               dsound
ELF     7e70a000-7e7a8000       Deferred        oleaut32<elf>
  \-PE  7e720000-7e7a8000       \               oleaut32
ELF     7e7a8000-7e801000       Deferred        rpcrt4<elf>
  \-PE  7e7b0000-7e801000       \               rpcrt4
ELF     7e801000-7e8a2000       Deferred        ole32<elf>
  \-PE  7e810000-7e8a2000       \               ole32
ELF     7e8a2000-7e8b6000       Deferred        lz32<elf>
  \-PE  7e8b0000-7e8b6000       \               lz32
ELF     7e8b6000-7e8d0000       Deferred        version<elf>
  \-PE  7e8c0000-7e8d0000       \               version
ELF     7e8d0000-7e8e3000       Deferred        libresolv.so.2
ELF     7e8e4000-7e8e7000       Deferred        libxau.so.6
ELF     7e8f6000-7e914000       Deferred        iphlpapi<elf>
  \-PE  7e900000-7e914000       \               iphlpapi
ELF     7e914000-7e941000       Deferred        ws2_32<elf>
  \-PE  7e920000-7e941000       \               ws2_32
ELF     7e941000-7e9cf000       Deferred        winmm<elf>
  \-PE  7e950000-7e9cf000       \               winmm
ELF     7e9cf000-7ea37000       Deferred        msvcrt<elf>
  \-PE  7e9e0000-7ea37000       \               msvcrt
ELF     7ea37000-7eaf5000       Deferred        comctl32<elf>
  \-PE  7ea40000-7eaf5000       \               comctl32
ELF     7eaf5000-7eb4e000       Deferred        shlwapi<elf>
  \-PE  7eb00000-7eb4e000       \               shlwapi
ELF     7eb4e000-7ec51000       Deferred        shell32<elf>
  \-PE  7eb60000-7ec51000       \               shell32
ELF     7ec51000-7ec9a000       Deferred        advapi32<elf>
  \-PE  7ec60000-7ec9a000       \               advapi32
ELF     7ec9a000-7ed35000       Deferred        gdi32<elf>
  \-PE  7ecb0000-7ed35000       \               gdi32
ELF     7ed35000-7ee73000       Deferred        user32<elf>
  \-PE  7ed50000-7ee73000       \               user32
ELF     7efa4000-7efaf000       Deferred        libnss_files.so.2
ELF     7efaf000-7efc6000       Deferred        libnsl.so.1
ELF     7efc6000-7efed000       Deferred        libm.so.6
ELF     7efed000-7efef000       Deferred        libnvidia-tls.so.1
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7ca1000-b7caa000       Deferred        libnss_compat.so.2
ELF     b7cab000-b7caf000       Deferred        libdl.so.2
ELF     b7caf000-b7df0000       Deferred        libc.so.6
ELF     b7df1000-b7e08000       Deferred        libpthread.so.0
ELF     b7e1b000-b7f2f000       Deferred        libwine.so.1
ELF     b7f31000-b7f4c000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000002e (D) C:\Program Files\Firaxis Games\Sid Meier's Civilization 4\Beyond the Sword\Civ4BeyondSword.exe
        0000002d    0 <==
0000000a 
        0000000c    0
        0000000b    0
00000008 
        0000000f    0
        0000000e    0
        0000000d    0
        00000009    0
```

---

### Post by zorkerz on 2007-10-25
so it appears my crash that logged me out of ubuntu was due to vertex shaders being enabled. 

I still occasionally get the problem where the game takes extreme amounts of time to open.

Unfortunately for me BTS is so slow in my computer its unplayable at the moment. Has anyone else played BTS with an intel x3100. Its an integrated card but i would have thought it could play games as old as civ IV it would be a huge bummer if it did not. I will have to try in vista see if it works there.

cheers

---

### Post by zorkerz on 2007-10-26
I tried BTS in vista it works fine with no lag (took significantly longer to load though). This is unfortunate but good because it means someday hopefully wine will be up to the task of playing BTS well enough for my computer.

It still occasionally gets stuck on init engine just before going to full screen. It eventually gets unstuck but it has taken as long as 40 minutes (I let it run in the background).

I guess this is goodbye for now from me until wine improves

cheers all

---

### Post by o3rat on 2007-10-26
@zorkerz

I have an intel x3100 too. My game takes a long time to load on and hangs for a bit on 'Init Audio.' Once the game loads i can run through all the menus and set up a custom game, but after I press launch when it gets to 'Finishing' the game graphics crash, (im guessing its the shader problem)

---

### Post by zorkerz on 2007-10-27
What is your crash like?
I got logged out and disabling vertex shaders fixed it.

---

### Post by o3rat on 2007-10-27
My initial game crash was just before it launched a new custom game, on the 'Finishing' Step. I then disable vertex shaders in wine, go into a game, but it was just too slow. So im assuming that its a intel x3100 driver issue.

---

### Post by zorkerz on 2007-10-28
Do you know exactly what the driver issue is? Is it that the linux drivers are not complete or functioning well? I played the game in vista on this computer and ran just fine and vista is a huge resource hog.

---

### Post by o3rat on 2007-10-28
I'm not really sure if that is the problem, but that is what I'm assuming because I can run the game fine in XP.

---

### Post by zorkerz on 2007-10-28
Ya i hear that. Though the other place that i think could contribute more to the problem is wine's implementation itself.

room for improvement:

-x3100 linux drivers

-wine implementation

Is there anywhere else that could cause serious performance lags?

at least both of these i would imagine would improve at a pretty significant rate.

---

### Post by nalmeth on 2007-10-28
Somewhat related to thread topic, just for reference, To Whom It May Concern:
On an Intel 965G integrated graphics card, I have had a damn trouble getting this game working.

With vertex shaders enabled, and anything other than WinXP set for Civ4, X crashes to GDM when its about to start the game (just when initial load finishes). 

I got the game to start and play on wine .48, but the scenario was ALL dark. Completely black. I could see characters but not terrain.

Game doesn't work for me in Cedega (crashes X), and doesn't work in wine .44, or .48 (only worked at all on .47 ).

I would assume the expansion will not work either :(

I'm going to try on my PC with an Nvidia card to see if it runs better... Good luck everyone

---

### Post by KhaaL on 2007-11-15
Today I gave it a shot, and in the middle of trying to get warlods setup (since I want to play a mod requiring it and bts) I messed up majorly making myself unable to run wineconf. I had of course to remove my ~./wine directory. And I had taken a *lot* of steps to get there...

Isn't it possible to make a script to automate the whole tiresome process?

---

### Post by nwadams on 2007-12-02
ok, so I got 1.74 working perfectly...but my BTS install keeps crashing when it does the directx install, i have d3dx9_31.dll,  d3dx9_32.dll and d3dx9_33.dll in my windows/system 32 folder
i also set msxml3 to native mode (didn't copy dll)

how do i get BTS installed...

---

### Post by KhaaL on 2007-12-03
> The game dosen't work unless you have the following DLLs in your system32 folder: d3dx9_26.dll d3dx9_32.dll mscoree.dll msxml3.dll d3dx9_31.dll d3dx9_33.dll msvcp71.dll msxml3r.dll mscoree.dll and msvcp71.dll. Notice that you need mscoree and msvcp71 only for BTS, vanilla dosen't require them. Also, you don't need any additional DLL overrides except for msxml3 (native).

Taken from [appdb]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9501")

---

### Post by sojusnik on 2007-12-03
Is it possible to play Civ IV with all addons and latest patches with WINE via Internet with a pal who has the same configuration on Windows XP?

---

### Post by Melhisedek on 2007-12-03
> **Micoz said:**
> 
I get bug with xml:
Caught unhandled exception creating XML parser object:
**[http://img519.imageshack.us/img519/681/xmlsb1.jpg]("http://img519.imageshack.us/img519/681/xmlsb1.jpg")**

Do you have any solutions?

I get the exact same problem... installed MSXML3 and all still no go :/ Any ideas?

---

### Post by nwadams on 2007-12-03
omg, i got it to work, ok, for th msxml3, in the warlords and bts folder there is a msxml3.dll file, delete it
and in wincfg, set mslxml3 to native

---

### Post by Melhisedek on 2007-12-03
Did all that still no go... now I get the wine window and than it just dissapears :/

Here is the output:
```

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:rpc:I_RpcServerStopListening (): stub
fixme:rpc:I_RpcWindowProc (0x10024,00000002,00000000,00000000): stub
fixme:rpc:I_RpcWindowProc (0x10024,00000082,00000000,00000000): stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\Firaxis Games\Sid Meier's Civilization 4\Beyond the Sword\Saves.lnk
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:shell:DllCanUnloadNow stub
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:shell:DllCanUnloadNow stub
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:shell:DllCanUnloadNow stub
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:shell:DllCanUnloadNow stub
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:shell:DllCanUnloadNow stub
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:shell:DllCanUnloadNow stub
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:shell:DllCanUnloadNow stub
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\Firaxis Games\Sid Meier's Civilization 4\Beyond the Sword\CivilizationIV.ini.lnk
fixme:msxml:schema_cache_add (0x121bd8)->(L"x-schema:CIV4GameInfoSchema.xml", var(vt 9)): stub
fixme:msxml:domdoc_putref_schemas (0x121bf0): semi-stub
fixme:msxml:domdoc_putref_schemas (0x121bf0): semi-stub
wine: Unhandled page fault on read access to 0x00000000 at address 0x229ef0d (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x0229ef0d).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0229ef0d ESP:0034fa4c EBP:0229cfd0 EFLAGS:00010212(   - 00      - RIA1)
 EAX:00000000 EBX:00000000 ECX:00000000 EDX:015f004c
 ESI:0a5fd838 EDI:00000000
Stack dump:
0x0034fa4c:  004d612f 00000000 0a5fc104 015f52cc
0x0034fa5c:  015f5238 0000000d 004d5f18 015f52cc
0x0034fa6c:  0034fa84 00a6e7fb 00000007 004d60c1
0x0034fa7c:  0a5fd838 0a5fd838 0034fbe4 00a7cb4b
0x0034fa8c:  00000000 0040b0fa 015f5238 015f5368
0x0034fa9c:  015f5238 00000000 0a5fc40c 0a5f8424
Backtrace:
=>1 0x0229ef0d in cvgamecoredll (+0xcef0d) (0x0229cfd0)
  2 0xccccc300 (0x000016b8)
  3 0x00000000 (0x00000000)
0x0229ef0d: movl        0x0(%eax),%eax
Modules:
Module  Address                 Debug info      Name (98 modules)
PE        350000-  35e000       Deferred        hapdbg
PE        360000-  373000       Deferred        zlib1
PE        400000- 105317e       Deferred        civ4beyondsword
PE       1060000- 13cf000       Deferred        d3dx9_33
PE       21d0000- 267f000       Export          cvgamecoredll
PE      10000000-1002b000       Deferred        boost_python-vc71-mt-1_32
PE      18000000-18038000       Deferred        binkw32
PE      1e000000-1e1ca000       Deferred        python24
PE      21100000-2118c000       Deferred        mss32
PE      65340000-653d2000       Deferred        oleaut32
PE      65f00000-65fc2000       Deferred        ole32
ELF     7b800000-7b92b000       Deferred        kernel32<elf>
  \-PE  7b820000-7b92b000       \               kernel32
ELF     7bc00000-7bca2000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca2000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
PE      7c340000-7c396000       Deferred        msvcr71
PE      7c3a0000-7c41b000       Deferred        msvcp71
ELF     7e09d000-7e0be000       Deferred        mpr<elf>
  \-PE  7e0a0000-7e0be000       \               mpr
ELF     7e0be000-7e10a000       Deferred        wininet<elf>
  \-PE  7e0d0000-7e10a000       \               wininet
ELF     7e10a000-7e146000       Deferred        urlmon<elf>
  \-PE  7e110000-7e146000       \               urlmon
ELF     7e146000-7e17a000       Deferred        libxslt.so.1
ELF     7e17a000-7e298000       Deferred        libxml2.so.2
ELF     7e2a8000-7e2d5000       Deferred        msxml3<elf>
  \-PE  7e2b0000-7e2d5000       \               msxml3
ELF     7e2d5000-7e331000       Deferred        rpcrt4<elf>
  \-PE  7e2e0000-7e331000       \               rpcrt4
ELF     7e3bf000-7e3f1000       Deferred        uxtheme<elf>
  \-PE  7e3d0000-7e3f1000       \               uxtheme
ELF     7e3f1000-7e406000       Deferred        midimap<elf>
  \-PE  7e400000-7e406000       \               midimap
ELF     7e406000-7e42d000       Deferred        msacm32<elf>
  \-PE  7e410000-7e42d000       \               msacm32
ELF     7e42d000-7e445000       Deferred        msacm32<elf>
  \-PE  7e430000-7e445000       \               msacm32
ELF     7e445000-7e481000       Deferred        wineoss<elf>
  \-PE  7e450000-7e481000       \               wineoss
ELF     7e481000-7e48a000       Deferred        libxcursor.so.1
ELF     7e48a000-7e4a7000       Deferred        imm32<elf>
  \-PE  7e490000-7e4a7000       \               imm32
ELF     7e4a7000-7e4af000       Deferred        libxrender.so.1
ELF     7e4bf000-7e55f000       Deferred        libgl.so.1
ELF     7e55f000-7e564000       Deferred        libxdmcp.so.6
ELF     7e564000-7e567000       Deferred        libxau.so.6
ELF     7e567000-7e658000       Deferred        libx11.so.6
ELF     7e658000-7e666000       Deferred        libxext.so.6
ELF     7e666000-7e66b000       Deferred        libxxf86vm.so.1
ELF     7e66b000-7e683000       Deferred        libice.so.6
ELF     7e683000-7e68b000       Deferred        libsm.so.6
ELF     7e68d000-7e692000       Deferred        libxfixes.so.3
ELF     7e692000-7e695000       Deferred        libxcomposite.so.1
ELF     7e695000-7e69b000       Deferred        libxrandr.so.2
ELF     7e69b000-7e729000       Deferred        winex11<elf>
  \-PE  7e6b0000-7e729000       \               winex11
ELF     7e7a0000-7e7c0000       Deferred        libexpat.so.1
ELF     7e7c0000-7e7eb000       Deferred        libfontconfig.so.1
ELF     7e7eb000-7e800000       Deferred        libz.so.1
ELF     7e800000-7e870000       Deferred        libfreetype.so.6
ELF     7e870000-7e8d8000       Deferred        msvcrt<elf>
  \-PE  7e880000-7e8d8000       \               msvcrt
ELF     7e8d8000-7e8eb000       Deferred        libresolv.so.2
ELF     7e8fb000-7e919000       Deferred        iphlpapi<elf>
  \-PE  7e900000-7e919000       \               iphlpapi
ELF     7e919000-7e946000       Deferred        ws2_32<elf>
  \-PE  7e920000-7e946000       \               ws2_32
ELF     7e946000-7e95a000       Deferred        lz32<elf>
  \-PE  7e950000-7e95a000       \               lz32
ELF     7e95a000-7e974000       Deferred        version<elf>
  \-PE  7e960000-7e974000       \               version
ELF     7e974000-7ea33000       Deferred        comctl32<elf>
  \-PE  7e980000-7ea33000       \               comctl32
ELF     7ea33000-7ea8c000       Deferred        shlwapi<elf>
  \-PE  7ea40000-7ea8c000       \               shlwapi
ELF     7ea8c000-7eb90000       Deferred        shell32<elf>
  \-PE  7eaa0000-7eb90000       \               shell32
ELF     7eb90000-7ec28000       Deferred        gdi32<elf>
  \-PE  7eba0000-7ec28000       \               gdi32
ELF     7ec28000-7ed65000       Deferred        user32<elf>
  \-PE  7ec40000-7ed65000       \               user32
ELF     7ed65000-7edf3000       Deferred        winmm<elf>
  \-PE  7ed70000-7edf3000       \               winmm
ELF     7edf3000-7ee3d000       Deferred        dsound<elf>
  \-PE  7ee00000-7ee3d000       \               dsound
ELF     7ee3d000-7ee89000       Deferred        advapi32<elf>
  \-PE  7ee50000-7ee89000       \               advapi32
ELF     7efa8000-7efb3000       Deferred        libnss_files.so.2
ELF     7efb3000-7efcb000       Deferred        libnsl.so.1
ELF     7efcb000-7eff0000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c64000-b7c6d000       Deferred        libnss_compat.so.2
ELF     b7c6e000-b7c72000       Deferred        libdl.so.2
ELF     b7c72000-b7dbc000       Deferred        libc.so.6
ELF     b7dbd000-b7dd5000       Deferred        libpthread.so.0
ELF     b7de5000-b7ef9000       Deferred        libwine.so.1
ELF     b7efb000-b7f17000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Firaxis Games\Sid Meier's Civilization 4\Beyond the Sword\Civ4BeyondSword.exe
        00000009    0 <==
Backtrace:
=>1 0x0229ef0d in cvgamecoredll (+0xcef0d) (0x0229cfd0)
  2 0xccccc300 (0x000016b8)
  3 0x00000000 (0x00000000)
err:seh:setup_exception nested exception on signal stack in thread 0009 eip 7bc63300 esp 7ffdbc7c stack 0x241000-0x350000
```

---

### Post by zorkerz on 2007-12-03
Anyone getting logged out of ubuntu when the try to run BTS in wine? A big pain because i have no way to tell whats happening. Opps i think I already asked this here. sorry

---

### Post by KhaaL on 2007-12-03
> **sojusnik said:**
> Is it possible to play Civ IV with all addons and latest patches with WINE via Internet with a pal who has the same configuration on Windows XP?

Yes. Again, this is stated in the appdb. You really should check it out, I try to keep it updated with each wine version!

Melhisedek & zorkerz are you using ATI graphic cards? Also, did you install Civ4 in a clean wine directory?

---

### Post by Melhisedek on 2007-12-03
Yeah... ATi card here, 0.9.46 and than upgraded to 0.9.50 through Synaptec. Tried the whole msxml3 thingie... installing stuff and all. Than setting native overrides. 

I also did a few registry tweaks for WOW to work, but Civ4 shows XML error so it shouldn't be that

---

### Post by nwadams on 2007-12-04
delete the msxml3.dll out of the beyond the sword folder

---

### Post by Melhisedek on 2007-12-04
I did that... After that game just shows blue wine window than it dissapears, with it in the folder I got XML error. I have that file in the windows/system32 folder in wine as well

---

### Post by KhaaL on 2007-12-04
Sounds like a weird issue... I'd point ATI as the culprit here but that's just a wild guess considering the nature of their (preciously?) bad drivers.

I don't know how to help you further Melhisedek, assuming you did instead on a clean .wine folder. but if you figure out the problem let us know.

---

### Post by Biffa2001 on 2007-12-05
I have managed to get the game working by loading Civ IV, Warlords & BTS on my XP partition, applying the latest patches and then running the game with the following command:

WINEDLLOVERRIDES="msxml3=n" wine '/media/hda5/Program Files/Firaxis Games/Sid Meier'\''s Civilization 4/Beyond the Sword/Civ4BeyondSword.exe´ 

BTS starts ok, the sound judders but a main concern is the black terrain graphics? Any idea how I can solve this please? I have tried every graphic option within the game and nothing makes a difference. I am running an NVidia VGA card.

Thanks guys
Steve

---

### Post by KhaaL on 2007-12-05
did you enable vertex shaders in winecfg (graphics tab)?

---

### Post by Biffa2001 on 2007-12-05
Yes, would having the wrong Nvidia drivers cause this problem? I am currently trying to see the easiest way to verify mine are working properly.

---

### Post by beermotor on 2008-01-30
Ok so I have the same issue with black terrain.  I enabled vertex shaders in winecfg - doesn't fix the problem (although maybe it stops it from being worse?).

I have an Nvidia card, 6800GT I think.

Game plays well in the new Wine version, just would like to fix the graphics issue.

---

### Post by KhaaL on 2008-01-30
Try lowering the graphic settings. Other than that, I don't know what the problem might be, but do post a solution if you figure it out so I can also post it on appdb!

---

### Post by luke16 on 2008-03-23
It looks like I am having a problem similiar to [Melhisedek,]("http://ubuntuforums.org/member.php?u=13121")
with this being my output:
```
$ wine Civ4BeyondSword.exe 
fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\Firaxis Games\Sid Meier's Civilization 4\Beyond the Sword\Saves.lnk
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\Firaxis Games\Sid Meier's Civilization 4\Beyond the Sword\Logs.lnk
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for C:\Program Files\Firaxis Games\Sid Meier's Civilization 4\Beyond the Sword\CivilizationIV.ini.lnk
fixme:winhttp:WinHttpCheckPlatform stub
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x230090 0x00000000
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
wine: Unhandled exception 0xc06d007f at address 0x7b840fa0 (thread 0032), starting debugger...
Unhandled exception: 0xc06d007f in 32-bit code (0x7b84101a).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b84101a ESP:0034f518 EBP:0034f57c EFLAGS:00200212(   - 00      - -IA1)
 EAX:7b82c171 EBX:7b8ac8a0 ECX:00000000 EDX:0034f5a8
 ESI:0034f5a8 EDI:00000000
Stack dump:
0x0034f518:  0034f5a8 00000004 7bc86afc c06d007f
0x0034f528:  00000000 00000000 7b840fa0 00000001
0x0034f538:  0034f5ac 7bc86afc 0034f574 0034f554
0x0034f548:  7bc397c0 c000007a 00c10924 0034f584
0x0034f558:  7b86348f c000007a 0034f574 00000000
0x0034f568:  0034f570 7b86344f 7b840faa 00c10924
Backtrace:
=>1 0x7b84101a RaiseException+0x7a() in kernel32 (0x0034f57c)
  2 0x004e9160 in civ4beyondsword (+0xe9160) (0x00000000)
0x7b84101a RaiseException+0x7a in kernel32: subl        $4,%esp
Modules:
Module  Address                 Debug info      Name (95 modules)
PE        350000-  35e000       Deferred        hapdbg
PE        360000-  373000       Deferred        zlib1
PE        400000- 105317e       Export          civ4beyondsword
PE       1060000- 13cf000       Deferred        d3dx9_33
PE       1cc0000- 2164000       Deferred        cvgamecoredll
PE      10000000-1002b000       Deferred        boost_python-vc71-mt-1_32
PE      18000000-18038000       Deferred        binkw32
PE      1e000000-1e1ca000       Deferred        python24
PE      21100000-2118c000       Deferred        mss32
PE      74980000-74ab0000       Deferred        msxml3
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bca2000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca2000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
PE      7c340000-7c396000       Deferred        msvcr71
PE      7c3a0000-7c41b000       Deferred        msvcp71
ELF     7e184000-7e198000       Deferred        wtsapi32<elf>
  \-PE  7e190000-7e198000       \               wtsapi32
ELF     7e198000-7e1ac000       Deferred        winhttp<elf>
  \-PE  7e1a0000-7e1ac000       \               winhttp
ELF     7e1ac000-7e1c9000       Deferred        imm32<elf>
  \-PE  7e1b0000-7e1c9000       \               imm32
ELF     7e210000-7e242000       Deferred        uxtheme<elf>
  \-PE  7e220000-7e242000       \               uxtheme
ELF     7e242000-7e268000       Deferred        msacm32<elf>
  \-PE  7e250000-7e268000       \               msacm32
ELF     7e268000-7e27f000       Deferred        msacm32<elf>
  \-PE  7e270000-7e27f000       \               msacm32
ELF     7e27f000-7e345000       Deferred        libasound.so.2
ELF     7e345000-7e359000       Deferred        midimap<elf>
  \-PE  7e350000-7e359000       \               midimap
ELF     7e359000-7e38e000       Deferred        winealsa<elf>
  \-PE  7e360000-7e38e000       \               winealsa
ELF     7e38e000-7e397000       Deferred        libxcursor.so.1
ELF     7e397000-7e39c000       Deferred        libxfixes.so.3
ELF     7e39c000-7e39f000       Deferred        libxcomposite.so.1
ELF     7e39f000-7e3a5000       Deferred        libxrandr.so.2
ELF     7e3a5000-7e3ad000       Deferred        libxrender.so.1
ELF     7e3ad000-7e3b2000       Deferred        libxdmcp.so.6
ELF     7e3b2000-7e4a3000       Deferred        libx11.so.6
ELF     7e4a3000-7e4b1000       Deferred        libxext.so.6
ELF     7e4b1000-7e4b6000       Deferred        libxxf86vm.so.1
ELF     7e4b6000-7e4ce000       Deferred        libice.so.6
ELF     7e4ce000-7e4d6000       Deferred        libsm.so.6
ELF     7e4ea000-7e578000       Deferred        winex11<elf>
  \-PE  7e500000-7e578000       \               winex11
ELF     7e5f2000-7e612000       Deferred        libexpat.so.1
ELF     7e612000-7e63d000       Deferred        libfontconfig.so.1
ELF     7e63d000-7e652000       Deferred        libz.so.1
ELF     7e652000-7e6c2000       Deferred        libfreetype.so.6
ELF     7e6d6000-7e73b000       Deferred        msvcrt<elf>
  \-PE  7e6e0000-7e73b000       \               msvcrt
ELF     7e73b000-7e766000       Deferred        ws2_32<elf>
  \-PE  7e740000-7e766000       \               ws2_32
ELF     7e766000-7e77f000       Deferred        version<elf>
  \-PE  7e770000-7e77f000       \               version
ELF     7e77f000-7e83e000       Deferred        comctl32<elf>
  \-PE  7e790000-7e83e000       \               comctl32
ELF     7e83e000-7e894000       Deferred        shlwapi<elf>
  \-PE  7e850000-7e894000       \               shlwapi
ELF     7e894000-7e99a000       Deferred        shell32<elf>
  \-PE  7e8a0000-7e99a000       \               shell32
ELF     7e99a000-7ea3b000       Deferred        oleaut32<elf>
  \-PE  7e9b0000-7ea3b000       \               oleaut32
ELF     7ea3b000-7ea4e000       Deferred        libresolv.so.2
ELF     7ea4e000-7ea62000       Deferred        lz32<elf>
  \-PE  7ea50000-7ea62000       \               lz32
ELF     7ea62000-7ea80000       Deferred        iphlpapi<elf>
  \-PE  7ea70000-7ea80000       \               iphlpapi
ELF     7ea80000-7eade000       Deferred        rpcrt4<elf>
  \-PE  7ea90000-7eade000       \               rpcrt4
ELF     7eade000-7eb7e000       Deferred        ole32<elf>
  \-PE  7eaf0000-7eb7e000       \               ole32
ELF     7eb7e000-7ec16000       Deferred        gdi32<elf>
  \-PE  7eb90000-7ec16000       \               gdi32
ELF     7ec16000-7ed52000       Deferred        user32<elf>
  \-PE  7ec30000-7ed52000       \               user32
ELF     7ed52000-7edde000       Deferred        winmm<elf>
  \-PE  7ed60000-7edde000       \               winmm
ELF     7edde000-7ee28000       Deferred        dsound<elf>
  \-PE  7edf0000-7ee28000       \               dsound
ELF     7ee28000-7ee72000       Deferred        advapi32<elf>
  \-PE  7ee30000-7ee72000       \               advapi32
ELF     7ef91000-7ef9c000       Deferred        libnss_files.so.2
ELF     7ef9c000-7efa6000       Deferred        libnss_nis.so.2
ELF     7efa6000-7efbe000       Deferred        libnsl.so.1
ELF     7efbe000-7efc7000       Deferred        libnss_compat.so.2
ELF     7efc7000-7efec000       Deferred        libm.so.6
ELF     7efec000-7efef000       Deferred        libxau.so.6
ELF     b7cc6000-b7cca000       Deferred        libdl.so.2
ELF     b7cca000-b7e14000       Deferred        libc.so.6
ELF     b7e15000-b7e2d000       Deferred        libpthread.so.0
ELF     b7e41000-b7f55000       Deferred        libwine.so.1
ELF     b7f57000-b7f73000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
        00000009    0
0000000a 
        0000000b    0
0000000c 
        0000000f    0
        0000000e    0
        0000000d    0
00000010 
        00000013    0
        00000012    0
        00000011    0
00000014 
        00000016    0
        00000015    0
0000002d (D) C:\Program Files\Firaxis Games\Sid Meier's Civilization 4\Beyond the Sword\Civ4BeyondSword.exe
        00000032    0 <==
Backtrace:
=>1 0x7b84101a RaiseException+0x7a() in kernel32 (0x0034f57c)
  2 0x004e9160 in civ4beyondsword (+0xe9160) (0x00000000)

```I've made sure that all of the mentioned dlls are in the system32 folder (i got them off the web), and that they are all set to native in winecfg. Any ideas?

EDIT: This was in the log folder, if it matters
[296.406] ERR: InitWinApp() failed, exiting 
[296.406] ERR: CIV Init FAILED, exiting

---

### Post by Graham1982 on 2008-06-12
> **MFonville said:**
> After a lot of reading on the web and trying to decipher some Finnish on the Finnish ubuntu forum I found out how to install Civilization 4 WITH Beyond the Sword with the latest Wine on Linux

Copy from a windows install the files:
c:\windows\system32\msvcr71.dll msvcp71.dll d3dx9_31.dll d3dx9_32.dll d3dx9_33.dll msxml3.dll msxml3r.dll d3dx9.dll mscoree.dll

to your .wine/windows/system32/

Next install Civ4
Next install the Civ4 1.74 patch
Next install Civ4 BtS

Next follow the instructions from [http://wiki.winehq.org/NativeMSXML3](http://wiki.winehq.org/NativeMSXML3) to install MSXML3 (at least on amd64, not sure for i386)

Have fun playing!

(This worked for me on Kubuntu AMD64)

These steps worked for me.

I copied d3dx9_24.dll right up to d3dx9_36.dll to my system32 folder because I read so many different posts, leading up to this one, that suggested random d3dx9_XX files.

I already had all of the other DLL files needed, except for mscoree.dll.  I, so far, haven't had to install MSXML3...I haven't bothered viewing that link yet, since I'm up and running without Native MSXMK3...Apparently...

I'm using Kubuntu 8.04 and Wine 0.9.59...

Okay...it got past the install but now I get "Error loading shader libraries"

I read that downgrading to 0.9.58 would probably fix this problem...I might get the motivation to try that.

---

### Post by KhaaL on 2008-06-12
> **Graham1982 said:**
> 
I read that downgrading to 0.9.58 would probably fix this problem...I might get the motivation to try that.

I don't think its neccesarly to downgrade to 0.9.58, I'm running BTS on RC4 and its working just as fine as it did on previous versions.

---

### Post by kannho on 2008-06-16
finally I got civ4 n BTS working on my laptop!!  :)

running wine 1.0rc5, I didn't install the game but copied from my other 
XP pc.  

I didn't copy many dll as stated on some the website, only installed msxml3 via winetricks and donwloaded msxml3r.dll  then the game complaint about d3dx9_37.dll so I agian downloaded that and override all 3 files.

And it work!!  Well, a bit sluggish and that is what I working on to improve now...

---

### Post by 4leite on 2008-08-17
> **Graham1982 said:**
> These steps worked for me.
  I, so far, haven't had to install MSXML3...I haven't bothered viewing that link yet, since I'm up and running without Native MSXMK3...Apparently...

I'm using Kubuntu 8.04 and Wine 0.9.59...

Okay...it got past the install but now I get "Error loading shader libraries"


I think it installs without msxml3 native but then doesn't run. Also, if you install and the switch to msxml3 native it doesn't work. So you need to enable msxml3 native before you install BOTH vanilla civ and BTS.

---

### Post by lzprst on 2008-08-26
> 

$ wine Civ4BeyondSword.exe
fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
wine: Unhandled page fault on read access to 0x80000044 at address 0x7bc41a8b (thread 001f), starting debugger...
Unhandled exception: page fault on read access to 0x80000044 in 32-bit code (0x7bc41a8b).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc41a8b ESP:0032f5a4 EBP:0032f5cc EFLAGS:00210286(   - 00      -RISP1)
 EAX:80000000 EBX:7bc8a544 ECX:65faf1f0 EDX:65f22392
 ESI:00000000 EDI:003c0154
Stack dump:
0x0032f5a4:  7bc8a544 00000000 0032f5bc 7bc3abaa
0x0032f5b4:  00000000 003c0018 0032f674 65f24247
0x0032f5c4:  7bc8a544 00000000 0032f62c 7bc43a8c
0x0032f5d4:  0032f594 b7d9102c 00110014 7bc34031
0x0032f5e4:  00110000 00000002 00110014 7bc339df
0x0032f5f4:  00110014 0032f634 7bc8a544 00000000
Backtrace:
=>1 0x7bc41a8b in ntdll (+0x31a8b) (0x0032f5cc)
  2 0x7bc43a8c RtlAllocateHeap+0x1c() in ntdll (0x0032f62c)
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file "ole32.dbg" ("")
  3 0x65f01b9b in ole32 (+0x1b9b) (0x0032f6c4)
  4 0x65f2389d in ole32 (+0x2389d) (0x0032f6e4)
  5 0x65f2376c in ole32 (+0x2376c) (0x0032f700)
  6 0x65f235cd in ole32 (+0x235cd) (0x0032f714)
  7 0x65f2354d in ole32 (+0x2354d) (0x0032f744)
  8 0x65f018b4 in ole32 (+0x18b4) (0x0032f7ac)
  9 0x65f02ca5 in ole32 (+0x2ca5) (0x0032f804)
  10 0x65fa9458 in ole32 (+0xa9458) (0x0032f828)
  11 0x65f3434b in ole32 (+0x3434b) (0x0032f894)
  12 0x65f4fefe in ole32 (+0x4fefe) (0x0032fb38)
  13 0x65f143c4 in ole32 (+0x143c4) (0x0032fb64)
  14 0x65f14397 in ole32 (+0x14397) (0x0032fb8c)
  15 0x006a5603 in civ4beyondsword (+0x2a5603) (0x014c5500)
  16 0x01010000 in civ4beyondsword (+0xc10000) (0x00b0b0ec)
  17 0x004115b0 in civ4beyondsword (+0x115b0) (0x00409690)
  18 0x000097e8 (0x56f18b56)
0x7bc41a8b: cmpl	$0x50414548,0x44(%eax)
Modules:
Module	Address			Debug info	Name (84 modules)
PE	  330000-  343000	Deferred        zlib1
PE	  350000-  35e000	Deferred        hapdbg
PE	  400000- 1038186	Export          civ4beyondsword
PE	 1040000- 13af000	Deferred        d3dx9_33
PE	10000000-1002b000	Deferred        boost_python-vc71-mt-1_32
PE	18000000-18038000	Deferred        binkw32
PE	1e000000-1e1ca000	Deferred        python24
PE	21100000-2118c000	Deferred        mss32
PE	65340000-653d2000	Deferred        oleaut32
PE	65f00000-65fc2000	Export          ole32
ELF	7b800000-7b93c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bca6000	Export          ntdll<elf>
  \-PE	7bc10000-7bca6000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
PE	7c340000-7c396000	Deferred        msvcr71
PE	7c3a0000-7c41b000	Deferred        msvcp71
ELF	7e44c000-7e460000	Deferred        midimap<elf>
  \-PE	7e450000-7e460000	\               midimap
ELF	7e460000-7e486000	Deferred        msacm32<elf>
  \-PE	7e470000-7e486000	\               msacm32
ELF	7e486000-7e49d000	Deferred        msacm32<elf>
  \-PE	7e490000-7e49d000	\               msacm32
ELF	7e49d000-7e4d8000	Deferred        wineoss<elf>
  \-PE	7e4a0000-7e4d8000	\               wineoss
ELF	7e524000-7e557000	Deferred        uxtheme<elf>
  \-PE	7e530000-7e557000	\               uxtheme
ELF	7e557000-7e560000	Deferred        libxcursor.so.1
ELF	7e560000-7e565000	Deferred        libxfixes.so.3
ELF	7e565000-7e568000	Deferred        libxcomposite.so.1
ELF	7e568000-7e56e000	Deferred        libxrandr.so.2
ELF	7e56e000-7e576000	Deferred        libxrender.so.1
ELF	7e576000-7e57b000	Deferred        libxxf86vm.so.1
ELF	7e57b000-7e57e000	Deferred        libxinerama.so.1
ELF	7e57e000-7e59e000	Deferred        imm32<elf>
  \-PE	7e580000-7e59e000	\               imm32
ELF	7e59e000-7e5a3000	Deferred        libxdmcp.so.6
ELF	7e5a3000-7e5bb000	Deferred        libxcb.so.1
ELF	7e5bb000-7e5be000	Deferred        libxau.so.6
ELF	7e5be000-7e6a5000	Deferred        libx11.so.6
ELF	7e6a5000-7e6b3000	Deferred        libxext.so.6
ELF	7e6b3000-7e6cb000	Deferred        libice.so.6
ELF	7e6cb000-7e6d3000	Deferred        libsm.so.6
ELF	7e6e2000-7e77a000	Deferred        winex11<elf>
  \-PE	7e6f0000-7e77a000	\               winex11
ELF	7e7a2000-7e7c3000	Deferred        libexpat.so.1
ELF	7e7c3000-7e7ed000	Deferred        libfontconfig.so.1
ELF	7e7ed000-7e802000	Deferred        libz.so.1
ELF	7e802000-7e872000	Deferred        libfreetype.so.6
ELF	7e881000-7e8cb000	Deferred        dsound<elf>
  \-PE	7e890000-7e8cb000	\               dsound
ELF	7e8cb000-7e8df000	Deferred        lz32<elf>
  \-PE	7e8d0000-7e8df000	\               lz32
ELF	7e8df000-7e8f8000	Deferred        version<elf>
  \-PE	7e8e0000-7e8f8000	\               version
ELF	7e8f8000-7e924000	Deferred        ws2_32<elf>
  \-PE	7e900000-7e924000	\               ws2_32
ELF	7e924000-7e9b6000	Deferred        winmm<elf>
  \-PE	7e930000-7e9b6000	\               winmm
ELF	7e9b6000-7ea20000	Deferred        msvcrt<elf>
  \-PE	7e9d0000-7ea20000	\               msvcrt
ELF	7ea20000-7eae0000	Deferred        comctl32<elf>
  \-PE	7ea30000-7eae0000	\               comctl32
ELF	7eae0000-7eb39000	Deferred        shlwapi<elf>
  \-PE	7eaf0000-7eb39000	\               shlwapi
ELF	7eb39000-7ec52000	Deferred        shell32<elf>
  \-PE	7eb50000-7ec52000	\               shell32
ELF	7ec52000-7eca4000	Deferred        advapi32<elf>
  \-PE	7ec60000-7eca4000	\               advapi32
ELF	7eca4000-7ed42000	Deferred        gdi32<elf>
  \-PE	7ecb0000-7ed42000	\               gdi32
ELF	7ed42000-7ee89000	Deferred        user32<elf>
  \-PE	7ed60000-7ee89000	\               user32
ELF	7efa9000-7efb4000	Deferred        libnss_files.so.2
ELF	7efb4000-7efcc000	Deferred        libnsl.so.1
ELF	7efcc000-7eff1000	Deferred        libm.so.6
ELF	7eff1000-7eff3000	Deferred        libxcb-xlib.so.0
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7d26000-b7d2f000	Deferred        libnss_compat.so.2
ELF	b7d30000-b7d34000	Deferred        libdl.so.2
ELF	b7d34000-b7e83000	Deferred        libc.so.6
ELF	b7e84000-b7e9c000	Deferred        libpthread.so.0
ELF	b7eab000-b7fe1000	Deferred        libwine.so.1
ELF	b7fe3000-b7fff000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000c 
	00000019    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	0000001b    0
	00000018    0
	00000017    0
0000001c 
	0000001d    0
0000001e (D) C:\Spill\Civ4\Beyond the Sword\Civ4BeyondSword.exe
	0000001f    0 <==
Backtrace:
=>1 0x7bc41a8b in ntdll (+0x31a8b) (0x0032f5cc)
  2 0x7bc43a8c RtlAllocateHeap+0x1c() in ntdll (0x0032f62c)
  3 0x65f01b9b in ole32 (+0x1b9b) (0x0032f6c4)
  4 0x65f2389d in ole32 (+0x2389d) (0x0032f6e4)
  5 0x65f2376c in ole32 (+0x2376c) (0x0032f700)
  6 0x65f235cd in ole32 (+0x235cd) (0x0032f714)
  7 0x65f2354d in ole32 (+0x2354d) (0x0032f744)
  8 0x65f018b4 in ole32 (+0x18b4) (0x0032f7ac)
  9 0x65f02ca5 in ole32 (+0x2ca5) (0x0032f804)
  10 0x65fa9458 in ole32 (+0xa9458) (0x0032f828)
  11 0x65f3434b in ole32 (+0x3434b) (0x0032f894)
  12 0x65f4fefe in ole32 (+0x4fefe) (0x0032fb38)
  13 0x65f143c4 in ole32 (+0x143c4) (0x0032fb64)
  14 0x65f14397 in ole32 (+0x14397) (0x0032fb8c)
  15 0x006a5603 in civ4beyondsword (+0x2a5603) (0x014c5500)
  16 0x01010000 in civ4beyondsword (+0xc10000) (0x00b0b0ec)
  17 0x004115b0 in civ4beyondsword (+0x115b0) (0x00409690)
  18 0x000097e8 (0x56f18b56)



following error message. seems a bit strange, I get the initializer as far as Init MP\Audio when I use the GUI to launch, then it stops. Any clue? Not exactly the easiest project I've attempted...

---

### Post by pokipoki08 on 2008-09-22
Possible Quick-fix for "No support for .ani cursors"

No more lagging or stuttering sounds as I move the cursor around. The wine error message still appears though.

Replace all cursor files with default cursor

```

cd ".wine/drive_c/Program Files/Firaxis Games/Sid Meier's Civilization 4/Assets/res/Cursors"
mkdir backup
cp -v *.ani backup/
rm -v *.ani
cp -v backup/Pointer.ani Pointer.ani
[COLOR="RoyalBlue"]cp -v Pointer.ani Airbomb.ani ; cp -v Pointer.ani Airlift.ani ; cp -v Pointer.ani Airstrike.ani ; cp -v Pointer.ani Build.ani ; cp -v Pointer.ani BuildLarge.ani ; cp -v Pointer.ani Claim.ani ; cp -v Pointer.ani Deplete.ani ; cp -v Pointer.ani Edit.ani ; cp -v Pointer.ani EMP.ani ; cp -v Pointer.ani Found.ani ; cp -v Pointer.ani GoTo.ani ; cp -v Pointer.ani Grip.ani ; cp -v Pointer.ani Link.ani ; cp -v Pointer.ani Mine.ani ; cp -v Pointer.ani Move.ani ; cp -v Pointer.ani Mutiny.ani ; cp -v Pointer.ani Nuke.ani ; cp -v Pointer.ani Ping.ani ; cp -v Pointer.ani Rebase.ani ; cp -v Pointer.ani Recon.ani ; cp -v Pointer.ani Repair.ani ; cp -v Pointer.ani RouteTo.ani ; cp -v Pointer.ani 'Size All.ani' ; cp -v Pointer.ani 'Size Diagonal 1.ani' ; cp -v Pointer.ani 'Size Diagonal 2.ani' ; cp -v Pointer.ani 'Size H.ani' ; cp -v Pointer.ani 'Size V.ani' ; cp -v Pointer.ani 'Split H.ani' ; cp -v Pointer.ani 'Split V.ani' ; cp -v Pointer.ani Stasis.ani ; cp -v Pointer.ani Waiting.ani ;[/COLOR]

```

Someone please verify that animated cursors no longer stalls the gameplay?

---

### Post by zorkerz on 2008-10-05
I could use some help from someone who has intact registry entries for beyond the sword.

Since I am lazy and do not like installing, patching, cracking civ and its expansions over and over again I have been copying the game data around. This also allows me to use the same game data for windows and wine testing in ubuntu and not have to install civ through wine. I have now, however, discovered a downside to this strategy.

I am trying to install the 3.17 patch for beyond the sword. I don't have the registry entry specifying where beyond the sword is installed. This causes me to get this error. 

> The setup has detected that no version of Sid Meier's Civilization 4 - Beyond the Sword is installed.

This update requires that a previous version of the application be installed.

If someone who has the intact registry entry(s) could tell me what it looks like it would save me considerable time reinstalling all of this.

Thanks

---

### Post by WaNaBePi on 2008-11-10
ok so im running ubuntu 8.10 (intrepid)
kernel linux 2.6.27.7 generic
gnome 2.24.4

i haven't even been using for 24 hours but i LOVE IT, its like fornicating with a computer. though it can be just a tiering to use as fornicating with a person can be.

so in any event im a complete nub, but im not a, complete, nimrod (obviously if i eventually made the switch to the light side ie. a lunix based system)

i would like to install civ iv and the expansion BtS

I've been reading through all the posts well up to page 8 before i got tired of trying to decipher all the new lingo

so my question is (running on a ~4 year old hardware setup, lab-top, hp)

i have access to multiple windows computers as i'm sure we all do even if we don't realize it.

so should i try the copy from windows route to try and install the above programs OR should i use "wine/cengiga*sp"

thanks in advance, as you may see, I'm am rather long winded and i apologize, however i need a very thorough how-to/explanation, to the best of the given posters ability on this subject

again, *THANK YOU!* 

oh and just an observation, there are no post numbers in the "reply to thread" screen of this forum i think that would be a helpful referencing tool if it were added. now granted its newest first but that doesn't help anyone who may read my post if i am unable to reference any past posts quickly... any way sorry i think you get the picture...

---

### Post by zorkerz on 2008-11-11
If you have easy windows access then I would recommend getting civ installed, updated and cracked in windows before touching wine. This way nothing will go wrong with the install process which i have never tried with wine so cannot speak to. Once you have a fully installed ready to use civ directory i would follow the instructions on the wine appdb. In my opinion this is the easiest way.

As for how well your computer will run civ under wine. The short answer is worse than in windows. I run xp soley for the purpose of playing civ. I have a thinkpad x61 with intel x3100 graphics card 2.2ghz cor2duo and 4 gigs ram (only 3 recognized by windows 3.8 by ubuntu). The killer for me is my graphics card. Civ works in wine on mycomp but it is too slow to be playable. It plays fine in xp without even needing to turn settings down.

---

### Post by WaNaBePi on 2008-11-11
hahaha well thats cool guess well have to talk to k2 to help us out or something cause in my case civ 4 is just to slow to play on this computer even with xp. so i guess I'm s.o.l. but thank you so much for the quick and concise  reply...now, to figure out how to get a java plug in to play chess on websites against people!

---

### Post by WaNaBePi on 2008-11-11
well the java was easy enough though i don't have sound, what ever i'll fix it later however... in keeping with the spirit of free open source ness what would it take to mod civ iv, for personal use of course. so that it would run on ubuntu better than windoze, because i refuse to accept that windoze works better for anything. to include programs that are only meant to work on windoze. i know it would be complicated to mod but i would be willing to help any one willing to take on this venture so to anyone reading this lets make a mod .... oh yea im a nub, but still, i will no longer let windoze get away with their evil ways, blinding an ignorant public and charging them for products and services that are no more reliable than what you can get for free, and rightly so, from linux ubuntu... what have you... so as i said im willing to be of what ever help i can be. i think there is no better way to learn all about ubuntu linux and the like, than to create and mod software and since i cant play the games i want, i have nothing better to do than to make it so that i can do what I want. not what some tool devloper wants me to do.... so ill help you, you help me, and we will help the community

SORRY ABOUT THE RANT, but my offer is stead fast ill keep my eyes on this thread for any takers and if there aren't, ill just have to go it alone

---

### Post by zorkerz on 2008-11-11
Well first off I think it would be wonderful to have something resembling civiv native to linux. Unfortunately anything that is native to linux im pretty sure would necessarily not be a mod (actually i could be wrong here and I bet there is a way to make it not run into legal trouble which is the real issue). THIS WOULD BE A MASSIVE UNDERTAKING. I believe civ uses alot of python and xml but to my knowledge the real problem is that the graphics are all dependent on directx which is windows proprietary. It would all need to be transfered over to opengl. All of this really gets over my head I don't realy know what it would take to make a civ linux port. I do know that firaxis does not appear to have any interest in this. They did not even release Beyond the Sword for mac.

There is nobody to my knowledge attempting this. The closest I have seen is freeciv which is a quite wonderful rendition of civII which actually at this point has expanded beyond the original game.

I would love something that would do all the computations of civiv. For me the graphics nonimportant. 

If you trying to really get civiv in linux wine is by far the closest you can get at this point. You could look into helping them out. Some apps run better in wine than windows this is at least theoretically possible in wine. 

oh man im just blabbering I wrote all this and forgot abotu it and ive come back and have no idea where I was. Basically i think the best place to put your work if you want civ in linux is wine. It develops pretty incredibly fast.

---

### Post by digitalb0y on 2008-11-30
I have BTS working just about perfect (from trial and error) I'm making a quick howto to help those who have had issues. Starting from a clean wine install

First of all download winetricks this makes the process so much easier.
```
wget http://www.kegel.com/wine/winetricks
```

then download cabextract is your system does not have it.
on ubunut type ```
sudo apt-get install cabextract
```
otherwise download cabextract here [http://www.cabextract.org.uk/](http://www.cabextract.org.uk/)

This is needed for winetricks.Once cabextract is installed lets run winetricks.

```
sh winetricks corefonts vcrun6 dotnet11 msxml3 msxml4 directx9
```
This installs windows fonts needed some DLLS, the XML engine, DOT.NET and DirectX 9

Then type
```
sh winetrcisk winxp 
```
This changes the version on windows to XP

then

install Civ4 from the Setup.exe on the CD

once its installed
now edit 
```
nano ~/My Games/Sid Meier's Civilization 4/CivizationIV.ini
```

Find the following and make sure it matches what is below

; Set to 1 for no tech splash screens
```
NoTechSplash = 1

```


; Set to 1 for no intro movie
```
NoIntroMovie = 1
```


; Enable voice over IP capture and playback
```
EnableVoice = 0
```


once done 
try to run the program.

It all works lets move onto Warlords.


now onto warlords.

run the cdrom setup.exe file and edit 
```
nano ~/My Games/Warlords/CivizationIV.ini 
```
file ini to the same as the orginal civ4.

try to run the program.

It it all works lets move onto Beyond the Sword.

** Make sure your not connected to the Internet or it will try to download updates and freeze the system.

If the install freezes at updating directx then install directx updates manually by running setup.exe in the directx folder.

edit the config file

```
nano ~/My Games/Beyond the Sword/CivizationIV.ini file
```

Find the following and make sure it matches what is below

; Set to 1 for no tech splash screens
```
NoTechSplash = 1

```

; Set to 1 for no intro movie
```
NoIntroMovie = 1
```

; Enable voice over IP capture and playback
```
EnableVoice = 0
```


now run BTS 

This is what worked for me I hope it helps you.

---

### Post by zorkerz on 2008-11-30
This looks like a great howto I have not had time to try it out. I was wondering if you had done any comparisons with how civ performs from your howto in comparison to on windows (xp preferably for me). Also what are your system specs. I have had great luck getting civ BTS to work through wine but the performance is much decreesed from in xp. This is a bummer because its the only reason keeping windows on my machine. My computer is a thinkpad x61 with core2duo 2.12ghz, 4gb ram, intel x3100 GMA 965.

Also it would be good to know what version of wine you have installed. 

Thanks for posting that.

---

### Post by zorkerz on 2008-12-07
Ok so here is a question. There are a bunch of differing accounts of what to install with winetricks both from this thread and from the tests on appdb. Most people can get BTS to work now its performance I am looking for.

I plan to do some experiments with various things installed and not but its exam times so it may take me a while. 

My question is what things did you install with winetricks that improved BTS 3.17 performance and what version of wine did you use (1.0.10 is now out)?

---

### Post by GepettoBR on 2008-12-09
I have BTS installed via Wine and it runs perfectly except for one big issue (apart from the animated cursors, etc): My keyboard won't work. Does anyone know how I can fix that?

I'm using the 3.17 patch and Wine 1.1.10, though it didn't work with 1.1.9 either.

---

### Post by weetabix on 2009-02-09
> **zorkerz said:**
> 
My question is what things did you install with winetricks that improved BTS 3.17 performance and what version of wine did you use (1.0.10 is now out)?

You really don't need winetricks at all. Biggest hamper of all I have when i added some Direct3D -settings, they only made the performance worse.
Here's some howtos I made:

Short story:

1. Copy d3dx9_26.dll to c:\windows\system32\
2. Install Civ4  (step 1 prevents asking about directx)
3. Install Warlords expansion
4. Copy mscoree.dll into c:\windows\system32\
5. Install Beyond the Sword -expansion (will update both the vanilla and warlords). 
	- Will get stuck "err:storage:BlockChainStream..." -error. Kill with Ctrl+C.
	- Install it again and it will work.
6. Update to Beyond the Sword to version 3.17 (gives error after install, ignore it).
7- Copy msxml3r.dll into folder where you installed the BtS -expansion.
8. Start winecfg, Libraries -tab and make msxml3 native.
9. Get no-dvd crack to BtS.
10. Start the game.

------
Detailed stuff:
I am using PulseAudio with Ubuntu 8.10, so I need to add padsp to every wine -command.
If you are using alsa or similar, leave padsp command part out. 
Versions used in installing are Ubuntu 8.10, Wine 1.1.8, Civilization Chronicles (Civ4 vanilla), Warlords -expansion (Retail UK/EU) and Beyond the Sword (Retail UK/EU). Machine is X2 3800+, Geforce 7900GT (restricted default drivers), 2GB memory.
The goal is to play with Beyond the Sword in fresh environment. No detail is given whether the vanilla Civ or Warlords -expansion actually work.
Drm get's in the way atleast. Use command line to be able the see the errors and kill with Ctrl+C when needed.
Shortcut should be used to play the game. Command line is used because you can see the errors.

1. Create prefix:  WINEPREFIX=~/wine/civ4 padsp winecfg
	Graphics settings:
		-emulate virtual desktop (I use same resolution as native)
	Sound:
		-I change the sound system from ALSA to OSS (because of PulseAudio).
		-I know that this isn't ideal, but it works for me.

2. Copy d3dx9_26.dll (a) to system32 -folder:
		cp d3dx9_26.dll ~/wine/civ4/drive_c/windows/system32/

3. Install Civ4 -game (my version is from Civilization - Chronicles). 
	-You can select if you want to install Xfire also.
	-d3d9_26.dll eliminated the directx question since in Chronicles, you cant say no to that and the installation would fail.
		WINEPREFIX=~/wine/civ4 padsp wine /media/CIV4DVD/setup.exe

4. Install Warlords -expansion. I de-selected the windows firewall -option.
		WINEPREFIX=~/wine/civ4 padsp wine /media/CIV4WARLORDS/setup.exe
	
5. Copy mscoree.dll (b) to system32 -folder:
		cp mscoree.dll ~/wine/civ4/drive_c/windows/system32/

6. Install Beyond the Sword
	WINEPREFIX=~/wine/civ4 padsp wine /media/CIV4BTSEU/setup.exe
	- It will install path for vanilla and for Warlords. This will take quite long time and it will be stucked at some point into error:
		"err:storage:BlockChainStream_WriteAt not enough blocks in chain to write data"
		Use Ctrl+C to kill the program.
	- Install again with same command:
		WINEPREFIX=~/wine/civ4 padsp wine /media/CIV4BTSEU/setup.exe
		-now it will work. 

7. Download 3.17 (at the moment, latest -version) and install it.
	- Download: [http://forums.civfanatics.com/downloads.php?do=file&id=9800](http://forums.civfanatics.com/downloads.php?do=file&id=9800)
	- Install: WINEPREFIX=~/wine/civ4 padsp wine Civ4BTS_Patch_v317.exe
		- It will give -5012 error, ignore it. Kill in console with Ctrl+C if it doesn't quit.

8. Finish the installation:
	- Copy msxml3r.dll (c) to where you installed the Beyond the Sword -game (and where the exe is).
		 cp msxml3r.dll ~/games/wine/civ4/Beyond\ the\ Sword/
	- Use winecfg to make msxml3 as native:  WINEPREFIX=~/wine/wineroots/civ4 padsp winecfg
		Libraries: write msxml3 and press Add. Ok to quit.

9. Fix the drm
	- get the no-dvd crack from internet
	- cd to game folder and make backup: 
		cd ~/games/wine/civ4/Beyond\ the\ Sword/ 
		mv Civ4BeyondSword.exe Civ4BeyondSword.exe.orig
	- Copy the cracked version in place:
		cp Civ4BeyondSword.exe ~/games/wine/civ4/Beyond\ the\ Sword/

10. Start the game
	- WINEPREFIX=~/wine/civ4 padsp wine ~/games/wine/civ4/Beyond\ the\ Sword/Civ4BeyondSword.exe
	
a) [http://www.dll-files.com/dllindex/dll-files.shtml?d3dx9_26](http://www.dll-files.com/dllindex/dll-files.shtml?d3dx9_26)
b) [http://www.dll-files.com/dllindex/dll-files.shtml?mscoree](http://www.dll-files.com/dllindex/dll-files.shtml?mscoree)
c) [http://www.dll-files.com/dllindex/dll-files.shtml?msxml3r](http://www.dll-files.com/dllindex/dll-files.shtml?msxml3r)

*Bonus*

1. Download Fall from Heaven II -mod and the media pack and patch "t".
 - [http://forums.civfanatics.com/downloads.php?do=file&id=1](http://forums.civfanatics.com/downloads.php?do=file&id=1)

2. Install them:
 - WINEPREFIX=~/wine/civ4 padsp wine FallfromHeaven2.exe
 - WINEPREFIX=~/wine/civ4 padsp wine FfH2040t.exe
 - WINEPREFIX=~/wine/civ4 padsp wine FfH2media.exe 

3. Start the game with mod starting automatically (from Advanced, Load Mod etc. it didn't work).
 - WINEPREFIX=~/wine/civ4 padsp wine ~/games/wine/civ4/Beyond\ the\ Sword/Civ4BeyondSword.exe mod=/Mods/Fall\ from\ Heaven\ 2/

---

### Post by zorkerz on 2009-02-09
My advice would be to look it up in the application database (appdb) on winehq.org. There you will see the results of other people setting it up with lots of different versions of wine (newest currently being 1.0.14). I would like to know how to optimize performance but I think that would take somebody methodically going through all of the tweeks. At the rate wine is developing I don't think this is worth it to anybody. You could also vote for it on the wine appdb that way its more likely to get some developer attention (at least in theory).

I found the method with winetricks found on appdb worked better than any others i have tried. However it is still way to slow to play on my computer in ubuntu when its fine in win xp.

good luck

---

### Post by GepettoBR on 2009-02-09
I find it very odd that so many people are complaining about the game running too slow to be playable. It runs faster than in XP for me.

Still, my keyboard doesn't work. :(

---

### Post by Neo40 on 2009-02-23
The only problem I see is when I finish the game and come back to my desktop,
the screen resolution stays at 1024x768 instead 1280x800. 
I,m using the latest wine 1.1.15. 
Is there a solution to fix this?
Thanks

---

### Post by GepettoBR on 2009-02-24
> **Neo40 said:**
> The only problem I see is when I finish the game and come back to my desktop,
the screen resolution stays at 1024x768 instead 1280x800. 
I,m using the latest wine 1.1.15. 
Is there a solution to fix this?
Thanks

That's easy. Just configure Wine to create a virtual desktop the same size as your regular desktop.

---

### Post by 3jdh on 2009-03-01
When I start up Civilization IV, it's unbearably slow, especially the interface.  But if I change the resolution (up or down, doesn't seem to matter) the game becomes very playable.  I do this every time I start the game.  It's kind of silly, but it seems to work.

I'm running on an Pentium M 1.6 Thinkpad, 1GB DDR, FireGl T2.  Wine 1.1.16.

---

### Post by zorkerz on 2009-03-01
Thats really odd but Im excited to hear it. I will have to give it a try on mine. If it actually makes civ playable that would be so so so cool! I really hate having a 10gib xp partition around just for civ.

---

### Post by GepettoBR on 2009-03-01
I have a separate Wine prefix for running CIV, NWN2 and C&C:RA3, which I wipe and reinstall whenever a new Wine development version rolls along. With Wine 1.1.16, CIV is now completely playable, so long as you have msxml3 and the proper DirectX DLLs (NOT installing DirectX via winetricks, just getting them from Windows). Even the Globe View now works flawlessly. The game speed is perfect at 1280x768 (the highest my monitor will go) with all graphical settings maxed out, except for anti-aliasing, which must be left at 0.

The keyboard problem I had turned out to be related to SCIM. Killing SCIM before starting CIV solves the problem nicely.

---

### Post by zorkerz on 2009-03-01
@GepettoBR Would you be willing to explain what you did to wine in more detail to get  civ working?

-Did you use winetricks at all? msxml3 can be installed manually here [http://wiki.winehq.org/NativeMSXML3](http://wiki.winehq.org/NativeMSXML3)
-Did you add a library overide for msxml3 and if so is it just the default one (native, builtin)?
-What dlls did you install (place in system32)? at times i have been told to try different combinations of d3dx9_26.dll, d3dx9_31.dll, d3dx9_32.dll, d3dx933.dll, msxml3.dll, msxml3r.dll, and possibly others.
-How did you install DirectX?
-Are you doing this with the compiz special effects enabled?

Have you tried Beyond the Sword?

I have a copy of the civ program files directory so that installing civ and the expansions is not necessary.

thanks
elias

the winehq appdb appears to be down for the moment so i don't have access to all the info id like at the moment

---

### Post by GepettoBR on 2009-03-02
I tried posting a new review in the appdb but for some reason, I kept getting 503 errors.

I didn't know there was a native way to install msxml3. I installed it via winetricks.

I also have corefonts, vcrun6, dotnet11 and dotnet20 installed via Winetricks, but IIRC dotnet20 isn't required for CIV (it is by NWN2, though).

I did not install DirectX, I merely copied the following DLLs from Windows to my Wine system32 folder: d3dx9_xx.dll with xx between 24 and 34 (including), d3dx10_33.dll and d3dx10_34.dll. I used the default (native, builtin) override for msxml3.dll (for the sake of completeness, I also have gdiplus (native) but that was also for Neverwinter Nights 2, and shouldn't affect Civilization IV at all).

This was all done before installing the game. I installed only the original game and Beyond the Sword, skipping Warlords, and patched BTS to version 3.17. Both installation and playing were done with Wine set to Windows XP, a virtual desktop as big as my actual desktop, Vertex Shader Support set to Hardware and Allow Pixel Shader enabled. I also used a No-CD crack because I had never gotten the game to work without one, but I don't know if it's still necessary with the current Wine build.

Civlization IV: Colonization also works flawlessly in the same Wine prefix (also using a No-CD crack).

If there's any important information I left out, like other config options, tell me and I'll post it here. Everything I installed is listed, though.

P.S.: cabextract is necessary for installing some of the winetricks packages.

---

### Post by zorkerz on 2009-03-02
Well no luck here. 

First I disabled compiz special effects it has never worked for me with this enabled. Then I tried it with just msxml.3 installed from winetricks it crashed with an error asking for d3dx9_36.dll (one you did not recommend). After adding d3dx9_36.dll it got as far as it did with any future tests. The game starts sound works and I can start a game but as soon as the loading is done before I actually get into civ it crashes and loggs me out. Occasionally I get hard freezes before this that require a compled reboot. In the past I have made it to the actual game but its been very slow. 

I then added corefonts, vcrun6, and dotnet11 one by one. Then added all the .dlls with and without d3dx9_36.dll. Next I realized I was using wine 1.1.17 instead of 1.1.16 so I tried it with the older version as well. None of this appeared to make any meaningful difference. 

Differences:
- I did not have all the dll files you mention in my windows system32 so I downloaded them offline I don't know if dll files by the same name might have different versions if so this would be a big problem.
-I did not install the game but used a preinstalled file that works fine in xp.
-i have warlords installed
-did not use cabextract it did not seem like any of the things we installed with winetricks needed it but I could be wrong.
-I did not have dotnet20 installed or the gdiplus (native) overide.

In the process of installing civ did you install directx by any chance?

My suspicion is that this comes down to our graphics cards. I have an intel GMA965 chipset which apparently has some key components of the linux driver missing. I hear some of this is starting to get fixed in jaunty but it looks like I will need to keep my 10 gig windows drive around for awhile longer. At least it keeps me away from civ when I need to be.

Thanks for your help.

---

### Post by GepettoBR on 2009-03-02
> **zorkerz said:**
> In the process of installing civ did you install directx by any chance?

My suspicion is that this comes down to our graphics cards. I have an intel GMA965 chipset which apparently has some key components of the linux driver missing. I hear some of this is starting to get fixed in jaunty but it looks like I will need to keep my 10 gig windows drive around for awhile longer. At least it keeps me away from civ when I need to be.

Thanks for your help.

I had installed DirectX when prompted by the CIV installer in the past, but it never worked. I only used the DLLs. And I double-checked, but I did not, in fact, copy d3dx9_36.dll from Windows. If you like, I can upload my versions of the other DLLs for you to see if it was indeed a version conflict.

Cabextract doesn't need to be called, but I read somewhere that it needs to be installed because Winetricks calls it.

As for the video card, it may be that the driver is the problem. As I was reading your post it occurred to me to ask what driver you were using (I know, for example, that the open-source nv driver for nVidia and the also open "ati" driver have a few bugs with DirectX applications in Wine, though I have no experience with Intel GPUs). If it is a driver problem, however, it is likely to be fixed by a kernel update such as the one we'll have on the jump to Jaunty, since new kernel = new drivers.

I think I can also get a hold on a computer with an Intel GPU but there's no way of telling if it's the same as yours until I have it with me. I'll do a Wubi install of Intrepid, get the latest Wine from the WineHQ repos and report back, probably in a week or so.

---

### Post by zorkerz on 2009-03-02
Your right it does say on the winetricks page > Also, some winetricks "packages" require the cabextract tool to be installed. The cabextract tool is for extracting Microsoft cabinet files, also called **.CAB** files. I don't think any of the things we installed have .cab files if they did I would expect to have seen an error in the terminal. So hopefully safe on this front. 

Ill hold out for awhile no the .dlls I can't invest much more time into this until my schedule loosens up a bit. Some day I would love to test out how many of those .dlls are actually needed not that they take up much space. Ive read people saying many different combinations are required.

I don't know what range of intel GPUs are affected by this issue. I know my card is an Intel Graphics Media Accelerator x3100. It reports itself as having a gl960/gm965 chipset. I don't know how to determin which one there are a few relatively minor differences according to wikipedia. 

Id love to hear about somebody elses experiences with a similar integrated intel GPU.

---

### Post by GepettoBR on 2009-03-02
> **zorkerz said:**
> Ill hold out for awhile no the .dlls I can't invest much more time into this until my schedule loosens up a bit. Some day I would love to test out how many of those .dlls are actually needed not that they take up much space. Ive read people saying many different combinations are required.
True. The combination I'm using is the one I saw on a BTS 3.13 review on AppDB. I just followed it and it worked, but I did see many comments ont eh page about people who had it working with other combinations. Sadly, I haven't the time to test all of this.

> **zorkerz said:**
> I don't know what range of intel GPUs are affected by this issue. I know my card is an Intel Graphics Media Accelerator x3100. It reports itself as having a gl960/gm965 chipset. I don't know how to determin which one there are a few relatively minor differences according to wikipedia. 

Id love to hear about somebody elses experiences with a similar integrated intel GPU.
The computers I have a chance of getting my hands on are both laptops, so they'll have integrated/on-board video. One of them is a Hewlett-Packard, the other a Sony Vaio. Maybe we'll get lucky on the chipset.

---

### Post by zorkerz on 2009-03-08
So ive finally installed Jaunty for real instead of in a virtual machine. Ive installed wine 1.1.16 and ive been testing variations of what was tried above. I have not had any drastic success. The farthest it gets is the civ loading screen before it goes full screen. If anyone can interpret it here is the terminal output with msxml, corefonts, dotnet11, and vcrun6 installed from winetricks and d3dx9_33.dll, and d3dx9_36.dll put in system32.

```
wine '/home/data/games/civiv/Beyond the Sword/Civ4BeyondSword.exe'
fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for Z:\home\data\games\civiv\Beyond the Sword\Logs.lnk
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for Z:\home\data\games\civiv\Beyond the Sword\Saves.lnk
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:shell:DllCanUnloadNow stub
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WinMain failed to build menu item for Z:\home\data\games\civiv\Beyond the Sword\CivilizationIV.ini.lnk
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x1002a 0x00000000
wine: Unhandled page fault on execute access to 0x00000000 at address (nil) (thread 0009), starting debugger...
Unhandled exception: page fault on execute access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00000000 ESP:0032fb64 EBP:00000008 EFLAGS:00010283(   - 00      -RIS1C)
 EAX:0a0d6ff0 EBX:00ccb140 ECX:0a0d7158 EDX:0a0d6ff0
 ESI:0a0d6d60 EDI:0a0d6ff0
Stack dump:
0x0032fb64:  0068b61a 0a0d6d60 7b85583e 01a73b12
0x0032fb74:  00000000 00002710 00000000 00000000
0x0032fb84:  00000000 ee1b90be 01c99faf 7b8557f9
0x0032fb94:  7b8b7ff4 0032fba8 7b855867 7b855859
0x0032fba4:  0068b71c 0068b335 0a0d6dc0 0a0d6d60
0x0032fbb4:  0a0d6d60 004e994c 00400000 0a0d6bb0
Backtrace:
=>0 0x00000000 (0x00000008)
  1 0x00000000 (0x00000000)
0x00000000: addb    %al,0x0(%eax)
Modules:
Module    Address            Debug info    Name (98 modules)
PE      330000-  343000    Deferred        zlib1
PE      350000-  35e000    Deferred        hapdbg
PE      400000- 1038186    Deferred        civ4beyondsword
PE     1040000- 13af000    Deferred        d3dx9_33
PE     1ca0000- 2153000    Deferred        cvgamecoredll
PE    10000000-1002b000    Deferred        boost_python-vc71-mt-1_32
PE    18000000-18038000    Deferred        binkw32
PE    1e000000-1e1ca000    Deferred        python24
PE    21100000-2118c000    Deferred        mss32
PE    69b10000-69c14000    Deferred        msxml3
ELF    7b800000-7b93f000    Deferred        kernel32<elf>
  \-PE    7b820000-7b93f000    \               kernel32
ELF    7bc00000-7bcb1000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb1000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
PE    7c340000-7c396000    Deferred        msvcr71
PE    7c3a0000-7c41b000    Deferred        msvcp71
ELF    7d7ac000-7d7c1000    Deferred        wtsapi32<elf>
  \-PE    7d7b0000-7d7c1000    \               wtsapi32
ELF    7d7c1000-7d7d6000    Deferred        midimap<elf>
  \-PE    7d7d0000-7d7d6000    \               midimap
ELF    7d7d6000-7d7ff000    Deferred        msacm32<elf>
  \-PE    7d7e0000-7d7ff000    \               msacm32
ELF    7d7ff000-7d818000    Deferred        msacm32<elf>
  \-PE    7d800000-7d818000    \               msacm32
ELF    7e019000-7e020000    Deferred        libgdbm.so.3
ELF    7e020000-7e038000    Deferred        libice.so.6
ELF    7e038000-7e096000    Deferred        libpulse.so.0
ELF    7e0a8000-7e0b1000    Deferred        librt.so.1
ELF    7e0b1000-7e179000    Deferred        libasound.so.2
ELF    7e17b000-7e184000    Deferred        libsm.so.6
ELF    7e184000-7e18b000    Deferred        libasound_module_pcm_pulse.so
ELF    7e18b000-7e1c2000    Deferred        winealsa<elf>
  \-PE    7e190000-7e1c2000    \               winealsa
ELF    7e20e000-7e241000    Deferred        uxtheme<elf>
  \-PE    7e210000-7e241000    \               uxtheme
ELF    7e241000-7e24a000    Deferred        libxcursor.so.1
ELF    7e24a000-7e24f000    Deferred        libxfixes.so.3
ELF    7e24f000-7e253000    Deferred        libxcomposite.so.1
ELF    7e253000-7e25b000    Deferred        libxrandr.so.2
ELF    7e25b000-7e265000    Deferred        libxrender.so.1
ELF    7e265000-7e26b000    Deferred        libxxf86vm.so.1
ELF    7e26b000-7e26e000    Deferred        libxinerama.so.1
ELF    7e26e000-7e28f000    Deferred        imm32<elf>
  \-PE    7e270000-7e28f000    \               imm32
ELF    7e28f000-7e294000    Deferred        libxdmcp.so.6
ELF    7e294000-7e2ae000    Deferred        libxcb.so.1
ELF    7e2ae000-7e2b2000    Deferred        libxau.so.6
ELF    7e2b2000-7e3a1000    Deferred        libx11.so.6
ELF    7e3a1000-7e3b0000    Deferred        libxext.so.6
ELF    7e3b0000-7e3b5000    Deferred        libuuid.so.1
ELF    7e3be000-7e3c2000    Deferred        libcap.so.1
ELF    7e3c2000-7e45e000    Deferred        winex11<elf>
  \-PE    7e3d0000-7e45e000    \               winex11
ELF    7e475000-7e49c000    Deferred        libexpat.so.1
ELF    7e49c000-7e4c9000    Deferred        libfontconfig.so.1
ELF    7e4c9000-7e4df000    Deferred        libz.so.1
ELF    7e4df000-7e555000    Deferred        libfreetype.so.6
ELF    7e567000-7e5b4000    Deferred        dsound<elf>
  \-PE    7e570000-7e5b4000    \               dsound
ELF    7e5b4000-7e6a0000    Deferred        oleaut32<elf>
  \-PE    7e5d0000-7e6a0000    \               oleaut32
ELF    7e6a0000-7e707000    Deferred        rpcrt4<elf>
  \-PE    7e6b0000-7e707000    \               rpcrt4
ELF    7e707000-7e819000    Deferred        ole32<elf>
  \-PE    7e720000-7e819000    \               ole32
ELF    7e819000-7e82e000    Deferred        lz32<elf>
  \-PE    7e820000-7e82e000    \               lz32
ELF    7e82e000-7e849000    Deferred        version<elf>
  \-PE    7e830000-7e849000    \               version
ELF    7e849000-7e876000    Deferred        ws2_32<elf>
  \-PE    7e850000-7e876000    \               ws2_32
ELF    7e876000-7e90a000    Deferred        winmm<elf>
  \-PE    7e880000-7e90a000    \               winmm
ELF    7e90a000-7e977000    Deferred        msvcrt<elf>
  \-PE    7e920000-7e977000    \               msvcrt
ELF    7e977000-7ea3e000    Deferred        comctl32<elf>
  \-PE    7e980000-7ea3e000    \               comctl32
ELF    7ea3e000-7ea9c000    Deferred        shlwapi<elf>
  \-PE    7ea50000-7ea9c000    \               shlwapi
ELF    7ea9c000-7ec29000    Deferred        shell32<elf>
  \-PE    7eab0000-7ec29000    \               shell32
ELF    7ec29000-7ec7e000    Deferred        advapi32<elf>
  \-PE    7ec40000-7ec7e000    \               advapi32
ELF    7ec7e000-7ed1f000    Deferred        gdi32<elf>
  \-PE    7ec90000-7ed1f000    \               gdi32
ELF    7ed1f000-7ee6e000    Deferred        user32<elf>
  \-PE    7ed40000-7ee6e000    \               user32
ELF    7ef98000-7efa4000    Deferred        libnss_files.so.2
ELF    7efa4000-7efaf000    Deferred        libnss_nis.so.2
ELF    7efaf000-7efc8000    Deferred        libnsl.so.1
ELF    7efc8000-7efee000    Deferred        libm.so.6
ELF    7eff7000-7f000000    Deferred        libnss_compat.so.2
ELF    f7ca9000-f7cad000    Deferred        libdl.so.2
ELF    f7cad000-f7e10000    Deferred        libc.so.6
ELF    f7e11000-f7e2a000    Deferred        libpthread.so.0
ELF    f7e3c000-f7f77000    Deferred        libwine.so.1
ELF    f7f79000-f7f9a000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\data\games\civiv\Beyond the Sword\Civ4BeyondSword.exe
    00000009    0 <==
0000000c 
    00000014    0
    00000013    0
    00000012    0
    0000000e    0
    0000000d    0
0000000f 
    00000016    0
    00000015    0
    00000011    0
    00000010    0
00000017 
    00000018    0
Backtrace:
=>0 0x00000000 (0x00000008)
  1 0x00000000 (0x00000000)
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr (nil)
```

---

### Post by GepettoBR on 2009-03-23
How aggravating.

I got the laptop, but couldn't for the life of me get anything to work. Since it isn't mine, I had to go with a Wubi installation. I don't know if that has to do with the problem, but Ubuntu's PulseAudio simply refused to work even after following the instructions on psyke's thread a few times. Switching to Kubuntu for Phonon I got sound, but something was wrong with mounting my CD - a problem that probably already existed in the GNOME installation as well, since it has nothing to do with the DE.

I couldn't even get to Wine, since a thorough test without sound isn't really possible, much less install the game.

---

### Post by zorkerz on 2009-03-23
Oh shucks. I just found out that UXA which will eventually replace EXA for at least some graphics cards (I think they are for memory management) is not turned on by default in jaunty due to instability. I have turned it on in my xorg.conf and if I get a good chance Ill try civ with that.

---

### Post by color_vision_researcher on 2009-07-30
I wanted to share with you all my experiences with Civ IV (running on 64-bit Jaunty Distro) and how I got around the 'shader' error others are getting.  

This [tutorial]("http://www.rikertothebridge.com/2009/05/installing-civilization-iv-warlords-and-beyond-the-sword-on-ubuntu-linux/") was great for the installing via wine!

Secondly, for those of you having the "Error Loading Shader" issues during the init portion of the load I offer this suggestion. 

1. Go into /home/user/My Games and open the BTS program folder. 

2. DELETE the CivilizationIV.ini file.

3. Rerun, the program (you will still have the error).  REOPEN the CivilizationIV.ini file like the last step.  

4. Go to the portion on the file where it says " Disable caching of xml and file system (may  slow initialization"

5. Change the DisableCaching = 0   to    DisableCaching = 1  

This got rid of the "Shader" error and corrected the issue for me.

Cheers.

---

### Post by Yeeha on 2009-08-28
How do you people get 3.19 patch installed, some suggest dcom98 but with that installer allways says that error 6005 that says theres another install going on.

---

### Post by Yeeha on 2009-08-30
Atlast i got it to run those who have same problem - i deleted .wine and first thing i did after creating new .wine was setting win98 and installing dcom98 and then directx9, xml3 and then installed the game and patch. Oddly enough when installed dcom98 previously after game install and set win98 patch didnt work.

---

