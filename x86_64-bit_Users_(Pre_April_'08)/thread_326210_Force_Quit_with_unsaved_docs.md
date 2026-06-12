---
title: "Force Quit with unsaved docs"
date: 2006-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Unterseeboot_234 on 2006-12-27
Finally got the install of ubuntu the way I want it. Everything works great except for when I try to close any window that has multiple docs. Example is Text Editor that has one unsaved text doc and a couple of other saved docs. If I click the Close Window [X], I get the normal warning: "You have "Untitled" not saved yet". Do you want to continue? [Yes] [No]. Before I can select either button, that dialog gets covered up by: "The Program is not responding. Do you want to Force Quit? [Force Quit] [Cancel]. If I don't hit that Cancel button fast on Force Quit, the underlying program will quit without giving me an opportunity to Save and exit gracefully.

This only happens with multiple tabs in Swiftfox or any of the windows with tabs across the menu bar, such as the Text Editor. I didn't have this before. Is there anything I can tweak?

thanks, all of you on the unbuntu forum, you were a big help getting my distro up to this point.

---

### Post by AgenT on 2006-12-29
> **Unterseeboot_234 said:**
> Finally got the install of ubuntu the way I want it. Everything works great except for when I try to close any window that has multiple docs. Example is Text Editor that has one unsaved text doc and a couple of other saved docs. If I click the Close Window [X], I get the normal warning: "You have "Untitled" not saved yet". Do you want to continue? [Yes] [No]. Before I can select either button, that dialog gets covered up by: "The Program is not responding. Do you want to Force Quit? [Force Quit] [Cancel]. If I don't hit that Cancel button fast on Force Quit, the underlying program will quit without giving me an opportunity to Save and exit gracefully.

This only happens with multiple tabs in Swiftfox or any of the windows with tabs across the menu bar, such as the Text Editor. I didn't have this before. Is there anything I can tweak?

thanks, all of you on the unbuntu forum, you were a big help getting my distro up to this point.What you may want to do is take out your LiveCD and boot it up. See if those problems still exist when you are in the LiveCD environment. If not, it may be best for you to do a reinstall of Ubuntu. It is definitely not necessary to fix your problem, but it may be easiest for you. Then again, the problem may have been with the install procedure and you may just end up with the exact same problem after a reinstall. But this does sound like you interrupted, quit or custom misconfigured the install procedure.

It may just be that one program is causing this. You can try debugging by reading the output of:
```
 dmesg
ps -ef
top (press q to quit top)
```top is useful to see in real time your CPU and memory usage. See if it spikes up when you are using a certain program.

> **Unterseeboot_234 said:**
> Is it Gnome or is it X11 that makes the dialog boxes and the multi-tab buttons in a document window? I have "fixed" a thing or two in ubuntu by doing a Synaptic re-install package.Sounds like your problem was badly installed packages or dependency problems. Strange. I do not know more about your story but can say that I never had such problems and I have upgraded and downgraded distributions for years (without doing a fresh install!).

As per your question: the answer is much more complicated than you probably expect. To sum up as quickly as possible: it depends on the program. X11 is always running the show and GNOME is just a name for the Desktop Environment which is nothing more than a collection of programs including a "themer" to make everything look coherent. Your Window Manager (GNOME uses Metacity) is what manages, creates, quits, etc. your windowed programs. As the title suggests, a window manager's job is just to manage the windows, not to draw or "create" them. The GUI toolkit is what is used to create the windows. GNOME programs usually use GTK (note that there are two major version of GTK, the old one and the newer one) so technically GTK is responsible for drawing all those widgets such as the OK dialogs, text input fields, etc. This assumes that your program uses GTK. There are a ton of toolkits.

Make a more detailed list of the programs you are having trouble with and find out what toolkits they use. Be warned: some programs actually have multiple versions of the same program that use different toolkits (for intergration reasons). For example, AbiWord has it's normal version (not sure what toolkit that is) and a GTK version called AbiWord-GNOME.

When people say GNU/Linux has freedom of choice, they really mean it.

---

### Post by rajeev1204 on 2006-12-29
hi

its a bug

i have that too

it seems to disappear after some time

really annoying !!

---

### Post by Unterseeboot_234 on 2006-12-29
OK then. I am going to live with this annoyance and maybe it will go away. I just need to know how to find what packages a program uses. I haven't yet read up on how to do that from all the documentation available. 

I suspect my annoyance has to do with Debian Menu. I found this hack on the forums to get Debian Menu functional ...

```
sudo apt-get install --reinstall menu

update-menus

sudo apt-get install --reinstall menu-xdg

update-menus
```

Debian Menu showed up. And then later, I had a one-time Dialog telling me Gnome had crashed, did I want to send a bug report? Sure. I click through the Next buttons until it asked me the Name of the program that crashed. Do What??? That's your job, isn't it???? (talking to the Dialog Box).

---

### Post by rajeev1204 on 2006-12-29
hi

yes i agree . the bug report should be automated . iam a newbie so i dont know what and why  it crashes . Isnt the bug tool supposed to do that ,instead it needs a detailed report . If i knew that would i file a bug report ?!

D'OH !

---

### Post by AgenT on 2006-12-29
To search for the package that has X file in it, use dpkg-query:
```
dpkg-query -S filename
```Where filename is the file you want to search for.
For more information:
```
man dpkg-query
```Ubuntu bugs should be reported in [Launchpad]("https://launchpad.net/distros/ubuntu/+bugs"). Please note that how fast the bug is fixed usually depends on how good the bug report is. Write a bad bug report and you can expect it to stay in the system for years. The reason is simple: developers need to be able to 1) understand exactly and in detail what the problem is and 2) need to reproduce the problem.

---

### Post by Unterseeboot_234 on 2006-12-31
Submitted a bug report. LiveCD 32-bit does not have this behavior. LiveCD-64 does have. My argument is: Force Quit should run as its own daemeon after all else fails.

---

