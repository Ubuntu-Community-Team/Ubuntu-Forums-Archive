---
title: "Ubuntuguide finnaly for amd64 !"
date: 2005-06-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by trommas on 2005-06-28
\\:D/ Yes, it's here! \\:D/

Took me long enough to test all the code, but the modification is complete!

Enjoy all you lucky owners of amd64 processors!

Find it here: [http://amd64.ubuntuguide.org]("http://amd64.ubuntuguide.org")

---

### Post by trommas on 2005-06-28
By the way. I would appreciate suggestions for improvement. 

Here are a some topics that needs to be solved (And I am currently looking into solutions for some of them):

- J2SE Runtime Environment
- Flash player (firefox plugin)
- Azureus
- Skype
- Multimedia codecs
- DVD playback
- Realplayer
- Rar

Please feel free to comment on some of these, or point out others.

---

### Post by petunia_volubilis on 2005-06-28
Hello, thanks a lot  :) 

just that clamav version is out of date and freshclam updates are impossible
looking for codecs and Co
still some problems with multisession cd burning (gnomebaker, but might be my computer problem)

---

### Post by Drain on 2005-06-28
A great number of things are the same for both the 32-bit and 64-bit versions of the ubuntuguide - if I might make a suggestion, is there a way to highlight the questions and answers that are different between versions?

---

### Post by olivierp on 2005-06-28
Hi trommas,
THanks for the guide.
For Java with a 64bit plugin, I'd suggest Blackdown:
[http://www.blackdown.org/java-linux/java2-status/jdk1.4-status.html#debs](http://www.blackdown.org/java-linux/java2-status/jdk1.4-status.html#debs)

For the Flash plugin, why not a pointer to a 32-bit chroot howto. This would also help for installing the statically linked skype-1.1.0.13 ?

---

### Post by DRF on 2005-06-28
For DVD playback I found the easiest way to set it up on my computer was to run the script at:
/usr/share/doc/libdvdread3/examples/install-css.sh

I think that script is put there by the libdvdread3 or something like that. It did need a few other packages to be apt-get'ed for it to compile the source the script aquired.

Then afterwards I had to speedup the DVD drive to avoid the horrible stuttering with the dma setting. (Note that I found on my computer that the chipset module had to be loaded before the ide-cd module).

Also the mistake I've spotted in the mplayer install section of the guide:
"sudo apt-get install mplayer-386" should be:
"sudo apt-get install mplayer-amd64" I think.

Would be great to get a recommended audio fix for some of the apps that don't work with the default audio setup. (eg audacity) preferably without removing esd and replacing it all with alsa as it's just a few apps that don't work.

I think thats about everything I've come across so far. Great guide! Keep up the good work. That guide has helpped me out a lot since moving from debian to ubuntu.

Daniel

---

### Post by braveerudite on 2005-06-28
[QUOTE=trommas]\\:D/ Yes, it's here! \\:D/

Took me long enough to test all the code, but the modification is complete!

Enjoy all you lucky owners of amd64 processors!

Find it here: [http://amd64.ubuntuguide.org]("http://amd64.ubuntuguide.org")[/QUOTE]
 Great ....this is very helpful....thx

---

### Post by trommas on 2005-06-28
Great to see that people are using the guide, and making suggestions. I'm currently looking into some alternatives for DVD playback and codecs. I'm also prioritizing an update to the latest version of the x86 guide (as you know there are quite frequent releases of the original x86 version).

You should all know that I'm fresh to the world of Gnu-linux and Ubuntu, but I'll just keep working and asking around till I get it right :)
This guide is teaching me alot as well.

Since it is mid-holiday season, I won't be able to get much work done in some time (I'll be road-tripping all over Norway). But just keep adding suggestions, I'll read them all, and add them to my to-do-list.

---

### Post by Optimal Aurora on 2005-06-28
[QUOTE=trommas]By the way. I would appreciate suggestions for improvement. 

Here are a some topics that needs to be solved (And I am currently looking into solutions for some of them):

- J2SE Runtime Environment
- Flash player (firefox plugin)
- Azureus
- Skype
- Multimedia codecs
- DVD playback
- Realplayer
- Rar

Please feel free to comment on some of these, or point out others.[/QUOTE]
Agreed it still isn't close to being official with those and a few others like: libdvdcss and evince and others but then I know where they are...

---

### Post by Axel_Fooley on 2005-06-29
[QUOTE=DRF]
Also the mistake I've spotted in the mplayer install section of the guide:
"sudo apt-get install mplayer-386" should be:
"sudo apt-get install mplayer-amd64" I think.
[/QUOTE]

Acctualy it should be:
"sudo apt-get install mplayer" - tested

And btw great guide, more of those.

---

### Post by abiezerm on 2005-06-30
hey, 

the guide is great  \\:D/ 

but would be amazing  put a wifi faq or somethin like tha

what u think?

PD: I need a hand with my wifi

---

### Post by Ruud on 2005-07-05
anyone got more codecs for MPlayer?
E.g. the Wmv codecs? :)

---

### Post by duffman25 on 2005-07-14
[QUOTE=DRF]For DVD playback I found the easiest way to set it up on my computer was to run the script at:
/usr/share/doc/libdvdread3/examples/install-css.sh

I think that script is put there by the libdvdread3 or something like that. It did need a few other packages to be apt-get'ed for it to compile the source the script aquired.
Daniel[/QUOTE]

Thanxs man! I downloaded an amd64 deb from marillat and didn't work for my machine (don't know why, because dpkg didn't show any errors on install...).

I think this should be added as a temporal solution while the backports for amd64 take shape... 

Thanxs again :D

---

### Post by nrayever on 2005-07-14
i think the re are some little modification between ubuntuguide for x86 and amd64. ubuntuguide for amd64 should be more specific on details as chroot32, flash-plugin, java, etc.....

i hope they update it.

---

### Post by Jet2k5 on 2005-07-16
[QUOTE=nrayever]i think the re are some little modification between ubuntuguide for x86 and amd64. ubuntuguide for amd64 should be more specific on details as chroot32, flash-plugin, java, etc.....

i hope they update it.[/QUOTE]


I agree.  You should set up something that shows the user how to set up a 32 chroot environmnet.  Like the ones from [here](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Building_a_clean_32bit_chroot_with_debbootstrap_on_AMD64)  also you should includ the part about installing Cedega.  I noticed that on the Ubuntu Guide you just fowared to a link that is quite frankly worthless for a n00b.  What I liked you to should be much easier.

---

