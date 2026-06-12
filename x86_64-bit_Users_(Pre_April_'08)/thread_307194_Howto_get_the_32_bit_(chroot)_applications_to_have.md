---
title: "Howto get the 32 bit (chroot) applications to have the same Gnome

theme/fonts"
date: 2006-11-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Biker on 2006-11-26
Gnome chroot 32-bit applications looks different in a x64 environment.

I set up a chroot 32-bit environment in Ubuntu Edgy 6.10 x64 with the
excellent howto I found here
[http://www.ubuntuforums.org/showthread.php?t=24575&highlight=dchroot.conf](http://www.ubuntuforums.org/showthread.php?t=24575&highlight=dchroot.conf)

Everything runs fine and I setup firefox32 with flashplayer 9.
Unfortunately the fonts and Gnome theme are completely different (ugly)
despite the use of the same shared home directory which contains my font
settings in ~/.fonts.conf and ~/.fonts

This is what I did to solve the problem:

1. Go into the chroot environment, 'dchroot -d'

2. sudo apt-get install gtk-theme-switch (gtk theme selector without having
Gnome)

3. (Optional) I am using the Murrine GTK2 engine in my x64 environment so I installed
the i386 version in the chroot 32-bit environment too.

wget [http://malteo.homelinux.net/pool/edgy-malteo/extras/gtk2-engines-murrine_0.31-1_i386.deb](http://malteo.homelinux.net/pool/edgy-malteo/extras/gtk2-engines-murrine_0.31-1_i386.deb)
sudo dpkg -i gtk2-engines-murrine_0.31-1_i386.deb

4. Now run gtk-theme-switch2 (for the gtk2 themes) and select your favorite
gtk2 theme from your ~/.themes directory

Your theme selection is saved in ~/.gtkrc-2.0

Mine looks like this,

(chroot)biker@ubuntu:~$ cat .gtkrc-2.0
# -- THEME AUTO-WRITTEN DO NOT EDIT
include "/home/biker/.themes/MurrinaFancyHuman/gtk-2.0/gtkrc"
include "/home/biker/.gtkrc-2.0.mine"
# -- THEME AUTO-WRITTEN DO NOT EDIT

5. The x64 environment and my chroot 32-bit environment are using the same
home directory so there is *no need* to copy these files (~/.gtkrc-2.0,
~/.fonts.conf and the fonts directory ~/.fonts) to the chroot environment.

6. Copy the gnome-font-properties settings (Like Application font and Font
Rendering) from your x64 system to the chroot 32-bit directory.

Type 'exit' in the chroot 32-bit environment.

Type in the x64 system,

sudo cp -R /etc/fonts /chroot/etc/

7. Run your 32-bit application like firefox32 and it looks like exactly the
same now as my other Gnome applications.

You can find a screenshot here of my Gnome Murrine theme running firefox32
in a x64 system.

[http://www.eovermeer.nl/~biker/screenshots/ss-chroot-ff32.png](http://www.eovermeer.nl/~biker/screenshots/ss-chroot-ff32.png)

8. You can run step 4 as root too, 'sudo gtk-theme-switch2'. Now running
'sudo synaptic32' from your x64 environment looks the same as the usual x64
synaptic but I find this a little bit dangerous.

---

