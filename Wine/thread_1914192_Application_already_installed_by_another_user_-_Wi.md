---
title: "Application already installed by another user - Wine error"
date: 2012-01-23
forum: Wine
---

### Post by scotchpotch on 2012-01-23
Hi

Newbie Linux user here.

I'm running Ubuntu 10.04 Netbook on an eMachines 250 (got rid of Windows XP). 

I was trying to load the Windows application Evernote, but unfortunately I used an older version of Wine (1.2) and the installation went wrong. I could not uninstall Evernote properly, but eventually managed to clear out all the files. I uninstalled Wine 1.2, used Computer Janitor to tidy up and then installed Wine 1.3. Tried installing Evernote and got this message:

[I]Evernote was already installed by another user. Only one per-user installation is supported.
An administrator can install Evernote for everyone after the per-user installation is removed.[/I]

I am the only user, set up as the administrator, but where I think the problem lies, is when I changed my user profile from Custom to Administator, so perhaps the other mystery user was set up as Custom - unfortunately I can't change it back.

When I reinstall Wine (again) it still shows Evernote in the Configure Wine applications window, although it is uninstalled.

I take it there must be a log file on the system that needs to be amended?

Any help would be appreciated.

---

### Post by ubudog on 2012-01-24
*Thread moved to the Wine subforum.*

Best,
ubudog

---

### Post by thatguruguy on 2012-01-25
When you re-installed Wine, did you delete your .wine folder in your home directory?

---

### Post by scotchpotch on 2012-01-25
thatguruguy - it was as simple as that! Duh! :redface:

I didn't see the .wine folder in my home drive at first. Viewed hidden files and there it was.

Deleted wine, deleted wine folder, reinstalled wine, ran Evernote installation - and bingo! Evernote runs perfectly.

Many thanks!

---

