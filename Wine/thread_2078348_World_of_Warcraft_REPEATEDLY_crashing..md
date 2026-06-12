---
title: "World of Warcraft REPEATEDLY crashing."
date: 2012-10-30
forum: Wine
---

### Post by xelab1090 on 2012-10-30
The launcher launches, everything boots up fine, no hiccups during the loading screen. But the gameplay. THE GAMEPLAY. It's so laggy I turned it down to Fair (2/5). Even then, I take a mere two or so steps at 10 FPS and then bam get hit with this error. Every time. Any help would be appreciated!


This application has encountered a critical error:

ERROR #134 (0x85100086) Fatal condition!

Program:	C:\Program Files (x86)\World of Warcraft\Wow.exe
ProcessID:	61

Failed to read file from local.

Details: (Streaming Status: Enabled / Mfil Rdy / Data Rdy, Build: 16135)
[105] err=0 text=SFileReadFile - DUNGEONS\TEXTURES\PANDAREN\EAST_TEMPLE\DK_EASTTEMPLE_BASIC_WALL01.blp - Data\texture.MPQ
[104] err=87 text=System_Mopaq::mopaq_read - fail to repair offset 0 amount 175972
[103] err=87 text=System_Mopaq::SectorReadHandler::InitializeAndRead - fail to repair offset 0 amount 175972
[102] err=-2062548855 text=System_Mopaq::SectorReadHandler::ReadAndDecompressData - PerformRead error 0 52 116574 175972 entry: 974817254 116626 175972 2147484160 0
[101] err=1006 text=System_Mopaq::MD5VerifyData::ValidateRead - InitializeMD5Buffer fail 2 52
[100] err=1006 text=System_Mopaq::MD5VerifyData::ValidateBlock - ValidateBlock fail - m_length:116626 m_baseOffset:974817254 blockIndex:1 length:16384, retry:3
[99] err=1006 text=System_Mopaq::MD5VerifyData::ValidateBlock - ValidateBlock fail - m_length:116626 m_baseOffset:974817254 blockIndex:1 length:16384, retry:2
[98] err=1006 text=System_Mopaq::MD5VerifyData::ValidateBlock - ValidateBlock fail - m_length:116626 m_baseOffset:974817254 blockIndex:1 length:16384, retry:1
[97] err=1006 text=System_Mopaq::MD5VerifyData::ValidateBlock - ValidateBlock fail - m_length:116626 m_baseOffset:974817254 blockIndex:0 length:16384, retry:1
[96] err=1006 text=RepairFile - Failed to re-read the bad section: offset = 0, length = 52
[95] err=1006 text=System_Mopaq::MD5VerifyData::ValidateRead - InitializeMD5Buffer fail 1 0
[94] err=1006 text=System_Mopaq::MD5VerifyData::ValidateBlock - ValidateBlock fail - m_length:116626 m_baseOffset:974817254 blockIndex:0 length:16384, retry:3
[93] err=1006 text=System_Mopaq::MD5VerifyData::ValidateBlock - ValidateBlock fail - m_length:116626 m_baseOffset:974817254 blockIndex:0 length:16384, retry:2
[92] err=1006 text=System_Mopaq::MD5VerifyData::ValidateBlock 

WoWBuild: 16135
Version: 5.0.5
Type:  WoW
Platform: X86
Session Time(hh:mm:ss):  00:01:03
Time in World(hh:mm:ss): 00:00:37
Number of Char Logins:  1
Realm: Wyrmrest Accord (206.16.119.21:3724)
Local Zone: The Jade Forest (area id = 5785)
Local Player: Oxymoronic, 06800000057AD271, (870, 2180.76, -1734.62, 230.413)
Total lua memory: 17293KB
Current Addon: (null)
Current Addon function: UNKNOWN
Current Addon object: (null)

Settings: 
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enUS"
SET showToolsUI "1"
SET accounttype "MP"
SET readTerminationWithoutNotice "-1"
SET launchThirtyTwoBitClient "1"
SET installLocale "enUS"
SET hwDetect "0"
SET videoOptionsVersion "5"
SET gxApi "D3D9"
SET gxWindow "0"
SET gxMaximize "0"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "1300"
SET waterDetail "3"
SET groundEffectDensity "128"
SET groundEffectDist "260"
SET environmentDetail "150"
SET terrainLodDist "650"
SET weatherDensity "3"
SET enterWorld "1"
SET accountList "!VAMPIRICFANG|JBLTV|BRINKSJM|WoW1|"
SET g_accountUsesToken "1"
SET realmName "Wyrmrest Accord"
SET gameTip "18"
SET gxTripleBuffer "1"
SET gxVSync "1"
SET gxCursor "0"
SET Gamma "1.000000"
SET sunShafts "2"
SET projectedTextures "1"
SET shadowMode "3"
SET shadowTextureSize "2048"
SET SSAO "1"
SET textureFilteringMode "3"
SET componentTextureLevel "0"
SET UIFaster "2"
SET mouseSpeed "1"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET VoiceActivationSensitivity "0.39999997615814"

