---
title: "Starting up a game corrupts my screen?"
date: 2008-07-09
forum: Wine
---

### Post by Muffinabus on 2008-07-09
I have wine working fine with Ventrilo and Steam, but the moment I start up a game my screen seems to change resolution and overlaps itself and creates some graphical glitches.  This happens even when the game hasn't started up yet (IE: when steam prepares it for launching).  It so far does this with Counter Strike: Source, Counter Strike (I didn't even have CS fully downloaded, it messed up even when it came up with the error saying that the game was unavailable), and World of Warcraft.

Now the weird thing is, I was able to take a screenshot and save it while the screen was messed up... and it looks fine.  This kind of implies that it's my monitor that can't display the resolution... but I'm running the game in a window AND using resolutions that I KNOW works on my monitor (IE: It's native resolution of 1360x768).

[http://img.photobucket.com/albums/v109/tmm_xiv/messedup.jpg](http://img.photobucket.com/albums/v109/tmm_xiv/messedup.jpg)

EDIT:  Sorry, should probably mention I'm using Wine 1.1 on the latest version of Ubuntu with all the updates.  I've also got my drivers installed correctly for my video card([link]("http://img.photobucket.com/albums/v109/tmm_xiv/OMFGYES.jpg")).  System specs are:  P4 2.8Ghz, Radeon 1950GT, 2GB RAM.

I also didn't have this problem before I upgraded to 1.1.  I was going to try reverting back to see if that helps.

---

### Post by Felson on 2008-07-09
Did you try running in windowed wine mode? I know you probably don't want to play that way, but it would be a good test. (winecfg->Graphics check "Emulate Virtual Desktop")

---

### Post by Muffinabus on 2008-07-09
Nope, seems to have the same effect.  It looks like it's running in a window but it still causes my screen to become corrupted.

---

### Post by Felson on 2008-07-09
Well, if even that screws with your screen, I don't think it can be a res/refesh problem. Before reverting back I would check [wine bugzilla]("http://bugs.winehq.org/") and see if anyone else is having the same kinda problem. Short of that, trying a version back isn't a bad idea. If that fixes it, you shold post a "regression" to wine bugzilla.

---

### Post by Muffinabus on 2008-07-09
Yeah, it's displaying the same resolution (as proven by the SC I took, it was still in 1360x768 ), it just LOOKS as if it has changed to a resolution that my monitor doesn't support.  What I see on screen is a huge garbled mess and the image overlaps a couple of times.

It's also a bit difficult to search for as I really have no clue what it's doing.  It's quite difficult to describe the problem.

EDIT:  Oh, and for some reason Wine decided to delete my installed applications.  Vent, Steam, and WoW aren't in my program files anymore...

---

### Post by Muffinabus on 2008-07-09
Got a picture showing you what it looks like.

[http://img.photobucket.com/albums/v109/tmm_xiv/DSCN0231.jpg](http://img.photobucket.com/albums/v109/tmm_xiv/DSCN0231.jpg)

Also, I downloaded Wolfenstein Enemy Territory just to try out and see if it was actually Wine causing the problems with runnings games and it worked just fine.

Anyone else have any ideas /: ?

EDIT:  It should be known that my screen stays like that even when I exit out of WoW.  The only way I've seen to get rid of it is to either restart or logout by hitting ctrl + alt + backspace.

---

### Post by Muffinabus on 2008-07-10
Shameful bump /:

---

### Post by Felson on 2008-07-10
I just had a thought.... what is your direct 3D stuff set to in your wineconfig->Graphics?

---

### Post by Muffinabus on 2008-07-10
I'm not sure, I'll check in a second (on my Windows install right now :3).  What should I be looking for?

---

### Post by Felson on 2008-07-10
Not 100% sure, but it sounds like wine is playing with your display settings. So the first thing I would try is shutting off all the hardware options. Eg uncheck both, and chose "none" for vertex shader. If that "fixes" the issue, turn them back on one at a time till you find the one that breaks it.

---

### Post by Muffinabus on 2008-07-10
Naw, it didn't work.  I unchecked all the boxes on the 'Graphics' tab of the Wine configuration and turned off Vertex Shader Support and Pixel Shader and WoW still started up all funky.

Do you know of any other settings where Wine may be causing funky things to happen with my resolution/windows?

Also, thanks for the help too, appreciate it.

---

### Post by Felson on 2008-07-10
Nope, that is the only place I know of. Does it do this with any game/app or just WOW? Or any that want 3D support? try running winecfg as a test (that is the same as wineconfig except it runs in wine...)

---

### Post by Muffinabus on 2008-07-10
So far it has only been with games.  I've ran Ventrilo and Steam with no problems, but the moment I start up counter strike or world of warcraft, everything goes nuts.  There WAS one time when I started up the Wine uninstall programs thing and it happened, but that was only once and it since has not happened again.

---

### Post by Felson on 2008-07-10
Ok, here is an idea on how to get some useful intell on what might be up... 
Open a terminal and:
```

cd ~
mkdir OutTmp
cd PathToGame
wine GameExe 2> ~/OutTmp/stderr > ~/OutTmp/stdout

```
After that we should have all the output of wine in those 2 files so we can look in the stderr one and see if there is anything useful.

---

### Post by Muffinabus on 2008-07-10
This was in stderr from starting up wow.exe.

```
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ec94,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3563
fixme:win:EnumDisplayDevicesW ((null),0,0x32f2c8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f42c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5a0,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x133d98) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x32f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f144,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x37402bc4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x32d194,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32d200,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x133d98) : stub
```

stdout was empty

---

### Post by Felson on 2008-07-10
Well... That didn't help me one bit. Maybe someone at wine HQ will be able to see if anything in there could cause that. Other then that, the last idea I have, is to reinstall wine + your Video drivers. Before a full reinstall, try 
```

cd ~
mv .wine .wine_bak
wineprefixcreate

```
And then run your game again. Failing that, uninstall wine + Video drivers, and then reinstall them.
If the above code doesn't help, or it causes wine to just not work for you installed apps, 
```

rm -rf .wine
mv .wine_bak .wine

```
to go back to the way it was.

---

### Post by Muffinabus on 2008-07-10
Will give it a try.  And the thought of reinstalling my video drivers makes me want to throw up );  It was quite a process to get them working... though I suppose there's little point in them working if I can't play any games :3

EDIT: doing the wineprefixcreate thing corrupted my graphics again AND made my programs not work, so I decided to revert it back, lol.  Nice try though (:

Guess it's time to... /shudder, reinstall my wine and my video drivers :3

---

### Post by agtownz on 2008-07-11
The same thing happens to me when I close TrueCombat Elite, which plays fullscreen and doesn't use Wine.

---

### Post by Felson on 2008-07-11
Looks like there is 3 of you now. pugface looks like he has the same issue. There has got to be something in winebugzilla by now, but I will be darnd if I have a clue what you guys need to search for.

---

### Post by pugface on 2008-07-12
Yes, I'm having the same issues. Could be a problem with the ATI drivers, I suppose, since I'm also using an ATI card (laptop 200M with the 8.6 catalyst drivers). The strange thing is that native games (2d and 3d) work fine for me, just like Muffinabus.

Edit: I just tried upgrading to Wine 1.1.1, it didn't seem to help.

---

### Post by mikaPELL on 2008-07-12
I'm experiencing the same problem as well. My video card is an ATI Radeon Mobility X1600...
My computer is an Asus F3JA, if that's relevant. Also, from some of the error messages I see, could the sound drivers be the problem? My sound card is an Intel HD, which has caused me quite a few problems earlier.

---

### Post by pugface on 2008-07-14
Don't suppose any of you have managed to find a fix? Did downgrading Wine work for anyone?

---

### Post by hyz on 2008-07-16
I seem to have the same problem. I have a x1400 running Catalyst 8.6. I don't think it's wine that's causing the problem because I tried Crossover and the results were the same as wine. Any ideas?

---

### Post by pugface on 2008-07-18
I guess we'll just have to hope it's a Wine issue and gets fixed in the next release...

---

### Post by JUMBODUMBO on 2008-07-19
Downgrading the drivers to Catalyst 8.4 or earlier works for me. Had the same problem with 8.6 and Wine. EnvyNG installs 8.6 now so can't use that anymore.

---

### Post by man_iii on 2008-07-20
Yep ... Ive been living with this weird Wine/ATI Catalyst v8.6 bug ... 

Tried EnvyNG ... without EnvyNG .... Only reverting the Driver to v8.4 gives me back wine goodness... 

I dunno what else to do ... :-P 

Anyone pestered DAAMIT (AMD / ATI) on this issue ? 

Maybe we need to submit a Winebug report ? 

Im a n00b when it comes to Ubuntu ... Pretty much a Slackware guy...

Used to make;make install ... never had any sillyness with apt or such like.... HELP!

---

### Post by JackCorbae on 2008-07-24
I get the same problem when trying to start NWN2 or The Sims 2 in Wine 1.1.1

The problem started when I went from ATI's 8.5 driver to the 8.6 version. 8.7 also doesn't fix the issue.

I could go back to 8.5 but in 8.5 my NWN characters were invisible! :) I could see their armour but not the person wearing it. It was kind of funny actually.

I found that I can fix the screen after exiting the application but use ALT+F1 to jump to the console and then ALT+F7 to get back to the x-window.

I'll stick to using WindowsXP for NWN and The Sims 2 until ATI release 8.8 and then I'll try again! :)

