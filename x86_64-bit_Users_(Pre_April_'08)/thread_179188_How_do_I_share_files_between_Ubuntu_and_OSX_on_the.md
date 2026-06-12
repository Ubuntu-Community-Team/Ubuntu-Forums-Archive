---
title: "How do I share files between Ubuntu and OSX on the same machine?"
date: 2006-05-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by coolowlBrisbane on 2006-05-19
[FONT="Franklin Gothic Medium"][SIZE="3"][COLOR="Purple"][/COLOR][/SIZE][/FONT]
A PowerBook G4 (the one just before the Intels) has OS X Tiger 4.6 and Ubuntu Breezy installed and it dual boots easily and runs well in either (oh, I cannot print with the HP laser in Ubuntu)...

I'd like to be able to share files between both partitions - have the one mount on the other's desktop or some arrangement of swap folder or whatever.

I've been mucking about both with Google and the search in this Forum to try and get some information but I guess I haven't phrased my qeustions correctly.

Anyway, if there's something fairly simple then I'd love to know how to do it - a system similar to the swap folder in VPC, or some way more elegant, perhaps?

Meanwhile, I feel a bit like this person ... ](*,)

---

### Post by skippy81 on 2006-05-19
Im not much of a Mac fan myself, but I believe they use a file system called HFS and HFS+.  

I just searched my disk and found kernel modules named "hfs" and "hfsplus".   You could have a crack at 

> modprobe hfsplus from a terminal and see if this lets you mount the mac volume.  I have no idea as to the stability of these drivers so I would exercise caution about writing to the Mac volume until you've learnt more about the hfs drivers.

---

### Post by ssam on 2006-05-19
for mounting ext2/3 (linux) partitions on mac os x there is [http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)

