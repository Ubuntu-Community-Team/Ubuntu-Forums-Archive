---
title: "Dungeons and Dragons Online"
date: 2008-02-08
forum: Wine
---

### Post by mad chey on 2008-02-08
Hi guys

Just wondering if anyone successfully got this working thru wine or ???

did some searching but cant seem to find a mention of this game at all

any feedback appreciated, we are playing in on dual boot xp atm but ofc would love to have it running in our regular operating system :P

regards

chey

---

### Post by ObiWan2001 on 2008-02-08
[http://lotrolinux.com/DDO/](http://lotrolinux.com/DDO/)

---

### Post by Ferrat on 2008-02-09
Update isn't working for me, says patchclient.dll is the wrong version, updated to 4.0 with manual update but still no go and can't find any other manual patches, trying to install it on a windows system now and then copy it and see if that works

Need to get a hold of the latest patchclient.dll from lotro since that is said to work with the linux patcher and DDO, just don't want to DL a 8GB+ file for a 400kb file ^^

---

### Post by Ferrat on 2008-02-10
Well it works like a charm, fullscreen is somewhat choppy but I got it running smooth on medium settings with high texture details without any problems when running a 1024x768 emulated desktop and removing the option to let Ubuntu handle the game window =) 

Haven't found anything that doesn't work yet, altho the help window is a bit messed up but you can just as well alt+tab to your browser and use the forums there

EDIT:
Did some tweaking and now I can run it at high settings with some extras turned up at 1280x1024 and still run at a constant 60+ FPS in dungeons (~30-40FPS in town), just had to turn of specular lighting because it made the screen flip up side down sometimes in some areas

---

### Post by Breetai on 2008-02-15
Okay n00b question.

The read me says 

[I]
"Compile the LotROLinux executable using

./configure
make
make install (as super user)"[/I]


Normally I just copy paste the command into the terminal and I'm off and running.  But that isn't working.  So how exactly do I compile it?

---

### Post by Ferrat on 2008-02-15
first use 

   ./configure

then 
    make 

then 
    sudo make install

---

### Post by drummingpariah on 2008-02-15
That really should be it.  Wasn't there a precompiled DDO launcher binary out there somewhere, though?

If you can't get it to compile, tell us EXACTLY what output you're getting when you try to.

---

### Post by banished_one on 2008-02-15
> **Ferrat said:**
> Update isn't working for me, says patchclient.dll is the wrong version, updated to 4.0 with manual update but still no go and can't find any other manual patches, trying to install it on a windows system now and then copy it and see if that works

Need to get a hold of the latest patchclient.dll from lotro since that is said to work with the linux patcher and DDO, just don't want to DL a 8GB+ file for a 400kb file ^^

well since you have this dll now can you share it please please (if its legal ofc)

---

### Post by Breetai on 2008-02-15
When I type in ./Configure it says
[I]
"bash: /configure: No such file or directory"[/I]

I feel I'm missing something n00bish

---

### Post by banished_one on 2008-02-16
well you have to change your directory first (using cd command in terminal)

---

### Post by Breetai on 2008-02-16
Man I really thought I was getting the hang of ths now I just feel stupid.

Tried
CD
./CONFIG
nothing

CD ./CONFIG
nothing

cd /home/login/desktop/ddo
./CONFIG
nothin

:confused:

---

### Post by Faud on 2008-02-16
You have to configure from where your files are so if your files are in your home folder then just go there so
```

cd
```takes you home so ```
/ddo
``` should take you to your ddo folder
you can then  use ```
ls
``` to check the contents of the folder you are in to make sure its there, then
```
./configure
```

---

### Post by banished_one on 2008-02-16
if you cant be sure of the adress of the file youre looking for you can get its adress by locate command, or just move the folder to your home folder so all you have to do will be

cd nameofyourfolder

./configure

make

sudo make install

(btw cd .. goes one folder up)

---

### Post by mad chey on 2008-03-21
ok ive installed ddo into wine fine

ive got the launcher thats been modified from lotro

the new launcher sees my ddo folder but im not sure what to put in the wineprefix box or even if i need to

ive searched the net and double even treble read the stuff on winehq, maybe im just missing something as its not launching

i have tried pointing the wine prefix to the dndlauncher.exe in the correct folder but nothing happens

looking forward to your learned help

ta chey

---

### Post by mad chey on 2008-03-22
I found this page and followed its instructions which are basically the same as i found before but asked for a couple of files to be moved

[http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/RPG/LOTRO-Launcher-32060.shtml](http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/RPG/LOTRO-Launcher-32060.shtml)

when i type

mono LotROLinux.run

into a terminal in my ddo directory, it activates the launcher the same as when i activate the launcher from my applications menu, i enter the password as normal and the launcher disappears and nothing happens.

