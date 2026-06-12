---
title: "[SOLVED] Compiz error on ubuntu 8.04"
date: 2008-10-30
forum: x86 64-bit Users
---

### Post by alt3rn1ty on 2008-10-30
Can anyone help correct the following please....
I opened a terminal and typed compiz (just being curious)

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0179 (rev a3) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

How do I correct the problem here?

Machine is a compaq presario laptop athlon 64 nvidia geforce4 440 go with ubuntu x64 8.04 installed.

---

### Post by alt3rn1ty on 2008-10-30
I may need to clarify this a bit ... its the last bit -

GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

How do I remove that value and where?

I recently tried update-manager -d to try 8.10, but decided to stay with 8.04 until 3d Acceleration is supported again for older geforce4. (I know nv will support it in 2D but I have too much 3D requirements so sticking with Hardy which works well).
Anyway it cleaned up nicely after I said no to going any further, and everything seems in order and working normally. I dont believe this update attempt affected compiz settings (linux updates as I understand will completely undo/reverse any changes if you cancel), rather this is probably a problem I had before but was not aware of it (I am still a relative noob with linux). But thought it worth a mention just in case, its the only change I have attempted recently.

---

### Post by alt3rn1ty on 2008-10-30
Found it :), apparently its a bug with hardy.....

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/209207](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/209207)

Brads post gave my solution -
1. System > Preferences > Advanced Desktop Effects Settings. (In my case this was System > Preferences > Compizconfig Settings Manager).
2. Scroll down and open "Scale" under the Window Management section.
3. Go to the Bindings Tab and open the first "Initiate Window Picker" configuration.
4. Choose a corner. This allows you to zoom out and see all your windows to choose one.
5. That's it, you now have a valid value for initiate_edge.

---