for mounting hfsplus partitions in linux see [https://wiki.ubuntu.com/AutomaticallyMountPartitions](https://wiki.ubuntu.com/AutomaticallyMountPartitions)

you probably need to set the hfs partition to be non journaled in mac os x disk utility.

---

### Post by coolowlBrisbane on 2006-05-19
[QUOTE=ssam]you probably need to set the hfs partition to be non journaled in mac os x disk utility.[/QUOTE]
That's the only part of the message I can understand - journaling is turned off.

Thank you for taking the time to reply but the solutions are way in advance of anything I can implement at this stage.

I was hoping to share files between the Ubuntu and OSX Tiger partitions on the same machine but looks as though there's no straightforward solution. Even if I could mount the volumes, I've no idea if the files would be readable anyway.:-| 

It was fun while it lasted.

---

### Post by aimislame15 on 2006-05-19
Its so simple. Don't give up! you simply use the mount command in terminal.

To mount your linux partition (which is formatted as ext2 or ext3) on the Mac OS X side, you would use a preference pane called Ext2FSX. Its a very simple preference pane that automatically mounts the linux partition on OSX. Here is the link.

[http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)

For mounting your Mac OS X partition on linux, it's a bit more difficult (yet still a cakewalk). You'll need to open your partitioning tool and find the /dev/disk number. Mine is /dev/disk0s10. Then you need to know the type of file system that your computer uses for OS X. Most of them are HFSPlus. Now go to the linux command prompt.

You need to create a directory in your /Media/ folder that will be the mounting place of your OSX partition. I decided to make mine /Media/mac.
Now you have all the pieces of the puzzle.

Place this stuff where it goes in the mount prompt.

```
mount -t <File system type> /dev/disk#s# -w /media/mac/
```

I hope that was thorough enough. If not, just msg me on AIM. My handle is aimislame15. Cheers :cheers:

---

### Post by coolowlBrisbane on 2006-05-20
[QUOTE=aimislame15] Its a very simple preference pane that automatically mounts the linux partition on OSX.

Thank you :-D 

That it's a Preference Pane makes all the difference to my understanding what the "thing" is ... I had been to that url, a previous poster had sent it so I went in search of enlightenment. I was none the wiser after having read the very sketchy text except that the developer had finally finished whatever-it-was.

It might be simplest for me to just have Ubuntu on the OSX desktop rather than trying to do a 2-way swap. Whatever text and pix I need to transfer to Ubuntu could be pushed from the Mac partition - I'm assuming Ubuntu can read plain text from TextWrangler and standard graphic formats. I want to use Scribus since it's not useable in Tiger yet (or not for me, others seem to get by with it) and I've text and pix on my Mac which I would need if I'm to use Scribus in Ubuntu. Emailing is another option but just a tad klunky!

Another question - how do I get Ubuntu to link up with my HP laser? It's a 5MP and uses Ethernet with an Asante bridge; can be direct or via the Ethernet hub. Don't know where to start getting Ubuntu to see the printer.

Thank you for your replies, I might just live long enough to actually get some work done with Ubuntu :???:

---

### Post by coolowlBrisbane on 2006-05-20
[QUOTE=aimislame15]Its a very simple preference pane that automatically mounts the linux partition on OSX.

Oh indeed it does. BUT (isn't there always?) it is *read only*. The widget for Tiger says something about it being 'read only' and it sounded like the widget itself, not my Ubuntu partition.:-? 

Is there some way I can get the Ubuntu partition to allow editing when it's mounted on the Mac? I have ticked 'ignore permissions' and have not ticked 'mount read only'.

Even if I can get the OSX partition to mount on Ubuntu, what liklihood is there of file sharing? Or will it be 'read only' as well?

Thank you for your offer of contacting you via AIM - I don't know where you are and unless you're in Australia there might be an insurmountable time difference plus I haven't tried to set up an AIM whatever, so I'll plug along with this forum for the time being.

---

### Post by aimislame15 on 2006-05-20
I've had very mixed luck with writing back and forth on the drives. At one time I was able, and then unable. I'll play around with the command line some more and see what I can do. I'm in Texas, but I'm online for a good portion of the day usually. I have actually never tried printing from linux, but lots of people seem to have problems with it. I'll look into that as well.

---

### Post by coolowlBrisbane on 2006-05-20
[QUOTE=aimislame15]I'll play around with the command line some more and see what I can do.[/QUOTE]
Great, thanks! Looks like the simple solution is to email the stuff I want to have in Ubuntu.

[QUOTE=aimislame15]I have actually never tried printing from linux, but lots of people seem to have problems with it. I'll look into that as well.[/QUOTE]
My partner can print from Ubuntu but with her USB inkjet, she's never tried the Ethernet route to my laser. Also she's got a Compaq so the version of Ubuntu is slightly different.

Thank you for your help, looks like there's no seamless simple solution - no equivilent of Classic but then neither is the price tag.:-k

---

### Post by EuroCity on 2006-05-21
BTW, does anyone know the development status of the HFS+ Journaled file system support in Linux (not only in Ubuntu, of course)? It seems that for now it is safe only as read-only solution; thus, sadly, no reliable write support.

Of course, full read-write support would be a very good thing from the sharing point of view, as most OS X volumes are formatted as HFS+ Journaled...

---

### Post by Ptero-4 on 2006-05-21
I use my HFS+ journaled drive for OSX and write to it from xubuntu fine. Haven't had data or filesystem corruption yet. As for the ext2fsx thing. You need to run fsck on the ext2/3 drive from the terminal and then unmount and mount the drive from the preference pane. And remember that this procedure needs to be done whenever you reboot after OSX crashed/was improperly shut down.

---

### Post by coolowlBrisbane on 2006-05-21
[QUOTE=Ptero-4] You need to run fsck on the ext2/3 drive from the terminal and then unmount and mount the drive from the preference pane. And remember that this procedure needs to be done whenever you reboot after OSX crashed/was improperly shut down.[/QUOTE]
Mmm, now this really is skating in areas of confusion. I've never had OSX crash on me yet but there's been many times when I've shutdown/restarted or loggedout/loggedin. Do you mean that I would need to go through some procedure (of which I'm not at all clear) each time I start up? The preference pane has few options, I've already ticked 'ignore permissions' and that doesn't seem to work.

What commands are written to the terminal? The writer of the preference pane doesn't have any instructions on using the terminal with his pane.

The instructions which came with the preference pane sounded like it was the preference pane's code that was 'read only' but it turns out that the action of the pane is to make the Ubuntu partition 'read only'. Altogether a different situation!

Apart from the klunky but workable solution of sending the text and pix I want to have in Ubuntu *by email* how can a non-geek old chook like me get the Ubuntu partition to accept editing? If it entails writing instructions in the terminal *each time* I start up the Tiger/Ubuntu machine, then that is not workable for me.

I use a PowerBook for Tiger/Ubuntu and Ubuntu does not appear to have any method by which I can set it to go to sleep. When Ubuntu is active the PB never stops so it's working overtime all the time. I've adopted the habit of shutting down completely when not actually using Ubuntu - it goes to sleep properly only in Tiger. And that's why having to write to the terminal and do other voodoo just to transfer some files is not a practical situation.

I guess these minor details will sort themselves out over time. Thank you to all posters who have offered information and solutions:D

---

### Post by EuroCity on 2006-05-22
So, if writing to HFS+ Journaled really works well, one could even imagine to use the OS X home folder also as the Ubuntu home folder, by making a symlink from /Users/username in OS X to /home/username in Ubuntu, of course with the same username, uid and gid (or at least symlinking the individual Documents, Pictures, etc. folders): would this be possibile, or would there be problems? After all, if one can write to the OS X volume, it should be possible, indeed...

Of course, this would be the ultimate "sharing" solution, as you could continue to store everything in your existing /Users folder, provided the OS X partition is big enough (personally, I have a separate partition on OS X only for /Users, similarly to having a separate /home partition on Linux).

I'm not so sure it's completely safe to write to HFS+ Journaled yet, however, at least officially: if I'm not mistaken, it is supported only as an "at your own risk" solution.

But there's hope for the near future, anyway...

---

### Post by Ptero-4 on 2006-05-24
[QUOTE=coolowlBrisbane]Mmm, now this really is skating in areas of confusion. I've never had OSX crash on me yet but there's been many times when I've shutdown/restarted or loggedout/loggedin. Do you mean that I would need to go through some procedure (of which I'm not at all clear) each time I start up? The preference pane has few options, I've already ticked 'ignore permissions' and that doesn't seem to work.

