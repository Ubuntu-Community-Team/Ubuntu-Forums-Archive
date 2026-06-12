---
title: "Flash"
date: 2008-04-24
forum: x86 64-bit Users
---

### Post by frcr on 2008-04-24
Haha!
Old posts archived, so we have a lot of free space for "MY FLASH DOESNT WORKZOR!!!111oneeleven" threads!

Since old script cant help with installing flash on Hardon i have to ask: Do you have any solution for this? Or should we just wait for Gnash release?

---

### Post by dom1n1k on 2008-04-24
Try install Gnash you can find it on Firefox plugins tab..

---

### Post by soxs on 2008-04-24
Flash just works fine. What did you do to install flash?
```
sudo apt-get install flashplugin-nonfree
``` did it for me

---

### Post by drfox on 2008-04-24
It doesn't work for me. I've removed and reinstalled flashplugin-nonfree multiple times. Gnash doesn't give me audio and often doesn't work for video either. Funny, because Flash was working until FF 3b4 came out. Not sure if it's Firefox or Hardy or my video card (nvidia). 

I'd appreciate any help.

Larry

---

### Post by stc77 on 2008-04-24
After upgrading to Herdy, my flash stopped working too. But indeed it has been installed as stated above. The problem seems to be, that the correct links for firefox 3b are missing: 
This solved the problem for me: 

sudo rm /usr/lib/firefox-3.0b5/plugins
sudo ln -s  /usr/lib/mozilla/plugins /usr/lib/firefox-3.0b5/

---

### Post by Tsukino Kyuuketsuki on 2008-04-24
I tried the 'sudo apt-get install flashplugin-nonfree' a thousand times, reinstalled flashplugin-nonfree million times and couldn't fix the problem... until I just went to google and looked for a tutorial, lol!

This is what I did:

1.- Download the stuff [here]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash"), lol 

2.- Go to the terminal
```
tar -zxvf install_flash_player_9_linux.tar.gz
```

then...
```

cd install_flash_player_9_linux/
./flashplayer-installer
```

3.- Close all the browsers and press enter.

4.- 'Proceed with the installation?' type Y and press enter....

And that's how I fixed it :) Hope it helps!

---

### Post by st0nedpenguin on 2008-04-24
I went to YouTube and Firefox demanded a plugin, I let it search and it offered me the Flash plugin and installed it itself.

No guides needed.

---

### Post by FredB on 2008-04-25
> **dom1n1k said:**
> Try install Gnash you can find it on Firefox plugins tab..

Forget Gnash. It can't play most video on other site than youtube.

Swfdec is a good and free alternative for flash.

---

### Post by jespdj on 2008-04-25
> **drfox said:**
> It doesn't work for me. I've removed and reinstalled flashplugin-nonfree multiple times. Gnash doesn't give me audio and often doesn't work for video either. Funny, because Flash was working until FF 3b4 came out. Not sure if it's Firefox or Hardy or my video card (nvidia).
What does "it doesn't work" mean? Do you get any error messages? If yes, then what are the error messages?

**sudo apt-get install flashplugin-nonfree** works without any problems for me, Flash in FF3b5 works just fine. In 64-bit Ubuntu it automatically installs nspluginwrapper, downloads Flash from the Adobe website and installs it.

---

