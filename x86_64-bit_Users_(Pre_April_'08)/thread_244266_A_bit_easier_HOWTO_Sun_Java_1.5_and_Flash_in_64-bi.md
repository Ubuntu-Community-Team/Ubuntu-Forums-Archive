---
title: "A bit easier HOWTO: Sun Java 1.5 and Flash in 64-bit Konqueror browser (in Dapper)!"
date: 2006-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by gsdefender on 2006-08-26
I have recently returned to Kubuntu after a stay with Debian sid (and hard disk trashing :-D). I had used a slight modification of the method shown  [here]("http://www.ubuntuforums.org/archive/index.php/t-90919.html") to get 32 bit Netscape plugins under Konqueror for AMD64 on sid, ([here]("http://gsdefender.wordpress.com/2006/08/12/konqueror-amd64-con-java-e-flash/"), Italian only, sorry) and after my return I wanted to check out if there was any difference.

For what concerns Java 1.5, the tiny thingie works perfectly as shown there: as I don't want to be considered a spoiler :-), I prefer redirecting you to the topic.

Good news, instead, for Flash: it can be oversimplified! :-D
There are fewer and easier steps to do:

[LIST=12]
[*]Enable at least the "universe" repository in /etc/apt/sources.list, then do a
```
sudo apt-get update
```
[*]Install some important packages for the 32 bit emulation layer, together with the ALSA support (for sound):
```
sudo apt-get install ia32-libs ia32-libs-kde lib32asound*
```
[*]Get the 32 bit konqueror-nsplugins package (the Netscape plugin detector) from [here](http://packages.ubuntulinux.org/dapper/utils/konqueror-nsplugins). Be careful to choose the **i386** link at the bottom of this page.
[*]Rename some files that may collide with the 32 bit package:
```
sudo mv /usr/bin/nspluginviewer /usr/bin/nspluginviewer64
sudo mv /usr/bin/nspluginscan /usr/bin/nspluginscan64

```
[*]We need to extract only two files from the 32 bit - forcing installation of the package may break something severely. So I suggest installing Midnight Commander, that has a virtual file system for Debian packages:
```
sudo apt-get install mc
```
[*]Open Midnight Commander as root with:
```
sudo mc
```
[*]Select the konqueror-nsplugins 32 bit package and press ENTER, then navigate to CONTENTS/usr/bin.
[*]Copy nspluginscan and nspluginviewer to /usr/bin by pressing Insert until the two files become yellow, then press F5 and write "/usr/bin" in the To: field.
[*]Quit the Midnight Commander, then do:
```

sudo mv /usr/bin/nspluginviewer /usr/bin/nspluginviewer32
sudo mv /usr/bin/nspluginscan /usr/bin/nspluginscan32
sudo ln -s /usr/bin/nspluginviewer32 /usr/bin/nspluginviewer
sudo ln -s /usr/bin/nspluginscan32 /usr/bin/nspluginscan

```
[*] Download [Macromedia Flash player]("http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash"), decompress the archive and copy the needed files this way:
```
sudo mkdir -p /usr/lib/mozilla/plugins
tar xfz install_flash_player_7_linux.tar.gz
sudo cp install_flash_player_7_linux/libflashplayer.so /usr/lib/mozilla/plugins
sudo cp install_flash_player_7_linux/flashplayer.xpt /usr/lib/mozilla/plugins

```
[*] Try Settings -> Configure Konqueror -> Plugin -> Locate new plugins (I only "think" they are called as so, as all I have at the moment is the italian localization :rolleyes:), then see if a plugin is detected in Plugin.
[/LIST]
Enjoy!

---

### Post by jyhelle on 2006-08-27
works great ! thanks / grazie mille

---

### Post by vlo on 2006-10-25
Didn't work for me. After following your guide I did the following:

I got it working by copying the following files from the following 32-bit packages to my /usr/lib32 directory. The packages can be found at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) . All the files reside in CONTENTS/usr/lib/ inside the archives.

libXcursor.so.1 and libXcursor.so.1.0.2 from package libxcursor1
libXfixes.so.3 and libXfixes.so.3.0.0 from package libxfixes3
libXft.so.2 and libXft.so.2.1.2 from package libxft2
libartsdsp.so.0 and libartsdsp.so.0.0.0 from package libarts1c2a
libartsc.so.0 libarts.so.0.0.0 from package libartsc0

---

### Post by kuja on 2006-10-25
Looks more complicated then you give it credit for, but doable. After doing this, will my 64-bit plugins still work?

---

### Post by gsdefender on 2006-10-26
> **vlo said:**
> Didn't work for me. After following your guide I did the following:

I got it working by copying the following files from the following 32-bit packages to my /usr/lib32 directory. The packages can be found at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) . All the files reside in CONTENTS/usr/lib/ inside the archives.

