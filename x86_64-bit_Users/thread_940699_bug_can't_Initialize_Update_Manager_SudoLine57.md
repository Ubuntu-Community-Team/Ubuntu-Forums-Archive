---
title: "bug can't Initialize Update Manager SudoLine57"
date: 2008-10-07
forum: x86 64-bit Users
---

### Post by ken78724 on 2008-10-07
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.
Please report this bug against the 'update-manager' package and include the following error message:
'E:Type 'sudo' is not known on line 57 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

for this, kindly treat me as a beginner. given multiple steps in one I make big mistakes. thanks.

Note, mine is a Mirus PC P5GC-MX with a 750 gig HD; installed 8.04-desktop-amd64.iso several weeks back. the unresolvable problem appears to prevent routine downloads of add-on programs I wish to use with my work. 

Once am able to move ahead want to do video editing/production work in addition to authoring. Thanks again.

---

### Post by cariboo on 2008-10-07
The message pretty well tells you what is wrong, to repair the problem press Alt-F2 and type:

```
gksu gedit /etc/apt/sources.list
```

Enter your password when prompted.

This will open the file /etc/apt/sources.list in a text editor as root

Next enable line numbering in the text editor by going to Edit-->Preferences-->View and check the line number box.

Scroll down to line 57 and completely remove the line.

Save the file and close the text editor.  Go to System-->Administration-->Synaptic Package Manager and click the Reload button. You should now be able to download packages again.

While you have Synaptic open go to Edit-->Mark Packages By Task, a window will pop up, just scroll down to Video Creation And Editing Suite and mark it for installation, this should install most of the programs you need for what you want to do.

Jim

---

### Post by ken78724 on 2008-10-07
Thanks Jim! Wish I could print these instructions. With the debate on tonight, I will be back at this in the morning. Warm regards.
Ken

---

### Post by ken78724 on 2008-10-08
Jim, believe I've followed instructions related to update manager. Thanks. But, the sound feature which I hear at login does not work for youtube; plus CNR.com downloads like flash 9, cinelarra, opera, Adobe Acrobat Reader, do not install. Have not sent a bug report in accord with a announcement for AMD 64 bit systems. Sure would like these capacities. Will log off and reboot to see if that may facilitate a correction.

Many thanks.

---

### Post by ken78724 on 2008-10-09
by activating Ubuntu options this overcame the lack of sound. Thanks to I presume ubuntu developers I enjoyed a youtube tonight. there's on my list to be solved. Guess it requires to keep plugging one by one. Warm regards.

---

