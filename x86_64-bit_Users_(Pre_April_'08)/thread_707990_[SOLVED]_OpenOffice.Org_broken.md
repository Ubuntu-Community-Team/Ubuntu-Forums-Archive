---
title: "[SOLVED] OpenOffice.Org broken"
date: 2008-02-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Pyre_Vulpimorph on 2008-02-25
OK, something is wrong.  My entire OpenOffice suite seems to have broken.  None of the applications, not word processor, spreadsheet, or even drawing will launch. I don't get so much as a splash screen to indicate a load attempt.  It all worked until about 4 days ago. There have been no updates via Synaptic for at least two weeks, so a corrupted update shouldn't be the the culprit.  I never saved anything, so I can't just click on a saved file to test it that way.

(why does it work fine until I actually need it? *grumble, grumble*)

I'm not mad, just surprised that it has suddenly stopped working properly.

---

### Post by prince_niceguy on 2008-02-25
type the following command in the terminal to get some details out.

```
oowriter
```

if there is error it will give some outputs in the terminal.

---

### Post by Pyre_Vulpimorph on 2008-02-25
*Error forking '/usr/lib/openoffice/program//soffice': 'Failed to execute child process "/usr/lib/openoffice/program/soffice" (Bad address)'*

How can I fix this?

---

### Post by prince_niceguy on 2008-02-25
have you tried reinstalling open office? try doing the same from synaptic.. see if it works...

---

### Post by Hagar Delest on 2008-02-26
Rename your OOo user profile (~/.openoffice.org2).

---

### Post by Pyre_Vulpimorph on 2008-02-27
Could you guide me through that?

(low bean count = NOOB)

Thanks in advance.

---

### Post by prince_niceguy on 2008-02-27
open nautilus.

press ctrl + h to see hidden files.

now you will see a folder .openoffice.org2. Rename it to .openoffice.org2.bak

now start open office and see if it works.

---

### Post by Pyre_Vulpimorph on 2008-02-27
Changing the folder's name to ".openoffice.org2.bak" didn't do anything.  I still get:

***Error forking '/usr/lib/openoffice/program//soffice': 'Failed to execute child process "/usr/lib/openoffice/program/soffice" (Bad address)'***

Curiously, if I open the file browser and manually travel to: **/usr/lib/openoffice/program/soffice** , I can open the OpenOffice suite by clicking on "soffice" and clicking "RUN".  Now, as long as this one program is running, all my problems disappear.  Typing "oowriter" into the terminal immediately opens a new OpenOffice app window, as does going through (Applications-->Office-->OpenOffice.org).

But as soon as I close all office windows, my problems return!  Typing "oowriter" in the terminal will get me the same error message, and going through the application menu gets me nothing at all.

Note:  after looking back into the file browser, ".openoffice.org2" and ".openoffice.org2.bak" now appear side-by-side.

---

### Post by Hagar Delest on 2008-02-28
Then it means that the problem is not with the configuration files. You can delete the newly created OOo user profile and rename the .bak one to get back your profile.

You could try to install the official version of OOo : [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by Jouke74 on 2008-02-28
I would indeed first try to reinstall OpenOffice with Synaptic.
Just open synaptic, look for all Openoffice packagages. 
Select the ones that are green with a right-click and click on re-install.

---

### Post by Pyre_Vulpimorph on 2008-02-28
*sigh*

OK, I used Synaptic and re-installed everything that even remotely mentioned OpenOffice.

I still get the Fork of Error.  :?

*Error forking '/usr/lib/openoffice/program//soffice': 'Failed to execute child process "/usr/lib/openoffice/program/soffice" (Bad address)'*

What I want want to know, is what on earth corrupted my installation in the first place!?

](*,)

---

### Post by Hagar Delest on 2008-02-29
Don't know, that's why the best solution IMHO is to install the official version.

---

### Post by djtm on 2008-03-06
**This post could be related to an Ubuntu bug filed at**: https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/187407 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hey,

not a big help, but this is a known issue of the current version of openoffice.org, see
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/187407](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/187407) for ubuntu
and [http://people.debian.org/~terpstra/message/20080223.203905.f65769c7.en.html](http://people.debian.org/~terpstra/message/20080223.203905.f65769c7.en.html) for debian

What you can do is upgrade the version of openoffice to the current version of hary.
This is really not trivial though:

As superuser you create a new file called
/etc/apt/sources.list.d/hardy.list

and put a line in it:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

than save.

Then you update the available packages in the package manager and install the new openoffice version. 
Then, important, remove the file 
/etc/apt/sources.list.d/hardy.list again and update the list of available packages again.

Then it should work. You may have to update only the package openoffice.org-base,
but several packages might be uninstalled in the process, so first check what packages are removed.

Hope you've got a good network connection where you are.

And good luck!

And I'm sorry but I cannot help more atm, maybe someone can explain the steps in more detail, if neccessary.

---

### Post by djtm on 2008-03-06
I found an even better solution.

As superuser edit the file
/usr/bin/ooffice

so that it looks like this:

```
#!/bin/sh
export OOO_EXTRA_ARG=''
#/usr/lib/openoffice/program/ooqstart  "$@"
/usr/lib/openoffice/program/soffice "$@"
```



works great for me.

---

### Post by simoncullen on 2008-04-10
Me too!  Thanks.

> **djtm said:**
> I found an even better solution.

As superuser edit the file
/usr/bin/ooffice

so that it looks like this:

```
#!/bin/sh
export OOO_EXTRA_ARG=''
#/usr/lib/openoffice/program/ooqstart  "$@"
/usr/lib/openoffice/program/soffice "$@"
```



works great for me.

---

### Post by Pyre_Vulpimorph on 2008-04-11
Yippeee !!

Thank You, DJTM, for that fix.  It all works fine now.


:popcorn:

---

