---
title: "Add 32 bit CUPS to print from Crossover"
date: 2007-08-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by ianmidd on 2007-08-22
I'm running 64-bit Feisty.

I'm using Crossover 6.1 to run Outlook 2003 to connect to our Exchange server.

Outlook works fine, but when I try to print, my only options are KDE print system and Wine Postscript Driver.  

I found a few tickets on the Crossover site that say Crossover requires the 32 bit cups libraries to print.

I have done quite a bit of searching but I can't find a way to install the 32-bit CUPS libraries.

Can anyone lead me in the right direction?

---

### Post by Kilz on 2007-08-22
This is an advanced topic, I will give an alternative at the end in case this looks like its to difficult for you.

First off a warning in case anyone suggest to just force in the package. Never ever,ever,ever force in libraries. They will overwrite the existing 64bit libraries that you need. Forcing applications is ok, but never libraries.
Ok, the short explanation. You will have to manually extract the files and add them to the correct location. This will be easier if you use nautilus in admin mode. So to start, open a terminal and type in ```
gksudo nautilus
```
Be very careful what you do because you may end up fubaring Ubuntu if you delete the wrong files.
[Go here to get the packages]("http://packages.ubuntu.com/"), but to save time , here is a link to [some of the cups libraries]("http://packages.ubuntu.com/feisty/libs/libcupsys2"). There are [a lot of them]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=cups&searchon=names&subword=1&version=feisty&release=all"). You will download the i386 or 32bit package.
What you are going to do is extract the internal file system in the deb
```
sudo dpkg -x somefile.deb
``` Then go in and copy the files in the /usr/lib of that extracted file system and copy then to the /usr/lib32 in your file system. You can drag an drop them in the nautilus in admin mode.
You are going to have to do it for that package and all required packages. You may need to do this for quite a lot of packages.

The alternative, 
Save the files as a postcript file or other file, then open it in a 64bit version and print them out from there. That or dont use 32bit office applications from the start.

---

### Post by ianmidd on 2007-08-23
Great! 

I'll give this a try as soon as I get a chance.

I am currently printing to PS from MS office and then printing the document.  I just figured there had to be a way to print directly.

The only 32-bit app I really use with crossover is Outlook 2003 to connect to our Exchange server.  I have given Evolution many honest trys but I don't think it's quite there yet as far as exchange connectivity goes.  It's too bad because I'd really like to use it instead.

I'm the sysadmin for our company with a lot of "less advanced" users who would find it diffucult to use anything other than Windows/Office, otherwise we would be running Linux almost everywhere.

I've already converted most of our desktop PC to linux thin clients using ThinStation to connect to our MS Terminal Server and I'm using IPCop for one of our routers.

I wouldn't call myself a Linux guru but I'm far from a noob.

---

### Post by Kilz on 2007-08-23
What do you think Evolution needs to be ready? Are those your needs as an advanced user, or the needs of the less advanced users? Have you made those needs known to the people working on it?

---

### Post by ianmidd on 2007-08-23
> **Kilz said:**
> What do you think Evolution needs to be ready? Are those your needs as an advanced user, or the needs of the less advanced users? Have you made those needs known to the people working on it?

They are mostly known from what I can find, and they are for our less advanced users.  

I *can* use it on a daily basis, but the formating it applied to replies, fwd's etc. look different, so I always get asked why mine always looks different.

Some others (maybe you can help with some of these?):

- It can be quite slow to display folder contents in a mailbox.  I know it's because it interfaces with OWA and not native exchange MAPI.  (I'm hoping the "agreement" between Novell and MS will bring improved inter-operability).  

- HTML Font rendering between Evolution and Outlook is hit and miss.  - I'd rather not use HTML fonts, but management has spent a lot of money on a branding consultant and instututed a company standard HTML signature.  It doesen't render well in evolution even though I have Windows fonts installed.

- I haven't found a good way to sync the entire mailbox for offline use.  The check box in the account setup does not do it, and it would take way too long to set the sync option for every folder in my mailbox.  - being the only IT peson at my company, I use e-mail to track support issues.  I am trying to move to a ticketing system (GLPI), but haven't had a chance to properly implement it.

- Random crashes or freezes when changing folders.  I do send the bug reports.

There are probably others I can't think of at the moment, but the last 2 are more or less related to no native MAPI support which is unfortunately out of *our* control.

---