so no change at all for me

i have attempted to attach a couple of screen shots, which might aid in your helping me, ive never done this to this site before so pls forgive me if i cock it up

regards  chey


ok so far in the wine prefix box i have tried

dndclient.exe
LotROLinux.run
dndlauncher.exe

ive tried putting ./ in front of them, ive also tried putting full addresses in them (folder paths)

and ive left it blank

always the same thing happens, it loads up as per the screenshot then i enter the password and click on login, something comes up under "World queue configuration read", but it literally flashes up before the whole thing closes so im not sure whats said, but i think it says "account authorised"

---

### Post by ajackson on 2008-03-23
OK first up make sure that you have version 0.7.6 as what follows relates to that version.

Once LotROLinux is installed (either by the deb or make install) run it with LotROLinux

The WINEPREFIX is one of those settings that if you don't know what it is for then you can safely ignore it (ie leave it blank) as you won't have used it. The only setting you really need to worry about is the Game Directory (which from the screenshot is ok).

You may want to change the "Save wine output" to yes, and then have a look at ~/,LotROLinux/run.log to see if you are getting an error messages that are causing the game to fail.

---

### Post by BatPenguin on 2008-03-24
> **mad chey said:**
> always the same thing happens, it loads up as per the screenshot then i enter the password and click on login, something comes up under "World queue configuration read", but it literally flashes up before the whole thing closes so im not sure whats said, but i think it says "account authorised"

Well, this is a very basic suggestion, but did you patch the game? You didn't mention anything about it, so make sure it's fully patched by running the patch option several times. For LotRO, that has caused similar problems for me. Also: do you have the Nvidia driver installed properly (as in, 3D works in other games)? If files have been copied, check permissions too. Pretty basic suggestions but I think worth mentioning since they've solved most of my problems with LotRO.

---

### Post by ajackson on 2008-03-24
> **BatPenguin said:**
> Well, this is a very basic suggestion, but did you patch the game? You didn't mention anything about it, so make sure it's fully patched by running the patch option several times.
Unless you have a copy of patchclient.dll from LotRO book 11 or book 12 (and have modified the Patch.cs file) then patching does not work for DDO as there is no patch function exposed (unless with the last big update they changed it but I doubt it).

---

### Post by mad chey on 2008-03-24
> **ajackson said:**
> Unless you have a copy of patchclient.dll from LotRO book 11 or book 12 (and have modified the Patch.cs file) then patching does not work for DDO as there is no patch function exposed (unless with the last big update they changed it but I doubt it).

As i have never played LOTRO i have no idea what book 11 or 12 is, so would anyone be able to link me the appropriate patch file that you are refering too

i have a complete install on a windows xp installation, but i am trying to work this so that i can install and play without having to do via windows, because to be truthfull i see no point in installing in windows and copying it to ubuntu when i might as well just play it on the windows install

my version of the launcher is the one you refer to, and it definately seems that i have targeted to the correct directory, i therefore conclude that it is the patching as has been suggested

---

### Post by ajackson on 2008-03-24
> **mad chey said:**
> As i have never played LOTRO i have no idea what book 11 or 12 is, so would anyone be able to link me the appropriate patch file that you are refering too
Unfortunately it is against Turbines and Codemasters terms of service to have a copy of the file available to download (I did ask them but got no reply), so I can't help you getting a copy of that file, sorry.

> my version of the launcher is the one you refer to, and it definately seems that i have targeted to the correct directory, i therefore conclude that it is the patching as has been suggested
Does the run.log file have anything useful in it? I know with LOTRO you get a black screen with a quit button in the middle of it if your files are out of date, but I don't know how DDO handles that problem.

---

### Post by mad chey on 2008-03-24
thanks for your speedy reply, im very tired atm and will look into that file to see if it has anything useful to say hopefully tomorrow

it does seem disappointing that i would have to purchase lotro and get to this book 11 thing to get the patch file i need, just to play ddo on ubuntu.

thanks

chey

---

