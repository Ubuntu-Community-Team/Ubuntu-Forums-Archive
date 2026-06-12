---
title: "Open Office failure down to 64/32 bit issue?"
date: 2006-06-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by mikecalder on 2006-06-11
... or is it an accessibility thing?

Open Office fails to start on my system - AMD64 with completely updated 6.06.

If I try to start ooffice in a terminal I get the messages:

Gtk-Message: Failed to load module "gail": libgailutil.so.17: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "atk-bridge": libspi.so.0: cannot open shared object file: No such file or directory

followed by a lot of other stuff.

These libraries seem to be the accessibility libraries - in a fit of curiosity the other day I tried to install these to get a screen magnifier, and nothing much happened so I went on to more pressing matters.

I've checked /usr/lib/gtk2.0/modules, and they seem to be there, so I wondered if it was a 32/64 bit thing, so got the 32 bit libraries and put them in /usr/lib32/gtk2.0/modules, but that didn't improve matters.

I did a search, and found one other person who seemed to have a similar problem, but theirs went away after reinstalling open office.  I tried that, but it didn't help.

Has anyone got any idea what I could do?

---

### Post by mikecalder on 2006-06-11
OK. Isn't it embarrassing when the first thing you try after posting in public fixes the issue?

In my case, the fix was to first remove, then re-install, ia32-libs-gtk, thusly:

sudo apt-get remove ia32-libs-gtk

sudo apt-get install ia32-libs-gtk

The remove step was nrecessary, because just doing the install resulted in a message that the installed version was the most up to date one.

I surmise that the libs got borked when I tried to install the Accessibility options, but the package database thought they were still OK.

Goes like a train, now.  Very Impressive, compared to the same program under KDE on Suse 10.0.

---

### Post by fluffington on 2006-06-11
[QUOTE=mikecalder]In my case, the fix was to first remove, then re-install, ia32-libs-gtk, thusly:

sudo apt-get remove ia32-libs-gtk

sudo apt-get install ia32-libs-gtk

The remove step was nrecessary, because just doing the install resulted in a message that the installed version was the most up to date one.[/QUOTE]

You can also reinstall a package with the reinstall option:

```
sudo apt-get --reinstall install ia32-libs-gtk
```

---

### Post by Kango_V on 2006-06-14
Reinstalling ia32-libs-gtk did not help here.

Uninstalling openoffice.org-gnome and openoffice.org-gtk enables openoffice to run, but without the nice gnome dialogs.

Anyone know how to solve this.

btw, if i wipe my home dir completely, log on and then run openoffice, all works ok (even with the above two packages installed).  There must be some setting stuck somewhare.

---

### Post by fragos on 2006-06-14
Many applications save configuration and user files in your /home/{user} directory as hidden files and directories whose names start with "." (period).  The latest Open Office uses .openoffice.org2 for the directory name.  You can see these files with ls -a on the command or with show hidden fils in Nautilus.  These files are created the first time an application is run.  If these hidden files become corrupted they can be deleted and new one will automatically be created.  You will of course loose all user configuration.

---

### Post by GOwin on 2006-06-15
I experienced the same problem with OOo but I haven't bothered fixing it yet. Will try the suggestions later.

I found it weird that I can't launch OOo using my account but it works with my other accounts in the computer.

I remember trying to run the accessibility/magnifier the other day, which wasn't successful. I don't remember if my OOo problem happpened after that.

---

### Post by kingmonkey on 2006-06-15
[QUOTE=mikecalder]
In my case, the fix was to first remove, then re-install, ia32-libs-gtk, thusly:

sudo apt-get remove ia32-libs-gtk

sudo apt-get install ia32-libs-gtk
[/QUOTE]

This didnt work for me neither. Been bugging me for some time, thought it would fix itself going to investigate the .ooffice option now. Will report back.

EDIT:

No luck with the ~/.openoffice.org2/ files. I did notice that if I removed ~/.openoffice.org2/user/config/javasettings_linux_x86.xml then instead of the splash screen popping up and closing down it just stayed there using a lot of CPU untill I closed it. If that file is renamed then it creates a new one:

Contents of old/original file:

