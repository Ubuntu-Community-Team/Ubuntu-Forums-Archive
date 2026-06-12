---
title: "Avant Window Navigator for x64"
date: 2007-02-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hexydes on 2007-02-05
Hey all,

I'm uploading this because I couldn't find a .deb file anywhere for x64, and for some reason the instructions for Ubuntu that were on Digg didn't work for me. Also, there was a .deb file included in that thread, but it was for 32-bit and of course didn't work, so I made my own .deb file. Hopefully it works for others (if it doesn't you're probably SOL because I don't have the slightest clue what I'm doing, seriously).

All I did was extract the source files, build them with ./configure, and then used "checkinstall" to make a binary (which failed, but for some reason still make the binary). Then the binary worked and I'm using the dock as we speak. Hopefully you all get lucky and it works for you as well. :)

---

### Post by cmost on 2007-02-05
Hey, thanks for thinking of the rest of us!  We appreciate it.  I'll try this when I get home tonight.  :-)

---

### Post by Hexydes on 2007-02-05
Yeah, I know what a PitA it is, and sadly enough, there are people out there that know even less than me (how is this even possible?!). :)

Hopefully that will help someone(s) out. The dock actually is pretty cool looking, although I can't really figure out how to make it work as an application launcher (it basically acts as an always-present application switcher).

---

### Post by cmost on 2007-02-06
Right now, it's only a window switcher.  They're apparently adding features such as app launcher.  If development on this takes off, we'll finally have a dock for Linux that rivals OS-X's dock.  My favorite dock was the Kiba-dock, but, I think development on that has hit a plateau.  Plus, you can never get anyone to give you a straight answer on how to get the thing to work properly.  Oh well.

---

### Post by flammenwurfer on 2007-02-06
I don't know if you've tried it or not, but there's a Gdesklet called StarterBar that looks and works JUST like the OSX dock.  It's super customizeable too.  I installed Avant but it seemed really buggy.  It might be good in the future but the so far I like the StarterBar a lot.

---

### Post by Hexydes on 2007-02-06
I was using one of the Gdesklet docks, but I didn't like how it looked/worked. Maybe it was a different one?

I really liked kiba-dock too, but something caused it to stop working and I couldn't get it working again so I gave up.

Avant seems good; if it becomes more feature-rich, I'd be happy to continue using it. Right now it is sort of useless, but it looks cool so I'm just gonna keep it. :)

---

### Post by flammenwurfer on 2007-02-06
Cool.  Avant does look pretty sweet, but it's not working well enough right now for me to use it.  I'll stick with StarterBar cuz it also looks good and does everything I want it to do.  I never heard of kiba-dock, is it a stand-alone app? or a desklet?

---

### Post by Hexydes on 2007-02-06
> **flammenwurfer said:**
> Cool.  Avant does look pretty sweet, but it's not working well enough right now for me to use it.  I'll stick with StarterBar cuz it also looks good and does everything I want it to do.  I never heard of kiba-dock, is it a stand-alone app? or a desklet?
Yeah, it is a stand-alone app. It is the one you see in all the demos where the icons bounce around on the screen. Except mine. When mine bounce, the app crashes. :(

---

### Post by Tommaso on 2007-02-10
Here it is a deb package from the lastest SVN...it fix many bugs...

Regards

---

### Post by cmost on 2007-02-10
Thanks man!

---

### Post by Tommaso on 2007-02-16
Here an update to 16/02/2007 realese....

---

### Post by Einaudi on 2007-02-17
> **Tommaso said:**
> Here an update to 16/02/2007 realese....

thank you guy :) 
keep working

---

### Post by Tommaso on 2007-03-06
Here an other  update from the last revision 143...

Regards, Tommaso

---

### Post by Tommaso on 2007-03-07
Update from the 156 revision...

Ciao ciao ):P

---

### Post by ffxr on 2007-03-07
thanks.. fella..

does anyone use this on xfce? its fairly light on gnome libraries.. so i like to use it.., (definately the most straight forward dock i can find, tho m open to suggestions..) but i have a problem adding program launchers to it.. is this cos of the gnome dependency or is just cos i am missin something?

---

### Post by unebaguettesvp on 2007-03-09
Thanks Tommaso!!!

