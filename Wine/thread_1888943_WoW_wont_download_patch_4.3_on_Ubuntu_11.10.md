---
title: "WoW wont download patch 4.3 on Ubuntu 11.10"
date: 2011-11-30
forum: Wine
---

### Post by Phaze08 on 2011-11-30
Ok, so my game used to work perfectly fine in all aspects (After many hours of tweaking settings) and it actually ran better and faster than in windows and didnt cause my system to overheat sometimes. I havent played in a while, but I will start in a week or so and I decided to get the patch out of the way. Problem is, when I do, it seems to be working right, then after a couple minutes, it says something about a critical error that has not been seen in windows and there is no solution available. So I click ok and the window seems to be working still, but when I check connection status, it shows upload and download to be 0kbps so its not working lol. It does this no matter how many times I try it and like I said it used to work. Not sure what happened, the only thing that has changed is its a newer version of Ubuntu. I'm using Gnome Shell if thats important. Im not sure how to fix this so any advice anyone has would be great, thanks. :D

---

### Post by cwwilson721 on 2011-11-30
The issue is the Blizz Downloader that doesn't play well in wine.

If you are able to, get to the "Downloader" preferences, and uncheck peer-to-peer. (Some have reported that works)

Also, try to set your computer to be the DMZ on router (WoW kept saying I was behind a firewall, even tho all ports were correctly forwarded)

If you can't get to preferences while running WoW in wine (like me), try a VM with Windows (I already have that, just in case), or a dual-boot into Windows.

It sucks, I know, but sometimes WoW needs Windows.

---

### Post by Phaze08 on 2011-11-30
If I was to use windows, I have dual boot, how would I get the patch to my ubuntu wow install? I have it on both because I used to use windows and keep a small install just in case I need it. Obviously its a good thing to do lol.

---

### Post by StephanVolkmann on 2011-11-30
> **Phaze08 said:**
> If I was to use windows, I have dual boot, how would I get the patch to my ubuntu wow install? I have it on both because I used to use windows and keep a small install just in case I need it. Obviously its a good thing to do lol.

you can rsync folders.....

---

### Post by Phaze08 on 2011-11-30
Where does the patch download to? Ill just pull that folder to ubuntu.

---

### Post by cwwilson721 on 2011-11-30
I just copy the entire WoW folder over to my Linux install.

Ubuntu will see the Windows partition, and you just open it up and copy it over.

Just make sure that wine launches WoW with the '-opengl' switch. It will modify the config.wtf file itself after that

---

### Post by Phaze08 on 2011-11-30
Thats what i did for my addons lol. Thanks ill probably just do  that.:D

And yeah, i use open gl, the fps is so much better than windows.

---

### Post by rob2nd9th on 2011-11-30
I'm full Ubuntu, (10.04)

I keep getting a freeze on the patch install.

Any pointers would be help full..


Wine  1.3.33

---

### Post by cwwilson721 on 2011-11-30
Only 'pointers' I've got is what I've already put up there.

---

### Post by johansson on 2011-12-01
Was having same issue, with ubuntu 11.10.  Download would start and then die right around a 1.5 megs.  Used cwwilson721's suggestion to uncheck peer to peer, worked fine.  Thanks ccwilson.

---

### Post by rob2nd9th on 2011-12-01
> **cwwilson721 said:**
> Only 'pointers' I've got is what I've already put up there.

Yep, done all that, but still having prob's so thought may be it was a version issue..


And still no joy?

---

### Post by cwwilson721 on 2011-12-01
Only other thing I can suggest is to make sure ALL the ports needed by WoW for playing and d/l are forwarded to your machine from your router (if you use one).

Search Google for correct port numbers for WoW.

Otherwise, [COLOR="Red"]AND THIS CAN BE DRASTIC[/COLOR], is copy your actual WoW folder out of '.wine', and delete that folder (".wine"), then run 'winecfg', and copy WoW back in. That will 'reset' your base install, and just copying WoW back to Program Files doesn't do anything to the 'environment'. Then, try again.

---

### Post by rob2nd9th on 2011-12-02
> **cwwilson721 said:**
> Otherwise, [COLOR="Red"]AND THIS CAN BE DRASTIC[/COLOR], is copy your actual WoW folder out of '.wine', and delete that folder (".wine"), then run 'winecfg', and copy WoW back in. That will 'reset' your base install, and just copying WoW back to Program Files doesn't do anything to the 'environment'. Then, try again.

Might try that over the weekend if all else fails.

---

### Post by ravenstar on 2011-12-03
Easy guys. Problem solution found. Just do follows:
1. open Launcher first time? you see error, bla bla click ok,
Launcher dont download but work, go in Prefences and off piring download.
2. Kill process Launcher and start again, all ok now wow 4.3 update downloading...

PS: tested on ubuntu 10.10, wine 1.3.5

PSS: sorry for my english 364

---

### Post by cwwilson721 on 2011-12-03
> **ravenstar said:**
> Easy guys. Problem solution found. Just do follows:
1. open Launcher first time? you see error, bla bla click ok,
Launcher dont download but work, go in Prefences and off piring download.
2. Kill process Launcher and start again, all ok now wow 4.3 update downloading...

PS: tested on ubuntu 10.10, wine 1.3.5

PSS: sorry for my english 364

I already posted this "solution"

But some of us (me included) cannot get to Preferences. But mine downloaded anyway. For me, it was already off (peer-to-peer)

---

### Post by rob2nd9th on 2011-12-04
> **cwwilson721 said:**
> Otherwise, [COLOR="Red"]AND THIS CAN BE DRASTIC[/COLOR], is copy your actual WoW folder out of '.wine', and delete that folder (".wine"), then run 'winecfg', and copy WoW back in. That will 'reset' your base install, and just copying WoW back to Program Files doesn't do anything to the 'environment'. Then, try again.

K did this then ran the launcher via the terminal :D

All up and running (sound keeps going off but can sort that)

Thanks for all the info..

---

### Post by cwwilson721 on 2011-12-04
As an aside:

What I do, to keep "WoW" separate from wine, is install it to it's own folder, and then create a link to it in the wine folder.

Example: WoW is ACTUALLY installed in /home/<USER>/WoW, and there is a link to that folder in /home/<USER>/.wine/drive_c/Program Files (Note: This is NOT how my system is REALLY setup, but gives you an example that works)

This way, I can delete the wine folder, run winecfg, and relink the folder. Takes 2 min, and done.

Another advantage to having WoW in it's own separate folder is that other users on this box can access it, too, if folder permissions are set correctly.

Do a Google search on "multi user access folder permissions linux" to get an idea how to do this.

---

### Post by Luc André on 2011-12-04
> **johansson said:**
> Was having same issue, with ubuntu 11.10.  Download would start and then die right around a 1.5 megs.  Used cwwilson721's suggestion to uncheck peer to peer, worked fine.  Thanks ccwilson.

Ditto for me. Worked.

---

### Post by zm0k4 on 2011-12-05
> **Luc André said:**
> Ditto for me. Worked.

 Me too on Gentoo.

---

### Post by Jestette on 2011-12-30
Alright, i've unchecked peer-to-peer and tried deleting the .wine folder as well. Now it's saying I have firewall, and my patch download speed jumps around from 1.5-1.2
Any suggestions before I look into this whole router business? I'm new to Ubuntu and it's ways, excuse my newbieness.

P.S. I cannot dual-boot with Windows, since Windows crashed my computer due to a registry error.

---

