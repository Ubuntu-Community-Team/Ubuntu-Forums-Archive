---
title: "To answer an oft-asked question about mounting HFS+ volumes as read-write..."
date: 2006-01-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by SectionThree on 2006-01-30
A question that has arisen on this forum often (I searched for the answer too quite a bit before investing a bit of time to figuring it out myself) is this:

"How do I mount an HFS+ volume on Ubuntu?" or "I mounted an HFS+ partition but it comes up as read-only. What do I do?"

Here's the answer: Open up the terminal and type the following:

sudo mount -w -t hfsplus /dev/hda[partition number] /media/[volume name]

;);)

Now here's the bare-bones explanation for you ppc-architecture noobs out there (whom this is mainly directed to, I consider myself a semi-noob myself...)...

You can easily find the partition number either by opening gparted or disks from the administration menu under "System".

*At this point, I must inform you KDE/Kubuntu users out there that I'm using Gnome, but the default Kubuntu installaton contains the same basic GUI utilities I mention here, you'll just have to find them differently than how I mention them here. But, if you were computer savvy enough to install ANY flavor of Linux in the first place, I have faith that you KDE folk will be able to find those things which I mention. :cool:?*

*Also, to all you noobs out there reading this, **THE COMMAND-LINE IS YOUR FRIEND!!!!**  Don't fear it, although it isn't the mouse-click interface that you're used to, if you do it wrong somehow, it will tell you why.  And now, back to the (non-italicized) message...*

I will now dissect the command I introduced earlier:

sudo mount -w -t hfsplus /dev/hda[partition number] /media/[volume name]

**sudo**  You need *sudo* because you cannot mount volumes without superuser (root) privledges. After you use *sudo* before a command, you wil be asked for your password. This is your administrator login password.

**-w -t hfsplus**  *-w* and *-t* are options for the *mount *command. *-w* stands for "write" and *-t* stands for "type." It's necessary to do it in this order because after *-t*, you will type in the filesystem, in this case, *hfsplus.* Don't type in *hfs+* because it's, well, wrong.

Here's an example of what I did in my case, where I wanted to mount my **13**th partition (formatted as hfs+) called "**Data**" as read-write. I typed the following in the Terminal:

