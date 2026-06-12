---
title: "Realplayer"
date: 2006-06-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by sweeper on 2006-06-02
Hi, my first post please excuse the fact that I am probably asking a much asked question :)
I have the new Dapper Ubuntu 64bit version, I downloaded Realplayergold.bin to my desktop and then entered into my teminal
cd ~/Desktop
sudo apt-get install libstdc++5
chmod +x RealPlayer10Gold.bin
sudo ./RealPlayerGold.bin

as per Wiki instructions but it tells me no such file exists?

Is there another way to get Realplayer for the 64bit Dapper?

I have never used Linux before and Ubuntu is just amazing but I really need realplayer before I can drop Windoze completely ;)

---

### Post by Sarisar on 2006-06-02
Oh I had trouble with realplayer and couldn't get the damn thing working even after reading the forum posts.

HOWEVER I managed to muddle my way through it.

I tried to install it the way it said and it didn't work, however I did have files in the wrong place and it mentioned where they were (run real through a console and it will saying missing /something/somewhere/filename.  I found I had those files in another place so I copied them over into that directory and it ran.

Now I have forgotten what files and where but I did make notes, and my notes say:

```
www.real.com/linux
However it causes problems sometimes so you may have to run the dkpg bit and then copy files over manually.
```

Which aren't really helpful.

So I know this isn't complete instructions (sorry) but maybe enough to nudge you in the right direction.  If it is let me know what you do have to do so I can update my notes.

Thanks :)

---

### Post by sweeper on 2006-06-02
[QUOTE=Sarisar]Oh I had trouble with realplayer and couldn't get the damn thing working even after reading the forum posts.

HOWEVER I managed to muddle my way through it.

I tried to install it the way it said and it didn't work, however I did have files in the wrong place and it mentioned where they were (run real through a console and it will saying missing /something/somewhere/filename.  I found I had those files in another place so I copied them over into that directory and it ran.

Now I have forgotten what files and where but I did make notes, and my notes say:

```
www.real.com/linux
However it causes problems sometimes so you may have to run the dkpg bit and then copy files over manually.
```

Which aren't really helpful.

So I know this isn't complete instructions (sorry) but maybe enough to nudge you in the right direction.  If it is let me know what you do have to do so I can update my notes.

Thanks :)[/QUOTE]

Thanks for reply. That might help if this wasn't my second day with any Linux at all :)
I think I may just install the 32 bit version.

Thanks anyway:)

---

### Post by henriquemaia on 2006-06-02
I just installed the normal realplayer for 32 bit and it is working like a charm. No complaints.

---

### Post by sweeper on 2006-06-02
I downloaded the 64 bit live cd last time, I would like just an install of the 32 bit (not live) is it called 'alternate' instead of 'desktop' please?

---

### Post by henriquemaia on 2006-06-02
[quote=sweeper]I downloaded the 64 bit live cd last time, I would like just an install of the 32 bit (not live) is it called 'alternate' instead of 'desktop' please?[/quote]

Yes. Alternate is not live. Download the alternate i386 version to have 32 bit.

---

### Post by sweeper on 2006-06-02
Thanks, there is also a 'server' version (not too sure what the difference is), I am downloading both anyway:)
Looks like alternate has more advanced install options which I don't really need.

---

### Post by henriquemaia on 2006-06-02
[quote=sweeper]Thanks, there is also a 'server' version (not too sure what the difference is), I am downloading both anyway:)
Looks like alternate has more advanced install options which I don't really need.[/quote]

Server is for minimum installations, without gui.

---

### Post by sweeper on 2006-06-02
[QUOTE=henriquemaia]Server is for minimum installations, without gui.[/QUOTE]

Ah OK thanks for clearing that up. :)

It's a shame I have to use the 32bit version just because I can't get realplayer for the 64 bit. Anyway I am still loving Ubuntu :)

---

### Post by JoWilly on 2006-06-02
realplayer 32 works perfectly in 64 bit. Search the forums, this was discussed 1-2 days ago.

Just install the deb with dpkg -i --force-architecture. Latest deb available in the marillat repos is version 10.07.

