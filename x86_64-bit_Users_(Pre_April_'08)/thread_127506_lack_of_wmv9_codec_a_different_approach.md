---
title: "lack of wmv9 codec: a different approach"
date: 2006-02-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Josef K. on 2006-02-09
I wonder if wine\cedega could be the **easy** answer for the lack of wmv9 codec in breezy 64 (since it hides a 32bit windows system)
I know I can spend next year learn how to use chroot :rolleyes: but last time I tried it I completely messed up my system :( ... and I guess wine could be an easyer solution
wine use an old version of wmplayer, but, don't know why, it fails to initialize audio system and (worst thing) it can't automatically update codecs
so I've downloaded a windows codecs pack (last k-lite codecpack) and tried to install it
unfortunately I got this (recursive) error message
> internal error: failed to expand "group" constant

any idea how to solve it?

---

### Post by jon_gunnar on 2006-02-09
[QUOTE=Josef K.]I wonder if wine\cedega could be the **easy** answer for the lack of wmv9 codec in breezy 64 (since it hides a 32bit windows system)
I know I can spend next year learn how to use chroot :rolleyes: but last time I tried it I completely messed up my system :( ... and I guess wine could be an easyer solution
wine use an old version of wmplayer, but, don't know why, it fails to initialize audio system and (worst thing) it can't automatically update codecs
so I've downloaded a windows codecs pack (last k-lite codecpack) and tried to install it
unfortunately I got this (recursive) error message

any idea how to solve it?[/QUOTE]

Not exactly answering you're question,but I did compile up vlc,an easy operations and it plays those pesky vmw9 files without any problem.
If you should be interested I used this guide for it:
[http://nanocrew.net/2005/09/01/compiling-vlc/](http://nanocrew.net/2005/09/01/compiling-vlc/)

---

### Post by Josef K. on 2006-02-09
> 
checking for BONJOUR... configure: error: Package requirements (avahi-client >= 0.6) were not met.

unfortunately that metod require avahi-client >= 0.6 which is in dapper but not in breezy (I've tried to install dapper packages but would make a mess cause conflict with almost everything in breezy :-k)

how did you manage to make it work? can you send me your deb file?

---

### Post by jon_gunnar on 2006-02-10
[QUOTE=Josef K.]unfortunately that metod require avahi-client >= 0.6 which is in dapper but not in breezy (I've tried to install dapper packages but would make a mess cause conflict with almost everything in breezy :-k)

how did you manage to make it work? can you send me your deb file?[/QUOTE]

I compiled the packages just following the guide at the address I gave [http://nanocrew.net/2005/09/01/compiling-vlc/](http://nanocrew.net/2005/09/01/compiling-vlc/) and got vlc_0.8.5-1_amd64.deb out of it.
Its an updated Brezzy system and I havent avahi installed at all as far as I can see.
I can send the deb if you want, no problem in that.

---

### Post by hunteramor on 2006-02-10
would you be able to provide me with that package too, please?  i've been having some trouble compiling VLC according to the instructions on that site.  when i'm compiling VLC at the end, I get:

> modules.c:(.text+0x43ef): undefined reference to `vlc_entry__libvc1'
modules.c:(.text+0x43fc): undefined reference to `vlc_entry__libvc1'
modules.c:(.text+0x4409): undefined reference to `vlc_entry__libvc1'
collect2: ld returned 1 exit status
make[2]: *** [vlc] Error 1
make[2]: Leaving directory `/home/hunter/videolan/vlc-trunk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/hunter/videolan/vlc-trunk'
make: *** [all] Error 2

and then it won't install.  not sure what i'm doing wrong, but a package would make all well  ;)

---

### Post by jon_gunnar on 2006-02-10
[QUOTE=hunteramor]would you be able to provide me with that package too, please?  i've been having some trouble compiling VLC according to the instructions on that site.  when i'm compiling VLC at the end, I get:



and then it won't install.  not sure what i'm doing wrong, but a package would make all well  ;)[/QUOTE]
No problem.But its around 6MB so I must find a place to store it.

---EDIT---
Glad it worked well for you.

---

### Post by Josef K. on 2006-02-10
maybe [www.filefront.com](www.filefront.com) ?

---

### Post by sbassett on 2006-02-11
Let me know, I would be happy to store that sucker. About to install ubuntu-64 tomorrow. I have plenty o space.

---

### Post by jon_gunnar on 2006-02-11
[QUOTE=sbassett]Let me know, I would be happy to store that sucker. About to install ubuntu-64 tomorrow. I have plenty o space.[/QUOTE]

I mailed it to **hunteramor** who reportet it to work flawlessly so if you want it just tell me were.

---

### Post by hunteramor on 2006-02-11
i've actually noted some funkiness when resizing (trying to fullscreen, and then go back...) but i'm not sure if that's VLC, or something else

(new system, still getting lots of kinks ironed out)

---

### Post by sbassett on 2006-02-11
[QUOTE=jon_gunnar]I mailed it to **hunteramor** who reportet it to work flawlessly so if you want it just tell me were.[/QUOTE]

[http://simon.doesntexist.com/](http://simon.doesntexist.com/)

then just select the upload button, and go from there (in the ubuntu section).

---

### Post by Josef K. on 2006-02-11
if you have composite manager activated is _for sure_ its fault
but sometimes I experience the same problem even without cm if the file I'm playing is BIG
I don't think is VLC

BTW
would one of you 2 give me a copy of that file?! :D

---

### Post by Heretic Monkey on 2006-02-14
[QUOTE=jon_gunnar]I compiled the packages just following the guide at the address I gave [http://nanocrew.net/2005/09/01/compiling-vlc/](http://nanocrew.net/2005/09/01/compiling-vlc/) and got vlc_0.8.5-1_amd64.deb out of it.
Its an updated Brezzy system and I havent avahi installed at all as far as I can see.
I can send the deb if you want, no problem in that.[/QUOTE]
I'm trying to install VLC for the WMV9 codecs, but i keep getting hung up trying to download the VC1 Ref Decoder.  What do i put in the space for "USERNAME" and "PWD"?  Are we supposed to have another established account somewhere or what?

---

### Post by jon_gunnar on 2006-02-14
[QUOTE=Heretic Monkey]I'm trying to install VLC for the WMV9 codecs, but i keep getting hung up trying to download the VC1 Ref Decoder.  What do i put in the space for "USERNAME" and "PWD"?  Are we supposed to have another established account somewhere or what?[/QUOTE]

Looks like it is problems there.But you can get it here [http://www.multimedia.cx/VC1_reference_decoder_release6.zip]("http://www.multimedia.cx/VC1_reference_decoder_release6.zip")

---

### Post by Heretic Monkey on 2006-02-14
Ok, followed the instructions step by stem on the previous site, but my VLC still won't play WMV9's.  I've tried downloading them from various sites, but none of them have video (not sure about audio, speakers busted now).  I looked in the preferences  of VLC, and the highest WMV video decoder listed was WMV2... is something seriously wrong here or what?

---

### Post by Josef K. on 2006-02-14
to compile VLC you need last avahi version (which's not in breezy)
however I suggest to use [this file]("http://ubuntuforums.org/showthread.php?t=62685"), that create a 32bit mplayer in your system without chroot, and wait for a decent amd64 native support in ffmpeg

---

### Post by jon_gunnar on 2006-02-14
[QUOTE=Josef K.]to compile VLC you need last avahi version (which's not in breezy)
however I suggest to use [this file]("http://ubuntuforums.org/showthread.php?t=62685"), that create a 32bit mplayer in your system without chroot, and wait for a decent amd64 native support in ffmpeg[/QUOTE]
I don't understand what you mean by this **avahi**.I compiles and run vlc just fine from the instructions without any avahi installed at all.But if you insist,guess my system and others are a little weird then.

---

### Post by Josef K. on 2006-02-14
> **jon_gunnar]I don't understand what you mean by this **avahi**.I compiles and run vlc just fine from the instructions without any avahi installed at all.But if you insist,guess my system and others are a little weird then.[/QUOTE]

on the last stage of installation, after
[QUOTE]./bootstrap  said:**
> 
the make hangs up saying I need avahi client >=0.6
the avahi client on breezy is [this]("http://packages.ubuntu.com/breezy/net/libavahi-client1") which is 0.5 version and according to adept almost everything in KDE need it (removing it you remove the entire kde) that's why I didn't try to manually update from avahi.org (too scare to mess up the system :))
I've no idea why you didn't experience the same error (maybe you use gnome or dapper?)

---

### Post by jon_gunnar on 2006-02-14
[QUOTE=Josef K.]on the last stage of installation, after

the make hangs up saying I need avahi client >=0.6
the avahi client on breezy is [this]("http://packages.ubuntu.com/breezy/net/libavahi-client1") which is 0.5 version and according to adept almost everything in KDE need it (removing it you remove the entire kde) that's why I didn't try to manually update from avahi.org (too scare to mess up the system :))
I've no idea why you didn't experience the same error (maybe you use gnome or dapper?)[/QUOTE]

Yes,I use gnome,prefer KDE in fact,but its work so why take the hassle with changing.And it's a updated breezy system yes.

---

### Post by thiago_moreira on 2006-06-23
I'm getting problems to compile VLC. Here is the error (when I type the "make" or the "./compile" command):

/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
make[6]: ** [libscreen_plugin.so] Erro 1
make[6]: Saindo do diretório `/home/thiago/videolan/vlc-trunk/modules/access/screen'
make[5]: ** [all-modules] Erro 1
make[5]: Saindo do diretório `/home/thiago/videolan/vlc-trunk/modules/access/screen'
make[4]: ** [all-recursive] Erro 1
make[4]: Saindo do diretório `/home/thiago/videolan/vlc-trunk/modules/access'
make[3]: ** [all] Erro 2
make[3]: Saindo do diretório `/home/thiago/videolan/vlc-trunk/modules/access'
make[2]: ** [all-recursive] Erro 1
make[2]: Saindo do diretório `/home/thiago/videolan/vlc-trunk/modules'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diretório `/home/thiago/videolan/vlc-trunk'
make: ** [all] Erro 2

Can anybody help me with that?

---

### Post by bforbes on 2006-06-24
What does "Saindo do diretório" mean in English?

Also, I got all the 32-bit codecs working fine with the latest mplayer in a 32-bit chroot, and the chroot was *not* hard to set up at all.
[http://ubuntuforums.org/showthread.php?t=24575&highlight=32+bit+chroot](http://ubuntuforums.org/showthread.php?t=24575&highlight=32+bit+chroot)

---

### Post by thiago_moreira on 2006-06-24
Saindo do diretório = Leaving directory.

Sorry about that. But did anybody here had success compiling the VLC?
(p.s.: Sorry about my English. It's a little bit rusty :mrgreen: )

---