### Post by Seraph0x on 2008-03-24
There is a full Lotro Client (with Book 11) available here:
[[COLOR="RoyalBlue"]DL from GamersShell[/COLOR]](http://www.gamershell.com/download_22627.shtml)

and here's the patchclient.dll from Book12 (EU)
[[COLOR="RoyalBlue"]DL from Rapidshare[/COLOR]](http://rapidshare.de/files/38920197/patchclient.dll.bz2.html)

---

### Post by mad chey on 2008-03-27
to let you know how im getting on

i got the patchclient.dll from lotro, and put it in my ddo folder

told the launcher to patch, it patched 39 files, i repeated the patch and it patched 1 file

then it just bypasses the patch stage as it did before, so i presumed it was done, although it hadnt patched a lot compared to what had been done in windows

i tried to login and instead of the launcher closing and getting nothing i got this error message

pls see attached image

i tried copying the dll file from my windows installation just in case the one i have over here was bad but still getting the same results

any further advice greatly appreciated

---

### Post by mad chey on 2008-03-27
yet another update

been playing with it, and mooching around on the net, googling my error messages and i needed to have a userpreferences.ini file present in my ddo folder to stop the above message coming thru

ok so ive got it to a point where the intro now runs, albeit at a very low resolution atm (didnt want to push my luck yet) but then after the cinematic it flashes up with the big blue dude and the loading bar then crashes to this error (see attachment)

and for the life of me i cannot get it to patch any more, it keeps saying that the patching is finished, ive tried using the patchclient.dll that came with the lotro book 11 and the patchclient.dll that is present after updating lotro from book 11 to current and i get the same result, tells me patching is complete

i've tried copying my dndclient.exe over from the windows install but that has made not difference to the error i am getting

i have also included an attachment of the patching process, it doesnt seem to be doing the middle commands, which it did do when it obtained the 39 and the 1 file.  basically on the line update programs, the first time i attempted to patch it said 39/39 and the second time 1/1 then nothing ever since

---

### Post by BatPenguin on 2008-03-28
> **mad chey said:**
> ok so ive got it to a point where the intro now runs, albeit at a very low resolution atm (didnt want to push my luck yet) but then after the cinematic it flashes up with the big blue dude and the loading bar then crashes to this error (see attachment)

That sounds a lot like what I was having a while back with LotRO. Check the LotRO thread a few pages back and see what I wrote. For me, this turned out to be a Wine settings problem, so check your wine config (including registry entries). For me, it was something about the ALSA config, look at the thread, I posted about what it was, don't remember now...sound emulation maybe? Anyway, try checking wine settings.

---

### Post by mad chey on 2008-03-28
cheers for that mate

i checked your posts in the other thread and apparently you checked driver emulation under alsa and that then allowed you to patch properly

well unfortunately, i have already got driver emulation under alsa checked as that is how i have wine set up for world of warcraft, ive tried it unchecked too just to make sure

i am a little sus about this latest version of wine tho, as for some reason you cannot (or at least i cannot) test the audio whilst in the audio tab of the wine config, which seems strange as i used to be able to in the old version i had.

world of warcraft still runs and has sound tho

............................................................

hmm as a test i copied all files from my windows box to here to see if i could get ddo to run, it launched perfectly fine and ran providing that i had wine configured to emulate windows 2000, it would not run whilst emulating xp, and would only run in 800x600 resolution and i got the same 131 error as before if i tried to change the resolution in game.

still tinkering ........................

---

### Post by ajackson on 2008-03-28
Rename the patchclient.dll file to something else before copying it into your DDO folder or the patch process will just overwrite it. Version 0.7.7 of LotROLinux lets you specify what the patchclient.dll file is called.

The other option you will probably need to set is the hi-res graphics to disabled as at the moment that file doesn't get patched (Turbines problem rather than something I can fix).

---

### Post by mad chey on 2008-04-02
ok i got the latest version of the launcher and now that i can define the name of the patch file, i have patching sorted

now i just have to get this error 131 thing sorted so i can play in a resolution bigger than 800x600


getting better tho eh

---

### Post by ajackson on 2008-04-03
> **mad chey said:**
> ok i got the latest version of the launcher and now that i can define the name of the patch file, i have patching sorted

now i just have to get this error 131 thing sorted so i can play in a resolution bigger than 800x600
If I've got my error codes right I think that error is OK as it will have generated a UserPrefs file for you now, edit that and change AllowFakeFullScreen to False and when you run it this time you should see the game start up properly (intro movies, etc).

---

### Post by mad chey on 2008-04-10
i seem to have buggered wine up, dont ask me how, it just stopped working, nothing will work anymore, none of the games at all, ive tried uninstalling and reinstalling to no avail, prob can fix but im gonna do a fresh install with our new release of ubuntu so i will get wine fresh then and apply all the advice and stuff i have learned then and hopefully be good to go

(fingers crossed)

---

### Post by Malvolio on 2008-04-20
Can anyone tell me how to get around "You can only run the game from the launcher program.[205]"?  I installed the game  and am using the LOTRO launcher.  I don't have a Windows install on my machine as I've entirely abandon the platform.

I also can't seem to get past updating the patch dll as, when I paste in the LOTRO dll and update the first update is for the patch dll and it keeps repeating that first update.

---

### Post by ajackson on 2008-04-21
> **Malvolio said:**
> Can anyone tell me how to get around "You can only run the game from the launcher program.[205]"?  I installed the game  and am using the LOTRO launcher.  I don't have a Windows install on my machine as I've entirely abandon the platform.

I also can't seem to get past updating the patch dll as, when I paste in the LOTRO dll and update the first update is for the patch dll and it keeps repeating that first update.

When you copy the patchclient.dll file into the DDO directory make sure it isn't called patchclient.dll, it will get overwritten if you do, ensure that under options you are specifying the correct name for that file.

After patching there should be a file called ~/.LotROLinux/patch.log, check to see if it conatins any warnings or errors.

One thing I'm not certain of is whether the LOTRO EU version of patchclient.dll works with the US version of DDO or the US version of patchclient.dll works with EU DDO (they appear to be different sizes the last time I looked).

---

### Post by Malvolio on 2008-04-21
Well, I got it to load and such, the intro is really choppy and... the game doesn't recognize my mouse and keyboard.  I can move the cursor around but the buttons don't do anything nor does pressing keys on the keyboard.  I have to close Wine in order to close the program.  I'm on a laptop using a trackball.

---

### Post by ajackson on 2008-04-21
> **Malvolio said:**
> Well, I got it to load and such, the intro is really choppy and... the game doesn't recognize my mouse and keyboard.  I can move the cursor around but the buttons don't do anything nor does pressing keys on the keyboard.  I have to close Wine in order to close the program.  I'm on a laptop using a trackball.
Check that the windows version is set to 2000 in winecfg, it does work in XP but you get a choppy into movie (on LOTRO swapping to another desktop and then back seems to cure that problem, don't know about DDO)

---

### Post by Malvolio on 2008-04-21
Wow, what a difference a year makes.  Heh.  That did it beautifully.  Thank you.

---

### Post by Malvolio on 2008-04-21
Okay, curiously enough, new problem.  DDO seems to beat the hell out of my wireless connection.  It's not an issue of ports, or rather the ports aren't att the heart of the issue.  I just seem to lose connection after a while of playing and restoring the connection often requires I quit DDO.  I've tried forwarding the ports that this one site suggested, tried running my laptop through the DMZ... nothing seems to work in the long run.  Any suggestions?

---

### Post by Malvolio on 2008-04-22
Well, I think I have the problem pegged to DDO kicking my router's ***.  I kid you not.  A couple hours of DDO and my router tosses over, refusing to allow a stable wireless connection.  I've even set DDO's connection speed to 104 kbps and it's not helped at all (54 is dial-up speed).

---

### Post by Malvolio on 2008-04-26
Noone else having this problem with the router?  My router is a Linksys WRT54g.

---

### Post by ajackson on 2008-04-27
> **Malvolio said:**
> Noone else having this problem with the router?  My router is a Linksys WRT54g.
Don't know if it is the same problem but there is a bug for LOTRO ([http://bugs.winehq.org/show_bug.cgi?id=12302]("http://bugs.winehq.org/show_bug.cgi?id=12302")), to do with lag.

Comment 23 say to try running (as root):
```
ethtool -K eth0 tx off
```
Changing eth0 to the correct network interface. I've not tried it yet but a couple of people say it has helped.

---

### Post by Malvolio on 2008-04-28
Well, I solved the router problem.  Turned out I didn't have QoS turned on.  But now I can't seem to chat in any channels outside tells.  I have opened the ports on my router that another forum suggested but it didn't work.  I even set the net port in UserPreferences.ini to 9000.  I'm at a loss as to what to do next.

---

### Post by Malvolio on 2008-04-29
And in upgrading Ubuntu to Hardy I've broken the game entirely.  Now it doesn't even load in Wine.

Append: Turns out the answer to this one was posted, I should read more threads.

---

### Post by valczir on 2008-05-01
I'm having the same old chat issue, and I can't seem to find the right google search terms to get any ideas as to how to fix them.  I've tried with wine versions 0.57, 0.58, and 0.60 (0.59 had an insane amount of errors - I couldn't even successfully run wineboot)

I've got the following registry keys, under HKEY_CURRENT_USER\Software\Wine\Direct3D set:
UseGLSL=enabled
DirectDrawRenderer=opengl
VideoMemorySize=256

I'm got wine set to run DDO with Windows 2000 settings.

From what I can tell, some people have fixed this issue - does anyone have any suggestions for me?

Oh, and for those of you who play, I'm formerly Valczir Darkvein from the Ghallanda server.  My current characters are Blecoeth Ripjaw (the barbarian), Gallidrien (the wizard), and Gethre (the rogue).  Valczir Darkvein will be making a sudden return either when monks are added, or when half-orcs are added - I'm not sure which, quite yet.

---

### Post by mad chey on 2008-05-01
im on the devourer server, Lynzza, Zavinia, Tzian are my main chars, and very proudly i am founder of the No Rush Dungeon Explorers

maybe see you on sometime

---

### Post by valczir on 2008-05-10
So... No one has help for me, eh?

---

### Post by Dwarrel on 2008-07-13
> **Malvolio said:**
> Well, I got it to load and such, the intro is really choppy and... the game doesn't recognize my mouse and keyboard.  I can move the cursor around but the buttons don't do anything nor does pressing keys on the keyboard.  I have to close Wine in order to close the program.  I'm on a laptop using a trackball.

Ive got the 205 error to. But i cant find anyone else who had it, so could you post how you fixed the error?

Got it fixed for me. If you get the 205 error it might be that your client is not uptodate. Try to patch the client.

---

### Post by glayo on 2008-07-24
I've got the update running and the launcher running but i get the US servers NOT the european as i wish .. where have i've done wrong ? what to do ? .. please reply quick ;)

Glayo

---

### Post by ajackson on 2008-07-24
> **glayo said:**
> I've got the update running and the launcher running but i get the US servers NOT the european as i wish .. where have i've done wrong ? what to do ? .. please reply quick ;)
Please don't demand quick responses (I don't care if you stuck a smiley at the end), all it does is get you ignored and your question goes unanswered.

