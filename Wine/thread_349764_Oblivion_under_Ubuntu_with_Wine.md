---
title: "Oblivion under Ubuntu with Wine"
date: 2007-01-30
forum: Wine
---

### Post by Mongoose on 2007-01-30
**The new Offical home of this HOWTO:**
[http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux)
The most up-to-date version will be there.   If you have a problem check the wiki before posting an issue in the fourms here.

[SIZE="5"]Oblivion under Ubuntu with Wine.[/SIZE]

Here's my first HOWTO on the Ubuntu Forums.  If I cock something up post a fix or comment, since I'm mostly going by memory here.  I saw some requests for this, and I thought this would be a great way to support Ubuntu.  =)

As of this writing WINE 0.9.29 provides the best play experience.  The GIT and 0.9.30 release now have improved D3D caps support, however this causes rendering errors for skinned meshes.  Mostly in the form of bad shadow maps and improper skinning.  This isn't a guide about developing wined3d, so let's get the last working version.  

1. Where do you get Wine?
Normally you could use the winehq.org site's guide to setup for Ubuntu, however 0.9.29 is now in the archives at wine.budgetdedicated.com.


```
	[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

	[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

```

2. Pick the package for the version of Ubuntu
You just need to download and install the package you need based on your distro, which will be either Edgy or Dapper. If you're on x86_64 you can just use the same i386 package by using the --force-architecture flag.  You'll need to install lib32 support of course if you're on x86_64, and don't forget asound32 for your ALSA sound!

```
	# x86_64 users should install the needed ia32-libs and force
	apt-get install -u ia32-libs lib32asound2 lib32z1 lib32stdc++6 linux32 
	dpkg -iE --force-architecture wine_0.9.29~winehq0~ubuntu~6.10-1_i386.deb

	# i386 users just install as normal
	dpkg -iE wine_0.9.29~winehq0~ubuntu~6.10-1_i386.deb

```


3. Wine setup is critical to getting this off the ground.  First make sure your .wine is 'modern and complete'.  This won't hose your old settings, but it will fix problems if you have setup from an older version of wine.  

```
	wineprefixcreate
```


4. Setup Wine for running Oblivion.
You may also need to copy d3dx9_27.dll to your ~/.wine/c_drive/Windows/System32 if needed.  This dll is mainly for some symbol resolution issues.  You can copy it from a Windows install or use cabextract and get it from the Oblivion DVD's DirectX.

```
	# This could be /media/cdrom or whatever your DVD mount point is called.
	apt-get install cabextract
	cabextract /media/cdrom/DXREDIST/Aug2005_d3dx9_27_x86.cab


```
Now on to the main event WINE configuration.

```
		winecfg
```

Once you load up winecfg you can do most of your tweaking in this nice GUI.

Graphics tab.

```
	[x] Emulate a virtual desktop 
	Desktop size: [1024]  x  [768]

	Vertex Shader Support [Hardware]
	[x] Allow Pixel Shader 
```

You can disable the virtual desktop, however if you have a misbehaving game it'll screw up your display resolution just like in Windows when it falls back.  How's that for compatibility?  =)


Audio tab.

```
[x] ALSA Driver

	Hardware Acceleration [Emulation]
	Default Sample Rate [44100]       Default Bits Per Sample [16]
	[x] Driver Emulation

```

Desktop Integration tab.

Here you should make a folder as your 'Windows folder base' and populate it.  I use ~/Documents/Windows/.  After you make these folders match them up in this interface, since Oblivion follows the logo requirements and uses a 'My Games' folder.

```
mkdir -p ~/Documents/Windows/{Desktop,Documents,Pictures,Music,Video}
```

Your ini and saved games will be under:

```
~/Documents/Windows/Documents/My Games/Oblivion/
```

I copied my old save games and such to the 'Saves' folder under Oblivion, and they all worked fine.


Drives tab.

Add a new drive for example 'D:' and click Show Advanced to set it as a CDROM drive.  Browse to the mount point for your Oblivion DVD or loopback image.  In my example it's '/opt/games/Windows/CDROM/'.


If you have the space I'd suggest copying your Oblivion DVD to a disk image, so you can keep it in your Collector's box. You all bought the Collector's Edition didn't you?  Well you should it has some cool stuff.  Here's a handy, dandy bash script to mount your Oblivion.iso.

```
#!/bin/sh
ISO=/opt/iso/Oblivion.iso
sudo mount -o loop -t iso9660 $ISO /opt/games/Windows/CDROM/

```


5. Registry editing in Wine.  Run the command below and it'll pop-up a Wine version of regedit.

```
wine regedit.exe

```

Now browse HKEY_CURRENT_USER / Software / Wine / Direct3D.  Right click in the pane to make New > String Value for each of the following key pairs:

```
OffscreenRenderingMode	fbo
	UseGLSL					enabled
	VideoMemorySize		256


```
Make sure you have 256MB of video memory and GLSL support before enabling.  Set whatever is needed for your card, but note w/o GLSL Oblivion won't run.  I use a Nvidia 6800 GS with 256MB of RAM, and it gets it done.


6. Installing in Wine.  There is nothing to this one, you just click and go.  The only thing that might bite you is if you see the error 'out of disk space', and you know you have enough space.  If you see this you might want to map another drive in Wine to the partition you're installing on.  For example I use G: for my /opt partition.  After this Wine will see the correct disk space for /opt on the G: drive.


```
	# Use /media/cdrom or whatever your mount point is here.
	cd /media/cdrom
	wine setup.exe
```


7. Install the patch.  Go grab the 1.1.5xx patch for Oblivion, and install it under Wine.  If you installed Oblivion under Wine then this is just watching the bar scroll to complete.


```
	# Check for your version's latest patch.  I use 'English'.
	[http://www.elderscrolls.com/](http://www.elderscrolls.com/)
	wine Oblivion_v1.1FinalEnglish.exe
```


8. First run.  I suggest copying the Oblivion icon on your desktop to your Windows/Desktop.  Go ahead and run the icon or OblivionLaucher.exe directly once.  Set the general options you want, and exit.  You'll want to reduce your game resolution and lower defaults as needed.  In general I find the types of shaders are the real slow down more than the draw distance, etc.  Turn off HDR/Bloom or you won't see anything.  =)


9. Tweaking Oblivion.ini.  There are a lot of sites that do an entire article on just this, however I'd suggest at least these two changes:


```
	bForce1XShaders=0
	bSaveOnInteriorExteriorSwitch=0
	SIntroSequence=
	bUseWaterShader=0
```


The 1X shaders cause crashes for menus and outdoors, so you don't want them.  The other option avoids saving everytime you open a door, and that means less file I/O.  Hell, you shouldn't be using these in Windows either.  If you don't care about looks so much you can enable gobal light model, which is much faster and looks much worst as well.  Clearing out the intro sequence resolves a crash for some.  Disabling the water shader means no pretty water, but it can be worth up to 50fps or more.  If you get 2fps anywhere in the game try disabling this shader, and you'll likely get a huge speed boost.  You can remove the purple color from the water by replacing its DDS texture.  I'd suggest editing the texture below to be a highly transparent light grey, or whatever you perfer. 

If you get 'purple water' once you turn off the water shader you can fix that by using Excors' replacement DDS texture:
```

# Just extract the contents ( 'Data\Textures\water\water00.dds' ) into your Oblivion/Data directory.
[http://games.build-a.com/oblivion/watertexture.zip](http://games.build-a.com/oblivion/watertexture.zip)

```

10. Playing!   Now you can finally play the game.  I suggest disabling all the debug spew to get more performance.  Also here is the shell script I use.


```
	#!/bin/sh
	# This script disables all the text output for Wine
	# debugging for improved performace.
	export WINEDEBUG=fixme-all,err-all,warn-all,trace-all
	OBLIVION_DIR=/opt/games/Windows/Oblivion
	cd ${OBLIVION_DIR}
	wine OblivionLauncher.exe


```
The new Offical home of this HOWTO:
[http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux)

You should also visit the Wine AppDB page:
[http://appdb.winehq.org/appview.php?iVersionId=5777](http://appdb.winehq.org/appview.php?iVersionId=5777)

Here's a screenshot of Oblivion in Wine at my blog for the old version of this HOWTO:
[http://mongooseichiban.blogspot.com/2007/01/oblivion-under-wine.html](http://mongooseichiban.blogspot.com/2007/01/oblivion-under-wine.html)

Here's a screenshot of Oblivion in Wine for the current version of this HOWTO:
[http://www.flickr.com/photos/terryhendrix/377865984/](http://www.flickr.com/photos/terryhendrix/377865984/)

---

### Post by glabouni on 2007-01-30
wine has now been upgraded to wine-0.9.30

anyways thanks for this howto, I'm gonna try it when I feel like finishing my oblivion game.

---

### Post by Mongoose on 2007-01-30
Don't use 0.9.30 -- I just said it won't work very well.  Please read more carefully.  =)

---

### Post by hikaricore on 2007-01-30
Beautiful howto, i'll be trying this out later. ^_^

---

### Post by bastiegast on 2007-02-01
> **hikaricore said:**
> Beautiful howto, i'll be trying this out later. ^_^

Sweet! Last Time I checked oblivion was nearly unplayable. Those guys from wine make great progress. Can't wait for 0.9.31:guitar:

---

### Post by bastiegast on 2007-02-01
Ok tried it myself, but ran into an crash upon launching the game. I googled it up and it seemed I had to remove *.bik from Data/Video then it worked.

---

### Post by Mongoose on 2007-02-01
In Oblivion.ini you can clear out this entry instead of moving files around, which is hacky:

SIntroSequence=

This way you can see the logo and map on the main game menu, and skip the company and production movies which likely cause your crash.

---

### Post by Xenophoribic on 2007-02-01
Curious what kind of settings you get, how it all looks in general, how the audio is, etc. I've just rebuilt and I'm packing a 7950GT. I want to know that I'll get good performance along with a gratifying visual and audio experience.

---

### Post by Mongoose on 2007-02-01
First, a warning about my current config.  I have about everything that works in Wine 'maxed out' when I play.  I have a large shadowmap memory setting, large textures, and I even enabled more options than the default.  I leave shadows and all that jazz enabled as well.  I like how the refraction shader looks, so I leave that on as well.  That's including turning on all the SM2.0 options including the SM2.0 lighting path.  I use a 6800 GS btw, and I turn on a few extra threads for various options since I have an AMD64x2.  

I get 30-60fps 'indoors' and anywhere from 2-70fps 'outside' with the same 'maxed out config'.   I can run around in caves with a torch throwing fireballs and fighting 2-3 people at once with 30-60fps, and that's typical usage for my gameplay.   It's really uneven 'outside' due to the fact that at night you can get 70fps in the same area that gets 2fps in the sunlight.  The way to get around this issue and not disable any shaders in the ini is to use 'Oblivion batch files' to toggle them on and off as needed.  I can't remember, but I think 0.9.30 doesn't have this huge slowdown problem.  Given 0.9.30 breaks mesh skinning you don't want to bother with it, since broken mesh animation/rendering ruins the game more than a slow down you can avoid.

I think the slow down might be caused by only 1 or 2 shaders using a slow code path in Wine.  The worst I've seen is where you have an ungodly amount dynamic lights across a rampart, but that's always going to be slow even if you were in Windows.   I would try toggling the various shaders on and off to see what works best for your card.

You can also use Ultra Ugly gobal lighting path, which seems to enable a vertex color light model.  If you really wanted to max out performance you could find the trouble shaders and rewrite them.   I think you can get over 200fps pretty easy then, but why would you want to at that point?     =)

I'm revising this HOWTO at my site, and plan to roll the 'fixes' back into this fourm post once I have time to take some screenshots.

[http://www.icculus.org/~mongoose/OblivionHOWTO.html](http://www.icculus.org/~mongoose/OblivionHOWTO.html)

Here's a link to an article on using batch files and console commands:
[http://www.tweakguides.com/Oblivion_11.html](http://www.tweakguides.com/Oblivion_11.html)

---

### Post by Xenophoribic on 2007-02-01
Thanks a lot, Mongoose. I was going to install a Windows partition just so I could play Oblivion trouble free, but your guide looks solid, and your explanation on your performance only solidifies my complete abstinence from Windows :)

---

### Post by nalmeth on 2007-02-01
This is crazy!

I had completely written off Oblivion without Cedega.

Thanks so much dude, can you write me a guide for getting a capable video card for dirt cheap? I'd buy you a six-pack :)

---

### Post by Mongoose on 2007-02-02
I've gone back and tested for the slow down briefly, and it appears you can crank down everything you can think of graphically and still be hit by it at times.  I also tried turning off AI and a few minor tests like that.  I hope it's not some stupid error condition slowing everything down, but it could be.   I got it to happen at night for the first time even with grass off too.  This doesn't explain the reason for the huge range in the same area from day to night or sunny to rainy.  I guess this means if you get 2fps use the console to make it rain, and you should be good to go.  The place I got 2fps at night I had it rain and I got 30+fps.  I hope it's not something stupid like the skydome -- since I didn't test turning that off and started playing for a bit.   =)

If you figure it out before I have time to play/test again post here.

UPDATE:

It was the water!   I couldn't even see water anywhere, but wireframe showed it was rendering.  I disabled the 'water system' in the console and jumped to 50fps.   If you find any more 2fps slow downs this doesn't fix post, so we can figure them together.  ;)

In the console type:  tws

UPDATE 2:

I dropped this HOWTO on the UESP wiki with details on how to fix 'purple water' and disable the water shader completely, so you don't have to toggle it off everytime you switch areas.

[http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux)

---

### Post by Xenophoribic on 2007-02-02
One last question, hoping it's a no. Are you using Oldblivion and assuming we would be and left it out for that reason, or are you using default Oblivion?

---

### Post by Mongoose on 2007-02-02
If you read the HOWTO it has no steps for Oldblivion at all.  You just need to turn off the shaders I've mentioned to get good performance.   I was turning off projected shadows for speedtree, but after disabling the water shader I found I can enable that and double my draw distance and still have a nice 25-70fps in combat outdoors with the particle systems on.   The 6800 GS isn't a monster card, but you really need to have that or above imho to play smooth even with the setup I've tried to peice together.

My goal with this is to make it possible to follow a guide and run Oblivion.  There is no guess work, and I'm giving you all the steps I use myself.  I may provide an ini at some point for people using the same hardware I have.   The only thing remotely special I do is enable more threads for the game, and frankly that doesn't help FPS very much.  I do crank my gamma up via the ini a little too, but that's just b/c Oblivion is so dark with HDR off.  I assume you know to turn off HDR, since Wine can't support it correctly right now.   =)

I thought I'd also mention since disabling the watershader I play with Beryl on AIGLX and run in 800x600.  The main thing bothering me is sometimes I get static sound fx hissing in the background, but I've been told that doesn't happen for most people.   If you run into an issue or a fix post here, so we can figure out workarounds.  I will warn you on Beryl + Oblivion in that it makes my GPU run hotter than if I disable Beryl.

---

### Post by Xenophoribic on 2007-02-04
I've followed your guide to the T, and I feel I'm having problems, as well as a friend of mine. He has a 7900GS, I have a 7950GT, and yet we're getting low FPS (20 on average). Along with that, there's static throughout the audio, except when talking directly to an NPC. I edited my Oblivion.ini and managed to raise my FPS slightly, but I think I'm missing something.

---

### Post by Mongoose on 2007-02-05
Did you turn off the water shader?  That was the biggest bang for the buck I found.  Also I've been tinkering with the GIT (0.9.30+) builds lately, and it's only a few shader fixes away from being able to play with all light passes now.   The only time I get down to 20FPS is when I have everything turned on except for water shader, which is brokem.  You might want to turn off grass / refraction shader / shadows / music / window envmaps as well.   I also play with full draw distance personally.   I always turn off music, since I assume directshow is broken.  I've had others tell me there audio is fine, so I didn't mention that in the HOWTO.

If you're using 0.9.29 and have edited your ini you should be doing fine.  Did you use a more recent version I updated here or at the wiki?  Also use tdt and make sure it's really low fps and not just audio sample loading or AI slowing you down.  You'd be surprised.  Also make sure you have the environment variable set every time you play, or you'll be wasting a lot of cycles just printing trace/fixme/warnings.  If you're still having problems load up 0.9.30 and in the console use 'slp 1010'.  That command basically turns off diffuse and specular lighting, so the meshes won't be jacked up, but it turns off a majority of lighting as well.  You can toggle it back on and off as needed while you play with 'slp 1111'.  That won't look very nice, but it'll run very fast and fixes most of the audio mixing issues for sound effects.   This is the reason I suggested using 0.9.29.  Tell me if this helps any.   I only have one set of hardware to test my ini settings on here.   If all this fails disable SM30 in your ini, since your card may provide more EXT than mine causing issues on a codepath I never hit.   =)

Edit:
I updated the shell script in this forum to disable all debug spew -- just like the HOWTO on the wiki.  Also you can turn down you sound effects slider to 25%.  You'll still hear combat and ambient effects fine, but the 'snow' will be low enough you can ignore it.  It might help to play with sample rate as well, but I still assume it's mostly the software mixing to blame.

---

### Post by bastiegast on 2007-02-05
> **Xenophoribic said:**
> I've followed your guide to the T, and I feel I'm having problems, as well as a friend of mine. He has a 7900GS, I have a 7950GT, and yet we're getting low FPS (20 on average). Along with that, there's static throughout the audio, except when talking directly to an NPC. I edited my Oblivion.ini and managed to raise my FPS slightly, but I think I'm missing something.

Almost exactly my problems, inside I do get reasonable fps, but outside it dropped to 2 or something, well this is mainly fixed by turning of the water shader as you said. But still the audio is only good when directly talking to somebody. Lately I figured out that the noise/static whatever it is called can be shut off by turning the effects volume down, however this makes the game less fun. I have yet to try your suggestions about th slp command.
I noticed in your screenshot you've hit tab (inventory screen) and you can still see the background around your character. If I hit either tab or esc I can see the menu or inventory screen but the background is gray/green, any idea what is causing this?
By the way, how can you check your fps? Is there a command to turn some display on?

If I not already said so, I love you howto, I might be starting to play oblivion in Linux because of this.

---

### Post by Mongoose on 2007-02-05
You're using a bad ini then, or you copied the old ini off the wine application db.  The background in the menu is on by default.  The old ini on wine appdb was made before the forced SM1.0 option was widely reported to be the cause of the menu crashing.  The reason I post all this info is because I had to figure it out myself mostly, and I don't think most people have the time or patience to do the same.   

If your card has less memory or some other handicap you should start disabling features.  Also you might want to run in 1024x768 or 800x600 resolutions.  I would suggest starting with a default ini the game makes, which is what I presented in the HOWTO.

<pre>
; Default menu background
bStaticMenuBackground=0

; Some basic threading options for dual core users, search for all options like:
;bUseThreaded*
;eg 
bUseThreadedBlood=1

; You can also wnable/increase havoc, speedtree, and openmp threads 
iNumHavokThreads=2

bUseMultiThreadedFaceGen=1

bUseMultiThreadedTrees=1


; Try these for performance
bEquippedTorchesCastShadows=0

bReportBadTangentSpace=0
iMultiSample=0

bDoTallGrassEffect=0

bForceMultiPass=0

bDrawShadows=0
bUseRefractionShader=0
iShadowFilter=0
bShadowsOnGrass=0

bDoStaticAndArchShadows=0

bDoActorShadows=0

; If you have a SM3.0 supported card use it
bAllow30Shaders=1


; Bump up brightness, lower brighter
fGamma=0.8900
</pre>

---

### Post by Xenophoribic on 2007-02-05
I've gotten my FPS fairly consistent, 30-50 in general, occasional dip into 20's. The audio problem is still there, and for some reason, NPC's are black. Details are just barely recognizable, it's as if a heavy shadow is over the textures.

---

### Post by Mongoose on 2007-02-05
Black? Either you have HDR on or you're turning off light passes.  I suggest 0.9.29, but if you must play in 0.9.30 you'll either have to give up diffuse lighting ( ouch ) or look at improperly animated meshes.   

You can turn HDR off in the game UI.

You can test if it's just shadows by using this ini setting:
```
bDrawShadows=0
```

To test light passes type this command in the console:
```
slp 1111
```

---

### Post by Megatog615 on 2007-02-07
I followed all the steps exactly, and the game screen is blank(like a darkish blue), but I can see the GUI.

wine --version
```
wine-0.9.29
```

Also, the sound is just static when I play the game. The menus are also very messed up.

---

### Post by Mongoose on 2007-02-07
Turn off HDR.  99% of the time people say this they have HDR on.  You can turn it off from the Launcher.

---

### Post by Megatog615 on 2007-02-10
Most of the sound is static, still.

---

### Post by Mongoose on 2007-02-10
That's caused by ambient sounds and sometimes music.  I turn sound effects down to 25% and turn everything else up to 100%.   I can hear sound effects fine, but the static is unnoticable -- however I think it has as much to do with your soundcard and speakers as to how much static you hear.   Also newer Wine builds the sound mixing appears to produce less static for Oblivion.   I assume it's caused by not clearing the extra space in the buffers, since they don't align by assumed block size.  I can hear hit/spell/etc sounds fine this way but not the static.  Sorry, it's the only work around besides patching Wine.

---

### Post by bastiegast on 2007-02-12
I tried playing it with wine 0.9.30. WOW! all shaders work, even bloom works too bad about the messed up models, will this be fixed in wine 0.9.31? It would be great :popcorn: can't wait!

---

### Post by kroenecker on 2007-02-12
I've read over the thread and don't see any advice for the following:

When I run Oblivion it works, but the screen freezes just before the King is attacked for the first time.  That is, going down the stairs and through the first door.

Does anyone else have this experience?  I installed v29 but that doesn't seem to help.  Maybe my video card is problematic: 6600 with 128 memory.

Ah well, it does run in windows and I do still have windows installed :P

---

### Post by Mongoose on 2007-02-12
Actually, Oblivion has a min requirement of 256MB iirc.  You should set your wine settings to 128MB instead of 256MB if you haven't already.   You'll be getting a lot of texture thrashing I'd imagine however...  but that's better than crashing.   You also need to dail down all your settings to smallest texture size.

Edit: I forgot to mention -- you should half your shadow map and related settings as well.  I don't think they're affected by the quality sliders.

---

### Post by Mblackwell on 2007-02-12
> **bastiegast said:**
> I tried playing it with wine 0.9.30. WOW! all shaders work, even bloom works too bad about the messed up models, will this be fixed in wine 0.9.31? It would be great :popcorn: can't wait!

Yeah I had the same thing. I hadn't had GLSL on because it doesn't work with Guild Wars (is slow and causes draw errors), but turning it on made everything in Oblivion work except the meshes were screwed up (as someone said before they would be). And it even ran smoothly. Awesome! Here's hoping. Just fix that and the sound and it's good to go!

---

### Post by Mongoose on 2007-02-13
I just updated the Oblivion:Linux wiki -- GIT wine fixes the mesh issue in 0.9.30!  Thanks to the guys at WineHQ for keeping me in the loop.   =)

---

### Post by zgerrz on 2007-02-16
At this point I have a problem since I do not see a folder called Direct3D. It just isn't there for me. I'm running the 0.9.30 version of wine.

> Now browse HKEY_CURRENT_USER / Software / Wine / Direct3D. Right click in the pane to make New > String Value for each of the following key pairs:

Any suggestions?

EDIT: I made the keys, but the parent folder which should be called "Direct3D" is currently called "New Key #1", and whenever I click on rename to change it, nothing happens.

EDIT: Apparently there is a bug in the 0.9.30 version of wine in renaming keys. It is fixed in 0.9.31 though. Just thought I would let people know about this.

---

### Post by zgerrz on 2007-02-17
Does anyone know why my game is very stuttery? NPCs will speak to me, but if I move around at the same time the audio will stutter and they will often have to repeat the same words again.

I also have some texture issues. During the main screen the options like "new" and "load" all have white spaces around them, and activating menu options does not happen "smoothly." Meaning I often have to click hard and be very precise to activate menu buttons.

Also, I get an incredible amount of static audio, but I hear that this problem doesn't really have a fix yet. I have to turn down the effects sounds to 0 to keep my sanity.

Sorry for some of the vague descriptions; it's just hard to explain some of these issues. The game just feels very "clunky."

By the way, thanks for the guide. I didn't even think it was possible to get this game running at all under wine. You have done a great service for the Oblivion community.

P.S. I'm running wine 0.9.31

---

### Post by Mongoose on 2007-02-17
If you're getting audio stutter it means your taxing your machine mostly.  You might want to adjust your threading or something.  On a related note you can get way over 30fps and still have bad play if you machine hits a heavy load.   =)

The problem with pixel shaders right now is if you enable the pbuffer option for offscreen targets it runs faster and fixes some graphical errors -- but causes a crash when you save due to how the screen is captured.  That's a real bitch for an RPG, but it does save a valid file before the crash at least.   =)

Try out my slider adjustment tip for the static in effects mixing.   I don't hear any static with my current build of Wine and my workaround, but there is still a bug in directsound mixing.   Also read the wiki page for the most up to date issues.

---

### Post by Mblackwell on 2007-02-17
Oi vey, I discovered that no matter what I did the character models were rendered wrong. My then thought was "well maybe it's my ini" (which is imported from when I used Windows), and so I renamed it. The default ini crashed before it even got to the "loading" screen. I remembered that disabling the intro movies solved a crash for some people, so I got rid of them. At that point I can at least get to "loading" but it crashes with a page fault before I can get to the menu.

I've checked everything and I have no idea why one ini crashes and the other doesn't. Either way I can't really play the game.

---

### Post by Mongoose on 2007-02-17
You should just follow the guide... it handles the intro issue and more -- also it provides work arounds.   This is a reason it was written -- also if you read you'd know 0.9.30 is broken. Read the wiki page linked from the #1 section of this thread.   =)

---

### Post by Mblackwell on 2007-02-17
I'm using 0.9.31. I followed the guide. I DO update my packages. :p

Edit: Here's something useful, here's each INI.

This one crashes:

```

[General]

SStartingCell=



SStartingCellY=

SStartingCellX=

SStartingWorld=



STestFile10=

STestFile9=

STestFile8=

bSTestFile7=

STestFile6=

STestFile5=

STestFile4=

STestFile3=

STestFile2=

STestFile1=



bEnableProfile=0

bDrawSpellContact=0

bRunMiddleLowLevelProcess=1

iHoursToSleep=3

bActorLookWithHavok=0

SMainMenuMusicTrack=special\tes4title.mp3

bUseEyeEnvMapping=1

bFixFaceNormals=0

bUseFaceGenHeads=1

bFaceMipMaps=1

bFaceGenTexturing=1

bDefaultCOCPlacement=0

uGridDistantTreeRange=15

uGridDistantCount=25

uGridsToLoad=5

fGlobalTimeMultiplier=1.0000

bNewAnimation=1

fAnimationDefaultBlend=0.1000

fAnimationMult=1.0000

bFixAIPackagesOnLoad=0

bForceReloadOnEssentialCharacterDeath=1

bKeepPluginWhenMerging=0

bCreate Maps Enable=0

SLocalSavePath=Saves\

SLocalMasterPath=Data\

bDisableDuplicateReferenceCheck=1

bTintMipMaps=0

uInterior Cell Buffer=3

uExterior Cell Buffer=36

iIntroSequencePriority=3

bPreloadIntroSequence=1

fStaticScreenWaitTime=3.0000

SCreditsMenuMovie=CreditsMenu.bik

SMainMenuMovie=Map loop.bik

SMainMenuMovieIntro=

SIntroSequence=

iFPSClamp=0

bRunVTuneTest=0

STestFile1=

bActivateAllQuestScripts=0

fQuestScriptDelayTime=5.0000

SMainMenuMusic=Special\TES4Title.mp3

bUseThreadedBlood=0

bUseThreadedMorpher=0

bExternalLODDataFiles=1






[Display]

uVideoDeviceIdentifierPart1=0

uVideoDeviceIdentifierPart2=0

uVideoDeviceIdentifierPart3=0

uVideoDeviceIdentifierPart4=0

fDecalLifetime=10.0000

bEquippedTorchesCastShadows=0

bReportBadTangentSpace=0

bStaticMenuBackground=1

bForcePow2Textures=0

bForce1XShaders=0

bHighQuality20Lighting=0

bAllow20HairShader=1

bAllowScreenShot=0

iMultiSample=0

bDoTallGrassEffect=1

bForceMultiPass=1

bDoTexturePass=1

bDoSpecularPass=1

bDoDiffusePass=1

bDoAmbientPass=1

bDoCanopyShadowPass=1

bDrawShadows=0

bUseRefractionShader=1

bUse Shaders=1

iNPatchNOrder=0

iNPatchPOrder=0

iNPatches=0

iLocation Y=0

iLocation X=0

bFull Screen=0

iSize W=800

iSize H=600

iAdapter=0

iScreenShotIndex=0

SScreenShotBaseName=ScreenShot

iAutoViewMinDistance=2000

iAutoViewHiFrameRate=40

iAutoViewLowFrameRate=20

bAutoViewDistance=0

fDefaultFOV=75.0000

fNearDistance=10.0000

fFarDistance=10000.0000

iDebugTextLeftRightOffset=10

iDebugTextTopBottomOffset=10

bShowMenuTextureUse=1

iDebugText=2

bLocalMapShader=1

bDoImageSpaceEffects=1

fShadowLOD2=400.0000

fShadowLOD1=200.0000

fLightLOD2=1500.0000

fLightLOD1=1000.0000

fSpecularLOD2=800.0000

fSpecularLOD1=500.0000

fEnvMapLOD2=800.0000

fEnvMapLOD1=500.0000

fEyeEnvMapLOD2=190.0000

fEyeEnvMapLOD1=130.0000

iPresentInterval=1







[Controls]

fVersion=1.7000

Forward=0011FFFF

Back=001FFFFF

Slide Left=001EFFFF

Slide Right=0020FFFF

Use=00FF00FF

Activate=0039FFFF

Block=003801FF

Cast=002EFFFF

Ready Item=0021FFFF

Crouch/Sneak=001DFFFF

Run=002AFFFF

Always Run=003AFFFF

Auto Move=0010FFFF

Jump=0012FFFF

Toggle POV=001302FF

Menu Mode=000FFFFF

Rest=0014FFFF

Quick Menu=003BFFFF

Quick1=0002FFFF

Quick2=0003FFFF

Quick3=0004FFFF

Quick4=0005FFFF

Quick5=0006FFFF

Quick6=0007FFFF

Quick7=0008FFFF

Quick8=0009FFFF

QuickSave=003FFFFF

QuickLoad=0043FFFF

Grab=002CFFFF

bInvertYValues=0

fXenonLookXYMult=0.0005

fMouseSensitivity=0.0020

;X = 1, Y = 2, Z = 3, XRot = 4, YRot = 5, ZRot = 6

iJoystickMoveFrontBack=2

iJoystickMoveLeftRight=1

fJoystickMoveFBMult=1.0000

fJoystickMoveLRMult=1.0000

iJoystickLookUpDown=6

iJoystickLookLeftRight=3

fJoystickLookUDMult=0.0020

fJoystickLookLRMult=0.0020

fXenonMenuMouseXYMult=0.0003

bBackground Mouse=0

bBackground Keyboard=0

bUse Joystick=1

fXenonLookMult=0.0030

fXenonMenuStickSpeedMaxMod=5.0000

iXenonMenuStickSpeedThreshold=20000

iXenonMenuStickThreshold=1000

;Language values: 0-English, 1-German, 2-French, 3-Spanish, 4-Italian

iLanguage=0





[Water]

fAlpha=0.5000

uSurfaceTextureSize=128

SSurfaceTexture=water

SNearWaterOutdoorID=NearWaterOutdoorLoop

SNearWaterIndoorID=NearWaterIndoorLoop

fNearWaterOutdoorTolerance=1024.0000

fNearWaterIndoorTolerance=512.0000

fNearWaterUnderwaterVolume=0.9000

fNearWaterUnderwaterFreq=0.3000

uNearWaterPoints=8

uNearWaterRadius=1000

uSurfaceFrameCount=32

uSurfaceFPS=12

bUseWaterReflectionsMisc=0

bUseWaterReflectionsStatics=0

bUseWaterReflectionsTrees=0

bUseWaterReflectionsActors=0

bUseWaterReflections=1

bUseWaterHiRes=0

bUseWaterDisplacements=1

bUseWaterShader=1

uDepthRange=125

bUseWaterDepth=1

bUseWaterLOD=1

fTileTextureDivisor=4.7500

fSurfaceTileSize=2048.0000



[Audio]

bDSoundHWAcceleration=1

fMinSoundVel=10.0000

fMetalLargeMassMin=25.0000

fMetalMediumMassMin=8.0000

fStoneLargeMassMin=30.0000

fStoneMediumMassMin=5.0000

fWoodLargeMassMin=15.0000

fWoodMediumMassMin=7.0000

fDialogAttenuationMax=35.0000

fDialogAttenuationMin=7.7500

bUseSoundDebugInfo=1

fUnderwaterFrequencyDelta=0.0000

bUseSoftwareAudio3D=0

fDefaultEffectsVolume=0.8000

fDefaultMusicVolume=0.3000

fDefaultFootVolume=0.8000

fDefaultVoiceVolume=0.8000

fDefaultMasterVolume=1.0000

bMusicEnabled=1

bSoundEnabled=1

fLargeWeaponWeightMin=25.0000

fMediumWeaponWeightMin=8.0000

fSkinLargeMassMin=30.0000

fSkinMediumMassMin=5.0000

fChainLargeMassMin=30.0000

fChainMediumMassMin=5.0000

fDBVoiceAttenuationIn2D=0.0000

iCollisionSoundTimeDelta=50

fGlassLargeMassMin=25.0000

fGlassMediumMassMin=8.0000

fClothLargeMassMin=25.0000

fClothMediumMassMin=8.0000

fEarthLargeMassMin=30.0000

fEarthMediumMassMin=5.0000

bUseSpeedForWeaponSwish=1

fLargeWeaponSpeedMax=0.9500

fMediumWeaponSpeedMax=1.1000

fPlayerFootVolume=0.9000

fDSoundRolloffFactor=4.0000

fMaxFootstepDistance=1100.0000

fHeadroomdB=2.0000

iMaxImpactSoundCount=32

fMainMenuMusicVolume=0.6





[ShockBolt]

bDebug=0

fGlowColorB=1.0000

fGlowColorG=0.6000

fGlowColorR=0.0000

fCoreColorB=1.0000

fCoreColorG=1.0000

fCoreColorR=1.0000

fCastVOffset=-10.0000

iNumBolts=7

fBoltGrowWidth=1.0000

fBoltSmallWidth=3.0000

fTortuosityVariance=8.0000

fSegmentVariance=35.0000

fBoltsRadius=24.0000



[Pathfinding]

bDrawPathsDefault=0

bPathMovementOnly=0

bDrawSmoothFailures=0

bDebugSmoothing=0

bSmoothPaths=1

bSnapToAngle=0

bDebugAvoidance=0

bDisableAvoidance=0

bBackgroundPathing=0



[MAIN]

bEnableBorderRegion=1





[Combat]

bEnableBowZoom=1

bDebugCombatAvoidance=0

fMinBloodDamage=1.0000

fHitVectorDelay=0.4000

iShowHitVector=0





[HAVOK]

bDisablePlayerCollision=0

fJumpAnimDelay=0.75

bTreeTops=0

iSimType=1

bPreventHavokAddAll=0

bPreventHavokAddClutter=0

fMaxTime=0.0167

bHavokDebug=0

fRF=1000.0000

fOD=0.9000

fSE=0.3000

fSD=0.9800

iResetCounter=5

fMoveLimitMass=95.0000

iUpdateType=0

bHavokPick=0





[Interface]

fDlgLookMult=0.3000

fDlgLookAdj=0.0000

fDlgLookDegStop=0.2000

fDlgLookDegStart=2.0000

fDlgFocus=2.1000

fKeyRepeatInterval=50.0000

fKeyRepeatTime=500.0000

fActivatePickSphereRadius=16.0000

fMenuModeAnimBlend=0.0000

iSafeZoneX=20

iSafeZoneY=20

iSafeZoneXWide=20

iSafeZoneYWide=20



[LoadingBar]



[Menu]

fCreditsScrollSpeed=40.0000

iConsoleTextYPos=890

iConsoleTextXPos=30

iConsoleVisibleLines=15

iConsoleHistorySize=50

rDebugTextColor=255,251,233

iConsoleFont=3

iDebugTextFont=3







[GamePlay]

bDisableDynamicCrosshair=0

bSaveOnTravel=1

bSaveOnWait=1

bSaveOnRest=1

bCrossHair=1

iDifficultyLevel=50

bGeneralSubtitles=0

bDialogueSubtitles=1

bInstantLevelUp=0

bHealthBarShowing=0

fHealthBarFadeOutSpeed=1.0000

fHealthBarSpeed=80.0000

fHealthBarHeight=4.0000

fHealthBarWidth=40.0000

fHealthBarEmittanceFadeTime=0.5000

fHealthBarEmittanceTime=1.5000





[Fonts]

SFontFile_1=Data\Fonts\Kingthings_Regular.fnt

SFontFile_2=Data\Fonts\Kingthings_Shadowed.fnt

SFontFile_3=Data\Fonts\Tahoma_Bold_Small.fnt

SFontFile_4=Data\Fonts\Daedric_Font.fnt

SFontFile_5=Data\Fonts\Handwritten.fnt





[SpeedTree]

iTreeClonesAllowed=1

fCanopyShadowGrassMult=1.0000

iCanopyShadowScale=512

fTreeForceMaxBudAngle=-1.0000

fTreeForceMinBudAngle=-1.0000

fTreeForceLeafDimming=-1.0000

fTreeForceBranchDimming=-1.0000

fTreeForceCS=-1.0000

fTreeForceLLA=-1.0000

fTreeLODExponent=1.0000

bEnableTrees=1

bForceFullLOD=0





[Debug]

bDebugFaceGenCriticalSection=0

bDebugFaceGenMultithreading=0

bDebugSaveBuffer=0





[BackgroundLoad]





[LOD]

fLodDistance=500.0000

bUseFaceGenLOD=0

iLODTextureTiling=2

iLODTextureSizePow2=8

fLODNormalTextureBlend=0.5000

bDisplayLODLand=1

bDisplayLODBuildings=1

bDisplayLODTrees=0

bLODPopTrees=0

bLODPopActors=0

bLODPopItems=0

bLODPopObjects=0

fLODFadeOutMultActors=5.0000

fLODFadeOutMultItems=2.0000

fLODFadeOutMultObjects=5.0000

fLODMultLandscape=1.0000

fLODMultTrees=1.2000

fLODMultActors=1.0000

fLODMultItems=1.0000

fLODMultObjects=1.0000

iFadeNodeMinNearDistance=400

fLODFadeOutPercent=0.9000

fLODBoundRadiusMult=3.0000

fTalkingDistance=2000.0000



fTreeLODMax=2.0000

fTreeLODMin=0.0200

fTreeLODDefault=1.2000



[Weather]

fSunGlareSize=350.0000

fSunBaseSize=250.0000

bPrecipitation=1

fAlphaReduce=1.0000

SBumpFadeColor=255,255,255,255

SLerpCloseColor=255,255,255,255

SEnvReduceColor=255,255,255,255



[Voice]

SFileTypeLTF=ltf

SFileTypeLip=lip

SFileTypeSource=wav

SFileTypeGame=mp3





[Grass]

iMinGrassSize=80

fGrassEndDistance=3000.0000

fGrassStartFadeDistance=2000.0000

bGrassPointLighting=0

bDrawShaderGrass=1

iGrassDensityEvalSize=2

iMaxGrassTypesPerTexure=2

fWaveOffsetRange=1.7500



[Landscape]

bCurrentCellOnly=0

bPreventSafetyCheck=0

fLandTextureTilingMult=2.0000





[bLightAttenuation]

fQuadraticRadiusMult=1.0000

fLinearRadiusMult=1.0000

bOutQuadInLin=0

fConstantValue=0.0000

fQuadraticValue=16.0000

fLinearValue=3.0000

uQuadraticMethod=2

uLinearMethod=1

fFlickerMovement=8.0000

bUseQuadratic=1

bUseLinear=0

bUseConstant=0





[BlurShaderHDRInterior]

fTargetLUM=1.0000

fUpperLUMClamp=1.0000

fEmissiveHDRMult=1.0000

fEyeAdaptSpeed=0.5000

fBrightScale=2.2500

fBrightClamp=0.2250

fBlurRadius=7.0000

iNumBlurpasses=1





[BlurShaderHDR]

fTargetLUM=1.2000

fUpperLUMClamp=1.0000

fGrassDimmer=1.3000

fTreeDimmer=1.2000

fEmissiveHDRMult=1.0000

fEyeAdaptSpeed=0.7000

fSunlightDimmer=1.3000

fSIEmmisiveMult=1.0000

fSISpecularMult=1.0000

fSkyBrightness=0.5000

fSunBrightness=0.0000

fBrightScale=1.5000

fBrightClamp=0.350

fBlurRadius=4.0000

iNumBlurpasses=2

iBlendType=2

bDoHighDynamicRange=0





[BlurShader]

fSunlightDimmer=1.0000

fSIEmmisiveMult=1.0000

fSISpecularMult=1.0000

fSkyBrightness=0.5000

fSunBrightness=0.0000

fAlphaAddExterior=0.2000

fAlphaAddInterior=0.5000

iBlurTexSize=256

fBlurRadius=0.0300

iNumBlurpasses=1

iBlendType=2





[GethitShader]

fBlurAmmount=0.5000

fBlockedTexOffset=0.0010

fHitTexOffset=0.0050

[MESSAGES]

bBlockMessageBoxes=0

bSkipProgramFlows=1

bAllowYesToAll=1

bDisableWarning=1

iFileLogging=0

[DistantLOD]

bUseLODLandData=0

fFadeDistance=12288.0000

[GeneralWarnings]

SGeneralMasterMismatchWarning=One or more plugins could not find the correct versions of the master files they depend on. Errors may occur during load or game play. Check the "Warnings.txt" file for more information.



SMasterMismatchWarning=One of the files that "%s" is dependent on has changed since the last save.

This may result in errors. Saving again will clear this message

but not necessarily fix any errors.



[Archive]

SMasterMiscArchiveFileName=Oblivion - Misc.bsa

SMasterVoicesArchiveFileName2=Oblivion - Voices2.bsa

SMasterVoicesArchiveFileName1=Oblivion - Voices1.bsa

SMasterSoundsArchiveFileName=Oblivion - Sounds.bsa

SMasterTexturesArchiveFileName1=Oblivion - Textures - Compressed.bsa

SMasterMeshesArchiveFileName=Oblivion - Meshes.bsa

SInvalidationFile=ArchiveInvalidation.txt

iRetainFilenameOffsetTable=1

iRetainFilenameStringTable=1

iRetainDirectoryStringTable=1

bCheckRuntimeCollisions=0

bInvalidateOlderFiles=1

bUseArchives=1

[CameraPath]

iTake=0

SDirectoryName=TestCameraPath

iFPS=60

SNif=Test\CameraPath.nif

[Absorb]

fAbsorbGlowColorB=1.0000

fAbsorbGlowColorG=0.6000

fAbsorbGlowColorR=0.0000

fAbsorbCoreColorB=1.0000

fAbsorbCoreColorG=1.0000

fAbsorbCoreColorR=1.0000

iAbsorbNumBolts=1

fAbsorbBoltGrowWidth=0.0000

fAbsorbBoltSmallWidth=7.0000

fAbsorbTortuosityVariance=2.0000

fAbsorbSegmentVariance=7.0000

fAbsorbBoltsRadius=5.0000

[OPENMP]

iThreads=3

iOpenMPLevel=10

[TestAllCells]

bFileShowTextures=1

bFileShowIcons=1

bFileSkipIconChecks=0

bFileTestLoad=0

bFileNeededMessage=1

bFileGoneMessage=1

bFileSkipModelChecks=0

[CopyProtectionStrings]

SCopyProtectionMessage2=Insert the Oblivion Disc.

SCopyProtectionTitle2=Oblivion Disc Not Found

SCopyProtectionMessage=Unable to find a CD-ROM/DVD drive on this computer.

SCopyProtectionTitle=CD-ROM Drive Not Found


```

And here's the one that doesn't:

```



[General]

SStartingCell=

SStartingCellY=

SStartingCellX=

SStartingWorld=

STestFile10=

STestFile9=

STestFile8=

STestFile7=

STestFile6=

STestFile5=

STestFile4=

STestFile3=

STestFile2=

STestFile1=

bEnableProfile=0

bDrawSpellContact=0

bRunMiddleLowLevelProcess=1

iHoursToSleep=3

bActorLookWithHavok=0

SMainMenuMusicTrack=special\tes4title.mp3

bUseEyeEnvMapping=1

bFixFaceNormals=0

bUseFaceGenHeads=1

bFaceMipMaps=1

bFaceGenTexturing=1

bDefaultCOCPlacement=0

uGridDistantTreeRange=15

uGridDistantCount=25

uGridsToLoad=5

fGlobalTimeMultiplier=1.0000

bNewAnimation=1

fAnimationDefaultBlend=0.1000

fAnimationMult=1.0000

bFixAIPackagesOnLoad=0

bForceReloadOnEssentialCharacterDeath=1

bKeepPluginWhenMerging=0

bCreate Maps Enable=0

SLocalSavePath=Saves\

SLocalMasterPath=Data\

bDisableDuplicateReferenceCheck=1

bTintMipMaps=0

uInterior Cell Buffer=6

uExterior Cell Buffer=72

iIntroSequencePriority=3

bPreloadIntroSequence=1

fStaticScreenWaitTime=3.0000

SCreditsMenuMovie=CreditsMenu.bik

SMainMenuMovie=Map loop.bik

SMainMenuMovieIntro=

SIntroSequence=

iFPSClamp=0

bRunVTuneTest=0

STestFile1=

bActivateAllQuestScripts=0

fQuestScriptDelayTime=5.0000

SMainMenuMusic=Special\TES4Title.mp3

bUseThreadedBlood=0

bUseThreadedMorpher=0

bExternalLODDataFiles=1

bBorderRegionsEnabled=1

bDisableHeadTracking=0

bTrackAllDeaths=0

SCharGenQuest=0002466E

uiFaceGenMaxEGTDataSize=67108864

uiFaceGenMaxEGMDataSize=67108864

SBetaCommentFileName=

bCheckCellOffsetsOnInit=0

bCreateShaderPackage=0

uGridDistantTreeRangeCity=4

uGridDistantCountCity=4

bWarnOnMissingFileEntry=0

iSaveGameBackupCount=1

bDisplayMissingContentDialogue=1

SSaveGameSafeCellID=2AEEA

bAllowScriptedAutosave=1

bPreemptivelyUnloadCells=0

iNumBitsForFullySeen=248

iPreloadSizeLimit=52428800

SOblivionIntro=OblivionIntro.bik

bUseHardDriveCache=1

bEnableBoundingVolumeOcclusion=0

bDisplayBoundingVolumes=0

bUseThreadedTempEffects=1

bUseThreadedParticleSystem=1

bUseMyGamesDirectory=1



[Display]

uVideoDeviceIdentifierPart1=0

uVideoDeviceIdentifierPart2=0

uVideoDeviceIdentifierPart3=0

uVideoDeviceIdentifierPart4=0

fDecalLifetime=10.0000

bEquippedTorchesCastShadows=0

bReportBadTangentSpace=0

bStaticMenuBackground=1

bForcePow2Textures=0

bForce1XShaders=0

bHighQuality20Lighting=1

bAllow20HairShader=1

bAllowScreenShot=1

iMultiSample=0

bDoTallGrassEffect=0

bForceMultiPass=1

bDoTexturePass=1

bDoSpecularPass=1

bDoDiffusePass=1

bDoAmbientPass=1

bDoCanopyShadowPass=0

bDrawShadows=0

bUseRefractionShader=1

bUse Shaders=1

iNPatchNOrder=0

iNPatchPOrder=0

iNPatches=0

iLocation Y=220

iLocation X=360

bFull Screen=0

iSize W=1024

iSize H=768

iAdapter=0

iScreenShotIndex=69

SScreenShotBaseName=ScreenShot

iAutoViewMinDistance=2000

iAutoViewHiFrameRate=40

iAutoViewLowFrameRate=20

bAutoViewDistance=0

fDefaultFOV=75.0000

fNearDistance=10.0000

fFarDistance=10000.0000

iDebugTextLeftRightOffset=10

iDebugTextTopBottomOffset=10

bShowMenuTextureUse=1

iDebugText=2

bLocalMapShader=1

bDoImageSpaceEffects=1

fShadowLOD2=300.0000

fShadowLOD1=150.0000

fLightLOD2=1000.0000

fLightLOD1=500.0000

fSpecularLOD2=800.0000

fSpecularLOD1=500.0000

fEnvMapLOD2=500.0000

fEnvMapLOD1=300.0000

fEyeEnvMapLOD2=150.0000

fEyeEnvMapLOD1=100.0000

iPresentInterval=0

fSpecualrStartMax=750.0000

fSpecularStartMin=0.0000

iActorShadowIntMax=10

iActorShadowIntMin=0

iActorShadowExtMax=10

iActorShadowExtMin=0

fGammaMax=0.6000

fGammaMin=1.4000

iMaxDecalsPerFrame=5

bDynamicWindowReflections=0

fShadowFadeTime=1.0000

fGamma=0.7280

bDecalsOnSkinnedGeometry=0

iShadowFilter=0

bAllowPartialPrecision=1

iShadowMapResolution=512

bShadowsOnGrass=0

bActorSelfShadowing=0

iActorShadowCountInt=2

iActorShadowCountExt=1

bAllow30Shaders=1

iTexMipMapMinimum=0

iTexMipMapSkip=1

bDoStaticAndArchShadows=0

bDoActorShadows=0

bIgnoreResolutionCheck=0

fNoLODFarDistancePct=1.0000

fNoLODFarDistanceMax=10000.0000

fNoLODFarDistanceMin=1500.0000

bFullBrightLighting=0

iMaxLandscapeTextures=0



[Controls]

fVersion=1.8000

Forward=0048FFFF

Back=004CFFFF

Slide Left=004BFFFF

Slide Right=004DFFFF

Use=00FF00FF

Activate=0051FFFF

Block=002C01FF

Cast=0049FFFF

Ready Item=0047FFFF

Crouch/Sneak=0053FFFF

Run=002A02FF

Always Run=0028FFFF

Auto Move=0010FFFF

Jump=0052FFFF

Toggle POV=0013FFFF

Menu Mode=000FFFFF

Rest=0014FFFF

Quick Menu=003BFFFF

Quick1=0002FFFF

Quick2=0003FFFF

Quick3=0004FFFF

Quick4=0005FFFF

Quick5=0006FFFF

Quick6=0007FFFF

Quick7=0008FFFF

Quick8=0009FFFF

QuickSave=003FFFFF

QuickLoad=0043FFFF

Grab=00B5FFFF

bInvertYValues=1

fXenonLookXYMult=0.0005

fMouseSensitivity=0.0020

;X=1, Y = 2, Z = 3, XRot = 4, YRot = 5, ZRot = 6

iJoystickMoveFrontBack=2

iJoystickMoveLeftRight=1

fJoystickMoveFBMult=1.0000

fJoystickMoveLRMult=1.0000

iJoystickLookUpDown=6

iJoystickLookLeftRight=3

fJoystickLookUDMult=0.0020

fJoystickLookLRMult=0.0020

fXenonMenuMouseXYMult=0.0003

bBackground Mouse=0

bBackground Keyboard=0

bUse Joystick=0

fXenonLookMult=0.0030

fXenonMenuStickSpeedMaxMod=5.0000

iXenonMenuStickSpeedThreshold=20000

iXenonMenuStickThreshold=1000

;Language values: 0-English, 1-German, 2-French, 3-Spanish, 4-Italian

iLanguage=0

Attack=00FF0009

Ready Weapon=0047FF02

Sneak=004EFF00

Change View=0013FF05

Journal=000FFF04

Wait=0014FF0A

fXenonMenuStickMapCursorMinSpeed=1.0000

fXenonMenuStickMapCursorMaxSpeed=15.0000

fXenonMenuStickMapCursorGamma=0.1700

fXenonMenuStickSpeedPlayerRotMod=3000.0000

fXenonMenuDpadRepeatSpeed=300.0000

fXenonMenuStickSpeed=300.0000

iXenonMenuStickDeadZone=15000

SlideLeft=004BFFFF

SlideRight=004DFFFF



[Water]

fAlpha=0.5000

uSurfaceTextureSize=128

SSurfaceTexture=water

SNearWaterOutdoorID=NearWaterOutdoorLoop

SNearWaterIndoorID=NearWaterIndoorLoop

fNearWaterOutdoorTolerance=1024.0000

fNearWaterIndoorTolerance=512.0000

fNearWaterUnderwaterVolume=0.9000

fNearWaterUnderwaterFreq=0.3000

uNearWaterPoints=8

uNearWaterRadius=1000

uSurfaceFrameCount=1

uSurfaceFPS=12

bUseWaterReflectionsMisc=0

bUseWaterReflectionsStatics=0

bUseWaterReflectionsTrees=0

bUseWaterReflectionsActors=0

bUseWaterReflections=0

bUseWaterHiRes=0

bUseWaterDisplacements=0

bUseWaterShader=1

uDepthRange=125

bUseWaterDepth=1

bUseWaterLOD=1

fTileTextureDivisor=4.7500

fSurfaceTileSize=2048.0000

uNumDepthGrids=3

bUseObliqueFrustumCulling=1



[Audio]

bDSoundHWAcceleration=1

fMinSoundVel=10.0000

fMetalLargeMassMin=25.0000

fMetalMediumMassMin=8.0000

fStoneLargeMassMin=30.0000

fStoneMediumMassMin=5.0000

fWoodLargeMassMin=15.0000

fWoodMediumMassMin=7.0000

fDialogAttenuationMax=35.0000

fDialogAttenuationMin=7.7500

bUseSoundDebugInfo=1

fUnderwaterFrequencyDelta=0.0000

bUseSoftwareAudio3D=0

fDefaultEffectsVolume=0.0100

fDefaultMusicVolume=0.3800

fDefaultFootVolume=0.7500

fDefaultVoiceVolume=1.0000

fDefaultMasterVolume=1.0000

bMusicEnabled=0

bSoundEnabled=1

fLargeWeaponWeightMin=25.0000

fMediumWeaponWeightMin=8.0000

fSkinLargeMassMin=30.0000

fSkinMediumMassMin=5.0000

fChainLargeMassMin=30.0000

fChainMediumMassMin=5.0000

fDBVoiceAttenuationIn2D=0.0000

iCollisionSoundTimeDelta=50

fGlassLargeMassMin=25.0000

fGlassMediumMassMin=8.0000

fClothLargeMassMin=25.0000

fClothMediumMassMin=8.0000

fEarthLargeMassMin=30.0000

fEarthMediumMassMin=5.0000

bUseSpeedForWeaponSwish=1

fLargeWeaponSpeedMax=0.9500

fMediumWeaponSpeedMax=1.1000

fPlayerFootVolume=0.9000

fDSoundRolloffFactor=4.0000

fMaxFootstepDistance=1100.0000

fHeadroomdB=2.0000

iMaxImpactSoundCount=32

fMainMenuMusicVolume=0.6000



[ShockBolt]

bDebug=0

fGlowColorB=1.0000

fGlowColorG=0.6000

fGlowColorR=0.0000

fCoreColorB=1.0000

fCoreColorG=1.0000

fCoreColorR=1.0000

fCastVOffset=-10.0000

iNumBolts=7

fBoltGrowWidth=1.0000

fBoltSmallWidth=3.0000

fTortuosityVariance=8.0000

fSegmentVariance=35.0000

fBoltsRadius=24.0000



[Pathfinding]

bDrawPathsDefault=0

bPathMovementOnly=0

bDrawSmoothFailures=0

bDebugSmoothing=0

bSmoothPaths=1

bSnapToAngle=0

bDebugAvoidance=0

bDisableAvoidance=0

bBackgroundPathing=1

bUseBackgroundPathing=1



[MAIN]

bEnableBorderRegion=1

fLowPerfCombatantVoiceDistance=1000.0000

iDetectionHighNumPicks=40

fQuestScriptDelayTime=5.0000

iLastHDRSetting=-1



[Combat]

bEnableBowZoom=1

bDebugCombatAvoidance=0

fMinBloodDamage=1.0000

fHitVectorDelay=0.4000

iShowHitVector=0

fLowPerfNPCTargetLOSTimer=1.0000

fHiPerfNPCTargetLOSTimer=0.5000

iMaxHiPerfNPCTargetCount=4

fLowPerfPCTargetLOSTimer=0.5000

fHiPerfPCTargetLOSTimer=0.2500

iMaxHiPerfPCTargetCount=4

iMaxHiPerfCombatCount=4



[HAVOK]

bDisablePlayerCollision=0

fJumpAnimDelay=0.7500

bTreeTops=0

iSimType=1

bPreventHavokAddAll=0

bPreventHavokAddClutter=0

fMaxTime=0.0167

bHavokDebug=0

fRF=1000.0000

fOD=0.9000

fSE=0.3000

fSD=0.9800

iResetCounter=5

fMoveLimitMass=95.0000

iUpdateType=0

bHavokPick=0

fCameraCasterSize=1.0000

iHavokSkipFrameCountTEST=0

fHorseRunGravity=3.0000

fQuadrupedPitchMult=1.0000

iNumHavokThreads=1

fChaseDeltaMult=0.0500

iEntityBatchRemoveRate=100

iMaxPicks=40

bAddBipedWhenKeyframed=0



[Interface]

fDlgLookMult=0.3000

fDlgLookAdj=0.0000

fDlgLookDegStop=0.2000

fDlgLookDegStart=2.0000

fDlgFocus=2.1000

fKeyRepeatInterval=50.0000

fKeyRepeatTime=500.0000

fActivatePickSphereRadius=16.0000

fMenuModeAnimBlend=0.0000

iSafeZoneX=20

iSafeZoneY=20

iSafeZoneXWide=20

iSafeZoneYWide=20

fMenuPlayerLightDiffuseBlue=0.8000

fMenuPlayerLightDiffuseGreen=0.8000

fMenuPlayerLightDiffuseRed=0.8000

fMenuPlayerLightAmbientBlue=0.2500

fMenuPlayerLightAmbientGreen=0.2500

fMenuPlayerLightAmbientRed=0.2500

bAllowConsole=1

bActivatePickUseGamebryoPick=0

iMaxViewCasterPicksGamebryo=10

iMaxViewCasterPicksHavok=10

iMaxViewCasterPicksFuzzy=5

bUseFuzzyPicking=1

fMenuBGBlurRadius=2.0000



[LoadingBar]

iMoveBarWaitingMilliseconds=10

iMoveBarChaseMilliseconds=100

iMoveBarMaxMilliseconds=2500

fLoadingSlideDelay=15.0000

fPercentageOfBar3=0.1500

fPercentageOfBar2=0.4400

fPercentageOfBar1=0.3500

fPercentageOfBar0=0.0600

bShowSectionTimes=0



[Menu]

fCreditsScrollSpeed=40.0000

iConsoleTextYPos=890

iConsoleTextXPos=30

iConsoleVisibleLines=15

iConsoleHistorySize=50

rDebugTextColor=255,251,233

iConsoleFont=3

iDebugTextFont=3



[GamePlay]

bDisableDynamicCrosshair=0

bSaveOnTravel=1

bSaveOnWait=1

bSaveOnRest=1

bCrossHair=1

iDifficultyLevel=50

bGeneralSubtitles=1

bDialogueSubtitles=1

bInstantLevelUp=0

bHealthBarShowing=0

fHealthBarFadeOutSpeed=1.0000

fHealthBarSpeed=80.0000

fHealthBarHeight=4.0000

fHealthBarWidth=40.0000

fHealthBarEmittanceFadeTime=0.5000

fHealthBarEmittanceTime=1.5000

STrackLevelUpPath=

fDifficulty=-0.4400

bTrackLevelUps=1

bAllowHavokGrabTheLiving=0

bEssentialTakeNoDamage=1

iDetectionPicks=21

bSaveOnInteriorExteriorSwitch=1



[Fonts]

SFontFile_1=Data\Fonts\Kingthings_Regular.fnt

SFontFile_2=Data\Fonts\Kingthings_Shadowed.fnt

SFontFile_3=Data\Fonts\Tahoma_Bold_Small.fnt

SFontFile_4=Data\Fonts\Daedric_Font.fnt

SFontFile_5=Data\Fonts\Handwritten.fnt



[SpeedTree]

iTreeClonesAllowed=16

fCanopyShadowGrassMult=1.0000

iCanopyShadowScale=512

fTreeForceMaxBudAngle=-1.0000

fTreeForceMinBudAngle=-1.0000

fTreeForceLeafDimming=-1.0000

fTreeForceBranchDimming=-1.0000

fTreeForceCS=-1.0000

fTreeForceLLA=-1.0000

fTreeLODExponent=1.0000

bEnableTrees=1

bForceFullLOD=1

fLODTreeMipMapLODBias=-0.2500

fLocalTreeMipMapLODBias=-0.7500



[Debug]

bDebugFaceGenCriticalSection=0

bDebugFaceGenMultithreading=0

bDebugSaveBuffer=0



[BackgroundLoad]

bBackgroundLoadLipFiles=1

bLoadBackgroundFaceGen=1

bUseMultiThreadedFaceGen=1

bBackgroundCellLoads=1

bLoadHelmetsInBackground=1

iAnimationClonePerLoop=5

bSelectivePurgeUnusedOnFastTravel=1

bUseMultiThreadedTrees=1

iExteriorPriority=50

bCloneModelsInBackground=0

iBackgroundLoadFaceMult=200

fBackgroundLoadingPerLoop=20.0000

fBackgroundLoadClonedPerLoop=5.0000

iBackgroundLoadExtraMaxFPS=20

iBackgroundLoadExtraMinFPS=10

iBackgroundLoadExtraMax=3000

iBackgroundLoadExtraMin=5

iBackgroundLoadExtraMilliseconds=2

iBackgroundLoadTreeMilliseconds=7

iBackgroundLoadMilliseconds=1

iBackgroundLoadLoading=1

bUseBackgroundFileLoader=0



[LOD]

fLodDistance=500.0000

bUseFaceGenLOD=0

iLODTextureTiling=2

iLODTextureSizePow2=8

fLODNormalTextureBlend=0.5000

bDisplayLODLand=1

bDisplayLODBuildings=1

bDisplayLODTrees=0

bLODPopTrees=0

bLODPopActors=0

bLODPopItems=0

bLODPopObjects=0

fLODFadeOutMultActors=10.7100

fLODFadeOutMultItems=9.4000

fLODFadeOutMultObjects=9.4000

fLODMultLandscape=1.0000

fLODMultTrees=0.5000

fLODMultActors=5.0000

fLODMultItems=5.0000

fLODMultObjects=5.0000

iFadeNodeMinNearDistance=400

fLODFadeOutPercent=0.9000

fLODBoundRadiusMult=3.0000

fTalkingDistance=2000.0000

fTreeLODMax=2.0000

fTreeLODMin=0.0200

fTreeLODDefault=1.2000

fObjectLODMax=15.0000

fObjectLODMin=1.0000

fObjectLODDefault=5.0000

fItemLODMax=15.0000

fItemLODMin=1.0000

fItemLODDefault=2.0000

fActorLODMax=15.0000

fActorLODMin=2.0000

fActorLODDefault=5.0000

bLODUseCombinedLandNormalMaps=1

bForceHideLODLand=0

fLODQuadMinLoadDistance=65536.0000

fLODFadeOutActorMultInterior=1.0000

fLODFadeOutItemMultInterior=1.0000

fLODFadeOutObjectMultInterior=1.0000

fLODFadeOutActorMultCity=1.0000

fLODFadeOutItemMultCity=1.0000

fLODFadeOutObjectMultCity=1.0000

fLODFadeOutActorMultComplex=1.0000

fLODFadeOutItemMultComplex=1.0000

fLODFadeOutObjectMultComplex=1.0000

fLODLandVerticalBias=-1000.0000



[Weather]

fSunGlareSize=350.0000

fSunBaseSize=250.0000

bPrecipitation=1

fAlphaReduce=1.0000

SBumpFadeColor=255,255,255,255

SLerpCloseColor=255,255,255,255

SEnvReduceColor=255,255,255,255



[Voice]

SFileTypeLTF=ltf

SFileTypeLip=lip

SFileTypeSource=wav

SFileTypeGame=mp3



[Grass]

iMinGrassSize=120

fGrassEndDistance=2848.0000

fGrassStartFadeDistance=1848.0000

bGrassPointLighting=0

bDrawShaderGrass=1

iGrassDensityEvalSize=2

iMaxGrassTypesPerTexure=2

fWaveOffsetRange=1.7500

fGrassWindMagnitudeMax=125.0000

fGrassWindMagnitudeMin=5.0000

fTexturePctThreshold=0.3000



[Landscape]

bCurrentCellOnly=0

bPreventSafetyCheck=0

fLandTextureTilingMult=2.0000

fLandFriction=2.5000

iLandBorder2B=0

iLandBorder2G=0

iLandBorder2R=0

iLandBorder1B=0

iLandBorder1G=255

iLandBorder1R=255



[bLightAttenuation]

fQuadraticRadiusMult=1.0000

fLinearRadiusMult=1.0000

bOutQuadInLin=0

fConstantValue=0.0000

fQuadraticValue=16.0000

fLinearValue=3.0000

uQuadraticMethod=2

uLinearMethod=1

fFlickerMovement=8.0000

bUseQuadratic=1

bUseLinear=0

bUseConstant=0



[BlurShaderHDRInterior]

fTargetLUM=1.0000

fUpperLUMClamp=1.0000

fEmissiveHDRMult=1.0000

fEyeAdaptSpeed=0.5000

fBrightScale=2.2500

fBrightClamp=0.2250

fBlurRadius=7.0000

iNumBlurpasses=1



[BlurShaderHDR]

fTargetLUM=1.2000

fUpperLUMClamp=1.0000

fGrassDimmer=1.3000

fTreeDimmer=1.2000

fEmissiveHDRMult=1.0000

fEyeAdaptSpeed=0.7000

fSunlightDimmer=1.3000

fSIEmmisiveMult=1.0000

fSISpecularMult=1.0000

fSkyBrightness=0.5000

fSunBrightness=0.0000

fBrightScale=1.5000

fBrightClamp=0.3500

fBlurRadius=4.0000

iNumBlurpasses=2

iBlendType=2

bDoHighDynamicRange=0



[BlurShader]

fSunlightDimmer=1.0000

fSIEmmisiveMult=1.0000

fSISpecularMult=1.0000

fSkyBrightness=0.5000

fSunBrightness=0.0000

fAlphaAddExterior=0.2000

fAlphaAddInterior=0.5000

iBlurTexSize=256

fBlurRadius=0.0300

iNumBlurpasses=1

iBlendType=2

bUseBlurShader=0



[GethitShader]

fBlurAmmount=0.5000

fBlockedTexOffset=0.0010

fHitTexOffset=0.0050



[MESSAGES]

bBlockMessageBoxes=0

bSkipProgramFlows=1

bAllowYesToAll=1

bDisableWarning=1

iFileLogging=0

bSkipInitializationFlows=1



[DistantLOD]

bUseLODLandData=0

fFadeDistance=12288.0000

iDistantLODGroupWidth=8



[GeneralWarnings]

SGeneralMasterMismatchWarning=One or more plugins could not find the correct versions of the master files they depend on. Errors may occur during load or game play. Check the "Warnings.txt" file for more information.

SMasterMismatchWarning=One of the files that "%s" is dependent on has changed since the last save.

This may result in errors. Saving again will clear this message

but not necessarily fix any errors.



[Archive]

SMasterMiscArchiveFileName=Oblivion - Misc.bsa

SMasterVoicesArchiveFileName2=Oblivion - Voices2.bsa

SMasterVoicesArchiveFileName1=Oblivion - Voices1.bsa

SMasterSoundsArchiveFileName=Oblivion - Sounds.bsa

SMasterTexturesArchiveFileName1=Oblivion - Textures - Compressed.bsa

SMasterMeshesArchiveFileName=Oblivion - Meshes.bsa

SInvalidationFile=ArchiveInvalidation.txt

iRetainFilenameOffsetTable=1

iRetainFilenameStringTable=1

iRetainDirectoryStringTable=1

bCheckRuntimeCollisions=0

bInvalidateOlderFiles=1

bUseArchives=1

SArchiveList=Oblivion - Meshes.bsa, Oblivion - Textures - Compressed.bsa, Oblivion - Sounds.bsa, Oblivion - Voices1.bsa, Oblivion - Voices2.bsa, Oblivion - Misc.bsa



[CameraPath]

iTake=0

SDirectoryName=TestCameraPath

iFPS=60

SNif=Test\CameraPath.nif



[Absorb]

fAbsorbGlowColorB=1.0000

fAbsorbGlowColorG=0.6000

fAbsorbGlowColorR=0.0000

fAbsorbCoreColorB=1.0000

fAbsorbCoreColorG=1.0000

fAbsorbCoreColorR=1.0000

iAbsorbNumBolts=1

fAbsorbBoltGrowWidth=0.0000

fAbsorbBoltSmallWidth=7.0000

fAbsorbTortuosityVariance=2.0000

fAbsorbSegmentVariance=7.0000

fAbsorbBoltsRadius=5.0000



[OPENMP]

iThreads=10

iOpenMPLevel=10



[TestAllCells]

bFileShowTextures=1

bFileShowIcons=1

bFileSkipIconChecks=0

bFileTestLoad=0

bFileNeededMessage=1

bFileGoneMessage=1

bFileSkipModelChecks=0

bFileCheckModelCollision=0



[CopyProtectionStrings]

SCopyProtectionMessage2=Insert the Oblivion Disc.

SCopyProtectionTitle2=Oblivion Disc Not Found

SCopyProtectionMessage=Unable to find a CD-ROM/DVD drive on this computer.

SCopyProtectionTitle=CD-ROM Drive Not Found



```

---

### Post by solitary on 2007-02-17
Hello,
Followed your guide, exept the iso part. Is the game copy protected, (because I don't have Alchohol 120% or CloneCD)?

One problem is that my game won't save. I get the message "Saved succesfully" but no save game is created. An autosave is generated in the Saves directory, but this seem buggy. Becuase if I select save game from menu, this entry disappear from the list, and only "New Savegame" is left, but "New Savegame" dosen't function when you click on it. (I have generated a directory structure according to the guide, and linked the folders in the desktop integration tab in winecfg.)

The other problem is that the game always crash if I enter the doorway blow the stairs behind the "secret" celldoor. So I can't get any further and this. Maybe this is related to that the game cannot save?

Do you have any clue (I have checked file permissions and they look ok)?

---

### Post by Mongoose on 2007-02-18
**Ini question:**

1. Purge your ini and copy the default in its place.
2. Make the suggested changes to the ini.
3. If it still doesn't work actually read the entire guide and follow directions.

I can tell you didn't read instructions when you post an ini that doesn't have the changes.   If it doesn't work once you make the changes it would be the first case I heard that fails to work.   Of course, you a certain specification of hardware to run the game.

**ISO question:**
You must have the disc or ISO mounted to play, which is why the mount script was provided.  I updated the wiki as a reminder it has to be mounted to play.  Going outside causes a crash if you're using the '1X' PS path, so make sure that's disabled.   As for the save games -- they work properly for me and many others with the workaround settings provided in the guide.  You should double check your wine setup, and also ensure your permissions on the folders are correct.  My guess is you can write to the existing files and perhaps not create.   That's the only way I can think of that can happen. 

Read the guide at the wiki as it's more up-to-date.

---

### Post by zgerrz on 2007-02-18
> **solitary said:**
> Hello,
Followed your guide, exept the iso part. Is the game copy protected, (because I don't have Alchohol 120% or CloneCD)?


You don't actually need the disc or iso mounted to play.. Just get a No CD crack and apply it over your default Oblivion.exe.

Bethesda did not apply a very strict copy protection scheme to this game so the No CD crack works very easily.

---

### Post by bastiegast on 2007-02-18
> **solitary said:**
> Hello,
Followed your guide, exept the iso part. Is the game copy protected, (because I don't have Alchohol 120% or CloneCD)?

One problem is that my game won't save. I get the message "Saved succesfully" but no save game is created. An autosave is generated in the Saves directory, but this seem buggy. Becuase if I select save game from menu, this entry disappear from the list, and only "New Savegame" is left, but "New Savegame" dosen't function when you click on it. (I have generated a directory structure according to the guide, and linked the folders in the desktop integration tab in winecfg.)

The other problem is that the game always crash if I enter the doorway blow the stairs behind the "secret" celldoor. So I can't get any further and this. Maybe this is related to that the game cannot save?

Do you have any clue (I have checked file permissions and they look ok)?

I had the same problems and if I remember well it was fixed by upgrading to 0.9.31. Try ```
wine --version
```
To see what version of wine you have.

---

### Post by Sastraxi on 2007-02-18
Just to correct a point made earlier, Oblivion doesn't require 256 MB of video memory. I played through the game on Windows with a Radeon 9500 Pro (128 MB) just fine.

---

### Post by solitary on 2007-02-18
Version is wine 0.9.31. Still have problem with save games, dosn't seem to be the filepermission that is the problem. Maybe I should reinstall. The autosave file that is generated when you create a new game is created but the game informs that it is corrupted.

Since bForce1XShaders is set to 0 by default, this is a rare problem? Anyway I have double checked the ini parameters, and they are ok.

---

### Post by Mongoose on 2007-02-18
Yeah, it will run in the sense that you can play with low quality settings or a lot of trashing if you refuse to turn down settings -- at least for the 6600.  I said this eariler, which is true. 

Also you could try testing   that card under Wine, but I doubt it'll work.  I looked 9500 up and that card has 128MB, PS2, 4/4 pixel/vertex, and low memory bandwidth on top of that.  Also remember you're running this on OpenGL driver, which has a D3D wrapper in Wine.  I don't think that card would run the game under Wine, and I guess you'd have to use the PS1 only path in Windows.  That path doesn't function under Wine right now.  Wine is great, but please don't make assumptions -- just a few buffer implementation changes can cause a difference in video memory usage to be large enough to matter.

If you're curious 'recommended' is 6800 (256MB-512MB, 12-16 pipeline depends on which) and up with 1GB+ of main memory on the box.   You can certainly play with 128MB video and 512MB main memory, but under Wine you'd have to do some serious tweaking.   =)

---

### Post by solitary on 2007-02-18
Did a reinstall, but still no luck with the save games.

What kind of permission do you guys have on your oblivion files. I have them chmod 755?

---

### Post by Mblackwell on 2007-02-18
> **Mongoose said:**
> **Ini question:**

1. Purge your ini and copy the default in its place.
2. Make the suggested changes to the ini.
3. If it still doesn't work actually read the entire guide and follow directions.

I can tell you didn't read instructions when you post an ini that doesn't have the changes.   If it doesn't work once you make the changes it would be the first case I heard that fails to work.   Of course, you a certain specification of hardware to run the game.

What are you talking about? The ini file certainly has the changes so it won't load the start up movies, and also doesn't force 1xshaders (which is the default, to not force them). The changed ini also has the same thing. 

The top ini IS the default, except with the start up movies deleted out to get it to bring up the loading screen PERIOD.

As far as my computer specifications, they are certainly enough to run it at 800x600 under Windows with the details cranked up. I'm not some user with a Geforce MX who wonders why no games will run, I have a 6600GT :p.

The reason I posted 2 ini files was that maybe someone other than myself would be able to figure out what the difference between the two is that makes one crash after the loading screen (on INITIAL startup, in other words not even going to the main menu), and the other actually get into the game, just with screwed up character models (runs fairly smoothly too, so it's kind of sad).

---

### Post by Sastraxi on 2007-02-18
I didn't mean for you to take that post the wrong way, Mongoose. Nor am I naive enough to even start a real 3D application under linux with an ATI card :(

---

### Post by Mblackwell on 2007-02-18
I figured out the crash, it's due to the menu music. It was the only thing between the two ini files that was majorly different, and I figured it out on a whim.

Unfortunately, character models still render incorrectly (it's kind of funny to be able to see their eyes and teeth and hair but no skin).

If someone with basically everything working could post their ini file I'd love to pour over it.

---

### Post by solitary on 2007-02-18
Mblackwell: I hade the eye and mouth problem with nvidia drivers 8776, after upgrading to 9631 it renders characters properly.

---

### Post by Mblackwell on 2007-02-18
> **solitary said:**
> Mblackwell: I hade the eye and mouth problem with nvidia drivers 8776, after upgrading to 9631 it renders characters properly.

That did it. Ran like crap though until I disabled the water shader. Now it's all happiness and roses except the sound.

---

### Post by solitary on 2007-02-18
Did you have any problems getting save games to work, I am stuck in Jail because of it i think?

---

### Post by Mblackwell on 2007-02-18
> **solitary said:**
> Did you have any problems getting save games to work, I am stuck in Jail because of it i think?

If you don't set the OffscreenRenderingMode to fbo in the registry it will crash every time the game saves (it will still save, it just crashes).

---

### Post by kroenecker on 2007-02-19
This is poop.  I bought a new card (7800 GT) and I'm still seeing the crashing when I follow the king during the opening sequence.

---

### Post by kroenecker on 2007-02-19
Just to be clear it's just before the King is attacked for the first time.

This is uber frustrating :P

Solitary,

I'm certain that I'm having the exact same problem as you.  Did you figure out what is wrong?

---

### Post by bastiegast on 2007-02-20
Movies crash the game, I removed all files from Data/Videos in the oblivion directory. However, I can't even get start oblivion if I have those movies enabled.

EDIT: I'm sorry I thought you meant opening movie, but your talking about the crash in the beginning of the game, never mind my post.

---

### Post by M_the_C on 2007-02-20
> **kroenecker said:**
> This is poop.  I bought a new card (7800 GT) and I'm still seeing the crashing when I follow the king during the opening sequence.
I know it's not the best solution but there is a mod that skips the opening sequence.

[Link]("http://www.tessource.net/files/file.php?id=8353")

---

### Post by Mongoose on 2007-02-20
You set the option in the ini to blank to disable the opening movie.  All the other movies play fine w/o crashing for everyone that's done this so far.  Please read the guide, since it's very annoying to read about people stumbling over the same issues again and again.  It's pretty clearly laid out how to do these things without deleting any files or having to install mods just to workaround a simple ini setting.

I was going to quit posting in this thread, but it's kind of outrageous when the information is already in the same thread more than once.   =/

---

### Post by dbd on 2007-02-20
Before I start I'd like to say a big thank you to Mongoose, although it doesn't work for me yet the wiki was very well written and will probably help a lot of people :)

However, I can't get it to work, I've followed the wiki page exactly and tried many things mentioned in the thread, but have had no success :(
I can install it, install the patch and set up the settings. Then when I actually click play I get the loading screen and then it freezes and I get this error message:
> wine: Unhandled page fault on read access to 0x00000300 at address 0x7de8c1ec (thread 001c), starting debugger...
Unhandled exception: page fault on read access to 0x00000300 in 32-bit code (0x7de8c1ec).

mezz@paul-ubuntu:/media/e/Oblivion_lin$ Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7de8c1ec ESP:0034f320 EBP:0034f358 EFLAGS:00010202(   - 00      - -RI1)
 EAX:00000001 EBX:7e30d3c0 ECX:7e30d3c0 EDX:00001023
 ESI:00000000 EDI:0034f348
Stack dump:
0x0034f320:  00000000 7e30d3c0 7b8ab500 b7ea53f5
0x0034f330:  7e3eeb6c 00000006 0034f358 7e3c1638
0x0034f340:  00000002 018c06f0 0034f648 7e30d3c0
0x0034f350:  00000006 00000001 0034f368 7dcfefe4
0x0034f360:  7e30d3c0 00000c11 0034f438 7de829e2
0x0034f370:  7e30d3c0 00981d68 0057fa2a 0057fa47
Backtrace:
=>1 0x7de8c1ec __glUpdateWinFBOSize+0x1c() in fglrx_dri.so (0x0034f358)
  2 0x7dcfefe4 in fglrx_dri.so (+0x2c7fe4) (0x0034f368)
  3 0x7de829e2 __glim_Enable+0xbf2() in fglrx_dri.so (0x0034f438)
  4 0x7e3b75b8 in libgl.so.1 (+0x685b8) (0x0034f448)
  5 0x7ba6292e in wined3d (+0x1292e) (0x0034f4e8)
  6 0x7bfc4a45 in d3d9 (+0x4a45) (0x0034f518)
  7 0x006c9afd in oblivion (+0x2c9afd) (0x15000564)
  8 0x00000001 (0x00a482b0)
  9 0x006d1fe0 in oblivion (+0x2d1fe0) (0x006d2930)
0x7de8c1ec __glUpdateWinFBOSize+0x1c in fglrx_dri.so: call      *0x300(%esi)
Modules:
Module  Address                 Debug info      Name (97 modules)
PE      400000-b73000   Export          oblivion
PE      b80000-dcf000   Deferred        d3dx9_27
PE      18000000-18068000       Deferred        binkw32
ELF     7b800000-7b926000       Deferred        kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7ba37000-7baef000       Export          wined3d<elf>
  \-PE  7ba50000-7baef000       \               wined3d
ELF     7bc00000-7bc94000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc94000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf34000-7bfae000       Deferred        libglu.so.1
ELF     7bfae000-7bfd8000       Export          d3d9<elf>
  \-PE  7bfc0000-7bfd8000       \               d3d9
ELF     7c3b5000-7c3ca000       Deferred        midimap<elf>
  \-PE  7c3c0000-7c3ca000       \               midimap
ELF     7c3f0000-7c408000       Deferred        msacm32<elf>
  \-PE  7c400000-7c408000       \               msacm32
ELF     7c408000-7c4c0000       Deferred        libasound.so.2
ELF     7c4c0000-7c4eb000       Deferred        winealsa<elf>
  \-PE  7c4d0000-7c4eb000       \               winealsa
ELF     7c4eb000-7c527000       Deferred        wineoss<elf>
  \-PE  7c4f0000-7c527000       \               wineoss
ELF     7c527000-7c559000       Deferred        uxtheme<elf>
  \-PE  7c530000-7c559000       \               uxtheme
ELF     7c559000-7c55e000       Deferred        libxfixes.so.3
ELF     7c55e000-7c57a000       Deferred        imm32<elf>
  \-PE  7c570000-7c57a000       \               imm32
ELF     7c57a000-7c598000       Deferred        ximcp.so.2
ELF     7cfc1000-7cfca000       Deferred        libxcursor.so.1
ELF     7d0c8000-7d0ca000       Deferred        xlcutf8load.so.2
ELF     7d0ca000-7d0cd000       Deferred        libxrandr.so.2
ELF     7d95d000-7d966000       Deferred        librt.so.1
ELF     7d967000-7d96f000       Deferred        libxrender.so.1
ELF     7d96f000-7d972000       Deferred        libxinerama.so.1
ELF     7da37000-7e34f000       Export          fglrx_dri.so
ELF     7e34f000-7e3ef000       Export          libgl.so.1
ELF     7e3ef000-7e3f4000       Deferred        libxdmcp.so.6
ELF     7e3f4000-7e4bd000       Deferred        libx11.so.6
ELF     7e4bd000-7e4ca000       Deferred        libxext.so.6
ELF     7e4ca000-7e4e2000       Deferred        libice.so.6
ELF     7e4e2000-7e4eb000       Deferred        libsm.so.6
ELF     7e4eb000-7e578000       Deferred        winex11<elf>
  \-PE  7e500000-7e578000       \               winex11
ELF     7e578000-7e596000       Deferred        libexpat.so.1
ELF     7e596000-7e5c5000       Deferred        libfontconfig.so.1
ELF     7e5c5000-7e5d9000       Deferred        libz.so.1
ELF     7e5d9000-7e643000       Deferred        libfreetype.so.6
ELF     7e643000-7e66f000       Deferred        ws2_32<elf>
  \-PE  7e650000-7e66f000       \               ws2_32
ELF     7e66f000-7e689000       Deferred        wsock32<elf>
  \-PE  7e680000-7e689000       \               wsock32
ELF     7e689000-7e6ee000       Deferred        msvcrt<elf>
  \-PE  7e6a0000-7e6ee000       \               msvcrt
ELF     7e6ee000-7e707000       Deferred        version<elf>
  \-PE  7e6f0000-7e707000       \               version
ELF     7e707000-7e75f000       Deferred        shlwapi<elf>
  \-PE  7e720000-7e75f000       \               shlwapi
ELF     7e75f000-7e853000       Deferred        shell32<elf>
  \-PE  7e770000-7e853000       \               shell32
ELF     7e853000-7e89c000       Deferred        dsound<elf>
  \-PE  7e860000-7e89c000       \               dsound
ELF     7e89c000-7e92a000       Deferred        winmm<elf>
  \-PE  7e8b0000-7e92a000       \               winmm
ELF     7e92a000-7e93d000       Deferred        libresolv.so.2
ELF     7e93d000-7e95b000       Deferred        iphlpapi<elf>
  \-PE  7e940000-7e95b000       \               iphlpapi
ELF     7e95b000-7e9b0000       Deferred        rpcrt4<elf>
  \-PE  7e970000-7e9b0000       \               rpcrt4
ELF     7e9b0000-7ea49000       Deferred        ole32<elf>
  \-PE  7e9c0000-7ea49000       \               ole32
ELF     7ea49000-7ea7f000       Deferred        dinput<elf>
  \-PE  7ea50000-7ea7f000       \               dinput
ELF     7ea7f000-7ea98000       Deferred        dinput8<elf>
  \-PE  7ea90000-7ea98000       \               dinput8
ELF     7ea98000-7eade000       Deferred        advapi32<elf>
  \-PE  7eaa0000-7eade000       \               advapi32
ELF     7eade000-7eae9000       Deferred        libgcc_s.so.1
ELF     7ebc8000-7ec7f000       Deferred        gdi32<elf>
  \-PE  7ebe0000-7ec7f000       \               gdi32
ELF     7ec7f000-7edb9000       Deferred        user32<elf>
  \-PE  7eca0000-7edb9000       \               user32
ELF     7edb9000-7ee78000       Deferred        comctl32<elf>
  \-PE  7edc0000-7ee78000       \               comctl32
ELF     7ee78000-7ee83000       Deferred        libnss_files.so.2
ELF     7ee83000-7ee99000       Deferred        libnsl.so.1
ELF     7ee99000-7eea2000       Deferred        libnss_compat.so.2
ELF     7eea2000-7eea5000       Deferred        libxau.so.6
ELF     7eea5000-7eeb9000       Deferred        lz32<elf>
  \-PE  7eeb0000-7eeb9000       \               lz32
ELF     7efc3000-7efe9000       Deferred        libm.so.6
ELF     7efe9000-7efee000       Deferred        libxxf86vm.so.1
ELF     7efee000-7eff8000       Deferred        libnss_nis.so.2
ELF     b7d63000-b7d67000       Deferred        libdl.so.2
ELF     b7d67000-b7e9b000       Deferred        libc.so.6
ELF     b7e9c000-b7eaf000       Deferred        libpthread.so.0
ELF     b7ec6000-b7fd7000       Deferred        libwine.so.1
ELF     b7fd9000-b7ff4000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000001b (D) E:\Oblivion_lin\Oblivion.exe
        00000021   -1
        00000020   -1
        0000001f   15
        0000001e   15
        0000001d    0
        0000001c    0 <==
00000017
        0000001a    0
        00000018    0


BTW I'm running wine-0.9.31, and have a ATI Radeon 9800Pro graphics card (runs Oblivion OK in windows) with the official ATI proprietary drivers installed. Also I'm using the European version since I live in the UK so ran the Euro patch, but that should not make this kind of difference.

Also I'm excited by that fact that it gave me a Backtrace, I'm tempted to download the wine source and start playing with the code, but then again I have no idea if this is a wine bug (or is everything like this a wine bug? I really don't know much about wine's depths). And learning to find my way around the wine source code is probably a big job. 

Any ideas?

---

### Post by kroenecker on 2007-02-20
Mongoose,

Thanks for all of your input.  If you read my post, I'm not referring to the movies.  The game starts fine.  I follow the king down the steps and then it crashes.

---

### Post by solitary on 2007-02-21
kroenecker: The game still crashes if I try to save. But now I can make it a little bit further by setting bAllowScriptedAutosave=0. But I get stuck again a little bit further down.. Think the king is supposed to be attacked, but none is coming :P

---

### Post by Mongoose on 2007-02-21
I was referring to the couple of posts suggesting the deletion of files and installing mods instead of changing a line in the ini.   If you change that line you skip the intro crash and still get working movies in game such as the main menu scrolling map.

As for crash on save -- if you have offscreen target set to fbo and it still crashes it's likely a video driver issue.  If you have an ATi card that's likely the case.  As mentioned in the guide the settings given are known to work on Nvidia 6800 and later.   As I talked to people on irc with 78xx, 79xx, and 88xx that got it running.

Looking at the dump it's pretty clear the ATI FBO implementation caused the crash posted above as well.  You should report this issue to Wine developers, and see if it is indeed a driver issue or bug.  You can do this by clicking on the Wine AppDB link in the first post and file a bug.

I try to reply to all posts I see in one reply, so pick through this and find your reply.

Update:
I updated the wiki in regard to the ATI crashes.  If setting the OffscreenRenderingMode to 'pbuffer' in the Oblivion.ini doesn't help then you might be stuck until it's fixed in your driver or Wine developers workaround and/or fix it.  Again I urge you as one of the few people using an ATI card to report this to Wine developers if you want to see it fixed.

Update 2:
It might help to start listing the setups that work as well as narrowing down those that don't...  I'll start by posting what I use.

"Works for me"
* 6800 GS, 1.0-9746 Nvidia driver
* AMD64x2, Ubuntu Linux x86_64, Wine GIT and Wine 0.9.31 Ubuntu packages
* Oblivion.ini differs from the guide by having all the threading options enabled

---

### Post by Mblackwell on 2007-02-21
I should point that in general, even in Windows, you shouldn't exactly expect Oblivion to work well unless you have NV40 or higher (or equivalent) hardware.

If you have lower end hardware than that (such as FX cards), the only real option is Oldblivion, which I don't think currently works under Wine, does it?

---

### Post by kroenecker on 2007-02-21
Solitary: I wonder what similarity we are sharing?  I got a bit further by turning off all save options in the ini, but nobody attacked :P  

I'm using (without success):
AMD Athlon(tm) 64 Processor 3200+
GeForce 7600 GT/PCI/SSE2/3DNOW!
2.1.0 NVIDIA 97.46
2.6.17-11-generic
Xorg Version 7.1.1
Ubuntu 6.10 (edgy)

---

### Post by Mongoose on 2007-02-21
Let's try and focus on important information:

* x86_64 or i386 linux?
* Which Wine version?
* What changes besides the ones in the guide did you make to your Oblivion.ini?

Also, if you're crashing with an Nvidia card on save it's likely you didn't read the guide -- set offscreen to FBO and it shouldn't crash.  Wine defaults to backbuffer, which is known to cause a crash.

---

### Post by dbd on 2007-02-22
Ok, I've reported the bug to the wine ppl. It's here if anyone wants to look:
[http://bugs.winehq.org/show_bug.cgi?id=7518](http://bugs.winehq.org/show_bug.cgi?id=7518)

---

### Post by solitary on 2007-02-22
Settings that differ from guide is:
[wine regedit.exe]
VideoMemorySize          384   (GPU: 256 + AGP aperture size: 128 )
[Oblivion.ini]
bAllowScriptedAutosave=0

Software:
Oblivion (DVD English euro version) + patch: Oblivion_v1.1UKEnglish
Wine 0.9.31 (wine.budgetdedicated.com)
Nvidia 9746 (albertmilone bleeding edge ubuntu drivers, repo: latest)
Kernel version: 2.6.17.11 on x86 (generic and 386)

Hardware:
AMD Sempron 3400+, s754 (No Overclock)
nVidia 7600GT 256MB AGP (No Overclock)
Soundblaster Live Value
Kingston RAM 2*512 MB CL2,5 
Seagate SATA 320 GB 
Seasonic S12 430W

PS.
OffscreenRenderingMode is set to fbo.

---

### Post by Mongoose on 2007-02-22
Did you try setting OffscreenRenderingMode to pbuffer to see how that runs on ATi?  With Nvidia pbuffer runs much better, but crashes on saves due to the way a screen dump is done for the save thumbnails.  I thought someone posted a bug on that and audio too.  It's in the write up, but I didn't see any bugs filed.  I might try to get some dumps posted later for those.  Thanks, without an ATi user to post traces and do follow ups that will never get fixed otherwise.   =)

Also you might want to include that FBO crash backtrace you posted the other day, since it's more descriptive.  Perhaps I was looking at it wrong, but the attachment I saw in the DB didn't have enough info to make a conclusion about it.

solitary: I assume that's a known working config?  I wonder if you could get more performance by just removing the aperture memory from your total.  I'm unsure how that figure really is used by Wine.  It wouldn't hurt to test without it and see if you get a slight performance boost in case readpixels calls or FBO operations are hammering your AGP.

---

### Post by dbd on 2007-02-23
Yeah, I tried setting OffscreenRenderingMode to pbuffer (I assume you mean in the registry, not in the ini, by the way, the ini is what you suggest in the "Known Issues" section of the wiki).

However, I'm not sure if that is working since the Direct3D folder did not exist in HKEY_CURRENT_USER / Software / Wine / so I had to create it, is that usual? (This may be because I didn't have my graphics card driver installed when installing wine, should I reinstall wine?)

Also graphics settings auto-detect fails in the settings thing in the Launcher, it says "Video Hardware Unrecognised" when I click reset to defaults. Is that usual?

By the way, I've now added the backtrace on the wine bug report.

---

### Post by Mongoose on 2007-02-23
You should've gone by the guide and ran wineprefixcreate, which would've fixed registry issues like missing default folders/keys.  Yeah, I likely typed something else in and removed it or it got edited out later.  I'll fix it -- thanks.   It was likely a suggestion for setting light passes.

Update: 
Wiki was updated about a suggestion for ATi users thanks to Winehackers!

---

### Post by Inc&#940;nus on 2007-02-23
Hi there mongoose, thanks for giving your time to help with this - I've spent a while today fighting this problem over cups of coffee, as I haven't had anything else to do, and I just thought I'd venture a post...

I'm getting the same apparently fglrx-related error with a 9800 Pro - that output (dbd) looks just like mine - and I've been able to reproduce it on 0.9.29-0.9.31, with a new wine directory each time and just the Oblivion-related keys and the suggested dx9 dll.

My first thoughts were to change the suggested render mode from fbo, same result with pbuffer and default, then to change UseFastTLS to 2 from 0, and even  try 1 - didn't work, same thing.

I've also tried all combinations of the above with fglrx 8.32.5-1 and 8.33.6, then aslight  kernel upgrade to a newer 2.6.16 and did it all again. Same thing every time.

I now have a hunch I'm going to try. Will post back later if it works - just thought I'd add my experience of it.

---

### Post by Mongoose on 2007-02-24
It could just be a bug in the ATi FBO implementation as well.  I don't have the hardware to confirm that however...  it might be helpful to send the crash to ATi drivers developers however they handle their bugs.  The crash is certainly in the ATi driver, but I'm unable to step the code to see how reasonable the request was... seeing how it's working for Nvidia users and it's just setup for FBO...  I'm certainly leaning toward it being ATi's fault.

---

### Post by solitary on 2007-02-25
I get a few more fps when setting VideoMemorySize 384 rather than 256.

A little progress. Changed vm.swappiness to 0 and now the king gets attacked and I get to play the tutorial :), maybe you can verify this kroenecker? But I still cannot create savegames..

---

### Post by dbd on 2007-02-25
> **Mongoose said:**
> You should've gone by the guide and ran wineprefixcreate, which would've fixed registry issues like missing default folders/keys.  
I did :)

Anyway, it seems the wine people agree with you and blame ATI. So I've reported the bug to ATI:
[http://ati.cchtml.com/show_bug.cgi?id=581](http://ati.cchtml.com/show_bug.cgi?id=581)
Although I'm not quite sure what that website is, because the link from the ATI site to there said that it was not official, but if it isn't for the official ATI developers (with the closed source code) then who is it for???

Also the wine people said not to use FBO as it isn't supported yet, but as far as I know I'm using pbuffer, not fbo (not that I really explain what these things are :D).

---

### Post by Mongoose on 2007-02-25
Well, FBO at present is the only way you can run Oblivion w/o crashing everytime you do certain readpixels like operations -- like saving a game.  I personally wouldn't worry about it much, since FBO will likely become default in the future and works the best for now.  Using pbuffer or backbuffer registry settings will crash you out of Oblivion if you go outside or save the game for example.  It may seem random, but it's all due to how bethsoft does certain image space effects and how Wine handles it.  Calling one of those functions then causes the crash.  The best way to see it is to save a game.

---

### Post by solitary on 2007-03-01
Thank you Mongoose. Thanks to you I got the game running fine :)

---

### Post by Mongoose on 2007-03-02
bitte sher... I updated the wiki for a rare crash if you have JoyStick enabled in the Oblivion.ini.  I'm not sure that's really a direct cause, but I suggested disabling joystick for more fps.  He can repeat a crash if it's enabled and avoid crashing goes away if it's disabled.  I don't know what to make of that unless he has a joystick driver doing odd things.   =)

Also someone posting on the wiki claimed setting in game software sound helps if you're getting static, but last time I tried it did not.  Head over to the wiki if you're curious.

---

### Post by Lincolns_back on 2007-03-03
hey im not sure how to psot inmy own forum or make on so im postign here my wine was fien  one day i went into winecfg then clickedadd program and it came up with this 

err:shell:SHGetFolderPathW Failed to create directory 'L"z:\\home\\lincoln\\Desktop"'.
err:commdlg:IShellBrowserImpl_BrowseObject could not browse to folder 

so i cant add programs with it adn cant install stuff it jsut freezes on stuff plz help i tryed reinstalloing it but didnt work

---

### Post by Mongoose on 2007-03-05
This isn't really related to Oblivion under Wine, and should be a separate thread.  If you can't access that directory you have problems beyond Wine.   I suggest you start a new thread:

1. Go to the Gaming fourm by clicking the link at the top of this thread.
2. Click the make new post link in the upper left hand side.

You may be able to use this link directly:
[http://ubuntuforums.org/newthread.php?do=newthread&f=93](http://ubuntuforums.org/newthread.php?do=newthread&f=93)

---

### Post by Iarwain ben-adar on 2007-03-06
Hi Mongoose,

nice how-to!

Unfortunately it doesn't completely add up for me..

I ran wineprefixcreate, but i have no Direct3D folder in my Wine registry..

How can i fix this?


Iarwain

---

### Post by bastiegast on 2007-03-06
You can just make the folder and keys in your registry.

---

### Post by Iarwain ben-adar on 2007-03-06
I can't seem to find an option to make a folder in my registry..

Is that possible?

Nvm,
i found it under "Edit, New, Key" :D


Iarwain

---

### Post by Iarwain ben-adar on 2007-03-06
Damn it,

now i get this error..


Iarwain

---

### Post by Pensacola on 2007-03-06
I'm trying to get oblivion to work with Wine, but I don't have a HKEY_CURRENT_USER / Software / Wine / Direct3D folder in my regedit.exe, the Direct3D just isn't there. 
How can I fix this?

---

### Post by Iarwain ben-adar on 2007-03-06
See post #79 :wink:


Iarwain

---

### Post by Mongoose on 2007-03-06
That message box could mean you're out of diskspace perhaps.  I'd double check.  =)

---

### Post by Iarwain ben-adar on 2007-03-06
I have 8,6G free space, so i don't think space would be a problem :D


Iarwain

---

### Post by Mongoose on 2007-03-07
If you read the guide that doesn't mean Wine can see it.  That's why I said to double check your game install doesn't cross mounted partitions.  Otherwise there is a chance it'll only see root or home as your entire C: or G: drive for example -- even if you're installing to /usr or /opt.  

If that's not it you need to get some debug output from a terminal before anything can be well debugged.

---

### Post by Iarwain ben-adar on 2007-03-07
I tried installing from the same partition (not my NFS, like before)

This is what i get from the terminal
> iarwain@iarwain-laptop:~$ sudo mount tes4.obliv.mdf -o loop /test
iarwain@iarwain-laptop:~$ wine /test/setup.exe
iarwain@iarwain-laptop:~$ fixme:process:IsWow64Process (0xffffffff 0x34df78) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da80) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7ac) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7b0) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da80) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7ac) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7b0) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da80) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7ac) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7b0) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da80) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7ac) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7b0) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da80) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7ac) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7b0) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da80) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7ac) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7b0) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da80) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7ac) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7b0) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da80) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7ac) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7b0) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da80) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7ac) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7b0) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da80) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7ac) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7b0) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da80) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7ac) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7b0) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da80) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7ac) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7b0) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da80) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7ac) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7b0) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da80) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7ac) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7b0) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da80) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7ac) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7b0) stub!
fixme:process:IsWow64Process (0xffffffff 0x34da80) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7ac) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d7b0) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d8d4) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d8d4) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d8d4) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d8d4) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d8d4) stub!
fixme:process:IsWow64Process (0xffffffff 0x341160) stub!
fixme:process:IsWow64Process (0xffffffff 0x341160) stub!
fixme:process:IsWow64Process (0xffffffff 0x341160) stub!
fixme:process:IsWow64Process (0xffffffff 0x341160) stub!
fixme:process:IsWow64Process (0xffffffff 0x341160) stub!
fixme:process:IsWow64Process (0xffffffff 0x341144) stub!
err:ole:get_unmarshaler_from_stream Failed to read common OBJREF header, 0x00000001
fixme:ole:NdrClearOutParameters (0x7c99eee0,0x864212,0x7c99f014): stub
fixme:process:IsWow64Process (0xffffffff 0x341534) stub!
fixme:reg:GetNativeSystemInfo (0x341510) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x341704) stub!
fixme:reg:GetNativeSystemInfo (0x3416e0) using GetSystemInfo()
fixme:x11drv:X11DRV_SetWindowRgn not supported on other thread window 0x2002c
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGING: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGED: stub
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGING: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGED: stub
fixme:shell:IShellLinkA_fnGetPath (0x1a52588): WIN32_FIND_DATA is not yet filled.
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell:IShellLinkA_fnGetPath (0x1a52588): WIN32_FIND_DATA is not yet filled.
fixme:mscoree:GetCORVersion (0x33f734, 600, 0x33f724): semi-stub!
fixme:shell:IShellLinkA_fnGetPath (0x1a51ff0): WIN32_FIND_DATA is not yet filled.
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33f630
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33ef80
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33ef80
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33ef80
fixme:mscoree:LoadLibraryShim (0xa02668 L"fusion.dll", (nil), (nil), 0x33ef64): semi-stub
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell:IShellLinkA_fnGetPath (0x1a51ff0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1a58210): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1a58210): WIN32_FIND_DATA is not yet filled.
fixme:process:IsWow64Process (0xffffffff 0x34d9f0) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d9f0) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d9f0) stub!
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-1000-00000a000000}
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-1000-00000a000000}
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-1000-00000a000000}
err:rpc:I_RpcReceive we got fault packet with status 0x6be

iarwain@iarwain-laptop:~$                      


Iarwain

---

### Post by Mongoose on 2007-03-07
Hmm... looks like an OLE problem as far as I can tell.  You're using the Windows XP profile, correct?   Also give me your Wine version.   It will likely run correctly if you run setup.exe from the mount point /test if it's just a relocation issue:

 cd /test
 wine setup.exe

---

### Post by Iarwain ben-adar on 2007-03-08
I don't know whatt profile i'm using ;o

```
iarwain@iarwain-laptop:~$ wine --version
wine-0.9.32
iarwain@iarwain-laptop:~$

```

I'll try installing from /test/ later, as i need to go to school :D

EDIT:

using wine from /test/ gives me the same error.. :?
Repeating the first error for about 20 times,
> fixme:process:IsWow64Process (0xffffffff 0x341160) stub!
fixme:process:IsWow64Process (0xffffffff 0x341144) stub!
err:ole:get_unmarshaler_from_stream Failed to read common OBJREF header, 0x00000001
fixme:ole:NdrClearOutParameters (0x7c9adee0,0x864212,0x7c9ae014): stub
fixme:process:IsWow64Process (0xffffffff 0x341534) stub!
fixme:reg:GetNativeSystemInfo (0x341510) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x341704) stub!
fixme:reg:GetNativeSystemInfo (0x3416e0) using GetSystemInfo()
fixme:x11drv:X11DRV_SetWindowRgn not supported on other thread window 0x2002c
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGING: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGED: stub
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGING: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGED: stub
fixme:mscoree:GetCORVersion (0x33f734, 600, 0x33f724): semi-stub!
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33f630
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33ef80
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33ef80
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33ef80
fixme:mscoree:LoadLibraryShim (0xa02668 L"fusion.dll", (nil), (nil), 0x33ef64): semi-stub
fixme:shell:IShellLinkA_fnGetPath (0x1a1ebb0): WIN32_FIND_DATA is not yet filled.
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell:IShellLinkA_fnGetPath (0x1a1ebb0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1a24840): WIN32_FIND_DATA is not yet filled.
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell:IShellLinkA_fnGetPath (0x1a24840): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1a24a80): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1a24a80): WIN32_FIND_DATA is not yet filled.
fixme:process:IsWow64Process (0xffffffff 0x34d9f0) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d9f0) stub!
fixme:process:IsWow64Process (0xffffffff 0x34d9f0) stub!
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-1000-00000a000000}
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-1000-00000a000000}
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-1000-00000a000000}
err:rpc:I_RpcReceive we got fault packet with status 0x6be



Iarwain

---

### Post by Jiraiya_sama on 2007-03-09
Mongoose, I'm currently working on an automatic installer for oblivion based off your oblivion guide, and I was gonna post it here, if that's ok with you.

---

### Post by Andrew500 on 2007-03-09
I followed the instructions to the T and got it to the loading screen, but it sits at 0% loaded (the little cursor doesn't move).  Any ideas?  I've done all the .ini tweaks and everything.

---

### Post by Mongoose on 2007-03-09
Jiraiya_sama: 
I personally don't see the need for such an installer after seeing all the problems with the Morrowind install till this day.  I'm sure someone would like it however.  It would make more sense to be in a separate thread however, since this thread is about a different method.  It'll make replying to issues easier to handle people doing different install methods in different threads.  =)

Andrew500:
ATi?

---

### Post by Mongoose on 2007-03-10
Iarwain ben-adar:

Try downgrading to 0.9.29 and reinstalling Oblivion to rule out a new bug in winetools/wine completely.  I can't tell from your output exactly what's wrong, but it can't load several paths for one thing and that could contribute to the OLE errors.   I went back in the thread and saw you manually edited your wine registry, which might be related to this problem.

1.) From what I know about msi/like bugs it might help to uninstall your partial Oblivion install manually or using the uninstaller if you have it and dare.  You can skip doing this and hope for the best.

2.) Run wineprefix and follow the guide again.  This should fix your registry missing important default keys.

3.) You need to run winecfg and double check to ensure your Wine profile is XP, drives match your partitions, and paths are working correctly.  

Extra) Are you installing in a desktop of Wine or as a managed Window?  I don't think it has anything to do with the lock up, but it's interesting some of the FIXMEs I see in that output.

---

### Post by Iarwain ben-adar on 2007-03-10
I will try that

Problem is that winehq is not reachable.. (is it offline?)


Iarwain

---

### Post by Breepee on 2007-03-10
> **Iarwain ben-adar said:**
> I will try that

Problem is that winehq is not reachable.. (is it offline?)


I cant reach winehq either for the last 24 hours or so...

---

### Post by Iarwain ben-adar on 2007-03-10
Do you know an alternative link for 0.9.29?

Please note that i'm on Feisty..

Maybe that could be my problem :?


Iarwain

---

### Post by Mongoose on 2007-03-10
Read the guide at the wiki.  Click on the budgetdedicated link and download the archived version.    The first post of this thread has a link to it.

---

### Post by Iarwain ben-adar on 2007-03-10
With wine .29 i  get the same error :?


Iarwain

---

### Post by Mongoose on 2007-03-11
Then it's your wine setup for sure.  First try using a native ole32.dll and if that fails...  You could take the nuclear option, and move your .wine to dotwine-old and start over.  Read the guide carefully, and if the wiki looks incorrect click on the history and read the last commit by 'Mongoose' to be sure it's not misinformation.  If it works then you can go back and compare to see what was wrong.  Make sure you reinstall the mozilla componets, etc as well.  

I can't be sure what you're doing wrong, but it's related to your setup.  I still think it's related to your path and drive setup -- it could be you have a componet everyone one else seems to have installed.  I find that unlikely however, or someone else would have the issue.  It's clearly not a problem related to Oblivion itself.  I'd suggest starting a new general 'Wine install issue' thread if you can't get anywhere with a new .wine.  If the 'clean' .wine works get meld via synaptic.  Use meld to visually diff the *.reg files in dotwine-old and .wine.  Good luck.

---

### Post by Iarwain ben-adar on 2007-03-11
Well, i did what you said,

and when i want to edit my registry, i still don't get a Direct3d folder..

Could this be a problem? Or do i make it like i did previously?


Iarwain

---

### Post by ahaslam on 2007-03-11
[QUOTE=Mongoose]I turn on a few extra threads for various options since I have an AMD64x2.[/QUOTE]
What does this do, how is it done & what's the benefit? I'm assuming it makes better use of both cores, so I'm quite interested in this. Can it be done for other games also?

Excuse my n00bness, I'm new to the world of dual core processors & modern games ;)

Thank you ;)

PS. Should 1 gig of RAM be adequate for good performance under WINE?

---

### Post by Iarwain ben-adar on 2007-03-12
The same..

I'm getting quite desperate. The problem is, there is no info on this problem.. :?


Iarwain

---

### Post by Iarwain ben-adar on 2007-03-12
Update:

i tried installing on Windows, and got the same error!

So it has to do something with my dvd of Oblivion..


Iarwain

---

### Post by bastiegast on 2007-03-12
> **Iarwain ben-adar said:**
> Update:

i tried installing on Windows, and got the same error!

So it has to do something with my dvd of Oblivion..


Iarwain

Very sorry for your DVD but I can't help but to laugh about the situation:oops: , are you going to return it?

---

### Post by Iarwain ben-adar on 2007-03-12
The problem lies in the fact that i can't find my DVD,
(i'm trying to install from iso)

So either way, i'm pretty ******* :D

Btw, i checked the md5sum, and it shows no errors (or whatever k3b does)


Iarwain

---

### Post by Mongoose on 2007-03-12
It let's you divide given tasks across threads, which leads to better parallelism.  It leads to performance / feature increases in general.  In Oblivion you can use more threads for animation, sound, and physics.  Just read the ini it's pretty clear to me, however oblivion ini guides should provide all the details you need.

You having 1GB might mean closing your office suite, etc when you play.  =)

---

### Post by Mongoose on 2007-03-12
So it WAS a path/drive error more or less...   =p

As a side note, if you check your ~/.wine/dosdevices you might notice your device links are off from time to time -- if you can't print check there.  I just fixed a printer issue by fixing the lpr link heh.  Well, after the OLE issue it had to be filesystem.  Oblivion is pretty cheap now, and you should buy a copy.  The expansion Shivering Isles is being released this week.  I might pick SI up, but I need to do work.  ^_^

---

### Post by Iarwain ben-adar on 2007-03-13
UPDATE:

I tried extracting the files with unshield,
but on "meshes.bsa" it fails..

Still running the program.

Is there any way i could try to extract it forcefully?

>   extracting: ./Oblivion/Data/Oblivion - Meshes.bsa
[unshield_file_save:658] Decompression failed with code -3. bytes_to_read=12198, volume_bytes_left=470562711, volume=2
Failed to extract file 'Oblivion - Meshes.bsa'.



Iarwain

---

### Post by ahaslam on 2007-03-13
> **Mongoose said:**
> It let's you divide given tasks across threads, which leads to better parallelism.  It leads to performance / feature increases in general.  In Oblivion you can use more threads for animation, sound, and physics.  Just read the ini it's pretty clear to me, however oblivion ini guides should provide all the details you need.

You having 1GB might mean closing your office suite, etc when you play.  =)

Thank you I'll look into that. I'm running XFCE, so at least that'll help with memory ;) I'm just reluctant to buy more of the same ram, I'm waiting for ddr2-6400 to become more affordable ;)

Could you elaborate further on your specs? I have an E6300 @ 2562MHz with a 7950GT & 1G of DDR2-5300 @ 732MHz but amazingly I struggle with native games like Nexuiz & Quake 4 :mad:  

So if you think my system is up to the task, I'll splash out on a copy of Oblivion after pay day (there may even be a new version of wine by then too) ;)

PS. *'800x600'* - would 1440x900 (full screen, native res.) be possible at decent frame rates?

---

### Post by Mongoose on 2007-03-13
I run an AMD64x2, 2GB RAM, 6800GS w/ 256MB, and normally the Ubuntu packaged Wine -- currently 0.9.32.  I only run GIT for debugging.  I get an acceptable frame rate given my GPU 20-50fps in general, but if you play around you can get it steady over 60 if you give up some things like draw distance with this card.  I turn off the water shader and grass in the game, but I crank up the draw distance on everything else higher than default.   The water shader really stresses my GPU, and the grass is annoying to play in and it's a ton of geometery you can avoid rendering.  I find the draw distance setting on grass very lame -- if you crank it down it's visually jarring and you can't see much waist deep in it.  Play with the grass slider in a feild to see what I mean.  When I played in Windows I turned grass up higher than trees to avoid the jarring visuals of seeing unnatural looking breaks in the grass / trees / terrian.  For fun turn grass to notch 1 -- I like to call it The Elder Scrolls: Okami -- only the flower/grass at your feet render.  How's that for jarring visuals in a photorealistic game?  =)

The Wine desktop is set at 1024x764 with Oblivion fullscreen, which lets me monitor my GPU temp, debug spew, etc when playing if needed.   You could run managed and have the game run windowed too I suppose, but using the Wine desktop avoids some issues with other games such as screen resolution resizing on crash.  I can't say I suggest playing it fullscreen on your monitor unless you like to only see the game itself.  I found when I played resolution didn't have that big an impact -- within reason.

As I posted before your results will vary.  I think a 7950GT is more than enough to get good play.

---

### Post by ahaslam on 2007-03-13
Thank you, I suppose it's all about finding the compromise that works well, while still allowing you to enjoy the game. I'll have to purchase the game & start tinkering ;)

---

### Post by BatPenguin on 2007-03-13
Hi there,

Great guide! First of all, a big thank-you to all of you making this possible and writing these instructions. Just read about this today, installed the game and tried it. It's getting pretty close to playable but not quite there yet on my system, hopefully somebody could help me a bit here...I feel like I'm very close to having this working.

I've followed the guide and installed everything. I think I've done everything ok, and basically "it works" (sound problem is there, though, plus I had to make the registry entries myself). Some ALSA error messages, too, but since sound sort of works, I don't think it's causing my bigger problem which is a very bad frame rate. Like not just "the machine is not bought yesterday" laggy but way slower than it should be. And: if I go and change the OffscreenRenderingMode registry entry to "pbuffer" or "backbuffer" the game is suddenly extremly smooth and feels really, really good -- except for one big problem: whenever I look at an Oblivion gate, the whole screen goes totally green except for the gate which looks just weird in the middle of the screen there...and returns to normal when I look away from it. With "fbo" there's no "green screen" problem but the  game gets maybe (at most) half of the fps of those buffering modes and is not playable even with everything turned completely down. I got the idea of trying these pbuffer/backbuffer options from this howto: [http://www.icculus.org/~mongoose/OblivionHOWTO.html](http://www.icculus.org/~mongoose/OblivionHOWTO.html)

Now, is it possible to tweak something so that pbuffer or backbuffer would work without these green screen issues (anybody heard of that before?), or is there some other problem at work...should the difference between fbo and these buffer modes be this big? or is the fbo not working OK for me for some reason...

The system isn't exactly new but quite capable of running this game in Windows (and apparently with these pbuffer etc. modes): Athlon XP 2800, Geforce 6800 Ultra 256MB, 2.5 gigs RAM.

Could this be related to xorg settings? I'm using 24 bit color, normally run beryl but have it turned off for this. If xorg settings could affect it (triplebuffer etc. whatever those do), I'd be happy to post my xorg.conf. 

I'd really appreciate any tips on what could be causing this huge difference in performance between fbo and pbuffer/backbuffer and how I could either get fbo closer to the pbuffer performance or get rid of the green oblivion gates problems.

---

### Post by Mblackwell on 2007-03-13
Yeah I had performance problems too with fbo, which basically had to be on if I didn't want a crash when I saved. I think the crash when save might be fixed though, but apparently there's the problem you just described.

I hope everything gets fixed soon. They seem to be going pretty rapidly on this one.

---

### Post by surdin on 2007-03-13
> **Iarwain ben-adar said:**
> Do you know an alternative link for 0.9.29?

Please note that i'm on Feisty..

Maybe that could be my problem :?


Iarwain

This 'How To' does work in Feisty... at least it did for me.. works very well.

---

### Post by Mongoose on 2007-03-13
Wow, you use pbuffer without the readpixels aka save game crash?  That's very interesting.

Edit: I'll look into this tonight.  I haven't been able to do valid testing after my recent kernel upgrade due to my GPU overheating.  It wouldn't hurt trying to confirm before I hit 120C hah.

It appears 0.9.23 works with pbuffer setting, but I haven't tested problem areas like the imperial sewers.  I'll update the wiki.

Looks like I already had the information in there -- so I just added emphasis.  I'm not changing the default setting in the wiki until someone can vouch for it with more play time and all shaders on...  ;)

---

### Post by STiYaKuzA on 2007-03-14
hey mongoose thanks for the great howto, but i had the exact same problem as dbd (the ati/wine bug). however, one interesting point i noted was that if i tried running oblivion in cedega, there is no problem at all, even without the oldblivion patch(with the exception of the texture problems due to cedega's lack of shader 2.0 support), so i'm pretty certain its a wine bug...

---

### Post by BatPenguin on 2007-03-14
> **Mongoose said:**
> 
It appears 0.9.23 works with pbuffer setting, but I haven't tested problem areas like the imperial sewers.  I'll update the wiki.


I'm assuming you meant 0.9.32 not 23, right? I was going to give a few earlier wine versions like 31, 30 and 29 a a try tonight (using 0.9.32 now) to see if either my fbo gets more fps or pbuffer stops doing that green screen problem. I'll let you all know how it goes...and please, if anybody has more suggestions on improving fbo performance or fixing my pbuffer problem, let me know. So far I haven't seen anybody else reporting this green screen thing so it'd be interesting to know if it's something specific to my setup or a general wine problem etc.

---

### Post by Mongoose on 2007-03-14
> I'm assuming you meant 0.9.32 not 23, right?

Never post with a fever.  Yes, 0.9.32 -- I feel a lot better today.  You'll find 0.9.23 is the only version that doesn't crash on game save ( which does a funky type of readpixels ) using pbuffer.   =)

> due to cedega's lack of shader 2.0 support

Yeah, so you likely can't even get any lighting either.  "Oldblivion" isn't really much of an option, which I've mentioned before ini tuning will do more for you than it will.  Also dissabling the specular pass can be a bad idea in some areas -- it will lead to a crash.  The bottome line is cedega isn't working nearly as well hq wine, and ATi need to fix their drivers.  HQ Wine has even supported bloom for a while.  The only things most people need fixed now are audio mixing and HDR support.

---

### Post by BatPenguin on 2007-03-15
Hi again,

Alright, still trying to get the most performance out of my box for hopefully getting Oblivion playable. Could people who have it running at a decent playable speed please either post their xorg.conf files or let me know if you're using the following options in xorg (I guess this has to do with Nvidia users, I have the GF6800 Ultra):

Option "RenderAccel" 
- do you have it as true or false? Any difference to frame rates? Mine's true

Composite extension
- enabled or not? Mine is, not sure if it has to be, using Beryl with the Nvidia GLX extension

Beryl / XGL etc. 
- do you have beryl activated while playing?
- do you play in a full-screen or window?

Color Depth
- what do you have set? Any difference between 24 bit and 16 bit modes, recommendations?

Thanks!

---

### Post by Mongoose on 2007-03-15
Switch to metacity using the Beryl settings icon in the notification area aka tray.  This will give you  much better performance in general.  Always switch before starting an OpenGL game for improved performace.  Once you switch window manager like that the first two questions no longer apply in a sense.  I use AIGLX for my xorg settings, and the new beryl 0.2 release from last night.  Not that it matters about the version just FYI there is a new release.  ;)

I play fullscreen inside a 1024x748 Wine desktop. 

Stay at 24bit, or you'll be dithering a lot.

---

### Post by BatPenguin on 2007-03-15
OK, thanks for the settings help! Still not quite enough to get me running with the fbo setting, I guess I'll wait and hope for a version of wine that'll support the pbuffers setting, that would seem to be fast enough for playing. Anyway, thanks again!

---

### Post by Mongoose on 2007-03-15
I'd urge you like other ATi users on this thread to request that they fix their drivers.  You bought the hardware, so you have as much of a right as anyone to demand working drivers.  

I don't know how you feel about the whole issue, but it would be best to just get an Nvidia GPU if possible.  The 7950GTs are affordable now that the 8XXXs are out.  There are also 7600s and 6800s that are relatively cheap as well.  If you're on a laptop with integrated video I feel for you.

---

### Post by Jason_25 on 2007-03-16
I just had to post a screenshot.  
On the system I am testing on right now: Kubuntu Feisty Fawn AMD64 daily build with Wine 0.9.32 on a : 939 3700+@2.75 / 2GB @ 250 / 6800 Ultra. I'm getting from 20-40 fps at 1024x768 high details with bloom.  I haven't tried HDR.  Maybe 25% less performance than Windows.

I had to tweak these in the ini to keep from crashing:
SMainMenuMovieIntro=
SIntroSequence=
And I had to change the offscreen render from fbo to pbuffer to get the water to show up correctly.

For now, I have visual glitches like the water not looking as good as it's supposed to, and objects popping in and out sometimes.  I also get the static near water occasionally.  

It's very playable.  I would give the game a silver on the Wine AppDB.

---

### Post by BatPenguin on 2007-03-16
> **Jason_25 said:**
> I just had to post a screenshot.  
On the system I am testing on right now: Kubuntu Feisty Fawn AMD64 daily build with Wine 0.9.32 on a : 939 3700+@2.75 / 2GB @ 250 / 6800 Ultra. I'm getting from 20-40 fps at 1024x768 high details with bloom.  I haven't tried HDR.  Maybe 25% less performance than Windows.

Hey, this sounds great...my system is similar though slower (Athlon XP 2800 but also 6800 Ultra, AGP version though). I'm getting pretty good performance with pbuffers as well, but as I explained earlier, I'm getting a green screen while looking at Oblivion gates. Since apparently you're not suffering these pbuffer / screen going green things and we're using the same Wine version and graphics card, I'd be VERY interested in seeing what you have in your xorg.conf and Oblivion.ini, just to see what (if anything) is different. So would you mind posting them or e-mailing directly to me: risto.rossi at welho.com . Thanks!

(I'm using Edgy, though, so perhaps the different Xorg version in Fawn might help you as well...I don't think I'll upgrade before the final Feisty release)

---

### Post by BatPenguin on 2007-03-16
> **Jason_25 said:**
> 
For now, I have visual glitches like the water not looking as good as it's supposed to, and objects popping in and out sometimes.  I also get the static near water occasionally.  

It's very playable.  I would give the game a silver on the Wine AppDB.

Oh hey, just noticed in your screenshot: is that the terminal window you use to launch wine that I see underneath your Wine desktop? The one with the messages...if it is, you should turn all those debugging messages off with the export command given in the wiki somewhere. That gave me some extra speed. Anyway, looks great...looking forward to peeking at your xorg.conf and Oblivion.ini if you don't mind.

---

### Post by Mongoose on 2007-03-16
1. I see you didn't read the guide, or it would've answered those questions.  ;)
2. Yeah turn off debugging for better gameplay -- see guide at the wiki.  
3. ATi users can't play still it seems, still has some issues like audio mixing sfx and no HDR yet -- but I voted for silver a while back too.

---

### Post by Iarwain ben-adar on 2007-03-16
HaHa!

With my new dvd, i'm ready to rock! Or atleast i thought..

Installed by instructions, patched aswell.

1 (or 2) problem(s) remaining:

The most annoying, see screenshots.
The lesser: the static sound. It's driving me nuts :D


Iarwain

---

### Post by Mongoose on 2007-03-16
Upgrade to 0.9.32.

Edit:
Oh yes, today or last night I updated the wiki to recommend setting pbuffer by default as render target.  Everyone has reported it working so well that I don't think I need to run an entire game again to test it.  Thanks.  ;)

---

### Post by Iarwain ben-adar on 2007-03-16
Thanks for stating the obvious :oops:

With all the fiddling with wine, i somethimes forget wich version i have..

On with the gaming!


Iarwain

---

### Post by slugkilla on 2007-03-16
Hey my sister's boy friend gave me this game. The game is very choppy and pretty much unplable once the 3D stuff starts. I've got a semprone 2200 or something like that, 515 MB ram, and a 5200 FX Ultra Nvidia with 128 MB. Should I get more ram or what? Thanks for all the hard work you have put into this.

---

### Post by Mongoose on 2007-03-17
A 5200FX is far below the min requirements.  Look for an option in the ini for 'GobalLight' something.  Basically, it'll disable all lighting for you.  That should help some, but realise that you really won't be 'playing Oblivion' at the point of disabling all the graphical features.  You should also turn off nearly all shaders -- look for ini guides for Windows players on 5xxx cards for help.  

Oldbivion was canned after editing the ini was found to be more effective after all.  If you can spare $50-$90 get a 6800 or a low end to mid range 7xxxx.  Just make sure it's "OpenGL 2.0", which will support the features you need for the game in Wine.

---

### Post by slugkilla on 2007-03-17
I can't really afford a new card right now, and it does not really matter to me if the graphics look like crap. I really just want to actually play it for a bit. Do you know of a good web page that talks about the bare minimum for graphic settings? I googled 5200 and oblivion and found a lot of oblivion.ini files, but the game always just starts lagging when that dude with the glowing necklace thing comes up.

Edit: Is it possible to get the game running with ridiculously crapy graphics. Like with blocks shapes  and mono tone color and other exaggerated simplistic graphics?

---

### Post by Mongoose on 2007-03-18
You could disable rendering of actors I suppose, but then you'd only see the landscape and buildings.  I'm going to be frank with you here -- 5200 was an entry level card in its heyday, which was very short lived since it even had horrible vertex and pixel shader performance at the time of its release.  You can disable everything but the texture pass before the game crashes if you want to go that far, however it will crash when certian objects that require specular pass are encountered.  

To be honest a 6xxx is the true floor for this game especially in Wine, which uses OpenGL.  I'd actually suggest waiting for a card upgrade before playing so you won't be so disappointed with flat textures and removing all water / trees / actors / etc in the game.  Save up a little cash and get a 6800 second hand or at a local store clearance.  People often sell their old cards when they updgrade and the 8xxxx cards are pushing the 6xxx and 7xxx cards down now.  I assume you only have the option of AGP, so it's good to know you can often reenable pipelines on the GS line and get a 'free' GT in a way.  I have an 6800 AGP like this on my old box.  The only thing better for AGP is an overly expensive 7800GS iirc, which is likely the last AGP that will be made as far as I know.  Just remember it's better to have last generations midrange than today's entry level as a good rule.  

[http://en.wikipedia.org/wiki/Comparison_of_NVIDIA_Graphics_Processing_Units](http://en.wikipedia.org/wiki/Comparison_of_NVIDIA_Graphics_Processing_Units)

You'll note the FX series only has limited OpenGL 2.0 support, but it's really just a 1.5 with very few extentions.  In this case it's very slow for what it does and it does very little of what you want to begin with... I wouldn't go lower than a 6600, which is the lowest end card to feature HDR support.  If you live near a college you might be able to get one for $20 even.  You never know.

Edit:
The reason I'm saying you might get it second hand so cheap is due to the fact all new systems are PCI Express.  Some people might just be ready to toss out old systems altogether for as low as $50 when they move.  Good luck.  ;)

---

### Post by Mblackwell on 2007-03-18
Seriously, on Windows back when I had a 5200, Oblivion ran pretty well with Oldblivion. In fact I was able to set the draw distances to basically the max, and except for the fact that sometimes lighting was fubar it was definitely playable and pretty great. Since you're using a 5200 you're basically screwed otherwise because it's no good with DirectX 9 rendering.

---

### Post by UberKnight on 2007-03-18
I followed the [latest guide]("http://www.uesp.net/wiki/Oblivion:Linux") and seem to have gotten the game working (although the directory suggestions don't work: "My Games" with the .ini file has to reside in my /home/{user} folder).

However, does anyone know how I can get the music to play?  I have not disabled it in the .ini.  Do I need any other DirectX files?

Thanks chaps, and good luck to those of you still struggling with this!

[Edit] Scratch that--just tried the actual game, lots of static, and character creation faces screwy.  Started a game and only have a partial head visible, no body, lol.  Will read more of these posts ;)

---

### Post by bastiegast on 2007-03-18
> **UberKnight said:**
> I followed the [latest guide]("http://www.uesp.net/wiki/Oblivion:Linux") and seem to have gotten the game working (although the directory suggestions don't work: "My Games" with the .ini file has to reside in my /home/{user} folder).

However, does anyone know how I can get the music to play?  I have not disabled it in the .ini.  Do I need any other DirectX files?

Thanks chaps, and good luck to those of you still struggling with this!

[Edit] Scratch that--just tried the actual game, lots of static, and character creation faces screwy.  Started a game and only have a partial head visible, no body, lol.  Will read more of these posts ;)

Did you upgrade to the latest wine?

By the way, compiled wine 0.9.33 yesterday, it doesn't fix the disappearing trees and bushes :( 

I wish I could help developing wine, but I'm stuck on 1/4th oh "Thinking in C++" :) , and with my Java skills I won't be of much help.

---

### Post by Mblackwell on 2007-03-18
> **UberKnight said:**
>  Started a game and only have a partial head visible, no body, lol.  Will read more of these posts ;)

Update your video driver to something newer than what's in the repos.

---

### Post by ahaslam on 2007-03-18
I purchased a copy of Oblivion today & thanks to your guide, installation & setup was painless :)

For some reason my experience is not consistent, sometimes it's very jerky & unplayable, while other times it's fairly smooth (I can always tell whether it'll be ok, by how the mouse moves at the first screen). I followed your directions to the letter (only with wine 0.9.33) & followed this guide for optimisations: [http://www.atomicmpc.com.au/article.asp?SCID=27&CIID=36546&p=4](http://www.atomicmpc.com.au/article.asp?SCID=27&CIID=36546&p=4) which made little/no difference, so I returned the ini back to default, with only your amendments. 

A couple of problems that are consistent are the sound (choppy & noisy) and the graphics (which suck). I followed your advice on the sound effects, which reduced the noise but it's still very apparent. I've included a screenshot to show my graphics, I'd appreciate any suggestions that may help improve the aesthetics & performance.

[ATTACH]27753[/ATTACH]

Oldblivion looks better than this: [http://www.oldblivion.com/?page=screenshots](http://www.oldblivion.com/?page=screenshots)

---

### Post by ahaslam on 2007-03-18
And a big problem... pressing 'Tab' to open the journal crashes the game. Another annoyance is that the brightness regularly changes suddenly, this happens at least 10 times per minute. Finally, it often hangs when exiting the game, requiring a reboot before you next play & all settings will be lost.

I will try wine 0.9.32 & see if it makes a difference.
_______________________________________

Ok, I've tried wine 0.9.32 & my experience has not changed. Another glitch worth a mention is that when an enemy is killed, they are engulfed by a huge sphere, until they're resting motionless on the floor :neutral: 

Some help would be greatly appreciated, this is the first PC game I've bought ;)

Tony.

---

### Post by Mongoose on 2007-03-18
The wiki keeps a list of 'known issues' for the current recommended version, which is 0.9.32 atm.  Wine 0.9.33 hasn't been able to be tested as much.  

Mp3 decoding in Oblivion doesn't even work for some Windows installs correctly.  Just a warning before you start adding native DLL overrides.  I'd suggest just disabling for now and getting a free speed boost. 

If you enable SM20 lighting it'll look better than no lighting:

[http://mongooseichiban.blogspot.com/2007/03/update-oblivion-in-wine.html](http://mongooseichiban.blogspot.com/2007/03/update-oblivion-in-wine.html) 

( Image was too big for Ubuntu fourms, however this is an undoctored and full resolution image of how it looks when I play. )

HDR isn't working yet, so you may want to enable bloom for now.  With HDR this game really shines.

As for the 5200 comments: yeah, last I checked you can't use PS1 in Oblivion with Wine w/o a crash.  You're out of luck until that works.

---

### Post by UberKnight on 2007-03-18
> 

[QUOTE]Originally Posted by UberKnight View Post
I followed the latest guide and seem to have gotten the game working (although the directory suggestions don't work: "My Games" with the .ini file has to reside in my /home/{user} folder).

However, does anyone know how I can get the music to play? I have not disabled it in the .ini. Do I need any other DirectX files?

Thanks chaps, and good luck to those of you still struggling with this!

[Edit] Scratch that--just tried the actual game, lots of static, and character creation faces screwy. Started a game and only have a partial head visible, no body, lol. Will read more of these posts
Did you upgrade to the latest wine?

By the way, compiled wine 0.9.33 yesterday, it doesn't fix the disappearing trees and bushes

I wish I could help developing wine, but I'm stuck on 1/4th oh "Thinking in C++" , and with my Java skills I won't be of much help.[/QUOTE]

Strange thing happened.  I updated the nvidia drivers to the latest using the Envy script (Automatix had installed on older version).

However, the game is now super slow and won't load a game or start a new one.  Any ideas?

---

### Post by ahaslam on 2007-03-18
> If you enable SM20 lighting it'll look better than no lighting

How do you do this? I can't find it in the ini or in game :-k

Cheers ;)
____________________________________________

I enabled 'bAllowQuality20Lighting' along with bloom & it doesn't look as good as your example.

I've taken a couple of screens showing the sudden brightness changes & the spheres:

[ATTACH]27765[/ATTACH] [ATTACH]27766[/ATTACH]

Any advice for the 'Tab - Journal' problem (complete crash every time)? Would you mind sharing your ini?

PS. I've attached my ini, I'd be grateful if someone could have a look at it ;)

---

### Post by Mongoose on 2007-03-18
You have:
bForce1XShaders=1

Should be:
bForce1XShaders=0

You also want to enable SM3:

bAllow30Shaders=1

Also a common setting to disable is refraction shader for the gates, etc.

bUseRefractionShader=0

And finally don't use background loading on everything.  It's very unstable in Windows, and I'd suggest skipping it Wine.  If you see weird phyiscs bugs you have threads dying that shouldn't be as well and may be better off cutting back your thread settings.

This is directed at people that don't read the guide at the wiki or other posts in this thread in general.  ^_^

Read the wiki guide before asking the same questions over and over please.  It's fine you have a valid bug or concern, but if you don't try the guide 100% the first time you play then you're missing the point.  I see a lot of people assume they can do whatever and eventually have to go back to the guide anyway.  If you're not very exp with tweaking the ini or understand the options you should just follow the guide the first time.  Then make changes to customize to your machine after you get it working.  Several people here have been working on tweaks for the ini for quite a while now.  If we tell you to at least do those 5 or 6 settings in the guide there is a reason, and in fact the reason is also written up in the guide itself.

---

### Post by dyous87 on 2007-03-19
Does anyone know if there is anyway I can get this game to run with the ATI Mobility Radeon using the fglrx drivers. The install went fine and whenever I try to run Oblivion It get up to a white screen that says "loading" and then crashes and exits. I don't know what else to do. 

This is my xorg config file:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Mobility Radeon x1400"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option          "UseFastTls" "2"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Mobility Radeon x1400"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
Option "Composite" "0"
EndSection

```

And this is my Oblivion.ini:

```


[General]

SStartingCell=

SStartingCellY=

SStartingCellX=

SStartingWorld=

STestFile10=

STestFile9=

STestFile8=

STestFile7=

STestFile6=

STestFile5=

STestFile4=

STestFile3=

STestFile2=

STestFile1=

bEnableProfile=0

bDrawSpellContact=0

bRunMiddleLowLevelProcess=1

iHoursToSleep=3

bActorLookWithHavok=0

SMainMenuMusicTrack=special\tes4title.mp3

bUseEyeEnvMapping=0

bFixFaceNormals=0

bUseFaceGenHeads=1

bFaceMipMaps=1

bFaceGenTexturing=1

bDefaultCOCPlacement=0

uGridDistantTreeRange=15

uGridDistantCount=25

uGridsToLoad=5

fGlobalTimeMultiplier=1.0000

bNewAnimation=1

fAnimationDefaultBlend=0.1000

fAnimationMult=1.0000

bFixAIPackagesOnLoad=0

bForceReloadOnEssentialCharacterDeath=1

bKeepPluginWhenMerging=0

bCreate Maps Enable=0

SLocalSavePath=Saves\

SLocalMasterPath=Data\

bDisableDuplicateReferenceCheck=1

bTintMipMaps=0

uInterior Cell Buffer=3

uExterior Cell Buffer=36

iIntroSequencePriority=3

bPreloadIntroSequence=1

fStaticScreenWaitTime=3.0000

SCreditsMenuMovie=CreditsMenu.bik

SMainMenuMovie=Map loop.bik

SMainMenuMovieIntro=Oblivion iv logo.bik

SIntroSequence=

iFPSClamp=0

bRunVTuneTest=0

STestFile1=

bActivateAllQuestScripts=0

fQuestScriptDelayTime=5.0000

SMainMenuMusic=Special\TES4Title.mp3

bUseThreadedBlood=0

bUseThreadedMorpher=0

bExternalLODDataFiles=1



[Display]

uVideoDeviceIdentifierPart1=0

uVideoDeviceIdentifierPart2=0

uVideoDeviceIdentifierPart3=0

uVideoDeviceIdentifierPart4=0

fDecalLifetime=0.0

bEquippedTorchesCastShadows=0

bReportBadTangentSpace=0

bStaticMenuBackground=1

bForcePow2Textures=0

bForce1XShaders=0

bHighQuality20Lighting=0

bAllow20HairShader=1

bAllowScreenShot=0

iMultiSample=0

bDoTallGrassEffect=1

bForceMultiPass=1

bDoTexturePass=1

bDoSpecularPass=1

bDoDiffusePass=1

bDoAmbientPass=1

bDoCanopyShadowPass=0

bDrawShadows=0

bUseRefractionShader=0

bUse Shaders=1

iNPatchNOrder=0

iNPatchPOrder=0

iNPatches=0

iLocation Y=0

iLocation X=0

bFull Screen=1

iSize W=640

iSize H=480

iAdapter=0

iScreenShotIndex=0

SScreenShotBaseName=ScreenShot

iAutoViewMinDistance=2000

iAutoViewHiFrameRate=40

iAutoViewLowFrameRate=20

bAutoViewDistance=0

fDefaultFOV=75.0000

fNearDistance=10.0000

fFarDistance=10000.0000

iDebugTextLeftRightOffset=10

iDebugTextTopBottomOffset=10

bShowMenuTextureUse=1

iDebugText=2

bLocalMapShader=1

bDoImageSpaceEffects=1

fShadowLOD2=400.0000

fShadowLOD1=200.0000

fLightLOD2=1500.0000

fLightLOD1=1000.0000

fSpecularLOD2=550.0

fSpecularLOD1=250.0

fEnvMapLOD2=800.0000

fEnvMapLOD1=500.0000

fEyeEnvMapLOD2=190.0000

fEyeEnvMapLOD1=130.0000

iPresentInterval=1

iShadowFilter=0

iActorShadowCountExt=0

iActorShadowCountInt=0

bActorSelfShadowing=0

bShadowsOnGrass=0

bDynamicWindowReflections=0

iTexMipMapSkip=2

fGrassStartFadeDistance=0.0

fGrassEndDistance=0.0

bDecalsOnSkinnedGeometry=0

bFullBrightLighting=1

iMaxLandscapeTextures=1

bLODPopActors=1

bLODPopItems=1

bLODPopObjects=1



[Controls]

fVersion=1.7000

Forward=0011FFFF

Back=001FFFFF

Slide Left=001EFFFF

Slide Right=0020FFFF

Use=00FF00FF

Activate=0039FFFF

Block=003801FF

Cast=002EFFFF

Ready Item=0021FFFF

Crouch/Sneak=001DFFFF

Run=002AFFFF

Always Run=003AFFFF

Auto Move=0010FFFF

Jump=0012FFFF

Toggle POV=001302FF

Menu Mode=000FFFFF

Rest=0014FFFF

Quick Menu=003BFFFF

Quick1=0002FFFF

Quick2=0003FFFF

Quick3=0004FFFF

Quick4=0005FFFF

Quick5=0006FFFF

Quick6=0007FFFF

Quick7=0008FFFF

Quick8=0009FFFF

QuickSave=003FFFFF

QuickLoad=0043FFFF

Grab=002CFFFF

bInvertYValues=0

fXenonLookXYMult=0.0005

fMouseSensitivity=0.0020

;X=1, Y = 2, Z = 3, XRot = 4, YRot = 5, ZRot = 6

iJoystickMoveFrontBack=2

iJoystickMoveLeftRight=1

fJoystickMoveFBMult=1.0000

fJoystickMoveLRMult=1.0000

iJoystickLookUpDown=6

iJoystickLookLeftRight=3

fJoystickLookUDMult=0.0020

fJoystickLookLRMult=0.0020

fXenonMenuMouseXYMult=0.0003

bBackground Mouse=0

bBackground Keyboard=0

bUse Joystick=0

fXenonLookMult=0.0030

fXenonMenuStickSpeedMaxMod=5.0000

iXenonMenuStickSpeedThreshold=20000

iXenonMenuStickThreshold=1000

;Language values: 0-English, 1-German, 2-French, 3-Spanish, 4-Italian

iLanguage=0



[Water]

fAlpha=0.5000

uSurfaceTextureSize=128

SSurfaceTexture=water

SNearWaterOutdoorID=NearWaterOutdoorLoop

SNearWaterIndoorID=NearWaterIndoorLoop

fNearWaterOutdoorTolerance=1024.0000

fNearWaterIndoorTolerance=512.0000

fNearWaterUnderwaterVolume=0.9000

fNearWaterUnderwaterFreq=0.3000

uNearWaterPoints=8

uNearWaterRadius=1000

uSurfaceFrameCount=32

uSurfaceFPS=12

bUseWaterReflectionsMisc=0

bUseWaterReflectionsStatics=0

bUseWaterReflectionsTrees=0

bUseWaterReflectionsActors=0

bUseWaterReflections=0

bUseWaterHiRes=0

bUseWaterDisplacements=0

bUseWaterShader=0

uDepthRange=125

bUseWaterDepth=1

bUseWaterLOD=1

fTileTextureDivisor=4.7500

fSurfaceTileSize=2048.0000



[Audio]

bDSoundHWAcceleration=1

fMinSoundVel=10.0000

fMetalLargeMassMin=25.0000

fMetalMediumMassMin=8.0000

fStoneLargeMassMin=30.0000

fStoneMediumMassMin=5.0000

fWoodLargeMassMin=15.0000

fWoodMediumMassMin=7.0000

fDialogAttenuationMax=35.0000

fDialogAttenuationMin=7.7500

bUseSoundDebugInfo=1

fUnderwaterFrequencyDelta=0.0000

bUseSoftwareAudio3D=0

fDefaultEffectsVolume=0.8000

fDefaultMusicVolume=0.3000

fDefaultFootVolume=0.8000

fDefaultVoiceVolume=0.8000

fDefaultMasterVolume=1.0000

bMusicEnabled=0

bSoundEnabled=0

fLargeWeaponWeightMin=25.0000

fMediumWeaponWeightMin=8.0000

fSkinLargeMassMin=30.0000

fSkinMediumMassMin=5.0000

fChainLargeMassMin=30.0000

fChainMediumMassMin=5.0000

fDBVoiceAttenuationIn2D=0.0000

iCollisionSoundTimeDelta=50

fGlassLargeMassMin=25.0000

fGlassMediumMassMin=8.0000

fClothLargeMassMin=25.0000

fClothMediumMassMin=8.0000

fEarthLargeMassMin=30.0000

fEarthMediumMassMin=5.0000

bUseSpeedForWeaponSwish=1

fLargeWeaponSpeedMax=0.9500

fMediumWeaponSpeedMax=1.1000

fPlayerFootVolume=0.9000

fDSoundRolloffFactor=4.0000

fMaxFootstepDistance=1100.0000

fHeadroomdB=2.0000

iMaxImpactSoundCount=32

fMainMenuMusicVolume=0.6



[ShockBolt]

bDebug=0

fGlowColorB=1.0000

fGlowColorG=0.6000

fGlowColorR=0.0000

fCoreColorB=1.0000

fCoreColorG=1.0000

fCoreColorR=1.0000

fCastVOffset=-10.0000

iNumBolts=7

fBoltGrowWidth=1.0000

fBoltSmallWidth=3.0000

fTortuosityVariance=8.0000

fSegmentVariance=35.0000

fBoltsRadius=24.0000



[Pathfinding]

bDrawPathsDefault=0

bPathMovementOnly=0

bDrawSmoothFailures=0

bDebugSmoothing=0

bSmoothPaths=1

bSnapToAngle=0

bDebugAvoidance=0

bDisableAvoidance=0

bBackgroundPathing=0



[MAIN]

bEnableBorderRegion=1



[Combat]

bEnableBowZoom=1

bDebugCombatAvoidance=0

fMinBloodDamage=1.0000

fHitVectorDelay=0.4000

iShowHitVector=0



[HAVOK]

bDisablePlayerCollision=0

fJumpAnimDelay=0.75

bTreeTops=0

iSimType=1

bPreventHavokAddAll=0

bPreventHavokAddClutter=0

fMaxTime=0.0167

bHavokDebug=0

fRF=1000.0000

fOD=0.9000

fSE=0.3000

fSD=0.9800

iResetCounter=5

fMoveLimitMass=95.0000

iUpdateType=0

bHavokPick=0



[Interface]

fDlgLookMult=0.3000

fDlgLookAdj=0.0000

fDlgLookDegStop=0.2000

fDlgLookDegStart=2.0000

fDlgFocus=2.1000

fKeyRepeatInterval=50.0000

fKeyRepeatTime=500.0000

fActivatePickSphereRadius=16.0000

fMenuModeAnimBlend=0.0000

iSafeZoneX=20

iSafeZoneY=20

iSafeZoneXWide=20

iSafeZoneYWide=20



[LoadingBar]



[Menu]

fCreditsScrollSpeed=40.0000

iConsoleTextYPos=890

iConsoleTextXPos=30

iConsoleVisibleLines=15

iConsoleHistorySize=50

rDebugTextColor=255,251,233

iConsoleFont=3

iDebugTextFont=3



[GamePlay]

bDisableDynamicCrosshair=0

bSaveOnTravel=1

bSaveOnWait=1

bSaveOnRest=1

bCrossHair=1

iDifficultyLevel=50

bGeneralSubtitles=0

bDialogueSubtitles=1

bInstantLevelUp=0

bHealthBarShowing=0

fHealthBarFadeOutSpeed=1.0000

fHealthBarSpeed=80.0000

fHealthBarHeight=4.0000

fHealthBarWidth=40.0000

fHealthBarEmittanceFadeTime=0.5000

fHealthBarEmittanceTime=1.5000



[Fonts]

SFontFile_1=Data\Fonts\Kingthings_Regular.fnt

SFontFile_2=Data\Fonts\Kingthings_Shadowed.fnt

SFontFile_3=Data\Fonts\Tahoma_Bold_Small.fnt

SFontFile_4=Data\Fonts\Daedric_Font.fnt

SFontFile_5=Data\Fonts\Handwritten.fnt



[SpeedTree]

iTreeClonesAllowed=1

fCanopyShadowGrassMult=1.0000

iCanopyShadowScale=512

fTreeForceMaxBudAngle=-1.0000

fTreeForceMinBudAngle=-1.0000

fTreeForceLeafDimming=-1.0000

fTreeForceBranchDimming=-1.0000

fTreeForceCS=-1.0000

fTreeForceLLA=-1.0000

fTreeLODExponent=1.0000

bEnableTrees=1

bForceFullLOD=0



[Debug]

bDebugFaceGenCriticalSection=0

bDebugFaceGenMultithreading=0

bDebugSaveBuffer=0



[BackgroundLoad]



[LOD]

fLodDistance=500.0000

bUseFaceGenLOD=0

iLODTextureTiling=2

iLODTextureSizePow2=8

fLODNormalTextureBlend=0.5000

bDisplayLODLand=0

bDisplayLODBuildings=0

bDisplayLODTrees=0

bLODPopTrees=0

bLODPopActors=0

bLODPopItems=0

bLODPopObjects=0

fLODFadeOutMultActors=5.0000

fLODFadeOutMultItems=2.0000

fLODFadeOutMultObjects=5.0000

fLODMultLandscape=1.0000

fLODMultTrees=0.2

fLODMultActors=2.0

fLODMultItems=2.0

fLODMultObjects=2.0

iFadeNodeMinNearDistance=400

fLODFadeOutPercent=0.9000

fLODBoundRadiusMult=3.0000

fTalkingDistance=2000.0000

fTreeLODMax=2.0000

fTreeLODMin=0.0200

fTreeLODDefault=1.2000



[Weather]

fSunGlareSize=350.0000

fSunBaseSize=250.0000

bPrecipitation=1

fAlphaReduce=1.0000

SBumpFadeColor=255,255,255,255

SLerpCloseColor=255,255,255,255

SEnvReduceColor=255,255,255,255



[Voice]

SFileTypeLTF=ltf

SFileTypeLip=lip

SFileTypeSource=wav

SFileTypeGame=mp3



[Grass]

iMinGrassSize=80

fGrassEndDistance=3000.0000

fGrassStartFadeDistance=2000.0000

bGrassPointLighting=0

bDrawShaderGrass=1

iGrassDensityEvalSize=2

iMaxGrassTypesPerTexure=2

fWaveOffsetRange=1.7500



[Landscape]

bCurrentCellOnly=0

bPreventSafetyCheck=0

fLandTextureTilingMult=2.0000



[bLightAttenuation]

fQuadraticRadiusMult=1.0000

fLinearRadiusMult=1.0000

bOutQuadInLin=0

fConstantValue=0.0000

fQuadraticValue=16.0000

fLinearValue=3.0000

uQuadraticMethod=2

uLinearMethod=1

fFlickerMovement=8.0000

bUseQuadratic=1

bUseLinear=0

bUseConstant=0



[BlurShaderHDRInterior]

fTargetLUM=1.0000

fUpperLUMClamp=1.0000

fEmissiveHDRMult=1.0000

fEyeAdaptSpeed=0.5000

fBrightScale=2.2500

fBrightClamp=0.2250

fBlurRadius=7.0000

iNumBlurpasses=1



[BlurShaderHDR]

fTargetLUM=1.2000

fUpperLUMClamp=1.0000

fGrassDimmer=1.3000

fTreeDimmer=1.2000

fEmissiveHDRMult=1.0000

fEyeAdaptSpeed=0.7000

fSunlightDimmer=1.3000

fSIEmmisiveMult=1.0000

fSISpecularMult=1.0000

fSkyBrightness=0.5000

fSunBrightness=0.0000

fBrightScale=1.5000

fBrightClamp=0.350

fBlurRadius=4.0000

iNumBlurpasses=2

iBlendType=2

bDoHighDynamicRange=0



[BlurShader]

fSunlightDimmer=1.0000

fSIEmmisiveMult=1.0000

fSISpecularMult=1.0000

fSkyBrightness=0.5000

fSunBrightness=0.0000

fAlphaAddExterior=0.2000

fAlphaAddInterior=0.5000

iBlurTexSize=256

fBlurRadius=0.0300

iNumBlurpasses=1

iBlendType=2

bUseBlurShader=0



[GethitShader]

fBlurAmmount=0.5000

fBlockedTexOffset=0.0010

fHitTexOffset=0.0050



[MESSAGES]

bBlockMessageBoxes=0

bSkipProgramFlows=1

bAllowYesToAll=1

bDisableWarning=1

iFileLogging=0



[DistantLOD]

bUseLODLandData=0

fFadeDistance=12288.0000



[GeneralWarnings]

SGeneralMasterMismatchWarning=One or more plugins could not find the correct versions of the master files they depend on. Errors may occur during load or game play. Check the "Warnings.txt" file for more information.

SMasterMismatchWarning=One of the files that "%s" is dependent on has changed since the last save.

This may result in errors. Saving again will clear this message

but not necessarily fix any errors.



[Archive]

SMasterMiscArchiveFileName=Oblivion - Misc.bsa

SMasterVoicesArchiveFileName2=Oblivion - Voices2.bsa

SMasterVoicesArchiveFileName1=Oblivion - Voices1.bsa

SMasterSoundsArchiveFileName=Oblivion - Sounds.bsa

SMasterTexturesArchiveFileName1=Oblivion - Textures - Compressed.bsa

SMasterMeshesArchiveFileName=Oblivion - Meshes.bsa

SInvalidationFile=ArchiveInvalidation.txt

iRetainFilenameOffsetTable=1

iRetainFilenameStringTable=1

iRetainDirectoryStringTable=1

bCheckRuntimeCollisions=0

bInvalidateOlderFiles=1

bUseArchives=1



[CameraPath]

iTake=0

SDirectoryName=TestCameraPath

iFPS=60

SNif=Test\CameraPath.nif



[Absorb]

fAbsorbGlowColorB=1.0000

fAbsorbGlowColorG=0.6000

fAbsorbGlowColorR=0.0000

fAbsorbCoreColorB=1.0000

fAbsorbCoreColorG=1.0000

fAbsorbCoreColorR=1.0000

iAbsorbNumBolts=1

fAbsorbBoltGrowWidth=0.0000

fAbsorbBoltSmallWidth=7.0000

fAbsorbTortuosityVariance=2.0000

fAbsorbSegmentVariance=7.0000

fAbsorbBoltsRadius=5.0000



[OPENMP]

iThreads=3

iOpenMPLevel=10



[TestAllCells]

bFileShowTextures=1

bFileShowIcons=1

bFileSkipIconChecks=0

bFileTestLoad=0

bFileNeededMessage=1

bFileGoneMessage=1

bFileSkipModelChecks=0



[CopyProtectionStrings]

SCopyProtectionMessage2=Insert the Oblivion Disc.

SCopyProtectionTitle2=Oblivion Disc Not Found

SCopyProtectionMessage=Unable to find a CD-ROM/DVD drive on this computer.

SCopyProtectionTitle=CD-ROM Drive Not Found

bSaveOnInteriorExteriorSwitch=0


```

I used to get it running under cedega when I was using dapper but I had to use Oldblivion which just looks horrid. I ditched that. If I could get this game running decently with wine I'd be ecstatic :lolflag:  lol

---

### Post by ahaslam on 2007-03-19
> **Mongoose said:**
> You have:
bForce1XShaders=1

Should be:
bForce1XShaders=0

You also want to enable SM3:

bAllow30Shaders=0

Also a common setting to disable is refraction shader for the gates, etc.

bUseRefractionShader=0

And finally don't use background loading on everything.  It's very unstable in Windows, and I'd suggest skipping it Wine.  If you see weird phyiscs bugs you have threads dying that shouldn't be as well and may be better off cutting back your thread settings.

This is directed at people that don't read the guide at the wiki or other posts in this thread in general.  ^_^

Read the wiki guide before asking the same questions over and over please.  It's fine you have a valid bug or concern, but if you don't try the guide 100% the first time you play then you're missing the point.  I see a lot of people assume they can do whatever and eventually have to go back to the guide anyway.  If you're not very exp with tweaking the ini or understand the options you should just follow the guide the first time.  Then make changes to customize to your machine after you get it working.  Several people here have been working on tweaks for the ini for quite a while now.  If we tell you to at least do those 5 or 6 settings in the guide there is a reason, and in fact the reason is also written up in the guide itself.

Thank you, greatly appreciated. It now works, no stuttering brightness, no spheres, 'tab' works, it's playable ;)

I'm sorry, I admit that I didn't read all the posts in this thread, but I did read the entire wiki, maybe I missed something.

Thanks again, you're a star :KS

---

### Post by bastiegast on 2007-03-19
> **Mongoose said:**
> The wiki keeps a list of 'known issues' for the current recommended version, which is 0.9.32 atm.  Wine 0.9.33 hasn't been able to be tested as much.  

Mp3 decoding in Oblivion doesn't even work for some Windows installs correctly.  Just a warning before you start adding native DLL overrides.  I'd suggest just disabling for now and getting a free speed boost. 

If you enable SM20 lighting it'll look better than no lighting:

[http://mongooseichiban.blogspot.com/2007/03/update-oblivion-in-wine.html](http://mongooseichiban.blogspot.com/2007/03/update-oblivion-in-wine.html) 

( Image was too big for Ubuntu fourms, however this is an undoctored and full resolution image of how it looks when I play. )

HDR isn't working yet, so you may want to enable bloom for now.  With HDR this game really shines.

As for the 5200 comments: yeah, last I checked you can't use PS1 in Oblivion with Wine w/o a crash.  You're out of luck until that works.

In that post you link to, you claim everything works except for music, certain sound effects and HDR. But what about the water shader? I tried enabling it a few times and it doesn't slow me down to 2 fps anymore(but still gives a huge performance hit) but the water renders far from perfectly. 
Also I still see no background when I press tab for inventory or escape(minor issue, I know), just a green screen, no sepia as its supposed to be. I understand the disappearing trees glitch will be fixed soon?

---

### Post by ahaslam on 2007-03-19
'bAllow30Shaders=1' does nothing for me - RendererInfo.txt shows; '3.0 Shaders: no' which is weird as I have a 7950gt. I assume this is what's causing my 20fps inside, as memory & processor are not fully utilised :-k

Anyone else have this? Any ideas?

PS. my ini is now using only your recommended alterations ;)

---

### Post by dbd on 2007-03-19
> **dyous87 said:**
> Does anyone know if there is anyway I can get this game to run with the ATI Mobility Radeon using the fglrx drivers. 

At the moment it seems that there is a bug in the ATI drivers making it impossible for all of us sufferring the pain of owning ATI cards to play the game I'm afraid. :'(

---

### Post by dyous87 on 2007-03-20
> **dbd said:**
> At the moment it seems that there is a bug in the ATI drivers making it impossible for all of us sufferring the pain of owning ATI cards to play the game I'm afraid. :'(

Soo there is absolutely no way for me to get this working?? That is horrible. I hate ATI!! :(

---

### Post by strycore on 2007-03-20
ok here's my two cents 
The tutorial works pretty well , and I guess the only problem now is a few slowdowns and the static sound.

For the static I strongly suggest that you use a PCI card , at first I tried with the integrated card of my A8N SLI but I had a SB LIVE 5.1 hanging around so i tried it and now it's MUCH better !
Well, I still have static but at least I do have sound , like Mongoose suggests put the effects volume to a low level and it will almost be bearable.

As I might have understood , the static sound is caused by a kinda lag in the sound mixing of wine, so the faster your machine , the less static you should have (that's just a supposition ) 

Now I wonder if a 'Linux mod' for TES4 could be made, a mod that would remove all the buggy stuff like what generates the static ...

Edit : 
I played a bit more , until I closed the first Oblivion Gate , with a correct configuration and Wine 0.9.33 there has been no crash at all . Also , if you have managed to get Oblivion running stable , then don't bother with windowed modes and low resolutions , running the game fullscreen @ 1680x1050 is exactly the same as in windowed mode @ 800x600. I suppose nobody likes to play in a window ;)

I am runnning Oblivion on a pretty standard machine for this game : 
Athlon64 3000+ (no fancy dual core)
1Gb Ram
Geforce 6800 Ultra
and on the software side : Ubuntu Edgy with kernel 2.6.19 and nvidia drivers up to date

---

### Post by UberKnight on 2007-03-20
My setup still doesn't work.  I've followed the howto to the letter.  I can't get past the intro movie when you start a new game (please note, I am not talking about the intro sequence, this has been disabled).  This is after I updated the Nvidia drivers to the latest 1.0-9755 (installed with Envy script).

Previously I could get into a game, though I had a character that was only a head without much of a face.  This was with the Nvidia driver installed with the Automatix script (an older version of the Nvidia driver).  According to the guide, this bug would be resolved when updating to the latest drivers...

Oh, and I won't bother mentioning the static (even with the 25% sound effects volume) or stuttering sound...

If anyone has any suggestions, I'd appreciate it.  I can run the game fine on Windows but would prefer to get it working in Ubuntu so that I can move to the OS more permanently.

---

### Post by ahaslam on 2007-03-20
I am also using the new driver, though it works, things get quite unstable at times & rarely exits properly.
In a previous post (I'm learning), Mongoose mentioned that he was using the 1.0-9746 Nvidia driver.
Tomorrow I'll try that version (there was no improvement in benchmarks after upgrading anyway), I suggest you try the same.

---

### Post by UberKnight on 2007-03-21
Thanks, I'll look into this.  By the way, Mongoose's post that you are referring to is [here]("http://www.ubuntuforums.org/showthread.php?p=2190079&highlight=1.0-9746#post2190079").  Just thought it might help some other people.

Cheers

---

### Post by dyous87 on 2007-03-21
I don't know I keep playing around with the configuration. I've tried different versions of wine and I even tired getting it to run with oldblivion. When ever I launch oblivion i get this output:

```
david@david-laptop:~$ wine /home/david/.wine/drive_c/Program*Files/Bethesda*Softworks/Oblivion/Oblivion.exe
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x11100020) : stub, simulating 128MB for now, returning 128MB left
wine: Unhandled page fault on read access to 0x00000004 at address 0x582454 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000004 in 32-bit code (0x00582454).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00582454 ESP:0033e5d0 EBP:00000000 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000000 ECX:04061692 EDX:ffffffff
 ESI:00000000 EDI:1f001bf4
Stack dump:
0x0033e5d0:  00000000 00000000 1f001bf4 1b000f48
0x0033e5e0:  00000000 00000000 7bc7a4e8 111cd6e8
0x0033e5f0:  00000158 15000a28 7bc36600 0053004c
0x0033e600:  00000000 00360038 7bc29ba4 0046004e
0x0033e610:  003a005f 00000067 7bc3587e 0033e73e
0x0033e620:  0033e758 11100000 7bc28ba1 b7dfdff4
Backtrace:
=>1 0x00582454 in oblivion (+0x182454) (0x00000000)
0x00582454: movl        0x4(%ebp),%edx
Modules:
Module  Address                 Debug info      Name (99 modules)
PE      400000-b73000   Export          oblivion
PE      b80000-dcf000   Deferred        d3dx9_27
PE      18000000-18068000       Deferred        binkw32
ELF     7b800000-7b924000       Deferred        kernel32<elf>
  \-PE  7b820000-7b924000       \               kernel32
ELF     7bc00000-7bc96000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc96000       \               ntdll
ELF     7bd75000-7bdef000       Deferred        libglu.so.1
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf47000-7c000000       Deferred        wined3d<elf>
  \-PE  7bf60000-7c000000       \               wined3d
ELF     7c3b6000-7c3e0000       Deferred        d3d9<elf>
  \-PE  7c3c0000-7c3e0000       \               d3d9
ELF     7c631000-7c646000       Deferred        midimap<elf>
  \-PE  7c640000-7c646000       \               midimap
ELF     7c646000-7c66c000       Deferred        msacm32<elf>
  \-PE  7c650000-7c66c000       \               msacm32
ELF     7c66c000-7c684000       Deferred        msacm32<elf>
  \-PE  7c670000-7c684000       \               msacm32
ELF     7c684000-7c73c000       Deferred        libasound.so.2
ELF     7c73c000-7c767000       Deferred        winealsa<elf>
  \-PE  7c750000-7c767000       \               winealsa
ELF     7c767000-7c7a3000       Deferred        wineoss<elf>
  \-PE  7c770000-7c7a3000       \               wineoss
ELF     7c7a3000-7c7d5000       Deferred        uxtheme<elf>
  \-PE  7c7b0000-7c7d5000       \               uxtheme
ELF     7c7d7000-7c7e0000       Deferred        libxcursor.so.1
ELF     7c7e0000-7c7fd000       Deferred        imm32<elf>
  \-PE  7c7f0000-7c7fd000       \               imm32
ELF     7c7fd000-7c81b000       Deferred        ximcp.so.2
ELF     7d010000-7d015000       Deferred        libxfixes.so.3
ELF     7d015000-7d01d000       Deferred        libxrender.so.1
ELF     7d9ab000-7d9b4000       Deferred        librt.so.1
ELF     7d9b5000-7d9b7000       Deferred        xlcutf8load.so.2
ELF     7d9b7000-7d9ba000       Deferred        libxrandr.so.2
ELF     7d9ba000-7d9bd000       Deferred        libxinerama.so.1
ELF     7da7e000-7e35d000       Deferred        fglrx_dri.so
ELF     7e35d000-7e3fd000       Deferred        libgl.so.1
ELF     7e3fd000-7e402000       Deferred        libxdmcp.so.6
ELF     7e402000-7e4cb000       Deferred        libx11.so.6
ELF     7e4cb000-7e4d8000       Deferred        libxext.so.6
ELF     7e4d8000-7e4f0000       Deferred        libice.so.6
ELF     7e4f0000-7e57e000       Deferred        winex11<elf>
  \-PE  7e500000-7e57e000       \               winex11
ELF     7e57e000-7e59c000       Deferred        libexpat.so.1
ELF     7e59c000-7e5cb000       Deferred        libfontconfig.so.1
ELF     7e5cb000-7e5df000       Deferred        libz.so.1
ELF     7e5df000-7e649000       Deferred        libfreetype.so.6
ELF     7e649000-7e675000       Deferred        ws2_32<elf>
  \-PE  7e650000-7e675000       \               ws2_32
ELF     7e675000-7e68f000       Deferred        wsock32<elf>
  \-PE  7e680000-7e68f000       \               wsock32
ELF     7e68f000-7e6f4000       Deferred        msvcrt<elf>
  \-PE  7e6a0000-7e6f4000       \               msvcrt
ELF     7e6f4000-7e708000       Deferred        lz32<elf>
  \-PE  7e700000-7e708000       \               lz32
ELF     7e708000-7e721000       Deferred        version<elf>
  \-PE  7e710000-7e721000       \               version
ELF     7e721000-7e779000       Deferred        shlwapi<elf>
  \-PE  7e730000-7e779000       \               shlwapi
ELF     7e779000-7e86d000       Deferred        shell32<elf>
  \-PE  7e790000-7e86d000       \               shell32
ELF     7e86d000-7e8b6000       Deferred        dsound<elf>
  \-PE  7e880000-7e8b6000       \               dsound
ELF     7e8b6000-7e944000       Deferred        winmm<elf>
  \-PE  7e8c0000-7e944000       \               winmm
ELF     7e944000-7e957000       Deferred        libresolv.so.2
ELF     7e957000-7e975000       Deferred        iphlpapi<elf>
  \-PE  7e960000-7e975000       \               iphlpapi
ELF     7e975000-7e9ca000       Deferred        rpcrt4<elf>
  \-PE  7e980000-7e9ca000       \               rpcrt4
ELF     7e9ca000-7ea63000       Deferred        ole32<elf>
  \-PE  7e9e0000-7ea63000       \               ole32
ELF     7ea63000-7ea99000       Deferred        dinput<elf>
  \-PE  7ea70000-7ea99000       \               dinput
ELF     7ea99000-7eab2000       Deferred        dinput8<elf>
  \-PE  7eaa0000-7eab2000       \               dinput8
ELF     7eab2000-7eaf7000       Deferred        advapi32<elf>
  \-PE  7eac0000-7eaf7000       \               advapi32
ELF     7eaf7000-7eb02000       Deferred        libgcc_s.so.1
ELF     7eb06000-7eb09000       Deferred        libxau.so.6
ELF     7eb09000-7eb12000       Deferred        libsm.so.6
ELF     7ebf1000-7eca9000       Deferred        gdi32<elf>
  \-PE  7ec10000-7eca9000       \               gdi32
ELF     7eca9000-7ede3000       Deferred        user32<elf>
  \-PE  7ecc0000-7ede3000       \               user32
ELF     7ede3000-7ee9f000       Deferred        comctl32<elf>
  \-PE  7edf0000-7ee9f000       \               comctl32
ELF     7efa9000-7efb4000       Deferred        libnss_files.so.2
ELF     7efb4000-7efca000       Deferred        libnsl.so.1
ELF     7efca000-7eff0000       Deferred        libm.so.6
ELF     7eff0000-7eff5000       Deferred        libxxf86vm.so.1
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7cc0000-b7cc9000       Deferred        libnss_compat.so.2
ELF     b7cca000-b7cce000       Deferred        libdl.so.2
ELF     b7cce000-b7e02000       Deferred        libc.so.6
ELF     b7e03000-b7e16000       Deferred        libpthread.so.0
ELF     b7e26000-b7f37000       Deferred        libwine.so.1
ELF     b7f39000-b7f54000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Bethesda Softworks\Oblivion\Oblivion.exe
        00000011   -1
        00000010   -1
        0000000f   15
        0000000e   15
        0000000d    0
        00000009    0 <==
david@david-laptop:~$ 

```

there has to be a way to get this to work! :confused:

---

### Post by Mongoose on 2007-03-21
Yeah, I don't mention performance issues that don't affect all hardware.  For example it's not slow on 8xxx and ATi cards crash even if you force PS1 iirc.  There is a minor issue with speedtree sometimes showing enlarged instanced billboards of trees, but I never heard of anyone else seeing it.  You say the speedtree bug is different for you it seems.   You may have to alter your ini for menu backgrounds in the mean time -- just disable the static backgrounds.  You might want to file a bug on that, since it appears I forgot how it's supposed to work.  Now that you mention it I vaguely remember the effect on menu backgrounds.   Also it seems the fix for sneak cursor broke life detect effect.

Ati users: Try disabling PS2 lighting, set goballightmodel on, and force PS1 option on with pbuffer and if that fails try fbo.  I think it would "work", but it would likely crash if you load your menu or go outside.  If this is the case you can file a bug on PS1 support in Wine legitamately, however PS2 can't be used until ATi fixes their drivers.  The best solution I can offer is to get an Nvidia GPU if possible.  It would solve your problems the quickest at the cost of treasure, and getting ATi to fix drivers might cost of blood.  ;) 

SM30 issue:  Likely a Wine level of support issue.

Movie issue: You can disable that movie in the ini too, however it works for everyone else just fine.  The skinning bug aka 'eyes and mouth' is caused by having older drivers.  I don't know about 1.0-9755, but that should be fine.  If you're stumped try downgrading to 1.0-9746, but first make sure your OpenGL is functioning properly.

dyous87: Make sure you disable the intro movie as suggested in the guide.  That's typically where it 'pops'.

---

### Post by xopher on 2007-03-21
Thank's for the great how to/tutorial :)

Ok, now that that's out of the way, I got Oblivion running, it runs nicely, graphically great. My only problem (as it seems) is the static noise. Haven't read about a fix for it yet? Isn't there one? For me, as Im a headphone user, the static is unbearable..

Im running Feisty, a64 3800+, 2048MB RAM, NVIDIA GF6800 [256MB], and the default drivers (96.31). My soundcard is an oldish Audigy1.

Hope this gets resolved soon, can't wait to play Oblivion for REAL ;) Haven't had windows installed for a long time now, so I almost gave up hope completely at one point.

Oh, and Im running the latest update of Oblivion on wine 0.9.33, with the settings recommended in the tutorial, Ive tried playing around with the sound settings, and the static still persists.

---

### Post by golem3 on 2007-03-21
Are you serious? 20-30fps under WINE??? AMazing...I need to try this out!

---

### Post by ahaslam on 2007-03-21
I have noticed something that was mentioned earlier in this thread which was not commented about & I have the same concern.

When initially choosing your video options from the first screen & clicking 'reset to defaults' I get the message: 'video hardware unrecognised' and the medium settings are chosen with a low resolution. This may seem insignificant when you can simply select the desired visual levels, but I'm led to believe that it disables some features (like 3.0 shaders) & causes huge slowdowns.

I have read forum posts from windows users with high end 7 series cards & the new 8 series cards, where they get less performance than what their previous mid range 6 series cards offered. The usual suggestion is to update directx & then nothing further is heard, so whether it works or not, who knows? 

This made me think about the d3dx9_27.dll & upgrading it, which I did, to version 33 but I had no luck. I'm assuming it's a wine thing & that it's probably going to be the thing that solves many issues.

**So to those of you with speed/stability issues, is your card supported? Of course the same question also goes to those who are experiencing good frame rates & stability.**

My system specs:

Intel Core 2 Duo E6300 OC'd to 2800MHz
BFG 7950GT 512MB OC'd to near 7900GTX specs (650/1550)
Corsair 2x512MB (dual channel) DDR2-5400 C4 OC'd to 800MHz

---

### Post by Mongoose on 2007-03-21
The static is caused by the audio mixing for just one type of sound in game.  If you look at audio options you'll see 4 sliders.  You can slide the effects down to 0 if static bothers you ( with headphones I can see that being unavoidable without post filtering ).  You still hear hit sounds footsteps, speech, etc.  The game is very playable like this since it really only disables sounds like spell casting, rocks falling, etc.  Ambient life sound seems to mix with voice btw, so it's fine too.

The music is a directshow issue, which is altogether different.  There are unoffical patches for directshow already, however merging them may not be so easy or possible due to recent changes in the source tree.  If you're interested in helping development visit [http://winehq.org](http://winehq.org) and have at it -- even if it's just testing and debugging patches.

---

### Post by dyous87 on 2007-03-22
Ok I've uninstalled everything, my fglrx drivers, wine and Oblivion and then i reinstalled following the directions on the wiki again. This time i get closer. I get to the loading screen which just hangs and crashes. I've tried everything. I tried putting different options in the xorg.config. I even tried loading dx9 and dx3d dll's off windows xp. I've also tried different options in the registry including fbo, pbuffer or backbuffer. None of them give me a different result. I have heard that some people, not on this forum were able to get this to work with the fglrx drivers but so far I have been unsuccessful.
When I try to run Oblivion wine still gives me this output:

```
david@david-laptop:~$ wine /media/cdrom0/OblivionLauncher.exe
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,35,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,70,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,105,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,140,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,175,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,210,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,245,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,255,2): stub!
david@david-laptop:~$ fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x110e0020) : stub, simulating 128MB for now, returning 128MB left
wine: Unhandled page fault on read access to 0x00000130 at address 0x7decf848 (thread 0010), starting debugger...
Unhandled exception: page fault on read access to 0x00000130 in 32-bit code (0x7decf848).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7decf848 ESP:0034f260 EBP:0034f268 EFLAGS:00210206(   - 00      - RIP1)
 EAX:00000000 EBX:7e322c00 ECX:7e357224 EDX:00000000
 ESI:00000010 EDI:7e322c00
Stack dump:
0x0034f260:  0141656c 00000000 0034f298 7de246d5
0x0034f270:  7e322c00 7bd28080 7b8ab8e0 b7de3eb6
0x0034f280:  0034f440 00000013 7e323aa0 00000001
0x0034f290:  7e329204 7e322c00 0034f388 7de2631a
0x0034f2a0:  7e322c00 00000000 00000000 00687365
0x0034f2b0:  7bc7a4e8 0034f3f4 0034f41c 0034f35c
Backtrace:
=>1 0x7decf848 __glBuffersHWRenderable+0x58() in fglrx_dri.so (0x0034f268)
  2 0x7de246d5 __R300TCLPunt+0x545() in fglrx_dri.so (0x0034f298)
  3 0x7de2631a __R300TCLValidate+0x40a() in fglrx_dri.so (0x0034f388)
  4 0x7de183b9 __R300TCLFFXValidate+0x429() in fglrx_dri.so (0x0034f438)
  5 0x7deab09e __glim_Clear+0x31e() in fglrx_dri.so (0x0034f458)
  6 0x7e3cb718 in libgl.so.1 (+0x67718) (0x0034f468)
  7 0x7bf4914e in wined3d (+0x1914e) (0x0034f4e8)
  8 0x7bfeca45 in d3d9 (+0xca45) (0x0034f518)
  9 0x006c99fd in oblivion (+0x2c99fd) (0x15000564)
  10 0x00000001 (0x00a37718)
  11 0x006d1fe0 in oblivion (+0x2d1fe0) (0x006d29e0)
0x7decf848 __glBuffersHWRenderable+0x58 in fglrx_dri.so: testb  $0x1,0x130(%edx)
Modules:
Module  Address                 Debug info      Name (99 modules)
PE      400000-b59000   Export          oblivion
PE      b60000-daf000   Deferred        d3dx9_27
PE      18000000-18068000       Deferred        binkw32
ELF     7b800000-7b924000       Deferred        kernel32<elf>
  \-PE  7b820000-7b924000       \               kernel32
ELF     7bc00000-7bc96000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc96000       \               ntdll
ELF     7bd75000-7bdef000       Deferred        libglu.so.1
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf1d000-7bfd6000       Export          wined3d<elf>
  \-PE  7bf30000-7bfd6000       \               wined3d
ELF     7bfd6000-7c000000       Export          d3d9<elf>
  \-PE  7bfe0000-7c000000       \               d3d9
ELF     7c638000-7c64d000       Deferred        midimap<elf>
  \-PE  7c640000-7c64d000       \               midimap
ELF     7c64d000-7c673000       Deferred        msacm32<elf>
  \-PE  7c650000-7c673000       \               msacm32
ELF     7c673000-7c68b000       Deferred        msacm32<elf>
  \-PE  7c680000-7c68b000       \               msacm32
ELF     7c68b000-7c6c7000       Deferred        wineoss<elf>
  \-PE  7c690000-7c6c7000       \               wineoss
ELF     7c6c7000-7c77f000       Deferred        libasound.so.2
ELF     7c77f000-7c7aa000       Deferred        winealsa<elf>
  \-PE  7c790000-7c7aa000       \               winealsa
ELF     7c7aa000-7c7dc000       Deferred        uxtheme<elf>
  \-PE  7c7b0000-7c7dc000       \               uxtheme
ELF     7c7de000-7c7e7000       Deferred        libxcursor.so.1
ELF     7c7e7000-7c804000       Deferred        imm32<elf>
  \-PE  7c7f0000-7c804000       \               imm32
ELF     7c804000-7c822000       Deferred        ximcp.so.2
ELF     7d017000-7d01c000       Deferred        libxfixes.so.3
ELF     7d01c000-7d024000       Deferred        libxrender.so.1
ELF     7d9b2000-7d9bb000       Deferred        librt.so.1
ELF     7d9bc000-7d9be000       Deferred        xlcutf8load.so.2
ELF     7d9be000-7d9c1000       Deferred        libxrandr.so.2
ELF     7d9c1000-7d9c4000       Deferred        libxinerama.so.1
ELF     7da85000-7e364000       Export          fglrx_dri.so
ELF     7e364000-7e404000       Export          libgl.so.1
ELF     7e404000-7e4cd000       Deferred        libx11.so.6
ELF     7e4cd000-7e4da000       Deferred        libxext.so.6
ELF     7e4da000-7e4f2000       Deferred        libice.so.6
ELF     7e4f2000-7e580000       Deferred        winex11<elf>
  \-PE  7e500000-7e580000       \               winex11
ELF     7e580000-7e59e000       Deferred        libexpat.so.1
ELF     7e59e000-7e5cd000       Deferred        libfontconfig.so.1
ELF     7e5cd000-7e5e1000       Deferred        libz.so.1
ELF     7e5e1000-7e64b000       Deferred        libfreetype.so.6
ELF     7e64b000-7e677000       Deferred        ws2_32<elf>
  \-PE  7e650000-7e677000       \               ws2_32
ELF     7e677000-7e691000       Deferred        wsock32<elf>
  \-PE  7e680000-7e691000       \               wsock32
ELF     7e691000-7e6f6000       Deferred        msvcrt<elf>
  \-PE  7e6a0000-7e6f6000       \               msvcrt
ELF     7e6f6000-7e70a000       Deferred        lz32<elf>
  \-PE  7e700000-7e70a000       \               lz32
ELF     7e70a000-7e723000       Deferred        version<elf>
  \-PE  7e710000-7e723000       \               version
ELF     7e723000-7e77b000       Deferred        shlwapi<elf>
  \-PE  7e730000-7e77b000       \               shlwapi
ELF     7e77b000-7e86f000       Deferred        shell32<elf>
  \-PE  7e790000-7e86f000       \               shell32
ELF     7e86f000-7e8b8000       Deferred        dsound<elf>
  \-PE  7e880000-7e8b8000       \               dsound
ELF     7e8b8000-7e946000       Deferred        winmm<elf>
  \-PE  7e8c0000-7e946000       \               winmm
ELF     7e946000-7e959000       Deferred        libresolv.so.2
ELF     7e959000-7e977000       Deferred        iphlpapi<elf>
  \-PE  7e960000-7e977000       \               iphlpapi
ELF     7e977000-7e9cc000       Deferred        rpcrt4<elf>
  \-PE  7e980000-7e9cc000       \               rpcrt4
ELF     7e9cc000-7ea65000       Deferred        ole32<elf>
  \-PE  7e9e0000-7ea65000       \               ole32
ELF     7ea65000-7ea9b000       Deferred        dinput<elf>
  \-PE  7ea70000-7ea9b000       \               dinput
ELF     7ea9b000-7eab4000       Deferred        dinput8<elf>
  \-PE  7eaa0000-7eab4000       \               dinput8
ELF     7eab4000-7eaf9000       Deferred        advapi32<elf>
  \-PE  7eac0000-7eaf9000       \               advapi32
ELF     7eaf9000-7eb04000       Deferred        libgcc_s.so.1
ELF     7ebe3000-7ec9b000       Deferred        gdi32<elf>
  \-PE  7ec00000-7ec9b000       \               gdi32
ELF     7ec9b000-7edd5000       Deferred        user32<elf>
  \-PE  7ecc0000-7edd5000       \               user32
ELF     7edd5000-7ee91000       Deferred        comctl32<elf>
  \-PE  7ede0000-7ee91000       \               comctl32
ELF     7ee91000-7eea7000       Deferred        libnsl.so.1
ELF     7eea7000-7eeb0000       Deferred        libnss_compat.so.2
ELF     7eeb2000-7eeb7000       Deferred        libxdmcp.so.6
ELF     7eeb7000-7eec0000       Deferred        libsm.so.6
ELF     7efca000-7eff0000       Deferred        libm.so.6
ELF     7eff0000-7eff5000       Deferred        libxxf86vm.so.1
ELF     7eff5000-7f000000       Deferred        libnss_files.so.2
ELF     b7d51000-b7d54000       Deferred        libxau.so.6
ELF     b7d54000-b7d5e000       Deferred        libnss_nis.so.2
ELF     b7d60000-b7d64000       Deferred        libdl.so.2
ELF     b7d64000-b7e98000       Deferred        libc.so.6
ELF     b7e99000-b7eac000       Deferred        libpthread.so.0
ELF     b7ebc000-b7fcd000       Deferred        libwine.so.1
ELF     b7fcf000-b7fea000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000f (D) C:\Program Files\Bethesda Softworks\Oblivion\Oblivion.exe
        00000015   -1
        00000014   -1
        00000013   15
        00000012   15
        00000011    0
        00000010    0 <==
0000000b 
        0000000e    0
        0000000c    0

```

[Here]("http://storm.cis.fordham.edu/~youssef/oblivion_fail.png") is an image of the only thing I can get to show up without it hanging then crashing.

---

### Post by ahaslam on 2007-03-22
OK, I've been informed that 'unrecognised' hardware *shouldn't* cause a problem, it just seems a coincidence.

Regarding the hang upon exiting the game, I get the following in the output:
> wine: Unhandled page fault on read access to 0x0000000c at address 0xb7d918d2 (thread 0010), starting debugger...
err:ntdll:RtlpWaitForCriticalSection section 0x7efecfa4 "loader.c: loader_section" wait timed out in thread 0015, blocked by 0010, retrying (60 sec)
... and it never quits, or even re-attempts, it has to be killed.

Back to performance, I tried out 'Oldblivion' & noticed no visual, performance or stability difference (other than water, as it didn't use the custom texture). This makes me wonder whether it's even utilising the 2.0 shaders. Enabling/disabling SM20 lighting also shows no differences.

Any suggestions would be greatly appreciated ;)

---

### Post by dbd on 2007-03-22
> **dyous87 said:**
> Ok I've uninstalled everything, my fglrx drivers, wine and Oblivion and then i reinstalled following the directions on the wiki again. This time i get closer. I get to the loading screen which just hangs and crashes.

Thats exactly how far I managed to get when I hit the crash that was apparently an ATI driver problem. Where is this forum thread where people have got it to work with ATI?

---

### Post by dyous87 on 2007-03-22
> **dbd said:**
> Thats exactly how far I managed to get when I hit the crash that was apparently an ATI driver problem. Where is this forum thread where people have got it to work with ATI?

I don't remember where I got it but I did read somewhere that someone had managed to get further with the fglrx drivers. I don't know. The annoying this is when I was using dapper I used to play fine with oldblivion using cedega. I don't however want to use cedega or oldblivion. There has to be something we could do. Some kind of configuration one of us hasn't tried yet. I've been googling for the answer but no luck. 

Of course if I end up getting it working I will post how. Please do the same. We could ge tthis working lol. Don't give up!

[Edit]: I found where I read about someone getting it working. This guy hlord running Suse has appeared to get Oblivion running on wine with the fglrx drivers using version 
9.11. 
[http://appdb.winehq.org/appview.php?iVersionId=4596](http://appdb.winehq.org/appview.php?iVersionId=4596)

He is running it in windows 2000 mode. I have tried running it in windows 2000 mode but have not been able to replicate his results. I am not running wine 9.11 however and I was trying it on the newest release of course with no luck.

---

### Post by dyous87 on 2007-03-23
I just tested it out with wine version.0.9.12 and it loaded up to the main menu
The game was ridiculously slow however and unplayable. I was able to load a new game and it didn't crash. It seems that the new versions of wine ie: 0.9.29-0.9.33 have some kind of confliction  with the fglrx drivers which is quite annoying cause only the new versions of wine seem to run oblivion to the point where it is actually playable.

---

### Post by Mongoose on 2007-03-23
The "problem" is newer versions of Wine support more shaders.  As I tried to explain to someone else in this thread earlier the problem lays at the feet of the ATi drivers failure.  If you debug the application you'll notice FBO / PS operations 'crashing' inside the ATi driver itself.  It's not the Wine developer's fault.

I've already mentioned some possible ways to get around this ( basically disabling combinations of shaders ).  It'll likely be a trail and error to find a path that "works".  As I mentioned before at some point you're not playing Oblivion anymore when you have to disable almost all graphics.

0.9.33 issues: I haven't had time to look at that build at all.  I'm working on a super secret project right now, and I have little time for helping with Wine stuff.

---

### Post by dyous87 on 2007-03-23
Yes I understand that. But anyway I've been playing around with previous versions of wine just to see what happens. I installed .0.9.24 and it seems to get the menu and load to a new game where it just keeps crashing on me. The first time I was able to actually get the the character creation to. Hmm anyway I guess for now us fglrx users are going to have to wait till ATI decides to release proper drivers. I'm going to continue playing around with 0.9.24 just to see what I can do.

[Edit]: I just set vertex shaders in winecfg from hardware to emulated and now it doesn't crash anymore.  This is a feature that I noticed is not in the new releases of wine. Is there any reason for that, and if it was included would it perhaps allow us to run it on the new wine releases? I just found ti curious.

---

### Post by ahaslam on 2007-03-23
Is there anywhere where I can report my exit bug: [http://www.ubuntuforums.org/showpost.php?p=2338140&postcount=160](http://www.ubuntuforums.org/showpost.php?p=2338140&postcount=160) or is it already known?

& is there a way to verify what shaders are in use?

I'm going on holiday tomorrow & I would like to set the ball rolling before I leave.

Tony ;)

---

### Post by ahaslam on 2007-03-23
HDR works with the current wine release, see my screenshots attached :)
This does have a huge performance hit & it still shows no 3.0 shaders :-k
This also solves the black background when you have the journal open ;)

Here's a how-to: [http://www.bethsoft.com/bgsforums/index.php?act=ST&f=23&t=517690&st=0](http://www.bethsoft.com/bgsforums/index.php?act=ST&f=23&t=517690&st=0)

& here's the screens:

---

### Post by bastiegast on 2007-03-23
The howto you link to is for windows? Mind giving a little more information? I just wanted to test if HDR works with latest git-wine only to find it was disabled because it's "not supported". Previous wine releases I could just enable HDR(i would still get a black screen but at least the option was enabled.).

---

### Post by ahaslam on 2007-03-23
Just follow the guide & it should work using Wine 0.9.33.

---

### Post by kroenecker on 2007-03-24
Wow it works but it's incredibly slow.

---

### Post by Mongoose on 2007-03-29
New patch has been released.  Several crash fixes, bug fixes, quest fixes, and improvements like LoD terrian update.  I haven't had time to test this myself, but it should be fine.

Release notes:
[http://www.elderscrolls.com/downloads/updates_patchnotes6.htm](http://www.elderscrolls.com/downloads/updates_patchnotes6.htm)

Patch:
[http://www.elderscrolls.com/downloads/updates_patches.htm](http://www.elderscrolls.com/downloads/updates_patches.htm)

---

### Post by xopher on 2007-03-29
Thanks for the information :) Going to try it out.

Edit: And it works just fine.

---

### Post by bastiegast on 2007-03-30
Tony,
Yeah it works :) but slows me down to 8 fps so ill play just with bloom for now.
However since I followed that guide I started getting black skies I tried downgrading GIT --> .33 Same, .33 --> .32 again the same, I have but when I turn HDR on the sky renders properly, is there any way to restore the changes I made to make HDR work? Or is this problem related to something else?

Edit: Never mind, of course I created a backup of the changed file, changed it back and the sky was blue again :), still I upgraded to the new patch and now I'm seeing messed up (partly purple) ground textures :S

---

### Post by Mongoose on 2007-03-30
That's likely from the new terrian LoD system.  I guess they have 'land shaders' now, which I didn't expect...  I would have thought they'd just use detail textures for it.  I'll try the patch this weekend and see what else is going on.  ^_^

---

### Post by Cappy on 2007-03-30
"Fixed infinite dialogue loop when arrested by guards who have high disposition to you."

Aha .. I got stuck in that .. the guards were telling me "Since it's your first time I'll let you go but don't let me catch you again!" and then they kept saying it over and over T_T

---

### Post by Mongoose on 2007-03-31
The LoD fixes look pretty good compared to the crap they used to be.  I do get rare crashes, but it seems to be related to time played and the amount of threads used.   The shader paks seem to have been updated too, or the detection routine is working better.

---

### Post by ahaslam on 2007-04-03
How do you guys put up with the spriting trees & grass?
It drives me crazy :mad:

---

### Post by bastiegast on 2007-04-03
> **Anthony Haslam said:**
> How do you guys put up with the spriting trees & grass?
It drives me crazy :mad:

Yup, drives me crazy too, especially so because before wine .32 it worked just fine

---

### Post by Mongoose on 2007-04-03
It seems to affect everyone slightly differently.  It's clearly speedtree impostors being drawn with incorrect transforms.  I put it under known issues on the wiki some time ago...  that said for me it 's not that pronounced for some reason.  Sometimes I see one billboarded tree scaled very large, but it's often so far off it doesn't bother me.  It doesn't always appear either, which is mostly due to time of day and weather effects.

---

### Post by ahaslam on 2007-04-04
> **bastiegast said:**
> Yup, drives me crazy too, especially so because before wine .32 it worked just fine
Are the developers aware (I can't find it on Bugzilla)?

---

### Post by Mongoose on 2007-04-04
I dropped off testing Wine / Oblivion for a bit as I mentioned before.  I mentioned it in passing, but never filed a bug myself.  I haven't even looked at the wiki since the 1.2 patch update -- it might have bad information on it by now hah.

---

### Post by bastiegast on 2007-04-04
Too bad, your a genius! :guitar:  you really had an answer for everything, makes me very curious what kind of "super secret" project your working on :p

---

### Post by Corvias on 2007-04-04
Please Help! I've been trying to get Oblivion to work for a week now and I can't get it going. Here are the facts, and a dump from the terminal

- PC: Athlon64 X2, 2GB ram, Nvidia 7800GT
- Ubuntu Edgy
- Wine .9.34
- Followed the howto on uesp
- Crash occurs right after the initial loading screen
- Yes, I disabled the intro movies, created the Direct3D key, and added the string values.
- Using 1.2 patch and Nights of the Nine
- Beryl is not running
- Below is terminal dump, and my oblivion.ini is attached. (renamed to .txt to allow upload).

Thank You In Advance! If you need more info, just let me know

```
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R32F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D32
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D15S1
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D24X4S4
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D32F_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D24FS8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A32B32G32R32F and WINED3DFMT_D16
fixme:d3d:IWineD3DDeviceImpl_SetMultithreaded No thread safety in wined3d yet
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1d5bb0) : stub, simulating 64MB for now, returning 64MB left
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {71985f4b-1ca1-11d3-9cc8-00c04f7971e0} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {a2e3074f-6c3d-11d3-b653-00c04f79498e} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {71985f4b-1ca1-11d3-9cc8-00c04f7971e0} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {a2e3074f-6c3d-11d3-b653-00c04f79498e} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:quartz:AcceptProcAFR (0x11459810, 0x11781058)
wine: Unhandled page fault on read access to 0x00000000 at address 0x144620b5 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x144620b5).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:144620b5 ESP:0033ea08 EBP:0033ea30 EFLAGS:00010202(   - 00      - -RI1)
 EAX:00000000 EBX:11671018 ECX:11670db8 EDX:11780eb8
 ESI:00000001 EDI:11780fb8
Stack dump:
0x0033ea08:  11780fb8 116710b0 7bc2855f 11780eb4
0x0033ea18:  11780eb4 0033ea5c 14412b0b 11780eb4
0x0033ea28:  116710b0 11671018 0033ea5c 14412904
0x0033ea38:  117810c0 0033ea4c 11780f2c 11671018
0x0033ea48:  00000000 00000000 00000000 00000001
0x0033ea58:  00000000 0033eaac 1441283f 11780fb8
Backtrace:
=>1 0x144620b5 in qedit (+0x620b5) (0x0033ea30)
  2 0x14412904 in qedit (+0x12904) (0x0033ea5c)
  3 0x1441283f in qedit (+0x1283f) (0x0033eaac)
  4 0x14414125 in qedit (+0x14125) (0x0033ead8)
  5 0x144145d7 in qedit (+0x145d7) (0x0033eaf0)
  6 0x7b9d275e in quartz (+0x2275e) (0x0033ed00)
  7 0x7b9d25a4 in quartz (+0x225a4) (0x0033eed0)
  8 0x7b9d1272 in quartz (+0x21272) (0x0033f010)
  9 0x006aad66 in oblivion (+0x2aad66) (0x00000008)
  10 0x00000000 (0x00000000)
0x144620b5: movl        0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (118 modules)
PE      400000-baf000   Export          oblivion
PE      bb0000-dff000   Deferred        d3dx9_27
PE      14400000-145b9000       Export          qedit
PE      18000000-18068000       Deferred        binkw32
ELF     7b512000-7b560000       Deferred        libgcrypt.so.11
ELF     7b560000-7b600000       Deferred        comdlg32<elf>
  \-PE  7b570000-7b600000       \               comdlg32
ELF     7b739000-7b767000       Deferred        libcrypt.so.1
ELF     7b767000-7b800000       Deferred        oleaut32<elf>
  \-PE  7b780000-7b800000       \               oleaut32
ELF     7b800000-7b924000       Deferred        kernel32<elf>
  \-PE  7b820000-7b924000       \               kernel32
ELF     7b937000-7b9a6000       Deferred        libgnutls.so.13
ELF     7b9a6000-7b9ff000       Export          quartz<elf>
  \-PE  7b9b0000-7b9ff000       \               quartz
ELF     7bc00000-7bc95000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc95000       \               ntdll
ELF     7bcaa000-7bcbd000       Deferred        libtasn1.so.3
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf27000-7bf56000       Deferred        libcups.so.2
ELF     7bf9b000-7bfcd000       Deferred        winspool<elf>
  \-PE  7bfa0000-7bfcd000       \               winspool
ELF     7bfcd000-7bfe1000       Deferred        avicap32<elf>
  \-PE  7bfd0000-7bfe1000       \               avicap32
ELF     7bfe1000-7c000000       Deferred        devenum<elf>
  \-PE  7bff0000-7c000000       \               devenum
ELF     7c272000-7c276000       Deferred        libgpg-error.so.0
ELF     7c885000-7c8ff000       Deferred        libglu.so.1
ELF     7c8ff000-7c9b9000       Deferred        wined3d<elf>
  \-PE  7c910000-7c9b9000       \               wined3d
ELF     7caf4000-7cb1b000       Deferred        msvfw32<elf>
  \-PE  7cb00000-7cb1b000       \               msvfw32
ELF     7cb1f000-7cb49000       Deferred        d3d9<elf>
  \-PE  7cb30000-7cb49000       \               d3d9
ELF     7cd64000-7cd79000       Deferred        midimap<elf>
  \-PE  7cd70000-7cd79000       \               midimap
ELF     7cd79000-7cd9f000       Deferred        msacm32<elf>
  \-PE  7cd80000-7cd9f000       \               msacm32
ELF     7cd9f000-7ce57000       Deferred        libasound.so.2
ELF     7ce57000-7ce82000       Deferred        winealsa<elf>
  \-PE  7ce60000-7ce82000       \               winealsa
ELF     7ce82000-7ceb4000       Deferred        uxtheme<elf>
  \-PE  7ce90000-7ceb4000       \               uxtheme
ELF     7d14f000-7d167000       Deferred        msacm32<elf>
  \-PE  7d160000-7d167000       \               msacm32
ELF     7d169000-7d16e000       Deferred        libxfixes.so.3
ELF     7d16e000-7d177000       Deferred        libxcursor.so.1
ELF     7d177000-7d194000       Deferred        imm32<elf>
  \-PE  7d180000-7d194000       \               imm32
ELF     7d1bc000-7d1da000       Deferred        ximcp.so.2
ELF     7d1da000-7d1dc000       Deferred        xlcutf8load.so.2
ELF     7d1dc000-7d1df000       Deferred        libxrandr.so.2
ELF     7d1df000-7d1e7000       Deferred        libxrender.so.1
ELF     7d1e7000-7d1ea000       Deferred        libxinerama.so.1
ELF     7d9ef000-7d9f1000       Deferred        libnvidia-tls.so.1
ELF     7d9f1000-7e363000       Deferred        libglcore.so.1
ELF     7e363000-7e3f7000       Deferred        libgl.so.1
ELF     7e3f7000-7e3fc000       Deferred        libxdmcp.so.6
ELF     7e3fc000-7e4c5000       Deferred        libx11.so.6
ELF     7e4c5000-7e4d2000       Deferred        libxext.so.6
ELF     7e4d2000-7e4d7000       Deferred        libxxf86vm.so.1
ELF     7e4d7000-7e4ef000       Deferred        libice.so.6
ELF     7e4ef000-7e57e000       Deferred        winex11<elf>
  \-PE  7e500000-7e57e000       \               winex11
ELF     7e57e000-7e59c000       Deferred        libexpat.so.1
ELF     7e59c000-7e5cb000       Deferred        libfontconfig.so.1
ELF     7e5cb000-7e5df000       Deferred        libz.so.1
ELF     7e5df000-7e64c000       Deferred        libfreetype.so.6
ELF     7e64c000-7e6b1000       Deferred        msvcrt<elf>
  \-PE  7e660000-7e6b1000       \               msvcrt
ELF     7e6b1000-7e6dd000       Deferred        ws2_32<elf>
  \-PE  7e6c0000-7e6dd000       \               ws2_32
ELF     7e6dd000-7e6f7000       Deferred        wsock32<elf>
  \-PE  7e6e0000-7e6f7000       \               wsock32
ELF     7e6f7000-7e710000       Deferred        version<elf>
  \-PE  7e700000-7e710000       \               version
ELF     7e710000-7e768000       Deferred        shlwapi<elf>
  \-PE  7e720000-7e768000       \               shlwapi
ELF     7e768000-7e862000       Deferred        shell32<elf>
  \-PE  7e780000-7e862000       \               shell32
ELF     7e862000-7e8ab000       Deferred        dsound<elf>
  \-PE  7e870000-7e8ab000       \               dsound
ELF     7e8ab000-7e939000       Deferred        winmm<elf>
  \-PE  7e8c0000-7e939000       \               winmm
ELF     7e939000-7e94c000       Deferred        libresolv.so.2
ELF     7e94c000-7e96a000       Deferred        iphlpapi<elf>
  \-PE  7e950000-7e96a000       \               iphlpapi
ELF     7e96a000-7e9bf000       Deferred        rpcrt4<elf>
  \-PE  7e980000-7e9bf000       \               rpcrt4
ELF     7e9bf000-7ea5a000       Deferred        ole32<elf>
  \-PE  7e9d0000-7ea5a000       \               ole32
ELF     7ea5a000-7ea90000       Deferred        dinput<elf>
  \-PE  7ea60000-7ea90000       \               dinput
ELF     7ea90000-7eaa9000       Deferred        dinput8<elf>
  \-PE  7eaa0000-7eaa9000       \               dinput8
ELF     7eaa9000-7eaee000       Deferred        advapi32<elf>
  \-PE  7eab0000-7eaee000       \               advapi32
ELF     7eaee000-7eaf9000       Deferred        libgcc_s.so.1
ELF     7eaf9000-7eb0d000       Deferred        lz32<elf>
  \-PE  7eb00000-7eb0d000       \               lz32
ELF     7ebec000-7eca5000       Deferred        gdi32<elf>
  \-PE  7ec00000-7eca5000       \               gdi32
ELF     7eca5000-7eddf000       Deferred        user32<elf>
  \-PE  7ecc0000-7eddf000       \               user32
ELF     7eddf000-7ee9b000       Deferred        comctl32<elf>
  \-PE  7edf0000-7ee9b000       \               comctl32
ELF     7efa5000-7efb0000       Deferred        libnss_files.so.2
ELF     7efb0000-7efc6000       Deferred        libnsl.so.1
ELF     7efc6000-7efec000       Deferred        libm.so.6
ELF     7efed000-7eff6000       Deferred        libsm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d00000-b7d09000       Deferred        libnss_compat.so.2
ELF     b7d0a000-b7d0e000       Deferred        libdl.so.2
ELF     b7d0e000-b7e42000       Deferred        libc.so.6
ELF     b7e43000-b7e56000       Deferred        libpthread.so.0
ELF     b7e56000-b7e59000       Deferred        libxau.so.6
ELF     b7e6a000-b7f7b000       Deferred        libwine.so.1
ELF     b7f7d000-b7f98000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Bethesda Softworks\Oblivion\Oblivion.exe
        00000011    0
        00000010    0
        0000000e   15
        0000000d    0
        00000009    0 <==

```

---

### Post by ahaslam on 2007-04-05
I've added the tree spriting to Bugzilla, along with my exiting problem. Someone else has reported the white noise, so let's hope future Wine releases address some issues ;)

---

### Post by Corvias on 2007-04-05
I got it to run! Of course it was the ONLY and LAST thing I tried. It was the music. I set bMusicEnabled to 0 and I got to the main menu, char creation and the game itself. I feel dumb. Sorry if anyone was actually looking into this. 

More Details: No tab crash and animation seems great. Only two issues now are no music (obviously) and the sound has a lot of static (sounds like a waterfall).

---

### Post by NullHead on 2007-04-05
Hay need some help hear ... i used the guide at the front of this thread and it got the menu to load but still no go on the actual game playing it just crashes when i load a save 

i'm running a 
AMD athlon 4000
Nvidia geforce 7600gs with xgl and beryl 
realtek ac'97 
Ubuntu 6.10 x86 64 
wine 0.9.34 ... compiled from source 

thx

---

### Post by Corvias on 2007-04-06
NullHead,

First, I'd make sure Beryl is not running when you attempt to start oblivion. On my system at least, Beryl doesn't play nice with other 3D apps. Basically, go to the re gem icon on the panel bar and switch your window manager to Metacity while you're running/trying to run Oblivion. 

By looking at you crash dump, (this is just a guess, I'm not a guru by any stretch of the imagination) it looks like you have anti-aliasing turned on and wine doesn't like it. try turning it off. Also, try disabling music in your oblivion.ini (that's what made things work for me).

---

### Post by Kiwi-Hawk on 2007-04-09
Hi
First up I'm here bcause Mepis user's  Ubuntu  code as a base

Is there away to track whats happening,. I get to start screen and can set screen size
etc; I get a direct HAL video driver ( not sure this is right ) but I press play I get the window close and a new one open and that close's

I have a 3.2gig Intel Aus p5w dh board with 2gig ram and a wee EN7950GT 512 ram nvidia video card.

I run Mepis 6.5 final and wine 0.9.9 OUbuntu2 all update done.

I should mention too the sound work but as set itself on oss sound in wine cfg.
I did not think this would be a problem as it works



cheers
Kiwi-Hawk

---

### Post by Iarwain ben-adar on 2007-04-10
You can try running it via terminal ;)


Iarwain

---

### Post by ahaslam on 2007-04-11
> **Kiwi-Hawk said:**
> 
I get to start screen and can set screen size
etc; I get a direct HAL video driver ( not sure this is right ) but I press play I get the window close and a new one open and that close's

So the game doesn't run?

> **Kiwi-Hawk said:**
> I run Mepis 6.5 final and wine 0.9.9 OUbuntu2 all update done. 

I'm assuming that comes with the distro? What version of Wine is that (winecfg > About)?

See here if it's old: [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

---

### Post by NullHead on 2007-04-11
> **Corvias said:**
> 

it looks like you have anti-aliasing turned on and wine doesn't like it. try turning it off. Also, try disabling music in your oblivion.ini (that's what made things work for 
me).

Well I tried turning off the music in the Oblivion.ini but I'm not shure if i got it right.
And for the anti-aliasing ... well I can't tell if it is on or off at this point the Oblivion Launcher>options>Video said that it is off.... 

hears the next dunp...

Thanks

---

### Post by ahaslam on 2007-04-13
I'm very disappointed in performance, averaging 20 fps is not good. 
I have taken overclocking to high levels on the cpu, memory & vga card without making any difference. My cpu does not go over 40% utilisation (average over cores), memory sits at 69% & my gpu stays very cool, so I'm guessing it's not under huge strain. My current spec's are as follows: C2D @ 3.15GHz, 2x512MB DDR2-5400 @ 900MHz 4-4-4-12, 7950GT @ 660,785

And here's some screens showing fps (default graphic levels, no hdr):

---

### Post by cor2y on 2007-04-13
Maybe for now its better to dual boot to XP (I know most people probably loathe this) or perhaps try to run Oldblivion on top of Oblvion after all isn't that what the Cedega people recommend?

---

### Post by bastiegast on 2007-04-13
Man, don't use oldoblivion, you see his screenshots? The graphics are fine and he is getting 20 fps. Graphics in oldoblivion suck. And cedega 6 runs Oblivion pretty well (hate to say but better than wine actually, water shader works to some degree, sound is almost perfect)

---

### Post by ahaslam on 2007-04-13
> **cor2y said:**
> Maybe for now its better to dual boot to XP (I know most people probably loathe this) or perhaps try to run Oldblivion on top of Oblvion after all isn't that what the Cedega people recommend?

I don't own or desire XP, but I have thought about running 2000 in Qemu :-k

> **bastiegast said:**
> Man, don't use oldoblivion, you see his screenshots? The graphics are fine and he is getting 20 fps. Graphics in oldoblivion suck. And cedega 6 runs Oblivion pretty well (hate to say but better than wine actually, water shader works to some degree, sound is almost perfect)

Yeah, oldblivion really is no good, I tried it & it didn't help with speed, just looked like sh1t.
I really think that supported/unsupported video cards make all the difference, why else would people with high end 6 series cards be getting better performance than myself?

Regards Cedega, is performance better also? 

The big game stoppers for me are: tree spriting, sound & performance. I really don't find it too enjoyable atm.

---

### Post by ahaslam on 2007-04-13
Ok, tried Cedega. Nice to have good sound (I jumped in surprise at one point) & no spriting trees. The performance is also better, by about an average of 10fps. It certainly uses more system resources, but not enough to max out the system, you can still multi-task. The problem is the stability, menus are incredibly glitchy & the game quits randomly & frequently. So with that taken in consideration, Cedega is certainly not worth a subscription. 

I only managed to take one screenie for comparison:

---

### Post by rivethead on 2007-04-13
Is there anyway if i already have Oblivion installed on my windows partition that i could play it from that partition? Adding some stuff to wine or what not? im not really sure, but i have to keep my windows partition for audio software and that would be very handy.

---

### Post by xopher on 2007-04-13
Basically yes, if you just get the wine-registry edited correctly..

---

### Post by xopher on 2007-04-13
> **Anthony Haslam said:**
> Ok, tried Cedega. Nice to have good sound (I jumped in surprise at one point) & no spriting trees. The performance is also better, by about an average of 10fps.

Right, the sound is the only thing really annoying me in Wine/Oblivion right now.

Any ideas on getting it fixed? :/ Wouldn't want to switch over to cedega just because of this.

---

### Post by ahaslam on 2007-04-13
> **xopher said:**
> Right, the sound is the only thing really annoying me in Wine/Oblivion right now.
Any ideas on getting it fixed? :/ Wouldn't want to switch over to cedega just because of this.
The sound issue has been reported at bugzilla, unfortunatly unless you're a developer your bug reports don't seem to be taken seriously. They need to be told the exact problem & it's unlikely that we're going to know, it just doesn't work properly.

[http://bugs.winehq.org/show_bug.cgi?id=7912](http://bugs.winehq.org/show_bug.cgi?id=7912)

---

### Post by xopher on 2007-04-13
Well yeah, it would really ease the progress of tracing the bug if we'd narrow it down from 'it can be anything' to at least a specific area. On to my next question: How do I do this then? :)

Oh goody, a new version of Wine released, again :rolleyes:

Notes:

> Wine 0.9.35 was released today, with the following main changes:

    * Broken aRts sound driver now removed for good.
    * Many fixes to the Quartz DLL sound support.
    * File I/O performance improvements.
    * The usual assortment of Direct3D fixes.
    * Lots of bug fixes.

---

### Post by ahaslam on 2007-04-13
lol :) At least he was honest from the outset ;)

---

### Post by rivethead on 2007-04-13
Ive followed this guide a couple times with no luck, it seems im still getting a d3dx9_27.dll error even though i have copied it to the correct directory.

---

### Post by NullHead on 2007-04-14
> **rivethead said:**
> Ive followed this guide a couple times with no luck, it seems im still getting a d3dx9_27.dll error even though i have copied it to the correct directory.

Try this from your cdrom and see what it does.


```
WINEDLLOVERRIDES=mscoree="" wine DXREDIST/DXSETUP.exe
```

---

### Post by rivethead on 2007-04-16
> **NullHead said:**
> Try this from your cdrom and see what it does.

code
-----------
WINEDLLOVERRIDES=mscoree="" wine DXREDIST/DXSETUP.exe
-----------

That worked for me thanks alot man, now i just have to get a Config that works worth a crap for it.

---

### Post by NullHead on 2007-04-16
> **rivethead said:**
> That worked for me thanks alot man, now i just have to get a Config that works worth a crap for it.

No problem, but I can't take all of the credit ... Vit Hrachovy at winehq gave me this help...yet it still doesn't work for me

> **rivethead said:**
> now I just have to get a Config that works worth a crap for it.

A conig for what??

---

### Post by Death_Sargent on 2007-04-16
ITS CALLED CEDEGA

for 5 bucks it works.

I would respond to any replies to this post but I'm busing playing my windows games under something that works. Snicker

no really its just 5 bucks a month 15 up front and hey it works nice and easy. 

not to be a douche but there is really no reason to use wine for gaming unless your skilled in programing and well hate having free time

---

### Post by bastiegast on 2007-04-16
> **Death_Sargent said:**
> ITS CALLED CEDEGA

for 5 bucks it works.

I would respond to any replies to this post but I'm busing playing my windows games under something that works. Snicker

no really its just 5 bucks a month 15 up front and hey it works nice and easy. 

not to be a douche but there is really no reason to use wine for gaming unless your skilled in programing and well hate having free time

Most provoking post i've ever seen, but I will reply..

First: Cedega was crap compared to wine until just a few days ago, due to the lack of Pixel Shader 2.0 support. Second: Oblivion seems to be a pain to play under cedega since its crashy.
Third: Why use wine? Since wine is open source and we all use linux here so I don't have to explain the advantages to you.
Next, if your to lazy/unskilled to edit one or two lines of oblivion.ini and copy a dll then pay your five dollars I rather take five minutes of my valuable free time to do that and play Oblivion in wine.

Anyway, you better put this sort of posts in of the thousands wine vs. cedega threads(I should too, but I couldn't resist).

---

### Post by Cappy on 2007-04-16
Is wine still lacking the Pixel Shader 2.0 support? I always thought Cedega was built on wine with an "easy to use" interface.

---

### Post by NullHead on 2007-04-16
Slap Slap!!

---

### Post by bastiegast on 2007-04-16
> **Cappy said:**
> Is wine still lacking the Pixel Shader 2.0 support? I always thought Cedega was built on wine with an "easy to use" interface.

Read my post, cedega was lacking PS 2.0 support, wine had it for a while.

---

### Post by rivethead on 2007-04-16
Ive got it up and running really nice acctually and with most sounds even, im pretty happy about that. However ive got this wierd issue happening now lol and i cant figure this one out either.

[[IMG]http://lh3.google.com/image/rivethead/RiQxLnAMtrI/AAAAAAAAACk/iqGIKlO3PGA/s144/obliv.jpg[/IMG]]("http://picasaweb.google.com/rivethead/RandomPics/photo#5054218757334677170")

Any idea what would be causing that? Ive checked the config file, texture sizes, and nVidia drivers.

---

### Post by NullHead on 2007-04-16
A bigger picture would be nice ;)

and I added a fixed Oblivion.ini

---

### Post by NullHead on 2007-04-16
Hay I  finally  got it to work. Bloom and HDR screen effects don't work though. Great How-To Thanks!! :D

---

### Post by rivethead on 2007-04-16
> **NullHead said:**
> A bigger picture would be nice ;)

and I added a fixed Oblivion.ini

You should be able to click on that pic and have a larger one but if not, it appears as though the skins are not displaying on the models, just hair , eyes and mouth.

---

### Post by Mblackwell on 2007-04-17
Update to a newer version of Nvidia than what's in the repos.

---

### Post by NullHead on 2007-04-17
> **rivethead said:**
> You should be able to click on that pic and have a larger one but if not, it appears as though the skins are not displaying on the models, just hair , eyes and mouth.

Do you have bloom  screen effects turned on? if so turn them off.

---

### Post by Mongoose on 2007-04-20
It helps if you read the wiki, since this is a Known Issue using old Nvidia drivers.  Thanks for playing.  =)

I see 0.9.35 fixed a lot of the remaining shader issues -- at least after playing for 5mins for the first time in weeks.

---

### Post by ahaslam on 2007-04-21
Is the tree spriting still apparent?

---

### Post by bastiegast on 2007-04-22
> **Anthony Haslam said:**
> Is the tree spriting still apparent?

It still is. But it seems like the static has reduced. 

I'm suffering from a very frustrating problem lately, Oblivion seems to randomly clear out all my save games, when I save again the save just disappears. When I restart Oblvion the saves are back luckily. 

Maybe it is because I dragged my savegames around too much between patched and unpatched oblivion installs. 

It seems Im not the only one experiencing this problem; someone filed a bug: [http://bugs.winehq.org/show_bug.cgi?id=8128]("http://bugs.winehq.org/show_bug.cgi?id=8128")

---

### Post by Mongoose on 2007-04-22
Are you playing Shivering Isles?  You should be aware of the uid bug by now and how it corrupts save games.  It only affects Oblivion on the PC iirc.

Update:
Oh, rereading your post after reading the linked bug: Yeah, that's a different issue and it has nothing to do with losing savegames or corruption.  That's more of a UI issue in the game.  Go go threads.  ;)

---

### Post by ahaslam on 2007-04-22
> **bastiegast said:**
> It still is. But it seems like the static has reduced. 


Thanks for the reply. Nice to hear the sound's a bit better. 
As Oblivion takes time to play, I'm waiting for it to work properly. I want to experience it as intended, without MS.

;)

---

### Post by Jarn on 2007-04-24
Hi, I just attempted to install Oblivion. It is really laggy. The FPS doesn't isn't so bad when I'm standing still, about 20, but as soon as I try to turn or anything it drops down to 1. And my machine, while not uber, is not sub-par.

AMD Athlon 64 3200+
1 gig of ram
nVidia Geforce 6800
Wine 0.9.35
Kubuntu 7.04

EDIT: Also, is there any way to change where Oblivion stores it's files? It picked a location I don't like. It picked ~/My Games/Oblivion/ and I don't approve!

EDIT2: If I use the ugly tlb switch, I get about 30 fps and yet I still lag. Though the fps is fine, I lag. I think I've noticed similar things in other games I play.

---

### Post by NullHead on 2007-04-25
> **Jarn said:**
> Hi, I just attempted to install Oblivion. It is really laggy. The FPS doesn't isn't so bad when I'm standing still, about 20, but as soon as I try to turn or anything it drops down to 1. And my machine, while not uber, is not sub-par.

AMD Athlon 64 3200+
1 gig of ram
nVidia Geforce 6800
Wine 0.9.35
Kubuntu 7.04

EDIT: Also, is there any way to change where Oblivion stores it's files? It picked a location I don't like. It picked ~/My Games/Oblivion/ and I don't approve!

EDIT2: If I use the ugly tlb switch, I get about 30 fps and yet I still lag. Though the fps is fine, I lag. I think I've noticed similar things in other games I play.

Are you using beryl or compiz? If so they will diminish your preformance a little. Did you follow the HOW-TO at the front of this thread?

---

### Post by Jarn on 2007-04-25
No I'm not using either of those and yes I followed the HOWTO.

---

### Post by bastiegast on 2007-04-25
> **Jarn said:**
> 
EDIT: Also, is there any way to change where Oblivion stores it's files? It picked a location I don't like. It picked ~/My Games/Oblivion/ and I don't approve!


Yes there is and it is actually mentioned in the guide. Oblivion stores your savegames in your My Documents fiolder which you can set in winecfg, go to the tab desktop intergration, and set your My Documents folder to any location you want.

About the performance, I have a similair system and am able to play oblivion, di you disable the water shader in ~/My\ Games/Oblivion/Oblivion.ini and are you using the latest nvidia drivers? You might want to disable some shaders and see what happens.

---

### Post by Jarn on 2007-04-25
I did disable the shaders. I don't know if I'm using the latest nVidia drivers, I know there's no newer ones when I apt-get update and then apt-get upgrade... but if I have to download them from somewhere, I may not be.

---

### Post by Mblackwell on 2007-04-25
There's newer beta drivers. Usually the drivers in the repos are slightly (or more than slightly) depreciated.

---

### Post by NullHead on 2007-04-25
I would download the stable ones from Nvidia's website [hear]("http://www.nvidia.com/page/home.html")

---

### Post by ahaslam on 2007-05-02
Is it me or is the tree spriting worse in Wine 0.9.36 :-k

The static isn't constant any more, it just comes & goes. The frame rate also seems a little better, but trees appearing & staying in front of you is a real game killer.

---

### Post by Jarn on 2007-05-02
Lucky for you. My framerates still are barely playable, with newest drivers, newest Wine, and no Beryl or Compiz.

---

### Post by Mongoose on 2007-05-02
If it's really bad you can set speedtree draw distance closer, and it should 'fix' it as a stop gap.   If not file a new bug or report about draw distance not affecting speedtree.  ;)

I need to load up Oblivion agian soon, and see how it's going.

Latest Nvidia drivers via the Nvidia install package:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

If Oblivion is running slow for you, and you have a OpenGL '2.1' card you're doing something wrong.  Some cards claiming OpenGL 2.0 support in drivers are really just OpenGL 1.5 with minor feature improvements, so be warned.  That means 6600GT+ should do it, but I've seen some value cards that fail that generalization.

---

### Post by kentpend on 2007-05-03
I followed the guide up to the "first run" part, at which point it crashed.  The black program box comes up on the wine desktop, but then then it just quits.  I had the same result after trying several versions of wine too.

I am currently running Feisty.

Any tips on how to go about solving this?

---

### Post by NullHead on 2007-05-03
> **Jarn said:**
> Lucky for you. My framerates still are barely playable, with newest drivers, newest Wine, and no Beryl or Compiz.

What is your video card manufacturer name and model number Nvidia or Ati What?

---

### Post by Jarn on 2007-05-03
EVGA nVidia Geforce 6800

---

### Post by NullHead on 2007-05-03
> **Jarn said:**
> EVGA nVidia Geforce 6800

Are the settings turned up to high? I might play with those. Check the on-board ram and see if it's 256mb or above. Check your refresh rate on your desktop and turn that down and see what that does. I am really confused as of why this problem is happening ... and if you truly want performance use...dare I say *WINDOWS!* I'm not proud that I dual boot but I own a Creative X-FI and have to use you know what for my games, but it does do game quite nicely. you might consider this if your too desperate.

---

### Post by Jarn on 2007-05-03
It is 256mb. The settings are very low. I have tried oblivion in both a new X session and in my desktop with similar results. My desktop has a refresh rate of 54Hz and the new X session was 60.

---

### Post by bastiegast on 2007-05-04
> **kentpend said:**
> I followed the guide up to the "first run" part, at which point it crashed.  The black program box comes up on the wine desktop, but then then it just quits.  I had the same result after trying several versions of wine too.

I am currently running Feisty.

Any tips on how to go about solving this?

Two possible reasons: No/invalid nvidia drivers or you didn't disable the intro movies. The INI file is located in in My Games/Oblivion/Oblivion.ini 

Also what video card are you using and how much Ram does it have?

---

### Post by kentpend on 2007-05-05
The intro sequence turned out to be the problem; apparently it hadn't saved correctly the first time I disabled it.

But I've run into a different problem now: it crashes when it reaches the player creation menu.  All other menus in the game seem to be fine when I tested using previous saves, although I haven't tried talking to any NPCs yet.

I am running on a 7900GT, 256Mb

---

### Post by boosted_sled on 2007-05-06
make sure you don't have any wine/Oblivion processes still running.  I had this problem once.

---

### Post by boosted_sled on 2007-05-06
I've got Oblivion running fairly well (no music, mixer bug, what looks like some kind of blending bug on certain spell effects?), but I need to run under Oscuro's Oblivion Overhaul 1.31 to use my previous saved games.  Unfortunately, Oblivion isn't picking up the mod files and gives me a missing content warning.  The game works under the mod but I get the "exclamation point box" mesh for the missing content.  Few questions:

(1) Is there a trick to get mods working?
(2) what's the easiest mod manager (wrye bash, etc) to get running.  These all have some wine unfriendly dependencies.

Thx.

---

### Post by Jarn on 2007-05-06
OBMM is impossible, afaik. I don't think .NET Framework 2 can be installed under Wine. The only option is Wrye Bash, but I haven't been able to get that installed either.

---

### Post by Mongoose on 2007-05-07
Nah, you can just click to enable them from the laucher, however your mod in question could have other issues.  The expansions, etc are basically mods anyway.  If I had time to play I'd get the SI even with the new bugs heh.

---

### Post by Jarn on 2007-05-07
Does anyone know how to get Oldblivion running in Wine? I bet if I could use that I would get better framerates.

---

### Post by kentpend on 2007-05-07
> **boosted_sled said:**
> make sure you don't have any wine/Oblivion processes still running.  I had this problem once.

I don't think that's the issue, as this happened right after I  rebooted.  How do I check though?  Nothing related to wine is listed with the top command.

I ran into another issue.  Sometimes when I play, I can't look in certain directions without the entire screen turning green.  I *think* this is associated with looking towards an Oblivion gate, but I don't know for sure because I can't see anything.

---

### Post by Mongoose on 2007-05-07
Jarn: You'd be wrong about that.  If you want to 'go fast' just disable all the lighting.  iirc even my crappy card gets 300 fps at that point.  It's also a good way to cool down your card id you've been playing a while.  You can do more with the Oblivion.ini and editing the shader packs than using that horrible hack.  That's why it was discontinued amoung other reasons.

kentpend: You sound like you have driver issues, or you didn't follow the guide on the wiki.  I suggest disabling refraction shaders to fix gates -- however are you sure it's not a speed tree sprite rendering in the wrong location?  I'll go check and make sure some asshat didn't remove information off the wiki again.

---

### Post by Jarn on 2007-05-08
Umm... Oldblivion wasn't discontinued, it's still in development - they're working on a version that works wit Shivering Isles atm. And I already have all the lighting off and I still get low fps.

---

### Post by Mongoose on 2007-05-08
Well, I personally don't think it's worth digging back up.  Looking at the website it looks like it's still a back burner project at best.  If you have all lighting turned off, and you still can't run the game OldBlivion won't help you at all.  I'm talking about disabling everything but the texture pass.  You'd have to start changing model geometery to increase framerates at that point.  I don't mean to be an ***, but I can't believe you given what I know about the game.  

It's better to help with the Wine project than waste time running unstable hacks.  The new $50 7300s out now give little excuse if you're using a pre 2.0 OpenGL card still.  Those are two good reasons Oldblivion is dead.  Not to mention it is even of less value to someone with a Linux desktop.

---

### Post by boosted_sled on 2007-05-08
> **boosted_sled said:**
> I've got Oblivion running fairly well (no music, mixer bug, what looks like some kind of blending bug on certain spell effects?), but I need to run under Oscuro's Oblivion Overhaul 1.31 to use my previous saved games.  Unfortunately, Oblivion isn't picking up the mod files and gives me a missing content warning.  The game works under the mod but I get the "exclamation point box" mesh for the missing content.  Few questions:

(1) Is there a trick to get mods working? 

I had a patch & mod dependency mess to figure out.  With this straighted out my old Windows saves seem to be working.

>  (2) what's the easiest mod manager (wrye bash, etc) to get running.  These all have some wine unfriendly dependencies. 

I got wrye bash sorta running with a few source code edits.  Unfortunately the right mouse button event or menu display behavior is whacked with wxPython under my wine.

---

### Post by boosted_sled on 2007-05-08
> **kentpend said:**
> I don't think that's the issue, as this happened right after I  rebooted.  How do I check though?  

I could see these process with *ps aux*.  It only happened to me once.

---

### Post by Jarn on 2007-05-09
> **Mongoose said:**
> It's better to help with the Wine project than waste time running unstable hacks.  The new $50 7300s out now give little excuse if you're using a pre 2.0 OpenGL card still.I'm not using a pre-2.0 card. Or atleast, I don't think I am. It's not on newegg anymore so I can't check the specs there, but Wikipedia says that 6800s are OpenGL 2.0, and that's what I have: nVidia Geforece 6800.

> **Mongoose said:**
>  I can't believe you given what I know about the game.Why would I possibly lie? This makes me a little bit mad, frankly. I come here to try and get help and I get called a liar.

---

### Post by kentpend on 2007-05-09
> **Mongoose said:**
> 
kentpend: You sound like you have driver issues, or you didn't follow the guide on the wiki.  I suggest disabling refraction shaders to fix gates -- however are you sure it's not a speed tree sprite rendering in the wrong location?  I'll go check and make sure some asshat didn't remove information off the wiki again.

The refraction shader solved it, thanks.  For the menu issue, it is only the player creation menu, nothing else.

> I could see these process with ps aux. It only happened to me once.

There are no Oblivion or wine processes listed when I did that, and the player creation menu still crashed the game.

---

### Post by robgig1088 on 2007-05-09
Hey guys, I recently tried to install Oblivion with wine-0.9.36 and I'm having some (major) issues.  I followed the guide (several times, actually) to no avail.  Can't figure out what's causing my problems :( .  Heres the output i get... (the important parts.)

> 
$ wine Oblivion.exe
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16_LOCKABLE
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D32
.....
.....
.....
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D16
fixme:d3d:IWineD3DDeviceImpl_SetMultithreaded No thread safety in wined3d yet
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1cb118) : stub, simulating 256MB for now, returning 256MB left
wine: Unhandled page fault on read access to 0x00000d28 at address 0x7e2ffdb6 (thread 0017), starting debugger...
Unhandled exception: page fault on read access to 0x00000d28 in 32-bit code (0x7e2ffdb6).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e2ffdb6 ESP:7c889880 EBP:7c8898cc EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7cc8d238 ECX:7e4b7984 EDX:001cb118
 ESI:001790a0 EDI:00000001
Stack dump:
0x7c889880:  7cc01f3b 00008d40 00000000 00000000
0x7c889890:  834bb6a0 7bc572ab 7bc7a3b4 00000000
0x7c8898a0:  7bc29be1 7c889934 7bc5af8b 7c8898b8
0x7c8898b0:  7e4b49a4 001790a0 00000001 7c8898cc
0x7c8898c0:  7cc8d238 001790a0 00000001 7c88994c
0x7c8898d0:  7cc02ce3 001cb118 00000000 00000000
Backtrace:
=>1 0x7e2ffdb6 glIsRenderbufferEXT+0xe6() in libgl.so.1 (0x7c8898cc)
  2 0x7cc02ce3 in wined3d (+0x22ce3) (0x7c88994c)
  3 0x7cca5a75 in d3d9 (+0x5a75) (0x7c88997c)
  4 0x00410133 in oblivion (+0x10133) (0x00000000)
0x7e2ffdb6 glIsRenderbufferEXT+0xe6 in libgl.so.1: jmp  *0xd28(%eax)
Modules:
Module  Address                 Debug info      Name (94 modules)
PE        400000-  b73000       Export          oblivion
PE        b80000-  dcf000       Deferred        d3dx9_27
PE      18000000-18068000       Deferred        binkw32
ELF     7b800000-7b927000       Deferred        kernel32<elf>
  \-PE  7b820000-7b927000       \               kernel32
ELF     7bc00000-7bc96000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc96000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cb4d000-7cbcd000       Deferred        libglu.so.1
ELF     7cbcd000-7cc8e000       Export          wined3d<elf>
  \-PE  7cbe0000-7cc8e000       \               wined3d
ELF     7cc8e000-7ccba000       Export          d3d9<elf>
  \-PE  7cca0000-7ccba000       \               d3d9
ELF     7d01f000-7d034000       Deferred        midimap<elf>
  \-PE  7d030000-7d034000       \               midimap
ELF     7d034000-7d05a000       Deferred        msacm32<elf>
  \-PE  7d040000-7d05a000       \               msacm32
ELF     7d05a000-7d096000       Deferred        wineoss<elf>
  \-PE  7d060000-7d096000       \               wineoss
ELF     7d096000-7d0c8000       Deferred        uxtheme<elf>
  \-PE  7d0a0000-7d0c8000       \               uxtheme
ELF     7d35e000-7d376000       Deferred        msacm32<elf>
  \-PE  7d360000-7d376000       \               msacm32
ELF     7d378000-7d37d000       Deferred        libxfixes.so.3
ELF     7d37d000-7d386000       Deferred        libxcursor.so.1
ELF     7d386000-7d3a3000       Deferred        imm32<elf>
  \-PE  7d390000-7d3a3000       \               imm32
ELF     7d3a3000-7d3a9000       Deferred        libxrandr.so.2
ELF     7d3a9000-7d3b1000       Deferred        libxrender.so.1
ELF     7d3b1000-7d3b4000       Deferred        libxinerama.so
ELF     7d8d5000-7e26d000       Deferred        libglcore.so.1
ELF     7e26d000-7e302000       Export          libgl.so.1
ELF     7e302000-7e307000       Deferred        libxdmcp.so.6
ELF     7e307000-7e30a000       Deferred        libxau.so.6
ELF     7e30a000-7e3fb000       Deferred        libx11.so.6
ELF     7e3fb000-7e409000       Deferred        libxext.so.6
ELF     7e409000-7e40e000       Deferred        libxxf86vm.so.1
ELF     7e40e000-7e426000       Deferred        libice.so.6
ELF     7e426000-7e42f000       Deferred        libsm.so.6
ELF     7e42f000-7e4be000       Deferred        winex11<elf>
  \-PE  7e440000-7e4be000       \               winex11
ELF     7e55c000-7e57c000       Deferred        libexpat.so.1
ELF     7e57c000-7e5a7000       Deferred        libfontconfig.so.1
ELF     7e5a7000-7e5bb000       Deferred        libz.so.1
ELF     7e5bb000-7e626000       Deferred        libfreetype.so.6
ELF     7e626000-7e653000       Deferred        ws2_32<elf>
  \-PE  7e630000-7e653000       \               ws2_32
ELF     7e653000-7e66d000       Deferred        wsock32<elf>
  \-PE  7e660000-7e66d000       \               wsock32
ELF     7e66d000-7e6d4000       Deferred        msvcrt<elf>
  \-PE  7e680000-7e6d4000       \               msvcrt
ELF     7e6d4000-7e6ed000       Deferred        version<elf>
  \-PE  7e6e0000-7e6ed000       \               version
ELF     7e6ed000-7e745000       Deferred        shlwapi<elf>
  \-PE  7e700000-7e745000       \               shlwapi
ELF     7e745000-7e840000       Deferred        shell32<elf>
  \-PE  7e760000-7e840000       \               shell32
ELF     7e840000-7e889000       Deferred        dsound<elf>
  \-PE  7e850000-7e889000       \               dsound
ELF     7e889000-7e918000       Deferred        winmm<elf>
  \-PE  7e8a0000-7e918000       \               winmm
ELF     7e918000-7e92b000       Deferred        libresolv.so.2
ELF     7e92b000-7e949000       Deferred        iphlpapi<elf>
  \-PE  7e930000-7e949000       \               iphlpapi
ELF     7e949000-7e99e000       Deferred        rpcrt4<elf>
  \-PE  7e960000-7e99e000       \               rpcrt4
ELF     7e99e000-7ea3b000       Deferred        ole32<elf>
  \-PE  7e9b0000-7ea3b000       \               ole32
ELF     7ea3b000-7ea71000       Deferred        dinput<elf>
  \-PE  7ea40000-7ea71000       \               dinput
ELF     7ea71000-7ea8a000       Deferred        dinput8<elf>
  \-PE  7ea80000-7ea8a000       \               dinput8
ELF     7ea8a000-7ead1000       Deferred        advapi32<elf>
  \-PE  7eaa0000-7ead1000       \               advapi32
ELF     7ead1000-7eadd000       Deferred        libgcc_s.so.1
ELF     7eadd000-7eaf1000       Deferred        lz32<elf>
  \-PE  7eae0000-7eaf1000       \               lz32
ELF     7ebdb000-7ec99000       Deferred        gdi32<elf>
  \-PE  7ebf0000-7ec99000       \               gdi32
ELF     7ec99000-7edd5000       Deferred        user32<elf>
  \-PE  7ecc0000-7edd5000       \               user32
ELF     7edd5000-7ee91000       Deferred        comctl32<elf>
  \-PE  7ede0000-7ee91000       \               comctl32
ELF     7efa3000-7efae000       Deferred        libnss_files.so.2
ELF     7efae000-7efc5000       Deferred        libnsl.so.1
ELF     7efc5000-7efec000       Deferred        libm.so.6
ELF     7efec000-7efee000       Deferred        libnvidia-tls.so.1
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d00000-b7d09000       Deferred        libnss_compat.so.2
ELF     b7d0a000-b7d0e000       Deferred        libdl.so.2
ELF     b7d0e000-b7e4f000       Deferred        libc.so.6
ELF     b7e50000-b7e67000       Deferred        libpthread.so.0
ELF     b7e7b000-b7f8c000       Deferred        libwine.so.1
ELF     b7f8e000-b7fa9000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000f 
        00000011    0
        00000010    0
0000000d (D) C:\Program Files\Bethesda Softworks\Oblivion\Oblivion.exe
        00000019   -1
        00000018   15
        00000017    1 <==
        00000016   -1
        00000015   -1
        00000014   15
        00000012    0
        0000000e    0


Any help at all would be VERY appriciated =).  Btw, I use Nvidia and feisty x86.

EDIT:  ok i forgot to tell you guys how i installed it.  About a year ago, i downloaded it from a torrent (yes yes shame on me. I don;t game enough to justify the $50 price tag).  So I copied the (2x).daa files to my ipod then left them.  I re-copied them to my windows desktop when i needed to reformat my ipod.  From there, I extracted them with poweriso and installed.  Do you think they became corrupt perchance?

---

### Post by Mongoose on 2007-05-10
I use a 6800 also.  This proves you were clearly not being honest about your settings.  If you don't know how to make the settings just ask.  There is no shame in not known -- just shame in lying about it.  Don't worry, as a developer I have users lie to me all the time about issues.  It doesn't hurt my feelings.  ;)

---

### Post by Jarn on 2007-05-10
> **Mongoose said:**
> This proves you were clearly not being honest about your settings.Or, MUCH more likely, you have absolutely no idea what my problem is and you're accusing me of lying to cover it up. Why don't you just admit you don't know what my problem is?

---

### Post by robgig1088 on 2007-05-10
Well, I got it working.  I just renamed my Video directory and it worked.  :guitar:

---

### Post by Mongoose on 2007-05-12
Yeah, you're problem is your attitude.  I figured that out pretty quick.  If you don't like the Linux Oblivion guides go read some on Windows Oblivion.ini tweaking.  You can get a 30-50+ FPS play if you disable certain shaders with that card, and it'll still have a great visual quality.

By the way, you can get a smooth 100+ FPS if you actually disabled lighting.

---

### Post by Cappy on 2007-05-12
> **Mongoose said:**
> I use a 6800 also.  This proves you were clearly not being honest about your settings.  If you don't know how to make the settings just ask.  There is no shame in not known -- just shame in lying about it.  Don't worry, as a developer I have users lie to me all the time about issues.  It doesn't hurt my feelings.  ;)

Jarn has no reason to lie to you. He's only asking for help. If you know he should be getting higher FPS then he MUST have a problem somewhere. Even if there are settings he doesn't know about that you can point out, that doesn't mean he is dishonest.

Here is a mod I personally use:
[http://planetelderscrolls.gamespy.com/View.php?view=oblivionmods.detail&id=2731](http://planetelderscrolls.gamespy.com/View.php?view=oblivionmods.detail&id=2731)

It won't solve all your problems but it will help.

---

### Post by jimminy_kriket on 2007-05-12
anyone tried wine 0.9.37 yet?

Edit: Sweet! nice find cappy, ill try this out when my laptop comes back from repair >_<. Hopefully it's compatible with some other appearance mods i have ;D.

---

### Post by Jarn on 2007-05-12
> **Mongoose said:**
> Yeah, you're problem is your attitude.  I figured that out pretty quick.You're the one who seems to have an attitude problem. Someone comes asking for help and when you can't help them you start to throw around words like "liar".

> **Mongoose said:**
> By the way, you can get a smooth 100+ FPS if you actually disabled lighting.AND you get condescending! On top of that, you apparently don't even read. I've said before that FPS is only ONE of my problems, though it's the main one. Even when I have great FPS (like in the menus, where I have 200+), I still lag.

> **Cappy said:**
> Here is a mod I personally use:
[http://planetelderscrolls.gamespy.com/View.php?view=oblivionmods.detail&id=2731](http://planetelderscrolls.gamespy.com/View.php?view=oblivionmods.detail&id=2731)Thank you! I'll take a look at that later. :)

---

### Post by Mongoose on 2007-05-12
Hey, you lied -- it's pretty simple.  You didn't try disabling lighting.  I'm going to call you out on that.  It's not even important, since there is no point playing without lighting.  I get many emails and questions everyday where I just end up pointing people back at documents they supposedly read -- then they find the answer when they actually read the document.  I just don't pussyfoot around when it comes to things like that.

If you're now convinced it's not graphics how will altering your meshes or using Oldbivion help?  Perhaps you should try playing the game without any mods loaded and checking your thread settings.  Maybe you'll actually try suggestions at some point before dismissing them out of hand.  Disabling lighting would've ruled out graphics as a factor.  Also rereading your post history I'm pretty sure it's time for an ignore.  This is the last time I'll reply to you -- waste of time.

---

### Post by Cappy on 2007-05-12
I almost forgot - I had a similar problem running UT2004 at first. One of those desktop "CPU monitors" was causing my games to lag. It was lagging no matter how much I turned down my game quality and in menus too. Similar to your problem.
I have a few suggestions along the same kind of fix:
Goto System-->Administration-->Services and try unchecking "powernowd" and "acpid". I also disabled some stuff like the Bluetooth manager/Printer Services since I don't need them. Then reboot.

If that doesn't work, try adding "noapic nolapic acpi=off" onto the end of your kernel line in 
```

sudo gedit /boot/grub/menu.lst

```

Mine would look like this with it added on:
```

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=maybe_some_numbers_here ro noapic nolapic acpi=off
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

```
(then reboot)

If the kernel line doesn't help you might as well just take it off.

My last suggestion is to try the sidenet script on this page: 
[http://ubuntuforums.org/showthread.php?t=185557](http://ubuntuforums.org/showthread.php?t=185557)
I think it will wipe the registry and possibly any files in your .wine/dosdevices so a copy is recommended. I don't specifically know what the script does but it sets up wine "correctly" and has fixed a lot of problems for me. I don't know if its special powers extend to fixing FPS loss though =P

---

### Post by ahaslam on 2007-05-12
> **jimminy_kriket said:**
> anyone tried wine 0.9.37 yet?
Anyone? Running Arch64 atm, wouldn't want to waste time if tree spriting is still rampant ;)

---

### Post by Enverex on 2007-05-12
Don't really have time to look through all 27 pages but I just thought that I'd add that "kittycat" fixed the music in Morrowind and Oblivion so they play in Wine 0.9.37 now.

---

### Post by lordhebe on 2007-05-13
Hey I'm about to get Oblvion (I just got a new Geforce 7300 GT, so I will be able to play it properly (if slowly) but I'm curious about the whole "Tree sprite" thingy. Could someone post a screenshot so I can see what it looks like? Thanks.

---

### Post by Enverex on 2007-05-13
> **lordhebe said:**
> Hey I'm about to get Oblvion (I just got a new Geforce 7300 GT, so I will be able to play it properly (if slowly) but I'm curious about the whole "Tree sprite" thingy. Could someone post a screenshot so I can see what it looks like? Thanks.

I'd recommend not bothering for now, you wont enjoy the game because you'll need to lower the graphics settings so much, videos are still missing as well. I'd wait until it works better.

---

### Post by bastiegast on 2007-05-13
> **lordhebe said:**
> Hey I'm about to get Oblvion (I just got a new Geforce 7300 GT, so I will be able to play it properly (if slowly) but I'm curious about the whole "Tree sprite" thingy. Could someone post a screenshot so I can see what it looks like? Thanks.

Posting screenshots wouldn't help you much. The problem is some tree's, the bushes and the grass flashes in game, they disappear and reappear randomly which is very annoying.

> **Enverex said:**
> I'd recommend not bothering for now, you wont enjoy the game because you'll need to lower the graphics settings so much, videos are still missing as well. I'd wait until it works better.
Your own experience might not be representive for all. The problems atm with oblivion are:

 Occasional sound stutter
 static sound(although i found it to be rarer nowadays)
 No music(enverex, what do you mean by "kittycat?")
 HDR causing severe slowdown and needs tweaking to work
 Water shader doesn't render properly and causes severe slowdown(although the water looks acceptable)
 Tree spriting

That's about it, you'll be playing without water shader and without HDR. I turn the grass distance to zero which gives me a huge performance boost and makes the tree spritingproblem invisible

Quite a trade of compared to windows I admit but still playable and the game looks pretty nice.

And I don't know how many times I need to say this but as long as you follow the guide p**erformance is not an issue** I play on a nvidia 6800 on 1280 x 1024 with bloom most graphical settings maxed (except for noted) at a steady 20 fps outside

---

### Post by Enverex on 2007-05-13
I'm a bugs list and AppDB admin, WineHQ channel op and work closely with the devs, I'm pretty sure my "experiences" are going to trump most peoples considering I document most of these issues.

What I mean by "kittycat" is the Dev that goes by that handle fixed the issue with the music in the GIT tree prior to the release of Wine 0.9.37 which means if you update to Wine 0.9.37 that the music will now work in Wine and the static sound, as a positive side-effect should also now be gone.

---

### Post by bastiegast on 2007-05-13
> **Enverex said:**
> I'm a bugs list and AppDB admin, WineHQ channel op and work closely with the devs, I'm pretty sure my "experiences" are going to trump most peoples considering I document most of these issues.

What I mean by "kittycat" is the Dev that goes by that handle fixed the issue with the music in the GIT tree prior to the release of Wine 0.9.37 which means if you update to Wine 0.9.37 that the music will now work in Wine and the static sound, as a positive side-effect should also now be gone.

That's pretty cool.. and weird since I compiled .37 from source a few days ago and didn't notice any improvements on sound in Oblivion. Well Im going to try it again anyway.

I got a bit annoyed when you said you didn't recommend playing it without clearly stating what worked and what didn't so the guy could decide himself if he thinks its playable. 

The only reason I don't play the game now is something I didn't include in my list since not everyone seems to suffer from it. my savegame list gets cleared after playing for a while, if I restart the game the savegames are back however.(someone did filed a bug I believe)

---

### Post by Enverex on 2007-05-13
> **bastiegast said:**
>  if I restart the game the save games are back however.(someone did filed a bug I believe)

Yes, me. This issue is a critical one to the game, it doesn't just clear the list, it deletes the saves too apparently. I was testing it with a few others, I'd save 8 times or so, try and load and the list would clear and only my initial save was there. Browsing to the folder in the file-system showed that the saves don't exist anymore at all. I don't think people are going to like playing if their progress may just disappear.

Anyway, I felt half of the atmosphere from Oblivion came from it's graphics. Having to nerf things such as lighting and HDR as well as having glitches kills immersion and low frame rates (<40fps) also don't help, thus the recommendation to wait till it works better.

---

### Post by lordhebe on 2007-05-13
Well thanks for your recommendations, I will keep them in mind. My brother has a windows PC and he's going to be playing it the most (he's buying it actually). If I can play better than that then I'm happy, but again- backup, cedega. I have some money I can spend on a cedega subscription if I have troubles getting it running, it's just I would like to get it running on wine because I want to support the wine project and cedega is really buggy with feisty. :mad:

Anyway thanks again.

EDIT: Oh and how bad is the visual quality? All screenshots I've seen look pretty good to me, like windows. That's why i was asking for a screenshot, I was just curious to see how bad it was.

---

### Post by Enverex on 2007-05-13
Running things on Wine doesn't really help the Wine project, infact it usually slows it down due to devs being flooded with stupid questions, but what does help is people buying copies of Crossover or actually coding for Wine and fixing bugs, heh (sorry if that sounded blunt, the amount of accounts I've had to reject on the AppDB lately from people that thought they were helping by submitting complete rubbish...).

---

### Post by lordhebe on 2007-05-13
> **Enverex said:**
> Running things on Wine doesn't really help the Wine project, infact it usually slows it down due to devs being flooded with stupid questions, but what does help is people buying copies of Crossover or actually coding for Wine and fixing bugs, heh (sorry if that sounded blunt, the amount of accounts I've had to reject on the AppDB lately from people that thought they were helping by submitting complete rubbish...).

No offense taken, because I know that I'm not one of the people you are referring to, my wineHQ account is still active, and I am careful not to post bullcrap, i simply share my experiences with others in an attempt to help the user as much as possible. I can't imagine how this could harm the wine project.

BTW I can't code for peanuts, so that's not an option.

Once again though, thanks for your advice on the game.

---

### Post by robgig1088 on 2007-05-13
Hey guys, I've been getting some glitches in the game (as expected) but I just wanted to confirm that they are wine bugs and not because I'm using hte Nvidia beta driver.

1.  Not all textures load for the trees.  Some leaves/branches are black and it looks really bad. (similar to the Nvidia "black window" bug?)
2.  Tree sprites randomly appear in the place of grass.  Turning off the grass solves the issue.
3.  Lower fps when it rains? (maybe this is my imagination?)
4.  FBO and PBuffer mess up equally with 0.9.37 (see #2)

---

### Post by Mongoose on 2007-05-14
Music works now since 0.9.37.  The static issue is pretty much fixed too.  I can't hear it on my speaker setup anymore anyway with the sound update.  Movies work just fine if you read the guide, and don't do something stupid like delete your movie files -- which was a famous suggestion here for a while.

---

### Post by Mongoose on 2007-05-14
bastiegast: The savegame bug is an Oblivion bug if you're referring to the 'guard bug'.  Any 
changes you make to wine can't fix it.  I have never had the bug in Wine or Windows for a reason that's easy to guess.  Also I forgot to metion I ended up turning the music back off after testing it out once.  It got pretty annoying.  ;)

Enverex: Given his hardware he wouldn't be using HDR that much anyway.  Disabling a couple of shaders he may be able to get a steady 30fps.  If you 'keep waiting' you'll always be waiting at that point.  Even Windows players tweak their settings for performance over visual quality -- especially on the lower end cards.  Also just because you're involved with QA doesn't mean your experience is going to be the same as someone on different hardware -- or even better someone with different practices when it comes to settings.

---

### Post by Mongoose on 2007-05-14
Are you suggesting running Oldblivion under wine then?  Since that doesn't even work as well as tweaking the ini you have no point to make there.  That's what my post was about.  You want kids to file bugs on Oldblivion instead of Oblivion now?  That would be pretty funny since that hack doesn't work properly under Wine.  Maybe you should learn to read the posts too.

---

### Post by bastiegast on 2007-05-14
I'm not referring to the guard bug as I'm sure there are no guards involved here, I'm referring to this: [http://bugs.winehq.org/show_bug.cgi?id=8128](http://bugs.winehq.org/show_bug.cgi?id=8128)

And if you look at the comments at appdb you'll find I'm not the only one having this problem :)

Edit: Oh and you say music works, you mean with the setup from the guide? Because I still experience static and I don't hear any music, yes I enabled music in the ini file and I checked if the music volume slider in Oblivion was up.

---

### Post by Mongoose on 2007-05-14
Yes, since 0.9.37 music will work even on the laucher and intro movies correctly as well as in game.  It was pretty nice to load Oblivion up and see the main menu movie with full music, etc.  

As for your bug, I thought you were referring to the corrupt saves caused by some mods and the SI expansion.   I haven't had time to load up Oblivion aside from checking out the music to remember if they have a new patch out for it at BethSoft.

---

### Post by Cercer on 2007-05-14
> **robgig1088 said:**
> Well, I got it working.  I just renamed my Video directory and it worked.  :guitar:

I've just got the same problem. Could you please clarify what you mean by "renamed my Video directory"?

Thanks in advance

---

### Post by Enverex on 2007-05-14
> **Cercer said:**
> I've just got the same problem. Could you please clarify what you mean by "renamed my Video directory"?

Thanks in advance

In the Data folder in your Oblivion install is a folder called Videos that... has the videos in it. S/He renamed it.

---

### Post by bastiegast on 2007-05-14
I'm all excited the sound is finally working and I can't wait to check it out, but somehow nothing changed for me. I upgraded/completely removed + reinstalled wine just to be sure but still static, no music and the game crashes if I try to enable the intro movies.
Should I make a fresh fake C drive and move oblivion there or something? What have I got wrong?

---

### Post by Enverex on 2007-05-14
> **bastiegast said:**
> I'm all excited the sound is finally working and I can't wait to check it out, but somehow nothing changed for me. I upgraded/completely removed + reinstalled wine just to be sure but still static, no music and the game crashes if I try to enable the intro movies.
Should I make a fresh fake C drive and move oblivion there or something? What have I got wrong?

What version of Wine are you using? You should be on 0.9.37.

---

### Post by robgig1088 on 2007-05-14
I have 0.9.37 and I get static still as well.  I tried messing with the settings but it doesn't do much.  Strangely, the static only appears in certain areas (it appears outside Weynon Priory but not inside the building).  Strange...

---

### Post by bastiegast on 2007-05-15
> **Enverex said:**
> What version of Wine are you using? You should be on 0.9.37.

yup 0.9.37

---

### Post by blakecraw on 2007-05-15
I was able to install and patch without a hitch, but when I run Oblivion it starts, but is basically unplayable. The screen is really dark, the play is choppy (maybe 5 fps in the first prison) and of course there's the static : )
-I am pretty sure the video trouble isn't due to my hardware, as it can run Oblivion fine in windows and even cedega. 

I had to rename Data/Video to Data/Videos for it to start at all (it crashed after the launcher before I did that) and I did copy the d3dx9_27.dll file from my windows partition. Other than that, I think I did a standard installation. 

I attatched the error output since its huge

Using wine 0.9.37

Thanks for any help

---

### Post by Mongoose on 2007-05-16
blakecraw: Renaming your video folder is not recommended.  You can remove the single problem logo movie and fix that crash -- read the guide.  Then the movies in the intro, game, and main menu will continue to work.  If you don't want to see any videos edit the ini file to disable them -- altering the video directory may lead to other bugs in itself.  Every other movie in the game works just fine.  I would suggest reading the wiki and trying that before asking for help.  You should follow the guide and get it running then modify it as you like.

Just to wrap up -- removing data from the game isn't as smart as simply editing the ini to disable the feature.  Using a supported interface is safe, but hacky workarounds are more likely to cause trouble with future patches and mods.

---

### Post by Death_Sargent on 2007-05-16
you know its probubly just the fact feisty reinstalls dash.

remove dash and cedega runs fine

---

### Post by blakecraw on 2007-05-16
Sorry bout not being up to date, I had followed the forum's install guide, not the wiki. I went over to the wiki and followed it, but I'm still having some trouble:

I put my Video folder back the way it was and used the ini tweak, which worked great.

If I try to start a new game, and skip the emperor's speech via escape, the game crashes. If I watch that entire video, I can create a character and play, and the graphics are really good now, at least when I stand still, but the game is really choppy (maybe 5 fps). If I load a save game from just after character creation, it works most of the time, but occasionally crashes when trying to load. Additionally, if I pause the game by pressing escape, the screen behind the pause menu is solid green, and the mouse lags a lot, so much that it's almost impossible to navigate the menu.

One more thing, I can only run the game with OffscreenRenderingMode set to pbuffer or backbuffer, fbo causes the game to crash.

I attatched the error output from when I try to skip the emperor's speech.

---

### Post by Mongoose on 2007-05-17
Yes, pbuffer is recommended on the wiki.  Try disabling the 'water shader' and refraction shaders for massive speed boosts and rendering improvements.  That changed several versions back in the wiki.  As always getting a game working in wine isn't the same as keeping it working in wine -- you'll often have to change your settings as new versions come out.

Yes, #!/bin/bash always helps.  The wiki scripts should all be able to run in sh last I checked.

---

### Post by Rafael, Jr. on 2007-05-17
Hi, I followed your instructions and it works!  Like it did on windows.  I'm running wine 0.9.37 and applied the latest patch 1.2.0146 of oblivion.  I have an Intel P4 2.66mhz with Nvidia 6800 128m and 2 gis of ram.

I deleted the .wine directory and upgraded to latest wine version then followed your instructions.  Finally worked where I was failing before.

I have a problem.  It seems like my character is nearsighted, because I cannot see any enemies until they're right up on me.  Makes it hard to sneak up on people.  any way around this?

---

### Post by Enverex on 2007-05-17
Have you tried increasing the option setting in game to increase the draw distance for whatever that would come under?

---

### Post by Rafael, Jr. on 2007-05-17
I think I fixed it by using the actor fade control on the video options.  Thanks for the reply.

---

### Post by Megatog615 on 2007-05-17
I'm getting the page fault when I try to run the game with the "Play" button.

---

### Post by bastiegast on 2007-05-18
> **Megatog615 said:**
> I'm getting the page fault when I try to run the game with the "Play" button.

Did you bother reading the guide? It says clearly you should disable the videos in your ini file.

---

### Post by Megatog615 on 2007-05-19
I did. I even deleted the folder and still receive the error.

Here it is:
```
wine: Unhandled page fault on read access to 0x00000000 at address 0x498609 (thread 0010), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00498609).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00498609 ESP:0034f448 EBP:013b6888 EFLAGS:00010202(   - 00      - -RI1)
 EAX:00000000 EBX:013b6418 ECX:00001001 EDX:12001401
 ESI:00000000 EDI:013b6618
Stack dump:
0x0034f448:  00000001 00000016 00080000 00000003
0x0034f458:  00000071 40c8f2cb 0034f9b7 00020024
0x0034f468:  00000000 00400000 00000000 013b6b0c
0x0034f478:  00000000 00000000 00000000 00000000
0x0034f488:  00000000 00000000 00000000 00000000
0x0034f498:  02c3cc86 7bc7f6f4 00183d18 0000000a
Backtrace:
=>1 0x00498609 in oblivion (+0x98609) (0x013b6888)
  2 0x00000000 (0x00000001)
  3 0x00000000 (0x00000000)
0x00498609: movl        0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (95 modules)
PE        400000-  baf000       Export          oblivion
PE        bb0000-  dff000       Deferred        d3dx9_27
PE      18000000-18068000       Deferred        binkw32
ELF     7b800000-7b930000       Deferred        kernel32<elf>
  \-PE  7b820000-7b930000       \               kernel32
ELF     7bc00000-7bc9b000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc9b000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cbe1000-7cc61000       Deferred        libglu.so.1
ELF     7cc78000-7cd4f000       Deferred        wined3d<elf>
  \-PE  7cc90000-7cd4f000       \               wined3d
ELF     7cd4f000-7cd7b000       Deferred        d3d9<elf>
  \-PE  7cd60000-7cd7b000       \               d3d9
ELF     7d00d000-7d023000       Deferred        midimap<elf>
  \-PE  7d010000-7d023000       \               midimap
ELF     7d023000-7d04a000       Deferred        msacm32<elf>
  \-PE  7d030000-7d04a000       \               msacm32
ELF     7d04a000-7d10f000       Deferred        libasound.so.2
ELF     7d10f000-7d144000       Deferred        winealsa<elf>
  \-PE  7d120000-7d144000       \               winealsa
ELF     7d144000-7d177000       Deferred        uxtheme<elf>
  \-PE  7d150000-7d177000       \               uxtheme
ELF     7d3fc000-7d408000       Deferred        libgcc_s.so.1
ELF     7d408000-7d420000       Deferred        msacm32<elf>
  \-PE  7d410000-7d420000       \               msacm32
ELF     7d420000-7d429000       Deferred        libxcursor.so.1
ELF     7d429000-7d446000       Deferred        imm32<elf>
  \-PE  7d430000-7d446000       \               imm32
ELF     7d446000-7d44c000       Deferred        libxrandr.so.2
ELF     7d44c000-7d44f000       Deferred        libxinerama.so.1
ELF     7d990000-7d992000       Deferred        libnvidia-tls.so.1
ELF     7d992000-7e304000       Deferred        libglcore.so.1
ELF     7e304000-7e398000       Deferred        libgl.so.1
ELF     7e398000-7e39d000       Deferred        libxdmcp.so.6
ELF     7e39d000-7e3a0000       Deferred        libxau.so.6
ELF     7e3a0000-7e491000       Deferred        libx11.so.6
ELF     7e491000-7e49f000       Deferred        libxext.so.6
ELF     7e49f000-7e4a4000       Deferred        libxxf86vm.so.1
ELF     7e4a4000-7e4bc000       Deferred        libice.so.6
ELF     7e4bc000-7e4c5000       Deferred        libsm.so.6
ELF     7e4c5000-7e4ca000       Deferred        libxfixes.so.3
ELF     7e4ca000-7e4d2000       Deferred        libxrender.so.1
ELF     7e4dc000-7e57c000       Deferred        winex11<elf>
  \-PE  7e4f0000-7e57c000       \               winex11
ELF     7e615000-7e635000       Deferred        libexpat.so.1
ELF     7e635000-7e660000       Deferred        libfontconfig.so.1
ELF     7e660000-7e674000       Deferred        libz.so.1
ELF     7e674000-7e6df000       Deferred        libfreetype.so.6
ELF     7e6f6000-7e761000       Deferred        msvcrt<elf>
  \-PE  7e710000-7e761000       \               msvcrt
ELF     7e761000-7e790000       Deferred        ws2_32<elf>
  \-PE  7e770000-7e790000       \               ws2_32
ELF     7e790000-7e7aa000       Deferred        wsock32<elf>
  \-PE  7e7a0000-7e7aa000       \               wsock32
ELF     7e7aa000-7e7c4000       Deferred        version<elf>
  \-PE  7e7b0000-7e7c4000       \               version
ELF     7e7c4000-7e81f000       Deferred        shlwapi<elf>
  \-PE  7e7d0000-7e81f000       \               shlwapi
ELF     7e81f000-7e91e000       Deferred        shell32<elf>
  \-PE  7e830000-7e91e000       \               shell32
ELF     7e91e000-7e96a000       Deferred        dsound<elf>
  \-PE  7e930000-7e96a000       \               dsound
ELF     7e96a000-7e9fa000       Deferred        winmm<elf>
  \-PE  7e980000-7e9fa000       \               winmm
ELF     7e9fa000-7ea0d000       Deferred        libresolv.so.2
ELF     7ea0d000-7ea2c000       Deferred        iphlpapi<elf>
  \-PE  7ea10000-7ea2c000       \               iphlpapi
ELF     7ea2c000-7ea83000       Deferred        rpcrt4<elf>
  \-PE  7ea40000-7ea83000       \               rpcrt4
ELF     7ea83000-7eb29000       Deferred        ole32<elf>
  \-PE  7ea90000-7eb29000       \               ole32
ELF     7eb29000-7eb61000       Deferred        dinput<elf>
  \-PE  7eb30000-7eb61000       \               dinput
ELF     7eb61000-7eb7a000       Deferred        dinput8<elf>
  \-PE  7eb70000-7eb7a000       \               dinput8
ELF     7eb7a000-7ebc3000       Deferred        advapi32<elf>
  \-PE  7eb90000-7ebc3000       \               advapi32
ELF     7ebc3000-7ec5e000       Deferred        gdi32<elf>
  \-PE  7ebe0000-7ec5e000       \               gdi32
ELF     7ec5e000-7edaa000       Deferred        user32<elf>
  \-PE  7ec80000-7edaa000       \               user32
ELF     7edaa000-7ee7b000       Deferred        comctl32<elf>
  \-PE  7edb0000-7ee7b000       \               comctl32
ELF     7ee7b000-7ee86000       Deferred        libnss_files.so.2
ELF     7ee86000-7ee90000       Deferred        libnss_nis.so.2
ELF     7ee90000-7ee99000       Deferred        libnss_compat.so.2
ELF     7ee9c000-7eeb0000       Deferred        lz32<elf>
  \-PE  7eea0000-7eeb0000       \               lz32
ELF     7efc2000-7efe9000       Deferred        libm.so.6
ELF     7efe9000-7f000000       Deferred        libnsl.so.1
ELF     b7cb7000-b7cbb000       Deferred        libdl.so.2
ELF     b7cbb000-b7dfc000       Deferred        libc.so.6
ELF     b7dfd000-b7e14000       Deferred        libpthread.so.0
ELF     b7e2b000-b7f3d000       Deferred        libwine.so.1
ELF     b7f3f000-b7f5a000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000f (D) C:\Program Files\Bethesda Softworks\Oblivion\Oblivion.exe
        00000012   15
        00000011    0
        00000010    0 <==
0000000b 
        0000000e    0
        0000000c    0

```

---

### Post by bastiegast on 2007-05-19
First I thought you might not have copied d3dx9_27.dll but I tried renaming my own and got a different error message. 

You do need to provide a little more information: What kind of video card do you have? Wine version? Do you have recent video drivers installed?

---

### Post by Mblackwell on 2007-05-19
If you don't have more recent or the most recent video drivers installed and the latest Wine you're going to have some issues.

Also without the latest Wine you may (or must) disable music to prevent crashes.

---

### Post by Cappy on 2007-05-19
Everything is updated but I crash whenever I go into viewing range of a Oblivion gates. It doesn't crash if I save outside before I see the gate and then reload.
I tried turning off the Refraction shader but it is still happening.
bForce1XShaders is off also.
Running the 64-bit OS on my signature.

---

### Post by Megatog615 on 2007-05-19
NVIDIA Geforce 7800GT, 9755 Drivers.
Wine 0.9.37

---

### Post by bastiegast on 2007-05-19
> **Megatog615 said:**
> NVIDIA Geforce 7800GT, 9755 Drivers.
Wine 0.9.37

At the moment I'm afraid I have no idea what could be wrong and I can only urge you to triple check if you have all your settings exactly as in the guide/wiki. Also have a look on [http://appdb.winehq.org/appview.php?iVersionId=5777]("http://appdb.winehq.org/appview.php?iVersionId=5777") you might find some helpful information there.

---

### Post by Megatog615 on 2007-05-19
I have actually posted a comment for [Bug 6740](http://bugs.winehq.org/show_bug.cgi?id=6740), #7.

---

### Post by Enverex on 2007-05-19
You are using a NoCD patch right?

---

### Post by Megatog615 on 2007-05-19
No. I mounted the iso image I've created from my original DVD. It gets past the disc check(otherwise it asks for the disc).

---

### Post by Enverex on 2007-05-20
> **Megatog615 said:**
> No. I mounted the iso image I've created from my original DVD. It gets past the disc check(otherwise it asks for the disc).

Try using one anyway, most copy protections don't work in Wine, even if sometimes it appears that they do.

---

### Post by xokmillzo on 2007-05-20
Hey I am pretty new to wine and am having some difficulty with this guide. I followed it to the letter however whenever I run the game it crashes no menue no nothing the launcher works fine and I can change setings but nothing else works and if i hit play it crashes I will post the wine output and my ini file below. If anyone could help that would be really great.
PS I made the reccomended changees to the ini and have teh reg keys exactally the way the guide states
also my wine version is
wine-0.9.37
ps
I meet all the system requirements and can run the game on windows I have a geforce 6800gt 1gig of ram a 2.0ghz processor ect ect.
Wine Output
```
xavier@xavier-desktop:~$ wine /media/hdb1/TES/obvlin/Oblivion.exe
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:mixer:ALSA_MixerInit No master control found, disabling mixer
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D16
fixme:d3d:IWineD3DDeviceImpl_SetMultithreaded No thread safety in wined3d yet
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1d14b0) : stub, simulating 256MB for now, returning 256MB left
wine: Unhandled page fault on read access to 0x00000004 at address 0x58dc7c (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000004 in 32-bit code (0x0058dc7c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0058dc7c ESP:0033e64c EBP:00000000 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000000 ECX:6034a759 EDX:ffffffff
 ESI:00000000 EDI:00a691d8
Stack dump:
0x0033e64c:  00000000 00000000 60074101 1f001a5c
0x0033e65c:  1b000f28 00000000 00000000 0033e998
0x0033e66c:  7bc435c6 0033ea14 7bc95d20 15000a14
0x0033e67c:  00a691d8 00002800 00000000 00000000
0x0033e68c:  00000000 600742c9 00802431 0033e80c
0x0033e69c:  00000000 600741fd 00000208 0033ea14
Backtrace:
=>1 0x0058dc7c in oblivion (+0x18dc7c) (0x00000000)
0x0058dc7c: movl        0x4(%ebp),%ecx
Modules:
Module  Address                 Debug info      Name (97 modules)
PE        400000-  baf000       Export          oblivion
PE        bb0000-  dff000       Deferred        d3dx9_27
PE      18000000-18068000       Deferred        binkw32
ELF     7b800000-7b927000       Deferred        kernel32<elf>
  \-PE  7b820000-7b927000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7ca89000-7cb09000       Deferred        libglu.so.1
ELF     7cb09000-7cbce000       Deferred        wined3d<elf>
  \-PE  7cb20000-7cbce000       \               wined3d
ELF     7cbce000-7cbfa000       Deferred        d3d9<elf>
  \-PE  7cbe0000-7cbfa000       \               d3d9
ELF     7cf51000-7cf66000       Deferred        midimap<elf>
  \-PE  7cf60000-7cf66000       \               midimap
ELF     7cf66000-7cf8c000       Deferred        msacm32<elf>
  \-PE  7cf70000-7cf8c000       \               msacm32
ELF     7cf8c000-7d051000       Deferred        libasound.so.2
ELF     7d051000-7d082000       Deferred        winealsa<elf>
  \-PE  7d060000-7d082000       \               winealsa
ELF     7d082000-7d0be000       Deferred        wineoss<elf>
  \-PE  7d090000-7d0be000       \               wineoss
ELF     7d0be000-7d0f0000       Deferred        uxtheme<elf>
  \-PE  7d0d0000-7d0f0000       \               uxtheme
ELF     7d398000-7d3b0000       Deferred        msacm32<elf>
  \-PE  7d3a0000-7d3b0000       \               msacm32
ELF     7d3b2000-7d3b7000       Deferred        libxfixes.so.3
ELF     7d3b7000-7d3c0000       Deferred        libxcursor.so.1
ELF     7d3c0000-7d3dd000       Deferred        imm32<elf>
  \-PE  7d3d0000-7d3dd000       \               imm32
ELF     7d3dd000-7d3e3000       Deferred        libxrandr.so.2
ELF     7d3e3000-7d3eb000       Deferred        libxrender.so.1
ELF     7d3eb000-7d3ee000       Deferred        libxinerama.so
ELF     7d91b000-7d91d000       Deferred        libnvidia-tls.so.1
ELF     7d91d000-7e28f000       Deferred        libglcore.so.1
ELF     7e28f000-7e323000       Deferred        libgl.so.1
ELF     7e323000-7e328000       Deferred        libxdmcp.so.6
ELF     7e328000-7e32b000       Deferred        libxau.so.6
ELF     7e32b000-7e41c000       Deferred        libx11.so.6
ELF     7e41c000-7e42a000       Deferred        libxext.so.6
ELF     7e42a000-7e42f000       Deferred        libxxf86vm.so.1
ELF     7e42f000-7e447000       Deferred        libice.so.6
ELF     7e447000-7e450000       Deferred        libsm.so.6
ELF     7e450000-7e4df000       Deferred        winex11<elf>
  \-PE  7e460000-7e4df000       \               winex11
ELF     7e54d000-7e56d000       Deferred        libexpat.so.1
ELF     7e56d000-7e598000       Deferred        libfontconfig.so.1
ELF     7e598000-7e5ac000       Deferred        libz.so.1
ELF     7e5ac000-7e617000       Deferred        libfreetype.so.6
ELF     7e617000-7e644000       Deferred        ws2_32<elf>
  \-PE  7e620000-7e644000       \               ws2_32
ELF     7e644000-7e65e000       Deferred        wsock32<elf>
  \-PE  7e650000-7e65e000       \               wsock32
ELF     7e65e000-7e6c5000       Deferred        msvcrt<elf>
  \-PE  7e670000-7e6c5000       \               msvcrt
ELF     7e6c5000-7e6d9000       Deferred        lz32<elf>
  \-PE  7e6d0000-7e6d9000       \               lz32
ELF     7e6d9000-7e6f2000       Deferred        version<elf>
  \-PE  7e6e0000-7e6f2000       \               version
ELF     7e6f2000-7e74a000       Deferred        shlwapi<elf>
  \-PE  7e700000-7e74a000       \               shlwapi
ELF     7e74a000-7e845000       Deferred        shell32<elf>
  \-PE  7e760000-7e845000       \               shell32
ELF     7e845000-7e88e000       Deferred        dsound<elf>
  \-PE  7e850000-7e88e000       \               dsound
ELF     7e88e000-7e91d000       Deferred        winmm<elf>
  \-PE  7e8a0000-7e91d000       \               winmm
ELF     7e91d000-7e930000       Deferred        libresolv.so.2
ELF     7e930000-7e94e000       Deferred        iphlpapi<elf>
  \-PE  7e940000-7e94e000       \               iphlpapi
ELF     7e94e000-7e9a3000       Deferred        rpcrt4<elf>
  \-PE  7e960000-7e9a3000       \               rpcrt4
ELF     7e9a3000-7ea40000       Deferred        ole32<elf>
  \-PE  7e9b0000-7ea40000       \               ole32
ELF     7ea40000-7ea76000       Deferred        dinput<elf>
  \-PE  7ea50000-7ea76000       \               dinput
ELF     7ea76000-7ea8f000       Deferred        dinput8<elf>
  \-PE  7ea80000-7ea8f000       \               dinput8
ELF     7ea8f000-7ead6000       Deferred        advapi32<elf>
  \-PE  7eaa0000-7ead6000       \               advapi32
ELF     7ead6000-7eae2000       Deferred        libgcc_s.so.1
ELF     7ebdd000-7ec9c000       Deferred        gdi32<elf>
  \-PE  7ebf0000-7ec9c000       \               gdi32
ELF     7ec9c000-7edd8000       Deferred        user32<elf>
  \-PE  7ecc0000-7edd8000       \               user32
ELF     7edd8000-7ee94000       Deferred        comctl32<elf>
  \-PE  7ede0000-7ee94000       \               comctl32
ELF     7efa6000-7efb1000       Deferred        libnss_files.so.2
ELF     7efb1000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efef000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d53000-b7d5c000       Deferred        libnss_compat.so.2
ELF     b7d5d000-b7d61000       Deferred        libdl.so.2
ELF     b7d61000-b7ea2000       Deferred        libc.so.6
ELF     b7ea2000-b7eb9000       Deferred        libpthread.so.0
ELF     b7eca000-b7fdb000       Deferred        libwine.so.1
ELF     b7fdd000-b7ff8000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) E:\TES\obvlin\Oblivion.exe
        00000010    1
        0000000f   15
        0000000e   15
        0000000d    0
        00000009    0 <==
xavier@xavier-desktop:~$ 

```

INI
```
[General]

SStartingCell=



SStartingCellY=

SStartingCellX=

SStartingWorld=



STestFile10=

STestFile9=

STestFile8=

STestFile7=

STestFile6=

STestFile5=

STestFile4=

STestFile3=

STestFile2=

STestFile1=



bEnableProfile=0

bDrawSpellContact=0

bRunMiddleLowLevelProcess=1

iHoursToSleep=3

bActorLookWithHavok=0

SMainMenuMusicTrack=special\tes4title.mp3

bUseEyeEnvMapping=1

bFixFaceNormals=0

bUseFaceGenHeads=1

bFaceMipMaps=1

bFaceGenTexturing=1

bDefaultCOCPlacement=0

uGridDistantTreeRange=15

uGridDistantCount=25

uGridsToLoad=5

fGlobalTimeMultiplier=1.0000

bNewAnimation=1

fAnimationDefaultBlend=0.1000

fAnimationMult=1.0000

bFixAIPackagesOnLoad=0

bForceReloadOnEssentialCharacterDeath=1

bKeepPluginWhenMerging=0

bCreate Maps Enable=0

SLocalSavePath=Saves\

SLocalMasterPath=Data\

bDisableDuplicateReferenceCheck=1

bTintMipMaps=0

uInterior Cell Buffer=3

uExterior Cell Buffer=36

iIntroSequencePriority=3

bPreloadIntroSequence=1

fStaticScreenWaitTime=3.0000

SCreditsMenuMovie=CreditsMenu.bik

SMainMenuMovie=Map loop.bik

SMainMenuMovieIntro=Oblivion iv logo.bik

SIntroSequence=

iFPSClamp=0

bRunVTuneTest=0

STestFile1=

bActivateAllQuestScripts=0

fQuestScriptDelayTime=5.0000

SMainMenuMusic=Special\TES4Title.mp3

bUseThreadedBlood=0

bUseThreadedMorpher=0

bExternalLODDataFiles=1





[Display]

uVideoDeviceIdentifierPart1=0

uVideoDeviceIdentifierPart2=0

uVideoDeviceIdentifierPart3=0

uVideoDeviceIdentifierPart4=0

fDecalLifetime=10.0000

bEquippedTorchesCastShadows=0

bReportBadTangentSpace=0

bStaticMenuBackground=1

bForcePow2Textures=0

bForce1XShaders=0

bHighQuality20Lighting=0

bAllow20HairShader=1

bAllowScreenShot=0

iMultiSample=0

bDoTallGrassEffect=1

bForceMultiPass=1

bDoTexturePass=1

bDoSpecularPass=1

bDoDiffusePass=1

bDoAmbientPass=1

bDoCanopyShadowPass=1

bDrawShadows=0

bUseRefractionShader=1

bUse Shaders=1

iNPatchNOrder=0

iNPatchPOrder=0

iNPatches=0

iLocation Y=0

iLocation X=0

bFull Screen=1

iSize W=640

iSize H=480

iAdapter=0

iScreenShotIndex=0

SScreenShotBaseName=ScreenShot

iAutoViewMinDistance=2000

iAutoViewHiFrameRate=40

iAutoViewLowFrameRate=20

bAutoViewDistance=0

fDefaultFOV=75.0000

fNearDistance=10.0000

fFarDistance=10000.0000

iDebugTextLeftRightOffset=10

iDebugTextTopBottomOffset=10

bShowMenuTextureUse=1

iDebugText=2

bLocalMapShader=1

bDoImageSpaceEffects=1

fShadowLOD2=400.0000

fShadowLOD1=200.0000

fLightLOD2=1500.0000

fLightLOD1=1000.0000

fSpecularLOD2=800.0000

fSpecularLOD1=500.0000

fEnvMapLOD2=800.0000

fEnvMapLOD1=500.0000

fEyeEnvMapLOD2=190.0000

fEyeEnvMapLOD1=130.0000

iPresentInterval=1







[Controls]

fVersion=1.7000

Forward=0011FFFF

Back=001FFFFF

Slide Left=001EFFFF

Slide Right=0020FFFF

Use=00FF00FF

Activate=0039FFFF

Block=003801FF

Cast=002EFFFF

Ready Item=0021FFFF

Crouch/Sneak=001DFFFF

Run=002AFFFF

Always Run=003AFFFF

Auto Move=0010FFFF

Jump=0012FFFF

Toggle POV=001302FF

Menu Mode=000FFFFF

Rest=0014FFFF

Quick Menu=003BFFFF

Quick1=0002FFFF

Quick2=0003FFFF

Quick3=0004FFFF

Quick4=0005FFFF

Quick5=0006FFFF

Quick6=0007FFFF

Quick7=0008FFFF

Quick8=0009FFFF

QuickSave=003FFFFF

QuickLoad=0043FFFF

Grab=002CFFFF

bInvertYValues=0

fXenonLookXYMult=0.0005

fMouseSensitivity=0.0020

;X = 1, Y = 2, Z = 3, XRot = 4, YRot = 5, ZRot = 6

iJoystickMoveFrontBack=2

iJoystickMoveLeftRight=1

fJoystickMoveFBMult=1.0000

fJoystickMoveLRMult=1.0000

iJoystickLookUpDown=6

iJoystickLookLeftRight=3

fJoystickLookUDMult=0.0020

fJoystickLookLRMult=0.0020

fXenonMenuMouseXYMult=0.0003

bBackground Mouse=0

bBackground Keyboard=0

bUse Joystick=0

fXenonLookMult=0.0030

fXenonMenuStickSpeedMaxMod=5.0000

iXenonMenuStickSpeedThreshold=20000

iXenonMenuStickThreshold=1000

;Language values: 0-English, 1-German, 2-French, 3-Spanish, 4-Italian

iLanguage=0





[Water]

fAlpha=0.5000

uSurfaceTextureSize=128

SSurfaceTexture=water

SNearWaterOutdoorID=NearWaterOutdoorLoop

SNearWaterIndoorID=NearWaterIndoorLoop

fNearWaterOutdoorTolerance=1024.0000

fNearWaterIndoorTolerance=512.0000

fNearWaterUnderwaterVolume=0.9000

fNearWaterUnderwaterFreq=0.3000

uNearWaterPoints=8

uNearWaterRadius=1000

uSurfaceFrameCount=32

uSurfaceFPS=12

bUseWaterReflectionsMisc=0

bUseWaterReflectionsStatics=0

bUseWaterReflectionsTrees=0

bUseWaterReflectionsActors=0

bUseWaterReflections=1

bUseWaterHiRes=0

bUseWaterDisplacements=1

bUseWaterShader=0

uDepthRange=125

bUseWaterDepth=1

bUseWaterLOD=1

fTileTextureDivisor=4.7500

fSurfaceTileSize=2048.0000



[Audio]

bDSoundHWAcceleration=1

fMinSoundVel=10.0000

fMetalLargeMassMin=25.0000

fMetalMediumMassMin=8.0000

fStoneLargeMassMin=30.0000

fStoneMediumMassMin=5.0000

fWoodLargeMassMin=15.0000

fWoodMediumMassMin=7.0000

fDialogAttenuationMax=35.0000

fDialogAttenuationMin=7.7500

bUseSoundDebugInfo=1

fUnderwaterFrequencyDelta=0.0000

bUseSoftwareAudio3D=0

fDefaultEffectsVolume=0.8000

fDefaultMusicVolume=0.3000

fDefaultFootVolume=0.8000

fDefaultVoiceVolume=0.8000

fDefaultMasterVolume=1.0000

bMusicEnabled=0

bSoundEnabled=1

fLargeWeaponWeightMin=25.0000

fMediumWeaponWeightMin=8.0000

fSkinLargeMassMin=30.0000

fSkinMediumMassMin=5.0000

fChainLargeMassMin=30.0000

fChainMediumMassMin=5.0000

fDBVoiceAttenuationIn2D=0.0000

iCollisionSoundTimeDelta=50

fGlassLargeMassMin=25.0000

fGlassMediumMassMin=8.0000

fClothLargeMassMin=25.0000

fClothMediumMassMin=8.0000

fEarthLargeMassMin=30.0000

fEarthMediumMassMin=5.0000

bUseSpeedForWeaponSwish=1

fLargeWeaponSpeedMax=0.9500

fMediumWeaponSpeedMax=1.1000

fPlayerFootVolume=0.9000

fDSoundRolloffFactor=4.0000

fMaxFootstepDistance=1100.0000

fHeadroomdB=2.0000

iMaxImpactSoundCount=32

fMainMenuMusicVolume=0.6





[ShockBolt]

bDebug=0

fGlowColorB=1.0000

fGlowColorG=0.6000

fGlowColorR=0.0000

fCoreColorB=1.0000

fCoreColorG=1.0000

fCoreColorR=1.0000

fCastVOffset=-10.0000

iNumBolts=7

fBoltGrowWidth=1.0000

fBoltSmallWidth=3.0000

fTortuosityVariance=8.0000

fSegmentVariance=35.0000

fBoltsRadius=24.0000



[Pathfinding]

bDrawPathsDefault=0

bPathMovementOnly=0

bDrawSmoothFailures=0

bDebugSmoothing=0

bSmoothPaths=1

bSnapToAngle=0

bDebugAvoidance=0

bDisableAvoidance=0

bBackgroundPathing=0



[MAIN]

bEnableBorderRegion=1





[Combat]

bEnableBowZoom=1

bDebugCombatAvoidance=0

fMinBloodDamage=1.0000

fHitVectorDelay=0.4000

iShowHitVector=0





[HAVOK]

bDisablePlayerCollision=0

fJumpAnimDelay=0.75

bTreeTops=0

iSimType=1

bPreventHavokAddAll=0

bPreventHavokAddClutter=0

fMaxTime=0.0167

bHavokDebug=0

fRF=1000.0000

fOD=0.9000

fSE=0.3000

fSD=0.9800

iResetCounter=5

fMoveLimitMass=95.0000

iUpdateType=0

bHavokPick=0





[Interface]

fDlgLookMult=0.3000

fDlgLookAdj=0.0000

fDlgLookDegStop=0.2000

fDlgLookDegStart=2.0000

fDlgFocus=2.1000

fKeyRepeatInterval=50.0000

fKeyRepeatTime=500.0000

fActivatePickSphereRadius=16.0000

fMenuModeAnimBlend=0.0000

iSafeZoneX=20

iSafeZoneY=20

iSafeZoneXWide=20

iSafeZoneYWide=20



[LoadingBar]



[Menu]

fCreditsScrollSpeed=40.0000

iConsoleTextYPos=890

iConsoleTextXPos=30

iConsoleVisibleLines=15

iConsoleHistorySize=50

rDebugTextColor=255,251,233

iConsoleFont=3

iDebugTextFont=3







[GamePlay]

bDisableDynamicCrosshair=0

bSaveOnTravel=1

bSaveOnWait=1

bSaveOnRest=1

bCrossHair=1

iDifficultyLevel=50

bGeneralSubtitles=0

bDialogueSubtitles=1

bInstantLevelUp=0

bHealthBarShowing=0

fHealthBarFadeOutSpeed=1.0000

fHealthBarSpeed=80.0000

fHealthBarHeight=4.0000

fHealthBarWidth=40.0000

fHealthBarEmittanceFadeTime=0.5000

fHealthBarEmittanceTime=1.5000





[Fonts]

SFontFile_1=Data\Fonts\Kingthings_Regular.fnt

SFontFile_2=Data\Fonts\Kingthings_Shadowed.fnt

SFontFile_3=Data\Fonts\Tahoma_Bold_Small.fnt

SFontFile_4=Data\Fonts\Daedric_Font.fnt

SFontFile_5=Data\Fonts\Handwritten.fnt





[SpeedTree]

iTreeClonesAllowed=1

fCanopyShadowGrassMult=1.0000

iCanopyShadowScale=512

fTreeForceMaxBudAngle=-1.0000

fTreeForceMinBudAngle=-1.0000

fTreeForceLeafDimming=-1.0000

fTreeForceBranchDimming=-1.0000

fTreeForceCS=-1.0000

fTreeForceLLA=-1.0000

fTreeLODExponent=1.0000

bEnableTrees=1

bForceFullLOD=0





[Debug]

bDebugFaceGenCriticalSection=0

bDebugFaceGenMultithreading=0

bDebugSaveBuffer=0





[BackgroundLoad]





[LOD]

fLodDistance=500.0000

bUseFaceGenLOD=0

iLODTextureTiling=2

iLODTextureSizePow2=8

fLODNormalTextureBlend=0.5000

bDisplayLODLand=1

bDisplayLODBuildings=1

bDisplayLODTrees=1

bLODPopTrees=0

bLODPopActors=0

bLODPopItems=0

bLODPopObjects=0

fLODFadeOutMultActors=5.0000

fLODFadeOutMultItems=2.0000

fLODFadeOutMultObjects=5.0000

fLODMultLandscape=1.0000

fLODMultTrees=1.2000

fLODMultActors=1.0000

fLODMultItems=1.0000

fLODMultObjects=1.0000

iFadeNodeMinNearDistance=400

fLODFadeOutPercent=0.9000

fLODBoundRadiusMult=3.0000

fTalkingDistance=2000.0000



fTreeLODMax=2.0000

fTreeLODMin=0.0200

fTreeLODDefault=1.2000



[Weather]

fSunGlareSize=350.0000

fSunBaseSize=250.0000

bPrecipitation=1

fAlphaReduce=1.0000

SBumpFadeColor=255,255,255,255

SLerpCloseColor=255,255,255,255

SEnvReduceColor=255,255,255,255



[Voice]

SFileTypeLTF=ltf

SFileTypeLip=lip

SFileTypeSource=wav

SFileTypeGame=mp3





[Grass]

iMinGrassSize=80

fGrassEndDistance=3000.0000

fGrassStartFadeDistance=2000.0000

bGrassPointLighting=0

bDrawShaderGrass=1

iGrassDensityEvalSize=2

iMaxGrassTypesPerTexure=2

fWaveOffsetRange=1.7500



[Landscape]

bCurrentCellOnly=0

bPreventSafetyCheck=0

fLandTextureTilingMult=2.0000





[bLightAttenuation]

fQuadraticRadiusMult=1.0000

fLinearRadiusMult=1.0000

bOutQuadInLin=0

fConstantValue=0.0000

fQuadraticValue=16.0000

fLinearValue=3.0000

uQuadraticMethod=2

uLinearMethod=1

fFlickerMovement=8.0000

bUseQuadratic=1

bUseLinear=0

bUseConstant=0





[BlurShaderHDRInterior]

fTargetLUM=1.0000

fUpperLUMClamp=1.0000

fEmissiveHDRMult=1.0000

fEyeAdaptSpeed=0.5000

fBrightScale=2.2500

fBrightClamp=0.2250

fBlurRadius=7.0000

iNumBlurpasses=1





[BlurShaderHDR]

fTargetLUM=1.2000

fUpperLUMClamp=1.0000

fGrassDimmer=1.3000

fTreeDimmer=1.2000

fEmissiveHDRMult=1.0000

fEyeAdaptSpeed=0.7000

fSunlightDimmer=1.3000

fSIEmmisiveMult=1.0000

fSISpecularMult=1.0000

fSkyBrightness=0.5000

fSunBrightness=0.0000

fBrightScale=1.5000

fBrightClamp=0.350

fBlurRadius=4.0000

iNumBlurpasses=2

iBlendType=2

bDoHighDynamicRange=1





[BlurShader]

fSunlightDimmer=1.0000

fSIEmmisiveMult=1.0000

fSISpecularMult=1.0000

fSkyBrightness=0.5000

fSunBrightness=0.0000

fAlphaAddExterior=0.2000

fAlphaAddInterior=0.5000

iBlurTexSize=256

fBlurRadius=0.0300

iNumBlurpasses=1

iBlendType=2





[GethitShader]

fBlurAmmount=0.5000

fBlockedTexOffset=0.0010

fHitTexOffset=0.0050

[MESSAGES]

bBlockMessageBoxes=0

bSkipProgramFlows=1

bAllowYesToAll=1

bDisableWarning=1

iFileLogging=0

[DistantLOD]

bUseLODLandData=0

fFadeDistance=12288.0000

[GeneralWarnings]

SGeneralMasterMismatchWarning=One or more plugins could not find the correct versions of the master files they depend on. Errors may occur during load or game play. Check the "Warnings.txt" file for more information.



SMasterMismatchWarning=One of the files that "%s" is dependent on has changed since the last save.

This may result in errors. Saving again will clear this message

but not necessarily fix any errors.



[Archive]

SMasterMiscArchiveFileName=Oblivion - Misc.bsa

SMasterVoicesArchiveFileName2=Oblivion - Voices2.bsa

SMasterVoicesArchiveFileName1=Oblivion - Voices1.bsa

SMasterSoundsArchiveFileName=Oblivion - Sounds.bsa

SMasterTexturesArchiveFileName1=Oblivion - Textures - Compressed.bsa

SMasterMeshesArchiveFileName=Oblivion - Meshes.bsa

SInvalidationFile=ArchiveInvalidation.txt

iRetainFilenameOffsetTable=1

iRetainFilenameStringTable=1

iRetainDirectoryStringTable=1

bCheckRuntimeCollisions=0

bInvalidateOlderFiles=1

bUseArchives=1

[CameraPath]

iTake=0

SDirectoryName=TestCameraPath

iFPS=60

SNif=Test\CameraPath.nif

[Absorb]

fAbsorbGlowColorB=1.0000

fAbsorbGlowColorG=0.6000

fAbsorbGlowColorR=0.0000

fAbsorbCoreColorB=1.0000

fAbsorbCoreColorG=1.0000

fAbsorbCoreColorR=1.0000

iAbsorbNumBolts=1

fAbsorbBoltGrowWidth=0.0000

fAbsorbBoltSmallWidth=7.0000

fAbsorbTortuosityVariance=2.0000

fAbsorbSegmentVariance=7.0000

fAbsorbBoltsRadius=5.0000

[OPENMP]

iThreads=3

iOpenMPLevel=10

[TestAllCells]

bFileShowTextures=1

bFileShowIcons=1

bFileSkipIconChecks=0

bFileTestLoad=0

bFileNeededMessage=1

bFileGoneMessage=1

bFileSkipModelChecks=0

[CopyProtectionStrings]

SCopyProtectionMessage2=Insert the Oblivion Disc.

SCopyProtectionTitle2=Oblivion Disc Not Found

SCopyProtectionMessage=Unable to find a CD-ROM/DVD drive on this computer.

SCopyProtectionTitle=CD-ROM Drive Not Found
```

---

### Post by NullHead on 2007-05-23
The wine AppDB is down........:(

---

### Post by Enverex on 2007-05-23
> **NullHead said:**
> The wine apt-db is down........:(

It's "AppDB". Nothing to do with Apt. It's down because of vandalism and someone deciding to try and delete most of it. It should be restored soon.

---

### Post by lordhebe on 2007-05-23
> **Enverex said:**
> It's "AppDB". Nothing to do with Apt. It's down because of vandalism and someone deciding to try and delete most of it. It should be restored soon.

Typo? I think he meant to say App-db

---

### Post by NullHead on 2007-05-23
Yes it was a typo ... sorry for that :redface:

---

### Post by Mongoose on 2007-05-24
Someone vandalized the wiki recently as well.  I guess some asshat doesn't like Linux having nice games too.  ^^

---

### Post by saru411 on 2007-05-24
i will be waiting for someone to fix the wiki/other location before i try to install oblivion again. this might be the reason im having issues in my other posts.

---

### Post by Mongoose on 2007-05-24
The wiki was restored to an earlier version at the time of my comment.

---

### Post by raeb on 2007-05-26
> **xokmillzo said:**
> Hey I am pretty new to wine and am having some difficulty with this guide. I followed it to the letter however whenever I run the game it crashes no menue no nothing the launcher works fine and I can change setings but nothing else works and if i hit play it crashes I will post the wine output and my ini file below. If anyone could help that would be really great.
PS I made the reccomended changees to the ini and have teh reg keys exactally the way the guide states
also my wine version is
wine-0.9.37
ps
I meet all the system requirements and can run the game on windows I have a geforce 6800gt 1gig of ram a 2.0ghz processor ect ect.
Wine Output
```
xavier@xavier-desktop:~$ wine /media/hdb1/TES/obvlin/Oblivion.exe
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:mixer:ALSA_MixerInit No master control found, disabling mixer
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_X4R4G4B4 and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_R16F and WINED3DFMT_D16
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24S8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D24X8
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A16B16G16R16F and WINED3DFMT_D16
fixme:d3d:IWineD3DDeviceImpl_SetMultithreaded No thread safety in wined3d yet
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1d14b0) : stub, simulating 256MB for now, returning 256MB left
wine: Unhandled page fault on read access to 0x00000004 at address 0x58dc7c (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000004 in 32-bit code (0x0058dc7c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0058dc7c ESP:0033e64c EBP:00000000 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000000 ECX:6034a759 EDX:ffffffff
 ESI:00000000 EDI:00a691d8
Stack dump:
0x0033e64c:  00000000 00000000 60074101 1f001a5c
0x0033e65c:  1b000f28 00000000 00000000 0033e998
0x0033e66c:  7bc435c6 0033ea14 7bc95d20 15000a14
0x0033e67c:  00a691d8 00002800 00000000 00000000
0x0033e68c:  00000000 600742c9 00802431 0033e80c
0x0033e69c:  00000000 600741fd 00000208 0033ea14
Backtrace:
=>1 0x0058dc7c in oblivion (+0x18dc7c) (0x00000000)
0x0058dc7c: movl        0x4(%ebp),%ecx
Modules:
Module  Address                 Debug info      Name (97 modules)
PE        400000-  baf000       Export          oblivion
PE        bb0000-  dff000       Deferred        d3dx9_27
PE      18000000-18068000       Deferred        binkw32
ELF     7b800000-7b927000       Deferred        kernel32<elf>
  \-PE  7b820000-7b927000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7ca89000-7cb09000       Deferred        libglu.so.1
ELF     7cb09000-7cbce000       Deferred        wined3d<elf>
  \-PE  7cb20000-7cbce000       \               wined3d
ELF     7cbce000-7cbfa000       Deferred        d3d9<elf>
  \-PE  7cbe0000-7cbfa000       \               d3d9
ELF     7cf51000-7cf66000       Deferred        midimap<elf>
  \-PE  7cf60000-7cf66000       \               midimap
ELF     7cf66000-7cf8c000       Deferred        msacm32<elf>
  \-PE  7cf70000-7cf8c000       \               msacm32
ELF     7cf8c000-7d051000       Deferred        libasound.so.2
ELF     7d051000-7d082000       Deferred        winealsa<elf>
  \-PE  7d060000-7d082000       \               winealsa
ELF     7d082000-7d0be000       Deferred        wineoss<elf>
  \-PE  7d090000-7d0be000       \               wineoss
ELF     7d0be000-7d0f0000       Deferred        uxtheme<elf>
  \-PE  7d0d0000-7d0f0000       \               uxtheme
ELF     7d398000-7d3b0000       Deferred        msacm32<elf>
  \-PE  7d3a0000-7d3b0000       \               msacm32
ELF     7d3b2000-7d3b7000       Deferred        libxfixes.so.3
ELF     7d3b7000-7d3c0000       Deferred        libxcursor.so.1
ELF     7d3c0000-7d3dd000       Deferred        imm32<elf>
  \-PE  7d3d0000-7d3dd000       \               imm32
ELF     7d3dd000-7d3e3000       Deferred        libxrandr.so.2
ELF     7d3e3000-7d3eb000       Deferred        libxrender.so.1
ELF     7d3eb000-7d3ee000       Deferred        libxinerama.so
ELF     7d91b000-7d91d000       Deferred        libnvidia-tls.so.1
ELF     7d91d000-7e28f000       Deferred        libglcore.so.1
ELF     7e28f000-7e323000       Deferred        libgl.so.1
ELF     7e323000-7e328000       Deferred        libxdmcp.so.6
ELF     7e328000-7e32b000       Deferred        libxau.so.6
ELF     7e32b000-7e41c000       Deferred        libx11.so.6
ELF     7e41c000-7e42a000       Deferred        libxext.so.6
ELF     7e42a000-7e42f000       Deferred        libxxf86vm.so.1
ELF     7e42f000-7e447000       Deferred        libice.so.6
ELF     7e447000-7e450000       Deferred        libsm.so.6
ELF     7e450000-7e4df000       Deferred        winex11<elf>
  \-PE  7e460000-7e4df000       \               winex11
ELF     7e54d000-7e56d000       Deferred        libexpat.so.1
ELF     7e56d000-7e598000       Deferred        libfontconfig.so.1
ELF     7e598000-7e5ac000       Deferred        libz.so.1
ELF     7e5ac000-7e617000       Deferred        libfreetype.so.6
ELF     7e617000-7e644000       Deferred        ws2_32<elf>
  \-PE  7e620000-7e644000       \               ws2_32
ELF     7e644000-7e65e000       Deferred        wsock32<elf>
  \-PE  7e650000-7e65e000       \               wsock32
ELF     7e65e000-7e6c5000       Deferred        msvcrt<elf>
  \-PE  7e670000-7e6c5000       \               msvcrt
ELF     7e6c5000-7e6d9000       Deferred        lz32<elf>
  \-PE  7e6d0000-7e6d9000       \               lz32
ELF     7e6d9000-7e6f2000       Deferred        version<elf>
  \-PE  7e6e0000-7e6f2000       \               version
ELF     7e6f2000-7e74a000       Deferred        shlwapi<elf>
  \-PE  7e700000-7e74a000       \               shlwapi
ELF     7e74a000-7e845000       Deferred        shell32<elf>
  \-PE  7e760000-7e845000       \               shell32
ELF     7e845000-7e88e000       Deferred        dsound<elf>
  \-PE  7e850000-7e88e000       \               dsound
ELF     7e88e000-7e91d000       Deferred        winmm<elf>
  \-PE  7e8a0000-7e91d000       \               winmm
ELF     7e91d000-7e930000       Deferred        libresolv.so.2
ELF     7e930000-7e94e000       Deferred        iphlpapi<elf>
  \-PE  7e940000-7e94e000       \               iphlpapi
ELF     7e94e000-7e9a3000       Deferred        rpcrt4<elf>
  \-PE  7e960000-7e9a3000       \               rpcrt4
ELF     7e9a3000-7ea40000       Deferred        ole32<elf>
  \-PE  7e9b0000-7ea40000       \               ole32
ELF     7ea40000-7ea76000       Deferred        dinput<elf>
  \-PE  7ea50000-7ea76000       \               dinput
ELF     7ea76000-7ea8f000       Deferred        dinput8<elf>
  \-PE  7ea80000-7ea8f000       \               dinput8
ELF     7ea8f000-7ead6000       Deferred        advapi32<elf>
  \-PE  7eaa0000-7ead6000       \               advapi32
ELF     7ead6000-7eae2000       Deferred        libgcc_s.so.1
ELF     7ebdd000-7ec9c000       Deferred        gdi32<elf>
  \-PE  7ebf0000-7ec9c000       \               gdi32
ELF     7ec9c000-7edd8000       Deferred        user32<elf>
  \-PE  7ecc0000-7edd8000       \               user32
ELF     7edd8000-7ee94000       Deferred        comctl32<elf>
  \-PE  7ede0000-7ee94000       \               comctl32
ELF     7efa6000-7efb1000       Deferred        libnss_files.so.2
ELF     7efb1000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efef000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d53000-b7d5c000       Deferred        libnss_compat.so.2
ELF     b7d5d000-b7d61000       Deferred        libdl.so.2
ELF     b7d61000-b7ea2000       Deferred        libc.so.6
ELF     b7ea2000-b7eb9000       Deferred        libpthread.so.0
ELF     b7eca000-b7fdb000       Deferred        libwine.so.1
ELF     b7fdd000-b7ff8000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) E:\TES\obvlin\Oblivion.exe
        00000010    1
        0000000f   15
        0000000e   15
        0000000d    0
        00000009    0 <==
xavier@xavier-desktop:~$ 

```

INI
```
[General]

SStartingCell=



SStartingCellY=

SStartingCellX=

SStartingWorld=



STestFile10=

STestFile9=

STestFile8=

STestFile7=

STestFile6=

STestFile5=

STestFile4=

STestFile3=

STestFile2=

STestFile1=



bEnableProfile=0

bDrawSpellContact=0

bRunMiddleLowLevelProcess=1

iHoursToSleep=3

bActorLookWithHavok=0

SMainMenuMusicTrack=special\tes4title.mp3

bUseEyeEnvMapping=1

bFixFaceNormals=0

bUseFaceGenHeads=1

bFaceMipMaps=1

bFaceGenTexturing=1

bDefaultCOCPlacement=0

uGridDistantTreeRange=15

uGridDistantCount=25

uGridsToLoad=5

fGlobalTimeMultiplier=1.0000

bNewAnimation=1

fAnimationDefaultBlend=0.1000

fAnimationMult=1.0000

bFixAIPackagesOnLoad=0

bForceReloadOnEssentialCharacterDeath=1

bKeepPluginWhenMerging=0

bCreate Maps Enable=0

SLocalSavePath=Saves\

SLocalMasterPath=Data\

bDisableDuplicateReferenceCheck=1

bTintMipMaps=0

uInterior Cell Buffer=3

uExterior Cell Buffer=36

iIntroSequencePriority=3

bPreloadIntroSequence=1

fStaticScreenWaitTime=3.0000

SCreditsMenuMovie=CreditsMenu.bik

SMainMenuMovie=Map loop.bik

SMainMenuMovieIntro=Oblivion iv logo.bik

SIntroSequence=

iFPSClamp=0

bRunVTuneTest=0

STestFile1=

bActivateAllQuestScripts=0

fQuestScriptDelayTime=5.0000

SMainMenuMusic=Special\TES4Title.mp3

bUseThreadedBlood=0

bUseThreadedMorpher=0

bExternalLODDataFiles=1





[Display]

uVideoDeviceIdentifierPart1=0

uVideoDeviceIdentifierPart2=0

uVideoDeviceIdentifierPart3=0

uVideoDeviceIdentifierPart4=0

fDecalLifetime=10.0000

bEquippedTorchesCastShadows=0

bReportBadTangentSpace=0

bStaticMenuBackground=1

bForcePow2Textures=0

bForce1XShaders=0

bHighQuality20Lighting=0

bAllow20HairShader=1

bAllowScreenShot=0

iMultiSample=0

bDoTallGrassEffect=1

bForceMultiPass=1

bDoTexturePass=1

bDoSpecularPass=1

bDoDiffusePass=1

bDoAmbientPass=1

bDoCanopyShadowPass=1

bDrawShadows=0

bUseRefractionShader=1

bUse Shaders=1

iNPatchNOrder=0

iNPatchPOrder=0

iNPatches=0

iLocation Y=0

iLocation X=0

bFull Screen=1

iSize W=640

iSize H=480

iAdapter=0

iScreenShotIndex=0

SScreenShotBaseName=ScreenShot

iAutoViewMinDistance=2000

iAutoViewHiFrameRate=40

iAutoViewLowFrameRate=20

bAutoViewDistance=0

fDefaultFOV=75.0000

fNearDistance=10.0000

fFarDistance=10000.0000

iDebugTextLeftRightOffset=10

iDebugTextTopBottomOffset=10

bShowMenuTextureUse=1

iDebugText=2

bLocalMapShader=1

bDoImageSpaceEffects=1

fShadowLOD2=400.0000

fShadowLOD1=200.0000

fLightLOD2=1500.0000

fLightLOD1=1000.0000

fSpecularLOD2=800.0000

fSpecularLOD1=500.0000

fEnvMapLOD2=800.0000

fEnvMapLOD1=500.0000

fEyeEnvMapLOD2=190.0000

fEyeEnvMapLOD1=130.0000

iPresentInterval=1







[Controls]

fVersion=1.7000

Forward=0011FFFF

Back=001FFFFF

Slide Left=001EFFFF

Slide Right=0020FFFF

Use=00FF00FF

Activate=0039FFFF

Block=003801FF

Cast=002EFFFF

Ready Item=0021FFFF

Crouch/Sneak=001DFFFF

Run=002AFFFF

Always Run=003AFFFF

Auto Move=0010FFFF

Jump=0012FFFF

Toggle POV=001302FF

Menu Mode=000FFFFF

Rest=0014FFFF

Quick Menu=003BFFFF

Quick1=0002FFFF

Quick2=0003FFFF

Quick3=0004FFFF

Quick4=0005FFFF

Quick5=0006FFFF

Quick6=0007FFFF

Quick7=0008FFFF

Quick8=0009FFFF

QuickSave=003FFFFF

QuickLoad=0043FFFF

Grab=002CFFFF

bInvertYValues=0

fXenonLookXYMult=0.0005

fMouseSensitivity=0.0020

;X = 1, Y = 2, Z = 3, XRot = 4, YRot = 5, ZRot = 6

iJoystickMoveFrontBack=2

iJoystickMoveLeftRight=1

fJoystickMoveFBMult=1.0000

fJoystickMoveLRMult=1.0000

iJoystickLookUpDown=6

iJoystickLookLeftRight=3

fJoystickLookUDMult=0.0020

fJoystickLookLRMult=0.0020

fXenonMenuMouseXYMult=0.0003

bBackground Mouse=0

bBackground Keyboard=0

bUse Joystick=0

fXenonLookMult=0.0030

fXenonMenuStickSpeedMaxMod=5.0000

iXenonMenuStickSpeedThreshold=20000

iXenonMenuStickThreshold=1000

;Language values: 0-English, 1-German, 2-French, 3-Spanish, 4-Italian

iLanguage=0





[Water]

fAlpha=0.5000

uSurfaceTextureSize=128

SSurfaceTexture=water

SNearWaterOutdoorID=NearWaterOutdoorLoop

SNearWaterIndoorID=NearWaterIndoorLoop

fNearWaterOutdoorTolerance=1024.0000

fNearWaterIndoorTolerance=512.0000

fNearWaterUnderwaterVolume=0.9000

fNearWaterUnderwaterFreq=0.3000

uNearWaterPoints=8

uNearWaterRadius=1000

uSurfaceFrameCount=32

uSurfaceFPS=12

bUseWaterReflectionsMisc=0

bUseWaterReflectionsStatics=0

bUseWaterReflectionsTrees=0

bUseWaterReflectionsActors=0

bUseWaterReflections=1

bUseWaterHiRes=0

bUseWaterDisplacements=1

bUseWaterShader=0

uDepthRange=125

bUseWaterDepth=1

bUseWaterLOD=1

fTileTextureDivisor=4.7500

fSurfaceTileSize=2048.0000



[Audio]

bDSoundHWAcceleration=1

fMinSoundVel=10.0000

fMetalLargeMassMin=25.0000

fMetalMediumMassMin=8.0000

fStoneLargeMassMin=30.0000

fStoneMediumMassMin=5.0000

fWoodLargeMassMin=15.0000

fWoodMediumMassMin=7.0000

fDialogAttenuationMax=35.0000

fDialogAttenuationMin=7.7500

bUseSoundDebugInfo=1

fUnderwaterFrequencyDelta=0.0000

bUseSoftwareAudio3D=0

fDefaultEffectsVolume=0.8000

fDefaultMusicVolume=0.3000

fDefaultFootVolume=0.8000

fDefaultVoiceVolume=0.8000

fDefaultMasterVolume=1.0000

bMusicEnabled=0

bSoundEnabled=1

fLargeWeaponWeightMin=25.0000

fMediumWeaponWeightMin=8.0000

fSkinLargeMassMin=30.0000

fSkinMediumMassMin=5.0000

fChainLargeMassMin=30.0000

fChainMediumMassMin=5.0000

fDBVoiceAttenuationIn2D=0.0000

iCollisionSoundTimeDelta=50

fGlassLargeMassMin=25.0000

fGlassMediumMassMin=8.0000

fClothLargeMassMin=25.0000

fClothMediumMassMin=8.0000

fEarthLargeMassMin=30.0000

fEarthMediumMassMin=5.0000

bUseSpeedForWeaponSwish=1

fLargeWeaponSpeedMax=0.9500

fMediumWeaponSpeedMax=1.1000

fPlayerFootVolume=0.9000

fDSoundRolloffFactor=4.0000

fMaxFootstepDistance=1100.0000

fHeadroomdB=2.0000

iMaxImpactSoundCount=32

fMainMenuMusicVolume=0.6





[ShockBolt]

bDebug=0

fGlowColorB=1.0000

fGlowColorG=0.6000

fGlowColorR=0.0000

fCoreColorB=1.0000

fCoreColorG=1.0000

fCoreColorR=1.0000

fCastVOffset=-10.0000

iNumBolts=7

fBoltGrowWidth=1.0000

fBoltSmallWidth=3.0000

fTortuosityVariance=8.0000

fSegmentVariance=35.0000

fBoltsRadius=24.0000



[Pathfinding]

bDrawPathsDefault=0

bPathMovementOnly=0

bDrawSmoothFailures=0

bDebugSmoothing=0

bSmoothPaths=1

bSnapToAngle=0

bDebugAvoidance=0

bDisableAvoidance=0

bBackgroundPathing=0



[MAIN]

bEnableBorderRegion=1





[Combat]

bEnableBowZoom=1

bDebugCombatAvoidance=0

fMinBloodDamage=1.0000

fHitVectorDelay=0.4000

iShowHitVector=0





[HAVOK]

bDisablePlayerCollision=0

fJumpAnimDelay=0.75

bTreeTops=0

iSimType=1

bPreventHavokAddAll=0

bPreventHavokAddClutter=0

fMaxTime=0.0167

bHavokDebug=0

fRF=1000.0000

fOD=0.9000

fSE=0.3000

fSD=0.9800

iResetCounter=5

fMoveLimitMass=95.0000

iUpdateType=0

bHavokPick=0





[Interface]

fDlgLookMult=0.3000

fDlgLookAdj=0.0000

fDlgLookDegStop=0.2000

fDlgLookDegStart=2.0000

fDlgFocus=2.1000

fKeyRepeatInterval=50.0000

fKeyRepeatTime=500.0000

fActivatePickSphereRadius=16.0000

fMenuModeAnimBlend=0.0000

iSafeZoneX=20

iSafeZoneY=20

iSafeZoneXWide=20

iSafeZoneYWide=20



[LoadingBar]



[Menu]

fCreditsScrollSpeed=40.0000

iConsoleTextYPos=890

iConsoleTextXPos=30

iConsoleVisibleLines=15

iConsoleHistorySize=50

rDebugTextColor=255,251,233

iConsoleFont=3

iDebugTextFont=3







[GamePlay]

bDisableDynamicCrosshair=0

bSaveOnTravel=1

bSaveOnWait=1

bSaveOnRest=1

bCrossHair=1

iDifficultyLevel=50

bGeneralSubtitles=0

bDialogueSubtitles=1

bInstantLevelUp=0

bHealthBarShowing=0

fHealthBarFadeOutSpeed=1.0000

fHealthBarSpeed=80.0000

fHealthBarHeight=4.0000

fHealthBarWidth=40.0000

fHealthBarEmittanceFadeTime=0.5000

fHealthBarEmittanceTime=1.5000





[Fonts]

SFontFile_1=Data\Fonts\Kingthings_Regular.fnt

SFontFile_2=Data\Fonts\Kingthings_Shadowed.fnt

SFontFile_3=Data\Fonts\Tahoma_Bold_Small.fnt

SFontFile_4=Data\Fonts\Daedric_Font.fnt

SFontFile_5=Data\Fonts\Handwritten.fnt





[SpeedTree]

iTreeClonesAllowed=1

fCanopyShadowGrassMult=1.0000

iCanopyShadowScale=512

fTreeForceMaxBudAngle=-1.0000

fTreeForceMinBudAngle=-1.0000

fTreeForceLeafDimming=-1.0000

fTreeForceBranchDimming=-1.0000

fTreeForceCS=-1.0000

fTreeForceLLA=-1.0000

fTreeLODExponent=1.0000

bEnableTrees=1

bForceFullLOD=0





[Debug]

bDebugFaceGenCriticalSection=0

bDebugFaceGenMultithreading=0

bDebugSaveBuffer=0





[BackgroundLoad]





[LOD]

fLodDistance=500.0000

bUseFaceGenLOD=0

iLODTextureTiling=2

iLODTextureSizePow2=8

fLODNormalTextureBlend=0.5000

bDisplayLODLand=1

bDisplayLODBuildings=1

bDisplayLODTrees=1

bLODPopTrees=0

bLODPopActors=0

bLODPopItems=0

bLODPopObjects=0

fLODFadeOutMultActors=5.0000

fLODFadeOutMultItems=2.0000

fLODFadeOutMultObjects=5.0000

fLODMultLandscape=1.0000

fLODMultTrees=1.2000

fLODMultActors=1.0000

fLODMultItems=1.0000

fLODMultObjects=1.0000

iFadeNodeMinNearDistance=400

fLODFadeOutPercent=0.9000

fLODBoundRadiusMult=3.0000

fTalkingDistance=2000.0000



fTreeLODMax=2.0000

fTreeLODMin=0.0200

fTreeLODDefault=1.2000



[Weather]

fSunGlareSize=350.0000

fSunBaseSize=250.0000

bPrecipitation=1

fAlphaReduce=1.0000

SBumpFadeColor=255,255,255,255

SLerpCloseColor=255,255,255,255

SEnvReduceColor=255,255,255,255



[Voice]

SFileTypeLTF=ltf

SFileTypeLip=lip

SFileTypeSource=wav

SFileTypeGame=mp3





[Grass]

iMinGrassSize=80

fGrassEndDistance=3000.0000

fGrassStartFadeDistance=2000.0000

bGrassPointLighting=0

bDrawShaderGrass=1

iGrassDensityEvalSize=2

iMaxGrassTypesPerTexure=2

fWaveOffsetRange=1.7500



[Landscape]

bCurrentCellOnly=0

bPreventSafetyCheck=0

fLandTextureTilingMult=2.0000





[bLightAttenuation]

fQuadraticRadiusMult=1.0000

fLinearRadiusMult=1.0000

bOutQuadInLin=0

fConstantValue=0.0000

fQuadraticValue=16.0000

fLinearValue=3.0000

uQuadraticMethod=2

uLinearMethod=1

fFlickerMovement=8.0000

bUseQuadratic=1

bUseLinear=0

bUseConstant=0





[BlurShaderHDRInterior]

fTargetLUM=1.0000

fUpperLUMClamp=1.0000

fEmissiveHDRMult=1.0000

fEyeAdaptSpeed=0.5000

fBrightScale=2.2500

fBrightClamp=0.2250

fBlurRadius=7.0000

iNumBlurpasses=1





[BlurShaderHDR]

fTargetLUM=1.2000

fUpperLUMClamp=1.0000

fGrassDimmer=1.3000

fTreeDimmer=1.2000

fEmissiveHDRMult=1.0000

fEyeAdaptSpeed=0.7000

fSunlightDimmer=1.3000

fSIEmmisiveMult=1.0000

fSISpecularMult=1.0000

fSkyBrightness=0.5000

fSunBrightness=0.0000

fBrightScale=1.5000

fBrightClamp=0.350

fBlurRadius=4.0000

iNumBlurpasses=2

iBlendType=2

bDoHighDynamicRange=1





[BlurShader]

fSunlightDimmer=1.0000

fSIEmmisiveMult=1.0000

fSISpecularMult=1.0000

fSkyBrightness=0.5000

fSunBrightness=0.0000

fAlphaAddExterior=0.2000

fAlphaAddInterior=0.5000

iBlurTexSize=256

fBlurRadius=0.0300

iNumBlurpasses=1

iBlendType=2





[GethitShader]

fBlurAmmount=0.5000

fBlockedTexOffset=0.0010

fHitTexOffset=0.0050

[MESSAGES]

bBlockMessageBoxes=0

bSkipProgramFlows=1

bAllowYesToAll=1

bDisableWarning=1

iFileLogging=0

[DistantLOD]

bUseLODLandData=0

fFadeDistance=12288.0000

[GeneralWarnings]

SGeneralMasterMismatchWarning=One or more plugins could not find the correct versions of the master files they depend on. Errors may occur during load or game play. Check the "Warnings.txt" file for more information.



SMasterMismatchWarning=One of the files that "%s" is dependent on has changed since the last save.

This may result in errors. Saving again will clear this message

but not necessarily fix any errors.



[Archive]

SMasterMiscArchiveFileName=Oblivion - Misc.bsa

SMasterVoicesArchiveFileName2=Oblivion - Voices2.bsa

SMasterVoicesArchiveFileName1=Oblivion - Voices1.bsa

SMasterSoundsArchiveFileName=Oblivion - Sounds.bsa

SMasterTexturesArchiveFileName1=Oblivion - Textures - Compressed.bsa

SMasterMeshesArchiveFileName=Oblivion - Meshes.bsa

SInvalidationFile=ArchiveInvalidation.txt

iRetainFilenameOffsetTable=1

iRetainFilenameStringTable=1

iRetainDirectoryStringTable=1

bCheckRuntimeCollisions=0

bInvalidateOlderFiles=1

bUseArchives=1

[CameraPath]

iTake=0

SDirectoryName=TestCameraPath

iFPS=60

SNif=Test\CameraPath.nif

[Absorb]

fAbsorbGlowColorB=1.0000

fAbsorbGlowColorG=0.6000

fAbsorbGlowColorR=0.0000

fAbsorbCoreColorB=1.0000

fAbsorbCoreColorG=1.0000

fAbsorbCoreColorR=1.0000

iAbsorbNumBolts=1

fAbsorbBoltGrowWidth=0.0000

fAbsorbBoltSmallWidth=7.0000

fAbsorbTortuosityVariance=2.0000

fAbsorbSegmentVariance=7.0000

fAbsorbBoltsRadius=5.0000

[OPENMP]

iThreads=3

iOpenMPLevel=10

[TestAllCells]

bFileShowTextures=1

bFileShowIcons=1

bFileSkipIconChecks=0

bFileTestLoad=0

bFileNeededMessage=1

bFileGoneMessage=1

bFileSkipModelChecks=0

[CopyProtectionStrings]

SCopyProtectionMessage2=Insert the Oblivion Disc.

SCopyProtectionTitle2=Oblivion Disc Not Found

SCopyProtectionMessage=Unable to find a CD-ROM/DVD drive on this computer.

SCopyProtectionTitle=CD-ROM Drive Not Found
```

I'm getting the exact same error.  wine 0.9.37, Ubuntu fiesty, opteron 165 + nvidia 7900GT.  Any clues?

EDIT: fixed: reinstalled everything from the ground up and it works, with no sound but it's an ALSA issue.

---

### Post by ahaslam on 2007-06-01
Is there any improvement with Wine 0.9.38?

---

### Post by MikeSz on 2007-06-03
I just cannot get this game working!!  Its making me want to go back to windows because its just easier!!!  Everytime I try to run it, despite having gone through the walkthrough god knows how many times (as far as I can tell ive followed all the steps correctly) it just drops out whenever I try to play it.  I get the menu and as soon as I click on play , boom - back to the desktop!!!  Can anyone please tell me how to sort this, in a way that a 'human being' can understand?

---

### Post by Mongoose on 2007-06-04
Mike: If you read the wiki you should be aware of all the major issues.  For example if you have an ATi card you're out of luck in general.  If you can't figure out the cause or follow the wiki guide perhaps you should just play under Windows.  

Wine is a moving target, and you have to be able to figure out at issues on your own as not everyone's setup is the same.  The guides try to cover the general case and common exceptions.  I personally think it's getting easier and easier to run games under Wine, but I've been doing that for a very long time.  We can run some games like Oblivion now without modifing the game itself for example.  

If you calm down and reread the known issues in the wiki you might find your answer, and if you don't run inside a terminal window and get information to figure out your issue.  At that point you can come back here and ask for help and are likely to get results.  Most people read posts like yours and go "sucks for him, works fine for me" due to the fact you don't have any such information.   You're much more likely to get help from a passerby when you offer some building blocks.  Also you'll notice I personally don't attempt to help people I assume are using illegal copies of the game.  I'm not saying you are, but there are  some here that are -- you can tell by their issues.  ;)

---

### Post by MikeSz on 2007-06-07
Thanks for your reply. 

Ive installed it on a second hard-drive with windows on it but I would like to run it under Ubuntu and wine then I donthave to use Windows.  I prefer Ubuntu and am learning things steadily.  

Let me go over a couple of points if these help at all.

1) I have an Nvidia GeForce XFX 7600GS and ive enabled the restricted drivers.  

2) the only problem I had with the walkthrough was the Direct 3D registry folder - it simply wasnt there in my registry when I got to that stage of the walkthrough so I created it and the keys specified.

3) My copy of oblivion is genuine - I got it brand new when it first came out and if there is any way of proving that then I will quite happily do so (such as posting a photo or whatever).  

4) I can install the program, get to the menu, hear the music, but as soon as I click play, the program crashes straight back to the desktop.  Ive gone over the wiki and the walkthrough and the only things I am missing (apart from the glitches above) are that I havent copied the DVD on to the hard disk - didnt think this was essential and secondly, I couldnt extract the file mentioned (cant remember what it was off the top of my head)

So is this just a case of trying to figure it out, if so, can you point me in the direction of what you think needs changing?

---

### Post by Enverex on 2007-06-07
Can you paste the entire terminal output from start to finish when you try and play? (use the code thing to wrap it in on the forum).

---

### Post by MikeSz on 2007-06-07
I can do, im at work at the moment so will do it in a couple of hours when I get home ;)

---

### Post by MikeSz on 2007-06-07
Opps.  Ive started from scratch, gone through the wiki and found some things that I hadnt done right before by keeping an eye on the terminal.  would seem that my registry changes (the direct3d bit) were not being saved so I had to "sudo wine regedit.exe" in order to get the changes done.  so that saved.  However now, there is a slightly different problem.  when I click on the launcher, the oblivion menu pops up for a split second then closes again.  there are no entries in terminal to say why.  Looking at the icon, it has a padlock on it and it says in the permissions that I dont own it so It looks liike ive locked myself out of it!!  Ive attached a screenshot.  I cant navigate to my wine directory in terminal for some reason, its a hidden file and no matter how I try, I just cant navigate to it.  Does anyone have any ideas as to this latest development?

---

### Post by MikeSz on 2007-06-07
ooops - picture attached this time....

---

### Post by Cappy on 2007-06-07
The directory is ".wine" - Directories or files with a dot on the front make them "hidden". The command "ls -la" will show you them while in the terminal or while in the File Browser (nautilus) Goto (View --> Show Hidden Files).

The root problem .. maybe you installed Oblivion as root.
```
sudo chown -R yourusername:yourusername ~/.wine
```
I think that will do it.

---

### Post by Enverex on 2007-06-07
Yeah, never run Wine or anything to do with Wine (regedit, etc) with sudo or as root, EVER. You'll just break your Wine install.

---

### Post by MikeSz on 2007-06-07
you'd think so wouldnt you :p unfortunately that hasnt worked.  thought it may be because there are spaces and that didnt work either!!!  Ive copied and pasted the path from the location bar in nautilus so I know i havent typed it in wrong as well.  Here is the output from terminal...

bespin@bespin-desktop:~$ cd /home/bespin/.wine/drive_cbespin@bespin-desktop:~/.wine/drive_c$ cd /home/bespin/.wine/drive_c/Program Files/Bethesda Softworks/Oblivion
bash: cd: /home/bespin/.wine/drive_c/Program: No such file or directory
[email]bespin@bespin-desktop:~/.wine[/email]/drive_c$ 
[email]bespin@bespin-desktop:~/.wine[/email]/drive_c$ cd /home/bespin/.wine/drive_c/Program Files/Bethesda Softworks/Oblivion
bash: cd: /home/bespin/.wine/drive_c/Program: No such file or directory
[email]bespin@bespin-desktop:~/.wine[/email]/drive_c$ 
[email]bespin@bespin-desktop:~/.wine[/email]/drive_c$ cd /home/bespin/.wine/drive_c/ProgramFiles/BethesdaSoftworks/Oblivion
bash: cd: /home/bespin/.wine/drive_c/ProgramFiles/BethesdaSoftworks/Oblivion: No such file or directory
[email]bespin@bespin-desktop:~/.wine[/email]/drive_c$

---

### Post by MikeSz on 2007-06-07
seemed the only way to do it - wouldnt save the files otherwise in regedit - kept give me permission errors in terminal

---

### Post by bastiegast on 2007-06-07
The reason you couldn't change to your oblivion directory is that it probably is owned by root. You will probably get a permission denied if you try to cd .wine.


Your wine install is probably a bit messed up because you ran some things as a root. It probably is fixable but the easiest solution is to start over and if you run into permission problems DONT run your wine apps as root but ask here first.
If you have nothing else in your wine directory that is valuable to you you can delete it like this:

[CODE]sudo rm -rf ~/.wine[
wineprefixcreate/CODE]
-WARNING- This will delete all your programs and settings that you installed in wine

wineprefixcreate will make a new wine directory.

---

### Post by Jarn on 2007-06-08
To get there in the terminal:

```
cd ~/.wine/drive_c/Program\ Files/Bethesda\ Softworks/Oblivion
```

As far as not having pemissions, do (if bespin is your username, else replace bespin with your username)

```
cd ~
sudo chown -R bespin:bespin .wine

```

---

### Post by Mongoose on 2007-06-08
Try this instead:

echo ${USER}
This will tell your user name, and use that in place of yourusername below.

sudo chown -R yourusername:yourusername .wine

for example for me it would be:

$ echo ${USER}
mongoose
$ sudo chown -R mongoose:mongoose .wine

That should recursively set your user as the owner for your .wine directory.  If you installed games as root do the same to them to make them user owned.

---

### Post by Enverex on 2007-06-08
This was nothing to do with permissions, it was a simple case of not knowing how to use the terminal.

Ok, example:

cd Games/Program Files/Bob

is seens as two commands because of the space between Program and Files.
You can get around this with one of two methods, either escape the spaces uses backslashes, i.e.

cd Games/Program\ Files/Bob

Or by putting it in speechmarks...

cd "Games/Program Files/Bob"

The only time a folder in your Wine install will have the wrong permissions is if you've copied it over from an NTFS partiton (or other Windows install, which is a bad idea) or used sudo to install something, which is an even worse idea and is likely to just break things (as well as give Wine the ability to delete everything on your PC, a bug in Diablo 2 a while back would cause it to remove your HDs Master Boot Record).

---

### Post by jimminy_kriket on 2007-06-16
Bumpity Bump!

Any improvements with 0.9.39?

Sorry I would check myself but my laptop is in repair >_<

---

### Post by bastiegast on 2007-06-16
It might be related to my setup but since wine-git somewhere between 0.9.37 and 0.9.38 Oblivion crashed when I tried to load a game. The game would loads (the progress bar shows everyting is loaded) but then it would crash. Since I upgraded to wine 0.9.39 the game just crashes before the progress bar is completely full.

---

### Post by Jeremy Jackins on 2007-06-16
Hi, I followed your guide at [http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux), and it all worked very well, only the second time I ran oblivion the audio no longer worked. Now when I run olbivion I get this error: 
```

ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
```

any idea what could have happened?


EDIT: the music plays fine during the launcher, it's when it boots into the actualy game that this happens.

---

### Post by ahaslam on 2007-06-17
> **jimminy_kriket said:**
> Bumpity Bump!

Any improvements with 0.9.39?

Sorry I would check myself but my laptop is in repair >_<

0.9.38 is the best version for me (best sound). Just tried .39 & experienced frequent crashes while loading saves & new areas.

I should have waited longer, by the time this game truly runs well you'll be able to buy it for a fiver.

---

### Post by Enverex on 2007-06-17
Set Wine to use OSS, not ALSA. ALSA still has many issues.

---

### Post by ESPOiG on 2007-06-23
i followed this and it works all fine, besides the hacking the .ini file for some reason, eg such as i disabled the videos at startup but it still crashed so i had to move them.

also once in the game my character moves by himself and i pressed q just incase i accidently pressed it but it didnt change. and the hotkeys thing is up and i cant jump, it is like my keyboard is not working??

but i can look with the mouse, any ideas?

---

### Post by ESPOiG on 2007-06-23
well i figured it out, it was a game controller i had plugged in, but now the game crashes?? when it is unplugged

the problem is that my Oblivion_default.ini that i changed the settings in wont take affect in the game, why?

---

### Post by Cappy on 2007-06-23
That's not the correct ini - that is the one that is copied when the user's ini is missing.
The correct ini is in "My Documents/Games/Oblivion" or something like that

---

### Post by Mongoose on 2007-06-24
Yes, it's .../Windows/Documents/My Games/Oblivion/Oblivion.ini -- which you should have set this path during the guide.  I set my 'Windows' to ~/Documents/Windows as noted in the guide and place all the stuff like My Documents ( I renamed it Documents ) there.  This way your Windows application won't put them in your fake root or whatever you have by default.

---

### Post by Mongoose on 2007-06-24
You should disable joystick in the ini -- iirc it can still cause crashes.  I had a dozen people report the issue still happens, but they could be on older versions! hah

If you read the Known Issues section it'll tell you how.  Enjoy your Linux Gaming, and note Quake Wars is coming soon as a native game.  ;)

---

### Post by ESPOiG on 2007-06-24
hey yeh thx i did figure out that it was supposed to be the .ini in my saved games :D sorry.

but also it seems to crash when i try and leave the sewers this is in the latest release of wine, any ideas?

---

### Post by Mongoose on 2007-06-24
You disabled the joystick?  There was some reports disabling the joystick in the ini resolved one of the reasons for crashing exiting the sewers, but was the least common.  I think 0.9.39 has a thread issue iirc.  Try using the 'blessed' versions from the guide first.  Remember to file thread bugs with wine app db.  ;)

---

### Post by ESPOiG on 2007-06-24
i have allready disabled the joystick and all the other things, but it still crashes when leaving the sewers

---

### Post by Mongoose on 2007-06-24
In the recommended version?  If not like I said it's likely the threading issue some people have reported with the latest version of wine.

---

### Post by ESPOiG on 2007-06-25
wats the threading issue sorry if im gettin annoying :D

---

### Post by bastiegast on 2007-06-26
It doesn't matter what the threading issue is, just tell us the version of wine your using(by typing wine --version) en if its 0.9.39, try downgrading(by uninstalling wine, downloading a lower version and installing that one) see if that helps.

The problem is that you might be using a version of wine that people have reported problems with, if so the source of your problems might lie in that.

---

### Post by Copperteeth on 2007-06-27
Alright, i followed the guide down to the last detail except for the shell script but i can not get it to launch. After i saw this thread i went out and bought the game because my graphics card is simalar to yours Mongoose, except its a GeForce 6200. Now i got it installed and everything, i got all the nessicary dll's but when i go to run play game on the launcher, it closes the launcher, displays a tiny box in the cornor and then it just closes the virtual desktop and gives me the following in the terminal:

```
tyler@tyler-ubuntu:~$ fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:d3d:IWineD3DDeviceImpl_SetMultithreaded No thread safety in wined3d yet
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x110e0020) : stub, simulating 128MB for now, returning 128MB left
wine: Unhandled page fault on read access to 0x000002a0 at address 0x7e25b466 (thread 0016), starting debugger...
Unhandled exception: page fault on read access to 0x000002a0 in 32-bit code (0x7e25b466).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e25b466 ESP:7c6498d0 EBP:7c64994c EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7ca61b58 ECX:00209420 EDX:00000000
 ESI:110e0020 EDI:ff000000
Stack dump:
0x7c6498d0:  7c9d2cd6 00000c11 0020a570 00000001
0x7c6498e0:  00000000 00000000 00000000 00000000
0x7c6498f0:  00000000 00000000 00000000 a4014934
0x7c649900:  01c7b874 7bc61669 00000000 0034550f
0x7c649910:  1801509a 0fe365e8 00000000 0020a570
0x7c649920:  00000000 11852880 7b8b0888 11850458
Backtrace:
=>1 0x7e25b466 glTexImage2D+0x406() in libgl.so.1 (0x7c64994c)
  2 0x7ca7aaa5 in d3d9 (+0xaaa5) (0x7c64997c)
  3 0x0041028a in oblivion (+0x1028a) (0x00000000)
0x7e25b466 glTexImage2D+0x406 in libgl.so.1: jmp        *0x2a0(%eax)
Modules:
Module  Address                 Debug info      Name (97 modules)
PE        400000-  b59000       Export          oblivion
PE        b60000-  daf000       Deferred        d3dx9_27
PE      18000000-18068000       Deferred        binkw32
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bc98000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc98000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c91b000-7c99b000       Deferred        libglu.so.1
ELF     7c99b000-7ca63000       Deferred        wined3d<elf>
  \-PE  7c9b0000-7ca63000       \               wined3d
ELF     7ca63000-7ca8f000       Export          d3d9<elf>
  \-PE  7ca70000-7ca8f000       \               d3d9
ELF     7ce9b000-7ceb0000       Deferred        midimap<elf>
  \-PE  7cea0000-7ceb0000       \               midimap
ELF     7ceb0000-7ced6000       Deferred        msacm32<elf>
  \-PE  7cec0000-7ced6000       \               msacm32
ELF     7ced6000-7cf9b000       Deferred        libasound.so.2
ELF     7cf9b000-7cfcd000       Deferred        winealsa<elf>
  \-PE  7cfb0000-7cfcd000       \               winealsa
ELF     7cfcd000-7d009000       Deferred        wineoss<elf>
  \-PE  7cfd0000-7d009000       \               wineoss
ELF     7d009000-7d03b000       Deferred        uxtheme<elf>
  \-PE  7d010000-7d03b000       \               uxtheme
ELF     7d2db000-7d2f3000       Deferred        msacm32<elf>
  \-PE  7d2e0000-7d2f3000       \               msacm32
ELF     7d2f5000-7d2fa000       Deferred        libxfixes.so.3
ELF     7d2fa000-7d303000       Deferred        libxcursor.so.1
ELF     7d303000-7d320000       Deferred        imm32<elf>
  \-PE  7d310000-7d320000       \               imm32
ELF     7d320000-7d326000       Deferred        libxrandr.so.2
ELF     7d326000-7d32e000       Deferred        libxrender.so.1
ELF     7d32e000-7d331000       Deferred        libxinerama.so
ELF     7d85e000-7e1d0000       Deferred        libglcore.so.1
ELF     7e1d0000-7e264000       Export          libgl.so.1
ELF     7e264000-7e269000       Deferred        libxdmcp.so.6
ELF     7e269000-7e35a000       Deferred        libx11.so.6
ELF     7e35a000-7e368000       Deferred        libxext.so.6
ELF     7e368000-7e36d000       Deferred        libxxf86vm.so.1
ELF     7e36d000-7e385000       Deferred        libice.so.6
ELF     7e385000-7e38e000       Deferred        libsm.so.6
ELF     7e38e000-7e41d000       Deferred        winex11<elf>
  \-PE  7e3a0000-7e41d000       \               winex11
ELF     7e52d000-7e54d000       Deferred        libexpat.so.1
ELF     7e54d000-7e578000       Deferred        libfontconfig.so.1
ELF     7e578000-7e58c000       Deferred        libz.so.1
ELF     7e58c000-7e5f7000       Deferred        libfreetype.so.6
ELF     7e5f7000-7e624000       Deferred        ws2_32<elf>
  \-PE  7e600000-7e624000       \               ws2_32
ELF     7e624000-7e63e000       Deferred        wsock32<elf>
  \-PE  7e630000-7e63e000       \               wsock32
ELF     7e63e000-7e6a5000       Deferred        msvcrt<elf>
  \-PE  7e650000-7e6a5000       \               msvcrt
ELF     7e6a5000-7e6b9000       Deferred        lz32<elf>
  \-PE  7e6b0000-7e6b9000       \               lz32
ELF     7e6b9000-7e6d3000       Deferred        version<elf>
  \-PE  7e6c0000-7e6d3000       \               version
ELF     7e6d3000-7e72c000       Deferred        shlwapi<elf>
  \-PE  7e6e0000-7e72c000       \               shlwapi
ELF     7e72c000-7e82a000       Deferred        shell32<elf>
  \-PE  7e740000-7e82a000       \               shell32
ELF     7e82a000-7e873000       Deferred        dsound<elf>
  \-PE  7e830000-7e873000       \               dsound
ELF     7e873000-7e902000       Deferred        winmm<elf>
  \-PE  7e880000-7e902000       \               winmm
ELF     7e902000-7e915000       Deferred        libresolv.so.2
ELF     7e915000-7e933000       Deferred        iphlpapi<elf>
  \-PE  7e920000-7e933000       \               iphlpapi
ELF     7e933000-7e988000       Deferred        rpcrt4<elf>
  \-PE  7e940000-7e988000       \               rpcrt4
ELF     7e988000-7ea27000       Deferred        ole32<elf>
  \-PE  7e9a0000-7ea27000       \               ole32
ELF     7ea27000-7ea5d000       Deferred        dinput<elf>
  \-PE  7ea30000-7ea5d000       \               dinput
ELF     7ea5d000-7ea76000       Deferred        dinput8<elf>
  \-PE  7ea60000-7ea76000       \               dinput8
ELF     7ea76000-7eabe000       Deferred        advapi32<elf>
  \-PE  7ea80000-7eabe000       \               advapi32
ELF     7eabe000-7eaca000       Deferred        libgcc_s.so.1
ELF     7ebb4000-7ec74000       Deferred        gdi32<elf>
  \-PE  7ebd0000-7ec74000       \               gdi32
ELF     7ec74000-7edb1000       Deferred        user32<elf>
  \-PE  7ec90000-7edb1000       \               user32
ELF     7edb1000-7ee6e000       Deferred        comctl32<elf>
  \-PE  7edc0000-7ee6e000       \               comctl32
ELF     7ee6e000-7ee79000       Deferred        libnss_files.so.2
ELF     7ee79000-7ee83000       Deferred        libnss_nis.so.2
ELF     7ee83000-7ee9a000       Deferred        libnsl.so.1
ELF     7ee9a000-7eea3000       Deferred        libnss_compat.so.2
ELF     7eea3000-7eea5000       Deferred        libnvidia-tls.so.1
ELF     7efc7000-7efee000       Deferred        libm.so.6
ELF     7efef000-7eff2000       Deferred        libxau.so.6
ELF     b7cf3000-b7cf7000       Deferred        libdl.so.2
ELF     b7cf7000-b7e38000       Deferred        libc.so.6
ELF     b7e39000-b7e50000       Deferred        libpthread.so.0
ELF     b7e62000-b7f76000       Deferred        libwine.so.1
ELF     b7f78000-b7f93000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000f (D) C:\Program Files\Bethesda Softworks\Oblivion\Oblivion.exe
        00000018   -1
        00000017   15
        00000016    1 <==
        00000015   -1
        00000014   -1
        00000013   15
        00000011    0
        00000010    0
0000000b 
        0000000e    0
        0000000c    0


```

Not sure what i did wrong, im going to try a few more things

EDIT: I fixed the problem, renamed the video folder and it runs . Also, it runs better for me, well better and nicer when i have version 0.9.39

---

### Post by Copperteeth on 2007-06-27
> **kroenecker said:**
> I've read over the thread and don't see any advice for the following:

When I run Oblivion it works, but the screen freezes just before the King is attacked for the first time.  That is, going down the stairs and through the first door.

Does anyone else have this experience?  I installed v29 but that doesn't seem to help.  Maybe my video card is problematic: 6600 with 128 memory.

Ah well, it does run in windows and I do still have windows installed :P

Im having the same problem and im not running oldblivion. I have a 6200

---

### Post by Enverex on 2007-06-27
Also make sure you've updated the game to at least version 1.2.

---

### Post by piratenaapje on 2007-06-30
I've tried getting oblivion to run under wine, but failed. I then proceeded to try it under cedega and finally succeeded in my attempt. Only, outdoor locations look weird now, specifically: the grass. It looks something like this: [IMG]http://piratenaapje.thesneaky.com/Image/Schermafdruk-3.png[/IMG]
My ini looks like this: 




```

[General]

SStartingCell=



SStartingCellY=

SStartingCellX=

SStartingWorld=



STestFile10=

STestFile9=

STestFile8=

STestFile7=

STestFile6=

STestFile5=

STestFile4=

STestFile3=

STestFile2=

STestFile1=



bEnableProfile=0

bDrawSpellContact=0

bRunMiddleLowLevelProcess=1

iHoursToSleep=3

bActorLookWithHavok=0

SMainMenuMusicTrack=special\tes4title.mp3

bUseEyeEnvMapping=0

bFixFaceNormals=0

bUseFaceGenHeads=1

bFaceMipMaps=1

bFaceGenTexturing=1

bDefaultCOCPlacement=0

uGridDistantTreeRange=15

uGridDistantCount=25

uGridsToLoad=5

fGlobalTimeMultiplier=1.0000

bNewAnimation=1

fAnimationDefaultBlend=0.1000

fAnimationMult=1.0000

bFixAIPackagesOnLoad=0

bForceReloadOnEssentialCharacterDeath=1

bKeepPluginWhenMerging=0

bCreate Maps Enable=0

SLocalSavePath=Saves\

SLocalMasterPath=Data\

bDisableDuplicateReferenceCheck=1

bTintMipMaps=0

uInterior Cell Buffer=3

uExterior Cell Buffer=36

iIntroSequencePriority=3

bPreloadIntroSequence=1

fStaticScreenWaitTime=3.0000

SCreditsMenuMovie=CreditsMenu.bik

SMainMenuMovie=Map loop.bik

SMainMenuMovieIntro=Oblivion iv logo.bik

SIntroSequence=

iFPSClamp=0

bRunVTuneTest=0

STestFile1=

bActivateAllQuestScripts=0

fQuestScriptDelayTime=5.0000

SMainMenuMusic=Special\TES4Title.mp3

bUseThreadedBlood=0

bUseThreadedMorpher=0

bExternalLODDataFiles=1



bBorderRegionsEnabled=1

bDisableHeadTracking=0

bTrackAllDeaths=0

SCharGenQuest=0002466E

uiFaceGenMaxEGTDataSize=67108864

uiFaceGenMaxEGMDataSize=67108864

SBetaCommentFileName=

bCheckCellOffsetsOnInit=0

bCreateShaderPackage=0

uGridDistantTreeRangeCity=4

uGridDistantCountCity=4

bWarnOnMissingFileEntry=0

iSaveGameBackupCount=1

bDisplayMissingContentDialogue=1

SSaveGameSafeCellID=2AEEA

bAllowScriptedAutosave=1

bPreemptivelyUnloadCells=0

iNumBitsForFullySeen=248

iPreloadSizeLimit=26214400

SOblivionIntro=OblivionIntro.bik

bUseHardDriveCache=0

bEnableBoundingVolumeOcclusion=0

bDisplayBoundingVolumes=0

bUseThreadedTempEffects=0

bUseThreadedParticleSystem=0

bUseMyGamesDirectory=1



bCheckIDsOnInit=0





[Display]

uVideoDeviceIdentifierPart1=1086435912

uVideoDeviceIdentifierPart2=1244241277

uVideoDeviceIdentifierPart3=3628906455

uVideoDeviceIdentifierPart4=1564319504

fDecalLifetime=0.0000

bEquippedTorchesCastShadows=0

bReportBadTangentSpace=0

bStaticMenuBackground=1

bForcePow2Textures=0

bForce1XShaders=0

bHighQuality20Lighting=0

bAllow20HairShader=1

bAllowScreenShot=0

iMultiSample=0

bDoTallGrassEffect=1

bForceMultiPass=1

bDoTexturePass=1

bDoSpecularPass=1

bDoDiffusePass=1

bDoAmbientPass=1

bDoCanopyShadowPass=0

bDrawShadows=0

bUseRefractionShader=0

bUse Shaders=1

iNPatchNOrder=0

iNPatchPOrder=0

iNPatches=0

iLocation Y=0

iLocation X=0

bFull Screen=1

iSize W=800

iSize H=600

iAdapter=0

iScreenShotIndex=0

SScreenShotBaseName=ScreenShot

iAutoViewMinDistance=2000

iAutoViewHiFrameRate=40

iAutoViewLowFrameRate=20

bAutoViewDistance=0

fDefaultFOV=75.0000

fNearDistance=10.0000

fFarDistance=10000.0000

iDebugTextLeftRightOffset=10

iDebugTextTopBottomOffset=10

bShowMenuTextureUse=1

iDebugText=2

bLocalMapShader=1

bDoImageSpaceEffects=1

fShadowLOD2=400.0000

fShadowLOD1=200.0000

fLightLOD2=1500.0000

fLightLOD1=1000.0000

fSpecularLOD2=550.0000

fSpecularLOD1=250.0000

fEnvMapLOD2=800.0000

fEnvMapLOD1=500.0000

fEyeEnvMapLOD2=190.0000

fEyeEnvMapLOD1=130.0000

iPresentInterval=1



fSpecualrStartMax=1000.0000

fSpecularStartMin=0.0000

iActorShadowIntMax=10

iActorShadowIntMin=0

iActorShadowExtMax=10

iActorShadowExtMin=0

fGammaMax=0.6000

fGammaMin=1.4000

iMaxDecalsPerFrame=10

bDynamicWindowReflections=0

fShadowFadeTime=1.0000

fGamma=1.0000

bDecalsOnSkinnedGeometry=0

iShadowFilter=0

bAllowPartialPrecision=1

iShadowMapResolution=1024

bShadowsOnGrass=0

bActorSelfShadowing=0

iActorShadowCountInt=0

iActorShadowCountExt=0

bAllow30Shaders=0

iTexMipMapMinimum=0

iTexMipMapSkip=0

bDoStaticAndArchShadows=0

bDoActorShadows=0

bIgnoreResolutionCheck=0

fNoLODFarDistancePct=1.0000

fNoLODFarDistanceMax=10240.0000

fNoLODFarDistanceMin=1700.0000



fGrassStartFadeDistance=0.0

fGrassEndDistance=0.0

bFullBrightLighting=1

iMaxLandscapeTextures=1

bLODPopActors=1

bLODPopItems=1

bLODPopObjects=1



bLandscapeBlend=1





[Controls]

fVersion=1.8000

Forward=0011FFFF

Back=001FFFFF

Slide Left=001EFFFF

Slide Right=0020FFFF

Use=00FF00FF

Activate=0039FFFF

Block=003801FF

Cast=002EFFFF

Ready Item=0021FFFF

Crouch/Sneak=001DFFFF

Run=002AFFFF

Always Run=003AFFFF

Auto Move=0010FFFF

Jump=0012FFFF

Toggle POV=001302FF

Menu Mode=000FFFFF

Rest=0014FFFF

Quick Menu=003BFFFF

Quick1=0002FFFF

Quick2=0003FFFF

Quick3=0004FFFF

Quick4=0005FFFF

Quick5=0006FFFF

Quick6=0007FFFF

Quick7=0008FFFF

Quick8=0009FFFF

QuickSave=003FFFFF

QuickLoad=0043FFFF

Grab=002CFFFF

bInvertYValues=0

fXenonLookXYMult=0.0005

fMouseSensitivity=0.0020

;X=1, Y = 2, Z = 3, XRot = 4, YRot = 5, ZRot = 6

iJoystickMoveFrontBack=2

iJoystickMoveLeftRight=1

fJoystickMoveFBMult=1.0000

fJoystickMoveLRMult=1.0000

iJoystickLookUpDown=6

iJoystickLookLeftRight=3

fJoystickLookUDMult=0.0020

fJoystickLookLRMult=0.0020

fXenonMenuMouseXYMult=0.0003

bBackground Mouse=0

bBackground Keyboard=0

bUse Joystick=0

fXenonLookMult=0.0030

fXenonMenuStickSpeedMaxMod=5.0000

iXenonMenuStickSpeedThreshold=20000

iXenonMenuStickThreshold=1000

;Language values: 0-English, 1-German, 2-French, 3-Spanish, 4-Italian

iLanguage=0



Attack=00FF00FF

Ready Weapon=0021FFFF

Sneak=001DFFFF

Change View=001302FF

Journal=000FFFFF

Wait=0014FFFF

fXenonMenuStickMapCursorMinSpeed=1.0000

fXenonMenuStickMapCursorMaxSpeed=15.0000

fXenonMenuStickMapCursorGamma=0.1700

fXenonMenuStickSpeedPlayerRotMod=3000.0000

fXenonMenuDpadRepeatSpeed=300.0000

fXenonMenuStickSpeed=300.0000

iXenonMenuStickDeadZone=15000



SlideLeft=001EFFFF

SlideRight=0020FFFF





[Water]

fAlpha=0.5000

uSurfaceTextureSize=128

SSurfaceTexture=water

SNearWaterOutdoorID=NearWaterOutdoorLoop

SNearWaterIndoorID=NearWaterIndoorLoop

fNearWaterOutdoorTolerance=1024.0000

fNearWaterIndoorTolerance=512.0000

fNearWaterUnderwaterVolume=0.9000

fNearWaterUnderwaterFreq=0.3000

uNearWaterPoints=8

uNearWaterRadius=1000

uSurfaceFrameCount=1

uSurfaceFPS=12

bUseWaterReflectionsMisc=0

bUseWaterReflectionsStatics=0

bUseWaterReflectionsTrees=0

bUseWaterReflectionsActors=0

bUseWaterReflections=0

bUseWaterHiRes=0

bUseWaterDisplacements=0

bUseWaterShader=0

uDepthRange=125

bUseWaterDepth=1

bUseWaterLOD=1

fTileTextureDivisor=4.7500

fSurfaceTileSize=2048.0000



uNumDepthGrids=3

bUseObliqueFrustumCulling=1





[Audio]

bDSoundHWAcceleration=1

fMinSoundVel=10.0000

fMetalLargeMassMin=25.0000

fMetalMediumMassMin=8.0000

fStoneLargeMassMin=30.0000

fStoneMediumMassMin=5.0000

fWoodLargeMassMin=15.0000

fWoodMediumMassMin=7.0000

fDialogAttenuationMax=35.0000

fDialogAttenuationMin=7.7500

bUseSoundDebugInfo=1

fUnderwaterFrequencyDelta=0.0000

bUseSoftwareAudio3D=0

fDefaultEffectsVolume=0.0000

fDefaultMusicVolume=0.0000

fDefaultFootVolume=0.0000

fDefaultVoiceVolume=0.8000

fDefaultMasterVolume=0.0000

bMusicEnabled=0

bSoundEnabled=1

fLargeWeaponWeightMin=25.0000

fMediumWeaponWeightMin=8.0000

fSkinLargeMassMin=30.0000

fSkinMediumMassMin=5.0000

fChainLargeMassMin=30.0000

fChainMediumMassMin=5.0000

fDBVoiceAttenuationIn2D=0.0000

iCollisionSoundTimeDelta=50

fGlassLargeMassMin=25.0000

fGlassMediumMassMin=8.0000

fClothLargeMassMin=25.0000

fClothMediumMassMin=8.0000

fEarthLargeMassMin=30.0000

fEarthMediumMassMin=5.0000

bUseSpeedForWeaponSwish=1

fLargeWeaponSpeedMax=0.9500

fMediumWeaponSpeedMax=1.1000

fPlayerFootVolume=0.9000

fDSoundRolloffFactor=4.0000

fMaxFootstepDistance=1100.0000

fHeadroomdB=2.0000

iMaxImpactSoundCount=32

fMainMenuMusicVolume=0.6000





[ShockBolt]

bDebug=0

fGlowColorB=1.0000

fGlowColorG=0.6000

fGlowColorR=0.0000

fCoreColorB=1.0000

fCoreColorG=1.0000

fCoreColorR=1.0000

fCastVOffset=-10.0000

iNumBolts=7

fBoltGrowWidth=1.0000

fBoltSmallWidth=3.0000

fTortuosityVariance=8.0000

fSegmentVariance=35.0000

fBoltsRadius=24.0000





[Pathfinding]

bDrawPathsDefault=0

bPathMovementOnly=0

bDrawSmoothFailures=0

bDebugSmoothing=0

bSmoothPaths=1

bSnapToAngle=0

bDebugAvoidance=0

bDisableAvoidance=0

bBackgroundPathing=0



bUseBackgroundPathing=1





[MAIN]

bEnableBorderRegion=1



fLowPerfCombatantVoiceDistance=1000.0000

iDetectionHighNumPicks=40

fQuestScriptDelayTime=5.0000

iLastHDRSetting=-1





[Combat]

bEnableBowZoom=1

bDebugCombatAvoidance=0

fMinBloodDamage=1.0000

fHitVectorDelay=0.4000

iShowHitVector=0



fLowPerfNPCTargetLOSTimer=1.0000

fHiPerfNPCTargetLOSTimer=0.5000

iMaxHiPerfNPCTargetCount=4

fLowPerfPCTargetLOSTimer=0.5000

fHiPerfPCTargetLOSTimer=0.2500

iMaxHiPerfPCTargetCount=4

iMaxHiPerfCombatCount=4





[HAVOK]

bDisablePlayerCollision=0

fJumpAnimDelay=0.7500

bTreeTops=0

iSimType=1

bPreventHavokAddAll=0

bPreventHavokAddClutter=0

fMaxTime=0.0167

bHavokDebug=0

fRF=1000.0000

fOD=0.9000

fSE=0.3000

fSD=0.9800

iResetCounter=5

fMoveLimitMass=95.0000

iUpdateType=0

bHavokPick=0



fCameraCasterSize=1.0000

iHavokSkipFrameCountTEST=0

fHorseRunGravity=3.0000

fQuadrupedPitchMult=1.0000

iNumHavokThreads=1

fChaseDeltaMult=0.0500

iEntityBatchRemoveRate=100

iMaxPicks=40

bAddBipedWhenKeyframed=0





[Interface]

fDlgLookMult=0.3000

fDlgLookAdj=0.0000

fDlgLookDegStop=0.2000

fDlgLookDegStart=2.0000

fDlgFocus=2.1000

fKeyRepeatInterval=50.0000

fKeyRepeatTime=500.0000

fActivatePickSphereRadius=16.0000

fMenuModeAnimBlend=0.0000

iSafeZoneX=20

iSafeZoneY=20

iSafeZoneXWide=20

iSafeZoneYWide=20



fMenuPlayerLightDiffuseBlue=0.8000

fMenuPlayerLightDiffuseGreen=0.8000

fMenuPlayerLightDiffuseRed=0.8000

fMenuPlayerLightAmbientBlue=0.2500

fMenuPlayerLightAmbientGreen=0.2500

fMenuPlayerLightAmbientRed=0.2500

bAllowConsole=1

bActivatePickUseGamebryoPick=0

iMaxViewCasterPicksGamebryo=10

iMaxViewCasterPicksHavok=10

iMaxViewCasterPicksFuzzy=5

bUseFuzzyPicking=1

fMenuBGBlurRadius=2.0000





[LoadingBar]



iMoveBarWaitingMilliseconds=10

iMoveBarChaseMilliseconds=100

iMoveBarMaxMilliseconds=2500

fLoadingSlideDelay=15.0000

fPercentageOfBar3=0.1500

fPercentageOfBar2=0.4400

fPercentageOfBar1=0.3500

fPercentageOfBar0=0.0600

bShowSectionTimes=0





[Menu]

fCreditsScrollSpeed=40.0000

iConsoleTextYPos=890

iConsoleTextXPos=30

iConsoleVisibleLines=15

iConsoleHistorySize=50

rDebugTextColor=255,251,233

iConsoleFont=3

iDebugTextFont=3





[GamePlay]

bDisableDynamicCrosshair=0

bSaveOnTravel=1

bSaveOnWait=1

bSaveOnRest=1

bCrossHair=1

iDifficultyLevel=50

bGeneralSubtitles=0

bDialogueSubtitles=1

bInstantLevelUp=0

bHealthBarShowing=0

fHealthBarFadeOutSpeed=1.0000

fHealthBarSpeed=80.0000

fHealthBarHeight=4.0000

fHealthBarWidth=40.0000

fHealthBarEmittanceFadeTime=0.5000

fHealthBarEmittanceTime=1.5000



STrackLevelUpPath=

fDifficulty=0.0000

bTrackLevelUps=1

bAllowHavokGrabTheLiving=0

bEssentialTakeNoDamage=1

iDetectionPicks=21

bSaveOnInteriorExteriorSwitch=0





[Fonts]

SFontFile_1=Data\Fonts\Kingthings_Regular.fnt

SFontFile_2=Data\Fonts\Kingthings_Shadowed.fnt

SFontFile_3=Data\Fonts\Tahoma_Bold_Small.fnt

SFontFile_4=Data\Fonts\Daedric_Font.fnt

SFontFile_5=Data\Fonts\Handwritten.fnt





[SpeedTree]

iTreeClonesAllowed=1

fCanopyShadowGrassMult=1.0000

iCanopyShadowScale=512

fTreeForceMaxBudAngle=-1.0000

fTreeForceMinBudAngle=-1.0000

fTreeForceLeafDimming=-1.0000

fTreeForceBranchDimming=-1.0000

fTreeForceCS=-1.0000

fTreeForceLLA=-1.0000

fTreeLODExponent=1.0000

bEnableTrees=1

bForceFullLOD=0



fLODTreeMipMapLODBias=-0.7500

fLocalTreeMipMapLODBias=-0.2500





[Debug]

bDebugFaceGenCriticalSection=0

bDebugFaceGenMultithreading=0

bDebugSaveBuffer=0





[BackgroundLoad]



bBackgroundLoadLipFiles=0

bLoadBackgroundFaceGen=0

bUseMultiThreadedFaceGen=1

bBackgroundCellLoads=1

bLoadHelmetsInBackground=1

iAnimationClonePerLoop=5

bSelectivePurgeUnusedOnFastTravel=0

bUseMultiThreadedTrees=1

iExteriorPriority=50

bCloneModelsInBackground=0

iBackgroundLoadFaceMult=200

fBackgroundLoadingPerLoop=20.0000

fBackgroundLoadClonedPerLoop=5.0000

iBackgroundLoadExtraMaxFPS=20

iBackgroundLoadExtraMinFPS=10

iBackgroundLoadExtraMax=3000

iBackgroundLoadExtraMin=5

iBackgroundLoadExtraMilliseconds=2

iBackgroundLoadTreeMilliseconds=7

iBackgroundLoadMilliseconds=1

iBackgroundLoadLoading=1

bUseBackgroundFileLoader=0



iPostProcessMillisecondsEditor=50

iPostProcessMillisecondsLoadingQueuedPriority=20

iPostProcessMilliseconds=5





[LOD]

fLodDistance=500.0000

bUseFaceGenLOD=0

iLODTextureTiling=2

iLODTextureSizePow2=8

fLODNormalTextureBlend=0.5000

bDisplayLODLand=1

bDisplayLODBuildings=1

bDisplayLODTrees=1

bLODPopTrees=0

bLODPopActors=0

bLODPopItems=0

bLODPopObjects=0

fLODFadeOutMultActors=5.0000

fLODFadeOutMultItems=2.0000

fLODFadeOutMultObjects=5.0000

fLODMultLandscape=1.0000

fLODMultTrees=0.2000

fLODMultActors=2.0000

fLODMultItems=2.0000

fLODMultObjects=2.0000

iFadeNodeMinNearDistance=400

fLODFadeOutPercent=0.9000

fLODBoundRadiusMult=3.0000

fTalkingDistance=2000.0000



fTreeLODMax=2.0000

fTreeLODMin=0.0200

fTreeLODDefault=1.2000



fObjectLODMax=15.0000

fObjectLODMin=1.0000

fObjectLODDefault=5.0000

fItemLODMax=15.0000

fItemLODMin=1.0000

fItemLODDefault=2.0000

fActorLODMax=15.0000

fActorLODMin=2.0000

fActorLODDefault=5.0000

bLODUseCombinedLandNormalMaps=1

bForceHideLODLand=0

fLODQuadMinLoadDistance=65536.0000

fLODFadeOutActorMultInterior=1.0000

fLODFadeOutItemMultInterior=1.0000

fLODFadeOutObjectMultInterior=1.0000

fLODFadeOutActorMultCity=1.0000

fLODFadeOutItemMultCity=1.0000

fLODFadeOutObjectMultCity=1.0000

fLODFadeOutActorMultComplex=1.0000

fLODFadeOutItemMultComplex=1.0000

fLODFadeOutObjectMultComplex=1.0000

fLODLandVerticalBias=0.0000





[Weather]

fSunGlareSize=350.0000

fSunBaseSize=250.0000

bPrecipitation=1

fAlphaReduce=1.0000

SBumpFadeColor=255,255,255,255

SLerpCloseColor=255,255,255,255

SEnvReduceColor=255,255,255,255





[Voice]

SFileTypeLTF=ltf

SFileTypeLip=lip

SFileTypeSource=wav

SFileTypeGame=mp3





[Grass]

iMinGrassSize=80

fGrassEndDistance=3000.0000

fGrassStartFadeDistance=2000.0000

bGrassPointLighting=0

bDrawShaderGrass=1

iGrassDensityEvalSize=2

iMaxGrassTypesPerTexure=2

fWaveOffsetRange=1.7500



fGrassWindMagnitudeMax=125.0000

fGrassWindMagnitudeMin=5.0000

fTexturePctThreshold=0.3000





[Landscape]

bCurrentCellOnly=0

bPreventSafetyCheck=0

fLandTextureTilingMult=2.0000



fLandFriction=2.5000

iLandBorder2B=0

iLandBorder2G=0

iLandBorder2R=0

iLandBorder1B=0

iLandBorder1G=255

iLandBorder1R=255





[bLightAttenuation]

fQuadraticRadiusMult=1.0000

fLinearRadiusMult=1.0000

bOutQuadInLin=0

fConstantValue=0.0000

fQuadraticValue=16.0000

fLinearValue=3.0000

uQuadraticMethod=2

uLinearMethod=1

fFlickerMovement=8.0000

bUseQuadratic=1

bUseLinear=0

bUseConstant=0





[BlurShaderHDRInterior]

fTargetLUM=1.0000

fUpperLUMClamp=1.0000

fEmissiveHDRMult=1.0000

fEyeAdaptSpeed=0.5000

fBrightScale=2.2500

fBrightClamp=0.2250

fBlurRadius=7.0000

iNumBlurpasses=1





[BlurShaderHDR]

fTargetLUM=1.2000

fUpperLUMClamp=1.0000

fGrassDimmer=1.3000

fTreeDimmer=1.2000

fEmissiveHDRMult=1.0000

fEyeAdaptSpeed=0.7000

fSunlightDimmer=1.3000

fSIEmmisiveMult=1.0000

fSISpecularMult=1.0000

fSkyBrightness=0.5000

fSunBrightness=0.0000

fBrightScale=1.5000

fBrightClamp=0.3500

fBlurRadius=4.0000

iNumBlurpasses=2

iBlendType=2

bDoHighDynamicRange=0





[BlurShader]

fSunlightDimmer=1.0000

fSIEmmisiveMult=1.0000

fSISpecularMult=1.0000

fSkyBrightness=0.5000

fSunBrightness=0.0000

fAlphaAddExterior=0.2000

fAlphaAddInterior=0.5000

iBlurTexSize=256

fBlurRadius=0.0300

iNumBlurpasses=1

iBlendType=2



bUseBlurShader=0





[GethitShader]

fBlurAmmount=0.5000

fBlockedTexOffset=0.0010

fHitTexOffset=0.0050





[MESSAGES]

bBlockMessageBoxes=0

bSkipProgramFlows=1

bAllowYesToAll=1

bDisableWarning=1

iFileLogging=0

bSkipInitializationFlows=1





[DistantLOD]

bUseLODLandData=0

fFadeDistance=12288.0000

iDistantLODGroupWidth=8





[GeneralWarnings]

SGeneralMasterMismatchWarning=One or more plugins could not find the correct versions of the master files they depend on. Errors may occur during load or game play. Check the "Warnings.txt" file for more information.



SMasterMismatchWarning=One of the files that "%s" is dependent on has changed since the last save.

This may result in errors. Saving again will clear this message

but not necessarily fix any errors.





[Archive]

SMasterMiscArchiveFileName=Oblivion - Misc.bsa

SMasterVoicesArchiveFileName2=Oblivion - Voices2.bsa

SMasterVoicesArchiveFileName1=Oblivion - Voices1.bsa

SMasterSoundsArchiveFileName=Oblivion - Sounds.bsa

SMasterTexturesArchiveFileName1=Oblivion - Textures - Compressed.bsa

SMasterMeshesArchiveFileName=Oblivion - Meshes.bsa

SInvalidationFile=ArchiveInvalidation.txt

iRetainFilenameOffsetTable=1

iRetainFilenameStringTable=1

iRetainDirectoryStringTable=1

bCheckRuntimeCollisions=0

bInvalidateOlderFiles=1

bUseArchives=1

SArchiveList=Oblivion - Meshes.bsa, Oblivion - Textures - Compressed.bsa, Oblivion - Sounds.bsa, Oblivion - Voices1.bsa, Oblivion - Voices2.bsa, Oblivion - Misc.bsa





[CameraPath]

iTake=0

SDirectoryName=TestCameraPath

iFPS=60

SNif=Test\CameraPath.nif





[Absorb]

fAbsorbGlowColorB=1.0000

fAbsorbGlowColorG=0.6000

fAbsorbGlowColorR=0.0000

fAbsorbCoreColorB=1.0000

fAbsorbCoreColorG=1.0000

fAbsorbCoreColorR=1.0000

iAbsorbNumBolts=1

fAbsorbBoltGrowWidth=0.0000

fAbsorbBoltSmallWidth=7.0000

fAbsorbTortuosityVariance=2.0000

fAbsorbSegmentVariance=7.0000

fAbsorbBoltsRadius=5.0000





[OPENMP]

iThreads=3

iOpenMPLevel=10





[TestAllCells]

bFileShowTextures=1

bFileShowIcons=1

bFileSkipIconChecks=0

bFileTestLoad=0

bFileNeededMessage=1

bFileGoneMessage=1

bFileSkipModelChecks=0

bFileCheckModelCollision=0





[CopyProtectionStrings]

SCopyProtectionMessage2=Insert the Oblivion Disc.

SCopyProtectionTitle2=Oblivion Disc Not Found

SCopyProtectionMessage=Unable to find a CD-ROM/DVD drive on this computer.

SCopyProtectionTitle=CD-ROM Drive Not Found
```

If anyone knows what I'm doing wrong, please tell me. Thanks for your time.

---

### Post by Mongoose on 2007-06-30
A 6200 does like 1/5th the shader and 1/3-1/4 vertex operations per second of a 6800 GS ( both PCI-E ).  Yeah, you'd have to turn off shaders and lighting I'd think -- so that ugly image is about right.  I still consider the 6800 the minimum under wine if you want all the whiz bang shaders.  I'm just being frank about the fact some cards can't really run Oblivion as it was intended.  I'm eyeing a 8600GTS right now, but the new Nvidia line up may be out this holiday season...  I have a small form factor case and the die shrink of the G84s are more appealing than the size and heat of the G80s.  There is a 512MB GDDR3 8600GTS coming out at the end of July iirc.  My only issue is the 128bit memory interface bottleneck on this card, but it crushes all 7xxx cards' skulls with shader operations to more than make up for it.  Beware of assholes selling DDR2 cards in any line.   Never buy a card without looking closely at the real specs.  I suggest [http://www.gpureview.com](http://www.gpureview.com)

Speaking of shaders... I was told that the new 9.0c patch should be in Wine sooner or later, which chould fix many if not all shader issues for those who's card supports it.  That means we might be able to flip the water and refraction shaders back on for lesser cards.  Wait and see I guess -- they have to fix the threading bugs first.  Looks like 0.9.40 has the same issues as 0.9.39 from reports.

---

### Post by lou1998 on 2007-07-03
Hi,
I followed the instructions in the wiki and read through this entire thread.  Oblivion works well until I try to leave the sewer.  Then it just shuts down.
I am running Ubuntu 6.06
Nvidia 7900GT with the 9755 driver
Wine 9.40

Thanks,
Lou

---

### Post by Mongoose on 2007-07-03
Try 0.9.38 then.  ;)

---

### Post by boosted_sled on 2007-07-03
I followed the guide and was running under 0.9.36 with all the usual reported problems but the game was basically playable.  The water sound problem was a pita, though.

I went to 0.9.39 and it crashes on load just as others have experienced

I went to 0.9.38 and the sound is fixed but now my frame rate is very erratic and frequently falls to <5 fps.  Sometimes it is fine.  Anyone else experience this?  Should I try 0.9.37?

I'm on athlon64 with a 7600 GS

---

### Post by boosted_sled on 2007-07-03
I did some more testing using a battle with about a dozen goblins who kick my a$$ after a few min.  Sometimes I get through it with 25+ fps and the gameplay is great.  Most of the time the frame rate drops to <5 in a step function and never recovers.  In either case the Oblivion .exe has one core hammered all the time.  The video mode doesn't have any effect on this.  Seems like some piece of code is slipping into a mode where it just starts hogging cycles.

This is *so* close.  The sound and gameplay are execellent when the framerate stays up.

---

### Post by Enverex on 2007-07-04
Sate of Oblivion in current GIT (pre .41)

Disable music in the INI file else you risk Wine going psycho once you get ingame.
Videos work but you're unable to skip the logo videos at the start (Bethesda, etc).
Performance is still generally poor (but playable).
Constant white noise is fixed.
The crash when entering an outside area (i.e. leaving the sewer) is fixed.
New regression causing the game to lock up if you move outside and the game tries to load further (this should be patched soon though).

Probably a few things I've forgotten. I've updated the AppDB page with all the bugs so check that for progress and details.

---

### Post by lordxale on 2007-07-18
Greetings fellow Oblivion players! I have a very peculiar problem with my Oblivion install...When I launch the game, I can only save for the first 1 or 2 minutes of play.  It doesn't seem to matter what I'm doing, as long as the game is running; if I take any time at all creating a character I'll never be able to save at all.  By using the default Imperial character, usually I can save right about until the Emperor and his bodyguards open the secret door in cell. The effect is the same when I use saves copied from my Windows install. 

I followed the guide here and from the UESP:wiki (which are nearly identical, and great guides, too!). I've tried wine 0.9.37, 0.9.38, all with the 1.0.something version of Oblivion that came on my install cd, the a 1.1.something version, and the newest 1.2 version from Bethesda's website. Now I've moved on to wine 0.9.41, and it's the same thing.  Naturally, I would think it's a permissions issue or something, but then why would it work for the first couple of minutes?  Either way, I've tried installing it in /opt and in the default directory, checked all my permissions a million times, checked my wine install, and I'm running out of ideas!

The only official reference to anything like this behavior is here: [http://bugs.winehq.org/show_bug.cgi?id=8128](http://bugs.winehq.org/show_bug.cgi?id=8128) but it was dismissed as an Oblivion problem, and that it should have been fixed with a new patch - well, on windows I never patched it at all and I never ran in to this, and nevertheless the behavior is the same with the newest patch.  The bug report in the link also suggests that you get only ONE save per play, and I can make as many saves as I want for the first couple minutes. Another user (can't remember where) posted that disabling music in the oblivion.ini file cured his save problems, (bMusicEnabled=0, I think, I'm not posting this from the computer it is installed on) but that didn't work for me.  

I've also tried a cracked exe in case the copy protection is at fault, but that didn't help either. I have not tried them with the newest version of wine yet, though.  

I'm leaning towards this problem being with Oblivion, simply because I can't find anything wrong with my wine install.  But, looking at some windows-only forums of Oblivion players hasn't turned up anything like this either.  

So I'm torn; I don't even know if I should be posting this here! I can't figure out if  this is my problem, wine's problem, or Oblivion's problem!

Help me! anybody! :) Thanks in advance for any help any of you might have!  For the record, my hardware is more than enough to get it going - a64 3200+ @ 2.2ghz, 2gb ddr400, evga 6800gs, audigy2 zs platinum on Kubuntu 7.04 i386.

Thanks, and sorry for writing you all a book!

---

### Post by Nick Blinko on 2007-07-19
I'm considering purchasing oblivion, especially since how I loved the previous elder scrolls games alot.

I have a few obstacles first though.
the first one is linux, but if I follow this guide correctly that shouldn't be too much of an issue.
The second one is my pc specs, they're pretty slim, but they do meet the minimum specs.
2.0ghz processor
512 mb of ram
GeForce 6200 256 mb agp8x

How well would it run? I don't care how bad the game looks, but would it be possible to have a stable 30- 40 fps with this setup with everything off or toned down? How well does oldblivion work and can I use that with ubuntu aswell?

---

### Post by Mongoose on 2007-07-19
It should be similar, since it's the same guide in wiki form.  I moved revisions of the guide from here and my personal webpage to the wiki, so it can be maintained outside the core 'Oblivion dudes' in this forum.  It helps keep questions to a minimum if more people can contribute.  At least with good moderation.  Several of us drop by and maintain the wiki from time to time.  ^^

I was never able to reproduce that bug myself, however I avoided several known issues by waiting for a proper patch.  I guess I should link the Linux wiki to a more general patch information.

You should read this:

[http://www.uesp.net/wiki/Oblivion:Patch](http://www.uesp.net/wiki/Oblivion:Patch)


Nick Blinko:

A 6200 is borderline, and you'd have to disable most of the visual effects including most lighting for that frame rate last I checked.  You're on AGP, so it may be hard to upgrade your GPU cheaply.  If you read an earlier post I made in this thread you'll see how underpowered that card is relative to a 6800, and my suggestions for picking the best GPU if you plan on upgrading.  I don't have anymore to add to that, really.

---

### Post by ironfistchamp on 2007-07-26
Has anyone got OBSE working in Wine? Some of my fav mods need it. Just wondered if anyone had a guide. I either get told that it does not support this version or it goes through and looks fine but doesn't start Oblivion.

Thanks

Ironfistchamp

---

### Post by blackjackel on 2007-07-27
I just followed the guide and i get this:

ELF     7e92b000-7e949000       Deferred        iphlpapi<elf>
  \-PE  7e930000-7e949000       \               iphlpapi
ELF     7e949000-7e9a2000       Deferred        rpcrt4<elf>
  \-PE  7e960000-7e9a2000       \               rpcrt4
ELF     7e9a2000-7ea41000       Deferred        ole32<elf>
  \-PE  7e9b0000-7ea41000       \               ole32
ELF     7ea41000-7ea77000       Deferred        dinput<elf>
  \-PE  7ea50000-7ea77000       \               dinput
ELF     7ea77000-7ea90000       Deferred        dinput8<elf>
  \-PE  7ea80000-7ea90000       \               dinput8
ELF     7ea90000-7ead8000       Deferred        advapi32<elf>
  \-PE  7eaa0000-7ead8000       \               advapi32
ELF     7ead8000-7eae4000       Deferred        libgcc_s.so.1
ELF     7ebce000-7ec8e000       Deferred        gdi32<elf>
  \-PE  7ebf0000-7ec8e000       \               gdi32
ELF     7ec8e000-7edcb000       Deferred        user32<elf>
  \-PE  7ecb0000-7edcb000       \               user32
ELF     7edcb000-7ee88000       Deferred        comctl32<elf>
  \-PE  7edd0000-7ee88000       \               comctl32
ELF     7ee88000-7ee93000       Deferred        libnss_files.so.2
ELF     7ee93000-7eeaa000       Deferred        libnsl.so.1
ELF     7eeaa000-7eeb3000       Deferred        libnss_compat.so.2
ELF     7efcf000-7eff6000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d50000-b7d54000       Deferred        libdl.so.2
ELF     b7d54000-b7e95000       Deferred        libc.so.6
ELF     b7e96000-b7ead000       Deferred        libpthread.so.0
ELF     b7eb7000-b7fcb000       Deferred        libwine.so.1
ELF     b7fcd000-b7fe8000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000f (D) C:\Program Files\Bethesda Softworks\Oblivion\Oblivion.exe
        00000014    1 <==
        00000013   -1
        00000012   -1
        00000011    0
        00000010    0
0000000b 
        0000000e    0
        0000000c    0

[email]remix5x@remix5x-desktop:~/.wine[/email]/drive_c/Program Files/Bethesda Softworks/Oblivion$ wine OblivionLauncher.exe 
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:win:SetLayeredWindowAttributes (0x20020,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20020,0x00000000,35,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20020,0x00000000,70,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20020,0x00000000,105,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20020,0x00000000,140,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20020,0x00000000,175,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20020,0x00000000,210,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20020,0x00000000,245,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20020,0x00000000,255,2): stub!
fixme:wave:wodPlayer_Reset shouldn't have headers left
[email]remix5x@remix5x-desktop:~/.wine[/email]/drive_c/Program Files/Bethesda Softworks/Oblivion$ ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:d3d:IWineD3DDeviceImpl_SetMultithreaded No thread safety in wined3d yet
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x19e538) : stub, simulating 768MB for now, returning 768MB left
wine: Unhandled page fault on read access to 0x00000d28 at address 0x7e31c7b6 (thread 0023), starting debugger...
Unhandled exception: page fault on read access to 0x00000d28 in 32-bit code (0x7e31c7b6).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e31c7b6 ESP:7cf71880 EBP:7cf718cc EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7d33b638 ECX:0019e538 EDX:0019e538
 ESI:00000000 EDI:ff000000
Stack dump:
0x7cf71880:  7d2a95db 00008d40 00000000 00000100
0x7cf71890:  00000000 00000003 18015ef6 00000040
0x7cf718a0:  7bc29ec1 00000001 00000040 0019e538
0x7cf718b0:  7e4cf924 00000000 ff000000 7cf718cc
0x7cf718c0:  7d33b638 00000000 ff000000 7cf7194c
0x7cf718d0:  7d2aa27e 0019e538 bd834d9e 00000000
Backtrace:
=>1 0x7e31c7b6 glIsRenderbufferEXT+0xe6() in libgl.so.1 (0x7cf718cc)
  2 0x7d2aa27e in wined3d (+0x2a27e) (0x7cf7194c)
  3 0x7d35565d in d3d9 (+0x565d) (0x7cf7197c)
  4 0x0041028a in oblivion (+0x1028a) (0x00000000)
0x7e31c7b6 glIsRenderbufferEXT+0xe6 in libgl.so.1: jmp  *0xd28(%eax)
Modules:
Module  Address                 Debug info      Name (94 modules)
PE        400000-  b59000       Export          oblivion
PE        b60000-  daf000       Deferred        d3dx9_27
PE      18000000-18068000       Deferred        binkw32
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d1f2000-7d272000       Deferred        libglu.so.1
ELF     7d272000-7d33d000       Export          wined3d<elf>
  \-PE  7d280000-7d33d000       \               wined3d
ELF     7d33d000-7d36b000       Export          d3d9<elf>
  \-PE  7d350000-7d36b000       \               d3d9
ELF     7d4c0000-7d4d5000       Deferred        midimap<elf>
  \-PE  7d4d0000-7d4d5000       \               midimap
ELF     7d4d5000-7d4fb000       Deferred        msacm32<elf>
  \-PE  7d4e0000-7d4fb000       \               msacm32
ELF     7d4fb000-7d5c0000       Deferred        libasound.so.2
ELF     7d5c0000-7d5f2000       Deferred        winealsa<elf>
  \-PE  7d5d0000-7d5f2000       \               winealsa
ELF     7d5f2000-7d624000       Deferred        uxtheme<elf>
  \-PE  7d600000-7d624000       \               uxtheme
ELF     7d87b000-7d893000       Deferred        msacm32<elf>
  \-PE  7d880000-7d893000       \               msacm32
ELF     7d895000-7d89a000       Deferred        libxfixes.so.3
ELF     7d89a000-7d8a3000       Deferred        libxcursor.so.1
ELF     7d8a3000-7d8c0000       Deferred        imm32<elf>
  \-PE  7d8b0000-7d8c0000       \               imm32
ELF     7d8c0000-7d8c6000       Deferred        libxrandr.so.2
ELF     7d8c6000-7d8ce000       Deferred        libxrender.so.1
ELF     7d8ef000-7d8f1000       Deferred        libnvidia-tls.so.1
ELF     7d8f1000-7e289000       Deferred        libglcore.so.1
ELF     7e289000-7e31f000       Export          libgl.so.1
ELF     7e31f000-7e324000       Deferred        libxdmcp.so.6
ELF     7e324000-7e327000       Deferred        libxau.so.6
ELF     7e327000-7e418000       Deferred        libx11.so.6
ELF     7e418000-7e426000       Deferred        libxext.so.6
ELF     7e426000-7e42b000       Deferred        libxxf86vm.so.1
ELF     7e42b000-7e443000       Deferred        libice.so.6
ELF     7e443000-7e44c000       Deferred        libsm.so.6
ELF     7e44c000-7e4d5000       Deferred        winex11<elf>
  \-PE  7e460000-7e4d5000       \               winex11
ELF     7e545000-7e565000       Deferred        libexpat.so.1
ELF     7e565000-7e590000       Deferred        libfontconfig.so.1
ELF     7e590000-7e5a4000       Deferred        libz.so.1
ELF     7e5a4000-7e60f000       Deferred        libfreetype.so.6
ELF     7e60f000-7e63c000       Deferred        ws2_32<elf>
  \-PE  7e620000-7e63c000       \               ws2_32
ELF     7e63c000-7e656000       Deferred        wsock32<elf>
  \-PE  7e640000-7e656000       \               wsock32
ELF     7e656000-7e6bd000       Deferred        msvcrt<elf>
  \-PE  7e670000-7e6bd000       \               msvcrt
ELF     7e6bd000-7e6d1000       Deferred        lz32<elf>
  \-PE  7e6c0000-7e6d1000       \               lz32
ELF     7e6d1000-7e6eb000       Deferred        version<elf>
  \-PE  7e6e0000-7e6eb000       \               version
ELF     7e6eb000-7e744000       Deferred        shlwapi<elf>
  \-PE  7e700000-7e744000       \               shlwapi
ELF     7e744000-7e842000       Deferred        shell32<elf>
  \-PE  7e760000-7e842000       \               shell32
ELF     7e842000-7e88a000       Deferred        dsound<elf>
  \-PE  7e850000-7e88a000       \               dsound
ELF     7e88a000-7e918000       Deferred        winmm<elf>
  \-PE  7e8a0000-7e918000       \               winmm
ELF     7e918000-7e92b000       Deferred        libresolv.so.2
ELF     7e92b000-7e949000       Deferred        iphlpapi<elf>
  \-PE  7e930000-7e949000       \               iphlpapi
ELF     7e949000-7e9a2000       Deferred        rpcrt4<elf>
  \-PE  7e960000-7e9a2000       \               rpcrt4
ELF     7e9a2000-7ea41000       Deferred        ole32<elf>
  \-PE  7e9b0000-7ea41000       \               ole32
ELF     7ea41000-7ea77000       Deferred        dinput<elf>
  \-PE  7ea50000-7ea77000       \               dinput
ELF     7ea77000-7ea90000       Deferred        dinput8<elf>
  \-PE  7ea80000-7ea90000       \               dinput8
ELF     7ea90000-7ead8000       Deferred        advapi32<elf>
  \-PE  7eaa0000-7ead8000       \               advapi32
ELF     7ead8000-7eae4000       Deferred        libgcc_s.so.1
ELF     7ebce000-7ec8e000       Deferred        gdi32<elf>
  \-PE  7ebf0000-7ec8e000       \               gdi32
ELF     7ec8e000-7edcb000       Deferred        user32<elf>
  \-PE  7ecb0000-7edcb000       \               user32
ELF     7edcb000-7ee88000       Deferred        comctl32<elf>
  \-PE  7edd0000-7ee88000       \               comctl32
ELF     7ee88000-7ee93000       Deferred        libnss_files.so.2
ELF     7ee93000-7eeaa000       Deferred        libnsl.so.1
ELF     7eeaa000-7eeb3000       Deferred        libnss_compat.so.2
ELF     7efcf000-7eff6000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d20000-b7d24000       Deferred        libdl.so.2
ELF     b7d24000-b7e65000       Deferred        libc.so.6
ELF     b7e66000-b7e7d000       Deferred        libpthread.so.0
ELF     b7e87000-b7f9b000       Deferred        libwine.so.1
ELF     b7f9d000-b7fb8000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000001e (D) C:\Program Files\Bethesda Softworks\Oblivion\Oblivion.exe
        00000023    1 <==
        00000022   -1
        00000021   -1
        00000020    0
        0000001f    0
0000001a 
        0000001d    0
        0000001b    0
wine OblivionLauncher.exe 
[email]remix5x@remix5x-desktop:~/.wine[/email]/drive_c/Program Files/Bethesda Softworks/Oblivion$ wine OblivionLauncher.exe 
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,35,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,70,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,105,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,140,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,175,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,210,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,245,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,255,2): stub!
fixme:wave:wodPlayer_Reset shouldn't have headers left
[email]remix5x@remix5x-desktop:~/.wine[/email]/drive_c/Program Files/Bethesda Softworks/Oblivion$ ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:d3d:IWineD3DDeviceImpl_SetMultithreaded No thread safety in wined3d yet
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x19e5d8) : stub, simulating 768MB for now, returning 768MB left
wine: Unhandled page fault on read access to 0x00000d28 at address 0x7e31a7b6 (thread 0014), starting debugger...
Unhandled exception: page fault on read access to 0x00000d28 in 32-bit code (0x7e31a7b6).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e31a7b6 ESP:7cf6f880 EBP:7cf6f8cc EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7d33a638 ECX:0019e5d8 EDX:0019e5d8
 ESI:00000000 EDI:ff000000
Stack dump:
0x7cf6f880:  7d2a85db 00008d40 00000000 00000100
0x7cf6f890:  00000000 00000003 18015ef6 00000040
0x7cf6f8a0:  7bc29ec1 00000001 00000040 0019e5d8
0x7cf6f8b0:  7e4cd924 00000000 ff000000 7cf6f8cc
0x7cf6f8c0:  7d33a638 00000000 ff000000 7cf6f94c
0x7cf6f8d0:  7d2a927e 0019e5d8 9eceabe6 00000000
Backtrace:
=>1 0x7e31a7b6 glIsRenderbufferEXT+0xe6() in libgl.so.1 (0x7cf6f8cc)
  2 0x7d2a927e in wined3d (+0x2927e) (0x7cf6f94c)
  3 0x7d35465d in d3d9 (+0x1465d) (0x7cf6f97c)
  4 0x0041028a in oblivion (+0x1028a) (0x00000000)
0x7e31a7b6 glIsRenderbufferEXT+0xe6 in libgl.so.1: jmp  *0xd28(%eax)
Modules:
Module  Address                 Debug info      Name (94 modules)
PE        400000-  b59000       Export          oblivion
PE        b60000-  daf000       Deferred        d3dx9_27
PE      18000000-18068000       Deferred        binkw32
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d1f1000-7d271000       Deferred        libglu.so.1
ELF     7d271000-7d33c000       Export          wined3d<elf>
  \-PE  7d280000-7d33c000       \               wined3d
ELF     7d33c000-7d36a000       Export          d3d9<elf>
  \-PE  7d340000-7d36a000       \               d3d9
ELF     7d4bf000-7d4d4000       Deferred        midimap<elf>
  \-PE  7d4d0000-7d4d4000       \               midimap
ELF     7d4d4000-7d4fa000       Deferred        msacm32<elf>
  \-PE  7d4e0000-7d4fa000       \               msacm32
ELF     7d4fa000-7d5bf000       Deferred        libasound.so.2
ELF     7d5bf000-7d5f1000       Deferred        winealsa<elf>
  \-PE  7d5d0000-7d5f1000       \               winealsa
ELF     7d5f1000-7d623000       Deferred        uxtheme<elf>
  \-PE  7d600000-7d623000       \               uxtheme
ELF     7d879000-7d891000       Deferred        msacm32<elf>
  \-PE  7d880000-7d891000       \               msacm32
ELF     7d893000-7d898000       Deferred        libxfixes.so.3
ELF     7d898000-7d8a1000       Deferred        libxcursor.so.1
ELF     7d8a1000-7d8be000       Deferred        imm32<elf>
  \-PE  7d8b0000-7d8be000       \               imm32
ELF     7d8be000-7d8c4000       Deferred        libxrandr.so.2
ELF     7d8c4000-7d8cc000       Deferred        libxrender.so.1
ELF     7d8ed000-7d8ef000       Deferred        libnvidia-tls.so.1
ELF     7d8ef000-7e287000       Deferred        libglcore.so.1
ELF     7e287000-7e31d000       Export          libgl.so.1
ELF     7e31d000-7e322000       Deferred        libxdmcp.so.6
ELF     7e322000-7e325000       Deferred        libxau.so.6
ELF     7e325000-7e416000       Deferred        libx11.so.6
ELF     7e416000-7e424000       Deferred        libxext.so.6
ELF     7e424000-7e429000       Deferred        libxxf86vm.so.1
ELF     7e429000-7e441000       Deferred        libice.so.6
ELF     7e441000-7e44a000       Deferred        libsm.so.6
ELF     7e44a000-7e4d3000       Deferred        winex11<elf>
  \-PE  7e460000-7e4d3000       \               winex11
ELF     7e545000-7e565000       Deferred        libexpat.so.1
ELF     7e565000-7e590000       Deferred        libfontconfig.so.1
ELF     7e590000-7e5a4000       Deferred        libz.so.1
ELF     7e5a4000-7e60f000       Deferred        libfreetype.so.6
ELF     7e60f000-7e63c000       Deferred        ws2_32<elf>
  \-PE  7e620000-7e63c000       \               ws2_32
ELF     7e63c000-7e656000       Deferred        wsock32<elf>
  \-PE  7e640000-7e656000       \               wsock32
ELF     7e656000-7e6bd000       Deferred        msvcrt<elf>
  \-PE  7e670000-7e6bd000       \               msvcrt
ELF     7e6bd000-7e6d1000       Deferred        lz32<elf>
  \-PE  7e6c0000-7e6d1000       \               lz32
ELF     7e6d1000-7e6eb000       Deferred        version<elf>
  \-PE  7e6e0000-7e6eb000       \               version
ELF     7e6eb000-7e744000       Deferred        shlwapi<elf>
  \-PE  7e700000-7e744000       \               shlwapi
ELF     7e744000-7e842000       Deferred        shell32<elf>
  \-PE  7e760000-7e842000       \               shell32
ELF     7e842000-7e88a000       Deferred        dsound<elf>
  \-PE  7e850000-7e88a000       \               dsound
ELF     7e88a000-7e918000       Deferred        winmm<elf>
  \-PE  7e8a0000-7e918000       \               winmm
ELF     7e918000-7e92b000       Deferred        libresolv.so.2
ELF     7e92b000-7e949000       Deferred        iphlpapi<elf>
  \-PE  7e930000-7e949000       \               iphlpapi
ELF     7e949000-7e9a2000       Deferred        rpcrt4<elf>
  \-PE  7e960000-7e9a2000       \               rpcrt4
ELF     7e9a2000-7ea41000       Deferred        ole32<elf>
  \-PE  7e9b0000-7ea41000       \               ole32
ELF     7ea41000-7ea77000       Deferred        dinput<elf>
  \-PE  7ea50000-7ea77000       \               dinput
ELF     7ea77000-7ea90000       Deferred        dinput8<elf>
  \-PE  7ea80000-7ea90000       \               dinput8
ELF     7ea90000-7ead8000       Deferred        advapi32<elf>
  \-PE  7eaa0000-7ead8000       \               advapi32
ELF     7ead8000-7eae4000       Deferred        libgcc_s.so.1
ELF     7ebce000-7ec8e000       Deferred        gdi32<elf>
  \-PE  7ebf0000-7ec8e000       \               gdi32
ELF     7ec8e000-7edcb000       Deferred        user32<elf>
  \-PE  7ecb0000-7edcb000       \               user32
ELF     7edcb000-7ee88000       Deferred        comctl32<elf>
  \-PE  7edd0000-7ee88000       \               comctl32
ELF     7ee88000-7ee93000       Deferred        libnss_files.so.2
ELF     7ee93000-7eeaa000       Deferred        libnsl.so.1
ELF     7eeaa000-7eeb3000       Deferred        libnss_compat.so.2
ELF     7efcf000-7eff6000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7cbe000-b7cc2000       Deferred        libdl.so.2
ELF     b7cc2000-b7e03000       Deferred        libc.so.6
ELF     b7e04000-b7e1b000       Deferred        libpthread.so.0
ELF     b7e25000-b7f39000       Deferred        libwine.so.1
ELF     b7f3b000-b7f56000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000f (D) C:\Program Files\Bethesda Softworks\Oblivion\Oblivion.exe
        00000014    1 <==
        00000013   -1
        00000012   -1
        00000011    0
        00000010    0
0000000b 
        0000000e    0
        0000000c    0

[email]remix5x@remix5x-desktop:~/.wine[/email]/drive_c/Program Files/Bethesda Softworks/Oblivion$ [email]remix5x@remix5x-desktop:~/.wine[/email]/drive_c/Program Files/Bethesda Softworks/Oblivion$ clrsc
bash: clrsc: command not found
[email]remix5x@remix5x-desktop:~/.wine[/email]/drive_c/Program Files/Bethesda Softworks/Oblivion$ clear screen

[email]remix5x@remix5x-desktop:~/.wine[/email]/drive_c/Program Files/Bethesda Softworks/Oblivion$ wine OblivionLauncher.exe 
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,35,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,70,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,105,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,140,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,175,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,210,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,245,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,255,2): stub!
fixme:wave:wodPlayer_Reset shouldn't have headers left
[email]remix5x@remix5x-desktop:~/.wine[/email]/drive_c/Program Files/Bethesda Softworks/Oblivion$ fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:d3d:IWineD3DDeviceImpl_SetMultithreaded No thread safety in wined3d yet
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1c9010) : stub, simulating 768MB for now, returning 768MB left
wine: Unhandled page fault on read access to 0x00000d28 at address 0x7e31b7b6 (thread 0016), starting debugger...
Unhandled exception: page fault on read access to 0x00000d28 in 32-bit code (0x7e31b7b6).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e31b7b6 ESP:7cd1e880 EBP:7cd1e8cc EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7d0e9638 ECX:001c9010 EDX:001c9010
 ESI:00000000 EDI:ff000000
Stack dump:
0x7cd1e880:  7d0575db 00008d40 00000000 00000000
0x7cd1e890:  31cb32b2 7bc57e9b 7bc7b498 00000000
0x7cd1e8a0:  7bc29ec1 7cd1e934 7bc5bdfb 7cd1e8b8
0x7cd1e8b0:  7e4ce924 00000000 ff000000 7cd1e8cc
0x7cd1e8c0:  7d0e9638 00000000 ff000000 7cd1e94c
0x7cd1e8d0:  7d05827e 001c9010 00000000 00000000
Backtrace:
=>1 0x7e31b7b6 glIsRenderbufferEXT+0xe6() in libgl.so.1 (0x7cd1e8cc)
  2 0x7d05827e in wined3d (+0x2827e) (0x7cd1e94c)
  3 0x7d10365d in d3d9 (+0x1365d) (0x7cd1e97c)
  4 0x0041028a in oblivion (+0x1028a) (0x00000000)
0x7e31b7b6 glIsRenderbufferEXT+0xe6 in libgl.so.1: jmp  *0xd28(%eax)
Modules:
Module  Address                 Debug info      Name (94 modules)
PE        400000-  b59000       Export          oblivion
PE        b60000-  daf000       Deferred        d3dx9_27
PE      18000000-18068000       Deferred        binkw32
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cfa0000-7d020000       Deferred        libglu.so.1
ELF     7d020000-7d0eb000       Export          wined3d<elf>
  \-PE  7d030000-7d0eb000       \               wined3d
ELF     7d0eb000-7d119000       Export          d3d9<elf>
  \-PE  7d0f0000-7d119000       \               d3d9
ELF     7d4c0000-7d4d5000       Deferred        midimap<elf>
  \-PE  7d4d0000-7d4d5000       \               midimap
ELF     7d4d5000-7d4fb000       Deferred        msacm32<elf>
  \-PE  7d4e0000-7d4fb000       \               msacm32
ELF     7d4fb000-7d5c0000       Deferred        libasound.so.2
ELF     7d5c0000-7d5f2000       Deferred        winealsa<elf>
  \-PE  7d5d0000-7d5f2000       \               winealsa
ELF     7d5f2000-7d624000       Deferred        uxtheme<elf>
  \-PE  7d600000-7d624000       \               uxtheme
ELF     7d87a000-7d892000       Deferred        msacm32<elf>
  \-PE  7d880000-7d892000       \               msacm32
ELF     7d894000-7d899000       Deferred        libxfixes.so.3
ELF     7d899000-7d8a2000       Deferred        libxcursor.so.1
ELF     7d8a2000-7d8bf000       Deferred        imm32<elf>
  \-PE  7d8b0000-7d8bf000       \               imm32
ELF     7d8bf000-7d8c5000       Deferred        libxrandr.so.2
ELF     7d8c5000-7d8cd000       Deferred        libxrender.so.1
ELF     7d8ee000-7d8f0000       Deferred        libnvidia-tls.so.1
ELF     7d8f0000-7e288000       Deferred        libglcore.so.1
ELF     7e288000-7e31e000       Export          libgl.so.1
ELF     7e31e000-7e323000       Deferred        libxdmcp.so.6
ELF     7e323000-7e326000       Deferred        libxau.so.6
ELF     7e326000-7e417000       Deferred        libx11.so.6
ELF     7e417000-7e425000       Deferred        libxext.so.6
ELF     7e425000-7e42a000       Deferred        libxxf86vm.so.1
ELF     7e42a000-7e442000       Deferred        libice.so.6
ELF     7e442000-7e44b000       Deferred        libsm.so.6
ELF     7e44b000-7e4d4000       Deferred        winex11<elf>
  \-PE  7e460000-7e4d4000       \               winex11
ELF     7e545000-7e565000       Deferred        libexpat.so.1
ELF     7e565000-7e590000       Deferred        libfontconfig.so.1
ELF     7e590000-7e5a4000       Deferred        libz.so.1
ELF     7e5a4000-7e60f000       Deferred        libfreetype.so.6
ELF     7e60f000-7e63c000       Deferred        ws2_32<elf>
  \-PE  7e620000-7e63c000       \               ws2_32
ELF     7e63c000-7e656000       Deferred        wsock32<elf>
  \-PE  7e640000-7e656000       \               wsock32
ELF     7e656000-7e6bd000       Deferred        msvcrt<elf>
  \-PE  7e670000-7e6bd000       \               msvcrt
ELF     7e6bd000-7e6d1000       Deferred        lz32<elf>
  \-PE  7e6c0000-7e6d1000       \               lz32
ELF     7e6d1000-7e6eb000       Deferred        version<elf>
  \-PE  7e6e0000-7e6eb000       \               version
ELF     7e6eb000-7e744000       Deferred        shlwapi<elf>
  \-PE  7e700000-7e744000       \               shlwapi
ELF     7e744000-7e842000       Deferred        shell32<elf>
  \-PE  7e760000-7e842000       \               shell32
ELF     7e842000-7e88a000       Deferred        dsound<elf>
  \-PE  7e850000-7e88a000       \               dsound
ELF     7e88a000-7e918000       Deferred        winmm<elf>
  \-PE  7e8a0000-7e918000       \               winmm
ELF     7e918000-7e92b000       Deferred        libresolv.so.2
ELF     7e92b000-7e949000       Deferred        iphlpapi<elf>
  \-PE  7e930000-7e949000       \               iphlpapi
ELF     7e949000-7e9a2000       Deferred        rpcrt4<elf>
  \-PE  7e960000-7e9a2000       \               rpcrt4
ELF     7e9a2000-7ea41000       Deferred        ole32<elf>
  \-PE  7e9b0000-7ea41000       \               ole32
ELF     7ea41000-7ea77000       Deferred        dinput<elf>
  \-PE  7ea50000-7ea77000       \               dinput
ELF     7ea77000-7ea90000       Deferred        dinput8<elf>
  \-PE  7ea80000-7ea90000       \               dinput8
ELF     7ea90000-7ead8000       Deferred        advapi32<elf>
  \-PE  7eaa0000-7ead8000       \               advapi32
ELF     7ead8000-7eae4000       Deferred        libgcc_s.so.1
ELF     7ebce000-7ec8e000       Deferred        gdi32<elf>
  \-PE  7ebf0000-7ec8e000       \               gdi32
ELF     7ec8e000-7edcb000       Deferred        user32<elf>
  \-PE  7ecb0000-7edcb000       \               user32
ELF     7edcb000-7ee88000       Deferred        comctl32<elf>
  \-PE  7edd0000-7ee88000       \               comctl32
ELF     7ee88000-7ee93000       Deferred        libnss_files.so.2
ELF     7ee93000-7eeaa000       Deferred        libnsl.so.1
ELF     7eeaa000-7eeb3000       Deferred        libnss_compat.so.2
ELF     7efcf000-7eff6000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d0f000-b7d13000       Deferred        libdl.so.2
ELF     b7d13000-b7e54000       Deferred        libc.so.6
ELF     b7e55000-b7e6c000       Deferred        libpthread.so.0
ELF     b7e76000-b7f8a000       Deferred        libwine.so.1
ELF     b7f8c000-b7fa7000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000f (D) C:\Program Files\Bethesda Softworks\Oblivion\Oblivion.exe
        00000018   -1
        00000017   15
        00000016    1 <==
        00000015   -1
        00000014   -1
        00000013   15
        00000011    0
        00000010    0
0000000b 
        0000000e    0
        0000000c    0




The game looks like its about to launch, flickers, then just dumps me back to the desktop.

Latest nvidia drivers, dual 8800 ultras in SLI.

---

### Post by Mongoose on 2007-07-27
What version of WINE is that?  Also are you sure you have the latest Nvidia drivers?  It could be a threading issue causing that invalid address.  It could also be failing to load the extention properly, but it's hard to tell not knowing more about it.

---

### Post by jjmatt on 2007-07-28
So i just installed wine and oblivion like your how to suggested, everything works fine, except when I try to load a game, it will load, then drop me into the game, but the screen is all black, and I get this error in wine:
> 
err:ntdll:RtlpWaitForCriticalSection section 0x13b6b8c "?" wait timed out in thread 0010, blocked by 0015, retrying (60 sec)


There is more output that happens before this, but I'm assuming that's the only thing that corresponds to the unresponsive black screen.

I'm running wine-0.9.41, the latest oblivion, and have the latest nvidia drivers. I have a nvidia geforce 6800. 

Thanks for your help

[edit] also, if it helps, when I went to edit the registry in wine, there was no section titled Direct3D, so I coudln't change any settings

---

### Post by Mongoose on 2007-07-29
1. Don't use 0.9.41 use the suggested version 0.9.38 first.  Once you have that working try your luck with the broken threading. 

2. If you read the wiki more carefully it tells you how to make the Direct3D section.  I have considered making the text blink as everyone skips over it.  I've now made it as easy as possible with step by step instructions.  To make it easier would assume no piror knowledge of English or basic modern computing skills.

If the Direct3D key 'folder' does not exist then you can create it.  
1. Right-click the Wine folder icon. 
2. Select New > Key from the pop-up menu.
3. Name the new 'folder' Direct3D.

Update:
Updated Known Issues on the wiki, which notes that Wine 0.9.39+ crashes with pbuffer in use on transistions and more.

---

### Post by PurposeOfReason on 2007-08-19
I followed this guide to get Oblivion to run even the part about using 32bit wine even though they offer 64bit. Oblivion installed fine and the menu starts, but when I click play there is a flicker and then it stops. The only thing that didn't go well was cabextrat which gave me:
```
shawn@shawn-desktop:~$ cabextract /media/cdrom/DXREDIST/Aug2005_d3dx9_27_x86.cab
/media/cdrom/DXREDIST/Aug2005_d3dx9_27_x86.cab: Input/output error

All done, errors in processing 1 file(s)
shawn@shawn-desktop:~$
```

Terminal output for starting Oblivion
```
shawn@shawn-desktop:~$ wine /media/cdrom0/OblivionLauncher.exe
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,35,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,70,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,105,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,140,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,175,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,210,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,245,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,255,2): stub!
shawn@shawn-desktop:~$ ALSA lib ../../../src/pcm/pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:d3d:IWineD3DDeviceImpl_SetMultithreaded No thread safety in wined3d yet
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1985b0) : stub, simulating 512MB for now, returning 512MB left
wine: Unhandled page fault on read access to 0x00000d28 at address 0x7e422446 (thread 0013), starting debugger...
Unhandled exception: page fault on read access to 0x00000d28 in 32-bit code (0x7e422446).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7e422446 ESP:7cc1b880 EBP:7cc1b8cc EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7cffcb58 ECX:001985b0 EDX:001985b0
 ESI:0017a1e8 EDI:ff000000
Stack dump:
0x7cc1b880:  7cf6d88b 00008d40 00000000 00000100
0x7cc1b890:  00000000 00000003 18015ef6 00000040
0x7cc1b8a0:  7bc29ec1 00000001 00000040 001985b0
0x7cc1b8b0:  7e5e8544 0017a1e8 ff000000 7cc1b8cc
0x7cc1b8c0:  7cffcb58 0017a1e8 ff000000 7cc1b94c
0x7cc1b8d0:  7cf6e637 001985b0 272362f8 00000000
Backtrace:
=>1 0x7e422446 glIsRenderbufferEXT+0xe6() in libgl.so.1 (0x7cc1b8cc)
  2 0x7cf6e637 in wined3d (+0x1e637) (0x7cc1b94c)
  3 0x7d015aa5 in d3d9 (+0x5aa5) (0x7cc1b97c)
  4 0x0041028a in oblivion (+0x1028a) (0x00000000)
0x7e422446 glIsRenderbufferEXT+0xe6 in libgl.so.1: jmp  *0xd28(%eax)
Modules:
Module  Address                 Debug info      Name (94 modules)
PE        400000-  b59000       Export          oblivion
PE        b60000-  daf000       Deferred        d3dx9_27
PE      18000000-18068000       Deferred        binkw32
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bc98000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc98000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cea4000-7cf24000       Deferred        libglu.so.1
ELF     7cf36000-7cffe000       Export          wined3d<elf>
  \-PE  7cf50000-7cffe000       \               wined3d
ELF     7cffe000-7d02a000       Export          d3d9<elf>
  \-PE  7d010000-7d02a000       \               d3d9
ELF     7d168000-7d17d000       Deferred        midimap<elf>
  \-PE  7d170000-7d17d000       \               midimap
ELF     7d17d000-7d1a3000       Deferred        msacm32<elf>
  \-PE  7d180000-7d1a3000       \               msacm32
ELF     7d1a3000-7d268000       Deferred        libasound.so.2
ELF     7d268000-7d29a000       Deferred        winealsa<elf>
  \-PE  7d270000-7d29a000       \               winealsa
ELF     7d29a000-7d2cc000       Deferred        uxtheme<elf>
  \-PE  7d2a0000-7d2cc000       \               uxtheme
ELF     7d51d000-7d535000       Deferred        msacm32<elf>
  \-PE  7d520000-7d535000       \               msacm32
ELF     7d535000-7d53a000       Deferred        libxfixes.so.3
ELF     7d53a000-7d543000       Deferred        libxcursor.so.1
ELF     7d543000-7d560000       Deferred        imm32<elf>
  \-PE  7d550000-7d560000       \               imm32
ELF     7d560000-7d568000       Deferred        libxrender.so.1
ELF     7db10000-7db12000       Deferred        libnvidia-tls.so.1
ELF     7db12000-7e398000       Deferred        libglcore.so.1
ELF     7e398000-7e424000       Export          libgl.so.1
ELF     7e424000-7e429000       Deferred        libxdmcp.so.6
ELF     7e429000-7e42c000       Deferred        libxau.so.6
ELF     7e42c000-7e51d000       Deferred        libx11.so.6
ELF     7e51d000-7e52b000       Deferred        libxext.so.6
ELF     7e52b000-7e530000       Deferred        libxxf86vm.so.1
ELF     7e530000-7e548000       Deferred        libice.so.6
ELF     7e548000-7e551000       Deferred        libsm.so.6
ELF     7e552000-7e558000       Deferred        libxrandr.so.2
ELF     7e563000-7e5f2000       Deferred        winex11<elf>
  \-PE  7e570000-7e5f2000       \               winex11
ELF     7e65b000-7e67b000       Deferred        libexpat.so.1
ELF     7e67b000-7e6a6000       Deferred        libfontconfig.so.1
ELF     7e6a6000-7e6ba000       Deferred        libz.so.1
ELF     7e6ba000-7e724000       Deferred        libfreetype.so.6
ELF     7e724000-7e751000       Deferred        ws2_32<elf>
  \-PE  7e730000-7e751000       \               ws2_32
ELF     7e751000-7e76b000       Deferred        wsock32<elf>
  \-PE  7e760000-7e76b000       \               wsock32
ELF     7e76b000-7e7d2000       Deferred        msvcrt<elf>
  \-PE  7e780000-7e7d2000       \               msvcrt
ELF     7e7d2000-7e7e6000       Deferred        lz32<elf>
  \-PE  7e7e0000-7e7e6000       \               lz32
ELF     7e7e6000-7e800000       Deferred        version<elf>
  \-PE  7e7f0000-7e800000       \               version
ELF     7e800000-7e859000       Deferred        shlwapi<elf>
  \-PE  7e810000-7e859000       \               shlwapi
ELF     7e859000-7e957000       Deferred        shell32<elf>
  \-PE  7e870000-7e957000       \               shell32
ELF     7e957000-7e9a0000       Deferred        dsound<elf>
  \-PE  7e960000-7e9a0000       \               dsound
ELF     7e9a0000-7ea2f000       Deferred        winmm<elf>
  \-PE  7e9b0000-7ea2f000       \               winmm
ELF     7ea2f000-7ea42000       Deferred        libresolv.so.2
ELF     7ea42000-7ea60000       Deferred        iphlpapi<elf>
  \-PE  7ea50000-7ea60000       \               iphlpapi
ELF     7ea60000-7eab5000       Deferred        rpcrt4<elf>
  \-PE  7ea70000-7eab5000       \               rpcrt4
ELF     7eab5000-7eb54000       Deferred        ole32<elf>
  \-PE  7eac0000-7eb54000       \               ole32
ELF     7eb54000-7eb8a000       Deferred        dinput<elf>
  \-PE  7eb60000-7eb8a000       \               dinput
ELF     7eb8a000-7eba3000       Deferred        dinput8<elf>
  \-PE  7eb90000-7eba3000       \               dinput8
ELF     7eba3000-7ebeb000       Deferred        advapi32<elf>
  \-PE  7ebb0000-7ebeb000       \               advapi32
ELF     7ebeb000-7ebf7000       Deferred        libgcc_s.so.1
ELF     7ece1000-7eda1000       Deferred        gdi32<elf>
  \-PE  7ed00000-7eda1000       \               gdi32
ELF     7eda1000-7eede000       Deferred        user32<elf>
  \-PE  7edc0000-7eede000       \               user32
ELF     7eede000-7ef9b000       Deferred        comctl32<elf>
  \-PE  7eef0000-7ef9b000       \               comctl32
ELF     7ef9b000-7efa6000       Deferred        libnss_files.so.2
ELF     7efa6000-7efb0000       Deferred        libnss_nis.so.2
ELF     7efb0000-7efc7000       Deferred        libnsl.so.1
ELF     7efc7000-7efee000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     f7cb9000-f7cbd000       Deferred        libdl.so.2
ELF     f7cbd000-f7dfe000       Deferred        libc.so.6
ELF     f7dff000-f7e16000       Deferred        libpthread.so.0
ELF     f7e28000-f7f3c000       Deferred        libwine.so.1
ELF     f7f3e000-f7f5c000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e (D) C:\Program Files\Bethesda Softworks\Oblivion\Oblivion.exe
        00000013    1 <==
        00000012   -1
        00000011   -1
        00000010    0
        0000000f    0
0000000b 
        0000000c    0

```

---

### Post by PurposeOfReason on 2007-08-19
Well I was able to get the game to run now. The only problems are that when one of the Mythic Dawn are killed at the beginning the screen goes yellow for a while. I guess from the effect that happens when they die. Then when I try to exit the sewer, the games just closes.

---

### Post by Mongoose on 2007-08-20
Are you not running WINE 0.9.38?

**Wine 0.9.39+ crashes with pbuffer in use on transistions and more.**

Read the Known Issues section in the wiki.

---

### Post by HeavyAl on 2007-08-22
Hey guys, anyone tried this with the new Wine 0.9.43? Are we still having the pthread issue or any of the other show stoppers?

---

### Post by 47thRonin on 2007-08-23
hi. i got cedega 6.0.2 on ubuntu7.04. i am a new user of linux.  so i installed game from cedega and i 8600gt sonic vga. i installad nvidia driver with envy. my wine version is 0.9.43 and i close bloom and hdr and vsync and distant areas... etc. vertex shader 2.0 and other one 2.0 and i glsh flaot ... everything is ok. and i m looked at the first post on this forum and i got it and used that settings but no changes finnaly. i have got same problem from introduction. so this is my screenshot. it tells what my problem is. (sorry about my poor english) please heeeelp

[IMG]http://i13.tinypic.com/5zeetsx.jpg[/IMG]

---

### Post by HeavyAl on 2007-08-23
> **HeavyAl said:**
> Hey guys, anyone tried this with the new Wine 0.9.43? Are we still having the pthread issue or any of the other show stoppers?

Hehe, well, sorry to quote myself, but YEAH, it DOES work with the latest wine. Almost flawlessly. I get the yellow color explosion when the guys in the red hoods die, but so far thats it - no pthreads issue! You do still have to turn off hdr and bloom though .. kind of sucks because this machine is one of the new dell inspiron 1720's with an nvidia 256 megs ram - it came with Vista (what a POS!!) and ran Oblivion in full wide-screen glory with everything set to max .. I guess wine will get there eventually but this will do for now ..

---

### Post by patros on 2007-08-24
Ok, I've read the Oblivion:Linux UESPWiki and followed the directions there. I've also read every single post here... all 37 pages.

I uninstalled my wine and deleted my .wine directory (I had the current Feisty version installed). I installed wine version 0.9.38 from winehq, followed the UESP wiki instruction to the letter. I even tried it again just in case I missed something. I've deleted my .wine directory and my oblivion.ini and started over from scratch in case I stuffed something up.

My laptop specs...
Ubuntu Feisty (all packages upto date)
Latest Ubuntu nVidia drivers (1.0-9755)
Wine version 0.9.38 from winehq
Intel dual core T2250 @ 1.73GHz (I tried setting the cpu freq so it remained maxed out on both cores)
2G Ram
nVidia Geforce Go 7600/PCI/SSE2 256Mb
I'm using the original DVD.

The game looks great, some sound issues but that's not my problem. My FPS sit around 20 (resolution 800x600), but if I cast a spell, fight, run around, etc they drop as low as 5, and that's indoors. Changing resolution doesn't seem to have any affect on my FPS, it's the same at 1440x900.

I've enabled the threading options in the oblivion.ini but only one core is being used. My system recognises two cores and uses them but wine/oblivion only makes use of one of them. Could this be my problem or is my system just not up to spec. I don't know that much about 3d rendering but I thought my video card would be ok.

Thanks for any help.

---

### Post by Mongoose on 2007-08-25
Did you disable the refraction and 'water' shaders as suggested?  Also you're amount of video memory may get some texture thrashing, but I forgot if that's always the case.

Yeah, the thing to remember with gaming in WINE is that it's always a very specific setup to get best results.

---

### Post by Mongoose on 2007-08-25
It's good to hear a report that pbuffers issue is likely resolved.  ^^

---

### Post by patros on 2007-08-25
Thanks for still answering questions on this thread Mongoose.

I'd already disabled the refraction and water shaders and set texture size to small.

Is it normal that Oblivion won't use both cores in my system? Has anyone else had Oblivion in Wine making use of a dual core?

---

### Post by Mongoose on 2007-08-25
[http://www.gpureview.com/show_cards.php?card1=368&card2=409](http://www.gpureview.com/show_cards.php?card1=368&card2=409)

Yeah, your card is a little 'slow' for the game.  I consider the shader operations and memory bandwidth of the 6800 AGP the floor for this game ( in WINE ) as you may have read.  You may be best served looking at tweak guides on the web for lower end cards.  They have detailed option descriptions that will help you make the best compromises.  If you just want smooth play over graphics you can disable some of the lighting passes with just a console command.  I have disabled everything but diffuse+texture pass to avoid overheating a few times, and it'll also give quite a frame rate boost.  Good luck.

---

### Post by hugstrees on 2007-08-25
Hi, hopefully This question hasn't been answered already.  I searched and came up with nothing.  Maybe you can help me out.  I followed the installation guide, and I can run OblivionLauncher.exe.  However, when I click Play, it just dies, and this is my terminal output:

```
[user]@[user]:~/My Games/Oblivion$ err:module:import_dll Library d3dx9_27.dll (which is needed by L"C:\\windows\\profiles\\[user]\\My Documents\\My Games\\Oblivion\\Oblivion.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\profiles\\[user]\\My Documents\\My Games\\Oblivion\\Oblivion.exe" failed, status c0000135
```

The guide did mention that I would need to run cabextract, and I did, but no luck :(

Any idea what I've done wrong?  Any help would be much appreciated.

---

### Post by patros on 2007-08-26
Hi hugstrees, I think I know what you have done. Check out the [http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux) wiki page. This thread leaves out the command to actually copy the file d3dx9_27.dll to your system32 folder. It only has the command to extract the file.

---

### Post by hugstrees on 2007-08-26
Thank for the reply, that seems to have done the trick!  Now it's telling me that it's unable to detect a cd-rom/dvd drive, though.
Edit: Sorry, I got it working.  Thanks again for the help!

---

### Post by Mongoose on 2007-08-26
I'll check the wiki, since it's likely someone could've 'nuked' the copy command at one point.  We had a problem with Windows users trying to 'fix' it once or twice.  There is no xcopy in Linux.  ^^

Update:

cp d3dx9_27.dll ~/.wine/drive_c/windows/system32/  <-- yeah it was there... I could expand on that I guess

---

### Post by patros on 2007-08-26
The command is on the wiki page but it is not on the first post of this thread. I guess they missed the part about the wiki page being the upto date version to refer to.

---

### Post by HeavyAl on 2007-08-28
Hey all,

I was wondering, has anyone tried comparing their experience running Oblivion with WINE vs running it in Cedega? 

I've personally found that Cedega runs Oblivion smoother than WINE but with the caveat that the character textures are all skewed/stretched. Under WINE everything works including the textures, but the response of the game is slower overall. 

I wonder what extra optimizations are being done in Cedega to get the performance improvements? I was under the impression that the Cedega engine was not much different than the WINE implementation .. perhaps not, eh?

Anyway, here are my (most pertinent) specs; any recommendations are appreciated:

Dell 1721 w/ Core 2 DUO
2Gigs RAM
nVidia 256 Meg geforce go 8600

---

### Post by drspastic on 2007-09-07
Hi Mongoose

I'm afraid I don't understand this below section of your HOWTO. I do receive the disk space error. Could you please clarify as to how exactly I 'map' another drive?

you wrote:-

6. Installing in Wine. There is nothing to this one, you just click and go. The only thing that might bite you is if you see the error 'out of disk space', and you know you have enough space. If you see this you might want to map another drive in Wine to the partition you're installing on. For example I use G: for my /opt partition. After this Wine will see the correct disk space for /opt on the G: drive.


Code:

	# Use /media/cdrom or whatever your mount point is here.
	cd /media/cdrom
	wine setup.exe

---

### Post by yogakills on 2007-09-07
Mongoose,

got to this stage no probs, but when you confirm where oblivion is to be installed i get the predicted "out of disk space".

I am a little unclear what you mean by "If you see this you might want to map another drive in Wine to the partition you're installing on."

I have tried creating (in winecfg) a different drive letter and linking it to /home/folder (with all the necessary permissions) and installing to this, but no difference. still out of space.

Any ideas??

regards



[QUOTE=Mongoose;2084780]**The new Offical home of this HOWTO:**
[http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux)
The most up-to-date version will be there.   If you have a problem check the wiki before posting an issue in the fourms here.

[SIZE="5"]Oblivion under Ubuntu with Wine.[/SIZE]

6. Installing in Wine.  There is nothing to this one, you just click and go.  The only thing that might bite you is if you see the error 'out of disk space', and you know you have enough space.  If you see this you might want to map another drive in Wine to the partition you're installing on.  For example I use G: for my /opt partition.  After this Wine will see the correct disk space for /opt on the G: drive.


```
	# Use /media/cdrom or whatever your mount point is here.
	cd /media/cdrom
	wine setup.exe
```

---

### Post by Mongoose on 2007-09-07
Are you actually out of diskspace then?  Making a new drive letter makes sure Wine uses the partition's free space -- not the mountpoint's partition.  This means if you don't make a new drive letter mapping you could end up seeing Wine report root's free space for say /opt/games.    You should need about 5GB free to install Oblivion with KotN, and SI will likely require even more.  As long as you're remapping the drive and installing under that new drive in Wine it should be fine.  If it's a new Wine bug try using the suggested version in the HOWTO to install, which I believe is 0.9.38 still.

My install:
4.8G    Oblivion/

---

### Post by martinrandau on 2007-09-14
Howdy, and thanks for the howto. I have set it up according to the howto (with regedit, winecfg exactly as specifed) and everything works except from one thing: the graphics looks really weird. I have attached a screenshot.

I'm running Gutsy Gibbon 64 with a nvidia 8600GT.

---

### Post by Mongoose on 2007-09-14
What version of Wine is that?  It looks like a normal / parallax issue.

---

### Post by martinrandau on 2007-09-14
Thanks for your quick reply!

This is 0.9.43, the one found from the ubuntu wine wiki.

What's a normal/parallax issue and how do I fix it? Another version of wine?

---

### Post by Mongoose on 2007-09-16
Yeah, you can try downgrading to 0.9.38 or another version.  I don't think I've loaded up 0.9.43 or got a report on it either, so I can't speak for it.  Basically, it means graphic effects are not being applied properly ( by Wine ).  Normal and Parallax maps make textures appear to have additional depth by affecting the lighting model.  At least that's the simple version of it.  ^^

---

### Post by martinrandau on 2007-09-16
Hi!

I tried each version from 0.9.39 up to 0.9.43 with the same problem. 0.9.38 was not available for 64-bit at the moment. Version 39 and 40 wouldn't load the game after the menus. 

Here's an output from the terminal as soon as I enter the game (ie after the menus): 

```

...
fixme:d3d:state_vertexblend Vertex blending enabled, but not supported by hardware
fixme:d3d:state_vertexblend Vertex blending enabled, but not supported by hardware
fixme:d3d:state_vertexblend Vertex blending enabled, but not supported by hardware
fixme:d3d:state_vertexblend Vertex blending enabled, but not supported by hardware
fixme:d3d_shader:shader_generate_main Can't handle opcode texdp3tex in hwShader
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:d3d:IWineD3DDeviceImpl_ResourceReleased Vertex buffer released while bound to a state block, stream 0
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
```

It goes on like that all while the game is running.

I tried to look for anything with vertex or shaders in the Oblivion.ini file but couldn't find anything.

Any ideas?

---

### Post by Enverex on 2007-09-16
Fixmes aren't errors, ignore them. Athough to speed up the game, put "WINEDEBUG=-all" before the wine command which will turn the messages off.

---

### Post by martinrandau on 2007-09-16
Ok, but something is wrong with the graphics and I was thinking that it might have something to do with the fixme errors. 

Anything else I can try except from different versions of wine?

---

### Post by Mongoose on 2007-09-17
Read the wiki Known Issues.  Most of the versions of Wine you just tried aren't considered playable.  It's due to the fact some of those versions will crash changing areas or with certain effects for some setups.  Also make sure you report issues to the AppDB as described at the wiki.  Are you sure you have the correct Nvidia drivers?  I honestly can't say which version is best for 8800 right now, since I bought a PS3 instead.  Speaking of which the new IBM Cell SDK 3.0 preview is out.  ^^

---

### Post by martinrandau on 2007-09-18
Thanks for your reply. I managed to get it to work by using the lowest graphics settings, but the game looks just plain awful then (back to SNES). I will buy cedega and try that or else just wait for a fix. I got WoW meanwhile :lolflag:

---

### Post by willz06jw on 2007-09-23
OK I got it working using the wiki

my problem was that I didn't understand that the ini file was in the "My Games" folder that oblivion sets up.  Also I had to change the video directory name -- the cutscenes were crashing it after the king intro scene.  

Now I just have to figure out how to make the wine display full screen so I can see all of the buttons (and not be hidden by the Ubuntu bars at the bottom and top of my screen).

Thanks for the wiki,
Will

---

### Post by boosted_sled on 2007-10-02
> **boosted_sled said:**
> I did some more testing using a battle with about a dozen goblins who kick my a$$ after a few min.  Sometimes I get through it with 25+ fps and the gameplay is great.  Most of the time the frame rate drops to <5 in a step function and never recovers.  In either case the Oblivion .exe has one core hammered all the time.  The video mode doesn't have any effect on this.  Seems like some piece of code is slipping into a mode where it just starts hogging cycles.

This is *so* close.  The sound and gameplay are execellent when the framerate stays up.

Shoot. After all this time I finally figured this out.  One of the fan wires was jamming my video card fan.  Back to Oblivion on linux!

---

### Post by Baender on 2007-10-12
I installed Oblivion with wine 0.9.38 but the game starts very slow, the menu laggs. How it looks in game, i have not seen yet. I installed ubuntu and then wine, nothing else has been changed. Do i need any graphic driver or something other program, to get normal fps? I only installed ubuntu 7.3 nothing other has changed.

---

### Post by Jerryfan on 2007-10-12
My game has been running great. I am even using the bloom effect thatI was told would not run under wine. There are a few things i have found to make the game run better. When I save at an outside point, it seems to load a lot better the next time. Sometimes when transferring from an inside to an outside area, all my menus and such go underneath the screen. After it loads correctly the first time, it will load right up on other exits to outside areas. I have found that if the menus go under, you have to totally restart your system or every time you try to load an outside area, you will have this problem.
Anyways, to all trying to get this running under wine, I have been playing a fully modded version of oblivion for some time now.

---

### Post by Enverex on 2007-10-12
> **Baender said:**
> I installed Oblivion with wine 0.9.38 but the game starts very slow, the menu laggs. How it looks in game, i have not seen yet. I installed ubuntu and then wine, nothing else has been changed. Do i need any graphic driver or something other program, to get normal fps? I only installed ubuntu 7.3 nothing other has changed.

That's an old version of Wine.

What graphics card and drivers are you using as that will also be a massive issue...

---

### Post by Flink on 2007-10-14
Hi there!
I've just tried to install Oblivion, and it doesn't work very well. First it seems to be quite slow. I've copied my saved games from my windows partition, and there's something odd when save is loaded. With my very last saved game, I can't play at all, screen is all black, music is playing but nothing else is working. I've tried with an older save and I've been able to play about 30 seconds before a complete freeze of the game (music still playing though).

But still I can launch a new game, and it seems to be working fine (haven't tried too long).

This is from wine when game freezes :
[INDENT]err:seh:setup_exception stack overflow 4 bytes in thread 0017 eip 7d105978 esp 7b4efffc stack 0x7b4f0000-0x7b600000
err:ntdll:RtlpWaitForCriticalSection section 0x14c6bfc "?" wait timed out in thread 0010, blocked by 0017, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7e5bc860 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 0011, blocked by 0017, retrying (60 sec)[/INDENT]

I'm on a kubuntu gutsy with ubuntu wine, nvidia drivers from distro too. My config : core 2 duo 2,4 Ghz, 1 GB ram, Geforce 8600 GT 512 MB.

---

### Post by Baender on 2007-10-14
> **Enverex said:**
> That's an old version of Wine.

What graphics card and drivers are you using as that will also be a massive issue...

At first i must say, that it is very curios for me, that each tuturial looks so easy about wine. Just install ubuntu and add wine, vouila 're able to play Oblivion :confused: Now to your question, as i wrote i installed ubuntu 7.04 and installed wine 0.9.38. Thats it, no graphics driver or any additional packages. btw i 've got an ATI Radeon 9800 Pro card.
P.S. i also installed Mafia, and at first the game was so slow, the menu was laggy, ingame the same. But i activated the not supported graphicdriver support (i don't now the english description, i've got the german) ->Administration->the last one. After the activation the performance was the same on as under windows, but then oblivion does't start, it crashs in the loadingscreen, then i deactivated the driver support.
Please can you write me your proceeding in adding special packages drivers etc, i can not believe that one should only install ubuntu and wine and then oblivion works.

---

### Post by beeldings on 2007-10-18
Ubuntu 7.10
Wine 0.9.47
AMD Athlon 64 3200+
2 GB DDR 400
GeForce 7800 GS AGP

I followed the Oblivion guide over at UESPWiki. The game installed and patched without incident. However, when I run the game my framerate is rather low during combat sequences. I am currently running the game using *fbo* and I disabled the water effects using the Oblivion.ini tweak posted in the guide. I am running the game with sound/music enabled at a resolution of 1024x768 with all graphics options disabled. Other than what is listed on the Wiki entry, are there other possible tweaks that I may have overlooked that will increase my framerate?

On another note, I must say that I am pleased with what I have seen with Oblivion + Wine. I previously ran Oblivion with Cedega, but due to performance issues with Cedega (the game would intermittently freeze for about 1 to 2 seconds during and after combat) and the lack of Cedega updates in general, I decided to test Oblivion on regular Wine. If this is any indication of where the Wine project is heading, I cannot wait to see how future versions of Wine will change Linux gaming. :)

---

### Post by Mongoose on 2007-10-18
For one thing the wiki should tell you to use pbuffer, and also try the version recommended if the lastest version has problems.  Often with wine an older version might play a game better than a newer one.

---

### Post by alb@nian on 2007-10-20
With an older computer there's no chance to work ???

---

### Post by boosted_sled on 2007-10-21
0.9.47 still has the 'freezing yellow' outdoors issue for me.  Dungeons seem to work fine.

---

### Post by inversekinetix on 2007-10-25
Im a brand new linux user so bare with me,  I set ub the latest wine 0.9.47  on gutsy and the install went fine,  I went through all the instructions to set up oblivion, fine no problem.  however when i come to edit the registry theres no trace of direct3d anywhere to be seen?

any ideas?

---

### Post by bastiegast on 2007-10-25
> **inversekinetix said:**
> Im a brand new linux user so bare with me,  I set ub the latest wine 0.9.47  on gutsy and the install went fine,  I went through all the instructions to set up oblivion, fine no problem.  however when i come to edit the registry theres no trace of direct3d anywhere to be seen?

any ideas?

Yup, just make it. Right click, add new key, etc.

---

### Post by Mongoose on 2007-10-25
Read the wiki it has numbered step by step instructions.

[http://www.uesp.net/wiki/Oblivion:Linux#Registry_editing_in_Wine](http://www.uesp.net/wiki/Oblivion:Linux#Registry_editing_in_Wine)

It doesn't get easier than that.

---

### Post by inversekinetix on 2007-10-26
Thanks , i tried that last night, but no dice, when i run the program the menu comes up, but as soon as i click play game it shuts down :(    Also wine wouldnt let me uninstall oblivion, when i tried to it just reinstalled it again but at 100x speed.

any ideas?

---

### Post by Mongoose on 2007-10-26
That doesn't make sense.  Did you have the DVD mounted?  Try the suggested older version at the wiki if you have any more problems, since the latest version has bugs.

---

### Post by inversekinetix on 2007-10-26
> **Mongoose said:**
> That doesn't make sense.  Did you have the DVD mounted?  Try the suggested older version at the wiki if you have any more problems, since the latest version has bugs.


i tried mounting the iso with a nautilus?  script, it wouldnt mount anything so i burned a disk and did it from that.   i applied the patch too without problems, I'll try again when i get home.  Thanks for the fast reply.

---

### Post by Tym_The_Enchanter on 2007-10-26
I have followed the wiki and got Oblivion installed successfully. Thanks for an excellent howto :)

However I have a problem with trees rendering in a very funny way (see  [this screenshot]("http://img.photobucket.com/albums/v253/tym_the_enchanter/oblivion_trees.png")).

My setup is:

wine 0.9.38
Nvidia 8800GTS
Core2 Quad 6600
4 Gb Ram
nvidia 9755 drivers (also tried 100.14.19)

I have also tried wine 0.9.44 & 0.9.47 with the same effect and the added problem that I can only run in fbo mode due to crashes when loading exterior areas (which is already mentioned on the wiki though).

Does any one have any idea what might be the cause & how fix this please?

---

### Post by zeroxwolfx on 2007-10-26
Hi, I am a linux noob and am trying to install oblivion on wine version 9.47 however, I followed the wiki, but when the installation is nearly done, I get an error that says "Feature transfer error" "File:D:\Data7.cab" "Feature:not ready"

Please tell me this is fixable...

---

### Post by BaffledMollusc on 2007-10-26
I'm trying to run Oblivion under Wine, and when I load a saved game and try to play, I get a frame rate of about 1 frame per 30 seconds. Essentially the game freezes, and updates now and then.

I'm running Ubuntu 7.10 and Wine 9.47 (although I've also tried 9.46; same problem).

I'm using an ATI Radeon X800Pro with the latest fglrx 8.42.3 drivers. The problem exists regardless of whether I use fbo or pbuffer, and whether I set Wine to emulate Win98, XP or 2000.

It doesn't matter if I use ALSA, OSS or turn off sound completely, and regardless of whether I run it fullscreen or in a virtual desktop. The debug output of wine doesn't show anything that looks like a critical error.

If I try and start a new game rather than loading a save one, the progress bar goes right across, and then freezes permanently. Wine debug output in this case is
```

fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #536870923: "WARNING: 0:1: extension 'GL_ARB_draw_buffers' is not supported\n"
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0010), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00000000 ESP:0034eb24 EBP:0034ebc0 EFLAGS:00210242(   - 00      - RIZ1)
 EAX:00000000 EBX:71eb5080 ECX:0034eb98 EDX:00000000
 ESI:00000000 EDI:72947040
Stack dump:
0x0034eb24:  7dec2139 72947040 71eb5080 00000000
0x0034eb34:  00000000 00000000 00000000 0034eb98
0x0034eb44:  00000000 00000011 00000003 00000000
0x0034eb54:  00000000 00007010 00000000 00000000
0x0034eb64:  00000004 0000001f 73408e58 0034eb90
0x0034eb74:  7deb9af0 00000000 00000000 00000000
Backtrace:
=>1 0x00000000 (0x0034ebc0)

```

Does anyone have any ideas or suggestions?

---

### Post by NullHead on 2007-10-27
> **BaffledMollusc said:**
> I'm trying to run Oblivion under Wine, and when I load a saved game and try to play, I get a frame rate of about 1 frame per 30 seconds. Essentially the game freezes, and updates now and then.

I'm running Ubuntu 7.10 and Wine 9.47 (although I've also tried 9.46; same problem).

I'm using an ATI Radeon X800Pro with the latest fglrx 8.42.3 drivers. The problem exists regardless of whether I use fbo or pbuffer, and whether I set Wine to emulate Win98, XP or 2000.

It doesn't matter if I use ALSA, OSS or turn off sound completely, and regardless of whether I run it fullscreen or in a virtual desktop. The debug output of wine doesn't show anything that looks like a critical error.

If I try and start a new game rather than loading a save one, the progress bar goes right across, and then freezes permanently. Wine debug output in this case is
```

fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #536870923: "WARNING: 0:1: extension 'GL_ARB_draw_buffers' is not supported\n"
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0010), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00000000 ESP:0034eb24 EBP:0034ebc0 EFLAGS:00210242(   - 00      - RIZ1)
 EAX:00000000 EBX:71eb5080 ECX:0034eb98 EDX:00000000
 ESI:00000000 EDI:72947040
Stack dump:
0x0034eb24:  7dec2139 72947040 71eb5080 00000000
0x0034eb34:  00000000 00000000 00000000 0034eb98
0x0034eb44:  00000000 00000011 00000003 00000000
0x0034eb54:  00000000 00007010 00000000 00000000
0x0034eb64:  00000004 0000001f 73408e58 0034eb90
0x0034eb74:  7deb9af0 00000000 00000000 00000000
Backtrace:
=>1 0x00000000 (0x0034ebc0)

```

Does anyone have any ideas or suggestions?

Delete your Oblivion.ini file and start the game again. In my  case I've had the same problem but I foobared by Oblivion.ini I was also using the latest wine.

---

### Post by BaffledMollusc on 2007-10-27
> **NullHead said:**
> Delete your Oblivion.ini file and start the game again. In my  case I've had the same problem but I foobared by Oblivion.ini I was also using the latest wine.

Thanks for the suggestion, but I've tried that, as well as turning off practically every option I can find in the .ini file with no luck. Has anyone managed to get it running with an X800?

---

### Post by Nick Blinko on 2007-11-02
Well, I finally got the game to run under wine and it runs surprisingly well for my dinosaur rig. But I've been having a problem leaving the sewers at the beginning of the game, everytime I try to leave to go outside the game just crashes, so I can't really get much farther than the sewers.

EDIT: okay I messed around with the offscreenrender and changed it to fbo, now I can go outside but the rendering is really messed up, the hud flickers, sky blue flashes. The sky is all messed up, and it'll crash when transitioning areas. I've tried pbuffer and backbuffer too, same error.

---

### Post by drcranium on 2007-11-02
I'm trying to run Oblivion from my vista partition for various reasons.  My linux partititon is a little small and I don't want to use up precious free space.  Any ideas on how to configure Wine for this?  I can run the launcher by going though my mounted NTFS partition and running it but it doesn't seem to recognize the cd drive.  But Wine does recognize it.  Also when the auto launcher from CD it tries to install because the installation is on the NTFS partition.  It seems to me like the two are seperated and just can't commnunicate.  By the two I mean Drive and Partition.  Any ideas.  I thought I read about editing the WINE registry but I'm not familar with that.

---

### Post by Mblackwell on 2007-11-03
Did you mount everything as "drives" in winecfg?

---

### Post by drcranium on 2007-11-03
I think so.  I have my D drive leading to my mounted CD ROM drive.  I have it listed as a CD Drive also.  I am able to get other programs to work it seems.  I installed Jedi Knight II on my Windows partition and it seemed to work correctly.

---

### Post by Mongoose on 2007-11-03
Tym:
Hmm... I had an issue kind of like that, but the speedtree sprites would transform incorrectly but not deform.  I can't remember what I did to fix it to be honest either.  ^^

BaffledMollusc:
Last I checked ATi cards still don't work.  They don't support GLSL properly.

drcranium:
Are you sure it's writing to the partiion correctly?  Also you have to setup the 'My Documents / My Games' directories in Wine for 'Windows Logo' games.  They require certain directories to exist.

---

### Post by drcranium on 2007-11-03
YAY I got it to work.  I "reinstalled" it on the windows partition and WINE just seemed to add what it needed.  It took like three seconds.  Then I ran in a terminal and saw it required the dll.  So i extracted it and now Oblivion on Linux without using any hard drive space.  Thanks for putting up the tutorial Mongoose.

EDIT: Ok maybe not.  It runs but I have restart my character and when I do everything has a black tint.  I think I just have to play with the configuration some more.    Thanks again

---

### Post by Nick Blinko on 2007-11-03
Wow,

Thanks for helping me, what you suggested really fixed my problem....

---

### Post by Mblackwell on 2007-11-03
> **Nick Blinko said:**
> Wow,

Thanks for helping me, what you suggested really fixed my problem....

Was that sarcasm?

---

### Post by ZugZugTheOrc on 2007-11-04
Hey everybody!

First off, I want to explain my situation so you understand some of my limitations...
I'm in the US Navy on deployment. I do not have a high-speed download capability, and loading this webpage took 10 minutes. :) So if you decide to give me a hand please reply to me in an email (letsgetfree at rcbarnes dot com).

Now with that out of the way... 

I've decided to take that leap of faith that everyone always talks about when they decide to make the switch to Linux. I've abandoned Windows!! The only thing keeping me from switching in the first place is that games never worked well under Linux. Now I know that to be false.

My problem with Oblivion is this, I dont know jack about Linux except for some basic commands. I think I mucked up my Wine config (no idea where that is stored..LOL).. and when I tried to install Oblivion the first time I got like 10% through and it died saying an error I didnt bother to write down. Sorry. But now when I try to install it I get this error (I learned! See the attached Screenshot)

What do I need to do to fix this? I cant even install it to start tweaking anything! :(

Anyways, please give me a hand if you're able. And do reply to my email rather than here. It takes forever to load one page from these forums for me. Thanks a million!

~Zug Zug

---

### Post by Dapman01 on 2007-11-06
I have a problem with Oblivian
It installs cleanly, but after the startup menu (you know after you put in the DVD) but after I press play it acts as though I have not done anything at all.  The menu closes and nothing happens.

I have a 7800GT 2 Gigs of ram and a 4000+ so I meet the system requirement

---

### Post by Dapman01 on 2007-11-06
bump

---

### Post by Dapman01 on 2007-11-06
bump

---

### Post by zeroxwolfx on 2007-11-07
> **zeroxwolfx said:**
> Hi, I am a linux noob and am trying to install oblivion on wine version 9.47 however, I followed the wiki, but when the installation is nearly done, I get an error that says "Feature transfer error" "File:D:\Data7.cab" "Feature:not ready"

Please tell me this is fixable...

upgraded to version 0.9.48 wine... STILL can't get oblivion to work... still get glassy textures, still crashes when I go outside... help!!

---

### Post by jimminy_kriket on 2007-11-07
Sorry if you have already been recomended to try this, but have you tried using the wine version in the OP? Mongoose has said a million times that the newer versions have problems with oblivion.

---

### Post by Dapman01 on 2007-11-08
> **jimminy_kriket said:**
> Sorry if you have already been recomended to try this, but have you tried using the wine version in the OP? Mongoose has said a million times that the newer versions have problems with oblivion.

I can't find the old version of wine, can you

---

### Post by Tym_The_Enchanter on 2007-11-09
check the first post in this thread or the wiki page for links to winehq and budgetdedicated to get the oplder packages.

---

### Post by PhillipJ on 2007-11-11
I couldn't find an older version of WINE built for 7.10 but I have Oblivion running using 0.9.49. Had a problem where it would only use shader model 1 for a while, needed to uninstall wine and oblivion and re-install. Also, I haven't patched at all as it seems very stable at the moment.  I followed the instructions posted by Mongoose except used pbuffer instead of fbo.  works inside and outside, saves, quicksaves, tab all work. Actually is more stable than the unpatched version under XP. Running at 1280 x 1024 but I think that's a little much at this stage.

setup:

Athlon64 s939 3000+ @ 2.3 GHz
2x 7600GS 256MB SLI
Asus A8N-SLI board
2GB generic DDR400
Ubuntu 7.10
Wine 0.9.49

Issues:

-don't get any static in the sound but sometimes all the sliders move themselves to 0. I think this is becuase wine can't find a hardware mixer. I'm using onboard realtek sound. When sound is turned up it sounds good though. [edit] restarting X fixes the sound, I'm too much of a noob to know why.

-shader model 3 won't enable despite enabling it in Oblivion.ini. Apparently it's using shader package 2 (as opposed to 13 which everone else seems to use). Haven't tried renaming package 19 to 2 yet.

-SLI is enabled in xconfig (SFR) and the heads-up says it's working and both heat up during play but Renderinfo.txt says SLI = no

- water was purple until i installed the replacement pack as suggested.

- artifacts present when using SLIAA

- trees/grass still popping up and disappearing, trees at long distance 'shimmering.' neither problem is too bad.


[edit] some FPS results:

inside: 20-40
outside: 10-20
outside (bloom enabled): 10-20

- disabled SLI, outside FPS with bloom went up to 25-30

---

### Post by element8 on 2007-11-15
followed the walkthough, got everything running smooth except the radial menu (1-10 where you assign hotkeys for weapons/spells) is always up, and when i hit tab > click on the fist it stays up in there too, not sure how to get rid of it? i'm moving a little slowly too it seems, when i look around there's no slowdown so i think it has to do with the menu being up there problem

i read that sometimes block gets stuck on when you alt+tab away, i'm playing in a window, but i didn't alt+tab away or anything but it seems like something is stuck on that is causing these things to happen, any ideas?

---

### Post by element8 on 2007-11-15
here's a screenshot to help explain what's going on, i'm using wine version 0.9.47 i could try updating to 0.9.49 if that seems to have less problems?

[IMG]http://img406.imageshack.us/img406/4924/screenshot3kb3.png[/IMG]

---

### Post by White-Wolf52 on 2007-11-16
hey, im having a problem with oblivion, i got it installed fine, i changed the name of the oblivion logo in the video folder, i changed the stuff in the .ini, but when i press play on the launcher, the launcher closes, it waits a second and then the whole wine window closes, any help would be great

---

### Post by element8 on 2007-11-16
if it's crashing it should give you some sort of message in the terminal window you launched it from?

also i tried going up to latest wine version and going back to 0.9.29 and still getting that circle up there

---

### Post by White-Wolf52 on 2007-11-16
well, i launched it from the oblivion icon on the desktop/no window came up, wasnt using the terminal tho

---

### Post by White-Wolf52 on 2007-11-16
k, just tried opening it with the terminal, here is what came up:

wolf@wolf-desktop:~$ wine \k:\OblivionLauncher.exe 
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,0,2): stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f414,0x00000000), stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,35,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,70,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,105,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,140,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,175,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,210,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,245,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,255,2): stub!
err:module:import_dll Library d3dx9_27.dll (which is needed by L"C:\\Program Files\\Bethesda Softworks\\Oblivion\\Oblivion.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Bethesda Softworks\\Oblivion\\Oblivion.exe" failed, status c0000135

---

### Post by White-Wolf52 on 2007-11-16
> **White-Wolf52 said:**
> k, just tried opening it with the terminal, here is what came up:

wolf@wolf-desktop:~$ wine \k:\OblivionLauncher.exe 
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,0,2): stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f414,0x00000000), stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,35,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,70,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,105,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,140,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,175,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,210,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,245,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,255,2): stub!
err:module:import_dll Library d3dx9_27.dll (which is needed by L"C:\\Program Files\\Bethesda Softworks\\Oblivion\\Oblivion.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Bethesda Softworks\\Oblivion\\Oblivion.exe" failed, status c0000135

so i asume this is all telling me that i need the d3dx9_27.dll, but where do i get this from(cant get it from the net, i do beleive my bro being an *** right now and shut it off)

---

### Post by Felson on 2007-11-16
You will need to copy it from an existing winblows install. You should also be able to find a site that has it using Google. 

[http://www.dll-files.com/dllindex/dll-files.shtml?d3dx9_27]("http://www.dll-files.com/dllindex/dll-files.shtml?d3dx9_27")
Seems to have it, but downloading binary files from  random random sites may not really be the safest thing to do....

---

### Post by White-Wolf52 on 2007-11-16
well, ill check on the microsoft website first

---

### Post by White-Wolf52 on 2007-11-16
ok, so i got the d3dx9.dll file, i put in in the system32 folder, i open the launcher/press play, the launcher closes(wine window stays open) then a small window comes up with oblivion as the title, then closes and the wine window closes, i get this as the output from the terminal:
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
wine: Unhandled page fault on read access to 0x00000000 at address 0x498749 (thread 0010), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00498749).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00498749 ESP:0034f448 EBP:01a4b814 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:01a4b3a4 ECX:01a4b810 EDX:12002f01
 ESI:00000000 EDI:01a4b5a4
Stack dump:
0x0034f448:  00000001 00000016 00080000 00000003
0x0034f458:  00000071 4db3b599 0034f9b1 00020024
0x0034f468:  00000000 00400000 0034f488 01a4ba98
0x0034f478:  0005795c 00002710 00000013 00000001
0x0034f488:  000000c8 7e9dd160 00000001 00000000
0x0034f498:  0034f4c8 7b891c3e 000000c8 00000003
Backtrace:
=>1 0x00498749 in oblivion (+0x98749) (0x01a4b814)
  2 0x00000000 (0x00000001)
  3 0x00000000 (0x00000000)
0x00498749: movl        0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (93 modules)
PE        400000-  baf000       Export          oblivion
PE        bb0000-  dff000       Deferred        d3dx9_27
PE      18000000-18068000       Deferred        binkw32
ELF     7b800000-7b92a000       Deferred        kernel32<elf>
  \-PE  7b820000-7b92a000       \               kernel32
ELF     7bc00000-7bca2000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca2000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf1c000-7c000000       Deferred        wined3d<elf>
  \-PE  7bf30000-7c000000       \               wined3d
ELF     7c1ee000-7c21d000       Deferred        d3d9<elf>
  \-PE  7c200000-7c21d000       \               d3d9
ELF     7c5d0000-7c5e5000       Deferred        midimap<elf>
  \-PE  7c5e0000-7c5e5000       \               midimap
ELF     7c5e5000-7c6ab000       Deferred        libasound.so.2
ELF     7cc0d000-7cc34000       Deferred        msacm32<elf>
  \-PE  7cc20000-7cc34000       \               msacm32
ELF     7cc34000-7cc4c000       Deferred        msacm32<elf>
  \-PE  7cc40000-7cc4c000       \               msacm32
ELF     7cc4c000-7cc82000       Deferred        winealsa<elf>
  \-PE  7cc60000-7cc82000       \               winealsa
ELF     7cc82000-7ccb4000       Deferred        uxtheme<elf>
  \-PE  7cc90000-7ccb4000       \               uxtheme
ELF     7ccb4000-7ccbd000       Deferred        libxcursor.so.1
ELF     7ccbd000-7ccda000       Deferred        imm32<elf>
  \-PE  7ccc0000-7ccda000       \               imm32
ELF     7ccda000-7ccdf000       Deferred        libxfixes.so.3
ELF     7ccdf000-7cce2000       Deferred        libxcomposite.so.1
ELF     7cce2000-7cce8000       Deferred        libxrandr.so.2
ELF     7cce8000-7ccf0000       Deferred        libxrender.so.1
ELF     7d9ea000-7e382000       Deferred        libglcore.so.1
ELF     7e382000-7e418000       Deferred        libgl.so.1
ELF     7e418000-7e41d000       Deferred        libxdmcp.so.6
ELF     7e41d000-7e50e000       Deferred        libx11.so.6
ELF     7e50e000-7e51c000       Deferred        libxext.so.6
ELF     7e51c000-7e521000       Deferred        libxxf86vm.so.1
ELF     7e521000-7e539000       Deferred        libice.so.6
ELF     7e539000-7e541000       Deferred        libsm.so.6
ELF     7e54d000-7e5da000       Deferred        winex11<elf>
  \-PE  7e560000-7e5da000       \               winex11
ELF     7e63a000-7e65a000       Deferred        libexpat.so.1
ELF     7e65a000-7e685000       Deferred        libfontconfig.so.1
ELF     7e686000-7e688000       Deferred        libnvidia-tls.so.1
ELF     7e691000-7e6a6000       Deferred        libz.so.1
ELF     7e6a6000-7e716000       Deferred        libfreetype.so.6
ELF     7e716000-7e743000       Deferred        ws2_32<elf>
  \-PE  7e720000-7e743000       \               ws2_32
ELF     7e743000-7e75d000       Deferred        wsock32<elf>
  \-PE  7e750000-7e75d000       \               wsock32
ELF     7e75d000-7e7c5000       Deferred        msvcrt<elf>
  \-PE  7e770000-7e7c5000       \               msvcrt
ELF     7e7c5000-7e7d9000       Deferred        lz32<elf>
  \-PE  7e7d0000-7e7d9000       \               lz32
ELF     7e7d9000-7e7f3000       Deferred        version<elf>
  \-PE  7e7e0000-7e7f3000       \               version
ELF     7e7f3000-7e84c000       Deferred        shlwapi<elf>
  \-PE  7e800000-7e84c000       \               shlwapi
ELF     7e84c000-7e94f000       Deferred        shell32<elf>
  \-PE  7e860000-7e94f000       \               shell32
ELF     7e94f000-7e999000       Deferred        dsound<elf>
  \-PE  7e960000-7e999000       \               dsound
ELF     7e999000-7ea27000       Deferred        winmm<elf>
  \-PE  7e9b0000-7ea27000       \               winmm
ELF     7ea27000-7ea3a000       Deferred        libresolv.so.2
ELF     7ea3a000-7ea58000       Deferred        iphlpapi<elf>
  \-PE  7ea40000-7ea58000       \               iphlpapi
ELF     7ea58000-7eab2000       Deferred        rpcrt4<elf>
  \-PE  7ea60000-7eab2000       \               rpcrt4
ELF     7eab2000-7eb54000       Deferred        ole32<elf>
  \-PE  7eac0000-7eb54000       \               ole32
ELF     7eb54000-7eb8a000       Deferred        dinput<elf>
  \-PE  7eb60000-7eb8a000       \               dinput
ELF     7eb8a000-7eba3000       Deferred        dinput8<elf>
  \-PE  7eb90000-7eba3000       \               dinput8
ELF     7eba3000-7ebef000       Deferred        advapi32<elf>
  \-PE  7ebb0000-7ebef000       \               advapi32
ELF     7ebef000-7ec87000       Deferred        gdi32<elf>
  \-PE  7ec00000-7ec87000       \               gdi32
ELF     7ec87000-7edc4000       Deferred        user32<elf>
  \-PE  7eca0000-7edc4000       \               user32
ELF     7edc4000-7ee83000       Deferred        comctl32<elf>
  \-PE  7edd0000-7ee83000       \               comctl32
ELF     7ee83000-7ee9b000       Deferred        libnsl.so.1
ELF     7ee9b000-7eea4000       Deferred        libnss_compat.so.2
ELF     7eea4000-7eea7000       Deferred        libxau.so.6
ELF     7efcf000-7eff4000       Deferred        libm.so.6
ELF     7eff5000-7f000000       Deferred        libnss_files.so.2
ELF     b7c70000-b7c7a000       Deferred        libnss_nis.so.2
ELF     b7c80000-b7c84000       Deferred        libdl.so.2
ELF     b7c84000-b7dce000       Deferred        libc.so.6
ELF     b7dcf000-b7de7000       Deferred        libpthread.so.0
ELF     b7df3000-b7f07000       Deferred        libwine.so.1
ELF     b7f09000-b7f25000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000f (D) C:\Program Files\Bethesda Softworks\Oblivion\Oblivion.exe
        00000013   15
        00000012   15
        00000011    0
        00000010    0 <==
0000000b 
        0000000e    0
        0000000c    0
fixme:winmm:MMDRV_Exit Closing while ll-driver open

---

### Post by White-Wolf52 on 2007-11-16
nvm, im good so far, game starts, found a reference to my problem on the bugzilla site, some bug for :   thief: shadow, or something along those lines, currently waiting for oblivion to load :D, although, is it normal for it to take over 5 min?

---

### Post by Scotty562 on 2007-11-17
You guys are great. Oblivion works great for me using .49 :). I shouldn't say great... my poor geforce go 8400 gs can't really handle it that well haha.

---

### Post by Miru on 2007-11-24
Everything is working except for three problems.

1) when it's doing its intro thing, assuring me betheseda made this, pressing esc won't skip it.
2) when I go into the video settings menu it will alternate running and freezing for a second.
3) the edges look choppy. 
[IMG]http://i71.photobucket.com/albums/i149/MiruX/Aliasing.jpg[/IMG]
EDIT:
also trying to install shivering isles yields
A required security module cannot be activated.
This program cannot be executed (7000).

Please have a look at [http://www.securom.com/message.asp?m=module&c=7000](http://www.securom.com/message.asp?m=module&c=7000) for further, more detailed information.

---

### Post by sirdilznik on 2007-11-24
> **Cappy said:**
> Is wine still lacking the Pixel Shader 2.0 support? I always thought Cedega was built on wine with an "easy to use" interface.

I could be wrong, but I think the newer versions of wine support pixel shader 2.0 and GLSL.  Cedega is a fork of wine (it was originally called winex) with proprietary code added in.  Although I'm sure there is some sharing of information among the projects, they really are 2 separate projects on separate paths.

---

### Post by sirdilznik on 2007-11-24
> **Miru said:**
> 

1) when it's doing its intro thing, assuring me betheseda made this, pressing esc won't skip it.
You can have the game skip the intro sequence and get you to the start screen a whole lot faster by making a simple edit in your Oblivion.ini file (located in the My Games folder by default).  Find this line:
```
SIntroSequence=bethesda softworks HD720p.bik,2k games.bik,game studios.bik,Oblivion Legal.bik
``` and change it to:
```

SIntroSequence=
```

---

### Post by KhaaL on 2007-12-05
Just wanted to add: those who suffer from having a black window while the GUI is still visible, the solution lies here: [http://www.bethsoft.com/bgsforums/index.php?act=ST&f=23&t=517690&st=0](http://www.bethsoft.com/bgsforums/index.php?act=ST&f=23&t=517690&st=0)

If that dosen't work, or you can't be arsed to do it, simply turn off HDR

EDIT: That link worked for me in indoor areas, where outdoor areas became black. I switched to bloom and outdoors now work. The problem happened to me while using fbo and pbuffer, and the solution was only tested with fbo.

---

### Post by rax_m on 2007-12-09
Hi there.. 

I want to run Oblivion under wine, and was wondering whether it was possible to use the already installed instance on the Windows partition? 

If not, would it be possible to (re-)install Oblivion onto the Windows partition from Wine. I have tried this, but I get an error saying there is not enough disk space (I have 11GB free). 

Thanks for the help
Cheers
Rax

---

### Post by KhaaL on 2007-12-09
I tried running a wine install of oblivion from windows and it did work. But it did get very haywire - however I think it's because of the problem I mentioned in my previous post (shader package).

---

### Post by rax_m on 2007-12-09
Hi Khaal, 

Thx for the reply.. how did you get it working ? 

When I run the OblivionLauncher.exe from the windows partition, I get the launcher but the options to "Play" is greyed out.. 

Rax

---

### Post by KhaaL on 2007-12-09
Oh, i installed it in wine (which went fine) and then I could run the wine install version from windows. Though i had a no-cd patch applied too.


...Now that i think of it, i also had a previous install of oblivion on that partition, so that *might* affect why it worked for me.

---

### Post by rax_m on 2007-12-10
ok.. thanks. 
Unfortunately I don't have enough space on any of the linux partitions to install it properly.. dang!

---

### Post by shaft350x on 2007-12-17
Perhaps someone can help me with this.

1. Magic effects such as detect life, don't show up, nor do fire effects from fire spells with a longer duration (weak fireball)

2. Hitting CAPS LOCK to turn on always run, does not work.

I followed the guide at the beginning of this thread, and I am using the latest version of WINE (9.50 I think)

---

### Post by jmoskow on 2007-12-31
I am trying to install Oblivion under wine following the info from the beginning of this thread.  But i keep getting the error below.  Googled and really did not find too much info.  Anyone encounter this problem?


A required security module cannot be activated.
This program cannot be executed (7000).

Please have a look at [http://www.securom.com/message.asp?m=module&c=7000](http://www.securom.com/message.asp?m=module&c=7000) for further, more detailed information.

I am running Gutsy with the newest version of Wine.  Maybe I should use an older version as per the wiki.  Has anyone successfully used the new version of Wine to run Oblivion?  Video card is Nidia 7950GT.
Any thoughts would be appreciated.
John

---

### Post by Mongoose on 2007-12-31
Is this a GotY disc?  The guide only covers the first pressing of Oblivion and the separate content paks.  The Shivering Isles required a round the 'bout install method due to similar issues. Securom is horrible for Linux gaming.  Read the Wiki guide and use the unpack install method suggested for SI as a basis.

---

### Post by daarmys1st on 2008-01-04
Man you not the only one its not working very well for me nether. I got the same error. And yes I'm using a gotY disk.  :mad:

---

### Post by beerfan on 2008-01-13
I have joined your ranks. I was dual-booting to play Oblivion but I finally got it installed and running on Ubuntu with a few tweaks. The wiki guide is great.

I just wanted to note my hardware and quirks for others. I have a Core2 Duo e6700 with 2GB of Ram and Nvidia 8800GT with 512MB of Ram. The game runs beautifully at 1650x1080 in Winxp with all settings maxed. I never checked what fps I was getting but I'd guess that it was well over 50fps.

In Ubuntu I'm running Wine 0.9.52 (just released yesterday) and the proprietary Nvidia driver 169.04. I am not running the newer 169.07 because it has a bug that causes the fan to run full blast all the time. I have turned on 2x anti-aliasing in the nvidia driver settings since Oblivion doesn't allow turning on AA in the game for some reason.

I have water shading, Bloom, and HDR turned off and I'm not using a virtual wine screen but just playing the game full screen at 1650x1080. The game is rather slow at around 10-30fps outside. I've turned off grass completely, tried lower resolutions, tweaking distance settings, etc. but nothing seems to make any difference. I'm guessing that it's the fault of this first run nvidia driver. Hopefully the next version will improve performance a lot because it's rather painful to play at this framerate after being used to playing it much smoother.

Everything else works great except for the loss of water detail which is a bummer. Oh well, hopefully this is useful for someone.

---

### Post by niethslim on 2008-01-16
Does the tutorial work with WINE 0.9.46 ?

---

### Post by KhaaL on 2008-01-16
> **niethslim said:**
> Does the tutorial work with WINE 0.9.46 ?

short answer: yes

---

### Post by niethslim on 2008-01-16
OK, I have a problem.
> 5. Registry editing in Wine. Run the command below and it'll pop-up a Wine version of regedit.

Code:

wine regedit.exe

Now browse HKEY_CURRENT_USER / Software / Wine / Direct3D. Right click in the pane to make New > String Value for each of the following key pairs:

Code:

OffscreenRenderingMode	fbo
	UseGLSL					enabled
	VideoMemorySize		256

Make sure you have 256MB of video memory and GLSL support before enabling. Set whatever is needed for your card, but note w/o GLSL Oblivion won't run. I use a Nvidia 6800 GS with 256MB of RAM, and it gets it done.


I don't have a Direct3D  directory where the tutorial specifies it should exist.
I created one, is this the right thing to do?

EDIT: Never mind, I found the answer in the WIKI.

---

### Post by carltonh on 2008-01-27
Just a note, I noticed an obvious performance boost with 0.9.54 vs. 0.9.53 and previous versions.  I'm using Nvidia 169.09 driver, and I'm also using Zenwalk 5.0, but I think you'll notice the same for Ubuntu.  HDR still does not work.  (Did it work with 0.9.38?)  Water textures look good, I'm not getting any crashes, etc.

I would like to get multiple people to try and if agreed, then we can consider updating the UESP wiki to say 0.9.38 is an old stable and 0.9.54 is a new recommended stable wine version for playing Oblivion.

Anyone else getting better performance on Linux than Windows?  This might be partly due to the really low footprint of XFCE that I'm using, but maybe GNOME and KDE would be the same.

---

### Post by darklegion on 2008-01-29
> **carltonh said:**
> Anyone else getting better performance on Linux than Windows?  This might be partly due to the really low footprint of XFCE that I'm using, but maybe GNOME and KDE would be the same.

Nope, no difference between wine-0.9.54 and 0.9.53 and earlier.Certainly not better than windows.

What hardware and settings are you using?
I'm using the following:
Intel E2160@2.8ghz
Nvidia 7900GS 256mb@550/823
2gb DDR800 ram

Oblivion settings:
Resolution : 1280x960
Texture Size : Medium
Lighting : Bloom=on, HDR=off
View Distance : Maximum
Distant Land : On
Anti-Aliasing : Off

Wine settings:
0.9.54
OffscreenRenderingMode : fbo

Operating system:
Gentoo AMD64

Window manager:
Ratpoison (I doubt that this makes any difference unless the gui is doing a lot of background tasks, or you are using less than 1gb of ram and so need to conserve it.)


I get 10-20fps in most outdoor areas (not even in a battle).In windows I get around 40-60 fps.

EDIT: While ingame hit the tilde key "~" and type "tdt" to check FPS.

---

### Post by carltonh on 2008-01-29
> Wine settings:0.9.54
OffscreenRenderingMode : fbo

Darklegion,

The directions you followed that say to use "fbo" are out of date and no longer apply to ~ 0.9.52 - 0.9.54.  Change "fbo" to "pbuffer" and you will notice a big performance improvement as well as stability under 0.9.54.  I'm also using an Nvidia 7 series (7600 GT 256MB) and so yours should work similarly.

I will try to check my FPS, and assuming I still have Oblivion installed on Windows, I'll do a comparison.
[B]
EDIT EDIT EDIT[/B]: Ok, I made a big dumb mistake.  I thought I had the OffScreenRenderingMode still set to Pbuffer, but an some point it got switched to" fbo" and I'm not sure when.  So trying pbuffer and backbuffer with 0.9.54, I am still getting lock up crashes. :(

I apologize for the mix up.

---

### Post by beerfan on 2008-01-30
> **carltonh said:**
> Darklegion,

The directions you followed that say to use "fbo" are out of date and no longer apply to ~ 0.9.52 - 0.9.54.  Change "fbo" to "pbuffer" and you will notice a big performance improvement as well as stability under 0.9.54.  I'm also using an Nvidia 7 series (7600 GT 256MB) and so yours should work similarly.

I will try to check my FPS, and assuming I still have Oblivion installed on Windows, I'll do a comparison.

The off-screen rendering mode certainly does make a difference for me. Using pbuffer mode causes Oblivion to hang predictably when moving into another area. This may be a driver issue though. I didn't notice any framerate increase when using pbuffer either when I just tested it again.

Core2 Duo e6750
nvidia 8800GT 512MB
Wine 0.9.54
nvidia driver 169.09

I see 15-20fps outside with water shading turned on and 20-25fps with it turned off. However, I also see "borders" in the water (for lack of a better name) with water shading turned on. It's like a wide border in between one "area" and the next moving in the direction of the water current. That's another reason I just leave it off.

25fps is bearable but it's not even close to what I was seeing in windows. I haven't noticed any difference at all between 0.9.52-54 (which is all I have experience with). I don't think there was even a perceptible difference in performance between the 169.04 and 169.09 nvidia drivers which was disappointing to say the least.

---

### Post by darklegion on 2008-01-30
> **carltonh said:**
> Darklegion,

The directions you followed that say to use "fbo" are out of date and no longer apply to ~ 0.9.52 - 0.9.54.  Change "fbo" to "pbuffer" and you will notice a big performance improvement as well as stability under 0.9.54.  I'm also using an Nvidia 7 series (7600 GT 256MB) and so yours should work similarly.
.

I tried pbuffer as well and there was no noticable performance increase and the game crashed after a short period.

[QUOTE=beerfan]
I don't think there was even a perceptible difference in performance between the 169.04 and 169.09 nvidia drivers which was disappointing to say the least.
[/QUOTE]

169.09 is virtually the same driver with a few minor bugfixes, so it's no suprise that there's no performance increase.

---

### Post by ericstoesser on 2008-01-30
..omg,.... i can't even get it installed. i try running setup.exe under wine and i get a security error. wtf
im getting 
A required security module cannot be activated.
This program cannot be executed (7000).

Please have a look at [http://www.securom.com/message.asp?m=module&c=7000](http://www.securom.com/message.asp?m=module&c=7000) for further, more detailed information.
WTF IM CONFUSED AS HELL!! HELP PLEASE!!!:confused::(
btw..... im running the latest wine.... and i read this thread for 45 minutes, and got nothing! PLEASE HELP!!!
dell inspiron 1521, AMD athlon x2, 1 gbram,

---

### Post by beerfan on 2008-01-30
> **ericstoesser said:**
> ..omg,.... i can't even get it installed. i try running setup.exe under wine and i get a security error. wtf
im getting 
A required security module cannot be activated.
This program cannot be executed (7000).

Please have a look at [http://www.securom.com/message.asp?m=module&c=7000](http://www.securom.com/message.asp?m=module&c=7000) for further, more detailed information.
WTF IM CONFUSED AS HELL!! HELP PLEASE!!!:confused::(
btw..... im running the latest wine.... and i read this thread for 45 minutes, and got nothing! PLEASE HELP!!!
dell inspiron 1521, AMD athlon x2, 1 gbram,

Let me guess...you have the Game of the Year edition?

Did you read the wiki page? It explains this.

[http://www.uesp.net/wiki/Oblivion:Linux#Oblivion_Game_of_the_Year_Edition](http://www.uesp.net/wiki/Oblivion:Linux#Oblivion_Game_of_the_Year_Edition)

---

### Post by beerfan on 2008-01-30
> **darklegion said:**
> 169.09 is virtually the same driver with a few minor bugfixes, so it's no suprise that there's no performance increase.

I believe I read in another thread that 169.07 showed improvements in 3D over the .04 driver but due to the permanent fan bug I wasn't using it so I couldn't really say. However, I wouldn't say that I am *surprised* that more improvements weren't made but that doesn't mean I can't be disappointed. :-)

---

### Post by ericstoesser on 2008-01-31
> **beerfan said:**
> Let me guess...you have the Game of the Year edition?

Did you read the wiki page? It explains this.

[http://www.uesp.net/wiki/Oblivion:Linux#Oblivion_Game_of_the_Year_Edition](http://www.uesp.net/wiki/Oblivion:Linux#Oblivion_Game_of_the_Year_Edition)
how do i create a HKEY_LOCAL_MACHINE\System\MountedDevices in regedit? I don't know how to do this. whats the command? idk.. i have the latest wine btw...:confused:

---

### Post by KhaaL on 2008-01-31
type "regedit" in the console, and then you can go to HKEY... by the navigation menu on the left.

---

### Post by ericstoesser on 2008-01-31
the instructions tel me to download an old wine version, for another os... feisty. im on gutsy... I have game of the year edition... I got wine installed, the latest one btw... I edited my registry to the direction's specifications.......sighs....

---

### Post by ericstoesser on 2008-01-31
I also get a .wine is not owned by you when i try to run setup under wine....

---

### Post by Sugi on 2008-02-01
I just installed Oblivion restarted.  It ran pretty good without any real tinkes, but I do get some crashes once in a while.  Thanks :)


Side question, how do you get those FPS readout in the screen shot?  Does anyone know how to do this?

---

### Post by beerfan on 2008-02-01
> **ericstoesser said:**
> the instructions tel me to download an old wine version, for another os... feisty. im on gutsy... I have game of the year edition... I got wine installed, the latest one btw... I edited my registry to the direction's specifications.......sighs....

According to [http://www.uesp.net/wiki/Oblivion:Linux#Oblivion_Game_of_the_Year_Edition](http://www.uesp.net/wiki/Oblivion:Linux#Oblivion_Game_of_the_Year_Edition) you need to run the oblivion installer with wine in windows vista mode and by adding the mountdevices registry key. You did that? If so then I have no other suggestions.

I have the original release and it installs flawlessly. It's unfortunate that their special edition includes copy protection.

[quote=ericstoesser]I also get a .wine is not owned by you when i try to run setup under wine....[/quote]

This sounds like you configured Wine as root. Open a terminal and type "ls -ld .wine" and if it says "root root" instead of your username then that's the problem. You could change the ownership with "sudo chown -R [username] .wine" but I don't know if that is a good idea not having tried it. You could also just delete ~/.wine and start over from scratch. Take these suggestions with a big grain of salt since I don't know what your situation is or what effect these commands will have for you.

---

### Post by beerfan on 2008-02-01
> **Sugi said:**
> I just installed Oblivion restarted.  It ran pretty good without any real tinkes, but I do get some crashes once in a while.  Thanks :)


Side question, how do you get those FPS readout in the screen shot?  Does anyone know how to do this?

Open the console with the ~ key and type "tdt" and hit enter.

[http://www.uesp.net/wiki/Oblivion:Console](http://www.uesp.net/wiki/Oblivion:Console)

---

### Post by sheen on 2008-02-03
Thanks a lot for all these tips, It works fine, just one problem :
I got lag then fast freeze into display option only (other options panels works), so I can't change display settings.

Any advices are welcome, thanks.

---

### Post by Bethesda on 2008-02-06
Heya all =)

So I got Oblivion working after carefully reading all of your suggestions and guides - I'm a newbie on Ubuntu so bear with me please.

So, I play around 15 FPS , inside and outside 25-30.

Doesn't really matter if I'm in battle stangly enough.
It's not like I can't play it, it's more like me asking things I could do to increase my FPS without upgrading my PC; of which I will post the major parts down here.
( I made those .ini changes according to the guide by the way, also in Wine Virtualbox or not, around the same FPS )

Intel Core 2 Duo 2x2400
Nvidea 8600 GT
2GB DDR3 1066
Around 100GB HDD space left

Erm, that's about what you guys need to know I think.

One last thing, when I tab into menu , or face-conversation and get out of it I have around 50-60 FPS for about 5 seconds ( this FPS seems really good and playable ) and then it shifts down again to 15... : /

Water looks good, NPS OK, Models OK. 

Hope to get some nice information =)

Bethesda

---

### Post by KhaaL on 2008-02-06
> **Bethesda said:**
> Heya all =)

So I got Oblivion working after carefully reading all of your suggestions and guides - I'm a newbie on Ubuntu so bear with me please.

So, I play around 15 FPS , inside and outside 25-30.

Doesn't really matter if I'm in battle stangly enough.
It's not like I can't play it, it's more like me asking things I could do to increase my FPS without upgrading my PC; of which I will post the major parts down here.
( I made those .ini changes according to the guide by the way, also in Wine Virtualbox or not, around the same FPS )

Intel Core 2 Duo 2x2400
Nvidea 8600 GT
2GB DDR3 1066
Around 100GB HDD space left

Erm, that's about what you guys need to know I think.

One last thing, when I tab into menu , or face-conversation and get out of it I have around 50-60 FPS for about 5 seconds ( this FPS seems really good and playable ) and then it shifts down again to 15... : /

Water looks good, NPS OK, Models OK. 

Hope to get some nice information =)

Bethesda


Intresting login name ;)

The best way to get performance increase was by skipping bloom and shader effects alltoghether. I compensated with using higher-res textures (look for replacements at tessource) - granted the graphic isn't the same but i rather have smoother graphics than pretty and sluggish.

I _think_ the performance issues are because of wine isn't optimized enough.

---

### Post by person_99 on 2008-02-06
> 
Heya all =)

So I got Oblivion working after carefully reading all of your suggestions and guides - I'm a newbie on Ubuntu so bear with me please.

So, I play around 15 FPS , inside and outside 25-30.

Doesn't really matter if I'm in battle stangly enough.
It's not like I can't play it, it's more like me asking things I could do to increase my FPS without upgrading my PC; of which I will post the major parts down here.
( I made those .ini changes according to the guide by the way, also in Wine Virtualbox or not, around the same FPS )

Intel Core 2 Duo 2x2400
Nvidea 8600 GT
2GB DDR3 1066
Around 100GB HDD space left

Erm, that's about what you guys need to know I think.

One last thing, when I tab into menu , or face-conversation and get out of it I have around 50-60 FPS for about 5 seconds ( this FPS seems really good and playable ) and then it shifts down again to 15... : /

Water looks good, NPS OK, Models OK.

Hope to get some nice information =)

Bethesda

That is very odd. Here are my current specs:
AMD Athlon x64 2800+ ~1.8ghz
Nvidia Geforce 6200
1gb ram DDR 400

I get arounda constant 25-40 fps on High, 1024 x 768 with bloom.
That is nearly double what I get in Windows.

Try making sure you are in XP or Vista compatibility mode.

I had it in 2000 compatibility mode for a while and I had similar problems come to think of it.
You also might try turning off bloom or even just running in OpenGL.

---

### Post by Bethesda on 2008-02-06
You will have to excuse me, but where is this pixel shader thing to turn off?

Bethesda

Let me edit this: If I grey out the 'Pixel Shader' box in Wine the game does not run, so I don't think that is am option for me.

And with the hardware I posted on the previous page I should be able to not have 15 FPS right? May it be under Wine ofcourse...

---

### Post by Melhisedek on 2008-02-07
What kind of fps are you guys getting in Oblivion?
I'm interested in higher resolutions 1680x1050 mostly as that is native for my monitor

---

### Post by BatPenguin on 2008-02-12
The game runs pretty OK for me now, I'm playing the Shivering Isles and getting about 15-20 FPS outside and more indoors with 1360x768. I'd like to run it with Compiz-fusion enabled, though, but when I start it like that, the screen doesn't go fullscreen (I can see my bottom panel and the window titlebar, can't move window) and the colors are black & white for some reason. 

My machine's pretty nice (Nvidia 7950GT, Quad Core, 3 gigs RAM)., so I'd imagine it should be able to take it, and I wouldn't mind losing a few FPS just be able to use Compiz-fusion.

Anybody running it under Gutsy, latest Wine and COmpiz-fusion enabled?

---

### Post by LeXrius on 2008-02-17
Does anyone know why this game locks up? when im out side i play for about 30 seconds then it just freezes, but if im in a building its extremely stable.

any idea's?

---

### Post by pandayanyan on 2008-02-17
So I have to start out saying thank you mongoose for helping me out here. That walkthough you made really made that painless. I have no programming experience and am only on my second day using Linux and I figured it out from your simple explanations. Thanks for supporting the newbs..:guitar:.... ha:lolflag: ha ANYWAY

now to my problem. I fallowed the documentation exactly and when i load the game through wine it shows the splash screen then just crashes.:mad: No errors or anything it just closes and wine shuts down. I can do that as many times as I want but I can click on anything or actually boot the game. I have tried it from the cd the windows emulated desktop(wine) and even through a shortcut on my ubuntu desktop. 
What do I do? I realize I am new to this but I cant even find mention of any one else having my problem. CAn anyone help?:confused:

OBLIVION is my favorite game. I LOVE LINUX..(even if i am a newb).. CAN MY TWO PASSIONS UNITE? ha ha... 


edit:
I am running wine version 0.9.46
Amd athalon x2 
nvidia geforce 7300 LE
1.5gb ram

---

### Post by sveden on 2008-02-17
Fairly sure I installed according to this Howto but I can't get Oblivion to start. I can get the first screen to load but when I click play it crashes.

How would I check the error log to see where my hangup is?

---

### Post by beerfan on 2008-02-18
> **LeXrius said:**
> Does anyone know why this game locks up? when im out side i play for about 30 seconds then it just freezes, but if im in a building its extremely stable.

any idea's?

This sounds like the rendering mode issue which I had. Does it lock up only when you're moving? If so then follow the instructions here to change your rendering mode to fbo. That resolved it for me.

[http://www.uesp.net/wiki/Oblivion:Linux#OffscreenRenderingMode](http://www.uesp.net/wiki/Oblivion:Linux#OffscreenRenderingMode)

---

### Post by carltonh on 2008-02-18
Just a note about upgrading video cards under Linux.  I had a 256MM 7600GT and upgraded to a 512 MB 8600GT.  Although it made a noticeable improvement in WinXP performance, in Linux it made very little improvement in Oblivion with the 169.09 driver in wine 0.9.55.  Note that I did remember to alter regedit to properly reflect 512 MB memory.

---

### Post by pandayanyan on 2008-02-18
> **sveden said:**
> Fairly sure I installed according to this Howto but I can't get Oblivion to start. I can get the first screen to load but when I click play it crashes.

How would I check the error log to see where my hangup is?

i am having the same problem (see above post) can anyone help us?

---

### Post by Mongoose on 2008-02-23
If it crashes going right into game it's likely that you didn't disable the 'logo' movie before the intro movie.  For some reason it often causes a crash.  Just comment that movie out of the list in the INI.  The wiki should mention this, but I haven't been updating the wiki for some time now.  =)

---

### Post by bastiegast on 2008-02-23
It's been a while since I checked out Oblivion in wine. There used to be a bug that caused grass and bushes to randomly appear and disappear. I can't find the bug in appdb anymore but it seems still apparent in the game when I test it. 

Is the bug fixed yet?

---

### Post by darklegion on 2008-02-23
> **bastiegast said:**
> It's been a while since I checked out Oblivion in wine. There used to be a bug that caused grass and bushes to randomly appear and disappear. I can't find the bug in appdb anymore but it seems still apparent in the game when I test it. 

Is the bug fixed yet?

The bug stopped occurring for me around the time I upgraded to an 8800gt from a 7900gs and I'm pretty sure that the card change was what fixed it and not an upgrade to wine.In fact I just tested it and the issue doesn't occur with 0.9.53 or 0.9.56.There is a bug for the game "The Witcher" which has rendering errors when used with 6xxx and 7xxx nvidia cards that don't occur when using 8xxx series cards.This seems to occur because wine uses up some of the shader pipelines for the directx to opengl conversion which results in not enough shaders being left over to render everything correctly.I'm thinking that this is what causes the trees pop in and out with Oblivion.Look here for the bug report: [http://bugs.winehq.org/show_bug.cgi?id=11285](http://bugs.winehq.org/show_bug.cgi?id=11285)

---

### Post by bastiegast on 2008-02-24
Ok thanks for the info!
That sounds very logical to me because the first time I experienced this bug was in wine 0.9.33 if I remember correctly. That release improved directx support and a lot of shaders started working in Oblivion.

---

### Post by jpittack on 2008-02-26
> john@Turion:/media/cdrom$ ls
john@Turion:/media/cdrom$ wine setup.exe
wine: could not load L"c:\\windows\\system32\\setup.exe": Module not found


Should be the right mount point.  Did I miss something?

Background: Hardy using 9.54 Gutsy debs because 9.55 is blah.  Game of the Year Edition.  Proper fixes for this seems to have been taken. HKEY_LOCAL_MACHINE\System\MountedDevices already existed.

---

### Post by foosed on 2008-02-28
Where does the .dll file go after i extract it with cabextract?

EDIT: Figured this out with the --help in cabextract, still not able to run oblivion though. launcher opens but then says it cant find the disk.

EDIT: Got Oblivion up and running, fairly well, under wine 9.55. A few little bugs but nothing that makes it unplayable, if you try to click through the intro sequence all hell breaks loose, and sometimes a random buzzing in the audio, but it's easy to ignore and it goes away after a while. Thanks to OP for a great how-to.

---

### Post by carltonh on 2008-02-28
Good news.  0.9.56 has stubs for the d3dx9_27.dll.  So before I upgraded from 0.9.56, I removed that Windows DLL file from Wine's System32 directory.  I upgraded and ran Oblivion, and so far, and although with the performance limited by fbo, Oblivion runs fine.

This means that Oblivion can be now finally be run with no code that requires a Microsoft license.  Now if they can just get pbuffer to work again soon, and before they declare a 1.0 release, I'll be very happy.

---

### Post by Strike&gt;&gt; on 2008-02-29
jpittack I couldn't get my plugins and mods to work. got almost the same error. I fixed it by putting the .exe files(your plugins) inside the data folder in your oblivion folder. I guess default is:
home/yourusername/.wine/drive_c/Program Files/Bethesda Softworks/oblivion/Data
Just drag the mods there and right click on them and choose open with wine emulator. 

BTW does anyone else getting bad FPS inside the buildings, like inside Battlehorn? My fps outside is around 40 but drops dramatically when i face enemies, or go inside buildings, to around <10 fps.

---

### Post by darklegion on 2008-03-03
> **carltonh said:**
> Good news.  0.9.56 has stubs for the d3dx9_27.dll.  So before I upgraded from 0.9.56, I removed that Windows DLL file from Wine's System32 directory.  I upgraded and ran Oblivion, and so far, and although with the performance limited by fbo, Oblivion runs fine.

This means that Oblivion can be now finally be run with no code that requires a Microsoft license.  Now if they can just get pbuffer to work again soon, and before they declare a 1.0 release, I'll be very happy.

AFAIK pbuffers are not better or faster than fbos, at least with nvidia cards.I'd say that the reason that pbuffers worked better in older wine versions was simply because the wine code for pbuffers was better/faster/more complete, but that is not the case with newer wine releases.

---

### Post by Felson on 2008-03-13
Anyone ever get obse working? 
[http://obse.silverlock.org/](http://obse.silverlock.org/)
There are a tonne of cool adons that use it.

---

### Post by scottyboycj2 on 2008-03-18
okay it would appear that i am unfortunately a LE' N00B (new to Linux,Ubuntu,wine) is there any script that will enable me to just run oblivion or is that completely out of the question .... if it is is there any  
newbie instructions 

:lolflag:

PS~ be nice now we were all le' n00bs at one point lolz {post back soon}

---

### Post by StephanG on 2008-03-19
My oblivion works fine, except that the game crashes whenever I try to open the journal, just wondering if anyone has some advice on this.  I don't know if its been fixed or not but I get the same problem on wine 0.9.56 and 0.9.57, is there some hack I could try?

[-o< I just want to play Oblivion:-(

---

### Post by StephanG on 2008-03-19
Don't worry, it works now, I just installed shivering isles and now it works!!!

---

### Post by Trythos on 2008-03-21
Hi...I'm a total Ubuntu noob that just changed OS cos i got pissed off at vista =)...and i've been trying to use wine to run oblivion. but every tme i start the game i keep getting " Unable to find a CD-ROM/DVD drive on this computer". can sum1 help me out?

---

### Post by Mongoose on 2008-03-22
Read the wiki to see how to install and setup the game.

---

### Post by Sugi on 2008-03-24
I am having problems within the game.  I am doing the Fighter's Guild quests.  My current rank is a Warder.  I can't get any more contacts (Jobs) from any of the Guild Leaders.  Not in  Anvil, Bravil, Cheydinhal, or Chorrol

I have the following quests:
Azani Blackheart
The Fugitives
The Wandering Scholar
Trolls of Forsaken Mine
The Noble's Daughter
Mystery at Harlun's Watch

I have talked to Modryn Oreyn and he seems like he is still in the Fighter's Guild.  So, I don't think he has been kicked out yet.  I have talked to Azzan in Fighters Guild of Anvil, but he says there is no more contacts for me.  I have not done the quest "The Stone of St. Alessia" but I am have not been demoted.  I am still Warder.  I can't get any more contacts or promotions.  What should I do?

Sugi

---

### Post by oedipuss on 2008-03-29
I 've read that since wine 0.9.40 or so HDR works in oblivion.
I've got an nvidia 7600 GT , and I can't get it to show anything else than the old blue screen + UI, with wine 0.9.58 .. 
Is there anything special that must be done with wine for hdr to work ? 


PS: So far I've tried with a full dx9 installation in wine and with a regular wine + d3dx9_27.dll and various combinations of offscreenrendering modes (fbo, pbuffer,..) all with no success. Also, I've tried disabling various other shaders through the oblivion ini file , with no results whatsoever concerning hdr.

---

### Post by beerfan on 2008-03-29
> **oedipuss said:**
> I 've read that since wine 0.9.40 or so HDR works in oblivion.
I've got an nvidia 7600 GT , and I can't get it to show anything else than the old blue screen + UI, with wine 0.9.58 .. 
Is there anything special that must be done with wine for hdr to work ?

It's never worked for me either. I see blue outside and black indoors. I figure if it's working for some then it must be a hardware or driver issue but who knows.

---

### Post by oedipuss on 2008-03-30
I replaced the file shaderpackage002 with shaderpackage019 in the /data/shaders folder , and now hdr works with no apparent sideeffects ^_^ It seems there was some king of misdetection, or something.
Also, it's not that slow.. The water shader still seems the one responsible for most of the performance loss.  With it , there seems to be a cap at about 7 to 10 fps outdoors, regardless of detail settings or resolution, and without it, it goes up to 20, and possibly more with some tweaking. It doesn't seem much but it gets playable.

---

### Post by bastiegast on 2008-03-30
Ok the shaderpackage switching thing is a dirty hack but it worked for me too. Just don't randomly start switching shader packages.
Here's the procedure(If I remember correctly):

- Start Oblivion with HDR ENABLED
- Load a random saved game, doesn't matter which one, just get in-game.
- Close Oblivion
- Find and open My Games/RenderInfo.txt (same directory as Oblivion.ini)
- Find the line "Shader Package" and read the number.
- Go to Program Files/Bethesda Softworks/Oblivion/Data/Shaders/
- Replace the shaderpackageXXX.dsp corresponding to the number - found in renderinfo.txt with shaderpackage001.sdp (BUT MAKE A BACKUP FIRST)
- Start Oblivion and hope it works

Remember, this is a hack and it might mess up the game, but if you backed up properly you can quite easily restore it.
Also disable the water shader as explained in the wiki to gain some performance.

---

### Post by oedipuss on 2008-03-30
> **bastiegast said:**
> Just don't randomly start switching shader packages.


Why not XD
Pretty psychedelic effects, except when it page faults :P

I wonder what's the reason behind the limited performance. Some posts on oblivion+cedega say that it can approach native windows fps,  (possibly with hdr too once cedega supports it properly), so it should be possible under wine too, theoretically. 
With the water shader turned off, it doesn't get more than a +5 fps boost, still nowhere near native.

Do you think it will ever get fixed ? And I don't mean with the exact same speed as in windows, that's improbable if not impossible, but at least approach it, as other games do.

---

### Post by bastiegast on 2008-03-31
> **oedipuss said:**
> Why not XD
Pretty psychedelic effects, except when it page faults :P

I wonder what's the reason behind the limited performance. Some posts on oblivion+cedega say that it can approach native windows fps,  (possibly with hdr too once cedega supports it properly), so it should be possible under wine too, theoretically. 
With the water shader turned off, it doesn't get more than a +5 fps boost, still nowhere near native.

Do you think it will ever get fixed ? And I don't mean with the exact same speed as in windows, that's improbable if not impossible, but at least approach it, as other games do.

Probably Oblivion will one day be able to run at native speed in wine, maybe next week, maybe in the next few years.

---

### Post by carltonh on 2008-03-31
I doubt Oblivion will run it native speeds in Wine in the immediate future, although with my old 7600GT, it was really close.  Unfortunately, with my new 8600GT, the relative improvement in XP was high but in Linux was hardly any improvement.

Now that there is a Codeweavers Crossover Games, I thought it worthwhile to pledge that I would buy a $39.95 version of Codeweavers if they got Oblivion working well too.  Hopefully some of y'all here might also think it worth it to financially encourage them to improve Wine specifically for Oblivion to make the same pledge.  If more of y'all do, then there is a good chance that it will improve sooner as opposed to later.  I spent $100 on a new graphics card just for Oblivion, and so I'll happily spend $40 for Wine/Crossover improvements for Oblivion.

You can go here to pledge for Oblivion:
[http://www.codeweavers.com/compatibility/browse/name/?app_id=2407](http://www.codeweavers.com/compatibility/browse/name/?app_id=2407)

---

### Post by pandayanyan on 2008-04-01
ok so since my last post (quite a few pages back) I have tried all the suggestions given to me and even reread the wiki step by step and still i am having a few problems. 

My first problem is with oblivion.sh . Whenever I run it (via shell or through menu entry as suggested in the wiki) it doesnt do anything. In  terminal it says  CANT OPEN OBLIVION.SH (both when using root or Normal User). When accessed through the menu it Doesnt do anything.

My second problem is If i run Oblivion through wine programs bethesda oblivion it bring up wine and goes to the autorun menu (splash box with play data files options tech support exit) and everything there works but when i click on play it closes wine and doesnt do anything else. 
I am confident it is not any of the aforementioned .ini settings now after much work there. What else could it be? 


Here is a copy of my oblivion.sh in case something is wrong there:
#!/bin/sh
# This script disables all the text output for Wine
# debugging for improved performace.
export WINEDEBUG=fixme-all,err-all,warn-all,trace-all
"/home/USER/.wine/drive_c/Program Files/Bethesda Softworks/Oblivion/Data/"=/opt/games/Windows/Oblivion
cd ${"/home/USER/.wine/drive_c/Program Files/Bethesda Softworks/Oblivion/Data/"}
wine OblivionLauncher.exe


Any help would be greatly appreciated....

---

### Post by Outworlder on 2008-04-01
> **oedipuss said:**
> Why not XD
Pretty psychedelic effects, except when it page faults :P

I wonder what's the reason behind the limited performance. Some posts on oblivion+cedega say that it can approach native windows fps,  (possibly with hdr too once cedega supports it properly), so it should be possible under wine too, theoretically. 
With the water shader turned off, it doesn't get more than a +5 fps boost, still nowhere near native.

Do you think it will ever get fixed ? And I don't mean with the exact same speed as in windows, that's improbable if not impossible, but at least approach it, as other games do.

Actually, nothing says native or above native speeds aren't possible.

Just means there's a lot of optimizations left to do.

---

### Post by oedipuss on 2008-04-03
I'm curious what the bottleneck might be. There must be one, since as long as hdr and water are enabled I'm getting almost exactly the same fps in most resolutions, and with most detail settings, such as large textures and grass (which if I remember correctly were an important factor in XP)..  Ok, removing all trees had some impact, but I don't think that counts :P

@pandayanyan : 
Is that script pasted exactly as it is in your pc ? Because you should change the USER to your username. 
Also, try running oblivion from a terminal : cd to wherever it is installed (from the script I'm guessing it's at ~/.wine/drive_c/Program Files/Bethesda Softworks/Oblivion, ~ means /home/*username*/ ) and run 'wine Oblivion.exe'. Maybe the output will help determine the problem.
Oh and look for reports for missing dll files in that output. In my case it needed d3dx9_27.dll and d3dx9_36.dll copied in the same dir as the exe to work.

---

### Post by Mishtal on 2008-04-04
so while this isnt exactly a life or death situation for me (it is just a game after all)
i have been attempting to install and then run oblivion for the past4 days or so, as i eagerly went out to purchase it after remembering it existed.
the game of the year edition, sadly, wont even begin installation, 
but my roommate had a copy of the original game, which would install. i made an image of it for ease of use, have wine set up to recognize the iso as a CD-ROM, et cetera et cetera

so, i have the game installed, have followed mongooses most helpful walkthrough (to the appropriate letter, anyway)

and when i go to run the game, get the following output from the command line

wine /media/disk/Oblivion/Oblivion.exe

(disk is my internal partition for documents etcetera, im lazy and havnt gotten around to renaming it)
```

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:win:EnumDisplayDevicesW ((null),0,0x34f00c,0x00000000), stub!
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
wine: Unhandled page fault on read access to 0x00000000 at address 0x498749 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00498749).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00498749 ESP:0034f448 EBP:01301284 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:01300d8c ECX:01301280 EDX:12000f01
 ESI:00000000 EDI:01300f8c
Stack dump:
0x0034f448:  00000001 00000016 00080000 00000003
0x0034f458:  00000071 bffdcb0e 0034f9b4 00010024
0x0034f468:  00000000 00400000 0034f488 01301790
0x0034f478:  0002870e 00002710 0000000f 00000001
0x0034f488:  000000a0 7b8b0888 00000001 00000000
0x0034f498:  0034f4c8 7b8915fa 000000a0 00000003
Backtrace:
=>1 0x00498749 in oblivion (+0x98749) (0x01301284)
  2 0x00000000 (0x00000001)
  3 0x00000000 (0x00000000)
0x00498749: movl        0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (90 modules)
PE        400000-  baf000       Export          oblivion
PE        bb0000-  dff000       Deferred        d3dx9_27
PE      18000000-18068000       Deferred        binkw32
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7dc6b000-7dd4b000       Deferred        wined3d<elf>
  \-PE  7dc80000-7dd4b000       \               wined3d
ELF     7dd4b000-7dd7a000       Deferred        d3d9<elf>
  \-PE  7dd50000-7dd7a000       \               d3d9
ELF     7e18b000-7e1a0000       Deferred        midimap<elf>
  \-PE  7e190000-7e1a0000       \               midimap
ELF     7e1a0000-7e1c7000       Deferred        msacm32<elf>
  \-PE  7e1b0000-7e1c7000       \               msacm32
ELF     7e1c7000-7e1df000       Deferred        msacm32<elf>
  \-PE  7e1d0000-7e1df000       \               msacm32
ELF     7e1df000-7e2a5000       Deferred        libasound.so.2
ELF     7e2a5000-7e2db000       Deferred        winealsa<elf>
  \-PE  7e2b0000-7e2db000       \               winealsa
ELF     7e2db000-7e30d000       Deferred        uxtheme<elf>
  \-PE  7e2e0000-7e30d000       \               uxtheme
ELF     7e30d000-7e312000       Deferred        libxfixes.so.3
ELF     7e312000-7e32f000       Deferred        imm32<elf>
  \-PE  7e320000-7e32f000       \               imm32
ELF     7e32f000-7e337000       Deferred        libxrender.so.1
ELF     7e348000-7e3e8000       Deferred        libgl.so.1
ELF     7e3e8000-7e3ed000       Deferred        libxdmcp.so.6
ELF     7e3ed000-7e3f0000       Deferred        libxau.so.6
ELF     7e3f0000-7e4e1000       Deferred        libx11.so.6
ELF     7e4e1000-7e4ef000       Deferred        libxext.so.6
ELF     7e4ef000-7e4f4000       Deferred        libxxf86vm.so.1
ELF     7e4f4000-7e50c000       Deferred        libice.so.6
ELF     7e50c000-7e514000       Deferred        libsm.so.6
ELF     7e516000-7e51f000       Deferred        libxcursor.so.1
ELF     7e51f000-7e525000       Deferred        libxrandr.so.2
ELF     7e525000-7e5b0000       Deferred        winex11<elf>
  \-PE  7e530000-7e5b0000       \               winex11
ELF     7e632000-7e652000       Deferred        libexpat.so.1
ELF     7e652000-7e67d000       Deferred        libfontconfig.so.1
ELF     7e67d000-7e692000       Deferred        libz.so.1
ELF     7e692000-7e702000       Deferred        libfreetype.so.6
ELF     7e702000-7e72f000       Deferred        ws2_32<elf>
  \-PE  7e710000-7e72f000       \               ws2_32
ELF     7e72f000-7e749000       Deferred        wsock32<elf>
  \-PE  7e740000-7e749000       \               wsock32
ELF     7e749000-7e7b1000       Deferred        msvcrt<elf>
  \-PE  7e760000-7e7b1000       \               msvcrt
ELF     7e7b1000-7e7c5000       Deferred        lz32<elf>
  \-PE  7e7c0000-7e7c5000       \               lz32
ELF     7e7c5000-7e7df000       Deferred        version<elf>
  \-PE  7e7d0000-7e7df000       \               version
ELF     7e7df000-7e838000       Deferred        shlwapi<elf>
  \-PE  7e7f0000-7e838000       \               shlwapi
ELF     7e838000-7e93b000       Deferred        shell32<elf>
  \-PE  7e850000-7e93b000       \               shell32
ELF     7e93b000-7e985000       Deferred        dsound<elf>
  \-PE  7e940000-7e985000       \               dsound
ELF     7e985000-7ea13000       Deferred        winmm<elf>
  \-PE  7e990000-7ea13000       \               winmm
ELF     7ea13000-7ea26000       Deferred        libresolv.so.2
ELF     7ea37000-7ea55000       Deferred        iphlpapi<elf>
  \-PE  7ea40000-7ea55000       \               iphlpapi
ELF     7ea55000-7eaae000       Deferred        rpcrt4<elf>
  \-PE  7ea60000-7eaae000       \               rpcrt4
ELF     7eaae000-7eb4f000       Deferred        ole32<elf>
  \-PE  7eac0000-7eb4f000       \               ole32
ELF     7eb4f000-7eb85000       Deferred        dinput<elf>
  \-PE  7eb60000-7eb85000       \               dinput
ELF     7eb85000-7eb9e000       Deferred        dinput8<elf>
  \-PE  7eb90000-7eb9e000       \               dinput8
ELF     7eb9e000-7ebe7000       Deferred        advapi32<elf>
  \-PE  7ebb0000-7ebe7000       \               advapi32
ELF     7ebe7000-7ec82000       Deferred        gdi32<elf>
  \-PE  7ec00000-7ec82000       \               gdi32
ELF     7ec82000-7edc0000       Deferred        user32<elf>
  \-PE  7eca0000-7edc0000       \               user32
ELF     7edc0000-7ee7e000       Deferred        comctl32<elf>
  \-PE  7edd0000-7ee7e000       \               comctl32
ELF     7ef9d000-7efa8000       Deferred        libnss_files.so.2
ELF     7efa8000-7efb2000       Deferred        libnss_nis.so.2
ELF     7efb2000-7efca000       Deferred        libnsl.so.1
ELF     7efca000-7efef000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7ca1000-b7ca5000       Deferred        libdl.so.2
ELF     b7ca5000-b7def000       Deferred        libc.so.6
ELF     b7df0000-b7e08000       Deferred        libpthread.so.0
ELF     b7e19000-b7f2d000       Deferred        libwine.so.1
ELF     b7f2f000-b7f4b000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a
        0000000c    0
        0000000b    0
00000008 (D) F:\Oblivion\Oblivion.exe
        0000000f   15
        0000000e   15
        0000000d    0
        00000009    0 <==
fixme:winmm:MMDRV_Exit Closing while ll-driver open

```


ive tried this on wine .9.58 and also .9.46
this specific output is for .9.46, however .9.58 wont run either.

while it would be nice to be able to run the game without having to resort to windows, i dont really expect it. my system is a HP compaq nw8440 laptop that has had some substantial modifications made to it before purchase from HP, and is.. glitchy... to say the least, so its not like i actually expected to succeed in getting oblivion to work.

i run ubuntu 7.10 with no interesting changes of note from the regular installation, an intel core due processor and an ati graphics card of some type.

*shrug*

ill send a bug ticket over to the folks at wine when i get around to it.
but, out of curiousity, does anyone see, just at a glance, what might be the issue?


after edit-

it may be necessary to mention that i did in fact take the d3dx9_27 dll file from the image and place it into my wine/windows/system32 dil. so, even though my code snippit complains about that, the reason isnt that i didnt copy the dll.

thanks!
-Mishtal

---

### Post by rpaolsen on 2008-04-04
I got Oblivion working with this guide, but when i install Shivering Isles it doesnt allow me to start a new game (nothing happens when i click yes on start new game) and the game crashes when i try to load an savegame. None of the patches are installed.

I get the following output from wine:
```
wine: Unhandled page fault on read access to 0x0000016c at address 0x48c083 (thread 000f), starting debugger...
Unhandled exception: page fault on read access to 0x0000016c in 32-bit code (0x0048c083).

```Followed by an register dump.

System being used is Ubuntu 7.10 64bit and Wine 0.9.46.


PROBLEM IS SOLVED!
Somehow the extracting program didn't extract all the needed files. After extracting the files again everything worked perfect.

---

### Post by pandayanyan on 2008-04-04
No i changed that when i posted it here. My actual username is put in the REAL code.:lolflag: i wish that was all that was wrong to be honest.

This is what i get when running it under terminal:

```
err:module:import_dll Library d3dx9_27.dll (which is needed by L"C:\\Program Files\\Bethesda Softworks\\Oblivion\\Oblivion.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Bethesda Softworks\\Oblivion\\Oblivion.exe" failed, status c0000135

```

so i am guessing I need that d3dx9_27.dll which shouldnt be a problem I will try that and see if it fixes it thank you for your help!!!!


WOOT!!!! That fixed it thank you!!! I think i am in love with you now ha ha! anyways thanks again.

---

### Post by Outworlder on 2008-04-06
You people should consider posting crashes at  [Wine's Application Database]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=3150"), or creating bug reports in [Wine's bugzilla]("http://bugs.winehq.org/").

---

### Post by pandayanyan on 2008-04-07
I am having a different problem now. Oblivion runs perfect but when it gets to the part in the beginning where the captain dies when the first group of assassins attack you and the emperor the game freezes and eventuallly crashes my system. I cant find an error log for oblivion and since even my OS freezes when it crashes I cant see the terminal so i have nothing to show.
I found someone who had this problem previously disabled joystick and music in the oblivion.ini I have already done that and it still freezes. Other than this hang up the game runs very quickly and efficiently. 
Any suggestions?:confused:

I am using wine 0.9.46 
installed oblivion using the wiki here: [http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux)

---

### Post by carltonh on 2008-04-08
I've been having an odd sound problem and I'm not sure if it Wine or just Oblivion itself.  (using current patch, unofficial patch, and Shivering Isles) I've had it from 0.9.55-0.9.59 but I doubt it is caused by a particular Wine version.

The starting screens have sound and act normally until the main title screen where the IV in obl"IV"ion is on screen.  There should be sound there, but there is usually none.  I go into audio options and sometimes sound is reset to all sliders at minimum, so I reset them to default.  If I load my existing game, then I can get no sound no matter how I adjust audio sliders.  Sometimes I can exit, restart, and start a new game and sound will work again.  _Only then_ if I load my current game over the new game can I get sound to work in my saved game again.  Then if I exit the game and return later, I have to repeat the whole process, which doesn't always work either, and then sound will sometimes work in my saved game.

I have never manually adjusted my Oblivion.ini settings, nor manually edited anything within a saved game.  Is there some fix I could try that way?  Any other advice?

The only software I had installed that I think might have affected Linux sound settings is Tuxguitar, Fluidsynth, and TiMidity++.  I didn't have sound problems in Oblivion before loading these.

---

### Post by pandayanyan on 2008-04-15
bump

---

### Post by brento73 on 2008-04-16
I'm having the exact same issue, no sound once the game is loaded. There really isn't much in the Oblivion:Linux wiki about audio, just some basic settings, so I'm wondering if anyone else has been able to figure this out?

---

### Post by scarmatil on 2008-04-20
I solved the sound problem by using OSS instead of ALSA.
With pulseaudio, you just need to use the wrapper :
```
 % padsp wine OblivionLauncher.exe
```

and that did the trick :)

---

### Post by marcmarc on 2008-04-27
So, as you may have guessed, I'm trying to get oblivion running with wine, and failing.

Firstly, I have it working pretty good with cedega.  There's just a weird sound issue, and I'm going with wine because it gives me more customization options.

I'm using Ubuntu 8.04, with wine 0.9.60

It installs perfectly, when it opens up, all the screens run great.  I went through the .ini and tweaked all the settings suggested both in the wineappDB, and the wiki.

When it runs though, it just renders black.  It's pretty interesting actually, the HUD shows up- there's a compass, crosshair, etc.  I can punch the cup off the table and hear it fall, I just can't see anything.  HDR is disabled.

Here's my registry:
DirectDrawRenderer fbo
OffscreenRenderingMode fbo
PixelShaderMode enabled
UseGLSL enabled
VideoMemorySize 256

---

### Post by beerfan on 2008-04-28
> **marcmarc said:**
> When it runs though, it just renders black.  It's pretty interesting actually, the HUD shows up- there's a compass, crosshair, etc.  I can punch the cup off the table and hear it fall, I just can't see anything.  HDR is disabled.

Try disabling Bloom. HDR works for me but bloom is not supported still as far as I know.

---

### Post by marcmarc on 2008-04-28
> **beerfan said:**
> Try disabling Bloom. HDR works for me but bloom is not supported still as far as I know.

Hmm, I've disabled bloom and I still get the same problem.
I tried the trick some people mentioned about replacing shaderpackage002 with shaderpackage001, but that merely resulted in a crash.

I also changed my registry to this:
[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"OffscreenRenderingMode"="fbo"
"UseGLSL"="enabled"
"VideoMemorySize"="256"

In case the other settings were causing trouble, but this didn't manage to fix it either.

---

### Post by 4rk3typ3 on 2008-04-28
The latest 0.9.60 release of WINE has been able to do alot more with oblivion, I was actually able to make the settings high then tweak a few down (core 2 duo E6400 & Nvidia Geforce 8800GTS 640MB).

---

### Post by SolidCube on 2008-04-29
I'm trying to run Oblivion on Heron i386, wine-0.9.59.  The installer runs fine, and the initial menu comes up, but then I get the following error.  Any clues?

```
 wine: Unhandled page fault on read access to 0x00020498 at address 0x1111ca7 (thread 003f), starting debugger...
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Unhandled exception: page fault on read access to 0x00020498 in 32-bit code (0x01111ca7).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:01111ca7 ESP:7f22ff04 EBP:7f22ffe8 EFLAGS:00010296(   - 00      RISAP1)
 EAX:00000000 EBX:7b8b2888 ECX:ffffffff EDX:00000000
 ESI:7ffdf000 EDI:00020498
Stack dump:
0x7f22ff04:  7f22ff2c 01111037 7b875be7 7ffdf000
0x7f22ff14:  00000000 00000000 00000000 00000000
0x7f22ff24:  00000000 00000000 ffffffff 7b82ec74
0x7f22ff34:  7b8443f0 7b8b2888 7ffdf000 00000000
0x7f22ff44:  7f22ffe8 51fe2100 1ab70109 00000000
0x7f22ff54:  00000000 00000000 00000000 00000000

```

---

### Post by jlacroix on 2008-05-04
I get 93 FPS on my Windows XP partition with high settings and 1280x1024 when walking outside in Oblivion. In Ubuntu, I get 15 if I'm lucky. This is ridiculous, I'm giving up on Oblivion in Linux until some significant advances are made.

---

### Post by tghe-retford on 2008-05-17
> **marcmarc said:**
> When it runs though, it just renders black.  It's pretty interesting actually, the HUD shows up- there's a compass, crosshair, etc.  I can punch the cup off the table and hear it fall, I just can't see anything.  HDR is disabled.
I had the same problem when I realised that anti-aliasing was enabled. Disabling it fixed the problem and I could see again.

---

### Post by VinisLentoje on 2008-05-25
Hello,
I have this strange problem, can't even start installing the game. (see attachment).
I get this terminal output:

```
err:virtual:map_file_into_view shared writable mmap not supported, broken filesystem?
err:virtual:NtMapViewOfSection map_file_into_view 0x340000 1000 000000000 failed
err:storage:ImplBIGBLOCKFILE_WriteAt Unable to get a page to write. This should never happen
err:virtual:map_file_into_view shared writable mmap not supported, broken filesystem?
err:virtual:NtMapViewOfSection map_file_into_view 0x340000 1000 000000000 failed
err:storage:ImplBIGBLOCKFILE_WriteAt Unable to get a page to write. This should never happen
err:virtual:map_file_into_view shared writable mmap not supported, broken filesystem?
err:virtual:NtMapViewOfSection map_file_into_view 0x340000 1000 000000000 failed

```

Can someone tell me what I did wrong?

---

### Post by Enverex on 2008-05-25
> **VinisLentoje said:**
> Hello,
I have this strange problem, can't even start installing the game. (see attachment).
I get this terminal output:

```
err:virtual:map_file_into_view shared writable mmap not supported, broken filesystem?
err:virtual:NtMapViewOfSection map_file_into_view 0x340000 1000 000000000 failed
err:storage:ImplBIGBLOCKFILE_WriteAt Unable to get a page to write. This should never happen
err:virtual:map_file_into_view shared writable mmap not supported, broken filesystem?
err:virtual:NtMapViewOfSection map_file_into_view 0x340000 1000 000000000 failed
err:storage:ImplBIGBLOCKFILE_WriteAt Unable to get a page to write. This should never happen
err:virtual:map_file_into_view shared writable mmap not supported, broken filesystem?
err:virtual:NtMapViewOfSection map_file_into_view 0x340000 1000 000000000 failed

```

Can someone tell me what I did wrong?

Install Oblivion in Wine, don't run it from a Windows partition (that should have been obvious from the broken filesystem comments).

---

### Post by VinisLentoje on 2008-05-25
> **Enverex said:**
> Install Oblivion in Wine, don't run it from a Windows partition (that should have been obvious from the broken filesystem comments).

Damn, my C drive is mapped on ex-windows NTFS partition, and wine won't let me change the C drive directory anymore. So I guess, normal installation won't happen.

"But I tried unshielding data[1-8].cab to a directory of my choice and run the game. It works! so I guess that's solved, at least partially."

^ crashes while trying to edit the starting face =[

---

### Post by Enverex on 2008-05-25
Mapping Wine's C to an NTFS drive is quite possibly the worst thing you could ever do. Recommended action : rm -rf ~/.wine and start over.

---

### Post by VinisLentoje on 2008-05-25
> **Enverex said:**
> Mapping Wine's C to an NTFS drive is quite possibly the worst thing you could ever do. Recommended action : rm -rf ~/.wine and start over.

1st, Ya I know, /me n00b.

2nd, deleting wine directory didn't help, it automatically sets C dir to  "../drive_c" and I still can't change it.

---

### Post by Enverex on 2008-05-25
> **VinisLentoje said:**
> 1st, Ya I know, /me n00b.

2nd, deleting wine directory didn't help, it automatically sets C dir to  "../drive_c" and I still can't change it.

../drive_c is right, that's ~/.wine/drive_c.

---

### Post by VinisLentoje on 2008-05-25
> **Enverex said:**
> ../drive_c is right, that's ~/.wine/drive_c.

...and that's not very good in my situation.
I wonder what happened? I was able to change C drive in older wine. Gotta do something. I figured, that drive information are kept in ~/.wine/dosdevices in shortcuts to those dirs they are mapped to. Can You tell me how to change their target?

---

### Post by Enverex on 2008-05-25
> **VinisLentoje said:**
> ...and that's not very good in my situation.
I wonder what happened? I was able to change C drive in older wine. Gotta do something. I figured, that drive information are kept in ~/.wine/dosdevices in shortcuts to those dirs they are mapped to. Can You tell me how to change their target?

Ah right, is your $HOME folder on an NTFS drive? That's..... really such a bad idea and you need to fix it on some native Linux drive.

---

### Post by VinisLentoje on 2008-05-25
> **Enverex said:**
> Ah right, is your $HOME folder on an NTFS drive? That's..... really such a bad idea and you need to fix it on some native Linux drive.

the thing is, there was some mix up when assigning folders on installation and now  I only have 744 MB left in my HOME folder, so I want to keep away from writing into it as much as possible. The guy (my friend, programmer & Linux pr0) who owns my linux HDD made a real mess in it.

---

### Post by VinisLentoje on 2008-05-25
OK, now I've got the installer running, but when I try to install I get this error (see attachment)
And no, I'm not trying to install into a NTFS partition.

---

### Post by KazukiFlame on 2008-05-26
i understand we can't load obmm yet.

but is there anyway to simply get oblivion in linux to at least read the load list generated by obmm in xp?

like i make the load list in xp, n run oblivion in linux?!

---

### Post by VinisLentoje on 2008-06-02
Bump

---

### Post by Delever on 2008-06-03
> **KazukiFlame said:**
> i understand we can't load obmm yet.

but is there anyway to simply get oblivion in linux to at least read the load list generated by obmm in xp?

like i make the load list in xp, n run oblivion in linux?!

You can install .net framework using winetricks, then install obmm, and launch it from command line like this:

cd "/home/<username>/.wine/drive_c/Program Files/Bethesda Softworks/Oblivion"
wine OblivionModManager.exe

not everything works, though.

---

### Post by Delever on 2008-06-03
> **VinisLentoje said:**
> OK, now I've got the installer running, but when I try to install I get this error (see attachment)
And no, I'm not trying to install into a NTFS partition.

Installed fine with latest wine (rc3), and no modifications.

---

### Post by Delever on 2008-06-03
Ok, I have question myself.

Soon after I got oblivion working, I decided to push it further and try to install additional mods. Specifically, francesco's overhaul. Everything worked fine (exe installer!), I just needed to solve some problems with load order, and was able to do that with WryeBash (again, win).

Well, the problem I am having, is, that (as far as I could trace), it seems that Francesco's mod adds or modifies some sounds, which can not be played by oblivion itself natively, so it tries to build playback graph with direct sound and fails. Of course, it works if I disable sounds (i can leave music enabled), but, well, I want it perfect :D.

I tried:
- Installing ffdshow codecs, got Media Player Classic to work. However, it seems that it uses internal codec to play mp3 files (i don't have much knowledge about this, and I don't really know if not playable files are mp3 or wav).
- Locate what exactly causes this: with francesco's creatures disabled, problem disappears, so probably sounds which cause this are from creatures (I suspect Imps).

I had idea that I may be able to run it by extracting francesco's bsa file contents to oblivion data folder, and then simply remove original bsa and mp3/wav files from extracted folder, o better, recreate that bsa without sound files. I found that OBMM can do this, i got it to run (posted about that in previously), but "extract all" command crashes at the beginning.

If anyone has more ideas, I would be glad if you post them.

---

### Post by Delever on 2008-06-04
Yes! I was able to recreate FraNewCrea.bsa without "sound" directory, and it works now!

So I can now report success with Oblivion and huge mod working (some sounds missing, but that's not too bad) :guitar:

---

### Post by xpxzampop on 2008-06-13
Could I get you guys to look at this: [http://ubuntuforums.org/showthread.php?p=5176106](http://ubuntuforums.org/showthread.php?p=5176106)

---

### Post by halfduplex on 2008-06-19
hello, im also trying to get oblivion working under ubuntu with wine, but it failed.:( i already installed it several times and tried different things, but nothing works. ok, the installer works but the game itself wont start. ive followed your wiki.

Here's my terminal output:

```
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(1680,1050)
wine: Unhandled page fault on read access to 0x00000004 at address 0x58dc7c (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000004 in 32-bit code (0x0058dc7c).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0058dc7c ESP:0033e64c EBP:00000000 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000000 ECX:2743f65d EDX:ffffffff
 ESI:00000000 EDI:00a691d8
Stack dump:
0x0033e64c:  00000000 00000000 27701005 1f001aa0
0x0033e65c:  1b000f28 00000000 00000000 0033f500
0x0033e66c:  0033e864 7fffffa6 0033e80c 15000a14
0x0033e67c:  00a691d8 00002800 00000000 00000000
0x0033e68c:  00000000 277013cd 00802431 0033e80c
0x0033e69c:  00000000 277010f9 00000001 00000000
Backtrace:
0x0058dc7c: movl	0x4(%ebp),%ecx
Modules:
Module	Address			Debug info	Name (96 modules)
PE	  400000-  baf000	Export          oblivion
PE	  bb0000-  dff000	Deferred        d3dx9_27
PE	18000000-18068000	Deferred        binkw32
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7d051000-7d05c000	Deferred        libgcc_s.so.1
ELF	7d16b000-7dc80000	Deferred        libglcore.so.1
ELF	7dc80000-7dd24000	Deferred        libgl.so.1
ELF	7dd24000-7de27000	Deferred        wined3d<elf>
  \-PE	7dd40000-7de27000	\               wined3d
ELF	7e1b9000-7e1e9000	Deferred        d3d9<elf>
  \-PE	7e1c0000-7e1e9000	\               d3d9
ELF	7e257000-7e26b000	Deferred        midimap<elf>
  \-PE	7e260000-7e26b000	\               midimap
ELF	7e26b000-7e291000	Deferred        msacm32<elf>
  \-PE	7e270000-7e291000	\               msacm32
ELF	7e291000-7e2a8000	Deferred        msacm32<elf>
  \-PE	7e2a0000-7e2a8000	\               msacm32
ELF	7e2a8000-7e36b000	Deferred        libasound.so.2
ELF	7e37c000-7e3b2000	Deferred        winealsa<elf>
  \-PE	7e390000-7e3b2000	\               winealsa
ELF	7e3b2000-7e3e5000	Deferred        uxtheme<elf>
  \-PE	7e3c0000-7e3e5000	\               uxtheme
ELF	7e3e5000-7e3ee000	Deferred        libxcursor.so.1
ELF	7e3ee000-7e3f3000	Deferred        libxfixes.so.3
ELF	7e3f3000-7e3f6000	Deferred        libxcomposite.so.1
ELF	7e3f6000-7e3fc000	Deferred        libxrandr.so.2
ELF	7e3fc000-7e404000	Deferred        libxrender.so.1
ELF	7e404000-7e407000	Deferred        libxinerama.so.1
ELF	7e407000-7e427000	Deferred        imm32<elf>
  \-PE	7e410000-7e427000	\               imm32
ELF	7e427000-7e42c000	Deferred        libxdmcp.so.6
ELF	7e42c000-7e444000	Deferred        libxcb.so.1
ELF	7e444000-7e447000	Deferred        libxau.so.6
ELF	7e447000-7e52e000	Deferred        libx11.so.6
ELF	7e52e000-7e53c000	Deferred        libxext.so.6
ELF	7e53c000-7e541000	Deferred        libxxf86vm.so.1
ELF	7e541000-7e543000	Deferred        libnvidia-tls.so.1
PE	7e54c000-7e550000	Deferred        libasound_module_rate_speexrate.
ELF	7e552000-7e5e9000	Deferred        winex11<elf>
  \-PE	7e560000-7e5e9000	\               winex11
ELF	7e5ff000-7e620000	Deferred        libexpat.so.1
ELF	7e620000-7e64a000	Deferred        libfontconfig.so.1
ELF	7e64a000-7e65f000	Deferred        libz.so.1
ELF	7e65f000-7e6cf000	Deferred        libfreetype.so.6
ELF	7e6cf000-7e6fb000	Deferred        ws2_32<elf>
  \-PE	7e6e0000-7e6fb000	\               ws2_32
ELF	7e6fb000-7e715000	Deferred        wsock32<elf>
  \-PE	7e700000-7e715000	\               wsock32
ELF	7e715000-7e77f000	Deferred        msvcrt<elf>
  \-PE	7e730000-7e77f000	\               msvcrt
ELF	7e77f000-7e793000	Deferred        lz32<elf>
  \-PE	7e780000-7e793000	\               lz32
ELF	7e793000-7e7ac000	Deferred        version<elf>
  \-PE	7e7a0000-7e7ac000	\               version
ELF	7e7ac000-7e805000	Deferred        shlwapi<elf>
  \-PE	7e7c0000-7e805000	\               shlwapi
ELF	7e805000-7e918000	Deferred        shell32<elf>
  \-PE	7e820000-7e918000	\               shell32
ELF	7e918000-7e962000	Deferred        dsound<elf>
  \-PE	7e920000-7e962000	\               dsound
ELF	7e962000-7e9f4000	Deferred        winmm<elf>
  \-PE	7e970000-7e9f4000	\               winmm
ELF	7e9f4000-7ea07000	Deferred        libresolv.so.2
ELF	7ea18000-7ea36000	Deferred        iphlpapi<elf>
  \-PE	7ea20000-7ea36000	\               iphlpapi
ELF	7ea36000-7ea97000	Deferred        rpcrt4<elf>
  \-PE	7ea40000-7ea97000	\               rpcrt4
ELF	7ea97000-7eb3b000	Deferred        ole32<elf>
  \-PE	7eab0000-7eb3b000	\               ole32
ELF	7eb3b000-7eb72000	Deferred        dinput<elf>
  \-PE	7eb40000-7eb72000	\               dinput
ELF	7eb72000-7eb8a000	Deferred        dinput8<elf>
  \-PE	7eb80000-7eb8a000	\               dinput8
ELF	7eb8a000-7ebdc000	Deferred        advapi32<elf>
  \-PE	7eba0000-7ebdc000	\               advapi32
ELF	7ebdc000-7ec77000	Deferred        gdi32<elf>
  \-PE	7ebf0000-7ec77000	\               gdi32
ELF	7ec77000-7edbe000	Deferred        user32<elf>
  \-PE	7ec90000-7edbe000	\               user32
ELF	7edbe000-7ee7d000	Deferred        comctl32<elf>
  \-PE	7edd0000-7ee7d000	\               comctl32
ELF	7ef9d000-7efa8000	Deferred        libnss_files.so.2
ELF	7efa8000-7efb2000	Deferred        libnss_nis.so.2
ELF	7efb2000-7efca000	Deferred        libnsl.so.1
ELF	7efca000-7efef000	Deferred        libm.so.6
ELF	7efef000-7eff1000	Deferred        libxcb-xlib.so.0
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	f7d25000-f7d29000	Deferred        libdl.so.2
ELF	f7d29000-f7e78000	Deferred        libc.so.6
ELF	f7e79000-f7e91000	Deferred        libpthread.so.0
ELF	f7ea2000-f7fd8000	Deferred        libwine.so.1
ELF	f7fda000-f7ff9000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Programme\Oblivion\Oblivion.exe
	0000001b   15
	0000001a   15
	00000019    0
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
fixme:winmm:MMDRV_Exit Closing while ll-driver open

```

im using ubuntu hardy amd 64 on an intel q6600, 4gb ram ddr2, nvidia 8800gt.

maybe anyone can help me!
thanks in advance


EDIT: 
Now I had to reinstall my whole Ubuntu and Wine system, and now it works FINE ;)
(i dont know why, maybe some needed packages were not on my system)
(24.06.2008 )

---

### Post by keaton_guy on 2008-06-21
I'm having the same problem as the above poster from GotY version. Really hoping this gets fixed.

---

### Post by Hiperi0n on 2008-06-27
I can't start the game. I configure it without bloom, antialiasing and a standard resolution, but it won't launch after the launcher. The launcher menu music works fine.

> err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
wine: Call from 0x6c5851 to unimplemented function d3dx9_27.dll.D3DXGetImageInfoFromFileInMemory, aborting
wine: Unimplemented function d3dx9_27.dll.D3DXGetImageInfoFromFileInMemory called at address 0x6c5851 (thread 001c), starting debugger...
W: memblock.c: Memory pool destroyed but not all memory blocks freed! 19 remain.
E: memblock.c: Assertion '(uint8_t*) ptr < (uint8_t*) p->memory.ptr + p->memory.size' failed at pulsecore/memblock.c:276, function mempool_slot_idx(). Aborting.

---

### Post by halfduplex on 2008-07-07
> **Hiperi0n said:**
> wine: Call from 0x6c5851 to unimplemented function d3dx9_27.dll.D3DXGetImageInfoFromFileInMemory, aborting
wine: Unimplemented function d3dx9_27.dll.D3DXGetImageInfoFromFileInMemory called at address 0x6c5851 (thread 001c), starting debugger...
hmmm....did you copy the d3dx9_27.dll into your system32 folder?

---

### Post by Gnominator on 2008-07-20
My Oblivion crashes when I trying to load savegame with the following message:

```

err:quartz:ACMWrapper_ProcessSampleData Error sending sample (80040227)
filesource.c:1385: FileAsyncReader_EndFlush: Assertion `!This->sample_list[x].pSample' failed.
wine: Assertion failed at address 0xb7f80410 (thread 0009), starting debugger...
Unhandled exception: assertion failed in 32-bit code (0xb7f80410).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7f80410 ESP:0032e9dc EBP:0032e9f8 EFLAGS:00200202(   - 00      - - I1)
 EAX:00000000 EBX:000069ad ECX:000069ad EDX:00000006
 ESI:000069ad EDI:b7de2ff4
Stack dump:
0x0032e9dc:  0032e9f8 00000006 000069ad b7cc3085
0x0032e9ec:  b7de2ff4 0032ea98 b7c936b0 0032eb24
0x0032e9fc:  b7cc4a01 00000006 0032ea98 00000000
0x0032ea0c:  7bbf0b28 00000070 7bbf0b30 0032ea3c
0x0032ea1c:  b7d0109d 0032ea5c 7bbf0b30 7bbf0b94
0x0032ea2c:  0032eb34 b7de2ff4 00000060 7bbf0b30
Backtrace:
=>1 0xb7f80410 (0x0032e9f8)
  2 0xb7cc4a01 abort+0x101() in libc.so.6 (0x0032eb24)
  3 0xb7cbc10e __assert_fail+0xee() in libc.so.6 (0x0032eb68)
  4 0x7c94df0b in quartz (+0x1df0b) (0x0032eb98)
  5 0x7c96ba2b Parser_Stop+0xfb() in quartz (0x0032ebc8)
  6 0x7c94ffe1 in quartz (+0x1ffe1) (0x0032ebd8)
  7 0x7c9587dd in quartz (+0x287dd) (0x0032ed38)
  8 0x7c958aa7 in quartz (+0x28aa7) (0x0032ed98)
  9 0x7c958cd0 in quartz (+0x28cd0) (0x0032ede8)
0xb7f80410: popl	%ebp
Modules:
Module	Address			Debug info	Name (110 modules)
PE	  330000-  33b000	Deferred        tes4r
PE	  400000-  baf000	Deferred        oblivion
PE	  bb0000-  dff000	Deferred        d3dx9_27
PE	18000000-18068000	Deferred        binkw32
ELF	7b800000-7b931000	Deferred        kernel32<elf>
  \-PE	7b820000-7b931000	\               kernel32
ELF	7bc00000-7bca5000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca5000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7c8ca000-7c907000	Deferred        winemp3<elf>
  \-PE	7c8d0000-7c907000	\               winemp3
ELF	7c907000-7c927000	Deferred        devenum<elf>
  \-PE	7c910000-7c927000	\               devenum
ELF	7c927000-7c995000	Export          quartz<elf>
  \-PE	7c930000-7c995000	\               quartz
ELF	7cfe3000-7cff7000	Deferred        avicap32<elf>
  \-PE	7cff0000-7cff7000	\               avicap32
ELF	7cff7000-7d01f000	Deferred        msvfw32<elf>
  \-PE	7d000000-7d01f000	\               msvfw32
ELF	7d109000-7dc1e000	Deferred        libglcore.so.1
ELF	7dc1e000-7dcc2000	Deferred        libgl.so.1
ELF	7dcee000-7ddf1000	Deferred        wined3d<elf>
  \-PE	7dd00000-7ddf1000	\               wined3d
ELF	7ddf1000-7de21000	Deferred        d3d9<elf>
  \-PE	7de00000-7de21000	\               d3d9
ELF	7df57000-7df62000	Deferred        libgcc_s.so.1
ELF	7e14a000-7e15e000	Deferred        midimap<elf>
  \-PE	7e150000-7e15e000	\               midimap
ELF	7e15e000-7e221000	Deferred        libasound.so.2
ELF	7e227000-7e24d000	Deferred        msacm32<elf>
  \-PE	7e230000-7e24d000	\               msacm32
ELF	7e24d000-7e282000	Deferred        winealsa<elf>
  \-PE	7e260000-7e282000	\               winealsa
ELF	7e282000-7e2b5000	Deferred        uxtheme<elf>
  \-PE	7e290000-7e2b5000	\               uxtheme
ELF	7e2b5000-7e2be000	Deferred        libxcursor.so.1
ELF	7e2be000-7e2c3000	Deferred        libxfixes.so.3
ELF	7e2c3000-7e2c6000	Deferred        libxcomposite.so.1
ELF	7e2c6000-7e2cc000	Deferred        libxrandr.so.2
ELF	7e2cc000-7e2d4000	Deferred        libxrender.so.1
ELF	7e2d4000-7e2d9000	Deferred        libxxf86vm.so.1
ELF	7e2d9000-7e2dc000	Deferred        libxinerama.so.1
ELF	7e2dc000-7e2fc000	Deferred        imm32<elf>
  \-PE	7e2e0000-7e2fc000	\               imm32
ELF	7e2fc000-7e301000	Deferred        libxdmcp.so.6
ELF	7e301000-7e319000	Deferred        libxcb.so.1
ELF	7e319000-7e31c000	Deferred        libxau.so.6
ELF	7e31c000-7e403000	Deferred        libx11.so.6
ELF	7e403000-7e411000	Deferred        libxext.so.6
ELF	7e411000-7e429000	Deferred        libice.so.6
ELF	7e429000-7e431000	Deferred        libsm.so.6
ELF	7e43f000-7e441000	Deferred        libnvidia-tls.so.1
ELF	7e444000-7e45b000	Deferred        msacm32<elf>
  \-PE	7e450000-7e45b000	\               msacm32
ELF	7e45d000-7e4f4000	Deferred        winex11<elf>
  \-PE	7e470000-7e4f4000	\               winex11
ELF	7e527000-7e548000	Deferred        libexpat.so.1
ELF	7e548000-7e572000	Deferred        libfontconfig.so.1
ELF	7e572000-7e587000	Deferred        libz.so.1
ELF	7e587000-7e5f7000	Deferred        libfreetype.so.6
ELF	7e623000-7e64f000	Deferred        ws2_32<elf>
  \-PE	7e630000-7e64f000	\               ws2_32
ELF	7e64f000-7e669000	Deferred        wsock32<elf>
  \-PE	7e650000-7e669000	\               wsock32
ELF	7e669000-7e6d3000	Deferred        msvcrt<elf>
  \-PE	7e680000-7e6d3000	\               msvcrt
ELF	7e6d3000-7e6e7000	Deferred        lz32<elf>
  \-PE	7e6e0000-7e6e7000	\               lz32
ELF	7e6e7000-7e78c000	Deferred        oleaut32<elf>
  \-PE	7e700000-7e78c000	\               oleaut32
ELF	7e78c000-7e7e5000	Deferred        shlwapi<elf>
  \-PE	7e7a0000-7e7e5000	\               shlwapi
ELF	7e7e5000-7e8fa000	Deferred        shell32<elf>
  \-PE	7e800000-7e8fa000	\               shell32
ELF	7e8fa000-7e944000	Deferred        dsound<elf>
  \-PE	7e900000-7e944000	\               dsound
ELF	7e944000-7e9d6000	Deferred        winmm<elf>
  \-PE	7e950000-7e9d6000	\               winmm
ELF	7e9d6000-7e9e9000	Deferred        libresolv.so.2
ELF	7e9fc000-7ea15000	Deferred        version<elf>
  \-PE	7ea00000-7ea15000	\               version
ELF	7ea15000-7ea33000	Deferred        iphlpapi<elf>
  \-PE	7ea20000-7ea33000	\               iphlpapi
ELF	7ea33000-7ea95000	Deferred        rpcrt4<elf>
  \-PE	7ea40000-7ea95000	\               rpcrt4
ELF	7ea95000-7eb39000	Deferred        ole32<elf>
  \-PE	7eaa0000-7eb39000	\               ole32
ELF	7eb39000-7eb70000	Deferred        dinput<elf>
  \-PE	7eb40000-7eb70000	\               dinput
ELF	7eb70000-7ebc2000	Deferred        advapi32<elf>
  \-PE	7eb80000-7ebc2000	\               advapi32
ELF	7ebc2000-7ec60000	Deferred        gdi32<elf>
  \-PE	7ebd0000-7ec60000	\               gdi32
ELF	7ec60000-7eda7000	Deferred        user32<elf>
  \-PE	7ec80000-7eda7000	\               user32
ELF	7eda7000-7ee67000	Deferred        comctl32<elf>
  \-PE	7edb0000-7ee67000	\               comctl32
ELF	7ef82000-7ef8d000	Deferred        libnss_files.so.2
ELF	7ef8d000-7ef97000	Deferred        libnss_nis.so.2
ELF	7ef97000-7efaf000	Deferred        libnsl.so.1
ELF	7efaf000-7efd4000	Deferred        libm.so.6
ELF	7efd4000-7efd6000	Deferred        libxcb-xlib.so.0
ELF	7efdd000-7eff5000	Deferred        dinput8<elf>
  \-PE	7efe0000-7eff5000	\               dinput8
ELF	b7c94000-b7c98000	Deferred        libdl.so.2
ELF	b7c98000-b7de7000	Export          libc.so.6
ELF	b7de8000-b7e00000	Deferred        libpthread.so.0
ELF	b7e23000-b7e2c000	Deferred        libnss_compat.so.2
ELF	b7e2c000-b7f62000	Deferred        libwine.so.1
ELF	b7f64000-b7f80000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Oblivion\Oblivion.exe
	0000001f    0
	0000001d    0
	0000001c    0
	00000019   15
	00000018    0
	00000009    0 <==
0000000c 
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	00000017    0
Backtrace:
=>1 0xb7f80410 (0x0032e9f8)
  2 0xb7cc4a01 abort+0x101() in libc.so.6 (0x0032eb24)
  3 0xb7cbc10e __assert_fail+0xee() in libc.so.6 (0x0032eb68)
  4 0x7c94df0b in quartz (+0x1df0b) (0x0032eb98)
  5 0x7c96ba2b Parser_Stop+0xfb() in quartz (0x0032ebc8)
  6 0x7c94ffe1 in quartz (+0x1ffe1) (0x0032ebd8)
  7 0x7c9587dd in quartz (+0x287dd) (0x0032ed38)
  8 0x7c958aa7 in quartz (+0x28aa7) (0x0032ed98)
  9 0x7c958cd0 in quartz (+0x28cd0) (0x0032ede8)
Aborted

```

Can anybody help me with that?
My wine's version is 1.1.1 :(

P.S. The same thing happens when I trying to start new game second time.
So, first run works, second not.
Can anybody tell me why that happens?

P.P.S. Using Oblivion GotY

---

### Post by Kinetic Being on 2008-07-21
Can anyone help me figure out how to get this running...

I installed it fine, followed the guide, but when I start the game, it comes up as a black screen and doesn't do anything from there. This is what the terminal gives me:  

```
matt@matt-desktop:~$ export WINEDEBUG=fixme-all,err-all,warn-all,trace-all
matt@matt-desktop:~$ OBLIVION_DIR=/home/matt/oblivion
matt@matt-desktop:~$ cd ${OBLIVION_DIR}
matt@matt-desktop:~/oblivion$ wine OblivionLauncher.exe
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
matt@matt-desktop:~/oblivion$ *********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 469
Software fallback:ctx->Multisample.Enabled
***************************************************************************
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
```

---

### Post by Viranh on 2008-07-27
There appears to be a fix on the wine wiki. 
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem) 
Good luck!

---

### Post by aestrivex on 2008-07-29
> **Gnominator said:**
> My Oblivion crashes when I trying to load savegame with the following message:

```

err:quartz:ACMWrapper_ProcessSampleData Error sending sample (80040227)
filesource.c:1385: FileAsyncReader_EndFlush: Assertion `!This->sample_list[x].pSample' failed.
wine: Assertion failed at address 0xb7f80410 (thread 0009), starting debugger...
Unhandled exception: assertion failed in 32-bit code (0xb7f80410).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7f80410 ESP:0032e9dc EBP:0032e9f8 EFLAGS:00200202(   - 00      - - I1)
 EAX:00000000 EBX:000069ad ECX:000069ad EDX:00000006
 ESI:000069ad EDI:b7de2ff4
Stack dump:
0x0032e9dc:  0032e9f8 00000006 000069ad b7cc3085
0x0032e9ec:  b7de2ff4 0032ea98 b7c936b0 0032eb24
0x0032e9fc:  b7cc4a01 00000006 0032ea98 00000000
0x0032ea0c:  7bbf0b28 00000070 7bbf0b30 0032ea3c
0x0032ea1c:  b7d0109d 0032ea5c 7bbf0b30 7bbf0b94
0x0032ea2c:  0032eb34 b7de2ff4 00000060 7bbf0b30
Backtrace:
=>1 0xb7f80410 (0x0032e9f8)
  2 0xb7cc4a01 abort+0x101() in libc.so.6 (0x0032eb24)
  3 0xb7cbc10e __assert_fail+0xee() in libc.so.6 (0x0032eb68)
  4 0x7c94df0b in quartz (+0x1df0b) (0x0032eb98)
  5 0x7c96ba2b Parser_Stop+0xfb() in quartz (0x0032ebc8)
  6 0x7c94ffe1 in quartz (+0x1ffe1) (0x0032ebd8)
  7 0x7c9587dd in quartz (+0x287dd) (0x0032ed38)
  8 0x7c958aa7 in quartz (+0x28aa7) (0x0032ed98)
  9 0x7c958cd0 in quartz (+0x28cd0) (0x0032ede8)
0xb7f80410: popl	%ebp
Modules:
Module	Address			Debug info	Name (110 modules)
PE	  330000-  33b000	Deferred        tes4r
PE	  400000-  baf000	Deferred        oblivion
PE	  bb0000-  dff000	Deferred        d3dx9_27
PE	18000000-18068000	Deferred        binkw32
ELF	7b800000-7b931000	Deferred        kernel32<elf>
  \-PE	7b820000-7b931000	\               kernel32
ELF	7bc00000-7bca5000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca5000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7c8ca000-7c907000	Deferred        winemp3<elf>
  \-PE	7c8d0000-7c907000	\               winemp3
ELF	7c907000-7c927000	Deferred        devenum<elf>
  \-PE	7c910000-7c927000	\               devenum
ELF	7c927000-7c995000	Export          quartz<elf>
  \-PE	7c930000-7c995000	\               quartz
ELF	7cfe3000-7cff7000	Deferred        avicap32<elf>
  \-PE	7cff0000-7cff7000	\               avicap32
ELF	7cff7000-7d01f000	Deferred        msvfw32<elf>
  \-PE	7d000000-7d01f000	\               msvfw32
ELF	7d109000-7dc1e000	Deferred        libglcore.so.1
ELF	7dc1e000-7dcc2000	Deferred        libgl.so.1
ELF	7dcee000-7ddf1000	Deferred        wined3d<elf>
  \-PE	7dd00000-7ddf1000	\               wined3d
ELF	7ddf1000-7de21000	Deferred        d3d9<elf>
  \-PE	7de00000-7de21000	\               d3d9
ELF	7df57000-7df62000	Deferred        libgcc_s.so.1
ELF	7e14a000-7e15e000	Deferred        midimap<elf>
  \-PE	7e150000-7e15e000	\               midimap
ELF	7e15e000-7e221000	Deferred        libasound.so.2
ELF	7e227000-7e24d000	Deferred        msacm32<elf>
  \-PE	7e230000-7e24d000	\               msacm32
ELF	7e24d000-7e282000	Deferred        winealsa<elf>
  \-PE	7e260000-7e282000	\               winealsa
ELF	7e282000-7e2b5000	Deferred        uxtheme<elf>
  \-PE	7e290000-7e2b5000	\               uxtheme
ELF	7e2b5000-7e2be000	Deferred        libxcursor.so.1
ELF	7e2be000-7e2c3000	Deferred        libxfixes.so.3
ELF	7e2c3000-7e2c6000	Deferred        libxcomposite.so.1
ELF	7e2c6000-7e2cc000	Deferred        libxrandr.so.2
ELF	7e2cc000-7e2d4000	Deferred        libxrender.so.1
ELF	7e2d4000-7e2d9000	Deferred        libxxf86vm.so.1
ELF	7e2d9000-7e2dc000	Deferred        libxinerama.so.1
ELF	7e2dc000-7e2fc000	Deferred        imm32<elf>
  \-PE	7e2e0000-7e2fc000	\               imm32
ELF	7e2fc000-7e301000	Deferred        libxdmcp.so.6
ELF	7e301000-7e319000	Deferred        libxcb.so.1
ELF	7e319000-7e31c000	Deferred        libxau.so.6
ELF	7e31c000-7e403000	Deferred        libx11.so.6
ELF	7e403000-7e411000	Deferred        libxext.so.6
ELF	7e411000-7e429000	Deferred        libice.so.6
ELF	7e429000-7e431000	Deferred        libsm.so.6
ELF	7e43f000-7e441000	Deferred        libnvidia-tls.so.1
ELF	7e444000-7e45b000	Deferred        msacm32<elf>
  \-PE	7e450000-7e45b000	\               msacm32
ELF	7e45d000-7e4f4000	Deferred        winex11<elf>
  \-PE	7e470000-7e4f4000	\               winex11
ELF	7e527000-7e548000	Deferred        libexpat.so.1
ELF	7e548000-7e572000	Deferred        libfontconfig.so.1
ELF	7e572000-7e587000	Deferred        libz.so.1
ELF	7e587000-7e5f7000	Deferred        libfreetype.so.6
ELF	7e623000-7e64f000	Deferred        ws2_32<elf>
  \-PE	7e630000-7e64f000	\               ws2_32
ELF	7e64f000-7e669000	Deferred        wsock32<elf>
  \-PE	7e650000-7e669000	\               wsock32
ELF	7e669000-7e6d3000	Deferred        msvcrt<elf>
  \-PE	7e680000-7e6d3000	\               msvcrt
ELF	7e6d3000-7e6e7000	Deferred        lz32<elf>
  \-PE	7e6e0000-7e6e7000	\               lz32
ELF	7e6e7000-7e78c000	Deferred        oleaut32<elf>
  \-PE	7e700000-7e78c000	\               oleaut32
ELF	7e78c000-7e7e5000	Deferred        shlwapi<elf>
  \-PE	7e7a0000-7e7e5000	\               shlwapi
ELF	7e7e5000-7e8fa000	Deferred        shell32<elf>
  \-PE	7e800000-7e8fa000	\               shell32
ELF	7e8fa000-7e944000	Deferred        dsound<elf>
  \-PE	7e900000-7e944000	\               dsound
ELF	7e944000-7e9d6000	Deferred        winmm<elf>
  \-PE	7e950000-7e9d6000	\               winmm
ELF	7e9d6000-7e9e9000	Deferred        libresolv.so.2
ELF	7e9fc000-7ea15000	Deferred        version<elf>
  \-PE	7ea00000-7ea15000	\               version
ELF	7ea15000-7ea33000	Deferred        iphlpapi<elf>
  \-PE	7ea20000-7ea33000	\               iphlpapi
ELF	7ea33000-7ea95000	Deferred        rpcrt4<elf>
  \-PE	7ea40000-7ea95000	\               rpcrt4
ELF	7ea95000-7eb39000	Deferred        ole32<elf>
  \-PE	7eaa0000-7eb39000	\               ole32
ELF	7eb39000-7eb70000	Deferred        dinput<elf>
  \-PE	7eb40000-7eb70000	\               dinput
ELF	7eb70000-7ebc2000	Deferred        advapi32<elf>
  \-PE	7eb80000-7ebc2000	\               advapi32
ELF	7ebc2000-7ec60000	Deferred        gdi32<elf>
  \-PE	7ebd0000-7ec60000	\               gdi32
ELF	7ec60000-7eda7000	Deferred        user32<elf>
  \-PE	7ec80000-7eda7000	\               user32
ELF	7eda7000-7ee67000	Deferred        comctl32<elf>
  \-PE	7edb0000-7ee67000	\               comctl32
ELF	7ef82000-7ef8d000	Deferred        libnss_files.so.2
ELF	7ef8d000-7ef97000	Deferred        libnss_nis.so.2
ELF	7ef97000-7efaf000	Deferred        libnsl.so.1
ELF	7efaf000-7efd4000	Deferred        libm.so.6
ELF	7efd4000-7efd6000	Deferred        libxcb-xlib.so.0
ELF	7efdd000-7eff5000	Deferred        dinput8<elf>
  \-PE	7efe0000-7eff5000	\               dinput8
ELF	b7c94000-b7c98000	Deferred        libdl.so.2
ELF	b7c98000-b7de7000	Export          libc.so.6
ELF	b7de8000-b7e00000	Deferred        libpthread.so.0
ELF	b7e23000-b7e2c000	Deferred        libnss_compat.so.2
ELF	b7e2c000-b7f62000	Deferred        libwine.so.1
ELF	b7f64000-b7f80000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Oblivion\Oblivion.exe
	0000001f    0
	0000001d    0
	0000001c    0
	00000019   15
	00000018    0
	00000009    0 <==
0000000c 
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	00000017    0
Backtrace:
=>1 0xb7f80410 (0x0032e9f8)
  2 0xb7cc4a01 abort+0x101() in libc.so.6 (0x0032eb24)
  3 0xb7cbc10e __assert_fail+0xee() in libc.so.6 (0x0032eb68)
  4 0x7c94df0b in quartz (+0x1df0b) (0x0032eb98)
  5 0x7c96ba2b Parser_Stop+0xfb() in quartz (0x0032ebc8)
  6 0x7c94ffe1 in quartz (+0x1ffe1) (0x0032ebd8)
  7 0x7c9587dd in quartz (+0x287dd) (0x0032ed38)
  8 0x7c958aa7 in quartz (+0x28aa7) (0x0032ed98)
  9 0x7c958cd0 in quartz (+0x28cd0) (0x0032ede8)
Aborted

```

Can anybody help me with that?
My wine's version is 1.1.1 :(

P.S. The same thing happens when I trying to start new game second time.
So, first run works, second not.
Can anybody tell me why that happens?

P.P.S. Using Oblivion GotY

i solved this by reverting back to wine 1.1.0, in which it runs fine.

---

### Post by eternal_sage on 2008-08-22
ok. not sure if this has been answered before, cause this is a LOT of replies :D, if so, just smack me for being dumb.

anyway, how do you get the plug-ins menu (where you enable and disable mods) to work properly? for me its not giving me a check box to enable the mods, but the DLC mods (Knights of the Nine, etc) all have boxes with checks in them. will i have to do this in config files? if so, where and how?

also, it (the tutorial) talks about making some edits to oblivion.ini. i don't have one, but i do have an Oblivion_default.ini. is this the same thing? if so, where do i put these edits? just paste at the end?

thanks!

edit: D'OH! i found the Oblivion.ini in my save games folder. still not sure about the edits though. thanks for helping a newb!

edit2: double D'OH!! i found i could enable mods by double clicking them. then their box shows up like normal. still not sure about the .ini bit.

---

### Post by M4rotku on 2008-08-24
> **Mongoose said:**
> 

Desktop Integration tab.

Here you should make a folder as your 'Windows folder base' and populate it.  I use ~/Documents/Windows/.  After you make these folders match them up in this interface, since Oblivion follows the logo requirements and uses a 'My Games' folder.

```
mkdir -p ~/Documents/Windows/{Desktop,Documents,Pictures,Music,Video}
```

Your ini and saved games will be under:

```
~/Documents/Windows/Documents/My Games/Oblivion/
```

I copied my old save games and such to the 'Saves' folder under Oblivion, and they all worked fine.



I find this part of the how-to to be rather confusing.  I made the directory ~/Documents/Windows/...

but how do I configure things so that my saved games will be in that folder.  Pretty much, I'm wondering what I'm supposed to do within the Desktop Intergration tab in order to complete this part of the how-to.

Much thanks,
M4rotku

---

### Post by M4rotku on 2008-08-26
bump,  I really don't want to have to boot into Vista for this. :(

---

### Post by governmentproj13 on 2008-08-30
i'm trying to change the wine memory, but there is no place to put the registry key, because the folder for Direct3D isn't there! o.o  Can I just add it?  I have Direct3D, although I didn't have it when I installed wine.  But I definitely have it now.  What do I do?  Reinstall wine?  Or just manually add the folder, then the key?

Here's a pic:
[http://i146.photobucket.com/albums/r275/governmentproj13/Screenshot.png](http://i146.photobucket.com/albums/r275/governmentproj13/Screenshot.png)

---

### Post by M4rotku on 2008-09-01
Another question.  How do I get Direct3d?  I navigated to the correct place within the Registry Editor, and it was not there.  How would I go about either acquiring it or fixing wine so that it is recognized?

---

### Post by BeccyBug on 2008-09-02
> **Xenophoribic said:**
> I was going to install a Windows partition just so I could play Oblivion trouble free 

Ditto that thanks - Oblivion and Guild Wars are probably the only 2 reasons I've still got windows on my other pc.  It says on the wiki that shivering isles works - does that count too, for knights of the nine and thieves den etc...?

---

### Post by brento73 on 2008-09-02
As for the reg key, you can just add it. I think there's a guide out there that tells exactly how, but I can't recall where.

Shivering Isles, Knights of the Nine, etc are all just data files for the same game engine, so to my knowledge they should all work fine. I've played with all the currently available official content, and the only issue I had was trying to install the Fighter's Stronghold since it was a download(I bought the others on disc) and uses it's own downloader/installer. I just installed it on a friends winXP computer and then copied the files from the 'data' folder over to my computer.

---

### Post by OliW on 2008-09-28
Well I'm having no luck with any Oblivion+Wine+Ubuntu guides. :(

Whenever I try and load Oblivion, it crashes when trying to play the intro videos (the launcher shows fine, I'm talking about after you click play). The full error is way too long to post in here but here's the business end:

```
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
wine: Unhandled page fault on write access to 0xcf6bb86c at address 0x401c05 (thread 001c), starting debugger...
Unhandled exception: page fault on write access to 0xcf6bb86c in 32-bit code (0x00401c05).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00401c05 ESP:0033ecb4 EBP:cf6bb864 EFLAGS:00010203(   - 00      - RI1C)
 EAX:32342d4c EBX:cdcdcdd0 ECX:00000000 EDX:00aae97c
 ESI:00aae940 EDI:019dea8c
Stack dump:
0x0033ecb4:  cdcdcdcd 019de710 018db24c 019de918
0x0033ecc4:  00401eb1 cdcdcdd0 00000001 006c582f
0x0033ecd4:  cdcdcdcd 018db24c 0191be98 00000000
0x0033ece4:  6e6f7269 746e656d 3070616d 0015f550
0x0033ecf4:  cdcdcdcd 11fadd80 7d096dec 0033ed3c
0x0033ed04:  b7f0bf9e 00000017 7bc33e71 11fae278
Backtrace:
0x00401c05: movl	%ecx,0x8(%ebp)
Modules:
Module	Address			Debug info	Name (100 modules)
PE	  400000-  b59000	Export          oblivion
PE	  b60000-  daf000	Deferred        d3dx9_27
PE	18000000-18068000	Deferred        binkw32
ELF	7b800000-7b930000	Deferred        kernel32<elf>
  \-PE	7b820000-7b930000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7c22b000-7cf9d000	Deferred        libglcore.so.1
ELF	7cf9d000-7d0a0000	Deferred        wined3d<elf>
  \-PE	7cfb0000-7d0a0000	\               wined3d
ELF	7d0a0000-7d0d0000	Deferred        d3d9<elf>
  \-PE	7d0b0000-7d0d0000	\               d3d9
ELF	7dff6000-7e099000	Deferred        libgl.so.1
ELF	7e103000-7e117000	Deferred        midimap<elf>
  \-PE	7e110000-7e117000	\               midimap
ELF	7e117000-7e13d000	Deferred        msacm32<elf>
  \-PE	7e120000-7e13d000	\               msacm32
ELF	7e13d000-7e18d000	Deferred        libpulse.so.0
ELF	7e194000-7e1ab000	Deferred        msacm32<elf>
  \-PE	7e1a0000-7e1ab000	\               msacm32
ELF	7e1ab000-7e1b4000	Deferred        librt.so.1
ELF	7e1b4000-7e27c000	Deferred        libasound.so.2
ELF	7e27c000-7e2b2000	Deferred        winealsa<elf>
  \-PE	7e290000-7e2b2000	\               winealsa
ELF	7e2b2000-7e2e5000	Deferred        uxtheme<elf>
  \-PE	7e2c0000-7e2e5000	\               uxtheme
ELF	7e2e5000-7e2ee000	Deferred        libxcursor.so.1
ELF	7e2ee000-7e2f3000	Deferred        libxfixes.so.3
ELF	7e2f3000-7e2f7000	Deferred        libxcomposite.so.1
ELF	7e2f7000-7e2fe000	Deferred        libxrandr.so.2
ELF	7e2fe000-7e308000	Deferred        libxrender.so.1
ELF	7e308000-7e30b000	Deferred        libxinerama.so.1
ELF	7e30b000-7e32b000	Deferred        imm32<elf>
  \-PE	7e310000-7e32b000	\               imm32
ELF	7e32b000-7e330000	Deferred        libxdmcp.so.6
ELF	7e330000-7e349000	Deferred        libxcb.so.1
ELF	7e349000-7e437000	Deferred        libx11.so.6
ELF	7e437000-7e446000	Deferred        libxext.so.6
ELF	7e446000-7e45e000	Deferred        libice.so.6
ELF	7e45e000-7e467000	Deferred        libsm.so.6
ELF	7e476000-7e478000	Deferred        libnvidia-tls.so.1
ELF	7e47a000-7e47e000	Deferred        libcap.so.1
ELF	7e47e000-7e485000	Deferred        libasound_module_pcm_pulse.so
ELF	7e485000-7e51c000	Deferred        winex11<elf>
  \-PE	7e490000-7e51c000	\               winex11
ELF	7e5cf000-7e5f6000	Deferred        libexpat.so.1
ELF	7e5f6000-7e623000	Deferred        libfontconfig.so.1
ELF	7e623000-7e639000	Deferred        libz.so.1
ELF	7e639000-7e6af000	Deferred        libfreetype.so.6
ELF	7e6cd000-7e6f9000	Deferred        ws2_32<elf>
  \-PE	7e6d0000-7e6f9000	\               ws2_32
ELF	7e6f9000-7e713000	Deferred        wsock32<elf>
  \-PE	7e700000-7e713000	\               wsock32
ELF	7e713000-7e77d000	Deferred        msvcrt<elf>
  \-PE	7e720000-7e77d000	\               msvcrt
ELF	7e77d000-7e791000	Deferred        lz32<elf>
  \-PE	7e780000-7e791000	\               lz32
ELF	7e791000-7e7ea000	Deferred        shlwapi<elf>
  \-PE	7e7a0000-7e7ea000	\               shlwapi
ELF	7e7ea000-7e8ff000	Deferred        shell32<elf>
  \-PE	7e800000-7e8ff000	\               shell32
ELF	7e8ff000-7e949000	Deferred        dsound<elf>
  \-PE	7e910000-7e949000	\               dsound
ELF	7e949000-7e9db000	Deferred        winmm<elf>
  \-PE	7e950000-7e9db000	\               winmm
ELF	7e9db000-7e9ef000	Deferred        libresolv.so.2
ELF	7e9f1000-7e9f4000	Deferred        libxcb-xlib.so.0
ELF	7e9f4000-7ea0d000	Deferred        version<elf>
  \-PE	7ea00000-7ea0d000	\               version
ELF	7ea0d000-7ea2b000	Deferred        iphlpapi<elf>
  \-PE	7ea10000-7ea2b000	\               iphlpapi
ELF	7ea2b000-7ea8d000	Deferred        rpcrt4<elf>
  \-PE	7ea40000-7ea8d000	\               rpcrt4
ELF	7ea8d000-7eb31000	Deferred        ole32<elf>
  \-PE	7eaa0000-7eb31000	\               ole32
ELF	7eb31000-7eb68000	Deferred        dinput<elf>
  \-PE	7eb40000-7eb68000	\               dinput
ELF	7eb68000-7ebba000	Deferred        advapi32<elf>
  \-PE	7eb70000-7ebba000	\               advapi32
ELF	7ebba000-7ec58000	Deferred        gdi32<elf>
  \-PE	7ebd0000-7ec58000	\               gdi32
ELF	7ec58000-7ed9f000	Deferred        user32<elf>
  \-PE	7ec70000-7ed9f000	\               user32
ELF	7ed9f000-7ee5e000	Deferred        comctl32<elf>
  \-PE	7edb0000-7ee5e000	\               comctl32
ELF	7ee5e000-7ee6a000	Deferred        libnss_files.so.2
ELF	7ee6a000-7ee75000	Deferred        libnss_nis.so.2
ELF	7ee75000-7ee7e000	Deferred        libnss_compat.so.2
ELF	7ee7e000-7ee84000	Deferred        libxxf86vm.so.1
ELF	7ee84000-7ee9c000	Deferred        dinput8<elf>
  \-PE	7ee90000-7ee9c000	\               dinput8
ELF	7efbc000-7efe2000	Deferred        libm.so.6
ELF	7efe2000-7efe5000	Deferred        libxau.so.6
ELF	7efe7000-7f000000	Deferred        libnsl.so.1
ELF	b7d6d000-b7d71000	Deferred        libdl.so.2
ELF	b7d71000-b7ecf000	Deferred        libc.so.6
ELF	b7ed0000-b7ee9000	Deferred        libpthread.so.0
ELF	b7f07000-b803d000	Deferred        libwine.so.1
ELF	b803f000-b805b000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
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
0000001b (D) C:\Program Files\Bethesda Softworks\Oblivion\Oblivion.exe
	00000021   -1
	00000020   -1
	0000001f   15
	0000001e   15
	0000001d    0
	0000001c    0 <==
Backtrace:
fixme:winmm:MMDRV_Exit Closing while ll-driver open
```

I've tried many different versions of Wine, ranging from 0.9.2x up to the latest git version... All come back that way.

I've tried whole new installations on most of the versions, so I'm pretty secure that it's not a installation blip.

I've also tried a few versions of the d3d dll. No love.

I've seen (somewhere - can't remember now) that somebody experiencing this problem reinstalled Ubuntu and it just worked. I've got too much configuration to consider dumping the whole system just for one game... If anybody has any ideas, I'd *really* love to hear from you.

---

### Post by bankie on 2008-10-06
I'm having some problems with Oblivion: No sky and abysmal performance.

Relevant Specs:
Core2 Quad Q6600 @ 3.2Ghz
GeForce GTX260
4GB 4-4-4-12 @ 800Mhz
On-board Realtek Audio

I originally had a problem where the entire screen was black save for the HUD. I fixed this by replacing one of the shaderpackage files. For some reason the RendererInfo.txt file shows my video card as using "Shader Package 2" (Windows lists it as 13). Enabling Distant Land causes the game to crash.

Once I replaced shaderpackage002 with 019 everything looked beautiful save for the lack of sky (It's black and there is no sun). Indoor performance is incredibly fast. Outdoor performance is in the single digits. I can get the game to be playable by reducing the view distance to the lowest setting. For perspective Oblivion will run from 20-60fps with HDR and 4xAA outdoors in Vista.

---

### Post by Fen_Star on 2008-10-20
I was wondering if anyone could tell me if the GOTY edition works, I have see stuff that says it does and stuff that says it doesn't I'm using wine 1.0 rc2 Thanks.

---

### Post by handy on 2008-10-20
Does anyone know the Linux command, (it has to be downloaded in Sabayon at least) that allows you to easily change the case of all files in a directory?

Here is the story:

I made a how-to for installing Oblivion mods in the UESPWiki, a year ago or so, I looked there a couple of months ago & someone had added the info' about this command, which I downloaded & used.  It is a great time saver for us when we add mods & to make sure that there is no confusion caused by windows case insensitivity.  You know file & File being the same thing in windows & two different identities under the Linux kernel.

Anyway, the reason I am writing this, is that someone has basically rewritten the entire how-to with a pile of useless to most people information & deleted the useful stuff.

So, does anyone know the name of this case changing file?

Thanks in advance. :-)

---

### Post by moggy812 on 2008-10-29
i have got the game to work, however, i need to work out the shaders bit so i can see my character in the start new game as it is all black at the mo, the rest is ok, i can veal with the stuttery sound... oh and the video bit stutters and hangs too, any help would be great.
my thanks.
mogg.
oh i am running wine 1.1.7 on ubuntu, and my driver is ATi

---

### Post by strudelthebest on 2008-11-14
Hi all! I got Oblivion:GOTY Edition so I tried to install it on Ubuntu 8.04 and play it with wine 1.0 ('cause I read it worked fine for most of the games) I followed the guide up to the point where you actually install the game.. but have some troubles on the install itself.
Running either of wine OblivionLauncher.exe or wine Setup.exe gives me this output:

```
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
bus@bussel:/media/cdrom$ fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0xeda520,0x00000004,0xeda51c) Unknown information class
```

while if I go through folders to /media/cdrom, right-clicking on OblivionLauncher.exe, all options are blocked except for TheElderScrolls.com and Exit so obviously I cannot install the game :)

This is the screenshot: [IMG]http://img99.imageshack.us/img99/5130/screenshottheelderscrolqd1.png[/IMG]

(i'm italian so esci means exit :D
anyway i haven't read all replies, 'cause it's 50+ pages :S, if the problem is solved anywhere else please post me where is so i can check ^^)

Thanks in advance, hoping someone can help me :)
P.S. for further information (as my hardware or software configuration) post back, i'll reply as soon as possible :)

---

### Post by das letzte einhorn on 2008-11-25
I would like some troubleshooting help here, because there is probably something wrong with what I have setup so far.

I have Oblivion + KotN + SI and all the unofficial patches for each of the modules updated to the latest versions. I am running Oblivion with:

Ibex / Wine 1.1.9
Q6600 @ 2.4GHz
NVidia GeForce 8800GT
4 GB RAM
M-Audio Audiophile 192

I can run the game in Wine, but I have to set all graphic options to Ultra Low and with a desktop of 1440*900 I get about 20-30 fps. I remember that when I had Windows XP 64bit I could run the game @ 1680*1050 with the highest options and have 100+ fps. The most annoying bug is that I cannot enter towns anymore, it crashes after about 5 seconds. I have not tested this in Windows Vista, but I doubt that this issue is related to one of the patches since a lot of people use them and have no issues.

My registry keys are OffscreenRenderingMode=fbo, VideoMemorySize=512 and DirectDrawRenderer=opengl. I have posted in a relevant bug report : [http://bugs.winehq.org/show_bug.cgi?id=14128](http://bugs.winehq.org/show_bug.cgi?id=14128) . I am wondering however since it seems that most people can run the game flawless if they had any feedback or advice for me.

Thanks!

---

### Post by darklegion on 2008-12-19
I have a similar system to yours(only my cpu differs).I get around 20-30fps outdoors, with medium settings.The direct3d > opengl conversion takes a heavy performance hit at the moment.I suggest you raise your settings to at least medium settings, though, performance will be a few frames slower, but it'll look a lot better.
I also suggest overclocking your cpu, I gained around 7fps going from 2.8ghz to 3.3ghz with my e2500.
Probably the best option at the moment, though, is to use cedega.It's still slower than windows but you should get around 30-40 fps outdoors, with near max settings, including HDR.Towns are still slow though (much like wine).There's also a bug where the item dropping sounds are louder than normal.

I don't get the crashing in towns bug. so I can't help you there.

---

### Post by darklegion on 2008-12-19
> 
I would like some troubleshooting help here, because there is probably something wrong with what I have setup so far.

I have Oblivion + KotN + SI and all the unofficial patches for each of the modules updated to the latest versions. I am running Oblivion with:

Ibex / Wine 1.1.9
Q6600 @ 2.4GHz
NVidia GeForce 8800GT
4 GB RAM
M-Audio Audiophile 192

I can run the game in Wine, but I have to set all graphic options to Ultra Low and with a desktop of 1440*900 I get about 20-30 fps. I remember that when I had Windows XP 64bit I could run the game @ 1680*1050 with the highest options and have 100+ fps. The most annoying bug is that I cannot enter towns anymore, it crashes after about 5 seconds. I have not tested this in Windows Vista, but I doubt that this issue is related to one of the patches since a lot of people use them and have no issues.

My registry keys are OffscreenRenderingMode=fbo, VideoMemorySize=512 and DirectDrawRenderer=opengl. I have posted in a relevant bug report : [http://bugs.winehq.org/show_bug.cgi?id=14128](http://bugs.winehq.org/show_bug.cgi?id=14128) . I am wondering however since it seems that most people can run the game flawless if they had any feedback or advice for me.

Thanks!

I have a similar system to yours(only my cpu differs).I never get more than around 30-40fps average outdoors, no matter how it's configured.The direct3d > opengl conversion takes a heavy performance hit at the moment.I suggest you raise your settings to at least medium settings, though, performance will be a few frames slower, but it'll look a lot better.
I also suggest overclocking your cpu, I gained around 7fps going from 2.8ghz to 3.3ghz with my e2500.
Probably the best option at the moment, though, is to use cedega.It's still slower than windows but you should get around 30-40 fps outdoors, with near max settings, including HDR.Towns are still slow though (much like wine).There's also a bug where the item dropping sounds are louder than normal.

I don't get the crashing in towns bug. so I can't help you there.

---

### Post by darklegion on 2008-12-20
Try wine-1.1.11.I get around 28-42 fps outdoors with high settings (and HDR with SM-3.0).I get 40+ fps with medium settings.Speed of oblivion under wine is now as good as cedega, possibly better!

---

### Post by bloeper on 2008-12-27
I have followed you're guide, but oblivion won't even install...
When i run setup.exe i get this output:

```

wine: Call from 0x7b845450 to unimplemented function ntoskrnl.exe.IoRegisterShutdownNotification, aborting
wine: Unimplemented function ntoskrnl.exe.IoRegisterShutdownNotification called at address 0x7b845450 (thread 0014), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.IoRegisterShutdownNotification called in 32-bit code (0x7b8454c3).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b8454c3 ESP:7ec18704 EBP:7ec18768 EFLAGS:00000246(   - 00      - IZP1)
 EAX:7b82ecb9 EBX:7b8b7ff4 ECX:00000000 EDX:7ec18790
 ESI:7ec18790 EDI:7ec1881c
Stack dump:
0x7ec18704:  7ec18790 00000008 0000003c 80000100
0x7ec18714:  00000001 00000000 7b845450 00000002
0x7ec18724:  7edfab40 7edfd048 001119d0 0000002a
0x7ec18734:  00111990 00000032 7ee04ff4 00000004
0x7ec18744:  7bc5cfeb 001119d8 00111648 00000022
0x7ec18754:  7ee04ff4 001118f4 7b84545a 00000000
Backtrace:
=>1 0x7b8454c3 in kernel32 (+0x254c3) (0x7ec18768)
  2 0x7edfaad5 in ntoskrnl (+0x1aad5) (0x7ec18798)
  3 0x7edf36ec in ntoskrnl (+0x136ec) (0x7ec187d8)
  4 0x00451b20 in ebios32.sys (+0x1b20) (0x7ec18800)
  5 0x0045275e in ebios32.sys (+0x275e) (0x7ec18890)
  6 0x0045299a in ebios32.sys (+0x299a) (0x7ec189b4)
  7 0x00110fd8 (0x00780076)
  8 0x00000000 (0x00000000)
0x7b8454c3: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (31 modules)
PE	  450000-  453620	Export          ebios32.sys
ELF	7b800000-7b93d000	Export          kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7ea9d000-7eb09000	Deferred        msvcrt<elf>
  \-PE	7eab0000-7eb09000	\               msvcrt
ELF	7ec1a000-7ec2e000	Deferred        libresolv.so.2
ELF	7ec32000-7ec48000	Deferred        hal<elf>
  \-PE	7ec40000-7ec48000	\               hal
ELF	7ec48000-7ec67000	Deferred        iphlpapi<elf>
  \-PE	7ec50000-7ec67000	\               iphlpapi
ELF	7ec67000-7ecca000	Deferred        rpcrt4<elf>
  \-PE	7ec70000-7ecca000	\               rpcrt4
ELF	7eddb000-7ee13000	Export          ntoskrnl<elf>
  \-PE	7ede0000-7ee13000	\               ntoskrnl
ELF	7ee13000-7ee66000	Deferred        advapi32<elf>
  \-PE	7ee20000-7ee66000	\               advapi32
ELF	7ee66000-7ee72000	Deferred        libnss_files.so.2
ELF	7ee72000-7ee7d000	Deferred        libnss_nis.so.2
ELF	7ee7d000-7ee86000	Deferred        libnss_compat.so.2
ELF	7ee8b000-7eea0000	Deferred        winedevice<elf>
  \-PE	7ee90000-7eea0000	\               winedevice
ELF	7efc0000-7efe6000	Deferred        libm.so.6
ELF	7efe7000-7f000000	Deferred        libnsl.so.1
ELF	b7d78000-b7d7c000	Deferred        libdl.so.2
ELF	b7d7c000-b7eda000	Deferred        libc.so.6
ELF	b7edb000-b7ef4000	Deferred        libpthread.so.0
ELF	b7f0e000-b8045000	Deferred        libwine.so.1
ELF	b8047000-b8064000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a 
	0000000b    0
0000000c 
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f (D) C:\windows\system32\winedevice.exe
	00000014    0 <==
	00000011    0
	00000010    0
Backtrace:
=>1 0x7b8454c3 in kernel32 (+0x254c3) (0x7ec18768)
  2 0x7edfaad5 in ntoskrnl (+0x1aad5) (0x7ec18798)
  3 0x7edf36ec in ntoskrnl (+0x136ec) (0x7ec187d8)
  4 0x00451b20 in ebios32.sys (+0x1b20) (0x7ec18800)
  5 0x0045275e in ebios32.sys (+0x275e) (0x7ec18890)
  6 0x0045299a in ebios32.sys (+0x299a) (0x7ec189b4)
  7 0x00110fd8 (0x00780076)
  8 0x00000000 (0x00000000)
wine: Call from 0x7b845450 to unimplemented function ntoskrnl.exe.IoReleaseCancelSpinLock, aborting
wine: Call from 0x7b845450 to unimplemented function ntoskrnl.exe.IoReleaseRemoveLockAndWaitEx, aborting
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0xeda520,0x00000004,0xeda51c) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0xed940c): Stub!
Error: API mismatch: the NVIDIA kernel module has version 177.80,
but this NVIDIA driver component has version 173.14.12.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
Error: API mismatch: the NVIDIA kernel module has version 177.80,
but this NVIDIA driver component has version 173.14.12.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
fixme:win:EnumDisplayDevicesW ((null),0,0xed9258,0x00000000), stub!
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00000000 ESP:00ed917c EBP:00ed9658 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7e3a5ff4 ECX:0000364d EDX:00000001
 ESI:00ed9638 EDI:7e38bc40
Stack dump:
0x00ed917c:  7e2fd264 00000001 00ed9638 00001908
0x00ed918c:  00000004 00000004 00000000 000080e1
0x00ed919c:  00008367 00000000 00000000 00000000
0x00ed91ac:  00000000 00ed91bc 7ffd8c00 ffffffff
0x00ed91bc:  00000000 00000000 00000000 001338b0
0x00ed91cc:  00000328 00ed95a0 7e3a6a00 7e38baa6
Backtrace:
=>1 0x00000000 (0x00ed9658)
  2 0x7e37a9f2 WineDirect3DCreate+0x22() in wined3d (0x00ed9688)
  3 0x7e3bf5c7 Direct3DCreate9+0x77() in d3d9 (0x00ed96b8)
  4 0x0054447c in setup (+0x14447c) (0x00ed96fc)
  5 0x005448bc in setup (+0x1448bc) (0x00edad3c)
  6 0x004812dd in setup (+0x812dd) (0x00eef93c)
  7 0x00434383 in setup (+0x34383) (0x00eefdbc)
  8 0x00000008 (0x00768e48)
0x00000000: addb	%al,0x0(%eax)
Modules:
Module	Address			Debug info	Name (77 modules)
PE	  400000-  cf0000	Export          setup
ELF	7b800000-7b93d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7ceba000-7dbfa000	Deferred        libglcore.so.1
ELF	7e1d6000-7e27b000	Deferred        libgl.so.1
ELF	7e295000-7e3aa000	Export          wined3d<elf>
  \-PE	7e2b0000-7e3aa000	\               wined3d
ELF	7e3aa000-7e3db000	Export          d3d9<elf>
  \-PE	7e3b0000-7e3db000	\               d3d9
ELF	7e41b000-7e44e000	Deferred        uxtheme<elf>
  \-PE	7e420000-7e44e000	\               uxtheme
ELF	7e44e000-7e457000	Deferred        libxcursor.so.1
ELF	7e457000-7e45c000	Deferred        libxfixes.so.3
ELF	7e45c000-7e460000	Deferred        libxcomposite.so.1
ELF	7e460000-7e467000	Deferred        libxrandr.so.2
ELF	7e467000-7e471000	Deferred        libxrender.so.1
ELF	7e471000-7e474000	Deferred        libxinerama.so.1
ELF	7e474000-7e495000	Deferred        imm32<elf>
  \-PE	7e480000-7e495000	\               imm32
ELF	7e495000-7e49a000	Deferred        libxdmcp.so.6
ELF	7e49a000-7e4b3000	Deferred        libxcb.so.1
ELF	7e4b3000-7e4b6000	Deferred        libxcb-xlib.so.0
ELF	7e4b6000-7e4b9000	Deferred        libxau.so.6
ELF	7e4b9000-7e5a8000	Deferred        libx11.so.6
ELF	7e5a8000-7e5b7000	Deferred        libxext.so.6
ELF	7e5b7000-7e5bd000	Deferred        libxxf86vm.so.1
ELF	7e5bd000-7e5d5000	Deferred        libice.so.6
ELF	7e5d5000-7e5de000	Deferred        libsm.so.6
ELF	7e5e1000-7e5e3000	Deferred        libnvidia-tls.so.1
ELF	7e5f8000-7e693000	Deferred        winex11<elf>
  \-PE	7e610000-7e693000	\               winex11
ELF	7e6aa000-7e6d1000	Deferred        libexpat.so.1
ELF	7e6d1000-7e6fe000	Deferred        libfontconfig.so.1
ELF	7e6fe000-7e714000	Deferred        libz.so.1
ELF	7e714000-7e78a000	Deferred        libfreetype.so.6
ELF	7e78a000-7e7b7000	Deferred        ws2_32<elf>
  \-PE	7e790000-7e7b7000	\               ws2_32
ELF	7e7b7000-7e7d2000	Deferred        wsock32<elf>
  \-PE	7e7c0000-7e7d2000	\               wsock32
ELF	7e7d2000-7e878000	Deferred        oleaut32<elf>
  \-PE	7e7e0000-7e878000	\               oleaut32
ELF	7e878000-7e88c000	Deferred        libresolv.so.2
ELF	7e8a6000-7e8c5000	Deferred        iphlpapi<elf>
  \-PE	7e8b0000-7e8c5000	\               iphlpapi
ELF	7e8c5000-7e928000	Deferred        rpcrt4<elf>
  \-PE	7e8d0000-7e928000	\               rpcrt4
ELF	7e928000-7e9ce000	Deferred        ole32<elf>
  \-PE	7e940000-7e9ce000	\               ole32
ELF	7e9ce000-7ea93000	Deferred        comctl32<elf>
  \-PE	7e9e0000-7ea93000	\               comctl32
ELF	7ea93000-7eaee000	Deferred        shlwapi<elf>
  \-PE	7eaa0000-7eaee000	\               shlwapi
ELF	7eaee000-7ec02000	Deferred        shell32<elf>
  \-PE	7eb00000-7ec02000	\               shell32
ELF	7ec02000-7ec55000	Deferred        advapi32<elf>
  \-PE	7ec10000-7ec55000	\               advapi32
ELF	7ec55000-7ecf4000	Deferred        gdi32<elf>
  \-PE	7ec70000-7ecf4000	\               gdi32
ELF	7ecf4000-7ee40000	Deferred        user32<elf>
  \-PE	7ed10000-7ee40000	\               user32
ELF	7ee40000-7ee55000	Deferred        lz32<elf>
  \-PE	7ee50000-7ee55000	\               lz32
ELF	7ee55000-7ee70000	Deferred        version<elf>
  \-PE	7ee60000-7ee70000	\               version
ELF	7ef90000-7ef9c000	Deferred        libnss_files.so.2
ELF	7ef9c000-7efa7000	Deferred        libnss_nis.so.2
ELF	7efa7000-7efc0000	Deferred        libnsl.so.1
ELF	7efc0000-7efe6000	Deferred        libm.so.6
ELF	b7cb5000-b7cbe000	Deferred        libnss_compat.so.2
ELF	b7cbf000-b7cc3000	Deferred        libdl.so.2
ELF	b7cc3000-b7e21000	Deferred        libc.so.6
ELF	b7e22000-b7e3b000	Deferred        libpthread.so.0
ELF	b7e55000-b7f8c000	Deferred        libwine.so.1
ELF	b7f8e000-b7fab000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) D:\setup.exe
	00000009    0 <==
0000000c 
	00000026    0
	00000021    0
	0000001b    0
	0000001a    0
	00000013    0
	0000000e    0
	0000000d    0
00000017 
	0000001d    0
	0000001c    0
	00000019    0
	00000018    0
0000001e 
	00000022    0
	00000020    0
	0000001f    0
00000023 
	00000027    0
	00000025    0
	00000024    0
00000032 
	00000033    0
Backtrace:
=>1 0x00000000 (0x00ed9658)
  2 0x7e37a9f2 WineDirect3DCreate+0x22() in wined3d (0x00ed9688)
  3 0x7e3bf5c7 Direct3DCreate9+0x77() in d3d9 (0x00ed96b8)
  4 0x0054447c in setup (+0x14447c) (0x00ed96fc)
  5 0x005448bc in setup (+0x1448bc) (0x00edad3c)
  6 0x004812dd in setup (+0x812dd) (0x00eef93c)
  7 0x00434383 in setup (+0x34383) (0x00eefdbc)
  8 0x00000008 (0x00768e48)

```

I must mention i have the GOTY edition...
I run wine 1.0.1

Does anybody know what this means?

---

### Post by Mongoose on 2008-12-27
1. Fix your Nvidia driver install.
2. READ the wiki entry on how to install GotY edition, which has extra copy protection.  ;)

> **bloeper said:**
> I have followed you're guide, but oblivion won't even install...
When i run setup.exe i get this output:

```

Error: API mismatch: the NVIDIA kernel module has version 177.80,
but this NVIDIA driver component has version 173.14.12.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
Error: API mismatch: the NVIDIA kernel module has version 177.80,
but this NVIDIA driver component has version 173.14.12.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.

```

I must mention i have the GOTY edition...
I run wine 1.0.1

Does anybody know what this means?

---

### Post by bloeper on 2008-12-28
The nvidia error is fixed, i was forgotten to reboot computer after new driver install...
Where can i find the installation instructions of GOTY?

[edit]
Busy with installing, get install menu now in anyway, gotta look how far it goes.

[edit2]
Installation has completed, game runs, only need to find out how to make the mouse listen better.. Sometimes it doesn't get my "clicks"

---

### Post by unimatrix on 2009-02-05
Oh man, the performance is just horrible. I'm getting around 1 FPS inside houses. This used to be much better but then something was ****** up in Ubuntu Hardy and further. I think Wine screwed up the vertex shader, as we can see from these benchmarks:
[IMG]http://www.phoronix.com/data/img/results/wine_feb08_tests/05.png[/IMG]
It's been like this ever since (wine 1.1.14 at the moment).

I've tried every possible option and the only thing I can do to make the game playable is to set the resolution to 640x480.

My HW:
AMD Athlon 3500+
nVidia GeForce 6600

And yes, it's good enough. It works on Windows and it used to work on Linux.

---

### Post by Enverex on 2009-02-05
Were those 3DMark tests ran with an ATi card or an nVidia card?

---

### Post by unimatrix on 2009-02-06
Here's the article:
[http://www.phoronix.com/scan.php?page=article&item=wine_feb08_tests&num=1](http://www.phoronix.com/scan.php?page=article&item=wine_feb08_tests&num=1)

It was an nVidia.

---

### Post by ahaslam on 2009-02-10
Hi, long time since I played Oblivion, there were far too many bugs. Now it runs smoothly with good graphics. There seems to only be 2 quirks remaining:

1. The water effects are missing when using pbuffer & show lines when using fbo. Old news, I know...

2. Weird bookshelves, have a look at the screenshot. This affects *most* bookshelves in the game, along with a few random objects. I've heard nothing about it elsewhere.

For the first time I'm actually enjoying this game tho, can't believe how ahead of the times it was, it wows me at every turn.

Wine 1.1.14
Nvidia 180.22

---

### Post by unimatrix on 2009-02-10
Here's a glitch I get. Anyone familiar with it?

---

### Post by OliW on 2009-02-10
unimatrix: yeah - turning off distant land will fix it but it ruins how the game looks =( 

Very unfortunate - I wish they'd just port the damned game.

---

### Post by Progressive on 2009-02-10
I had that same problem, [only worse]("http://ubuntuforums.org/showthread.php?t=984826"). I thought it might be ATI-specific. Perhaps it is a bug in wine itself. I know there are some Fallout 3 patches around somewhere which are necessary in order for it to run. Perhaps some will help us out for Oblivion.

For what its worth, I just started playing Morrowind again to get back in the swing of things because of how quickly [OpenMW]("http://openmw.sourceforge.net/jaws/") has been developing. If you use all the texture overhaul mods, unofficial patches, Tamriel Rebuilt, and so forth it is actually quite stunning. Most of these things should also work with OpenMW when it is released. OpenMW itself isn't yet playable, because NPCs, animations, and scripting have yet to be implemented. However, textures, meshes, sound, collision detection, and a basic GUI are all working, and the other stuff is on the way. The graphics will be much improved using the latest lighting, since it is based on OGRE, and the stability will be much better since it will be native on linux. The scripting engine is progressing well and will be even more powerful than original Morrowind.

In the meantime, for regular ol Morrowind there is a Morrowind Graphics Extender that allows for oblivion-like effects, but I have been unable to get it to work in WINE. It uses .NET 2.0, but it still should be able to run using winetricks. Perhaps in future versions.

All this Morrowind stuff has been able to hold me over temporarily until Oblivion and Fallout are playable.

---

### Post by unimatrix on 2009-02-11
Thanks OliW, that worked. But yeah, Oblivion without distant landscape is like YouTube without the flash plugin...

It's so sad. Looks like Wine will never be ready to do anything useful. It's always just catching up and we can only play games on Linux after a few years when everyone's already forgotten about them.

I guess I have no choice but to install Windows again.

---

### Post by frost9928 on 2009-03-04
Just to let everyone know what worked for me.

Installation of Oblivion GOTY under wine:

Very simple and works really well on my comp.

Go to the wine website and follow the instructions for adding the wine repository for Ubuntu that houses the latest version of wine 1.1.16. (Not the stable release but haven't had any problems so far.)

1. Install Wine-1.1.16 from synaptic. You may have to enable the wineHQ repo through the options.

2. Insert Oblivion GOTY DVD 1 and explore the folder to find the DXREDIST folder. Open the folder and install DirectX directly into wine using DXSETUP.exe

Note: I have read other's say in other forums that it's not a good idea to install DirectX as a whole into wine... Might be true but it worked for me.

3. When DX9 has completed it's install. Run the Setup.exe from the root folder of the GOTY DVD. If your experience is the same as mine the installer will launch and proceed as it would on Windows.

4. Run Oblivion GOTY. (If you need oldblivion like I do the setup instructions for that should be identical to the windows instructions.)

Good luck.

---

### Post by Iedenez on 2009-03-10
Can you help me, please? My game crashes when I'm trying to levelup. I've installed Ubuntu just a week ago and I'm trying to continue playing my windows saves = ) I hope someone knows the problem)


-Well I had OOO mod installed. I've turned it off and all is great.

---

### Post by kidux on 2009-03-10
> **OliW said:**
> Very unfortunate - I wish they'd just port the damned game.
Not bloody likely! With MS having the exclusive rights to this and Fallout 3's DLC, an official port won't happen in our lifetimes.

---

### Post by cbergy on 2009-03-22
Hi all,

I used the guide mentioned in the first page, and installed Oblivion easily.

My problem is that keyboard doesn't work. I tried running by emulating a virtual-desktop, and nothing changed.

Do you have any ideas here? I have wine-1.0, and Ubuntu.8.04.

---

### Post by WiseMaturin on 2009-03-22
Run into a problem. When I browse the registry editor, I get to ...Software/Wine, and then there is no Direct3D.

Should I create a listing for it, or is there something else I should have done?

---

### Post by WiseMaturin on 2009-03-23
Actually, I tried frost9928's way, and it worked better than everything else I've tried.
I haven't been able to even get wine 0.9.29, or 0.9.38, or anything earlier than 1.0 installed.
It *did* mess up on the main menu, there was no text at all except "Elder Scrolls: Oblivion". And it did crash after the main video when it zooms into the jail cell.

So I guess you still have to do all the same wine configurations and tweaks for it to work then?

Edit://
Ignore me, as I am an idiot. If I get TRULY stumped, I'll open my mouth again.

---

### Post by polo12 on 2009-04-05
I installed Oblivion yesterday and had it running fine. It would load saved games normally. 

However, today I booted it up and Oblivion crashes to my desktop mid-load of a save game. No error message or anything.

Anyone have any ideas?

:?:

---

### Post by unimatrix on 2009-04-06
Broken savegame is the first thing that comes to mind. Try loading an older savegame.
Alternatively, make sure you haven't changed the graphic settings (bloom/hdr), and if you have, change it back to how it was yesterday. It can sometimes cause savegame loading problems.

---

### Post by polo12 on 2009-04-07
I got it working. Something may be wrong with my install, but oddly enough the main menu's load button is the only one giving me that problem. For now, I have to start a new game, hit escape, and use the load button from that menu.

---

### Post by jakk337 on 2009-04-20
Hey guys, what about 9.04 ubuntu. :( I am having trouble.

---

### Post by OliW on 2009-04-21
I'm actually finding things a lot better under Jaunty. I used winetricks to install directx9, set the suggested registry settings and it plays pretty well.

Both how it looks and the speed it does that are a little disappointing but it's understandable given that so much is non-native. But hopefully one day it'll just work and it'll work as well as it does on Windows.

---

### Post by jdeslip on 2009-04-21
I have a strange problem.  I installed it and everything seems fine - except my character is always walking/running forward.  I can't stop it.  I tried hitting Q to turn off "auto move", but it does nothing.  I tried changing the control for "auto move" but still now luck.  It seems that "auto move" is stuck on.  Anyone else have this problem?

---

### Post by Necis on 2009-04-21
The game freezes. right at the part where the rats first break through the wall at the beginning of the game.

I am using Ubuntu 9.04 with wine 1.1.19

---

### Post by jdeslip on 2009-04-22
OK, I figured out the solution to my "always walking forward" problem.  It only happened when I had my joystick plugged in to my PC.  It seems you can fix it by adjusting the following parameter in Oblivion.ini

bUse Joystick=0

---

### Post by DarkW0lf on 2009-04-24
> **Mongoose said:**
> 1. Fix your Nvidia driver install.
2. READ the wiki entry on how to install GotY edition, which has extra copy protection.  ;)

I am having a similar issue as bloeper except wine doesn't give an error for my nvidia card.

winecfg is set for Windows Vista and I have HKEY_LOCAL_MACHINE\System\MountedDevices listed in regedit (does there need to be a certain value).

I can use setup.exe from both the disc and iso but neither will work. I also tried installing direct x 9 before running setup.exe like another poster but got a similar error for dxsetup.exe.

System is 
Compaq Presario F572US (laptop)
AMD64 Athlon x2 
1 gb ram (will be upgraded in near future) 
xubuntu 8.04 LTS
wine 1.0.0-1 
NVIDIA 6150 (169.12 'new')

---

### Post by hardwarejunkie9 on 2009-05-04
Here's my story:

I had difficulty using the oblivion wiki method for installation due to the setup.exe not properly opening. 

I made sure to use the winetricks Direct X installation, and still no luck.

I tried to install Direct X into Wine directly as was suggested and it WORKED. I recommend adding the method as a corollary to the current install for those with a similar problem.

Now, however, I have a different issue.
The game runs spectacularly, (of course, I'm running an nvidia 9100 with 1 gig of RAM on the card). However, the TOP bar of hte screen is dominated by my ubuntu desktop interface. 
It appears to only run in the windowed mode and it blocks off the quest update information at the top, so no "You are Now Encumbered" information or feedback on the duration of spells,
any advice?

---

### Post by Outworlder on 2009-05-04
> **hardwarejunkie9 said:**
> Here's my story:

I had difficulty using the oblivion wiki method for installation due to the setup.exe not properly opening. 

I made sure to use the winetricks Direct X installation, and still no luck.

I tried to install Direct X into Wine directly as was suggested and it WORKED. I recommend adding the method as a corollary to the current install for those with a similar problem.

Now, however, I have a different issue.
The game runs spectacularly, (of course, I'm running an nvidia 9100 with 1 gig of RAM on the card). However, the TOP bar of hte screen is dominated by my ubuntu desktop interface. 
It appears to only run in the windowed mode and it blocks off the quest update information at the top, so no "You are Now Encumbered" information or feedback on the duration of spells,
any advice?

Yeah, there are solutions. Unfortunately, they are specific to your window manager, which I assume is either Metacity or Compiz.

If Compiz, add rules in the Window Decoration plugin to not show decorations, maximize and make the window fullscreen.

---

### Post by hardwarejunkie9 on 2009-05-04
How does one do that? I'm running with the basic Ubuntu Jaunty release.

---

### Post by hardwarejunkie9 on 2009-05-09
Update: Not entirely sure how to pull off the compiz trick, BUT, by alt+tab method you can take oblivion out of windowed mode and get rid of the boundary issues.

---

### Post by OliW on 2009-05-10
To get rid of the boundary issues you need to run ccsm (package: compizconfig-settings-manager). Enable Window Rules and under the Fullscreen click add.

You have multiple options but I find targeting the window title works best. If you already have something in that box, make sure you're doing an "or" add.

I run a twinview setup so I need this to work on just one screen. To do that, I launch wine in a very specified way:```
wine explorer /desktop=Oblivion,1920x1200 OblivionLauncher.exe
```

That will force Oblivion into a 1920x1200 window so alter the desktop size to fit your monitor. Make sure you run the oblivion settings doobrey or oblivion will crash. Check fullscreen and select your window's size.

And in this case, I have the following fullscreen compiz rule: ```
title=Oblivion - Wine desktop
```

---

### Post by DarkW0lf on 2009-05-16
I finally got it installed.
(64bit Repo Unshield is fixed it doesn't need a patch)

Now I have an issue with the in-game menu causing the system to crash. Whenever I try to pull it up (by default the tab key) game exits.

It also has brightness issues, I tried turning off the bloom lighting but now it's too dark. (Figure I still got some .ini/settings to finaggle)

[Edit]

If you are installing the GOTY edition, you need to extract from cab files just like Shivering Isles (the wiki in the Game of the Year section doesn't reference SI install only some reg keys, which I don't think actually affects GOTY install.)

Does anyone know how to get the SI 1.2 patch to run ? Or extract the necessary files ? SI must be patched (RefID issue). Patch runs and tells me that it can't find Oblivion.exe (reports an invalid reg or missing ini setting).

```

CPU:		Athlon 64 X2
RAM:		2 GB
OS:		Xubuntu x64 8.04 LTS
VideoCard:	Nvidia GeForce Go 6150 128MB
Driver:		169.12
Wine:		1.0.0-1 (from Synaptic)
Edition:	Game Of The Year
Renderer:	fbo

```
```

Program					Works?	Fix/Notes
setup.exe				no	Fix:unshield SI instructions
oblivion.exe				yes	
oblivionlauncher.exe			no	Crashes/Page Faults
ShiveringIsles_v1.2.0416English.exe	no	Can't find Oblivion.exe
tes_construction_set_1.2.404.exe	no	installshield error -6003
oblivion-construction-set.exe		no	installshield error -6003

Problems/Crashes		Crash?	Fix/Notes
oblivionlauncher.exe		yes	
journal				yes	Fix:bUseRefractionShader=0
exit sewers			yes	Fix:Turn LOD off, View Distance low, Resolution 640x480
                                        Or use fbo to render
journal/map (outdoors)		yes	Fix:bForce1xShaders=0
outdoor after few minutes	yes	Fix:bForce1xShaders=0 (don't set or it will crash near nirnroots)
blue/white-washed screen	no	Fix:Turn Bloom off in video settings
                                        Or clear bForce1xShaders
no starlight/torch glow		no	Fix:bForce1xShaders=0 also helps this (bloom related?)
glowing orb around Mythic Dawn	no	?? (I haven't encountered any for awhile but above may fix this)
ISO				no	dd cannot make good enough iso of disc

```

---

### Post by deh1963 on 2009-05-31
Deleted by user.

---

### Post by Muchacho_Gasolino on 2009-06-06
I've been reading over this thread and have seen some mixed messages.

I have an ATI x300, and I am using the open source (mesa/ati/radeon) drivers. Am I screwed?

I've tried using wine 0.9.38, 1.1.20, and 1.1.23. Same error in all of them. I can watch the intro movie with the king (or not, if i rename the video directory), and then it crashes right after that. I've tried installing DirectX as well as enabling and disabling most of the graphics settings.

Anyone have any suggestions?

---

### Post by DaftPyramid on 2009-06-07
For some reason I don't have an Oblivion.ini file. How can I fix this?

---

### Post by Muchacho_Gasolino on 2009-06-07
If you have run OblivionLauncher.exe before, then you have one. You may be looking in the wrong place. I believe the default settings place the file in ```
~/My Games/Oblivion
``` If you haven't, run OblivionLauncher once to create the file.

---

### Post by DaftPyramid on 2009-06-07
Thanks. You were right, I was looking in the wrong place. Everything works the way it should so far.

---

### Post by SlatzG on 2009-06-23
Well, i'm new to these forums, i've tried searching the web myself for the answer, and i've tried fixing it myself, and i've not been able to figure out why it is that when i launch Oblivion, it immediately says "The program OblivionLauncher.exe has encountered a serious problem and needs to close." and quits. Could someone help? I've run it in console to get the output and this is what i get:

wine: Unhandled page fault on read access to 0x000000a8 at address 0x7d55bab7 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x000000a8 in 32-bit code (0x7d55bab7).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7d55bab7 ESP:0032eb3c EBP:00000001 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:00000001 EBX:7d787000 ECX:00000000 EDX:00000000
 ESI:7c18caa0 EDI:0032ebe0
Stack dump:
0x0032eb3c:  b7e76480 7c18c590 b7e74ff4 0032ebf0
0x0032eb4c:  00000010 0032eb74 b7d899c5 b7e76140
0x0032eb5c:  00000000 00000000 b7dfd633 00000000
0x0032eb6c:  0032ebf0 0032ebe0 00000001 7d555b96
0x0032eb7c:  00000010 0032ebe0 7d787000 7d558aad
0x0032eb8c:  00000000 7d787000 00000000 0032ebf0
Backtrace:
=>0 0x7d55bab7 in libgl.so.1 (+0x66ab7) (0x00000001)
  1 0x00000000 (0x00000000)
0x7d55bab7: movl    0xa8(%edx),%eax
Modules:
Module    Address            Debug info    Name (102 modules)
PE      400000-  baf000    Deferred        oblivion
PE      bb0000-  dff000    Deferred        d3dx9_27
PE    18000000-18068000    Deferred        binkw32
ELF    7b800000-7b954000    Deferred        kernel32<elf>
  \-PE    7b820000-7b954000    \               kernel32
ELF    7bc00000-7bcb1000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb1000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c5dd000-7d4f5000    Deferred        libglcore.so.1
ELF    7d4f5000-7d5af000    Export          libgl.so.1
ELF    7d5af000-7d6df000    Deferred        wined3d<elf>
  \-PE    7d5c0000-7d6df000    \               wined3d
ELF    7d7a8000-7d7d9000    Deferred        d3d9<elf>
  \-PE    7d7b0000-7d7d9000    \               d3d9
ELF    7d829000-7d83e000    Deferred        midimap<elf>
  \-PE    7d830000-7d83e000    \               midimap
ELF    7d83e000-7d864000    Deferred        msacm32<elf>
  \-PE    7d840000-7d864000    \               msacm32
ELF    7d864000-7d87c000    Deferred        msacm32<elf>
  \-PE    7d870000-7d87c000    \               msacm32
ELF    7e07d000-7e083000    Deferred        libattr.so.1
ELF    7e083000-7e08a000    Deferred        libgdbm.so.3
ELF    7e08a000-7e0e9000    Deferred        libpulse.so.0
ELF    7e0f7000-7e1bf000    Deferred        libasound.so.2
ELF    7e1c1000-7e1c6000    Deferred        libcap.so.2
ELF    7e1c6000-7e1cd000    Deferred        libasound_module_pcm_pulse.so
ELF    7e1cd000-7e204000    Deferred        winealsa<elf>
  \-PE    7e1e0000-7e204000    \               winealsa
ELF    7e204000-7e237000    Deferred        uxtheme<elf>
  \-PE    7e210000-7e237000    \               uxtheme
ELF    7e237000-7e240000    Deferred        libxcursor.so.1
ELF    7e240000-7e245000    Deferred        libxfixes.so.3
ELF    7e245000-7e249000    Deferred        libxcomposite.so.1
ELF    7e249000-7e251000    Deferred        libxrandr.so.2
ELF    7e251000-7e25b000    Deferred        libxrender.so.1
ELF    7e25b000-7e261000    Deferred        libxxf86vm.so.1
ELF    7e261000-7e264000    Deferred        libxinerama.so.1
ELF    7e264000-7e285000    Deferred        imm32<elf>
  \-PE    7e270000-7e285000    \               imm32
ELF    7e285000-7e28a000    Deferred        libxdmcp.so.6
ELF    7e28a000-7e2a4000    Deferred        libxcb.so.1
ELF    7e2a4000-7e2a8000    Deferred        libxau.so.6
ELF    7e2a8000-7e2ad000    Deferred        libuuid.so.1
ELF    7e2ad000-7e39c000    Deferred        libx11.so.6
ELF    7e39c000-7e3ac000    Deferred        libxext.so.6
ELF    7e3ac000-7e3c4000    Deferred        libice.so.6
ELF    7e3c4000-7e3cd000    Deferred        libsm.so.6
ELF    7e3ce000-7e3d0000    Deferred        libnvidia-tls.so.1
ELF    7e3d0000-7e3d9000    Deferred        librt.so.1
ELF    7e3db000-7e477000    Deferred        winex11<elf>
  \-PE    7e3f0000-7e477000    \               winex11
ELF    7e4d3000-7e4fa000    Deferred        libexpat.so.1
ELF    7e4fa000-7e527000    Deferred        libfontconfig.so.1
ELF    7e527000-7e53d000    Deferred        libz.so.1
ELF    7e53d000-7e5b4000    Deferred        libfreetype.so.6
ELF    7e5b4000-7e5ca000    Deferred        libresolv.so.2
ELF    7e5d8000-7e5f8000    Deferred        iphlpapi<elf>
  \-PE    7e5e0000-7e5f8000    \               iphlpapi
ELF    7e5f8000-7e626000    Deferred        ws2_32<elf>
  \-PE    7e600000-7e626000    \               ws2_32
ELF    7e626000-7e641000    Deferred        wsock32<elf>
  \-PE    7e630000-7e641000    \               wsock32
ELF    7e641000-7e6b0000    Deferred        msvcrt<elf>
  \-PE    7e650000-7e6b0000    \               msvcrt
ELF    7e6b0000-7e6c4000    Deferred        lz32<elf>
  \-PE    7e6c0000-7e6c4000    \               lz32
ELF    7e6c4000-7e6df000    Deferred        version<elf>
  \-PE    7e6d0000-7e6df000    \               version
ELF    7e6df000-7e73d000    Deferred        shlwapi<elf>
  \-PE    7e6f0000-7e73d000    \               shlwapi
ELF    7e73d000-7e8c9000    Deferred        shell32<elf>
  \-PE    7e750000-7e8c9000    \               shell32
ELF    7e8c9000-7e916000    Deferred        dsound<elf>
  \-PE    7e8d0000-7e916000    \               dsound
ELF    7e916000-7e9ad000    Deferred        winmm<elf>
  \-PE    7e920000-7e9ad000    \               winmm
ELF    7e9ad000-7ea1a000    Deferred        rpcrt4<elf>
  \-PE    7e9c0000-7ea1a000    \               rpcrt4
ELF    7ea1a000-7eb15000    Deferred        ole32<elf>
  \-PE    7ea30000-7eb15000    \               ole32
ELF    7eb15000-7eb4e000    Deferred        dinput<elf>
  \-PE    7eb20000-7eb4e000    \               dinput
ELF    7eb4e000-7eb68000    Deferred        dinput8<elf>
  \-PE    7eb50000-7eb68000    \               dinput8
ELF    7eb68000-7ebbe000    Deferred        advapi32<elf>
  \-PE    7eb70000-7ebbe000    \               advapi32
ELF    7ebbe000-7ec5f000    Deferred        gdi32<elf>
  \-PE    7ebd0000-7ec5f000    \               gdi32
ELF    7ec5f000-7edaa000    Deferred        user32<elf>
  \-PE    7ec80000-7edaa000    \               user32
ELF    7edaa000-7ee72000    Deferred        comctl32<elf>
  \-PE    7edb0000-7ee72000    \               comctl32
ELF    7ef9c000-7efa8000    Deferred        libnss_files.so.2
ELF    7efa8000-7efb3000    Deferred        libnss_nis.so.2
ELF    7efb3000-7efcc000    Deferred        libnsl.so.1
ELF    7efcc000-7eff2000    Deferred        libm.so.6
ELF    7eff7000-7f000000    Deferred        libnss_compat.so.2
ELF    b7d12000-b7d16000    Deferred        libdl.so.2
ELF    b7d16000-b7e79000    Deferred        libc.so.6
ELF    b7e7a000-b7e93000    Deferred        libpthread.so.0
ELF    b7ea1000-b7fdc000    Deferred        libwine.so.1
ELF    b7fde000-b7ffc000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Bethesda Softworks\Oblivion\Oblivion.exe
    0000001b   15
    0000001a   15
    00000019    0
    00000009    0 <==
0000000c 
    00000015    0
    00000013    0
    00000012    0
    0000000e    0
    0000000d    0
0000000f 
    00000016    0
    00000014    0
    00000011    0
    00000010    0
00000017 
    00000018    0
Backtrace:
=>0 0x7d55bab7 in libgl.so.1 (+0x66ab7) (0x00000001)
  1 0x00000000 (0x00000000)
fixme:winmm:MMDRV_Exit Closing while ll-driver open

---

### Post by u235sentinel on 2009-06-23
> **SlatzG said:**
> Well, i'm new to these forums, i've tried searching the web myself for the answer, and i've tried fixing it myself, 


I've had nothing but trouble getting this to work with Wine but Crossover games 7.2.0 however it works nearly perfect.  Music, sound, graphics.  Nearly perfect not perfect.  It does a screen flip now and then when I'm outdoors.  Sometimes it just stops then I have to restart again (but that's rare).

I've tried for months to get it this stable under regular Wine (any version).  Some work better than other's but overall it's been tough.

Crossover games has worked every time.  Something to consider at least.

---

### Post by DarkW0lf on 2009-07-09
I found switching to fbo foxes screen flips and aborts.

And launcher will not run under wine but run oblivion.exe directly and the game works.

I am trying to figure out the crash when I walk near nirnroots and the graphic glitches around npc summons (black cylinder around monsters or glowing orb around assassins)

---

### Post by JH9234 on 2009-07-29
When i try to run oblivion it brings up the startup screen then when i click play it crashes to desktop, there r no error messages, what can i do?

---

### Post by OliW on 2009-07-29
> **JH9234 said:**
> When i try to run oblivion it brings up the startup screen then when i click play it crashes to desktop, there r no error messages, what can i do?

Run it from a terminal to see the errors. Then report back.

---

### Post by slow-wave on 2009-08-11
Trying to get Oblivion to run on my little brothers laptop. The game has installed fine and runs flawlessly on the maximum graphic settings. There's only one problem: The character keeps moving, at all times, and the W-, A-, S-, and D-keys don't do anything.

I've disabled joysticks in the .ini-file but that doesn't make a difference.

Any advice?

---

### Post by Progressive on 2009-08-13
I noticed that adding the native dinput.dll file helps with keyboard and mouse issues.

---

### Post by gobberpooper on 2009-08-14
> **Progressive said:**
> I noticed that adding the native dinput.dll file helps with keyboard and mouse issues.

Where do I find that? I think many people are getting this problem. I got it today, somebody on the WineHQ reported it today, and the post above got the problem too. And it's all recently

---

### Post by fernandoc1 on 2009-10-10
I'm having some lot of trouble with the later wine versions. I have attached a print screen of what is happening with me. I'm using Ubuntu 9.04 32bit, wine-1.1.31 and a NVIDIA Driver Version 180.44.
Can someone help me?

---

### Post by beastrace91 on 2009-10-13
> **gobberpooper said:**
> Where do I find that? I think many people are getting this problem. I got it today, somebody on the WineHQ reported it today, and the post above got the problem too. And it's all recently

Where you find any native .dll file - on a Windows install.

@fernandoc1 As for your graphics issue try installing the newer nVidia driver from [here](ftp://download.nvidia.com/XFree86/Linux-x86/). The 185.xx.xx drivers are the latest "stable" ones how ever I have had good luck (and better performance) using the 190.25 beta one (I have not had time to test the 190.xx drivers higher than this, sometimes the beta drivers can cause dumps/crashes so use at your own risk)

When gaming on Linux it is important to keep up with the latest drivers as they almost always solve issues/improve performance with each release :)

Hope this helps,
~Jeff

---

### Post by DarkW0lf on 2009-11-06
I have tried disabling music and sound effects which I thought I read somewhere either here or at the uesp.net wiki was suppose to help with crashing when walking near nirnroots but that didn't help.

Is there something else to prevent nirnroot crashes ?

I also can't get to shivering isles because the island is not there (giant yellow exclaimation) I know this related to plugin.txt but I have no such file, what does plugin.txt look like so I can properly load SI ?

---

### Post by handy on 2009-11-06
If you can't get past your problems with Wine, give Codeweavers Crossover Games a go.  They have trial, so you can try it & see if it works before you need to buy, & it is quite cheap too.

They are the prime supporters of Wine.  It is where the main Wine guys get money to live on.  They are really nice people, & follow their forum very closely.

If you pose a problem you often get a reply from one of the dev's.

Quite the opposite to Transgaming's evil forum from my experience.

Last I looked Oblivion still wasn't one of their supported games, but people are running it via Crossover Games, so if nothing else, you might even find help by looking in the Oblivion section of their forum.

---

### Post by DarkW0lf on 2009-11-07
The games runs and most things work but just have those two main glitches

It will crash when I approach nirnroots.
And I don't seem to be able to load plugins.

(The island for Door in Niben Bay isn't there, though I got the quest for it. And I haven't checked Anvil to see if the related Knights stuff is there.)

---

### Post by handy on 2009-11-08
> **DarkW0lf said:**
> ...
And I don't seem to be able to load plugins. 

Are you watching the case used in the names in the plugins?

Windows isn't case sensitive, so you have to be careful with the plugins, destination directory names & such.

There is a Linux bash command that would recursively turn everything in directory to whatever case you told it.  Unfortunately I can't remember the command?  Anyone? 

I wrote a how-to Oblivion mods & Linux for the UESP wiki, but someone overwrote it with a pile of over complicated windows centric rubbish.  I don't know what's there now I haven't looked for well over a year?

---

### Post by mr_raider on 2009-11-08
I seem to have an unusual problem. Everything runs fine, but the game will freeze for a second or two as soon as an enemy deteects me and enters combat mode. The same happens when the enemy dies. The rest of the time, the framerate is OK.  

Ubuntu 9.04 x64
Oblivion updated to latest patch (no expansions)
Wine. 1.1.20

Mods: 
Unofficial oblivion patch
KCAS advancement
Galerion's unarmored ACROBATICS
Better hadn to hand
BT MOd

Hardware:

AMD Athlon II 620
Nividia 9800gt
4 gigs of RAM

The problem does not seem to happen on my other desktop computer running windows 7 x64, although I remember having this probably originally in Win XP back in 2006. I don't remember how I fixed it. For reference, the desktop is a Phenom ii 920 and 8800gts (g92).

---

### Post by DarkW0lf on 2009-11-11
Game pausing when entering and leaving combat is related to music.
There was a post somewhere I read to use the native quartz.dll instead of WINE's builtin but that caused music glitches and a main menu freeze for me so I still use the builtin quartz.dll (it doesn't pause that long for me)

I fixed the issue with nirnroots. When I set bForce1xShaders,the system would crash, apperantly nirnroots need the other shaders to render.

So keep bForce1xShaders clear. Unless your hardware is really low end.
Looks like an extra GB of memory helped in my case and the game looks better (maybe a little slow but not bad).

handy or mr_raider: where is your plugins.txt stored ? In Oblivion's Program Files folder or the My Games folder ? And what case ? I think my list matches the case of the filenames but maybe I don't have plugins.txt in the right spot. Does the exe expect lowercase or uppercase (I know windows doesn't care but sometimes programs [.exe] expect one or the other). Is it just filepaths (like archiveinvalidation.txt) or does it need other info ?

mr_raider: since you list your mods and I don't know if anyone else is using any can you tell me where (relative to oblivion.exe) you keep it and the contents.

Or is plugins.txt read by OblivionLauncher.exe and not Oblivion.exe (for me the launcher won't run in WINE)

---

### Post by Drakon on 2009-11-12
Having some unusual FPS drops - I can actually get outdoors to work better than indoors. Unfortunately, I drop down to 8-11 fps indoors at its worst.
  There is no change in the bottom end(8-20 vs 8-30) in FPS between the lowest and highest graphics settings (minus HDR which is a gray screen) when indoors. (Lowest settings outdoors is smoother than lowest settings indoors, never tried highest outdoors)
  This ranges from 30 (30 feels fine) when at the entrance to an indoor area facing away from the bulk of the area, to 8 (so says the TDT command, but that number feels extremely high.. its a slow slideshow) when at the entrance facing into the map.
  It feels as if it is rendering everything regardless of what is hidden behind walls.
  Fullbright helps (maybe adds 5 fps to the bottom end) but I don't see that as a very good solution.
  Oblivion ran fine on the same hardware with windows (GeForce 7600 GS, 1 gig ram, intel pentium 4 2.4 ghz, never really took note of the fps at the time).
Also have the latest patch.

Wondering if anyone else has/had a similar problem.

Edit - Oh yeah, running Jaunty 9.04 with wine version 1.1.32

---

### Post by DarkW0lf on 2009-11-13
I found that when in interior spaces bloom lighting can cause slowdowns particularly during flame effects (like fireplaces or alot of candles). Daylight or a few candles doesn't seem to cause any issue. Turning bloom off helps. What's Fullbright ? Do you mean turning the brightness up ?

Loading objects that don't appear (behind walls) can be help by adjusting fade but that will affect all objects in range.

I would also suggest another 1 GB of memory (RAM) particulary if you running on a Pentium 4.

[edit]
Duh never mind...
Found that I had putting plugins.txt in profile/Application Data/Oblivion and not profile/Local Settings/Application/Oblivion/

There is a difference and some websites don't seem to take note.
However third party plugins don't seem to load but Shivering Isles and Kuh-niggits of the Nine do. (However I do need to resurrect the two NPC's from Niben Bay, seems they dropped of the face of the Earth since the island hasn't been there).

---

### Post by mr_raider on 2009-11-14
> **DarkW0lf said:**
> 
mr_raider: since you list your mods and I don't know if anyone else is using any can you tell me where (relative to oblivion.exe) you keep it and the contents.

Or is plugins.txt read by OblivionLauncher.exe and not Oblivion.exe (for me the launcher won't run in WINE)

I put all my plugins in the Oblivion\Data folder and load them from the Oblivion launcher "Data files" option. Never had an issue. The only thing I was never able to install was OBSE. I never  touched the plugins.txt file.

---

### Post by Z_Z on 2009-11-15
Works perfectly for me.

---

### Post by DarkW0lf on 2009-11-18
Yes I know, I edited my post.

But some plugins still have glitches.
Several pieces of armor disappear when equipped with Robert's body replacers (bound gauntlets, boots, and cuirass for example) The plugin doesn't seem to do anything and I have to add like a hundred lines to archiveinvalidation.txt Several armors and boots .nifs can also cause the bound/glass cuirass or bound boots to disappear when they are added to archiveinvalidation.txt

Whenever I summon bound armor I just have arms, head and legs (no torso, hands or feet) So I removed those nifs from archiveinvalidation.txt but for some reason the hands are still an issue.

I am still having problems with trying to run the launcher and the construction set. (attached the errors below)

---

### Post by DarkW0lf on 2009-11-18
<<damn, glitchy forum double post>>

---

### Post by DarkW0lf on 2009-11-26
Of late I been having a glitch where the screen remains black as I leave from an interior to an exterior space (like from ruins/forts to outside).
There's no GUI or console available, game load screen fades out but UI does not fade back in. Music still plays during freeze.

---

### Post by beastrace91 on 2009-11-28
If the issue just started happening have you updated your Wine recently perhaps? If so I'd try reverting back to the previous version and see if this resolves your issue.

Cheers,
~Jeff

---

### Post by a!man_96 on 2009-11-28
Gonna try it through..

---

### Post by DarkW0lf on 2009-11-30
No I haven't updated wine recently.
The only updates I recall seeing in the manager were tzdata and cups related.

Recently it seems that it no longer crashes on Interior/Exterior Switch but it continues to crash when outside of towns or dungeons after about a minute or two. Only this one particular savegame(character) seems to do this, other savegames(other characters) are fine.

---

### Post by DarkW0lf on 2009-11-30
On an unrelated note, I see that OBMM,OBSE and two plugins for GIMP (.dds and normal maps[.nif?]) have their sources released anyone know of linux versions of these.

---

### Post by beastrace91 on 2009-11-30
If you have your music enabled can you try disabling it? I know there is an issue with the quartz.dll file that causes crashes in Morrowind/Oblivion when combat music starts. If this is the case for you it is just a simple native .dll overwrite to fix the issue.

Regards,
~Jeff

---

### Post by The Grey Wizard on 2009-12-02
Too cool

---

### Post by DarkW0lf on 2009-12-05
> **beastrace91 said:**
> If you have your music enabled can you try disabling it? I know there is an issue with the quartz.dll file that causes crashes in Morrowind/Oblivion when combat music starts. If this is the case for you it is just a simple native .dll overwrite to fix the issue.

Regards,
~Jeff

Oh no no no, it is precisely the native .dll that crashes me at the main menu. The built in quartz only seems to lag a little. Most of the cells where I crash seem to be around Aleswell or Fort Empire. I haven't noticed any combat relation to the crash. Although I guess it could be, just that it doesn't crash during all combat only in certain exterior cells.

I'll try again but music hasn't been a big deal.

[edit]
No, disabling music does not prevent crashing (tried walking to Fort Empire from Wawnet, still crashes)
[/edit]

And Drakon: try searching for a No Lights Flicker mod (it's a esm file) Doesn't help with all lights but does turn off flicker for low end systems. I tried it but it doesn't deal with pulsing lights like at Leyawin Mages Guild but does deal with torch or fire flicker. There are four light effects in CS: flicker, pulse and slow versions of each; I haven't found a plugin that turns them all off.

[edit]
Okay No Lights Flicker does seem to turn off all light effects but they are still animated (candles still flicker or pulse but not the actual light).

Frame rates don't drop as much but it still slows a little.
I don't think there is an actual animation for candle nifs in the CS, so why do they still pulse ?
[/edit]

---

### Post by DarkW0lf on 2009-12-29
I downloaded the latest driver for nvidia (turns out they just released another one after I downloaded this one, just my luck) But how do you install it ?

I know that sounds stupid but I extracted and read the docs, it wants me to exit X and run the script. That's fine but how do I exit X in Xubuntu ?

I found a failsafe terminal in the login screen but that is still an X terminal. What is the install directions expecting ? I can't login to a terminal like I can in BSD, how do you do this in Xubuntu ?

---

### Post by HarrisonNapper on 2009-12-29
You could just boot to recovery mode and go to the CLI from there -shrug-. I know there are better ways to do that, but I'm not sure which ones work in XFCE and switching to another tty and killing X is something I've only done once personally (I don't want to mess up your desktop :))

Cheers.

---

### Post by beastrace91 on 2009-12-29
> **DarkW0lf said:**
> But how do you install it ?

Press ctrl+alt+f1 when you logged into the system to get to a tty login.

Give it your login information and then run ```
sudo /etc/init.d/gdm stop
``` to kill your X server. Install the driver and then run ```
sudo /etc/init.d/gdm start
``` to kick X back online again after the installation.

Also just as a note if you have older nVidia drivers installed its a good idea to get rid of the old kernel module before install the new one, do so with **sudo rmmod nvidia**

And lastly - more information on the subject can be found on the help.ubuntu.com page for install nVidia drivers - [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

Always be sure to check there among other places before posting a question :)

Cheers,
~Jeff

---

### Post by DarkW0lf on 2010-01-12
Xubuntu uses xfce, would the command still be :
```
sudo /etc/init.d/gdm stop
```

Would there be anything else that might be specific to Xubuntu/XFCE ?

[edit]

Ok nevermind, XFCE also uses gdm. (Just wasn't sure).

But during boot system reports that 173.14 is already installed.
NVIDIA X Server Settings says I am using 190.something (I know there is newer, I haven't downloaded it yet.)
Why the different reportings ?

Appears to run much smoother but certain areas have big frame drops (Like the Sacellum of Arden-Sul).
And Dreamwalk Camp isn't there; empty space, I have stairs and then everything but a rug drops to sea level. Like the cell is missing or something. (I have been playing some in SI).
[/edit]

---

### Post by DarkW0lf on 2010-02-06
I compiled the three plugins for gimp (dds, normalmaps, hdr) okay but nifskope I am having an issue.

The package did not have a make or configure script but the install directions on niftools site says to run ./makeconfig.sh (or something like that) Has anyone built nifskope 1.0.21 ?

(windows version of nifskope also won't run in Virtual Box either, it crashes VM)

---

### Post by DarkW0lf on 2010-03-10
Just a note for the Wiki and the thread:

Some packages newer than 1.1.28 are missing a file to read mp3's and so Oblivion has no sound and is laggy.

I think the file is called winemp3.ac8.so or something like that. It needs to be in /lib32/wine (or your system's path for wine libraries).

Has anyone had much like with the CS in wine/VB ?

---

### Post by tnt533 on 2010-04-06
Followed the guide. Install went well. Game starts fine with bad audio but I can fix that when I get to it. My problem is when I try to start a new game, it just freezes. I can't get beyond the main menu.

Any thoughts?

Running Karmic 32bit
4 gigs of RAM
5600+ AMD Dual Core
8800GTX x2 but no SLI enabled as of yet
   Most current nVidia driver downloaded and installed from nVidia.com

Wine 1.0.1

---

### Post by spoons on 2010-04-06
> **tnt533 said:**
> Followed the guide. Install went well. Game starts fine with bad audio but I can fix that when I get to it. My problem is when I try to start a new game, it just freezes. I can't get beyond the main menu.

Any thoughts?

Running Karmic 32bit
4 gigs of RAM
5600+ AMD Dual Core
8800GTX x2 but no SLI enabled as of yet
   Most current nVidia driver downloaded and installed from nVidia.com

Wine 1.0.1

Try the latest version of WINE and follow the instructions at [www.winehq.org](www.winehq.org) to enable the PPA.

---

### Post by tnt533 on 2010-04-06
> **spoons said:**
> Try the latest version of WINE and follow the instructions at [www.winehq.org](www.winehq.org) to enable the PPA.


I added the ppa for the dev version of wine and updated. Now the game won't even get to the launcher screen. 

I'll start over fresh and see where it gets me.

---

### Post by tnt533 on 2010-04-06
Wine 1.1.41 had issues with installshield which prevented me from installing but after compiling 1.1.42 from source everything went well. 

The game runs but now I have all of my environmental sounds not working except the music and the common freeze just before and after combat issue.

I'll start digging tonight for resolutions. Any suggestions would be appreciated.

Thanks for the point in the right direction.

***EDIT***

The issues with short freezes surrounding combat seem to be caused by the change in audio tracks. The issue has disappeared but I'll bet it will be back. 

I still have not managed to find a solution to the lack of audio. The only sound I get is music and character voice overs. No battle sounds, footsteps, etc... I've searched quite a bit and can't seem to find someone else having the same issue.

If anyone has any insight, I would be appreciative! TIA.

Ubuntu Karmic Koala 9.10 32bit
M2N32-SLI PREMIUM Motherboard
AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
8gigs RAM
nVidia 8800GTX x2 *not SLI enabled* running driver v195.36.15
MCP55 High Definition Audio onboard nVidia

---

### Post by tnt533 on 2010-04-07
> **DarkW0lf said:**
> Just a note for the Wiki and the thread:

Some packages newer than 1.1.28 are missing a file to read mp3's and so Oblivion has no sound and is laggy.

I think the file is called winemp3.ac8.so or something like that. It needs to be in /lib32/wine (or your system's path for wine libraries).

Has anyone had much like with the CS in wine/VB ?

Do you have any more information? I searched by the file name you provided but it seems to be incorrect.

---

### Post by KruSuPhy on 2010-04-18
uhm, sorry for the revive, but i need some help if anyone can offer it. in my regedit, software > wine > there is no Direct3D, only direct is DirectSound. does anyone know what i should do?

---

### Post by DarkW0lf on 2010-04-27
> **tnt533 said:**
> Do you have any more information? I searched by the file name you provided but it seems to be incorrect.

Yes, oops.

Some packages do not have the file needed to parse mp3's.

It should be winemp3.acm.so (not sure where I got the 8 from)

Check winehq for bugs, there should be one regarding games that lost audio (oblivion being one), someone found that this file is missing from wherever your distro keeps it libraries for wine.
(/usr/lib/wine for ubuntu I think). It doesn't affect all packages but seems to affect 64bit ubuntu at least (I guess 32 bit too I don't know).

I am using wine 1.1.36 because 1.1.38 had issues even with the file added back to the directory.

Even with the file, you will still get underrun errors but all sound should still play. You will have to get the file from a package before they stopped including it.

I don't know about 1.1.41 or 1.1.42, I haven't check to see if they have been packged for download for 8.04 yet or not. Have been busy with other things. Though in an unrelated matter I have heard that 1.1.41 has fixed some audio issues but not sure if it is in relation to this particular problem.

Ubuntu is not the only distro with this problem which is why I suggested UESP make some note of it like they did with some of the other unusable versions of WINE.

---

### Post by DarkW0lf on 2010-04-27
> **KruSuPhy said:**
> uhm, sorry for the revive, but i need some help if anyone can offer it. in my regedit, software > wine > there is no Direct3D, only direct is DirectSound. does anyone know what i should do?

Yes, right click, and add new key.

---

### Post by DarkW0lf on 2010-04-27
> **tnt533 said:**
> 
The issues with short freezes surrounding combat seem to be caused by the change in audio tracks. The issue has disappeared but I'll bet it will be back. 


Some people have said the native quartz.dll helps with this.
But on my system it just makes things crash.
You could try that and see if it helps on your system.

> **tnt533 said:**
> 
I still have not managed to find a solution to the lack of audio. The only sound I get is music and character voice overs. No battle sounds, footsteps, etc... I've searched quite a bit and can't seem to find someone else having the same issue.


This is the same thing I warned about earlier.
You are missing winemp3.acm.so from /usr/lib/wine

See if you can extract it from an older package.
(Try 1.1.28, some say that is the most recent version before the file went missing).

---

### Post by BlackRat90 on 2010-05-13
> **DarkW0lf said:**
> This is the same thing I warned about earlier.
You are missing winemp3.acm.so from /usr/lib/wine

See if you can extract it from an older package.
(Try 1.1.28, some say that is the most recent version before the file went missing).

I am not missing this file but i still have this problem...

---

### Post by BlackRat90 on 2010-05-13
[http://bugs.winehq.org/show_bug.cgi?id=21609](http://bugs.winehq.org/show_bug.cgi?id=21609)

---

### Post by DarkW0lf on 2010-05-14
I am comment #22 on that bug.

Adding the file worked for me but I still get underrun errors, though all sound's play.

See also bug 20042 or 20277.

However there have been some people saying the most recent version fixes this issue, I haven't tried newer versions yet (1.1.44 is supposed to work).

---

### Post by BlackRat90 on 2010-05-17
Im using 1.1.42 perhaps i should try updating.

---

### Post by BlackRat90 on 2010-05-17
1.1.44 still doesn't work for me.

---

### Post by DarkW0lf on 2010-06-25
Blackrat have you tried making a copy of that file and copying an old one into the directory.

Maybe the file is still bork'ed ?

Are you using a 64bit machine ?

Attached is my file from xubuntu 64bit it is from WINE 1.0.0.1
I have this in the directory WINE uses for its libs.
All sounds and music work for me but I still get an underrun error
(something about ALSA pcm underrun)

I keep forgetting to download 1.1.28 and trying that file.

---

### Post by child on 2010-07-09
Hi! I'm also having trouble with getting this game to run normally even with the lowest settings. My configuration is:  Ubuntu Lucid (up to date) wine 1.2-rc6 an Intel Celeron 3.06 GHz 2 Gb DDR2 RAM and a GeForce 8600 GTS 512Mb  I've managed to install it (following the instructions of this tutorial and other tutorials, and once without them), tried with wine and wine and POL, but everytime I try, even with the lowest settings the gameplay loos more like a comic than a game.(Back in win xp it ran good on quite high settings even with the Quarl's Texture Pack installed.) If you know something that mught be helpful, please reply. Thanks!

---

### Post by spoons on 2010-07-09
Make sure in Wine's options the audio is set to Emulation, NOT full. Also make sure that vertex shaders are enabled. See if this fixes your issue.

---

### Post by jackhynes on 2010-10-25
wine-1.3.5 using Nvidia GTS 240 1GB / 3GB RAM / i7 

The game crashes when I try to load it directly and gives me: 
```
fixme:win:EnumDisplayDevicesW ((null),0,0x32ef24,0x00000000), stub!
wine: Unhandled page fault on read access to 0xffffffff at address 0x7b0a86c5 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0xffffffff in 32-bit code (0x7b0a86c5).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b0a86c5 ESP:0032ec1c EBP:00000001 EFLAGS:00210286(  R- --  I S - -P- )
 EAX:ffffffff EBX:00000000 ECX:7cae4e00 EDX:00000001
 ESI:7cc37908 EDI:00000008
Stack dump:
0x0032ec1c:  00000000 7cae4e00 7cc37908 00000001
0x0032ec2c:  b76d43c0 b76d2ff4 b76d43c0 7cae4e00
0x0032ec3c:  00000000 00000001 00000001 00000000
0x0032ec4c:  7cc37908 00000055 7cba33ac 7b0a8bb6
0x0032ec5c:  00000000 7cae4e00 7cc37908 00000001
0x0032ec6c:  00013118 00000001 00000001 00000000
Backtrace:
0x7b0a86c5: call	*%eax
Modules:
Module	Address			Debug info	Name (108 modules)
PE	  400000-  baf000	Deferred        oblivion
PE	  bb0000-  dff000	Deferred        d3dx9_27
PE	18000000-18068000	Deferred        binkw32
PE	78000000-78044000	Deferred        msvcrt
ELF	7aac0000-7b800000	Export          libglcore.so.1
ELF	7b800000-7b976000	Deferred        kernel32<elf>
  \-PE	7b810000-7b976000	\               kernel32
ELF	7bc00000-7bcba000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcba000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d1a3000-7d247000	Deferred        libgl.so.1
ELF	7d259000-7d38a000	Deferred        wined3d<elf>
  \-PE	7d260000-7d38a000	\               wined3d
ELF	7d38a000-7d3be000	Deferred        d3d9<elf>
  \-PE	7d390000-7d3be000	\               d3d9
ELF	7d3be000-7d3d4000	Deferred        midimap<elf>
  \-PE	7d3c0000-7d3d4000	\               midimap
ELF	7d3d4000-7d3fa000	Deferred        msacm32<elf>
  \-PE	7d3e0000-7d3fa000	\               msacm32
ELF	7d3fa000-7d413000	Deferred        msacm32<elf>
  \-PE	7d400000-7d413000	\               msacm32
ELF	7dc14000-7dc3c000	Deferred        libvorbis.so.0
ELF	7dc3c000-7ddb4000	Deferred        libvorbisenc.so.2
ELF	7ddb4000-7de00000	Deferred        libflac.so.8
ELF	7de00000-7de3c000	Deferred        libdbus-1.so.3
ELF	7de3c000-7dea4000	Deferred        libsndfile.so.1
ELF	7dea4000-7deee000	Deferred        libpulsecommon-0.9.21.so
ELF	7deee000-7df30000	Deferred        libpulse.so.0
ELF	7df30000-7dff6000	Deferred        libasound.so.2
ELF	7e036000-7e03d000	Deferred        libogg.so.0
ELF	7e03d000-7e046000	Deferred        libwrap.so.0
ELF	7e046000-7e054000	Deferred        libxi.so.6
ELF	7e054000-7e059000	Deferred        libxcb-atom.so.1
ELF	7e059000-7e05f000	Deferred        libxtst.so.6
ELF	7e05f000-7e062000	Deferred        libx11-xcb.so.1
ELF	7e06e000-7e074000	Deferred        libasound_module_pcm_pulse.so
ELF	7e074000-7e0ab000	Deferred        winealsa<elf>
  \-PE	7e080000-7e0ab000	\               winealsa
ELF	7e109000-7e13d000	Deferred        uxtheme<elf>
  \-PE	7e110000-7e13d000	\               uxtheme
ELF	7e13d000-7e147000	Deferred        libxcursor.so.1
ELF	7e147000-7e14d000	Deferred        libxfixes.so.3
ELF	7e14d000-7e151000	Deferred        libxcomposite.so.1
ELF	7e151000-7e159000	Deferred        libxrandr.so.2
ELF	7e159000-7e163000	Deferred        libxrender.so.1
ELF	7e163000-7e169000	Deferred        libxxf86vm.so.1
ELF	7e169000-7e16d000	Deferred        libxinerama.so.1
ELF	7e16d000-7e18e000	Deferred        imm32<elf>
  \-PE	7e170000-7e18e000	\               imm32
ELF	7e18e000-7e194000	Deferred        libxdmcp.so.6
ELF	7e194000-7e198000	Deferred        libxau.so.6
ELF	7e198000-7e1b2000	Deferred        libxcb.so.1
ELF	7e1b2000-7e1b7000	Deferred        libuuid.so.1
ELF	7e1b7000-7e2d4000	Deferred        libx11.so.6
ELF	7e2d4000-7e2e4000	Deferred        libxext.so.6
ELF	7e2e4000-7e2fd000	Deferred        libice.so.6
ELF	7e2fd000-7e306000	Deferred        libsm.so.6
ELF	7e306000-7e30f000	Deferred        librt.so.1
ELF	7e313000-7e315000	Deferred        libnvidia-tls.so.1
ELF	7e318000-7e3bf000	Deferred        winex11<elf>
  \-PE	7e330000-7e3bf000	\               winex11
ELF	7e40d000-7e434000	Deferred        libexpat.so.1
ELF	7e434000-7e464000	Deferred        libfontconfig.so.1
ELF	7e464000-7e479000	Deferred        libz.so.1
ELF	7e479000-7e4f0000	Deferred        libfreetype.so.6
ELF	7e4f0000-7e504000	Deferred        libresolv.so.2
ELF	7e516000-7e537000	Deferred        iphlpapi<elf>
  \-PE	7e520000-7e537000	\               iphlpapi
ELF	7e537000-7e567000	Deferred        ws2_32<elf>
  \-PE	7e540000-7e567000	\               ws2_32
ELF	7e567000-7e582000	Deferred        wsock32<elf>
  \-PE	7e570000-7e582000	\               wsock32
ELF	7e582000-7e5e5000	Deferred        shlwapi<elf>
  \-PE	7e590000-7e5e5000	\               shlwapi
ELF	7e5e5000-7e7d3000	Deferred        shell32<elf>
  \-PE	7e600000-7e7d3000	\               shell32
ELF	7e7d3000-7e81b000	Deferred        dsound<elf>
  \-PE	7e7e0000-7e81b000	\               dsound
ELF	7e81b000-7e8b0000	Deferred        winmm<elf>
  \-PE	7e820000-7e8b0000	\               winmm
ELF	7e8b0000-7e923000	Deferred        rpcrt4<elf>
  \-PE	7e8c0000-7e923000	\               rpcrt4
ELF	7e923000-7ea23000	Deferred        ole32<elf>
  \-PE	7e940000-7ea23000	\               ole32
ELF	7ea23000-7ea5c000	Deferred        dinput<elf>
  \-PE	7ea30000-7ea5c000	\               dinput
ELF	7ea5c000-7ea77000	Deferred        dinput8<elf>
  \-PE	7ea60000-7ea77000	\               dinput8
ELF	7ea77000-7ea90000	Deferred        version<elf>
  \-PE	7ea80000-7ea90000	\               version
ELF	7ea90000-7eaea000	Deferred        advapi32<elf>
  \-PE	7eaa0000-7eaea000	\               advapi32
ELF	7eaea000-7eb77000	Deferred        gdi32<elf>
  \-PE	7eb00000-7eb77000	\               gdi32
ELF	7eb77000-7ecaa000	Deferred        user32<elf>
  \-PE	7eb90000-7ecaa000	\               user32
ELF	7ecaa000-7ed9a000	Deferred        comctl32<elf>
  \-PE	7ecb0000-7ed9a000	\               comctl32
ELF	7ef9a000-7efa6000	Deferred        libnss_files.so.2
ELF	7efa6000-7efb1000	Deferred        libnss_nis.so.2
ELF	7efb1000-7efc8000	Deferred        libnsl.so.1
ELF	7efc8000-7efee000	Deferred        libm.so.6
ELF	7eff8000-7f000000	Deferred        libnss_compat.so.2
ELF	b7575000-b7579000	Deferred        libdl.so.2
ELF	b7579000-b76d7000	Deferred        libc.so.6
ELF	b76d8000-b76f2000	Deferred        libpthread.so.0
ELF	b7704000-b7844000	Deferred        libwine.so.1
ELF	b7846000-b7864000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Bethesda Softworks\Oblivion\Oblivion.exe
	0000001d   15
	0000001c   15
	0000001b    0
	00000009    0 <==
0000000e services.exe
	00000016    0
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000018    0
	00000017    0
	00000013    0
	00000012    0
00000019 explorer.exe
	0000001a    0
Backtrace:
fixme:winmm:MMDRV_Exit Closing while ll-driver open
err:mmtime:TIME_MMTimeStop Timer still active?!
```

The launcher opens fine but won't let me launch the game and it has been patched to the latest version. Why can't I load the game?

---

### Post by Agent_Riot on 2010-10-30
I have a minor issue running Oblivion under 9.10 karmic. Oblivion, the latest patch and the unofficial patch all install no problem. The opening menu loads and I can click "play". the company logo's load and then the OBLIVION rock logo comes in. then I see nothing but the scrolling map in the screen's center. No ES4 Oblivion above or new, load, etc... below it. And my mouse doesn't appear or work, nor does my keyboard do anything. I've updated my graphics drivers (i'm aware they can barely run Oblivion) still no luck. Wine is current, and i've followed every instruction on this page.
[http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux)

Still no luck. I have to alt+F4 or alt tab then right clk-close to get out of the program.

System is Dell XPS m1330
Graphics: intel 965gm
Using logitech usb cordless mouse (touchpad doesn't work either)
Plugging in usb keyboard is also a no-go.

On the graphics issue, i tried to contact Dell about buying the graphics card upgrade (128mb geforce) since I decided i'd like it, but you apparently can only get it during initial purchase. (boo-hoo)

Any ideas on the issue? Info will be provided as needed. 
Thanks a million.
Danny

---

### Post by Agent_Riot on 2010-10-30
Can't edit previous post. NEW INFO.
Updating Wine (I was a point or two behind in versions) allows me to load game. Menus appear and I can start a game. After the intro video, I can see the character customization to the left, but no facial image to the right. Starting the game, I can see my HUD (health, spell, crosshair, etc..), but everything else is black. I can move, even hear the voices of the mocking guy in the other cell and the guards, but I can nothing at all. Every page I read on this says it's my video card. Can anyone confirm this?

Thanks again,
Danny

---

### Post by bobwyajnr on 2010-10-30
> **Agent_Riot said:**
> Every page I read on this says it's my video card. Can anyone confirm this?

Thanks again,
Danny

Hi **Danny**

Intel don't really make 3D graphics cards. Their latest cards (under Windows) have only just caught up with proper 1080p video decode acceleration. They tend to only play older <DX8.0 3D games with (perhaps) lowered FPS/resolution - and that's on a Windows platform!! Asking an Integrated Graphics Media Accelerator X3100 to perform in WINE, on Ubuntu, is like praying for a miracle...

The long and short of it is that if you want to play demanding DX9.0c games on a GNU/Linux system you really want an Nvidia GPU (or at a push an AMD/ATI GPU). But even the optional Dell 'GeForce' (128MB Nvidia GeForce Go 8400) would be struggling with graphics heavy game like Oblivion. The 8400 is a video decode media acceleration card like the Intel one. It may be labelled as DX10.0 but it won't play any real DX10.0 games...

You have to shop around to get a laptop with a half decent GPU but things have improved dramatically (since ATI cut Nvidia to ribbons with the 4xxxM series). The new range of Dell 14"+ XPS models have quite decent Nvidia 420/425 mobility GPUs:
[Mobility GPU performance charts]("http://www.notebookcheck.net/NVIDIA-Geforce-GT-425M.34152.0.html")

big purchases = lots of research :popcorn:

Bob

---

### Post by Agent_Riot on 2010-10-30
As far as the intel goes, that figured. But i'm fine for now since I don't really have the time to play games on my laptop, not to mention I didn't really buy one for that reason. I was checking on the issue since I got the game to load that far.

If I did run a game on Wine, it'd be like Diablo 2 or something less intensive.

If I get another laptop, it may be a higher end one where i'll just wipe it and put Ubuntu on it. This one came with it preinstalled which made it easier. I checked the laptop's motherboard and there's not even a spot for the card, hence Dell saying I had to order it at time of purchase.

Thanks for the info though, Bob.

Danny

---

### Post by NightwishFan on 2010-10-30
I think minimal playable chipset with Oblivion on Linux would be a Nvidia 6 Series integrated. Which is not too bad, as Windows with such a chip struggles with Oblivion.

Intel graphics do not have required shader support yet so all you will get is a black screen. Though in Wine 1.2 it should run great. (except for the black screen and low fps :D).

---

### Post by bobwyajnr on 2010-10-30
> **Agent_Riot said:**
> 
If I get another laptop, it may be a higher end one where i'll just wipe it and put Ubuntu on it. This one came with it preinstalled which made it easier. I checked the laptop's motherboard and there's not even a spot for the card, hence Dell saying I had to order it at time of purchase.


(I am not a Dell sales rep. and have an ASUS laptop BTW!!)

I gather (from the Ubuntu UK podcast) that Dell pulled Ubuntu installed machines from their website. But I believe that you can hassle them by phone for one...

I paid a fortune just to a get an OK standard ATI 4650M laptop. Now Dell have their new XPS 15" range and cheaper... BTW lol at Nvidia's 2Gb 435 graphics card :popcorn:

Bob

---

### Post by mito551 on 2010-10-31
i'm doing a multiple posting, as far as i know. (well, other post wasn't posted by me, but still) but still, i didn't get answer from other posts.
my problem is - Oblivion doesn't save at all. it says "Save Succesful", but don't save. save file isn't being created what should i do. i suppose, this is because of permissions. can i change it, so Oblivion can create a save file?
System - Ubuntu 10.10
Wine - 1.3.6
Oblivion - clean (not GOTY, no SI, no KotN) 1.2.x

---

### Post by NightwishFan on 2010-10-31
You aren't running Wine as root are you?

---

### Post by mito551 on 2010-11-01
sudo wine where/my/oblivion/lies/OblivionLauncher ?
if i sudo that, it says that "program encountered serious problem and needs to close"

---

### Post by NightwishFan on 2010-11-01
Ok, my apologies. I was not suggesting you do that, I was merely asking. No, you should not run wine as root. If you run it as a normal user you should not have permission errors.

---

### Post by mito551 on 2010-11-01
i did login as root and oblivion did save. but it isn't convinient. is there any way to launch as root from my user?

---

### Post by NightwishFan on 2010-11-01
No, do not run wine as root it is not designed to. Just run:
```
sudo chown -R *yourusername* .wine
```

---

### Post by buzzmandt on 2010-11-01
```
sudo chown -R username:username /home/username/.wine
``` if your oblivion is in the .wine directory or can point it to the oblivion folder specifically should take care of it for you. and don't forget to enter your username where the line says username

---

### Post by mito551 on 2010-11-01
no luck. still doesnt save. only way i found is to login as root and run oblivion. any more ideas?

---

### Post by NightwishFan on 2010-11-01
It certainly saves on my end. Try deleting the .wine folder and trying again. Or install Wine from this ppa: 
[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

Just run this to install Wine ppa:
```
sudo apt-add-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get dist-upgrade
```

Never run wine as root. In fact you now have an installed oblivion under /root/.wine I would delete that wine folder there.

---

### Post by mito551 on 2010-11-01
still nothing. deleted root wine. updated with your commands. still nothing.

---

### Post by NightwishFan on 2010-11-01
Not sure what to tell you. It *should* work. Are you installing Oblivion in a nonstandard way such as a crack/iso, if so that might be why. I have successfully used Oblivion on nearly every version of Ubuntu/Wine.

---

### Post by mito551 on 2010-11-02
ok, i reinstalled wine, Oblivion. aaaaaand... suddenly! it worked! i can save now. thank you^^

---

### Post by june_cover on 2010-11-15
Hi guys.
I launch Oblivion under Ubunta 10.10 amd64 and wine 1.2.1.
It works stable, but very slow, near 10-15 fps, regardless of quality settings.
Can somebody advise me how improve performance?

My system also including Athlon64 X2 4200+, 2 GB RAM, GeForce 8800 GTS with 320 MB video memory, 260.19.21 (latest) nVidia driver.
Under Vista on this computer the Oblivion gives 25-30 fps with high quality settings.
----------------
sorry for my english

---

### Post by bobwyajnr on 2010-11-15
> **june_cover said:**
> 
Can somebody advise me how improve performance?


Wine 1.3.7? :popcorn:

Bob

---

### Post by NightwishFan on 2010-11-15
Some of these tips are no longer valid (since they are already the default) but give them a go. [http://ubuntuforums.org/showthread.php?t=349764](http://ubuntuforums.org/showthread.php?t=349764)

---

### Post by june_cover on 2010-11-16
Now i upgraded Wine to 1.3.7 and made some tweaks in Oblivion.ini.
Nothing changes. Oblivion runs with average 15 fps in outdoor locations.
However i want to believe, that it possible to reach performance closer to Windows.
Have any ideas?

----
Athlon 64 X2, 2 GB RAM, GeForce 8800 GTS 320 MB, Ubuntu 10.10 @ 64bit
----
sorry for my english

---

### Post by gunit888 on 2010-11-28
I'm trying to get Oblivion up and running myself.  I'm running Ubuntu 10.10 with Wine 1.3.8.  I've installed and patched Oblivion with the official 1.2 patch and the unofficial 3.2 patch.  I'm able to start a new game, and the intro story video will play.  However, game freezes once the video ends (whether I let it play out or skip it early with escape).  The music will play after this happens, as if I was in the jail at the start of the game.  I know my hardware is sufficient because I've played Oblivion on the same machine under Windows.  I've tried most of the tweaks I've found and nothing seems to make a difference on this issue.  Any idea what I can try to get past the lock up?

---

### Post by unelsson on 2010-12-08
Just confirming with the recent test that Oblivion works on Ubuntu 10.10 and Wine 1.2.1. I'm using Shivering Isles expansion and the newest patch. I'm also using Compiz (with effects and emerald window manager). I'm running this in a window, with a resolution of 1280x1024 or 800x600. Performance is playable and short playtest didn't crash, freeze or have any graphic glitches. Some tuning was done to make it work.

I got major crashes on the first tries. Then I installed SI, patched the game, set the resolution from Oblivion.ini. Then I was able to get to the start menu.

iSize W=1280
iSize H=1024

Other resolutions (like 800x600) seem to work also.

I also had to turn the music off from Oblivion.ini. If I didn't, I'd get as far as to the menu, but crash when starting a new game.

Some sound effects do not play (e.g. colliding into objects, throwing objects).

Some input device -related bugs occur if I keep going in between programs (alt-tab in and out).

OblivionLauncher.exe crashes if I try to go to settings.

---

### Post by cyrex on 2011-02-01
Just installed Oblivion with wine 1.3.12 on Ubuntu 10.10 32bit. It worked out of the box with no problems but the sound issue.

It was solved by changing to OSS and doing the padsp wine oblivionlauncher.exe change

I have full graphics with an nvidia 9500 with 512mb. I have full everything and i get between 30fps up to 60fps in many parts. The game looks awesome indeed.

---

### Post by Caelen on 2011-04-02
I recently switched over from windows 7 to ubuntu 10.10, and I'm trying to get Oblivion to work, amongst other things. After much poking about, playing with the synaptic package manager and software center, and more than a handful of failures before it all started working, I hit a wall. Oblivion will start, but the window is always very small, and the settings don't get saved when I exit (it always crashes when I exit the game).

Ubuntu 10.10 64 bit
Wine 1.3.16
Oblivion, SI, and all 9 DLCs, most recent patches
AMD Phenom II x6 1075T
8GB RAM
nVidia GeForce 7800GT (replacing with AMD Radeon HD6870 in the near future, for Skyrim of course)

I'm starting the game with the oblivion launcher, as I can't get the .exe to launch directly. I haven't made any changes to it, because I'm very very new to linux. I've seen mention of a "padsp wrapper" for the exe, but I don't have the slightest clue how to find it or make it. I've also come across references to a shell script, but again, I don't know how to get one of those put together either, beyond "use a text editor and save it as .sh".

I have successfully installed and run EVE Online (though there are some bugs still) and a few other windows programs, so I know wine is working at least.

I also installed python, wxpython, and the other requirements for Wrye Bash (as well as Wrye Bash itself) in preparation for Oblivion to start working, and I can't get Wrye to run either. All of it was installed in wine.

Any help would be appreciated ^^

EDIT: I've been going through [Oblivion:Linux]("http://www.uesp.net/wiki/Oblivion:Linux") to try and get things up and running, and it's leaving me with more questions, but very little in the way of answers. It's written for older versions of wine, and doesn't mention anything newer than 1.1.20. How much of this do I actually need to do to make it work? And, of course, how do I do these things?

"To get things working with PulseAudio you will need to turn off everything except OSS, have hardware acceleration to "Full", driver emulation unchecked, and change your shortcut icon to run `padsp wine ...` to run wine in the pulseaudio wrapper."

How do I make this change, and what exactly does it mean? I found the padsp manpage, but it's not making sense to me as far as what I actually have to do. Do I specify a file path for the oblivion exe? Does padsp apply to everything in wine, or just specific programs?

[Playing]("http://www.uesp.net/wiki/Oblivion:Linux#Playing.21")

Does this still work with wine 1.3? Where do I save the .sh file?

---

### Post by Ceretrea on 2011-06-06
I am having trouble understanding the advice on here in relation to the current version of Wine and what I need to do to Oblivion to get it past the main menu screen. I am brand new to Linux and Ubuntu and am really struggling to understand how to get it to work. 

I also have no idea how to install Wrye Bash under Wine either, despite searching the net for advice I am completely lost :(

---

### Post by WirrLicht on 2011-06-24
ubuntu 11.04

same problem here... something is (i guess :)  - i am new to ubuntu -) wrong with the sound. as long as there is no music/sound, oblivion and morrowind seem to work fine. but as soon as there is any soung, the games both are slowed down to zero.

my sound is nvidia mcp73 geforce 7100

and what the hell is that paspd-thing?

---

