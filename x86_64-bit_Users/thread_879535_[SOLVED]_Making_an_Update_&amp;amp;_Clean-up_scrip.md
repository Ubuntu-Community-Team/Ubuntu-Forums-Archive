---
title: "[SOLVED] Making an Update &amp;amp; Clean-up script on the panel"
date: 2008-08-04
forum: x86 64-bit Users
---

### Post by alt3rn1ty on 2008-08-04
Hello, on windows I have become very reliant on CCleaner to sweep the system once in a while, and I want to make a script which I can run once a blue moon on linux to do several maintainance tasks all in one, But, also want to make an icon for it which can be assigned to the panel. So basicly you click the panel icon and the script executes all commands therein in turn (batch file in dos, not sure how you refer to this in linux). Typically I am looking at the following collection of commands (But knowing this is an update and clean-up script if you have any additional suggestions for inclusion I would very much appreciate those too. 

sudo apt-get update && sudo apt-get upgrade
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo deborphan | xargs sudo apt-get -y remove –purge
  # I think I need to install this first with sudo apt-get install deborphan

Also are there any potential dangers to doing an update/clean out this way?

Edit: And to comment on particular lines for future reference in linux scripts do we use the # symbol?

And and and.... lol, can the whole script be made to run quiet, although I doubt this because It will prompt me for a password for sudo

---

### Post by alt3rn1ty on 2008-08-04
Sorry folks I found my own answers to this one, remembered I had some old unix pdf's in my windows archives (knew they would come in handy one day), and with a bit more searching found I needed to just use a text editor to create the content, then chmod 777 filename

#!/bin/sh
echo &#8220;Updating and cleaning system&#8221;
sudo apt-get update && sudo apt-get upgrade
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo deborphan | xargs sudo apt-get -y remove &#8211;purge
echo "All done, exiting"
exit

Then just right click panel and add to panel custom application launcher, the executeable script, runs in terminal, and add my own icon.

Job solved I think, unless anyone sees anything potentially screwed up there (think I had better leave this a day at least for someone to say 'yep looks okay here')

---

### Post by alt3rn1ty on 2008-08-07
:)Well I think I can safely mark this solved with no further suggestion for improvements.

---