As for the answer, well..............

---

### Post by glayo on 2008-07-24
Ok . got thru the problem , it patches and i can see the EU server/worlds. i can login and the startscreen shows.. then it crashes with an error 201 files are not found or you dont have the right auterization.. 

some files are created during the run , for example the .launcher/WorldQuene.config
and that file is Read only. it deletes with each run so it dosn't help to change the auth. manually

Question 1.
How can i make the file read and writeable 

Question 2
Is there something else im doing wrong?

/Glayo

---

### Post by Lordrath on 2008-08-08
I am having a similar problem, I Have a Dell E510 all usb setup (because there arent any ps/2 ports on the box at all. When I start up DDO I cannot get fullscreen, the introduction video is real choppy, and when I get to the character selection screen, my mouse moves around but none of the buttons will input as well as my keyboard, I receive no errors of any kind, (I found the best way to install this without any problems is to install the game and update it on a windows drive and copy the files over.) Anyway back to the problem, no input of any kind on keyboard and limited imput on mouse with no fullscreen and choppy intro video. I will tinker with this a bit and if I come up with a good solution I will post it here immediately.

Thanks for the help in advance.

-LR

---

### Post by Lordrath on 2008-08-08
Ok, I got a general solution for the basic stuff, (keyboard, mouse, and video) 

1.Open up winecfg

2.Click on the Applications tab the go to add application.

3.Locate your dndclient.exe (by default it is going to be in ~/.wine/drive_c/Program Files/Turbine/Dungeons and Dragons Online - Stormreach)

4. Set the compatibility to Windows 2000 and apply changes.

5. Run your game

The only problem I see at the moment is that it doesn't detect voice capture devices, but I am working on a solution to that as well so stay tuned.

-LR

---

### Post by Lordrath on 2008-08-19
Ok I got ddo working with my mic now, it took me a few weeks of trial and error but basically what I gather is that DDO is not able to detect oss drivers for more than one sound card, so I had to rewrite my .asoundrc file to enable duplex for dmix. Now I have two sound cards so this wont work for everyone.

1. Open Terminal and type *aplay -l* you should get something that looks like this.

[I]**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/I]