```
<?xml version="1.0" encoding="UTF-8"?>
<!--This is a generated file. Do not alter this file!-->
<java xmlns="http://openoffice.org/2004/java/framework/1.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
<enabled xsi:nil="true"/>
<userClassPath xsi:nil="true"/>
<vmParameters xsi:nil="true"/>
<jreLocations xsi:nil="true"/>
<javaInfo xsi:nil="false" vendorUpdate="2004-01-30" autoSelect="true">
<vendor>Free Software Foundation, Inc.</vendor>
<location>file:///usr</location>
<version>1.4.2</version>
<features>0</features>
<requirements>0</requirements>
<vendorData>660069006C0065003A002F002F002F007500730072002F006C0069006200330032002F006C0069006200670063006A002E0073006F002E003600</vendorData>
</javaInfo>
</java>
```

And contents of newly generated file:

```
<?xml version="1.0" encoding="UTF-8"?>
<!--This is a generated file. Do not alter this file!-->
<java xmlns="http://openoffice.org/2004/java/framework/1.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
<enabled xsi:nil="true"></enabled>
<userClassPath xsi:nil="true"></userClassPath>
<vmParameters xsi:nil="true"></vmParameters>
<jreLocations xsi:nil="true"></jreLocations>
<javaInfo xsi:nil="true"></javaInfo>
</java>
```

Also this is the error I get when I start ooffice with openoffice.org-gnome + gtk installed using my original file:

```
$ ooffice
Gtk-Message: Failed to load module "gail": libgail.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "atk-bridge": libspi.so.0: cannot open shared object file: No such file or directory


Fatal exception: Signal 11
Stack:
/usr/lib/openoffice/program/libuno_sal.so.3[0x55e5c51f]
/usr/lib/openoffice/program/libuno_sal.so.3[0x55e5c83f]
/usr/lib/openoffice/program/libuno_sal.so.3[0x55e5c8dd]
[0xffffe500]
/lib32/libc.so.6(vsscanf+0x6d)[0x564f707d]
/lib32/libc.so.6(sscanf+0x2b)[0x564f1e7b]
/usr/lib/openoffice/program/libvclplug_gtk680li.so(_Z13InitAtkBridgev+0x35)[0x592f8fdd]
/usr/lib/openoffice/program/libvclplug_gtk680li.so(create_SalInstance+0x19d)[0x592f7341]
/usr/lib/openoffice/program/libvcl680li.so[0x55791369]
/usr/lib/openoffice/program/libvcl680li.so[0x5579146a]
/usr/lib/openoffice/program/libvcl680li.so(_Z7InitVCLRKN3com3sun4star3uno9ReferenceINS1_4lang20XMultiServiceFactoryEEE+0xb7)[0x555f4ad3]/usr/lib/openoffice/program/libvcl680li.so[0x555f4c31]
/usr/lib/openoffice/program/libvcl680li.so(_Z6SVMainv+0x29)[0x555f4cf9]
/usr/lib/openoffice/program/soffice.bin(sal_main+0x47)[0x80646db]
/lib32/libc.so.6(__libc_start_main+0xd2)[0x564b4ea2]
/usr/lib/openoffice/program/soffice.bin(_ZN6Window11RequestHelpERK9HelpEvent+0x31)[0x8064615]
/usr/lib/openoffice/program/soffice: line 233: 13279 Aborted                 "$sd_prog/$sd_binary" "$@"

```

I have no idea whats going on here. I think its something to do with a temp path workaround thing.

---

### Post by dpmillerau on 2006-06-26
I fixed my OO2 install by removing openoffice,org-gnome & openoffice.org-gtk

I actually removed all the openoffice pacakages and then installed the basics - it worked, then I added these and it didn't. Had upgraded from 5.04 via 6.10.

---

### Post by ruudiculus on 2006-09-06
**dpmillerau**, you're totally right! It runs again! With progress bar on the splashscreen. Thanks a lot!

---

### Post by ravikm on 2006-09-12
> **dpmillerau said:**
> I fixed my OO2 install by removing openoffice,org-gnome & openoffice.org-gtk

I actually removed all the openoffice pacakages and then installed the basics - it worked, then I added these and it didn't. Had upgraded from 5.04 via 6.10.

i used;
sudo apt-get remove openoffice.org-gnome openoffice.org-gtk

now open office works.....

thanks,
ravi.

---

### Post by kellykamay on 2006-09-22
here's what i did, by using synaptic package manager i search all openoffice.org and openoffice.org2 files(and other files such openoffice.org-writer,openoffice.org-base etc..) and mark them as complete removal..then apply

after that i erased my .openoffice.org2/ directory with rm -rf

then a fresh new install $ sudo apt-get install openoffice.org2

and viola!!! its working now..

---

