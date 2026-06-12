---
title: "NvClock CVS"
date: 2007-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by d-_-b on 2007-10-21
Hi all. I was wondering if someone could help a noob looking to install the NEWEST version of NvClock CVS (whatever CVS means...). supposedly this is the only version that supports fan control of the new geforce 8800GTX. 
O and please, post STEP BY STEP procedures on how to go about doing this on kubuntu. i need step by step since i get lost pretty easily... lol 
Thanks linux pros. :)

---

### Post by d-_-b on 2007-10-22
can anybody help me? please? :)

---

### Post by snkmad on 2007-10-22
Well im quite new to linux, but ill try to help. 
CVS stands for Current Version System. Its like a Work-In-progress source code of a program.

[Nvidia overclocking utlity]("http://sourceforge.net/projects/nvclock/")
Thats the site for that program. I just went to look at the cvs code, and just found a [README]("http://nvclock.cvs.sourceforge.net/nvclock/nvclock/README?revision=1.9&view=markup") file, which explains how to build the program from source. 
Its more than 14 months old, but the install procedures should be the same or similar.

To download the source to compile, you´ll need a cvs client.

Hope this get you going somewhere...

---

### Post by ben10 on 2008-01-03
sudo apt-get install cvs nvclock

BAM

---

### Post by Sockerdrickan on 2008-01-03
```
#!bin/sh
cd

echo "\nThis script will download & compile nvclock to your home dir."
echo "\n- PRESS ENTER -\n"
cvs -q -d:pserver:anonymous@nvclock.cvs.sourceforge.net:/cvsroot/nvclock login
cvs -q -z3 -d:pserver:anonymous@nvclock.cvs.sourceforge.net:/cvsroot/nvclock co -P nvclock

cd nvclock
sh autogen.sh
./configure -q
make -s

echo -n "\nMoving binary to /home/`whoami` and removing cvs dir..."
mv src/nvclock ../nvclock_cli
cd
rm -rf nvclock
mv nvclock_cli nvclock
echo " Done"

echo "\nnvclock has been built from CVS. Have a nice day `whoami`."
```

I wrote this have fun.

---

### Post by dboot on 2008-01-04
Any luck?

I have an 8800 GT with the same problem after upgrading nvidia drivers (fan is always at 100%). After installing nvclock v0.8 and running "nvclock -f -F 40," I get "Error: Your card doesn't support fanspeed adjustments!"

Any help would be appreciated!

---

### Post by Sockerdrickan on 2008-01-04
Did you really use my script I just posted to get the latest cvs / compiled?

---

### Post by dboot on 2008-01-04
I first tried compiling it myself with the source from the website. I ran it with the parameters I previously said and got the same error. Then I found this thread and used your shell script to download and install the latest version (thinking the version I downloaded was not the latest). I ran the same parameters and got the same error.

Any thoughts?

More specifically, I have a BFG nVidia 8800GT OC. I suppose the latest version of nvclock just isn't compatible with my specific graphics card.

---

### Post by crjackson on 2008-01-04
> **Tux0r said:**
> ```
#!bin/sh
cd

echo "\nThis script will download & compile nvclock to your home dir."
echo "\n- PRESS ENTER -\n"
cvs -q -d:pserver:anonymous@nvclock.cvs.sourceforge.net:/cvsroot/nvclock login
cvs -q -z3 -d:pserver:anonymous@nvclock.cvs.sourceforge.net:/cvsroot/nvclock co -P nvclock

cd nvclock
sh autogen.sh
./configure -q
make -s

echo -n "\nMoving binary to /home/`whoami` and removing cvs dir..."
mv src/nvclock ../nvclock_cli
cd
rm -rf nvclock
mv nvclock_cli nvclock
echo " Done"

echo "\nnvclock has been built from CVS. Have a nice day `whoami`."
```

I wrote this have fun.

Not to butt in, however I'd like to give this script a shot.

I realize I would save the script to a text file and then execute it using a bash command.  Problem is I don't know what the command would be.  I faintly recall something like sh/ filename.sh but I can't be for sure.

Could you please clearify that for me?

Thanks...

---

### Post by dboot on 2008-01-04
The easiest and quickest way for me to use the script is to open the terminal, "vi <anyfilename>", press "i" for insert, paste the script in the terminal and make sure it's the entire script, press ":wq" to save and quit the file, then "chmod +x <filename>" to give it executable permissions, and finally "./<filename>" to run it.

There are several ways to run the script and I know this is more info than you need, but hopefully it will help others.

---

### Post by crjackson on 2008-01-04
> **dboot said:**
> The easiest and quickest way for me to use the script is to open the terminal, "vi <anyfilename>", press "i" for insert, paste the script in the terminal and make sure it's the entire script, press ":wq" to save and quit the file, then "chmod +x <filename>" to give it executable permissions, and finally "./<filename>" to run it.

There are several ways to run the script and I know this is more info than you need, but hopefully it will help others.