Remember the letters in the first set of brackets [] because that is your sound driver.

Then go back to terminal and type sudo gedit ~/.asoundrc

2. Copy and Paste this into the file:

[I]# Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card0 {
type hw
card 0
device 0
}

pcm.snd_card1 {
type hw
card 1
device 0
}

# Allow mixing of multiple output streams to this device
pcm.output {
type dmix
ipc_key 1024
ipc_perm 0660 # Sound for everybody in your group!
slave.pcm "snd_card0"

slave {
# This stuff provides some fixes for latency issues.
# buffer_size should be set for your audio chipset.
period_time 0
period_size 1024
buffer_size 8192
# buffer_size 4096
# buffer_size 2048
}

bindings {
0 0
1 1
}
}

pcm.input {
type dsnoop
ipc_key 2048
slave.pcm "snd_card0"

## Possible artsd full duplex fix:
# slave {
# period_time 0
# period_size 1024
# buffer_size 8192
# }

bindings {
0 0
1 1
}
}
# Allow reading from the default device.
# Also known as record or capture.
pcm.input1 {
type dsnoop
ipc_key 2049
slave.pcm "snd_card1"

## Possible artsd full duplex fix:
slave {
period_time 0
period_size 1024
buffer_size 8192
# buffer_size 4096
# buffer_size 2048
}

bindings {
0 0
1 1
}
}
# This is what we want as our default device
# a fully duplex (read/write) audio device.
pcm.duplex {
type asym
playback.pcm "**Primary Sound Driver (Sound device 0)**"
capture.pcm "**Secondary Sound Driver (Sound device 1)**"
# capture.pcm "input1"
}