What commands are written to the terminal? The writer of the preference pane doesn't have any instructions on using the terminal with his pane.

The instructions which came with the preference pane sounded like it was the preference pane's code that was 'read only' but it turns out that the action of the pane is to make the Ubuntu partition 'read only'. Altogether a different situation!

Apart from the klunky but workable solution of sending the text and pix I want to have in Ubuntu *by email* how can a non-geek old chook like me get the Ubuntu partition to accept editing? If it entails writing instructions in the terminal *each time* I start up the Tiger/Ubuntu machine, then that is not workable for me.

I use a PowerBook for Tiger/Ubuntu and Ubuntu does not appear to have any method by which I can set it to go to sleep. When Ubuntu is active the PB never stops so it's working overtime all the time. I've adopted the habit of shutting down completely when not actually using Ubuntu - it goes to sleep properly only in Tiger. And that's why having to write to the terminal and do other voodoo just to transfer some files is not a practical situation.

I guess these minor details will sort themselves out over time. Thank you to all posters who have offered infor"mation and solutions:D[/QUOTE]

To put it simple:
UNIX systems use the time when they unmount mounted partitions as a checkpoint to define that the integrity of the data in those partitions is complete.
If the computer is turned off with partitions still mounted (The OS crashed) the OS won't have that "checkpoint" and there will be inconsistensies between the state of the partition's data in the last "checkpoint" and the actual data at that moment.
*NIX OS's react to such inconsistensies mounting the partition read-only to keep the user from further increasing those inconsistensies and corrupting the data in that partition.
The only way under *NIX OS's to fix such disk problems is using a tool called fsck, which scans the affected partition(s), fixes any data corruption that might exist and creates a new "checkpoint". After that the OS will see the data as consistent with the "checkpoint" and will mount the partition writable again.

This means that AS LONG AS OSX DOESN'T CRASH OR LOCKS UP HARD the partition will always mount writable. The running of fsck is only the first time you run ext2fsx (due to a bug in ext2fsx) or after a OSX crash.

---

### Post by coolowlBrisbane on 2006-05-24
[QUOTE=Ptero-4]The running of fsck is only the first time you run ext2fsx (due to a bug in ext2fsx) or after a OSX crash.[/QUOTE]
Ah! Finally I get the picture:D 

Since it seems to be a command-line app I'd best side-step it and just stick to emailing my stuff for now.

Thank you for all your help, everyone who replied and took part :D

---

### Post by xurios on 2006-05-24
Here is exactly how I mount and read/write my OS X partition from Ubuntu. Please forgive me when I explain stuff that you probably already know, I just wanted to be as complete and clear as possible.

From the OS X side:

A) Forget ext2hfs. It's buggy. (If you really want to read the Ubuntu volume from OS X, you can use it, but it can cause crashes. When I need it, I install, use it, and quickly uninstall it.)

B) Go into terminal and type 

```

diskutil disableJournal /

```

Make sure you get the slash in there, that's the name OS X is using for the volume you want to mount in Ubuntu. This command has two effects: It will make it so you can **[color=red]WRITE TO YOUR HFS+ (OS X volume) from Ubuntu[/color]**. It will also mess up spotlight from the OS X side, so any time you want spotlight functionality from OS X, then do the above command from OS X, but type 'enableJournal' instead of 'disableJournal'. Essentailly, using spotlight in OS X and being able to write to your OS X partition from Ubuntu are mutually exclusive. Spotlight requires enableJournal, writing from Ubuntu requires disableJournal (you can always mount and read the OS X partition from Ubuntu, irrespesctive of what you do with journaling, just not always write to it). enable/disableJournal settings stay in effect until you change them. 

**From the Ubuntu side:**

A) Open two files in some text editor: 

/etc/fstab

/etc/yaboot.conf

Looking in yaboot.conf, you can find the name Ubuntu is using for your OS X partition. Look for a line that looks like this:

```
 
macosx=/dev/hda3

```
This is from my yaboot.conf file. My Ubuntu installation is using /dev/hda3 for OS X, yours may differ.

