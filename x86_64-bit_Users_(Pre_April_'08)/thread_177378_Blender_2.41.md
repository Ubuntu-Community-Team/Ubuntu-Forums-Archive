---
title: "Blender 2.41"
date: 2006-05-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by omenone on 2006-05-16
Anyone have the current version of blender running on Breezy? I have the amd64 release and I can't get it to compile. Is there a more recent package I can install somewhere? The one that currently installs with the cd is 2.37.

Thanks!

---

### Post by FluffyElmo on 2006-05-17
I can't test this as Blender doesn't seem to get along with my video driver anymore. You may be able to install the most current version from the Dapper repositories. General instructions, I assume if you can compile code you can follow them and figure out what they do;)
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.breezy
sudo gedit /etc/apt/sources.list
```
In the file change all occurances of 'breezy' with 'dapper' and then save.
```
sudo apt-get update
```
Run Synaptic and try upgrading Blender. Note that you should only update Blender, if it depends on other system files such as glibc and wants to update them then *don't*. After it has installed then go back to the Breezy repositories.
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.dapper
sudo cp /etc/apt/sources.list.breezy /etc/apt/sources.list
sudo apt-get update
```

Note again that you don't want to update to Dapper as it is unstable and in testing.  The Blender packages in the Dapper repositories are tested against Dapper not Breezy so there may be some issues.

When I tried it on my box it worked with just Blender needing to be updated. However the new Blender behaved just as badly as the old Blender (crashing gdm) so I can't say that it was successful per-se. If the old Blender works for you it might be worth a try and as long as you don't change system libraries you can always revert back to the old version easily enough.

Good Luck!

---

### Post by omenone on 2006-05-17
No dice. The list of stuff to upgrade attatched to blender was like 15 items long. I feel kind of lame knowing how easy it is to get it working under windows. I mean, I would never do it... But I know how easy it would be. Any more help?:-k

---