###################
# CONVERSION PLUG #
###################
# Setting the default pcm device allows the conversion
# rate to be selected on the fly.
# duplex mode allows any alsa enabled app to read/write
# to the dmix plug (Fixes a problem with wine).
pcm.!default {
type plug
slave.pcm "duplex"
}
########
# AOSS #
########
# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)
pcm.dsp0 {
type plug
slave.pcm "output"
}

#
pcm.dsp1 {
type plug
slave.pcm "output1"
}
[/I]

Please take note of the bold lettering, you will have to change those two values to the driver of the sound devices you discovered in step 1.

3. Go to System - Preferences - Sound and change all the sound devices to ALSA (not sure if there are any consequences for not doing this but I usually do it anyway.)

4. Go back to your terminal and type winecfg

5. Click on the audio tab and go to alsa and see if the names of your sound cards are under the Waveout and Wavein.

6. Then you should be able to start up DDO and go to your audio options and both sound cards will be detected under the advanced audio button.

(Dont forget to check and make sure all your sound is turned up in ubuntu or your mic will not work and you will spend the next two days banging your head on the desk trying to figure it out.)

Thats it kiddies good luck and happy gaming

-LR

---

### Post by ashiruni on 2009-11-09
I'm getting a rather confusing error. I've got pylotro running and patching fine, but when I attempt to login I get this error:

```

err:menubuilder:WinMain unknown option -a
err:menubuilder:WinMain unknown option -r

Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !

```

this last line repeats for a long while, approximately 150 lines, as the program attempts to bypass OpenGL. It closes out with:

```

err:wgl:X11DRV_ChoosePixelFormat No libGL on this box - disabling OpenGL support !
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl

*** Finished ***

```

Anybody know what's going on?

---

### Post by Fentekreel on 2009-11-20
Does anyone know where to get the installer script?  the DDO page is no longer there.

---

### Post by Toffeeapple on 2009-11-20
I use [this]("http://www.lotrolinux.com/pylotro-setup.exe") to patch and launch both LOTR and DDO. You install it like any other windows app to the prefix that you have DDO or LOTR. Or if you don't have them installed in a separate prefix (I heartily recommend that you do) then your basic default wine setup.

Old command line launcher can be found [here]("http://www.bmx-chemnitz.de/~mfr/LOTRO/").

And [PyLotRO]("http://www.lotrolinux.com/download.php") which need python and Qt4 and pyQt4 can be found here with instructions for adding it to ubuntu repository.

Personally I find the first option to be the most simple and easy.

Hope that helps.

---

### Post by pappo on 2009-12-30
I have just reloaded Ubuntu (9.04) onto a PC that would not run Windows7 and I am a DDO player (Khyber server).
I have DDO on a laptop but I want to install it on my desktop but with Linux.

Has anyone posted a step-by-step method for running DDO under Ubuntu?
I have wine, python, qt4 all installed.

Do I need to install the Turbine Download Manager first, or can I just copy the DDO folder from my laptop which does have DDO running under win7?

Any help would be appreciated.

---

### Post by Drakmor on 2010-01-03
Hey, I've followed the instructions on the wine app DB, and it works up to the point of launching. It says the following: Hardware texture compression support was not detected. This video card feature is required to run the game. [129]
I don't have a fancy graphics card, but it worked on windoes xp for me on the same computer. Any ideas?

---

### Post by pappo on 2010-01-03
> **Drakmor said:**
> Hey, I've followed the instructions on the wine app DB, and it works up to the point of launching. It says the following: Hardware texture compression support was not detected. This video card feature is required to run the game. [129]
I don't have a fancy graphics card, but it worked on windoes xp for me on the same computer. Any ideas?

The same thing happened to me.  I am getting error 129 - texture compression....etc..  I was running DDO on this PC under XP and then Windows 7 with no problems.
I don't know if this is something that DirectX does and maybe we need to install that, but I have read about DirectX installs on Linux causing a lot of problems.
Anyone out there with a solution ?? It would be appreciated.

---

### Post by Drakmor on 2010-01-08
Maybe you need a graphics card driver..... also, are you using the linux or wine version of PyLotRO. I'm running the wine version, if I knew how to use the linux one I would, but maybe it's that.

EDIT: Also, I was looking in my wine registry for the direct 3d key so I could change the video memory or whatever, but I didn't see anything about direct 3d.... that may be a problem.

