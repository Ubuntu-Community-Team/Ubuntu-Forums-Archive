---
title: "Computer freezes completely when I log out."
date: 2007-09-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by dopefish124 on 2007-09-05
Hi there! 
Often when I  log out or switch user on Ubuntu it freezes completely: the computer becomes unresponsive and the screen goes completely blank. I try terminating X with Ctrl+Alt+Backspace but it doesn't help at all. All I can do is manually switch off my computer and start it up again but I hate doing that and I fear problems could arise from it. So, why could this be happening and how do I fix it? I will post more details if necessary.

Thanks in advance! :)

---

### Post by Kilz on 2007-09-05
> **dopefish124 said:**
> Hi there! 
Often when I  log out or switch user on Ubuntu it freezes completely: the computer becomes unresponsive and the screen goes completely blank. I try terminating X with Ctrl+Alt+Backspace but it doesn't help at all. All I can do is manually switch off my computer and start it up again but I hate doing that and I fear problems could arise from it. So, why could this be happening and how do I fix it? I will post more details if necessary.

Thanks in advance! :)

It sounds like a bad video driver install to me.

---

### Post by cjazz on 2007-09-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/107115](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/107115) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I don't know what video card or driver you're using, but this has been a problem for me as well. It's a confirmed bug for the restricted driver fglrx for my card, ATI Radeon 200M.

In the bug report discussion, a workaround is suggested: editing /etc/X11/gdm/gdm.conf so that ALWAYSRESTARTSERVER=true. That's for Gnome users. KDE users, I believe, would edit etc/kde3/kdm/kdmrc and add or uncomment the line "TerminateServer=True". I should add that so far the Gnome workaround is working for me, but not everyone has reported success with this.

---