---

### Post by Felson on 2008-07-25
Never thought of this as a workaround to your guys issue before, but since changing TTYS seems to "fix" the screwed up video, why don't one of you try a script I made...
[here]("http://ubuntuforums.org/showthread.php?t=854354")
It creates a new XWindow session to run your game with. If nothing else, it will probably stop your main session from going nuts.

---

### Post by Melcar on 2008-07-25
[http://www.phoronix.com/forums/showthread.php?t=10940]("http://www.phoronix.com/forums/showthread.php?t=10940")

It's the driver's fault.  I have yet to find mention of any real fix.  Fglrx 8.5 and before work fine, however, so you may want to rollback your drivers.  Currently, we are trying to get some Wine based tests on PTS. If we do manage to agree on a suitable Wine benchmark, hopefully the generated feedback will help overall Wine compatibility.

---

### Post by Akingboy on 2008-07-25
Had the same problem with ATI's driver 8.7
Then I uninstalled them and installed the ones from Ubuntus options menu.

---

### Post by JackCorbae on 2008-07-25
I've opened a ticket with ATI - whether it does any good or not is anyone's guess.

Maybe everyone should do they same. Sure, there's only four of us so far but every little bit helps! :)

Ah ... I just found this response in my mailbox:

We have responded to your issue.
Solution:	

The issue may be hardware related.  Testing the card in another system in a supported operating system would help.  If you are noticing the corruption before the OS loads it is also an indication of a hardware issue with the card.  If reverting to the earlier drivers resolves the issue it would sound more software related than anything else.

We do not offer support or troubleshooting for any of the Radeon based cards in Linux at this time.

 

Regarding LINUX support for ATI Video cards:

Although we have driver for Linux posted on the ATI website, we do not troubleshoot driver or multimedia issues in Linux directly. We work closely with the Linux community to provide support options. On our website we do have link to several Linux support sites that may help you. I have included the link below to this website..

Our web site offers several links to Linux support web sites that may help you.

You may click on the link below and go to its website to find information that might be helpful to your case. Our Engineers are informal contributors.
[http://wiki.cchtml.com/index.php/Main_Page\](http://wiki.cchtml.com/index.php/Main_Page\)
This is also a very good article from a third party
[http://www.rage3d.com/content/articles/atilinuxhowto/Linux_ATI.html#SECTION000140000000000000000](http://www.rage3d.com/content/articles/atilinuxhowto/Linux_ATI.html#SECTION000140000000000000000)

If you are experiencing problems with our latest driver release, or if you have suggestions about how to make our drivers better, please take the time to submit your feedback.

Note: We do not respond to all support inquires. 

Continue to the Linux Driver Feedback submission page.

 
Ticket Information:
Ticket #:	737-1353165
Date Created:	7/24/2008 10:07 PM EDT
Category: 	Linux Driver Feedback

To update or check the status of this Ticket:
- Go to: [http://support.ati.com/ics/support/default.asp?deptID=894&ticketID=1353165](http://support.ati.com/ics/support/default.asp?deptID=894&ticketID=1353165)
- Log in, and you will be automatically taken to the Ticket page.


Customer Care
ATI Technologies Inc.
ati.com

---

### Post by JackCorbae on 2008-07-25
I filled in their online "Linux Crew Driver Feedback Program" form. Anyone else having the problem should also fill in the form:

[http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=508&type=web](http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=508&type=web)

---

### Post by Melcar on 2008-07-25
Don't worry guys.  I already mentioned Wine problems on the mailing list.  Also, hopefully we can get some viable benchmarks running under Wine for PTS sometime soon, which should allow for a better "grasp" of the situation (instead of just bug reports).

---

