---
title: "Newbie with a couple of questions"
date: 2009-06-25
forum: x86 64-bit Users
---

### Post by howcanshe on 2009-06-25
Hi everyone first post so be kind :D

I decided to make the switch from Windows 7 Build 7100 to Ubuntu as I wanted a lighter/faster operating system.
So far I'm really pleased with it, all I use my computer for is downloading torrents, watching, converting, ripping and burning movies and occasional internet surfing.

Though I now have a few questions that I hope someone here can help with.

I have an ATI Radeon X1650, I have installed ATI Catilyst and installed what I thought were the latest drivers.  However whenever I try to run Catilyst I get a message telling me I need to install the correct drivers?

Something which may be related is the playback of mkv files, 720p or 1080i they start to judder, the audio continues but the video playback is pretty dire.  
I always used to use VLC on the PP and the same files worked fine, so installed that straight away but I actually get better playback with the bundled player!

I have also tried to install Handbrake following some instructions from the net, it seems to have all gone ok and there is an icon in my applications menu.  Yet when I try to load it nothing happens, I click the icon and absolutely nothing not even an error message.

I also have installed Bittorrent which I used to use in windows, when I load a torrent in Ubuntu it comes up in its own window, is there not an application like utorrent/bittorrent where it lists all my uploads/downloads so that I can ensure that I am maintaining a good ratio.

And finally is lightscribe supported by Ubuntu, I am yet to try this as I have no idea how to even burn a disc yet!

As mentioned above I am a n00b so if any help could be really spelled out it would be appreciated.

Thanks a lot!!

---

### Post by bedtime_with_the_bear on 2009-06-25
Not sure about your ATI issues as I'm an nVidia user, but take a look at Vuze for torrents.

---

### Post by Divider on 2009-06-25
Well here is your solution even though you might not like it.

Your stuck between a rock and a hard place, you either need to install the radeon-hd drivers that only support 2D apps or you need to go out and get a radeon 4870, i can tell you from personal experince the nitemare with ati and linux, but the 4870 is "out of the box" compatible and has full 3d support, just download drivers and install, no complicated steps, so bs, it just works. Like ubuntu :P hope this helps.

---

### Post by timjohn7 on 2009-06-25
For your torrent issue, try Transmission or use the latest version of Opera as your browser.  It's built-in torrent facility shows all activity and ratio.
Welcome to Ubuntu!

---

### Post by tospig on 2009-06-25
ktorrent is my torrent app of choice, and it's just like utorrent.

---

### Post by Cheesemill on 2009-06-25
Check out Deluge for your torrents, I'd recommend the latest version fromthe PPA's.

---

### Post by Arup on 2009-06-25
Transmission is as good as utorrent, make sure to add their repo to get the latest. As for your video card. if I am not mistaken, ATI's latest Catalyst are not supposed to work with them.

---

### Post by howcanshe on 2009-06-26
Wow!!

Thanks for all your help so far!!
It seems there are many torrent programs available for me to choose from, I can install them and see for myself ;)

Unfortunately I am now having a bigger issue with my video card/monitor.  I installed an update so that I could watch DVDs on my PC.
When I restarted I don't even get to the login screen, my screen is just striped black and white, I can press escape to boot into the CLI but i'm pretty useless with that type of thing and don't really know where to start!

I have searched the forum and it seems to be a common problem with Nvidia drivers but didn't want to follow those tutorials as I am using an ATI.

Regarding changing the card, financially that is not an option but I do have a couple of spares in my house, i'll see what they are and see if I can get them to work.

I also tried to use BBC iPlayer last night and that wouldn't work either :(

---

### Post by markharding557 on 2009-06-27
hello howcanshe 
if you want support for your ati you will have to use intrepid because it is unsuppoted on jaunty.
of course if you do not need 3d then you can use the open source driver.
use a torrent app from the repository it will work better.
i personally like deluge you pick your own.
regards to your later post what update did you install?
the software you need for dvd is libdcss from the medibuntu repository and totem-xine because toten gsteamer can not handle the dvd menu
[http://www.medibuntu.org/]("http://www.medibuntu.org/")

---

