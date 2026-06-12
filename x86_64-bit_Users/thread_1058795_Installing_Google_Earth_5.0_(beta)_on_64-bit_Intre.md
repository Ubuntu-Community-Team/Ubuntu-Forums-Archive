---
title: "Installing Google Earth 5.0 (beta) on 64-bit Intrepid"
date: 2009-02-03
forum: x86 64-bit Users
---

### Post by mhenriday on 2009-02-03
Interested as I am in seeing what the ocean bottom looks like at depths that a former sport diver never could reach, I downloaded the **GoogleEarthLinux.bin** file, and then entered

```
chmod a+x name_of_file.bin

sudo ./name_of_file.bin
```

in a terminal. Everything starts out well :

> Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.0.11337.1968.

But this promising beginning is followed by :

> loki_setup: Konstigt storleksvärde för valmöljlighet option

/usr/lib/gio/modules/libgiogconf.so: fel ELF-klass: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: fel ELF-klass: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: fel ELF-klass: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
loki_setup: Konstigt storleksvärde för valmöljlighet option

Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...
Warning: Unable to create prefs directory '/root/.googleearth'. Filen existerar.
./googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

When I attempt to load the programme by entering ```
googleearth
```in a terminal, the programme does initiate, but then disappears almost immediately from my screen. I've repeated this procedure several times, with the same unfortunate result. So for the moment, I've gone back to the **Mediabuntu** repository version of **Google Earth 4.3**, which lacks the ocean floor. Has anyone else succeeded in installing the bin file on a 64-bit **Intrepid** setup ? Any tips as to how I might be able to do so ?...

Henri

---

### Post by portis on 2009-02-03
you can delete or rename the libcrypt.so.0.9.8 shipped with googleearth, and make a softlink to /usr/lib32/libcrypt.so.0.9.8 in the googleearth directory.

> **mhenriday said:**
> Interested as I am in seeing what the ocean bottom looks like at depths that a former sport diver never could reach, I downloaded the **GoogleEarthLinux.bin** file, and then entered

```
chmod a+x name_of_file.bin

sudo ./name_of_file.bin
```

in a terminal. Everything starts out well :



But this promising beginning is followed by :



When I attempt to load the programme by entering ```
googleearth
```in a terminal, the programme does initiate, but then disappears almost immediately from my screen. I've repeated this procedure several times, with the same unfortunate result. So for the moment, I've gone back to the **Mediabuntu** repository version of **Google Earth 4.3**, which lacks the ocean floor. Has anyone else succeeded in installing the bin file on a 64-bit **Intrepid** setup ? Any tips as to how I might be able to do so ?...

Henri

---

### Post by aaronb on 2009-02-03
Please do **not** use the 'su' or 'sudo' commands as it is not needed for the below instructions.

1. Download google earth 5.0 beta
2. Right click on file and give it permissions at execute.
3. Run the installer in a terminal and follow on screen instructions. (I have a applications folder in my user folder for apps that I do not want to install system wide).
4. Delete libssl.so.0.9.8 and/or libcrypto.so.0.9.8 from the google earth folder.
5. Run the google earth using the icon that appears on your desk top.

---

### Post by jespdj on 2009-02-04
The libcrypto problem is a [known problem](http://ubuntuforums.org/showthread.php?t=1058081&highlight=google+earth) that's not specific to the 64-bit version.

Since Google Earth is a 32-bit program, you do need to install the necessary 32-bit libraries to make it work. The [getlibs](http://ubuntuforums.org/showthread.php?t=474790) script can do this automatically for you (I haven't tried it myself with Google Earth 5.0).

---

### Post by mhenriday on 2009-02-04
Thanks to all those who replied ! Unfortunately, the 32-bit libraries mentioned by **jespdj**, were already installed on my box, so the solution did not lie there. What I ended up doing, after perusing **elcorazon**'s suggestion on [_*page 2 of this thread*_]("http://ubuntuforums.org/showthread.php?t=1058081&highlight=google+earth&page=2"), was to enter the following
[INDENT]```
sudo su -
cd /opt/google-earth
mv libcrypto.so.0.9.8 libcrypto.so.0.9.8.bak 
```[/INDENT]
into a terminal, and as **elcorazon** so aptly put it, *Voila !*...

However, I still encounter a problem ; whenever I load **Google Earth 5.0**, it opens to a window with a smaller window to the upper left which completely obscures the **Google Earth** menu row (see the first screenshot below). Unfortunately, I haven't been able to find any way to remove or even just move the little window ; instead, I have to re-size the main window and draw it down under the intruder (see the second screenshot below). Any suggestions as to how I can deal with this problem ?...

Henri

---

### Post by jespdj on 2009-02-04
Do you have Compiz (desktop effects) running? That can cause problems with some 3D graphics applications in combination with some graphics card drivers.

Try switching off Compiz (System > Preferences > Appearance, Visual Effects, choose "None").

---

### Post by Stunts on 2009-02-04
Just press "Alt" and click and drag the window to somewhere else.
=-)
Hope it was of help!

---

### Post by mhenriday on 2009-02-04
Thanks for your responses, **jespdj** and **Stunts** ! My problem did not lie with my **Compiz** settings, which my **Nvidia Geforce 7900GTX** card seems to handle fairly well, but rather with the fact that the title bar of the «Ruler» tool (if, indeed, it is called so in English - I'm translating here from the Swedish), which allows one to measure distances and bearings, was hidden under the **Ubuntu** panel. Thus I couldn't move it by simply grasping the title bar with my left mouse button and dragging it to a convenient location ; instead I first had to downsize my Google Earth window before I could get to «Tools» to turn the Ruler off - that is, until I finally realised that, just as **Stunts** points out above, all that had to be done was to hold down the «Alt» key, which allowed me to grab hold of the Ruler window anywhere on its surface. So can it go ! Sometimes the simplest solutions are the best - if one can think of them !...

Henri

---

