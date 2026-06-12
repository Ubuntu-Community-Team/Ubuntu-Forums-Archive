---
title: "No sound playing in Wine"
date: 2011-09-11
forum: Wine
---

### Post by weirdAbacist on 2011-09-11
I recently installed Wine to see how well Steam runs (so i can finally get rid of my Windows Vista dualboot and just have Ubuntu!) and everything seems to run smoothly except the sound. Now I realize this is a common problem, and I've tried a few solutions, but none have worked thus far.

First I tried disabling PulseAudio, as that seems to be a large culprit. I used "sudo nano /etc/pulse/client.conf" and changed "autospawn = yes" to "autospawn = no" and then used "killall pulseaudio" to shut down the program, but that didn't help.

I then tried messing with the audio configuration of Wine itself with the "winecfg" command, and I realized that no matter what drivers I select (ALSA, OSS, JACK, NAS, EsounD) and whether I select "Full" or "Emulation," I get no sound feedback when I click "Test Sound."

At this point I am out of ideas. I am still new to Ubuntu, so I could be overlooking something very simple. I appreciate any and all feedback!

EDIT: In case it's relevant, I am running Ubuntu 11.04 and Wine 1.2.2

-weird

---

### Post by An Sanct on 2011-09-11
I would advice you to try "PlayOnLinux" as it is a front end for wine configuration and helps with installation and tweaking of software (games).

---