We REALLY appreciate it!

---

### Post by Tommaso on 2007-03-09
An update from 158 revision...:guitar:

---

### Post by Didjit on 2007-03-10
Confused how this works. I keep getting the laucher in a black bar about and inch long accross my screen. doesn't look anything like the screen shots I have seen. Is there a setting I may be missing?

Didjit

---

### Post by Tommaso on 2007-03-10
> **Didjit said:**
> Confused how this works. I keep getting the laucher in a black bar about and inch long accross my screen. doesn't look anything like the screen shots I have seen. Is there a setting I may be missing?

Didjit

Hi,
You have to enable the composite manager like Beryl or compiz.....you can find a wiki here:

[http://www.beryl-project.org/](http://www.beryl-project.org/)

or if you run an Ubuntu/Feisty you can enable the "desktop effects" in System>Preferences>Desktop Effects.

Regards, Tommaso

---

### Post by Didjit on 2007-03-10
Ah! I thought it was something outside of Beryl.  Ok, thanks.

Didjit

---

### Post by Tommaso on 2007-03-14
update to realese 160. ;-)

---

### Post by Tommaso on 2007-03-20
Realese 161...now with beryl thumbnails support!!

---

### Post by KKTrigger on 2007-03-21
> **Tommaso said:**
> Realese 161...now with beryl thumbnails support!!

Thanks!!! Troppo comodo, grazie! :popcorn:

---

### Post by Tommaso on 2007-03-21
> **KKTrigger said:**
> Thanks!!! Troppo comodo, grazie! :popcorn:

Prego!!!:guitar: 

Realese 166...

---

### Post by Einaudi on 2007-03-21
is there a changelog somewhere? it's difficult to see what change between releases :)

now if only he used a "zoom effect" (as seen in macosx) instead than the "jump effect" it'll be great.

PS
vai Tommy :)

---

### Post by Tommaso on 2007-03-22
Realese 169....

> **Einaudi said:**
> is there a changelog somewhere? it's difficult to see what change between releases :)


No problem...

> **Einaudi said:**
> 
now if only he used a "zoom effect" (as seen in macosx) instead than the "jump effect" it'll be great.


Unfortunately I can't see it in te TODO but it would be great!

---

### Post by reacocard on 2007-03-22
Hexydes, Tommaso, I maintain an [Ubuntu repository for AWN]("http://syzygy42.tuxfamily.org/dists/edgy/avant-window-navigator/"), but I only have 32-bit packages because I don't have a 64-bit computer to build on. If you like, I can host your packages in my repo, so that 64-bit users can also enjoy this.

---

### Post by Trevice on 2007-03-22
yes please!!!!!!!!!!!!!

I love awn and it would be great if we could have a repository

---

### Post by nicoladimaria on 2007-03-23
it works only with sudo and I can't understand why
disinstalled because it's too buggy yet

---

