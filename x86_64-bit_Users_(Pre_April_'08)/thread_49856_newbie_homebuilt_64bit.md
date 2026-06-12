---
title: "newbie homebuilt 64bit"
date: 2005-07-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by marshall_symons on 2005-07-18
hello, im marshall. im 23 and never went to school for computers and really dont know what im doing. this is my second computer ever and the last was a p3 with warty warthog on it, i would like to also connect them together eventuly. i really like linux's ethics and the spirit of it so i decided that any computer i own would be a open source one.
today for the first time ever i built a computer with my friend brady. its an amd 64 athalon 3200 754 socket, the board was free with it, an ecs 755-a2. i put in a kaser 128mb ddr vid card, a dvd rom. i want to watch dvds on this but dont get exactly what to do to make it happen. 
i downloaded the things below but i have really no idea what im doing.  the fuzzy clock says quarter past twelve, so im off to bed


libxine1-1.0.1cvs-050717.k7.rpm
w32codec-0.52-1.i386.rpm
ibdvdcss-1.2.8-2.network.i386.rpm

---

### Post by Flac on 2005-07-18
im no pro... So umm... i am probably completely off, but i dont know if you can use .rpm on ubuntu... I *think* rpm is for distro's based in red-hat. but umm, dont quote me on it.

 As for dvd's, im not sure, i've heard a lot of people say to run DVD's you've got to set up a chroot in 32bit(which i've just done, its a lot easier then i thought it'd be)

 [http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Building_a_clean_32bit_chroot_with_debbootstrap_on_AMD64](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Building_a_clean_32bit_chroot_with_debbootstrap_on_AMD64)
is the guide i followed to get it done, if that is the rout you decide to take. But i would wait for a more experienced user then myself to confirm/slap me in the face, befor you go to too much trouble.

---

### Post by Terracotta on 2005-07-18
Indeed, the .rpm stands for Red-hat-Package Management or something like that, Red-hat and all its derivatives use it, and also mandrake (which used to be a red-hat derivative) and suse-linux uses it as well.
For ubuntu wich is a debian based distro you'll need a package with a .deb extension instead of .rpm. Also, when you have an 64bit installation of ubuntu/debian you won't be able to install an i386 package, that one only works if you have a 32bit version installed of Ubuntu. But normally you should be able to find the suited packages with Synaptic (when you have ubuntu) or kynaptic (when you have Kubuntu). If you launch this program and press ctrl+f, you can search for libxine, or ibdvdcss ... and select it...
w32codecs arent available in 64bit version yet, that's because they aren't available in the windows world in 64bit as well.

Just remember this, to install software you can use Synaptic or Kynaptic, linux distro's are often centralised, this means that they offer all programs you need to install, so you won't have to search the net for a particular program. For further details I'd recommend [amd64.ubuntuguide.org](amd64.ubuntuguide.org), or [www.ubuntuguide.org](www.ubuntuguide.org), there's also a kde ubuntuguide, but to find that you need to go to [www.kubuntu.org](www.kubuntu.org).
I hope this was of any help.

---

### Post by ninotob on 2005-07-18
[QUOTE=marshall_symons].... i want to watch dvds on this but dont get exactly what to do to make it happen. ...[/QUOTE]
 Try here:  [http://ubuntuguide.org/#dvdplayback](http://ubuntuguide.org/#dvdplayback)

Then install xine or mplayer (media players).  Realize of course that watching DVDs in linux basically requires cracking the copy protection.  The first link will give you that capability, and the following entries will give you programs for watching media.

---

### Post by Jet2k5 on 2005-07-18
The ubuntu guide is the best.  Although I don't know if following the 32-bit Ubuntu Guide is the right thing to do, since there might be some different package versions/names and some might not even be fore 64-bit.  I know however there is the right plugins for you to play DVD's on Ubuntu 64-bit.  So instead follow this link here, [http://amd64.ubuntuguide.org/#codecs](http://amd64.ubuntuguide.org/#codecs)  .  From what I've read ubuntu has DVD support out of the box, you just need a pretty good media player.  Totem is pretty crappy.  So I suggest you used either xine ( my favorite ) or mplayer.  Mplayer doesn't have a DVD Menu support from the beginning , but you can get a plugin to fix that.

Good luck.

---