---

### Post by sweeper on 2006-06-03
[QUOTE=JoWilly]realplayer 32 works perfectly in 64 bit. Search the forums, this was discussed 1-2 days ago.

Just install the deb with dpkg -i --force-architecture. Latest deb available in the marillat repos is version 10.07.[/QUOTE]
I can't access the marillat repos I have added 
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) stable main 

to my source list but I get a message about a pubkey, any help would be very much appreciated.

---

### Post by Jiilik on 2006-06-03
Looking at the original post, there's a typo in there... the last and second to last lines should both refer to the same filename-- there's a '10' missing in there I think.

---

### Post by sweeper on 2006-06-03
[QUOTE=Jiilik]Looking at the original post, there's a typo in there... the last and second to last lines should both refer to the same filename-- there's a '10' missing in there I think.[/QUOTE]

I noticed that too :)
I added the 10 and still no luck, but I have just tried it again and it's installed, however firefox now crashes on the bbc website, and I wanted RealPlayer to listen to the BBC. 

I think I read somewhere about need ing to put some files in Firefoxs folder, I can't remember where I saw the post though, can anyone help please?

---

### Post by JoWilly on 2006-06-03
hhmm.... so the realplayer plugin crashes firefox ?

... have you tried with the mplayer mozilla plugin ? it is "supposed" to play realmedia... (need to uninstall realplayer first)

---

### Post by sweeper on 2006-06-03
I can't uninstall it now, it says 'not available in any software channel.'

---

### Post by JoWilly on 2006-06-03
[QUOTE=sweeper]I can't uninstall it now, it says 'not available in any software channel.'[/QUOTE]

Remove it from the shell with dpkg -r

---

### Post by JoWilly on 2006-06-03
FYI you can see all the formats the mplayer plugin supports by typing "about:plugins" in the firefox location bar.

EDit: geez it puts a smiley.... about : plugins

---

### Post by sweeper on 2006-06-03
[QUOTE=JoWilly]FYI you can see all the formats the mplayer plugin supports by typing "about:plugins" in the firefox location bar.

EDit: geez it puts a smiley.... about : plugins[/QUOTE]

I tried it and Firefox crashed](*,) 

> 
Remove it from the shell with dpkg -r

Can you tell me how to do that please?

---

### Post by JoWilly on 2006-06-03
[QUOTE=sweeper]I tried it and Firefox crashed](*,) 



Can you tell me how to do that please?[/QUOTE]

Yep... it crashed because of the realplayer plugin.

To uninstall realplayer open the gnome-terminal and do:

"sudo dpkg -r realplayer" (or the realplayer name of your deb)

---

### Post by JoWilly on 2006-06-03
FYI the realplayer plugin should work fine with any 32 bit browser. I.ex, get firefox32 from getfirefox.com (or swiftfox from getswiftfox.com). Then extract it and launch it from its folder. It should work out of the box and you can also automatically have it install flash by clicking on a flash video's install request.

---

### Post by sweeper on 2006-06-03
[QUOTE=JoWilly]Yep... it crashed because of the realplayer plugin.

To uninstall realplayer open the gnome-terminal and do:

"sudo dpkg -r realplayer" (or the realplayer name of your deb)[/QUOTE]

I get this

dpkg - warning: ignoring request to remove realplayer which isn't installed.

edit
Also I can't download swiftfox because Friefox crashes when I click on any downloads too. I installed Epiphany from synaptic but that crashes too.

---

### Post by JoWilly on 2006-06-03
It seems that realplayer for amd64 is comming real soon now !

You can check the nightly builds here:

[http://forms.helixcommunity.org/helix/builds/?category=realplay-current]("http://forms.helixcommunity.org/helix/builds/?category=realplay-current")

According to the build log, the amd64 build failed. We can have high hopes that this will compile soon :)

---

### Post by JoWilly on 2006-06-03
[QUOTE=sweeper]I get this

dpkg - warning: ignoring request to remove realplayer which isn't installed.

