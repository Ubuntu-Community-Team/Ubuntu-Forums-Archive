---
title: "Apple iPod nano 4 GB (3G) Big Problem"
date: 2008-03-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by natibo on 2008-03-15
I bought this ipod for my wife.  I was excited becasue my ipod [Apple iPod Video 60 GB Black MA147LL/A (5th Generation)] works great with Amarok.

With thew ipod, it is a different story.  Songs transfer (Amarok, Gtkpod) to the ipod, and I can even see them and even play them when I browse the drive with nautilis.  However, when I eject the ipod, it syas that there is no music on it.

Two things:

1.   I know about rockbox and do not want to go there yet.  I want album art, and the ability to load photos.

2.  I have found posts related to the problem, but I believe that are related to 32-bit systems.  I am a newbie, and am not sure how to force install or the like.


Any help would be greatly appreciated.:confused:

---

### Post by Gundamironfist on 2008-03-17
:(:mad::( I am experiencing the same exact problem with my 4gig nano... someone please help.

---

### Post by EricDB on 2008-03-30
I managed to get Amarok to transfer music and playlists.  I downloaded libgpod 0.6.0, then built Amarok from source. 

However, it still isn't transferring album art.  Damn Apple.

---

### Post by bsolar on 2008-03-30
First of all to even be able to see a track uploaded with amarok or gtkpod on a new ipod (3g nano, touch), you have to manually edit a file to add the FirewireGuid: [http://gtkpod.wikispaces.com/Sysinfo+File](http://gtkpod.wikispaces.com/Sysinfo+File)

If the problem is the cover art, I finally managed it to work on my ipod nano 8gb (second generation).

The problem was the hfs+ permissions. It was impossible to set the model and create the Artwork directory and artwork files...

To make it work (without formatting it with FAT) I had to give write permissions to everyone for the SysInfo file, create the Artwork directory and give it write permissions, then copy in it a ArtworkDB file created with gtkpod.

Try to do the following:

[LIST=1]
[*]mkdir ~/ipodfakemount
[*]open gtkpod, create a fake ipod repository and give it mount point ~/ipodfakemount
[*]try to connect the fake ipod with gtkpod. It should ask you to create the files in the empty mountpoint. Let it do it and exit gtkpod.
[*]mount your actual iPod let's say in /media/iPod/
[*]sudo chmod a+w /media/iPod/iPod_Control/Device/SysInfo
[*]sudo mkdir /media/iPod/iPod_Control/Artwork
[*]sudo chmod a+w /media/iPod/iPod_Control/Artwork
[*]sudo cp ~/ipodfakemount/iPod_Control/Artwork/ArtworkDB /media/iPod/iPod_Control/Artwork/
[*]sudo chmod a+w /media/iPod/iPod_Control/Artwork/ArtworkDB
[/LIST]

Now you can remove ~/ipodfakemount and from Amarok you should set your ipod model with the little iPod menu in the devices tab.

Artwork update should now work!

---

### Post by camoto on 2008-04-02
Interesting.  I just added the backport for the newest build of amarok with libgpod 6 which supports the newer ipods and it worked like a charm with album art and everything.  I didn't even have to rebuild my Amarok library.

---

