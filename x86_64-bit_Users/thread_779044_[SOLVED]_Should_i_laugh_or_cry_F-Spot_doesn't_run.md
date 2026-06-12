---
title: "[SOLVED] Should i laugh or cry? F-Spot doesn't run"
date: 2008-05-02
forum: x86 64-bit Users
---

### Post by rajeev1204 on 2008-05-02
hi folks

So iam using the latest ubuntu 8.04 LTS.64 bit.


What is the use of advertising it as the best ubuntu ever when a certain application doesnt even run?


I have this issue with F spot.Never runs/opens.

Shouldnt they check that every application included by default atleast opens once ?!

Atleast firefox beta runs fine .

THis thing doesnt even open.

I really dont know what more to say about this.(I and many others have filed a bug)

Bug status says medium.Hmm ya right, who uses photo management software these days.
:confused:

---

### Post by TenPlus1 on 2008-05-02
I never did like F-spot, I'd much rather have gThumb installed instead :)

---

### Post by gsiliceo on 2008-05-02
Do you have a fresh installation? and, did you check your cd for defects using the built-in option?
And if you run f-spot from terminal what output does it give you?¡

---

### Post by SuperSon!c on 2008-05-02
> **rajeev1204 said:**
> hi folks

So iam using the latest ubuntu 8.04 LTS.64 bit.


What is the use of advertising it as the best ubuntu ever when a certain application doesnt even run?


I have this issue with F spot.Never runs/opens.

Shouldnt they check that every application included by default atleast opens once ?!

Atleast firefox beta runs fine .

THis thing doesnt even open.

I really dont know what more to say about this.(I and many others have filed a bug)

Bug status says medium.Hmm ya right, who uses photo management software these days.
:confused:

f spot works fine here.

---

### Post by rajeev1204 on 2008-05-02
> **gsiliceo said:**
> Do you have a fresh installation? and, did you check your cd for defects using the built-in option?
And if you run f-spot from terminal what output does it give you?¡



rajeev@rajeev-desktop:~$ f-spot
Stacktrace:

Segmentation fault
rajeev@rajeev-desktop:~$ 

thats it.

---

### Post by Kevbert on 2008-05-02
Probably the best thing to do is to re-install it via Synaptic Package Manager.
I'm using Hardy 64 bit and it seems to work fine.
What's the bug report number ?

---

### Post by rajeev1204 on 2008-05-02
> **Kevbert said:**
> Probably the best thing to do is to re-install it via Synaptic Package Manager.
I'm using Hardy 64 bit and it seems to work fine.
What's the bug report number ?

bug no 202771

I have tried reinstalling etc.I did a dist upgrade and also fresh hardy install.

No luck.

---

### Post by conehead77 on 2008-05-02
Hm, i installed 65bit 8.04 last week and just tried to run f-spot:
```

F-Spot encountered a Fatal Error
F-Spot cannot find the Dbus session bus. Make sure dbus is configured properly or start a new session for f-spot using "dbus-launch f-spot"

Details:
Platform Information: Linux 2.6.24-16-generic x86_64 unknown GNU/Linux

Distribution Information:

[/etc/debian_version]
lenny/sid

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"

```

When running "dbus-launch f-spot" in terminal it all works fine...

---

### Post by enchantedsky on 2008-05-02
I have a similar problem with F-Spot, except it does run when you click on it, or run it from the Terminal. The problem is when you put in an SD card/Flash drive filled with pictures in your computer, it asks you if you want to run F-Spot with your pictures on the disk. When you click on it, it does nothing, never executing F-Spot

---

### Post by Elim_Garak on 2008-05-08
> **gsiliceo said:**
> Do you have a fresh installation? and, did you check your cd for defects using the built-in option?
And if you run f-spot from terminal what output does it give you?¡

I've had a similar error.  I uninstalled F-Spot and then reinstalled it through aptitude.  When running in terminal, this is what I get:

