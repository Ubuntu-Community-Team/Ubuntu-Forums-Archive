---
title: "Why Me!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!"
date: 2008-05-13
forum: Wine
---

### Post by gaurdianAQ on 2008-05-13
I had wine up and working fine and was able to run my games then I decided to play around with settings and the last setting I changed was I made the dpi up to max to see what it would do now all the text is so huge that I cant even get down to change the setting and I cant find a text config file either why is it always me lol not to sound poor me or anything but this stuff happens a lot to me lol

---

### Post by NightwishFan on 2008-05-13
I see that sounds like an intense problem. I am not sure how to change font size, but you can use tab to guess if you are on the ok/apply buttons in winecfg, then push enter to accept.

---

### Post by gaurdianAQ on 2008-05-13
is it possible for someone to point me to a text file config at all? I tryed completly removing it which is supposed to remove config files but that didnt work maybe rebooting will work I will laugh if it did lol

---

### Post by NightwishFan on 2008-05-13
I do not use wine but I will shoot blindly to point you in the right direction. Perhaps try to enable hidden files and look in the /home/youruser/.wine folder for a config file. Rebooting may not work but perhaps purging wine and deleting the said .wine folder may work.

---

### Post by Fenris_rising on 2008-05-13
i  did that to. go to winehq support/faq. the answer is there. it requires the use of an rm command so be carefull.

---

### Post by Ripfox on 2008-05-13
Nah you don't have to rm anything from the command line.

Go to synaptic and tic "completely remove" wine then open your home folder and enable "view hidden files" and delete the .wine folder. Good to go to start over then.

---

### Post by happyhamster on 2008-05-13
No need to remove wine. Try it like this:
[http://ubuntuforums.org/showthread.php?t=733352](http://ubuntuforums.org/showthread.php?t=733352)

---

### Post by gaurdianAQ on 2008-05-13
how do I view hidden files anyways Im still a bit of a linux noob lol

---

### Post by Ripfox on 2008-05-13
> **happyhamster said:**
> No need to remove wine. Try it like this:
[http://ubuntuforums.org/showthread.php?t=733352](http://ubuntuforums.org/showthread.php?t=733352)

Nice link

---

### Post by gaurdianAQ on 2008-05-13
omg ty ty so much ty I was getting pretty anoyed lol I wish I could be that smart and here Im hoping to be a computer engineer after high school lol EDIT: woa who knew there were so many hidden folders crap thats a lot wow lol

---

### Post by situz on 2008-05-13
> **gaurdianAQ said:**
> omg ty ty so much ty I was getting pretty anoyed lol I wish I could be that smart and here Im hoping to be a computer engineer after high school lol EDIT: woa who knew there were so many hidden folders crap thats a lot wow lol

... aaaaaand breath! :lolflag:

thanks for the link btw, had the same problem :P

---

### Post by Fenris_rising on 2008-05-14
this is from the winehq site. this is how i sorted out my similar
problem. remember 'rm' is dangerous so be very careful.

2.13. How do I uninstall Wine? How do I wipe the virtual Windows installation?

You can remove your virtual Windows installation and start from scratch by eliminating (or renaming) the hidden .wine directory in your home folder, such as with rm -rf ~/.wine

If you want to remove Wine entirely after you installed it with your distribution's package manager, you can generally uninstall in the same way. Note, however, that uninstalling Wine will not eliminate the virtual Windows installation - to do that you must follow the instructions above.

Since Wine is beta software, periodically we may update the default configuration generated when you first use Wine. Sometimes users have success getting an application to work by wiping (or moving) their ~/.wine folder, rerunning winecfg with the new Wine version, and reinstalling the application.

---