libXcursor.so.1 and libXcursor.so.1.0.2 from package libxcursor1
libXfixes.so.3 and libXfixes.so.3.0.0 from package libxfixes3
libXft.so.2 and libXft.so.2.1.2 from package libxft2
libartsdsp.so.0 and libartsdsp.so.0.0.0 from package libarts1c2a
libartsc.so.0 libarts.so.0.0.0 from package libartsc0

These dependencies weren't needed when I wrote the howto, sorry.

---

### Post by gsdefender on 2006-10-26
> **kuja said:**
> Looks more complicated then you give it credit for, but doable. After doing this, will my 64-bit plugins still work?

No: by replacing those executables you will be limited to 32-bit plugins only.

---

### Post by kuja on 2006-10-26
> **gsdefender said:**
> No: by replacing those executables you will be limited to 32-bit plugins only.
Thought so.

---

### Post by heinkel_111 on 2007-01-27
Hmm I am just in the process of testing this, on an machine running Kubuntu Edgy 64 on AMD64X2 processor

I removed all the "free" GNU-flash an other non-proprietary versions from my system. I followed the steps in the top post and also checked the dependencies. Then I started a new konqueror from the command line, and browsed off to youtube to test. 

The results are, so far, promising but not satisfactory:
- audio is perfect
- video is also perfect (as far as I can see) but
the window where the flash video plays doesn't have the ordinary "player" appearance: there is no slider, no play button, no sound controller - the entire player control panel is gone :(

Am I missing a component? Shoud the flashplayer-mozplugin.so also be there? (As of now I only have the flashplayer.xpt and libflashplayer.so installed as 32 bit plugins).

These are the error messages generated in konsole while testing this random youtube movie page:
```
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(process:7969): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:7969): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `GDK_IS_DISPLAY (display)' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);

(<unknown>:7969): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
QObject: 17 timers now exist for object KJS::WindowQObject::unnamed
QObject: 18 timers now exist for object KJS::WindowQObject::unnamed
.....counts up until..........
QObject: 63 timers now exist for object KJS::WindowQObject::unnamed
QObject: 20 timers now exist for object KJS::WindowQObject::unnamed
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  10
  Minor opcode:  0
  Resource id:  0x4c00008
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x4c00008
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  25
  Minor opcode:  0
  Resource id:  0x4c00008
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  10
  Minor opcode:  0
  Resource id:  0x4c00021
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x4c00021
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  25
  Minor opcode:  0
  Resource id:  0x4c00021
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(process:8004): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:8004): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `GDK_IS_DISPLAY (display)' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);

(<unknown>:8004): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  10
  Minor opcode:  0
  Resource id:  0x4c00008
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x4c00008
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  25
  Minor opcode:  0
  Resource id:  0x4c00008

```

I particularily don't like the OpenSSL error mesages here, does anyone understand what they mean?

EDIT: the badgerbadgerbager.com test page seems to work, it is youtube that is not working properly!

---

### Post by heinkel_111 on 2007-01-27
I AM TRYING TO GET THIS TO WORK WITH FLASHPLAYER 9, NOT 7!