---

### Post by checksquid on 2010-01-13
I was also getting the texture compression error 129. Installing the proprietary driver for my graphics card fixed it. I have an NVidia card in a Lenovo T61 laptop. Hope that's helpful to someone!

---

### Post by pappo on 2010-01-13
> **checksquid said:**
> I was also getting the texture compression error 129. Installing the proprietary driver for my graphics card fixed it. I have an NVidia card in a Lenovo T61 laptop. Hope that's helpful to someone!

I will try that.  I am not sure what driver to use.  I am using motherboard graphics.
I have the following, as show by lspci:

VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

I used this same MB when I was running DDO under Windows XP.  I will have to check the forums to see which driver is the proprietary one for this chip.

Thanks for the response.

---

### Post by neuthral on 2010-02-14
I got this working under Ubuntu Hardy, but seem to get only about 10-fps in game when i got around 50fps in winXP, i tried with both ati propertiary drivers and Envy drivers and get about 700 fps in _glxgears_ 

I have Intel celeron 3.0Ghz, 2gb Ram, ati HD4350.

Plz help me.

---

### Post by pappo on 2010-02-14
> **neuthral said:**
> I got this working under Ubuntu Hardy, but seem to get only about 10-fps in game when i got around 50fps in winXP, i tried with both ati propertiary drivers and Envy drivers and get about 700 fps in _glxgears_ 

I have Intel celeron 3.0Ghz, 2gb Ram, ati HD4350.

Plz help me.

Can you explain how you got it working ?  I can't get by getting error 129 all the time ?
I used the LOTRO install, as previously recommended, and all that went well.   Only when I try to start the game I always get the video error 129.

---

### Post by neuthral on 2010-02-14
> **pappo said:**
> Can you explain how you got it working ?  I can't get by getting error 129 all the time ?
I used the LOTRO install, as previously recommended, and all that went well.   Only when I try to start the game I always get the video error 129.

I installed wine 1.0.1 from synaptic.
I installed DDO in wine (over my winXP install) and then complied the LotRO client, i even installed DirectX 9c in wine-doors but still no good fps..

---

### Post by hxcobd on 2010-02-14
Mal, I've had a similar issue with a Linksys WRT54G router just eventually dying after having to serve up a gaming/torrent connection for a while.

I tried to troubleshoot it for literally weeks, even installed DD-WRT, and nothing helped it.

I chalked it up to Linksys routers being garbage. I bought a Belkin instead and haven't had a single issue since.

I've owned 2-3 Linksys routers now and will never buy one again. Absolute garbage products.

---

### Post by ajackson on 2010-02-15
> **pappo said:**
> Can you explain how you got it working ?  I can't get by getting error 129 all the time ?
I used the LOTRO install, as previously recommended, and all that went well.   Only when I try to start the game I always get the video error 129.
It's been said in this thread (and the LotRO one) quite often, the only people who are having any joy use NVidia or ATI graphics cards, the Intel drivers are pretty rubbish at the moment. Until that changes you will not get much joy out of gaming under wine.

---

### Post by pappo on 2010-02-15
> **ajackson said:**
> It's been said in this thread (and the LotRO one) quite often, the only people who are having any joy use NVidia or ATI graphics cards, the Intel drivers are pretty rubbish at the moment. Until that changes you will not get much joy out of gaming under wine.

ajackson - thanks.  you are right.  I need to get my old nVidia card out, install it, and see if that makes the difference.
My system is a Dell OptiPlex GX280 and it has PCIe slots, so I just need to get an inexpensive nVidia or ATI card, disable the motherboard video, and try DDO with Wine again.

I'll be back to let everyone know if that was the fix.

---

### Post by Rumbl3 on 2010-02-15
AL lib: alAuxEffectSlot.c:507: alcDestroyContext(): deleting 1 AuxiliaryEffectSlot(s)

AL lib: alEffect.c:1167: exit(): deleting 1 Effect(s)

*** Finished ***

This is what i get when i try to run it. I get to the game video go past that runs like butter gets to the part says it's connecting to the server or authenticating or whatever. Game freezes and i get a game error that i have to alt-tab and hit enter to close the game. 

Then that comes up in launch game- wine output

Anyone have a clue what that means?

games updated and stuff. I followed the directions on winehq.org

---

### Post by Ferrat on 2010-02-16
> **Rumbl3 said:**
> AL lib: alAuxEffectSlot.c:507: alcDestroyContext(): deleting 1 AuxiliaryEffectSlot(s)

AL lib: alEffect.c:1167: exit(): deleting 1 Effect(s)

*** Finished ***

This is what i get when i try to run it. I get to the game video go past that runs like butter gets to the part says it's connecting to the server or authenticating or whatever. Game freezes and i get a game error that i have to alt-tab and hit enter to close the game. 