----------------------------------------
Installation settings:
----------------------------------------
UID:  wow_enus
Expansion Level: 4
PTR: 0
Beta: 0
PatchURL: 'http://enUS.patch.battle.net:1119/patch'
ProductCode: 'WoW'

----------------------------------------
               GxInfo
----------------------------------------
GxApi: D3D9
Shader Model: 3_0
  Vertex: vs_3_0
  Pixel: ps_3_0
Adapter Count: 1

Adapter 0 (primary):
  Driver: nv4_disp.dll
  Version: 6.15.0012.6658
  Description: NVIDIA GeForce 8800 GTX
  DeviceName: \\.\DISPLAY1

---

### Post by xelab1090 on 2012-10-30
This isn't the entire error message, I cut it off. It's available upon request, as I keep running into it trying to make WoW run decent. My OS is 64-bit Ubuntu 12.10, I installed the latest graphics drivers as well. I think the biggest thing that's biting at me is Windows was faster! I left it because it was slow! :P

---

### Post by squakie on 2012-10-30
Why don't you check the gaming and leisure forum?

---

### Post by CharlesA on 2012-10-30
You do know this a Linux forum, right? It looks like you are trying to run Warcraft from a 64-bit Windows machine.

In any case, try to repair or reinstall the Warcraft installation and see if that fixes the problem because the error is 'cannot read load file.'

---

### Post by oldos2er on 2012-10-30
Moved to Wine.

---

### Post by CharlesA on 2012-10-30
> **oldos2er said:**
> Moved to Wine.
Don't think it's a wine thing as they are running it on a Windows box.

@OP: It would be a better idea to either post on the battle.net forums or over here:
[http://www.sevenforums.com/](http://www.sevenforums.com/)

---

### Post by xelab1090 on 2012-10-30
I'm so sick of people assuming I'm stupid...

Okay. I used the search function already, I thumbed over multiple forum posts, but I didn't see any one having any problem like I'm having. Second, I built this computer myself in 2010, the OS is Linux, Ubuntu 12.10, I assure you of this. It looks like it's not loading the textures correctly if I'm interpreting the error correctly. Is there any way to fix this?

---

### Post by xelab1090 on 2012-10-30
I'm not running windows. That's the directory Wine set up so the game would function in Linux.

---

### Post by CharlesA on 2012-10-30
How are you running Warcraft then? Wine or CrossOver/Virtualization?

---

### Post by xelab1090 on 2012-10-30
....Wine 1.5.16

---

### Post by cwwilson721 on 2012-10-30
We need to know what Graphics Hardware you're running (I.E. Ati/AMD, Nvidia, Intel, whatever)

And (only if NOT Intel) what driver version you have

Are you running in "-opengl" mode or just D3D?

One thing you may want to try first is a WoW repair running the Repair.exe file in the WoW folder (where ever you have it installed)(you may have a bad file in there)
Ex:
```
env WINEPREFIX=/home/<username>/.wine wine "C:/Program Files(x86)/World of Warcraft/Repair.exe"
```

---

### Post by xelab1090 on 2012-10-31
I'm using an Nvidia 8800 GTX, it was at the bottom of the error msg. The driver version, is I believe; 304.54 or something like that. I do not know if it's in OpenGL or D3D, is there a way of telling? World of Warcraft doesn't have a repair tool any more as well, they incorporated it into the launcher when Cataclysm hit.

EDIT: I believe it's running in D3d9 mode.

---

### Post by xelab1090 on 2012-10-31
Alright, got it running in OpenGL mode, it looks like poop but there's no other option right now! The servers are shutting down for maintenance, which is weird since it's a wednesday, but what ever, got it working. I was having to type in the terminal to load it though. Is there a way I can run it in OpenGL just by clicking on the icon rather than having to use the terminal?

EDIT: Was in Orgrimmar and running in OpenGL mode and got another error, since the other server I have characters on was still up, saying it "Failed to read file from local". It's a texture loading issue, too, I know it is. When I cast to use my mount the cast bar was just a green line, and when I was on my mount my character completely disappeared. I look at all the things that failed to load, they're all textures or texture.mpq...

---

### Post by cwwilson721 on 2012-10-31
Still don't know the hardware you are using.

**Personally, I prefer "running" (and in my case, faster than Windows) than "pretty"

If I can see it, I can kill it. If I cannot see it, no matter how good it looks, it can kill me. ** /endrant about opengl

---

### Post by xelab1090 on 2012-10-31
I'm using...
 
Intel e5200 Dual Core Processor clocked at 2.5Ghz
4Gb of DDR2 800 RAM
500Gb 7200 RPM HDD
NVIDIA 8800GTX 768mb with current drivers installed.
Intel P5KPL-CM motherboard
500W BFG PSU
CD Optical Drive
Case(not that it matters) Antec 300

---

### Post by cwwilson721 on 2012-10-31
> **xelab1090 said:**
> I'm using...
 
Intel e5200 Dual Core Processor clocked at 2.5Ghz
4Gb of DDR2 800 RAM
500Gb 7200 RPM HDD
NVIDIA 8800GTX 768mb with [COLOR="Red"]current drivers installed[/COLOR].
Intel P5KPL-CM motherboard
500W BFG PSU
CD Optical Drive
Case(not that it matters) Antec 300

Your video hardware is technically the same as mine. The processor difference is almost a wash, so I mostly expect the same FPS as my setup. However, mine has been "optimized" over MANY years (since Vanilla, and the great mass wine boot from Blizzard). All in all, it should do OK. Not great in 25+ mans, but doable.

That is what I was wondering (the part in red above), along with manufacturer/chip of the video.

Are the drivers the ones from Ubuntu? or from Nvidia?

It does make a difference.

And what version?

The questions I am asking are to help you out. Different versions from different sources create different outcomes. Some from Nvidia don't have the needed "support" files for Ubuntu to correctly 'translate' the wine D3D calls to opengl and let them render in hardware. On the same token, there are some Ubuntu packaged drivers that seem to be lacking something, and causing issues with wine and WoW. 

*[SIZE="1"](All of the above is EXTREMELY simplistic. But, at a certain level, true. I feel the "troll alert" about to sound off. But let's help the OP first, then carry on the discussion afterwards, AFTER he gets to kill some 'toons in WoW)[/SIZE]*

---

### Post by cwwilson721 on 2012-10-31
As an addendum to the above:

I am currently waiting on hardware for my cable/internet, and am stuck for the time being, on a GPRS  phone tether for my internet, and as such, no WoW, or any patches since MoP .

As such, I'll  try to help as much as possible, but may have to rely on the OP and others in this GREAT community (no disrespect at all. It's TRULY how I feel) to help out with actual results.