Adding some more here. in youtube it looks like this, everything is there, but resized so small it is almost invisible in upper left corner of player window:
[img]http://www.thcsp.net/images/div/bugs/konqueror64-flash9-problem.png[/img]

---

### Post by gsdefender on 2007-01-28
Much time has passed, and the latest nspluginwrapper is now compatible with konqueror. I advice you to restore your original files, and give nspluginwrapper + the latest Flash 9 stable a try.

---

### Post by heinkel_111 on 2007-01-28
> **gsdefender said:**
> Much time has passed, and the latest nspluginwrapper is now compatible with konqueror. I advice you to restore your original files, and give nspluginwrapper + the latest Flash 9 stable a try.

Well, these forums are magical, I search through time ;) to find advice and this looked like the simplest way, so I decided to give it a try. :)

Anyway, thank you gsdefender for new and up to date advice, I will follow as you lead this time too :D

---

### Post by kuja on 2007-01-28
> **gsdefender said:**
> Much time has passed, and the latest nspluginwrapper is now compatible with konqueror. I advice you to restore your original files, and give nspluginwrapper + the latest Flash 9 stable a try.

:O

---

### Post by heinkel_111 on 2007-01-28
Hi, I have restored my original files, and started from near scratch again, trying to follow the nspluginwrapper approach.

As kubuntu 6.10 to the best of my knowledge is not really binarchcompatible (?) i downloaded the source code for the nspluginwrapper, and built the nspluginviewer on my 32-bit computer and the rest on my 64 bit computer. This is what the installation currently looks like on my 64 bit machine:
```

myuser@mymachine:/usr/lib/nspluginwrapper$ ls -lhp x86_64/linux/
totalt 92K
-rwxr-xr-x 1 root root 20K 2007-01-28 12:14 npconfig
-rwxr-xr-x 1 root root 69K 2007-01-28 12:14 npwrapper.so
myuser@mymachine:/usr/lib/nspluginwrapper$ ls -lhp i386/linux/
totalt 272K
-rwxr-xr-x 1 root root 270K 2007-01-28 12:18 npviewer.bin
myuser@mymachine:/usr/lib/nspluginwrapper$  

```

For me, the of the whole package fails on the 64 bit kubuntu edgy machine because /usr/include/gnu/stubs-32.h is missing:
```

In file included from /usr/include/features.h:346,
                 from /usr/include/stdint.h:26,
                 from /home/thomas/nedlastede/programmer/nspluginwrapper64/nspluginwrapper-0.9.91.2/src/sysdeps.h:35,
                 from /home/thomas/nedlastede/programmer/nspluginwrapper64/nspluginwrapper-0.9.91.2/src/npw-viewer.c:22:
/usr/include/gnu/stubs.h:7:27: error: gnu/stubs-32.h: No such file or directory
make: *** [npviewer-npw-viewer.o] Error 1

```

This is not fatal as I had a 32 bit machine to build the viewer on. I then manually copied the 32 bit npviewer.bin to my installation directory (as shown in directory listings above).

However, just firing up konqueror now i see the Netscape plugins icon, but there are no actual plugins below that, so either my pluginwrapper install is failing* or my plugins are in the wrong place for the pluginwrapper/viewer to see them. Suggestions for testing, anyone?

* In the [release notes](http://gwenole.beauchesne.info/en/projects/nspluginwrapper/help#release_notes), the nspluginwrapper developer gwenole beauchesne notes that a specially built version of konqueror is required, and I don't have that.....
However, I don't think that he is always correct as his binarch support seems to fail on my system too...

---

### Post by kuja on 2007-01-28
I figured out how to get past the gnu/stubsj-32.h problem . .. it's in libc6-dev-i386. It will also fail again on Ubuntu systems somewhere else, with a more difficult to get past error. It looks like the fix for the problem is supposed to be this: "export CFLAGS=-fno-stack-protector", but no joy here :(

---

