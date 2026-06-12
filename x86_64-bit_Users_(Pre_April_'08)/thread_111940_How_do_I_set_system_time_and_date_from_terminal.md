---
title: "How do I set system time and date from terminal?"
date: 2006-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by gdgardnerw on 2006-01-03
I unplugged the old iMac and the battery is dead. I went to reboot Ubuntu and the gnome desktop would not come up. I believe it is a system date/time issue. How does one reset the system date/time from the monitor or terminal mode?:???:

---

### Post by ibook-linux on 2006-01-03
easy fix
you can do that by typing in the following format:

date mmddHHMMYYyy

so
date 121520152005
Dec 15 8:15 2005

or date 010309392006
Jan 3 9:39 2006

Yes for some reason debian and ubuntu are very date sensitive. Even apt-get will not work if you have the incorrect date.

---

### Post by gdgardnerw on 2006-01-03
Thank you, ibook-linux, for that help. I got the date and time reset. That's the good news.:smile: 

The bad news is, I still get a brown screen! What else do I need to do to get GNOME up and running again?](*,)

---

### Post by ibook-linux on 2006-01-03
hmmmm the date and time should have fixed it. Not sure why you are still getting a blank screen.

Try the usual apt-get update, apt-get upgrade and see if that helps. I have fixed a lot of issues by a simple update when it really shouldn't have anything to do with it.

If that doesn't work try reinstalling gnome.
apt-get install ubuntu-desktop

you might have to uninstall gnome first then reinstall. Or try KDE or XFCE4 and see if that works.
apt-get install kubuntu-desktop
apt-get install xubuntu-desktop

as a last ditch effort try resetting xorg
dpkg-reconfigure xserver-xorg

it should auto detect everything and all you should have to do is answear yes to everything.

Try all that and if none of those work let us know. Maybe someone else has some ideas.

---

### Post by gdgardnerw on 2006-01-03
When I try to update / upgrade, I get 

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock administration directory (/var/lib/dpkg/), are you root?

I should be root. I type su and put in my password with which I sign on ubuntu and it indicates Authorization failure. I don't understand this. How could it be that I am not root?:(

dpkg-reconfigure xserver-xorg  says I can only run this as root.  I am the one who configured and installed ubuntu. How could it be that I am not root?

And now I see that it is not letting me change the system date and time per the same issue, I imagine.

---

### Post by ibook-linux on 2006-01-03
wow, hmmm
Try using sudo command before apt-get and then type in your admin password when it asks for it. See what that does.

---

### Post by gdgardnerw on 2006-01-03
:) You are a genious! The sudo before the date and update allowed me to do all! It is now up and running! 

Thank you very much!

---

### Post by ibook-linux on 2006-01-03
AWESOME! Glad it worked.

Yes I ran into many of the same issues when I first tried linux through a straight debian woody distro. For some reason my computer thought it was 1937 and refused to do anything.

You proabably had some dependency issues that was gumming up the works. When ever I run into something screwy I always run the update first and see if that fixes it. Usually it does but I have no idea why it does because it really shouldn't. I guess it is the linux equivalent of kicking it. lol

Glad everything now works for you. :p

---