Now, my /etc/fstab file looks like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda3	/media/Gato	hfsplus rw,user,auto 	0	0

```

The last line is what I added so that Ubuntu will automatically mount my OS X partition, and make it readable and writable. The /dev/hda3 line is my OS X partition (info which I got from the yaboot.conf file), and the /media/Gato is where I will mount it. the /media directory already exists in Ubuntu. I had to make the Gato (just type [font=monaco][color=blue]mkdir /media/Gato[/color][/font] from a terminal in Ubuntu, replacing 'Gato'  of course with whatever you want to call it). Make sure you save your fstab file.This should get your OS X partition to show up automatically on your desktop in Ubuntu, when you reboot. The new line in fstab will not take effect until then. You can mount it manually in Ubuntu as well, without rebooting. For my configuration, I type
[font=monaco]
sudo mount -w -t hfsplus /dev/hda3 /media/Gato
[/font]
You would of course change the /dev/hda3 to whatever you found in your yaboot.conf file, and /media/Gato with wherever you want to mount it (you can mount it just about anywhere you want).

I wish you success!

---

### Post by coolowlBrisbane on 2006-05-24
[QUOTE=xurios]Please forgive me when I explain stuff that you probably already know[/QUOTE]
Thank you for that assumption however in this case I'm completely at sea.:???: 

[QUOTE=xurios]diskutil disableJournal /[/QUOTE]
Journaling is already disabled since I use Tech Tool and it's not able to optimize with journaling on. And I've no use for Spotlight so at least that part is simple enough.

[QUOTE=xurios]The last line is what I added so that Ubuntu will automatically mount my OS X partition, and make it readable and writable.[/QUOTE] Does this mean that I can take some files from Tiger and transfer them to Ubuntu?

Pheww, it's a complex procedure. Thank you very much for explaining step by step. I may live long enough to give it a whirl. :-k

---

### Post by xurios on 2006-05-24
> Does this mean that I can take some files from Tiger and transfer them to Ubuntu?

This means that your os x partition (your whole mac world, and assuming that it works out :) ) will be on the desktop of ubuntu, just like any other folder or drive that is living there. It will be readable and writable. You will also be able to find it in media/yourchoicehere. The only problem you may have is with permissions, since you are not the same user on Ubuntu as you are on OS X. Any folder you want to use from one side to the other, you will have to set them read/write for everybody.

Oh, I did this all from the Dapper Drake version, I don't know if you can write to HFS+ from Breezy Badger :( It's worth a try. Maybe someone else can tell us about that.

---

### Post by pindar on 2006-05-24
[QUOTE=xurios]The only problem you may have is with permissions, since you are not the same user on Ubuntu as you are on OS X.[/QUOTE]

Well, this is easy to fix, and it's something I do on all my double-boot macs: the first user on OS X gets the uid (number) 501, so all you have to do is assign the same number and name to yourself in linux. So assuming your user is called joeschmoe, you run the command

```
sudo usermod -u 501 joeschmoe
```

and have the same uid in both systems.

---

### Post by Ptero-4 on 2006-05-26
I can read and write to my OSX HFS+ partition from xubuntu breezy.

---

### Post by EuroCity on 2006-05-26
You should probably also change the ownership of the files in your home folder (but I don't remember how to do that).

It might be easier (as I did) to give the first user account (uid = 1000) created by Ubuntu a generic name (I called it *ubuntu*) and then create another user, which will be your "real" username and assigning it an uid = 501, and so on for other previously existing OS X users (the names must be the same in OS X and Ubuntu, of course). The 501 username should have administrative privileges also in Ubuntu, as in OS X, in order to automatically become a "sudoer".

---

### Post by pindar on 2006-05-26
[QUOTE=EuroCity]You should probably also change the ownership of the files in your home folder (but I don't remember how to do that).

It might be easier (as I did) to give the first user account (uid = 1000) created by Ubuntu a generic name (I called it *ubuntu*) and then create another user, which will be your "real" username and assigning it an uid = 501, and so on for other previously existing OS X users (the names must be the same in OS X and Ubuntu, of course). The 501 username should have administrative privileges also in Ubuntu, as in OS X, in order to automatically become a "sudoer".[/QUOTE]
That's not a bad suggestion at all! Yes, I do remember there was one problem with changing the uid after installation: Gnome would complain it couldn't read some config files. But it's not that difficult to change ownership in your home folder:
```
sudo chown -R YOUR_NAME /home/YOUR_NAME
```
should do the trick. There's a certain security risk in having a generic name like "ubuntu" in your system. If you look into your log files, you'll see that there are constant ssh attacks which try to guess a username and a password; they typically use generic names like "test," "www," or "user." I don't know if any of these stupid scripts has already included a user "ubuntu," but it might happen. You're still safe if you have a decent password, but nevertheless, there's one more possibility to get into your machine.

---

