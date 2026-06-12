---
title: "Wine install/run problem in Kubuntu 12.04"
date: 2013-07-04
forum: Wine
---

### Post by Peptid on 2013-07-04
Hi All,

I recently switched to Kubuntu 12.04 from Ubuntu, and now trying to install Wine. I used the command

```

sudo apt-get install wine
```


and everything went smoothly, at least as appears in konsole. Wine icons appear in kickoff, but they do not startas I click on either of them. Moreover, there is no .wine directory under /home/username, therefore I cannot install any programs at all.

What could be possibly went wrong with my installation process to cause such errors or should I do some post-install stuff?

Thank you.

---

### Post by Lightning Dragon on 2013-07-04
Hi,

Please attempt to remove/clear all the wine folders you installed. Which means purging it. I have prepared a few links to help you with that;

[http://askubuntu.com/questions/15551/how-to-remove-wine-completely](http://askubuntu.com/questions/15551/how-to-remove-wine-completely)
[http://ubuntuforums.org/showthread.php?t=1518970](http://ubuntuforums.org/showthread.php?t=1518970)
[http://forum.winehq.org/viewtopic.php?t=10322](http://forum.winehq.org/viewtopic.php?t=10322)

Then reboot and turn off the computer and do a hard reset (flip the switch and press the power button again) and then boot back into the computer. Now, assuming you haven't add the PPA, you can add the ppa through the software center by going to "software" and then add this; [I]ppa:ubuntu-wine/ppa 

[/I]Or you can do it via the terminal with the following; 

[I]sudo add-apt-repository ppa:ubuntu-wine/ppa
[/I]

Next do the following commands separately;

[I]sudo apt-get update

sudo apt-get install wine1.5[/I]

Make sure you sudo it. Next, if it appears that the *.wine* folder is not there, hold CTRL and then press H while in the HOME directory to show *hidden* folders. The *.wine* folder should be there now. 

Please report any problems.

---

### Post by Peptid on 2013-07-05
> **Lightning Dragon said:**
> Hi,

Please attempt to remove/clear all the wine folders you installed. Which means purging it. I have prepared a few links to help you with that;

[http://askubuntu.com/questions/15551/how-to-remove-wine-completely](http://askubuntu.com/questions/15551/how-to-remove-wine-completely)
[http://ubuntuforums.org/showthread.php?t=1518970](http://ubuntuforums.org/showthread.php?t=1518970)
[http://forum.winehq.org/viewtopic.php?t=10322](http://forum.winehq.org/viewtopic.php?t=10322)

Then reboot and turn off the computer and do a hard reset (flip the switch and press the power button again) and then boot back into the computer. Now, assuming you haven't add the PPA, you can add the ppa through the software center by going to "software" and then add this; [I]ppa:ubuntu-wine/ppa 

[/I]Or you can do it via the terminal with the following; 

[I]sudo add-apt-repository ppa:ubuntu-wine/ppa
[/I]

Next do the following commands separately;

[I]sudo apt-get update

sudo apt-get install wine1.5[/I]

Make sure you sudo it. Next, if it appears that the *.wine* folder is not there, hold CTRL and then press H while in the HOME directory to show *hidden* folders. The *.wine* folder should be there now. 

Please report any problems.

Hi, I followed your instructions and they worked! Thank you.

But, I need to make an addendum; .wine folder isn't created until I ran 'Configure Wine' from kickoff. Now, the folder is created and everything works OK.

---

### Post by Lightning Dragon on 2013-07-05
Hi,

I'm glad it worked out for you. I can't say that I ever heard of the folder only being creating when accessing the Configure Wine program as normally the folder is there when I install, but thanks for sharing with the thread. Could help others with the same problem. :)

---