### Post by hackle577 on 2008-04-25
I'm having trouble with this too. The first time I went to YouTube I let FF3b5 install the regular Flash plugin (not Swfdec or Gnash). After that, it worked fine for one day, now I don't get video or audio. :(

EDIT: I also have flashplugin-nonfree installed, could that be creating a conflict somehow?

---

### Post by The Pinny Parlour on 2008-04-25
swfgec and gnash are troublesome.  Adobe flash works the best IMO.

Remove swfgec and gnash via Synaptic Package Manager.  Install via Synaptic, Adobe Flash.  Everything just works then.

---

### Post by hackle577 on 2008-04-25
I never installed them. I just used Adobe's. It's worked since yesterday when I upgraded but now it's on the fritz. :-\

---

### Post by hackle577 on 2008-04-25
Ok, wtf lol. It's working fine now although I didn't do anything...

---

### Post by chih on 2008-04-25
> **stc77 said:**
> After upgrading to Herdy, my flash stopped working too. But indeed it has been installed as stated above. The problem seems to be, that the correct links for firefox 3b are missing: 
This solved the problem for me: 

sudo rm /usr/lib/firefox-3.0b5/plugins
sudo ln -s  /usr/lib/mozilla/plugins /usr/lib/firefox-3.0b5/

This worked for me! Thanks, stc77. I attempted sudo apt-get install flashplugin-nonfree several times before settling for swfdec-mozilla, which worked for youtube (but gave an ugly preview image, haha). However it did not work for vimeo.com, so I finally tried this method and it worked, woohoo.

---

### Post by kklimonda on 2008-04-25
Hi,
  I have a problem with flash on 8.04 x86_64 (ya, rly ;]).. I've installed flashplugin-nonfree, libflashsupport and everything works fine - i can watch youtube videos, play all those nifty flash games and watch great adverts.. at least for as long as something goes wrong and flash dies.. Then all i can do is restart Firefox to get it working again. I had similar issues under Fedora 8 x86_64 (it has also died) but i could just reload page and it worked.

---

### Post by Pancetilla on 2008-04-26
> **stc77 said:**
> After upgrading to Herdy, my flash stopped working too. But indeed it has been installed as stated above. The problem seems to be, that the correct links for firefox 3b are missing: 
This solved the problem for me: 

sudo rm /usr/lib/firefox-3.0b5/plugins
sudo ln -s  /usr/lib/mozilla/plugins /usr/lib/firefox-3.0b5/

Worked for me, thank you very much.

---

### Post by FredB on 2008-04-26
> **The Pinny Parlour said:**
> swfgec and gnash are troublesome.  Adobe flash works the best IMO.

Remove swfgec and gnash via Synaptic Package Manager.  Install via Synaptic, Adobe Flash.  Everything just works then.

Well... As there is no version for 64 bits distro, swfdec is one of the answer. And flash is now more a pollution than everything else on the web.

I will celebrate 11 years on the internet next august...

---

### Post by nikosal on 2008-04-27
After the 8,04 upgrade, flash on firefox 2 still on the system worked just fine, but on firefox 3.05b not at all. 
God knows how many different things I tried and advices I used. 

[LIST]
[*]Auto installation (you know, the window that appears and asks you to search and add plugins, the moment you have visited a flash site).After the first "installation" system was responding "you already have the flash player installed) but still no flash content 
[*] Uninstalling and reinstalling 3.0.5b numerous times
[*] Manual installations (half a dozen)
[*]Copying the libflashplayer.so file... here and there around the pc 
[*]And various other things found here or on other sites/documentation/forums (I believe I have forgotten what most of these attempts were about), with still no result
[/LIST]

So it still was "firefox 2 ok, 3 not". 

Then I read the above message: 
sudo rm /usr/lib/firefox-3.0b5/plugins
sudo ln -s /usr/lib/mozilla/plugins /usr/lib/firefox-3.0b5/

And that was my problem solver!!!! Thanks alot!
[I]
Question of the novice: What exactly seems that my problem was after all this? [/I]

---

### Post by enchantedsky on 2008-04-27
Adobe's Flash player for Linux sucks. Youtube videos maximized are choppy, and make my CPU reach 100%. I know it's not my computers fault because:

1) Older versions of Flash 9 have smooth video, and CPU levels are low

2) Windows XP Flash has smooth video on the same computer.

---

### Post by The Pinny Parlour on 2008-05-02
> **enchantedsky said:**
> Adobe's Flash player for Linux sucks. Youtube videos maximized are choppy, and make my CPU reach 100%. I know it's not my computers fault because:

1) Older versions of Flash 9 have smooth video, and CPU levels are low

2) Windows XP Flash has smooth video on the same computer.

My experience is yours in reverse. go figure.

---

### Post by shane2peru on 2008-05-02
> **stc77 said:**
> After upgrading to Herdy, my flash stopped working too. But indeed it has been installed as stated above. The problem seems to be, that the correct links for firefox 3b are missing: 
This solved the problem for me: 

