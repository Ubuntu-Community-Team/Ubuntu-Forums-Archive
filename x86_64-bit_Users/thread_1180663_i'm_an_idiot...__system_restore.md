---
title: "i'm an idiot...  system restore?"
date: 2009-06-07
forum: x86 64-bit Users
---

### Post by interceptorV8 on 2009-06-07
i'm wondering what i should do - or if i should do anything at all.   

i'd like to know if there is a non destructive way of doing some form of system restore to 9.04 without losing everything.  

the mess started when for some reason, the 'program files' folder in my windows vista partition just went missing one day....  maybe deleted by accident from ubuntu or something...   i don't use windows that often, but every now and then i switch back for an hour or two so i thought i'd do a simple restore to vista (which wasn't "simple" at all) and then restore ubuntu's grub menu and get back to normal.  well the IDIOT i am forgot to take into consideration that the 9.04 LIVE cd i downloaded and installed is the 64 bit version.  the version that was shipped to me, which i decided to use JUST because it was "official" was the 32 bit version...     i didn't realize this until i was already up and running ubuntu and went to download some deb packages and the 64 bit packages wouldn't download.  i was PISSED...  didn't lose any data, but i had to go through the process again and re-download all of my programs and get compiz back to where i wanted it.   

so it's running just OKAY now.  ever since i messed with it though i've noticed some reoccuring problems such as:

after i log in, i get a curiously long black screen... lasts longer than it used to

some programs have been MORE glitchy than normal (pidgin keeps getting disconnected and crashes...  PLUS i can't seem to install the latest deb package of pidgin either - but i had it before the mess started)

deluge crashes when i make a new torrent file sometimes...  but i understand deluge to be somewhat unstable to begin with.

i downloaded gnu sound to test it out - as soon as i click on the icon/launcher - the machine logs me out...  uninstalled that little ******* immediately.

before i messed with the system...  9.04 was running great for the most part...  i'm worried i messed it up...    i'd like to restore the system somehow w/o losing data.

---

### Post by ddales on 2009-06-07
You're stuck with 32bit without a complete new re-install.  There is no upgrade path from 32 to 64 bit.  There is also no system recovery scheme per se.

What I use just in case:

1. rsync all my important stuff to an external USB Drive nightly
2. get a copy of clonezilla and make images to store in a safe place.  clonezilla is not system specific, you can image just about any OS
3. use Dropbox for encrypted offsite storage
4. once a month I create archive DVDs of important stuff like documents and photos

---

### Post by bford16 on 2009-06-07
While there is no 'system restore' with a default Linux install, you *can* reinstall Ubuntu without losing data, provided you had set up a separate partition for the /home folder.  You can do this during the install procedure by choosing the option to manually partition the drive. You should set up a small "swap" partitiion (mine is 2GB), a root partitiion "/" (I used 10GB), and the balance of space for "/home."  Then, if you decide to reinstall from the Live CD, you just reformat "/," and leave the rest alone.  This will allow you to reinstall without losing data.

---