Then that comes up in launch game- wine output

Anyone have a clue what that means?

games updated and stuff. I followed the directions on winehq.org

Using AL for audio? 
open a terminal, type 
```
winecfg
```
click audio tab and select ALSA, if that doesn't then try OSS

---

### Post by nanderv on 2010-03-15
Hi,

I installed the game, didn't apply the patch, and installed the wine version of the launcher. The game worked, but under low quality instead of the high I get on windows. But that's not the worst, the worst is that once I enter stormwrench city, my client says 'finished' and once opened again I get the pub, but not the harbour, the harbour just gives me 'finished'. Is there a work-around for this? I have a pretty new middle-end nVidia card, so support shouldn't be the problem.

---

### Post by beerthirty on 2010-04-10
> **nanderv said:**
> Hi,

I installed the game, didn't apply the patch, and installed the wine version of the launcher. The game worked, but under low quality instead of the high I get on windows. But that's not the worst, the worst is that once I enter stormwrench city, my client says 'finished' and once opened again I get the pub, but not the harbour, the harbour just gives me 'finished'. Is there a work-around for this? I have a pretty new middle-end nVidia card, so support shouldn't be the problem.

I have the same problem with DDO closing and displaying Finished.  It's showed up at the most inopportune times also.. in the middle of the shroud and when main-tanking Horoth.  I'm running Karmic with Wine 1.1.42 (this also happened with the last stable release of Wine).  I made the switch over to Ubuntu from XP and have played about 5 days on it.  It generally crashes like said above once or twice while playing for 4-5 hours. 

Also running on an NVidia (GTS250).  I'm interested in debugging it, but I still pretty green and could use some pointers.

---

### Post by barryman5000 on 2010-04-15
Hey guys, I too was getting the texture compression error.  I fixed the problem by downloading driconf.

```
sudo apt-get install driconf
```

It will then show up under your System menu as 3d acceleration options or something like that (not on that computer right now).

Then you just set the compression option to yes.

After doing this the game works great!!

---

### Post by neuthral on 2010-07-20
Ok, i changed to a Nvidia card and reinstalled ubuntu lucid.
Now when i run the game it wont download the latest patch, and when i try to patch trough PyLotro i get this:

wine: Call from 0x7bc49e10 to unimplemented function MSVCR71.dll.__CppXcptFilter, aborting
err:seh:setup_exception_record stack overflow 1556 bytes in thread 0027 eip 68195c2a esp 00240d1c stack 0x240000-0x241000-0x340000

---

### Post by boast on 2010-11-18
> **barryman5000 said:**
> Hey guys, I too was getting the texture compression error.  I fixed the problem by downloading driconf.

```
sudo apt-get install driconf
```

It will then show up under your System menu as 3d acceleration options or something like that (not on that computer right now).

Then you just set the compression option to yes.

After doing this the game works great!!

The graphics are a broken for some textures, but at least it launches now, thanks!!

---

### Post by Mynamesukx on 2011-06-13
So I have been trying to get DDO to work on Ubuntu 10.04 with wine 1.3.21 and I cannot seem to get it to launch. First I was getting a 129 error and would have to press <enter> on a black screen to even get back to change anything. Now it is sending me an error message in the launcher that reads...

p, li { white-space: pre-wrap; } X Error of failed request:  BadValue (integer parameter out of range for operation)
   
 Major opcode of failed request:  129 (XFree86-VidModeExtension)
   Minor opcode of failed request:  17 (XF86VidModeGetGammaRamp)
   Value in failed request:  0x5000120
   Serial number of failed request:  1263
   Current serial number in output stream:  1263
 
 *** Finished ***

I cannot seem to figure this one out. If anyone would please let me know how to fix this I would be most grateful.

---

### Post by desktorp on 2011-06-13
It could be a bad video driver.  What is your graphics situation?  Onboard or a card? Intel, Nvidia, or ATi/AMD?  Check your driver but if it's fine, you may need to hunt down some logs ..xorg log maybe? (/var/log/xorg.something.something)

---

### Post by Mynamesukx on 2011-06-14
I do not know how to do what it is that you are talking about. I know that I have netbook I believe the brand is Asus. The actual video card would be whatever comes with the lappy, so probably intergrated. How does one check the drivers in Ubuntu? Or do you mean through wine? My wine tricks drivers are just about everything that the interweb has told me I would need to play this game.

---

### Post by ajackson on 2011-06-14
If only there was a [sticky]("http://ubuntuforums.org/showthread.php?t=885111") that covered this sort of thing :)

If you have got a netbook rather than a laptop then I doubt DDO would work on it anyway.

---

