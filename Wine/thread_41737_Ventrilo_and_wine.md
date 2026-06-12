---
title: "Ventrilo and wine"
date: 2005-06-14
forum: Wine
---

### Post by endy on 2005-06-14
I'm sure I'm not alone when I say I've been trying to get ventrilo working for a while. Well today I got it working with no hastle and since a quick search here for 'ventrilo' turned up only one topic I thought I'd post what I found :D

Note: The version of wine I used was from the backports repository, I haven't tried any other version so step 1 may be unnecessary.

1. Add the extra repositores from the Unnoffical Ubuntu Guide:
```

[http://www.ubuntuguide.org/#repositories](http://www.ubuntuguide.org/#repositories)

``` 

2. Install the following packages:
```

wine (version 0.0.20050419-1~5.04ubp1)
libwine (version 0.0.20050419-1~5.04ubp1)
libwine-alsa (version 0.0.20050419-1~5.04ubp1)
cabextract

``` 

3. Download Ventrilo: 
```

[http://www.ventrilo.com/download.php](http://www.ventrilo.com/download.php) 

``` 

4. Make a directory for ventrilo and extract it:
```

mkdir ~/ventrilo
cd ~/ventrilo
cabextract /path/to/ventrilo-2.2.0-Windows-i386.exe

``` 

5. Edit the file:
```

~/.wine/drive_c/windows/system.ini

``` 

And add the following line:
```

MSACM.msgsm610=msgsm32.acm

```

6. Next you need to get your hands on the windows file 'msgsm32.acm' from an existing windows partition (C:/WINDOWS/system32/msgsm32.acm) and copy it to  '~/.wine/drive_c/windows/system/'.

7. Run vent:
```

cd ~/ventrilo
wine ./Ventrilo.exe

```

I hope it works, and I also hope I'm didn't state the obvious  :razz:

---

### Post by Snipersnest on 2005-06-14
Good howto man... But I'd perfer to Support Linux....So I use TeamSpeak

[www.goteamspeak.com]("http://www.goteamspeak.com")

If you look closely on the Vent forums theres a post there saying the guy will never release the Linux version of Vent. Mainly because hes so worried about his precious code. Supoort Linux...use TeamSpeak. Theres a new version of TeamSpeak due out soon...should blow the socks off vent with all the extras they've been talking about.

---

### Post by gil-galad on 2005-06-14
I have gotten ventrillo to work doing exactly that.  However, it is very unstable and it doesn't work with some features like hotkeys.  Teamspeak works **much** better.

---

### Post by endy on 2005-06-14
I totally agree, I have used Teamspeak for years and have loved every minute of it but recently everyone I know in clan gaming is using ventrilo.

Btw, I checked out the ventrilo homepage recently and the new forum has a linux section. However there is no news to speak of and you can't post in it but is major progress compared to what used to happen on the ventrilo site (ie mention linux and get your post flamed or ignored).

Anyway I eagerly await Teamspeak 3 and a native Ventrilo for linux, I only wish we had a GPL product in the mix but seeing as I can't code that myself I wont complain :)

---

### Post by gil-galad on 2005-06-14
Unfortunately, probably even if we had a GPL product no one would use it so it wouldn't be very useful.  If your clan is using ventrillo then you would be stuck.  What would be nice is a reverse engineer of ventrillo.  :)

---

### Post by artinla on 2005-06-27
I am confused with all of you recommending teamspeak..  As I understand it, teamspeak cannot connect to a ventrilo server.   That would mean I can only play on servers which also happen to be running a teamspeak server.  Since ventrilo is by far the most prevalent VOIP server, why would I want to do that?

---

### Post by endy on 2005-06-30
I think teamspeak is being recommended as it already has a native linux client, and it's always better to support native software first.

One note on this method is it must be very cpu intensive because everything stutters with ventrilo running when I play in game (tested ET, Quake3, Doom3) and I have an AMD64 3500+ which handles evertything else I throw at it. So this is still not real solution until we get a native binary (or source) for linux.

---

### Post by Snipersnest on 2005-06-30
[QUOTE=endy]I think teamspeak is being recommended as it already has a native linux client, and it's always better to support native software first.

One note on this method is it must be very cpu intensive because everything stutters with ventrilo running when I play in game (tested ET, Quake3, Doom3) and I have an AMD64 3500+ which handles evertything else I throw at it. So this is still not real solution until we get a native binary (or source) for linux.[/QUOTE]
 Sounds like you need to change sound cards or drivers... I had that problem with my onboard sound too. But it was the soundcard not the program.

---

### Post by endy on 2005-06-30
Hmm, thats strange cos I'm using a SB Audigy2 which I thought was well supported on linux, and works fine in all games :S

I'll check if wine needs any extra config, any other suggestions would be welcome :)

---

### Post by gil-galad on 2005-06-30
Using ventrillo through wine AND playing a game is VERY cpu intensive.  I noticed this because I overclock my cpu to various speeds.  Anything less than 2ghz on my computer, and ventrillo stutters like crazy.  Just don't use ventrillo.

---

### Post by Soulfly on 2005-07-03
[QUOTE=gil-galad]Using ventrillo through wine AND playing a game is VERY cpu intensive.  I noticed this because I overclock my cpu to various speeds.  Anything less than 2ghz on my computer, and ventrillo stutters like crazy.  Just don't use ventrillo.[/QUOTE]

Isn't that (your first sentence) a too definite statement to make after just testing it on just one setup (HW-kernel-drivers-sw-configurations) ?

---

### Post by ludzter on 2005-07-21
I need some help, my "push to talk" hotkey only works if i have ventrilo marked, so lets  say i am chatting with some friends with x-chat, then i cant talk to the people on the vent server...

---

### Post by gil-galad on 2005-07-22
[QUOTE=ludzter]I need some help, my "push to talk" hotkey only works if i have ventrilo marked, so lets  say i am chatting with some friends with x-chat, then i cant talk to the people on the vent server...[/QUOTE]
 Theres nothing you can do about that.  Push to talk only works when the window is in focus.

---

### Post by seethru on 2005-08-19
[QUOTE=gil-galad]Theres nothing you can do about that.  Push to talk only works when the window is in focus.[/QUOTE]
 not getting any sound from this, I believe I'm missing codec's.

---

### Post by Gnobody on 2005-08-19
Use Gnome Meeting!  It is SIP which is the most popular standard of VoIP.

---

### Post by IeU on 2005-08-21
[QUOTE=Gnobody]Use Gnome Meeting!  It is SIP which is the most popular standard of VoIP.[/QUOTE]

am i able to conect to ventrilo servers ?

---

### Post by zrothe on 2005-10-17
[QUOTE=IeU]am i able to conect to ventrilo servers ?[/QUOTE]


Thats priceless.

---

### Post by zrothe on 2005-10-17
[QUOTE=endy]I'm sure I'm not alone when I say I've been trying to get ventrilo working for a while. Well today I got it working with no hastle and since a quick search here for 'ventrilo' turned up only one topic I thought I'd post what I found :D

Note: The version of wine I used was from the backports repository, I haven't tried any other version so step 1 may be unnecessary.

1. Add the extra repositores from the Unnoffical Ubuntu Guide:
```

[http://www.ubuntuguide.org/#repositories](http://www.ubuntuguide.org/#repositories)

``` 

2. Install the following packages:
```

wine (version 0.0.20050419-1~5.04ubp1)
libwine (version 0.0.20050419-1~5.04ubp1)
libwine-alsa (version 0.0.20050419-1~5.04ubp1)
cabextract

``` 

3. Download Ventrilo: 
```

[http://www.ventrilo.com/download.php](http://www.ventrilo.com/download.php) 

``` 

4. Make a directory for ventrilo and extract it:
```

mkdir ~/ventrilo
cd ~/ventrilo
cabextract /path/to/ventrilo-2.2.0-Windows-i386.exe

``` 

5. Edit the file:
```

~/.wine/drive_c/windows/system.ini

``` 

And add the following line:
```

MSACM.msgsm610=msgsm32.acm

```

6. Next you need to get your hands on the windows file 'msgsm32.acm' from an existing windows partition (C:/WINDOWS/system32/msgsm32.acm) and copy it to  '~/.wine/drive_c/windows/system/'.

7. Run vent:
```

cd ~/ventrilo
wine ./Ventrilo.exe

```

I hope it works, and I also hope I'm didn't state the obvious  :razz:[/QUOTE]



I can now hear people which is GREAT! , but I still cannot talk. When I go under settings and hit monitor sometimes it says

"Codec Initialization failed: Unable to find specified codec."

Other times starts monitoring but it says "Abs Zero" over and over.

---

### Post by zrothe on 2005-10-17
I take that back, I just played around with the devices and its working. Thanks for this guide, helped me alot.


BTW I was able to get key bindings to work.

One for example was I bount insert to 'mute microphone'.

You do it the exact way you would in windows, only thing is the mouse cursor seems to get stuck in the center when you opent he bindings window. I had to tab my way to the key input field and hit insert. Then I just slung the mouse to the right and kept clicking until it finally went into that field. Then just shift+tab untill you get to the top drop down and then select mute microphone then tab to the add button and hit spacebar....wala.

---

### Post by zazeem on 2005-10-17
hi can someone help me, i got ventrilo running fine but i cant talk on it at all, i can only hear others. is there some way to enable o i can speak to them over vent??

zazeem@ubuntu:~/ventrilo$ wine ./Ventrilo.exe
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:create_server class {96749377-3391-11d2-9ee3-00c04f797396} not registered
fixme:ole:CoCreateInstance no classfactory created for CLSID {96749377-3391-11d2-9ee3-00c04f797396}, hres is 0x80040150
err:ole:CoGetClassObject class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
err:ole:create_server class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
fixme:ole:CoCreateInstance no classfactory created for CLSID {a910187f-0c7a-45ac-92cc-59edafb77b53}, hres is 0x80040150
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
err:wave:OSS_OpenDevice ioctl(/dev/dsp, SNDCTL_DSP_SETTRIGGER, 3) failed (Broken pipe)

---

### Post by zrothe on 2005-10-18
[QUOTE=zazeem]hi can someone help me, i got ventrilo running fine but i cant talk on it at all, i can only hear others. is there some way to enable o i can speak to them over vent??

zazeem@ubuntu:~/ventrilo$ wine ./Ventrilo.exe
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:create_server class {96749377-3391-11d2-9ee3-00c04f797396} not registered
fixme:ole:CoCreateInstance no classfactory created for CLSID {96749377-3391-11d2-9ee3-00c04f797396}, hres is 0x80040150
err:ole:CoGetClassObject class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
err:ole:create_server class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
fixme:ole:CoCreateInstance no classfactory created for CLSID {a910187f-0c7a-45ac-92cc-59edafb77b53}, hres is 0x80040150
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
err:wave:OSS_OpenDevice ioctl(/dev/dsp, SNDCTL_DSP_SETTRIGGER, 3) failed (Broken pipe)[/QUOTE]

Undersettings make sure you have the correct inbound and outbound devices slected, also make sure mux is on record and line is on mic.

---

### Post by zazeem on 2005-10-23
how do i set these? or wqhich onbes do i use and where do i find them??

---

### Post by wastrel on 2005-11-05
Hi, thanks for your help, this worked... to a point.

I have ventrilo up and connecting to server, and it 
does the startup sound, but I get no other sound 
from it... I have no idea where to check.

It isn't muted, and I've tried both of the options under 
"output device" in the voice tab in setup.  

I do get an error box when I connect to a server 

"Unable to initiate outbound codec (GSM 6.10 - 11 KHz, 16 bit):  Unable to find the specified codec."

Which doesn't seem to relate to hearing sound, necessarily... 
I dont have a microphone and don't care about talking.

Any ideas what I should check to fix this?

---

### Post by Snocrash on 2005-11-06
[QUOTE=Snipersnest]Good howto man... But I'd perfer to Support Linux....So I use TeamSpeak

[www.goteamspeak.com]("http://www.goteamspeak.com")

If you look closely on the Vent forums theres a post there saying the guy will never release the Linux version of Vent. Mainly because hes so worried about his precious code. Supoort Linux...use TeamSpeak. Theres a new version of TeamSpeak due out soon...should blow the socks off vent with all the extras they've been talking about.[/QUOTE]

From the Ventrilo Forums....
_________________________
Pending release

The Ventrilo / Linux client tech support forum is here pending the official release of the client.

The forum will be activated once the first release is made available.

Thank you for your support and interest in the Linux client.

At the current time we do not have an official release date. Once we do it will be posted here and possibly some indication on the download page.

--Flag
Flagship is offline   	
_________________________

Not that I don't like or use TeamSpeak....Just an FYI

-Sno

---

### Post by Tartin on 2005-11-12
[QUOTE=Snocrash]From the Ventrilo Forums....
_________________________
Pending release

The Ventrilo / Linux client tech support forum is here pending the official release of the client.

The forum will be activated once the first release is made available.

Thank you for your support and interest in the Linux client.

At the current time we do not have an official release date. Once we do it will be posted here and possibly some indication on the download page.

--Flag
Flagship is offline   	
_________________________

Not that I don't like or use TeamSpeak....Just an FYI

-Sno[/QUOTE]

They are working on the 2.3 version of a native linux client. Most people use the 2.2.4 version of it, since it uses the only free server version. Newer versions won't accept more than 8 connections...

I would gladly pay to use the new versions, but they ain't selling it to any private persons.

---

### Post by Accessed on 2005-12-10
I have managed to get ventrilo to work in SuSe. But I can only hear ppl when the setup 
window is open. LOL Unfortunately, I can't talk while the setup window is open. Anyone
have any ideas?

---

### Post by Rizado on 2006-04-04
[QUOTE=Accessed]I have managed to get ventrilo to work in SuSe. But I can only hear ppl when the setup 
window is open. LOL Unfortunately, I can't talk while the setup window is open. Anyone
have any ideas?[/QUOTE]With the latest wine versions PTT works even when ventrilo is not marked, But only when running games in wine, not native.

---

### Post by cesiel1993 on 2006-04-18
I cant find the wine directory on my comp but when I do all this: ```
cd ~/.wine
cd drive_c
cd windows
cd system
```

it manages to find it.  If you know where it could possibly be from the file directory or how to do it from the terminal please tell me :).

-CES

EDIT: FOUND IT ^^^ NVM

---

### Post by cesiel1993 on 2006-04-18
Sorry for the double post but this is totally different from my last.  Got everything setup but I cant talk because I cant set a hotkey ...is there a way to get around this ?

---

### Post by Rizado on 2006-04-19
[QUOTE=cesiel1993]Sorry for the double post but this is totally different from my last.  Got everything setup but I cant talk because I cant set a hotkey ...is there a way to get around this ?[/QUOTE]Can't set a hotkey in what way? Are your mouse stuck or something else?
Because if the mouse is stuck you have to press the mouse and tab your way to use Directinput to detect hotkey and disable it.

---

### Post by cesiel1993 on 2006-04-19
I AM SO STUPID AHHH... thx 

Problem, gets stuck in the middle of the ventrilo screen

---

### Post by Kmujo on 2006-05-02
hrm, i was fortunate enough to be a former linix user, and so happen to come back to linux using ubuntu. i've managed to setup wine, but the biggest issue seems to be that i cannot get winecfg to detect my "SBLive! Value [CT4831] (ALSA)" audio device. it seems to work fine natively, but when trying to get OSS/Esound/ALSA or NSS to find the device have just seem to baffle me, and this is the problem why i cannot speak running ventrilo under wine. the weird thing is, i can hear the connecting sounds in ventrilo but unable to hear people talk. also when going to ventrilo setup to select the default input/output audio device, it doesnt detect it.

side note: i noticed ubuntu is finding an alternate native audio driver that i dont know what exactly its for (assuming emulation) "SigmaTel STAC9721,23 (OSS Mixer)"

so if anyone can tell me how i can get wine to detect my SBLive! i think that'll solve my issue and possibly alot others.

---

### Post by -X- on 2006-05-23
If your mouse gets stuck in the middle when you're at the options screen try pushing tab a couple of times and then space to deselect "used DirectInput to detect hotkey"

---

### Post by Iskander on 2006-07-29
I need to know how to install those packages he mentioned in step 1, I new to Ubuntu and Im pretty good at it( At Least thats what I think ). Ive installed wine properlly I hope...

---

### Post by kingvicious on 2006-08-07
i get this error when i tryed what you had to do

kingvicious@kingvicious:~/ventrilo$ wine ./ventrilo-2.3.0-Windows-i386.exe
err:module:import_dll Library msi.dll (which is needed by L"c:\\windows\\system32\\msiexec.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\msiexec.exe" failed, status c0000135
kingvicious@kingvicious:~/ventrilo$
n'

any ideas?

---

### Post by Catewilliams on 2006-08-13
I'm having a problem with re-installing. For awhile, I couldn't hear anything on Vent, but everyone else could hear me. So when I couldn't fix it with my sound settings, I tried to Uninstall it. 

But now, when I click 'download' on the vent website, I open the file with wine and it doesn't actually install Vent, either I can remove it, repair it or update it. Any ideas why this is happening/how I could fix it?

---

### Post by dom02 on 2006-08-15
I've gotten it to run but when I join a server ventrilo freezes.  People see me connected to the server so it must be freezing right after I connect.  Anyone else have this problem?

---

### Post by Granden on 2006-08-18
Hi,
I have successfully setup ventrilo this way you describe in the first post.
But I got a problem after a few minutes connection time. When I speak the other dont hear me. The time for this to happen warries. So I belive it might be something about if Im quiet for a while that happens. But I dont know.

Im glad for any help because its getting a irritating not being able to speak and have to disconnect and connect again.

/granden

---

### Post by Catewilliams on 2006-08-22
> **dom02 said:**
> I've gotten it to run but when I join a server ventrilo freezes.  People see me connected to the server so it must be freezing right after I connect.  Anyone else have this problem?


I had this problem a few times, and I never found a sure fire way to fix it. All I had to do was disconnect and re connect, and if that didn't work, Un-install and Re-install. It didn't talk long, but it wasn't the best way to go about it. Also, try repairing it. If you open up the ventrilo set up file, it should have 3 options to either Repair, Remove or Modify. - Hope this helps!

---

### Post by Intangir on 2006-09-03
ive had the same problem yall have had

when i use alsa i sound fine, and i can hear fine, but after 3-10 minutes my outgoing craps out, sometimes if i hit setup it works again for a few more minutes, sometimes it doesnt fix it and i have to restart it, sometimes it just locks up completely...


if i use oss i can hear fine for hours without issue, but when i talk everyone else hears me as sounding 'really fast and broken up' its like its taking the samples from recording and playing them to fast (and running out and breaking up)

so.. i have to choose between alsa - good quality, no stability
or oss - good stability, terrible input quality

ive been using oss so everyone always complain i sound like a robot on crack

---

### Post by qwew on 2006-09-04
I've been trying to get Ventrilo to work, but I can't seem to get past the problem with the codecs. I've downloaded the .acm file that is needed, put it in the right directory and edited the system.ini file to include it, but Vent still tells me it's unable to initialise the GSM codec.

Any ideas where I'm going wrong here?

---

### Post by vitamindew on 2006-10-15
I just installed ubuntu and im trying to get ventrilo to work. I dont want to set up a server I just want to connect to one. Do I still need to do all those steps with re-naming things?

---

### Post by betadan on 2006-10-28
i would use team spek but it's kinfa hard to convince 150 othe people to use it was well just cuz i use linux

---

### Post by np1 on 2006-11-01
Well it seems that I was not only one who had problems with no hotkey working when not playing games in wine. 
Well here is program to provide workaround for this. Basically it listens keypresses from event device and  sends them to Ventrilo's window. 
You can get it from [http://np1.pp.fi/ventriloctrl/]("http://np1.pp.fi/ventriloctrl/")
Also remember to check for updates :-)

Edit: Ouh btw its source code so you need gcc etc.

Edit2: btw here is script to install Ventrilo [http://kanava.org/~hifi/linuxventrilo.sh]("http://kanava.org/~hifi/linuxventrilo.sh")


P.S. I still have problem with hearing only 1 speaker at time even with hardware mixing or other ppl muted, I wonder if there is a solution..

---

### Post by kr0n1x on 2006-11-04
i tried the linuxventrilo.sh but doesn't work...
```
pasquale@pasquale-desktop:~$ cd Desktop/
pasquale@pasquale-desktop:~/Desktop$ chmod 755 linuxventrilo.sh 
pasquale@pasquale-desktop:~/Desktop$ ./linuxventrilo.sh 
./linuxventrilo.sh: 9: Syntax error: "(" unexpected
pasquale@pasquale-desktop:~/Desktop$ sudo chmod 755 linuxventrilo.sh 
pasquale@pasquale-desktop:~/Desktop$ sudo ./linuxventrilo.sh 
./linuxventrilo.sh: 9: Syntax error: "(" unexpected
pasquale@pasquale-desktop:~/Desktop$ 
```

what is the problem? why doesn't work?](*,)

---

### Post by Katryx on 2006-11-19
> **kr0n1x said:**
> i tried the linuxventrilo.sh but doesn't work...
```
pasquale@pasquale-desktop:~$ cd Desktop/
pasquale@pasquale-desktop:~/Desktop$ chmod 755 linuxventrilo.sh 
pasquale@pasquale-desktop:~/Desktop$ ./linuxventrilo.sh 
./linuxventrilo.sh: 9: Syntax error: "(" unexpected
pasquale@pasquale-desktop:~/Desktop$ sudo chmod 755 linuxventrilo.sh 
pasquale@pasquale-desktop:~/Desktop$ sudo ./linuxventrilo.sh 
./linuxventrilo.sh: 9: Syntax error: "(" unexpected
pasquale@pasquale-desktop:~/Desktop$ 
```

what is the problem? why doesn't work?](*,)

Here's a wild guess, but maybe there's a misplaced "(" on the ninth line of the script?

---

### Post by kr0n1x on 2006-11-20
i found another archive with ventrilo already compiled..i need only to do:
cd ventrilofolder
wine ventrilo

thx anyway for reply;)

---

### Post by qrm on 2006-11-20
the program for forwarding keypresses to ventrilo works perfectly :> thanks a lot

---

### Post by surndliha on 2006-11-20
> **np1 said:**
> Well it seems that I was not only one who had problems with no hotkey working when not playing games in wine. 
Well here is program to provide workaround for this. Basically it listens keypresses from event device and  sends them to Ventrilo's window. 
You can get it from [http://np1.pp.fi/ventriloctrl/]("http://np1.pp.fi/ventriloctrl/")
Also remember to check for updates :-)

Edit: Ouh btw its source code so you need gcc etc.

Edit2: btw here is script to install Ventrilo [http://kanava.org/~hifi/linuxventrilo.sh]("http://kanava.org/~hifi/linuxventrilo.sh")


P.S. I still have problem with hearing only 1 speaker at time even with hardware mixing or other ppl muted, I wonder if there is a solution..

Dude this is the SHIIT :) tnx alot it works perfectly with my sb live 5.1 digital (SB0220) card with hardware mixing.
Can't wait for you to add mouse support tho :) Been using 4 years mouse middle button for talk button. Any info or news when it's gonna happen? a month, two, a year?

---

### Post by xstaticxgpx on 2006-11-24
i tried this, but when i go to setup under ventrilo i get a


"wavOutGetDevCaps failed." and then my mouse starts freaking out and i cant do anything, any reason why that would happen? But it does open setup, and i can join servers and i have sound... i just want to be able to change my setup and my push to talk

---

### Post by kr0n1x on 2006-11-24
disconnect from the server, set your bind etc...and next try to connect in server and check mouse problem:) i had your equal problem yesterday..

---

### Post by xstaticxgpx on 2006-11-24
it doesnt matter if im connected to a server or not.

---

### Post by Darkdelusions on 2006-12-04
I am having the same issue where my mouse freaks out connected or not connected

---

### Post by angryservoguy on 2006-12-13
> **np1 said:**
> Well it seems that I was not only one who had problems with no hotkey working when not playing games in wine. 
Well here is program to provide workaround for this. Basically it listens keypresses from event device and  sends them to Ventrilo's window. 
You can get it from [http://np1.pp.fi/ventriloctrl/]("http://np1.pp.fi/ventriloctrl/")
Also remember to check for updates :-)

Edit: Ouh btw its source code so you need gcc etc.

Edit2: btw here is script to install Ventrilo [http://kanava.org/~hifi/linuxventrilo.sh]("http://kanava.org/~hifi/linuxventrilo.sh")


Doesn't work for me, message I get is 
> Could not find Ventrilo window. Is Ventrilo running?


Despite the fact I am speaking on Vent

---

### Post by deboring21 on 2006-12-14
> **zrothe said:**
> When I go under settings and hit monitor sometimes it says

"Codec Initialization failed: Unable to find specified codec."

Other times starts monitoring but it says "Abs Zero" over and over.

I get that same message and I messed around with the device settings but still can't get it working, any ideas?

---

### Post by YaseenKriel on 2006-12-18
i am unable to install libwine-alsa option? how do i install it? Everything else installs fine.

---

### Post by Sammi on 2006-12-18
> **YaseenKriel said:**
> i am unable to install libwine-alsa option? how do i install it? Everything else installs fine.
Don't quote me on it, but I think that the package you are referring to has been incorporated into the main Wine package, so you should be fine :)

This howto is old. Someone(else than me) should update it :rolleyes:

---

### Post by YaseenKriel on 2006-12-19
thanx for the info Sammi, i used the info on wine site to get ventrilo installed, seems to be working 
will test it tonight. 

[http://appdb.winehq.org/appview.php?iVersionId=3936&iTestingId=5901](http://appdb.winehq.org/appview.php?iVersionId=3936&iTestingId=5901)

---

### Post by mb108 on 2006-12-30
Anybody tried this in Ubuntu?
[http://www.voice-overlay.info.ms/](http://www.voice-overlay.info.ms/)

It will start up in wine and will recognize that vent is up also, but when I connect to a server it dies.

Just wonderin.

---

### Post by Rizado on 2007-01-03
> **angryservoguy said:**
> Doesn't work for me, message I get is 


Despite the fact I am speaking on VentIf you use VentriloMIX it won't work. If you look at the ventrilo window you'll se it's called ventrilo 2.1.4 or something like that instead of just Ventrilo.

---

### Post by asnd16 on 2007-01-06
I can get it running but then I get the GSM codec error and I am unable to do chat but I am able to veiw who is talking but unable to hear or speak.  I can do the comments thats about it. ](*,)

---

### Post by asnd16 on 2007-01-06
I can get it running with wine but as soon as I connect to the server I get a codec error and am unable to hear others talking nor am I able to talk in return.  ](*,)

---

### Post by Rizado on 2007-02-11
> **asnd16 said:**
> I can get it running with wine but as soon as I connect to the server I get a codec error and am unable to hear others talking nor am I able to talk in return.  ](*,)You're probably missing the codec the server uses. Follow the instructions here: [http://appdb.winehq.org/appview.php?iVersionId=3936](http://appdb.winehq.org/appview.php?iVersionId=3936)
It's the ones about "MSACM.msgsm610=msgsm32.acm" you want.

