---
title: "trying out opensuse: couple of questions"
date: 2007-03-23
forum: openSUSE and SUSE Linux Enterprise
---

### Post by letitsnow on 2007-03-23
i just installed opensuse 10.2(kde) in a triple boot setup with xp and kubuntu. i'm very impressed at how it looks, but rather disappointed with problems getting online. my machine is a desktop with an onboard intel wired ethernet adapter. it is recognized, but thinks a cable is unplugged. i can get on the net fine with kubuntu, so it's not a hardware issue.

i need to install the restricted codecs as well, but i don't know how. i have all 6 cd's if that helps any.

Thanks!

---

### Post by Adamant1988 on 2007-03-23
You're not the only one who has had issues getting online.  Have you tried using YaST to reconfigure your ethernet card?

---

### Post by letitsnow on 2007-03-23
i attempted too, but i didn't know exactly what to do. it saw the card and the info it had about it seemed ok. 

i'm gonna boot into suse now and fiddle with things for a while.

---

### Post by Adamant1988 on 2007-03-23
I know you're not the only one who has had issues getting connected.  Admittedly I had no such problems with my hardware when I ran it, so I don't know anything about fixing it.  Perhaps check their forums/wiki.

---

### Post by letitsnow on 2007-03-23
I got it! i had to uncheck the 'update name servers and search list via DHCP' option in configure. i'm posting from suse right now.

no, about those codecs....

---

### Post by Adamant1988 on 2007-03-23
There is lots of documentation on the opensuse wiki regarding restricted formats.  I've taken the time to find the ones you'll most likely find relevant. 

[ openSuSE Restricted Formats](http://opensuse-community.org/Restricted_Formats)
[ Flash for openSuSE ](http://opensuse-community.org/Restricted_Formats/Flash9)
[ libDVDcss ](http://download.videolan.org/pub/libdvdcss/1.2.9/rpm/libdvdcss2-1.2.9-1.i386.rpm)

---

### Post by letitsnow on 2007-03-23
Wow, thank you so much! 

i looked at an opensuse wiki and couldn't find crap, it had a lot of stuff about how linking to any of those was a violation of the GPL though.

Thanks!

---

### Post by letitsnow on 2007-03-24
somehow i managed to mess up the xserver. i added those repos, and shut down for the night, now when i try to boot it just goes to a blank screen. when i boot to recovery mode and type startx it get and error saying no screens found on display 0:0 (or maybe it was 0:0:0)

does dpkg --reconfigure xserver-xorg work in suse? and what is the command line text editor, it doesn't have nano and i don't know how to use vi.

Thanks!

---

### Post by julian67 on 2007-03-25
> **letitsnow said:**
> somehow i managed to mess up the xserver. i added those repos, and shut down for the night, now when i try to boot it just goes to a blank screen. when i boot to recovery mode and type startx it get and error saying no screens found on display 0:0 (or maybe it was 0:0:0)

does dpkg --reconfigure xserver-xorg work in suse? and what is the command line text editor, it doesn't have nano and i don't know how to use vi.

Thanks!

No opensuse doesn't use dpkg. You need to re-configure X. Boot to the terminal but don't try to start X. Log in as root in the terminal and type yast and hit return and you'll be into the yast config tool within the terminal, it's probably easier to use than the gui tool anyway and you can redo your x server configuration. If you need some help using Vim (and who doesn't?) look at the [Vim commands cheat sheet]("http://www.tuxfiles.org/linuxhelp/vimcheat.html") which will hep you get started. 

To enable multimedia support you will need to add a couple of repositories. Here's how: [http://en.opensuse.org/Additional_YaST_Package_Repositories]("http://en.opensuse.org/Additional_YaST_Package_Repositories")

You'll need the Packman and Guru repos enabled. I don't know if you're using Gnome or KDE in openSuse. For Gnome install Gstreamer 10 and the good, bad and ugly plug ins and the fluendo codecs. You can then use Rhythmbox as your music player and Totem will play the movies.  

In KDE you'll need to uninstall the original K3b, Amarok and everything Xine except xinetd!!!! Install Amarok-xine, libxine1 and xine-extra from Guru repos and you'll have a great CD/DVD burner app, 1st class audio player and can use Kaffeine for your movies. 

Alternatively for movies install mplayer and for music Audacious is a nice Winamp style player with plug ins containing all the codecs you'd need. Both these apps are fine with any desktop envronment.

---

### Post by letitsnow on 2007-03-25
Thanks, i'll give that a whirl.

when X was working i had to specify what display to use i.e.:
```
sudo kate --display=:0 /filename
```
is this normal?

---

### Post by julian67 on 2007-03-25
> **letitsnow said:**
> Thanks, i'll give that a whirl.

when X was working i had to specify what display to use i.e.:
```
sudo kate --display=:0 /filename
```
is this normal?

No :lolflag:

reconfigure X

---

### Post by letitsnow on 2007-03-25
ok, i've got everything going now. the issue with editing files was that i wasn't using kdesu, i was using sudo. 

after using it for a little while i do have to say it isn't as light as kubuntu. it uses 80mb more memory(actually swap) than kubuntu doing the same things(playing music with amarok and browsing the web). it is very pretty and well finished though.

---

### Post by julian67 on 2007-03-26
You might want to check hich services are running and disable those you don't need. [managing system services suse]("http://forums.suselinuxsupport.de/index.php?showtopic=37949")

The board where that thread is located is an excellent place to find answers to your questions about openSuse, there is a wiki, very good howtos and so on.

---

