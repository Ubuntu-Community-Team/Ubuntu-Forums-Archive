---
title: "NVidia Drivers and X Server"
date: 2008-05-02
forum: x86 64-bit Users
---

### Post by ggormsen on 2008-05-02
Hello everyone.  to start I have searched for an answer before I posted.  I have just spent the last 2 hours trying different "solutions" but to no avail.  If this is in the wrong area, please don't be too harsh, as I too had a tough time trying to figure out where to put this post.  And now, after that disclaimer, here we go.

I own a PC with a NVidia 256 7600GT.  I have 2 monitors.  I just made the switch to Ubuntu 8.04 Hardy Heron from WinXP last nite and have now been a Linux operator for a grand total of 5 1/2 hours (Most of which have been revolving around me pulling my hair out).

My main monitor is on.  My second monitor, however, is not.  I messed with resolution and the little Detect Displays button. That didn't work, so I did what any WinXP user would do, I went to NVidia's website and downloaded their "nvidia-linux-x86_64-169.12-pkg2.run" file.  

I then double clicked it, but was told that didn't work, so I read a few threads until I found out that I had to allow it to work as a program, so, I right clicked, went to properties, and allowed it to open as a program.  I double clicked and it told me to sign in as root, so I read a thread that told me how to get there.  Then, I logged into root, , and double clicked it.  It said that I needed to turn off the X Server.  I read about how to do that. Type Telinit 3 into the Terminal and it will shut off the xserver.  I did and then double clicked the Nvidia file again.  It said that it still wasn't shut off.  I changed to Telinit 2.  Still nothing.  Telinit 1... I didn't know it would give me that black screen.  I typed telinit 3 and it logged me back into my admin account.  I went back into root and tried again.

If it had worked, I wouldn't be here... :)

Any positive assistance is helpful.
Thanks!

---

### Post by jrbush82 on 2008-05-03
I've always installed my NVIDIA drivers the same way on all flavors of Ubuntu, and it has always seemed to work for me.  Do the following:

1.)  Download the correct Linux drivers from the NVIDIA web site.
2.)  Press CTRL+ALT+F2
3.)  Login
4.)  Type in: "sudo su"
5.)  Type in your user password
6.)  Type in: "/etc/init.d/gdm stop"
7.)  Type in: "apt-get install build-essential"
8.)  Goto the location where you downloaded the NVIDIA driver
9.)  Type in: "sh NVIDIA_DRIVER_FILE_NAME"
10.) Go through the prompts, say no to search for kernel module... it will compile and what not.. then say yes to let it overwrite your xorg.conf file.
11.) Once the install is done, type in: "/etc/init.d/gdm start"
12.) You should see the NVIDIA logo when it starts up
13.) Now, open up a terminal within gnome (applications > accessories > terminal)
14.) Type in: "sudo nvidia-settings"
15.) Type in your password if prompted
16.) Expand the window that pops up, it always shows up as a small little box for me.. .make it as large as you can
17.) Choose the option: "X Server Display Configuration"
18.) Choose the second monitor that is disabled in the right pane, and click configure just below it
19.) Choose the TwinView option
20.) Once it is enabled, determine which monitor you would like to be your primary, choose it and then Check the box "Make this the primary display for the X screen", which is located at the bottom of the right pane.
21.) Choose Save to X Configuration File
22.) Keep the default location of /etc/X11/xorg.conf (a backup will automatically be made)
23.) Quit the application
24.) Logout (this restarts the xorg server)
25.) You now should have dual monitors, and your login screen should be on the one that you chose to be the primary), while the other is now on.

I did this from memory, so let me know if you get stumped because I forgot something.

Good luck!

---

### Post by ggormsen on 2008-05-03
That, along with this little tid bit of code...
```
sudo apt-get install envyng-gtk
```
...worked wonders.  Thank you so very much.

---

### Post by flanadr on 2008-05-03
Thanks jrbush for the very clear instructions. Although I'm only using a single monitor I followed your instructions to install the drivers. Unfortunately it didn't work for my setup. When I follow the instructions and restart the X server I end up with a very badly messed up screen (i.e. its like having double or more vision). Also I'm using the "fi" keyboard mode and it always seems to change it back to "us" mode. Any other ideas would be appreciated.

Adrian

My setup is:

Processor: AMD Athlon 64X2
Mother Board: M3N78-EMH HDMI (Nvidia GeForce 8200)
Monitor: Acer X222W 22"

---

### Post by esunday on 2008-05-03
Try using EnvyNG  - either thru Synaptic, or even better, google it and go to the developers website, I can't recall his name.  He has done all the scripts, piece of cake everytime ...

---