However I have a problem. If two people speak at the same time I only hear the first one. Apperantly this can be fixed by checking "Use DirectSound" but this is only implemented in 2.3.0+ and I have to use 2.1.4 because of the user limitation. My guess the problem I have is this one [http://bugs.winehq.org/show_bug.cgi?id=5924](http://bugs.winehq.org/show_bug.cgi?id=5924). Got any ideas what I can do?

---

### Post by zayla on 2007-02-23
I'm on a mac and wanted push to talk to work.  So I wrote something using bits from the little program that fixed it for linux and other stuff.  The code is called "relay" and you can get it at:

[http://www.mediamax.com/attercob](http://www.mediamax.com/attercob)

---

### Post by LSparky on 2007-02-28
im gettin some errors
this shows up in the console
ALSA lib pcm_dmix.c:862:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:556:(snd_pcm_dsnoop_open) unable to open slave
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet

ventrilo is way to buggy

i was getting a wave out error when i clicked on setup
my friends cant hear me
now when i click on setup ventrilo dissapears

i think im going to switch to team speak!

---

### Post by LSparky on 2007-02-28
somebody reverse engineer a version of ventrilo for linux. 
so that we dont have to use ventrilos program in wine!
 but so we can still connect to the ventrilo network, that would be nice.

---

### Post by Sammi on 2007-02-28
> **LSparky said:**
> somebody reverse engineer a version of ventrilo for linux. 
so that we dont have to use ventrilos program in wine!
 but so we can still connect to the ventrilo network, that would be nice.
I think you need to appreciate how much work that is. You are asking for very much.

---

### Post by RAdams on 2007-03-09
This solution works great for me... EXCEPT that even with my mic cranked all the way up in the system control panel, and outbound and mic level all the way up in Ventrilo Setup, I'm STILL too quiet! What should I do about this? Also, none of the event sounds play, except the one when I disconnect from a server.

---

### Post by Sammi on 2007-03-09
In your system tray volume control application you should be able to enable something called "boost" or something. Make sure you first go to Edit -> Preferences and enable everything there, so you are sure you can see all options.

---

### Post by RAdams on 2007-03-13
> **Sammi said:**
> In your system tray volume control application you should be able to enable something called "boost" or something. Make sure you first go to Edit -> Preferences and enable everything there, so you are sure you can see all options.

I'm using Kubuntu, hence, KDE.

---

### Post by Innu on 2007-03-20
I have problem.

My voice is like robot if server uses codec GSM >= 11025hz. 8000hz is alright and Speex codec is alright too. 

err:wave:OSS_OpenDevice ioctl(/dev/dsp, SNDCTL_DSP_SETTRIGGER, 3) failed (Broken pipe)
This error comes with GSM >= 11025hz codec.

---

### Post by willskills on 2007-03-20
I would really like to know how their linux client is coming along....... I want to be able to use Ventrilo & have WoW sound at the same time.

This, in theory, should work through 'aoss' - but it doesn't. Start Ventrilo and it locks out your soundcard. Start WoW first, and then of course Ventrilo can't open your card - so, same problem.

If anyone actually has Vent running & game sound of any kind - please get in touch!

I didn't need to install ventrilo control either - I have push to talk bound to Mouse3 - works like a charm =)

---

### Post by Rizado on 2007-03-22
> **willskills said:**
> I would really like to know how their linux client is coming along....... I want to be able to use Ventrilo & have WoW sound at the same time.They aren't working on a linux client. It has been "under development" for years and it's safe to say they wont start until maybe when teamspeak 3 is released. They probably say a client is on the way because some server admins might want a cross platform solution and might choose teamspeak instead. But now a linux version is "soon" to be released and they can use that aswell.

---

### Post by Sammi on 2007-03-22
I'm really looking forward to TeamSpeak 3. It's going to kick Ventrilo's butt.

Check out this quote from the [official TeamSpeak FAQ]("http://www.goteamspeak.com/index.php?page=faq&id=2&item=58#q58"): 
> All platforms (Windows, Linux and Mac) will be 100% feature compatible and feature rich so regardless of which platform you use, all new features will be available across all platforms.Here's a development blog that explains a lot about TeamSpeak 3:
[http://www.goteamspeak.com/index.php?page=blog](http://www.goteamspeak.com/index.php?page=blog)

---

### Post by mad chey on 2007-03-29
as im a total newbie to linux and ubuntu, and therefore am not ready to do too much changing of code etc, i cannot use wine on my pc due to it being 64bit

so i cheated and am using ventrillo thru qemu, basically create an image, install windows on that image and then install and use vent, some tweaking of volumes etc to get sound right but tbh its a lot less of a headache than trying to understand all these changes to coding etc

maybe one day i will be more technically advanced and will understand what im doing to my pc instead of just aimlessley following how toos and not knowing if im about to blow my pc up 

pls dont flame this, im just trying to offer a workable alternative to someone like me who is a total newbie and finds the how toos for cedega installation confusing and far to complicated for their level atm

---

### Post by SBFC on 2007-03-29
> They aren't working on a linux client. It has been "under development" for years and it's safe to say they wont start until maybe when teamspeak 3 is released. They probably say a client is on the way because some server admins might want a cross platform solution and might choose teamspeak instead. But now a linux version is "soon" to be released and they can use that aswell.

Aye. My friends all use Vent (despite the fact I'm personally running a TS server) and so went to their site to see if they had a Linux client. I saw the 'in development' and was impressed/hopefull.

I then went to their forums and noticed the __locked__ Linux section was created back in 2005. Meh.

---

### Post by dutchman72 on 2007-03-30
If you dig deep enough into the forum for Ventrilo, you will find the authors comment on making a vent client for Linux. It's not going to happen, he does not want to open source his code. That is why it has said under development for years.

---

### Post by Sammi on 2007-03-30
They only say it's in development to shut up people who ask about it.

---

### Post by Jovec on 2007-04-04
> **dutchman72 said:**
> If you dig deep enough into the forum for Ventrilo, you will find the authors comment on making a vent client for Linux. It's not going to happen, he does not want to open source his code. That is why it has said under development for years.

It's the communities fault for running server apps for Vent (and games) that don't provide a native linux client.

---

### Post by desiredreality on 2007-04-15
when i run apt-get install i get this error is there another way like a way to build it from the sorce  ```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libasound2 (> 1.0.11) but 1.0.10-2ubuntu4 is to be installed
        Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
        Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed        Depends: libgphoto2-2 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be installed        Depends: libgphoto2-port0 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be installed
        Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
        Depends: libxml2 (>= 2.6.26) but 2.6.24.dfsg-1ubuntu1 is to be installed        Depends: libxslt1.1 (>= 1.1.17) but 1.1.15-1ubuntu1 is to be installed
E: Broken packages

```

and when i put in the version it cant find it ?

---

### Post by Jovec on 2007-05-09
Posting in case someone else may find this useful.

My Ventrilo works under Wine, with WoW running, and using the PTT key.  I am not using aoss or the PTT script/hack.  I should also note that the Linux Teamspeak client works fine for me with WoW, as long as I start TS first.

This probably won't be helpful for most of you experiencing other problems, but the error I was getting was "Unable to CreateDirectSoundBuffer" when trying to talk or use Test mode when WoW was running.  When WoW was not running, Vent worked fine for me.

Vent version: ventrilo-2.3.0-Windows-i386.exe
Wine version: wine-0.9.36
WoW version: Latest (obvioulsy)

Under System --> Preferences --> Sound, all options on the Devices tab set to ALSA.

The trick is in the loading, allowing Vent to create the necessary input buffer before WoW does (which I don't think WoW needs anyway).

1. Load Vent
2. Connect to your sever
3. Go to Setup, and start Test mode (leave it activated)
4. Start WoW
5. After WoW loads, cancel Test mode and close the settings.
6. Vent and WoW should be playing nicely.

My Vent settings are as follows: "Use DirectSound" checked wherever it appears. Hardware input Mixing set to None. "Use DirectInput to detect Hotkey' unchecked/disabled.  My PTT key is Mouse3. I also followed the Vent steps listed on the Wine App DB.

My Sound settings in winecfg are set to OSS.

---

### Post by bluewagon on 2007-05-15
how do i install ventrilctrl, i really couldnt figure it out from the readme, all it said was type ./runctrl.sh , but it doesnt tell me where to put the file, and when i do try that i get 
./runctrl.sh: 9: ./ventriloctrl: not found
or ./runctrl.sh: 9: ./ventriloctrl: no permission (or something like that)

---

### Post by hikaricore on 2007-05-15
> **bluewagon said:**
> how do i install ventrilctrl, i really couldnt figure it out from the readme, all it said was type ./runctrl.sh , but it doesnt tell me where to put the file, and when i do try that i get 
./runctrl.sh: 9: ./ventriloctrl: not found
or ./runctrl.sh: 9: ./ventriloctrl: no permission (or something like that)

[SIZE="5"]**Updated ventriloctrl with instructions thanks to calebgray: [http://www.calebgray.com/uploads/ventriloctrl/ventriloctrl-0.5.zip]("http://www.calebgray.com/uploads/ventriloctrl/ventriloctrl-0.5.zip")  ~08/23/2008**[/SIZE]

[SIZE="4"]***** The following is ancient and outdated from over a year ago and likely no longer works I'm sorry but I won't be answering private messages about my walkthrough. ***  ~06/21/2008**[/SIZE]

--Incase anyone else stumbles upon this post,
--You can download ventriloctrl here: [http://np1.pp.fi/ventriloctrl/ventriloctrl-0.3.tar.gz](http://np1.pp.fi/ventriloctrl/ventriloctrl-0.3.tar.gz)
--I've also mirrored it here just incase the creator's site is down: [http://hikaricore.googlepages.com/ventriloctrl-0.3.tar.gz](http://hikaricore.googlepages.com/ventriloctrl-0.3.tar.gz)

You need to compile ventriloctrl to run it.

Direct from the README file:
> 
Ventriloctrl
-------------
Ventriloctrl is program to send keypresses to Ventrilo client even
if it is not on top.


Requirements
------------
Event Device included in kernel
_Xorg(Xfree?) development libraries_
Reading rights for event device

Compiling
---------
make


So you will first need to install build-essential if you never have:

```
sudo apt-get install build-essential
```

Then the development libraries for Xorg (this should be enough):

```
sudo apt-get install xorg-dev
```

Then run:

```
make
```

From the directory you extracted ventrilocontrol into.

it should output something like this:

> [hikaricore@devistate:~/ventriloctrl-0.3 (.6 Mb)]$ make
gcc -Wall -O3 -o ventriloctrl ventriloctrl.c -lX11
gcc -Wall -O3 -o findkey findkey.c

If get an error, let me know I'll try and figure out what dev files I missed.

Now for configuring it, this part is fun.

You will need to find out what device your system uses for input.  For example on my system it's:

**/dev/input/event1**

Yours may differ.  So you need to run

```
**sudo** ./findkey /dev/input/event#
```

Replacing the # with numbers ranging from 0 to 6, example:

```
**sudo** ./findkey /dev/input/event0
```

Upon running this command press some keys on your keyboard, if you don't see any output in the terminal hit Ctrl+C to exit the program and try the next number.  Like I said it varries.

> 
ok I guess I was a little vague with this part, so I'm giving you an example of what it should look like:

[I][hikaricore@devistate:!]$ sudo ./findkey /dev/input/event2
key 28 state 0
key 97 state 1
key 97 state 0
key 54 state 1
key 54 state 0[/I]

Above is the output of findkey, showing:  Enterkey (up), Right Ctrl (down,up) Right Shift (down,up)

These key numbers will vary from keyboard to keyboard.

But for example if I wanted to use my right Ctrl key for ventriloctrl I would use the number 54 in the following step of the setup.  If you run findkey and only see the text you're typing out on the keyboard, you need to move on to the next device.  ^_^



Once you find the correct /dev/input/event# press the key you want to use for vent, remember the number it outputs in the terminal, then you'll need to edit the **runctrl.sh** file.

```
pico runctrl.sh
```

Which will look something like this:

```

# Config, see README for instructions
EVENT_DEVICE="**/dev/input/event1**"
INPUT_KEY="**97**"


# Don't touch
./ventriloctrl $EVENT_DEVICE $INPUT_KEY

```

Replace the input_key with the number from the key you chose for your vent key, then replace (if needed) the /dev/input/event# with the one you found to work on your system.

Hit Ctrl+o to save.  Then Ctrl+x to close pico.

Now for the tricky part.

Ventrilo Control requires the ability to read and write to the device you've chosen.

There are a number of ways to do this but I'll tell you the one that will work and stay working.
 
We're going to write a udev rule so that the group ventrilo has read/write access to your event device.

```

sudo groupadd ventrilo
sudo gpasswd -a **YOURUSERNAME** ventrilo

```

Replace YOURUSERNAME with the username you plan to be using on Ubuntu at the time of running vent.

Now to write the udev rule.

```

sudo pico /etc/udev/rules.d/10-local.rules

```

This may bring up a new blank file, this is pretty much expected in newer versions of Ubuntu.
But no worries, time to move on.

In this file, type or paste the following:
(Replacing the ??? with the number of the /dev/input/event# device you found to work, for example if it was /dev/input/event2, replace ??? with the number 2.)

```
KERNEL=="event[???]", NAME="input/%k", GROUP="ventrilo", MODE="0660"
```

Hit Ctrl+o to save and Ctrl+x to exit pico.

One last step, we need to reload udev.

```
sudo /etc/init.d/udev restart
```

Now you should be able to run the file in your ventriloctrl directory called **runctrl.sh**.

```
./runctrl.sh
```

You will need to have vent running before you start this script.

If all goes well you should be able to go into the vent settings and set your key, with the key you chose to use.  It will probably show as the A key when you hit that key, but this is the default of the ventriloctrl program and I'm not even going to begin telling you about modifying that.  :P  In most cases this should work perfectly.

Let me know if you have any problems.

--Aaron

Sources used for figuring out this damn mess:
[random thoughts : by Imago]("http://imago.devinity.de/")
[Writing udev rules]("http://reactivated.net/writing_udev_rules.html")
Incase anyone needs to further understand the udev segment.

---

### Post by misfitpierce on 2007-05-16
Nice and ty ill try it out in a bit

---

### Post by Rajia on 2007-05-16
I'm doing great with this until I get up to the findkey command:  command not found.  Thoughts?

---

### Post by Rajia on 2007-05-16
Thanks, Hikari--this is fantastic.


Easy enough for even a newb like me to get running in only . . . 4 or 5 hours.  #-o

---

### Post by FragMonkey on 2007-05-22
Alright so I got my ventrilo working! I had basically the same problems all you guys had, but after tinkering for about 6 hours, I finally got something that works well!
Go to my post and scroll down to my last reply to see the settings I used:
[http://ubuntuforums.org/showthread.php?t=449999]("http://ubuntuforums.org/showthread.php?t=449999")

And to add to that:
If you want to be able to get sound from other apps besides ventrilo (as using my settings will only let sound come from ventrilo) then you would right click the ventrilo icon and click properties, and form there go to (I believe, as I'm not at my pc right now) the launcher tab and add "aoss" before the word "wine" in the laucnh parameters. I hope that makes sense. 
Alternativiley, if you launch Ventrilo through the terminal, you would add "aoss" before "wine" so it would be "aoss wine path-to-exe"

I hope all that made sense, as I am typing this from school on a Windows XP.

---

### Post by Electricboots on 2007-05-26
I've been googling and searching left and right, I cannot seem to get this working properly...

For the sound, I am using the motherboard nForce3 250Gb AC'97 Audio Controller...

winecfg is setup like this:
[LIST]
[*]Only OSS is checked
[*]Hardware Acceleration: Full
[*]Driver Emulation: unchecked
[/LIST]

In System->Preferences->Sound, I have ALSA selected in all the dropdowns in the Devices tab.

I deleted .asound.rc from my home dir.

I start WoW by doing:
```
aoss wine /home/eboots/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe
```

I start Ventrilo by doing:
```
aoss wine /home/eboots/.wine/drive_c/Program\ Files/Ventrilo/Ventrilo.exe
```

... but I still cannot get output sound to work in both apps at the same time, only the one in the foreground will output any sound... :(

I opened a terminal screen, I manually went to the directory where World of Warcraft is installed, and then I did 'aoss wine WoW.exe'. I could see the following error in the middle of all the "fixme" things:
```
err:wave:wodOpen fragment size set failed, size is now 8192
Your Open Sound System driver did not let us configure small enough sound fragments.
This may cause delays and other problems in audio playback with certain applications.
```

I started Ventrilo the same way, I did not see any error messages (apart from the usual 'fixme' things).


Also, could the following wine error message explain anything?  Could this be related to the fact that aoss doesn't seem to let two apps output sound at the same time?
```
ALSA lib ../../../src/pcm/pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
```
(I got the error above when trying Ventrilo alone while winecfg has only ALSA checked)

---

### Post by Rellin on 2007-05-26
> If all goes well you should be able to go into the vent settings and set your key, with the key you chose to use. It will probably show as the A key when you hit that key, but this is the default of the ventriloctrl program and I'm not even going to begin telling you about modifying that. :P In most cases this should work perfectly.
I got all of the other stuff done, but never experienced this.  Also, it doesn't work for me :(.

---

### Post by hikaricore on 2007-05-26
> **Rellin said:**
> I got all of the other stuff done, but never experienced this.  Also, it doesn't work for me :(.

perhaps you missed a step or didn't launch the modified bash file after completing configuration?

the steps are near flawless so saying it doesn't work for me is just a little vague.

---

### Post by Rellin on 2007-05-27
Actually it turns out what I quoted was key!  I entered "A" as my push to talk key (although I use HOME) and now it works!  GREAT!!!  <3 <3 <3

EDIT:  NICE!!  Also works for LCTRL which is exactly what I wanted.  You are the best.

---

### Post by Drooling_Sheep on 2007-05-29
Nevermind, I got it working

[http://gentoo-wiki.com/HOWTO_Ventrilo_Via_Wine](http://gentoo-wiki.com/HOWTO_Ventrilo_Via_Wine) 

That is helpful if your mic doesn't work.

---

### Post by Cappy on 2007-06-07
I've successfully setup ventrilo a few times with the use of the sidenet script:
[https://help.ubuntu.com/community/WineForAMD64#head-aa2244ea3332a3e6c4aea59069ae827a2fed3469](https://help.ubuntu.com/community/WineForAMD64#head-aa2244ea3332a3e6c4aea59069ae827a2fed3469)
Sidenet is the only way I've gotten it to work on my computers. I think sidenet is only for fresh Wine installs because it resets the registry and such.

I am using ALSA, 44100 (or whatever the second from the top is), and Full Hardware. I don't think the settings here matter very much because anything I change still lets Ventrilo run.

OSS makes me sound "like a robot" so I don't use it. The "robot voice" can also be caused by packet loss if your Vent server is running UDP.
Voice Activation works perfectly too.

Direct Input on the output so I can hear multiple voices. Weird little bug, I have to press Setup (and then press Okay) whenever I go into a Vent Server to begin hearing multiple voices.

---

### Post by rivethead on 2007-06-18
Ive had Vent running in previous releases of Ubuntu, and ive been trying very hard to get it to work with 7.04 im not sure whats going wrong this time. Im on a Dell XPS gen2 laptop with Sigmatel Sound, I have my Winecfg exactly as the faq states and my vent settings are the way the faqs state aswell. Ive copied over the correct ACM file and added it to wine's system.ini.  I have mic volume up and mic boost checked and in my system preferences under sound everythings set to ALSA the way it should be.

When i load ventrilo it loads up fine But when i click setup i get the errors,

WavOutGetDevCaps failed.
WavInGetDevCaps failed.

And when attempting to test the audio nothing happens at all. Never records audio. And when i click on Monitor, it repetitively spits out  Abs Zero in ventrilo. 

Not sure why i cant get it running this time arround, ive had it working fine before with minimal effort. Am i completely missing somthing ?

---

### Post by Cappy on 2007-06-19
Do you have your sound card selected in the "Hardware Input Mixer (Optional)"? You should select any options in those 3 fields that you have a choice of.

Turn "DirectSound" on for input and see if that works. 
You can also try OSS in winecfg.

It takes some playing are with the settings in Ventrilo itself mostly so don't worry too much about the winecfg settings other than just having ALSA/OSS off or on.

---

### Post by amic on 2007-06-20
I've followed all the instructions to a T, however, even after copying over the msgsm32.acm to the wine system folder, and editing the .ini, I continue to get the error where it says it's unable to find the GSM codec

---

### Post by dafreak on 2007-06-21
Ok I've followed all of the steps to run this program and I just can not get it to work at all. I should note that while this program is running it does not seem to capture the keystrokes even though I gave it the necessary permissions as described in the installation post. The only thing I did out of order was to install the xorg-dev files so after I did that I did another make. The program runs fine but if I'm playing EVE it does not capture my keystrokes. I'm using a Saitek Gaming Keyboard Pro if that makes a difference. At first I tried using the command pad (event6) but I went with using the keyboard itself and event3 instead. Is it possible using xbindkeys to somehow get this to work with my mx610 side buttons at all? That's what I'd really like to do.

---

### Post by phyrex1an on 2007-07-03
> **hikaricore said:**
> ...

Thanks for the great guide, it helped me a lot. I still have one problem thought, it seems as I don't have permission to listen to the input device.
```
./runctrl.sh 
```
have no effect while
```
sudo ./runctrl.sh
```
works perfectly.

I have created the ventrilo group and added myself to it.
```

sudo groupadd ventrilo
sudo gpasswd -a phyrex1an ventrilo

```

This is how my runctrl.sh look:
```
#!/bin/sh

# Config, see README for instructions
EVENT_DEVICE="/dev/input/event1"
INPUT_KEY="97"


# Don't touch
./ventriloctrl $EVENT_DEVICE $INPUT_KEY
```

This is how my /etc/udev/rules.d/10-local.rules look:
```
KERNEL=="event[1]", NAME="input/%k", GROUP="ventrilo", MODE="0660"
```

I have restarted udev, I think that the /dev/input/event1 thing existed before I made the new udev rule so it's maybe possible that there is another rule that overwrite the one I made?

---

### Post by hikaricore on 2007-07-03
There shouldn't be a problem running runctrl as a normal user after the permissions are set.

There could reasonably be a udev rule overriding it, but I'm not sure.

Please post the output of:

```
ls -la /dev/input/event1
```

p.s. /dev/input/event* always exists ^_^  we're just giving you read/write permission to it for ventctrl to work properly.

---

### Post by phyrex1an on 2007-07-03
> **hikaricore said:**
> p.s. /dev/input/event* always exists ^_^  we're just giving you read/write permission to it for ventctrl to work properly.
Ah, did know that, obviously :)

Anyway, I just did a full reboot and that seemed to solve it. I feel pretty stupid right now for not trying that before asking for help. I'm pretty sure that I did restart udev however so I dunno why it did a difference.
Sorry for the trouble and thanks for helping.

---

### Post by jadugartir on 2007-07-07
for many of us, teamspeak is not an option if we are an active member of an endgame raiding guild. i do not know of anyone on my whole server who uses teamspeak.

my guild does 25 man raids almost every day of the week so getting ventrilo to work on ubuntu is a high priority.

where do i download those packages that are listed? synaptic didnt have them

---

### Post by hikaricore on 2007-07-07
By packages I'm guessing you mean WINE?

---

### Post by Th1r1on on 2007-07-07
> **Rellin said:**
> Actually it turns out what I quoted was key!  I entered "A" as my push to talk key (although I use HOME) and now it works!  GREAT!!!  <3 <3 <3

EDIT:  NICE!!  Also works for LCTRL which is exactly what I wanted.  You are the best.

Ok This is my 1st post in the forums guys and sorry for being a noob for starters :)

I followed your perfect guide step by step hikaricore but I still see my ventrillo not getting the job done if I havent clicked on it ... I was thinking maybe that the mapping of LCTRL maybe wasnt supposed to work but as I see Rellin manages to use it nicely that way :( 
Also I restarted my pc and then I had to sudo the ventriloctrl : 

```
sudo ./runctrl.sh 
```

and I get normally 

```
Ventrilo Control v0.3-SVN for Linux by Purkka Productions
=====================================================
WARNING: This program reads DIRECTLY your keyboard!
         You need correct permissions to read the
         event device.
Window selected. Please test pressing the key to talk before going to play.

Use CTRL-C to quit.

```

but nothing happens there... I am Perfectly sure I have the right event ( event1) and also the right mapping for my key ( Left Control = 29 , for me that is ) any suggestions ? :(
Thanx in advance for your time guys!

EDIT : 
```
  ls -la /dev/input/event1
crw-rw---- 1 root ventrilo 13, 65 2007-07-07 16:06 /dev/input/event1

``` 
Just Because I saw you asked another person for it

---

### Post by scwoodal on 2007-07-07
> **phyrex1an said:**
> Ah, did know that, obviously :)

Anyway, I just did a full reboot and that seemed to solve it. I feel pretty stupid right now for not trying that before asking for help. I'm pretty sure that I did restart udev however so I dunno why it did a difference.
Sorry for the trouble and thanks for helping.

I had to log in/out after I added myself to the ventrilo group as I don't think it takes effect for your current session.

---

### Post by scwoodal on 2007-07-07
Would anyone know how to get the left "ALT" key to work for push to talk in Ventrilo? It recognizes the left ALT key when I press it in the Ventrilo setup, but when I try to test it out and talk it doesn't work.

If I set my push to talk key to any letter (ie T) it works and people can hear me, but using  the left ALT key does not. 

Any ideas?

---

### Post by Th1r1on on 2007-07-07
> **scwoodal said:**
> Would anyone know how to get the left "ALT" key to work for push to talk in Ventrilo? It recognizes the left ALT key when I press it in the Ventrilo setup, but when I try to test it out and talk it doesn't work.

If I set my push to talk key to any letter (ie T) it works and people can hear me, but using  the left ALT key does not. 

Any ideas?

That's what I found out right this moment ! I changed my key to "A" for example and it works perfectly but it wont do any good for games like wow :(

I mean having a key like : ctrl . alt would be better but as I see it you can only get a letter ... (maybe keyboard incompatibility ? :S )

---

### Post by Sugi on 2007-07-07
i can't use my mic on vent. is there some kind of setup i need to do to fix this? maybe through winecfg?

---

### Post by hikaricore on 2007-07-07
I don't understand why people are still launching runctrl with sudo....  did you read my guide?  honestly?

And btw you're not supposed to use the A key for real... it is the default key remaped by the ventrilctrl app to whatever key you setup.

---

### Post by Ziggyz on 2007-07-08
Where do you add step 5, and how would you dp step 6?

> **"The ini file"] [mci]

MPEGVideo=mciqtz.drv

MPEGVideo2=mciqtz.drv

avivideo=mciavi32.dll

cdaudio=mcicda.dll

sequencer=mciseq.dll

vcr=mcivisca.drv

 said:**
> 

MSACM.imaadpcm=imaadp32.acm

MSACM.msadpcm=msadp32.acm

MSACM.msg711=msg711.acm

MSACM.winemp3=winemp3.acm

vidc.MRLE=msrle32.dll

vidc.MSVC=msvidc32.dll

vidc.CVID=iccvid.dll

; vidc.IV50=ir50_32.dll

; vidc.IV31=ir32_32.dll

; vidc.IV32=ir32_32.dll



---

### Post by madman1337 on 2007-07-11
hmm for some reason libwine will not install. it keeps giving me an error that says that it has broken packages, but then when I downloaded just the deb's from other websites it still fails to install and doesn't give me an error at all. and so if I cant get libwine to install I can't get libwine-alsa to install :(

---

### Post by dahli.llama on 2007-07-15
> **Th1r1on said:**
> Ok This is my 1st post in the forums guys and sorry for being a noob for starters :)

I followed your perfect guide step by step hikaricore but I still see my ventrillo not getting the job done if I havent clicked on it ... I was thinking maybe that the mapping of LCTRL maybe wasnt supposed to work but as I see Rellin manages to use it nicely that way :( 
Also I restarted my pc and then I had to sudo the ventriloctrl : 

```
sudo ./runctrl.sh 
```

and I get normally 

```
Ventrilo Control v0.3-SVN for Linux by Purkka Productions
=====================================================
WARNING: This program reads DIRECTLY your keyboard!
         You need correct permissions to read the
         event device.
Window selected. Please test pressing the key to talk before going to play.

Use CTRL-C to quit.

```

but nothing happens there... I am Perfectly sure I have the right event ( event1) and also the right mapping for my key ( Left Control = 29 , for me that is ) any suggestions ? :(
Thanx in advance for your time guys!

EDIT : 
```
  ls -la /dev/input/event1
crw-rw---- 1 root ventrilo 13, 65 2007-07-07 16:06 /dev/input/event1

``` 
Just Because I saw you asked another person for it

I am having the same trouble and I am doing the exact same thing.  The Vent CTRL script just doesn't seem to do anything for me.

```

#!/bin/sh

# Config, see README for instructions
EVENT_DEVICE="/dev/input/event1"
INPUT_KEY="34"


# Don't touch
./ventriloctrl $EVENT_DEVICE $INPUT_KEY

```

That is my runctrl.sh file.  I'm trying to use G as my PTT button.

```
KERNEL=="event[1]", NAME="input/%k", GROUP="ventrilo", MODE="0660"

```

And that's the 10-local.rules file.

I don't know what I've done wrong, but that's where I'm at.

Edit:  Ok, I got the Ventrilo Control thing working.  It seems that the permissions to the event were not working correctly.  I ended up following the steps in the README file and got ownership by doing 
```

sudo chown <your username> /dev/input/eventx

```

So at least that is working, but I'm still having troubles with the sound.


I use a Logitech USB headset and I cannot seem to get Vent to work so I can listen and talk on the headset at the same time.  If I start up vent with the aoss option, I can talk, but as soon as someone says something to me, then I can no longer talk.  I have it setup right now so that I hear things through my speakers and then talk through the headset, but that's sub-optimal.  Any suggestions on that?

---

### Post by hikaricore on 2007-07-15
Several users said they needed to reboot after adding udev rules for some reason, as restarting udev did not read the new rules.  *shrug*

chowning the device is only a temporary effect and if your udev rule is not working resets after a reboot.

---

### Post by dahli.llama on 2007-07-15
> **hikaricore said:**
> Several users said they needed to reboot after adding udev rules for some reason, as restarting udev did not read the new rules.  *shrug*

chowning the device is only a temporary effect and if your udev rule is not working resets after a reboot.

Ah,  Good to know.  I still forget that rebooting is occasionally still necessary in Linux :D

---

### Post by dahli.llama on 2007-07-17
Ok, I would really like some help getting this to work.

I have a Logitech USB headset that I would like to use with Ventrilo.  My system uses the nVida Nforce onboard sound for the speakers, and I would like to get gameplay sounds through the speakers.  My Wine version is 0.9.40 (the latest I can get with Synaptic).  I am running Ubuntu 7.04 64-bit.

The problem I am having is that I cannot get Vent setup so that I can listen through the headset and talk through the headset at the same time.  I've tried to follow all of the tutorials here and nothing seems to help.  Other programs seem to work ok with multiple sound sources, and in Teamspeak I can use my headset just find, but I can't in Vent. 

If I run Vent with the aoss wrapper, then when I go into test mode I can talk and listen on my headset, but once I connect to a server and someone says something to me I can no longer speak back.  If I don't run with the aoss wrapper, then I cannot get it to play any sounds through my headset, but I can talk using the headset mic, and listen through the PC speakers.  This is what I'm doing for now and it works, but if I do this, then I get no sound out of the game.

[IMG]http://www.whatmission.net/Stuff/soundcfg.png[/IMG]
This is my sound settings in Ubuntu.  The other options available are:
- Autodetect
- USB Audio
- Nvidia CK804-IEC958
- Nvidia CK804
- ALSA
- ESD
- OSS


[IMG]http://www.whatmission.net/Stuff/ventcfg.png[/IMG]
My Vent settings without the aoss wrapper.

[IMG]http://www.whatmission.net/Stuff/ventaosscfg.png[/IMG]
My Vent setting with the aoss wrapper

[IMG]http://www.whatmission.net/Stuff/winecfg.png[/IMG]
My Wine audio settings.

I hope someone can give me some insight to why I'm having problems with this.  Sound has been my biggest issue since I started working with Linux and Wine, and I'd love to get this solved.

Thanks a ton in advance.

---

### Post by Xailia on 2007-08-09
Despite reading everyone's posts here and following the instructions I am still having issues getting this to work correctly on two separate systems, which leads me to believe its something I am doing wrong.  I have everything working except the push to talk feature (outside of the ventrilo window).  So the issue has something to do with my permissions and the script...

I setup the ventrilo group, gave it permissions to read the keyboard, and added myself to the group.  I know this is working because when I run findkey with event1 pressing the DEL key I get this output:

```
rshields@genepi-rshields:~/ventriloctrl-0.3$ ./findkey /dev/input/event1
key 28 state 0
key 111 state 1
^[[3~key 111 state 0
key 111 state 1
^[[3~key 111 state 0

```

I then start ventrilo

```
wine ./Ventrilo.exe
```

With the window selected I am able to use the push to talk button (DEL), I can hear everyone and they can hear me.

I then open a new console look at my runctrl.sh:

```

#!/bin/sh

# Config, see README for instructions
EVENT_DEVICE="/dev/input/event1"
INPUT_KEY="111"


# Don't touch
./ventriloctrl $EVENT_DEVICE $INPUT_KEY

```

Looks good to me.

I run it:

```
./runctrl.sh
``` or I have also tried
```
sh ./runctrl.sh
```

either one will start the program:
```
Ventrilo Control v0.3-SVN for Linux by Purkka Productions
=====================================================
WARNING: This program reads DIRECTLY your keyboard!
         You need correct permissions to read the
         event device.
Window selected. Please test pressing the key to talk before going to play.

Use CTRL-C to quit.
```
it starts up and finds the ventrilo window.  I proceed to click DEL.  No luck.

Any thoughts?

---

### Post by DahVid on 2007-08-09
Use the free, open source, multiplatformal [mumble](mumble.sf.net)

---

### Post by Xailia on 2007-08-09
I see lots of people in this thread suggesting mumble and teamspeak since they are both multiple platform and just plain work.  The problem is I, like everyone else posting for help, doesn't have power over what server we run.  I am stuck with Ventrilo and have to figure a way to get this to work or go back to Windows (Oh God...please no).

Trust me, if given the option I will definitely promote anything other than Ventrilo when given the opportunity.  Until then, any suggestions on how to get this working?

(Sorry if I came off bitter or snappy...I am just frustrated with the endless hours I have spend trying to get this working).

---

### Post by hikaricore on 2007-08-09
Have you set the key again in Ventrilo after running ventriloctrl?

The ventriloctrl program intercepts & outputs a chosen key, which it remaps as A.
(DO NOT worry about the key A, it's just what the program uses, the important thing is that it remaps your chosen key so use YOUR key)

You must set the key in Ventrilo AFTER you have started ventriloctrl.  This only needs
to be done once, so if you havn't tried this method give it a shot.  ^_^

---

### Post by Xailia on 2007-08-09
Well, currently it is working.  The problem is I have no idea why (I don't really consider it a complete victory until I figure out why).

Thanks for the tip on setting it after I start Vent.  I have tried it in the past, but I was changing so many things at once I am sure it was negated in the shuffle.  I will let you know how things work out.

On a side note, when this is completely working I am going to write a HOWTO start to finish of how to install ubuntu, WoW, and Ventrilo.  I will be sure to reference this thread and give all of you guys many many many thanks.

---

### Post by Xailia on 2007-08-10
Well it has a 50-50 chance of working...I just keep restarting things until it kicks in.  I am going to poke around and try to identify the problem - any thoughts on where to start?

---

### Post by hikaricore on 2007-08-10
> **Xailia said:**
> Well it has a 50-50 chance of working...I just keep restarting things until it kicks in.  I am going to poke around and try to identify the problem - any thoughts on where to start?

The biggest problem is that VentriloCtrl is a cheap hack.

It intercepts keys in a way that really isn't 100% fool-proof.

This is the nature of the main issue.  The key hooks that Ventrilo requires are not properly implemented in WINE (hell they aren't really recommended to use in ***dows programming AFAIK) and probably won't be for a long time.  If the WINE devs were to implement certain buggy features such as this it could in turn break other compatibilities and cause major regressions.  On top of that Ventrilo isn't really a huge priority, as there are other voice communication methods, making Vent work better in WINE is on the back burner.

On the subject of bad hacks.  I noticed on my girl's system that every so often the program (ventrilctrl) would just stop working or wouldn't work to begin with.  I ended up writing a very lame bash script, and setting it as a cron job to occur every 4 minutes.  :lolflag:

**Here's my crappy script which I don't suggest using.**  It's lametastic.
I'm posting this out of pure morbid amusement (it also requires ventriloctrl to be in /usr/bin or /usr/local/bin):

```

#!/bin/bash

EVENT_DEVICE="/dev/input/event1"
INPUT_KEY="127"

            if [ -n "$(pidof Ventrilo.exe)" ]; then

                echo expression evaluated as true

                killall ventriloctrl && sleep 1.5 && ventriloctrl $EVENT_DEVICE $INPUT_KEY &

            else
                echo expression evaluated as false
            fi

```

All it really does is check to see if Ventrilo is running.  If it is it kills ventriloctrl, waits 1.5 seconds, and runs it again.  Of course you'll need your proper settings listed in device and key for it to even function.

I guess if this helps anyone it was worth posting, but there really has to be a better way folks. :p

p.s.  The echos serve no purpose, they're there because I never bothered to take them out while testing the script.

---

### Post by Rich43 on 2007-08-11
Dudes! **You need to check out mumble!!!**

[http://mumble.sourceforge.net/](http://mumble.sourceforge.net/)

Its a real good open source project, better than TS or vent... but not well promoted..so tell your friends!

---

### Post by hikaricore on 2007-08-11
Thank you, we're aware of Mumble.

There is no need to spam it around here :P

---

### Post by JesseEklund on 2007-08-11
I'm having problems setting up the udev group. The terminal keeps spitting this when i try and add my username in:

```
jesse@ROOM:~/ventrilo/ventctrl$ sudo gpasswd -a -DizMal- ventrilo
gpasswd: unknown user -DizMal-
```

Any ideas?

---

### Post by hikaricore on 2007-08-11
> **JesseEklund said:**
> I'm having problems setting up the udev group. The terminal keeps spitting this when i try and add my username in:

```
jesse@ROOM:~/ventrilo/ventctrl$ sudo gpasswd -a -DizMal- ventrilo
gpasswd: unknown user -DizMal-
```

Any ideas?

I've never actually seen/tried a username with dashes in it before I'm guessing that could be the issue?

---

### Post by dafreak on 2007-08-11
Well I finally got ventriloctrl to work properly but now for some unknown reason folks that are listening to me report that after a while the voice goes to crap. I also notice that when this happen ventriloctrl responds slower to the push to talk key. Ideas?

---

### Post by JesseEklund on 2007-08-14
Its not the dashes because it happens even when i attempt to not use them.

---

### Post by damutt13 on 2007-08-18
Hello there, I read your tutorial on the VentirloCTRL program, and I followed them perfectly and everything was fine.. until i ran "./runctrl.sh", it gave me:

code@code-laptop:~/source/ventriloctrl-0.3$ ./runctrl.sh
Ventrilo Control v0.3-SVN for Linux by Purkka Productions
=====================================================
WARNING: This program reads DIRECTLY your keyboard!
         You need correct permissions to read the
         event device.
Could not find Ventrilo window. Is Ventrilo running?


I am running 2.3.0 ventrilo, ubuntu 7.

Any help would be appreciated, thanks.

---

### Post by MemoryDump on 2007-08-22
well I've tried the script and got everything setup as instructed.. even rebooted and VENT is still not getting the keyboard signal to PUSH to Talk.

I have my key in VENT set to "`" GRAVE which is key# 41 according to my event2

any ideas?

---

### Post by Xailia on 2007-08-23
I had an insane amount of trouble getting Ubuntu, WoW, Cedega, and Ventrilo (WITH push to talk) to all play nice together.  I finally got it working and wrote up an extensive guide on [www.eqjunkies.com]("www.eqjunkies.com").  The direct link to the guide (when it gets pushed off the homepage is: [http://www.eqjunkies.com/?p=125]("http://www.eqjunkies.com/?p=125").  Hopefully it can help some of you out; if you have any problems please comment on eqjunkies and I will do my best to help you!

Special thanks to these forums also because all of you helped along the way!

---

### Post by MemoryDump on 2007-08-23
> **Xailia said:**
> I had an insane amount of trouble getting Ubuntu, WoW, Cedega, and Ventrilo (WITH push to talk) to all play nice together.  I finally got it working and wrote up an extensive guide on [www.eqjunkies.com]("www.eqjunkies.com").  The direct link to the guide (when it gets pushed off the homepage is: [http://www.eqjunkies.com/?p=125]("http://www.eqjunkies.com/?p=125").  Hopefully it can help some of you out; if you have any problems please comment on eqjunkies and I will do my best to help you!

Special thanks to these forums also because all of you helped along the way!

your instructions at "Step Nine: Push to Talk" are almost identical to those posted in this forum thread already :(
Those are the steps I followed and I'm still not getting it to work :(

would a windows manage conflict with this? I'm using compiz-fusion.

---

### Post by Xailia on 2007-08-23
If you would like, try using my settings:

Post the output of:

```
cat /proc/bus/input/devices
```

Are you running ./findkey as root or as your normal user?

If not, do it as your normal user.  If it doesn't work: goto System->Administration->Users and Groups->manage Groups->Ventrilo

Is your username checked?

What key to do you have set for Ventrilo push to talk and what value is in the runctrl.sh?

Are you running the script and ventrilo in seperate terminal windows?  (I don't know if this is a necessary, just trying to match my settings so I can better help you figure out what is the cause)

If you post your config files I can see if there is a problem anywhere that I can find.  Its hard to debug w/o the full picture.

---

### Post by MemoryDump on 2007-08-23
> **Xailia said:**
> If you would like, try using my settings:

Post the output of:

```
cat /proc/bus/input/devices
```


```
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
H: Handlers=mouse0 ts0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=045e Product=00db Version=0111
N: Name="Microsoft Natural® Ergonomic Keyboard 4000"
P: Phys=usb-0000:00:1d.0-1/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe
B: LED=107

I: Bus=0003 Vendor=045e Product=00db Version=0111
N: Name="Microsoft Natural® Ergonomic Keyboard 4000"
P: Phys=usb-0000:00:1d.0-1/input1
S: Sysfs=/class/input/input3
H: Handlers=kbd event3 
B: EV=10000f
B: KEY=7fff 2c3027 bf004440 0 0 1 10f80 8807c407 ffe77bfa d9715fff febeffdf ffefffff ffffffff fffffffe
B: REL=40
B: ABS=1 0

I: Bus=0003 Vendor=046d Product=c506 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.0-2/input0
S: Sysfs=/class/input/input4
H: Handlers=mouse1 ts1 event4 
B: EV=20007
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=103
B: LED=ff00

I: Bus=0003 Vendor=045e Product=0047 Version=0110
N: Name="Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)"
P: Phys=usb-0000:00:1d.7-3.4/input0
S: Sysfs=/class/input/input5
H: Handlers=mouse2 ts2 event5 
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=ACPI_FPB/button/input0
S: Sysfs=/class/input/input6
H: Handlers=kbd event6 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input7
H: Handlers=kbd event7 
B: EV=3
B: KEY=100000 0 0 0

```


> **Xailia said:**
> Are you running ./findkey as root or as your normal user?
normal user

> **Xailia said:**
> 
If not, do it as your normal user.  If it doesn't work: goto System->Administration->Users and Groups->manage Groups->Ventrilo

Is your username checked?

I'm in the group :)

> **Xailia said:**
> 
What key to do you have set for Ventrilo push to talk and what value is in the runctrl.sh?

I use the GRAVE key "`".

```
#!/bin/sh

# Config, see README for instructions
EVENT_DEVICE="/dev/input/event2"
INPUT_KEY="41"


# Don't touch
./ventriloctrl $EVENT_DEVICE $INPUT_KEY

```


> **Xailia said:**
> 
Are you running the script and ventrilo in seperate terminal windows?  

I run Vent using a launcher on my desktop which uses aoss. I've tested vent and it works properly as long it's the active window. Then I'll open up a terminal and run the script which appears to load properly.

---

### Post by Xailia on 2007-08-23
I don't know your exact hardware, but your output is slightly perplexing.

For one thing, it appears as though your keyboard shows up twice:

```
I: Bus=0003 Vendor=045e Product=00db Version=0111
N: Name="Microsoft Natural® Ergonomic Keyboard 4000"
P: Phys=usb-0000:00:1d.0-1/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe
B: LED=107

I: Bus=0003 Vendor=045e Product=00db Version=0111
N: Name="Microsoft Natural® Ergonomic Keyboard 4000"
P: Phys=usb-0000:00:1d.0-1/input1
S: Sysfs=/class/input/input3
H: Handlers=kbd event3 
B: EV=10000f
B: KEY=7fff 2c3027 bf004440 0 0 1 10f80 8807c407 ffe77bfa d9715fff febeffdf ffefffff ffffffff fffffffe
B: REL=40
B: ABS=1 0
```

It seems your keyboard is both event2 and event3, correct me if I am wrong.  

Something else that is confusing is that you have this:
```

I: Bus=0003 Vendor=046d Product=c506 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.0-2/input0
S: Sysfs=/class/input/input4
H: Handlers=mouse1 ts1 event4 
B: EV=20007
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=103
B: LED=ff00
```

When your mouse is also a microsoft one.  Do you have a USB pad or is that your microphone?

Suggestions:

[LIST=1]
[*]Try changing from event2 to event3, see if it makes a difference
[*]Try using your mouse event (#5).  (Remember to use ./findkey again with the mouse, change the script to the new value, and set your push to talk button.
[/LIST]

Let me know what comes of this.

---

### Post by MemoryDump on 2007-08-23
I'm not sure why I'd have 2x keyboards listed/configured ?? :confused:

As for the mice, I do have 2 mice connected to my system. I have my primary one which is a Logitech MX700 Wireless (which I'm guessing why it's listed as a USB Receiver) and a Microsoft wired one which I use in the event my Logitech dies cause the rechargeble batteries dies. (which seems to occur to happen more lately as I need to replace those batteries)

I'm at work right now so I can't test anything at the moment.. but I do recall trying event3 last night and I wasn't getting anything. Only event2 seemed to be working for me.

Not sure what you mean by trying to use my mouse from event #5 :confused:

thanks for the assistance btw :D

---

### Post by Xailia on 2007-08-23
> Not sure what you mean by trying to use my mouse from event #5

What I meant was using your mouse to trigger push to talk instead of your keyboard.  When I was having trouble with my keyboard sending the signal, I found that if I used my mouse for the push to talk it would work...very odd.

Try going through the configuration process (findkey and runctrl).  You can try it as root for now to see if it will help.

---

### Post by Aesir09 on 2007-08-23
works fine for me from what i can remember, make sure your mic is not muted:

```
alsamixer
```

---

### Post by MemoryDump on 2007-08-23
> **Xailia said:**
> What I meant was using your mouse to trigger push to talk instead of your keyboard.  When I was having trouble with my keyboard sending the signal, I found that if I used my mouse for the push to talk it would work...very odd.

Try going through the configuration process (findkey and runctrl).  You can try it as root for now to see if it will help.

I've tried with event5 and using a mouse button and still no success :(
I went through ALL the steps again for this and I'm %100 sure it's setup correctly.

event2 is my keyboard and event5 is my Microsoft Mouse.. I even tried using the DELETE key and still no go.. Vent itself works fine when I assign a new key.

HELP! :confused:

---

### Post by Xailia on 2007-08-24
try this:

start ventrilo, then start the script.

Go into Vent and then set your key again in the push to talk.  I have noticed sometimes no matter what you hit (only hit the desired key though), it changes to "A", when that happens it is more likely to work.

---

### Post by MemoryDump on 2007-08-24
ok.. I just re-read 3/4 of all the posts in this thread and just realized that most of you have wincfg sound option set to OSS rather than ALSA... does this make a difference as far as making this script work? Like I said.. Vent works fine,, just not in conjuction with this script :(

---

### Post by Xailia on 2007-08-24
It really shouldn't have an affect on it...the script is just grabbing event handlers from the keyboard and intercepting them.   

The only thing I could think to do at this point is edit the script to output the keyboard signal every time it receives it.  You could also add a line to make sure it is getting the right window.  I will take a look at it tonight when I get off work and see if I can modify it for you to make it easier to debug the situation.

---

### Post by MemoryDump on 2007-08-24
> **Xailia said:**
> It really shouldn't have an affect on it...the script is just grabbing event handlers from the keyboard and intercepting them.   

The only thing I could think to do at this point is edit the script to output the keyboard signal every time it receives it.  You could also add a line to make sure it is getting the right window.  I will take a look at it tonight when I get off work and see if I can modify it for you to make it easier to debug the situation.
muchly appreciated :D

---

### Post by Dogfighter on 2007-08-25
heya, im sorry if this has been cleared earlier but i didnt read all pages.

ive followed the instructions, but whenever i want to test the sound i get the error:  "Open Input Device failed." :(

cant hear ppl talk nor can they hear me.
ive tried around but i wasnt able to fix it.
im using a soundblaster live soundcard.

any help appreciated :)

---

### Post by MemoryDump on 2007-08-26
> **Xailia said:**
> It really shouldn't have an affect on it...the script is just grabbing event handlers from the keyboard and intercepting them.   

The only thing I could think to do at this point is edit the script to output the keyboard signal every time it receives it.  You could also add a line to make sure it is getting the right window.  I will take a look at it tonight when I get off work and see if I can modify it for you to make it easier to debug the situation.
any luck with the moded code? :)

---

### Post by Xailia on 2007-08-27
I didn't get a chance to look at it (and I kind of forgot...) I put it on my list of things to do though.

---

### Post by Dogfighter on 2007-08-28
> **Dogfighter said:**
> heya, im sorry if this has been cleared earlier but i didnt read all pages.

ive followed the instructions, but whenever i want to test the sound i get the error:  "Open Input Device failed." :(

cant hear ppl talk nor can they hear me.
ive tried around but i wasnt able to fix it.
im using a soundblaster live soundcard.

any help appreciated :)

anyone? :???:

---

### Post by Xailia on 2007-08-28
First off, make sure you don't have anything muted.  Secondly, in the ventrilo setup try different output device options till you find one that works.  If that fails...

Goto the console and type:

```
winecfg
```

Click on the audio tab and let me know what it says under OSS and ALSA  for output devices (or just take a screenshot).

---

### Post by Xailia on 2007-08-28
Here is a modified version of ventriloctrl.c for those of you who have problems.  When you start it will output all the windows it is going through until it finds the right one (was already there just uncommented it) along with outputing a message every time you send a key to Ventrilo.  Hopefully this helps you figure out what is going on.
```

// 
// Original code by Adam Pierce - http://www.doctort.org/adam/
// http://www.doctort.org/adam/nerd-notes/x11-fake-keypress-event.html
//

//
// find_window() -function contributed by Markus Lindqvist
//

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <X11/Xlib.h>
#include <X11/keysym.h>

// evdev input
#include <linux/input.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>

#define VERSION "v0.3-SVN"
#define VENTWIN "Ventrilo"

// define key to send to Ventrilo, default is A
#define KEYCODE XK_A

XKeyEvent createKeyEvent(Display *display, Window win,
			Window winRoot, int press,
			int keycode, int modifiers)
{
	XKeyEvent event;

	event.display     = display;
	event.window      = win;
	event.root        = winRoot;
	event.subwindow   = None;
	event.time        = CurrentTime;
	event.x           = 1;
	event.y           = 1;
	event.x_root      = 1;
	event.y_root      = 1;
	event.same_screen = True;
	event.keycode     = XKeysymToKeycode(display, keycode);
	event.state       = modifiers;
	event.send_event  = 1;
	event.serial      = 0;
	if(press)
		event.type = KeyPress;
	else
		event.type = KeyRelease;

	return event;
}

Window *find_window(Display *display, Window start, const char *name)
{
	Window *children = 0;
	Window root;
	Window parent;
	int i;
	unsigned int childrenCount = 0;
	XQueryTree(display, start, &root, &parent, &children, &childrenCount);
	    
	char *window_name = 0;
	for(i=0; i<childrenCount; ++i) {
		if(XFetchName(display, children[i], &window_name) == 1) {
			printf("value: %s\n", window_name);
			if(strcmp(name, window_name) == 0) {
				XFree(window_name);
				return &children[i];
			}
			XFree(window_name);
		}
	}

	for(i=0; i<childrenCount; ++i) {
		Window *window = find_window(display, children[i], name);
		if(window != 0) {
			XFree(children);
			return window;
		}
	}

	if(children != 0)
		XFree(children);

	return 0;
}

int main(int argc, char **argv)
{
	// xlib
	Display *display;
	Window winRoot;
	Window *winFocus = 0;
	XKeyEvent event;

	// check parameters
	if (argc < 3) {
		printf("usage: %s <device> <listen key>\n", argv[0]);
		return 1;
	}

	printf("Ventrilo Control %s for Linux by Purkka Productions\n", VERSION);
	printf("=====================================================\n");
	printf("WARNING: This program reads DIRECTLY your keyboard!\n");
	printf("         You need correct permissions to read the\n");
	printf("         event device.\n");

	// evdev
	int fd;
	fd = open(argv[1], O_RDONLY);
	if(!fd) {
		printf("Error: Can't opening device %s\n", argv[1]);
		return 1;
	}
	struct input_event ev;

	display = XOpenDisplay(0);
	if(display == NULL) {
		printf("Error: Could not open display!\n");
		return 1;
	}

	winRoot = XDefaultRootWindow(display);
	winFocus = find_window(display, winRoot, VENTWIN);

	if(!winFocus) {
		printf("Could not find Ventrilo window. Is Ventrilo running?\n");
		return 1;
	}

	printf ("Window selected. Please test pressing the key to talk before going to play.\n");
	printf ("\nUse CTRL-C to quit.\n");

	// main loop after selecting window
	while(1)
	{
		read(fd, &ev, sizeof(struct input_event));
		if(ev.type == 1) {
			if(ev.code == atoi(argv[2])) {
				if(ev.value == 1) {
					printf("Sending Key!\n");
					// send press event
					event = createKeyEvent(display, *winFocus, winRoot, 1, KEYCODE, 0);
					XSendEvent(event.display, event.window, True, KeyPressMask, (XEvent *)&event);
					XFlush(display);
				} else if(!ev.value) {
					// send release event
					event = createKeyEvent(display, *winFocus, winRoot, 0, KEYCODE, 0);
					XSendEvent(event.display, event.window, True, KeyPressMask, (XEvent *)&event);
					XFlush(display);
				}
			}
		}
	}

	return 0;
}
```

---

### Post by Dogfighter on 2007-08-28
> **Xailia said:**
> First off, make sure you don't have anything muted.  Secondly, in the ventrilo setup try different output device options till you find one that works.  If that fails...

Goto the console and type:

```
winecfg
```

Click on the audio tab and let me know what it says under OSS and ALSA  for output devices (or just take a screenshot).

nothing is muted, teamspeak, xmms, games ect work fine.
ive tried all possible output devices already, i get the same error everywhere.

in the audio options only OSS is enabled, should i enable ALSA too?

*EDIT* just tried that, and it doesnt work either.
when i unselect OSS and only have ALSA on i get the same error again. :/

---

### Post by Xailia on 2007-08-28
Did you play with the settings from within ventrilo?  You can select different sound devices...

---

### Post by Dogfighter on 2007-08-28
yea like i said i did... but it doesnt make a difference.
the question is, do i need  to manually install the soundcard?
ive just plugged it in and booted up and everything was working...

in the volumecontrol it does show (SBLIVE) so its got detected.
but i cannot select it in the vent options. :confused:

see screenie.

---

### Post by Xailia on 2007-08-28
As long as its showing up in your wine configure under ALSA or OSS as an output device then the installation is not the problem.

---

### Post by Dogfighter on 2007-08-28
just had a look and it doesnt show up in the OSS section...
only this "sigmatel" i have no idea what that is, or is it the same?

---

### Post by Xailia on 2007-08-28
try uninstalling and reinstalling wine and see what comes of it.  There is probably a way to go through the configs and have it redetect stuff, but nothing beats a clean install...

---

### Post by Dogfighter on 2007-08-28
hmm for some reason it now works.
all ive done is i installed SDL_net which was required by a game i was installing, after that it  worked lol.
well anyway thanks for the help :)

---

### Post by MrJavalava on 2007-09-03
Is there a more recent version of how to make ventrilo and wine work more reliable? This guide is sort of outdated.

I'm looking for a wiki that has checkpoints, so I can be sure I'm on the right track when setting up both wine and ventrilo. At the moment the whole thing seems sluggish. I think it's because of Alsa or OSS for that matter. Ventrilo or winecfg takes up to 2 or 3 minutes before I see the GUI. 

I might wanna lateron try to make WoW work along with Wine but it does not appeal to me just yet, since I find the reliability abit dodgy.

---

### Post by Xailia on 2007-09-03
```
Is there a more recent version of how to make ventrilo and wine work more reliable? This guide is sort of outdated.
```

Yes, I wrote one here: [http://www.eqjunkies.com/?p=125]("http://www.eqjunkies.com/?p=125")

---

### Post by hikaricore on 2007-09-03
> **Xailia said:**
> ```
Is there a more recent version of how to make ventrilo and wine work more reliable? This guide is sort of outdated.
```

Yes, I wrote one here: [http://www.eqjunkies.com/?p=125]("http://www.eqjunkies.com/?p=125")

Ok.... I can deal with you recommending Cedega.

However, the push to talk walk-through you posted is half wrong.  And stripping everyone out and just saying "thanks all" for credit isn't really the best way to handle things, atleast link back to your sources.

I am **NOT** amused. :mad:

> Step Nine: Push to Talk

    * Type:

    cat /proc/bus/input/devices

    * Look through the list and find your keyboard and look for the line that looks like this: H: Handlers=kbd event1

    * In this case my device event variable is /dev/input/event1

    * Type:

    sudo groupadd ventrilo
    sudo gpasswd -a YOURUSERNAME ventrilo
    sudo gedit /etc/udev/rules.d/10-local.rules

    * The &#8220;YOURUSERNAME&#8221; above is the username you use to login to linux.
    * paste in this line of code replacing the &#8220;???&#8221; with the event number you found in the first step:

    KERNEL=="event[???]", NAME="input/%k", GROUP="ventrilo", MODE="0660"

    * Save the file and RESTART the computer.
    * Download this.
    * Find the file on your desktop and right click. Select &#8220;Extract here&#8221;
    * Open a terminal (Applications->Accessories->Terminal)
    * The following is taken from the program&#8217;s readme file
    * Type (replace # with the event number you found earlier).:

    ./findkey /dev/input/event#

   1. Press the key you want to use as push to talk, record the keynumber (for instance, the DEL key is 111).
   2. Type:

    gedit runctrl.sh

   1. Change EVENT DEVICE and INPUT KEY to reflect the values you found/selected.
   2. Run Ventrilo by opening a terminal and going to your ventrilo directory

    cd /ventrilo
    wine ./Ventrilo.exe

Open a new terminal and goto the ventriloctrl directory. Run the script:

    ./runctrl.sh

Your push to talk should now be operational.

Note: You must run the runctrl.sh after you run Ventrilo, everytime.

---

### Post by Xailia on 2007-09-03
I did not mean to offend...I did give the links in the beginning (including this thread).  Aside from the group for adding a ventrilo group (from this thread) the majority of it came from the readme file included with the script.

Again, I didn't mean to offend you nor did I mean to downplay the role of my sources.  (I will edit the post to make this more apparent).

I think we are all working towards the same goal - getting things working on Ubuntu as best as possible.  I know Cedega isn't free so it doesn't fit in with Ubuntu's outlook, but as a user I found that it worked better than  wine so I used it.  I would love to use free/open source whenever possible, but it has preform as well (or better).

On a side note...the guide does work for many people, so I am not sure what portion of it "half wrong", but I imagine you have more experience with Ubuntu/Linux than I ever will.

---

### Post by MrJavalava on 2007-09-04
Anyhu...

It might be the setup of Wine that is not correctly setup for all that I know. It shouldn't be this slow nor unreliable, I know wine is not perfect in any way, but still..

Sometimes the ventrilo nor winecfg does not start at all, while I'm trying to starting either programs, the startup affects other programs aswell. I can't see it takes up resources or anything like that, it just stalls for a bit.

The computer I'm currently running with:

Thinkpad T41p, aka P-M 1,7GHz and with an ATI mobility FIREGL T2 gfx card (wish it were Nvidia.. meh)

current setup:
Ubuntu Feisty
CompizFusion with XGL (in case it matters)

---

### Post by MrJavalava on 2007-09-04
Btw, I've actually used your guide.......

---

### Post by Xailia on 2007-09-04
The problem with wine not starting fast is fairly out of my league...but I have a couple ideas that come to mind:

Go into winecfg and try to turn down all of the audio/graphics settings - my gut is wine is trying to use a driver that isn't completely compatible with one of those devices, but like I said, I really have no idea; just guessing.

---

### Post by misse- on 2007-09-04
I need help. I got it to work, but after a reboot it simply crashes when checking  "Use directsound"

Wine settings:

OSS and ESD checked. Full hardware support, 44800 16bit no driver emulation.

In Ventrilo it works altough I sound like a robot with default mapper's on both. But when I check directsound it crashes and give me the following output:


```
wine: Unhandled page fault on read access to 0x00000138 at address 0xb7d0e34c (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000138 in 32-bit code (0xb7d0e34c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7d0e34c ESP:00338878 EBP:00338894 EFLAGS:00210206(   - 00      - RIP1)
 EAX:0000000a EBX:7d222344 ECX:0000008b EDX:00000815
 ESI:00000138 EDI:00338a18
Stack dump:
0x00338878:  7d208b8e 00338a18 00000138 0000022c
0x00338888:  7ef10a30 7d208b59 7d222344 003388d4
0x00338898:  7d20444c 0000000a 00338a18 003388e4
0x003388a8:  7b88cb21 7eeaac20 7b88cb21 0000000a
0x003388b8:  7bc3200f ffffffff 7b8b0888 00338904
0x003388c8:  7ef29168 7ef72170 001461ec 00338934
Backtrace:
=>1 0xb7d0e34c memcpy+0x1c() in libc.so.6 (0x00338894)
  2 0x7d20444c OSS_widMessage+0x2fc() in wineoss (0x003388d4)
  3 0x7ef0f179 MMDRV_Message+0x459() in winmm (0x00338934)
  4 0x7ef0f589 MMDRV_PhysicalFeatures+0x189() in winmm (0x00338974)
  5 0x7ef1cc2e waveInMessage+0x11e() in winmm (0x003389b4)
  6 0x7e9bb757 DirectSoundCaptureEnumerateA+0x197() in dsound (0x00338c64)
  7 0x00425780 in ventrilo 2.1.4 (+0x25780) (0x00338ca4)
  8 0x00452d09 in ventrilo 2.1.4 (+0x52d09) (0x00338cd4)
  9 0x0044f6b1 in ventrilo 2.1.4 (+0x4f6b1) (0x00338cf8)
  10 0x00451862 in ventrilo 2.1.4 (+0x51862) (0x00338d48)
  11 0x004512a1 in ventrilo 2.1.4 (+0x512a1) (0x00338dc4)
  12 0x00451253 in ventrilo 2.1.4 (+0x51253) (0x00338de4)
  13 0x00427b65 in ventrilo 2.1.4 (+0x27b65) (0x00338e68)
  14 0x0045050a in ventrilo 2.1.4 (+0x5050a) (0x00338e84)
  15 0x7ee6a7aa WINPROC_wrapper+0x1a() in user32 (0x00338eb4)
  16 0x7ee6aebe in user32 (+0xaaebe) (0x00338ef4)
  17 0x7ee6f1fb in user32 (+0xaf1fb) (0x003393c4)
  18 0x7ee7062b WINPROC_call_window+0x15b() in user32 (0x00339404)
  19 0x7ee36ffc in user32 (+0x76ffc) (0x00339474)
  20 0x7ee3ae22 in user32 (+0x7ae22) (0x003394d4)
  21 0x7ee3b29a SendMessageW+0x4a() in user32 (0x00339514)
  22 0x7ede588f in user32 (+0x2588f) (0x00339604)
  23 0x7ede6466 in user32 (+0x26466) (0x00339624)
  24 0x7ee6a7aa WINPROC_wrapper+0x1a() in user32 (0x00339654)
  25 0x7ee6aebe in user32 (+0xaaebe) (0x00339694)
  26 0x7ee6eeb3 CallWindowProcA+0xa3() in user32 (0x003396e4)
  27 0x00450cf2 in ventrilo 2.1.4 (+0x50cf2) (0x00339704)
  28 0x0045126a in ventrilo 2.1.4 (+0x5126a) (0x00339720)
  29 0x00450302 in ventrilo 2.1.4 (+0x50302) (0x00339780)
  30 0x0045050a in ventrilo 2.1.4 (+0x5050a) (0x0033979c)
  31 0x7ee6a7aa WINPROC_wrapper+0x1a() in user32 (0x003397cc)
  32 0x7ee6aebe in user32 (+0xaaebe) (0x0033980c)
  33 0x7ee6f1fb in user32 (+0xaf1fb) (0x00339cdc)
  34 0x7ee7062b WINPROC_call_window+0x15b() in user32 (0x00339d1c)
  35 0x7ee37516 DispatchMessageW+0x96() in user32 (0x00339d5c)
  36 0x7ee05afb IsDialogMessageW+0xfb() in user32 (0x00339ebc)
  37 0x7ee37a78 IsDialogMessageA+0x68() in user32 (0x00339efc)
  38 0x00453034 in ventrilo 2.1.4 (+0x53034) (0x0047f3a0)
  39 0x00000202 (0x000100f4)
  40 0x00000000 (0x00000000)
0xb7d0e34c memcpy+0x1c in libc.so.6: repe movsl (%esi),%es:(%edi)
Modules:
Module  Address                 Debug info      Name (102 modules)
PE        400000-  492000       Export          ventrilo 2.1.4
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cf99000-7cfdf000       Deferred        riched20<elf>
  \-PE  7cfa0000-7cfdf000       \               riched20
ELF     7cfdf000-7cff3000       Deferred        riched32<elf>
  \-PE  7cff0000-7cff3000       \               riched32
ELF     7cff3000-7d044000       Deferred        libgcrypt.so.11
ELF     7d044000-7d059000       Deferred        libtasn1.so.3
ELF     7d059000-7d087000       Deferred        libcrypt.so.1
ELF     7d087000-7d0f7000       Deferred        libgnutls.so.13
ELF     7d0f7000-7d128000       Deferred        libcups.so.2
ELF     7d18e000-7d1c0000       Deferred        uxtheme<elf>
  \-PE  7d1a0000-7d1c0000       \               uxtheme
ELF     7d1c0000-7d1d5000       Deferred        midimap<elf>
  \-PE  7d1d0000-7d1d5000       \               midimap
ELF     7d1d5000-7d1ed000       Deferred        msacm32<elf>
  \-PE  7d1e0000-7d1ed000       \               msacm32
ELF     7d1ed000-7d227000       Export          wineoss<elf>
  \-PE  7d1f0000-7d227000       \               wineoss
ELF     7d227000-7d2ec000       Deferred        libasound.so.2
ELF     7d2ec000-7d30e000       Deferred        libaudiofile.so.0
ELF     7d31f000-7d339000       Deferred        wineesd<elf>
  \-PE  7d330000-7d339000       \               wineesd
ELF     7d339000-7d342000       Deferred        libxcursor.so.1
ELF     7d342000-7d35f000       Deferred        imm32<elf>
  \-PE  7d350000-7d35f000       \               imm32
ELF     7d35f000-7d367000       Deferred        libxrender.so.1
ELF     7d368000-7d36c000       Deferred        libgpg-error.so.0
ELF     7d36c000-7d376000       Deferred        libesd.so.0
ELF     7df78000-7e1ce000       Deferred        i915_dri.so
ELF     7e1ce000-7e1d7000       Deferred        libdrm.so.2
ELF     7e1d7000-7e237000       Deferred        libgl.so.1
ELF     7e237000-7e23c000       Deferred        libxdmcp.so.6
ELF     7e23c000-7e23f000       Deferred        libxau.so.6
ELF     7e23f000-7e330000       Deferred        libx11.so.6
ELF     7e330000-7e33e000       Deferred        libxext.so.6
ELF     7e33e000-7e343000       Deferred        libxxf86vm.so.1
ELF     7e343000-7e35b000       Deferred        libice.so.6
ELF     7e35b000-7e364000       Deferred        libsm.so.6
ELF     7e364000-7e369000       Deferred        libxfixes.so.3
ELF     7e369000-7e36d000       Deferred        iso8859-15.so
ELF     7e36d000-7e373000       Deferred        libxrandr.so.2
ELF     7e375000-7e3ff000       Deferred        winex11<elf>
  \-PE  7e380000-7e3ff000       \               winex11
ELF     7e50f000-7e52f000       Deferred        libexpat.so.1
ELF     7e52f000-7e55a000       Deferred        libfontconfig.so.1
ELF     7e55a000-7e56e000       Deferred        libz.so.1
ELF     7e56e000-7e5d9000       Deferred        libfreetype.so.6
ELF     7e5d9000-7e677000       Deferred        oleaut32<elf>
  \-PE  7e5f0000-7e677000       \               oleaut32
ELF     7e677000-7e68b000       Deferred        olepro32<elf>
  \-PE  7e680000-7e68b000       \               olepro32
ELF     7e68b000-7e6ad000       Deferred        oledlg<elf>
  \-PE  7e690000-7e6ad000       \               oledlg
ELF     7e6ad000-7e6e2000       Deferred        winspool<elf>
  \-PE  7e6c0000-7e6e2000       \               winspool
ELF     7e6e2000-7e7a0000       Deferred        comctl32<elf>
  \-PE  7e6f0000-7e7a0000       \               comctl32
ELF     7e7a0000-7e7f9000       Deferred        shlwapi<elf>
  \-PE  7e7b0000-7e7f9000       \               shlwapi
ELF     7e7f9000-7e8fc000       Deferred        shell32<elf>
  \-PE  7e810000-7e8fc000       \               shell32
ELF     7e8fc000-7e99d000       Deferred        comdlg32<elf>
  \-PE  7e900000-7e99d000       \               comdlg32
ELF     7e99d000-7e9e6000       Export          dsound<elf>
  \-PE  7e9b0000-7e9e6000       \               dsound
ELF     7e9e6000-7ea3f000       Deferred        rpcrt4<elf>
  \-PE  7e9f0000-7ea3f000       \               rpcrt4
ELF     7ea3f000-7eade000       Deferred        ole32<elf>
  \-PE  7ea50000-7eade000       \               ole32
ELF     7eade000-7eb14000       Deferred        dinput<elf>
  \-PE  7eaf0000-7eb14000       \               dinput
ELF     7eb14000-7eb27000       Deferred        libresolv.so.2
ELF     7eb27000-7eb45000       Deferred        iphlpapi<elf>
  \-PE  7eb30000-7eb45000       \               iphlpapi
ELF     7eb45000-7eb72000       Deferred        ws2_32<elf>
  \-PE  7eb50000-7eb72000       \               ws2_32
ELF     7eb72000-7eb98000       Deferred        msacm32<elf>
  \-PE  7eb80000-7eb98000       \               msacm32
ELF     7eb98000-7ebe0000       Deferred        advapi32<elf>
  \-PE  7eba0000-7ebe0000       \               advapi32
ELF     7ebe0000-7ebec000       Deferred        libgcc_s.so.1
ELF     7ece7000-7eda7000       Deferred        gdi32<elf>
  \-PE  7ed00000-7eda7000       \               gdi32
ELF     7eda7000-7eee5000       Export          user32<elf>
  \-PE  7edc0000-7eee5000       \               user32
ELF     7eee5000-7ef73000       Export          winmm<elf>
  \-PE  7eef0000-7ef73000       \               winmm
ELF     7efa6000-7efb1000       Deferred        libnss_files.so.2
ELF     7efb1000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efef000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c91000-b7c9a000       Deferred        libnss_compat.so.2
ELF     b7c9b000-b7c9f000       Deferred        libdl.so.2
ELF     b7c9f000-b7de0000       Export          libc.so.6
ELF     b7de1000-b7df8000       Deferred        libpthread.so.0
ELF     b7e09000-b7f1d000       Deferred        libwine.so.1
ELF     b7f1f000-b7f3a000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) H:\.wine\drive_c\Program Files\VentriloMIX\Ventrilo 2.1.4.exe
        00000009    0 <==


```

---

### Post by fallenfantasyx on 2007-09-07
i followed this guide word for word my only problem is my mic works but eveytime i talk i get alot of background noise from nothing like someone is welding ive been told...any ideas?

---

### Post by Jttm69 on 2007-09-17
So, the endless question.  Can Ventrilo be used by a Ubuntu user? And can Teamspeak connect to Ventrilo servers?

---

### Post by hikaricore on 2007-09-17
[COLOR="DarkSlateBlue"]Can it be used?[/COLOR]  YES
[COLOR="DarkSlateBlue"]Can it be used **EASILY**?[/COLOR]  Not really.

[COLOR="DarkSlateBlue"]Can Teamspeak connect to Ventrilo servers:[/COLOR]  lol no

[COLOR="Navy"]Will it work?[/COLOR]  Depends on you doing everything right and not getting frustrated.

There are alternatives to using these: [http://mumble.sourceforge.net/](http://mumble.sourceforge.net/)

---

### Post by Christobevii3 on 2007-09-26
When i use wine with ventrilo it lags out the incoming voices after a while and i have to disconnect and reconnect.  Does anyone know what is causing this or a solution?  Thanks!

---

### Post by joaomat on 2007-09-26
Hi guys !!

I'm new to linux, just installed Kurumin in my old laptop after getting tired of the Xtra  slow motion with WinXP.

I'm quite happy with it, just have some problems with my network, as the wireless PMCI card is not recognized on startup, but with time I'll get over it...

This is just to say Thanks to** endy** for his nice tut.
My ventrilo is working like a charm, perfect sound and not lagging at all.

Thanks again !!

:guitar:

---

### Post by sk8dork on 2007-10-03
> **Christobevii3 said:**
> When i use wine with ventrilo it lags out the incoming voices after a while and i have to disconnect and reconnect.  Does anyone know what is causing this or a solution?  Thanks!

i think i had the same problem you are having. 

i was tearing my hair out trying to get vent working the last couple nights. a few weeks ago i had vent working great with wine and wow using OSS (alsa hasn't worked very well in wine for me until version 9.46). don't ask me how, but if i brought up vent first and then wow, i could use OSS in both. since then i've reinstalled ubuntu (currently using xubuntu with openbox) and when i tried vent again a few days ago i kept getting the GSM codec error. i had the msgsm32.acm file in the right place, had the line added to my system.ini, but it still wouldn't work. i reinstalled vent, still nothing. i read somewhere (maybe this thread) where someone didn't have a system.ini so they only added the one line mentioned in the first post (two lines if you consider they had to add the [drivers32] line). since i already had a system.ini i decided to make a backup of it and clear it out except for just the [drivers32] line and the MSACM line from the first post, this solved my GSM codec problem.

which brought me to the problem the person is having that i quoted. whether connected to a server or not, when testing in the setup screen or when trying to chat in a server, it would work for a short while and then stop. either the push to talk button would stick in the on or off mode or sound would just stop. i figured out that i had to have output sound settings checked for directsound, but input sound unchecked for directsound. i am now able to chat in the vent server perfectly fine. i have winecfg set to use alsa with hardware acceleration set to full, driver emulation checkbox checked, both vent and wow sound great. i have to have the check box checked for directinput or whatever in vent setup for the push to talk key to work with wow focused and vent in the background.

---

### Post by Lord C on 2007-10-19
Thanks for the guide, was useful. I always forget that darn windows system dll.

By the way guys, look up [mumble]("http://mumble.sourceforge.net/"). It's just like Ventrilo.
I'd rather use Vent or Mumble, because TeamSpeak has very poor sound quality ime.

---

### Post by SanCo.ac on 2007-10-29
./findkey command doesn't work, anyone wanna help.. annoys me to death that NONE has a answer to this.

---

### Post by Goronok on 2007-10-29
> **SanCo.ac said:**
> ./findkey command doesn't work, anyone wanna help.. annoys me to death that NONE has a answer to this.

Not sure what you could be doing wrong, but from your ventriloctrl directory run :

sudo ./findkey /dev/input/event*

replace * with 0-6 until you find one that will function with your keyboard. /event1 is what ended up working with my Dell E1705 notebook.  If the first one you try Ctrl-C to stop the script and try another number.

Hope this helps.

---

### Post by SanCo.ac on 2007-10-29
nope, that's what I did, do I need to place it some special dir or something

---

### Post by Zaiden on 2007-10-30
Will this guide work with Ventrilo 2.1.1, or only the newest version?

---

### Post by MemoryDump on 2007-10-31
> **Zaiden said:**
> Will this guide work with Ventrilo 2.1.1, or only the newest version?

should work with any version

---

### Post by boolat on 2007-11-01
hello,

I just installed ventrilo 2.3.0,
In the setup I have no microphone ?

hardware --> line :  option no microphone ?

[IMG]http://img259.imageshack.us/img259/8299/snapshot7tu7.jpg[/IMG]

thx

---

### Post by Nhira on 2007-11-03
I'm trying to access the Setup in ventrilo but everytime I push this button Ventrilo closing.

Any idea what's happening or how I can solve it?


Btw, I can listen the others really good -_-

---

### Post by sonicborg on 2007-11-06
get it working almost fine.
 sound works fine, USB mic (usb headset) works fine, and when i have the program in focus i can push to talk

but when i come off focus, then i lose push to talk faciility, and this script doesnt work no matter how many options i correct in it.

---

### Post by Zaiden on 2007-11-11
I attempted trying to get the push to talk key working through the instructions, but there is absolutely no ./findkey command. No matter how many times I tried through the terminal, ./findkey would not work.

---

### Post by Lord C on 2007-11-12
Flasgship said they'd started coding a GNU/Linux version of Ventrilo years ago (05-30-2005, 01:10 PM).

[QUOTE=Flasgship]The Ventrilo / Linux client tech support forum is here pending the official release of the client.

The forum will be activated once the first release is made available.

Thank you for your support and interest in the Linux client.

At the current time we do not have an official release date. Once we do it will be posted here and possibly some indication on the download page.

--Flag[/QUOTE]

If all the people here with Ventrilo/Wine problems could start requesting on the official Ventrilo forums - maybe we could get them to release a beta, or even alpha of the GNU/Linux version. 

Whatever they have so far, is better than nothing, right?

[http://www.ventrilo.com/forums/showthread.php?p=88149#post88149](http://www.ventrilo.com/forums/showthread.php?p=88149#post88149)

Personally I use Mumble these days, which I find to have every feature that I used on Ventrilo, if not more. The only problem is, as I know a lot of you will say, people already have Ventrilo servers etc, and migrating people to another client is always a headache.
But if your friends believe in the FOSS philosophy, shouldn't be that hard really.

---

### Post by Nhira on 2007-11-17
Hello.

I download Ventrilo 3.0.0 this morning, when I select to install it I got the message;
Ventrilo 2.3.0 is already installed and you need to unistall it in order to instal Ventrilo 3.0.0
Do you want to unistall it?

I select Yes but nothing happened, so I unistall it manually.

Now I'm trying to make Ventrilo 3.0.0 run and it says;
Ventrilo 3.0.0 is already installed and you need to unistall it in order to instal Ventrilo 3.0.0
Do you want to unistall it?

But.. the only thing named as Ventrilo I have is this damn .exe!
And I can't install it..

Any idea what's happening?
It's driving me crazy... I tried every thing I know but nothing..

---

### Post by bpdiomus on 2007-11-17
Hi Nhira,

Have u tried to remove from your system.reg, user.reg and userdef.reg anything that refers to Ventrilo? (in your ~/.wine directory)

I've found only one post mentionning this and it was the one that helped me.
Spreading the word.

bpdiomus

---

### Post by Blindey on 2007-11-18
I just downloaded Ventrilo 3.0.0 and am using it through Wine (0.9.49).

So far I haven't discovered any problems, except I am unable to talk.

I can hear everybody very clearly, and even my PTT works (I can hear the "beep" each time I press it, but they aren't able to hear me.

Any suggestions on what i should do in order to get that working?

I really appreciate it!

---

### Post by Ferrat on 2007-11-19
Im running both WoW and Ventrilo without any problems, can both hear and talk on vent and got game sound and no problem with the focus being needed for push to talk (vent v.2.14)

---

### Post by cibercanon on 2007-11-20
i keep getting 
Failed to get encoder for specified Codec.

Unable to initialize outbound codec (GSM 6.10 - 11 KHz, 16 bit): Unable to find the specified codec no matter what i do

---

### Post by poompt on 2007-11-28
> **cibercanon said:**
> i keep getting 
Failed to get encoder for specified Codec.

Unable to initialize outbound codec (GSM 6.10 - 11 KHz, 16 bit): Unable to find the specified codec no matter what i do

I'm getting the same problem, I added MSACM.msgsm610=msgsm32.acm to system.ini and copied msgsm32.acm first from a Windows installation and then a downloaded version to ~/.wine/drive_c/windows/system/, and yet I still get this error whenever I try to connect to a server. Anything I missed or that might resolve this issue?

---

### Post by arxix on 2007-12-03
> **poompt said:**
> I'm getting the same problem, I added MSACM.msgsm610=msgsm32.acm to system.ini and copied msgsm32.acm first from a Windows installation and then a downloaded version to ~/.wine/drive_c/windows/system/, and yet I still get this error whenever I try to connect to a server. Anything I missed or that might resolve this issue?

I get the same thing. I just upgraded to 3.0.1 and I get it in both versions. 

Any other thoughts?

EDIT!
I replaced my copy of the msgsm32.acm file ( copied from my XP 64 pro partition) with the one [COLOR="Silver"]from the link in the first post in the thread[/COLOR] and magically it works! I guess the one I had from before doesn't like wine.

The link that had the file is no longer valid. If someone would like to host it, please do. 

I will post 

Hope this helps everyone!
-ArXiX

---

### Post by ABX on 2007-12-17
Following this guide I've managed to install Ventrilo on my Ubuntu. I had to play a little with some files to remove all the errors and now it's ok.

But my microphone stops working after 4-5 minutes of starting Ventrilo. The only way to make it work again is to restart Ventrilo clinet. I can hear all the time tho.

---

### Post by kguthrie on 2007-12-17
I got push to talk working, but only when Ventrilo was in focus.  Also, I had full sound in Ventrilo when it was running by itself, but when I started WoW through Wine, I lost sound in both and couldn't hear anything, and PTT also stopped working.  Anyone know what the deal is?

---

### Post by asnd16 on 2007-12-19
> **Nhira said:**
> Hello.

I download Ventrilo 3.0.0 this morning, when I select to install it I got the message;
Ventrilo 2.3.0 is already installed and you need to unistall it in order to instal Ventrilo 3.0.0
Do you want to unistall it?

I select Yes but nothing happened, so I unistall it manually.

Now I'm trying to make Ventrilo 3.0.0 run and it says;
Ventrilo 3.0.0 is already installed and you need to unistall it in order to instal Ventrilo 3.0.0
Do you want to unistall it?

But.. the only thing named as Ventrilo I have is this damn .exe!
And I can't install it..

Any idea what's happening?
It's driving me crazy... I tried every thing I know but nothing..

I have the same issue!!!

---

### Post by kr0n1x on 2007-12-29
i've ubuntu gutsy 64bit and i can't hear other players in ventrilo, but i can hear ventrilo sounds (like warning etc)

i've this error:
```
Codec initialization failed:
Unable to find the specific codec
```

---

### Post by murka10 on 2008-01-01
Hi,
i start ventrilo 2.1.3, under setup i can't select my line... same problem like the person on page 18 has.
anyone know a fix?
[IMG]http://img232.imageshack.us/img232/2043/85578579ff3.jpg[/IMG]

---

### Post by SvenW on 2008-01-02
Running the ventriloctl program (actually the runctrl.sh script) results in:

"Could not find Ventrilo window. Is Ventrilo running?"

I am staring at the open Ventrilo window so I am not sure why the script cannot find the window. If I remove the comment marks from the ventriloctrl.c so that it prints all the windows out, I see all my open windows being listed *except* the ventrilo window . . .

---

### Post by kr0n1x on 2008-01-04
i solved my problem with ventrilo 2.1.4 and ubuntu gutsy 64 bit.

i readed 2 pages... i think i fixed my problem checking the codec file permissions.

i changed also the position of the new line in system.ini file... but putting it again at the last line it works anyway...

2 useful pages:
[http://slinux.net/how-to-install-ventrilo-2-3-on-linux](http://slinux.net/how-to-install-ventrilo-2-3-on-linux)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3668](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3668)

good luck... anyway i'm using the 64bit version of msgsm32.acm (i think it is...) it is 19,5 kb.

---

### Post by arxix on 2008-01-04
> **kr0n1x said:**
> i solved my problem with ventrilo 2.1.4 and ubuntu gutsy 64 bit.

i readed 2 pages... i think i fixed my problem checking the codec file permissions.

i changed also the position of the new line in system.ini file... but putting it again at the last line it works anyway...

2 useful pages:
[http://slinux.net/how-to-install-ventrilo-2-3-on-linux](http://slinux.net/how-to-install-ventrilo-2-3-on-linux)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3668](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3668)

good luck... anyway i'm using the 64bit version of msgsm32.acm (i think it is...) it is 19,5 kb.

The file I sent you is NOT the WIN x64bit one. If you try to use the file from a WIN x64 partition it will not work, you have to get the file from driversguide.com or a non x64 version of windows. Or as Kronix did, he got it from me. 

Anyone want to host the correct version of the file for others to download?

Hope this helps some people.

-ArXiX

---

### Post by sh!ft on 2008-01-14
I managed to make it work with arxix's help.

Put the file in the "/home/youruser/.wine/drive_c/windows/system" .. NOT system32.

Add the line to system.ini like it says, and then go into system32 and create a symbolic link to the system folders copy of msgsm32.dll.

IT ONLY WORKS with the file that is "24.5 KB (25088 bytes)" in size. 

The 19kb breaks to high heaven, as does the smaller one.

BTW I'm running gutsy x86_64, enjoy.

---

### Post by andrewjoy on 2008-01-26
Do we have any way to find out the protocall that vet uses to connect and emulate it in another program the same way pidgon connects to msn google talk ect ?

Or do vent servers have sum sort of check to confirm its a vent cliant ?

---

### Post by Totaltech on 2008-01-29
> **endy said:**
> I'm sure I'm not alone when I say I've been trying to get ventrilo working for a while. Well today I got it working with no hastle and since a quick search here for 'ventrilo' turned up only one topic I thought I'd post what I found :D

Note: The version of wine I used was from the backports repository, I haven't tried any other version so step 1 may be unnecessary.

1. Add the extra repositores from the Unnoffical Ubuntu Guide:
```

[http://www.ubuntuguide.org/#repositories](http://www.ubuntuguide.org/#repositories)

``` 

2. Install the following packages:
```

wine (version 0.0.20050419-1~5.04ubp1)
libwine (version 0.0.20050419-1~5.04ubp1)
libwine-alsa (version 0.0.20050419-1~5.04ubp1)
cabextract

``` 

3. Download Ventrilo: 
```

[http://www.ventrilo.com/download.php](http://www.ventrilo.com/download.php) 

``` 

4. Make a directory for ventrilo and extract it:
```

mkdir ~/ventrilo
cd ~/ventrilo
cabextract /path/to/ventrilo-2.2.0-Windows-i386.exe

``` 

5. Edit the file:
```

~/.wine/drive_c/windows/system.ini

``` 

And add the following line:
```

MSACM.msgsm610=msgsm32.acm

```

6. Next you need to get your hands on the windows file 'msgsm32.acm' from an existing windows partition (C:/WINDOWS/system32/msgsm32.acm) and copy it to  '~/.wine/drive_c/windows/system/'.

7. Run vent:
```

cd ~/ventrilo
wine ./Ventrilo.exe

```

I hope it works, and I also hope I'm didn't state the obvious  :razz:

I have to preface this with this is only my second day using Ubuntu so please forgive my ignorances.  I have installed all the packets but when i try to do the cabextract in step 4 I get a file does not exist

totaltech@totaltech-laptop:~/ventrilo$ cabextract /home/totaltech/Desktop/ventrilo-2.2.0-Windows-i386.exe
/home/totaltech/Desktop/ventrilo-2.2.0-Windows-i386.exe: No such file or directory

please help the very very new guy.

thanks in advance

---

### Post by SBFC on 2008-02-09
> **murka10 said:**
> 
i start ventrilo 2.1.3, under setup i can't select my line... 

I'm experiencing the same problem. I've tried Alsa, OSS, and both. 

What's really driving me crazy is the fact I've had Ventrilo working with this soundcard before, only on a different system. But now, for whatever reason, just refuses to work.

---

### Post by applezip on 2008-02-09
I cannot get ventriloctrl to use tilde (~ and `) as a key.

Other keys I can get working, like letters, but I can't get ~ to work.

---

### Post by Sil3n7 on 2008-02-23
Hey, this is my first post here and i am really trying to make the complete switch from windows to ubuntu, all i have left is to get vent working.

I have done all of the steps on the first page and i believe i did them correctly, but when i try to run Ventrilo.exe with wine i get the error:

SHGetSpecialFolderPath failed.
Program aborting

in a pop-up.  My terminal also gives me the error:

```
fixme:ntdll:FILE_GetNtStatus Converting errno 40 to STATUS_UNSUCCESSFUL
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\drew\\Application Data".
```

i also get the second error when i run Warcraft 3 also.  I'm very new to ubuntu so this could be a very obvious fix that i just missed. TY for any help

---

### Post by bulazeem on 2008-02-23
It took me FOREVER to find out how to do this but once i found hikaricore's post, I was able to get ventriloctrl working in about 5 min.  However, i still have one problem.  Ventrilo now keys my microphone when i press tab (which is what i set it to) as well as "a".  Any help there?  Is there a way i can change the "a"?


edit:  i think it does this because ventrilo is set to push to talk button "a" and so when i am in a game like wow and wow has the focus, since it is in wine just like ventrilo, a actually sends the signal to key the microphone.

---

### Post by ScottyBoyNow on 2008-02-24
I can get it to work with sensitivity, to talk. But whenever I try use PTT, it doesn't. I am going to see if the ventriloctrl thing will work. If not, I am buggered!

Edit! 

I can get the insert working now. I just got the OSS Drivers sorted out and that fixed it. Only problem now is the background Ventrilo with the 'insert' key.

---

### Post by Sammi on 2008-02-24
@Sil3n7
Have you tries running winecfg once to create the default Windows folders?

Just write winecfg in a terminal and press enter.

---

### Post by Sil3n7 on 2008-02-26
yes, i have run the winecfg in terminal and when i browse the drive_c i have both the windows folder and Program Files folder.  Still getting the same error though.  i toyed around with using different versions of windows also but no luck there.

---

### Post by dutyandcourage@gmail.com on 2008-02-29
I followed this guide and my vent allowed me to connect to servers and listen in on conversations. However I had some trouble with push to talk and lag while playing other games. After an hour of fiddling around I found that enabling hardware acceleration in the sound tab of the wine configuration utility solved this problem.

Also I was getting Abs Zero when I tried monitoring in the ventrilo client setup. I fixed this by enabling mic boost in the ubuntu volume control. I did this by opening my volume control opening preferences in the edit menu and then finding the Mic Boost (+20 DB) option and checking the check box. This enables the option in the switches tab of the volume control which you also have to check.

After that my vent was working perfectly. Still a couple sound glitches here and htere but they are hardly a problem.

---

### Post by Metaleks on 2008-03-15
Okay, first let me start off by saying vent runs perfectly.  Perfectly!

But.  I can't seem to get runctrl to work.  I've followed the guide to the word, any ideas as to what my problem may be?

---

### Post by Lazy8s on 2008-03-22
Bah I got my sound card ( X-Fi platinum ) to run with drivers I found here [http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi) but Ubuntu does not recognize me as having a sound device still. Now when I run ventrilo from wine I see:

> 
~/ventrilo$ wine ventrilo
err:mixer:MIX_Open ioctl( /dev/mixer, SOUND_MIXER_DEVMASK ) failed ( Invalid argument )
err: ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396 } not registered
err: ole:CoGetClassObject class c7a-45ac-92cc-59edafb77b53 } could be created for context 0x17
{96749377-3391-11d2-9ee3-00c04f797396 } not registered
err: ole:create_server class {96749377-3391-11d2-9ee3-00c04f797396 } not registered
fixme: ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err: ole:CoGetClassObject no class object {96749377-3391-11d2-9ee3-00c04f797396 } could be created for context 0x17
err: ole:CoGetClassObject class {a910187f-0c7a-45ac-92cc-59edafb77b53 } not registered
err: ole:CoGetClassObject class {a910187f-0c7a-45ac-92cc-59edafb77b53 } not registered
err: ole:create_server class {a910187f-0c7a-45ac-92cc-59edafb77b53 } not registered
fixme: ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err: ole:CoGetClassObject no class object {a910187f-0


And when I join a vent server I get the message:

> 
VoiceCommMixerStart: Non-mux based mixer does not have any connections.


Under Setup I choose Soundblaster X-FI as Output ( direct sound checked ), Default DirectSound device as input ( use direct sound checked ).

Then for hardware input mixer I have Mixer: Sound Blaster X-Fi, Mux:rec and then there are no choices for Line. I take this to mean my soundcard won't let me use my mic then?

---

### Post by SBFC on 2008-03-24
> **Lazy8s said:**
> 
Then for hardware input mixer I have Mixer: Sound Blaster X-Fi, Mux:rec and then there are no choices for Line. I take this to mean my soundcard won't let me use my mic then?

I'm having problems with the Line selection as well. Also, I don't even have a choice for Mux. I've had Vent working with this soundcard before, although I can't remember how many versions ago.

I can connect to a server and listen to conversations...just can't seem to get Line working so that I can talk. Very frustrating.

I've tried both ALSA and OSS.

---

### Post by Louis Cypher on 2008-03-26
Finally got Vent working with World of Warcraft.  This is the most recent patch. 2.4 i think.  I tried a bunch of different setups but in the end this worked for me.  This info was taken from the Winehq website.

> First time it works flawlessly for me.
by Alexander Lindskog on Wednesday December 12th 2007, 7:44
Hi guys.

I managed to get Vent running without any of the problems I used to have (no ALSA, no Push-to-talk). I'm positive it has something to do with the latest wine update but in case this helps you here are the settings I used. (all other combinations failed to work :) )

Wine 0.9.50

Winecfg:
-Audio:
--ALSA
--Hardware acceleration: Full
--Driver emulation: Checked

Vent:
Output device: Default DirectSound device
-Use Direct Sound: Checked

Input device: Default wave mapper
-Use Direct Sound: Not checked

Use Direct Input to detect Hotkey: Not checked

The only thing I did not need was the last line, Use Direct Input to detect Hotkey: Not checked.  I left it checked and all is well.  Also in WoW make sure the option under Sound & Voice --> Sound Options--> Game Sound Output-->  uncheck Use Hardware.

The push-to-talk works great and the sound is just like in Winblows.  The only problem, which is not a problem really, is after the character select screen there is beep from the speakers but that lasts less than a second.

I'm running Ubuntu 7.10+Gnome
Dell XPS 410n
audio is Sigmatel STAC9227

---

### Post by MemoryDump on 2008-03-26
> **Louis Cypher said:**
> Finally got Vent working with World of Warcraft.  This is the most recent patch. 2.4 i think.  I tried a bunch of different setups but in the end this worked for me.  This info was taken from the Winehq website.



The only thing I did not need was the last line, Use Direct Input to detect Hotkey: Not checked.  I left it checked and all is well.  Also in WoW make sure the option under Sound & Voice --> Sound Options--> Game Sound Output-->  uncheck Use Hardware.

The push-to-talk works great and the sound is just like in Winblows.  The only problem, which is not a problem really, is after the character select screen there is beep from the speakers but that lasts less than a second.

I'm running Ubuntu 7.10+Gnome
Dell XPS 410n
audio is Sigmatel STAC9227

how did you setup the push-to-talk? just vent itself? or the script mentioned in this post?

---

### Post by Louis Cypher on 2008-03-26
The push-to-talk was setup in vent.  I didn't use the script in this post.  Also I'm running WoW in windowed mode, under video options, with Maximized option selected.  Hope that helps

---

### Post by SBFC on 2008-03-26
> **Louis Cypher said:**
> 
The only thing I did not need was the last line, Use Direct Input to detect Hotkey: Not checked.  I left it checked and all is well.  Also in WoW make sure the option under Sound & Voice --> Sound Options--> Game Sound Output-->  uncheck Use Hardware.

Thanks for posting this...Vent actually works now..even if I have nothing selected for Mixer, Mux, and Line.

Only problem now is that PTT isn't working...even with VentriloCtrl...more tinkering to do yet.

---

### Post by Shadowfire on 2008-03-31
> **endy said:**
> Anyway I eagerly await Teamspeak 3 and a native Ventrilo for linux, I only wish we had a GPL product in the mix but seeing as I can't code that myself I wont complain :)

Endy, 

Just FYI, there is a GPL product called Mumble.  You can get it here:

[http://mumble.sourceforge.net/]("http://mumble.sourceforge.net/")

I use it... It is wonderful.. Infact TS3 will be stealing something that it has been doing for a long time - 3D positional audio.  Check it out. 

Enjoy!

---

### Post by Coolbreeze... on 2008-04-01
So, Theoretically could we Recode Ventrilo to run on Linux? If I were to attempt this what kind of programming language does Ventrilo use?...C++ or some thing else...any one know?  Then I assume I'd be converting it to some type of UNIX language.  

Anyone know what 2 languages and where I can fin documentation on each of them.   And possibly some kind of Editor...what program would I use to edit the code then compile it?

Or am I just an Idiot and this is basically Impossible?

Thanks

---

### Post by Anamatronix on 2008-04-03
Long time reader, first time poster :P

I've been reading and rereading this thread, struggling to get vent running. And I have (woot). However I've gotten to the point a lot of posters have, and that is I can't get my mic to be recognised and actually speak to people. Similar to someone posting ealier, using a logitech usb headset; I don't get lag or any probs with hearing people. 

I've only really just started using ubuntu, so I'm fairly noob. So people who have gotten their mics working, can we please get a little more detailed discription? I don't need PTT or WoW or anythign else running- just need to be able to talk :P 

Appreciation will be shown with caek for any help :)

---

### Post by Sammi on 2008-04-04
> **Anamatronix said:**
> Long time reader, first time poster :P

I've been reading and rereading this thread, struggling to get vent running. And I have (woot). However I've gotten to the point a lot of posters have, and that is I can't get my mic to be recognised and actually speak to people. Similar to someone posting ealier, using a logitech usb headset; I don't get lag or any probs with hearing people. 

I've only really just started using ubuntu, so I'm fairly noob. So people who have gotten their mics working, can we please get a little more detailed discription? I don't need PTT or WoW or anythign else running- just need to be able to talk :P 

Appreciation will be shown with caek for any help :)Do you hear yourself in the headphones when you speak in the microphone?

If not then the mic might be turned off in the audio mixer app you can find in the top right corner, besides the clock.

---

### Post by Louis Cypher on 2008-04-09
Just a follow up to using Vent with WoW.  I haven't changed my settings from the previous post, they are working fine.  I was having a problem when holding the ALT key while fighting, I use macros, and I would be pressing the right mouse button at the same time.  When I did that I would get a Metacity right-click menu.  Needless to say this sucked and would sometimes lock up the ALT button which screwed Vent from capturing my PTT button.  This is what I did to disable that from happening:

I use gconf-editor installed from the repo's

1. Launch gconf-editor
2. go to apps->metacity->general
3. in the right pane scroll to the option **mouse_button_modifier**
4. Double click and change <Alt> to <Super> or <Ctrl> or <Shift> or any other key you want to use.

Like I said this was a minor annoyance but maybe this will help someone else.

---

### Post by Mushed on 2008-05-07
So I've been trying to get Wine and Vent going for a while now, but I keep running into some problems. 
I'm running Hardy LTS and the newest Wine whatever version that might be. 
So I can get sound through Vent where I can hear eveyone talking, but no matter what I do I get this error: Failed to open input device. Another program might have it open already. rc = -10
There is no other program open. 
I have my wine set up as OSS, driver emulation on. And I have tried many other variations and differnt settings. 
Pleaze Halp.

---

### Post by Sammi on 2008-05-10
> **Mushed said:**
> So I've been trying to get Wine and Vent going for a while now, but I keep running into some problems. 
I'm running Hardy LTS and the newest Wine whatever version that might be. 
So I can get sound through Vent where I can hear eveyone talking, but no matter what I do I get this error: Failed to open input device. Another program might have it open already. rc = -10
There is no other program open. 
I have my wine set up as OSS, driver emulation on. And I have tried many other variations and differnt settings. 
Pleaze Halp.The problem is that Wine is using OSS. OSS is old and technically challenged. It doesn't allow more than one program to access the sound card at a time. Ideally you should use the newer ALSA in stead, but it doesn't work that well for everyone in Wine. That why I've written this guide for routing OSS through ALSA, by using a little and genious application named alsa-oss:

 [https://help.ubuntu.com/community/WorldofWarcraft#head-9f4c9e2df7bf2ce0429e495e9e6e55f58eac4e49](https://help.ubuntu.com/community/WorldofWarcraft#head-9f4c9e2df7bf2ce0429e495e9e6e55f58eac4e49)

---

### Post by ducks on 2008-05-10
i think i have figured it out i have edited the runctrl.sh file to use left ctrl but in vent i have it set "a" as the hot key and it works fine :)

---

### Post by noob of all noobs on 2008-05-14
hello.
 I just siwtcheds over to ubuntu 8.04 this week after using windows for many years. After much diffiulty I have gotten everything to work except xfi drivers (had to resort to onboard sound) which is not an issue. Now I'm trying to get ventrilo to work in wine and I have no sound. I followed all of the how-to's I could find [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9832](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9832)
etcetc but no luck. I've tried to run it using OSS, ALSA and tried to run it with alsa-oss and got these errors:


ephex@ephex-desktop:~$ aoss wine /ephex/.wine/drive_c/Program\Files/Ventrilo/Ventrilo.exe
ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
wine: cannot find '/ephex/.wine/drive_c/ProgramFiles/Ventrilo/Ventrilo.exe'
ephex@ephex-desktop:~$ 

maybe I'm doing something unbelievably stupid (more then likely) but I  don't know what it is. As I've been looking through these forums for 2 days now this is a last resort. I hope this is enough information sorry for being such a linux noob.
thanks in advance!

---

### Post by katyl on 2008-05-15
Noob, 
If you're copy and pasting that, looks like your missing the /home at the start of the command...

aoss wine /home/ephex/.wine/drive_c/Program\ Files/Ventrilo\Ventrilo.exe 
Make sure you're getting the proper case on the file name, but if I remember right from when I had vent installed, it's right.

---

### Post by TuckLive on 2008-05-20
I'm running Wine in 8.04 and when I try to connect to a server I get an error about not having the codecs.  Where can I get these and where would they go?

---

### Post by Sammi on 2008-05-20
> **TuckLive said:**
> I'm running Wine in 8.04 and when I try to connect to a server I get an error about not having the codecs.  Where can I get these and where would they go?
That's covered in steps 5 and 6 in the guide.

---

### Post by Christor on 2008-05-26
I'm running Wine in 8.04 in a 64-bit environment and I just finished installing Ventrilo 2.1.4.
I added "MSACM.msgsm610=msgsm32.acm" to the system.ini file and I added msgsm32.acm to the system directory.

Here is my issue: I still get the "Codec Initialization failed: Unable to find the specified codec." error.


And before you post an answer, YES! I have done all the steps provided in the HowTo correctly and I have set Ventrilo to use the GSM 6.10 codec.
(DSP Group TreuSpeech and Lernout & Hauspie works, but the Ventrilo server use GSM 6.10 codec)

*Fixed
I had a msgsm32.acm both in system and system32 directory, Ventrilo was probably not sure which one to use.

---

### Post by Vidar' on 2008-05-27
Did all this, and I too have a problem with the GSM codec..

Removed msgsm file from system32 so it was only in system, and it still doesn't work. Downloaded all GSM codec files via synaptic but that didn't help.

Any ideas?

> Failed to get encoder for specified Codec.

Unable to initialize outbound codec (GSM 6.10 - 44 KHz, 16 bit): Unable to find the specified codec.

P.S. Can't hear anyone, or broadcast.

---

### Post by cykotiktek on 2008-06-08
Ok i am stuck I play WoW on 8.04 no real issues but with ventrilo I can speak they can hear me but i can't hear them.  I have tried all of the different settings in ventrilo and i have had it working in the past I am wondering if an update didn't kill something.  

Also if i am playing WoW i can only have sound from one thing like if i start WoW first vent will not work at all but if i start vent i have no sound in wow

---

### Post by BongoBob on 2008-06-09
Hello everyone.

I have followed every step in both the Ventrilo and Ventctrl guide, and have a problem. Vent runs, and I am able to connect to my World of Warcraft Guild's Ventrilo server. However, upon connecting, after 2 or 3 seconds I am unable to push the button to talk. It doesn't register the button. If I go into settings and reset the keybinding, it works again for 2 or 3 seconds before it stops working again.

Any tips on how I can solve this?

---

### Post by blithen on 2008-06-12
> **hikaricore said:**
> --Incase anyone else stumbles upon this post,
--You can download ventriloctrl here: [http://np1.pp.fi/ventriloctrl/ventriloctrl-0.3.tar.gz](http://np1.pp.fi/ventriloctrl/ventriloctrl-0.3.tar.gz)
--I've also mirrored it here just incase the creator's site is down: [http://hikaricore.googlepages.com/ventriloctrl-0.3.tar.gz](http://hikaricore.googlepages.com/ventriloctrl-0.3.tar.gz)

You need to compile ventriloctrl to run it.

Direct from the README file:


So you will first need to install build-essential if you never have:

```
sudo apt-get install build-essential
```

Then the development libraries for Xorg (this should be enough):

```
sudo apt-get install xorg-dev
```

Then run:

```
make
```

From the directory you extracted ventrilocontrol into.

it should output something like this:



If get an error, let me know I'll try and figure out what dev files I missed.

Now for configuring it, this part is fun.

You will need to find out what device your system uses for input.  For example on my system it's:

**/dev/input/event1**

Yours may differ.  So you need to run

```
**sudo** ./findkey /dev/input/event#
```

Replacing the # with numbers ranging from 0 to 6, example:

```
**sudo** ./findkey /dev/input/event0
```

Upon running this command press some keys on your keyboard, if you don't see any output in the terminal hit Ctrl+C to exit the program and try the next number.  Like I said it varries.



Once you find the correct /dev/input/event# press the key you want to use for vent, remember the number it outputs in the terminal, then you'll need to edit the **runctrl.sh** file.

```
pico runctrl.sh
```

Which will look something like this:

```

# Config, see README for instructions
EVENT_DEVICE="**/dev/input/event1**"
INPUT_KEY="**97**"


# Don't touch
./ventriloctrl $EVENT_DEVICE $INPUT_KEY

```

Replace the input_key with the number from the key you chose for your vent key, then replace (if needed) the /dev/input/event# with the one you found to work on your system.

Hit Ctrl+o to save.  Then Ctrl+x to close pico.

Now for the tricky part.

Ventrilo Control requires the ability to read and write to the device you've chosen.

There are a number of ways to do this but I'll tell you the one that will work and stay working.
 
We're going to write a udev rule so that the group ventrilo has read/write access to your event device.

```

sudo groupadd ventrilo
sudo gpasswd -a **YOURUSERNAME** ventrilo

```

Replace YOURUSERNAME with the username you plan to be using on Ubuntu at the time of running vent.

Now to write the udev rule.

```

sudo pico /etc/udev/rules.d/10-local.rules

```

This may bring up a new blank file, this is pretty much expected in newer versions of Ubuntu.
But no worries, time to move on.

In this file, type or paste the following:
(Replacing the ??? with the number of the /dev/input/event# device you found to work, for example if it was /dev/input/event2, replace ??? with the number 2.)

```
KERNEL=="event[???]", NAME="input/%k", GROUP="ventrilo", MODE="0660"
```

Hit Ctrl+o to save and Ctrl+x to exit pico.

One last step, we need to reload udev.

```
sudo /etc/init.d/udev restart
```

Now you should be able to run the file in your ventriloctrl directory called **runctrl.sh**.

```
./runctrl.sh
```

You will need to have vent running before you start this script.

If all goes well you should be able to go into the vent settings and set your key, with the key you chose to use.  It will probably show as the A key when you hit that key, but this is the default of the ventriloctrl program and I'm not even going to begin telling you about modifying that.  :P  In most cases this should work perfectly.

Let me know if you have any problems.

--Aaron

Sources used for figuring out this damn mess:
[random thoughts : by Imago]("http://imago.devinity.de/")
[Writing udev rules]("http://reactivated.net/writing_udev_rules.html")
Incase anyone needs to further understand the udev segment.
this doesn't work for me I need more help. it just doesn't work.

---

### Post by byzantines2000 on 2008-06-20
I have an issue stating that it is "unable to activate directsound for selected device. DirectSoundCaptureCreate failed, hr = 80004005"

where did I go wrong? lol

---

### Post by edkuk13 on 2008-06-20
I have found a solution to my problem without much stepwork. I am using Ubuntu 8.04, vent 3.x, and wine 1.0. Follow this link and easy steps and it may work for you.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9832](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9832) 

Eric

ps I had to use ALSA for WoW, Vent, and Ubuntu 8.04

I used WoW in full screen

---

### Post by hikaricore on 2008-06-21
> **blithen said:**
> this doesn't work for me I need more help. it just doesn't work.


I wrote that guide over a year ago and it seems it no longer works the same way with the new version of Ventrilo.
I've added a warning to the top of my original post and will be removing the link from my signature line.

Best of luck,


--Aaron

---

### Post by Mahinva on 2008-06-21
In following the instructions [_here_](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9832), I find myself unable to locate the "system.ini" file that should be found in /.wine/drive_c/**windows**/. I found this thread, and attempted to follow step 5, however this seems to verify that no system.ini files exists.

Where can I find a copy of system.ini? If someone posts the contents of their system.ini (a copy that's not been modified) - could I essentially copy that text and create a system.ini of my own?

Alternatively, since I am dualbooting Ubuntu and Windows XP - I could look for a system.ini file in XP. However, I am uncertain whether the file in XP has been altered - I'm uncertain the purpose of system.ini and don't want to risk putting a file that may confuse Wine somehow. Is it okay just to go into XP and copy the system.ini file?

I already have "MSACM.msgsm610=msgsm32.acm" installed it in the appropriate folder.

---

### Post by darkpck on 2008-06-29
Worked for me. Thanks a bunch.~

---

### Post by locosway on 2008-07-08
> **hikaricore said:**
> I wrote that guide over a year ago and it seems it no longer works the same way with the new version of Ventrilo.
I've added a warning to the top of my original post and will be removing the link from my signature line.

Best of luck,


--Aaron

After spending a few hours reading this thread and others like it I've come to the conclusion that PTT is broken in the current version of wine/ventrilo.

Hikaricore, not sure if you're planning on working on a newer version of your script. It would be nice if you would get something working and then submit it to wine so they can think about incorporating it. If I knew how to program I'd do it myself.

Either way, if someone knows how to get PTT working in Vent without having it as the focus I'd be interested to hear how you did it.

---

### Post by trashguy on 2008-07-09
I have gotten PTT to work on my mouse with ventrolctrl. You just have to make 2 changes:

Edit ventriloctrl.c:

You can change this line to any key you want that is supported by linux/input.h Here is a list: [http://lxr.linux.no/linux/include/linux/input.h](http://lxr.linux.no/linux/include/linux/input.h)

#define KEYCODE XK_A

I use T just because it isn't a key I use in WoW

#define KEYCODE XK_T

Save the file and go throught he make porcess. Then edit runctrl.sh  On my G5 mouse the thumb button is 275

EVENT_DEVICE="/dev/input/event2"
INPUT_KEY="275"

So far everything has been working out, hope that helps some people,

---

### Post by tisepti on 2008-07-11
Ive run into an error where ventrilo is unable to play voices coming in. I am able to hear other sounds of ventrilo such as login and logout as well as seeing names light up. Other wine programs work fine with sound as well.

I have tried reinstalling ventrilo and replacing my msgsm32.acm as well as playing arround with vent settings. I had previously been able to hear fine. I have not changed anything about ventrilo or wine prior to this bug (that I know of).

My wine console log is as follows (I cant read it well enough to tell if there is something significant in it).

all of this happens at startup - nothing shows up in the log as a result of a new voice comming in.

```

err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:create_server class {96749377-3391-11d2-9ee3-00c04f797396} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {96749377-3391-11d2-9ee3-00c04f797396} could be created for context 0x17
err:ole:CoGetClassObject class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
err:ole:CoGetClassObject class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
err:ole:create_server class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {a910187f-0c7a-45ac-92cc-59edafb77b53} could be created for context 0x17
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub

```

---

### Post by T313C0mun1s7 on 2008-07-13
> **Snocrash said:**
> From the Ventrilo Forums....
_________________________
Pending release

The Ventrilo / Linux client tech support forum is here pending the official release of the client.

The forum will be activated once the first release is made available.

Thank you for your support and interest in the Linux client.

At the current time we do not have an official release date. Once we do it will be posted here and possibly some indication on the download page.

--Flag
Flagship is offline       
_________________________

Not that I don't like or use TeamSpeak....Just an FYI

-Sno
  You posted this in 2005 and we are now halfway through 2008 - I guess we know where they stand!! Oh and they are up to version 3.0.1 now. :lolflag:

---

### Post by Nectar on 2008-07-21
Trying to run the make command....

[SIZE="1"]blaze@blaze-desktop:~$ make /home/blaze/Desktop/ventriloctrl-0.3
make: Nothing to be done for `/home/blaze/Desktop/ventriloctrl-0.3'.
blaze@blaze-desktop:~$ /home/blaze/Desktop/ventriloctrl-0.3 make
bash: /home/blaze/Desktop/ventriloctrl-0.3: is a directory
blaze@blaze-desktop:~$ ventriloctrl-0.3 make
bash: ventriloctrl-0.3: command not found
blaze@blaze-desktop:~$ ventriloctrl-0.3$ make
bash: ventriloctrl-0.3$: command not found
blaze@blaze-desktop:~$ /home/blaze/Desktop/ventriloctrl-0.3$ make
bash: /home/blaze/Desktop/ventriloctrl-0.3$: No such file or directory
blaze@blaze-desktop:~$ /home/blaze/Desktop/ventriloctrl-0.3
bash: /home/blaze/Desktop/ventriloctrl-0.3: is a directory
blaze@blaze-desktop:~$ /home/blaze/Desktop/ventriloctrl-0.3 make
bash: /home/blaze/Desktop/ventriloctrl-0.3: is a directory
blaze@blaze-desktop:~$ make ventrilocrl.c
make: *** No rule to make target `ventrilocrl.c'.  Stop.
blaze@blaze-desktop:~$ /home/blaze/Desktop/ventriloctrl-0.3 make
bash: /home/blaze/Desktop/ventriloctrl-0.3: is a directory
blaze@blaze-desktop:~$ ventriloctrl-0.3 (.6Mb)]$ make
bash: syntax error near unexpected token `.6Mb'
blaze@blaze-desktop:~$ 
[/SIZE]

Not sure what to do to get it from the folder directory.. help please :-/

---

### Post by aoanla on 2008-07-21
> **Nectar said:**
> Trying to run the make command....

[SIZE="1"]blaze@blaze-desktop:~$ make /home/blaze/Desktop/ventriloctrl-0.3
make: Nothing to be done for `/home/blaze/Desktop/ventriloctrl-0.3'.
blaze@blaze-desktop:~$ /home/blaze/Desktop/ventriloctrl-0.3 make
bash: /home/blaze/Desktop/ventriloctrl-0.3: is a directory
blaze@blaze-desktop:~$ ventriloctrl-0.3 make
bash: ventriloctrl-0.3: command not found
blaze@blaze-desktop:~$ ventriloctrl-0.3$ make
bash: ventriloctrl-0.3$: command not found
blaze@blaze-desktop:~$ /home/blaze/Desktop/ventriloctrl-0.3$ make
bash: /home/blaze/Desktop/ventriloctrl-0.3$: No such file or directory
blaze@blaze-desktop:~$ /home/blaze/Desktop/ventriloctrl-0.3
bash: /home/blaze/Desktop/ventriloctrl-0.3: is a directory
blaze@blaze-desktop:~$ /home/blaze/Desktop/ventriloctrl-0.3 make
bash: /home/blaze/Desktop/ventriloctrl-0.3: is a directory
blaze@blaze-desktop:~$ make ventrilocrl.c
make: *** No rule to make target `ventrilocrl.c'.  Stop.
blaze@blaze-desktop:~$ /home/blaze/Desktop/ventriloctrl-0.3 make
bash: /home/blaze/Desktop/ventriloctrl-0.3: is a directory
blaze@blaze-desktop:~$ ventriloctrl-0.3 (.6Mb)]$ make
bash: syntax error near unexpected token `.6Mb'
blaze@blaze-desktop:~$ 
[/SIZE]

Not sure what to do to get it from the folder directory.. help please :-/

Something tells me that you're not at home in a terminal.

You want to change directory to the /home/blaze/Desktop/ventriloctrl-0.3 directory first, and then run make.
So

```

cd ./Desktop/ventriloctrl-0.3
make

```

(The . means "start from the directory I'm presently in" - your starting directory in a terminal is your home directory - /home/blaze )

---

### Post by Nectar on 2008-07-21
Got it. Thanks a ton!

---

### Post by bartoruiz on 2008-07-28
For those people that reboot and reboot until they got ventriloctrl to work.

The answer is simple, event ID changes for your keyboard when you restart (at least on my USB keyb)

So I made this little addon to the script to look for the correct event for my Keyboard, feel free to use it or improve it

```

#!/bin/sh

killall ventriloctrl

DEVICESEARCH=`cat /proc/bus/input/devices | awk '/BTC Multimedia USB Keyboard/{getline;getline;getline;getline;print}' | awk '{print $3}'`

# Config, see README for instructions
EVENT_DEVICE="/dev/input/$DEVICESEARCH"
INPUT_KEY="56"

sudo chown root:ventrilo $EVENT_DEVICE
sleep 1

# Don't touch
./ventriloctrl $EVENT_DEVICE $INPUT_KEY

```

The chown part makes sure ventrilo group has read access (you need to be part of that group ofc)

---

### Post by afallenhope on 2008-08-06
Hey great tutorial!

Thanks a lot.
I've noticed the audio quality is realllly high. so be sure to change it when you sign in and stuff.
cheers,

afh

---

### Post by T313C0mun1s7 on 2008-08-06
> **afallenhope said:**
> Hey great tutorial!

Thanks a lot.
I've noticed the audio ***quality*** is realllly high. so be sure to change it when you sign in and stuff.
cheers,

afh

AH . . . I don't thing quality is the word you are looking for here. If it is, why would you want to lower it?

Hmm . . . ***Volume*** maybe??

---

### Post by Krusnix on 2008-08-07
Hey guys I'm having some trouble using a usb logitech headset with ventrilo. The issue being when I click setup, it does not show me the logitech usb headset for input and output options. I like to hear music through my speakers, and talk to my friends via the headset so it makes it a little troublesome for me (especially since I can only hear them talk.) I've looked around including the guide at the wow website "http://forums.worldofwarcraft.com/thread.html?topicId=2200220013&sid=1", but I get stuck at the first step since my terminal doesnt recognize the [precat] stuff. Any and all help will be greatly appreciated.

---

### Post by T313C0mun1s7 on 2008-08-07
> **Krusnix said:**
> Hey guys I'm having some trouble using a usb logitech headset
  The issue is the headset. They are known to be problematic with Linux depending on which one you have. Mine works great, but I know there are models with issues.

[http://www.google.com/search?q=ubuntu+logitech+headset&ie=UTF-8](http://www.google.com/search?q=ubuntu+logitech+headset&ie=UTF-8)

---

### Post by Krusnix on 2008-08-07
I do see that, but the thing is ubuntu can see the usb headset (since i'm able to actually set the audio settings to it at night when i want to listen to music, and i can hear myself through it when "test" it), and even the wine software sees the "USB Mixer" under the oss settings (unfortunately it doesnt see it via the alsa stuff).

EDIT: I somehow got it somewhat working. I set everything to OSS in sounds, and I set the wine drivers to use oss. The problem now is the fact that now when I choose usb audio for the output and input, I can only hear what people are saying once I press setup. As if it cannot handle simultaneous streams.. So currently it outputs to my speakers, and uses my headset as the input.

---

### Post by connorh123 on 2008-08-09
For some reason I can't use my mic. My hotkey is ctrl and I still can't talk. Any help?

---

### Post by T313C0mun1s7 on 2008-08-09
> **connorh123 said:**
> For some reason I can't use my mic. My hotkey is ctrl and I still can't talk. Any help?
  Unlike when native running under windows, wine can only capture the hotkey when the program is in focus. Without more information I can't tell if this is your issue or not, but it is why I gave up and went back to windows. Ventrilo is useless if I can't use it while in game.

---

### Post by connorh123 on 2008-08-10
Does anyone else share this mic problem?

---

### Post by Tulth on 2008-08-10
Hey guys, I made an ugly python hack to automate starting up ventriloctrl.  This program uses python-xlib, so you'll have to download that from the package manager first.

NOTE!!: It sets ownership to your username for the /dev/input/<yourkeyboard> keyboard device.  This is probably a security no-no!

You should be able to just paste this into a text file, then save it as something like runvent.py.  After this, you'll need to execute: chmod a+x runvent.py

Be sure to edit the following paths to the exes at the top of the program: 
* ventriloctrl
* your .wine folder (I use a separate wine root just for vent)
* ventrilo.exe

Oh, and if it does not find your keyboard, you may have to edit the KEYBOARD_LABEL_REGEX to create a regular expression to find your keyboard.

```

#! /usr/bin/python

import os
import re
import time
import sys

# Change path so we find Xlib
sys.path.insert(1, os.path.join(sys.path[0], '..'))
from Xlib import X, display, Xutil

VENTRILO_WINDOW_NAME = "Ventrilo"
# if vent doesn't start in this many seconds, timeout and quit
VENTRILO_START_TIMEOUT = 12 
INPUT_KEY="69" # my numlock key

def my_home_folder():
    return os.getenv('HOME')
    
WINEPREFIX='WINEPREFIX="%s/wine_ventrilo"' % (my_home_folder())
VENTRILO_EXE = "%s/ventrilo/ventrilo.exe" % (my_home_folder())
VENTRILOCTRL = "%s/ventriloctrl-0.3/ventriloctrl" % (my_home_folder())

KEYBOARD_LABEL_REGEX   = r'n: name="([^"]*keyboard[^"]*)".*'
KEYBOARD_HANDLER_REGEX = r'h: handlers=.*(event[0-9]+).*'

class venterror(Exception):
    def __init__(self, msg):
        self.msg = msg


def find_keyboard_event_handlers():
    (child_stdin, child_stdout_and_stderr) = os.popen4('cat /proc/bus/input/devices')
    child_lines = child_stdout_and_stderr.readlines()
    devices = [[]]
    for line in child_lines:
        if line != '\n':
            devices[-1] += [line.lower()]
        else:
            devices+=[[]]
    pkeyboard = re.compile(KEYBOARD_LABEL_REGEX)
    keyboard_indices = []
    for (index, device) in zip(range(len(devices)),devices):
        for line in device:
            m = pkeyboard.match(line);
            if m:
                keyboard_indices += [index]
    phandler = re.compile(KEYBOARD_HANDLER_REGEX)
    keyboard_eventhandlers = set()
    for keyboard_index in keyboard_indices:
        working_device = devices[keyboard_index]
        for line in working_device:
            m = phandler.match(line);
            if m:
                for match in  m.groups():
                    keyboard_eventhandlers.add(match)
    return keyboard_eventhandlers


def set_keyboard_permissions(keyboard_eventhandlers):
    my_uid = os.getuid()
    for keyboard_eventhandler in keyboard_eventhandlers:
        command = 'gksu chown %s /dev/input/%s' % (my_uid,keyboard_eventhandler)
        os.system(command)
    return

def find_xwindow(name):
    xdisplay = display.Display()
    if xdisplay == None:
        raise venterror("ERROR: Could not open X Display!")
    # get the screen
    xscreen = xdisplay.screen()
    # get the root window
    xroot_win = xscreen.root
    xwindow_tree = xscreen.root.query_tree()
    found_win = None
    for xchild in xwindow_tree._data['children']:
        xchild_name = xchild.get_wm_name()
        if xchild_name == name:
            found_win = xchild
    return found_win

def start_vent():
    start_time = time.time()
    command = '%s wine %s' % (WINEPREFIX, VENTRILO_EXE)
    print command
    (vent_stdin, vent_stdouterr) = os.popen4(command)
    done = False
    while not done:
        os.system('sleep 1')
        vent_window = find_xwindow(VENTRILO_WINDOW_NAME)
        if vent_window != None:
            done = True
        elif time.time() - start_time > VENTRILO_START_TIMEOUT:
            raise venterror("ERROR: Vent startup timeout!")
    return (vent_stdin, vent_stdouterr)

def start_keyboard_forwarders(keyboard_eventhandlers):
    vctrls_stdios = []
    for keyboard_eventhandler in keyboard_eventhandlers:
        command = '%s /dev/input/%s %s' % (VENTRILOCTRL, keyboard_eventhandler, INPUT_KEY)
        vctrls_stdios += [os.popen4(command)]
    return vctrls_stdios



def main():
    keyboard_eventhandlers = find_keyboard_event_handlers()
    set_keyboard_permissions(keyboard_eventhandlers)
    (vent_stdin, vent_stdouterr) = start_vent()
    keyboard_forwarders_stdios = start_keyboard_forwarders(keyboard_eventhandlers)
    done = False
    while not done:
        os.system('sleep 10')
        vent_window = find_xwindow(VENTRILO_WINDOW_NAME)
        # if I wakeup and don't see the vent window, quit
        if vent_window == None:
            done = True

if __name__ == "__main__":
    main()

```

I'd like to hear about if it helps anyone and if anyone makes improvements.  I don't know popen that well, but I think someone that does could use it to determine when the child process is/isn't running to remove the python-xlib dependency.

---

### Post by connorh123 on 2008-08-16
Um correct me if I'm wrong, but aren't you supposed to download this, [http://www.ventrilo.com/dlprod.php?id=301](http://www.ventrilo.com/dlprod.php?id=301)

---

### Post by Tulth on 2008-08-16
No, that is just a script to start the server, not the client.

---

### Post by Lord C on 2008-08-18
> **T313C0mun1s7 said:**
> You posted this in 2005 and we are now halfway through 2008 - I guess we know where they stand!! Oh and they are up to version 3.0.1 now. :lolflag:

My sentiments exactly.

Flagship are really an amateur shambles. It really annoys me how they delete any post on their forums asking about the Linux client.

---

### Post by Ziggyz on 2008-08-19
> Ventrilo Control v0.3-SVN for Linux by Purkka Productions
=====================================================
WARNING: This program reads DIRECTLY your keyboard!
         You need correct permissions to read the
         event device.
Window selected. Please test pressing the key to talk before going to play.

Use CTRL-C to quit.

Is there no fix for this?  I am having this exact same problem, and I have read nearly every single guide that is possible for any person to access using an internet connection.  I can't seem to get it to work, and so fat it kinds looks like everyone has been ignoring help for this kind of error, or is there just not fix?

---

### Post by T313C0mun1s7 on 2008-08-19
> **Ziggyz said:**
> Is there no fix for this?  I am having this exact same problem, and I have read nearly every single guide that is possible for any person to access using an internet connection.  I can't seem to get it to work, and so fat it kinds looks like everyone has been ignoring help for this kind of error, or is there just not fix?

I am not exactly sure if you are asking if there is a fix with the hotkey not working, or with the "Ventrilo Control v0.3-SVN for Linux by Purkka Productions" script. I am not associated in any way with Purkka Productions and I don't know what the script does, as I have not used it.

The issue at hand is that because WINE is not the app in focus and Vent is running under WINE, the hotkey will not work. WINE is not reading the keyboard when it is in the background. My assumption is that the script you are mentioning is an attempt to work around that by having something that reads the keyboard directly regardless of what program is currently the active one. If my assumption is correct then this script my be the key and you should try presenting your question to Purkka Productions. If I am wrong then the answer is there is just no way around this glaring problem, and it has been asked so many times that people have given up on trying to address it.

---

### Post by Ziggyz on 2008-08-19
Im asking whether or not people are able to open the actual script....  It is saying that I need permission to do it, and I cant.

---

### Post by T313C0mun1s7 on 2008-08-19
Maybe, that's not how I read it though.
> 
Ventrilo Control v0.3-SVN for Linux by Purkka Productions
================================================== ===
WARNING: This program reads DIRECTLY your keyboard!
You need correct permissions to read
the event device.
Window selected. Please test pressing the key to talk before going to play.

Use CTRL-C to quit.
To me it looks like a warning that you need to make sure you run it with correct permissions because it does not do error checking. The  fact it continues on with
> 
Window selected. Please test pressing the key to talk before going to play.

Use CTRL-C to quit.
instead of just dieing makes me think it is running, it just has no way of showing progress so it asks you to verify it works before you start the game.

Does the owner of the script not have any support or forums available? The fact that no one else here has answered makes me wonder if anyone else here has used this. I know I haven't. I still think you would be better served either getting answers from the source, or from a community that is familiar with it.

---

### Post by connorh123 on 2008-08-21
So is there no way to get my microphone to work and my sound to work on Ventrilo?

---

### Post by T313C0mun1s7 on 2008-08-21
> **connorh123 said:**
> So is there no way to get my microphone to work and my sound to work on Ventrilo?

Your last post here was 4 days ago, and you didn't ask about your microphone. ADD/ADHD much?

It is possible to get your microphone working, it just does not do much good unless you want to keep the Ventrilo/WINE window in the foreground and in focus (the active window) so it can capture the hotkey. I mean you could play your game and listen to others, then switch to the Ventrilo/WINE application to respond. That kind of sucks however.

---

### Post by ooobuntooo on 2008-08-22
Is there a 3rd party Ventrollo client for Linux?
E.g. Pidgin = Windows Live Messenger.

---

### Post by aoanla on 2008-08-22
> **ooobuntooo said:**
> Is there a 3rd party Ventrollo client for Linux?
E.g. Pidgin = Windows Live Messenger.

Not that I'm aware of, although the actual VoIP protocols they use are well-understood (and standards).

Ironically, Ventrilo seems to have become more popular than Mumble and Team Speak for gaming at the moment, although the latter two both have linux clients...

---

### Post by louisgag on 2008-08-22
After struggling a long time with my audio settings to get vent to work I finally realized that I had to enable the "Digital" input in the gnome alsa mixer... (Even if my microphone is just some standard mic)

so if your setup is still not working but you have dmix and dsnoop detected you might wanna run command ```
alsamixer
``` and try to enable some devices you would not suspect of being the microphone.

---

### Post by Ziggyz on 2008-08-23
> **T313C0mun1s7 said:**
> Maybe, that's not how I read it though.
To me it looks like a warning that you need to make sure you run it with correct permissions because it does not do error checking. The  fact it continues on with
instead of just dieing makes me think it is running, it just has no way of showing progress so it asks you to verify it works before you start the game.

Does the owner of the script not have any support or forums available? The fact that no one else here has answered makes me wonder if anyone else here has used this. I know I haven't. I still think you would be better served either getting answers from the source, or from a community that is familiar with it.

Although I downloaded the script from a different website, I followed the exact instructions here and on other websites... I am not using a different program...

---

### Post by connorh123 on 2008-08-23
Well when I change my codec, it goes back to what it was before. It's like you can't apply it or anything.

---

### Post by zmjjmz on 2008-09-01
Ok, I've been trying to get ventriloctrl working for a while now.
Here's the script I made as per the README:
```
#!/bin/bash
cd ~/.wine/drive_c/Program\ Files/Ventrilo/
WINEDEBUG="-all" wine Ventrilo.exe &
sleep 3
ventriloctrl /dev/input/event1 96

```
96 should be F12, but it doesn't work D:
```
lrwxrwxrwx 1 root root  9 2008-09-01 08:03 usb-Apple_Computer_Apple_Internal_Keyboard_._Trackpad-event-kbd -> ../event1

```
I'm pretty sure that should work... but...

---

### Post by Tulth on 2008-09-02
Make sure vent is setup to use the 'A' key for push to talk.  Despite what you program it to, it always sends the 'A' key to ventrilo.  The key you program only changes what key you press to send a fake 'A' keypress to ventrilo.

---

### Post by zmjjmz on 2008-09-02
It was like that, yes.
I've switched it back because I don't need ventriloctrl at the moment, but I set the vent settings according to what it said in the README

---

### Post by Tulth on 2008-09-02
Hrm, one other thing to check: are you sure you had permissions set?  I noted the permissions reset every reboot.

---

### Post by zmjjmz on 2008-09-02
> **Tulth said:**
> Hrm, one other thing to check: are you sure you had permissions set?  I noted the permissions reset every reboot.

Permissions for what now?
The event1?

---

### Post by Tulth on 2008-09-02
Right, the typically /dev/input/X

---

### Post by zmjjmz on 2008-09-02
> **Tulth said:**
> Right, the typically /dev/input/X

Should I chmod 777 /dev/input/event1?
Seems dangerous...

---

### Post by Tulth on 2008-09-02
Right, ventctrl needs permissions to read it, and yes I think it is a possible security hole.

---

### Post by zmjjmz on 2008-09-02
> **Tulth said:**
> Right, ventctrl needs permissions to read it, and yes I think it is a possible security hole.

Hm?
I could probably run ventriloctrl as root.

---

### Post by Prefix100 on 2008-09-02
Yea, run as root thats how I used to do it.

Create a bash script that does the vent ctrl, then opens vent.

---

### Post by zmjjmz on 2008-09-02
Didn't work D:

---

### Post by SBFC on 2008-09-02
Running it as root isn't necessary.

Follow the instructions [here ]("http://ubuntuforums.org/showpost.php?p=2662867&postcount=83") and you'll be able to give a group permission to the events (and add yourself to the group).

I stumbled upon this post some time back and it works perfectly. My thanks to hikaricore.

---

### Post by zmjjmz on 2008-09-02
I'm just going to point out that hikaricore said that the instructions were outdated because the new ventriloctrl has better instructions built in, but I'll try it anyways.

---

### Post by SBFC on 2008-09-03
> **zmjjmz said:**
> I'm just going to point out that hikaricore said that the instructions were outdated because the new ventriloctrl has better instructions built in, but I'll try it anyways.

Could be. Perhaps I'm using an outdated version.

---

### Post by Landara on 2008-10-07
The only thing is Teamspeak has crappy sound quality.

---

### Post by zmjjmz on 2008-10-07
> **Landara said:**
> The only thing is Teamspeak has crappy sound quality.

From my experience Ventrilo isn't much better, though it could just be WINE.

---

### Post by Sammi on 2008-10-08
If you have possibility of getting your guild on board, then your best option for a good Linux gaming VoIP app is Mumble:

[http://mumble.sourceforge.net](http://mumble.sourceforge.net)

It works problem free on Win/Mac/Linux, is fast, sounds as good as the others, if not better, and is open source. What more could you want? Other than it being able to connect to Ventrilo and Teamspeak servers of course... damn proprietary protocols...

---

### Post by jeaves on 2008-11-16
Not sure if this is the best place for this question... I'm getting some horrible sound quality out of Vent run through wine. My mic records just fine in the Ubuntu recorder, though. 

Ubuntu 8.04 
Wine 1.1.8
Vent 3.0.4

Even the connect wav is choppy, and my sound recording with just about any codec or speed sounds extremely staticy and far away. 
Any suggestions?

---

### Post by T313C0mun1s7 on 2008-11-16
> **jeaves said:**
> Not sure if this is the best place for this question... I'm getting some horrible sound quality out of Vent run through wine. My mic records just fine in the Ubuntu recorder, though. 

Ubuntu 8.04 
Wine 1.1.8
Vent 3.0.4

Even the connect wav is choppy, and my sound recording with just about any codec or speed sounds extremely staticy and far away. 
Any suggestions?
Just a shot in the dark here, but make sure you are NOT running any other VoIP software (softphone, Skype, etc) or P2P (ie torrent) applications at the same time.

The fact that it works locally with Ubuntu recorder is a hint that it is most likely a network issue. Probably 98% of all VoIP quality issues end up being network issues because VoIP traffic must be realtime and the packets must arrive in the correct order. TCP/IP as a protocol is just not built that way, so in order to achive that all other traffic must get out of the way. For this reason you should use QOS to prioritize traffic, but no amount of QOS will fix you trying to use a bit torrent client at the same time. Remember, you are most likely using this app while playing a MMORP game, and that is going to tax your Internet connection enough on its own.

---

### Post by jeaves on 2008-11-16
> **T313C0mun1s7 said:**
> Just a shot in the dark here, but make sure you are NOT running any other VoIP software (softphone, Skype, etc) or P2P (ie torrent) applications at the same time.


It sounds network related to me as well, though I'm having the same sound quality problems when *disconnected* from Vent, but running the mic test through the setup. I've done testing with all programs disabled (even shut down my wife's pc) 

Here's some screens of my setup for the Voice and Speech tabs.

---

### Post by T313C0mun1s7 on 2008-11-16
This type of network troubleshooting goes beyond and off topic from this thread. Also, I currently don't have a Linux machine set up (also I just UNinstalled VMWare Workstation). So I can't and won't go too deep into specifics, but I can give some advice to help you narrow this down.

If the problems are static, buzzing, or the like you have a sound issue. If the problems are echo, stuttering, delay, or choppiness, then it is a network issue. VoIP traffic is very touchy and things that don't bother other traffic will cause problems for VoIP. Echo is when one end or the other is trasmitting too "hot" and you get reflective power. Stutter, choppiness, stuttering and delay is when the lag is too long, the pakets come in out of order, or or you have packet loss.

Start by looking at all network traffic on your computer, look for anything that might fragment the packets or delay the traffic. Poorly set rwin and mtu can cause fragmentation. Also if the mtu is different from other equipment between endpoints it will cause fragmentation.

If the issue is not to be found on your computer, move to the local network. Use network tools to determine if the flow is ok. If there are no network issues, look to pysical network issues. This means a cable that cas been kinked or had a desk set on it, cheap consumer quality switches and routers, etc. A CAT5 cable that and been kinked and straightend is BAD.

Belken likes to sell patch cables that are both bent too sharply and zip tied in the middle when packaged. In otherwords, they detroy the cable by putting it in the packaging. If you don't believe me read the EIA/TIA 568 standard. There is a lot of crap quality networking products that are sold to consumers. This could also be the cause of issues.

I don't want to go on a rant here but what I am trying to say is eliminate one posibility at a time and work outward. First look to your computer, then your network, then your internal equipment, then to your ISP, then past the ISP gateway towards the other endpoint. Not all of this is within your control, but by the time you have to make calls for the stuff not under your control you will know that all is well on your end, and know what you are talking about.

---

### Post by Sammi on 2008-11-17
> **T313C0mun1s7 said:**
> This type of network troubleshooting goes beyond and off topic from this thread. Also, I currently don't have a Linux machine set up (also I just UNinstalled VMWare Workstation). So I can't and won't go too deep into specifics, but I can give some advice to help you narrow this down.

If the problems are static, buzzing, or the like you have a sound issue. If the problems are echo, stuttering, delay, or choppiness, then it is a network issue. VoIP traffic is very touchy and things that don't bother other traffic will cause problems for VoIP. Echo is when one end or the other is trasmitting too "hot" and you get reflective power. Stutter, choppiness, stuttering and delay is when the lag is too long, the pakets come in out of order, or or you have packet loss.

Start by looking at all network traffic on your computer, look for anything that might fragment the packets or delay the traffic. Poorly set rwin and mtu can cause fragmentation. Also if the mtu is different from other equipment between endpoints it will cause fragmentation.

If the issue is not to be found on your computer, move to the local network. Use network tools to determine if the flow is ok. If there are no network issues, look to pysical network issues. This means a cable that cas been kinked or had a desk set on it, cheap consumer quality switches and routers, etc. A CAT5 cable that and been kinked and straightend is BAD.

Belken likes to sell patch cables that are both bent too sharply and zip tied in the middle when packaged. In otherwords, they detroy the cable by putting it in the packaging. If you don't believe me read the EIA/TIA 568 standard. There is a lot of crap quality networking products that are sold to consumers. This could also be the cause of issues.

I don't want to go on a rant here but what I am trying to say is eliminate one posibility at a time and work outward. First look to your computer, then your network, then your internal equipment, then to your ISP, then past the ISP gateway towards the other endpoint. Not all of this is within your control, but by the time you have to make calls for the stuff not under your control you will know that all is well on your end, and know what you are talking about.
As a former ISP phone supporter, I say that this is first grade advise for users.

Network troubleshooting is a long elimination process. You test one thing at a time, to see if it works, and move on until you find the faulty point in the network chain.

---

### Post by louisgag on 2008-11-17
JEAVES: try disabling directsound.

---

### Post by T313C0mun1s7 on 2008-11-17
I just want to clarify something from my hastily written previous post. Just because your network is passing traffic does not mean that all is well, and more sensitive applications will show symptoms first. Any real time streaming protocol is going to be subject to having issues when everything else seems ok.

Here are some examples. A network cable may be passing traffic and you may not notice issues, but just because there is continuity between the correct pins on the cable does not mean all is well. Being improperly terminated by having the outer sheath stripped back more than 1/4 inch, or nicking the inner sheaths of the wires a little where you pull it off will cause issues. As will allowing the cable to EVER be bent at a radius more than outer diameter of the cable (about 1/4 inch). Also, the conductors of the cable can become stretched if it is ever pulled exerting more than 3 lbs/square inch of pull. A rule of thumb when pulling bulk cable is, if it is enough to lift the box off the ground it is too much. All of these things can cause cross talk, reflected power, noise, and other issues that will ultimately lead to problems such as retransmission of packets.

Network packets can also collide forcing retransmission, this possibility increases the more endpoints you have and the longer the distance is between endpoints. This is why cables have maximum lengths. They also have MINIMUM lengths; the twist cannot do its job canceling noise if the cable is not at least 24 inches long. Make sure you do not have any cables anywhere less than 2 feet long.

The equipment itself can cause issues. This is why enterprise switches and routers advertise the speed of the switching fabric and the method of packet transmission (such as store and forward). Don't expect great quality out of a $50 switch.

I am not trying to sound like an elitist, in fact there is some very good consumer equipment out there, but I have personally seen problems such as these in the past. I engineered and implemented a fiber-to-the-home development serving 360 homes, and I saw a lot of this along the way. We were serving both Internet access and phone service (as VoIP) so implementation was critical. In one case an installer who did not know what he was doing terminated the cables in such a way that where he has punched them down to the termination block the outer sheath was stripped back 3 inches. This fact alone caused a large amount of packet loss. Not so much that he had no Internet, but enough that he got frequent 404 errors at websites and was only getting about 256K when he should have been getting 3M.

The point of this whole post is that TCP/IP was designed from the ground up to be survivable. The Internet is supposed to be able to survive a nuclear war and still be mostly working. Most every protocol transmitting across TCP/IP takes advantage of the fact that things can get delayed or need to be retransmitted. Things can get pretty messed up before you notice anything is wrong. Real time streaming applications like Video and VoIP are exceptions to this. Things need to be near perfect to really get this stuff working well. We can get around a little of this with things like buffering, but it only goes so far. There are a lot of problems that can exist but seem "invisible" until you try to do something like run voice while gaming.

---

### Post by SBFC on 2008-11-30
Has anyone else been having issues with ventrictrl lately? I recently upgraded to 8.10 and while monitoring all events in /dev/input I get no feedback what-so-ever.

---

### Post by nzadLithium on 2008-12-01
same here, i tried seeing if /dev/input/event(my event) had any output at all, made a bash script inf look and told it to cat /dev/input/event(event number). It gave out nothing, so I took a look in gogle, found this question on launchpad: [https://answers.launchpad.net/ubuntu/+question/51132](https://answers.launchpad.net/ubuntu/+question/51132)
which is askin about the problem, + [https://bugs.launchpad.net/ubuntu/+bug/298963](https://bugs.launchpad.net/ubuntu/+bug/298963) which is asking same thing as well, and from the second one theres a link [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/267682/comments/84](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/267682/comments/84) which has someone who has figured out the problem, but i've heard nothing about a fix. I might try writing a push to talk hack that uses x for key reporting, then it would work, but we'll have to see how annoyed I am with no push to talk XD

---

### Post by SBFC on 2008-12-02
> **nzadLithium said:**
> same here, i tried seeing if /dev/input/event(my event) had any output at all, made a bash script inf look and told it to cat /dev/input/event(event number). It gave out nothing, so I took a look in gogle, found this question on launchpad: [https://answers.launchpad.net/ubuntu/+question/51132](https://answers.launchpad.net/ubuntu/+question/51132)
which is askin about the problem, + [https://bugs.launchpad.net/ubuntu/+bug/298963](https://bugs.launchpad.net/ubuntu/+bug/298963) which is asking same thing as well, and from the second one theres a link [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/267682/comments/84](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/267682/comments/84) which has someone who has figured out the problem, but i've heard nothing about a fix. I might try writing a push to talk hack that uses x for key reporting, then it would work, but we'll have to see how annoyed I am with no push to talk XD

Well, I've been working on a script that monitors X instead of /dev/input/event* using python-xlib and have made some progress. I am a bit stumped right now, though.

I tried to follow the original ventriloctrl.c (from what I could follow) and right now it is able to locate the Ventrilo window and send events. Only problem, and I can't figure out why, is the event isn't sent unless you hover over Ventrilo with the mouse. You don't have to select it, you just have to hover. Obviously not ideal.

I've been stumped on this last bit since last night and have made no progress. Maybe someone else with more knowledge could offer some input. I've attached what I have so far.

---

### Post by nzadLithium on 2008-12-02
That would have to be something to do with the window focus still, when you place ur mouse over something thats not in focus, and scroll on it, it will still scroll, so there must be some sort of semi-focus mode as well XD

I've got quite a bit of time over the holidays, so if u don't get your python one working, i'll try writing one up in c++ :D

---

### Post by SBFC on 2008-12-02
Yeah. It just confused me because the original ventriloctrl only sends a KeyPress/KeyRelease event. It doesn't manipulate focus at all (from what I can tell).

Maybe python-xlib just behaves a little differently.

---

### Post by SBFC on 2008-12-03
Ha. Finally got it. Spent the last two nights trying to figure this out and all it took was one line of code to get it working. 

```
local_dsp.sync()
```

Uploaded what I have. It's set up similar to the real ventriloctrl in that your Vent settings have to be set the same.

This script uses the left alt key (keycode 64) but you can edit it and set it to whatever you like. Just need to get the proper keycode. I used xev.

Not sure if I'll work on improving it simply because the original ventriloctrl is better. It monitors input events from the keyboard whereas mine monitors events from X. This means that mine is constrained to whatever display it is run on where as the original works no matter which display you happen to be on. 

I (usually) play games on a separate X screen so the original really was nice. 

The reason I say I may not improve it is because I'm assuming the bug with the input events will get fixed.

---

### Post by Sammi on 2008-12-03
Good work SBFC.

Just one request: Can you please write up a short step by step guide for us noobs, on how to configure and run your script? Haven't ever run a python script before. Thanks ):P

---

### Post by SBFC on 2008-12-03
Sure will. I was planning on it but wanted to get a few modifications in first. When I get home from work I'll finish up with the changes and then repost it with some instructions.

---

### Post by SBFC on 2008-12-04
So...here's pyvent then.

You'll need python2.5 and python-xlib

```
sudo apt-get install python2.5 python-xlib
```

Download the attachment and drop it wherever you want. Run it without any arguments and you'll be able to monitor your key presses/mouse clicks

```

oblivion@macabre:~/dev/python$ ./pyvent.py

Required arguments not supplied so
will run findkey.

Running findkey...
Press the key or mouse button you wish to
have as your PTT and findkey will tell you
the command to execute.
Press Ctrl-C to exit.

./pyvent.py 2 64


```

Follow the instructions and press the key you wish to have as your PTT. This will will tell you the proper arguments to run pyvent with.

In the above I pressed the left alt button.

As for Ventrilo settings, the original ventriloctrl rules still apply. As per their README:

```

Make sure to set these things exactly like below:
	* Check: "Use Push To Talk Hotkey ( PTT Mode )"
	* Uncheck: "Use Direct Input to detect Hotkey"
	* Hotkey: "Keyboard: A" (if you are pushing the key that you setup in the Getting Started section, and it is not appearing as "Keyboard: A" then we have a problem)
	* Check: "Use Direct Sound" for "Output device"
	* Uncheck: "Use Direct Sound" for "Input device"

```

Once this is all done fire up Ventrilo and then execute pyvent with the command it gave you.

As of right now pyvent is constrained to whatever X display it is executed on. So if you use a separate X server to play games you'll have to launch Ventrilo, pyvent, and your game on the additional X screen. I'm attempting to get around this but ran into a snag.

Any questions feel free to ask and I'll do my best to answer them.

NOTE:

If you have multiple versions of python installed you'll probably have to run pyvent as follows:

```

python2.5 pyvent.py

```

It may work with previous versions, I didn't try. I know it won't work with Python3.0, however.

---

### Post by nzadLithium on 2008-12-04
ah nice. I may be able to use vent again XD Or it could decide as per usual that it would rather freeze after 5 mins :p Did you upload/link this to the wine page on running vent? I think alot of users could benefit from it :D

---

### Post by subdancer on 2008-12-04
nice work SBFC its workin with your script in intrpid. thx
but its not working perfect. im using a logitech G5 mouse and im using the button at the thumb as push to talk key. pyvent is echoing "2 8" for the key so it recognizes it. problem is i need to check "Use Direct Input to detect Hotkey" in ventrilo so it recognizes the button i want to use. but then pyvent isnt working anymore. if i uncheck "Use Direct Input to detect Hotkey" pyvent is working with every key exept the one i want to use :(

any ideas how to solve this?

---

### Post by SBFC on 2008-12-04
I'll mess around with it and see if I can come up with anything. To be honest I forgot to test it using mouse buttons. :oops:

---

### Post by SBFC on 2008-12-04
Ha. My bad. It was a mistake on my part that was quick to fix. 

I've reattached the script in the original post that contained it.

---

### Post by subdancer on 2008-12-05
works like a charm now :) thx alot for you work to the community, and for the quick fix :D

windows [-X 
linux for the win!!  :guitar:

---

### Post by AndersAA on 2008-12-05
Has anyone found a program to set ventrilo hotkeys that allow input to happen at the same time?

If I have something requireing input (say text document) and I hold my push to talk button down, I can't write anything at the same time.  This is really annoying me, I didn't have that limitation with early ventriloctrl versions (before the xorg 1.5 security fix that broke it).

---

### Post by SBFC on 2008-12-05
Have you tried the file I uploaded on the last page? It doesn't block input.

---

### Post by AndersAA on 2008-12-05
> **SBFC said:**
> Have you tried the file I uploaded on the last page? It doesn't block input.

This has been driving me nuts for a good month now, thanks a bunch!

---

### Post by subdancer on 2008-12-05
im trying to make a bash.sh script so it starts ventrilo and pyvent with one click 

```

#!/bin/sh
wine /home/XXXX/.wine/drive_c/Programme/Ventrilo/Ventrilo.exe
python /home/XXXX/.wine/drive_c/Programme/Ventrilo/pyvent.py 4 8

```

when i run it it starts ventrilo but the pyvent seems not starting or atleast the button is not working. is the script code right like this?

---

### Post by SBFC on 2008-12-05
> **subdancer said:**
> im trying to make a bash.sh script so it starts ventrilo and pyvent with one click 

```

#!/bin/sh
wine /home/XXXX/.wine/drive_c/Programme/Ventrilo/Ventrilo.exe
python /home/XXXX/.wine/drive_c/Programme/Ventrilo/pyvent.py 4 8

```

when i run it it starts ventrilo but the pyvent seems not starting or atleast the button is not working. is the script code right like this?

Use this:
```

#!/bin/sh
wine /home/XXXX/.wine/drive_c/Programme/Ventrilo/Ventrilo.exe &
sleep 10
python /home/XXXX/.wine/drive_c/Programme/Ventrilo/pyvent.py 4 8 &

```

The '&' lets Ventrilo run in the background so your shell script can execute more commands. Without it no other commands will execute until Ventrilo is closed.

'sleep' pauses the shell script for 10 seconds. Without this Ventrilo will not be finished loading by the time pyvent launches. pyvent will then not detect a running instance of Ventrilo and then it will exit.

---

### Post by AndersAA on 2008-12-06
This is the script I use, incase anyone is interested, I use capslock, so I disable the capslock key before starting it.
```

#!/bin/bash
xmodmap -e "clear Lock"

amixer -c1 sset Mic,0 100%
export WINEPREFIX="$HOME/Ventrilo"


if [ "$1" == "2" ]; then
    cd /home/neuron/Ventrilo/drive_c/Program\ Files/VentriloMIX
    wine "Ventrilo 2.3.0.exe" &
else
    cd /home/neuron/Ventrilo/drive_c/Program\ Files/Ventrilo/
    wine Ventrilo.exe &
fi

PID="$!"

sleep 2
~/.bin/pyvent.py 2 66 &

wait $PID
pkill -f pyvent.py

```

---

### Post by edkuk13 on 2008-12-06
I am newish to linux. I am trying to run pyvent.py and I have acces denied. I cannot use sudo ./pyvent.py . Is there a legitimate command to do this?

---

### Post by MindFlayer on 2008-12-07
> **edkuk13 said:**
> I am newish to linux. I am trying to run pyvent.py and I have acces denied. I cannot use sudo ./pyvent.py . Is there a legitimate command to do this?

Don't run sudo. You only need to set pyvent.py to be executable. You do this by running "chmod +x pyvent.py" in the directory where pyvent.py is located.

---

### Post by edkuk13 on 2008-12-07
Thank you. That helped. Now I am having a new problem. I type in terminal : ./pyvent.py 2 37   after starting vent and it responds:

eric@husband:~$ cd /home/eric/pyvent
eric@husband:~/pyvent$ ./pyvent.py 2 37
Ventrilo found...

yet the key for left ctrl is still unactive.

---

### Post by SBFC on 2008-12-08
> **edkuk13 said:**
> Thank you. That helped. Now I am having a new problem. I type in terminal : ./pyvent.py 2 37   after starting vent and it responds:

eric@husband:~$ cd /home/eric/pyvent
eric@husband:~/pyvent$ ./pyvent.py 2 37
Ventrilo found...

yet the key for left ctrl is still unactive.

Do you mean to say that you press left ctrl and vent ppt does not activate?

---

### Post by Will Murray on 2008-12-08
Ok so I used the OP's guide and have everything running etc. 

But I can't talk in vent. I have my hot key set, but I can not specify my Mux or my Line as there is nothing in the drop down menus.

I quite new to ubuntu/linux as well. :( 

```
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:create_server class {96749377-3391-11d2-9ee3-00c04f797396} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {96749377-3391-11d2-9ee3-00c04f797396} could be created for context 0x17
err:ole:CoGetClassObject class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
err:ole:CoGetClassObject class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
err:ole:create_server class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {a910187f-0c7a-45ac-92cc-59edafb77b53} could be created for context 0x17
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
```

---

### Post by Sammi on 2008-12-08
@SBFC
Just tried the script out. Works like a charm :KS

---

### Post by SBFC on 2008-12-08
> **Will Murray said:**
> Ok so I used the OP's guide and have everything running etc. 

But I can't talk in vent. I have my hot key set, but I can not specify my Mux or my Line as there is nothing in the drop down menus.

I quite new to ubuntu/linux as well. :( 



You actually don't need to specify a Mixer, Mux, or Line (least I don't). Just make sure 'User Direct Sound' above Output device is checked, Output device is set to 'Default DirectSound device', 'Use Direct Sound' above Input device is unchecked, and Input device is set to 'Default wave mapper'.

---

### Post by edkuk13 on 2008-12-09
I cannot even get vent to acknowlege mic when PTT is off. My icon remains red.

-my mic works in voice recorder

---

### Post by edkuk13 on 2008-12-09
I had no problems using vent before I upgraded 8.04 to 8.10

---

### Post by Sammi on 2008-12-09
Could be regressions in Wine. Check the appdb for more updated config info: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=2169](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2169)

---

### Post by edkuk13 on 2008-12-09
It's kinda weird. when I start vent by it self I get an error saying input is being used by another program and vent loads but does not work. When I start my internet radio and then vent the mic works and the sound does not work(no error).

---

### Post by edkuk13 on 2008-12-11
I fixed all my issues with World of Warcraft a:

1) clean install Ubuntu 8.10
2) followed steps file:///media/disk/Important%20Documents/Important%20Documents/http%20_www.fsckin.com_2007_12_%2020_how-to-run-world-of-%20warcraft-wow-in-linux-using-%20wine_.htm

3)followed steps for ventrilo: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9832](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9832)

Thank you for your help!

---

### Post by captaincrook on 2008-12-21
> **edkuk13 said:**
> Thank you. That helped. Now I am having a new problem. I type in terminal : ./pyvent.py 2 37   after starting vent and it responds:

eric@husband:~$ cd /home/eric/pyvent
eric@husband:~/pyvent$ ./pyvent.py 2 37
Ventrilo found...

yet the key for left ctrl is still unactive.

Same boat here. Will work when using a wine window, as usual.

---

### Post by Zackie on 2008-12-22
i ran the script and got this:

```
Required arguments not supplied so
will run findkey.

Running findkey...
Press the key or mouse button you wish to
have as your PTT and findkey will tell you
the command to execute.
Press Ctrl-C to exit.

/home/zackie/Desktop/pyvent.py 2 37

```

What do i need to do now?

I restarted and it worked for about 2 mins and then stopped.It had to be "IN FOCUS"or the ACTIVE APP for PTT to work as well as just the mic sensitivity talk.

---

### Post by SBFC on 2008-12-23
It told you what you should do to run pyvent. 

```
/home/zackie/Desktop/pyvent.py 2 37
```

Start Ventrilo and then run pyvent with those arguments. Make sure in Ventrilo Setup that your PTT key is set to 'A' (this is the key that pyvent sends to the Ventrilo window).

---

### Post by Zackie on 2008-12-23
Rock on that seemed to work...! Thanks duder!


Zackie...:guitar:


Edit--- It worked for about 2 mins then it just stoped... Vent work i can hear people but PTT will not work. Any ideas?

---

### Post by SBFC on 2008-12-23
You're sure that pyvent is still running when it seems to quit working?

---

### Post by Zackie on 2008-12-23
yeah I run vent then open term then run what you told me it says it found Vent and i minimized the term and Vent will work for about 2 mins then it will just stop.. I won't even open anything else just trying to test vent... and it will do the same regardless.


edit--- When it does work it is on ALSA driver when i switch it to OSS i get:

Failed to open input device. Another program might have it open already. rc=-10

With OSS i can hear them they can't hear me... With ALSA I can talk to them and they can here me but only for about 2-3 mins... with nothing else open... and it staying in focus.

---

### Post by SBFC on 2008-12-23
Did you configure Ventrilo with all the settings from the [original]("http://ubuntuforums.org/showpost.php?p=6304758&postcount=299") posting?
```
* Check: "Use Push To Talk Hotkey ( PTT Mode )"
	* Uncheck: "Use Direct Input to detect Hotkey"
	* Hotkey: "Keyboard: A" (if you are pushing the key that you setup in the Getting Started section, and it is not appearing as "Keyboard: A" then we have a problem)
	* Check: "Use Direct Sound" for "Output device"
	* Uncheck: "Use Direct Sound" for "Input device"
```

Reason I ask is because you noted Ventrilo has to have the focus to work (which pyvent is supposed to work around).

---

### Post by Zackie on 2008-12-23
Yeah, I have all of those settings and it just seems not to want to work...:(

Edit--- Usually when i restart or wait about 1-2 hours it will work with out it being "in focus" when I first start it and it does work I load another app (such as a game) to see if it work in that game, but to no avail. However, when I restart to refresh it works with terminal open and i can put the Terminal in focus and use ctrl and it will work with vent for about 2 mins then quit... :(



2nd Edit---- So i get up today and the CTRL worked great i changed nothing but the sound is not there i can hear when i log in and out  in vent but i can not hear others talking.After about 5 mins this time CTRL stoped working... And still no sound:(

---

### Post by captaincrook on 2008-12-23
Hmm well I can say that for me, the settings are pretty much identical. I noticed that holding/hammering my ptt key (which is shift btw) RARELY (stress) gets a response, but the light stays green. So I must "focus" on Ventrilo (or a wine window at that) to "release" the key. Too many quotes and parenthesis I know. Anyways, if its any problem, I use OSS for wine, in the aoss wrapper. ALSA produces garbled sound with the mic and sounds in vent, but OSS works like a treat. As for now, pyvent just doesn't work unless a wine window is focused.

---

### Post by Zackie on 2008-12-24
Thats about what mine is doing too.

---

### Post by SBFC on 2008-12-29
Not sure if this is what is causing your problem but I found it interesting: [http://ubuntuforums.org/showthread.php?t=1024363]("http://ubuntuforums.org/showthread.php?t=1024363")

---

### Post by europa on 2008-12-30
> **SBFC said:**
> Not sure if this is what is causing your problem but I found it interesting: [http://ubuntuforums.org/showthread.php?t=1024363]("http://ubuntuforums.org/showthread.php?t=1024363")

This is not the same issue.  I had this same issue though and got it to work with these settings:

[IMG]http://img234.imageshack.us/img234/4296/screenshotwineconfigurauh6.png[/IMG]

[IMG]http://img387.imageshack.us/img387/5738/screenshotsetup304win32ql3.png[/IMG]

I also tried to install the windows98 version of ventrilo but I was having issues with uninstalling the winxp version so i'm not sure if that took or not.

Let me know what works for you.

---

### Post by captaincrook on 2009-01-03
I had Direct Input disabled, but it won't work either way on or off. Are there any other things that need to be run and/or installed? Using Hardy, dunno if I mentioned that.

---

### Post by champton on 2009-01-11
When I loaded vent before, all I would get from the devices on the setup screen is "default" for both input and output. If this is the same for you, read on...

Step 1) Make sure you can record and playback a message in Ubuntu's default Sound Recorder... Applications -> Sound & Video -> Sound Recorder. If you can't, then your mic isn't working correctly. Try adjusting settings in alsamixer from the command line.

Step 2) sudo apt-get remove Pulseaudio... This is a key factor for the issue I was having, it's blocking at least vent if not wine itself from seeing real alsa devices. I restarted my machine after doing this just to make sure it was shutdown. If you kill both pulseaudio processes you should be fine. NOTE: When removing this package I noticed it asked if I wanted to remove pulseaudio and ubuntu-desktop. I just hit enter and didn't have a problem afterwards. I assume the ubuntu-desktop in that particular package is just the gui interface for pulseaudio. 

Step 3) winecfg -> Audio -> Check only Alsa then check Driver Emulation

Step 4) Load Vent Setup, you should now see d:mix and d:snoop for the devices, select them and do not check the direct sound for either one. Also uncheck Play Key Clicks, not only is that annoying but it also seems to interfear with the outgoing audio from being played.

Hope this helps someone out there.

---

### Post by FiskFisk33 on 2009-01-22
i have your symptoms champton, but theres no pulseaudio installed :(


actually, when i press the monitor button, there should come up numbers in that list, but nothing happens.

---

### Post by kzersatz on 2009-01-22
are all of you trying to use Ventrilo ver3?

has anybody tested running the last release of Ventrilo v2?

---

### Post by FiskFisk33 on 2009-01-22
not an option for me...

---

### Post by kzersatz on 2009-01-22
mmm
last i checked ver3 wasnt a requirement for connecting to most servers

i may be mistaken though
:(

---

### Post by h4mx0r on 2009-01-22
I don't get the whole deal about sound apps. I mean there's that pulseaudio/alsa thing going on then you see apps like pidgin which don't want to add sound support. So basically everyone is generally crap at coding audio apps I suppose. A GPL app that bridged the gap between teamspeak and ventrilo with crossplatform support could easily crush all opposition in usage spectrum. I heard there was a current GPL app called mumble. If anyone wants to write a wrapper to connect mumble to teamspeak or ventrilo servers feel free to do so.

---

### Post by Lederallergie on 2009-01-26
Sorry if this has been posted already, but I have a problem where everything works fine in ventrilo until i try to speak, that all the sound in vent dies and I have to restart it.

Anyone got any ideas?

---

### Post by Zoquara on 2009-01-28
I'm having problems getting things set up... I have Wine 1.1.13, Ubuntu 8.04, and the most current Ventrilo for Windows (3.0.4) and can get no sound in Vent at all.

On the Ventrilo downloads page, I noticed "Third party utilities // Linux Ventrilo Script (Version 2.1.0_02)" What's that for? Would it be useful, or no idea?

Sorry if I'm asking dumb questions.... I just started using Ubuntu last night :???:

---

### Post by boogarat on 2009-01-29
This would be an amazingly useful forum thread on how to install Ventrilo in Ubuntu if I wasn't a linux nub and don't understand the first 3 steps .... if anyone could update me I'd greatly appreciate a more thorough explanation on steps 1-3

---

### Post by flinstonex on 2009-02-08
So every time i want to run ventrilo i need to type this into a terminal?
```
cd ~/ventrilo
wine ./Ventrilo.exe
```

Is there any way to create a desktop icon?

please and thanks.

[EDIT] Also, i dont understand step one
> 1. Add the extra repositores from the Unnoffical Ubuntu Guide:
Code:

[http://www.ubuntuguide.org/#repositories](http://www.ubuntuguide.org/#repositories)

Can someone help me with this, i don't understand what i'm supposed to do for step one.
[/EDIT]

---

### Post by Sammi on 2009-02-09
> **flinstonex said:**
> Also, i dont understand step one

Can someone help me with this, i don't understand what i'm supposed to do for step one.
[/EDIT]That link is dead. You want this: [http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Add_Extra_Ubuntu_Repositories](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Add_Extra_Ubuntu_Repositories)

---

### Post by atalon on 2009-02-21
I realize this is a ubuntu forum but was hoping to get this to work in Fedora 10. I have the python and lib ver. mentioned and I get the follow message:

```
# ./pyvent.py
Traceback (most recent call last):
  File "./pyvent.py", line 182, in <module>
    main()
  File "./pyvent.py", line 129, in main
    ctx = RECORD_DSP.record_create_context(
  File "/usr/lib/python2.5/site-packages/Xlib/display.py", line 218, in __getattr__
    raise AttributeError(attr)
AttributeError: record_create_context

```

---

### Post by Synthuir on 2009-03-10
Alright, I installed Ventrilo on Wine once, and it didn't work. I re-installed it following the exact directions above, and it worked!... For 2 days. Now whenever I log on, it says "Failed to get coder for specific codec." I can still log in, but I cannot hear nor speak whatsoever. I'm assuming the codec has something to do with the speakers/ microphone, but not sure exactly what could be wrong. Can somebody help me? Thanks.

Also, we should lobby for an Ubuntu Ventrilo :/

---

### Post by SBFC on 2009-03-10
> **atalon said:**
> I realize this is a ubuntu forum but was hoping to get this to work in Fedora 10. I have the python and lib ver. mentioned and I get the follow message:

```
# ./pyvent.py
Traceback (most recent call last):
  File "./pyvent.py", line 182, in <module>
    main()
  File "./pyvent.py", line 129, in main
    ctx = RECORD_DSP.record_create_context(
  File "/usr/lib/python2.5/site-packages/Xlib/display.py", line 218, in __getattr__
    raise AttributeError(attr)
AttributeError: record_create_context

```

I think this may be what you're looking for. 
[http://forums.fedoraforum.org/showthread.php?t=211662]("http://forums.fedoraforum.org/showthread.php?t=211662")

---

### Post by Alethenorio on 2009-03-15
I have been able to use ventrilo with speex codec pretty good for the most part (Because wine has a bug that doesn't allow GSM to work) and also PTT works when running some games (But doesnt when trying to speaking and browsing off of a proper ubuntu window like firefox or such).

I am having one real annoying problem though. I am using a Logitech MX518 mouse which has an application button on top of the scroll wheel. Running Xev shows that ubuntu recognizes that as mouse button 10 however I am able to use every single button out of my mouse when setting up PTT hotkey except for that one. Ventrilo will recognize all my mouse buttons except for that one button which is the one I usually use for PTT.

Does anybody have any idea what the problem might be?

Also any valid tips for Ubuntu 8.10 are welcome (Such as is ventriloctrl still in development and working? Is it possible to disable the side button from going back and forth through page on firefox).

Thanks

---

### Post by Alethenorio on 2009-03-29
Has nobody encountered this problem whatsoever?

I have gone through countless guides including this one

[http://ubuntuforums.org/showthread.php?t=65471&highlight=LOGITECH+MX](http://ubuntuforums.org/showthread.php?t=65471&highlight=LOGITECH+MX)

The application button seems to be recognized fine under ubuntu (At least when testing in the lamp icon under mouse preferences it is being recognized) however under the Ventrillo setup clicking on the application button to set it as PTT does nothing whatsoever. I am not sure whether it is not being recognized by wine or ventrillo itself.

Going crazy here.

---

### Post by mendres on 2009-04-02
I have Ubuntu 9.04 Beta installed, now tryed to get the script to work. Started ./pyvent but doesn't recognize any keypress. Any solution for this?

Of course, python and python-xlib installed.

---

### Post by innocente on 2009-04-09
Hey There,


i notied a little problem with this tython script :\

if i try to set keys wich aren't "repeating" keys, like CTRL, ALT, SHIFT then it doesn't work. in this case i works only if i activate the ventrilo window, or i move the mouse over the window.

Could you please fix this python script to accept keys like Left and Right ctrl, alt, shift, tab etc..

Ty

---

### Post by SBFC on 2009-04-09
> **innocente said:**
> Hey There,


i notied a little problem with this tython script :\

if i try to set keys wich aren't "repeating" keys, like CTRL, ALT, SHIFT then it doesn't work. in this case i works only if i activate the ventrilo window, or i move the mouse over the window.

Could you please fix this python script to accept keys like Left and Right ctrl, alt, shift, tab etc..

Ty

Are you saying it doesn't work with any of those keys or those keys in combination? I myself use alt so there shouldn't be a problem with any of those.

---

### Post by SBFC on 2009-04-09
> **mendres said:**
> I have Ubuntu 9.04 Beta installed, now tryed to get the script to work. Started ./pyvent but doesn't recognize any keypress. Any solution for this?

Of course, python and python-xlib installed.

It may be something in 9.04 but as I haven't upgraded (and don't plan to anytime soon) I have no way of testing.

You may like to try the original ventriloctrl as the only reason I made pyvent was because ventriloctrl didn't work in Ubuntu 8.10. Maybe it'll work with 9.04.

---

### Post by Dekafox on 2009-04-27
I'm running 8.04 64-bit, wine 1.1.20, and Ventrillo 3.01.  The issue doesn't seem to be a problem with vent per se, but maybe in communication?

I"m running it with padsp so it plays nice with WoW, which it does.  If I plug in a analog jack mic, it works.  The problem is I just was given MS Livechat USB headphones.

After a little bit of research (and installation of PulseAudio Device Chooser) I was able to get the headphone potion working fine.  The issue I'm having now is with the mic part.

For Output I have PulseAudio Virtual OSS selected, which as I said works fine.  Under Input device, I now see "Default wave mapper" "Pulseaudio Virtual OSS" and "USB Mixer".  The second one is my analog jack apparently, as that's what I used before.  The last one is the new headphones.  Now here's where it gets weird.

I can go into setup, and hit Monitor, and see feedback when I talk into it, showing Vent is seeing it.  The Volume Meter for Recording from PA device chooser shows also when I talk into it.  If I input:
arecord -f S16_LE | aplay
I hear the echo properly.  However, as soon as I connect to the actual server I get:
Failed to open input device. Another program might have it open already. rc = -1

As far as I can tell though, nothing should have it locked open.  Help?

---

### Post by kaotic2 on 2009-05-04
> **mendres said:**
> I have Ubuntu 9.04 Beta installed, now tryed to get the script to work. Started ./pyvent but doesn't recognize any keypress. Any solution for this?

Of course, python and python-xlib installed.

I'm having the same problem with 9.04- Has anyone found a way to fix this?

---

### Post by Waste on 2009-05-15
Having the same issue with the script.
It doesn't recognoze any keyboard or mouse input at all.
Any possible way to manually enter the key/mouse button you wish to use?

---

### Post by SBFC on 2009-05-17
> **Waste said:**
> Having the same issue with the script.
It doesn't recognoze any keyboard or mouse input at all.
Any possible way to manually enter the key/mouse button you wish to use?

Yes, you could. But it wouldn't matter. The part of the script that detects your button/mouse presses and then tells you the keycode behaves the same way as the part of the script that detects button/mouse presses to notify vent.

---

### Post by Waste on 2009-05-17
> **SBFC said:**
> Yes, you could. But it wouldn't matter. The part of the script that detects your button/mouse presses and then tells you the keycode behaves the same way as the part of the script that detects button/mouse presses to notify vent.

Bah, well I got the ventriloctrl to detect my keypresses but as soon as I lose focus on vent it fails to work again. I think it may have something to do with the hotkey I use which is my "forward" button on my mouse but the script didn't work on any other key on my keyboard either. This is following both install procedures mentioned with ventriloctrl.

---

### Post by Kam20 on 2009-05-24
Ok im trying to install vent and i follow the process listed above and i get stuck on step 5...this is what i get in the terminal 

kelly@kelly:~/ventrilo$ ~/.wine/drive_c/windows/system.ini
bash: /home/kelly/.wine/drive_c/windows/system.ini: Permission denied


am i doing something wrong?

---

### Post by Falc7 on 2009-05-24
Hi, i installed vent, everything seems to be working, PTT turns green ect, but ventrilo isen't using the microphone. So when i hear people talking, its through the speakers not my usb headset, and therefore they cna't hear me either, because ventrilo isen't using the headset. 
Can anyone help?

---

### Post by aquaspeeder on 2009-05-25
I have a question about an issue that I've seen pop up on winehq and, I think, the ventrilo forums but I haven't found much information on it or any fixes. 

The problem I'm having is that whenever someone tries to amplify their inbound vent settings or they try to turn up my individual volume, then one of two things happens.  Either I come thru as unbearable static or they'll hear half a word then I drop off into silence. The server is using speex,  I've got Direct sound options checked in ventrilo options and hardware accel set to full, driver emulation checked in winecfg.  My mic sounds just fine on my own system so I'm not sure what's causing this. Is this normal for everyone? Is it my onboard sound? A lot of people seem to turn up their inbound and I, reportedly, come thru as quiet so I end up having to explain this issue quite often.

---

### Post by blueadept on 2009-06-02
> **endy said:**
> I think teamspeak is being recommended as it already has a native linux client, and it's always better to support native software first.

One note on this method is it must be very cpu intensive because everything stutters with ventrilo running when I play in game (tested ET, Quake3, Doom3) and I have an AMD64 3500+ which handles evertything else I throw at it. So this is still not real solution until we get a native binary (or source) for linux.

I don't know why Flagship is worried about their code... they can release a binary on Linux the same as on Windows... I don't see how it's differnet, but I can answer the CPU issue... it's not CPU, it's ventrillo messing with the screen and wine while your game is full screen, you can solve this problem by running Ventrilo on a virtual screen... set up another user to install ventrilo in, and run "vncserver" in that user... then you can open up a virtual screen and run ventrilo there as a different user and a different copy of wine... then all will work much smoother.. you can also get a small app called "ventriloctrl" (I forget where from, but I'm sure google will know) that allows you to bind a PTT key and pass it into the wine virtual machine so that you can use PTT with vent under wine.... when I was playing wow, I found this worked very well.. although it's a little tedius to set up... we just need to harass flagship for a Linux version...

---

### Post by Shadowfaux on 2009-06-07
> **Kam20 said:**
> Ok im trying to install vent and i follow the process listed above and i get stuck on step 5...this is what i get in the terminal 

kelly@kelly:~/ventrilo$ ~/.wine/drive_c/windows/system.ini
bash: /home/kelly/.wine/drive_c/windows/system.ini: Permission denied


am i doing something wrong?

Instead of "~/.wine/drive_c/windows/system.ini" in the first line, try "sudo [name of text editor] ~/.wine/drive_c/windows/system.ini" and see if that does any better.

---

### Post by ExplicitViper on 2009-06-16
i keep getting this error. can anyone tell me how to fix it?

Failed to get encoder for specified Codec.

Unable to initialize outbound codec (GSM 6.10 - 44 KHz, 16 bit): Unable to find the specified codec

---

### Post by willemuk on 2009-06-21
> **Falc7 said:**
> Hi, i installed vent, everything seems to be working, PTT turns green ect, but ventrilo isen't using the microphone. So when i hear people talking, its through the speakers not my usb headset, and therefore they cna't hear me either, because ventrilo isen't using the headset. 
Can anyone help?


Open up the Pulseaudio Device Chooser. Go to the 'volume control'. Do this while vent is running. Click the little arrow and hoover over 'Move Stream'. Choose you usb headset.
Now you should be sorted.

You can do this for every application seperate, music over your speakers via Mplayer, music over your headset while listening to youtube etc.

Enjoy

---

### Post by geekygirl on 2009-06-29
> **ExplicitViper said:**
> i keep getting this error. can anyone tell me how to fix it?

Failed to get encoder for specified Codec.

Unable to initialize outbound codec (GSM 6.10 - 44 KHz, 16 bit): Unable to find the specified codec

It just means that the server your are connecting to with your client requires that codec to be installed in order for you to use Vent.

Mac has the same problem - it requires the Speex codec, but it needs to be installed on the server not the client end. (Speex sounds terrible compared to GSM 6.10 IMO as well lol)

---

### Post by manji_kun on 2009-06-29
this made it easy for me, a newbie to Linux to keep up with guildies from WoW it was so simple, it's almost  as if you intended it for mac users :-p

---

### Post by reiki on 2009-07-12
Or you can just go get a cheap mini laptop and run Vent on that while you game in Wine on your main machine.

:-)

---

### Post by Iksf on 2009-08-01
Mumble ftw

---

### Post by fraktik on 2009-08-10
> **ExplicitViper said:**
> i keep getting this error. can anyone tell me how to fix it?

Failed to get encoder for specified Codec.

Unable to initialize outbound codec (GSM 6.10 - 44 KHz, 16 bit): Unable to find the specified codec
Solution is easy: copy file **msgsm32.acm** to **~/.wine/drive_c/windows/system_32_/** (in older version was in **~/.wine/drive_c/windows/system/**, so move it. If is it dont enought, then:

#*gedit ~/.wine/drive_c/windows/system.ini*
ad this to *[drivers32]* section (end of file)
**MSACM.msgsm610=msgsm32.acm**


* the file **msgsm32.acm** come from Win (usualy on patch *C:/WINDOWS/system32/msgsm32.acm*) 


Here is some full english instalation text for cedega:> Lets do some changes to the ventrilo install
- Using Konqueror or similar, navigate to the fake Windows files used by Cedega for Ventrilo. In my case this is,
~/.cedega/Ventrilo/c_drive/windows
- Open up the system.ini file using your favourite text editor (KEdit) and add the following line to the bottom of the script in the Drivers 32 section
MSACM.msgsm610=msgsm32.acm
[img_assist|fid=11|thumb=0|alt=ventrilo and linux step 4]
- You have just told Ventrilo to use the MicroSoft GSM610 codec file called msgsm32.acm - this file won't have shipped with your Linux distro so go get it from somewhere and copy it to ~/.cedega/Ventrilo/c_drive/windows/system32:
cp /mnt/win/Windows/system32/msgsm32.acm ~/.cedega/Ventrilo/c_drive/windows/system32/
then change the permissions so users can use it
chmod a+r msgsm32.acm
- Your done in here so save and close all those windows. 
 from [http://www.slinux.net/how-to-install-ventrilo-2-3-on-linux](http://www.slinux.net/how-to-install-ventrilo-2-3-on-linux)

---

### Post by 8Kuula on 2009-08-13
H!

I get this error when i connect to ventrilo server:
"Unable to initalize outbound codec (GSM 6.10 - 11025 Hz, 16bit): Unable to open codec stream, Code = 8"

I have done:
- zero modifications, wine 1.1.27 should have needed files & changes, or so i did understand from patch notes.
- copied/moved msgsm32.acm file to ../windows/system/, ../windows/system32/ and ..windows/ directories. (not same time, but did try all those directories)
 - edited system.ini to add line "MSACM.msgsm610=msgsm32.acm" and commented out that wine 1.1.27 line, whitch is lowercase "msacm. ..."
- reinstalled ventrilo with default ~/.wine directory (aka did move ~/.wine other location and did install ventrilo, and did try same tricks as listed above)

yet no luck :(

Using Ubuntu 9.04-64bit, wine v1.1.27, Ventrilo 2.1.4

What im missing? :confused:
These measures have worked before.

Feels like ventrilo won't find that file for some reason, but no clue how to check that.
[FONT=monospace]
[/FONT]

---

### Post by #Peter on 2009-08-13
> **8Kuula said:**
> H!

I get this error when i connect to ventrilo server:
"Unable to initalize outbound codec (GSM 6.10 - 11025 Hz, 16bit): Unable to open codec stream, Code = 8"

I have done:
- zero modifications, wine 1.1.27 should have needed files & changes, or so i did understand from patch notes.
- copied/moved msgsm32.acm file to ../windows/system/, ../windows/system32/ and ..windows/ directories. (not same time, but did try all those directories)
 - edited system.ini to add line "MSACM.msgsm610=msgsm32.acm" and commented out that wine 1.1.27 line, whitch is lowercase "msacm. ..."
- reinstalled ventrilo with default ~/.wine directory (aka did move ~/.wine other location and did install ventrilo, and did try same tricks as listed above)

yet no luck :(

Using Ubuntu 9.04-64bit, wine v1.1.27, Ventrilo 2.1.4

What im missing? :confused:
These measures have worked before.

Feels like ventrilo won't find that file for some reason, but no clue how to check that.
[FONT=monospace]
[/FONT]

I'm having this exact problem. It used to work and now suddenly it just gives that error. Feels like I've tried everything =/

---

### Post by menikamatii on 2009-08-15
> **#Peter said:**
> I'm having this exact problem. It used to work and now suddenly it just gives that error. Feels like I've tried everything =/


me to.


i can hear, i can hear xmit button, but no one can hear me.
64 bit linux. usb mic.

[http://start.ubuntu.com/9.04/](http://start.ubuntu.com/9.04/)
*EDIT* i figured mine out. for some reason front mic was muted. 

top right  click the volume icon next to time/date  then hit volume control. turn yor mic up and make sure its not muted.

---

### Post by #Peter on 2009-08-15
> **menikamatii said:**
> me to.


i can hear, i can hear xmit button, but no one can hear me.
64 bit linux. usb mic.

[http://start.ubuntu.com/9.04/](http://start.ubuntu.com/9.04/)
*EDIT* i figured mine out. for some reason front mic was muted. 

top right  click the volume icon next to time/date  then hit volume control. turn yor mic up and make sure its not muted.

No my mic wasnt muted... As soon as I hit connect it says "Unable to initialize outbound codec (GSM 6.10 - 11025 Hz, 16 bit): Unable to open codec stream. Code = 8"

According to ventrilos own faq it is because the settings to the codecs are messed up... But I don't think I changed anything from the point it worked, so it's really weird.

---

### Post by Watch on 2009-08-16
> **#Peter said:**
> No my mic wasnt muted... As soon as I hit connect it says &quot;Unable to initialize outbound codec (GSM 6.10 - 11025 Hz, 16 bit): Unable to open codec stream. Code = 8&quot;

According to ventrilos own faq it is because the settings to the codecs are messed up... But I don't think I changed anything from the point it worked, so it's really weird.


Ventrilo's FAQ does not list this error, but rather the -8 error 

 I'm having the same problem. 
 Also this shows in console when the error occurs  ```
 err:gsm:GSM_DriverProc libgsm support not compiled in! 
```  I suppose they forgot to include libgsm in the compile...

---

### Post by #Peter on 2009-08-18
> **Watch said:**
> Ventrilo's FAQ does not list this error, but rather the -8 error 

 I'm having the same problem. 
 Also this shows in console when the error occurs  ```
 err:gsm:GSM_DriverProc libgsm support not compiled in! 
```  I suppose they forgot to include libgsm in the compile...
Oh ok, yeah my terminal gives that same error...
and also [BUMP]

---

### Post by tank110 on 2009-08-18
I had the exact same problem.
```

"Unable to initalize outbound codec (GSM 6.10 - 11025 Hz, 16bit): Unable to open codec stream, Code = 8"
```

Try going into winecfg, select the **Libraries** tab

**Add** new library, select msgsm32.acm from the drop down

Hit **Edit**, then select the **Native(Windows)** button.

This seems to have done the trick for me, good luck.

---

### Post by #Peter on 2009-08-19
> **tank110 said:**
> I had the exact same problem.
```

"Unable to initalize outbound codec (GSM 6.10 - 11025 Hz, 16bit): Unable to open codec stream, Code = 8"
```Try going into winecfg, select the **Libraries** tab

**Add** new library, select msgsm32.acm from the drop down

Hit **Edit**, then select the **Native(Windows)** button.

This seems to have done the trick for me, good luck.

Yes! That did it! Thanks man :)

---

### Post by YokoZar on 2009-08-22
I've uploaded my 1.1.28 packages for Ubuntu (9.04 is already built, 8.10
and 8.04 are still building as I write this).  One of the fixes in this
package is to build with support for libgsm, a new feature in Wine that
allows Ventrilo support out of the box.

However, this will only work on 32-bit Ubuntu at this time, as there is
no 32 bit version of this library available on Ubuntu 64.  I've already
fixed this in the development version (Ubuntu 9.10) and the "wine1.2"
package there.

As far as I know the only application affected is Ventrilo.  So just to
conclude:

Ubuntu 8.04, 8.10, 9.04 32 bit with Wine 1.1.28 or higher: Vent works.
Ubuntu 8.04, 8.10, 9.04 64 bit: Vent doesn't work.
Ubuntu 9.10 with wine1.2 package: Vent works.

Note that the "wine1.2" package is just the current Wine beta:
[http://yokozar.org/blog/archives/103](http://yokozar.org/blog/archives/103)

---

### Post by YokoZar on 2009-08-22
> **tank110 said:**
> I had the exact same problem.
```

"Unable to initalize outbound codec (GSM 6.10 - 11025 Hz, 16bit): Unable to open codec stream, Code = 8"
```

Try going into winecfg, select the **Libraries** tab

**Add** new library, select msgsm32.acm from the drop down

Hit **Edit**, then select the **Native(Windows)** button.

This seems to have done the trick for me, good luck.

Note that this may still work on 64 bit Ubuntu (because you're using windows gsm codec rather than Wine's built in one, the one that's broken on 64 bit Ubuntu before 9.10)

---

### Post by meltedblt on 2009-09-05
> **tank110 said:**
> I had the exact same problem.
```

"Unable to initalize outbound codec (GSM 6.10 - 11025 Hz, 16bit): Unable to open codec stream, Code = 8"
```Try going into winecfg, select the **Libraries** tab

**Add** new library, select msgsm32.acm from the drop down

Hit **Edit**, then select the **Native(Windows)** button.

This seems to have done the trick for me, good luck.

I've had the exact same problems, but while this solves the issue of the error code, I'm still unable to hear anything in Ventrilo as soon as I open any other program that could use sound, whether it be a music player or WoW or anything. This whole affair is giving me quite the headache.

---

### Post by Coralin on 2009-09-08
Well; I've followed the guide and gone through this thread, but can't see anyone else asking- I'm trying to get TTS working in Vent; others on the server (using windows) are able to hear it, but I'm getting nothing. The only thing I can see that may help explain it is in the vent settings, on the Speech tab- Above the "Play text-to-speech..." checkbox, there's a line of text that seems to be cut off, that says "The Microsoft Text-to-speech library is not"

Any suggestions?

---

### Post by Arminius on 2009-09-09
I've managed to get wine to install fine, and it's connected to the servor fine.
and I'm heading audio, just not over the headphones with the mic.

I went to system/preferences/sound
and set everything to usb logitech headset
but each time I bring up vent all I can hear is people over the original PC speakers

---

### Post by warpasylum on 2009-09-14
Hey guys,
     Installed this to my system running Jaunty with wine 1.0.1-0ubuntu6 and it runs perfectly out of the box following the original post. Only had to mess with the settings of my sound card a little. Thanks. :guitar:

---

### Post by ajax111 on 2009-09-25
Hello all. I get this error as well:

>Failed to get encoder for specified Codec.

>Unable to initialize outbound codec (GSM 6.10 - 44 KHz, 16 bit): Unable to find the specified codec.

I am running Ubuntu 9.04 and Wine 1.01
I am super new to Linux. 
So far I have installed Ventrillo (obviously) and successfully connected to the server. But can not hear *or* be heard and my PTT (left Alt) key does not work
I have gone through my Volume Settings, unmuted the mic and such
Gone to Applications>Wine configuration>Audio and selected the default (ALSA Driver)
Then to Applications>Wine configuration>Libraries and could not find the file "msgsm32.acm"

All the instructions I can find in this thread to replace that file or copy it, seem to be focused on Cedega and not Wine. Can someone help clarify the steps I need to take to  acquire the missing "msgsm32.acm" file and where to place it once I do get it. Then when I've got that fixed what do I do to get my PTT button to work? And when I'm playing an MMORPG how do I set it up that the PTT button will work in conjunction with it? Thanks in advance.

---

### Post by Sammi on 2009-09-27
> **ajax111 said:**
> Hello all. I get this error as well:

>Failed to get encoder for specified Codec.

>Unable to initialize outbound codec (GSM 6.10 - 44 KHz, 16 bit): Unable to find the specified codec.

I am running Ubuntu 9.04 and Wine 1.01
I am super new to Linux. 
So far I have installed Ventrillo (obviously) and successfully connected to the server. But can not hear *or* be heard and my PTT (left Alt) key does not work
I have gone through my Volume Settings, unmuted the mic and such
Gone to Applications>Wine configuration>Audio and selected the default (ALSA Driver)
Then to Applications>Wine configuration>Libraries and could not find the file "msgsm32.acm"

All the instructions I can find in this thread to replace that file or copy it, seem to be focused on Cedega and not Wine. Can someone help clarify the steps I need to take to  acquire the missing "msgsm32.acm" file and where to place it once I do get it. Then when I've got that fixed what do I do to get my PTT button to work? And when I'm playing an MMORPG how do I set it up that the PTT button will work in conjunction with it? Thanks in advance.Dude read what Yodozar is saying. Just update Wine to the newest version: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by Mandraix on 2009-09-27
Even when I ran both on Windows XP, TeamSpeak had more delay than Vent.

---

### Post by Duskao on 2009-09-30
Hey guys. I have got Ventrilo working pretty much perfect, except for PTT. I set it up using the guide in winehq.org. It is showing that the button is working fine in ventrilo, my little speaker lights up green when I press the button, but nobody can hear me. I used audacity to see if my mic is working and it is. It's quiet, but it is working. 
I'm fairly new to Ventrilo so if someone could let me know the things I need to have checked or unchecked in the setup part that would be great. 
Oh, I can hear everyone else in my guild talk.

Oh yeah, I'm using wine 1.1.30.

---

### Post by Tr10 on 2009-10-01
> **Duskao said:**
> Hey guys. I have got Ventrilo working pretty much perfect, except for PTT. I set it up using the guide in winehq.org. It is showing that the button is working fine in ventrilo, my little speaker lights up green when I press the button, but nobody can hear me. I used audacity to see if my mic is working and it is. It's quiet, but it is working. 
I'm fairly new to Ventrilo so if someone could let me know the things I need to have checked or unchecked in the setup part that would be great. 
Oh, I can hear everyone else in my guild talk.

Oh yeah, I'm using wine 1.1.30.

I am experiencing the same problem.

I have been using vent for years, yet I recently moved over to linux. I have been using ubuntu 8.10 for a little over 6 months. Ventrilo was working perfectly with PTT and a handy python script to let me use it while working. Ever seen I upgraded to wine 1.1.30 I have experienced the same problem described above. Ventrilo will let me talk for 4-6 seconds, then "Freeze" and prevent anyone from hearing me while displaying to me the green microphone stating that I am transmitting.

The only way to talk again is to open setup or restart vent.

I have read that this might be related to OSS and/or ALSA but I have never had a problem like this until I upgraded.

Any ideas?
Thanks for the input.

---

### Post by astendra on 2009-10-19
> **Tr10 said:**
> Ventrilo will let me talk for 4-6 seconds, then "Freeze" and prevent anyone from hearing me while displaying to me the green microphone stating that I am transmitting.

The only way to talk again is to open setup or restart vent.


I was able to fix this issue by disabling DirectSound in the ventrilo setup menu.

---

### Post by Lerena on 2009-10-24
I installed Ventrilo under Wine today, because I wanted to join a conversation my friend was having. As it turns out, I'm having difficulty getting my microphone to work. I checked with my dad since he's fairly good at this sort of thing and he couldn't get it to work either.

I'm not sure where to post this issue, but the main problem IS getting my microphone to work in Vent so I'll try this thread.

-My microphone is plugged in well and in the correct place
-I checked my volume to make sure it was enabled
-I tested in my settings to make sure it worked
-I even recorded myself in the sound recorder, but nothing recorded.
-I turned DirectSound off and an error popped up.

I can't be completely sure that my microphone doesn't work just yet, but that is what I believe. However, I want to make sure before going out and buying a new one. I'm using a cheap headset and my microphone worked until I switched to Ubuntu. I'm clueless how to get it working now.

Any suggestions or advice for me? I'm new to Ubuntu so please speak in newbie terms for me.

---

### Post by Rayve on 2009-10-26
Lerena,

Have you checked to make sure your sound isn't muted, either via your headphones or in vent?  I've had it before and not realize it.  Also, did you change your settings in System > Preferences > Sound for your headphone/mic to work?

Good luck!

---

### Post by Lerena on 2009-10-30
Maybe I didn't change my settings in system preferences. Where in my system sound preferences do I enable the microphone?

---

### Post by sunfire on 2009-10-30
> **Duskao said:**
> Hey guys. I have got Ventrilo working pretty much perfect, except for PTT. I set it up using the guide in winehq.org. It is showing that the button is working fine in ventrilo, my little speaker lights up green when I press the button, but nobody can hear me. I used audacity to see if my mic is working and it is. It's quiet, but it is working. 
I'm fairly new to Ventrilo so if someone could let me know the things I need to have checked or unchecked in the setup part that would be great. 
Oh, I can hear everyone else in my guild talk.

Oh yeah, I'm using wine 1.1.30.


I had some problems with working mic after pulseaudio update in 9.10 beta with wine 1.1.30 to 1.1.32. My mic stopped working. 

But after removing PULSEAUDIO and making
[X] Use Direct Sound -> [ ] Use Direct Sound  , from Ventrillo setup my mic started working fine again.

---

### Post by Unhumanje on 2009-11-13
I followed all the steps from the winehq guide,but upon connecting to a server I get this:
Unable to activate DirectSound for selected device.
DirectSoundCaptureCreate failed. HR=DSERR_NODRIVER. No sound driver is available for use.
Any ideas on a fix?Doesn't allow me to use my microphone,even though it's working perfectly in the ubuntu sound test.

p.s. I'm running ubuntu 9.10 and unfortunately I removed pulseaudio as the winehq recommended,so now I can't even start preferences-> Sound :X
Though mic still works in skype.

---

### Post by clearscreen on 2009-11-19
I'm not sure if this has been posted yet, better safe than sorry ;)

There is no longer a need to run Ventrilo through Wine! We have been working on an open-source alternative to this problem: [Mangler](http://www.mangler.org).

Mangler 1.0 will be released on the 1st of december, but there are already packages for our first release candidate and with a second release candidate being released this friday.

Current features include but not limited to:

[LIST=1]
[*]Connecting to Ventrilo 3.x servers
[*]Keyboard push to talk
[*]Mouse button push to talk
[*]Speex and GSM support
[*]Per-user volume controls
[*]Notification sound effects
[*]Setting your comment and URL
[/LIST]

I encourage anyone that wants to connect to ventrilo servers from Ubuntu (or any other Linux distro for that matter) to try. You won't be disappointed :)

Packages for various distributions and/or instructions for building from subversion can be found on [our download page](http://www.mangler.org/download/).

---

### Post by Alatar1 on 2009-11-19
My vent works just fine, im on jaunty, with wine 1.1.33 and i use direct sound, sounds great!
By the way try to ensure that whatever server your on uses the "Speex" codec, It works with linux as well as mac. Sounds fantastic to me. :)

I just downloaded vent, ran the installer through wine, and made sure to annoy my server admin to use speex, and it works spectacularly, and by the way, teamspeak my have a native linux client, but it sound like garbage in my all my experiences using it. and ventrilo servers have to be paid for.
Pretty much assures that you get proffessional tech support for vent servers and excellent sound quality.

*edit* 
Oh and can anyone get me that script to people to use PTT when its not themain window, It works when running behind WoW and other games just fine, but not behind anything else, only issue ive ever had with vent.

---

### Post by Vistro on 2009-12-01
Don't know if this has already been said, but upgrading to WINE1.2 removes the need for the winelib and winelib-asla packages, and it seems that the driver comes with WINE now.

---

### Post by aarons6 on 2009-12-07
there is a native client now.. check out [http://www.mangler.org/](http://www.mangler.org/)

---

### Post by farfrael on 2010-02-06
Hello,

Ventrilo installed successfully with wine.
microphone works fine but having some issues with the focus.

tried using both pyvent.py and ventriloctrl, recompiled the X server to make sure the record extension is installed and loaded. 

Either script launches but they do not detect any key press.
I tried using /dev/input/eventx (with x from 1 to 3) but still no success

somewhat stumped at this point ... what else did I miss that would be required for the key detection to work? Using x server 1.6.3

any help would be much appreciated

[SOLVED] was a permission problem. Now working fine

---

### Post by deaxd on 2010-05-09
Failed to get encoder for specified Codec. 

Unable to initialize outbound codec (GSM 6.10 - 22 KHz, 16 bit): Unable to find the specified codec. 



I'm using Ubuntu 9.10 Karmic Koala, and Wine 1.0.1, Ventrilo 3.0.5. There's no sound on games and ventrilo,..

Bugs:
1348	RegisterHotKey and UnregisterHotKey are not implemented. (Affects e.g. Adobe Photoshop.)	NEW		View
5178	Ventrilo loses talk ability while using Push-To-Talk option	NEW		View
5623	GetAsyncKeyState wrong if querying process doesn't have focus	NEW		View
5924	Ventrilo error when multiple people talk	NEW		View
8103	Ventrilo list does not draw correctly at times	NEW		View
10495	Wine should support PulseAudio	NEW		View
13500	ventrilo only supports half duplex	UNCONFIRMED		View
16600	Ventrilo starts having a long delay after some time

What works
Everything works using Speex codec

What does not
Any other codec

What was not tested
Nothing

Additional Comments
As long as you use Speex, it works fine. Can't get GSM 6.10 to work.


//from [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9832](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9832)

---

### Post by Kmus on 2010-05-25
Thank you aarons6 Mangler ([http://www.mangler.org/](http://www.mangler.org/)) is just what I need it. 

It works great :P[URL="http://www.mangler.org/"]
[/URL]

---

### Post by SamuelDinnadge on 2010-05-25
Awesome post!

---

### Post by schtufbox on 2010-05-26
> **aarons6 said:**
> there is a native client now.. check out [http://www.mangler.org/](http://www.mangler.org/)
Excellent stuff, thanks.

---

### Post by AlmightyMokona on 2011-06-30
Check out Mumble guys, I much prefer it to vent. Better quality, open source, better latency.

[http://mumble.sourceforge.net/Installing_Mumble](http://mumble.sourceforge.net/Installing_Mumble)

---

