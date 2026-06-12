---
title: "Ubuntu on the Intel Mac Mini"
date: 2006-05-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by sunset_studies on 2006-05-28
Hi,

I'm thinking about getting the Intel Core Duo Mac Mini, but I thought I'd make sure of a few things first. I don't expect to use  OSX (I sometimes have to use it at work - I prefer Ubuntu, the software, the community...), but I'd still like to keep it on the disk.


If anybody could answer any of these questions I'd be grateful:

1) Does XGL/Compiz (sorry, not sure of the exact terms) work with the integrated graphics?

2) Which hardware does/doesn't work? I recently read that the wireless doesn't work, and probably won't any time soon. Is this still the case?

3) Is 512 RAM enough? I'm willing to fork out the extra money for a gig if need be.

4) Is there a definitive howto for setting up a dual boot with OSX on the Intel Mac Mini? 

5) Is it easy/possible to get the remote working with Lirc?

6) Is the machine quiet? do the fans kick in more often than when using OSX on the same machine?

Thanks

---

### Post by amitofu on 2006-05-29
I have an Intel Mac Mini and a MacBook and they both run Ubuntu pretty much flawlessly.

[QUOTE=sunset_studies]1) Does XGL/Compiz (sorry, not sure of the exact terms) work with the integrated graphics?[/QUOTE]

I use AIGLX and Compiz on both machines and it runs very fast and very smoothly. The Intel Integrated Graphics chip has 3d support from open source drivers which is a big win over the proprietary Nvidia or ATI drivers needed for most computers these days. glxgears gives around 1770fps on my MacBook, for reference.

[QUOTE=sunset_studies]2) Which hardware does/doesn't work? I recently read that the wireless doesn't work, and probably won't any time soon. Is this still the case?[/QUOTE]

The wireless works just fine, including WPA. The sound works out of the headphone jack on the mini, but not through the built-in speaker yet. The only big thing not working is sleep, which isn't as big a deal on the Mini as it is on the MacBook.

[QUOTE=sunset_studies]3) Is 512 RAM enough? I'm willing to fork out the extra money for a gig if need be.[/QUOTE]

If your needs are light, 512MB is enough. I upgraded to 2 gigs.

[QUOTE=sunset_studies]4) Is there a definitive howto for setting up a dual boot with OSX on the Intel Mac Mini? [/QUOTE]

Not yet. I may write one. There are bits and pieces all over this forum and the web right now.

[QUOTE=sunset_studies]5) Is it easy/possible to get the remote working with Lirc?[/QUOTE]

Someone wrote a driver and posted it to the mactel-linux-devel mailing list. so it *can* be mde to work now. Expect better support soon though.

[QUOTE=sunset_studies]6) Is the machine quiet? do the fans kick in more often than when using OSX on the same machine?[/QUOTE]

The machine is very quiet. Same noise as with OS X (read: almost none).

I posted a [basic install howto in another thread]("http://ubuntuforums.org/showpost.php?p=1060679&postcount=22") whcih will get Dapper installed for you (which is 90% of the work). Let me know if you have any other questions.

---

### Post by sunset_studies on 2006-05-30
Hi amitofu and thanks for taking the time to answer my questions. I had a look at the mactel-linux devel/user mailing lists after posting here, and it does seem to have a lot of the info I was after - it just takes a little effort to find it all - so a 'howto' from you would be much appreciated. 

I think I'll just wipe osx completely as I really see no need for it now given the Linux hardware support that already exists... but if the only howto I can follow is for a Linux/OSX dual boot, I'll take that.

Dapper Final will be out before I get my Mini, this can only make things easier... right?

---

### Post by chusome on 2006-06-04
Based on most of the information posted it sounds like Ubuntu doesn't natively run on on Mactel's (efi support wise) but I just want to ask the question again so that there will be an absolute answer. 

**Do you have to run Bootcamp in order to Install the intel version of dapper on a Mactel or does it natively support efi?**

---

### Post by vihan on 2006-06-08
To chusome :

Check out this neat Debian Wiki which might help you out :

[http://wiki.debian.org/MacMiniIntel](http://wiki.debian.org/MacMiniIntel)

i don't own a an Intel Mac and haven't tried this out yet but by the looks of it you could get elilo working with a OS X and GNU/Linux dual boot.

To amitofu :

Thanks for letting me know someone is having a GNU/Linux distro running "flawlessly" :D 

i have a few questions for you :

0)How did you do the boot(via an external disk, a CD hack etc) for installing Ubuntu on your Intel Mac(s). Moreover did you use elilo or something else ?

1)The "working drivers" discription you gave below for the Intel Mac Mini are the same true for the Mac Book Pro as well ? i.e Graphics Card, Display, Wireless, working but sound is available only through headphone jack.

2)Are the following working :
   i)Internal modem
   ii)Ethernet card with Gigabit support
   iii)When you connect your Mac Book Pro running Ubuntu to a video        
      projector(via DVI or VGA) is the display visible on both the projector 
      screen AND the Mac ? This was an issue with the PPC PowerBooks,
      the image comes only on the projector screen and the Mac screen is 
      blank the hack was enabling frame buffer mode in Xorg. In Dapper this
      issue has been completely resolved. Dapper also picks up the internal
      modem and airport properly.

3)I know Airport will undoubtly be working, but is Airport Extreme working 
i.e will one get a 54MBps wireless link ?


Thanks for taking the time to read this people!

- vihan

---