Remember, WoW/wine changes every patch. Remember the hardware "debuff" between WotLK and Cata? Let's see how this turns out

---

### Post by holastickboy on 2012-10-31
Add this to your config.wtf file to improve performance even further

SET gxApi &#8220;opengl&#8221;
SET ffxDeath &#8220;0&#8243;
SET ffxGlow &#8220;0&#8243;

Reduces quality, but can significantly improve frame rate.  Use a questing mod such as carbonite or tomtom to guide you to quests on map (wow has a bug in which characters are not rendered on maps to show your location).

Edit: if you are running x64 Linux, you can run x64 WoW, which can increase your performance significantly (allows WoW to use more than 2GB of RAM).  Just be sure to apt-get install wine64 first, then you can do wine64 Wow-64.exe.  That adds a lot of performance for me!

---

### Post by xelab1090 on 2012-10-31
I got it working, a little bit. I did LFR on my priest and it crashed a couple times when I first got in there due to the textures not loading properly, but once I logged in the third time I stayed in game until I got bored and decided to log after doing both halves of LFR, about 3 hours. Right now I'm getting about 15-20 FPS in LFR, but I don't care, I'm running WoW in Linux.

---

### Post by cwwilson721 on 2012-10-31
> **holastickboy said:**
> Add this to your config.wtf file to improve performance even further

SET gxApi “opengl”
SET ffxDeath “0&#8243;
SET ffxGlow “0&#8243;

Reduces quality, but can significantly improve frame rate.  Use a questing mod such as carbonite or tomtom to guide you to quests on map (wow has a bug in which characters are not rendered on maps to show your location).

Edit: if you are running x64 Linux, you can run x64 WoW, which can increase your performance significantly (allows WoW to use more than 2GB of RAM).  Just be sure to apt-get install wine64 first, then you can do wine64 Wow-64.exe.  That adds a lot of performance for me!

Actually, that is not needed (wine64). a "fresh" wine1.5 installs as 64bit (if running 64 bit Ubuntu), with an option to run 32bit.

By default, any prefixes made are 64bit. If you want (or the Win prog says you HAVE TO) run a 32bit wine, just (in terminal when you create the prefix):
```
export WINEARCH=win32
export WINEPREFIX=<wherever you want it>
winecfg
```
The above will create the 32bit wine folder, install the gecko stuff and a few other things, and away you go.

---

### Post by MontrealCorp on 2013-01-10
on my ubuntu 12.04 evrything works great with wine for WC3.
 
the problem is only my mouse that seem to lag , whe i move it it take like 1 sec to actually see the movement i asked for, i just cant play dota like this ?
anyone got any solution, yes i did update my proprietary drivers 
 
ty

---

### Post by MontrealCorp on 2013-01-12
well i finally fix all my issues except one :(.

the way i did it with mose porblem and the resolution is to use playonlinux and disable the virtual desktop function in wine.

the only thing left is the sound :(

seem the sound is lagging, with echo and i hear it in slow motion too .

anyone knows what can i do to fix this?
ty

---

### Post by zurackjain on 2013-01-24
_content mistaked_[]("http://www.zhafguides.com/")

---

