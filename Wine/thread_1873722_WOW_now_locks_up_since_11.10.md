---
title: "WOW now locks up since 11.10"
date: 2011-11-01
forum: Wine
---

### Post by CPUUnlimited on 2011-11-01
Installed 11.10, had nothing but problems so I decided to format and start over.
Finally got everything working however now World Of Warcraft, which ran fine on 11.04, randomly locks up for about 30 seconds.  VERY annoying!  I have been looking all over the net for an answer, have seen lots of posts from others with the same issue, but no solution. :( If ANYONE has any idea of where to even start, please let me know.

Another issue is the sound in the game, RANDOMLY, I have to pick options, the change from hardware to software sound, then back to hardware to get the sound working again.  Yes, I have tried padsp, which makes NO difference at all.

If I run WOW in opengl mode, the random lockups are still there, AND my graphics are broken which is hard to explain, but many objects have sort of a 2d look instead of 3d look and have white boxes around them, that is the best I can describe it.  In directX mode this problem goes away.  The only thing I used my system for is WOW.  Thinking of formatting again and going back to 11.04, but I'd rather try to figure this out.

Thanks for any thoughts.

---

### Post by Perfect Storm on 2011-11-01
Moved to wine section.

---

### Post by Tweak42 on 2011-11-03
Although you described your problem very well, you left out a description of your hardware, video driver version, wine version, and any errors you get at lock up when running wow in a terminal.

---

### Post by CPUUnlimited on 2011-11-03
My hardware is an AMD Phenom II X4 840 on an MSI 790FX-GD70 MB, 1000 w Kingwin PS, 4 gig ram and water cooled.  The video card is an XFX GeForce GTX 550 Ti with 1 gig ram and the driver version is 285.05.09 (yes, I have tried other versions of the driver).
Wine version is 1.3.31 (also yes, I have tried other versions of Wine).

If it helps anyone, the problem with the lockup seems to happen more often when I have Mangler running, (vent client).  Also, this problem did NOT happen with Ubuntu 10.04 so I thought it may have just been a problem with the upgrade and have since formatted the HD and started all over again.

As for errors when running WOW from a terminal, I just started one now and will post the results at the next lockup.  Here are the errors I get at launch though:

fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a534552 (as fourcc: RESZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a534552) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a534552 (as fourcc: RESZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a534552) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a534552 (as fourcc: RESZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a534552) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:win:EnumDisplayDevicesW ((null),0,0x32f0c8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ef8c,0x00000000), stub!
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 10000 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 10000 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 10000 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 10000 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 10000 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 10000 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 10000 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 10000 channels, pretending there's only 2 channels
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x32f84c): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f318,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f1dc,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT/DATA_SEND_TIMEOUT 5000
fixme:process:GetLogicalProcessorInformation (0x1abe36c,0x1abe96c): stub
fixme:process:GetLogicalProcessorInformation (0x1abe36c,0x1abe96c): stub
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:process:GetLogicalProcessorInformation (0x1abe36c,0x1abe96c): stub
fixme:process:GetLogicalProcessorInformation (0x1abe36c,0x1abe96c): stub
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!

---

### Post by cwwilson721 on 2011-11-03
Things that may narrow it down:
[LIST]
[*]Make sure WoW is running (through winecfg) in XP mode
[*]Disable sound (Do it through BIOS if possible. ) Re-enable if that isn't the culprit (But the 1000 channels is making me lean this direction)
[/LIST]

Give these two things a try. It might work, might not, but in either case, will narrow it down

---

### Post by CPUUnlimited on 2011-11-03
OK, just locked up again, only WOW was running, mangler was NOT running.  The only errors in the terminal window were:
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.

which repeats over and over and over all the time the game is running, not just during the lockup.

The lockup also happens no matter what mode WOW is running in under wow, be it XP VISTA, etc.

A search on the internet for that 1000 chan error shows up ALL OVER the place in almost every post about Wine running games, such as wow, rift, COD etc.  Everyone just seems to ignore that error which seems strange to me.  

Seeing that the above error is happening over and over I suspect some sort of stack overflow issue after that error happens thousands of times, but that is just a guess.  Also a google search for that error also shows up in just about every post of Wine and gameing.

I will disable sound and attempt to test that... will post back soon again

---

### Post by CPUUnlimited on 2011-11-03
Sound seems like the problem... 2 troll dngs with no lockup when sound is off
... now.. for the big question.. how the heck do I fix it?

---

### Post by cwwilson721 on 2011-11-04
You'll have to run WoW w/out sound for now....

And wait for wine to fix the sound issues

---

### Post by CPUUnlimited on 2011-11-04
HAHA.. VERY funny... I don't think so!  There has to be a way to fix the sound, I just need to find a Linux GURU that understands the sound system better than me.  That shouldn't be hard.

---

### Post by 11hjpphty76lkjj on 2012-02-10
I'm having exactly the same problem. Even WITH my sound disabled... any other suggestions?

---

