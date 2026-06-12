---
title: "[SOLVED] Nvidia Issue"
date: 2008-03-18
forum: openSUSE and SUSE Linux Enterprise
---

### Post by uberlube on 2008-03-18
Well I decided to try openSUSE 10.3 for the first time and after a few minor installation problems, I got into the desktop. Then I went to the SuSe Nvidia Wiki with the 1 touch install button and tryed to install my drivers. After telling me that there were some missing dependencies I told it to continue on anyway. After the install, I rebooted and could no longer log into the desktop, it would just boot me into the recovery command line. I did a clean install and I want to try again but its giving me the same message during the driver install which I have posted below. Any advice would be great, and no, I dont need the legacy driver.

---

### Post by RebounD11 on 2008-03-18
Now that's an extremely weird one ... I never got that one before...

Did you try that right after installation and did you do an online update before trying that?

---

### Post by RedDwarf on 2008-03-18
x11-video-nvidiaG01 requires nvidia-gfxG01-kmp-default, and nvidia-gfxG01-kmp-default requires kernel-default 2.6.22.16-0.1 or greater (openSUSE 10.3 comes with 2.6.22.5-31).
So probably the problem is that you don't have the update repository. But anyway... "There are no installable providers of nvidia-gfxG01-kmp" is the less helpful error message of all times. And the proposed solutions are bad and worse.

That's why people uses Smart instead of libzypp...

---

### Post by RebounD11 on 2008-03-18
> **RedDwarf said:**
> x11-video-nvidiaG01 requires nvidia-gfxG01-kmp-default, and nvidia-gfxG01-kmp-default requires kernel-default 2.6.22.16-0.1 or greater (openSUSE 10.3 comes with 2.6.22.5-31).
So probably the problem is that you don't have the update repository. But anyway... "There are no installable providers of nvidia-gfxG01-kmp" is the less helpful error message of all times. And the proposed solutions are bad and worse.

That's why people uses Smart instead of libzypp...

I use them both.. SMART for installing and zypper for updates... lately I use zypper for CLI installs. It's the "easy" way... "easy"=lazy :D
So far nothing broke... no conflicts and no hanging updates... (when that happens I use Yast to update and then the update loop stops)

---

### Post by 67GTA on 2008-03-18
RedDwarf is on the right track. The nvidia driver version you are trying to install with the "one click" is the newest version and has to be compiled with the kernel. The default kernel before you do any system upgrades is not compatible.You will have to add the update repository to Yast, update the system, and then install the nvidia driver with the one click install. If you get in this situation again, you can use ```
sax2 -r -m 0=nv
``` to revert to the 2-D driver so you can get to the desktop again.

---

### Post by uberlube on 2008-03-19
Thanks guys for the response but I found that SUSE isn't for me. My curiosity has been satisfied and I've gone back to what I know. THNX though. :)

---

### Post by RedDwarf on 2008-03-19
> **RebounD11 said:**
> lately I use zypper for CLI installs. It's the "easy" way... "easy"=lazy :D
"zypper in <package>" or "smart install <package>"... with smart it's just four more chars. You are REALLY lazy!!! ;)
Perhaps you could add an alias?
> alias lazy='smart install --explain'
alias update='smart upgrade --update --explain'

---

### Post by RebounD11 on 2008-03-20
> **RedDwarf said:**
> "zypper in <package>" or "smart install <package>"... with smart it's just four more chars. You are REALLY lazy!!! ;)
Perhaps you could add an alias?

I forgot smart doesn't require the gui :)
My bad... and yes I am EXTREMELY lazy, in a good way. I don't do stuff I don't like. For example I didn't go to any class I didn't like in highschool... I've never in 4 years seen my history teacher... or geography teacher, or biology teacher... some classes I can't remember at all :D

---