Cool thanks.  I prolly won't use vi to make my text file, but was the ./<filename>   that I was looking for.

Thanks...

---

### Post by Sockerdrickan on 2008-01-05
Did my script work out for you crjackson

---

### Post by IanW on 2008-01-05
I had already compiled nvclock on my 64-bit system before your script appeared.

However, once nvclock is compiled and installed, you might find a better command is:-
```
nvclock -f -F auto
```

This worked perfectly for me (my self-compiled Gnome sensors-applet with Nvidia support is currently reporting my 8800GTS 320Mb is idling at 49C).

---

### Post by crjackson on 2008-01-05
> **Tux0r said:**
> Did my script work out for you crjackson

I haven't tried it yet.  I'm working out of town right now.  I'll let you know when I check it out.

---

### Post by bjaurelio on 2008-01-10
i ran your script, but i got this output. the errors happen when i download the source from the nvclock website. after ./autogen.sh and ./configure every time i try make fails. and yes i do have build-essential installed.

```
In file included from ../nvcontrol/nvcontrol.h:26,
                 from backend.c:28:
../nvcontrol/libnvcontrol.h:35:22: error: X11/Xlib.h: No such file or directory
../nvcontrol/libnvcontrol.h:36:21: error: X11/Xmd.h: No such file or directory
In file included from ../nvcontrol/nvcontrol.h:26,
                 from backend.c:28:
../nvcontrol/libnvcontrol.h:235: error: expected specifier-qualifier-list before ‘CARD8’
../nvcontrol/libnvcontrol.h:322: error: expected specifier-qualifier-list before ‘Display’
../nvcontrol/libnvcontrol.h:337: error: expected ‘)’ before ‘*’ token
../nvcontrol/libnvcontrol.h:338: error: expected ‘)’ before ‘*’ token
../nvcontrol/libnvcontrol.h:339: error: expected ‘)’ before ‘*’ token
../nvcontrol/libnvcontrol.h:340: error: expected ‘)’ before ‘*’ token
../nvcontrol/libnvcontrol.h:341: error: expected ‘)’ before ‘*’ token
../nvcontrol/libnvcontrol.h:342: error: expected ‘)’ before ‘*’ token
../nvcontrol/libnvcontrol.h:343: error: expected ‘)’ before ‘*’ token
make[2]: *** [backend.o] Error 1
libnvcontrol.c:32:19: error: X11/X.h: No such file or directory
libnvcontrol.c:33:22: error: X11/Xlib.h: No such file or directory
libnvcontrol.c:34:25: error: X11/Xlibint.h: No such file or directory
libnvcontrol.c:35:36: error: X11/extensions/extutil.h: No such file or directory
In file included from nvcontrol.h:26,
                 from libnvcontrol.c:39:
libnvcontrol.h:36:21: error: X11/Xmd.h: No such file or directory
In file included from nvcontrol.h:26,
                 from libnvcontrol.c:39:
libnvcontrol.h:235: error: expected specifier-qualifier-list before ‘CARD8’
libnvcontrol.h:322: error: expected specifier-qualifier-list before ‘Display’
libnvcontrol.h:337: error: expected ‘)’ before ‘*’ token
libnvcontrol.h:338: error: expected ‘)’ before ‘*’ token
libnvcontrol.h:339: error: expected ‘)’ before ‘*’ token
libnvcontrol.h:340: error: expected ‘)’ before ‘*’ token
libnvcontrol.h:341: error: expected ‘)’ before ‘*’ token
libnvcontrol.h:342: error: expected ‘)’ before ‘*’ token
libnvcontrol.h:343: error: expected ‘)’ before ‘*’ token
libnvcontrol.c:41: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘wire_to_event’
libnvcontrol.c:43: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Hooks’
libnvcontrol.c:56: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
libnvcontrol.c:57: error: expected ‘)’ before string constant
libnvcontrol.c:60: error: expected ‘)’ before ‘*’ token
libnvcontrol.c:81: error: expected ‘)’ before ‘*’ token
libnvcontrol.c:116: error: expected ‘)’ before ‘*’ token
libnvcontrol.c:155: error: expected ‘)’ before ‘*’ token
libnvcontrol.c:196: error: expected ‘)’ before ‘*’ token
libnvcontrol.c:258: error: expected ‘)’ before ‘*’ token
libnvcontrol.c:286: error: expected ‘)’ before ‘*’ token
libnvcontrol.c:312: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘wire_to_event’
make[2]: *** [libnvcontrol.o] Error 1
make[1]: *** No rule to make target `backend/libbackend.a', needed by `nvclock'.  Stop.
make: *** [all] Error 2

Moving binary to /home/bjaurelio and removing cvs dir...mv: cannot stat `src/nvclock': No such file or directory
mv: cannot stat `nvclock_cli': No such file or directory
 Done