### Post by shubham1 on 2011-09-11
[http://ubuntuforums.org/showpost.php?p=11237758&postcount=4](http://ubuntuforums.org/showpost.php?p=11237758&postcount=4)

---

### Post by lbeavisc on 2011-09-11
does sound work fine in ubuntu? can you record something? if so it may just be the settings in the wine program. i left the default soud setup in ubuntu  and selected alsa in wine and hit apply. I had to reload the winecfg to get the test to work and to get sound and mic to work i had to select alsa in the game for output and default for mic
the defau;t had to be the lowercase one in the dropdown menu

---

### Post by weirdAbacist on 2011-09-11
> **An Sanct said:**
> I would advice you to try "PlayOnLinux" as it is a front end for wine configuration and helps with installation and tweaking of software (games).

I am using PlayOnLinux actually (sorry, I should have included that information in my post). Steam is the only thing I downloaded via POL so far, and once Steam was up and running I installed one of the games I already own on Steam (Recettear). Unfortunately my save data is elsewhere (probably on my Vista boot) but that is a problem I will tackle at another time.

> **shubham1 said:**
> [http://ubuntuforums.org/showpost.php?p=11237758&postcount=4](http://ubuntuforums.org/showpost.php?p=11237758&postcount=4)

The linked post makes reference to PulseAudio, and I already tried these techniques to successfully disable it, although the silence persists.

> **lbeavisc said:**
> does sound work fine in ubuntu? can you record something? if so it may just be the settings in the wine program. i left the default soud setup in ubuntu  and selected alsa in wine and hit apply. I had to reload the winecfg to get the test to work and to get sound and mic to work i had to select alsa in the game for output and default for mic
the defau;t had to be the lowercase one in the dropdown menu

Sound works fine in Ubuntu. I just checked the Sound Preferences and the hardware is able to recognize both input and output. However I had to turn the volume up to hear the test output sound; when I tried winecfg again with max volume I was able to barely detect a faint sound (like a foot stepping on dry leaves) so wine audio seems to be working.

----------

UPDATE: Half-Life 2 has sound. Due to my poor problem solving skills I assumed Wine was the issue when the first program I tried running didn't work, but now I'm guessing the problem lies with Recettear itself. Sorry all!

---

### Post by lbeavisc on 2011-09-11
no problem! still havent got my issues fixed but for some reson now the audio recorded from the input is garbled in mint but worked fine in ubuntu. lol probably gonna switch back to ubuntu but disable unity and see if my mouse problem stops

oh you also may want to try the beta of wine by adding their ppa  *"ppa:ubuntu-wine/ppa"* instructions at their site [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

---

### Post by weirdAbacist on 2011-09-12
So it seems like Recettear's got some bugs to work out with Wine, and I'm trying my best now to fix them. I found two useful pages: ([Steam Games On Linux]("http://www.steamgamesonlinux.com/recettear-an-item-shops-tale/") and [Recettear Forums]("http://www.carpefulgur.com/forum/index.php?topic=178.0#"))

Steam Games On Linux puts it succinctly: "no sound without directx9 dsound=native"

Using winetricks I have installed the drivers for directx9 (d3dx9) and using winecfg I went to Library and set dsound to native only. This changed nothing.

I also followed the instructions on the Recettear Forums, similarly to no avail. I did the export command and installed both "directmusic" and "dsound," which seemed to work fine, although there's still no music when I run the game. Of interest though is this line in the forum post: "In the terminal you will use to both set this up and to run Recettear..." Am I supposed to run Recettear from the terminal? I've been running it through Steam, which itself runs through Wine, and I have no idea how I might run the program through the terminal alone.

ALSO! I managed to find the game files in the directory, and although the music doesn't play during the game, I have access to the music files and can play them perfectly fine outside of the game. I also tried running the game outside of Steam, but nothing happens when I try to run it directly from the directory.

---

### Post by Toz on 2011-09-12
> **weirdAbacist said:**
> Of interest though is this line in the forum post: "In the terminal you will use to both set this up and to run Recettear..." Am I supposed to run Recettear from the terminal? I've been running it through Steam, which itself runs through Wine, and I have no idea how I might run the program through the terminal alone.

If you're running this through POL, then you won't have to run it through the terminal. The command posted in that forum post simply sets the correct prefix before running the game. POL does this automatically for you.

From within POL, have you installed dsound? Which version of POL are you using?

---

### Post by An Sanct on 2011-09-12
> **Toz said:**
> If you're running this through POL, then you won't have to run it through the terminal. The command posted in that forum post simply sets the correct prefix before running the game. POL does this automatically for you.

From within POL, have you installed dsound? Which version of POL are you using?

(POL = PlayOnLinux)

---

### Post by Toz on 2011-09-12
> **An Sanct said:**
> (POL = PlayOnLinux)
Yes. 

What version of PlayOnLinux do you have installed? The reason that I ask is that version 3.8.8 (the one in the official ubuntu repositories), is outdated. You can get/install version 4.0.12 from the website. (Installation instructions in the "Ubuntu" section at [http://www.playonlinux.com/en/download.html]("http://www.playonlinux.com/en/download.html"))

The interesting part of the forum post that you linked to ([http://www.carpefulgur.com/forum/index.php?topic=178.0#]("http://www.carpefulgur.com/forum/index.php?topic=178.0#")) was the second half where the post mentions that **dsound** and **directmusic** need to be installed. The post talks about patching and using winetricks to do this, but its not necessary. If you're using POL, the method to install those two functions differs.

**On version 4.0.12**: you need to click on the "Configure" toolbar icon, select the game in the left pane, click the "Install Packages" tab on the right side, and install the dsound and directmusic packages.

The method to do it manually, using winetricks via the command-line, is more complicated. The methods above are simpler.

---

### Post by weirdAbacist on 2011-09-16
> **Toz said:**
> Yes. 

What version of PlayOnLinux do you have installed? The reason that I ask is that version 3.8.8 (the one in the official ubuntu repositories), is outdated. You can get/install version 4.0.12 from the website. (Installation instructions in the "Ubuntu" section at [http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html))

The interesting part of the forum post that you linked to ([http://www.carpefulgur.com/forum/index.php?topic=178.0#](http://www.carpefulgur.com/forum/index.php?topic=178.0#)) was the second half where the post mentions that **dsound** and **directmusic** need to be installed. The post talks about patching and using winetricks to do this, but its not necessary. If you're using POL, the method to install those two functions differs.

**On version 4.0.12**: you need to click on the "Configure" toolbar icon, select the game in the left pane, click the "Install Packages" tab on the right side, and install the dsound and directmusic packages.

The method to do it manually, using winetricks via the command-line, is more complicated. The methods above are simpler.

I have version 4.0.11 of POL. I tried the "Configure" option, and installing dsound and directmusic (and directx9 as well) was smooth and error-free. When I tried playing Recettear though, the game window won't appear now. I go to Steam, hit "Play now," a message pops up saying "preparing to launch Recettear," it disappears, and then nothing happens. I get the feeling that it is starting up but instantly closing, as I get the "Steam news" update that typically appears when exiting games.

EDIT: I just noticed that my Steam avatar's color ring changes color from blue to green when I try playing the game, signifying that I am "playing a game" (green) and not just "online" (blue), and the color quickly returns to blue after a few seconds. This confirms my suspicion that the game is starting but then immediately closing.

So the sound *might* be working now. The fact that I can't check seems to be a bigger problem though. :roll:

---

### Post by Toz on 2011-09-17
Try changing some of the settings on the Configure->Display tab. Specifically setting "Direct Draw Renderer" to "OpenGL" and increasing the value of the "Video Memory" setting. I would also suggest enabling the "Enable debugging" checkbox on the "General" tab so that you can see what error messages are being generated.

---

### Post by weirdAbacist on 2011-09-17
I just realized that another game I downloaded via Wine but independent of POL (Touhou 6) is also experiencing problems running, similar to Recettear (game won't start). This ends up being beneficial, as I have no idea how things work with Steam or POL but I have all the files for Touhou making debugging much easier.

When I try running Touhou via the terminal/wine, I get these error messages:

```
err:module:import_dll Library DSOUND.dll (which is needed by L"Z:\\home\\xander\\Desktop\\Touhou\\EoSD\\th06e.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\xander\\Desktop\\Touhou\\EoSD\\th06e.exe" failed, status c0000135

```When I checked winecfg it said that dsound was installed, so I'm not sure why that's an issue, and I don't understand the second error at all.

I feel like trying to fix one game in Wine is affecting the performance of all my games in Wine. :(

---

### Post by Toz on 2011-09-17
When you install a game from within POL, it creates a new separate windows environment instance (wineprefix) for each install (see ~/.PlayOnLinux/wineprefix). If you use the POL front end to run winecfg (making sure you've selected the correct app/game first), the changes will only affect that prefix.

When you install and app/game using wine directly, it defaults to the "wine" prefix found at ~/.wine. Unless you are cross-contaminating the prefixes, changes in one shouldn't affect the second.

With respect to **Recettear**, run the POL game with debugging enabled. It should give us a hint as to what is going on. Make sure you are running winecfg from within the POL frontend, with the game selected on the left pane first.

With respect to **Touhou**, try running winecfg from the command line to see its configuration files. From the error message above, it looks like dsound isn't installed in the default wine prefix. You can install dsound in the default prefix if you run 
```
winetricks
``` from the command line. If dsound does not exist as an option in your version of winetricks, you will need to upgrade to a newer version (see: [http://wiki.winehq.org/winetricks]("http://wiki.winehq.org/winetricks")). There is some more info about running this game in wine here: [http://touhou.wikia.com/wiki/Running_in_Linux]("http://touhou.wikia.com/wiki/Running_in_Linux")

---

### Post by weirdAbacist on 2011-09-17
First of all, I would like to thank you tremendously for consistently helping me out with all my Ubuntu gaming troubles, Toz. I really appreciate it!

When I run Recettear I get a similar error to Touhou:

```
err:module:import_dll Library d3dxof.dll (which is needed by L"C:\\Program Files\\Steamapps\\common\\recettear.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Steamapps\\common\\recettear.exe" failed, status c0000135
```Even the status code c0000135 is the same!

When I go to POL -> Configure to add d3dxof.dll, I can't find it in the Library. There are other d3dx# but not d3dxof, and I'm pretty sure I have d3dx9, directx9, and directmusic installed for POL.

As for Touhou, I already had dsound.dll, but I changed it from "native" to "builtin" and it's working just fine now. I must've changed it to native when trying to get POL sound to work.

---

### Post by Toz on 2011-09-18
No worries.

Do you have a copy of that file in **~/.PlayOnLinux/wineprefix/recettear/drive_c/windows/system32**? Note, the recettear directory may be named differently. 

If so, try changing it from built-in to native.

If not, locate a copy on your drive:
```
locate d3dxof.dll
```
and copy it there (I have a copy in /usr/lib/wine/fakedlls)

---

### Post by frogotronic on 2012-01-28
Hello,

  I am also using POL (latest version 4.0.14) and have installed Half-Life 2.  Everything installed and runs well, but no sound at all (including the Valve logo).

I've using the POL console to install **d3dx9 directmusic dsound**.

When I try the POL>Half-Life 2>Wine>Config>Audio Test, it fails.

Only the ALSA driver is installed/listed in the Wine>Config>Audio tab.

You mentioned I should run the game in DEBUG mode.  Where is the log going to be written to?  I'll post that and maybe we can solve this issue.

Thanks,
CH

---

### Post by Toz on 2012-01-28
> **cement_head said:**
> You mentioned I should run the game in DEBUG mode.  Where is the log going to be written to?

With the game highlighted in the main POL window, click on "Configure". On the "General" tab, there is an option called "Enable debugging". Make sure its selected (enabled).

Then, when you start the game, another terminal window will open that will contain debugging information. It appears that the log file is written to:

/home/<user>/.PlayOnLinux//tmp/errors<game>.log.e

---

### Post by frogotronic on 2012-01-28
> **Toz said:**
> With the game highlighted in the main POL window, click on "Configure". On the "General" tab, there is an option called "Enable debugging". Make sure its selected (enabled).

Then, when you start the game, another terminal window will open that will contain debugging information. It appears that the log file is written to:

/home/<user>/.PlayOnLinux//tmp/errors<game>.log.e

No terminal spawned and no errors log file was written.

---

### Post by frogotronic on 2012-01-29
Partial success.

I enabled mmdevapi, and now the sound test works, and the valve logo has sound.

But the game itself has no sound and under the Audio tabs in the game, no speakers are selected.  Selecting speakers does not restore sound.

- CH

---

### Post by frogotronic on 2012-01-29
Ok, I figured out how to run DEBUG mode. Here's (what I think) is the relative part:

```
[POL_Wine] Message: Running wine-1.3.25 Steam.exe -applaunch 220
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
err:wineboot:ProcessRunKeys Error running cmd L"C:\\windows\\system32\\winemenubuilder.exe -a -r" (2)
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 8 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 8 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:wbemprox:wbem_locator_ConnectServer 0x1ef7a0, L"ROOT\\CIMV2", (null), (null), (null), 0x00000080, (null), (nil), 0x4aec658)
err:ole:CoGetClassObject class {dff32fea-3331-48da-a272-ccfc238695be} not registered
err:ole:CoGetClassObject class {dff32fea-3331-48da-a272-ccfc238695be} not registered
err:ole:create_server class {dff32fea-3331-48da-a272-ccfc238695be} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {dff32fea-3331-48da-a272-ccfc238695be} could be created for context 0x17
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:win:RegisterDeviceNotificationA (hwnd=0x100ba, filter=0x32d5d0,flags=0x00000004) returns a fake device notification handle!
fixme:win:EnumDisplayDevicesW ((null),0,0x32c488,0x00000000), stub!
fixme:advapi:RegisterTraceGuidsW (0x3452630, 0x3eeb7b8, {3dada31d-19ef-4dc1-b345-037927193422}, 1, 0x3ebd5f8, (null), (null), 0x3eeb7d0,): stub
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd 0x10136
fixme:win:EnumDisplayDevicesW ((null),0,0x33e1f0,0x00000000), stub!
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:d3d:debug_d3dformat Unrecognized 0x434f5441 (as fourcc: ATOC) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x434f5441) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x41415353 (as fourcc: SSAA) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x41415353) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x434f5441 (as fourcc: ATOC) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x434f5441) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x41415353 (as fourcc: SSAA) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x41415353) in the format lookup table
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x14f478, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x33e114)
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 8 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 8 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
err:ntdll:RtlpWaitForCriticalSection section 0x7d7bac "?" wait timed out in thread 0024, blocked by 0025, retrying (60 sec)
err:iccvid:decode_cinepak CVID: unknown chunk_id 00003001
```

Now...How do I fix this?

- CH

---

### Post by ergo-proxy on 2012-01-30
How about testing in it wine instead of pol?

---

### Post by frogotronic on 2012-01-30
> **ergo-proxy said:**
> How about testing in it wine instead of pol?


Shouldn't that be the same...Isn't POL is just a GUI front end for WINE?

---

### Post by Toz on 2012-01-30
Yes and no, but mostly yes. POL also runs multiple versions of wine (depending on which version of wine best runs the application/game) and also makes some configuration changes that are known to work. Have a look at the script for an idea of what is being done: [http://www.playonlinux.com/repository/?script=474]("http://www.playonlinux.com/repository/?script=474")

You'll see that its using wine version 1.3.25, the hl2 prefix, and later on down the script, the installation and configuration of mmdevapi.

However, I'm not sure why sound isn't working for you. I would guess that the valve logo is simply a video file that is running, whereas the game itself uses separate audio and video streams.

Can you try this? Install pavucontrol from the repositories. Run the game. Start up pavucontrol (also known as Pulseaudio Volume Control) and look on the Playback tab. Is should list something like "ALSA plug-in[wine-preloader]". You might have an option to change the sound source there. Perhaps its sending the signal to the wrong sound source?

---

### Post by ergo-proxy on 2012-01-31
Sometimes it helps to change values in Audio tab (winecfg) from default to exact matching your hardaware or just check to emulate sound.

---

### Post by frogotronic on 2012-02-04
Hello,

Ok...I un-installed everything (via Synaptic) and deleted (trashed) my ~/.playonlinux folder from my home directory.

Reinstalled everything, and no sound.

So, I went into the config options of POL for HL2 and **enabled** both 

```
gameoverlayrenderer
mmdevapi
```

Both with "native, builtin"

Now, HL2 works perfectly and I have sound.  Awesome, thanks!

- CH

---