sudo mount -w -t hfsplus /dev/hda**13** /media/**Data**

Finally, you should get a warning message asking you if you really do want to mount said volume as read-write. Of course you do, so type *y* then hit **return**, and you'll be on your way!

---

### Post by slux on 2006-01-31
Hmm, does this also work when the filesystem has been marked unclean? 

Personally I've had no problem with gettings HFS+ mounted read-write with the default options except when the filesystem has not been cleanly unmounted.

The real problem comes when it needs to be checked, for some reason I've never gotten OS X to mark it clean and I used "the hpmount trick" for some time but that was fixed in Breezy so I had to go hunting for alternative solutions and ended up compiling a patched older version of the OS X disk tools for Linux.

---

### Post by SectionThree on 2006-01-31
I haven't had problems with unclean HFS+ filesystems because usually, as soon as things start to go awry, I back everything up, wipe everything out and start over again.

But, in case you don't have a large external drive you can do this with, give the mount command a whirl, and make sure you use the -w option, as it will force the problem partition to mount read-write.

If this doesn't work, try the -s option in the original mount argument, -s stands for "sloppy" and will allow a mount even if there are errors:
 
 [I]mount -s -w -t hfsplus /dev/hda** /media/****

[/I]If this doesn't work, you may want to move the problem volume to a new mount-point. You can do that with:

*mount --move olddir newdir* where olddir is the current mount point (/media/Data in my case) and newdir is where you want to move it to (usually /media/SomethingElse).

Let us know how it turns out...

---

### Post by ottojschlosser on 2006-01-31
For the benefit of other newbies, I'd like to clarify one detail: the 'volume name' you supply is a directory in /media, not the HFS volume name. I got the message '[name] does not exist' until I realized that I hadn't yet created a directory with that name in /media.

---

### Post by Brian McConnell on 2006-02-05
I tried this, still my disk mounts as read only :(

weird. any thoughts?

---

### Post by spaceballl on 2006-02-05
how do I get it to mount the partition automatically when ubuntu boots up?

-Kevin

---

### Post by SectionThree on 2006-02-07
[quote=Brian McConnell]I tried this, still my disk mounts as read only :(

weird. any thoughts?[/quote]

Try booting up into OS X (I'm assuming you have some version of Mac OS if you're using HFS+ filesystems) and *get info* on your problem volume. Open up the "Ownership and Permissions" section and give EVERYBODY (owner, group, guest) permission to do EVERYTHING (read, write, execute).  Now boot back up into Ubuntu and try mounting the offending volume again with the -w option and see how that works.

---

### Post by SectionThree on 2006-02-07
[quote=spaceballl]how do I get it to mount the partition automatically when ubuntu boots up?

-Kevin[/quote]

Try this:

Under your System/Preferences menu, open up Sessions.  Click the "Startup Programs" tab then the "Add" button.  Type in the command you use to mount your volume and click OK, and you're good to go!

---

### Post by Brian McConnell on 2006-02-08
[QUOTE=SectionThree]Try booting up into OS X (I'm assuming you have some version of Mac OS if you're using HFS+ filesystems) and *get info* on your problem volume. Open up the "Ownership and Permissions" section and give EVERYBODY (owner, group, guest) permission to do EVERYTHING (read, write, execute).  Now boot back up into Ubuntu and try mounting the offending volume again with the -w option and see how that works.[/QUOTE]
what you describe above was, indeed, the recipe for success.

---

### Post by SectionThree on 2006-02-09
[quote=Brian McConnell]what you describe above was, indeed, the recipe for success.[/quote] 
I'm glad I could help, and I appreciate your reply...  :cool:

---

### Post by SectionThree on 2006-02-09
[quote=ottojschlosser]For the benefit of other newbies, I'd like to clarify one detail: the 'volume name' you supply is a directory in /media, not the HFS volume name. I got the message '[name] does not exist' until I realized that I hadn't yet created a directory with that name in /media.[/quote] 
To clarify further, the easiest way to do this (GUI style) is to find the Media directory in your file browser (the "Finder," if you will).

If you're running Gnome, open up any folder from the desktop, and on that left-hand panel marked "Places," double-click on "File System." Find a folder called "Media" and open that. In the Media folder, create a new empty folder with the name you want your volume to go by (this is called the Mount Point), and that's it. That empty folder is where Linux will pretend your partition lives while it's mounted.

(For those of you out there in Kubuntu Land, the File System directory is right above the Home directory)

[I]Forgive me if I oversimplify but, well, it just seems **easier** that way, and I do tend to be a bit long-winded at times...
[/I]

---

### Post by spaceballl on 2006-02-24
Im still not completely satisfied w/ this...

For example, let's say I boot up KDE and want to use Amarok w/ my iTunes music library.

So I boot up Amarok and go to my iTunes library folder - can't. OS X or something blocks me from entering user accounts' directories. Does anyone know how to fix this and get around this???

-Kevin

---

### Post by SectionThree on 2006-03-02
Kevin, where do you keep the iTunes music library?

I'm kinda going out on a limb here because I keep all my media files on my 60 GB external drive and I've disabled the library, but here's an idea you can try:

If the music library folder is in its default location, OS X owns that directory and will brook no interference from rival operating system.  Boot up in OS X and move your iTunes folder into an actual volume (e.g. "Macintosh HD"), then open iTunes and set your prefrences so it knows the new location of the library.

Let us know if it works ;)

---

### Post by spaceballl on 2006-03-02
wow. I feel relatively dumb that i never thought of that idea... hahaha

I'll give it a shot later and let you know!

-Kevin

---

### Post by slux on 2006-03-03
I'll have to comment that after someone does as suggested and enables read, write and execute for *everybody* on their system for every single file on a volume, you have effectively destroyed the added security granted by having a multi-user system which is pretty similar to the permission situation that Windows has these days.

If you can manage, I'd strongly recommend being a bit more selective in what you grant everyone access to. IMO the best way to share your data between OS X and Ubuntu is by far to just give identical UIDs to your user in both operating systems after which you'll be able to normally access whatever you can in OS X when using your regular user account also in Ubuntu.

---

### Post by spaceballl on 2006-03-03
Giving my ubuntu the exact same username as my OS X machine will grant me permission??
I might just do that then. Should my Ubuntu name be the full name or the username

---

### Post by slux on 2006-03-03
Well, UIDs are what the system uses to distinguish the different users but they aren't really names, they're numbers associated with the usernames. To change your UID you'll need to change it in the user configuration files and change the ownership of the files (typically in your home dir) to correspond to that new user. 

The GNOME graphical configuration tools let you create new users with a given UID but won't let you change a previously created one. You can either create a new one, move the files and remove the old one or change the UID from the command line.

The easiest way to find out the UID of your OS X user account is most likely to check the ownership of a user-owned file on the OS X partition. Or maybe the OS X user administration tools reveal it too, I'm not sure.

---

### Post by SectionThree on 2006-03-05
Just to be safe, I'd make the "full name" and the "nickname" the same on OS X. That way, there's no question of who's in control no matter how you boot up.

By the way Slux, thanks for the tip!

---

### Post by Bil-E-daKid on 2006-05-07
Hello SectionThree,

Is there anyway of doing this from dapper if I don't have a Mac (I want to use my ipod with HFS+ but without using a Mac as I don't have one).

Just to clarify - by 'this' I mean, the set permissions on the HFS+ filesystem to "(owner, group, guest) permission to do EVERYTHING (read, write, execute)".

Thanks!

---

### Post by farruinn on 2006-05-08
[quote=Bil-E-daKid]Is there anyway of doing this from dapper if I don't have a Mac (I want to use my ipod with HFS+ but without using a Mac as I don't have one).

Just to clarify - by 'this' I mean, the set permissions on the HFS+ filesystem to "(owner, group, guest) permission to do EVERYTHING (read, write, execute)".[/quote]

Do you mean you want to use the iPod as an external hard drive with a non-mac/ppc Ubuntu install? My iPod is auto-mounted with hal/udev magic that I don't understand when I plug it in then I can use is as a hard drive. If this doesn't happen for you, you probably want to start a new thread specific to the iPod.

---

### Post by Bil-E-daKid on 2006-05-08
Hey there Nathan - thanks for the reply,

No (I don't think it was very clear), my question was in response to post #7 in this thread. 

[http://ubuntuforums.org/showpost.php?p=714077&postcount=7]("http://ubuntuforums.org/showpost.php?p=714077&postcount=7")

---

### Post by nkbj on 2006-05-10
On a related note:
When I mount HFS+ partitions made by Mac OS 9.1 in Ubuntu and try to write large files (such as vmlinux for booting by BootX) I get a write error with "No space left on device" even though df shows more than 100MB unused. I can write smaller files (a few KB) without problems. Is there a work-around for this?

Regards,
Niels Kristian

---

### Post by farruinn on 2006-05-10
[quote=nkbj]On a related note:
When I mount HFS+ partitions made by Mac OS 9.1 in Ubuntu and try to write large files (such as vmlinux for booting by BootX) I get a write error with "No space left on device" even though df shows more than 100MB unused. I can write smaller files (a few KB) without problems. Is there a work-around for this?[/quote]

You could try using the split command on a copy of the vmlinux, copy one portion at a time, then use 'cat [parts] > vmlinux' to concatenate the parts. I suggest reading the man pages for both commands before attempting this.

---

### Post by nkbj on 2006-05-10
[QUOTE=farruinn]You could try using the split command on a copy of the vmlinux, copy one portion at a time, then use 'cat [parts] > vmlinux' to concatenate the parts. I suggest reading the man pages for both commands before attempting this.[/QUOTE]

It could work except for the fact that I don't have the cat command in Mac OS Classic. :???: 

Regards,
Niels Kristian

---

### Post by farruinn on 2006-05-11
Use cat before you reboot:
 
```
$ split stuff
$ cp files /path/to/MacOS
$ cd /path/to/MacOS
$ cat files > vmlinux
```

---