edit
Also I can't download swiftfox because Friefox crashes when I click on any downloads too. I installed Epiphany from synaptic but that crashes too.[/QUOTE]

Manually delete the realplayer plugin (in /usr/lib/firefox/plugins or /usr/lib/mozilla/plugins or /usr/lib/mozilla-firefox/plugins). (run sudo nautilus)

To remove the deb try "sudo dpkg -r realplayer_10.0.7" if this is the name of the deb.

EDIT : but if you have manually deleted the plugin, you can keep realplayer if you want :)

---

### Post by JoWilly on 2006-06-03
to get swiftfox, in a terminal do:

"wget -c http://getswiftfox.com/builds/releases/swiftfox-1.5.0.4-athlon64.tar.bz2"

---

### Post by sweeper on 2006-06-03
[QUOTE=JoWilly]Manually delete the realplayer plugin (in /usr/lib/firefox/plugins or /usr/lib/mozilla/plugins or /usr/lib/mozilla-firefox/plugins). (run sudo nautilus)

To remove the deb try "sudo dpkg -r realplayer_10.0.7" if this is the name of the deb.

EDIT : but if you have manually deleted the plugin, you can keep realplayer if you want :)[/QUOTE]

No sign of it in firefox plugins and no variation of sudo dpkg -r realplayer is working either.

---

### Post by JoWilly on 2006-06-03
[QUOTE=sweeper]No sign of it in firefox plugins and no variation of sudo dpkg -r realplayer is working either.[/QUOTE]

Check the name of the deb file to see what its name is...

---

### Post by sweeper on 2006-06-03
[QUOTE=JoWilly]Check the name of the deb file to see what its name is...[/QUOTE]

It was a bin file RealPlayer10GOLD.bin, I have found the plugins in the firefox folder there are two nphelix files I cannot delete them though, the 'move to wastebasket' option is greyed out.

---

### Post by JoWilly on 2006-06-03
[QUOTE=sweeper]It was a bin file RealPlayer10GOLD.bin, I have found the plugins in the firefox folder there are two nphelix files I cannot delete them though, the 'move to wastebasket' option is greyed out.[/QUOTE]

Owww.. so it was not a deb, you could have tried a long time  !

The options are greyed out because you need to start nautilus as root.

Do: "sudo nautilus"

---

### Post by sweeper on 2006-06-03
[QUOTE=JoWilly]Owww.. so it was not a deb, you could have tried a long time  !

The options are greyed out because you need to start nautilus as root.

Do: "sudo nautilus"[/QUOTE]

OK thats sorted out the crashing, thanks for your help Jo :)

I will work on seeing if mplayer will do what I need tomorrow.

---

### Post by JoWilly on 2006-06-03
[QUOTE=sweeper]OK thats sorted out the crashing, thanks for your help Jo :)

I will work on seeing if mplayer will do what I need tomorrow.[/QUOTE]

Yep, and if mplayer doesn't do it, install 32 bit firefox or swiftfox as I said. The realplayer plugin should then work.

---

### Post by sweeper on 2006-06-03
[QUOTE=JoWilly]Yep, and if mplayer doesn't do it, install 32 bit firefox or swiftfox as I said. The realplayer plugin should then work.[/QUOTE]

I have downloaded swiftfox it is a tar.bz2 file I unpacked but don't know how to install it, can you help with that please?

---

### Post by JoWilly on 2006-06-03
[QUOTE=sweeper]I have downloaded swiftfox it is a tar.bz2 file I unpacked but don't know how to install it, can you help with that please?[/QUOTE]

Just enter the dir and double click on swiftfox to start it.

You can then put the swiftfox dir into your home dir, and if you want, reconfigure the firefox web icon lauchers properties to point to it...

---

### Post by sweeper on 2006-06-03
[QUOTE=JoWilly]Just enter the dir and double click on swiftfox to start it.

You can then put the swiftfox dir into your home dir, and if you want, reconfigure the firefox web icon lauchers properties to point to it...[/QUOTE]

Is this the one?    '"swiftfox" is an executable text file.' When I click it Mozilla opens?

I need some sleep anyway, thanks again :)

---