sudo rm /usr/lib/firefox-3.0b5/plugins
sudo ln -s  /usr/lib/mozilla/plugins /usr/lib/firefox-3.0b5/

Nice fix, thanks!

Shane

---

### Post by thekat on 2008-05-02
Fresh install here...

I just used apt-get ..
[B]
but..[/B]

[B]Sometimes I have to restart FireFox for flash to work.. 
[/B]
tk

---

### Post by mt330404 on 2008-05-03
good god.. ive been scouring the ubuntu forums for a solution to my flash problem including every solution mentioned in this thread, without success.

All sound was working great with Gutsy, but as soon as I upgraded to Hardy I had these issues. I'm finding that my dvd/mp3 players will playback music and video just fine, UNTIL i visit a webpage with flash video. The flash audio won't work, and it causes the audio in my dvd/mp3 players to stop working too. Sounds like an ALSA issue but I checked all my settings and tried changing some things up in my System>Preferences>Sound but no solution there. I have to restart my laptop in order to get my dvd/mp3 sound to come back.

I'm literally dying to figure out what the deal is here. Like I said, I tried every conventional sound troubleshoot but nothing at ALL has worked so far. I'm running a Sony VAIO VGN-A150 with Hardy Heron. 

PLEASE HELP!!!!!!

---

### Post by st0nedpenguin on 2008-05-04
> **FredB said:**
> Well... As there is no version for 64 bits distro, swfdec is one of the answer. And flash is now more a pollution than everything else on the web.

I will celebrate 11 years on the internet next august...

Lord knows what I'm running on 64 bit Hardy then...

---

### Post by Kidaf on 2008-05-06
I just past the last 3 hours working on a solution to my flash problems.

First of all, I uninstalled my non-free flash, and installed flash support through Firefox, just entering youtube and using Firefox built-in plugin installer (first option, Adobe (installer)).

Then, to correct my flash audio issue, I found out that Hardy comes with Pulseaudio as default, which is kinda buggy yet. So, stop and close your music player and any other app that plays sound, go to System > Preferences > Sound and change all to ALSA.

Now, on your terminal just stop pulseaudio from running 
```
killall pulseaudio
```

And rename the pulseaudio folder to avoid it being started again (avoid useless memory use)
```
mv .pulse .pulse-bak
```


Not only PulseAudio is flawed with flash, it just allows one audio stream. So you wouldn't be able to play your music player along with a flash audio, for instance. And that can easily be done with the good old ALSA.


Just cannot figure why Hardy comes with this PulseAudio crap.

---

### Post by soxs on 2008-05-06
> **Kidaf said:**
> I just past the last 3 hours working on a solution to my flash problems.

First of all, I uninstalled my non-free flash, and installed flash support through Firefox, just entering youtube and using Firefox built-in plugin installer (first option, Adobe (installer)).

Then, to correct my flash audio issue, I found out that Hardy comes with Pulseaudio as default, which is kinda buggy yet. So, stop and close your music player and any other app that plays sound, go to System > Preferences > Sound and change all to ALSA.

Now, on your terminal just stop pulseaudio from running 
```
killall pulseaudio
```

And rename the pulseaudio folder to avoid it being started again (avoid useless memory use)
```
mv .pulse .pulse-bak
```


Not only PulseAudio is flawed with flash, it just allows one audio stream. So you wouldn't be able to play your music player along with a flash audio, for instance. And that can easily be done with the good old ALSA.


Just cannot figure why Hardy comes with this PulseAudio crap.

Because its api is beautifull and dynamically, you can easily use plug and play usb headsets and all that stuff which bothers hell out of you when using alsa. The only problem, pulse audio has is that it is *new*, so it is a little buggy and only a minor percentage supports it. But it definitly IS the future.

---

### Post by peakshysteria on 2008-05-06
> **st0nedpenguin said:**
> I went to YouTube and Firefox demanded a plugin, I let it search and it offered me the Flash plugin and installed it itself.

No guides needed.

Same here. Working. But CPU is 100% while playing. Can someone else verify this? Or can it be fixed?

---

