---
title: "Caps Lock &amp; Num Lock Don't Work in Gnome (Dapper)"
date: 2006-03-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by AngryPanda on 2006-03-30
I have a strange problem.

When in Gnome *[SIZE="1"](do as the Gnomans do?)[/SIZE]*, the Caps Lock and Num Lock keys don't work. Pressing them lights up the corresponding LED on the keyboard, but this have no effect: unshifted lowercase letters remain that way, and the keys on the number pad act as arrow keys, etc.

I've installed Xgl and Compiz, which work great, but I figured that could be the problem, however booting into regular ol' Metacity doesn't solve the problem, unfortunately. Yet if I switch to a text terminal, then both Caps and Num Lock work as expected, so I figure it must be a general Gnome thing.

Unfortunately, I'm not sure when this started occurring, as I only noticed it relatively recently. I'm not sure what I installed or screwed up to make this happen.

I've looked on what--as far as I can tell--are the relevant configuration dialogs, and poked around in gconf. Even Google has not yielded any real insight. ](*,) Anybody have any suggestions on what I can try next?

(If the worst comes to the worst, I'll just reinstall when the finished Dapper comes out, since it's more of an inconvenience than anything else, but that seems like kind of a cop-out; I'd like to fix it, if possible.)

Dan

---

### Post by Enfenion on 2006-04-13
I sort of have the same problem... Came with compiz and xgl I suppose... My num lock works fine when I boot, but if i restart the session (by pressing Ctrl+Alt+Del or logging on and off) the num lock might switch, but the light doesn't.

This leaves me with a strange scene where num lock is on when the light is of and off when the light is on. I haven't tried with Caps Lock (because I never use this button), but it might be the same sort of problem as yours.

---

### Post by dbd on 2006-04-22
I have a very simmilar problem. Caps lock works find for me, but num lock doesn't.
Num lock works fine when in the console, or in kdm, but when actually in KDE the light goes on and off, but the number pad stays in number mode.

It must be caused by something in my home directory, since I recently reinstalled (formatting / and /user but not /home) and the problem remained (although I didn't test it straight away, so it could have been caused by something I installed). Also it is not the keyboard, since I have the same problem on two different keyboards.

Oh, and BTW, this is a 64bit machine, but with a regular 32 bit install (so shouldn't really be in this forum, but no point starting my own thread somewhere more appropriate).

---

### Post by Belathor on 2006-05-09
I have the same problem. And I think that it came with XGL as well. Both my Caps and Numlock don't work properly. (I find that the caps lock key becomes a shift key). Any luck trying to fix it?

---

### Post by dbd on 2006-05-09
Nope, afraid I havn't had any luck.

I'm just gonna format /home when I install the official release of breezy. Then test it after every major install of new software to find out what caused it.

---

### Post by NiceGuy on 2006-05-16
Hey All! I've just discovered that I've got the same problem as you lot. My CapsLock works as a shift key and the NumLock doesn't work (also the . on my numberpad will only work as a delete unless I press the shift key!?).

However a bit of searching on these fine forums has yeilded an answer:

[http://www.ubuntuforums.org/showthread.php?t=172612]("http://www.ubuntuforums.org/showthread.php?t=172612")

It seems that XGL/Compiz are to blame (in my case anyway)

To fix the problem I did the following:

1. ```
sudo gedit /etc/gdm/gdm.conf-custom
```
2. Scroll down the file and then comment out as shown (or remove if you prefer) the -kb bit (highlighted)
```
[servers]
0=Xgl

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -br -accel xv:fbo -accel glx:pbuffer [COLOR="Red"]#-kb[/COLOR]
flexible=true
```
3. Save and reboot
4. Go to System > Preferences > Keyboard. Then go to the Layouts tab and select the correct keyboard model and layout.
5. Open up gedit (or whatever) and check that everything is working properly!

---

### Post by Scunizi on 2006-05-16
I couldn't use the /, *, - or + keys on my numeric keypad all of a sudden.  I got them to work by changing the type of keyboard to Microsoft Natural.

---

### Post by delfick on 2006-05-30
[QUOTE=NiceGuy]

4. Go to System > Preferences > Keyboard. Then go to the Layouts tab and select the correct keyboard model and layout.

[/QUOTE]

I have no layouts or models there :'( (using Dapper)

how do i get them?

---

### Post by NiceGuy on 2006-05-30
[QUOTE=delfick]I have no layouts or models there :'( (using Dapper)

how do i get them?[/QUOTE]

Did you delete the -kb bit from /etc/gdm/gdm.conf-custom ?
If you did have you tried rebooting?

---

### Post by delfick on 2006-06-07
[QUOTE=NiceGuy]Did you delete the -kb bit from /etc/gdm/gdm.conf-custom ?
If you did have you tried rebooting?[/QUOTE]

I have the -kb bit and rebooting doesn't do anything

my gdm.conf-custom looks like this

> [daemon]

[security]
AllowRoot=true

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]
0=Xgl

[server-Xgl]
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -br -accel xv:fbo -accel glx: pbuffer -kb
flexible=true


(there wasn't a space between the glx: pbuffer bit before, but the : and the p were making a smily face :p)

so what can i do to fix my problem?

thnx

---

### Post by NiceGuy on 2006-06-07
If that is what your gdm.conf-custom looks like then you need to do what I suggested in [my previous post]("http://ubuntuforums.org/showthread.php?p=1023226#post1023226"). Either delete the -kb part (or comment it out using a # as shown), then reboot, go to System > Preferences > Keyboard and then select an appropriate keyboard model from the Layouts tab.

Let me know how it goes :D

ps. If you don't want smilies showing up in the code of your post then make sure that it you put it inside [CODE ] tags not [QUOTE ] tags :p eg.

> :p :p :p
```
:p :p :p
```

---

### Post by delfick on 2006-06-09
(hit's head on wall repetively)

sorry about that, i missed the "delete" part of that post 

but, now my numpad works correclty and i have layout options and such :D:D:D:D:D:D:D:D

thankyou for that...

the only problem though, one that i had before hand as well, is that my super button doesn't work.

xev recognises it but i don't know where to go from there...

thnx

---

### Post by Derspankster on 2006-10-23
> **NiceGuy said:**
> Hey All! I've just discovered that I've got the same problem as you lot. My CapsLock works as a shift key and the NumLock doesn't work (also the . on my numberpad will only work as a delete unless I press the shift key!?).

However a bit of searching on these fine forums has yeilded an answer:

[http://www.ubuntuforums.org/showthread.php?t=172612]("http://www.ubuntuforums.org/showthread.php?t=172612")

It seems that XGL/Compiz are to blame (in my case anyway)

To fix the problem I did the following:

1. ```
sudo gedit /etc/gdm/gdm.conf-custom
```
2. Scroll down the file and then comment out as shown (or remove if you prefer) the -kb bit (highlighted)
```
[servers]
0=Xgl

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -br -accel xv:fbo -accel glx:pbuffer [COLOR="Red"]#-kb[/COLOR]
flexible=true
```
3. Save and reboot
4. Go to System > Preferences > Keyboard. Then go to the Layouts tab and select the correct keyboard model and layout.
5. Open up gedit (or whatever) and check that everything is working properly!

Thank you, Thank you, Thank you - this has been driving me nuts. Simple fix. Thanks again for sharing it!

---

### Post by lolwhites on 2007-02-24
My Caps Lock key doesn't work at all, doesn't even light up the led (it does when I boot in Windows though). Num Lock is fine.

I tries Nice Guy's solution, but my gdm.conf-custon file doesn't have an -kb bit to remove.

Any thoughts?

---

### Post by Tahir on 2007-03-03
I had the same problem as lolwhites and all I did was this:

sudo gedit /etc/X11/xorg.conf

go the keyboard section bit and replace the line

Option		"XkbLayout"	"uk"

with

Option		"XkbLayout"	"gb"

NOW MY CAPS LOCK KEY WORKS :)

---

### Post by lolwhites on 2007-03-04
Cheers Tahir, that worked a treat!

---

### Post by irjason on 2007-03-10
I have been fighting this problem with the numberpad for hours now. Since I installed XGL/Compiz/Beryl. I finally found this post and have fixed the numberpad probelm. 
Now that I have removed "-kb" from /etc/gdm/gdm.conf-custom as suggested I get 100% CPU and flashing window decoration when I reboot. I find that if I stop and restart Beryl Manager everything is fine until I reboot again. Anyone have any ideas?

EDIT: I just realized this is in the 64 bit for Dapper. FWIW I am running 32 bit on an Athlon 64.

---

### Post by Odysseus145 on 2007-03-21
I have a very similar problem.  With num lock turned off, the numbers work but the +, -, etc don't.  With it turned on it's the opposite.  The numbers switch to arrows and the +, -, etc work.  I opened the gdm.conf-custom file but there was no entry under [servers].  This is driving me insane.

I'm using ubuntu edgy if that helps.

---

### Post by NEL01 on 2008-01-09
Hey all,
we are using KDE and i have this Caps Lock & Num Lock problem and i have discovered if your press 
SHIFT + NUMLOCK together it enables "Mouse Keys" which seems to disable numlock and turn Caps into a shift key. 
Pressing SHIFT + NUMLOCK together again deactivates it. 

We are using Fedora 7 and KDE not sure if i am posting in right place or if you will find it usefull but it seems to be the same problem as described above. 


Another common one we get is the keyboard stops working after a user logs in. We found that the user enabled "sticky keys" by pressing shift down for around 10 seconds. Pressing it again for around 10 seconds prompts you to disable it.

hope this helps as it was driving us crazy 

Cheers

Peter

---

### Post by mlnease on 2008-04-01
> **Tahir said:**
> I had the same problem as lolwhites and all I did was this:

sudo gedit /etc/X11/xorg.conf

go the keyboard section bit and replace the line

Option		"XkbLayout"	"uk"

with

Option		"XkbLayout"	"gb"

NOW MY CAPS LOCK KEY WORKS :)

Tahir,

I owe you big-time.  The 'uk' fix worked like a charm (for numlock in my case).  Thanks!

mike

---

### Post by jptechnical on 2008-06-11
> SHIFT + NUMLOCK together it enables "Mouse Keys" which seems to disable numlock

Oh my god... that was it... thank you sooooooo much.

---

### Post by clw3388 on 2008-07-12
SHIFT + NUMLOCK fixed my issue too. I did check the *-custom file and xorg.conf as well and neither of em helped.. Nice!!!

---