### Post by ffxr on 2007-03-23
those looking for a todo list and want to offer suggestions have a read on the authors blog: [http://njpatel.blogspot.com/](http://njpatel.blogspot.com/) you shoud find a link from there, its a good read anyway..

---

### Post by Tommaso on 2007-03-23
> **reacocard said:**
> Hexydes, Tommaso, I maintain an [Ubuntu repository for AWN]("http://syzygy42.tuxfamily.org/dists/edgy/avant-window-navigator/"), but I only have 32-bit packages because I don't have a 64-bit computer to build on. If you like, I can host your packages in my repo, so that 64-bit users can also enjoy this.

No problem for this...

---

### Post by reacocard on 2007-03-23
> **Tommaso said:**
> No problem for this...

Ok, great, I'll add them. They'll be up sometime this weekend.

---

### Post by fraCPH on 2007-04-11
Have you added it?
I still cannot find an amd64 directory in your repo.

---

### Post by reacocard on 2007-04-11
> **fraCPH said:**
> Have you added it?
I still cannot find an amd64 directory in your repo.

No, I haven't. I can't figure out how to get falcon to do amd64 for just one section of the repo. :(

---

### Post by quadrispro on 2007-04-30
@fraCPH:

Thank you for the deb, I hope you'll post here newer updates of AWN for amd64 ;)

---

### Post by cadraig on 2007-06-02
Heres one I downloaded tonight, Release 1.186 ;)

---

### Post by Alex&amp;Linux on 2007-06-10
Por eso, muchimas gracias!

---

### Post by s_spiff on 2007-08-11
rocking. Thanks for this. I came across this on the web and was hoping the forums would have a .deb for this. Thanks again.

---

### Post by tgm4883 on 2007-08-14
64-bit debs are now available for AWN from the AWN repo.

[http://ubuntuforums.org/showthread.php?t=385981&highlight=awn](http://ubuntuforums.org/showthread.php?t=385981&highlight=awn)

---

### Post by BobCFC on 2007-08-15
> **tgm4883 said:**
> 64-bit debs are now available for AWN from the AWN repo.

[http://ubuntuforums.org/showthread.php?t=385981&highlight=awn](http://ubuntuforums.org/showthread.php?t=385981&highlight=awn)



Thanks that thread also has a guide to installing the latest version from svn to get the new stuff.

It compiles fine on Gutsy Gibbon Tribe 4 (64bit) but when you run it from the terminal you get an error message:

> avant-window-navigator: error while loading shared libraries: libawn.so.0: cannot open shared object file: No such file or directory


This is a known bug and I found the solution on launchpad bugtracker.  Type this at the Terminal then run avant-window-navigator again:

```
sudo ldconfig
```

Works for me!

---

### Post by quadrispro on 2007-08-18
it's possible to get the last version of the app by **[uPure64 repository](http://www.janvitus.netsons.org/repository/)**

---

### Post by volksolwagen57 on 2007-08-24
So by adding this repository you can just update/upgrade and get it installed? I would prefer something that can be updated. I see that there are quite a few debs for easy install. I have tried it but it is too good to be true. It seems to install but it does not show up in the applications menu. Where and how can I install awn with all its features (including the drag and drop icon feature that I loved so much). I would rather build it with svn and have it available for update in the repository.
CAN ANYONE HELP PLEASE PLEASE PLEASE? My desktop looks stale with no cool stuff..... thanks!

---

### Post by tgm4883 on 2007-08-24
> **volksolwagen57 said:**
> So by adding this repository you can just update/upgrade and get it installed? I would prefer something that can be updated. I see that there are quite a few debs for easy install. I have tried it but it is too good to be true. It seems to install but it does not show up in the applications menu. Where and how can I install awn with all its features (including the drag and drop icon feature that I loved so much). I would rather build it with svn and have it available for update in the repository.
CAN ANYONE HELP PLEASE PLEASE PLEASE? My desktop looks stale with no cool stuff..... thanks!

Thats usually how repos work.  You can also get awn for 64-bit from the tuxfamily repo.  Search for the awn thread by reacocard

---

### Post by reacocard on 2007-08-24
> **tgm4883 said:**
> Thats usually how repos work.  You can also get awn for 64-bit from the tuxfamily repo.  Search for the awn thread by reacocard

Or have it posted for you. :)

[HOWTO: functional eye-candy with Avant-Window-Navigator and Affinity]("http://ubuntuforums.org/showthread.php?t=385981")

---

### Post by tgm4883 on 2007-08-24
> **reacocard said:**
> Or have it posted for you. :)

[HOWTO: functional eye-candy with Avant-Window-Navigator and Affinity]("http://ubuntuforums.org/showthread.php?t=385981")

awe, reacocard, I wan't going to give him everything on a silver platter :)

---

### Post by volksolwagen57 on 2007-08-27
silver platters make everything taste better.:)
on aside, does one absolutely have to run compiz/beryl to run AWN? i hope not...

---

### Post by Dark Star on 2007-08-27
Thanks for the .deb file. Will save my frds time :D

---

### Post by reacocard on 2007-08-27
> **volksolwagen57 said:**
> silver platters make everything taste better.:)
on aside, does one absolutely have to run compiz/beryl to run AWN? i hope not...

Well in theory any compositor should work, but AWN currently has a couple bugs when run under other compositors so pretty much, yeah they're needed. You could try running it under xfwm4 or xcompmgr, just keep in mind it will likely have more problems.

---