```

---

### Post by BobCFC on 2008-01-11
I tried for nearly an hour installing dev libraries in Synaptic on a fresh Hardy install trying to fix the same errors..

libx11-dev
libxext-dev

seemed to solve the first few, but I get stuck with 

undefined reference to `XOpenDisplay'


I saw that older version 0.8b2 of nvclock was already in apt-get but it was too old; said my 8800GTS was too new and unrecognised.  So I googled the interwebs hoping some kind soul had already compiled a recent version and I found this!!!

[http://debian.mirror.inra.fr/debian/pool/main/n/nvclock/](http://debian.mirror.inra.fr/debian/pool/main/n/nvclock/)

For my 64bit needs [http://debian.mirror.inra.fr/debian/pool/main/n/nvclock/nvclock_0.8b3-1_amd64.deb](http://debian.mirror.inra.fr/debian/pool/main/n/nvclock/nvclock_0.8b3-1_amd64.deb)  worked perfectly and now I have a silent fan!!!  There are also 32bit versions and even ARM and ia64 lol.  yay debian we still love you

As stated above:
```

nvclock -f -F auto
```

did the trick nicely untill they fix the bug in the 169.07 driver

---

### Post by Lutin on 2008-01-11
Hmmmm.

Downloaded the files, as above for Debian. However, when I open them with GDebi package installer I get the error message -

"Error: Dependancy is not satisfiable: libc6"

I do have the Libc6 packages installed. Any thoughts anyone?

Running Gutsy x64 on an AMD equipped Acer 7003 laptop.

---

### Post by BobCFC on 2008-01-17
Sorry I've been offline for a few days.

I think the problem is that I was using the new Hardy Heron alpha which has a more recent version of libc6, presumably the same as in Debian unstable.

It is possible to download the libc6 as a .deb file from Debian as well and it will work, but I have done this before and had trouble when Ubuntu updated something which relied on the old version.  It insisted on downgrading libc6 again which removed my new software grrrr.

I suppose you could keep a copy of the libc6 and nvclock debs around in case you need to reinstall them

---

### Post by TheBrainSlug on 2008-01-19
for gusty gibbon:
[http://morgoth.free.fr/ubuntu/pool/main/n/nvclock/](http://morgoth.free.fr/ubuntu/pool/main/n/nvclock/)
works for me :).
Wow, I think my ears just stopped bleeding!
Regards.

---

### Post by PARTyZAN on 2008-01-19
> **TheBrainSlug said:**
> for gusty gibbon:
[http://morgoth.free.fr/ubuntu/pool/main/n/nvclock/](http://morgoth.free.fr/ubuntu/pool/main/n/nvclock/)
works for me :).
Wow, I think my ears just stopped bleeding!
Regards.

Well, not for me. Could anyone package this for x86_64?

---

### Post by ben10 on 2008-01-19
To get NvClock runnin on my 64 bit ubuntu with my 8800gt I needed to apt-get install xorg-dev and the build-essential package (which I already had to get to install new nvidia drivers) Then i just downloaded the binary from the main nvclock website...then I think it would ./autogen.sh and ./configure and make and sudo make install nicely after that. Then just nvclock -F auto -f

---

### Post by KicktheCAN on 2008-01-20
I tried to change the fan speed on my 8800 GT using "nvclock -f -F auto" but I just got "Your card does not support fanspeed adjustments!" Does anybody know how to get around this? I need a way to slow down the fan as it is always running at 100%.

---

### Post by Spydr4590 on 2008-01-21
I'm a little new to compiling and I can compile this without GTK. However, I would like the GTK gui. Whenever I enable that in settings I get multiple errors. I'm really not sure how to get this working /build. Any assistance on building the gtk would be helpful!

Thanks :)

---

### Post by Artemis3 on 2008-01-21
> **ben10 said:**
> To get NvClock runnin on my 64 bit ubuntu with my 8800gt I needed to apt-get install xorg-dev and the build-essential package (which I already had to get to install new nvidia drivers) Then i just downloaded the binary from the main nvclock website...then I think it would ./autogen.sh and ./configure and make and sudo make install nicely after that. Then just nvclock -F auto -f

You can skip xorg-dev because this is only needed for NV-CONTROL (display/opengl tweaks) [see this post](http://ubuntuforums.org/showpost.php?p=4181624&postcount=21) Nvidia provides its own control center and [you can also use env variables](ftp://download.nvidia.com/XFree86/Linux-x86/169.07/README/index.html).

---

### Post by Artemis3 on 2008-01-21
> **KicktheCAN said:**
> I tried to change the fan speed on my 8800 GT using "nvclock -f -F auto" but I just got "Your card does not support fanspeed adjustments!" Does anybody know how to get around this? I need a way to slow down the fan as it is always running at 100%.

[Read my post here](http://ubuntuforums.org/showpost.php?p=4181624&postcount=21).

---

### Post by BobCFC on 2008-01-24
[169.09 drivers]("http://www.nvnews.net/vbulletin/showthread.php?t=106661") are out now which are supposed to fix the fan at 100% issue

---

