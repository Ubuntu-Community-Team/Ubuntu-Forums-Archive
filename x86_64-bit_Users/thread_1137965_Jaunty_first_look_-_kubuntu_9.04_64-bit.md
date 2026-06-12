---
title: "Jaunty first look - kubuntu 9.04 64-bit"
date: 2009-04-26
forum: x86 64-bit Users
---

### Post by CaseWestern on 2009-04-26
Hi All:

I have installed Kubuntu 9.04 or Jaunty on my Dell XPS M1350 computer a while ago and felt like giving some review/information.

Mine is 64-bit architecture.

Things Worked:

1. Wireless - Right away, didnt have to google for anything. I have Broadcom 1395 card on my computer.

2. Sound works fine.

3. Microphone - worked fine with skype

4. Webcam - also worked righaway with skype

5. Installed skype, firefox, vbox from the medibuntu repos.

6. Graphics are simply superb.  I have to install NVIDIA drivers from the repos.

7.  Installed flash directly from the medibuntu repos.  After adding the medibuntu to your software sources list, I have just given this command sudo apt-get install flashplugin-nonfree and it worked fine.

Issues encountered:

1. When I installed the latest Nvidia drivers (number 180) from the repos for my Geforce 8600 card, the kwallet is not working fine.  I configured kwalled with the knetworkmanager.  When I deactivated the Nvidia drivers kwallet seems to be working fine.  

   Then I decided to give a try with the older version of Nvidia drivers (number 173) with which I didnt encounter any issues.  Kwallet is working fine.

    Except that for now I dont have any issues.  This new release is simply superb.  I am sure the KDE 4.2 desktop environment will be as stable as the one in kubuntu 8.04 viz., KDE 3.5.10.

Thanks

---

### Post by CaseWestern on 2009-04-26
Those who have downgraded to 8.04 from 8.10 because of so many issues, I would suggest you to give it a try.  This has some really cool experience with KDE 4.2 environment.

---

### Post by rajputrajat on 2009-05-15
I want to move to 64 bit with kubuntu 9.04 this time...
...was just looking for the same information...
thanks for posting this....

one question...
did they release KDE 4.2.3 packages for 64 bit on the same day when they did for 32 bit..???

---

### Post by Arup on 2009-05-15
You did everything right except for the flash, you should have installed the x64 Flash 10 alpha which runs superb on x64 Jaunty, Phoronix tests confirms that the Flash 10 alpha x64 outperformns x32 flash in Linux and Windows.

---

### Post by yamushk on 2009-05-20
> **CaseWestern said:**
> Hi All:

3. Microphone - worked fine with skype

4. Webcam - also worked righaway with skype

Thanks

I think most of the things work for me, but not skype. I can hear (after playing around a bit and using this link: 
[http://wiki.archlinux.org/index.php/Skype#B._Making_ALSA_.2B_dMix_work_for_Skype](http://wiki.archlinux.org/index.php/Skype#B._Making_ALSA_.2B_dMix_work_for_Skype)) but cannot be heard. The webcam doesn't work (did not work in 8.04 either until I gave up).

Would be happy if anyone could lend a helping hand.
If running skype using this commend:

ALSA_OSS_PCM_DEVICE="skype" aoss skype

Then I get a lot of error message.

For example: 
ALSA lib ../../../src/pcm/pcm.c:2165:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL skype
and so on...

take care!

Yamushk

---