### Post by JoWilly on 2006-06-03
[QUOTE=sweeper]Is this the one?    '"swiftfox" is an executable text file.' When I click it Mozilla opens?

I need some sleep anyway, thanks again :)[/QUOTE]

Yep, that's it :) 

Have a good sleep ;)

---

### Post by sweeper on 2006-06-04
[QUOTE=JoWilly]Yep, that's it :) 

Have a good sleep ;)[/QUOTE]

Thanks Jo, back soon with more questions no doubt ;)

---

### Post by JoWilly on 2006-06-04
[QUOTE=sweeper]Thanks Jo, back soon with more questions no doubt ;)[/QUOTE]

I'll be waiting for you ;)

---

### Post by sweeper on 2006-06-04
[QUOTE=JoWilly]I'll be waiting for you ;)[/QUOTE]

I downloaded swiftfox for Athlon XP thinking it would be the 32 bit version, when I go to 'about swiftfox' it says 'Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.8.0.4) Gecko/20060601 Firefox/1.5.0.4' so I am not sure if it is the 64 bit version?

If it is the 32 bit version how can I alter the launcher so it loads instead of the 64 bit firefox please?

Also I deleted the Realplayer plugins in the Firefox folder and I have lost them, if I could uninstall and re-install realplayer that would replace them but I cannot uninstall realplayer as I mentioned yesterday...

---

### Post by JoWilly on 2006-06-04
[QUOTE=sweeper]I downloaded swiftfox for Athlon XP thinking it would be the 32 bit version, when I go to 'about swiftfox' it says 'Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.8.0.4) Gecko/20060601 Firefox/1.5.0.4' so I am not sure if it is the 64 bit version?

If it is the 32 bit version how can I alter the launcher so it loads instead of the 64 bit firefox please?

Also I deleted the Realplayer plugins in the Firefox folder and I have lost them, if I could uninstall and re-install realplayer that would replace them but I cannot uninstall realplayer as I mentioned yesterday...[/QUOTE]

Yes, swiftfox is 32bit. You can check this with "file swiftfox-bin".

To edit the launchers, right click on them (or for the menu, right click on applications to edit it) and for the command, replace firefox with swiftfox. 

(or you could also create a new launcher for swift fox).

You don't need to uninstall reaplayer, just launch the installer again, it will overwrite everything.

---

### Post by sweeper on 2006-06-04
[QUOTE=JoWilly]Yes, swiftfox is 32bit. You can check this with "file swiftfox-bin".

To edit the launchers, right click on them (or for the menu, right click on applications to edit it) and for the command, replace firefox with swiftfox. 

(or you could also create a new launcher for swift fox).

You don't need to uninstall reaplayer, just launch the installer again, it will overwrite everything.[/QUOTE]

When I change the command I get a message saying it cant find swiftfox, but if I just change the name sometimes swiftfox launches and sometimes firefox launches, I reinstalled realplayer and got the plugins back, I also copied them from the firefox folder to the swiftfox folder, it is working but swiftfox goes very slow when I use it.

---

### Post by JoWilly on 2006-06-04
[QUOTE=sweeper]When I change the command I get a message saying it cant find swiftfox, but if I just change the name sometimes swiftfox launches and sometimes firefox launches, I reinstalled realplayer and got the plugins back, I also copied them from the firefox folder to the swiftfox folder, it is working but swiftfox goes very slow when I use it.[/QUOTE]

You need to give the lauchers the full path for them to find it.

If swiftfox is slow with relplayer you could check with firefox from getfirefox.com (it is 32, as fast as swiftfox) to see if it's any better.

---

### Post by sweeper on 2006-06-04
[QUOTE=JoWilly]You need to give the lauchers the full path for them to find it.

If swiftfox is slow with relplayer you could check with firefox from getfirefox.com (it is 32, as fast as swiftfox) to see if it's any better.[/QUOTE]

I have re-installed the 32 bit version as I was getting fed up with trying to get 32 bits apps working on the 64 bit Ubuntu, Realplayer and helixplayer both make Firefox virtually unusable still.

---