> Stacktrace:

  at FSpot.Global..cctor () <0xffffffff>
  at FSpot.Global..cctor () <0x0000d>
  at (wrapper runtime-invoke) FSpot.Defines.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>
  at FSpot.Driver.Main (string[]) <0xffffffff>
  at FSpot.Driver.Main (string[]) <0x00144>
  at (wrapper runtime-invoke) FSpot.Driver.runtime_invoke_int_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	f-spot [0x51bb67]
	f-spot [0x43dacd]
	/lib/libpthread.so.0 [0x7f2d7f07b7d0]
	/lib/libc.so.6(memcpy+0x60) [0x7f2d7eb06d50]
	f-spot(mono_breakpoint_clean_code+0x1b) [0x42725b]
	f-spot [0x43f78d]
	f-spot [0x44005e]
	[0x41cc915b]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0x7f2d7fd5e7a0 (LWP 6221)]
[New Thread 0x41ed9950 (LWP 6223)]
[New Thread 0x4025f950 (LWP 6222)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0x00007f2d7eb5ada2 in select () from /lib/libc.so.6
  3 Thread 0x4025f950 (LWP 6222)  0x00007f2d7f07ae81 in nanosleep ()
   from /lib/libpthread.so.0
  2 Thread 0x41ed9950 (LWP 6223)  0x00007f2d7f077b99 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  1 Thread 0x7f2d7fd5e7a0 (LWP 6221)  0x00007f2d7eb5ada2 in select ()
   from /lib/libc.so.6

Thread 3 (Thread 0x4025f950 (LWP 6222)):
#0  0x00007f2d7f07ae81 in nanosleep () from /lib/libpthread.so.0
#1  0x00000000004b8f4f in ?? ()
#2  0x00007f2d7f0733f7 in start_thread () from /lib/libpthread.so.0
#3  0x00007f2d7eb61b2d in clone () from /lib/libc.so.6
#4  0x0000000000000000 in ?? ()

Thread 2 (Thread 0x41ed9950 (LWP 6223)):
#0  0x00007f2d7f077b99 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000004bb585 in ?? ()
#2  0x00000000004bdb37 in ?? ()
#3  0x00000000004cbc03 in ?? ()
#4  0x000000000046b3c1 in ?? ()
#5  0x00000000004855c3 in ?? ()
#6  0x00000000004cb287 in ?? ()
#7  0x00000000004e07d2 in ?? ()
#8  0x00007f2d7f0733f7 in start_thread () from /lib/libpthread.so.0
#9  0x00007f2d7eb61b2d in clone () from /lib/libc.so.6
#10 0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7f2d7fd5e7a0 (LWP 6221)):
#0  0x00007f2d7eb5ada2 in select () from /lib/libc.so.6
#1  0x00007f2d7f4f79bc in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#2  0x00007f2d7f4f7d98 in g_spawn_command_line_sync ()
   from /usr/lib/libglib-2.0.so.0
#3  0x000000000051bbf9 in ?? ()
#4  0x000000000043dacd in ?? ()
#5  <signal handler called>
#6  0x00007f2d7eb06d50 in memcpy () from /lib/libc.so.6
#7  0x000000000042725b in mono_breakpoint_clean_code ()
#8  0x000000000043f78d in ?? ()
#9  0x000000000044005e in ?? ()
#10 0x0000000041cc915b in ?? ()
#11 0x0000000000000000 in ?? ()
#0  0x00007f2d7eb5ada2 in select () from /lib/libc.so.6


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted



I, too, am in Heron with 64 bit.  Beyond this little quibble (which isn't much more than a quibble, really), Heron is fantastic!

---

### Post by mdr on 2008-05-08
this may seem daft but I recently installed gutsy on my wife's laptop and also installed digikam.

f-spot would not start in gnome and had a seg fault in terminal.  uninstalled digikam and all worked.

---

### Post by izak on 2008-05-08
Exact same setup and output as Elim_Garak.

---

### Post by stephenb on 2008-05-09
Yeap, I'm getting the same output as well. What a pain. 

This is yet another disappointment after my Hardy upgrade. I also get chaotic folder background patterns and in WINE I get a segmentation fault with everything.

All was fine in Feisty, but now I'm left asking, what else doesn't work?

---

### Post by Taboo Mirage on 2008-05-09
I really do suggest the people having trouble check out gThumb in the repositories.  F-Spot downloads an absolute ton of dependencies due to being written in C#; gThumb offers almost identical features as is much lighter.

---

### Post by Elim_Garak on 2008-05-09
> **izak said:**
> Exact same setup and output as Elim_Garak.

[FONT="Courier New"]Well, at least I'm not imagining things.  I submitted a bug report.  I'm not terribly concerned.  I can do without it, but it is nice to have the software working properly.

It's so nice to not be using Windows.  A buddy uses it, and every time he buys a camera, an MP3 player, or any such device, I end up getting called to remove all the extraneous and intrusive software these devices install on his system.  Windows users seem trained to actually believe they need all this extra bloat to use a simple MP3 player or camera, or even a USB drive.  Ridiculous.[/FONT]

---

### Post by stephenb on 2008-05-09
Yes, I already have gThumb and other programs I can use. So, not having F-Spot is not a big problem. 

But it is annoying to do an upgrade and suddenly lose functionality in a range of programs. It's not just F-Spot for me. As I mentioned before, since upgrading I've lost WINE completely. Some of my plugins in Firefox no longer work and I have display problems with folder backgrounds. 

The issue for me is not the ability to switch to other programs. The issue is why should I have to this far along with Ubuntu? The issue is that I got downgraded in some software (to the point of totally unusable) after an upgrade.   

And speaking of Windows, the people on gEdit have gone down the Microsoft track and put in a silly "hand" at the edge of blocks of text you highlight and drag and drop. Before there was a cursor line, so you knew where you were putting the block of text. Now I can't judge it because of this stupid fat hand in the way, and I end up dropping text in the middle of words. Again, here is a downgrade, not an upgrade. 

This kind of thing is what I call tinkering without thinking, and maybe that has been happening with some of the other programs.

---

### Post by izak on 2008-05-12
The nice thing about fspot is the way it sorts your photos for you. I really hope they patch this soon.

---

### Post by philinux on 2008-05-12
Weird - running fine here. Must be hardware related eh?

Is the app installed as standard by the live installer? I cant remember.
Not got digicam installed or gthumb

---

### Post by PostWax on 2008-05-12
Works just fine here.  Dual Core...Fresh install.  All is great!:lolflag:

---

### Post by linuxaz on 2008-05-12
Hello,
If you check launchpad, there are currently some issues with the 64 bit version of f-spot.  It seems to be MONO related.

linuxaz

---

### Post by rajeev1204 on 2008-05-17
ok todays updates fixed it . cool. :)

---

### Post by stephenb on 2008-05-17
Yeah, that's under pre-released updates, in case anyone doesn't check for those and so isn't getting the update. 

Haven't tested it except to see that it does indeed run.

Now, if only I could get a WINE update to fix that segmentation fault bug, then the bulk of my upgrade issues would be solved!

---

### Post by bford16 on 2008-05-18
I solved this problem by removing the f-spot database: ~/.gnome2/f-spot/photos.db.  I think (speculation) that f-spot failed to load because the program expects to find pictures at ~/Photos, but Gnome 2.22 does not have this folder.  It is called, "Pictures" now.

---

### Post by Elim_Garak on 2008-05-21
> **stephenb said:**
> Yeah, that's under pre-released updates, in case anyone doesn't check for those and so isn't getting the update. 

Haven't tested it except to see that it does indeed run.

Same deal here.  I tracked down the pre-released update.  As an aside, the .deb package was causing me grief, but I eventually got it to work.  How?  I have no idea.  It screwed up a couple times, I downloaded it again, and then all is fine.  As for F-Spot, it now opens, but, like you, I haven't done any testing with it.

For those who do not know where to find this pre-released update, you can go to [http://archive.ubuntu.com/ubuntu/pool/main/f/f-spot/]("http://archive.ubuntu.com/ubuntu/pool/main/f/f-spot/") to find it.

Thanks for the tip on the pre-released version!  It was rather helpful.

---

### Post by stephenb on 2008-05-21
No problem, but I should have been clearer. There's no need to track down the pre-release updates. Synaptic can do it for you. 

Just go to 

System > Administration > Synaptic > Settings > Repositories > Updates 

Then, tick the third box down where it says "Pre-released updates (hardy-proposed)"
Next, hit the reload button and when that's done close Synaptic. 

Finally, go to 

System > Administration > Update Manager

You'll see the proposed updates listed. Right click anywhere on the list so you have the option to uncheck all. Then just check the update you want and install. It saves any grief with .deb files.

Thanks for the thanks!

---

### Post by CalderCoalson on 2008-06-27
Removing ~/.gnome2/f-spot immediately fixed it for me too, thanks!

---

