---
title: "Assign 'open with ___' to files made by apps launched by scripts?"
date: 2008-09-03
forum: x86 64-bit Users
---

### Post by dai_vernon on 2008-09-03
For example, to launch Maple 11, I need to run a script called launch_maple that does a command or two.  I can set the .mw files that Maple uses to launch the launch_maple script, but then they just launch the program, not launch the program and open in the program.

How do I pass file locations to programs that launch via user created script?

---

### Post by Kilz on 2008-09-03
> **dai_vernon said:**
> For example, to launch Maple 11, I need to run a script called launch_maple that does a command or two.  I can set the .mw files that Maple uses to launch the launch_maple script, but then they just launch the program, not launch the program and open in the program.

How do I pass file locations to programs that launch via user created script?

An example in a shell script.

gedit /path/to/some/text/file 

This will open a specified txt file in gedit.

---

### Post by dai_vernon on 2008-09-03
No, that's not the situation.  The command to launch maple isn't simply maple.  I need to say '/home/taylorh/Documents/launch_maple' because of other things that need to happen before launch.  And even then, saying that command followed by a path to the file does nothing extra.

How can I pass the argument to the program?

---

### Post by brainspank on 2008-09-06
I'm not a gnome user, but I found this w/ google:

> I went through all the Gnome settings, Nautilus preferences, until I finally discovered: application preferences are changed by right-clicking on the file in question, selecting properties, and going to the Open With tab, then selecting the application you want to use.

you should be able to choose your script.  you will probably pass it %u, or whatever gnome uses to specify application arguments.  look at other app launches to see syntax for example.

---