### Post by JoWilly on 2006-06-04
[QUOTE=sweeper]I have re-installed the 32 bit version as I was getting fed up with trying to get 32 bits apps working on the 64 bit Ubuntu, Realplayer and helixplayer both make Firefox virtually unusable still.[/QUOTE]

Strange... usually it works fine.

Have you tried mplayer with the mozilla-mplayer plugin ? ( you will probably need to remove the realplayer plugins for them to take on).

For this you will also need to install w32codecs...  but I guess for dapper32 we are not in the right section here ;)

You can also make your life easier with automatix, there is a section for it.

Question: how is dapper32 compared to dapper64 ? Does dapper32 feel faster to you or is it the same ?

---

### Post by sweeper on 2006-06-04
[QUOTE=JoWilly]Strange... usually it works fine.

Have you tried mplayer with the mozilla-mplayer plugin ? ( you will probably need to remove the realplayer plugins for them to take on).

For this you will also need to install w32codecs...  but I guess for dapper32 we are not in the right section here ;)

You can also make your life easier with automatix, there is a section for it.

Question: how is dapper32 compared to dapper64 ? Does dapper32 feel faster to you or is it the same ?[/QUOTE]

32 is definitely slower, not a lot but it is noticeable, I think I have the w32 codecs from using easyubuntu, I will install mplayer, and see what happens, thanks again Jo. I will probably be back in the 64 bit forum if all goes well :)

edit
Mplayer is working fine and not affecting Firefox-thanks :)
I guess it would work with the 32 bit Firefox on 64 bit Ubuntu too.

---

### Post by JoWilly on 2006-06-04
[QUOTE=sweeper]
Mplayer is working fine and not affecting Firefox-thanks :)
I guess it would work with the 32 bit Firefox on 64 bit Ubuntu too.[/QUOTE]

Yes. For this you would have to install the 32 bit mplayer in dapper64 if you want to use the w32codecs.

Well.... actually the easiest to sort all these things in dapper64 would be a 32bit browser, 32bit mplayer + w32codecs. This way you  can install the macromedia flash too :)

You would have to force the things to install but I'm 99% sure it would work. A deb package with all the needed 32 files/libs would definitely be welcome. I unfortunately don't have the time for this now.

---

### Post by sweeper on 2006-06-04
[QUOTE=JoWilly]Yes. For this you would have to install the 32 bit mplayer in dapper64 if you want to use the w32codecs.

Well.... actually the easiest to sort all these things in dapper64 would be a 32bit browser, 32bit mplayer + w32codecs. This way you  can install the macromedia flash too :)

You would have to force the things to install but I'm 99% sure it would work. A deb package with all the needed 32 files/libs would definitely be welcome. I unfortunately don't have the time for this now.[/QUOTE]

I am pretty happy using 32 bit for now, when I have more experience/knowledge I will come back to the 64 bit, this is only my third or fourth day with any Linux :)
I am totally impressed with Ubuntu :)

---

### Post by JoWilly on 2006-06-04
[QUOTE=sweeper]I am pretty happy using 32 bit for now, when I have more experience/knowledge I will come back to the 64 bit, this is only my third or fourth day with any Linux :)
I am totally impressed with Ubuntu :)[/QUOTE]

Wow, your first days ? So yes, stick with 32bit as it will be a much better experience for you.

Best wishes ;)

---

### Post by JoWilly on 2006-06-05
There is a nice wiki here, the get firefox32 with java/flash/realplayer working "easily": [https://wiki.ubuntu.com/FirefoxAMD64FlashJava]("https://wiki.ubuntu.com/FirefoxAMD64FlashJava")

---

### Post by sweeper on 2006-06-07
[QUOTE=JoWilly]There is a nice wiki here, the get firefox32 with java/flash/realplayer working "easily": [https://wiki.ubuntu.com/FirefoxAMD64FlashJava]("https://wiki.ubuntu.com/FirefoxAMD64FlashJava")[/QUOTE]


Thanks Jo, I feel tempted to go back to the 64 bit version now ;) I will remember that article for when I do go back to it.:)

---

