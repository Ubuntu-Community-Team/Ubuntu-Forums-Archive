---
title: "PlayOnLinux 64-bit problems on Ubuntu 22.04"
date: 2022-07-06
forum: Wine
---

### Post by manucontrovento on 2022-07-06
Hello everyone, I humbly ask the community for help.

I've always used the PlayOnLinux front end to install some windows applications (mostly simple apps to configure audio devices, midi keyboards, etc....) and I've never had any particular problems.

The problems started with Ubuntu 22.04... in fact, until Ubuntu 20.04 (my previous installed os) everything was fine. Now I'm no longer allowed to create Wine drives for 64 bit apps!!! while I can create 32 bit drives normally.

The problem is that one of the apps I have to use (and which I was therefore able to install before the switch to 22.04) needs a 64-bit system...

The error that is displayed (at the 32 or 64 bit selection switch) is:

[B]Error in POL_Wine
It seems that Wine has crashed

If your application is still open, ignore this message.[/B]

(translation could not have an exact match, since my os is in italian and I see the error message in italian)

I've tried searching forums, articles etc but haven't found the problem described or solved anywhere... does anyone have any ideas?

Thanks!!!

---

### Post by Claus7 on 2022-07-06
Hello,

this error erupts from time to time. If, as the error says, things are working normally, then ignore it. Have you tried to see if things are working, without taking any notice of the message?
Could you please write the steps taken in order to create these drives?
e.g.:
1) Tools->Manage Wine versions
2) pick up amd64
3) wait a little until versions are displayed
4) install the desired version
5) then go to Configure->new->next->64bits windows installation
6) pick up the previously installed wine version
7) write a name
8) wait ... wait while drive is being created...
9) done
10) choose from the PlayOnLinux window the 64bit drive just created and install the programs you wish.

I would suggest you to remove playonlinux completely and start anew. During the steps described above I faced no issue. Check also another 64bit wine version. Just some ideas.
ah! and welcome to the forums!

Regards!

---

### Post by manucontrovento on 2022-07-07
Hello @Claus7 and thanks for your reply.
Yes, I already verified that I really need a 64 bit instance and on a 32 bit one , the application won't work.

The procedure i follow is very simple:

- I start PlayOnLinux (version is 4.3.4, up to date with ubuntu 22.04 repos)
- I click on Install new application
- I click on Install a application not present in the list
- the wizard window for new application installation is shown on screen. I click Next
- I select Install application in a new virtual device and click Next
- I enter a custom application name and click next
- I don't select any option and click next
- I select 64 bit windows installation and click next

and then the error is displayed.

---

### Post by Claus7 on 2022-07-07
Hello,

I repeated the steps you followed and I do not get any errors. I would advice you to follow my guidelines above, by choosing a specific  64bit version of wine that you think that will best fit your needs (usually the latest), because that way it might choose a wine version that has problems in your system and you could circumvent this.

In order to track down better the error, you could open playonlinux using a terminal and watch side by side the error message displayed there. It might be more verbal in order for you to track down the issue.

If you have not installed any applications, I would advice you to delete the .wine folder under your home directory, yet you will have to be cautious because, if you do so, anything installed will be lost. Use this as a last resort. Next time you invoke playonlinux this folder will be regenerated, yet without the programs installed previously.
Some more ideas.

Regards!

---

### Post by manucontrovento on 2022-07-08
Hello and thanks for your reply

Thanks to your suggestions I found out that there was no amd64 bit version installed!
I don't know the reason. In the past (until a few weeks ago, when using Ubuntu Studio 20.04) I never experienced these issues.

So I installed a 64 bit version, restarted PlayOnLinux, but unfortunately the problem is still there. Same error message and if I try to ignore the problem, no application is installed.

I'll try with playonlinux on terminal to check some errors details... Or maybe I'll try choosing a different amd64 bit wine version...

As last thing I can try removing the .wine folder, and reinstalling all windows applications, but my feeling is that it wouldn't solve the problem...

---

### Post by Claus7 on 2022-07-08
Hello,

hope one of the ideas to help you. In addition, since you haven't installed anything, it might help to remove the .playonlinux folder as well. One more thing I would try, would be to install the application directly via wine, without using playonlinux. 

Regards!

---

### Post by deadflowr on 2022-07-08
> One more thing I would try, would be to install the application directly via wine, without using playonlinux.
I do not have any need to run windows programs in wine or otherwise, but this might be of interest for those who do: [https://flathub.org/apps/details/com.usebottles.bottles]("https://flathub.org/apps/details/com.usebottles.bottles")

---

### Post by manucontrovento on 2022-07-16
Hi everyone, I found the solution! wine-stable and win64 packages were missing!

---

